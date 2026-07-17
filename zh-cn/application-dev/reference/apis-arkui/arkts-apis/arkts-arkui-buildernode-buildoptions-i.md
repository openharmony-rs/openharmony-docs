# BuildOptions

build的可选参数。

**起始版本：** 12

<!--Device-unnamed-export interface BuildOptions--><!--Device-unnamed-export interface BuildOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## enableProvideConsumeCrossing

```TypeScript
enableProvideConsumeCrossing?: boolean
```

定义BuilderNode内[状态管理V1](../../../../ui/state-management/arkts-state-management-overview.md#状态管理v1)自定义组件的[@Consume](../../../../ui/state-management/arkts-provide-and-consume.md)变量是否与BuilderNode外部的[@Provide](../../../../ui/state-management/arkts-provide-and-consume.md)变量双向同步，BuilderNode内[状态管理V2](../../../../ui/state-management/arkts-state-management-overview.md#状态管理v2)自定义组件的[@Consumer](../../../../ui/state-management/arkts-new-provider-and-consumer.md)变量是否与BuilderNode外部的[@Provider](../../../../ui/state-management/arkts-new-provider-and-consumer.md)变量双向同步。

从API version 20开始支持状态管理V1自定义组件的双向同步，从API version 23开始支持状态管理V2自定义组件的双向同步。

true表示支持，false表示不支持。

默认值：false

**类型：** boolean

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-BuildOptions-enableProvideConsumeCrossing?: boolean--><!--Device-BuildOptions-enableProvideConsumeCrossing?: boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## localStorage

```TypeScript
localStorage?: LocalStorage
```

给当前BuilderNode设置LocalStorage，挂载在此BuilderNode下的自定义组件共享该LocalStorage。如果自定义组件构造函数同时也传入LocalStorage，优先使用构造函数中传入的LocalStorage。

默认值：null

**类型：** LocalStorage

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-BuildOptions-localStorage?: LocalStorage--><!--Device-BuildOptions-localStorage?: LocalStorage-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## nestingBuilderSupported

```TypeScript
nestingBuilderSupported?: boolean
```

是否支持Builder嵌套Builder进行使用。其中，true表示支持，false表示不支持。

默认值：false

**类型：** boolean

**默认值：** false

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-BuildOptions-nestingBuilderSupported?: boolean--><!--Device-BuildOptions-nestingBuilderSupported?: boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

