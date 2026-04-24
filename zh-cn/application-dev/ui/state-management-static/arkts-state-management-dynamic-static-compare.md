# 状态管理动静态差异

由于动态语言不支持多线程，因此在动态语言上演进出静态语言，以原生支持多线程。

部分基于动态语言实现的功能无法通过静态语言实现，导致部分功能受限或行为发生更改。下面介绍状态管理功能在ArkTS-Dyn和ArkTS-Sta上的差异。

## V1和V2混用无需enableV2Compatibility
   
在ArkTS-Dyn（API version 19之后）中，状态管理V1和V2混用时，需要调用[`UIUtils.enableV2Compatibility`](../state-management/arkts-v1-v2-mixusage.md#enablev2compatibility)和[`UIUtils.makeV1Observed`](../state-management/arkts-v1-v2-mixusage.md#makev1observed)接口来实现V1和V2的状态变量传递。

而在ArkTS-Sta中，由于采用相同的状态管理实现逻辑，`@Component`和`@ComponentV2`天然支持V1/V2状态变量的传递，因此无需调用`UIUtils.enableV2Compatibility`和`UIUtils.makeV1Observed`接口，可以直接混用状态管理V1与V2。


具体混用规则可参考[状态管理V1V2混用指导](./arkts-v1-v2-mixusage.md)。

## 静态无需mutableBuilder

在ArkTS-Dyn中，当需要动态切换全局@Builder时，需要使用mutableBuilder来实现，因为[wrapBuilder](../state-management/arkts-wrapBuilder.md)不支持二次赋值。

而在ArkTS-Sta中，由于采用静态语言特性，可以直接使用状态变量配合条件渲染来实现全局@Builder的动态切换，无需使用mutableBuilder。

例如：

  ```typescript
  'use static'

  import { Entry, Builder, ComponentV2, Local, Text, Button, Column } from '@kit.ArkUI';

  @Builder
  function textBuilder(p: { text: string }) {
    Text(p.text)
  }

  @Builder
  function buttonBuilder(p: { text: string }) {
    Button(p.text)
  }

  @Entry
  @ComponentV2
  struct Index {
    @Local useText: boolean = true;
    @Local message: string = 'init';

    build() {
      Column() {
        // 直接通过条件判断切换@Builder
        if (this.useText) {
          textBuilder({ text: this.message })
        } else {
          buttonBuilder({ text: this.message })
        }
        Button('Switch Builder')
          .onClick(() => {
            this.useText = !this.useText;
          })
      }
    }
  }
  ```

## 双向绑定语法差异

ArkTS在不同语言版本和状态管理版本中提供了不同的双向绑定方式。

### 三种方式对比

| 特性 | 动态：`$$` 运算符 | 动态：`!!` 运算符 | 静态：`$$()` 函数 |
|------|------------------|------------------|-----------------|
| 语言版本 | ArkTS-Dyn | ArkTS-Dyn | ArkTS-Sta (静态) |
| 状态管理版本 | V1 | V2 | V1 |
| 系统组件双向绑定 | 支持 `$$this.text` | 支持 `this.text!!` | 支持 `$$(this.text)` |
| 自定义组件双向绑定 | 不支持 | 支持 `this.value!!` 语法糖 | 不支持，需使用@Param+@Event |
| 语法形式 | 前缀运算符 | 后缀运算符 | 函数调用 |
| 是否需要导入 | 否 | 否 | 是，需导入 `$$` |
| 起始API版本 | API 10 | API 12 | API 23 |

### 关键差异说明
- 自定义组件双向绑定

  ArkTS-Dyn：支持 `!!` 语法糖（API 12+）

   ```typescript
   // ArkTS-Dyn - 使用!!语法糖
   @ComponentV2
   struct Child {
     @Param value: number = 0;
     @Event $value: (val: number) => void = () => {};
   }

   // 父组件中直接使用!!语法糖
   Child({ value: this.value!! })
   ```

   ArkTS-Sta：不支持 `!!` 语法糖，必须显式使用 @Param + @Event

   ```typescript
   // ArkTS-Sta - 必须显式传递@Param和@Event
   import { ComponentV2, Param, Event } from '@kit.ArkUI';

   @ComponentV2
   struct Child {
     @Param value: number = 0;
     @Event $value: (val: number) => void = () => {};
   }

   // 父组件中必须显式传递参数
   Child({
     value: this.value,
     $value: (val: number) => { this.value = val; }
   })
   ```

- 系统组件双向绑定

   ArkTS-Dyn：

   - `$$` 运算符（API 10）
   - `!!` 运算符（API 12，推荐）

   ```typescript
   // ArkTS-Dyn - $$运算符
   TextInput({ text: $$this.text })

   // ArkTS-Dyn - !!运算符（API 12+，推荐使用）
   TextInput({ text: this.text!! })
   ```

   ArkTS-Sta：使用 `$$()` 函数

   ```typescript
   // ArkTS-Sta - $$()函数
   import { $$, TextInput } from '@ohos.arkui.component';

   TextInput({ text: $$(this.stateVar) })
   ```

### 使用建议

- ArkTS-Dyn状态管理V2：
   - 系统组件推荐使用 `!!` 运算符（API 12+）。
   - 自定义组件使用 `!!` 运算符实现双向绑定。

- ArkTS-Sta (静态)：
  - 系统组件使用 `$$()` 函数。
  - 自定义组件使用 `@Param` + `@Event` 显式传递，不支持语法糖。

## 修改状态变量后，@Monitor回调的触发机制不同

在状态变量被修改后，状态管理框架需要异步触发依赖状态变量的回调函数，比如触发[@Monitor](./arkts-static-new-monitor.md)回调，或者触发[@Computed](./arkts-static-new-computed.md)重新计算。ArkTS-Dyn中，该触发机制使用Promise任务异步，新建的Promise会被存入任务队列并延时执行。

ArkTS-Sta中，状态管理框架使用Vsync（渲染同步信号）异步触发依赖更新，在每一帧渲染UI组件之前执行依赖状态变量的回调函数。所以状态管理回调的触发机制不再依赖Promise任务，而是申请额外的Vsync渲染。Vsync由后端触发执行，相比Promise方案性能更好，但是可能会导致监听回调函数被执行的次数变少。受影响的[addMonitor](./arkts-static-new-addmonitor-clearmonitor.md)示例如下。

ArkTS-Dyn示例：

```ts
import { UIUtils } from '@kit.ArkUI';

@ObservedV2
class Info {
  @Trace message: string = 'not initialized';

  constructor() {
    UIUtils.addMonitor(this, 'message', this.onMessageChange);
    // 会触发onMessageChange回调，打印`message change from not initialized to initialized`
    this.message = 'initialized'; 
  }
  onMessageChange(monitor: IMonitor) {
    console.info(`message change from ${monitor.value()?.before} to ${monitor.value()?.now}`);
  }
}

@Entry
@ComponentV2
struct Page {
  info: Info = new Info();

  aboutToAppear(): void {
    // 会再次触发onMessageChange回调，打印`message change from initialized to Index aboutToAppear`
    this.info.message = 'Index aboutToAppear'; 
  }

  build() {
    Column() {
      Text('Hello world')
    }
  }
}
```

ArkTS-Sta示例：


```ts
'use static'

import { ObservedV2, Trace, Local, IMonitor, IMonitorDecoratedVariable, UIUtils,
         ComponentV2, Column, Entry, Button, Text } from '@kit.ArkUI';

@ObservedV2
class Info {
  @Trace message: string = 'not initialized';
  messageMonitor?: IMonitorDecoratedVariable;

  constructor() {
    this.messageMonitor = UIUtils.addMonitor(() => this.message, this.onMessageChange);
    // 不会触发onMessageChange回调，因为this.message修改时申请的Vsync在下方aboutToAppear执行后才被执行
    // 导致该修改被下方aboutToAppear里的修改覆盖。
    this.message = 'initialized';
  }
  onMessageChange(monitor: IMonitor) {
    monitor.dirty.forEach((path: string) => {
      console.info(`message change from ${monitor.value<string>(path)?.before} to ${monitor.value<string>(path)?.now}`);
    });
  }
}

@Entry
@ComponentV2
struct Page {
  @Local info: Info = new Info();

  aboutToAppear(): void {
    // 触发onMessageChange回调，打印`message change from not initialized to Index aboutToAppear`
    this.info.message = 'Index aboutToAppear';
  }

  build() {
    Column() {
      Text('Hello world')
    }
  }
}
```

