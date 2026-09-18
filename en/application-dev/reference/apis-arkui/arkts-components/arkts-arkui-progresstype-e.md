# ProgressType

Enumerates progress indicator types.

**Since:** 8

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Linear

```TypeScript
Linear = 0
```

Linear type. Since API version 9, the progress indicator adapts to vertical display when its height is greater than its width.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Ring

```TypeScript
Ring = 1
```

The ring is gradually displayed until completely filled.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Eclipse

```TypeScript
Eclipse = 2
```

Eclipse type, which visualizes the progress in a way similar to the moon waxing from new to full.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## ScaleRing

```TypeScript
ScaleRing = 3
```

Ring style with scales, which is similar to the clock scale style.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Capsule

```TypeScript
Capsule = 4
```

Capsule style. At both ends, the progress indicator works in the same manner as the eclipse style. In the middle part of the capsule, the progress indicator works in the same manner as the linear style. When the height is greater than the width, the progress indicator adapts to vertical display.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
