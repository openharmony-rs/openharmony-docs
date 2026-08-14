# Scroll

可滚动的容器组件，当子组件的布局尺寸超过父组件的尺寸时，内容可以滚动。支持设置滚动方向、滚动条、边缘效果、嵌套滚动以及自由滚动缩放等能力，适用于内容超出显示区域或需要复杂滚动交互的场景。 > **说明：** > > - 该组件嵌套List子组件滚动时，若List不设置宽高，则默认全部加载。在对性能有要求的场景下，开发者应指定List的宽高，以避免默认全部加载影响性能。 > > - 该组件滚动的前提是主轴方向大小小于内容大小。 > > - Scroll组件通用属性clip的默认值为true。 > > - Scroll组件的高度超出屏幕显示范围时，可以通过设置通用属性layoutWeight让Scroll高度适应主轴的剩余空间。 > > - 手指触摸屏幕时，会停止当前触摸范围内所有滚动组件的滚动动画（[scrollTo](arkts-arkui-scroller-c.md#scrollTo)和[scrollToIndex](arkts-arkui-scroller-c.md#scrollToIndex)接口 > 触发的滚动动画除外），包括边缘回弹动画。 > > - 组件内部已绑定手势实现跟手滚动等功能，需要增加自定义手势操作时请参考手势拦截增强进行处理。

## 子组件 支持单个子组件。 > 从API version 21开始，Scroll单个子组件的宽高最大为16777216px；API version 20及之前，Scroll单个子组件的宽高最大为1000000px。子组件超出该大小可能导致滚动或显示异常。

## Scroll

```TypeScript
Scroll(scroller?: Scroller)
```

创建Scroll滚动容器。

**起始版本：** 7

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为7。

**废弃版本：** -1

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-ScrollInterface-(scroller?: Scroller): ScrollAttribute--><!--Device-ScrollInterface-(scroller?: Scroller): ScrollAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数:**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| scroller | [Scroller](arkts-arkui-scroller-c.md) | 否 |  |

## 汇总

- [OffsetOptions](arkts-arkui-offsetoptions-i.md)
- [OffsetResult](arkts-arkui-offsetresult-i.md)
- [OnScrollFrameBeginHandlerResult](arkts-arkui-onscrollframebeginhandlerresult-i.md)
- [ScrollAnimationOptions](arkts-arkui-scrollanimationoptions-i.md)
- [ScrollEdgeOptions](arkts-arkui-scrolledgeoptions-i.md)
- [ScrollOptions](arkts-arkui-scrolloptions-i.md)
- [ScrollPageOptions](arkts-arkui-scrollpageoptions-i.md)
- [ScrollSnapOptions](arkts-arkui-scrollsnapoptions-i.md)
- [ScrollToIndexOptions](arkts-arkui-scrolltoindexoptions-i.md)
- [UIScrollEvent](arkts-arkui-uiscrollevent-i.md)
- [OnScrollEdgeCallback](arkts-arkui-onscrolledgecallback-t.md)
- [OnScrollFrameBeginCallback](arkts-arkui-onscrollframebegincallback-t.md)
- [ScrollOnDidZoomCallback](arkts-arkui-scrollondidzoomcallback-t.md)
- [ScrollOnScrollCallback](arkts-arkui-scrollonscrollcallback-t.md)
- [ScrollOnWillScrollCallback](arkts-arkui-scrollonwillscrollcallback-t.md)
- [ScrollAlign](arkts-arkui-scrollalign-e.md)
- [ScrollDirection](arkts-arkui-scrolldirection-e.md)
