# RecoverableStorage

```TypeScript
export declare class RecoverableStorage
```

Provides the capability of automatically saving and restoring declared state variables when the application is terminated due to resource control or exits abnormally. After a variable is declared through [connect](#connect), its value is saved automatically on the save occasions of the system recovery pipeline and restored automatically on the next recovery restart.

> **NOTE:** 
> 
> 1. For an application terminated due to resource control (for example, low memory), the value saved when the application switches to the background is restored after the restart.
> 
> 2. For **JS_ERROR** and **APP_FREEZE** exits, the value at the moment the error occurs is saved and then restored after the system automatically restarts the application. This requires the application to have called **enableAppRecovery** (default parameters meet the requirement) and not registered an error observer.
> 
> 3. Restoration is performed only when the application is restarted by the system with the recovery restart parameter. Starting the application manually always performs a cold start, where **connect** returns the default value.

**Since:** 26.1.0

<!--Device-unnamed-export declare class RecoverableStorage--><!--Device-unnamed-export declare class RecoverableStorage-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { AppStorageV2, PersistenceV2, Type, UIUtils, ConnectOptions, Binding, MutableBinding, CustomComponentLifecycle, CustomComponentLifecycleObserver, CustomComponentLifecycleState, ComponentInit, ComponentAppear, ComponentBuilt, ComponentReuse, ComponentActive, ComponentInactive, ComponentRecycle, ComponentDisappear, CollectionType, ConnectOptionsCollections, CustomComponentContext, IReusePool, IDefaultReusePool, IReusableInfo, StorageDefaultCreator, TypeConstructorWithArgs, PersistenceErrorCallback, TypeConstructor, TypeDecorator, MonitorCallback, MonitorOptions, GetterCallback, SetterCallback, ObservedResult, DecoratorInfo, ElementInfo, RecoverableStorage, RecoverableConnectOptions, RecoverableStorageError, NotifyOnErrorCallback } from '@kit.ArkUI';
```

## connect

```TypeScript
static connect<T extends object, S extends object>(
    params: RecoverableConnectOptions<T, S>
  ): T
```

Declares a recoverable state variable. If the variable has been stored (in memory or in a snapshot), the stored value is returned; otherwise, a default value is constructed through **defaultCreator** and returned.

> **NOTE:** 
> 
> 1. Only object types are supported. Connecting simple types such as **number**, **string**, and **boolean**throws **BusinessError(140124)** (same as PersistenceV2).
> 
> 2. If the same key of the same instance is connected again with the same type, the existing reference is returned; connecting with a mismatched type throws **BusinessError(140124)**.
> 
> 3. On a recovery restart, the restored value takes precedence over the default value. If restoration fails,the default value constructed through **defaultCreator** is returned and the error is reported through **notifyOnError**.
> 
> 4. The typical usage is mutating properties of the connected object. Reassigning the whole value of a V1 **\@State** variable causes the stored reference to be stale and is not tracked.
> 
> 5. Variables are isolated by the window-level instance ID obtained from **component**. Variables of
> 
> different instances do not affect each other.

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.1.0.

<!--Device-RecoverableStorage-static connect<T extends object, S extends object>(    params: RecoverableConnectOptions<T, S>  ): T--><!--Device-RecoverableStorage-static connect<T extends object, S extends object>(    params: RecoverableConnectOptions<T, S>  ): T-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| params | [RecoverableConnectOptions](arkts-arkui-arkui-statemanagement-recoverableconnectoptions-c.md)&lt;T, S&gt; | Yes | Connection options. |

**Return value:**

| Type | Description |
| --- | --- |
| T | Returns the restored value or the default value if the connection is successful. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| 140124 | Unsupported type or parameters. |

## keys

```TypeScript
static keys(component: BaseCustomComponent): Array<string>
```

Obtains all keys of the recoverable state variables registered by the current instance (identified by the window-level instance ID of **component**).

> **NOTE:** 
> 
> 
> The order of keys in the array is not sequential and unrelated to the order in which keys are registered.

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.1.0.

<!--Device-RecoverableStorage-static keys(component: BaseCustomComponent): Array<string>--><!--Device-RecoverableStorage-static keys(component: BaseCustomComponent): Array<string>-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| component | [BaseCustomComponent](../arkts-components/arkts-arkui-common-comp-basecustomcomponent-c.md) | Yes | Custom component instance, for which **this** is passed. |

**Return value:**

| Type | Description |
| --- | --- |
| Array&lt;string&gt; | All keys registered by the current instance. If no variable is registered, an empty array is returned. |

## remove

```TypeScript
static remove<T>(component: BaseCustomComponent, keyOrType: string | TypeConstructorWithArgs<T>): void
```

Unregisters the recoverable state variable of the specified key from the current instance (identified by the window-level instance ID of **component**). After the unregistration, the variable is no longer saved or restored, and connecting the key again returns the default value.

> **NOTE:** 
> 
> If a key that does not exist is unregistered, a warning is reported.

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.1.0.

<!--Device-RecoverableStorage-static remove<T>(component: BaseCustomComponent, keyOrType: string | TypeConstructorWithArgs<T>): void--><!--Device-RecoverableStorage-static remove<T>(component: BaseCustomComponent, keyOrType: string | TypeConstructorWithArgs<T>): void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| component | [BaseCustomComponent](../arkts-components/arkts-arkui-common-comp-basecustomcomponent-c.md) | Yes | Custom component instance, for which **this** is passed. |
| keyOrType | string &#124; [TypeConstructorWithArgs](arkts-arkui-arkui-statemanagement-typeconstructorwithargs-i.md)&lt;T&gt; | Yes | Key to be unregistered. If a type is specified, the key to be unregistered is the name of that type. |
