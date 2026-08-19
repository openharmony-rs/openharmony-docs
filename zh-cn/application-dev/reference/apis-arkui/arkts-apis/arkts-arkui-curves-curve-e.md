# Curve

插值曲线和动效请参考<!--RP1-->[贝塞尔曲线](../../../../design/ux-design/animation-attributes.md)<!--RP1End-->。 | 名称 | 值 | 说明 | | ------------------- | -- | ------------------------------ | | Linear | 0 | 表示动画从头到尾的速度都是相同的。 | | Ease | 1 | 表示动画以低速开始，然后加快，在结束前变慢，cubic-bezier(0.25, 0.1, 0.25, 1.0)。 | | EaseIn | 2 | 表示动画以低速开始，cubic-bezier(0.42, 0.0, 1.0, 1.0)。 | | EaseOut | 3 | 表示动画以低速结束，cubic-bezier(0.0, 0.0, 0.58, 1.0)。 | | EaseInOut | 4 | 表示动画以低速开始和结束，cubic-bezier(0.42, 0.0, 0.58, 1.0)。 | | FastOutSlowIn | 5 | 标准曲线，cubic-bezier(0.4, 0.0, 0.2, 1.0)。 | | LinearOutSlowIn | 6 | 减速曲线，cubic-bezier(0.0, 0.0, 0.2, 1.0)。 | | FastOutLinearIn | 7 | 加速曲线，cubic-bezier(0.4, 0.0, 1.0, 1.0)。 | | ExtremeDeceleration | 8 | 急缓曲线，cubic-bezier(0.0, 0.0, 0.0, 1.0)。 | | Sharp | 9 | 锐利曲线，cubic-bezier(0.33, 0.0, 0.67, 1.0)。 | | Rhythm | 10 | 节奏曲线，cubic-bezier(0.7, 0.0, 0.2, 1.0)。 | | Smooth | 11 | 平滑曲线，cubic-bezier(0.4, 0.0, 0.4, 1.0)。 | | Friction | 12 | 阻尼曲线，cubic-bezier(0.2, 0.0, 0.2, 1.0)。 |

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-curves-export enum Curve--><!--Device-curves-export enum Curve-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## Linear

```TypeScript
Linear
```

Linear. Indicates that the animation has the same velocity from start to finish.

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Curve-Linear--><!--Device-Curve-Linear-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## Ease

```TypeScript
Ease
```

Ease. Indicates that the animation starts at a low speed, then speeds up, and slows down before the end, CubicBezier(0.25, 0.1, 0.25, 1.0).

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Curve-Ease--><!--Device-Curve-Ease-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## EaseIn

```TypeScript
EaseIn
```

EaseIn. Indicates that the animation starts at a low speed, Cubic Bezier (0.42, 0.0, 1.0, 1.0).

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Curve-EaseIn--><!--Device-Curve-EaseIn-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## EaseOut

```TypeScript
EaseOut
```

EaseOut. Indicates that the animation ends at low speed, CubicBezier (0.0, 0.0, 0.58, 1.0).

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Curve-EaseOut--><!--Device-Curve-EaseOut-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## EaseInOut

```TypeScript
EaseInOut
```

EaseInOut. Indicates that the animation starts and ends at low speed, CubicBezier (0.42, 0.0, 0.58, 1.0).

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Curve-EaseInOut--><!--Device-Curve-EaseInOut-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## FastOutSlowIn

```TypeScript
FastOutSlowIn
```

FastOutSlowIn. Standard curve, cubic-bezier (0.4, 0.0, 0.2, 1.0).

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Curve-FastOutSlowIn--><!--Device-Curve-FastOutSlowIn-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## LinearOutSlowIn

```TypeScript
LinearOutSlowIn
```

LinearOutSlowIn. Deceleration curve, cubic-bezier (0.0, 0.0, 0.2, 1.0).

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Curve-LinearOutSlowIn--><!--Device-Curve-LinearOutSlowIn-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## FastOutLinearIn

```TypeScript
FastOutLinearIn
```

FastOutLinearIn. Acceleration curve, cubic-bezier (0.4, 0.0, 1.0, 1.0).

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Curve-FastOutLinearIn--><!--Device-Curve-FastOutLinearIn-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## ExtremeDeceleration

```TypeScript
ExtremeDeceleration
```

ExtremeDeceleration. Abrupt curve, cubic-bezier (0.0, 0.0, 0.0, 1.0).

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Curve-ExtremeDeceleration--><!--Device-Curve-ExtremeDeceleration-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## Sharp

```TypeScript
Sharp
```

Sharp. Sharp curves, cubic-bezier (0.33, 0.0, 0.67, 1.0).

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Curve-Sharp--><!--Device-Curve-Sharp-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## Rhythm

```TypeScript
Rhythm
```

Rhythm. Rhythmic curve, cubic-bezier (0.7, 0.0, 0.2, 1.0).

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Curve-Rhythm--><!--Device-Curve-Rhythm-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## Smooth

```TypeScript
Smooth
```

Smooth. Smooth curves, cubic-bezier (0.4, 0.0, 0.4, 1.0).

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Curve-Smooth--><!--Device-Curve-Smooth-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## Friction

```TypeScript
Friction
```

Friction. Damping curves, CubicBezier (0.2, 0.0, 0.2, 1.0).

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Curve-Friction--><!--Device-Curve-Friction-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

