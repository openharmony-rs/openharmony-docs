# Length

```TypeScript
declare type Length = string | number | Resource
```

长度类型，用于描述尺寸单位。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

| 类型 | 说明 |
| --- | --- |
| string | 需要显式指定像素单位，如'10px'，也可设置百分比字符串，如'100%'。<br>**说明：** <br>不指定像素单位时，默认单位vp，如'1 0'，等同于10。 |
| number | 默认单位vp。 |
| [Resource](arkts-arkui-resource-t.md) | 资源引用类型，引入系统资源或者应用资源中的尺寸。 |
