# ListItemGroup

该组件用来展示列表项分组，支持自定义分组头部和尾部区域、卡片样式、分割线、懒加载与预加载等能力，适用于需要对列表项进行逻辑分组展示的场景。宽度默认充满List组件，必须配合List组件来使用。 ListItemGroup的懒加载是指组件按需加载可见区域内的子组件。相比全量加载，使用懒加载可以提升应用启动速度，减少内存消耗。ListItemGroup和 [ForEach](../../../ui/rendering-control/arkts-rendering-control-foreach.md)、 [LazyForEach](../../../ui/rendering-control/arkts-rendering-control-lazyforeach.md)、 [Repeat](../../../ui/rendering-control/arkts-new-rendering-control-repeat.md)结合，懒加载能力存在差异： - 当ListItemGroup和ForEach结合，会一次性创建所有的子组件，在需要的时候布局和渲染屏幕范围内的节点。当用户滑动时，滑出屏幕范围的节点不会下树销毁，滑入屏幕范围的节点会布局和渲染。 - 当ListItemGroup和LazyForEach结合，会一次性创建、布局、渲染屏幕范围的节点。当用户滑动时，滑出屏幕范围的节点会下树销毁，滑入屏幕范围的节点会创建、布局、渲染。 - 当ListItemGroup和带virtualScroll的Repeat结合，它的懒加载行为和LazyForEach一致。当ListItemGroup和 不带virtualScroll的Repeat结合，它的懒加载行为和ForEach一致。 ListItemGroup的预加载是指除了加载显示区域内的子组件外，还支持空闲时隙提前加载部分显示区域外的子组件。使用预加载可以减少滚动丢帧，提升流畅性。预加载需要结合懒加载才会生效。ListItemGroup和 [ForEach](../../../ui/rendering-control/arkts-rendering-control-foreach.md)、 [LazyForEach](../../../ui/rendering-control/arkts-rendering-control-lazyforeach.md)、 [Repeat](../../../ui/rendering-control/arkts-new-rendering-control-repeat.md)结合，预加载能力存在差异： - 当ListItemGroup和ForEach结合，如果设置了cachedCount，除了会布局显示区域内子组件外，还会在空闲时隙根 据List组件的cachedCount属性预布局显示区域外cachedCount范围内的子组件。 - 当ListItemGroup和LazyForEach结合，如果设置了cachedCount，除了会创建和布局显示区域内子组件外，还 会在空闲时隙根据List组件的cachedCount属性预创建和预布局显示区域外cachedCount范围内的子组件。 - 当ListItemGroup和带virtualScroll的Repeat结合，它的预加载行为和LazyForEach一致。当ListItemGroup和 不带virtualScroll的Repeat结合，它的预加载行为和ForEach一致。 > **说明：** > > - 该组件的父组件只能是List。 > > - ListItemGroup组件不支持设置通用属性aspectRatio。 > > - 当ListItemGroup的父组件List的listDirection属性为Axis.Vertical时，设置 > 通用属性height不生效。ListItemGroup的高度为header高度、footer高度和所有ListItem布局后总高度之和。 > > - 当父组件List的listDirection属性为Axis.Horizontal时，设置通用属性width不生效。ListItemGroup > 的宽度为header宽度、footer宽度和所有ListItem布局后总宽度之和。 > > - ListItemGroup使用direction属性设置布局方向不生效，ListItemGroup组件布局方向跟随父容器List组件的布局方向。

## 子组件 包含ListItem子组件。支持通过渲染控制类型（ [if/else](../../../ui/rendering-control/arkts-rendering-control-ifelse.md)、 [ForEach](../../../ui/rendering-control/arkts-rendering-control-foreach.md)、 [LazyForEach](../../../ui/rendering-control/arkts-rendering-control-lazyforeach.md)和 [Repeat](../../../ui/rendering-control/arkts-new-rendering-control-repeat.md)）动态生成子组件，更推荐使用LazyForEach或Repeat以优化性能。

## ListItemGroup

```TypeScript
ListItemGroup(options?: ListItemGroupOptions)
```

创建ListItemGroup组件。该组件的父组件只能是List组件。

**起始版本：** 9

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为9。

**废弃版本：** -1

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-ListItemGroupInterface-(options?: ListItemGroupOptions): ListItemGroupAttribute--><!--Device-ListItemGroupInterface-(options?: ListItemGroupOptions): ListItemGroupAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数:**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [ListItemGroupOptions](arkts-arkui-listitemgroupoptions-i.md) | 否 | ListItemGroup组件参数，用于配置header、footer、间距和样式等。不传入时使用默认配置（无header、footer，间距为 0，无卡片样式）。 |

## 汇总

- [ListItemGroupOptions](arkts-arkui-listitemgroupoptions-i.md)
- [ListItemGroupHeaderFooterStyle](arkts-arkui-listitemgroupheaderfooterstyle-e.md)
- [ListItemGroupStyle](arkts-arkui-listitemgroupstyle-e.md)
