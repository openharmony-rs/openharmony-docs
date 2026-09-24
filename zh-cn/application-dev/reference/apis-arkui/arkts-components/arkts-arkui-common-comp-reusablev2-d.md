# @ReusableV2

```TypeScript
declare const ReusableV2: ClassDecorator & ((options: ReusableOptions) => ClassDecorator)
```

为了降低反复创建销毁自定义组件带来的性能开销，开发者可以使用\@ReusableV2装饰[\@ComponentV2](arkts-arkui-common-comp-componentv2-d.md#componentv2)装饰的自定义组件，达成组件复用的效果，适用于列表滚动、频繁切换组件显示/隐藏等需要反复创建和销毁组件的场景，支持通过参数配置内存优化策略。

开发指南参考：[\@ReusableV2装饰器：组件复用](../../../ui/state-management/arkts-new-reusableV2.md)。

组件复用的原理与适用场景参考：[组件复用最佳实践](https://developer.huawei.com/consumer/cn/doc/best-practices/bpta-component-reuse)。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full
