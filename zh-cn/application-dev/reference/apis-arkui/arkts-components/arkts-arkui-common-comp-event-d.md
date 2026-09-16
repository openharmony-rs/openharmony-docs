# @Event

```TypeScript
declare const Event: PropertyDecorator
```

@Event装饰回调方法，用于状态管理V2中，作为自定义组件的输出。@Event通常与@Param配合使用，@Param负责由父组件向子组件传递数据，@Event负责定义子组件向父组件传递消息的回调接口，适用于需要在子组件中触发父组件状态变更或事件处理的场景。

开发指南参考：[@Event：规范组件输出](../../../ui/state-management/arkts-new-event.md)。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**卡片能力：** 从API版本23开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full
