# LazyVGridLayout

该组件用于实现支持懒加载的网格布局，适用于在滚动容器中按需渲染大量网格项的场景，可减少首帧渲染时间和内存开销。 API版本26.0.0之前，其父组件支持[WaterFlow]{@link ./water_flow}和[FlowItem]{@link ./flow_item}组件，并支持使用自定义组件或 [NodeContainer]{@link ./node_container}组件封装后应用在WaterFlow或FlowItem中。 从API版本26.0.0开始，其父组件新增支持[List]{@link ./list}、[Scroll]{@link ./scroll}和 [LazyColumnLayout](docroot://reference/apis-arkui/arkui-ts/ts-container-lazycolumnlayout.md)，同时新增支持使用自定义组件或 [NodeContainer]{@link ./node_container}组件封装后应用在List、Scroll或LazyColumnLayout中。 更多关于懒加载布局的使用场景和完整示例，可参考[创建懒加载布局](docroot://ui/arkts-layout-development-create-lazy-layout.md)。 > **说明：** > > - LazyVGridLayout组件高度默认自适应内容，不建议设置会固定或约束组件垂直方向尺寸的属性，设置后会导致显示异常或无法正常滚动。涉及的属性包括 > [height]{@link CommonMethod#height(value: Length)}、[size]{@link CommonMethod#size}中的height、 > [constraintSize]{@link CommonMethod#constraintSize}中的minHeight/maxHeight、 > [aspectRatio]{@link CommonMethod#aspectRatio}、[layoutWeight]{@link CommonMethod#layoutWeight}，以及 > [height]{@link CommonMethod#height(heightValue: Length | LayoutPolicy)}取[LayoutPolicy]{@link LayoutPolicy}值的场景。 > > - 当父组件设置主轴方向尺寸时，LazyVGridLayout按照父组件可视区域进行懒加载；当父组件未设置主轴方向尺寸时，LazyVGridLayout会被内容撑开，导致所有子组件都会被加载布局。 > > - 该组件在不同父组件下的懒加载支持条件如下： > > 1. 在WaterFlow组件下，仅在WaterFlow组件的单列模式或分段布局中的单列分段，并且布局方向[FlexDirection]{@link FlexDirection}设置为FlexDirection.Column的情况 > 下支持懒加载。在WaterFlow的多列模式或横向布局（FlexDirection.Row或FlexDirection.RowReverse）下使用该组件，则不支持懒加载。此外，在布局方向为 > FlexDirection.ColumnReverse的WaterFlow组件下使用该组件会导致显示异常。 > > 2. 在List组件下，要求List组件布局方向必须是竖直方向（即[listDirection]{@link ListAttribute#listDirection}属性设置为Axis.Vertical）。在非竖直方向的List中 > 使用该组件会导致应用崩溃。当List设置了[lanes]{@link ListAttribute#lanes(value: number | LengthConstrain, gutter?: Dimension)}、 > [chainAnimation]{@link ListAttribute#chainAnimation}、[scrollSnapAlign]{@link ListAttribute#scrollSnapAlign}属性中的任意一个 > 或多个时，该组件的懒加载功能会失效。 > > 3. 在Scroll组件下，要求Scroll组件布局方向必须是竖直方向（即[scrollable]{@link ScrollAttribute#scrollable}属性设置为ScrollDirection.Vertical）。在 > 非竖直方向的Scroll中使用该组件会导致应用崩溃。 > > - 当懒加载功能生效时，该组件仅加载父组件可视区域内的子组件，并在帧间空闲时隙预加载可视区域上方和下方各半屏的内容。 > > - 此处的父组件指最靠近当前组件的上层滚动组件，其他文档下的具体含义请参考对应内容。

## LazyVGridLayout

```TypeScript
LazyVGridLayout()
```

创建垂直方向懒加载网格布局容器。

**起始版本：** 19

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为19。

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

<!--Device-LazyVGridLayoutInterface-(): LazyVGridLayoutAttribute--><!--Device-LazyVGridLayoutInterface-(): LazyVGridLayoutAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 汇总

