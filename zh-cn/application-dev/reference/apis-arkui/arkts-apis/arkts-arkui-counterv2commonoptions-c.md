# CounterV2CommonOptions

CounterV2CommonOptions定义了CounterV2的共通属性和事件。

**起始版本：** 26.0.0

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## focusable

```TypeScript
focusable?: boolean
```

设置CounterV2是否可获焦。

**说明：**

该属性对列表型和紧凑型CounterV2生效。

默认值：true

true：CounterV2可获焦；false：CounterV2不可获焦。

值为undefined时，按默认值处理。

**类型：** boolean

**默认值：** true

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本26.0.0开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## onHoverDecrease

```TypeScript
onHoverDecrease?: OnCounterV2HoverCallback
```

鼠标进入或退出CounterV2组件的"减小按钮"时，触发该回调。

默认值：undefined，表示不触发该回调。

值为undefined时，按默认值处理。

**类型：** OnCounterV2HoverCallback

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本26.0.0开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## onHoverIncrease

```TypeScript
onHoverIncrease?: OnCounterV2HoverCallback
```

鼠标进入或退出CounterV2组件的"增加按钮"时，触发该回调。

默认值：undefined，表示不触发该回调。

值为undefined时，按默认值处理。

**类型：** OnCounterV2HoverCallback

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本26.0.0开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## step

```TypeScript
step?: number
```

设置CounterV2的步长。

取值范围：大于等于1的整数。

默认值：1

超出取值范围按默认值处理。

**类型：** number

**默认值：** 1

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本26.0.0开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

