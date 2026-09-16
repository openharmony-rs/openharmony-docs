# @State

```TypeScript
declare const State: PropertyDecorator
```

@State用于[状态管理V1](../../../ui/state-management/arkts-state-management-overview.md#状态管理v1)，将自定义组件内的普通变量转变为状态变量，当状态变量变化时，触发组件内UI重新渲染。适用于需要在组件内管理可变状态的场景。

开发指南参考：[@State装饰器：组件内状态](../../../ui/state-management/arkts-state.md)。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full
