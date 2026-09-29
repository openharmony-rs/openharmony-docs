# MutableBinding

```TypeScript
export declare class MutableBinding<T>
```

Represents a generic class for mutable data binding, which allows the read and write operations on the bound value and provides complete **get** and **set** accessors.

**Since:** 20

<!--Device-unnamed-export declare class MutableBinding<T>--><!--Device-unnamed-export declare class MutableBinding<T>-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { AppStorageV2, PersistenceV2, Type, UIUtils, ConnectOptions, Binding, MutableBinding, CustomComponentLifecycle, CustomComponentLifecycleObserver, CustomComponentLifecycleState, ComponentInit, ComponentAppear, ComponentBuilt, ComponentReuse, ComponentActive, ComponentInactive, ComponentRecycle, ComponentDisappear, CollectionType, ConnectOptionsCollections, CustomComponentContext, IReusePool, IReusableInfo, StorageDefaultCreator, TypeConstructorWithArgs, PersistenceErrorCallback, TypeConstructor, TypeDecorator, MonitorCallback, MonitorOptions, GetterCallback, SetterCallback, ObservedResult, DecoratorInfo, ElementInfo } from '@kit.ArkUI';
```

## value

```TypeScript
get value(): T
```

Provides a **get** accessor to obtain the current bound value.

**Type:** T

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

<!--Device-MutableBinding-get value(): T--><!--Device-MutableBinding-get value(): T-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

```TypeScript
set value(newValue: T)
```

Provides the **set** accessor to set a new value for the current bound value. The **set** accessor must be provided when the **MutableBinding** class instance is constructed. Otherwise, a runtime error will be thrown when the **set** accessor is triggered.

**Type:** T

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

<!--Device-MutableBinding-set value(newValue: T)--><!--Device-MutableBinding-set value(newValue: T)-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
