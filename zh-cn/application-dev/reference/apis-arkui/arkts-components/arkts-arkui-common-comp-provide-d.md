# @Provide

```TypeScript
declare const Provide: PropertyDecorator & ((value: string | ProvideOptions) => PropertyDecorator)
```

\@Provide和[@Consume](arkts-arkui-common-comp-consume-d.md#consume)配套使用，用于[状态管理V1](../../../ui/state-management/arkts-state-management-overview.md#状态管理v1)，实现跨组件层级的双向同步，适用于需要跨越多层组件传递状态、避免逐层传递的场景，能够解决组件层级较深时状态传递繁琐的问题。\@Provide装饰的变量作为数据源，通过别名或变量名与\@Consume装饰的变量建立双向绑定关系。当\@Provide或\@Consume装饰的变量发生变化时，变化会自动同步到对方。

开发指南参考：[@Provide装饰器和@Consume装饰器：与后代组件双向同步](../../../ui/state-management/arkts-provide-and-consume.md)。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full
