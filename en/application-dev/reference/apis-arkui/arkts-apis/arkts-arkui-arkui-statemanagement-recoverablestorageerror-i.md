# RecoverableStorageError

```TypeScript
export declare interface RecoverableStorageError
```

Defines the error information reported through the callback of [RecoverableStorage](../../../ui/state-management/arkts-new-recoverablestorage.md).

**Since:** 26.1.0

<!--Device-unnamed-export declare interface RecoverableStorageError--><!--Device-unnamed-export declare interface RecoverableStorageError-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { AppStorageV2, PersistenceV2, Type, UIUtils, ConnectOptions, Binding, MutableBinding, CustomComponentLifecycle, CustomComponentLifecycleObserver, CustomComponentLifecycleState, ComponentInit, ComponentAppear, ComponentBuilt, ComponentReuse, ComponentActive, ComponentInactive, ComponentRecycle, ComponentDisappear, CollectionType, ConnectOptionsCollections, CustomComponentContext, IReusePool, IDefaultReusePool, IReusableInfo, StorageDefaultCreator, TypeConstructorWithArgs, PersistenceErrorCallback, TypeConstructor, TypeDecorator, MonitorCallback, MonitorOptions, GetterCallback, SetterCallback, ObservedResult, DecoratorInfo, ElementInfo, RecoverableStorage, RecoverableConnectOptions, RecoverableStorageError, NotifyOnErrorCallback } from '@kit.ArkUI';
```

## keys

```TypeScript
keys: Array<string>
```

Keys affected by the error.

**Type:** Array&lt;string&gt;

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.1.0.

<!--Device-RecoverableStorageError-keys: Array<string>--><!--Device-RecoverableStorageError-keys: Array<string>-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## message

```TypeScript
message: string
```

Extra information about the error.

**Type:** string

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.1.0.

<!--Device-RecoverableStorageError-message: string--><!--Device-RecoverableStorageError-message: string-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## reason

```TypeScript
reason: 'serialization' | 'deserialization'
```

Reason of the error. The value can be **'serialization'** (serialization failed, for example, the serialization budget is exceeded or a field cannot be serialized) or **'deserialization'** (deserialization failed, for example, the data is corrupted or the type does not match). Connect entry errors (unsupported type, invalid parameters) are **thrown** as BusinessError **140124** and are not reported through this callback. Recommended total user data: ≤100KB per instance (150KB serialization budget shared with system data).

**Type:** 'serialization' &#124; 'deserialization'

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.1.0.

<!--Device-RecoverableStorageError-reason: 'serialization' | 'deserialization'--><!--Device-RecoverableStorageError-reason: 'serialization' | 'deserialization'-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
