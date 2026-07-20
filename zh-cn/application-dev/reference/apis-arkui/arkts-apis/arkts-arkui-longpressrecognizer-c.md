# LongPressRecognizer

长按手势识别器对象，继承于[GestureRecognizer](arkts-arkui-gesturerecognizer-c.md)。

**继承/实现关系：** LongPressRecognizer extends [GestureRecognizer](arkts-arkui-gesturerecognizer-c.md)

**起始版本：** 18

<!--Device-unnamed-declare class LongPressRecognizer extends GestureRecognizer--><!--Device-unnamed-declare class LongPressRecognizer extends GestureRecognizer-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

<a id="getallowablemovement"></a>
## getAllowableMovement

```TypeScript
getAllowableMovement(): number
```

获取长按手势识别器识别的手势的最大移动距离。

**起始版本：** 22

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-LongPressRecognizer-getAllowableMovement(): number--><!--Device-LongPressRecognizer-getAllowableMovement(): number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 长按手势识别器识别的手势的最大移动距离，单位为px。<br/>取值范围：(0, +∞) |

<a id="getduration"></a>
## getDuration

```TypeScript
getDuration(): number
```

返回预设长按手势识别器触发长按最短时间阈值。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-LongPressRecognizer-getDuration(): number--><!--Device-LongPressRecognizer-getDuration(): number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 返回预设长按手势识别器触发长按最短时间阈值，单位为ms。<br/>取值范围：[0, +∞) |

<a id="isrepeat"></a>
## isRepeat

```TypeScript
isRepeat(): boolean
```

返回预设长按手势识别器是否连续触发事件回调。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-LongPressRecognizer-isRepeat(): boolean--><!--Device-LongPressRecognizer-isRepeat(): boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 预设长按手势识别器是否连续触发事件回调。当绑定长按手势且不会连续触发回调时，返回false。当绑定长按手势且会连续触发回调时，返回true。 |

