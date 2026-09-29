# ConnectOptionsCollections

```TypeScript
export class ConnectOptionsCollections<T extends CollectionType<S>, S extends object> extends ConnectOptions<T>
```

Defines the parameter type for the globalConnect API. **ConnectOptionsCollections** is inherited from [ConnectOptions\&lt;T\&gt;](arkts-arkui-arkui-statemanagement-connectoptions-c.md). You can use the **ConnectOptionsCollections** input parameter to persist container data (such as **Array\&lt;S&gt;**).

The following shows the examples of **StorageDefaultCreator\&lt;T&gt;** and **StorageDefaultCreator\&lt;S&gt;**:

**Inheritance/Implementation:** ConnectOptionsCollections extends ConnectOptions<T>

**Since:** 23

<!--Device-unnamed-export class ConnectOptionsCollections<T extends CollectionType<S>, S extends object> extends ConnectOptions<T>--><!--Device-unnamed-export class ConnectOptionsCollections<T extends CollectionType<S>, S extends object> extends ConnectOptions<T>-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { AppStorageV2, PersistenceV2, Type, UIUtils, ConnectOptions, Binding, MutableBinding, CustomComponentLifecycle, CustomComponentLifecycleObserver, CustomComponentLifecycleState, ComponentInit, ComponentAppear, ComponentBuilt, ComponentReuse, ComponentActive, ComponentInactive, ComponentRecycle, ComponentDisappear, CollectionType, ConnectOptionsCollections, CustomComponentContext, IReusePool, IReusableInfo, StorageDefaultCreator, TypeConstructorWithArgs, PersistenceErrorCallback, TypeConstructor, TypeDecorator, MonitorCallback, MonitorOptions, GetterCallback, SetterCallback, ObservedResult, DecoratorInfo, ElementInfo } from '@kit.ArkUI';
```

## defaultCreator

```TypeScript
defaultCreator?: StorageDefaultCreator<T>
```

Persists container data. **defaultSubCreator** should be provided together with **defaultCreator**; otherwise, the container data cannot be persisted. The collection item type **S** must be the same as the return type of **defaultSubCreator**.

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 23.

<!--Device-ConnectOptionsCollections-defaultCreator?: StorageDefaultCreator<T>--><!--Device-ConnectOptionsCollections-defaultCreator?: StorageDefaultCreator<T>-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## defaultSubCreator

```TypeScript
defaultSubCreator?: StorageDefaultCreator<S>
```

Default constructor function of the collection item, which is used to persist container data. When this parameter is used, **defaultCreator** must also be provided; otherwise, persistence will fail. When container data is persisted, if this parameter is not passed in, or if **defaultSubCreator** returns **undefined** or **null**, the persistence operation will fail. When a collection of user-defined classes (such as **Array&lt;ClassA&gt;**) is persisted, the generic type **T** in **defaultCreator** is **Array&lt;ClassA&gt;**, and **S** in **defaultSubCreator** is **ClassA**.

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 23.

<!--Device-ConnectOptionsCollections-defaultSubCreator?: StorageDefaultCreator<S>--><!--Device-ConnectOptionsCollections-defaultSubCreator?: StorageDefaultCreator<S>-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
