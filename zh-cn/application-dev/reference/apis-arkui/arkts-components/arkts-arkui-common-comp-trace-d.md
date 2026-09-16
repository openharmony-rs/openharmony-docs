# @Trace

```TypeScript
declare const Trace: PropertyDecorator
```

@Trace是属性装饰器，用于[状态管理V2](../../../ui/state-management/arkts-state-management-overview.md#状态管理v2)中。[@ObservedV2](arkts-arkui-common-comp-observedv2-d.md#observedv2)与@Trace配套使用，装饰类以及类中的属性，使被装饰的类和属性具有深度观测能力，即能够深度观测嵌套对象中属性值的变化，并触发UI自动刷新，适用于需要精确观测和管理类属性变化状态的场景。

开发指南参考：[@ObservedV2装饰器和@Trace装饰器：类属性变化观测](../../../ui/state-management/arkts-new-observedV2-and-trace.md)。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**卡片能力：** 从API版本12开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full
