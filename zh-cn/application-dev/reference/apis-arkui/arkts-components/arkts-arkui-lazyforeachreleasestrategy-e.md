# LazyForEachReleaseStrategy

资源释放策略枚举，用于配置LazyForEach待销毁节点的资源释放策略。

**起始版本：** 26.0.0

<!--Device-unnamed-declare enum LazyForEachReleaseStrategy--><!--Device-unnamed-declare enum LazyForEachReleaseStrategy-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## BATCH

```TypeScript
BATCH = 0
```

在下一次空闲时段内释放所有被丢弃的节点。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-LazyForEachReleaseStrategy-BATCH = 0--><!--Device-LazyForEachReleaseStrategy-BATCH = 0-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## PROGRESSIVE

```TypeScript
PROGRESSIVE = 1
```

在下一次空闲时段内，根据当前帧剩余时间逐个释放被丢弃的节点。未释放的节点将在后续空闲时段根据可用空闲时间继续释放。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-LazyForEachReleaseStrategy-PROGRESSIVE = 1--><!--Device-LazyForEachReleaseStrategy-PROGRESSIVE = 1-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

