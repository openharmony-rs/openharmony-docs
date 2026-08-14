# MutableBuilder

`MutableBuilder`继承自[WrappedBuilder](arkts-arkui-wrappedbuilder-c.md#WrappedBuilder)，用于封装 [全局`@Builder`](../../../ui/state-management/arkts-builder.md#全局自定义构建函数)，并支持在运行时切换构建函数。需要根据状态或条件动态替换全局`@Builder`内容时，建 议使用[mutableBuilder](../../../ui/state-management/arkts-mutableBuilder.md)函数创建`MutableBuilder`对象。其`builder`属性方法只能在自定义 组件的`build`函数或`@Builder`装饰的函数内部被调用。

**继承/实现关系：** MutableBuilder extends WrappedBuilder<Args>

**起始版本：** 22

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为22。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-unnamed-declare class MutableBuilder--><!--Device-unnamed-declare class MutableBuilder-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

