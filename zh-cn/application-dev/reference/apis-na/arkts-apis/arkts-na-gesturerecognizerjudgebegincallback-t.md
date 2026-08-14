# GestureRecognizerJudgeBeginCallback

```TypeScript
export type GestureRecognizerJudgeBeginCallback = (event: BaseGestureEvent, current: GestureRecognizer, recognizers: Array<GestureRecognizer>, touchRecognizers?: Array<TouchRecognizer>) => GestureJudgeResult
```

Defines the callback type used in onGestureRecognizerJudgeBegin.

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-unnamed-export type GestureRecognizerJudgeBeginCallback = (event: BaseGestureEvent, current: GestureRecognizer, recognizers: Array<GestureRecognizer>, touchRecognizers?: Array<TouchRecognizer>) => GestureJudgeResult--><!--Device-unnamed-export type GestureRecognizerJudgeBeginCallback = (event: BaseGestureEvent, current: GestureRecognizer, recognizers: Array<GestureRecognizer>, touchRecognizers?: Array<TouchRecognizer>) => GestureJudgeResult-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | [BaseGestureEvent](../../apis-arkui/arkts-apis/arkts-arkui-basegestureevent-i.md) | 是 | the event information |
| current | [GestureRecognizer](../../apis-arkui/arkts-apis/arkts-arkui-gesturerecognizer-c.md) | 是 | the current gesture recognizer of the component |
| recognizers | Array&lt;[GestureRecognizer](../../apis-arkui/arkts-apis/arkts-arkui-gesturerecognizer-c.md)&gt; | 是 | the gesture recognizers of the component on the response chain |
| touchRecognizers | Array&lt;[TouchRecognizer](../../apis-arkui/arkts-apis/arkts-arkui-touchrecognizer-c.md)&gt; | 否 | the touch recognizers of the component on the response chain |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [GestureJudgeResult](../../apis-arkui/arkts-apis/arkts-arkui-gesturejudgeresult-e.md) | the gesture judge result |

