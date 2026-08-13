# SwipeRecognizer

快滑手势识别器对象，继承于[GestureRecognizer](arkts-arkui-gesture-gesturerecognizer-c.md#GestureRecognizer)。

**继承/实现关系：** SwipeRecognizer extends [GestureRecognizer](arkts-arkui-gesture-gesturerecognizer-c.md#GestureRecognizer)

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-unnamed-export declare class SwipeRecognizer--><!--Device-unnamed-export declare class SwipeRecognizer-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## getDirection

```TypeScript
getDirection(): SwipeDirection
```

返回预设快滑手势识别器触发快滑手势滑动方向。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-SwipeRecognizer-getDirection(): SwipeDirection--><!--Device-SwipeRecognizer-getDirection(): SwipeDirection-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [SwipeDirection](arkts-arkui-gesture-swipedirection-e.md) | 预设快滑手势识别器触发快滑手势滑动方向。 |

## getVelocityThreshold

```TypeScript
getVelocityThreshold(): double
```

返回预设快滑手势识别器识别滑动最小速度阈值。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-SwipeRecognizer-getVelocityThreshold(): double--><!--Device-SwipeRecognizer-getVelocityThreshold(): double-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| double | 预设快滑手势识别器识别滑动最小速度阈值，单位为vp/s。&lt;br/&gt;取值范围：[0, +∞) |

