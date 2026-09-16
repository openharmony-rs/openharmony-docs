# @Extend

```TypeScript
declare const Extend: MethodDecorator & ((value: any) => MethodDecorator)
```

\@Extend装饰器用于扩展指定组件的样式，支持在装饰的函数中统一定义多个样式属性，并可通过参数传递实现样式的灵活复用，适用于需要将相同样式应用到多个组件、减少样式代码重复的场景。

开发指南参考：[\@Extend装饰器：定义扩展组件样式（ArkTS-Dyn）](../../../ui/state-management/arkts-extend.md)。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full
