# CompetitionStrategy

定义分发的事件是否为竞争手势，竞争场景手势原始节点和目标节点只有一个节点会响应手势，非竞争场景可以同时响应。

**起始版本：** 24

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## DEFAULT

```TypeScript
DEFAULT = 0
```

表示分发的事件为非竞争手势。

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本24开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## COMPETITION

```TypeScript
COMPETITION = 1
```

表示分发的事件为竞争手势。

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本24开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

