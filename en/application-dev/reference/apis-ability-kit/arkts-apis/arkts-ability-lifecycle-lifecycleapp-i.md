# LifecycleApp

interface of app lifecycle.

@interface LifecycleApp

**Since:** 7

**System capability:** SystemCapability.Ability.AbilityRuntime.FAModel

## Modules to Import

```TypeScript
```

## onActive

```TypeScript
onActive?(): void
```

Called back when an ability enters the &lt;b&gt;ACTIVE&lt;/b&gt; state.

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Ability.AbilityRuntime.FAModel

## onCompleteContinuation

```TypeScript
onCompleteContinuation?(result: number): void
```

Called back when a local ability migration is complete. <p>You can define the processing logic after the migration is complete. For example, you can display a prompt to notify the user of the successful migration and then exit the local ability.</p>

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Ability.AbilityRuntime.FAModel

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| result | number | Yes | Indicates the migration result code. The value `0` indicates that the migration is successful, and `-1` indicates that the migration fails. |

## onCreate

```TypeScript
onCreate?(): void
```

Called back when an ability is started for initialization.

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Ability.AbilityRuntime.FAModel

## onDestroy

```TypeScript
onDestroy?(): void
```

Called back before an ability is destroyed.

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Ability.AbilityRuntime.FAModel

## onHide

```TypeScript
onHide?(): void
```

Called back when an ability enters the &lt;b&gt;BACKGROUND&lt;/b&gt; state.

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Ability.AbilityRuntime.FAModel

## onInactive

```TypeScript
onInactive?(): void
```

Called back when an ability enters the &lt;b&gt;INACTIVE&lt;/b&gt; state (an ability in this state is not interactive and may change to the &lt;b&gt;BACKGROUND&lt;/b&gt; or &lt;b&gt;ACTIVE&lt;/b&gt; state).

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Ability.AbilityRuntime.FAModel

## onMemoryLevel

```TypeScript
onMemoryLevel?(level: number): void
```

Called when the system has determined to trim the memory, for example, when the ability is running in the background and there is no enough memory for running as many background processes as possible.

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Ability.AbilityRuntime.FAModel

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| level | number | Yes | Indicates the memory trim level, which shows the current memory usage status. |

## onNewWant

```TypeScript
onNewWant?(want: Want): void
```

Called when the launch mode of an ability is set to singleton.

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Ability.AbilityRuntime.FAModel

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| want | [Want](arkts-ability-app-ability-want-want-c.md) | Yes | Indicates the new `want` containing information about the ability. |

## onRemoteTerminated

```TypeScript
onRemoteTerminated?(): void
```

Called to notify the local device when a running ability on the remote device is destroyed after a reversible migration is performed for the ability from the local device to the remote device.

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Ability.AbilityRuntime.FAModel

## onRestoreAbilityState

```TypeScript
onRestoreAbilityState?(inState: PacMap): void
```

This method is called if an ability was destroyed at a certain time due to resource reclaim or was unexpectedly destroyed and the [onSaveAbilityState](#onsaveabilitystate) method was called to save its user data and states. Generally, this method is called after the onStart method.

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Ability.AbilityRuntime.FAModel

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| inState | [PacMap](arkts-ability-dataabilityhelper-pacmap-i.md) | Yes | Indicates the `PacMap` object used for storing data and states. This parameter can not be null. |

## onRestoreData

```TypeScript
onRestoreData?(data: Object): void
```

Restores the user data saved during the migration for an ability on the remote device immediately after the ability is created on the remote device. Lifecycle scheduling for the ability starts only after the user data is restored.

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Ability.AbilityRuntime.FAModel

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| data | Object | Yes | Indicates the user data to restore. |

## onSaveAbilityState

```TypeScript
onSaveAbilityState?(outState: PacMap): void
```

This method is called when the system determines that the ability may be destroyed in an unexpected situation, for example, when the screen orientation changes or the user touches the Home key. Generally, this method is used only to save temporary states.

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Ability.AbilityRuntime.FAModel

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| outState | [PacMap](arkts-ability-dataabilityhelper-pacmap-i.md) | Yes | Indicates the `PacMap` object used for storing user data and states. This parameter cannot be null. |

## onSaveData

```TypeScript
onSaveData?(data: Object): boolean
```

Saves the user data of a local ability generated during runtime. After the migration is triggered and the local ability is ready, this method is called when the Distributed Scheduler Service requests data from the local ability.

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Ability.AbilityRuntime.FAModel

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| data | Object | Yes | Indicates the user data to save. |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Returns `true` if the data is successfully saved; returns `false` otherwise. |

## onShow

```TypeScript
onShow?(): void
```

Called back when the state of an ability changes from &lt;b&gt;BACKGROUND&lt;/b&gt; to &lt;b&gt;INACTIVE&lt;/b&gt;.

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Ability.AbilityRuntime.FAModel

## onStartContinuation

```TypeScript
onStartContinuation?(): boolean
```

Asks a user whether to start the migration.

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Ability.AbilityRuntime.FAModel

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Returns `true` if the user allows the migration; returns `false` otherwise. |
