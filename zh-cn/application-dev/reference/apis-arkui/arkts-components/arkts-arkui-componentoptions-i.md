# ComponentOptions

Defines the options of Component ClassDecorator.

**起始版本：** 12

<!--Device-unnamed-declare interface ComponentOptions--><!--Device-unnamed-declare interface ComponentOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## freezeWhenInactive

```TypeScript
freezeWhenInactive : boolean
```

freeze UI state.

**类型：** boolean

**默认值：** false

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本12开始，该接口支持在ArkTS卡片中使用。

<!--Device-ComponentOptions-freezeWhenInactive : boolean--><!--Device-ComponentOptions-freezeWhenInactive : boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## poolAccepts

```TypeScript
poolAccepts?: Function[]
```

要重用的自定义组件集合。

**类型：** Function[]

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本26.0.0开始，该接口支持在ArkTS卡片中使用。

<!--Device-ComponentOptions-poolAccepts?: Function[]--><!--Device-ComponentOptions-poolAccepts?: Function[]-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## reusePool

```TypeScript
reusePool?: ReusePoolOwnership
```

自定义组件的重用类型。

**类型：** ReusePoolOwnership

**默认值：** perInstance

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本26.0.0开始，该接口支持在ArkTS卡片中使用。

<!--Device-ComponentOptions-reusePool?: ReusePoolOwnership--><!--Device-ComponentOptions-reusePool?: ReusePoolOwnership-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

