# 自定义组件的生命周期（推荐）
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @xin11112-->
<!--Designer: @zhangboren-->
<!--Tester: @TerryTsao-->
<!--Adviser: @zhang_yixin13-->

自定义组件的生命周期回调函数用于通知开发者该自定义组件的生命周期，这些回调函数是私有的，在运行时由开发框架在特定的时间进行调用，不能从应用程序中手动调用这些回调函数。该生命周期机制涵盖了自定义组件的初始化、出现、构建、回收与复用、激活与非激活、销毁等阶段，开发者可在相应阶段的回调中执行状态修改、数据埋点上报、监听注册等操作，还可借助CustomComponentLifecycle对生命周期状态进行监控与观察，适用于需要对组件生命周期进行精细化管理（如组件复用回收、状态埋点、激活控制等）的场景。

开发者指南见：[自定义组件生命周期（推荐）](../../../ui/state-management/arkts-custom-components-new-lifecycle.md)。

>**说明：**
>
> - 本模块首批接口从API version 23开始支持，后续版本的新增接口，采用上角标单独标记接口的起始版本。
>
> - 本模块接口仅可在Stage模型下使用。

## \@ComponentInit

ComponentInit: MethodDecorator

\@ComponentInit装饰的函数在自定义组件初始化即将完成时执行，先于\@ComponentAppear触发。开发者可以在此时注册生命周期监听器和修改状态变量。与\@ComponentAppear的区别在于：\@ComponentInit侧重于初始化阶段的准备操作（如注册监听），\@ComponentAppear侧重于组件即将展现前的状态变更，两者配合使用可分别承担初始化与显现前的职责。

**原子化服务API（仅ArkTS-Dyn）：** 从API version 23开始，该接口支持在原子化服务中使用。

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**示例：**

参见[生命周期使用示例](#生命周期使用示例)。

## \@ComponentAppear

ComponentAppear: MethodDecorator

与aboutToAppear相似，\@ComponentAppear装饰的函数在创建自定义组件的新实例后，在其build()函数执行前调用，不同的是，\@ComponentAppear装饰的函数仅在自定义组件处于[CustomComponentLifecycleState](#customcomponentlifecyclestate).INIT状态才会触发。允许在\@ComponentAppear装饰的函数中改变状态变量，更改将在后续执行build()函数中生效。

**原子化服务API（仅ArkTS-Dyn）：** 从API version 23开始，该接口支持在原子化服务中使用。

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**示例：**

参见[生命周期使用示例](#生命周期使用示例)。

## \@ComponentBuilt

ComponentBuilt: MethodDecorator

\@ComponentBuilt装饰的函数在自定义组件的build()函数首次执行后调用，即从CustomComponentLifecycleState.APPEARED到CustomComponentLifecycleState.BUILT的阶段触发。开发者可以在这个阶段实现埋点数据上报等不影响实际UI的功能。

**原子化服务API（仅ArkTS-Dyn）：** 从API version 23开始，该接口支持在原子化服务中使用。

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**示例：**

参见[生命周期使用示例](#生命周期使用示例)。

## \@ComponentDisappear

ComponentDisappear: MethodDecorator

+@ComponentDisappear装饰的函数在自定义组件销毁前执行，即向CustomComponentLifecycleState.DISAPPEARED状态转变时触发。不建议在此函数中改变状态变量，特别是\@Link变量的修改可能会导致应用程序行为不稳定。

**原子化服务API（仅ArkTS-Dyn）：** 从API version 23开始，该接口支持在原子化服务中使用。

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**示例：**

参见[生命周期使用示例](#生命周期使用示例)。

## \@ComponentReuse

ComponentReuse: MethodDecorator

当可复用的自定义组件从缓存中重新添加到节点树时调用\@ComponentReuse装饰的函数，即从CustomComponentLifecycleState.RECYCLED到CustomComponentLifecycleState.BUILT阶段触发，以接收组件的构造参数。最后，复用会递归遍历所有子组件，对每个完成复用的子组件，会调用子组件中\@ComponentReuse装饰的函数。

> **说明：**
>
> - 在状态管理V1的组件里，\@ComponentReuse装饰的函数允许有一个入参或者无参。入参params建议为Record\<string, Object \| undefined \| null\>类型。
>
> - 在状态管理V2的组件里，\@ComponentReuse装饰的函数没有入参。

**原子化服务API（仅ArkTS-Dyn）：** 从API version 23开始，该接口支持在原子化服务中使用。

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名  | 类型     | 必填   | 说明                                       |
| ---- | ------ | ---- | ------- |
| params   | Record\<string, Object \| undefined \| null\> | 否    | 组件复用时接收的构造参数，仅V1组件的复用回调支持该参数。不传此参数时，复用回调函数无入参。 |

**示例：**

参见[生命周期使用示例](#生命周期使用示例)。

## \@ComponentRecycle

ComponentRecycle: MethodDecorator

当组件被回收后，先执行应用程序中定义的资源释放等回收操作，完成回收后调用\@ComponentRecycle装饰的函数，即从CustomComponentLifecycleState.BUILT到CustomComponentLifecycleState.RECYCLED阶段触发。随后该组件被冻结，以避免该组件处于回收池时进行UI更新。最后，回收会递归遍历所有子组件，对每个完成回收的子组件调用子组件中\@ComponentRecycle装饰的函数。

**原子化服务API（仅ArkTS-Dyn）：** 从API version 23开始，该接口支持在原子化服务中使用。

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**示例：**

参见[生命周期使用示例](#生命周期使用示例)。

## \@ComponentActive

ArkTS-Dyn: ComponentActive: MethodDecorator

自定义组件由非激活状态转变为激活状态后，调用此装饰器装饰的函数。在组件回收复用场景下，当缓存的组件被重新复用（即从回收池重新添加到节点树）时，组件由非激活状态转为激活状态，触发此回调。

**起始版本：** 26.0.0

**原子化服务API（仅ArkTS-Dyn）：** 从API版本26.0.0开始，该接口支持在原子化服务中使用。

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## \@ComponentInactive

ArkTS-Dyn: ComponentInactive: MethodDecorator

自定义组件由激活状态转变为非激活状态后，调用此装饰器装饰的函数。在组件回收复用场景下，当组件被回收到复用池时，组件由激活状态转为非激活状态，触发此回调。

**起始版本：** 26.0.0

**原子化服务API（仅ArkTS-Dyn）：** 从API版本26.0.0开始，该接口支持在原子化服务中使用。

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**示例：**

参见[激活状态生命周期使用示例](#激活状态生命周期使用示例)。

## CustomComponentLifecycle

CustomComponentLifecycle用于监控自定义组件生命周期的变化，开发者可以通过[UIUtils.getLifecycle](../js-apis-stateManagement.md#getlifecycle23)获取CustomComponentLifecycle实例。

**ArkTS-Sta起始版本：** 24

### getCurrentState

getCurrentState(): CustomComponentLifecycleState

getCurrentState函数用于获取自定义组件当前的生命周期状态。调用此方法前，需先通过[UIUtils.getLifecycle](../js-apis-stateManagement.md#getlifecycle23)获取CustomComponentLifecycle实例。

**原子化服务API（仅ArkTS-Dyn）：** 从API version 23开始，该接口支持在原子化服务中使用。

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS-Sta起始版本：** 24

**返回值：**

| 类型                            | 说明       |
| -------- | -------- |
| [CustomComponentLifecycleState](#customcomponentlifecyclestate) | 自定义组件当前的生命周期状态。 |

**示例：**
```ts
import { UIUtils, ComponentBuilt } from '@kit.ArkUI';
import { hilog } from '@kit.PerformanceAnalysisKit';
@Entry
@Component
struct Index {
  @ComponentBuilt
  myBuilt() {
    // CustomComponentLifecycle.getCurrentState用于获得自定义组件当前的生命周期状态
    hilog.info(0x0000, 'testTag', 'Index Lifecycle is %{public}d', UIUtils.getLifecycle(this).getCurrentState());
  }
  build() {
    Column() {
      Text(`HelloWorld`)
    }
    .height('100%')
    .width('100%')
  }
}
```

### addObserver

addObserver(observer: CustomComponentLifecycleObserver): void

addObserver函数用于注册自定义组件生命周期监听器。调用此方法前，需先通过[UIUtils.getLifecycle](../js-apis-stateManagement.md#getlifecycle23)获取CustomComponentLifecycle实例。当自定义组件的生命周期发生变化时，会触发监听器中相应的生命周期回调函数。

调用addObserver注册监听器后，必须在组件销毁或不再需要监听时调用[removeObserver](#removeobserver)移除监听器，两者需成对使用。若未调用removeObserver移除监听器，可能导致监听器持续触发回调并引发内存泄漏。

**原子化服务API（仅ArkTS-Dyn）：** 从API version 23开始，该接口支持在原子化服务中使用。

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS-Sta起始版本：** 24

**参数：**

| 参数名  | 类型     | 必填   | 说明                                       |
| ---- | ------ | ---- | ------- |
| observer   | [CustomComponentLifecycleObserver](#customcomponentlifecycleobserver) | 是  | 自定义组件生命周期的监听器。 |

### removeObserver

removeObserver(observer: CustomComponentLifecycleObserver): void

removeObserver函数用于移除自定义组件生命周期监听器。调用此方法前，需先通过[UIUtils.getLifecycle](../js-apis-stateManagement.md#getlifecycle23)获取CustomComponentLifecycle实例。解除注册后，即使自定义组件的生命周期状态发生变化，也不会触发监听器中相应的生命周期回调函数。

**原子化服务API（仅ArkTS-Dyn）：** 从API version 23开始，该接口支持在原子化服务中使用。

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS-Sta起始版本：** 24

**参数：**

| 参数名  | 类型     | 必填   | 说明                                       |
| ---- | ------ | ---- | ------- |
| observer   | [CustomComponentLifecycleObserver](#customcomponentlifecycleobserver) | 是  | 自定义组件生命周期的监听器。 |

## CustomComponentLifecycleObserver

开发者注册自定义组件生命周期回调后，当该自定义组件的生命周期发生变化时，将触发监听器中相应的生命周期回调。

**ArkTS-Dyn起始版本：** 23

**ArkTS-Sta起始版本：** 24

### aboutToAppear


ArkTS-Sta: aboutToAppear(): void

ArkTS-Dyn: aboutToAppear?(): void

aboutToAppear函数在创建自定义组件的新实例后、其build()函数执行之前被调用。开发者可以在此阶段修改状态变量，更改将在后续执行build()函数中生效。其功能与[aboutToAppear](./ts-custom-component-lifecycle.md#abouttoappear)类似，但是在自定义组件状态机的约束下触发的。

**原子化服务API（仅ArkTS-Dyn）：** 从API version 23开始，该接口支持在原子化服务中使用。

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS-Dyn起始版本：** 23

**ArkTS-Sta起始版本：** 24

### onDidBuild


ArkTS-Sta: onDidBuild(): void

ArkTS-Dyn: onDidBuild?(): void

onDidBuild函数在自定义组件的build()函数执行后被调用，受自定义组件状态机约束，在被监听的自定义组件状态向CustomComponentLifecycleState.BUILT转变时触发回调。开发者可以在此阶段实现不影响实际UI的功能，例如事件数据上报。

**原子化服务API（仅ArkTS-Dyn）：** 从API version 23开始，该接口支持在原子化服务中使用。

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS-Dyn起始版本：** 23

**ArkTS-Sta起始版本：** 24

### aboutToDisappear


ArkTS-Sta: aboutToDisappear(): void

ArkTS-Dyn: aboutToDisappear?(): void

aboutToDisappear函数在自定义组件被销毁之前执行。不建议在aboutToDisappear函数中修改状态变量，特别是\@Link变量的修改可能会导致应用程序行为不稳定。其功能与[aboutToDisappear](./ts-custom-component-lifecycle.md#abouttodisappear)类似，不同的是，CustomComponentLifecycleObserver中的aboutToDisappear函数受状态机约束，只有被监听的自定义组件状态向CustomComponentLifecycleState.DISAPPEARED转变前触发回调。

**原子化服务API（仅ArkTS-Dyn）：** 从API version 23开始，该接口支持在原子化服务中使用。

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS-Dyn起始版本：** 23

**ArkTS-Sta起始版本：** 24

### aboutToReuse


ArkTS-Sta: aboutToReuse(params?: ReuseObject): void

ArkTS-Dyn: aboutToReuse?(params?: Record\<string, Object \| undefined \| null\>): void

当可复用的自定义组件从缓存中重新添加到节点树时调用aboutToReuse函数，受自定义组件状态机约束，即从CustomComponentLifecycleState.RECYCLED到CustomComponentLifecycleState.BUILT阶段触发回调。在状态管理V1的组件里，该函数允许有一个入参或者无参，当params存在时表示V1组件的复用回调；在状态管理V2的组件里，该函数没有入参。

> **说明：**
>
> - 在状态管理V1的组件里，aboutToReuse函数允许有一个入参或者无参。入参params建议为Record\<string, Object \| undefined \| null\>类型。
>
> - 在状态管理V2的组件里，aboutToReuse函数没有入参。

**原子化服务API（仅ArkTS-Dyn）：** 从API version 23开始，该接口支持在原子化服务中使用。

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS-Dyn起始版本：** 23

**ArkTS-Sta起始版本：** 24

**参数：**

| 参数名  | 类型     | 必填   | 说明                                       |
| ---- | ------ | ---- | ------- |
| params   | Record\<string, Object \| undefined \| null\> | 否    | 组件复用时接收的构造参数，仅V1组件的复用回调支持该参数。不传此参数时，复用回调函数无入参。 |

### aboutToRecycle

ArkTS-Sta: aboutToRecycle(): void

ArkTS-Dyn: aboutToRecycle?(): void

当组件被回收后，先执行应用程序中定义的资源释放等回收操作，完成回收后调用aboutToRecycle函数，受自定义组件状态机约束，即从CustomComponentLifecycleState.BUILT到CustomComponentLifecycleState.RECYCLED阶段触发回调。随后该组件被冻结，以避免该组件处于回收池时进行UI更新。最后，aboutToRecycle函数会递归遍历所有子组件，对每个完成回收的组件调用aboutToRecycle函数。

**原子化服务API（仅ArkTS-Dyn）：** 从API version 23开始，该接口支持在原子化服务中使用。

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS-Dyn起始版本：** 23

**ArkTS-Sta起始版本：** 24

**示例：**
```ts
import { ComponentInit, ComponentDisappear, UIUtils, CustomComponentLifecycleObserver, CustomComponentLifecycle } from '@kit.ArkUI';
import { hilog } from '@kit.PerformanceAnalysisKit';

export class Message {
  value: string | undefined;
  constructor(value: string) {
    this.value = value;
  }
}

@Entry
@Component
struct Index {
  @State isChildVisible: boolean = true;

  build() {
    Column() {
      Button('Hello')
        .fontSize(30)
        .fontWeight(FontWeight.Bold)
        .onClick(() => {
          this.isChildVisible = !this.isChildVisible;
        })
      if (this.isChildVisible) {
        // 如果只有一个复用的组件，可以不用设置reuseId。
        Child({ message: new Message('Child') })
          .reuseId('Child')
      }
    }
    .height('100%')
    .width('100%')
  }
}

@Reusable
@Component
struct Child {
  @State message: Message = new Message('AboutToReuse');
  @ComponentInit
  myInit(): void {
    registerObserver(UIUtils.getLifecycle(this));
  }
  @ComponentDisappear
  myDisappear(): void {
    unRegisterObserver(UIUtils.getLifecycle(this));
  }
  build() {
    Column() {
      Text(this.message.value)
        .fontSize(30)
    }
  }
}

export class MyObserver implements CustomComponentLifecycleObserver {
  // 重写CustomComponentLifecycleObserver中的生命周期事件。
  aboutToAppear() {
    hilog.info(0x0000, 'testTag', 'MyObserver aboutToAppear');
  }
  onDidBuild() {
    hilog.info(0x0000, 'testTag', 'MyObserver onDidBuild');
  }
  aboutToReuse(params?: Record<string, Object | undefined | null>) {
    // params存在时，为V1的复用；
    hilog.info(0x0000, 'testTag', 'MyObserver aboutToReuse');
  }
  aboutToRecycle() {
    hilog.info(0x0000, 'testTag', 'MyObserver aboutToRecycle');
  }
  aboutToDisappear() {
    hilog.info(0x0000, 'testTag', 'MyObserver aboutToDisappear');
  }
}

// 创建Observer对象
const observer = new MyObserver();

export function registerObserver(lifeCycle: CustomComponentLifecycle) {
  // 向lifeCycle注册监听
  lifeCycle.addObserver(observer);
}

export function unRegisterObserver(lifeCycle: CustomComponentLifecycle) {
  // 向lifeCycle取消注册监听
  lifeCycle.removeObserver(observer);
}
```

## CustomComponentLifecycleState

自定义组件当前的生命周期状态。

**原子化服务API（仅ArkTS-Dyn）：** 从API version 23开始，该接口支持在原子化服务中使用。

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS-Sta起始版本：** 24

| 名称 | 值 | 说明 |
| -- | -- | -- |
| INIT | 0 | 初始化状态。 |
| APPEARED | 1 | 准备展开状态。 |
| BUILT | 2 | 已展开状态。 |
| RECYCLED | 3 | 回收状态。 |
| DISAPPEARED | 4 | 删除状态。 |

**示例：**
```ts
import { CustomComponentLifecycleState, ComponentBuilt } from '@kit.ArkUI';
import { hilog } from '@kit.PerformanceAnalysisKit';

@Entry
@Component
struct Index {
  @ComponentBuilt
  myBuilt() {
    // CustomComponentLifecycleState.BUILT代表自定义组件为已展开状态
    hilog.info(0x0000, 'testTag', 'Index Lifecycle is %{public}d', CustomComponentLifecycleState.BUILT);
  }
  build() {
    Column() {
      Text(`HelloWorld`)
    }
    .height('100%')
    .width('100%')
  }
}
```

## 生命周期使用示例

本示例展示了生命周期回调函数的部分使用场景：

1. 创建自定义组件Child时触发\@ComponentInit、\@ComponentAppear；Child执行build()后，触发\@ComponentBuilt。

2. 更改this.switchChild为false，回收Child子组件，触发\@ComponentRecycle。

3. 更改this.switchChild为true，复用Child子组件，触发\@ComponentReuse。

4. 退出应用，在自定义组件Child销毁前，触发\@ComponentDisappear。

```ts
import { ComponentInit, ComponentAppear, ComponentBuilt, ComponentDisappear, ComponentReuse, ComponentRecycle } from '@kit.ArkUI';
import { hilog } from '@kit.PerformanceAnalysisKit';

export class Message {
  value: string | undefined;
  constructor(value: string) {
    this.value = value;
  }
}
@Entry
@Component
struct Index {
  @State switchChild: boolean = true;
  build() {
    Column() {
      Button('Hello')
        .fontSize(30)
        .fontWeight(FontWeight.Bold)
        .onClick(() => {
          this.switchChild = !this.switchChild;
        })
      if (this.switchChild) {
        // 如果只有一个复用的组件，可以不用设置reuseId。
        Child({ message: new Message('Child') })
          .reuseId('Child')
      }
    }
    .height('100%')
    .width('100%')
  }
}

@Reusable
@Component
struct Child {
  @State message: Message = new Message('Child');
  @State label: string = 'HelloWorld';
  @ComponentInit
  myInit() {
    // 自定义组件创建完毕后，触发myInit方法
    hilog.info(0x0000, 'testTag', 'Child myInit');
  }
  @ComponentAppear
  myAppear() {
    this.label = 'myAppear';
    hilog.info(0x0000, 'testTag', 'Child myAppear');
  }
  @ComponentBuilt
  myBuilt() {
    this.label = 'myBuilt';
    hilog.info(0x0000, 'testTag', 'Child myBuilt');
  }
  @ComponentRecycle
  myRecycle() {
    this.label = 'myRecycle';
    hilog.info(0x0000, 'testTag', 'Child myRecycle');
  }
  @ComponentDisappear
  myDisappear() {
    hilog.info(0x0000, 'testTag', 'Child myDisappear');
  }
  @ComponentReuse
  myReuse() {
    this.label = 'myReuse';
    hilog.info(0x0000, 'testTag', 'Child myReuse');
  }
  build() {
    Column() {
      Text(this.message.value)
        .fontSize(30)
    }
    .borderWidth(1)
    .height(100)
  }
}
```

## \@ComponentActive

激活生命周期装饰器。

被装饰的函数会在自定义组件从非激活态切换为激活态时触发。

自定义组件在创建后默认为激活态。

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS-Sta起始版本：** 26.0.0

**示例：**

参考[激活状态生命周期使用示例](#激活状态生命周期使用示例)。

## \@ComponentInactive

非激活生命周期装饰器。

被装饰的函数会在自定义组件从激活态切换为非激活态时触发。

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS-Sta起始版本：** 26.0.0

**示例：**

参考[激活状态生命周期使用示例](#激活状态生命周期使用示例)。

## 激活状态生命周期使用示例

以自定义组件复用场景为例，展示激活态与非激活态的状态切换与回调触发。

**ArkTS-Dyn示例：**

```ts
import { ComponentActive, ComponentInactive } from '@kit.ArkUI';

@Entry
@Component
struct Index {
  @State changeChild: boolean = false;

  build() {
    Column() {
      Button('change').onClick(() => {
        // 切换Child组件的显示状态，触发组件的回收或复用
        this.changeChild = !this.changeChild;
      })
      if (this.changeChild) {
        Child()
      }
    }
    .width('100%')
  }
}

@Reusable
@Component
struct Child {
  @ComponentActive
  myActive() {
    // 组件从非激活状态变为激活状态时触发
    console.info(`Child myActive`);
  }

  @ComponentInactive
  myInactive() {
    // 组件从激活状态变为非激活状态时触发
    console.info(`Child myInactive`);
  }

  build() {
    Text('Child')
  }
}
```

**ArkTS-Sta示例：**

```ts
'use static'
 
import { Entry, Text, Column, Component, Button, ClickEvent, Reusable, State, ComponentActive, ComponentInactive } from '@kit.ArkUI';
import hilog from '@ohos.hilog';
 
@Entry
@Component
struct Reuse {
  @State flag: boolean = true;

  build() {
    Column(undefined) {
      Button('switch')
        .onClick(() => {
          this.flag = !this.flag; // 切换回收、复用
        })
      if (this.flag) {
        FreezeChild()
      }
    }
  }
}
 
@Reusable
@Component
struct FreezeChild {
  @State message: string = '';
  @ComponentActive
  myActive() {
    // 当组件从非激活态切换为激活态时触发
    this.message += '-A';
    console.info(`FreezeChild myActive`);
  }
  @ComponentInactive
  myInActive() {
    // 当组件从激活态切换为非激活态时触发
    this.message += '-I';
    console.info(`FreezeChild myInActive`);
  }

  build() {
    Text(`message ${this.message}`)
      .fontSize(50)
  }
}
```
