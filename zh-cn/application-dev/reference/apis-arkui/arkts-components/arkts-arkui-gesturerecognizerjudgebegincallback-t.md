# GestureRecognizerJudgeBeginCallback

```TypeScript
declare type GestureRecognizerJudgeBeginCallback = (event: BaseGestureEvent, current: GestureRecognizer, recognizers: Array<GestureRecognizer>, touchRecognizers?: Array<TouchRecognizer>) => GestureJudgeResult
```

自定义手势识别器判定回调类型。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | BaseGestureEvent | 是 | 当前基础手势事件信息。 |
| current | GestureRecognizer | 是 | 当前即将要响应的识别器对象。 |
| recognizers | Array&lt;GestureRecognizer&gt; | 是 | 响应链上的其他手势识别器对象。 |
| touchRecognizers | Array&lt;TouchRecognizer&gt; | 否 | 响应链上的Touch识别器对象。 默认值为null，表示在当前手势绑定组件及其子孙组件没有可响应的Touch识别器。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| GestureJudgeResult | 手势是否裁决成功的判定结果。 |

