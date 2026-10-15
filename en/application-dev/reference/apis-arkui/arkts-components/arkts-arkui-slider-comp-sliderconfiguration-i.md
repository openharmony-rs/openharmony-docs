# SliderConfiguration

```TypeScript
declare interface SliderConfiguration extends CommonConfiguration<SliderConfiguration>
```

You need a custom class to implement the **ContentModifier** API. It inherits from [CommonConfiguration](arkts-arkui-common-comp-commonconfiguration-i.md).

**Inheritance/Implementation:** SliderConfiguration extends CommonConfiguration&lt;SliderConfiguration&gt;

**Since:** 12

<!--Device-unnamed-declare interface SliderConfiguration extends CommonConfiguration<SliderConfiguration>--><!--Device-unnamed-declare interface SliderConfiguration extends CommonConfiguration<SliderConfiguration>-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## triggerChange

```TypeScript
triggerChange: SliderTriggerChangeCallback
```

Triggers slider changes.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-SliderConfiguration-triggerChange: SliderTriggerChangeCallback--><!--Device-SliderConfiguration-triggerChange: SliderTriggerChangeCallback-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## max

```TypeScript
max: number
```

Maximum value.

**Type:** number

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-SliderConfiguration-max: number--><!--Device-SliderConfiguration-max: number-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## min

```TypeScript
min: number
```

Minimum value.

**Type:** number

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-SliderConfiguration-min: number--><!--Device-SliderConfiguration-min: number-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## step

```TypeScript
step: number
```

Step of the slider, which indicates the value increment of each slider movement.

**Type:** number

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-SliderConfiguration-step: number--><!--Device-SliderConfiguration-step: number-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## value

```TypeScript
value: number
```

Current progress.

**Type:** number

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-SliderConfiguration-value: number--><!--Device-SliderConfiguration-value: number-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
