# TextAreaOptions

TextArea初始化参数。

**起始版本：** 7

<!--Device-unnamed-declare interface TextAreaOptions--><!--Device-unnamed-declare interface TextAreaOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## controller

```TypeScript
controller?: TextAreaController
```

设置TextArea控制器。

**类型：** TextAreaController

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-TextAreaOptions-controller?: TextAreaController--><!--Device-TextAreaOptions-controller?: TextAreaController-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## placeholder

```TypeScript
placeholder?: ResourceStr
```

设置无输入时的提示文本。输入内容后，提示文本不显示。

仅设置placeholder属性时，手柄依然跟随拖动，手柄松开后光标停留在文字开头位置。

**类型：** ResourceStr

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-TextAreaOptions-placeholder?: ResourceStr--><!--Device-TextAreaOptions-placeholder?: ResourceStr-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## text

```TypeScript
text?: ResourceStr | Bindable<ResourceStr> | Bindable<Resource> | Bindable<string>
```

Sets the current value of TextArea.

**类型：** ResourceStr | Bindable<ResourceStr> | Bindable<Resource> | Bindable<string>

**起始版本：** 20

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-TextAreaOptions-text?: ResourceStr | Bindable<ResourceStr> | Bindable<Resource> | Bindable<string>--><!--Device-TextAreaOptions-text?: ResourceStr | Bindable<ResourceStr> | Bindable<Resource> | Bindable<string>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

