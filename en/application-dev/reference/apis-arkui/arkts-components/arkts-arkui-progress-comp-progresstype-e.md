# ProgressType

```TypeScript
declare enum ProgressType
```

Enumerates progress indicator types.

**Since:** 8

<!--Device-unnamed-declare enum ProgressType--><!--Device-unnamed-declare enum ProgressType-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Linear

```TypeScript
Linear = 0
```

Linear type. Since API version 9, the progress indicator adapts to vertical display when its height is greater than its width.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

<!--Device-ProgressType-Linear = 0--><!--Device-ProgressType-Linear = 0-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Ring

```TypeScript
Ring = 1
```

Ring type without scales. The ring gradually displays until it is fully filled.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

<!--Device-ProgressType-Ring = 1--><!--Device-ProgressType-Ring = 1-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Eclipse

```TypeScript
Eclipse = 2
```

Eclipse type, which visualizes the progress in a way similar to the moon waxing from new to full.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

<!--Device-ProgressType-Eclipse = 2--><!--Device-ProgressType-Eclipse = 2-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## ScaleRing

```TypeScript
ScaleRing = 3
```

Ring style with scales, which is similar to the clock scale style. Since API version 9, the progress indicator automatically switches to a non-scaled ring style when the outer scales overlap.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

<!--Device-ProgressType-ScaleRing = 3--><!--Device-ProgressType-ScaleRing = 3-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Capsule

```TypeScript
Capsule = 4
```

Capsule style. The progress display effect at the arc ends is the same as that of Eclipse, and the progress display effect in the middle section is the same as that of Linear. Since API version 9, when the height is greater than the width, the component is displayed vertically in an adaptive manner.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

<!--Device-ProgressType-Capsule = 4--><!--Device-ProgressType-Capsule = 4-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
