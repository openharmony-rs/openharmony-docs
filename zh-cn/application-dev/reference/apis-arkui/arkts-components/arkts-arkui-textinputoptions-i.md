# TextInputOptions

TextInput初始化参数。

**起始版本：** 7

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## controller

```TypeScript
controller?: TextInputController
```

设置TextInput控制器。

**类型：** TextInputController

**起始版本：** 8

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## placeholder

```TypeScript
placeholder?: ResourceStr
```

设置无输入时的提示文本。

**类型：** ResourceStr

**起始版本：** 7

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## text

```TypeScript
text?: ResourceStr
```

设置输入框当前的文本内容。</br>建议通过onChange事件将状态变量与文本实时绑定，</br>避免组件刷新时TextInput中的文本内容异常。

从API version 10开始，该参数支持[$$](../../../../ui/state-management/arkts-two-way-sync.md)双向绑定变量。

从API version 18开始，该参数支持[!!](../../../../ui/state-management/arkts-new-binding.md#系统组件参数双向绑定)双向绑定变量。

**类型：** ResourceStr

**起始版本：** 7

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

