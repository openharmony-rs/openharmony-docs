# ReusableOptions

可复用自定义组件的参数，用于配置内存优化策略，适用于需要降低可复用自定义组件内存使用量的场景。@interface ReusableOptions

**起始版本：** 26.0.0

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
```

## memoryOptimizationStrategy

```TypeScript
memoryOptimizationStrategy?: ReusableMemOptStrategy
```

可复用自定义组件的内存优化策略。该参数在创建可复用自定义组件时设定，不支持动态修改。传入[ENABLE_AUTO_CACHE_OPTIMIZATION](arkts-arkui-reusablememoptstrategy-e.md)时可启用自动内存优 化，在应用退后台、组件不可见或整机低内存等场景下自动释放复用池中的组件；不传入时使用默认值[DEFAULT](arkts-arkui-reusablememoptstrategy-e.md)（无内存优化策略）。

**类型：** [ReusableMemOptStrategy](arkts-arkui-reusablememoptstrategy-e.md)

**默认值：** ReusableMemOptStrategy.DEFAULT

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full
