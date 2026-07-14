# GestureCollectIntervention

定义手势和事件收集的干预操作类型。

**起始版本：** 26.0.0

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## CONTINUE

```TypeScript
CONTINUE = 0
```

继续正常的手势和事件收集流程。不进行任何干预。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本26.0.0开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## DISCARD_LOWER

```TypeScript
DISCARD_LOWER = 1
```

丢弃所有待收集的低优先级手势和事件。丢弃的部分包括左侧兄弟节点以及祖先节点（父节点及以上）的手势。仅保留当前节点和更高优先级节点中已收集的手势。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本26.0.0开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## DISCARD_HIGHER

```TypeScript
DISCARD_HIGHER = 2
```

丢弃已经收集到的高优先级手势和事件。会丢弃已收集的右侧兄弟节点和当前节点上的手势。将继续处理低优先级手势的收集流程（左侧兄弟节点和祖先节点）。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本26.0.0开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## DISCARD_SELF

```TypeScript
DISCARD_SELF = 3
```

丢弃当前节点自身的手势和事件。当前节点的手势和事件将从手势树中排除。兄弟节点（左侧和右侧）以及祖先节点的手势仍会继续收集。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本26.0.0开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## DISCARD_LOWER_PRIORITY_SIBLINGS

```TypeScript
DISCARD_LOWER_PRIORITY_SIBLINGS = 4
```

丢弃左侧兄弟节点中待收集的手势和事件。当前节点以及已收集的右侧兄弟节点的手势和事件将被保留。将继续处理父节点以及祖先节点的收集流程。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本26.0.0开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

