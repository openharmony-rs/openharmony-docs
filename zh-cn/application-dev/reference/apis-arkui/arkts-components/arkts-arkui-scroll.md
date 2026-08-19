# Scroll

可滚动的容器组件，当子组件的布局尺寸超过父组件的尺寸时，内容可以滚动。支持设置滚动方向、滚动条、边缘效果、嵌套滚动以及自由滚动缩放等能力，适用于内容超出显示区域或需要复杂滚动交互的场景。 > **说明：** > > - 该组件嵌套List子组件滚动时，若List不设置宽高，则默认全部加载。在对性能有要求的场景下，开发者应指定List的宽高，以避免默认全部加载影响性能。 > > - 该组件滚动的前提是主轴方向大小小于内容大小。 > > - Scroll组件通用属性clip的默认值为true。 > > - Scroll组件的高度超出屏幕显示范围时，可以通过设置通用属性layoutWeight让Scroll高度适应主轴的剩余空间。 > > - 手指触摸屏幕时，会停止当前触摸范围内所有滚动组件的滚动动画（[scrollTo](arkts-arkui-scroller-c.md#scrollto)和[scrollToIndex](arkts-arkui-scroller-c.md#scrolltoindex)接口 > 触发的滚动动画除外），包括边缘回弹动画。 > > - 组件内部已绑定手势实现跟手滚动等功能，需要增加自定义手势操作时请参考手势拦截增强进行处理。

## 子组件 支持单个子组件。 > 从API version 21开始，Scroll单个子组件的宽高最大为16777216px；API version 20及之前，Scroll单个子组件的宽高最大为1000000px。子组件超出该大小可能导致滚动或显示异常。

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
| scroller | [Scroller](arkts-arkui-scroller-c.md) | 否 |  |

## 汇总

### 接口

| 名称 | 说明 |
| --- | --- |
| [OffsetOptions](arkts-arkui-offsetoptions-i.md) | 初始滚动偏移量的参数选项。 |
| [OffsetResult](arkts-arkui-offsetresult-i.md) | 滑动偏移量对象。 |
| [OnScrollFrameBeginHandlerResult](arkts-arkui-onscrollframebeginhandlerresult-i.md) | [OnScrollFrameBeginCallback](arkts-arkui-onscrollframebegincallback-t.md)返回的实际相对上一帧滚动偏移量。 @since版本号高于内层元素版本号的情况，但这不影响接口的使用。 |
| [ScrollAnimationOptions](arkts-arkui-scrollanimationoptions-i.md) | 自定义滚动动效的参数选项。 |
| [ScrollEdgeOptions](arkts-arkui-scrolledgeoptions-i.md) | 滚动到边缘位置的参数选项。 |
| [ScrollOptions](arkts-arkui-scrolloptions-i.md) | 滚动到指定位置的参数选项。 @since版本号高于内层元素版本号的情况，但这不影响接口的使用。 |
| [ScrollPageOptions](arkts-arkui-scrollpageoptions-i.md) | 翻页模式的参数选项。 |
| [ScrollSnapOptions](arkts-arkui-scrollsnapoptions-i.md) | 限位滚动模式对象。 |
| [ScrollToIndexOptions](arkts-arkui-scrolltoindexoptions-i.md) | 滑动到指定Index的参数选项。 |
| [UIScrollEvent](arkts-arkui-uiscrollevent-i.md) | frameNode中[getEvent('Scroll')](../arkts-apis/arkts-arkui-typenode-getevent-f.md) 方法的返回值，可用于给Scroll节点设置滚动事件。 UIScrollEvent继承于UIScrollableCommonEvent。 |

### 类型

| 名称 | 说明 |
| --- | --- |
| [OnScrollEdgeCallback](arkts-arkui-onscrolledgecallback-t.md) | 滚动到边缘时触发的回调。 |
| [OnScrollFrameBeginCallback](arkts-arkui-onscrollframebegincallback-t.md) | Scroll每帧滚动前触发的回调。 |
| [ScrollOnDidZoomCallback](arkts-arkui-scrollondidzoomcallback-t.md) | Scroll每帧缩放完成时触发的回调。 |
| [ScrollOnScrollCallback](arkts-arkui-scrollonscrollcallback-t.md) | Scroll滚动时触发的回调。 |
| [ScrollOnWillScrollCallback](arkts-arkui-scrollonwillscrollcallback-t.md) | Scroll滚动前触发的回调。 |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [ScrollAlign](arkts-arkui-scrollalign-e.md) | 对齐方式枚举。 |
| [ScrollDirection](arkts-arkui-scrolldirection-e.md) | 滚动方向枚举。 FREE（自由滚动）模式下支持的能力： |

