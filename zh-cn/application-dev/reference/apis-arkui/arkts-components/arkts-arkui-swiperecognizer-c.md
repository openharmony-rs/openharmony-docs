# SwipeRecognizer

快滑手势识别器对象，继承于[GestureRecognizer](arkts-arkui-gesturerecognizer-c.md)。

**继承/实现关系：** SwipeRecognizer extends [GestureRecognizer](arkts-arkui-gesturerecognizer-c.md)

**起始版本：** 18

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## getDirection

```TypeScript
getDirection(): SwipeDirection
```

返回预设快滑手势识别器触发快滑手势滑动方向。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本18开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| SwipeDirection | 预设快滑手势识别器触发快滑手势滑动方向。 |

## getVelocityThreshold

```TypeScript
getVelocityThreshold(): number
```

返回预设快滑手势识别器识别滑动最小速度阈值。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本18开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 预设快滑手势识别器识别滑动最小速度阈值，单位为vp/s。<br/>取值范围：[0, +∞) |

