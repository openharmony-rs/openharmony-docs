# ComponentOptions

自定义组件参数，用于配置是否支持组件冻结和全局复用池，适用于需要优化自定义组件性能表现和提升组件复用效率的场景。

**起始版本：** 11

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
```

## freezeWhenInactive

```TypeScript
freezeWhenInactive : boolean
```

配置自定义组件支持组件冻结。true：开启组件冻结，false：不开启组件冻结。当开发者未指定ComponentOptions时，freezeWhenInactive将使用false作为默认值。从API version 11开始，支持通过此参数配置[@Component](../../../ui/state-management/arkts-create-custom-components.md#component)组 件冻结。示例可见[自定义组件冻结](../../../ui/state-management/arkts-custom-components-freeze.md)。从API version 12开始，支持通过此参数配置 [@ComponentV2](../../../ui/state-management/arkts-create-custom-components.md#componentv2)组件冻结。示例可见 [自定义组件冻结](../../../ui/state-management/arkts-custom-components-freezeV2.md)。

**类型：** boolean

**默认值：** false

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本11开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## poolAccepts

```TypeScript
poolAccepts?: Function[]
```

指定全局复用池可以接纳（即允许被复用）的自定义组件名称列表。当reusePool参数被设置时，系统会根据poolAccepts中列出的组件名称，将匹配的可复用组件缓存到该全局复用池中供后续复用。reusePool参数被设置时， poolAccepts必须为非空数组，单独设置poolAccepts不会使全局复用生效。当poolAccepts和reusePool都没有赋值时，全局复用不生效。

**类型：** Function[]

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本26.0.0开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## reusePool

```TypeScript
reusePool?: ReusePoolOwnership
```

在自定义组件上配置全局复用池的类型，适用于应用中存在多个同类型可复用自定义组件、需要在组件实例间共享或隔离复用资源以提升复用效率的场景。如果不传入，则全局复用池不会生效。reusePool需与poolAccepts配合使用， reusePool参数被设置时，poolAccepts必须为非空数组，否则全局复用不生效。

**类型：** [ReusePoolOwnership](arkts-arkui-reusepoolownership-t.md)

**默认值：** perInstance

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本26.0.0开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full
