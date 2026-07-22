# Grid

网格容器，由“行”和“列”分割的单元格所组成，通过指定“项目”所在的单元格做出各种各样的布局。

> **说明：**

> 组件内部已绑定手势实现跟手滚动等功能，需要增加自定义手势操作时请参考[手势拦截增强]{@link common}进行处理。

## 子组件

仅支持[GridItem]{@link gridItem}子组件和自定义组件。自定义组件在Grid下使用时，建议使用GridItem作为自定义组件的顶层组件，不建议给自定义组件设置属性和事件方法。

支持通过渲染控制类型（[if/else](docroot://ui/rendering-control/arkts-rendering-control-ifelse.md)、[ForEach](docroot://ui/rendering-control/arkts-rendering-control-foreach.md)、[LazyForEach](docroot://ui/rendering-control/arkts-rendering-control-lazyforeach.md)和[Repeat](docroot://ui/rendering-control/arkts-new-rendering-control-repeat.md)）动态生成子组件，更推荐使用LazyForEach或Repeat以优化性能。
> **说明：**  
>  
> Grid子组件的索引值计算规则：  
>  
> 按子组件的顺序依次递增。  
>  
> if/else语句中，只有条件成立分支内的子组件会参与索引值计算，条件不成立分支内的子组件不计算索引值。  
>  
> ForEach/LazyForEach和Repeat语句中，会计算展开所有子组件索引值。  
>  
> [if/else](docroot://ui/rendering-control/arkts-rendering-control-ifelse.md)、  
> [ForEach](docroot://ui/rendering-control/arkts-rendering-control-foreach.md)、  
> [LazyForEach](docroot://ui/rendering-control/arkts-rendering-control-lazyforeach.md)和  
> [Repeat](docroot://ui/rendering-control/arkts-new-rendering-control-repeat.md)发生变化以后，会更新子组件索引值。  
>  
> Grid子组件的visibility属性设置为Hidden或None时依然会计算索引值。  
>  
> Grid子组件的visibility属性设置为None时不显示，但依然会占用子组件对应的网格。  
>  
> Grid子组件设置position属性，会占用子组件对应的网格，子组件将显示在相对Grid左上角偏移position的位置。该子组件不会随其对应网格滚动，在对应网格滑出Grid显示范围外后不显示。  
>  
> 当Grid子组件之间留有空隙时，会根据当前的展示区域尽可能填补空隙，因此GridItem可能会随着网格滚动而改变相对位置。  
>  
> 从API version 21开始，Grid单个子组件的宽高最大为16777216px；API version 20及之前，Grid单个子组件的宽高最大为1000000px。子组件超出该大小可能导致滚动或显示异常。

## GridLayoutOptions<sup>10+</sup>对象说明

Grid布局选项。其中，irregularIndexes和onGetIrregularSizeByIndex可对仅设置rowsTemplate或columnsTemplate的Grid使用，可以指定一个index数组，并为其中的index对应的GridItem设置其占据的行数与列数，使用方法参见[示例3](docroot://reference/apis-arkui/arkui-ts/ts-container-grid.md#示例3可滚动grid设置跨行跨列节点)；onGetRectByIndex可对同时设置rowsTemplate和columnsTemplate的Grid使用，为指定的index对应的GridItem设置位置和大小，使用方法参见[示例1](docroot://reference/apis-arkui/arkui-ts/ts-container-grid.md#示例1固定行列grid)。

为提高Grid在跳转、列数变化等场景的性能，应该尽量使用GridLayoutOptions。即使Grid中没有任何特殊的跨行跨列节点，也可以通过使用'Grid(this.scroller, {regularSize: [1, 1]})'的方式提高跳转性能。参考<!--RP1-->[使用GridLayoutOptions提升Grid性能](docroot://performance/grid_optimization.md#使用gridlayoutoptions提升grid性能)<!--RP1End-->。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

<!--Table: 20%; 20%; 8%; 8%; 44%-->

| 名称 | 类型 | 只读 | 可选 | 说明 |  
| ----- | ------- | ---- | -- | --------------------- |  
| regularSize | [number, number] | 否 | 否 | 大小规则的GridItem在Grid中占的行数和列数，只支持占1行1列即[1, 1]。 <br/>**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。 |  
| irregularIndexes | number[] | 否 | 是 | 指定索引的GridItem在Grid中的大小是不规则的。当不设置onGetIrregularSizeByIndex时，irregularIndexes中GridItem的默认大小为垂直滚动Grid的一整行或水平滚动Grid的一整列。 <br/>**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。 |  
| onGetIrregularSizeByIndex | (index: number) => [number, number] | 否 | 是 | 配合irregularIndexes使用，设置不规则GridItem占用的行数和列数。开发者可为irregularIndexes中指明的index对应的GridItem设置占用的行数和列数。在API version 12之前，垂直滚动Grid不支持GridItem占多行，水平滚动Grid不支持GridItem占多列。<br/>**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。 |  
| onGetRectByIndex<sup>11+</sup> | (index: number) => [number, number,number,number] | 否 | 是 | 设置指定索引index对应的GridItem的位置及大小[rowStart,columnStart,rowSpan,columnSpan]。 <br/>其中rowStart为行起始位置，columnStart为列起始位置，无单位。 <br/>rowSpan为GridItem占用的行数，columnSpan为GridItem占用的列数，无单位。 <br/>rowStart和columnStart取大于等于0的自然数，若取负数时，rowStart和columnStart默认为0。 <br/>rowSpan和columnSpan取大于等于1的自然数，若取小数则向下取整，若小于1则按1计算。<br/>**说明：** <br/>第一种情况：某个GridItem发现给它指定的起始位置被占据了，则从起始位置[0,0]开始按顺序从左到右，从上到下寻找起始的放置位置。<br/>第二种情况：如果起始位置没有被占据，但其他位置被占据了，无法显示全部的GridItem大小，则只会布局一部分。<br/>**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。 |

## GridItemAlignment<sup>12+</sup>枚举说明

GridItem的对齐方式枚举。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

| 名称 | 值 | 说明 |  
| ------ |------| -------------------------------------- |  
| DEFAULT | 0 | 使用Grid的默认对齐方式。 |  
| STRETCH | 1 | 以一行中的最高的GridItem作为其他GridItem的高度。 |
> **说明：**  
>  
> 1、只有可滚动的Grid中，设置STRETCH参数会生效，其他场景不生效。<br/>  
> > 2、在Grid的一行中，如果每个GridItem都是大小规律的（只占一行一列），设置STRETCH参数会生效，存在跨行或跨列的GridItem的场景不生效。<br/>  
> > 3、设置STRETCH后，只有不设置高度的GridItem才会以当前行中最高的GridItem作为自己的高度，设置过高度的GridItem高度不会变化。<br/>  
> > 4、设置STRETCH后，Grid布局时会有额外的布局流程，可能会带来额外的性能开销。

## GridDirection<sup>8+</sup>枚举说明

主轴布局方向枚举。

**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

| 名称 |值| 说明 |  
| ------ |------| -------------------------------------- |  
| Row | 0 | 主轴布局方向沿水平方向布局，即自左往右先填满一行，再去填下一行。 |  
| Column | 1 | 主轴布局方向沿垂直方向布局，即自上往下先填满一列，再去填下一列。 |  
| RowReverse | 2 | 主轴布局方向沿水平方向反向布局，即自右往左先填满一行，再去填下一行。 |  
| ColumnReverse | 3 | 主轴布局方向沿垂直方向反向布局，即自下往上先填满一列，再去填下一列。 |

## ComputedBarAttribute<sup>10+</sup>对象说明

滚动条位置和长度对象。

**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

| 名称 | 类型 | 只读 | 可选 | 说明 |  
| ----------- | ------------ | ---- | ---- | ---------- |  
| totalOffset | number | 否 | 否 | Grid内容相对显示区域的总偏移，单位px。 |  
| totalLength | number | 否 | 否 | Grid内容总长度，单位px。 |

## Grid

```TypeScript
Grid(scroller?: Scroller, layoutOptions?: GridLayoutOptions)
```

创建网格容器。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-GridInterface-(scroller?: Scroller, layoutOptions?: GridLayoutOptions): GridAttribute--><!--Device-GridInterface-(scroller?: Scroller, layoutOptions?: GridLayoutOptions): GridAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数:**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| scroller | [Scroller](arkts-arkui-scroller-c.md) | 否 | 可滚动组件的控制器。用于与可滚动组件进行绑定。<br/>**说明：** <br/>不允许和其他滚动类组件，如： [ArcList]{@link @ohos.arkui.ArcList}、[List]{@link list}、[Grid]{@link grid}、[Scroll]{@link scroll}和 [WaterFlow]{@link water_flow}绑定同一个滚动控制对象。  |
| layoutOptions | [GridLayoutOptions](arkts-arkui-gridlayoutoptions-i.md) | 否 | Grid布局选项。 |

## 汇总

- [ComputedBarAttribute](arkts-arkui-grid-computedbarattribute-i.md)
- [GridLayoutOptions](arkts-arkui-grid-gridlayoutoptions-i.md)
- [StartLineInfo](arkts-arkui-grid-startlineinfo-i-sys.md)
- [UIGridEvent](arkts-arkui-grid-uigridevent-i.md)
- [OnGetStartIndexByIndexCallback](arkts-arkui-grid-ongetstartindexbyindexcallback-t-sys.md)
- [OnGetStartIndexByOffsetCallback](arkts-arkui-grid-ongetstartindexbyoffsetcallback-t-sys.md)
- [OnGridScrollIndexCallback](arkts-arkui-grid-ongridscrollindexcallback-t.md)
- [GridDirection](arkts-arkui-grid-griddirection-e.md)
- [GridItemAlignment](arkts-arkui-grid-griditemalignment-e.md)
