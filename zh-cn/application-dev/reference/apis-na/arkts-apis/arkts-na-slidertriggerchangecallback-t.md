# SliderTriggerChangeCallback

```TypeScript
export type SliderTriggerChangeCallback = (value: double, mode: SliderChangeMode) => void
```

定义SliderConfiguration中使用的回调类型。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-unnamed-export type SliderTriggerChangeCallback = (value: double, mode: SliderChangeMode) => void--><!--Device-unnamed-export type SliderTriggerChangeCallback = (value: double, mode: SliderChangeMode) => void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | double | 是 | 设置当前的进度值。<br/>取值范围：[[min](arkts-na-slider-slideroptions-i.md)-[max](arkts-na-slider-slideroptions-i.md)] |
| mode | [SliderChangeMode](arkts-na-slider-sliderchangemode-e.md) | 是 | 设置事件触发的相关状态值。 |

