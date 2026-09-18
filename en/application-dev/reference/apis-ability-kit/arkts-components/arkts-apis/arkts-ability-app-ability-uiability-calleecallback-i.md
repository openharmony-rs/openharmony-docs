# CalleeCallback

Defines the callback of the registration message notification of the UIAbility.

**Since:** 9

**System capability:** SystemCapability.Ability.AbilityRuntime.AbilityCore

## Modules to Import

```TypeScript
import { UIAbility, Callee, CalleeCallback, Caller, OnReleaseCallback, OnRemoteStateChangeCallback } from '@kit.AbilityKit';
```

## [[Call]]

```TypeScript
(indata: rpc.MessageSequence): rpc.Parcelable
```

Defines the callback of Callee.

**Since:** 9

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AbilityRuntime.AbilityCore

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| indata | [rpc.MessageSequence](../../apis-ipc-kit/arkts-apis/arkts-ipc-rpc-messagesequence-c.md) | Yes | Data to be transferred. |

**Return value:**

| Type | Description |
| --- | --- |
| [rpc.Parcelable](../../apis-ipc-kit/arkts-apis/arkts-ipc-rpc-parcelable-i.md) | Returned data object. |
