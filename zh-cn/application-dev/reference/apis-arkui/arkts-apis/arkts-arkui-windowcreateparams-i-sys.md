# WindowCreateParams

应用启动时的窗口参数配置。

**起始版本：** 20

**系统能力：** SystemCapability.Window.SessionManager

## isWindowLimitsForcible

```TypeScript
isWindowLimitsForcible?: boolean
```

是否覆盖系统窗口尺寸限制。
如果为true，则当前主窗口可以设置超出系统限制的窗口尺寸限制。

**类型：** boolean

**默认值：** false

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Window.SessionManager

**系统接口：** 此接口为系统接口。

## systemAnimationParams

```TypeScript
systemAnimationParams?: StartAnimationSystemParams
```

启动动画配置，仅对全屏应用生效。

不同应用间跳转场景不生效，仍保持系统默认动效。

**类型：** StartAnimationSystemParams

**起始版本：** 20

**系统能力：** SystemCapability.Window.SessionManager

**系统接口：** 此接口为系统接口。

