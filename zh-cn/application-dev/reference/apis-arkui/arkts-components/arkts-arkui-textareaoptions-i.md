# TextAreaOptions

TextArea初始化参数。

**起始版本：** 7

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为7。

**废弃版本：** -1

<!--Device-unnamed-declare interface TextAreaOptions--><!--Device-unnamed-declare interface TextAreaOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## controller

```TypeScript
controller?: TextAreaController
```

设置TextArea控制器。不设置时，组件使用内部默认控制器，但无法调用控制器相关方法。

**类型：** [TextAreaController](arkts-arkui-textareacontroller-c.md)

**起始版本：** 8

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为8。

**废弃版本：** -1

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-TextAreaOptions-controller?: TextAreaController--><!--Device-TextAreaOptions-controller?: TextAreaController-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## placeholder

```TypeScript
placeholder?: ResourceStr
```

设置无输入时的提示文本。输入内容后，提示文本不显示。 仅设置placeholder属性时，手柄依然跟随拖动，手柄松开后光标停留在文字开头位置。 默认值：空字符串，不设置时不显示提示文本。

**类型：** ResourceStr

**起始版本：** 7

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为7。

**废弃版本：** -1

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-TextAreaOptions-placeholder?: ResourceStr--><!--Device-TextAreaOptions-placeholder?: ResourceStr-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## text

```TypeScript
text?: ResourceStr
```

设置输入框当前的文本内容。默认值：空字符串。 建议通过onChange事件将状态变量与文本实时绑定， 避免组件刷新时TextArea中的文本内容异常。 从API version 10开始，该参数支持[\$\$](../../../ui/state-management/arkts-two-way-sync.md)双向绑定变量。 从API version 18开始，该参数支持[!!](../../../ui/state-management/arkts-new-binding.md#系统组件参数双向绑定)双向绑定变量。

**类型：** ResourceStr

**起始版本：** 7

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为7。

**废弃版本：** -1

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-TextAreaOptions-text?: ResourceStr--><!--Device-TextAreaOptions-text?: ResourceStr-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

