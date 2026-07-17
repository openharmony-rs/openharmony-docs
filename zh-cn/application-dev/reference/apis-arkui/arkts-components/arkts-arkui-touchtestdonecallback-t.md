# TouchTestDoneCallback

```TypeScript
declare type TouchTestDoneCallback = (event: BaseGestureEvent, recognizers: Array<GestureRecognizer>) => void
```

动态指定手势识别器是否参与手势处理的回调事件类型，回调内参数的生命周期跟随回调本身，参数内的方法仅支持在回调内同步使用。

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-unnamed-declare type TouchTestDoneCallback = (event: BaseGestureEvent, recognizers: Array<GestureRecognizer>) => void--><!--Device-unnamed-declare type TouchTestDoneCallback = (event: BaseGestureEvent, recognizers: Array<GestureRecognizer>) => void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | BaseGestureEvent | 是 | [触摸测试](../../../../ui/arkts-interaction-basic-principles.md#触摸测试)结束后的基础手势事件的信息。 <br/>**说明：** <br/>仅包含BaseGestureEvent的信息，不包含其子类拓展信息。<br/>axisHorizontal和axisVertical的值为0。 |
| recognizers | Array&lt;GestureRecognizer&gt; | 是 | [触摸测试](../../../../ui/arkts-interaction-basic-principles.md#触摸测试)结束后，所有手势识别器对象。 |

