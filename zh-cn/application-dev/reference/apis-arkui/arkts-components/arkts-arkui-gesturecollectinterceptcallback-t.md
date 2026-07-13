# GestureCollectInterceptCallback

```TypeScript
declare type GestureCollectInterceptCallback = (recognizers: Array<GestureRecognizer>,
   touchRecognizers?: Array<TouchRecognizer>) => GestureCollectIntervention
```

定义在[onGestureCollectIntercept](arkts-arkui-commonmethod-c.md#ongesturecollectintercept-1)中使用的回调类型。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本26.0.0开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| recognizers | Array&lt;GestureRecognizer&gt; | 是 | 响应链上组件的手势识别器对象。 |
| touchRecognizers | Array&lt;TouchRecognizer&gt; | 否 | 响应链上组件的触摸识别器对象。<br/>默认值为null。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| GestureCollectIntervention | 手势收集干预结果。 |

