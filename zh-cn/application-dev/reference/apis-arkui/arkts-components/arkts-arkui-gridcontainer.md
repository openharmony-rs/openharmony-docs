# GridContainer

纵向排布栅格布局容器，仅在栅格布局场景中使用。栅格布局通过将容器宽度划分为指定列数，实现响应式布局，子组件可占用不同的列数和偏移量。适用于响应式页面布局、多栏目内容展示、仪表盘布局等场景。 > **说明：** > > 从API version 9开始，该组件不再维护，推荐使用新组件[GridCol]{@link ./grid_col}、[GridRow]{@link ./grid_row}。 > > 该组件从API version 7开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。

## 子组件 可以包含子组件。

## GridContainer

```TypeScript
GridContainer(value?: GridContainerOptions)
```

创建纵向排布栅格布局容器。 > **说明：** > > 从API version 7开始支持，从API version 9开始废弃。

**起始版本：** 7

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为7。

**废弃版本：** 9

**替代接口：** <!--SUBSTITUTE_API-->grid_col/GridColInterface<!--/SUBSTITUTE_API-->

<!--Device-GridContainerInterface-(value?: GridContainerOptions): GridContainerAttribute--><!--Device-GridContainerInterface-(value?: GridContainerOptions): GridContainerAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数:**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 否 | GridContainer配置参数，用于设置栅格布局的列数、设备宽度类型、列间距和两侧间距。不传入时使用默认配置。  |

## 汇总

