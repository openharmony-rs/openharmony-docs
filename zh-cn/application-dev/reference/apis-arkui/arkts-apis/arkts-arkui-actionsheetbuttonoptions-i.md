# ActionSheetButtonOptions

弹窗中按钮的样式。
> **说明：**  
>  
> 为规范匿名对象的定义，API 18版本修改了此处的元素定义。其中，保留了历史匿名对象的起始版本信息，会出现外层元素@since版本号高于内层元素版本号的情况，但这不影响接口的使用。

**起始版本：** 18

<!--Device-unnamed-interface ActionSheetButtonOptions--><!--Device-unnamed-interface ActionSheetButtonOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## action

```TypeScript
action: VoidCallback
```

Button选中时的回调。

**类型：** VoidCallback

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-ActionSheetButtonOptions-action: VoidCallback--><!--Device-ActionSheetButtonOptions-action: VoidCallback-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## defaultFocus

```TypeScript
defaultFocus?: boolean
```

设置Button是否是默认焦点，true表示Button是默认焦点，false表示Button不是默认焦点。

默认值：false

**类型：** boolean

**默认值：** false

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-ActionSheetButtonOptions-defaultFocus?: boolean--><!--Device-ActionSheetButtonOptions-defaultFocus?: boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## enabled

```TypeScript
enabled?: boolean
```

点击Button是否响应，true表示Button可以响应，false表示Button不可以响应。

默认值：true

**类型：** boolean

**默认值：** true

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-ActionSheetButtonOptions-enabled?: boolean--><!--Device-ActionSheetButtonOptions-enabled?: boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## style

```TypeScript
style?: DialogButtonStyle
```

设置Button的风格样式。

默认值：DialogButtonStyle.DEFAULT

**类型：** DialogButtonStyle

**默认值：** DialogButtonStyle.DEFAULT

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-ActionSheetButtonOptions-style?: DialogButtonStyle--><!--Device-ActionSheetButtonOptions-style?: DialogButtonStyle-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## value

```TypeScript
value: string | Resource
```

Button文本内容。

当文本内容过长无法显示时，用省略号代替未显示的部分。

**类型：** string \| Resource

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-ActionSheetButtonOptions-value: string | Resource--><!--Device-ActionSheetButtonOptions-value: string | Resource-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

