# LazyForEachOptions

配置LazyForEach的参数。

**起始版本：** 26.0.0

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## customComponentFreezeMode

```TypeScript
customComponentFreezeMode?: LazyForEachCustomComponentFreezeMode
```

已移出组件树的缓存自定义节点的冻结模式。默认值：LazyForEachCustomComponentFreezeMode.AUTO。

**类型：** LazyForEachCustomComponentFreezeMode

**默认值：** LazyForEachCustomComponentFreezeMode.AUTO

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本26.0.0开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## memoryOptimizationStrategy

```TypeScript
memoryOptimizationStrategy?: LazyForEachMemOptStrategy
```

LazyForEach的内存优化策略。该参数在创建LazyForEach时设定，不支持动态修改。
默认值：[DEFAULT]。

**类型：** LazyForEachMemOptStrategy

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本26.0.0开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## releaseStrategy

```TypeScript
releaseStrategy?: LazyForEachReleaseStrategy
```

LazyForEach缓存节点的资源释放策略。默认值：LazyForEachReleaseStrategy.BATCH。
<br>默认值:默认值：LazyForEachReleaseStrategy.BATCH。

**类型：** LazyForEachReleaseStrategy

**默认值：** LazyForEachReleaseStrategy.BATCH

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本26.0.0开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

