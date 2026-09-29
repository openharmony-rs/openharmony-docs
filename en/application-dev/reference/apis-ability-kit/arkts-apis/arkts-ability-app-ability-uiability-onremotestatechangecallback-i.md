# OnRemoteStateChangeCallback

```TypeScript
export interface OnRemoteStateChangeCallback
```

Defines the callback that is invoked when the remote UIAbility state changes in the collaboration scenario.

**Since:** 10

<!--Device-unnamed-export interface OnRemoteStateChangeCallback--><!--Device-unnamed-export interface OnRemoteStateChangeCallback-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.AbilityCore

## Modules to Import

```TypeScript
import { UIAbility, Callee, CalleeCallback, Caller, OnReleaseCallback, OnRemoteStateChangeCallback } from '@kit.AbilityKit';
```

## [[Call]]

```TypeScript
(msg: string): void
```

Defines the callback of OnRemoteStateChange.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

<!--Device-OnRemoteStateChangeCallback-(msg: string): void--><!--Device-OnRemoteStateChangeCallback-(msg: string): void-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.AbilityCore

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| msg | string | Yes | Message used for disconnection. |
