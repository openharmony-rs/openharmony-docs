# QRCode

## QRCode

```TypeScript
@ComponentBuilder
export declare function QRCode(
    value: ResourceStr
): QRCodeAttribute
```

创建二维码组件，通过扫描组件显示的二维码图案可以获取二维码中包含的字符串信息。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-unnamed-@ComponentBuilderexport declare function QRCode(    value: ResourceStr): QRCodeAttribute--><!--Device-unnamed-@ComponentBuilderexport declare function QRCode(    value: ResourceStr): QRCodeAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [ResourceStr](../../apis-arkui/arkts-apis/arkts-arkui-resourcestr-t.md) | 是 | 二维码内容字符串。最大支持512个字符，若超出，则截取前512个字符。 &lt;br/&gt;**说明：** &lt;br/&gt;设置为null时与设置字符串“null”效果一致；设置为 undefined时与设置字符串“undefined”效果一致；当传入空字符串时，将生成无效二维码。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| QRCodeAttribute |  |


## QRCode

```TypeScript
@Builder
export declare function QRCode(
    style: CustomBuilderT<QRCodeAttribute>,
): QRCodeAttribute
```

定义QRCode组件。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-unnamed-@Builderexport declare function QRCode(    style: CustomBuilderT<QRCodeAttribute>,): QRCodeAttribute--><!--Device-unnamed-@Builderexport declare function QRCode(    style: CustomBuilderT<QRCodeAttribute>,): QRCodeAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| style | CustomBuilderT&lt;QRCodeAttribute&gt; | 是 | QRCode属性实例。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| QRCodeAttribute |  |

