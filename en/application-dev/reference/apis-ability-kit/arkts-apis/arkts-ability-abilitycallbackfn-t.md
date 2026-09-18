# AbilityCallbackFn

```TypeScript
type AbilityCallbackFn = (ability: any) => void
```

The callback is called when only an ability is monitored.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.Ability.AbilityRuntime.AbilityCore

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| ability | any | Yes | Indicates the ability to register for listening. |
