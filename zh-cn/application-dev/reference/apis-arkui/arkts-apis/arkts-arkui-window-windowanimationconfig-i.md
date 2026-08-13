# WindowAnimationConfig

窗口动画参数配置。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-window-interface WindowAnimationConfig--><!--Device-window-interface WindowAnimationConfig-End-->

**系统能力：** SystemCapability.Window.SessionManager

## curve

```TypeScript
curve: WindowAnimationCurve
```

动画曲线类型。

**类型：** [WindowAnimationCurve](arkts-arkui-window-windowanimationcurve-e.md)

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-WindowAnimationConfig-curve: WindowAnimationCurve--><!--Device-WindowAnimationConfig-curve: WindowAnimationCurve-End-->

**系统能力：** SystemCapability.Window.SessionManager

## duration

```TypeScript
duration?: long
```

动画播放的时长，单位毫秒（ms）。 默认值：0，最大值：3000。 根据动画曲线类型决定是否必填。

**类型：** long

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-WindowAnimationConfig-duration?: long--><!--Device-WindowAnimationConfig-duration?: long-End-->

**系统能力：** SystemCapability.Window.SessionManager

## param

```TypeScript
param?: WindowAnimationCurveParam
```

动画曲线参数，根据动画曲线类型决定是否必填。

**类型：** [WindowAnimationCurveParam](arkts-arkui-windowanimationcurveparam-t.md)

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-WindowAnimationConfig-param?: WindowAnimationCurveParam--><!--Device-WindowAnimationConfig-param?: WindowAnimationCurveParam-End-->

**系统能力：** SystemCapability.Window.SessionManager

