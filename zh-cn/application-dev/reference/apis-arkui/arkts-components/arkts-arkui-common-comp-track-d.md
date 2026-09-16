# @Track

```TypeScript
declare const Track: PropertyDecorator
```

@Track用于状态管理V1中，通过装饰class对象的指定属性实现属性级精准观测。当被@Track装饰的属性发生变化时，系统仅更新依赖该属性的UI组件，从而减少不必要的UI重渲染。适用于class对象包含较多属性，需要减少冗余UI刷新、优化渲染性能的场景。

开发指南参考：[@Track装饰器：class对象属性级更新](../../../ui/state-management/arkts-track.md)。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**卡片能力：** 从API版本11开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full
