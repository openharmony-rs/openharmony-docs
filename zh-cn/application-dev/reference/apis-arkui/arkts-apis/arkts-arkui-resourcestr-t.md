# ResourceStr

```TypeScript
declare type ResourceStr = string | Resource
```

字符串类型，用于描述字符串入参可以使用的类型。

**起始版本：** 7

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

| 类型 | 说明 |
| --- | --- |
| string | 字符串类型。 |
| [Resource](arkts-arkui-resource-t.md) | 资源引用类型，引入系统资源或者应用资源中的字符串。 |
