# CounterV2DateStyleOptions

CounterV2DateStyleOptions定义日期内联型CounterV2的属性和事件。 继承于[CounterV2CommonOptions](arkts-arkui-arkui-advanced-counterv2-counterv2commonoptions-c.md#CounterV2CommonOptions)，包含该接口所有属性。本节仅展示新增属性，继承属性请参见父接口。

**继承/实现关系：** CounterV2DateStyleOptions extends [CounterV2CommonOptions](arkts-arkui-arkui-advanced-counterv2-counterv2commonoptions-c.md#CounterV2CommonOptions)

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**废弃版本：** -1

<!--Device-unnamed-declare class CounterV2DateStyleOptions--><!--Device-unnamed-declare class CounterV2DateStyleOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## day

```TypeScript
day?: int
```

设置日期内联型初始日。 默认值：1 取值范围：[1, 31] 必须为合法日期，如month为2月时，day传入30将视为异常值，按默认值处理。 超出取值范围按默认值处理。 值为undefined时，按默认值处理。

**类型：** int

**默认值：** 1

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-CounterV2DateStyleOptions-day?: int--><!--Device-CounterV2DateStyleOptions-day?: int-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## month

```TypeScript
month?: int
```

设置日期内联型初始月份。 默认值：1 取值范围：[1, 12] 超出取值范围按默认值处理。 值为undefined时，按默认值处理。

**类型：** int

**默认值：** 1

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-CounterV2DateStyleOptions-month?: int--><!--Device-CounterV2DateStyleOptions-month?: int-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## onDateChange

```TypeScript
onDateChange?: OnDateCounterV2ChangeCallback
```

当日期改变时，触发该回调。回调参数date表示当前显示的日期值。 使用场景：当需要在日期变化时执行自定义操作（如更新关联数据、触发业务逻辑、记录日志等）时传入此回调。 默认值：undefined，表示不触发该回调。 值为undefined时，按默认值处理。

**类型：** [OnDateCounterV2ChangeCallback](arkts-arkui-ondatecounterv2changecallback-t.md)

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-CounterV2DateStyleOptions-onDateChange?: OnDateCounterV2ChangeCallback--><!--Device-CounterV2DateStyleOptions-onDateChange?: OnDateCounterV2ChangeCallback-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## year

```TypeScript
year?: int
```

设置日期内联型初始年份。 默认值：1 取值范围：[1, 5000] 超出取值范围按默认值处理。 值为undefined时，按默认值处理。

**类型：** int

**默认值：** 1

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-CounterV2DateStyleOptions-year?: int--><!--Device-CounterV2DateStyleOptions-year?: int-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

