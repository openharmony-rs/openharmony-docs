# @ohos.ability.particleAbility(ParticleAbility Module)

The particleAbility module provides APIs for operating a DataAbility and ServiceAbility. You can use the APIs to start and terminate a ParticleAbility, obtain a dataAbilityHelper object, and connect to or disconnect from a ServiceAbility.

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Ability.AbilityRuntime.FAModel

## Modules to Import

```TypeScript
import { particleAbility } from '@kit.AbilityKit';
```

## Summary

### Functions

| Name | Description |
| --- | --- |
| [acquireDataAbilityHelper](arkts-ability-particleability-acquiredataabilityhelper-f.md) | Obtains a dataAbilityHelper object. |
| [cancelBackgroundRunning](arkts-ability-particleability-cancelbackgroundrunning-f.md#cancelbackgroundrunning) | Requests to cancel a continuous task from the system. This API uses an asynchronous callback to return the result. |
| [cancelBackgroundRunning](arkts-ability-particleability-cancelbackgroundrunning-f.md#cancelbackgroundrunning-1) | Requests to cancel a continuous task from the system. This API uses a promise to return the result. |
| [connectAbility](arkts-ability-particleability-connectability-f.md) | Connects this ability to a ServiceAbility. |
| [disconnectAbility](arkts-ability-particleability-disconnectability-f.md#disconnectability) | Disconnects this ability from a specific ServiceAbility. This API uses an asynchronous callback to return the result. |
| [disconnectAbility](arkts-ability-particleability-disconnectability-f.md#disconnectability-1) | Disconnects this ability from a specific ServiceAbility. This API uses a promise to return the result. |
| [startAbility](arkts-ability-particleability-startability-f.md#startability) | Starts a ParticleAbility. This API uses an asynchronous callback to return the result. |
| [startAbility](arkts-ability-particleability-startability-f.md#startability-1) | Starts a ParticleAbility. This API uses a promise to return the result. |
| [startBackgroundRunning](arkts-ability-particleability-startbackgroundrunning-f.md#startbackgroundrunning) | Requests a continuous task from the system. This API uses an asynchronous callback to return the result. |
| [startBackgroundRunning](arkts-ability-particleability-startbackgroundrunning-f.md#startbackgroundrunning-1) | Requests a continuous task from the system. This API uses a promise to return the result. |
| [terminateSelf](arkts-ability-particleability-terminateself-f.md#terminateself) | Terminates this ParticleAbility. This API uses an asynchronous callback to return the result. |
| [terminateSelf](arkts-ability-particleability-terminateself-f.md#terminateself-1) | Terminates this ParticleAbility. This API uses a promise to return the result. |

### Enums

| Name | Description |
| --- | --- |
| [ErrorCode](arkts-ability-particleability-errorcode-e.md) | Enumerates the error codes that may be returned when an ability is started. |
