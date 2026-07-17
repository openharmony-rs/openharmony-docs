# AlertDialogButtonBaseOptions

警告弹窗中按钮的样式。

> **说明：**  
>  
> 为规范匿名对象的定义，API 18版本修改了此处的元素定义。其中，保留了历史匿名对象的起始版本信息，会出现外层元素@since版本号高于内层元素版本号的情况，但这不影响接口的使用。

**起始版本：** 18

<!--Device-unnamed-declare interface AlertDialogButtonBaseOptions--><!--Device-unnamed-declare interface AlertDialogButtonBaseOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## action

```TypeScript
action: VoidCallback
```

Button选中时的回调。

**类型：** VoidCallback

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-AlertDialogButtonBaseOptions-action: VoidCallback--><!--Device-AlertDialogButtonBaseOptions-action: VoidCallback-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## backgroundColor

```TypeScript
backgroundColor?: ResourceColor
```

Button背景颜色。

**类型：** ResourceColor

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-AlertDialogButtonBaseOptions-backgroundColor?: ResourceColor--><!--Device-AlertDialogButtonBaseOptions-backgroundColor?: ResourceColor-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## defaultFocus

```TypeScript
defaultFocus?: boolean
```

设置Button是否是默认焦点，默认值false。值为true表示Button为默认焦点，值为false表示Button不为默认焦点。

**类型：** boolean

**默认值：** false

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-AlertDialogButtonBaseOptions-defaultFocus?: boolean--><!--Device-AlertDialogButtonBaseOptions-defaultFocus?: boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## enabled

```TypeScript
enabled?: boolean
```

点击Button是否响应，默认值true。

值为true时，Button可以响应。值为false时，Button不可以响应。

**类型：** boolean

**默认值：** true

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-AlertDialogButtonBaseOptions-enabled?: boolean--><!--Device-AlertDialogButtonBaseOptions-enabled?: boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## fontColor

```TypeScript
fontColor?: ResourceColor
```

Button的文本颜色。

**类型：** ResourceColor

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-AlertDialogButtonBaseOptions-fontColor?: ResourceColor--><!--Device-AlertDialogButtonBaseOptions-fontColor?: ResourceColor-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## style

```TypeScript
style?: DialogButtonStyle
```

设置Button的风格样式，默认值DialogButtonStyle.DEFAULT。

**类型：** DialogButtonStyle

**默认值：** -

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-AlertDialogButtonBaseOptions-style?: DialogButtonStyle--><!--Device-AlertDialogButtonBaseOptions-style?: DialogButtonStyle-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## value

```TypeScript
value: ResourceStr
```

Button的文本内容，若值为null，则该按钮不显示。

**类型：** ResourceStr

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-AlertDialogButtonBaseOptions-value: ResourceStr--><!--Device-AlertDialogButtonBaseOptions-value: ResourceStr-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

