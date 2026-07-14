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


## List

```TypeScript
List(options?: ListOptions)
```

创建List列表容器。

**起始版本：** 7

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数:**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | ListOptions | 否 | 设置List组件参数。 |

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
