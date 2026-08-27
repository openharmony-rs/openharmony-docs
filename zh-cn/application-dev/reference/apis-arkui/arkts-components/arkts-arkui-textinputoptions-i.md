# TextInputOptions

TextInput初始化参数。

**起始版本：** 7

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
```

## controller

```TypeScript
controller?: TextInputController
```

设置TextInput控制器。当需要通过控制器调用光标设置、文本选择等方法时传入此参数。不设置时默认无控制器，无法使用控制器相关方法。

**类型：** [TextInputController](arkts-arkui-textinputcontroller-c.md)

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## placeholder

```TypeScript
placeholder?: ResourceStr
```

设置无输入时的提示文本。不设置时默认无提示文本。

**类型：** [ResourceStr](../arkts-apis/arkts-arkui-resourcestr-t.md)

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## text

```TypeScript
text?: ResourceStr
```

设置输入框当前的文本内容。不设置时默认为空字符串。建议通过onChange事件将状态变量与文本实时绑定，避免组件刷新时TextInput中的文本内容异常。从API version 10开始，该参数支持[\$\$](../../../ui/state-management/arkts-two-way-sync.md)双向绑定变量。从API version 18开始，该参数支持[!!](../../../ui/state-management/arkts-new-binding.md#系统组件参数双向绑定)双向绑定变量。

**类型：** [ResourceStr](../arkts-apis/arkts-arkui-resourcestr-t.md)

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full
