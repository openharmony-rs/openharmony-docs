# TouchTestDoneCallback

```TypeScript
export type TouchTestDoneCallback = (event: BaseGestureEvent, recognizers: Array<GestureRecognizer>) => void
```

Defines the callback type used in onTouchTestDone. When the user touch down, the system performs hit test process to collect all gesture recognizers based on the press location, when the collection is completed, and before gesture begin to be recognizing, the callback is triggered, you can get all recognizer's information from this callback.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-unnamed-export type TouchTestDoneCallback = (event: BaseGestureEvent, recognizers: Array<GestureRecognizer>) => void--><!--Device-unnamed-export type TouchTestDoneCallback = (event: BaseGestureEvent, recognizers: Array<GestureRecognizer>) => void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | the event information, basicly is the touch down information  |
| recognizers | Array&lt;\_\_\_MD\_LINK\_USD\_0\_\_\_&gt; | 是 | the gesture recognizers of the component on the response chain  |

