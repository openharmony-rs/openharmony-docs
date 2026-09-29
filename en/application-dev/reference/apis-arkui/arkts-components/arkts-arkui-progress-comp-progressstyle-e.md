# ProgressStyle

```TypeScript
declare enum ProgressStyle
```

Enumerates progress indicator styles.

**Since:** 7

<!--Device-unnamed-declare enum ProgressStyle--><!--Device-unnamed-declare enum ProgressStyle-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Linear

```TypeScript
Linear
```

Linear style. The progress bar is gradually filled from one end to the other along a straight line.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

<!--Device-ProgressStyle-Linear--><!--Device-ProgressStyle-Linear-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Ring

```TypeScript
Ring
```

Ring without scale. The ring is gradually displayed until it is completely filled.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

<!--Device-ProgressStyle-Ring--><!--Device-ProgressStyle-Ring-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Eclipse

```TypeScript
Eclipse
```

Eclipse style, which visualizes the progress in a way similar to the moon waxing from new to full.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

<!--Device-ProgressStyle-Eclipse--><!--Device-ProgressStyle-Eclipse-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## ScaleRing

```TypeScript
ScaleRing
```

Ring with scale. Displays a progress effect similar to a clock scale. Since API version 9, when the outer ring of the scale overlaps, it is automatically converted to a ring without scale.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

<!--Device-ProgressStyle-ScaleRing--><!--Device-ProgressStyle-ScaleRing-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Capsule

```TypeScript
Capsule
```

Capsule style. The progress display effect at the arc ends is the same as that of Eclipse, and the progress display effect in the middle is the same as that of Linear. Since API version 9, when the height is greater than the width, it is adaptively displayed vertically.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

<!--Device-ProgressStyle-Capsule--><!--Device-ProgressStyle-Capsule-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
