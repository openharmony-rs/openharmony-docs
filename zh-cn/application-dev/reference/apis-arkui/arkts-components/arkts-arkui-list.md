# List

List是ArkUI中的列表容器组件，用于呈现连续、多行或多列的同类数据，例如图片和文本，支持垂直或水平滚动。配合LazyForEach或Repeat可实现懒加载，提升长列表场景下的启动速度并减少内存消耗；支持预加载以减少滚动丢帧、提 升流畅性；支持单列/多列布局、分组列表、吸顶吸底等能力，适用于消息列表、商品列表、设置页面等场景。 List的懒加载是指组件按需加载显示区域内的子组件。相比全量加载，使用懒加载可以提升应用启动速度，减少内存消耗。List和 [ForEach](../../../ui/rendering-control/arkts-rendering-control-foreach.md)、 [LazyForEach](../../../ui/rendering-control/arkts-rendering-control-lazyforeach.md)、 [Repeat](../../../ui/rendering-control/arkts-new-rendering-control-repeat.md)结合，懒加载能力存在差异： - 当List和ForEach结合，会一次性创建所有的子组件，在需要的时候布局和渲染屏幕范围内的节点。当用户滑动时，划出屏幕范围的节点不会下树销毁，划入屏幕范围的节点会布局和渲染。 - 当List和LazyForEach结合，会一次性创建、布局、渲染屏幕范围的节点。当用户滑动时，划出屏幕范围的节点会下树销毁，划入屏幕范围的节点会创建、布局、渲染。 - 当List和带virtualScroll的Repeat结合，它的懒加载行为和LazyForEach一致。当List和不带virtualScroll的 Repeat结合，它的懒加载行为和ForEach一致。 如果可滚动组件嵌套List组件，并且滚动方向相同，List组件又没有设置主轴尺寸时，List组件会全量加载子组件，导致懒加载失效。该场景推荐使用List嵌套 ListItemGroup组件以优化性能。 List的预加载是指除了加载显示区域内可见的子组件外，还支持在空闲时隙提前加载部分显示区域外不可见的子组件。使用预加载可以减少滚动丢帧，提升流畅性。预加载需要结合懒加载才会生效。List支持通过 cachedCount设置预加载的数量。默认会预加载显示区域上下各一屏子组件（最大预加载16行子组件）。List和 [ForEach](../../../ui/rendering-control/arkts-rendering-control-foreach.md)、 [LazyForEach](../../../ui/rendering-control/arkts-rendering-control-lazyforeach.md)、 [Repeat](../../../ui/rendering-control/arkts-new-rendering-control-repeat.md)结合，预加载能力存在差异： - 当List和ForEach结合，如果设置了cachedCount，除了会布局显示区域内子组件外，还会在空闲时隙预布局显示区域外cachedCount范围内的子组件。 - 当List和LazyForEach结合，如果设置了cachedCount，除了会创建和布局显示区域内子组件外，还会在空闲时隙预创建和预布局显示区域外cachedCount范围内的子组件。 - 当List和带virtualScroll的Repeat结合，它的预加载行为和LazyForEach一致。当List和不带virtualScroll的 Repeat结合，它的预加载行为和ForEach一致。 > **说明：** > > 组件内部已绑定手势实现跟手滚动等功能，需要增加自定义手势操作时请参考手势拦截增强进行处理。

## 子组件 仅支持ListItem、ListItemGroup子组件和自定义组件。自定义组件在List下使用时，请使用ListItem或 ListItemGroup作为自定义组件的顶层组件，请勿直接给自定义组件设置属性和事件方法，因为List通过ListItem或ListItemGroup管理子组件的布局和事件处理，直接设置可能导致部分功能无法正常生效。 支持通过渲染控制类型（[if/else](../../../ui/rendering-control/arkts-rendering-control-ifelse.md)、 [ForEach](../../../ui/rendering-control/arkts-rendering-control-foreach.md)、 [LazyForEach](../../../ui/rendering-control/arkts-rendering-control-lazyforeach.md)和 [Repeat](../../../ui/rendering-control/arkts-new-rendering-control-repeat.md)）动态生成子组件，更推荐使用LazyForEach或Repeat以优化性能。 > **说明：** > > 在处理大量子组件时遇到卡顿问题，请采用懒加载、缓存列表项、动态预加载、组件复用和布局优化等方法进行优化。 > > 从API version 21开始，List单个子组件的宽高最大为16777216px；API version 20及之前，List单个子组件的宽高最大为1000000px。子组件超出该大小可能导致滚动或显示异常。 > > List的子组件的索引值计算规则： > > - 按子组件的顺序依次递增。 > > - if/else语句中，只有条件成立的分支内的子组件会参与索引值计算，条件不成立的分支内子组件不计算索引值。 > > - ForEach/LazyForEach/Repeat语句中，会计算展开所有子组件索引值。 > > - [if/else](../../../ui/rendering-control/arkts-rendering-control-ifelse.md)、 > [ForEach](../../../ui/rendering-control/arkts-rendering-control-foreach.md)、 > [LazyForEach](../../../ui/rendering-control/arkts-rendering-control-lazyforeach.md)和 > [Repeat](../../../ui/rendering-control/arkts-new-rendering-control-repeat.md)发生变化以后，会更新子组件索引值。 > > - ListItemGroup作为一个整体计算一个索引值，ListItemGroup内部的ListItem不计算索引值。 > > - List子组件的visibility属性设置为Hidden或None依然会计算索引值。

## List

```TypeScript
List(options?: ListOptions)
```

创建List列表容器。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

<!--Device-ListInterface-(options?: ListOptions): ListAttribute--><!--Device-ListInterface-(options?: ListOptions): ListAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数:**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [ListOptions](arkts-arkui-listoptions-i.md) | 否 | 设置List组件参数。不传入时使用默认配置。 |

## 汇总

### 接口

| 名称 | 说明 |
| --- | --- |
| [ChainAnimationOptions](arkts-arkui-chainanimationoptions-i-sys.md) | 链式联动动效属性集合，用于设置List最大间距、最小间距、动效强度、传导系数、边缘效果、刚度和阻尼。当列表需要精细控制链式联动弹性效果时，可通过调整本对象中的参数实现不同动效手感。 |
| [CloseSwipeActionOptions](arkts-arkui-closeswipeactionoptions-i.md) | 收起EXPANDED状态ListItem回调事件集合，用于设置收起动画完成后回调事件。 |
| [ListBackPressBehavior](arkts-arkui-listbackpressbehavior-i.md) | 定义List组件的系统返回键行为。 |
| [ListDividerOptions](arkts-arkui-listdivideroptions-i.md) | 用于设置List或ListItemGroup组件的分割线样式。 @since版本号高于内层元素版本号的情况，但这不影响接口的使用。 |
| [ListOptions](arkts-arkui-listoptions-i.md) | 用于设置List组件参数。 @since版本号高于内层元素版本号的情况，但这不影响接口的使用。 |
| [UIListEvent](arkts-arkui-uilistevent-i.md) | frameNode中[getEvent('List')](../arkts-apis/arkts-arkui-typenode-getevent-f.md)方法的返 回值，可用于给List节点设置滚动事件。 UIListEvent继承于UIScrollableCommonEvent。 |
| [VisibleListContentInfo](arkts-arkui-visiblelistcontentinfo-i.md) | 用于表示List可见内容区子组件的详细信息。 |

### 类型

| 名称 | 说明 |
| --- | --- |
| [OnListScrollIndexCallback](arkts-arkui-onlistscrollindexcallback-t.md) | List组件可见区域item变化事件的回调类型。 |
| [OnScrollVisibleContentChangeCallback](arkts-arkui-onscrollvisiblecontentchangecallback-t.md) | 有子组件划入或划出List显示区域时触发。 API版本26.0.0开始，List从有子组件变成空的List时，上报的start和end参数的index成员为-1，itemGroupArea和itemIndexInGroup成员为undefined。API版本26.0.0以前， List从有子组件变成空的List时，上报的start和end参数会保留上次有子组件时的值。 start和end的index同时返回0，代表List内只有一个子组件。 |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [ChainEdgeEffect](arkts-arkui-chainedgeeffect-e-sys.md) | 设置链式动效的边缘效果，用于决定列表滚动到边缘后继续拖动时列表项间距的变化方式。 |
| [ListItemAlign](arkts-arkui-listitemalign-e.md) | 设置子组件在List交叉轴方向的对齐方式。 |
| [ListItemGroupArea](arkts-arkui-listitemgrouparea-e.md) | 枚举了ListItemGroup各个区域。 |
| [ScrollSnapAlign](arkts-arkui-scrollsnapalign-e.md) | 设置列表项滚动结束对齐效果。 |
| [ScrollSnapAnimationSpeed](arkts-arkui-scrollsnapanimationspeed-e.md) | 设置列表项滚动限位动画速度。 |
| [ScrollState](arkts-arkui-scrollstate-e.md) | 滑动状态枚举。 |
| [StickyStyle](arkts-arkui-stickystyle-e.md) | ListItemGroup吸顶或吸底效果枚举。 |

