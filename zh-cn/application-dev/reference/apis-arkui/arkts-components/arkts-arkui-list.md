# List

列表包含一系列相同宽度的列表项。适合连续、多行呈现同类数据，例如图片和文本。

List的懒加载是指组件按需加载可见区域可见的子组件。相比全量加载，使用懒加载可以提升应用启动速度，减少内存消耗。List和
[ForEach](docroot://ui/rendering-control/arkts-rendering-control-foreach.md)、
[LazyForEach](docroot://ui/rendering-control/arkts-rendering-control-lazyforeach.md)、
[Repeat](docroot://ui/rendering-control/arkts-new-rendering-control-repeat.md)结合，懒加载能力存在差异：

- 当List和ForEach结合，会一次性创建所有的子节点，在需要的时候布局和渲染屏幕范围内的节点。当用户滑动时，划出屏幕范围的节点不会下树销毁，划入屏幕范围的节点会布局和渲染。
- 当List和LazyForEach结合，会一次性创建、布局、渲染屏幕范围的节点。当用户滑动时，划出屏幕范围的节点会下树销毁，划入屏幕范围的节点会创建、布局、渲染。
- 当List和带[virtualScroll]{@link RepeatAttribute#virtualScroll}的Repeat结合，它的懒加载行为和LazyForEach一致。当List和不带virtualScroll的
Repeat结合，它的懒加载行为和ForEach一致。

如果可滚动组件嵌套List组件，并且滚动方向相同，List组件又没有设置主轴尺寸时，List组件会全量加载子组件，导致懒加载失效。该场景推荐使用List嵌套[ListItemGroup]{@link list_item_group}组
件以实现优化性能。

List的预加载是指除了加载显示区域内可见的子组件外，还支持空闲时隙提前加载部分显示区域外不可见的子组件。使用预加载可以减少滚动丢帧，提升流畅性。预加载需要结合懒加载才会生效。List支持通过
[cachedCount]{@link ListAttribute#cachedCount(value: number)}设置预加载的数量。默认会预加载显示区域上下各一屏子节点（最大预加载16行子节点）。List和
[ForEach](docroot://ui/rendering-control/arkts-rendering-control-foreach.md)、
[LazyForEach](docroot://ui/rendering-control/arkts-rendering-control-lazyforeach.md)、
[Repeat](docroot://ui/rendering-control/arkts-new-rendering-control-repeat.md)结合，预加载能力存在差异：

- 当List和ForEach结合，如果设置了cachedCount，除了会布局显示区域内子组件外，还会在空闲时隙预布局显示区域外cachedCount范围内的子节点。
- 当List和LazyForEach结合，如果设置了cachedCount，除了会创建和布局显示区域内子组件外，还会在空闲时隙预创建和预布局显示区域外cachedCount范围内的子节点。
- 当List和带[virtualScroll]{@link RepeatAttribute#virtualScroll}的Repeat结合，它的预加载行为和LazyForEach一致。当List和不带virtualScroll的
Repeat结合，它的预加载行为和ForEach一致。

> **说明：**
>
> 组件内部已绑定手势实现跟手滚动等功能，需要增加自定义手势操作时请参考[手势拦截增强]{@link common}进行处理。

## 子组件

仅支持[ListItem]{@link list_item}、[ListItemGroup]{@link list_item_group}子组件和自定义组件。自定义组件在List下使用时，建议使用ListItem或ListItemGroup作为自定义组件的顶层组件，不建议给自定义组件设置属性和事件方法。

支持通过渲染控制类型（[if/else](docroot://ui/rendering-control/arkts-rendering-control-ifelse.md)、[ForEach](docroot://ui/rendering-control/arkts-rendering-control-foreach.md)、[LazyForEach](docroot://ui/rendering-control/arkts-rendering-control-lazyforeach.md)和[Repeat](docroot://ui/rendering-control/arkts-new-rendering-control-repeat.md)）动态生成子组件，更推荐使用LazyForEach或Repeat以优化性能。

> **说明：**  
>  
> 如果在处理大量子组件时遇到卡顿问题，请考虑采用懒加载、缓存列表项、动态预加载、组件复用和布局优化等方法来进行优化。最佳实践请参考  
> [优化长列表加载慢丢帧问题](https://developer.huawei.com/consumer/cn/doc/best-practices/bpta-best-practices-long-list)。  
>  
> 从API version 21开始，List单个子组件的宽高最大为16777216px；API version 20及之前，List单个子组件的宽高最大为1000000px。子组件超出该大小可能导致滚动或显示异常。  
>  
> List的子组件的索引值计算规则：  
>  
> - 按子组件的顺序依次递增。  
>  
> - if/else语句中，只有条件成立的分支内的子组件会参与索引值计算，条件不成立的分支内子组件不计算索引值。  
>  
> - ForEach/LazyForEach/Repeat语句中，会计算展开所有子节点索引值。  
>  
> - [if/else](docroot://ui/rendering-control/arkts-rendering-control-ifelse.md)、  
> [ForEach](docroot://ui/rendering-control/arkts-rendering-control-foreach.md)、  
> [LazyForEach](docroot://ui/rendering-control/arkts-rendering-control-lazyforeach.md)和  
> [Repeat](docroot://ui/rendering-control/arkts-new-rendering-control-repeat.md)发生变化以后，会更新子节点索引值。  
>  
> - ListItemGroup作为一个整体计算一个索引值，ListItemGroup内部的ListItem不计算索引值。  
>  
> - List子组件visibility属性设置为Hidden或None依然会计算索引值。

## ListOptions<sup>18+</sup>对象说明

用于设置List组件参数。

> **说明：**  
>  
> 为规范匿名对象的定义，API 18版本修改了此处的元素定义。其中，保留了历史匿名对象的起始版本信息，会出现外层元素@since版本号高于内层元素版本号的情况，但这不影响接口的使用。

**卡片能力：** 从API version 18开始，该接口支持在ArkTS卡片中使用。

**原子化服务API：** 从API version 18开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

<!--Table: 15%; 15%; 10%; 10%; 50%-->

| 名称 | 类型 | 只读 | 可选 | 说明 |  
| ------------ | ------------------------------------------- | ---- | -- | ------------------------------------------------------------ |  
| initialIndex<sup>7+</sup> | number | 否 | 是 | 设置当前List初次加载时显示区域起始位置的item索引值。<br/>默认值：0<br/>**说明：** <br/>设置为负数或超过了当前List最后一个item的索引值时视为无效取值，无效取值按默认值显示。<br/>从API version 14开始，如果在List组件创建完成后首次布局前（如List的[onAttach](docroot://reference/apis-arkui/arkui-ts/ts-universal-events-show-hide.md#onattach12)事件中），调用Scroller滚动控制器中不带动画的scrollToIndex或scrollEdge方法，会覆盖initialIndex设置的值。<br/>设置了initialIndex后，List从initialIndex对应的子组件开始布局，在这之前的子组件未参与布局，无法计算准确大小，因此通过[currentOffset]{@link scroll:Scroller.currentOffset}接口获取到的List的滚动总偏移量通过估算得出，可能会有误差。可通过设置[childrenMainSize](docroot://reference/apis-arkui/arkui-ts/ts-container-list.md#childrenmainsize12)确保List的滚动总偏移量的准确性。<br/>**卡片能力：** 从API version 9开始，该接口支持在ArkTS卡片中使用。<br/>**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。 |  
| space<sup>7+</sup> | number&nbsp;\|&nbsp;string | 否 | 是 | 子组件主轴方向的间隔。<br/>默认值：0<br/>参数类型为number时单位为vp。<br/>**说明：** <br/>设置为负数或者大于等于List内容区长度时，按默认值显示。<br/>space参数值小于List分割线宽度时，子组件主轴方向的间隔取分割线宽度。<br/> List子组件的visibility属性设置为None时不显示，但该子组件上下的space还是会生效。<br/>**卡片能力：** 从API version 9开始，该接口支持在ArkTS卡片中使用。<br/>**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。|  
| spaceWidth | [Dimension]{@link units:Dimension} | 否 | 是 | 子组件主轴方向的间隔。<br/>默认值：0<br/><br/>**说明：** <br/>设置为负数或者大于等于List内容区长度时，按默认值显示。<br/>space参数值小于List分割线宽度时，子组件主轴方向的间隔取分割线宽度。<br/>List子组件的visibility属性设置为None时不显示，但该子组件上下的space还是会生效。如果同时设置了spaceWidth和space，则spaceWidth优先生效。当spaceWidth为undefined或null时，space生效。<br/>**起始版本：** 26.0.0 <br/>**模型约束：** 此接口仅可在Stage模型下使用。<br/>**卡片能力：** 从API版本26.0.0开始，该接口支持在ArkTS卡片中使用。<br/>**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务中使用。|  
| scroller<sup>7+</sup> | [Scroller]{@link scroll:Scroller} | 否 | 是 | 可滚动组件的控制器。与List绑定后，可以通过它控制List的滚动。<br/>**说明：** <br/>不允许和其他滚动类组件，如：[ArcList]{@link ./../../../@ohos.arkui.ArcList}、[List]{@link list}、[Grid]{@link grid}、[Scroll]{@link scroll}和[WaterFlow]{@link water_flow}绑定同一个滚动控制对象。<br/>**卡片能力：** 从API version 9开始，该接口支持在ArkTS卡片中使用。<br/>**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。 |

## ListItemAlign<sup>9+</sup>枚举说明

设置子组件在List交叉轴方向的对齐方式。

**卡片能力：** 从API version 9开始，该接口支持在ArkTS卡片中使用。

**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

| 名称 | 值 | 说明 |  
| ------ | ------ | ------------------------- |  
| Start | 0 | ListItem在List中，交叉轴方向首部对齐。 |  
| Center | 1 | ListItem在List中，交叉轴方向居中对齐。 |  
| End | 2 | ListItem在List中，交叉轴方向尾部对齐。 |

## StickyStyle<sup>9+</sup>枚举说明

ListItemGroup吸顶或吸底效果枚举。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

| 名称 | 值 | 说明 |  
| ------ | ------ | ---------------------------------- |  
| None | 0 | ListItemGroup的header不吸顶，footer不吸底。<br/>**卡片能力：** 从API version 9开始，该接口支持在ArkTS卡片中使用。<br/>**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。 |  
| Header | 1 | ListItemGroup的header吸顶，footer不吸底。<br/>**卡片能力：** 从API version 9开始，该接口支持在ArkTS卡片中使用。<br/>**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。 |  
| Footer | 2 | ListItemGroup的footer吸底，header不吸顶。<br/>**卡片能力：** 从API version 9开始，该接口支持在ArkTS卡片中使用。<br/>**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。 |  
| BOTH<sup>20+</sup> | 3 | ListItemGroup的header吸顶，footer吸底。<br/>**卡片能力：** 从API version 20开始，该接口支持在ArkTS卡片中使用。<br/>**原子化服务API：** 从API version 20开始，该接口支持在原子化服务中使用。 |

## ScrollSnapAlign<sup>10+</sup>枚举说明

设置列表项滚动结束对齐效果。

**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

| 名称 | 值 | 说明 |  
| ------ | ------ | ---------------------------------------- |  
| NONE | 0 | 默认无项目滚动对齐效果。 |  
| START | 1 | 视图中的第一项将在列表的开头对齐。<br/>**说明：**<br/>当列表位移至末端，需要将末端的item完整显示，可能出现开头不对齐的情况。 |  
| CENTER | 2 | 视图中的中间项将在列表中心对齐。<br/>**说明：**<br/>顶端和末尾的item都可以在列表中心对齐，列表显示可能露出空白。 |  
| END | 3 | 视图中的最后一项将在列表末尾对齐。<br/>**说明：**<br/>当列表位移至顶端，需要将顶端的item完整显示，可能出现末尾不对齐的情况。 |

## ScrollSnapAnimationSpeed<sup>22+</sup>枚举说明

设置列表项滚动限位动画速度。

**原子化服务API：** 从API version 22开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

| 名称 | 值 | 说明 |  
| ------ | ------ | ---------------------------------------- |  
| NORMAL | 0 | 默认列表限位动画速度，通常用于列表项尺寸较大，划一下滚动一个列表项场景。 |  
| SLOW | 1 | 列表限位动画速度较慢，通常用于列表项尺寸较小，划一下滚动多个列表项场景。 |

## CloseSwipeActionOptions<sup>11+</sup>对象说明

收起[EXPANDED]{@link list_item:SwipeActionState}状态[ListItem]{@link list_item}回调事件集合，用于设置收起动画完成后回调事件。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

| 名称 | 类型 | 只读 | 可选 | 说明 |  
| ------- | -------- | ---- | -- | ---------------------- |  
| onFinish | ()=>void | 否 | 是 | 在收起动画完成后触发。 |

## ListDividerOptions<sup>18+</sup>对象说明

用于设置List或ListItemGroup组件的分割线样式。

> **说明：**  
>  
> 为规范匿名对象的定义，API 18版本修改了此处的元素定义。其中，保留了历史匿名对象的起始版本信息，会出现外层元素@since版本号高于内层元素版本号的情况，但这不影响接口的使用。

**卡片能力：** 从API version 18开始，该接口支持在ArkTS卡片中使用。

**原子化服务API：** 从API version 18开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

<!--Table: 15%; 15%; 10%; 10%; 50%-->

| 名称 | 类型 | 只读 | 可选 | 说明 |  
| ------- | -------- | ---- | -- | ---------------------- |  
| strokeWidth<sup>7+</sup> | [Length]{@link units:Length} | 否 | 否 | 分割线的线宽。<br/>单位：vp<br/>**说明：** <br/>设置为负数，百分比，或者大于等于List内容区长度时，按0处理。<br/>**卡片能力：** 从API version 9开始，该接口支持在ArkTS卡片中使用。<br/>**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。|  
| color<sup>7+</sup> | [ResourceColor]{@link units:ResourceColor} | 否 | 是 | 分割线颜色。<br/>默认值：0x08000000<br/>**卡片能力：** 从API version 9开始，该接口支持在ArkTS卡片中使用。<br/>**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。 |  
| startMargin<sup>7+</sup> | [Length]{@link units:Length} | 否 | 是 | 分割线与列表侧边起始端的距离。<br/>默认值：0 <br/>单位：vp<br/>**说明：** <br/>设置为负数或者百分比时，按默认值处理。<br/>endMargin + startMargin 超过列宽度后startMargin和endMargin均会被置0。<br/>**卡片能力：** 从API version 9开始，该接口支持在ArkTS卡片中使用。<br/>**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。|  
| endMargin<sup>7+</sup> | [Length]{@link units:Length} | 否 | 是 | 分割线与列表侧边结束端的距离。<br/>默认值：0 <br/>单位：vp<br/> **说明：** <br/>设置为负数或者百分比时，按默认值处理。<br/>endMargin + startMargin 超过列宽度后startMargin和endMargin均会被置0。<br/>**卡片能力：** 从API version 9开始，该接口支持在ArkTS卡片中使用。<br/>**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。|

## ScrollState枚举说明

滑动状态枚举。

**卡片能力：** 从API version 9开始，该接口支持在ArkTS卡片中使用。

**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

| 名称 | 值 | 说明 |  
| ------ | ------ | ---------------------------------------- |  
| Idle | 0 | 空闲状态。滚动状态回归空闲时触发，控制器提供的无动画方法控制滚动时触发。 |  
| Scroll | 1 | 滚动状态。手指拖动List，拖动滚动条和滚动鼠标滚轮时触发。|  
| Fling | 2 | 惯性滚动状态。动画控制的滚动都会触发。包括快速划动松手后的惯性滚动， <br/>划动到边缘回弹的滚动，快速拖动内置滚动条松手后的惯性滚动， <br/>使用滚动控制器提供的带动画的方法控制的滚动。 |

## VisibleListContentInfo<sup>12+</sup>对象说明

用于表示List可见内容区子组件的详细信息。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

| 名称 | 类型 | 只读 | 可选 | 说明 |  
| ------ | ------ | -- | ------ | ------|  
| index | number | 否 | 否 | 表示ListItem或ListItemGroup在List中的索引值。 |  
| itemGroupArea | [ListItemGroupArea]{@link ListItemGroupArea} | 否 | 是 | 表示处于ListItemGroup的哪一个区域。 |  
| itemIndexInGroup | number | 否 | 是 | 表示ListItem在ListItemGroup中的索引值。 |

## ListItemGroupArea<sup>12+</sup>枚举说明

枚举了ListItemGroup各个区域。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

| 名称 | 值 | 说明 |  
| ------ | ------ | ---------------------------------------- |  
| NONE | 0 | ListItemGroup内部ListItem区域、header区域以及footer区域以外的区域。 |  
| IN_LIST_ITEM_AREA | 1 | ListItemGroup内部ListItem区域。 |  
| IN_HEADER_AREA | 2 | ListItemGroup内部header区域。 |  
| IN_FOOTER_AREA | 3 | ListItemGroup内部footer区域。 |

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
| options | [ListOptions](arkts-arkui-listoptions-i.md) | 否 | 设置List组件参数。 |

## 汇总

- [ChainAnimationOptions](arkts-arkui-list-chainanimationoptions-i-sys.md)
- [CloseSwipeActionOptions](arkts-arkui-list-closeswipeactionoptions-i.md)
- [ListBackPressBehavior](arkts-arkui-list-listbackpressbehavior-i.md)
- [ListDividerOptions](arkts-arkui-list-listdivideroptions-i.md)
- [ListOptions](arkts-arkui-list-listoptions-i.md)
- [UIListEvent](arkts-arkui-list-uilistevent-i.md)
- [VisibleListContentInfo](arkts-arkui-list-visiblelistcontentinfo-i.md)
- [OnListScrollIndexCallback](arkts-arkui-list-onlistscrollindexcallback-t.md)
- [OnScrollVisibleContentChangeCallback](arkts-arkui-list-onscrollvisiblecontentchangecallback-t.md)
- [ChainEdgeEffect](arkts-arkui-list-chainedgeeffect-e-sys.md)
- [ListItemAlign](arkts-arkui-list-listitemalign-e.md)
- [ListItemGroupArea](arkts-arkui-list-listitemgrouparea-e.md)
- [ScrollSnapAlign](arkts-arkui-list-scrollsnapalign-e.md)
- [ScrollSnapAnimationSpeed](arkts-arkui-list-scrollsnapanimationspeed-e.md)
- [ScrollState](arkts-arkui-list-scrollstate-e.md)
- [StickyStyle](arkts-arkui-list-stickystyle-e.md)
