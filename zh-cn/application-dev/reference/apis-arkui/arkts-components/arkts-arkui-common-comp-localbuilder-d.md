# @LocalBuilder

```TypeScript
declare const LocalBuilder: MethodDecorator
```

`@LocalBuilder`拥有和局部[`@Builder`](arkts-arkui-common-comp-builder-d.md#builder)相同的功能，且比局部`@Builder`能够更好地确定组件的父子关系和状态管理的父子关系。适用于需要在自定义构建函数中维持组件父子关系，并保持状态管理同步的场景。开发指南参考：[`@LocalBuilder`装饰器：维持组件关系](../../../ui/state-management/arkts-localBuilder.md)。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**卡片能力：** 从API版本12开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full
