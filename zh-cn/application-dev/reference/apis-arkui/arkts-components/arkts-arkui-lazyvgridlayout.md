# LazyVGridLayout

该组件用于实现支持懒加载的网格布局。

API版本26.0.0之前，其父组件支持[WaterFlow]{@link water_flow}和[FlowItem]{@link flow_item}组件，并支持使用自定义组件或
[NodeContainer]{@link node_container}组件封装后应用在WaterFlow或FlowItem中。

从API版本26.0.0开始，其父组件新增支持[List]{@link list}、[Scroll]{@link scroll}和
[LazyColumnLayout](docroot://reference/apis-arkui/arkui-ts/ts-container-lazycolumnlayout.md)，同时新增支持使用自定义组件或
[NodeContainer]{@link node_container}组件封装后应用在List、Scroll或LazyColumnLayout中。

> **说明：**
>
> - 该组件从API version 19开始支持。后续版本如有新增内容，则采用上角标单独标记该内容的起始版本。
>
> - 本模块接口仅可在Stage模型下使用。
>
> - LazyVGridLayout组件高度默认自适应内容，不建议设置高度、高度约束或宽高比，设置后会导致显示异常。
>
> - 该组件在不同父组件下的懒加载支持条件如下：
> >   1. 在WaterFlow组件下，仅在WaterFlow组件的单列模式或分段布局中的单列分段，并且布局方向[FlexDirection]{@link FlexDirection}设置为
> FlexDirection.Column的情况下支持懒加载。在WaterFlow的多列模式或布局方向为FlexDirection.Row或FlexDirection.RowReverse的情况下使用该组件，则不支持懒加载。此外，在
> 布局方向为FlexDirection.ColumnReverse的WaterFlow组件下使用该组件会导致显示异常。
> >   2. 在List组件下，要求List组件布局方向必须是竖直方向（即[listDirection]{@link ListAttribute#listDirection}属性设置为Axis.Vertical）。在非竖直方向的
> List中使用该组件会导致应用崩溃。当List设置了lanes、chainAnimation、scrollSnapAlign属性中的任意一个时，该组件的懒加载功能会失效。
> >   3. 在Scroll组件下，要求Scroll组件布局方向必须是竖直方向（即[scrollable]{@link ScrollAttribute#scrollable}属性设置为
> ScrollDirection.Vertical）。在非竖直方向的Scroll中使用该组件会导致应用崩溃。
>
> - 当懒加载功能生效时，该组件仅加载父组件显示区域内的子组件，并在帧间空闲时隙预加载显示区域上方和下方各半屏的内容。

###### OnVisibleIndexesChangeCallback

OnVisibleIndexesChangeCallback = (start: number, end: number) => void

LazyVGridLayout可视区域内子组件的索引值发生变化时触发的回调类型。

**起始版本：** 26.0.0

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务中使用。

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型   | 必填 | 说明                                  |
| ------ | ------ | ---- | ------------------------------------- |
| start  | number | 是  | 当前可视区域内子组件的起始索引。可视区域内无子组件或者LazyVGridLayout内无子组件时返回-1。 |
| end  | number | 是  | 当前可视区域内子组件的结束索引。可视区域内无子组件或者LazyVGridLayout内无子组件时返回-1。 |


## LazyVGridLayout

```TypeScript
LazyVGridLayout()
```

创建垂直方向懒加载网格布局容器。

**起始版本：** 19

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本19开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 汇总

