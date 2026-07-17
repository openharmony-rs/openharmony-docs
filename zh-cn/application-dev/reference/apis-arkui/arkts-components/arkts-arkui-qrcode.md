# QRCode

用于显示单个二维码的组件。

> **说明：**

> - 二维码组件的像素点数量与内容有关，组件尺寸过小可能导致内容无法展示，此时需要适当调整组件尺寸。
>

## 子组件

无

## QRCode

```TypeScript
QRCode(value: ResourceStr)
```

创建二维码组件，通过扫描组件显示的二维码图案可以获取二维码中包含的字符串信息。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

<!--Device-QRCodeInterface-(value: ResourceStr): QRCodeAttribute--><!--Device-QRCodeInterface-(value: ResourceStr): QRCodeAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数:**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | ResourceStr | 是 | 二维码内容字符串。最大支持512个字符，若超出，则截取前512个字符。 <br>从API version 20开始，支持Resource类型。 <br/>**说明：**<br/>设置为null时与设置字符串“null”效果一致；设置为undefined时与设置字符串“undefined”效果一致；当传入空字符串时，将生成无效二维码。 |

## 汇总

