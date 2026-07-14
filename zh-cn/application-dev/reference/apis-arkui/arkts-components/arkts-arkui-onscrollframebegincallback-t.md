# OnScrollFrameBeginCallback

```TypeScript
declare type OnScrollFrameBeginCallback = (offset: number, state: ScrollState) => OnScrollFrameBeginHandlerResult
```

Scroll每帧滚动前触发的回调。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本18开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| offset | number | 是 | 即将发生的滑动量，单位vp。 |
| state | ScrollState | 是 | 当前滑动状态。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| OnScrollFrameBeginHandlerResult | data - 返回实际滑动量。 |

