# SliderShowStepOptions

```TypeScript
declare interface SliderShowStepOptions
```

Provides accessibility text mapping for the slider step markers.

**Since:** 20

<!--Device-unnamed-declare interface SliderShowStepOptions--><!--Device-unnamed-declare interface SliderShowStepOptions-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## stepsAccessibility

```TypeScript
stepsAccessibility?: Map<number, SliderStepItemAccessibility>
```

Accessibility text mapping for the slider step markers, read by tools such as screen readers to enhance accessibility.

Key value range: [0, INT32_MAX]. When the key is set to a negative number or a decimal, the setting does not take effect.

Default value: **{}**

**Type:** Map&lt;number, [SliderStepItemAccessibility](arkts-arkui-slider-comp-sliderstepitemaccessibility-i.md)&gt;

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

<!--Device-SliderShowStepOptions-stepsAccessibility?: Map<number, SliderStepItemAccessibility>--><!--Device-SliderShowStepOptions-stepsAccessibility?: Map<number, SliderStepItemAccessibility>-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
