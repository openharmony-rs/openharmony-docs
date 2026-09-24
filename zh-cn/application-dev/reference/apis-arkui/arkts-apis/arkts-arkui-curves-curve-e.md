# Curve

```TypeScript
enum Curve
```

插值曲线和动效请参考<!--RP1-->[贝塞尔曲线](arkts-arkui-curves.md)<!--RP1End-->。

| 名称 | 值 | 说明 |  
| ------------------- | -- | ------------------------------------------------------------ |  
| [Linear](arkts-arkui-curves-curve-e.md) | 0 | 表示动画从头到尾的速度都是相同的。 |
| [Ease](arkts-arkui-curves-curve-e.md) | 1 | 表示动画以低速开始，然后加快，在结束前变慢，cubic-bezier(0.25, 0.1, 0.25, 1.0)。 |
| [EaseIn](arkts-arkui-curves-curve-e.md) | 2 | 表示动画以低速开始，cubic-bezier(0.42, 0.0, 1.0, 1.0)。 |
| [EaseOut](arkts-arkui-curves-curve-e.md) | 3 | 表示动画以低速结束，cubic-bezier(0.0, 0.0, 0.58, 1.0)。 |
| [EaseInOut](arkts-arkui-curves-curve-e.md) | 4 | 表示动画以低速开始和结束，cubic-bezier(0.42, 0.0, 0.58, 1.0)。 |
| [FastOutSlowIn](arkts-arkui-curves-curve-e.md) | 5 | 标准曲线，cubic-bezier(0.4, 0.0, 0.2, 1.0)。 |
| [LinearOutSlowIn](arkts-arkui-curves-curve-e.md) | 6 | 减速曲线，cubic-bezier(0.0, 0.0, 0.2, 1.0)。 |
| [FastOutLinearIn](arkts-arkui-curves-curve-e.md) | 7 | 加速曲线，cubic-bezier(0.4, 0.0, 1.0, 1.0)。 |
| [ExtremeDeceleration](arkts-arkui-curves-curve-e.md) | 8 | 急缓曲线，cubic-bezier(0.0, 0.0, 0.0, 1.0)。 |
| [Sharp](arkts-arkui-curves-curve-e.md) | 9 | 锐利曲线，cubic-bezier(0.33, 0.0, 0.67, 1.0)。 |
| [Rhythm](arkts-arkui-curves-curve-e.md) | 10 | 节奏曲线，cubic-bezier(0.7, 0.0, 0.2, 1.0)。 |
| [Smooth](arkts-arkui-curves-curve-e.md) | 11 | 平滑曲线，cubic-bezier(0.4, 0.0, 0.4, 1.0)。 |
| [Friction](arkts-arkui-curves-curve-e.md) | 12 | 阻尼曲线，cubic-bezier(0.2, 0.0, 0.2, 1.0)。 |

**起始版本：** 7

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## Linear

```TypeScript
Linear = 0
```

表示动画从头到尾的速度都是相同的。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## Ease

```TypeScript
Ease = 1
```

表示动画以低速开始，然后加快，在结束前变慢，cubic-bezier(0.25, 0.1, 0.25, 1.0)。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## EaseIn

```TypeScript
EaseIn = 2
```

表示动画以低速开始，cubic-bezier(0.42, 0.0, 1.0, 1.0)。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## EaseOut

```TypeScript
EaseOut = 3
```

表示动画以低速结束，cubic-bezier(0.0, 0.0, 0.58, 1.0)。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## EaseInOut

```TypeScript
EaseInOut = 4
```

表示动画以低速开始和结束，cubic-bezier(0.42, 0.0, 0.58, 1.0)。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## FastOutSlowIn

```TypeScript
FastOutSlowIn = 5
```

标准曲线，cubic-bezier(0.4, 0.0, 0.2, 1.0)。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## LinearOutSlowIn

```TypeScript
LinearOutSlowIn = 6
```

减速曲线，cubic-bezier(0.0, 0.0, 0.2, 1.0)。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## FastOutLinearIn

```TypeScript
FastOutLinearIn = 7
```

加速曲线，cubic-bezier(0.4, 0.0, 1.0, 1.0)。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## ExtremeDeceleration

```TypeScript
ExtremeDeceleration = 8
```

急缓曲线，cubic-bezier(0.0, 0.0, 0.0, 1.0)。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## Sharp

```TypeScript
Sharp = 9
```

锐利曲线，cubic-bezier(0.33, 0.0, 0.67, 1.0)。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## Rhythm

```TypeScript
Rhythm = 10
```

节奏曲线，cubic-bezier(0.7, 0.0, 0.2, 1.0)。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## Smooth

```TypeScript
Smooth = 11
```

平滑曲线，cubic-bezier(0.4, 0.0, 0.4, 1.0)。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## Friction

```TypeScript
Friction = 12
```

阻尼曲线，cubic-bezier(0.2, 0.0, 0.2, 1.0)。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full
