# Curve

```TypeScript
declare enum Curve
```

Enumerates the interpolation curves. For details about the animation, see <!--RP1--> [Bezier Curve](../../../../design/ux-design/animation-attributes.md)<!--RP1End-->.

**Since:** 7

<!--Device-unnamed-declare enum Curve--><!--Device-unnamed-declare enum Curve-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Ease

```TypeScript
Ease
```

The animation starts slowly, accelerates, and then decelerates before ending. The curve is CubicBezier(0.25, 0.1, 0.25, 1.0).

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

<!--Device-Curve-Ease--><!--Device-Curve-Ease-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## EaseIn

```TypeScript
EaseIn
```

The animation starts at a low speed and then picks up speed until the end. The cubic-bezier curve (0.42, 0.0, 1.0, 1.0) is used.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

<!--Device-Curve-EaseIn--><!--Device-Curve-EaseIn-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## EaseInOut

```TypeScript
EaseInOut
```

The animation starts and ends at a low speed. The cubic-bezier curve(0.42, 0.0, 0.58, 1.0) is used.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

<!--Device-Curve-EaseInOut--><!--Device-Curve-EaseInOut-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## EaseOut

```TypeScript
EaseOut
```

The animation ends at a low speed. The cubic-bezier curve (0.0, 0.0, 0.58, 1.0) is used.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

<!--Device-Curve-EaseOut--><!--Device-Curve-EaseOut-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## ExtremeDeceleration

```TypeScript
ExtremeDeceleration
```

The animation uses the extreme deceleration cubic-bezier curve(0.0, 0.0, 0.0, 1.0).

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

<!--Device-Curve-ExtremeDeceleration--><!--Device-Curve-ExtremeDeceleration-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## FastOutLinearIn

```TypeScript
FastOutLinearIn
```

The animation uses the acceleration cubic-bezier curve(0.4, 0.0, 1.0, 1.0).

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

<!--Device-Curve-FastOutLinearIn--><!--Device-Curve-FastOutLinearIn-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## FastOutSlowIn

```TypeScript
FastOutSlowIn
```

The animation uses the standard cubic-bezier curve(0.4, 0.0, 0.2, 1.0).

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

<!--Device-Curve-FastOutSlowIn--><!--Device-Curve-FastOutSlowIn-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Friction

```TypeScript
Friction
```

The animation uses the friction cubic-bezier curve(0.2, 0.0, 0.2, 1.0).

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

<!--Device-Curve-Friction--><!--Device-Curve-Friction-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Linear

```TypeScript
Linear
```

The animation maintains a constant speed throughout the process.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

<!--Device-Curve-Linear--><!--Device-Curve-Linear-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## LinearOutSlowIn

```TypeScript
LinearOutSlowIn
```

The animation uses the deceleration cubic-bezier curve(0.0, 0.0, 0.2, 1.0).

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

<!--Device-Curve-LinearOutSlowIn--><!--Device-Curve-LinearOutSlowIn-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Rhythm

```TypeScript
Rhythm
```

The animation uses the rhythm cubic-bezier curve(0.7, 0.0, 0.2, 1.0).

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

<!--Device-Curve-Rhythm--><!--Device-Curve-Rhythm-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Sharp

```TypeScript
Sharp
```

The animation uses the sharp cubic-bezier curve(0.33, 0.0, 0.67, 1.0).

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

<!--Device-Curve-Sharp--><!--Device-Curve-Sharp-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Smooth

```TypeScript
Smooth
```

The animation uses the smooth cubic-bezier curve(0.4, 0.0, 0.4, 1.0).

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

<!--Device-Curve-Smooth--><!--Device-Curve-Smooth-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
