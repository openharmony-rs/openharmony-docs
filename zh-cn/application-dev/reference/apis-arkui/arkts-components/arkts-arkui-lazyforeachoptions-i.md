# LazyForEachOptions

用于配置LazyForEach的资源释放策略、内存优化策略，以及是否使能自定义组件冻结。

> **说明：**
> 
> 1. 注意：在使用LazyForEachOptions时，必须保证键值生成函数已经定义，否则将编译失败。
> 
> 2. 自定义组件冻结：在LazyForEach下，直接使用自定义组件时，使用该配置选择是否使能自定义组件的冻结功能。使能后，当自定义组件不在可视区域时，框架会暂停该组件的状态变量更新等处理逻辑，以降低资源消耗；组件重新进入可视区域
> 时恢复正常处理。
> 
> 3. 资源释放策略：LazyForEach会管理屏上区域节点和预加载区域节点，当节点滑动出预加载区域离开LazyForEach的管理范围时，LazyForEach不再管理该节点，该节点资源被释放。默认使用BATCH模式，
> LazyForEach会在当前帧释放所有待释放的节点；PROGRESSIVE模式会逐个释放资源，在释放每个节点资源时判断当前帧的时间是否足够，如果不够就会放到后续帧释放。在此策略下，LazyForEach可能会持有节点资源，缓存池
> 中的节点来不及扩充，在快速获取节点的场景下会导致复用率下降。开发者应根据应用情况选择合适的资源释放策略。

**起始版本：** 26.0.0

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
```

## customComponentFreezeMode

```TypeScript
customComponentFreezeMode?: LazyForEachCustomComponentFreezeMode
```

选择是否使能自定义组件冻结。仅在LazyForEach下直接使用自定义组件时生效，其他情况不适用。默认为[AUTO](arkts-arkui-lazyforeachcustomcomponentfreezemode-e.md)。

**类型：** [LazyForEachCustomComponentFreezeMode](arkts-arkui-lazyforeachcustomcomponentfreezemode-e.md)

**默认值：** LazyForEachCustomComponentFreezeMode.AUTO

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## memoryOptimizationStrategy

```TypeScript
memoryOptimizationStrategy?: LazyForEachMemOptStrategy
```

LazyForEach的内存优化策略。该参数在创建LazyForEach时设定，不支持动态修改。默认值：[DEFAULT](arkts-arkui-lazyforeachmemoptstrategy-e.md)

**类型：** [LazyForEachMemOptStrategy](arkts-arkui-lazyforeachmemoptstrategy-e.md)

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## releaseStrategy

```TypeScript
releaseStrategy?: LazyForEachReleaseStrategy
```

为LazyForEach配置资源释放策略。默认使用[BATCH](arkts-arkui-lazyforeachreleasestrategy-e.md)，批量释放节点。

**类型：** [LazyForEachReleaseStrategy](arkts-arkui-lazyforeachreleasestrategy-e.md)

**默认值：** LazyForEachReleaseStrategy.BATCH

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full
