# @Provider

```TypeScript
declare const Provider: (aliasName?: string) => PropertyDecorator
```

@Provider和@Consumer搭配使用，用于状态管理V2中，实现跨组件层级的数据双向同步。@Provider装饰数据提供方，为子组件提供数据，适用于组件层级较深、需要跨多层组件共享状态且避免逐层传递数据的场景，可简化状态管理流程，降低组件间的耦合度。

开发指南参考：[@Provider装饰器和@Consumer装饰器：跨组件层级双向同步](../../../ui/state-management/arkts-new-provider-and-consumer.md)。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**卡片能力：** 从API版本23开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full
