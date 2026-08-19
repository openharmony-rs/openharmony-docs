# ShouldBuiltInRecognizerParallelWithCallback

```TypeScript
export type ShouldBuiltInRecognizerParallelWithCallback = (current: GestureRecognizer, others: Array<GestureRecognizer>) => GestureRecognizer
```

Defines the callback type used in shouldBuiltInRecognizerParallelWith.

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-unnamed-export type ShouldBuiltInRecognizerParallelWithCallback = (current: GestureRecognizer, others: Array<GestureRecognizer>) => GestureRecognizer--><!--Device-unnamed-export type ShouldBuiltInRecognizerParallelWithCallback = (current: GestureRecognizer, others: Array<GestureRecognizer>) => GestureRecognizer-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| current | [GestureRecognizer](../../apis-arkui/arkts-apis/arkts-arkui-gesturerecognizer-c.md) | 是 | the current gesture recognizer of the component |
| others | Array&lt;[GestureRecognizer](../../apis-arkui/arkts-apis/arkts-arkui-gesturerecognizer-c.md)&gt; | 是 | the gesture recognizers of the component on the response chain |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [GestureRecognizer](../../apis-arkui/arkts-apis/arkts-arkui-gesturerecognizer-c.md) | gesture recognizer of the component |

