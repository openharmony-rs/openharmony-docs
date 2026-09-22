# @Consumer

```TypeScript
declare const Consumer: (aliasName?: string) => PropertyDecorator
```

[@Provider](arkts-arkui-common-comp-provider-d.md#provider)和@Consumer搭配使用，用于[状态管理V2](../../../ui/state-management/arkts-state-management-overview.md#状态管理v2)中，实现跨组件层级的数据双向同步。@Consumer装饰数据消费方，从数据源获取数据，适用于多层嵌套组件间需要共享和同步状态的场景，可避免通过多层组件逐级传递数据的繁琐操作，简化跨组件层级状态管理。如果@Consumer在组件树中未找到别名匹配的@Provider，将使用自身初始值，不进行数据同步。

开发指南参考：[@Provider装饰器和@Consumer装饰器：跨组件层级双向同步](../../../ui/state-management/arkts-new-provider-and-consumer.md)。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**卡片能力：** 从API版本23开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full
