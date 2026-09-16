# Dimension

```TypeScript
declare type Dimension = PX | VP | FP | LPX | Percentage | Resource
```

长度类型，用于描述尺寸单位。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**卡片能力：** 从API版本23开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

| 类型 | 说明 |
| --- | --- |
| [PX](arkts-arkui-px-t.md) | 需要指定以px像素单位，如'10px'。 |
| [VP](arkts-arkui-vp-t.md) | 需要指定数字或vp像素单位，如10或'10vp'。 |
| [FP](arkts-arkui-fp-t.md) | 需要指定以fp像素单位，如'10fp'。 |
| [LPX](arkts-arkui-lpx-t.md) | 需要指定以lpx像素单位，如'10lpx'。 |
| [Percentage](arkts-arkui-percentage-t.md) | 需要指定以百分比单位，如'10%'。 |
| [Resource](arkts-arkui-resource-t.md) | 资源引用类型，引入系统资源或者应用资源中的尺寸。 |
