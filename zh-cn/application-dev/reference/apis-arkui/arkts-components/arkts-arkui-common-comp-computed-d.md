# @Computed

```TypeScript
declare const Computed: MethodDecorator
```

@Computed为方法装饰器，用于状态管理V2中，装饰getter方法，使其变为计算属性，其返回值会被缓存，仅当依赖的源数据发生变化时才重新计算，减少重复计算带来的开销。

开发指南参考：[@Computed装饰器：计算属性](../../../ui/state-management/arkts-new-computed.md)。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**卡片能力：** 从API版本23开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full
