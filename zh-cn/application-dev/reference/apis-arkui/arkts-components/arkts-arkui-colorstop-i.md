# ColorStop

颜色断点类型，用于描述渐进色颜色断点。

**起始版本：** 10

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## color

```TypeScript
color: ResourceColor
```

渐变色断点处的颜色值。

**类型：** ResourceColor

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## offset

```TypeScript
offset: Length
```

渐变色断点（0~1之间的比例值，若数据值小于0则置为0，若数据值大于1则置为1）。

**说明：**

若传入字符串类型且内容为数字，则转换为对应的数值。

例如'10vp'转换为10，'10%'转换为0.1。

**类型：** Length

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

