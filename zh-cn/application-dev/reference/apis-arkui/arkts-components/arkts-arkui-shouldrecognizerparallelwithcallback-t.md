# ShouldRecognizerParallelWithCallback

```TypeScript
declare type ShouldRecognizerParallelWithCallback = (current: GestureRecognizer, others: Array<GestureRecognizer>) => GestureRecognizer
```

手势与响应链上其他组件的手势设置并行关系的回调事件类型。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-unnamed-declare type ShouldRecognizerParallelWithCallback = (current: GestureRecognizer, others: Array<GestureRecognizer>) => GestureRecognizer--><!--Device-unnamed-declare type ShouldRecognizerParallelWithCallback = (current: GestureRecognizer, others: Array<GestureRecognizer>) => GestureRecognizer-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| current | [GestureRecognizer](../arkts-apis/arkts-arkui-gesturerecognizer-c.md) | 是 | 当前组件的手势识别器，当前仅支持[GestureType](../arkts-apis/arkts-arkui-gesturecontrol-gesturetype-e.md).PAN_GESTURE类型的手势识别器。  |
| others | Array&lt;GestureRecognizer&gt; | 是 | 响应链上优先级高于当前组件的其他组件所持有的同类型[GestureType](../arkts-apis/arkts-arkui-gesturecontrol-gesturetype-e.md)的手势识别器。  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [GestureRecognizer](../arkts-apis/arkts-arkui-gesturerecognizer-c.md) | 与current识别器绑定并行关系的某个手势识别器。  |

