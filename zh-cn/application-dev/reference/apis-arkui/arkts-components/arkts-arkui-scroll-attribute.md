# Scroll属性/事件

定义Scroll组件的属性函数。

**继承/实现关系：** ScrollAttribute extends [ScrollableCommonMethod<ScrollAttribute>](ScrollableCommonMethod<ScrollAttribute>)

**起始版本：** 7

<!--Device-unnamed-declare class ScrollAttribute extends ScrollableCommonMethod<ScrollAttribute>--><!--Device-unnamed-declare class ScrollAttribute extends ScrollableCommonMethod<ScrollAttribute>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

<a id="edgeeffect"></a>
## edgeEffect

```TypeScript
edgeEffect(edgeEffect: EdgeEffect, options?: EdgeEffectOptions)
```

设置边缘滑动效果。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-ScrollAttribute-edgeEffect(edgeEffect: EdgeEffect, options?: EdgeEffectOptions): ScrollAttribute--><!--Device-ScrollAttribute-edgeEffect(edgeEffect: EdgeEffect, options?: EdgeEffectOptions): ScrollAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| edgeEffect | [EdgeEffect](../arkts-apis/arkts-arkui-edgeeffect-e.md) | 是 | Scroll组件的边缘滑动效果，支持弹簧效果和阴影效果。<br>默认值：<em>EdgeEffect.None</em> |
| options | [EdgeEffectOptions](arkts-arkui-edgeeffectoptions-i.md) | 否 | 组件内容大小小于组件自身时，是否开启滑动效果。设置为{ alwaysEnabled: true }会开启滑动效果，{ alwaysEnabled: false }不开启。<br>默认值：<em>{ alwaysEnabled: true }</em><br>**起始版本：** 11 |

<a id="enablebounceszoom"></a>
## enableBouncesZoom

```TypeScript
enableBouncesZoom(enable: boolean)
```

启用过缩放回弹效果。

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-ScrollAttribute-enableBouncesZoom(enable: boolean): ScrollAttribute--><!--Device-ScrollAttribute-enableBouncesZoom(enable: boolean): ScrollAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| enable | boolean | 是 | 启用过缩放回弹效果。设置为true表示启用该效果，设置为false表示禁用该效果。<br>默认值：true。 |

<a id="enablepaging"></a>
## enablePaging

```TypeScript
enablePaging(value: boolean)
```

设置是否支持划动翻页。如果同时设置了划动翻页enablePaging和限位滚动scrollSnap，则scrollSnap优先生效，enablePaging不生效。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-ScrollAttribute-enablePaging(value: boolean): ScrollAttribute--><!--Device-ScrollAttribute-enablePaging(value: boolean): ScrollAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | boolean | 是 | 是否支持划动翻页。设置为true支持滑动翻页，false不支持。<br>默认值：<em>false</em> |

<a id="enablescrollinteraction"></a>
## enableScrollInteraction

```TypeScript
enableScrollInteraction(value: boolean)
```

设置是否支持滚动手势。设置为false时不支持手指或鼠标滚动，但不影响控制器的滚动接口。组件无法通过鼠标按下拖动操作进行滚动。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-ScrollAttribute-enableScrollInteraction(value: boolean): ScrollAttribute--><!--Device-ScrollAttribute-enableScrollInteraction(value: boolean): ScrollAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | boolean | 是 | 是否支持滚动手势。设置为true时可以通过手指或者鼠标滚动，设置为false时无法通过手指或者鼠标滚动，但不影响控制器的滚动接口。<br>默认值：<em>true</em> |

<a id="friction"></a>
## friction

```TypeScript
friction(value: number | Resource)
```

设置摩擦系数，手动划动滚动区域时生效，仅影响惯性滚动过程，对惯性滚动过程中的链式效果有间接影响。设置为小于等于0的值时，按默认值处理。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-ScrollAttribute-friction(value: number | Resource): ScrollAttribute--><!--Device-ScrollAttribute-friction(value: number | Resource): ScrollAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | number \| Resource | 是 | 摩擦系数。<br>默认值：非可穿戴设备为<em>0.6</em>，可穿戴设备为<em>0.9</em><br>从API version 11开始，非可穿戴设备默认值为<em>0.7</em>。<br>从API version 12开始，非可穿戴设备默认值为<em>0.75</em>。 |

<a id="initialoffset"></a>
## initialOffset

```TypeScript
initialOffset(value: OffsetOptions)
```

设置初始滚动偏移量。只在首次布局时生效，后续动态修改该属性值不生效。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-ScrollAttribute-initialOffset(value: OffsetOptions): ScrollAttribute--><!--Device-ScrollAttribute-initialOffset(value: OffsetOptions): ScrollAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [OffsetOptions](arkts-arkui-offsetoptions-i.md) | 是 | 初始滚动偏移量。当输入的大小为百分比时，初始滚动偏移量为Scroll组件主轴方向大小与百分比数值之积。 |

<a id="maxzoomscale"></a>
## maxZoomScale

```TypeScript
maxZoomScale(scale: number)
```

设置Scroll组件内容的最大手势缩放比例。

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-ScrollAttribute-maxZoomScale(scale: number): ScrollAttribute--><!--Device-ScrollAttribute-maxZoomScale(scale: number): ScrollAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| scale | number | 是 | Scroll组件内容的最大手势缩放比例。<br>默认值：1。<br>取值范围：(0, +∞)，小于或等于0时按默认值1处理。 |

<a id="minzoomscale"></a>
## minZoomScale

```TypeScript
minZoomScale(scale: number)
```

设置Scroll组件内容的最小手势缩放比例。当maxZoomScale和minZoomScale不同时为1时，Scroll组件会启用缩放手势。

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-ScrollAttribute-minZoomScale(scale: number): ScrollAttribute--><!--Device-ScrollAttribute-minZoomScale(scale: number): ScrollAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| scale | number | 是 | Scroll组件内容的最小手势缩放比例。<br>默认值：1。<br>取值范围：(0, maxZoomScale]。大于maxZoomScale时按maxZoomScale处理。 |

<a id="nestedscroll"></a>
## nestedScroll

```TypeScript
nestedScroll(value: NestedScrollOptions)
```

设置前后两个方向的嵌套滚动模式，实现与父组件的滚动联动。Scroll设置enablePaging或者scrollSnap，并同时设置父组件优先的嵌套滚动时，嵌套滚动不生效。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-ScrollAttribute-nestedScroll(value: NestedScrollOptions): ScrollAttribute--><!--Device-ScrollAttribute-nestedScroll(value: NestedScrollOptions): ScrollAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [NestedScrollOptions](arkts-arkui-nestedscrolloptions-i.md) | 是 | 嵌套滚动选项。<br>默认值：<em>{ scrollForward: NestedScrollMode.SELF_ONLY, scrollBackward: NestedScrollMode.SELF_ONLY}</em> |

<a id="ondidscroll"></a>
## onDidScroll

```TypeScript
onDidScroll(handler: ScrollOnScrollCallback)
```

滚动事件回调，Scroll滚动时触发。

<p><strong>说明</strong><br>1、滚动组件触发滚动时触发，支持键鼠操作等其他触发滚动的输入设置。<br>2、通过滚动控制器API接口调用。<br>3、越界回弹。</p>

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-ScrollAttribute-onDidScroll(handler: ScrollOnScrollCallback): ScrollAttribute--><!--Device-ScrollAttribute-onDidScroll(handler: ScrollOnScrollCallback): ScrollAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| handler | [ScrollOnScrollCallback](arkts-arkui-scrollonscrollcallback-t.md) | 是 | Scroll滚动时触发的回调。 |

<a id="ondidzoom"></a>
## onDidZoom

```TypeScript
onDidZoom(event: ScrollOnDidZoomCallback)
```

每帧缩放完成时触发。

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-ScrollAttribute-onDidZoom(event: ScrollOnDidZoomCallback): ScrollAttribute--><!--Device-ScrollAttribute-onDidZoom(event: ScrollOnDidZoomCallback): ScrollAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | [ScrollOnDidZoomCallback](arkts-arkui-scrollondidzoomcallback-t.md) | 是 | 每帧缩放完成时回调。 |

<a id="onscroll"></a>
## onScroll

```TypeScript
onScroll(event: (xOffset: number, yOffset: number) => void)
```

滚动事件回调，返回滚动时水平、竖直方向偏移量，单位vp。

<p><strong>说明</strong><br>1、滚动组件触发滚动时触发，支持键鼠操作等其他触发滚动的输入设置。<br>2、通过滚动控制器API接口调用。<br>3、越界回弹。</p>

**起始版本：** 7

**废弃版本：** 12

**替代接口：** onWillScroll

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-ScrollAttribute-onScroll(event: (xOffset: number, yOffset: number) => void): ScrollAttribute--><!--Device-ScrollAttribute-onScroll(event: (xOffset: number, yOffset: number) => void): ScrollAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | (xOffset: number, yOffset: number) =&gt; void | 是 | callback when scroll,xOffset: 相对于上一帧水平方向的偏移量，Scroll中的内容向左滚动时偏移量为正，向右滚动时偏移量为负。<br/>单位vp。yOffset: 相对于上一帧竖直方向的偏移量，Scroll中的内容向上滚动时偏移量为正，向下滚动时偏移量为负。<br/>单位vp。 |

<a id="onscrolledge"></a>
## onScrollEdge

```TypeScript
onScrollEdge(event: OnScrollEdgeCallback)
```

滚动到边缘事件回调。

<p><strong>说明</strong><br>1、滚动组件滚动到边缘时触发，支持键鼠操作等其他触发滚动的输入设置。<br>2、通过滚动控制器API接口调用。<br>3、越界回弹。</p>

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-ScrollAttribute-onScrollEdge(event: OnScrollEdgeCallback): ScrollAttribute--><!--Device-ScrollAttribute-onScrollEdge(event: OnScrollEdgeCallback): ScrollAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | [OnScrollEdgeCallback](arkts-arkui-onscrolledgecallback-t.md) | 是 | 滚动到的边缘位置。<br>**起始版本：** 18 |

<a id="onscrollend"></a>
## onScrollEnd

```TypeScript
onScrollEnd(event: () => void)
```

滚动停止事件回调。

<p><strong>说明</strong><br>1、滚动组件触发滚动后停止，支持键鼠操作等其他触发滚动的输入设置。<br>2、通过滚动控制器API接口调用后停止，带过渡动效。</p>

**起始版本：** 7

**废弃版本：** 9

**替代接口：** onScrollStop

<!--Device-ScrollAttribute-onScrollEnd(event: () => void): ScrollAttribute--><!--Device-ScrollAttribute-onScrollEnd(event: () => void): ScrollAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | () =&gt; void | 是 |  |

<a id="onscrollframebegin"></a>
## onScrollFrameBegin

```TypeScript
onScrollFrameBegin(event: OnScrollFrameBeginCallback)
```

每帧滚动开始前触发。

<p><strong>说明</strong><br>满足以下任一条件时触发该事件：<br>1. 用户交互（如手指滑动、键鼠操作等）触发滚动。<br>2. Scroll惯性滚动。<br>3. 调用fling接口触发滚动。<br>不触发该事件的条件：<br>1. 调用除fling接口外的其他滚动控制接口。<br>2. 越界回弹。<br>3. 拖动滚动条。</p>

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-ScrollAttribute-onScrollFrameBegin(event: OnScrollFrameBeginCallback): ScrollAttribute--><!--Device-ScrollAttribute-onScrollFrameBegin(event: OnScrollFrameBeginCallback): ScrollAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | [OnScrollFrameBeginCallback](arkts-arkui-onscrollframebegincallback-t.md) | 是 | 每帧滚动开始回调函数。<br>**起始版本：** 18 |

<a id="onscrollstart"></a>
## onScrollStart

```TypeScript
onScrollStart(event: VoidCallback)
```

滚动开始时触发。

<p><strong>说明</strong><br>1、滚动组件开始滚动时触发，支持键鼠操作等其他触发滚动的输入设置。<br>2、通过滚动控制器API接口调用后开始，带过渡动效。</p>

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-ScrollAttribute-onScrollStart(event: VoidCallback): ScrollAttribute--><!--Device-ScrollAttribute-onScrollStart(event: VoidCallback): ScrollAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | [VoidCallback](../arkts-apis/arkts-arkui-voidcallback-t.md) | 是 | 滚动开始回调。<br>**起始版本：** 18 |

<a id="onscrollstop"></a>
## onScrollStop

```TypeScript
onScrollStop(event: VoidCallback)
```

滚动停止时触发。

<p><strong>说明</strong><br>1、滚动组件触发滚动后停止，支持键鼠操作等其他触发滚动的输入设置。<br>2、通过滚动控制器API接口调用后停止，带过渡动效。</p>

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-ScrollAttribute-onScrollStop(event: VoidCallback): ScrollAttribute--><!--Device-ScrollAttribute-onScrollStop(event: VoidCallback): ScrollAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | [VoidCallback](../arkts-apis/arkts-arkui-voidcallback-t.md) | 是 | 滚动停止回调。<br>**起始版本：** 18 |

<a id="onwillscroll"></a>
## onWillScroll

```TypeScript
onWillScroll(handler: ScrollOnWillScrollCallback)
```

滚动事件回调，Scroll滚动前触发。

<p><strong>说明</strong><br>1、滚动组件触发滚动时触发，支持键鼠操作等其他触发滚动的输入设置。<br>2、通过滚动控制器API接口调用。<br>3、越界回弹。</p>

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-ScrollAttribute-onWillScroll(handler: ScrollOnWillScrollCallback): ScrollAttribute--><!--Device-ScrollAttribute-onWillScroll(handler: ScrollOnWillScrollCallback): ScrollAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| handler | [ScrollOnWillScrollCallback](arkts-arkui-scrollonwillscrollcallback-t.md) | 是 | Scroll滚动前触发的回调。 |

<a id="onzoomstart"></a>
## onZoomStart

```TypeScript
onZoomStart(event: VoidCallback)
```

手势缩放开始触发。

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-ScrollAttribute-onZoomStart(event: VoidCallback): ScrollAttribute--><!--Device-ScrollAttribute-onZoomStart(event: VoidCallback): ScrollAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | [VoidCallback](../arkts-apis/arkts-arkui-voidcallback-t.md) | 是 | 缩放开始回调。 |

<a id="onzoomstop"></a>
## onZoomStop

```TypeScript
onZoomStop(event: VoidCallback)
```

手势缩放停止时触发。

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-ScrollAttribute-onZoomStop(event: VoidCallback): ScrollAttribute--><!--Device-ScrollAttribute-onZoomStop(event: VoidCallback): ScrollAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | [VoidCallback](../arkts-apis/arkts-arkui-voidcallback-t.md) | 是 | 缩放停止回调。 |

<a id="scrollbar"></a>
## scrollBar

```TypeScript
scrollBar(barState: BarState)
```

设置滚动条状态。如果容器组件无法滚动，则滚动条不显示。如果容器组件的子组件大小为无穷大，则滚动条不支持拖动和伴随滚动。从API version 10开始，当滚动组件存在圆角时，为避免滚动条被圆角截断，滚动条会自动计算距顶部和底部的避让距离。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-ScrollAttribute-scrollBar(barState: BarState): ScrollAttribute--><!--Device-ScrollAttribute-scrollBar(barState: BarState): ScrollAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| barState | [BarState](../arkts-apis/arkts-arkui-barstate-e.md) | 是 | 滚动条状态。<br>默认值：<em>BarState.Auto</em> |

<a id="scrollbarcolor"></a>
## scrollBarColor

```TypeScript
scrollBarColor(color: Color | number | string)
```

设置滚动条的颜色。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-ScrollAttribute-scrollBarColor(color: Color | number | string): ScrollAttribute--><!--Device-ScrollAttribute-scrollBarColor(color: Color | number | string): ScrollAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| color | [Color](../../apis-arkgraphics3d/arkts-apis/arkts-arkgraphics3d-scenetypes-color-i.md) \| number \| string | 是 | 滚动条的颜色。<br>默认值：<em>'\#66182431'</em><br>number为HEX格式颜色，支持rgb或者argb，示例：0xffffff。<br>string为rgb或者argb格式颜色，示例：'#ffffff'。 |

<a id="scrollbarcolor-1"></a>
## scrollBarColor

```TypeScript
scrollBarColor(color: Color | number | string | Resource)
```

设置滚动条的颜色。与scrollBarColor相比，color参数开始支持Resource类型。

**起始版本：** 22

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-ScrollAttribute-scrollBarColor(color: Color | number | string | Resource): ScrollAttribute--><!--Device-ScrollAttribute-scrollBarColor(color: Color | number | string | Resource): ScrollAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| color | [Color](../../apis-arkgraphics3d/arkts-apis/arkts-arkgraphics3d-scenetypes-color-i.md) \| number \| string \| Resource | 是 | 滚动条的颜色。<br>默认值：<em>'\#66182431'</em><br>number为HEX格式颜色，支持rgb或者argb，示例：0xffffff。string为rgb或者argb格式颜色，示例：'#ffffff'。 |

<a id="scrollbarwidth"></a>
## scrollBarWidth

```TypeScript
scrollBarWidth(value: number | string)
```

设置滚动条的宽度，不支持百分比设置。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-ScrollAttribute-scrollBarWidth(value: number | string): ScrollAttribute--><!--Device-ScrollAttribute-scrollBarWidth(value: number | string): ScrollAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | number \| string | 是 | 滚动条的宽度。<br>默认值：<em>4</em> <br>单位：vp<br>设置为小于0的值时，按默认值处理。设置为0时，不显示滚动条。 |

<a id="scrollbarwidth-1"></a>
## scrollBarWidth

```TypeScript
scrollBarWidth(value: number | string | Resource)
```

设置滚动条的宽度，不支持百分比设置。支持Resource资源类型。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-ScrollAttribute-scrollBarWidth(value: number | string | Resource): ScrollAttribute--><!--Device-ScrollAttribute-scrollBarWidth(value: number | string | Resource): ScrollAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | number \| string \| Resource | 是 | 滚动条的宽度。<br>单位：vp<br>默认值：<em>4</em><br>取值范围：[0, +∞)。设置为小于0的值时，按4vp处理。设置为0时，不显示滚动条。 |

<a id="scrollsnap"></a>
## scrollSnap

```TypeScript
scrollSnap(value: ScrollSnapOptions)
```

设置Scroll组件的限位滚动模式。限位动画期间onWillScroll事件上报的滚动操作来源类型为ScrollSource.FLING。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-ScrollAttribute-scrollSnap(value: ScrollSnapOptions): ScrollAttribute--><!--Device-ScrollAttribute-scrollSnap(value: ScrollSnapOptions): ScrollAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [ScrollSnapOptions](arkts-arkui-scrollsnapoptions-i.md) | 是 | Scroll组件的限位滚动模式。 |

<a id="scrollable"></a>
## scrollable

```TypeScript
scrollable(value: ScrollDirection)
```

设置滚动方向。该值被修改后会重置滚动偏移量。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-ScrollAttribute-scrollable(value: ScrollDirection): ScrollAttribute--><!--Device-ScrollAttribute-scrollable(value: ScrollDirection): ScrollAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [ScrollDirection](arkts-arkui-scrolldirection-e.md) | 是 | 滚动方向。<br>默认值：<em>ScrollDirection.Vertical</em> |

<a id="zoomscale"></a>
## zoomScale

```TypeScript
zoomScale(scale: number)
```

设置Scroll组件内容的缩放比例。该参数支持!!双向绑定变量。

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-ScrollAttribute-zoomScale(scale: number): ScrollAttribute--><!--Device-ScrollAttribute-zoomScale(scale: number): ScrollAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| scale | number | 是 | 设置Scroll组件内容的缩放比例。<br>默认值：1。<br>取值范围：(0, +∞)。 |

