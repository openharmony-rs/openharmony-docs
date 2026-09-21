# DataPanelShadowOptions

```TypeScript
declare interface DataPanelShadowOptions extends MultiShadowOptions
```

Inherits from [MultiShadowOptions](arkts-arkui-common-comp-multishadowoptions-i.md) and has all properties of **MultiShadowOptions**.

**Inheritance/Implementation:** DataPanelShadowOptions extends [MultiShadowOptions](arkts-arkui-common-comp-multishadowoptions-i.md)

**Since:** 10

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## colors

```TypeScript
colors?: Array<ResourceColor | LinearGradient>
```

Array of shadow colors for data segments.

Default value: same as the value of **valueColors**

**NOTE:** 

If the number of the set shadow colors is less than that of the data segments, the number of the displayed shadow colors is the same as the former.

If the number of the set shadow colors is greater than that of the data segments, the number of the displayed shadow colors is the same as the latter.

**Type:** Array&lt;[ResourceColor](../arkts-apis/arkts-arkui-resourcecolor-t.md) &#124; [LinearGradient](arkts-arkui-datapanel-comp-lineargradient-c.md)&gt;

**Default:** Consistent with valueColors

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
