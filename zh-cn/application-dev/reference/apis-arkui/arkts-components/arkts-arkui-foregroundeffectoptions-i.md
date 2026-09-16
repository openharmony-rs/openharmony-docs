# ForegroundEffectOptions

前景效果参数，用于配置组件前景的模糊半径，控制前景内容的模糊程度。

**起始版本：** 12

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## radius

```TypeScript
radius: number
```

模糊半径，设置后组件前景呈现模糊效果，数值越大模糊程度越高。取值范围：[0, +∞)，0表示不产生模糊效果。传入负数时自动修正为0。仅在组件范围内生效，与backgroundBlur等效果类接口连用时超出组件范围的效果无法生效。

**类型：** number

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full
