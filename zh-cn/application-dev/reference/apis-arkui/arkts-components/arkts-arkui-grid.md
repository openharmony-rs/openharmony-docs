# Grid

网格容器，由“行”和“列”分割的单元格所组成，通过指定“项目”所在的单元格做出各种各样的布局。 > **说明：** > > 组件内部已绑定手势实现跟手滚动等功能，需要增加自定义手势操作时请参考[手势拦截增强]{@link ./common}进行处理。

## 子组件 仅支持[GridItem]{@link ./gridItem}子组件和自定义组件。自定义组件在Grid下使用时，建议使用GridItem作为自定义组件的顶层组件，不建议给自定义组件设置属性和事件方法。 支持通过渲染控制类型（[if/else](docroot://ui/rendering-control/arkts-rendering-control-ifelse.md)、 [ForEach](docroot://ui/rendering-control/arkts-rendering-control-foreach.md)、 [LazyForEach](docroot://ui/rendering-control/arkts-rendering-control-lazyforeach.md)和 [Repeat](docroot://ui/rendering-control/arkts-new-rendering-control-repeat.md)）动态生成子组件，更推荐使用LazyForEach或Repeat以优化性能。 > **说明：** > > Grid子组件的索引值计算规则： > > 按子组件的顺序依次递增。 > > if/else语句中，只有条件成立分支内的子组件会参与索引值计算，条件不成立分支内的子组件不计算索引值。 > > ForEach/LazyForEach和Repeat语句中，会计算展开所有子组件索引值。 > > [if/else](docroot://ui/rendering-control/arkts-rendering-control-ifelse.md)、 > [ForEach](docroot://ui/rendering-control/arkts-rendering-control-foreach.md)、 > [LazyForEach](docroot://ui/rendering-control/arkts-rendering-control-lazyforeach.md)和 > [Repeat](docroot://ui/rendering-control/arkts-new-rendering-control-repeat.md)发生变化以后，会更新子组件索引值。 > > Grid子组件的visibility属性设置为Hidden或None时依然会计算索引值。 > > Grid子组件的visibility属性设置为None时不显示，但依然会占用子组件对应的网格。 > > Grid子组件设置position属性，会占用子组件对应的网格，子组件将显示在相对Grid左上角偏移position的位置。该子组件不会随其对应网格滚动，在对应网格滑出Grid显示范围外后不显示。 > > 当Grid子组件之间留有空隙时，会根据当前的展示区域尽可能填补空隙，因此GridItem可能会随着网格滚动而改变相对位置。 > > 从API version 21开始，Grid单个子组件的宽高最大为16777216px；API version 20及之前，Grid单个子组件的宽高最大为1000000px。子组件超出该大小可能导致滚动或显示异常。

## Grid

```TypeScript
Grid(scroller?: Scroller, layoutOptions?: GridLayoutOptions)
```

创建网格容器。

**起始版本：** 7

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为7。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-GridInterface-(scroller?: Scroller, layoutOptions?: GridLayoutOptions): GridAttribute--><!--Device-GridInterface-(scroller?: Scroller, layoutOptions?: GridLayoutOptions): GridAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数:**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| scroller | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 否 | 可滚动组件的控制器。用于与可滚动组件进行绑定。不设置时不绑定外部控制器，组件自行管理滚动行为。\_\_\_HTML\_TAG\_USD\_5\_\_\_**说明：** \_\_\_HTML\_TAG\_USD\_6\_\_\_不允许和其他滚动类组件，如： [ArcList]\_\_\_JSDOC\_LINK\_USD\_0\_\_\_、[List]\_\_\_JSDOC\_LINK\_USD\_1\_\_\_、[Grid]\_\_\_JSDOC\_LINK\_USD\_2\_\_\_、[Scroll]\_\_\_JSDOC\_LINK\_USD\_3\_\_\_和 [WaterFlow]\_\_\_JSDOC\_LINK\_USD\_4\_\_\_绑定同一个滚动控制对象。  |
| layoutOptions | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 否 | Grid布局选项，用于配置GridItem跨行跨列等布局信息。不传入时，Grid按照rowsTemplate、columnsTemplate 等常规属性以及GridItem自身属性进行布局，不启用GridLayoutOptions提供的布局选项。\_\_\_HTML\_TAG\_USD\_0\_\_\_ |

## 汇总

