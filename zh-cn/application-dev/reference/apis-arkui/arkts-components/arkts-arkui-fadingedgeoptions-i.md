# FadingEdgeOptions

fadingEdge属性边缘渐隐参数对象。

**起始版本：** 14

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
```

## fadingEdgeLength

```TypeScript
fadingEdgeLength?: LengthMetrics
```

设置边缘渐隐长度。默认值为32vp，设置小于0的值或undefined或不设置则取默认值。设置的长度超过容器高度的一半时，渐隐长度取容器高度的一半。

**类型：** LengthMetrics

**默认值：** 32vp

**起始版本：** 14

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本14开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full
