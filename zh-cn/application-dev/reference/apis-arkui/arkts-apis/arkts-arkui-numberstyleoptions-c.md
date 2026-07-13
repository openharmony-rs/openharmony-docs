# NumberStyleOptions

NumberStyleOptions定义了列表型和紧凑型Counter的属性和事件。

继承于[InlineStyleOptions](arkts-arkui-inlinestyleoptions-c.md)。

**继承/实现关系：** NumberStyleOptions extends [InlineStyleOptions](arkts-arkui-inlinestyleoptions-c.md)

**起始版本：** 11

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## label

```TypeScript
label?: ResourceStr
```

设置Counter的说明文本。

默认值：' '

值为undefined时，按默认值处理。

**类型：** ResourceStr

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## onBlurDecrease

```TypeScript
onBlurDecrease?: () => void
```

当前Counter组件的减小按钮失去焦点时触发的回调。

默认值：不触发减少按钮失去焦点时的回调。

值为undefined时，按默认值处理。

**类型：** () => void

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## onBlurIncrease

```TypeScript
onBlurIncrease?: () => void
```

当前Counter组件的增加按钮失去焦点时触发的回调。

默认值：不触发增加按钮失去焦点时的回调。

值为undefined时，按默认值处理。

**类型：** () => void

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## onFocusDecrease

```TypeScript
onFocusDecrease?: () => void
```

当前Counter组件的减小按钮获取焦点时触发的回调。

默认值：不触发减少按钮获取焦点时的回调。

值为undefined时，按默认值处理。

**类型：** () => void

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## onFocusIncrease

```TypeScript
onFocusIncrease?: () => void
```

当前Counter组件的增加按钮获取焦点时触发的回调。

默认值：不触发增加按钮获取焦点时的回调。

值为undefined时，按默认值处理。

**类型：** () => void

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

