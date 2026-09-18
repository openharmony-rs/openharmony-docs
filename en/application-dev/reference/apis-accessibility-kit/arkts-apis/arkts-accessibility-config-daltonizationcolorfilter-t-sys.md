# DaltonizationColorFilter (System API)

```TypeScript
type DaltonizationColorFilter = 'Normal' | 'Protanomaly' | 'Deuteranomaly' | 'Tritanomaly'
```

Color correction filters for different types of color vision deficiency.

The configuration takes effect when the daltonization feature is enabled ([daltonizationState](arkts-accessibility-config-con-sys.md#daltonizationstate) is set to **true**). When the daltonization feature is disabled ([daltonizationState](arkts-accessibility-config-con-sys.md#daltonizationstate) is set to **false**), the standard type is displayed.

**Since:** 9

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

**System API:** This is a system API.

| Type | Description |
| --- | --- |
| 'Normal' | Standard color vision. |
| 'Protanomaly' | Red-weak color vision deficiency. |
| 'Deuteranomaly' | Green-weak color vision deficiency. |
| 'Tritanomaly' | Blue-weak color vision deficiency. |
