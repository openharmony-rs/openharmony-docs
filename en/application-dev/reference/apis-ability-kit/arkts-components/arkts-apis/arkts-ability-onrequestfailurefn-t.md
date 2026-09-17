# OnRequestFailureFn

```TypeScript
export type OnRequestFailureFn = (name: string, failureCode: AbilityStartFailureCode, failureMessage: string) => void
```

Defines the callback for failed ability launches.

**Since:** 21

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 21.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| name | string | Yes | Name of the launched ability or system operation. The ability component name is in the format of '[bundleName]#[moduleName]#[abilityName]'. If the user cancels the launch automatically, this parameter is empty. |
| failureCode | [AbilityStartFailureCode](arkts-ability-app-ability-completionhandlerforabilitystartcallback-abilitystartfailurecode-e.md) | Yes | Error code of the failure cause. |
| failureMessage | string | Yes | Description of the failure cause. |
