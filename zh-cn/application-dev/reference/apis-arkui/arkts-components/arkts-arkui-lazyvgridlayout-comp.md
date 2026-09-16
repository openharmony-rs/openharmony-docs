# LazyVGridLayout

该组件用于实现支持懒加载的网格布局，适用于在滚动容器中按需渲染大量网格项的场景，可减少首帧渲染时间和内存开销。

API版本26.0.0之前，其父组件支持WaterFlow和FlowItem组件，并支持使用自定义组件或NodeContainer组件封装后应用在WaterFlow或FlowItem中。

从API版本26.0.0开始，其父组件新增支持List、Scroll和[LazyColumnLayout](../arkts-apis/arkts-arkui-arkui-components-arklazycolumnlayout-con.md#lazycolumnlayout)，同时新增支持使用自定义组件或NodeContainer组件封装后应用在List、Scroll或LazyColumnLayout中。

更多关于懒加载布局的使用场景和完整示例，可参考[创建懒加载布局](../../../ui/arkts-layout-development-create-lazy-layout.md)。

> **说明：** > > - LazyVGridLayout组件高度默认自适应内容，不建议设置会固定或约束组件垂直方向尺寸的属性，设置后会导致显示异常或无法正常滚动。涉及的属性包括 > height、size中的height、 > constraintSize中的minHeight/maxHeight、 > [aspectRatio](arkts-arkui-commonmethod-c.md#aspectratio)、[layoutWeight](arkts-arkui-commonmethod-c.md#layoutweight)，以及 > height取[LayoutPolicy](arkts-arkui-layoutpolicy-c.md)值的场景。 > > - 当父组件设置主轴方向尺寸时，LazyVGridLayout按照父组件可视区域进行懒加载；当父组件未设置主轴方向尺寸时，LazyVGridLayout会被内容撑开，导致所有子组件都会被加载布局。 > > - 该组件在不同父组件下的懒加载支持条件如下： > > 1. 在WaterFlow组件下，仅在WaterFlow组件的单列模式或分段布局中的单列分段，并且布局方向[FlexDirection](../arkts-apis/arkts-arkui-flexdirection-e.md)设置为FlexDirection.Column的情况 > 下支持懒加载。在WaterFlow的多列模式或横向布局（FlexDirection.Row或FlexDirection.RowReverse）下使用该组件，则不支持懒加载。此外，在布局方向为 > FlexDirection.ColumnReverse的WaterFlow组件下使用该组件会导致显示异常。 > > 2. 在List组件下，要求List组件布局方向必须是竖直方向（即[listDirection](arkts-arkui-list-comp-attribute.md#listdirection)属性设置为Axis.Vertical）。在非竖直方向的List中 > 使用该组件会导致应用崩溃。当List设置了[lanes](arkts-arkui-list-comp-attribute.md#lanes)、 > chainAnimation、[scrollSnapAlign](arkts-arkui-list-comp-attribute.md#scrollsnapalign)属性中的任意一个 > 或多个时，该组件的懒加载功能会失效。 > > 3. 在Scroll组件下，要求Scroll组件布局方向必须是竖直方向（即scrollable属性设置为ScrollDirection.Vertical）。在 > 非竖直方向的Scroll中使用该组件会导致应用崩溃。 > > - 当懒加载功能生效时，该组件仅加载父组件可视区域内的子组件，并在帧间空闲时隙预加载可视区域上方和下方各半屏的内容。 > > - 此处的父组件指最靠近当前组件的上层滚动组件，其他文档下的具体含义请参考对应内容。

## LazyVGridLayout

```TypeScript
LazyVGridLayout()
```

创建垂直方向懒加载网格布局容器。

**起始版本：** 19

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 汇总

## 示例

```TypeScript
### 示例1（实现懒加载网格布局）

该示例通过[WaterFlow](ts-container-waterflow.md)和LazyVGridLayout实现懒加载网格布局，并通过[onVisibleIndexesChange](#onvisibleindexeschange)在可视区域发生变化时触发回调，返回当前可视区域内子组件的起始索引值和结束索引值。

MyDataSource实现了[LazyForEach](ts-rendering-control-lazyforeach.md)数据源接口[IDataSource](ts-rendering-control-lazyforeach.md#idatasource)，用于通过LazyForEach给LazyVGridLayout提供子组件。

从API版本26.0.0开始，新增onVisibleIndexesChange事件。
```

```TypeScript

```

```TypeScript
### 示例2（设置头部组件或尾部组件及吸附效果）

该示例通过[WaterFlow](ts-container-waterflow.md)嵌套LazyVGridLayout，并通过[header](#header)、[footer](#footer)、[sticky](#sticky)实现网格顶部和底部吸附效果。滚动过程中header吸附在可视区域顶部，footer吸附在可视区域底部。

从API版本26.0.0开始，新增支持header、footer和sticky属性。


```

```TypeScript
### 示例3（设置自适应列数）

该示例通过设置[columnsTemplate](#columnstemplate)属性实现了LazyVGridLayout组件自适应列数，并使用了属性[columnsTemplate](#columnstemplate)中的auto-fill、auto-fit和auto-stretch。

从API version 19开始，新增[columnsTemplate](#columnstemplate)接口。
```
