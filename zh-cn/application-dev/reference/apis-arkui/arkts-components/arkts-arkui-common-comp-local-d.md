# @Local

```TypeScript
declare const Local: PropertyDecorator
```

@Local用于状态管理V2中，表示组件内部的状态，使得自定义组件内部的变量具有观测能力。适用于需要在自定义组件内部维护和观测局部状态的场景（如计数器、开关状态等）。使用@Local可以简化组件内部状态管理逻辑，当状态变化时自动触发UI刷新，无需手动管理。

开发指南参考：[@Local装饰器：组件内部状态](../../../ui/state-management/arkts-new-local.md)。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**卡片能力：** 从API版本23开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full
