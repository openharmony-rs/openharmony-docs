# CounterV2InlineStyleOptions

CounterV2InlineStyleOptions定义了数值内联型CounterV2的属性和事件。 继承于[CounterV2CommonOptions](arkts-arkui-arkui-advanced-counterv2-counterv2commonoptions-c.md#CounterV2CommonOptions)，包含该接口所有属性。本节仅展示新增属性，继承属性请参见父接口。 > **说明：** > > 1. min应小于等于max。若min大于max，则按max处理。

**继承/实现关系：** CounterV2InlineStyleOptions extends [CounterV2CommonOptions](arkts-arkui-arkui-advanced-counterv2-counterv2commonoptions-c.md#CounterV2CommonOptions)

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**废弃版本：** -1

<!--Device-unnamed-declare class CounterV2InlineStyleOptions--><!--Device-unnamed-declare class CounterV2InlineStyleOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## max

```TypeScript
max?: int
```

设置CounterV2的最大值。 默认值：999 取值范围：[min, +∞) 超出取值范围时（即设置值小于min），按min处理。 值为undefined时，按默认值处理。

**类型：** int

**默认值：** 999

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-CounterV2InlineStyleOptions-max?: int--><!--Device-CounterV2InlineStyleOptions-max?: int-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## min

```TypeScript
min?: int
```

设置CounterV2的最小值。 默认值：0 取值范围：(-∞, max] 超出取值范围时（即设置值大于max），按max处理。 值为undefined时，按默认值处理。

**类型：** int

**默认值：** 0

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-CounterV2InlineStyleOptions-min?: int--><!--Device-CounterV2InlineStyleOptions-min?: int-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## onChange

```TypeScript
onChange?: OnInlineCounterV2Change
```

数值改变时，触发该回调。回调参数value表示当前显示的数值。 使用场景：当需要在数值变化时执行自定义操作（如更新关联数据、触发业务逻辑、记录日志等）时传入此回调。 默认值：undefined，表示数值改变时不触发该回调。 值为undefined时，按默认值处理。

**类型：** [OnInlineCounterV2Change](arkts-arkui-oninlinecounterv2change-t.md)

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-CounterV2InlineStyleOptions-onChange?: OnInlineCounterV2Change--><!--Device-CounterV2InlineStyleOptions-onChange?: OnInlineCounterV2Change-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## textWidth

```TypeScript
textWidth?: double
```

设置数值文本的宽度。 默认值：自适应文本宽度。 取值范围：[0, +∞) 单位：vp 超出取值范围时（即设置值小于0），按0处理。 值为undefined时，按默认值处理。

**类型：** double

**默认值：** undefined

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-CounterV2InlineStyleOptions-textWidth?: double--><!--Device-CounterV2InlineStyleOptions-textWidth?: double-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## value

```TypeScript
value?: int
```

设置CounterV2的初始值。 默认值：0 有效值范围：[min, max]，其中min和max分别对应CounterV2的最小值和最大值。 值为undefined时，按默认值处理。 边界处理：若value小于min则按min处理，若value大于max则按max处理。

**类型：** int

**默认值：** 0

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-CounterV2InlineStyleOptions-value?: int--><!--Device-CounterV2InlineStyleOptions-value?: int-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

