# ForegroundBlur

设置前景模糊效果，支持通过模糊半径控制模糊程度。

**起始版本：** 26.0.0

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## radius

```TypeScript
radius: number
```

模糊半径。单位：px取值范围为[0, +∞)，默认值为0，负数、NaN和Infinity按默认值处理。值越大前景模糊效果越明显，为0时不模糊。

**类型：** number

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full
