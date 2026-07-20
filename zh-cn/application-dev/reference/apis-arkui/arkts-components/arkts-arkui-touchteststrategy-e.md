# TouchTestStrategy

事件派发策略。

**起始版本：** 11

<!--Device-unnamed-declare enum TouchTestStrategy--><!--Device-unnamed-declare enum TouchTestStrategy-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## DEFAULT

```TypeScript
DEFAULT = 0
```

自定义分发不产生影响，系统按当前节点命中状态分发事件。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本11开始，该接口支持在ArkTS卡片中使用。

<!--Device-TouchTestStrategy-DEFAULT = 0--><!--Device-TouchTestStrategy-DEFAULT = 0-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## FORWARD_COMPETITION

```TypeScript
FORWARD_COMPETITION = 1
```

应用指定分发事件到某个子节点，其他兄弟节点是否分发事件交由系统决定。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本11开始，该接口支持在ArkTS卡片中使用。

<!--Device-TouchTestStrategy-FORWARD_COMPETITION = 1--><!--Device-TouchTestStrategy-FORWARD_COMPETITION = 1-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## FORWARD

```TypeScript
FORWARD = 2
```

应用指定分发事件到某个子节点，系统不再分发事件到其他兄弟节点。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本11开始，该接口支持在ArkTS卡片中使用。

<!--Device-TouchTestStrategy-FORWARD = 2--><!--Device-TouchTestStrategy-FORWARD = 2-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

