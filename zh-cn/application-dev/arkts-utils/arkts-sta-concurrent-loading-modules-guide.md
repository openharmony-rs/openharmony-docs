# 业务模块并发加载场景 (ArkTS-Sta)
<!--Kit: ArkTS-->
<!--Subsystem: Utils-->
<!--Owner: @MofengMa-->
<!--Designer: @MofengMa-->
<!--Tester: @zsw_zhushiwei-->
<!--Adviser: @ge-yafang-->

应用启动或进入复杂页面时，可能需要初始化多个业务模块，例如定位、导航、订单、推荐等。如果这些初始化逻辑都在宿主线程串行执行，会增加页面可交互前的等待时间。ArkTS-Sta中可以使用[taskpool (启动任务池)](../reference/apis-arkts/arkts-sta-taskpool.md)并发执行彼此独立的初始化任务，在全部任务完成后再将模块实例返回宿主线程使用。

ArkTS-Sta不需要使用@Concurrent标记TaskPool任务函数，也不需要使用@Sendable声明模块对象。普通类实例可以在线程间共享；如果模块对象返回宿主线程后只由宿主线程访问，不需要额外同步。如果模块实例仍会被多个线程同时读写，则需要使用锁、原子类型或并发容器保护共享状态。

> **说明：**
>
> - 本文仅适用于ArkTS-Sta。
> - 本文中的“业务模块加载”指业务模块内部初始化逻辑的并发执行，不表示通过动态import()改变静态模块导入时机。模块初始化逻辑如果依赖UI组件、UI上下文或只允许在宿主线程调用的接口，不应放入TaskPool任务。

## 定义业务模块

以下示例定义两个独立业务模块。计算器模块用于模拟带有内部状态的业务SDK，定时器模块用于模拟异步业务能力。

```ts
// ArkTS-Sta示例
// sdk/Calculator.ets
export class Calculator {
  private history: Array<Array<string>> = [];
  totalCount: int = 0;

  static init(): Calculator {
    let calculator: Calculator = new Calculator();
    calculator.totalCount = 0;
    calculator.history = [];
    return calculator;
  }

  add(a: int, b: int): int {
    let result: int = a + b;
    this.newCalc(a + " + " + b, "" + result);
    return result;
  }

  sub(a: int, b: int): int {
    let result: int = a - b;
    this.newCalc(a + " - " + b, "" + result);
    return result;
  }

  mul(a: int, b: int): int {
    let result: int = a * b;
    this.newCalc(a + " * " + b, "" + result);
    return result;
  }

  getHistory(): Array<Array<string>> {
    return this.history;
  }

  showHistory(): void {
    for (let index: int = 0; index < this.totalCount; index++) {
      console.info(index + ": " + this.history[index][0] + " = " + this.history[index][1]); // 0: 1 + 2 = 3
    }
  }

  private newCalc(opt: string, ret: string): void {
    let record: Array<string> = [opt, ret];
    this.history.unshift(record);
    this.totalCount = this.history.length;
  }
}
```

```ts
// ArkTS-Sta示例
// sdk/TimerSdk.ets
export class TimerSdk {
  static init(): TimerSdk {
    return new TimerSdk();
  }

  countdown(time: int): Promise<boolean> {
    return new Promise<boolean>((resolve) => {
      setTimeout(() => {
        resolve(true);
      }, time);
    });
  }
}
```

## 并发初始化业务模块

多个初始化任务之间没有依赖关系时，可以使用TaskGroup统一提交。TaskGroup返回结果数组的顺序与addTask添加任务的顺序一致，适合在宿主线程汇总多个模块的初始化结果。

```ts
// ArkTS-Sta示例
// ModuleInitTask.ets
import { Calculator } from './sdk/Calculator';
import { TimerSdk } from './sdk/TimerSdk';

export class ModuleBundle {
  calculator: Calculator;
  timer: TimerSdk;

  constructor(calculator: Calculator, timer: TimerSdk) {
    this.calculator = calculator;
    this.timer = timer;
  }
}

export function initCalculator(): Calculator {
  return Calculator.init();
}

export function initTimerSdk(): TimerSdk {
  return TimerSdk.init();
}

export async function initBusinessModules(): Promise<ModuleBundle> {
  let group: taskpool.TaskGroup = new taskpool.TaskGroup("business-module-init");
  group.addTask(initCalculator);
  group.addTask(initTimerSdk);

  let results: Array<Any> = await taskpool.execute(group);
  return new ModuleBundle(results[0] as Calculator, results[1] as TimerSdk);
}
```

可以分别提交多个TaskPool任务，再通过Promise.all等待全部结果。该方式适合需要为不同任务分别设置回调或单独处理任务对象的场景。

```ts
// ArkTS-Sta示例
async function initModulesByPromiseAll(): Promise<ModuleBundle> {
  let calculatorPromise: Promise<Any> = taskpool.execute(initCalculator);
  let timerPromise: Promise<Any> = taskpool.execute(initTimerSdk);

  let results: Array<Any> = await Promise.all<Any>([calculatorPromise, timerPromise]);
  return new ModuleBundle(results[0] as Calculator, results[1] as TimerSdk);
}
```

## 在宿主线程使用业务模块

宿主线程在页面出现时触发模块初始化。初始化完成后，将返回的模块实例保存到页面成员中，后续按钮事件可以直接调用模块方法。

```ts
// ArkTS-Sta示例
// Index.ets
import { Entry, Text, Column, Component, Button, ClickEvent } from '@ohos.arkui.component'
import { State } from '@ohos.arkui.stateManagement'
import { Calculator } from './sdk/Calculator'
import { TimerSdk } from './sdk/TimerSdk'
import { initBusinessModules, ModuleBundle } from './ModuleInitTask'

@Entry
@Component
struct Index {
  @State loadState: string = "loading";
  calc?: Calculator;
  timer?: TimerSdk;

  aboutToAppear(): void {
    initBusinessModules().then((bundle: ModuleBundle) => {
      this.calc = bundle.calculator;
      this.timer = bundle.timer;
      this.loadState = "loaded";
    }).catch((error: Error) => {
      this.loadState = "failed";
      console.error("init business modules failed: " + error.message); // init business modules failed: xxx
    });
  }

  build() {
    Column(undefined) {
      Text(this.loadState).fontSize(20)
      Button("calculate add")
        .onClick((e: ClickEvent) => {
          let calculator: Calculator | undefined = this.calc;
          if (calculator === undefined) {
            console.info("calculator is not ready"); // calculator is not ready
            return;
          }
          let result: int = calculator.add(1, 2);
          console.info("result is " + result); // result is 3
        })
      Button("show history")
        .onClick((e: ClickEvent) => {
          let calculator: Calculator | undefined = this.calc;
          if (calculator === undefined) {
            console.info("calculator is not ready"); // calculator is not ready
            return;
          }
          calculator.showHistory();
        })
      Button("countdown")
        .onClick((e: ClickEvent) => {
          let timerSdk: TimerSdk | undefined = this.timer;
          if (timerSdk === undefined) {
            console.info("timer is not ready"); // timer is not ready
            return;
          }
          console.info("timer start"); // timer start
          timerSdk.countdown(1000).then(() => {
            console.info("timer end"); // timer end
          }).catch((error: Error) => {
            console.error("timer failed: " + error.message); // timer failed: xxx
          });
        })
    }
    .height('100%')
    .width('100%')
  }
}
```

## 使用建议

- 业务模块初始化任务之间没有依赖时，可使用TaskGroup并发执行；存在依赖时，应按依赖关系拆分为多轮任务，或在一个任务中按顺序初始化。
- TaskPool适合执行初始化计算、配置解析、缓存构建等短时任务。需要长期持有线程上下文、监听事件或维护线程亲和资源时，建议使用[EAWorker简介 (ArkTS-Sta)](eaworker-introduction.md)。
- 返回宿主线程的模块对象如果只在宿主线程使用，可以按普通对象使用；如果多个线程会继续访问同一模块实例，需要为内部可变状态设计同步策略。
- 不要在TaskPool任务中初始化只能在UI线程使用的对象，例如UI组件、窗口对象或需要宿主线程上下文的接口。
- 动态ArkTS中的Sendable容器迁移到ArkTS-Sta时，应改为普通静态类型、数组或并发容器，并明确是否需要共享、快照或同步访问。
