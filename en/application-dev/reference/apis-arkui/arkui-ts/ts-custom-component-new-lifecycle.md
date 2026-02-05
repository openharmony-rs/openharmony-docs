# Lifecycle of a Custom Component (Recommended)
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @seaside_wu1; @xin11112-->
<!--Designer: @chenbenzhi-->
<!--Tester: @TerryTsao-->
<!--Adviser: @zhang_yixin13-->

The lifecycle callbacks of a custom component are used to notify users of the lifecycle of the component. These callbacks are private and are invoked by the development framework at a specified time at runtime. They cannot be manually invoked from applications.

>**NOTE**
>
>- The initial APIs of this module are supported since API version 23. Newly added APIs will be marked with a superscript to indicate their earliest API version.

## \@ComponentInit

ComponentInit: MethodDecorator

Decorates a function that is called when the initialization of a custom component is about to complete. You can register a listener at this time.

> **NOTE**
>
> You cannot change the status variable in this callback. Otherwise, the application will break down.

**Atomic service API**: This API can be used in atomic services since API version 23.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Model restriction**: This API can be used only in the stage model.

**Example**

For details, see [Lifecycle Example](#lifecycle-example).

## \@ComponentAppear

ComponentAppear: MethodDecorator

Decorates a function that is called after a new instance of the custom component is created and before the **build()** function is executed. This callback is similar to **aboutToAppear**. The difference is that the **\@ComponentAppear** callback is triggered only when the custom component is in the **[CustomComponentLifecycleState](#customcomponentlifecyclestate).INIT** state. The state variable can be changed in **\@ComponentAppear**. The change will take effect in the subsequent **build()** function execution.

**Atomic service API**: This API can be used in atomic services since API version 23.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Model restriction**: This API can be used only in the stage model.

**Example**

For details, see [Lifecycle Example](#lifecycle-example).

## \@ComponentBuilt

ComponentBuilt: MethodDecorator

Decorates a function that is called after the **build()** function of the custom component is executed for the first time, that is, when the component status changes from from **CustomComponentLifecycleState.APPEARED** to **CustomComponentLifecycleState.BUILT**. You can use this callback for actions that do not affect the UI, such as tracking data reporting.

**Atomic service API**: This API can be used in atomic services since API version 23.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Model restriction**: This API can be used only in the stage model.

**Example**

For details, see [Lifecycle Example](#lifecycle-example).

## \@ComponentDisappear

ComponentDisappear: MethodDecorator

Decorates a function that is called when the custom component is destructed. You are advised not to change state variables in this function. Modifying the **\@Link** decorated variable may lead to unstable application behavior.

**Atomic service API**: This API can be used in atomic services since API version 23.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Model restriction**: This API can be used only in the stage model.

**Example**

For details, see [Lifecycle Example](#lifecycle-example).

## \@ComponentAttach

ComponentAttach: MethodDecorator

Decorates a function that is called after the custom component is mounted to the main tree, that is, when the component status changes from **CustomComponentLifecycleState.MOUNTED** to **CustomComponentLifecycleState.BUILT**. You can use this callback for actions that do not affect the UI, such as event data reporting.

**Atomic service API**: This API can be used in atomic services since API version 23.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Model restriction**: This API can be used only in the stage model.

**Example**

For details, see [Lifecycle Example](#lifecycle-example).

## \@ComponentDetach

ComponentDetach: MethodDecorator

Decorates a function that is called before the status of the custom component changes back from **CustomComponentLifecycleState.MOUNTED** to **CustomComponentLifecycleState.BUILT**. You can use this callback for actions that do not affect the UI, such as modifying non-status variables.

**Atomic service API**: This API can be used in atomic services since API version 23.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Model restriction**: This API can be used only in the stage model.

**Example**

For details, see [Lifecycle Example](#lifecycle-example).

## \@ComponentReuse

ComponentReuse: MethodDecorator

Decorates a function that is called when a reusable custom component is re-added to the node tree from the cache, that is, when the component status changes from the **CustomComponentLifecycleState.RECYCLED** to **CustomComponentLifecycleState.BUILT** phase, to receive the constructor parameters. At last, the function decorated by **\@ComponentReuse** recursively traverses all child components, and the **\@ComponentReuse** decorated function in each reused child component will be called.

> **NOTE**
>
> -  The value of **param** is not **undefined** in the callback of the reused state management V1 component.
>
> -  The value of **param** is **undefined** in the callback of the reused state management V2 component.

**Atomic service API**: This API can be used in atomic services since API version 23.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Model restriction**: This API can be used only in the stage model.

**Parameters**

| Parameter | Type    | Mandatory  | Description                                      |
| ---- | ------ | ---- | ------- |
| params   | Record\<string, Object \| undefined \| null> | No   | The value of **param** is not **undefined** in the reuse callback of the V1 component. The value of **param** is **undefined** in the reuse callback of the V2 component.|

**Example**

For details, see [Lifecycle Example](#lifecycle-example).

## \@ComponentRecycle

ComponentRecycle: MethodDecorator

Decorates a function that is called when the necessary recycling operations defined in the application are performed. That is, this function is triggeredd when the component status changes from **CustomComponentLifecycleState.BUILT** to **CustomComponentLifecycleState.RECYCLED**. At last, the function decorated by **\@ComponentRecycle** recursively traverses all child components, and the **\@ComponentRecycle** decorated function in each recycled child component will be called.

**Atomic service API**: This API can be used in atomic services since API version 23.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Model restriction**: This API can be used only in the stage model.

**Example**

For details, see [Lifecycle Example](#lifecycle-example).

## CustomComponentLifecycle

**CustomComponentLifecycle** monitors the lifecycle changes of a custom component.

### getCurrentState

getCurrentState(): CustomComponentLifecycleState

The **getCurrentState** function obtains the current lifecycle status of a custom component.

**Atomic service API**: This API can be used in atomic services since API version 23.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Model restriction**: This API can be used only in the stage model.

**Return value**

| Type                           | Description      |
| -------- | -------- |
| [CustomComponentLifecycleState](#customcomponentlifecyclestate) | Current lifecycle status of a custom component.|

**Example**
```ts
import { UIUtils, ComponentBuilt } from '@kit.ArkUI';
import { hilog } from '@kit.PerformanceAnalysisKit';
@Entry
@Component
struct Index {
  @ComponentBuilt
  myBuilt() {
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

Registers a listener for the lifecycle of a custom component. Lifecycle changes will trigger the lifecycle callback in the listener.

**Atomic service API**: This API can be used in atomic services since API version 23.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Model restriction**: This API can be used only in the stage model.

**Parameters**

| Parameter | Type    | Mandatory  | Description                                      |
| ---- | ------ | ---- | ------- |
| observer   | [CustomComponentLifecycleObserver](#customcomponentlifecycleobserver) | Yes | Listener for a custom component.|

### removeObserver

removeObserver(observer: CustomComponentLifecycleObserver): void

Removes a listener for the lifecycle of a custom component. After the listener is removed, the lifecycle callback in the listener is not triggered even if the component status changes.

**Atomic service API**: This API can be used in atomic services since API version 23.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Model restriction**: This API can be used only in the stage model.

**Parameters**

| Parameter | Type    | Mandatory  | Description                                      |
| ---- | ------ | ---- | ------- |
| observer   | CustomComponentLifecycleObserver | Yes | Listener for a custom component.|

## CustomComponentLifecycleObserver

Observes lifecycle status changes of a custom component, and triggers the lifecycle callback in the listener when detecting lifecycle status changes.

### aboutToAppear

aboutToAppear?(): void

Called after a new instance of the custom component is created and before its **build()** function is executed. You can modify the status variables in this phase. Its function is similar to that of [aboutToAppear](./ts-custom-component-lifecycle.md#abouttoappear), but it is triggered under the constraints of the custom component state machine.

**Atomic service API**: This API can be used in atomic services since API version 23.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Model restriction**: This API can be used only in the stage model.

### onDidBuild

onDidBuild?(): void

Called after a new instance of the custom component is created and its **build()** function is executed. You can use this callback for actions that do not affect the UI, such as event data reporting.

**Atomic service API**: This API can be used in atomic services since API version 23.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Model restriction**: This API can be used only in the stage model.

### aboutToDisappear

aboutToDisappear?(): void

Called before the custom component is destroyed. You are advised not to change state variables in the **aboutToDisappear** function. Modifying the **\@Link** decorated variable may lead to unstable application behavior. This function is similar to the earlier **aboutToDisappear** function, which is triggered under the constraints of the custom component state machine. Therefore, this function is added for compatibility.

**Atomic service API**: This API can be used in atomic services since API version 23.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Model restriction**: This API can be used only in the stage model.

### aboutToAttach

aboutToAttach?(): void

Called when the custom component is attached to the main tree. You can use this callback for actions that do not affect the UI, such as event data reporting.

**Atomic service API**: This API can be used in atomic services since API version 23.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Model restriction**: This API can be used only in the stage model.

### aboutToDetach

aboutToDetach?(): void

Called when a custom component is detached from the main tree. You can use this callback for actions that do not affect the UI, such as event data reporting.

**Atomic service API**: This API can be used in atomic services since API version 23.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Model restriction**: This API can be used only in the stage model.

### aboutToReuse

aboutToReuse?(params?: Record<string, Object | undefined | null>): void

Called when a reusable custom component is re-added to the node tree from the cache to receive the component constructors. The value of **param** is not **undefined** in the reuse callback of the V1 component. The value of **param** is **undefined** in the reuse callback of the V2 component.

**Atomic service API**: This API can be used in atomic services since API version 23.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Model restriction**: This API can be used only in the stage model.

**Parameters**

| Parameter | Type    | Mandatory  | Description                                      |
| ---- | ------ | ---- | ------- |
| params   | Record\<string, Object \| undefined \| null> | No   | The value of **param** is not **undefined** in the reuse callback of the V1 component. The value of **param** is **undefined** in the reuse callback of the V2 component.|

### aboutToRecycle

aboutToRecycle?(): void

Called after necessary component recycling operations defined in the application are performed. Then, the component is frozen to prevent UI updates when the component is in the recycling pool. At last, the **aboutToRecycle** function recursively traverses all child components, and the **aboutToRecycle** function in each recycled child component will be called.

**Atomic service API**: This API can be used in atomic services since API version 23.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Model restriction**: This API can be used only in the stage model.

**Example**
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
  @State switch: boolean = true;

  build() {
    Column() {
      Button('Hello')
        .fontSize(30)
        .fontWeight(FontWeight.Bold)
        .onClick(() => {
          this.switch = !this.switch;
        })
      if (this.switch) {
        // If only one reusable component is used, reuseId is optional.
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
  @State label: string = 'HelloWorld';
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
  // Override the lifecycle events in CustomComponentLifecycleObserver. CustomComponentLifecycleObserver cannot listen to the aboutToInit event of the parent component.
  aboutToAppear() {
    hilog.info(0x0000, 'testTag', 'MyObserver aboutToAppear');
  }
  onDidBuild() {
    hilog.info(0x0000, 'testTag', 'MyObserver onDidBuild');
  }
  aboutToAttach() {
    hilog.info(0x0000, 'testTag', 'MyObserver aboutToAttach');
  }
  aboutToDetach() {
    hilog.info(0x0000, 'testTag', 'MyObserver aboutToDetach');
  }
  aboutToReuse(param?: ESObject) {
    // The value of param is not undefined in the reuse callback of the V1 component and is undefined in the reuse callback of the V2 component.
    hilog.info(0x0000, 'testTag', 'MyObserver aboutToReuse');
  }
  aboutToRecycle() {
    hilog.info(0x0000, 'testTag', 'MyObserver aboutToRecycle');
  }
  // Unregister the listener in the aboutToDelete function of the parent component. As a result, the aboutToDisappear event of the parent component cannot be listened to.
  aboutToDisappear() {
    hilog.info(0x0000, 'testTag', 'MyObserver aboutToDisappear');
  }
}

// Create the Observer object.
const observer = new MyObserver();

export function registerObserver(lifeCycle: CustomComponentLifecycle) {
  // Register the listener with lifeCycle.
  lifeCycle.addObserver(observer);
}

export function unRegisterObserver(lifeCycle: CustomComponentLifecycle) {
  // Unregister the listener from lifeCycle.
  lifeCycle.removeObserver(observer);
}
```

## CustomComponentLifecycleState

Current lifecycle status of a custom component.

**Atomic service API**: This API can be used in atomic services since API version 23.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Model restriction**: This API can be used only in the stage model.

| Name| Value| Description|
| -- | -- | -- |
| INIT | 0 | Initial.|
| APPEARED | 1 | To build.|
| BUILT | 2 | Built.|
| MOUNTED | 3 | Mounted.|
| RECYCLED | 4 | Recycled.|
| DISAPPEARED | 5 | Deleted.|

**Example**
```ts
import { CustomComponentLifecycleState, ComponentBuilt } from '@kit.ArkUI';
import { hilog } from '@kit.PerformanceAnalysisKit';

@Entry
@Component
struct Index {
  @ComponentBuilt
  myBuilt() {
    hilog.info(0x0000, 'testTag', 'Index Lifecycle is %{public}d', CustomComponentLifecycleState.APPEARED);
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

## Lifecycle Example

This example demonstrates some use cases of the lifecycle callback functions.

1. Creating the custom component **Child** triggers the **\@ComponentInit** and **\@ComponentAppear** callbacks. After **build()** is executed for the **Child** component, the **\@ComponentBuilt** and **\@ComponentAttach** callbacks are triggered.

2. Changing **this.switch** to **false** and recycling the **Child** component trigger **\@ComponentDetach** and **\@ComponentRecycle**. Changing **this.switch** to **true** and reusing the **Child** component trigger **\@ComponentReuse** and **\@ComponentAttach**.

3. The **\@ComponentDisappear** callback is triggered before you exit the application and the **Child** component is destroyed.

```ts
import { ComponentInit, ComponentAppear, ComponentBuilt, ComponentAttach, ComponentDetach, ComponentDisappear, ComponentReuse, ComponentRecycle } from '@kit.ArkUI';
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
  @State switch: boolean = true;
  build() {
    Column() {
      Button('Hello')
        .fontSize(30)
        .fontWeight(FontWeight.Bold)
        .onClick(() => {
          this.switch = !this.switch;
        })
      if (this.switch) {
        // If only one reusable component is used, reuseId is optional.
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
  @State switch: boolean = true;
  @ComponentInit
  myInit() {
    hilog.info(0x0000, 'testTag', 'Child myInit');
  }
  @ComponentAppear
  myAppear() {
    this.label = 'myAppear'
    hilog.info(0x0000, 'testTag', 'Child myAppear');
  }
  @ComponentBuilt
  myBuilt() {
    this.label = 'myBuilt'
    hilog.info(0x0000, 'testTag', 'Child myBuilt');
  }
  @ComponentAttach
  myAttach() {
    this.label = 'myAttach'
    hilog.info(0x0000, 'testTag', 'Child myAttach');
  }
  @ComponentDetach
  myDetach() {
    this.label = 'myDetach'
    hilog.info(0x0000, 'testTag', 'Child myDetach');
  }
  @ComponentRecycle
  myRecycle() {
    this.label = 'myRecycle'
    hilog.info(0x0000, 'testTag', 'Child myRecycle');
  }
  @ComponentDisappear
  myDisappear() {
    this.label = 'myDisappear'
    hilog.info(0x0000, 'testTag', 'Child myDisappear');
  }
  @ComponentReuse
  myReuse() {
    this.label = 'myReuse'
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
