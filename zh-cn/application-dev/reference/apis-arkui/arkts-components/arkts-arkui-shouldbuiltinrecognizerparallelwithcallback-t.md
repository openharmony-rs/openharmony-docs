# ShouldBuiltInRecognizerParallelWithCallback

```TypeScript
declare type ShouldBuiltInRecognizerParallelWithCallback = (current: GestureRecognizer, others: Array<GestureRecognizer>) => GestureRecognizer
```

系统内置手势与响应链上其他组件的手势设置并行关系的回调事件类型。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| current | GestureRecognizer | 是 | 当前组件的系统内置手势识别器，当前版本只提供内置的[GestureType](arkts-arkui-gesturetype-e.md).PAN_GESTURE类型的手势识别器。 |
| others | Array&lt;GestureRecognizer&gt; | 是 | 响应链上更高优先级的其他组件相同类别的手势识别器。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| GestureRecognizer | 与current识别器绑定并行关系的某个手势识别器。 |

