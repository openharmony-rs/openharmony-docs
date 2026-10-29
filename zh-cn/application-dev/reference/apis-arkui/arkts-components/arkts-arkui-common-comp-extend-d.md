# @Extend

```TypeScript
declare const Extend: MethodDecorator
  & ((value: any) => MethodDecorator) & ExtendVersionDecorator
```

\@Extend装饰器用于扩展指定组件的样式，支持在装饰的函数中统一定义多个样式属性，并可通过参数传递实现样式的灵活复用，适用于需要将相同样式应用到多个组件、减少样式代码重复的场景。

开发指南参考：[\@Extend装饰器：定义扩展组件样式](../../../ui/state-management/arkts-extend.md)。

value：指定要扩展样式的目标内置UI组件类型（如Text、Column），传入组件的类型而非组件实例，不支持自定义组件。@Extend装饰器内定义的样式属性将绑定到该组件类型，使其可在该组件上以链式方式调用。MethodDecorator：方法装饰器，开发者无需关注该返回值。

**起始版本：** 7

**模型约束：** 此接口可在Stage模型和FA模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

<!--Device-unnamed-declare const Extend: MethodDecorator  & ((value: any) => MethodDecorator) & ExtendVersionDecorator--><!--Device-unnamed-declare const Extend: MethodDecorator  & ((value: any) => MethodDecorator) & ExtendVersionDecorator-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full
