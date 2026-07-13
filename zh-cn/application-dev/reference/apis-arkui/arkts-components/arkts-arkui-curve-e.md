# Curve

插值曲线，动效请参考<!--RP1-->[贝塞尔曲线](../../../../../design/ux-design/animation-attributes.md)<!--RP1End-->。

**起始版本：** 7

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## Linear

```TypeScript
Linear
```

表示动画在整个过程中速度保持一致。

**起始版本：** 7

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## Ease

```TypeScript
Ease
```

表示动画以低速开始，然后加快，在结束前减速，CubicBezier(0.25, 0.1, 0.25, 1.0)。

**起始版本：** 7

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## EaseIn

```TypeScript
EaseIn
```

表示动画以低速开始，CubicBezier(0.42, 0.0, 1.0, 1.0)。

**起始版本：** 7

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## EaseOut

```TypeScript
EaseOut
```

表示动画以低速结束，CubicBezier(0.0, 0.0, 0.58, 1.0)。

**起始版本：** 7

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## EaseInOut

```TypeScript
EaseInOut
```

表示动画以低速开始和结束，CubicBezier(0.42, 0.0, 0.58, 1.0)。

**起始版本：** 7

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## FastOutSlowIn

```TypeScript
FastOutSlowIn
```

标准曲线，CubicBezier(0.4, 0.0, 0.2, 1.0)。

**起始版本：** 7

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## LinearOutSlowIn

```TypeScript
LinearOutSlowIn
```

减速曲线，CubicBezier(0.0, 0.0, 0.2, 1.0)。

**起始版本：** 7

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## FastOutLinearIn

```TypeScript
FastOutLinearIn
```

加速曲线，CubicBezier(0.4, 0.0, 1.0, 1.0)。

**起始版本：** 7

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## ExtremeDeceleration

```TypeScript
ExtremeDeceleration
```

急缓曲线，CubicBezier(0.0, 0.0, 0.0, 1.0)。

**起始版本：** 7

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## Sharp

```TypeScript
Sharp
```

锐利曲线，CubicBezier(0.33, 0.0, 0.67, 1.0)。

**起始版本：** 7

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## Rhythm

```TypeScript
Rhythm
```

节奏曲线，CubicBezier(0.7, 0.0, 0.2, 1.0)。

**起始版本：** 7

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## Smooth

```TypeScript
Smooth
```

平滑曲线，CubicBezier(0.4, 0.0, 0.4, 1.0)。

**起始版本：** 7

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## Friction

```TypeScript
Friction
```

阻尼曲线，CubicBezier(0.2, 0.0, 0.2, 1.0)。

**起始版本：** 7

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

