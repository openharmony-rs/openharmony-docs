# Curve

插值曲线和动效请参考<!--RP1-->[贝塞尔曲线](../../../../../design/ux-design/animation-attributes.md)<!--RP1End-->。

| 名称 | 值 | 说明 |
| ------------------- | -- | ------------------------------------------------------------ |
| Linear | 0 | 表示动画从头到尾的速度都是相同的。 |
| Ease | 1 | 表示动画以低速开始，然后加快，在结束前变慢，cubic-bezier(0.25, 0.1, 0.25, 1.0)。 |
| EaseIn | 2 | 表示动画以低速开始，cubic-bezier(0.42, 0.0, 1.0, 1.0)。 |
| EaseOut | 3 | 表示动画以低速结束，cubic-bezier(0.0, 0.0, 0.58, 1.0)。 |
| EaseInOut | 4 | 表示动画以低速开始和结束，cubic-bezier(0.42, 0.0, 0.58, 1.0)。 |
| FastOutSlowIn | 5 | 标准曲线，cubic-bezier(0.4, 0.0, 0.2, 1.0)。 |
| LinearOutSlowIn | 6 | 减速曲线，cubic-bezier(0.0, 0.0, 0.2, 1.0)。 |
| FastOutLinearIn | 7 | 加速曲线，cubic-bezier(0.4, 0.0, 1.0, 1.0)。 |
| ExtremeDeceleration | 8 | 急缓曲线，cubic-bezier(0.0, 0.0, 0.0, 1.0)。 |
| Sharp | 9 | 锐利曲线，cubic-bezier(0.33, 0.0, 0.67, 1.0)。 |
| Rhythm | 10 | 节奏曲线，cubic-bezier(0.7, 0.0, 0.2, 1.0)。 |
| Smooth | 11 | 平滑曲线，cubic-bezier(0.4, 0.0, 0.4, 1.0)。 |
| Friction | 12 | 阻尼曲线，cubic-bezier(0.2, 0.0, 0.2, 1.0)。 |

**起始版本：** 7

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## Linear

```TypeScript
Linear = 0
```

Linear. Indicates that the animation has the same velocity from start to finish.

**起始版本：** 7

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## Ease

```TypeScript
Ease = 1
```

Ease. Indicates that the animation starts at a low speed, then speeds up, and slows down before the end,
CubicBezier(0.25, 0.1, 0.25, 1.0).

**起始版本：** 7

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## EaseIn

```TypeScript
EaseIn = 2
```

EaseIn. Indicates that the animation starts at a low speed, Cubic Bezier (0.42, 0.0, 1.0, 1.0).

**起始版本：** 7

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## EaseOut

```TypeScript
EaseOut = 3
```

EaseOut. Indicates that the animation ends at low speed, CubicBezier (0.0, 0.0, 0.58, 1.0).

**起始版本：** 7

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## EaseInOut

```TypeScript
EaseInOut = 4
```

EaseInOut. Indicates that the animation starts and ends at low speed, CubicBezier (0.42, 0.0, 0.58, 1.0).

**起始版本：** 7

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## FastOutSlowIn

```TypeScript
FastOutSlowIn = 5
```

FastOutSlowIn. Standard curve, cubic-bezier (0.4, 0.0, 0.2, 1.0).

**起始版本：** 7

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## LinearOutSlowIn

```TypeScript
LinearOutSlowIn = 6
```

LinearOutSlowIn. Deceleration curve, cubic-bezier (0.0, 0.0, 0.2, 1.0).

**起始版本：** 7

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## FastOutLinearIn

```TypeScript
FastOutLinearIn = 7
```

FastOutLinearIn. Acceleration curve, cubic-bezier (0.4, 0.0, 1.0, 1.0).

**起始版本：** 7

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## ExtremeDeceleration

```TypeScript
ExtremeDeceleration = 8
```

ExtremeDeceleration. Abrupt curve, cubic-bezier (0.0, 0.0, 0.0, 1.0).

**起始版本：** 7

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## Sharp

```TypeScript
Sharp = 9
```

Sharp. Sharp curves, cubic-bezier (0.33, 0.0, 0.67, 1.0).

**起始版本：** 7

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## Rhythm

```TypeScript
Rhythm = 10
```

Rhythm. Rhythmic curve, cubic-bezier (0.7, 0.0, 0.2, 1.0).

**起始版本：** 7

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## Smooth

```TypeScript
Smooth = 11
```

Smooth. Smooth curves, cubic-bezier (0.4, 0.0, 0.4, 1.0).

**起始版本：** 7

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## Friction

```TypeScript
Friction = 12
```

Friction. Damping curves, CubicBezier (0.2, 0.0, 0.2, 1.0).

**起始版本：** 7

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

