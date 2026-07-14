# QRCode属性/事件

除支持[通用属性](../../../../reference/apis-arkui/arkui-ts/ts-component-general-attributes.md)外，还支持以下属性。

支持[通用事件](../../../../reference/apis-arkui/arkui-ts/ts-component-general-events.md)。

**继承/实现关系：** QRCodeAttribute extends [CommonMethod<QRCodeAttribute>](CommonMethod<QRCodeAttribute>)

**起始版本：** 7

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## backgroundColor

```TypeScript
backgroundColor(value: ResourceColor)
```

设置二维码背景颜色。

**起始版本：** 7

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | ResourceColor | 是 | 二维码背景颜色。<br/>默认值：Color.White <br/>从API version 11开始，默认值改为'#ffffffff'，且不跟随系统深浅色模式切换而修改。 |

## color

```TypeScript
color(value: ResourceColor)
```

设置二维码颜色。

**起始版本：** 7

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | ResourceColor | 是 | 二维码颜色。默认值：'#ff000000'，且不跟随系统深浅色模式切换而修改。<br/> |

## contentOpacity

```TypeScript
contentOpacity(value: number | Resource)
```

设置二维码内容颜色的不透明度。不透明度最小值为0，最大值为1。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | number \| Resource | 是 | 二维码内容颜色的不透明度。<br/>默认值：1<br/>取值范围：[0, 1]，超出取值范围按默认值处理。 |

