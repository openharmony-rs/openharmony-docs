# Grid

网格容器，由“行”和“列”分割的单元格所组成，通过指定“项目”所在的单元格做出各种各样的布局。 > **说明：** > > 组件内部已绑定手势实现跟手滚动等功能，需要增加自定义手势操作时请参考手势拦截增强进行处理。

## 子组件 仅支持GridItem子组件和自定义组件。自定义组件在Grid下使用时，建议使用GridItem作为自定义组件的顶层组件，不建议给自定义组件设置属性和事件方法。 支持通过渲染控制类型（[if/else](../../../ui/rendering-control/arkts-rendering-control-ifelse.md)、 [ForEach](../../../ui/rendering-control/arkts-rendering-control-foreach.md)、 [LazyForEach](../../../ui/rendering-control/arkts-rendering-control-lazyforeach.md)和 [Repeat](../../../ui/rendering-control/arkts-new-rendering-control-repeat.md)）动态生成子组件，更推荐使用LazyForEach或Repeat以优化性能。 > **说明：** > > Grid子组件的索引值计算规则： > > 按子组件的顺序依次递增。 > > if/else语句中，只有条件成立分支内的子组件会参与索引值计算，条件不成立分支内的子组件不计算索引值。 > > ForEach/LazyForEach和Repeat语句中，会计算展开所有子组件索引值。 > > [if/else](../../../ui/rendering-control/arkts-rendering-control-ifelse.md)、 > [ForEach](../../../ui/rendering-control/arkts-rendering-control-foreach.md)、 > [LazyForEach](../../../ui/rendering-control/arkts-rendering-control-lazyforeach.md)和 > [Repeat](../../../ui/rendering-control/arkts-new-rendering-control-repeat.md)发生变化以后，会更新子组件索引值。 > > Grid子组件的visibility属性设置为Hidden或None时依然会计算索引值。 > > Grid子组件的visibility属性设置为None时不显示，但依然会占用子组件对应的网格。 > > Grid子组件设置position属性，会占用子组件对应的网格，子组件将显示在相对Grid左上角偏移position的位置。该子组件不会随其对应网格滚动，在对应网格滑出Grid显示范围外后不显示。 > > 当Grid子组件之间留有空隙时，会根据当前的展示区域尽可能填补空隙，因此GridItem可能会随着网格滚动而改变相对位置。 > > 从API version 21开始，Grid单个子组件的宽高最大为16777216px；API version 20及之前，Grid单个子组件的宽高最大为1000000px。子组件超出该大小可能导致滚动或显示异常。

## Grid

```TypeScript
Grid(scroller?: Scroller, layoutOptions?: GridLayoutOptions)
```

创建网格容器。

**起始版本：** 7

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为7。

**废弃版本：** -1

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-GridInterface-(scroller?: Scroller, layoutOptions?: GridLayoutOptions): GridAttribute--><!--Device-GridInterface-(scroller?: Scroller, layoutOptions?: GridLayoutOptions): GridAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数:**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| scroller | Scroller | 否 | 可滚动组件的控制器。用于与可滚动组件进行绑定。不设置时不绑定外部控制器，组件自行管理滚动行为。<br/>**说明：** <br/>不允许和其他滚动类组件，如： ArcList、List、Grid、Scroll和 WaterFlow绑定同一个滚动控制对象。 |
| layoutOptions | [GridLayoutOptions](arkts-arkui-gridlayoutoptions-i.md) | 否 | Grid布局选项，用于配置GridItem跨行跨列等布局信息。不传入时，Grid按照rowsTemplate、columnsTemplate 等常规属性以及GridItem自身属性进行布局，不启用GridLayoutOptions提供的布局选项。<br/> |

## 汇总

- [ComputedBarAttribute](arkts-arkui-computedbarattribute-i.md)
- [GridLayoutOptions](arkts-arkui-gridlayoutoptions-i.md)
- [StartLineInfo](arkts-arkui-startlineinfo-i-sys.md)
- [UIGridEvent](arkts-arkui-uigridevent-i.md)
- [OnGetStartIndexByIndexCallback](arkts-arkui-ongetstartindexbyindexcallback-t-sys.md)
- [OnGetStartIndexByOffsetCallback](arkts-arkui-ongetstartindexbyoffsetcallback-t-sys.md)
- [OnGridScrollIndexCallback](arkts-arkui-ongridscrollindexcallback-t.md)
- [GridDirection](arkts-arkui-griddirection-e.md)
- [GridItemAlignment](arkts-arkui-griditemalignment-e.md)
