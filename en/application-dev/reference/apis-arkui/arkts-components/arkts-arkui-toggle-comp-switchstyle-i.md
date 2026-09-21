# SwitchStyle

```TypeScript
declare interface SwitchStyle
```

Sets the style for the component of the **Switch** type.

**Since:** 12

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## pointColor

```TypeScript
pointColor?: ResourceColor
```

Color of the circular slider when the component is of the **Switch** type.

Default value: **$r('sys.color.ohos_id_color_foreground_contrary')**

**Type:** [ResourceColor](../arkts-apis/arkts-arkui-resourcecolor-t.md)

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## pointRadius

```TypeScript
pointRadius?: number | Resource
```

Radius of the circular slider when the component is of the **Switch** type. The unit is vp.

**NOTE:** 

Percentage values are not supported. The value specified is used only when it is greater than or equal to 0.

If the value is not specified or the specified one is less than 0, the radius is set using the following formula:

(Component height (in vp)/2) - (2 vp x Component height (in vp)/20 vp)

**Type:** number &#124; [Resource](../arkts-apis/arkts-arkui-resource-t.md)

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## trackBorderRadius

```TypeScript
trackBorderRadius?: number | Resource
```

Radius of the slider track border corners when the component is of the **Switch** type. The unit is vp.

**NOTE:** 

This parameter cannot be set in percentage. If the value specified is less than 0, the radius is set using the default value formula. If the value specified is greater than half of the component height, the latter is used. In other cases, the value specified is used.

If the value is not specified or the specified one is less than 0, the radius is set using the default value formula.

Default value formula: Component height (in vp)/2

**Type:** number &#124; [Resource](../arkts-apis/arkts-arkui-resource-t.md)

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## unselectedColor

```TypeScript
unselectedColor?: ResourceColor
```

Background color of the component when it is of the **Switch** type and is disabled.

Default value: **0x337F7F7F** (applies to both dark and light modes). Since API version 20, when [optimizing color mode switching overhead](../../../ui/ui-dark-light-color-adaptation.md#optimizing-color-mode-switching-overhead) is enabled, the default value is **0x19000000** (black with 10% opacity) in light mode and **0x19FFFFFF** (white with 10% opacity) in dark mode.

**Type:** [ResourceColor](../arkts-apis/arkts-arkui-resourcecolor-t.md)

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
