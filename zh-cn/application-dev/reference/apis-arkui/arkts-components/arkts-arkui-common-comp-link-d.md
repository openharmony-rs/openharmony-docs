# @Link

```TypeScript
declare const Link: PropertyDecorator
```

@Link用于[状态管理V1](../../../ui/state-management/arkts-state-management-overview.md#状态管理v1)，接收父组件传入的状态变量的引用，建立父子组件间的双向数据绑定。适用于需要在子组件中直接修改父组件状态、简化父子组件通信的场景。

开发指南参考：[@Link装饰器：父子双向同步](../../../ui/state-management/arkts-link.md)。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full
