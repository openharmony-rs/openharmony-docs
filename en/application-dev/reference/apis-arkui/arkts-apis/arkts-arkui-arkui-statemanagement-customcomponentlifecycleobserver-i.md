# CustomComponentLifecycleObserver

```TypeScript
export declare interface CustomComponentLifecycleObserver
```

After developers register a custom component lifecycle callback, when the lifecycle of the custom component changes, the corresponding lifecycle callback in the listener is triggered. The difference from the lifecycle decorators is that the lifecycle decorators respond to lifecycle events by the component itself, while **CustomComponentLifecycleObserver** observes component lifecycle events from the outside. If only the component itself needs to respond to lifecycle changes, use the lifecycle decorators. If you need to centrally monitor the lifecycles of multiple components, use **CustomComponentLifecycleObserver**.

**Since:** 23

<!--Device-unnamed-export declare interface CustomComponentLifecycleObserver--><!--Device-unnamed-export declare interface CustomComponentLifecycleObserver-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { AppStorageV2, PersistenceV2, Type, UIUtils, ConnectOptions, Binding, MutableBinding, CustomComponentLifecycle, CustomComponentLifecycleObserver, CustomComponentLifecycleState, ComponentInit, ComponentAppear, ComponentBuilt, ComponentReuse, ComponentActive, ComponentInactive, ComponentRecycle, ComponentDisappear, CollectionType, ConnectOptionsCollections, CustomComponentContext, IReusePool, IReusableInfo, StorageDefaultCreator, TypeConstructorWithArgs, PersistenceErrorCallback, TypeConstructor, TypeDecorator, MonitorCallback, MonitorOptions, GetterCallback, SetterCallback, ObservedResult, DecoratorInfo, ElementInfo } from '@kit.ArkUI';
```

## aboutToAppear

```TypeScript
aboutToAppear?(): void
```

Called after a new instance of a custom component is created and before its **build()** function is executed. Developers can modify state variables in this phase, and the changes will take effect in the subsequent execution of the **build()** function. Its function is similar to [aboutToAppear](../arkts-components/arkts-arkui-common-comp-basecustomcomponent-c.md#abouttoappear). It is subject to the custom component state machine and triggers the callback when the monitored custom component transitions to **[CustomComponentLifecycleState](arkts-arkui-arkui-statemanagement-customcomponentlifecyclestate-e.md).APPEARED**.

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 23.

<!--Device-CustomComponentLifecycleObserver-aboutToAppear?(): void--><!--Device-CustomComponentLifecycleObserver-aboutToAppear?(): void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## aboutToDisappear

```TypeScript
aboutToDisappear?(): void
```

Executed before a custom component is destroyed. It is not recommended to modify state variables in the **aboutToDisappear** function. In particular, modifying **\@Link** variables may cause unstable app behavior. Its function is similar to [aboutToDisappear](../arkts-components/arkts-arkui-common-comp-basecustomcomponent-c.md#abouttodisappear). The difference is that the **aboutToDisappear** function in **CustomComponentLifecycleObserver** is subject to the state machine and triggers the callback only before the state of the monitored custom component transitions to **[CustomComponentLifecycleState](arkts-arkui-arkui-statemanagement-customcomponentlifecyclestate-e.md).DISAPPEARED**.

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 23.

<!--Device-CustomComponentLifecycleObserver-aboutToDisappear?(): void--><!--Device-CustomComponentLifecycleObserver-aboutToDisappear?(): void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## aboutToRecycle

```TypeScript
aboutToRecycle?(): void
```

After a component is recycled, the recycling operations such as resource release defined in the app are performed first. After the recycling is complete, the **aboutToRecycle** function is called. It is subject to the custom component state machine, that is, it triggers the callback in the stage from **[CustomComponentLifecycleState](arkts-arkui-arkui-statemanagement-customcomponentlifecyclestate-e.md).BUILT** to **[CustomComponentLifecycleState](arkts-arkui-arkui-statemanagement-customcomponentlifecyclestate-e.md).RECYCLED**. Then the component is frozen to avoid UI updates while the component is in the reuse pool. Finally, recycling recursively traverses all child components, and for each child component that completes recycling, the **aboutToRecycle** function registered in the child component is called.

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 23.

<!--Device-CustomComponentLifecycleObserver-aboutToRecycle?(): void--><!--Device-CustomComponentLifecycleObserver-aboutToRecycle?(): void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Examples**

```TypeScript
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
  // Override the lifecycle events in CustomComponentLifecycleObserver.
  aboutToAppear() {
    hilog.info(0x0000, 'testTag', 'MyObserver aboutToAppear');
  }
  onDidBuild() {
    hilog.info(0x0000, 'testTag', 'MyObserver onDidBuild');
  }
  aboutToReuse(params?: Record<string, Object | undefined | null>) {
    // When params exists, it is V1 reuse.
    hilog.info(0x0000, 'testTag', 'MyObserver aboutToReuse');
  }
  aboutToRecycle() {
    hilog.info(0x0000, 'testTag', 'MyObserver aboutToRecycle');
  }
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

## aboutToReuse

```TypeScript
aboutToReuse?(params?: Record<string, Object | undefined | null>): void
```

Called when a reusable custom component is re-added to the node tree from the cache. It is subject to the custom component state machine, that is, it triggers the callback in the stage from **[CustomComponentLifecycleState](arkts-arkui-arkui-statemanagement-customcomponentlifecyclestate-e.md).RECYCLED** to **[CustomComponentLifecycleState](arkts-arkui-arkui-statemanagement-customcomponentlifecyclestate-e.md).BUILT**. Finally, reuse recursively traverses all child components, and for each child component that completes reuse, the **aboutToReuse** function registered in the child component is called. In a state management V1 component, this function can have one input parameter or no parameter. When **params** exists, it indicates the reuse callback of a V1 component. In a state management V2 component, this function has no input parameter.

> **NOTE:** 
> 
> - In a state management V1 component, the **aboutToReuse** function can have one input parameter or no parameter. The input parameter **params** is recommended to be of the Record\&lt;string, Object \| undefined \| null\&gt; type.
> 
> - In a state management V2 component, the **aboutToReuse** function has no input parameter.

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 23.

<!--Device-CustomComponentLifecycleObserver-aboutToReuse?(params?: Record<string, Object | undefined | null>): void--><!--Device-CustomComponentLifecycleObserver-aboutToReuse?(params?: Record<string, Object | undefined | null>): void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| params | Record&lt;string, Object &#124; undefined &#124; null&gt; | No | Construction parameters received when the component is reused. Only the reuse callback of a V1 component supports this parameter. If this parameter is not passed, the reuse callback function has no input parameter. |

## onDidBuild

```TypeScript
onDidBuild?(): void
```

Called after the **build()** function of a custom component is executed. It is subject to the custom component state machine and triggers the callback when the state of the monitored custom component transitions to **[CustomComponentLifecycleState](arkts-arkui-arkui-statemanagement-customcomponentlifecyclestate-e.md).BUILT**. Developers can implement functions that do not affect the actual UI in this phase, such as event data reporting.

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 23.

<!--Device-CustomComponentLifecycleObserver-onDidBuild?(): void--><!--Device-CustomComponentLifecycleObserver-onDidBuild?(): void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
