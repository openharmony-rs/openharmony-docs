# OnInlineCounterV2Change

```TypeScript
export type OnInlineCounterV2Change = (value: int) => void
```

定义数值内联型CounterV2的值变化回调类型。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-unnamed-export type OnInlineCounterV2Change = (value: int) => void--><!--Device-unnamed-export type OnInlineCounterV2Change = (value: int) => void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | int | 是 | 当前显示的数值。 <br>取值范围：[min, max]，其中min和max分别对应CounterV2的最小值和最大值。 |

