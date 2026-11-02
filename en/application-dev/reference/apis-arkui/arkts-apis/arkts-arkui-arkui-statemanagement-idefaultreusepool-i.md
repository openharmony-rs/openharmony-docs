# IDefaultReusePool

```TypeScript
export declare interface IDefaultReusePool
```

The **IDefaultReusePool** API provides the features related to the default reuse pool of a custom component.

**Since:** 26.1.0

<!--Device-unnamed-export declare interface IDefaultReusePool--><!--Device-unnamed-export declare interface IDefaultReusePool-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { AppStorageV2, PersistenceV2, Type, UIUtils, ConnectOptions, Binding, MutableBinding, CustomComponentLifecycle, CustomComponentLifecycleObserver, CustomComponentLifecycleState, ComponentInit, ComponentAppear, ComponentBuilt, ComponentReuse, ComponentActive, ComponentInactive, ComponentRecycle, ComponentDisappear, CollectionType, ConnectOptionsCollections, CustomComponentContext, IReusePool, IDefaultReusePool, IReusableInfo, StorageDefaultCreator, TypeConstructorWithArgs, PersistenceErrorCallback, TypeConstructor, TypeDecorator, MonitorCallback, MonitorOptions, GetterCallback, SetterCallback, ObservedResult, DecoratorInfo, ElementInfo } from '@kit.ArkUI';
```

## clearCache

```TypeScript
clearCache(reuseId?: string): void
```

Clears the nodes in the reuse pool of the custom component.

If **reuseId** is specified, only the nodes of the reusable custom component with the specified **reuseId** are cleared. If it is not specified, all nodes in the reuse pool are cleared.

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.1.0.

<!--Device-IDefaultReusePool-clearCache(reuseId?: string): void--><!--Device-IDefaultReusePool-clearCache(reuseId?: string): void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| reuseId | string | No | Reuse ID of the reusable custom component in the reuse pool to be cleared. |
