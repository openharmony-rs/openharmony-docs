# LongPressRecognizer

长按手势识别器对象，继承于[GestureRecognizer](arkts-arkui-gesture-gesturerecognizer-c.md)。

**继承/实现关系：** LongPressRecognizer extends [GestureRecognizer](arkts-arkui-gesture-gesturerecognizer-c.md)

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-unnamed-export declare class LongPressRecognizer--><!--Device-unnamed-export declare class LongPressRecognizer-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## getAllowableMovement

```TypeScript
getAllowableMovement(): double
```

获取长按手势识别器识别的手势的最大移动距离。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-LongPressRecognizer-getAllowableMovement(): double--><!--Device-LongPressRecognizer-getAllowableMovement(): double-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| double | 长按手势识别器识别的手势的最大移动距离，单位为px。<br/>取值范围：(0, +∞) |

## getDuration

```TypeScript
getDuration(): int
```

返回预设长按手势识别器触发长按最短时间阈值。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-LongPressRecognizer-getDuration(): int--><!--Device-LongPressRecognizer-getDuration(): int-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| int | 返回预设长按手势识别器触发长按最短时间阈值，单位为ms。<br/>取值范围：[0, +∞) |

## isRepeat

```TypeScript
isRepeat(): boolean
```

返回预设长按手势识别器是否连续触发事件回调。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-LongPressRecognizer-isRepeat(): boolean--><!--Device-LongPressRecognizer-isRepeat(): boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 预设长按手势识别器是否连续触发事件回调。当绑定长按手势且不会连续触发回调时，返回false。当绑定长按手势且会连续触发回调时，返回true。 |

