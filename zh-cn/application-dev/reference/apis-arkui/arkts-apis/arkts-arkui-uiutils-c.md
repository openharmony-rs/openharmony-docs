# UIUtils

UIUtils提供一些方法，用于处理状态管理相关的数据转换。

**起始版本：** 12

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## addMonitor

```TypeScript
static addMonitor(target: object, path: string | string[], monitorCallback: MonitorCallback, options?: MonitorOptions): void
```

给状态管理V2的状态变量动态添加监听方法，详见
[addMonitor/clearMonitor](../../../../ui/state-management/arkts-new-addMonitor-clearMonitor.md)。

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本20开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| target | object | 是 | 目标对象，仅支持[@ComponentV2](../../../../ui/state-management/arkts-create-custom-components.md#componentv2)和[@ObservedV2](../../../../ui/state-management/arkts-new-observedV2-and-trace.md)实例。&lt;/br&gt;对于不支持的类型，会抛出运行时错误。 |
| path | string \| string[] | 是 | 添加监听的变量名路径。可指定一个路径或者传入string数组用于一次性指定多个监听的变量路径。&lt;/br&gt;仅支持string和string数组，对于不支持的类型，会抛出运行时错误。 |
| monitorCallback | MonitorCallback | 是 | 给对应的状态变量注册的监听函数，即path路径对应的状态变量改变时，会回调对应的函数。&lt;/br&gt;对于不支持的类型，会抛出运行时错误。 |
| options | MonitorOptions | 否 | 监听函数的配置项，具体可见[MonitorOptions](arkts-arkui-monitoroptions-i.md)。默认为异步回调。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [130000](../errorcode-stateManagement.md#130000-addmonitorclearmonitor非法目标对象) | The target is not a custom component instance or V2 class instance. |
| [130001](../errorcode-stateManagement.md#130001-addmonitorclearmonitor非法路径) | The path is invalid. |
| [130002](../errorcode-stateManagement.md#130002-addmonitorclearmonitor非法回调方法) | monitorCallback is not a function or an anonymous function. |

## applySync

```TypeScript
static applySync<T>(task: TaskCallback): T
```

同步刷新指定的状态变量，该接口接收一个闭包函数，仅刷新闭包函数内的修改，包括更新[@Computed计算](../../../../ui/state-management/arkts-new-computed.md)、
[@Monitor回调](../../../../ui/state-management/arkts-new-monitor.md)以及重新渲染UI节点，详见
[applySync/flushUpdates/flushUIUpdates接口：同步刷新](../../../../ui/state-management/arkts-new-applySync-flushUpdates-flushUIUpdates.md)。

**起始版本：** 22

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本22开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| task | TaskCallback | 是 | 闭包函数，该闭包中产生的状态变量修改会同步执行。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 闭包函数执行得到的返回值。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [140001](../errorcode-stateManagement.md#140001-applysyncflushupdatesflushuiupdates非法调用) | The function is not allowed to be called in @Computed |

**示例：**

```TypeScript
import { UIUtils } from '@kit.ArkUI';

@Entry
@ComponentV2
struct Index {
  @Local w: number = 50; // 宽度
  @Local h: number = 50; // 高度
  @Local message: string = 'Hello';

  build() {
    Column() {
      Button('change size')
        .margin(20)
        .onClick(() => {
          // 在执行动画前，存在额外的修改
          UIUtils.applySync(() => {
            this.w = 100;
            this.h = 100;
            this.message = 'Hello World';
          });
          // 动画在1s内，Column方框的尺寸由（100*100）渐变为（200*200），方框内的文本变为Hello ArkUI
          this.getUIContext().animateTo({
            duration: 1000
          }, () => {
            console.info(`animateTo-in, w=${this.w}, h=${this.h}`);
            this.w = 200;
            this.h = 200;
            this.message = 'Hello ArkUI';
            console.info(`animateTo-out, w=${this.w}, h=${this.h}`);
          });
        })
      // Column方框
      Column() {
        Text(`${this.message}`)
      }
      .backgroundColor('#ff17a98d')
      .width(this.w)
      .height(this.h)
    }
  }
}

```

## canBeObserved

```TypeScript
static canBeObserved<T extends object>(source: T): ObservedResult
```

判断数据对象是否为可观察对象，并返回观察结果。详见[canBeObserved接口：判断对象是否为可被观察对象](../../../../ui/state-management/arkts-new-canBeObserved.md)。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本23开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| source | T | 是 | 输入一个数据对象，判断其是否可被观察。支持Array、Map、Set和Date类型数据。&lt;/br&gt;具体使用规则，详见[canBeObserved接口：判断对象是否为可被观察对象](../../../../ui/state-management/arkts-new-canBeObserved.md)。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| ObservedResult | 返回对象是否可被观察的结果。 |

**示例：**

```TypeScript
import { UIUtils } from '@kit.ArkUI';
import { DecoratorInfo, ElementInfo } from '@ohos.arkui.StateManagement';
import { hilog } from '@kit.PerformanceAnalysisKit';

const TAG = 'CanBeObserved';

class Student {
  public name?: string;

  constructor(name?: string) {
    this.name = name ?? '';
  }

  // 在对象中提供判断该对象是否为可被观察对象的方法
  test(): void {
    const result = UIUtils.canBeObserved(this);
    // 对象是否可被观察
    const isObserved = result.isObserved;
    hilog.info(0x00, TAG, `isObserved: ${JSON.stringify(isObserved)}`);
    // 对象是否可被观察的原因
    const reason = result.reason;
    hilog.info(0x00, TAG, `reason: ${reason}`);
    // 对象可被观察时，对象关联的装饰器信息
    const decoratorInfoArr = result.decoratorInfo;
    decoratorInfoArr.forEach((decorator: DecoratorInfo) => {
      // 装饰器名称
      const decoratorName = decorator.decoratorName;
      hilog.info(0x00, TAG, `decoratorName: ${decoratorName}`);
      // 装饰器装饰的属性名称
      const stateVariableName = decorator.stateVariableName;
      hilog.info(0x00, TAG, `stateVariableName: ${stateVariableName}`);
      // 装饰器所在的组件名称
      const owningName = decorator.owningComponentOrClassName;
      hilog.info(0x00, TAG, `owningComponentOrClassName: ${owningName}`);
      // 装饰器所在的组件id
      const owningId = decorator.owningComponentId;
      hilog.info(0x00, TAG, `owningComponentId: ${owningId}`);
      // 装饰器关联的组件信息
      const dependentInfo = decorator.dependentInfo;
      dependentInfo.forEach((elementInfo: ElementInfo) => {
        // 装饰器关联的组件名称
        const eleName = elementInfo.elementName;
        hilog.info(0x00, TAG, `elementName: ${eleName}`);
        // 装饰器关联的组件id
        const eleId = elementInfo.elementId;
        hilog.info(0x00, TAG, `elementId: ${eleId}`);
      });
    });
  }
}

@Entry
@Component
struct Index {
  @State student: Student = new Student('LiMei');

  build() {
    Column({ space: 20 }) {
      Classroom({ student: this.student })
      Home({ student: this.student })
      Button('test')
        .onClick(() => {
          // 开发者可以在任意页面中使用接口来判断当前对象是否为可被观察对象
          this.student.test();
        })
    }
    .height('100%')
    .width('100%')
    .justifyContent(FlexAlign.Center)
    .alignItems(HorizontalAlign.Center)
  }
}

@Component
export struct Classroom {
  @State student: Student = new Student();

  build() {
    Column() {
      Text('Classroom ' + this.student.name)
      School({ student: this.student })
    }
  }
}

@Component
export struct Home {
  @State student: Student = new Student();

  build() {
    Column() {
      Text('Home ' + this.student.name)
    }
  }
}

@Component
export struct School {
  @State student: Student = new Student();

  build() {
    Column() {
      Text('School ' + this.student.name)
    }
  }
}

```

## clearMonitor

```TypeScript
static clearMonitor(target: object, path: string | string[], monitorCallback?: MonitorCallback) : void
```

删除通过[addMonitor](arkts-arkui-uiutils-c.md#addmonitor-1)给状态管理V2的状态变量添加的监听方法，详见
[addMonitor/clearMonitor](../../../../ui/state-management/arkts-new-addMonitor-clearMonitor.md)。

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本20开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| target | object | 是 | 目标对象，仅支持[@ComponentV2](../../../../ui/state-management/arkts-create-custom-components.md#componentv2)和[@ObservedV2](../../../../ui/state-management/arkts-new-observedV2-and-trace.md)实例。&lt;/br&gt;对于不支持的类型，会抛出运行时错误。 |
| path | string \| string[] | 是 | 删除监听的变量名路径。可指定一个路径或者传入string数组用于一次性指定删除多个状态变量的监听函数。&lt;/br&gt;仅支持string和数组，对于不支持的类型，会抛出运行时错误。 |
| monitorCallback | MonitorCallback | 否 | 指定被删除的监听函数。&lt;/br&gt;当开发者不传此参数时，将删除path对应变量注册的所有监听函数。&lt;/br&gt;对于不支持的类型，会抛出运行时错误。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [130000](../errorcode-stateManagement.md#130000-addmonitorclearmonitor非法目标对象) | The target is not a custom component instance or V2 class instance. |
| [130001](../errorcode-stateManagement.md#130001-addmonitorclearmonitor非法路径) | The path is invalid. |
| [130002](../errorcode-stateManagement.md#130002-addmonitorclearmonitor非法回调方法) | monitorCallback is not a function or an anonymous function. |

## enableV2Compatibility

```TypeScript
static enableV2Compatibility<T extends object>(source: T): T
```

使V1的状态变量能够在\@ComponentV2中观察，主要应用于状态管理V1、V2混用场景。详见
[状态管理V1和V2混用指导（API version 19及之后）](../../../../ui/state-management/arkts-v1-v2-mixusage.md)。

**起始版本：** 19

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本19开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| source | T | 是 | 数据源，仅支持V1状态数据。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 如果数据源是V1的状态数据，则返回能够在@ComponentV2中观察的数据。否则返回数据源本身。 |

**示例：**

```TypeScript
import { UIUtils } from '@kit.ArkUI';

@Observed
class ObservedClass {
  name: string = 'Tom';
}

@Entry
@Component
struct CompV1 {
  @State observedClass: ObservedClass = new ObservedClass();

  build() {
    Column() {
      Text(`@State observedClass: ${this.observedClass.name}`)
        .onClick(() => {
          this.observedClass.name = 'State'; // 刷新
        })
      // 将V1的状态变量使能V2的观察能力
      CompV2({ observedClass: UIUtils.enableV2Compatibility(this.observedClass) })
    }
  }
}

@ComponentV2
struct CompV2 {
  @Param observedClass: ObservedClass = new ObservedClass();

  build() {
    // V1状态变量在使能V2观察能力后，可以在V2观察第一层的变化
    Text(`@Param observedClass: ${this.observedClass.name}`)
      .onClick(() => {
        this.observedClass.name = 'Param'; // 刷新
      })
  }
}

```

## flushUIUpdates

```TypeScript
static flushUIUpdates(): void
```

立即处理在调用该函数之前所有的状态变量修改，同步[标脏](../../../../ui/state-management/arkts-state-management-introduce.md#触发更新)对应的UI节点，但不会同步执行

**起始版本：** 22

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本22开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [140001](../errorcode-stateManagement.md#140001-applysyncflushupdatesflushuiupdates非法调用) | The function is not allowed to be called in @Computed |
| [140002](../errorcode-stateManagement.md#140002-flushupdatesflushuiupdates非法调用) | The function is not allowed to be called in @Monitor |

**示例：**

```TypeScript
import { UIUtils } from '@kit.ArkUI';

@Entry
@ComponentV2
struct Index {
  @Local w: number = 50; // 宽度
  @Local h: number = 50; // 高度
  @Local message: string = 'Hello';

  build() {
    Column() {
      Button('change size')
        .margin(20)
        .onClick(() => {
          // 在执行动画前，存在额外的修改
          this.w = 100;
          this.h = 100;
          this.message = 'Hello World';
          // 立即处理上述状态变量修改，同步标脏对应的UI节点
          UIUtils.flushUIUpdates();
          // 动画在1s内，Column方框的尺寸由（100*100）渐变为（200*200），方框内的文本变为Hello ArkUI
          this.getUIContext().animateTo({
            duration: 1000
          }, () => {
            console.info(`animateTo-in, w=${this.w}, h=${this.h}`);
            this.w = 200;
            this.h = 200;
            this.message = 'Hello ArkUI';
            console.info(`animateTo-out, w=${this.w}, h=${this.h}`);
          });
        })
      // Column方框
      Column() {
        Text(`${this.message}`)
      }
      .backgroundColor('#ff17a98d')
      .width(this.w)
      .height(this.h)
    }
  }
}

```

## flushUpdates

```TypeScript
static flushUpdates(): void
```

同步刷新在调用该函数之前所有的状态变量修改，包括更新@Computed计算、@Monitor回调以及重新渲染UI节点，详见
[applySync/flushUpdates/flushUIUpdates接口：同步刷新](../../../../ui/state-management/arkts-new-applySync-flushUpdates-flushUIUpdates.md)。

**起始版本：** 22

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本22开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [140001](../errorcode-stateManagement.md#140001-applysyncflushupdatesflushuiupdates非法调用) | The function is not allowed to be called in @Computed |
| [140002](../errorcode-stateManagement.md#140002-flushupdatesflushuiupdates非法调用) | The function is not allowed to be called in @Monitor |

**示例：**

```TypeScript
import { UIUtils } from '@kit.ArkUI';

@Entry
@ComponentV2
struct Index {
  @Local w: number = 50; // 宽度
  @Local h: number = 50; // 高度
  @Local message: string = 'Hello';

  build() {
    Column() {
      Button('change size')
        .margin(20)
        .onClick(() => {
          // 在执行动画前，存在额外的修改
          this.w = 100;
          this.h = 100;
          this.message = 'Hello World';
          UIUtils.flushUpdates();
          // 动画在1s内，Column方框的尺寸由（100*100）渐变为（200*200），方框内的文本变为Hello ArkUI
          this.getUIContext().animateTo({
            duration: 1000
          }, () => {
            console.info(`animateTo-in, w=${this.w}, h=${this.h}`);
            this.w = 200;
            this.h = 200;
            this.message = 'Hello ArkUI';
            console.info(`animateTo-out, w=${this.w}, h=${this.h}`);
          });
        })
      // Column方框
      Column() {
        Text(`${this.message}`)
      }
      .backgroundColor('#ff17a98d')
      .width(this.w)
      .height(this.h)
    }
  }
}

```

## getCustomComponentContext

```TypeScript
static getCustomComponentContext<T extends BaseCustomComponent>(customComponent: T): CustomComponentContext
```

返回给定@Component(V1)或@ComponentV2的[CustomComponentContext](arkts-arkui-customcomponentcontext-i.md)。使用它来访问组件的复用池。有关复用池的详细信息，请参阅
[全局复用池：集中化的组件回收与复用](../../../../ui/state-management/arkts-global-reuse-pool.md)。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本26.0.0开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| customComponent | T | 是 | 要获取其上下文的@Component或@ComponentV2实例。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| CustomComponentContext | 给定组件实例的上下文对象。 |

**示例：**

```TypeScript
import { UIUtils } from '@kit.ArkUI';

@ReusableV2
@ComponentV2
struct ReusableChild {
  aboutToRecycle() {
    console.info('ReusableChild aboutToRecycle');
  }
  aboutToReuse() {
    console.info('ReusableChild aboutToReuse');
  }

  build() {
    Text('ReusableChild')
  }
}

@Entry
@ComponentV2({ 
  reusePool: 'shared', // 声明共享全局复用池
  poolAccepts: [ReusableChild], // 全局复用池接纳子组件类型ReusableChild
  freezeWhenInactive: false // 关闭组件冻结功能。该参数必须在声明reusePool时提供，也可以开启组件冻结。
})
struct Index {
  @Local showChild: boolean = true;

  inspectPool() {
    // 获取此组件的CustomComponentContext
    const context = UIUtils.getCustomComponentContext(this);
    // 通过上下文访问复用池。
    const pool = context.getReusePool();
    if (pool) {
      const info = pool.getReusableInfo(ReusableChild);
      if (info && !Array.isArray(info)) {
        console.info(`ReusableChild 在池中: count=${info.count}, maxCount=${info.maxCount}`);
      }
    }
  }

  build() {
    Column() {
      Button('切换子组件')
        .onClick(() => { 
          this.showChild = !this.showChild;
        })
      Button('检查池')
        .onClick(() => {
          this.inspectPool();
        })
      if (this.showChild) {
        ReusableChild()
      }
    }
  }
}

```

## getLifecycle

```TypeScript
static getLifecycle<T extends BaseCustomComponent>(customComponent: T): CustomComponentLifecycle
```

getLifecycle用于获取[自定义组件的生命周期](ComponentInit)实例。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本23开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| customComponent | T | 是 | 自定义组件实例。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| CustomComponentLifecycle | 自定义组件的生命周期实例。 |

**示例：**

```TypeScript
import { UIUtils, ComponentAppear } from '@kit.ArkUI';

@Entry
@Component
struct Index {
  @State lifecycleState: number = -1;

  @ComponentAppear
  myAppear() {
    // UIUtils.getLifecycle获得自定义组件的生命周期实例，getCurrentState查询自定义组件当前生命周期。
    // 预期查询到的生命周期为CustomComponentLifecycleState.APPEARED = 1。
    this.lifecycleState = UIUtils.getLifecycle(this).getCurrentState();
  }

  build() {
    Text(`${this.lifecycleState}`)
  }
}

```

## getTarget

```TypeScript
static getTarget<T extends object>(source: T): T
```

从状态管理框架包裹的代理对象中获取原始对象。详见[getTarget接口：获取状态管理框架代理前的原始对象](../../../../ui/state-management/arkts-new-getTarget.md)。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| source | T | 是 | 数据源对象。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 数据源对象去除状态管理框架所加代理后的原始对象。 |

**示例：**

```TypeScript
import { UIUtils } from '@kit.ArkUI';

class NonObservedClass {
  name: string = 'Tom';
}

let nonObservedClass: NonObservedClass = new NonObservedClass();

@Entry
@Component
struct Index {
  @State someClass: NonObservedClass = nonObservedClass;

  build() {
    Column() {
      Text(`this.someClass === nonObservedClass: ${this.someClass === nonObservedClass}`) // false
      Text(`UIUtils.getTarget(this.someClass) === nonObservedClass: ${UIUtils.getTarget(this.someClass) ===
        nonObservedClass}`) // true
    }
  }
}

```

## makeBinding

```TypeScript
static makeBinding<T>(getter: GetterCallback<T>): Binding<T>
```

创建只读的单向数据绑定实例，用于构建[\@Builder](../../../../ui/state-management/arkts-builder.md)函数中参数类型为`Binding`的对应实参。

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本20开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| getter | GetterCallback&lt;T&gt; | 是 | 获取值的回调函数，每次访问值都会重新执行函数，获取最新值。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Binding&lt;T&gt; | 仅包含一个`value`属性，用于获取当前绑定的值。只能读取值，不能直接修改。 |

**示例：**

```TypeScript
import { Binding, UIUtils } from '@kit.ArkUI';

@Builder
function CustomButton(num1: Binding<number>) {
  Row() {
    Button(`Custom Button: ${num1.value}`)
      .onClick(() => {
        // num1.value += 1; 会报错，Binding类型不支持修改
      })
  }
}

@Entry
@ComponentV2
struct CompV2 {
  @Local number1: number = 5;
  @Local number2: number = 10;

  build() {
    Column() {
      Text('parent component')

      CustomButton(
        /**
         * 创建只读绑定实例
         * @param getter - 返回this.number1的函数
         * @returns 只读的Binding<number>对象
         *
         * 特点：
         * 1. 每次访问.value时重新计算
         * 2. 不能直接修改值
         */
        UIUtils.makeBinding<number>(
          () => this.number1 // GetterCallback
        )
      )
    }
  }
}

```

## makeBinding

```TypeScript
static makeBinding<T>(getter: GetterCallback<T>, setter: SetterCallback<T>): MutableBinding<T>
```

创建可修改的双向数据绑定实例，用于构建\@Builder函数中参数类型为`MutableBinding`的对应实参。

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本20开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| getter | GetterCallback&lt;T&gt; | 是 | 获取值的回调函数，每次访问值都会重新执行函数，获取最新值。 |
| setter | SetterCallback&lt;T&gt; | 是 | 定义如何更新值，当`.value`被修改时自动调用此函数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| MutableBinding&lt;T&gt; | 包含一个`value`属性，支持通过`.value`读取和修改数据，设置值时会检查类型是否匹配泛型`T`。 |

**示例：**

```TypeScript
import { Binding, MutableBinding, UIUtils } from '@kit.ArkUI';

@Builder
function CustomButton(num2: MutableBinding<number>) {
  Row() {
    Button(`Custom Button: ${num2.value}`)
      .onClick(() => {
        // MutableBinding类型支持修改
        num2.value += 1;
      })
  }
}

@Entry
@ComponentV2
struct CompV2 {
  @Local number1: number = 5;
  @Local number2: number = 10;

  build() {
    Column() {
      Text('parent component')

      CustomButton(
        /**
         * 创建可变绑定
         * @param getter - 返回this.number2的函数
         * @param setter - 当绑定值修改时调用的回调
         * @returns 可变的MutableBinding<number>对象
         *
         * 特点：
         * 1. 支持读取和写入操作
         * 2. 修改.value时会自动调用setter回调
         */
        UIUtils.makeBinding<number>(
          () => this.number2, // GetterCallback
          (val: number) => {
            this.number2 = val;
          }) // SetterCallback
      )
    }
  }
}

```

## makeObserved

```TypeScript
static makeObserved<T extends object>(source: T): T
```

将普通不可观察数据变为可观察数据。详见[makeObserved接口：将非观察数据变为可观察数据](../../../../ui/state-management/arkts-new-makeObserved.md)。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| source | T | 是 | 数据源对象。支持非@Observed和@ObservedV2装饰的class，JSON.parse返回的Object和@Sendable修饰的class。&lt;/br&gt;支持Array、Map、Set和Date。&lt;/br&gt;支持collections.Array, collections.Set和collections.Map。&lt;/br&gt;具体使用规则，详见[makeObserved接口：将非观察数据变为可观察数据](../../../../ui/state-management/arkts-new-makeObserved.md)。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 可观察的数据。 |

**示例：**

```TypeScript
import { UIUtils } from '@kit.ArkUI';

class NonObservedClass {
  name: string = 'Tom';
}

@Entry
@ComponentV2
struct Index {
  // 使用makeObserved将NonObservedClass实例变为可观察对象
  observedClass: NonObservedClass = UIUtils.makeObserved(new NonObservedClass());
  nonObservedClass: NonObservedClass = new NonObservedClass();

  build() {
    Column() {
      Text(`observedClass: ${this.observedClass.name}`)
        .onClick(() => {
          this.observedClass.name = 'Jane'; // 刷新
        })
      Text(`observedClass: ${this.nonObservedClass.name}`)
        .onClick(() => {
          this.nonObservedClass.name = 'Jane'; // 不刷新
        })
    }
  }
}

```

## makeV1Observed

```TypeScript
static makeV1Observed<T extends object>(source: T): T
```

将不可观察的对象包装成状态管理V1可观察的对象，其能力等同于@Observed，可初始化@ObjectLink。

该接口可搭配[enableV2Compatibility](arkts-arkui-uiutils-c.md#enablev2compatibility-1)应用于状态管理V1和V2混用场景，详见
[状态管理V1和V2混用指导（API version 19及之后）](../../../../ui/state-management/arkts-v1-v2-mixusage.md)。

**起始版本：** 19

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本19开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| source | T | 是 | 数据源。支持普通class、Array、Map、Set、Date类型。&lt;/br&gt;不支持[@arkts.collections (ArkTS容器集)](../../apis-arkts/arkts-apis/arkts-collections.md)和[@Sendable](../../../../arkts-utils/arkts-sendable.md)修饰的class。&lt;/br&gt;不支持undefined和null。不支持状态管理V2的数据和[makeObserved](arkts-arkui-uiutils-c.md#makeobserved-1)的返回值。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 对于支持的入参类型，返回状态管理V1的观察数据。对于不支持的入参类型，返回数据源对象本身。 |

**示例：**

```TypeScript
import { UIUtils } from '@kit.ArkUI';

class Outer {
  outerValue: string = 'outer';
  inner: Inner;

  constructor(inner: Inner) {
    this.inner = inner;
  }
}

class Inner {
  interValue: string = 'inner';
}

@Entry
@Component
struct Index {
  // 使用makeV1Observed将Inner实例包装为V1可观察对象，传入Outer构造函数
  @State outer: Outer = new Outer(UIUtils.makeV1Observed(new Inner()));

  build() {
    Column() {
      // makeV1Observed的返回值可初始化@ObjectLink
      Child({ inner: this.outer.inner })
    }
    .height('100%')
    .width('100%')
  }
}

@Component
struct Child {
  @ObjectLink inner: Inner;

  build() {
    Text(`${this.inner.interValue}`)
      .onClick(() => {
        this.inner.interValue += '!';
      })
  }
}

```

