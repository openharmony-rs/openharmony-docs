# SliderShowStepOptions

```TypeScript
declare interface SliderShowStepOptions
```

Provides accessibility text mapping for the slider step markers.

**Since:** 20

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## stepsAccessibility

```TypeScript
stepsAccessibility?: Map<number, SliderStepItemAccessibility>
```

Step value-to-text mappings for assistive technologies (for example, screen readers).

Value range for **Key**: [0, INT32_MAX].

If **Key** is set to a negative number or a decimal, the setting does not take effect.

Default value: **{}**

**Type:** Map&lt;number, [SliderStepItemAccessibility](arkts-arkui-slider-comp-sliderstepitemaccessibility-i.md)&gt;

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
