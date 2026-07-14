# TransitionAnimation

窗口转场动画配置。

**起始版本：** 20

**系统能力：** SystemCapability.Window.SessionManager

## config

```TypeScript
config: WindowAnimationConfig
```

本次转场动画配置。

**类型：** WindowAnimationConfig

**起始版本：** 20

**元服务API：** 从API版本20开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Window.SessionManager

## opacity

```TypeScript
opacity?: number
```

不透明度，转场动画作用的窗口属性，值为0时窗口完全透明，默认值为1.0。当动画类型为WindowTransitionType.DESTROY时，代表动画终点的不透明度。取值范围0~1.0，在动画结束时恢复为1.0。

**类型：** number

**起始版本：** 20

**元服务API：** 从API版本20开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Window.SessionManager

