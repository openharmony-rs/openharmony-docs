# @Reusable

```TypeScript
declare const Reusable: ClassDecorator & ((options: ReusableOptions) => ClassDecorator)
```

为了降低反复创建销毁自定义组件带来的性能开销，开发者可以使用\@Reusable装饰\@Component装饰的自定义组件，实现组件复用。\@Reusable支持通过reuseId标识不同类型的可复用组件，提供aboutToReuse回调接收复用参数，并支持配置内存优化策略。该装饰器适用于列表滚动、频繁切换组件显示与隐藏等需要反复创建销毁组件的场景。

开发指南参考：[@Reusable装饰器：组件复用](../../../ui/state-management/arkts-reusable.md)。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full
