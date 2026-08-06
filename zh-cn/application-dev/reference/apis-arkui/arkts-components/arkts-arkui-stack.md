# Stack

堆叠容器，子组件按照顺序依次入栈，后一个子组件覆盖前一个子组件。堆叠顺序基于子组件在父容器中的声明顺序，后声明的子组件具有更高的渲染层级，在视觉上覆盖前面的子组件。适用于需要层叠布局的场景，如页面上的悬浮按钮或提示信息、图片或视频上覆 盖文字标签、多层叠加的弹窗或对话框等。相比使用多个容器嵌套实现层叠效果，Stack提供了更简洁高效的解决方案。 > **说明：** > > - 该组件从API version 7开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。 > > - 通用属性[align]{@link CommonMethod#align(value: Alignment)}在该组件上支持镜像能力。

## 子组件 可以包含子组件。

## Stack

```TypeScript
Stack(options?: StackOptions)
```

堆叠容器，子组件按照顺序依次入栈，后一个子组件覆盖前一个子组件。堆叠顺序基于子组件在父容器中的声明顺序，后声明的子组件具有更高的渲染层级，在视觉上覆盖前面的子组件。 > **说明：** > > 组件嵌套层数过多会导致性能下降。在可通过组件属性或系统API实现相同布局效果的场景中，使用这些替代方法可以减少嵌套层数，从而优化性能。最佳实践请参考组件嵌套优化-优先使用组件属性代替嵌套组件。 > > 该接口的alignContent参数与[align]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_同时设置时，后设置的属性值会覆盖先设置的属性值。该接口的alignContent参数与 > alignContent属性同时设置时，以属性设置的值为准。

**起始版本：** 7

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为7。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

<!--Device-StackInterface-(options?: StackOptions): StackAttribute--><!--Device-StackInterface-(options?: StackOptions): StackAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数:**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 否 | 设置子组件在容器内的对齐方式。当需要将子组件对齐到特定位置（如顶部、底部、左上角等）而非默认居中时传入此参数；如果不传入此参数，则使用StackOptions的 默认配置，其中alignContent默认为Alignment.Center。 |

## 汇总

