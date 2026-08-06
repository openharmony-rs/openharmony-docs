# ReusableOptions

可复用自定义组件的参数，用于配置内存优化策略，适用于需要降低可复用自定义组件内存使用量的场景。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

<!--Device-unnamed-declare interface ReusableOptions--><!--Device-unnamed-declare interface ReusableOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## memoryOptimizationStrategy

```TypeScript
memoryOptimizationStrategy?: ReusableMemOptStrategy
```

可复用自定义组件的内存优化策略。该参数在创建可复用自定义组件时设定，不支持动态修改。传入[ENABLE\_AUTO\_CACHE\_OPTIMIZATION]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_时可启用自动内存优 化，在应用退后台、组件不可见或整机低内存等场景下自动释放复用池中的组件；不传入时使用默认值[DEFAULT]\_\_\_JSDOC\_LINK\_DESC\_USD\_1\_\_\_（无内存优化策略）。

**类型：** ReusableMemOptStrategy

**默认值：** ReusableMemOptStrategy.DEFAULT

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-ReusableOptions-memoryOptimizationStrategy?: ReusableMemOptStrategy--><!--Device-ReusableOptions-memoryOptimizationStrategy?: ReusableMemOptStrategy-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

