# MonitorOptions

```TypeScript
export interface MonitorOptions
```

Defines the optional parameters for [addMonitor](arkts-arkui-arkui-statemanagement-uiutils-c.md#addmonitor), which are used to configure the callback type and whether to enable the wildcard capability.

**Since:** 20

<!--Device-unnamed-export interface MonitorOptions--><!--Device-unnamed-export interface MonitorOptions-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { AppStorageV2, PersistenceV2, Type, UIUtils, ConnectOptions, Binding, MutableBinding, CustomComponentLifecycle, CustomComponentLifecycleObserver, CustomComponentLifecycleState, ComponentInit, ComponentAppear, ComponentBuilt, ComponentReuse, ComponentActive, ComponentInactive, ComponentRecycle, ComponentDisappear, CollectionType, ConnectOptionsCollections, CustomComponentContext, IReusePool, IReusableInfo, StorageDefaultCreator, TypeConstructorWithArgs, PersistenceErrorCallback, TypeConstructor, TypeDecorator, MonitorCallback, MonitorOptions, GetterCallback, SetterCallback, ObservedResult, DecoratorInfo, ElementInfo } from '@kit.ArkUI';
```

## enableWildcard

```TypeScript
enableWildcard?: boolean
```

Whether to enable the wildcard capability for the current **addMonitor**. The value **true** indicates to enable, and **false** indicates the opposite. The default value is **false**, which means to disable the capability. When the wildcard capability is disabled but the path contains a wildcard, the path is considered invalid.

**Type:** boolean

**Default:** false

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-MonitorOptions-enableWildcard?: boolean--><!--Device-MonitorOptions-enableWildcard?: boolean-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## isSynchronous

```TypeScript
isSynchronous?: boolean
```

Whether the current callback is a synchronous callback. The value **true** indicates a synchronous callback. The default value is **false**, which indicates an asynchronous callback.

**Type:** boolean

**Default:** false

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

<!--Device-MonitorOptions-isSynchronous?: boolean--><!--Device-MonitorOptions-isSynchronous?: boolean-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
