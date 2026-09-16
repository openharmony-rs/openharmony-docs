# FinishCallbackType

动画中定义onFinish回调的类型。

**起始版本：** 11

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## REMOVED

```TypeScript
REMOVED = 0
```

当整个动画结束并被移除时，将触发回调。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**卡片能力：** 从API版本11开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## LOGICALLY

```TypeScript
LOGICALLY = 1
```

当动画在逻辑上已经完成但可能仍处于长尾状态时触发回调。即动画的主要运动逻辑已完成时触发onFinish回调，但动画可能仍有长尾效果（如弹簧曲线的余震衰减）继续运行，此回调在逻辑完成时即触发，而非等待长尾效果完全消失。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**卡片能力：** 从API版本11开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full
