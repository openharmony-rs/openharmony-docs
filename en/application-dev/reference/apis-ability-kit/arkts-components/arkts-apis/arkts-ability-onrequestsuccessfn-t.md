# OnRequestSuccessFn

```TypeScript
export type OnRequestSuccessFn = (name: string) => void
```

Defines the callback for successful ability launches.

**Since:** 21

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 21.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| name | string | Yes | Name of the launched ability or system operation.  The ability component name is in the format of '[bundleName]#[moduleName]#[abilityName]'. |

**Examples**

See [OnRequestFailureFn](arkts-ability-onrequestfailurefn-t.md).
