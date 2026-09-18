# WindowAnimationCurve

Enumerates the types of window animation curves.

**Since:** 20

**System capability:** SystemCapability.Window.SessionManager

## LINEAR

```TypeScript
LINEAR = 0
```

The animation speed is constant from start to finish.

When this curve type is used, **duration** in [WindowAnimationConfig](arkts-arkui-window-windowanimationconfig-i.md) is mandatory.

When this curve type is used, **param** in [WindowAnimationConfig](arkts-arkui-window-windowanimationconfig-i.md) is optional and does not take effect.

**Since:** 20

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.Window.SessionManager

## INTERPOLATION_SPRING

```TypeScript
INTERPOLATION_SPRING = 1
```

Interpolator spring curve, an animation curve from 0 to 1, where the actual animation values are interpolated based on the curve. The animation duration is subject to the curve parameters, rather than the **duration** parameter in [WindowAnimationConfig](arkts-arkui-window-windowanimationconfig-i.md).

When this curve type is used, **duration** in [WindowAnimationConfig](arkts-arkui-window-windowanimationconfig-i.md) is optional and does not take effect.

When this curve type is used, **param** in [WindowAnimationConfig](arkts-arkui-window-windowanimationconfig-i.md) is mandatory.

**Since:** 20

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.Window.SessionManager

## CUBIC_BEZIER

```TypeScript
CUBIC_BEZIER = 2
```

Cubic Bézier curve.

When this curve type is used, **param** and **duration** in [WindowAnimationConfig](arkts-arkui-window-windowanimationconfig-i.md) are mandatory.

**Since:** 20

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.Window.SessionManager
