# RecoverableConnectOptions

```TypeScript
export declare class RecoverableConnectOptions<T extends object, S extends object>
```

Defines the options of [RecoverableStorage.connect](arkts-arkui-arkui-statemanagement-recoverablestorage-c.md#connect).

**Since:** 26.1.0

<!--Device-unnamed-export declare class RecoverableConnectOptions<T extends object, S extends object>--><!--Device-unnamed-export declare class RecoverableConnectOptions<T extends object, S extends object>-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { AppStorageV2, PersistenceV2, Type, UIUtils, ConnectOptions, Binding, MutableBinding, CustomComponentLifecycle, CustomComponentLifecycleObserver, CustomComponentLifecycleState, ComponentInit, ComponentAppear, ComponentBuilt, ComponentReuse, ComponentActive, ComponentInactive, ComponentRecycle, ComponentDisappear, CollectionType, ConnectOptionsCollections, CustomComponentContext, IReusePool, IDefaultReusePool, IReusableInfo, StorageDefaultCreator, TypeConstructorWithArgs, PersistenceErrorCallback, TypeConstructor, TypeDecorator, MonitorCallback, MonitorOptions, GetterCallback, SetterCallback, ObservedResult, DecoratorInfo, ElementInfo, RecoverableStorage, RecoverableConnectOptions, RecoverableStorageError, NotifyOnErrorCallback } from '@kit.ArkUI';
```

## defaultCreator

```TypeScript
defaultCreator: StorageDefaultCreator<T>
```

Constructor for obtaining the default value. It is used when the variable is connected for the first time (neither memory nor a snapshot holds the key) and as the fallback when restoration fails.

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.1.0.

<!--Device-RecoverableConnectOptions-defaultCreator: StorageDefaultCreator<T>--><!--Device-RecoverableConnectOptions-defaultCreator: StorageDefaultCreator<T>-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## defaultSubCreator

```TypeScript
defaultSubCreator?: StorageDefaultCreator<S>
```

Constructor for the nested **\

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.1.0.

<!--Device-RecoverableConnectOptions-defaultSubCreator?: StorageDefaultCreator<S>--><!--Device-RecoverableConnectOptions-defaultSubCreator?: StorageDefaultCreator<S>-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## notifyOnError

```TypeScript
notifyOnError?: NotifyOnErrorCallback
```

Callback for reporting serialization or deserialization errors. If this parameter is not specified, errors are handled internally without crashing the application.

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.1.0.

<!--Device-RecoverableConnectOptions-notifyOnError?: NotifyOnErrorCallback--><!--Device-RecoverableConnectOptions-notifyOnError?: NotifyOnErrorCallback-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## component

```TypeScript
component: BaseCustomComponent
```

Custom component instance, for which **this** is passed to obtain the window-level instance ID used for per-instance isolation.

**Type:** [BaseCustomComponent](../arkts-components/arkts-arkui-common-comp-basecustomcomponent-c.md)

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.1.0.

<!--Device-RecoverableConnectOptions-component: BaseCustomComponent--><!--Device-RecoverableConnectOptions-component: BaseCustomComponent-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## key

```TypeScript
key?: string
```

Key of the recoverable state variable. If this parameter is not specified, the name of the type is used.

**Type:** string

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.1.0.

<!--Device-RecoverableConnectOptions-key?: string--><!--Device-RecoverableConnectOptions-key?: string-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## type

```TypeScript
type: TypeConstructorWithArgs<T>
```

Type of the recoverable state variable. Only object types are supported; simple types such as **number**, **string**, and **boolean** are rejected.

**Type:** [TypeConstructorWithArgs](arkts-arkui-arkui-statemanagement-typeconstructorwithargs-i.md)&lt;T&gt;

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.1.0.

<!--Device-RecoverableConnectOptions-type: TypeConstructorWithArgs<T>--><!--Device-RecoverableConnectOptions-type: TypeConstructorWithArgs<T>-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
