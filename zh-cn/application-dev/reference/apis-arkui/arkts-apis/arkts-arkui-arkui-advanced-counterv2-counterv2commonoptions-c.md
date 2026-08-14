# CounterV2CommonOptions

CounterV2CommonOptions定义了CounterV2的共通属性和事件。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**废弃版本：** -1

<!--Device-unnamed-declare class CounterV2CommonOptions--><!--Device-unnamed-declare class CounterV2CommonOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## focusable

```TypeScript
focusable?: boolean
```

设置CounterV2是否可获焦。 **说明：** 该属性对列表型和紧凑型CounterV2生效。对数值内联型和日期内联型CounterV2不生效。 默认值：true true：CounterV2可获焦；false：CounterV2不可获焦。 值为undefined时，按默认值处理。

**类型：** boolean

**默认值：** true

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-CounterV2CommonOptions-focusable?: boolean--><!--Device-CounterV2CommonOptions-focusable?: boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## onHoverDecrease

```TypeScript
onHoverDecrease?: OnCounterV2HoverCallback
```

鼠标进入或退出CounterV2组件的“减少按钮”时，触发该回调。 使用场景：当需要在鼠标悬浮“减少按钮”时执行自定义操作（如改变按钮样式、显示提示信息等）时传入此回调。 **说明：** 该属性对列表型、紧凑型和数值内联型CounterV2生效。对日期内联型CounterV2不生效。 默认值：undefined，表示不触发该回调。 值为undefined时，按默认值处理。

**类型：** [OnCounterV2HoverCallback](arkts-arkui-oncounterv2hovercallback-t.md)

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-CounterV2CommonOptions-onHoverDecrease?: OnCounterV2HoverCallback--><!--Device-CounterV2CommonOptions-onHoverDecrease?: OnCounterV2HoverCallback-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## onHoverIncrease

```TypeScript
onHoverIncrease?: OnCounterV2HoverCallback
```

鼠标进入或退出CounterV2组件的“增加按钮”时，触发该回调。 使用场景：当需要在鼠标悬浮“增加按钮”时执行自定义操作（如改变按钮样式、显示提示信息等）时传入此回调。 **说明：** 该属性对列表型、紧凑型和数值内联型CounterV2生效。对日期内联型CounterV2不生效。 默认值：undefined，表示不触发该回调。 值为undefined时，按默认值处理。

**类型：** [OnCounterV2HoverCallback](arkts-arkui-oncounterv2hovercallback-t.md)

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-CounterV2CommonOptions-onHoverIncrease?: OnCounterV2HoverCallback--><!--Device-CounterV2CommonOptions-onHoverIncrease?: OnCounterV2HoverCallback-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## step

```TypeScript
step?: int
```

设置CounterV2的步长。 **说明：** 该属性对列表型、紧凑型和数值内联型CounterV2生效。对日期内联型CounterV2不生效。 取值范围：大于等于1的整数。 默认值：1 超出取值范围按默认值处理。 值为undefined时，按默认值处理。

**类型：** int

**默认值：** 1

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-CounterV2CommonOptions-step?: int--><!--Device-CounterV2CommonOptions-step?: int-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

