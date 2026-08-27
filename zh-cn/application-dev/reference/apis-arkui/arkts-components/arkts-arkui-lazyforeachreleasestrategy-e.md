# LazyForEachReleaseStrategy

选择LazyForEach的资源释放策略。

**起始版本：** 26.0.0

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## BATCH

```TypeScript
BATCH = 0
```

BATCH为默认使用的资源释放策略，该策略在当前帧释放掉所有废弃节点资源。如果存在节点复用，此时能够最大化节点复用率，但如果存在组件层级较深、子组件数量较多的节点，单节点资源释放耗时较长。大量节点在当前帧释放可能会导致超大帧，影响 性能。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## PROGRESSIVE

```TypeScript
PROGRESSIVE = 1
```

PROGRESSIVE为根据节点释放时间和当前帧剩余时间自动调整节点释放的策略，如果当前帧时间不足以释放剩余节点，会放到后续帧继续释放，避免超大帧的出现，优化性能。此时，LazyForEach会继续持有节点，可能导致复用率下降，在 节点大量产生来不及释放的情况下，内存会相应地升高。开发者需关注性能和内存的影响，合理选择资源释放策略。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full
