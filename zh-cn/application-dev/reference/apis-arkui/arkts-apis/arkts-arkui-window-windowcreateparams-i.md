# WindowCreateParams

应用启动时的窗口参数配置。

**起始版本：** 20

**系统能力：** SystemCapability.Window.SessionManager

## animationParams

```TypeScript
animationParams?: StartAnimationParams
```

The params of start animation

**类型：** StartAnimationParams

**起始版本：** 20

**系统能力：** SystemCapability.Window.SessionManager

## needAnimation

```TypeScript
needAnimation?: boolean
```

窗口拉起时是否需要动画

默认跟随产品配置，例如PC设备上拉起主窗默认有动画，Phone上拉起子窗默认无动画。当产品支持配置，跟随开发者设置的值。

**类型：** boolean

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Window.SessionManager

