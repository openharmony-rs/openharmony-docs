# CounterV2NumberStyleOptions

CounterV2NumberStyleOptions定义了列表型和紧凑型CounterV2的属性和事件。

继承于[CounterV2InlineStyleOptions](arkts-arkui-counterv2inlinestyleoptions-c.md)。

**继承/实现关系：** CounterV2NumberStyleOptions extends [CounterV2InlineStyleOptions](arkts-arkui-counterv2inlinestyleoptions-c.md)

**起始版本：** 26.0.0

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## label

```TypeScript
label?: ResourceStr
```

设置CounterV2的说明文本。

默认值：' '

值为undefined时，按默认值处理。

**类型：** ResourceStr

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本26.0.0开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## onBlurDecrease

```TypeScript
onBlurDecrease?: VoidCallback
```

当CounterV2组件的"减小按钮"失去焦点时，触发该回调。

默认值：undefined，表示不触发该回调。

值为undefined时，按默认值处理。

**类型：** VoidCallback

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本26.0.0开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## onBlurIncrease

```TypeScript
onBlurIncrease?: VoidCallback
```

当CounterV2组件的"增加按钮"失去焦点时，触发该回调。

默认值：undefined，表示不触发该回调。

值为undefined时，按默认值处理。

**类型：** VoidCallback

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本26.0.0开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## onFocusDecrease

```TypeScript
onFocusDecrease?: VoidCallback
```

当CounterV2组件的"减小按钮"获取焦点时，触发该回调。

默认值：undefined，表示不触发该回调。

值为undefined时，按默认值处理。

**类型：** VoidCallback

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本26.0.0开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## onFocusIncrease

```TypeScript
onFocusIncrease?: VoidCallback
```

当CounterV2组件的"增加按钮"获取焦点时，触发该回调。

默认值：undefined，表示不触发该回调。

值为undefined时，按默认值处理。

**类型：** VoidCallback

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本26.0.0开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

