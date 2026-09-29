# FillMode

```TypeScript
declare enum FillMode
```

Sets the status before and after execution of the animation in the current playback direction. The status after execution of the animation is jointly determined by the **fillMode** and **reverse** attributes. For example, if **fillMode** is set to **Forwards**, the target will retain the state defined by the last keyframe encountered during execution. In this case, if **reverse** is set to **false**, the target will retain the state defined by the last keyframe encountered in the forward direction, that is, the last image; if **reverse** is set to **true**, the target will retain the state defined by the last keyframe encountered in the backward direction, that is, the first image.

**Since:** 7

<!--Device-unnamed-declare enum FillMode--><!--Device-unnamed-declare enum FillMode-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## None

```TypeScript
None = 0
```

If the animation is not executed, no style is applied to the target. After the animation is played, the initial default state is restored.

**Since:** 7

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 10.

<!--Device-FillMode-None = 0--><!--Device-FillMode-None = 0-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Forwards

```TypeScript
Forwards = 1
```

The target component retains the state set by the last keyframe encountered during execution of the animation.

**Since:** 7

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 10.

<!--Device-FillMode-Forwards = 1--><!--Device-FillMode-Forwards = 1-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Backwards

```TypeScript
Backwards = 2
```

The animation applies the values defined in the first relevant keyframe once it is applied to the target component, and retains the values during the period set by **delay**. The first relevant keyframe depends on the value of **playMode**. If **playMode** is **Normal** or **Alternate**, the first relevant keyframe is in the **from** state. If **playMode** is **Reverse** or **AlternateReverse**, the first relevant keyframe is in the **to** state.

**Since:** 7

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 10.

<!--Device-FillMode-Backwards = 2--><!--Device-FillMode-Backwards = 2-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Both

```TypeScript
Both = 3
```

The animation follows the rules for both **Forwards** and **Backwards**, extending the animation attributes in both directions.

**Since:** 7

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 10.

<!--Device-FillMode-Both = 3--><!--Device-FillMode-Both = 3-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
