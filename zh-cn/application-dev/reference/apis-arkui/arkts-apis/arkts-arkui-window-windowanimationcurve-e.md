# WindowAnimationCurve

窗口动画曲线类型。

**起始版本：** 20

<!--Device-window-enum WindowAnimationCurve--><!--Device-window-enum WindowAnimationCurve-End-->

**系统能力：** SystemCapability.Window.SessionManager

## LINEAR

```TypeScript
LINEAR = 0
```

表示动画从头到尾的速度都是相同的。

使用该曲线类型时[WindowAnimationConfig](arkts-arkui-window-windowanimationconfig-i.md)中duration必填。

使用该曲线类型时[WindowAnimationConfig](arkts-arkui-window-windowanimationconfig-i.md)中param选填，且不生效。

**起始版本：** 20

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-WindowAnimationCurve-LINEAR = 0--><!--Device-WindowAnimationCurve-LINEAR = 0-End-->

**系统能力：** SystemCapability.Window.SessionManager

## INTERPOLATION_SPRING

```TypeScript
INTERPOLATION_SPRING = 1
```

表示插值器弹簧曲线，一条从0到1的动画曲线，实际动画值根据曲线进行插值计算。动画时间由曲线参数决定，不受[WindowAnimationConfig](arkts-arkui-window-windowanimationconfig-i.md)中的duration参数控制。

使用该曲线类型时[WindowAnimationConfig](arkts-arkui-window-windowanimationconfig-i.md)中duration选填，且不生效。

使用该曲线类型时[WindowAnimationConfig](arkts-arkui-window-windowanimationconfig-i.md)中param必填。

**起始版本：** 20

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-WindowAnimationCurve-INTERPOLATION_SPRING = 1--><!--Device-WindowAnimationCurve-INTERPOLATION_SPRING = 1-End-->

**系统能力：** SystemCapability.Window.SessionManager

## CUBIC_BEZIER

```TypeScript
CUBIC_BEZIER = 2
```

表示贝塞尔曲线。

使用该曲线类型时[WindowAnimationConfig](arkts-arkui-window-windowanimationconfig-i.md)中的param和duration为必填项。

**起始版本：** 20

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-WindowAnimationCurve-CUBIC_BEZIER = 2--><!--Device-WindowAnimationCurve-CUBIC_BEZIER = 2-End-->

**系统能力：** SystemCapability.Window.SessionManager

