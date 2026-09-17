# ToggleOptions

Options of the toggle.

> **NOTE:** 
> 
> To standardize anonymous object definitions, the element definitions here have been revised in API version 18.
> While historical version information is preserved for anonymous objects, there may be cases where the outer element
> 's

**Since:** 18

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## isOn

```TypeScript
isOn?: boolean
```

Whether the toggle is turned on.

**true**: on. **false**: off.

Default value: **false**

This parameter supports two-way binding through [&#36;&#36;](../../../ui/state-management/arkts-two-way-sync.md).

This property supports two-way binding through [!!](../../../ui/state-management/arkts-new-binding.md#two-way-binding-between-built-in-component-parameters).

**Type:** boolean

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## type

```TypeScript
type: ToggleType
```

Type of the toggle.

Default value: **ToggleType.Switch**

**Type:** [ToggleType](arkts-arkui-toggletype-e.md)

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
