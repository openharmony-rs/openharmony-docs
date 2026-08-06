# Row

沿水平方向布局的容器，支持设置子组件间距、对齐方式，适用于需要横向排列多个子组件的场景，如工具栏、标签栏、按钮组等。 > **说明：** > > 该组件从API version 7开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。 > > Row未设置宽度或高度时，在主轴或交叉轴方向上自适应子组件大小。

## 子组件 可以包含子组件。

## Row

```TypeScript
Row(options?: RowOptions)
```

创建横向线性布局容器，可设置子组件间距。 > **说明：** > > 在复杂界面中使用多组件嵌套时，若布局组件的嵌套层数过深或嵌套的组件数量过多，将会产生额外开销。建议通过移除冗余节点、利用布局边界减少布局计算、合理采用渲染控制语法及布局组件方法来优化性能。最佳实践请参考布局优化指导。

**起始版本：** 7

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为7。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

<!--Device-RowInterface-(options?: RowOptions): RowAttribute--><!--Device-RowInterface-(options?: RowOptions): RowAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数:**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 否 | 横向布局的配置对象，用于设置子组件间距（单位：vp），其中space属性支持设置number或string类型的值。当需要自定义子组件间距时传入此参数；不传入时默认 间距为0。 \_\_\_HTML\_TAG\_USD\_0\_\_\_ \_\_\_HTML\_TAG\_USD\_1\_\_\_**说明：** 从API version 9开始，space为负数或者justifyContent设置为FlexAlign.SpaceBetween、FlexAlign.SpaceAround、 FlexAlign.SpaceEvenly时不生效。 |

## Row

```TypeScript
Row(options?: RowOptions | RowOptionsV2)
```

创建横向线性布局容器，可设置子组件间距。 > **说明：** > > 在复杂界面中使用多组件嵌套时，若布局组件的嵌套层数过深或嵌套的组件数量过多，将会产生额外开销。建议通过移除冗余节点、利用布局边界减少布局计算、合理采用渲染控制语法及布局组件方法来优化性能。最佳实践请参考布局优化指导。

**起始版本：** 18

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为18。

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本18开始，该接口支持在ArkTS卡片中使用。

<!--Device-RowInterface-(options?: RowOptions | RowOptionsV2): RowAttribute--><!--Device-RowInterface-(options?: RowOptions | RowOptionsV2): RowAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数:**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | \_\_\_MD\_LINK\_USD\_0\_\_\_ \| RowOptionsV2 | 否 | 横向布局的配置对象，用于设置子组件间距（单位：vp），其中space属性支持设置number、string或Resource类型的 值。不传入时默认间距为0。 \_\_\_HTML\_TAG\_USD\_0\_\_\_**说明：** 从API version 9开始，space为负数或者justifyContent设置为FlexAlign.SpaceBetween、FlexAlign.SpaceAround、 FlexAlign.SpaceEvenly时不生效。  |

## 汇总

