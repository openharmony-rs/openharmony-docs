# SliderTriggerChangeCallback

```TypeScript
declare type SliderTriggerChangeCallback = (value: number, mode: SliderChangeMode) => void
```

定义SliderConfiguration中使用的回调类型。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | number | 是 | 设置当前的进度值。<br/>取值范围：[[min](arkts-arkui-slider-slideroptions-i.md#SliderOptions)-[max](arkts-arkui-slider-slideroptions-i.md#SliderOptions)] |
| mode | SliderChangeMode | 是 | 设置事件触发的相关状态值。 |

