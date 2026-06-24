# AnimationOptions

拖拽相关的动效参数。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## curve

```TypeScript
curve?: Curve | ICurve
```

设置动画曲线。

默认值：Curve.EaseInOut

**类型：** Curve | ICurve

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## duration

```TypeScript
duration?: number
```

动画持续时间，单位为毫秒。

默认值：1000

**说明：**

- 设置小于0的值时按0处理。

- 设置浮点型类型的值时，向下取整。例如，设置值为1.2，按照1处理。

**类型：** number

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

