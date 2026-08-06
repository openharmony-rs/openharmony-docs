# PopupTextOptions

设置文本样式。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-unnamed-export interface PopupTextOptions--><!--Device-unnamed-export interface PopupTextOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## fontColor

```TypeScript
fontColor?: ResourceColor
```

设置文本字体颜色。 默认值：\_\_\_INLINE\_CODE\_DESC\_USD\_0\_\_\_

**类型：** ResourceColor

**默认值：** $r('sys.color.ohos_id_color_text_secondary')

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-PopupTextOptions-fontColor?: ResourceColor--><!--Device-PopupTextOptions-fontColor?: ResourceColor-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## fontSize

```TypeScript
fontSize?: number | string | Resource
```

设置文本字体大小。 默认值：\_\_\_INLINE\_CODE\_DESC\_USD\_0\_\_\_ string类型可选值：可以转化为数字的字符串（如'10'）或带长度单位的字符串（如'10px'），不支持设置百分比字符串。 number：取值范围(0,+∞)。

**类型：** number \| string \| Resource

**默认值：** $r('sys.float.ohos_id_text_size_body2')

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-PopupTextOptions-fontSize?: number | string | Resource--><!--Device-PopupTextOptions-fontSize?: number | string | Resource-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## fontWeight

```TypeScript
fontWeight?: number | FontWeight | string
```

设置文本字体粗细。 number类型取值[100,900]，取值间隔为100，默认为400，取值越大，字体越粗。 string类型仅支持number类型取值的字符串形式，例如“400”，以及“bold”、“bolder”、“lighter”、“regular” 、“medium”分别对应FontWeight中相应的枚举值。 默认值：FontWeight.Regular

**类型：** number \| FontWeight \| string

**默认值：** FontWeight.Regular

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-PopupTextOptions-fontWeight?: number | FontWeight | string--><!--Device-PopupTextOptions-fontWeight?: number | FontWeight | string-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## text

```TypeScript
text?: ResourceStr
```

设置文本内容。 **ArkTS模式：** 该接口仅适用于ArkTS-Sta。 **ArkTS-Sta起始版本：** 23

**类型：** ResourceStr

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-PopupTextOptions-text?: ResourceStr--><!--Device-PopupTextOptions-text?: ResourceStr-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

