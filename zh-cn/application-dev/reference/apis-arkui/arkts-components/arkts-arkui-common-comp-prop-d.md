# @Prop

```TypeScript
declare const Prop: PropertyDecorator
```

@Prop用于[状态管理V1](../../../ui/state-management/arkts-state-management-overview.md#状态管理v1)，接收外部传入值，并与父组件建立单向同步关系。当父组件中[@State](arkts-arkui-common-comp-state-d.md#state)等装饰的状态变量发生变化时，会同步更新到子组件中对应的@Prop变量，触发子组件重新渲染。@Prop采用单向数据流机制，子组件对@Prop变量的修改仅在子组件内部生效，不会反向同步到父组件。适用于子组件需要响应父组件状态变化但不需要反向修改的场景。

开发指南参考：[@Prop装饰器：父子单向同步](../../../ui/state-management/arkts-prop.md)。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full
