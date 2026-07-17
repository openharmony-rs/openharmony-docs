# Scroll

可滚动的容器组件，当子组件的布局尺寸超过父组件的尺寸时，内容可以滚动。

> **说明：**
>
> - 该组件嵌套List子组件滚动时，若List不设置宽高，则默认全部加载，在对性能有要求的场景下建议指定List的宽高。
> - 该组件滚动的前提是主轴方向大小小于内容大小。
> - Scroll组件通用属性clip的默认值为true。
>

## 子组件

支持单个子组件。

## Scroll

```TypeScript
Scroll(scroller?: Scroller)
```

创建Scroll滚动容器。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-ScrollInterface-(scroller?: Scroller): ScrollAttribute--><!--Device-ScrollInterface-(scroller?: Scroller): ScrollAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数:**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| scroller | Scroller | 否 |  |

## 汇总

- [OffsetOptions](arkts-arkui-scroll-offsetoptions-i.md)
- [OffsetResult](arkts-arkui-scroll-offsetresult-i.md)
- [OnScrollFrameBeginHandlerResult](arkts-arkui-scroll-onscrollframebeginhandlerresult-i.md)
- [ScrollAnimationOptions](arkts-arkui-scroll-scrollanimationoptions-i.md)
- [ScrollEdgeOptions](arkts-arkui-scroll-scrolledgeoptions-i.md)
- [ScrollOptions](arkts-arkui-scroll-scrolloptions-i.md)
- [ScrollPageOptions](arkts-arkui-scroll-scrollpageoptions-i.md)
- [ScrollSnapOptions](arkts-arkui-scroll-scrollsnapoptions-i.md)
- [ScrollToIndexOptions](arkts-arkui-scroll-scrolltoindexoptions-i.md)
- [UIScrollEvent](arkts-arkui-scroll-uiscrollevent-i.md)
- [OnScrollEdgeCallback](arkts-arkui-scroll-onscrolledgecallback-t.md)
- [OnScrollFrameBeginCallback](arkts-arkui-scroll-onscrollframebegincallback-t.md)
- [ScrollOnDidZoomCallback](arkts-arkui-scroll-scrollondidzoomcallback-t.md)
- [ScrollOnScrollCallback](arkts-arkui-scroll-scrollonscrollcallback-t.md)
- [ScrollOnWillScrollCallback](arkts-arkui-scroll-scrollonwillscrollcallback-t.md)
- [ScrollAlign](arkts-arkui-scroll-scrollalign-e.md)
- [ScrollDirection](arkts-arkui-scroll-scrolldirection-e.md)
