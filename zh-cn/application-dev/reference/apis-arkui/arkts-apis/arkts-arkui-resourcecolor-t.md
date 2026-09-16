# ResourceColor

```TypeScript
declare type ResourceColor = Color | number | string | Resource
```

颜色类型，用于描述资源颜色类型。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

| 类型 | 说明 |
| --- | --- |
| [Color](arkts-arkui-color-e.md) | 颜色枚举值。 |
| number | HEX格式颜色，支持rgb或者argb。示例：0xffffff，0xffff0000。number无法识别传入位数，格式选择依据值的大小，例如0x00ffffff作rgb格式解析。 |
| string | 支持rgb、rgba或者argb的格式颜色。<br>rgb格式颜色示例：'#ffffff'、'rgb(255, 100, 255)'。<br>rgba格式颜色示例：'rgba(25 5, 100, 255, 0.5)'。<br>argb格式颜色示例：'#ff000000'。 |
| [Resource](arkts-arkui-resource-t.md) | 使用引入资源的方式，引入系统资源或者应用资源中的颜色。 |
