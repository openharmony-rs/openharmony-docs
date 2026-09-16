# Scroll

可滚动的容器组件，当子组件的布局尺寸超过父组件的尺寸时，内容可以滚动。支持设置滚动方向、滚动条、边缘效果、嵌套滚动以及自由滚动缩放等能力，适用于内容超出显示区域或需要复杂滚动交互的场景。

> **说明：** > > - 该组件嵌套List子组件滚动时，若List不设置宽高，则默认全部加载。在对性能有要求的场景下，开发者应指定List的宽高，以避免默认全部加载影响性能。 > > - 该组件滚动的前提是主轴方向大小小于内容大小。 > > - Scroll组件通用属性clip的默认值为true。 > > - Scroll组件的高度超出屏幕显示范围时，可以通过设置通用属性[layoutWeight](arkts-arkui-commonmethod-c.md#layoutweight)让Scroll高度适应主轴的剩余空间。 > > - 手指触摸屏幕时，会停止当前触摸范围内所有滚动组件的滚动动画（[scrollTo](arkts-arkui-scroller-c.md#scrollto)和[scrollToIndex](arkts-arkui-scroller-c.md#scrolltoindex)接口 > 触发的滚动动画除外），包括边缘回弹动画。 > > - 组件内部已绑定手势实现跟手滚动等功能，需要增加自定义手势操作时请参考手势拦截增强进行处理。

## 子组件

支持单个子组件。

> 从API version 21开始，Scroll单个子组件的宽高最大为16777216px；API version 20及之前，Scroll单个子组件的宽高最大为1000000px。子组件超出该大小可能导致滚动或显示异常。

## Scroll

```TypeScript
Scroll(scroller?: Scroller)
```

创建Scroll滚动容器。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

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
| [OnScrollFrameBeginHandlerResult](arkts-arkui-onscrollframebeginhandlerresult-i.md) | [OnScrollFrameBeginCallback](arkts-arkui-onscrollframebegincallback-t.md)返回的实际相对上一帧滚动偏移量。 |
| [ScrollAnimationOptions](arkts-arkui-scrollanimationoptions-i.md) | 自定义滚动动效的参数选项。 |
| [ScrollEdgeOptions](arkts-arkui-scrolledgeoptions-i.md) | 滚动到边缘位置的参数选项。 |
| [ScrollOptions](arkts-arkui-scrolloptions-i.md) | 滚动到指定位置的参数选项。 |
| [ScrollPageOptions](arkts-arkui-scrollpageoptions-i.md) | 翻页模式的参数选项。 |
| [ScrollSnapOptions](arkts-arkui-scrollsnapoptions-i.md) | 限位滚动模式对象。 |
| [ScrollToIndexOptions](arkts-arkui-scrolltoindexoptions-i.md) | 滑动到指定Index的参数选项。 |
| [UIScrollEvent](arkts-arkui-uiscrollevent-i.md) | frameNode中[getEvent('Scroll')](../arkts-apis/arkts-arkui-typenode-getevent-f.md)方法的返回值，可用于给Scroll节点设置滚动事件。 |

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
| [ScrollDirection](arkts-arkui-scrolldirection-e.md) | 滚动方向枚举。 |

## 示例

```TypeScript
### 示例1（设置scroller控制器）

该示例展示了Scroll组件部分属性和scroller控制器的使用。


```

```TypeScript
### 示例2（嵌套滚动实现方式一）

该示例使用onScrollFrameBegin事件实现了内层List组件和外层Scroll组件的嵌套滚动。


```

```TypeScript
### 示例3（嵌套滚动实现方式二）

该示例使用[nestedScroll](#nestedscroll10)属性实现了内层List组件和外层Scroll组件的嵌套滚动。


```

```TypeScript
### 示例4（嵌套滚动父组件向子组件传递滚动）

该示例使用[enableScrollInteraction](#enablescrollinteraction10)属性和[onScrollFrameBegin](#onscrollframebegin9)事件实现了父组件向子组件传递滚动。


```

```TypeScript
### 示例5（设置限位滚动）

该示例实现了Scroll组件的限位滚动。


```

```TypeScript
### 示例6（获取子组件索引）

该示例展示了如何获得List组件的子组件索引。


```

```TypeScript
### 示例7（设置边缘渐隐）

该示例实现了Scroll组件开启边缘渐隐效果并设置边缘渐隐长度。


```

```TypeScript
### 示例8（单边边缘效果）

该示例通过[edgeEffect](#edgeeffect)接口，实现了Scroll组件设置单边边缘效果。


```

```TypeScript
### 示例9（滑动翻页效果）

该示例通过[enablePaging](arkts-arkui-scroll-comp-attribute.md#enablepaging)接口，实现了Scroll组件滑动翻页效果。


```

```TypeScript
### 示例10（设置过界停留）

该示例通过[scrollTo](#scrollto)接口，实现了Scroll组件设置过界停留效果。


```

```TypeScript
### 示例11（自由滚动和缩放）

从API version 20开始，该示例实现了Scroll组件自由滚动和缩放效果。


```

```TypeScript
### 示例12（获取内容总大小）

从API version 22 开始，该示例实现了获取内容总大小的功能。


```

```TypeScript
### 示例13（设置滚动事件）

该示例通过FrameNode中的getEvent('Scroll')获取[UIScrollEvent](arkts-arkui-uiscrollevent-i.md)，并为Scroll设置滚动事件回调，用于事件监听方因无法直接修改页面代码而无法使用声明式接口设置回调的场景。

从API version 19开始，新增UIScrollEvent接口。
```
