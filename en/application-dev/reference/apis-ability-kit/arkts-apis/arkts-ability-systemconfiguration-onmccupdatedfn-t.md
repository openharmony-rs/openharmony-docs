# OnMCCUpdatedFn

```TypeScript
type OnMCCUpdatedFn = (mcc: string) => void
```

Defines an OnMCCUpdatedFn function.

@typedef { function }

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 24.

<!--Device-systemConfiguration-type OnMCCUpdatedFn = (mcc: string) => void--><!--Device-systemConfiguration-type OnMCCUpdatedFn = (mcc: string) => void-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| mcc | string | Yes | Indicates the mobile country code |
