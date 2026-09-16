# @ObservedV2

```TypeScript
declare const ObservedV2: ClassDecorator
```

@ObservedV2是类装饰器，用于状态管理V2中。@ObservedV2与@Trace配套使用，装饰类以及类中的属性，使得被装饰的类和属性具有深度观测的能力。相较于状态管理V1的@Observed，@ObservedV2提供了更细粒度的属性级深度观测能力，适用于需要精确追踪嵌套对象属性变化并驱动UI更新的场景，能够有效提升状态管理的性能和灵活性。

开发指南参考：[\@ObservedV2装饰器和\@Trace装饰器：类属性变化观测](../../../ui/state-management/arkts-new-observedV2-and-trace.md)。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**卡片能力：** 从API版本12开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full
