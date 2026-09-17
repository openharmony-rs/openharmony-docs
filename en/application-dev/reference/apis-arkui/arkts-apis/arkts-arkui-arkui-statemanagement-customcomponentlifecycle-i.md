# CustomComponentLifecycle

**CustomComponentLifecycle** monitors the lifecycle changes of a custom component.

**Since:** 23

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { AppStorageV2, PersistenceV2, Type, UIUtils, ConnectOptions, Binding, MutableBinding, CustomComponentLifecycle, CustomComponentLifecycleObserver, CustomComponentLifecycleState, ComponentInit, ComponentAppear, ComponentBuilt, ComponentReuse, ComponentActive, ComponentInactive, ComponentRecycle, ComponentDisappear, CollectionType, ConnectOptionsCollections, CustomComponentContext, IReusePool, IReusableInfo, StorageDefaultCreator, TypeConstructorWithArgs, PersistenceErrorCallback, TypeConstructor, TypeDecorator, MonitorCallback, MonitorOptions, GetterCallback, SetterCallback, ObservedResult, DecoratorInfo, ElementInfo } from '@kit.ArkUI';
```

## addObserver

```TypeScript
addObserver(observer: CustomComponentLifecycleObserver): void
```

Registers a listener for the lifecycle of a custom component. Lifecycle changes will trigger the lifecycle callback in the listener.

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 23.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| observer | [CustomComponentLifecycleObserver](arkts-arkui-arkui-statemanagement-customcomponentlifecycleobserver-i.md) | Yes | Listener for a custom component. |

## getCurrentState

```TypeScript
getCurrentState(): CustomComponentLifecycleState
```

getCurrentState(): CustomComponentLifecycleState

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 23.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Return value:**

| Type | Description |
| --- | --- |
| [CustomComponentLifecycleState](arkts-arkui-arkui-statemanagement-customcomponentlifecyclestate-e.md) | Current lifecycle status of a custom component. |

**Examples**

```TypeScript
import { UIUtils, ComponentBuilt } from '@kit.ArkUI';
import { hilog } from '@kit.PerformanceAnalysisKit';
@Entry
@Component
struct Index {
  @ComponentBuilt
  myBuilt() {
    // CustomComponentLifecycle.getCurrentState is used to obtain the current lifecycle state of a custom component.
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

## removeObserver

```TypeScript
removeObserver(observer: CustomComponentLifecycleObserver): void
```

Removes a listener for the lifecycle of a custom component. After the listener is removed, the lifecycle callback in the listener is not triggered even if the component status changes.

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 23.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| observer | [CustomComponentLifecycleObserver](arkts-arkui-arkui-statemanagement-customcomponentlifecycleobserver-i.md) | Yes | Listener for a custom component. |
