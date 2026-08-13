# scroll

## 汇总

### 类

| 名称 | 说明 |
| --- | --- |
| [Scroller](arkts-na-scroll-scroller-c.md) | 可滚动容器组件的控制器，可以将此组件绑定至容器组件，然后通过它控制容器组件的滚动。同一个控制器不可以控制多个容器组件，目前支持绑定到ArcList、 ArcScrollBar、List、Scroll、ScrollBar、 Grid、WaterFlow上。 |

### 接口

| 名称 | 说明 |
| --- | --- |
| [OffsetOptions](arkts-na-scroll-offsetoptions-i.md) | 初始滚动偏移量的参数选项。 |
| [OffsetResult](arkts-na-scroll-offsetresult-i.md) | 滑动偏移量对象。 |
| [OnScrollFrameBeginHandlerResult](arkts-na-scroll-onscrollframebeginhandlerresult-i.md) | [OnScrollFrameBeginCallback]返回的实际相对上一帧滚动偏移量。 |
| [ScrollAnimationOptions](arkts-na-scroll-scrollanimationoptions-i.md) | 自定义滚动动效的参数选项。 |
| [ScrollEdgeOptions](arkts-na-scroll-scrolledgeoptions-i.md) | 滚动到边缘位置的参数选项。 |
| [ScrollOptions](arkts-na-scroll-scrolloptions-i.md) | 滚动到指定位置的参数选项。 |
| [ScrollPageOptions](arkts-na-scroll-scrollpageoptions-i.md) | 翻页模式的参数选项。 |
| [ScrollSnapOptions](arkts-na-scroll-scrollsnapoptions-i.md) | 限位滚动模式对象。 |
| [ScrollToIndexOptions](arkts-na-scroll-scrolltoindexoptions-i.md) | 滑动到指定Index的参数选项。 |
| [UIScrollEvent](arkts-na-scroll-uiscrollevent-i.md) | frameNode中getEvent('Scroll')方法的返回值，可用于给 Scroll节点设置滚动事件。 UIScrollEvent继承于UIScrollableCommonEvent。 |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [ScrollAlign](arkts-na-scroll-scrollalign-e.md) | 对齐方式枚举。 |
| [ScrollDirection](arkts-na-scroll-scrolldirection-e.md) | 滚动方向枚举。 |

### 类型

| 名称 | 说明 |
| --- | --- |
| [OnScrollEdgeCallback](arkts-na-onscrolledgecallback-t.md) | 滚动到边缘时触发的回调。 |
| [OnScrollFrameBeginCallback](arkts-na-onscrollframebegincallback-t.md) | Scroll每帧滚动前触发的回调。 |
| [ScrollOnDidZoomCallback](arkts-na-scrollondidzoomcallback-t.md) | Scroll每帧缩放完成时触发的回调。 |
| [ScrollOnScrollCallback](arkts-na-scrollonscrollcallback-t.md) | Scroll滚动时触发的回调。 |
| [ScrollOnWillScrollCallback](arkts-na-scrollonwillscrollcallback-t.md) | Scroll滚动前触发的回调。 |

