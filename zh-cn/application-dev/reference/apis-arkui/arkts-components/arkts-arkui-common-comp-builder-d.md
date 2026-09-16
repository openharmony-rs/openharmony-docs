# @Builder

```TypeScript
declare const Builder: MethodDecorator
```

\@Builder装饰的函数也称为“自定义构建函数”，用于封装可复用的UI构建逻辑，可在自定义组件中多次调用，从而减少代码重复、提升UI构建的可维护性，适用于需要复用相同UI结构的场景。

开发指南参考：[@Builder装饰器：自定义构建函数](../../../ui/state-management/arkts-builder.md)。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full
