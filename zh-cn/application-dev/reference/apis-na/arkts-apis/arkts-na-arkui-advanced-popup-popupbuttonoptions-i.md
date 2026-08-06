# PopupButtonOptions

PopupButtonOptions定义按钮的相关属性和事件。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-unnamed-export interface PopupButtonOptions--><!--Device-unnamed-export interface PopupButtonOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## action

```TypeScript
action?: VoidCallback
```

设置按钮click回调。 默认不执行任何操作。

**类型：** VoidCallback

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-PopupButtonOptions-action?: VoidCallback--><!--Device-PopupButtonOptions-action?: VoidCallback-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## fontColor

```TypeScript
fontColor?: ResourceColor
```

设置按钮文本字体颜色。 默认值：\_\_\_INLINE\_CODE\_DESC\_USD\_0\_\_\_

**类型：** ResourceColor

**默认值：** $r('sys.color.ohos_id_color_text_primary_activated')

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-PopupButtonOptions-fontColor?: ResourceColor--><!--Device-PopupButtonOptions-fontColor?: ResourceColor-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## fontSize

```TypeScript
fontSize?: number | string | Resource
```

设置按钮文本字体大小。 默认值：\_\_\_INLINE\_CODE\_DESC\_USD\_0\_\_\_ string类型可选值：可以转化为数字的字符串（如'10'）或带长度单位的字符串（如'10px'），不支持设置百分比字符串。 设置值为异常值时取默认值。

**类型：** number \| string \| Resource

**默认值：** $r('sys.float.ohos_id_text_size_button2')

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-PopupButtonOptions-fontSize?: number | string | Resource--><!--Device-PopupButtonOptions-fontSize?: number | string | Resource-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## text

```TypeScript
text?: ResourceStr
```

设置按钮内容。 **ArkTS模式：** 该接口仅适用于ArkTS-Sta。 **ArkTS-Sta起始版本：** 23

**类型：** ResourceStr

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-PopupButtonOptions-text?: ResourceStr--><!--Device-PopupButtonOptions-text?: ResourceStr-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

