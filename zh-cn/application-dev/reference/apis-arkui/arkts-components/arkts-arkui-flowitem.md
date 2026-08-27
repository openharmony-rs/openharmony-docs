# FlowItem

瀑布流组件WaterFlow的子组件，用于展示瀑布流中的具体项。
> **说明：** > > * > > * 仅支持作为WaterFlow组件的子组件使用。 > > * 在滑动场景中，由于FlowItem及其子组件的频繁创建与销毁，建议将FlowItem中的组件封装为自定义组件，并使用@Reusable装饰器修饰，以增强组件的复用能力，从而减少ArkUI框架内部重复创建和销毁节点的开销。最佳实 > 践请参考 > [优化瀑布流加载慢丢帧问题-组件复用](https://developer.huawei.com/consumer/cn/doc/best-practices/bpta-waterflow-performance-optimization#section189041489339)。

## 子组件

支持单个子组件。

## FlowItem

```TypeScript
FlowItem()
```

用于创建瀑布流子组件，仅支持作为WaterFlow组件的子组件使用。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 汇总
