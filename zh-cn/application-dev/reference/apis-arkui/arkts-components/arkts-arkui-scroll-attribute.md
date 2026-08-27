# Scroll属性/事件

除支持通用属性和[滚动组件通用属性](arkts-arkui-scrollablecommonmethod-c.md)外，还 支持以下属性：除支持通用事件和[滚动组件通用事件](../../../reference/apis-arkui/arkui-ts/ts-container-scrollable-common.md#事件)外，还 支持以下事件：

**继承/实现关系：** ScrollAttribute extends ScrollableCommonMethod<ScrollAttribute>

**起始版本：** 7

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
```

## edgeEffect

```TypeScript
edgeEffect(edgeEffect: EdgeEffect, options?: EdgeEffectOptions)
```

设置边缘滑动效果。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| edgeEffect | [EdgeEffect](../arkts-apis/arkts-arkui-edgeeffect-e.md) | 是 | Scroll组件的边缘滑动效果，支持弹簧效果和阴影效果。默认值：EdgeEffect.None |
| options | [EdgeEffectOptions](arkts-arkui-edgeeffectoptions-i.md) | 否 | 组件内容大小小于组件自身时，是否开启滑动效果。设置为{ alwaysEnabled: true }会开启滑动效果，{ alwaysEnabled: false }不开启；不传入时使用默认值。默认值：{ alwaysEnabled: true }<br>**起始版本：** 11 |

## enableBouncesZoom

```TypeScript
enableBouncesZoom(enable: boolean)
```

设置是否启用过缩放回弹效果。

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| enable | boolean | 是 | 是否启用过缩放回弹效果。当用户缩放超出最大或最小缩放比例时，释放手势后内容会回弹到最大或最小缩放比例。设置为true表示启用该效果，设置为false表示禁用该效果。 默认值：true |

## enablePaging

```TypeScript
enablePaging(value: boolean)
```

设置是否支持滑动翻页。如果同时设置了滑动翻页enablePaging和限位滚动scrollSnap，则scrollSnap优先生效，enablePaging不生效。可用于书籍翻页、卡片分页浏览等场景。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | boolean | 是 | 是否支持滑动翻页。设置为true支持滑动翻页，false不支持。 默认值：false |

## enableScrollInteraction

```TypeScript
enableScrollInteraction(value: boolean)
```

设置是否支持滚动手势。可用于在自定义拖动、自定义滚动等业务需要接管滑动手势的场景中，临时禁用滚动组件的用户手势滚动。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | boolean | 是 | 是否支持滚动手势。设置为true时可以通过手指或者鼠标滚动，设置为false时无法通过手指或者鼠标滚动，但不影响控制器[Scroller](arkts-arkui-scroller-c.md)的滚动 接口。默认值：true |

## friction

```TypeScript
friction(value: number | Resource)
```

设置摩擦系数，手动滑动滚动区域时生效，仅影响惯性滚动过程，对惯性滚动过程中的链式效果有间接影响。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | number \| Resource | 是 | 摩擦系数。默认值：非可穿戴设备为0.6，可穿戴设备为0.9。从API version 11开始，非可穿戴设备默认值为0.7。从 API version 12开始，非可穿戴设备默认值为0.75。取值范围：(0, +∞)，设置为小于等于0的值时，按默认值处理。 |

## initialOffset

```TypeScript
initialOffset(value: OffsetOptions)
```

设置初始滚动偏移量。只在首次布局时生效，后续动态修改该属性值不生效。可用于页面首次显示时定位到指定滚动位置。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [OffsetOptions](arkts-arkui-offsetoptions-i.md) | 是 | 当输入的大小为百分比时，初始滚动偏移量为Scroll组件主轴方向大小与百分比数值之积。 |

## maxZoomScale

```TypeScript
maxZoomScale(scale: number)
```

设置Scroll组件内容的最大手势缩放比例。

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| scale | number | 是 | Scroll组件内容的最大手势缩放比例。 默认值：1 取值范围：(0, +∞)，小于或等于0时按默认值1处理。 |

## minZoomScale

```TypeScript
minZoomScale(scale: number)
```

设置Scroll组件内容的最小手势缩放比例。

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| scale | number | 是 | Scroll组件内容的最小手势缩放比例。 默认值：1 取值范围：(0, maxZoomScale]，小于或等于0时按默认值1处理，大于maxZoomScale时按maxZoomScale处理。 |

## nestedScroll

```TypeScript
nestedScroll(value: NestedScrollOptions)
```

设置前后两个方向的嵌套滚动模式，实现与父组件的滚动联动。适用于页面内列表与外层滚动区域联动等嵌套滚动场景。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [NestedScrollOptions](arkts-arkui-nestedscrolloptions-i.md) | 是 | 嵌套滚动选项，用于配置前后两个方向的嵌套滚动模式，包含scrollForward（向前滚动模式）和scrollBackward（向后滚动模式）字段。 NestedScrollMode.SELF_ONLY表示仅自身滚动，NestedScrollMode.SELF_FIRST表示自身优先滚动，NestedScrollMode.PARENT_FIRST表示父组件优先滚动， NestedScrollMode.PARALLEL表示自身和父组件同时滚动。默认值：{ scrollForward: NestedScrollMode.SELF_ONLY, scrollBackward: NestedScrollMode.SELF_ONLY }Scroll设置[enablePaging](#enablepaging)或者 [scrollSnap](#scrollsnap)，并同时设置父组件优先的嵌套滚动时，嵌套滚动不生效。 |

## onDidScroll

```TypeScript
onDidScroll(handler: ScrollOnScrollCallback)
```

滚动事件回调，Scroll滚动时触发。返回当前帧滚动的偏移量和当前滚动状态。触发该事件的条件：
1. 滚动组件触发滚动时触发，支持键鼠操作等其他触发滚动的输入设置。
2. 通过滚动控制器API接口调用。
3. 越界回弹。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| handler | [ScrollOnScrollCallback](arkts-arkui-scrollonscrollcallback-t.md) | 是 | Scroll滚动时触发的回调。 |

## onDidZoom

```TypeScript
onDidZoom(event: ScrollOnDidZoomCallback)
```

每帧缩放完成时触发。

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | [ScrollOnDidZoomCallback](arkts-arkui-scrollondidzoomcallback-t.md) | 是 | 每帧缩放完成时回调。 |

## onScroll

```TypeScript
onScroll(event: (xOffset: number, yOffset: number) => void)
```

滚动事件回调，返回滚动时水平、竖直方向偏移量，单位vp。触发该事件的条件：
1. 滚动组件触发滚动时触发，支持键鼠操作等其他触发滚动的输入设置。
2. 通过滚动控制器API接口调用。
3. 越界回弹。

**起始版本：** 7

**废弃版本：** 12

**替代接口：** onWillScroll

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | (xOffset: number, yOffset: number) = & gt; void | 是 | callback when scroll, xOffset: 相对于上一帧水平方向的偏移量，Scroll中的内容向左滚动时偏移量为正，向右滚动时偏移量为负。单位vp。 yOffset: 相对于上一帧竖直方向的偏移量，Scroll中的内容向上滚动时偏移量为正，向下滚动时偏移量为负。单位vp。 |

## onScrollEdge

```TypeScript
onScrollEdge(event: OnScrollEdgeCallback)
```

滚动到边缘事件回调。触发该事件的条件：
1. 滚动组件滚动到边缘时触发，支持键鼠操作等其他触发滚动的输入设置。
2. 通过滚动控制器API接口调用。
3. 越界回弹。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | [OnScrollEdgeCallback](arkts-arkui-onscrolledgecallback-t.md) | 是 | 滚动到的边缘位置。当Scroll设置为水平方向滚动时，上报[Edge.Center](../arkts-apis/arkts-arkui-edge-e.md)表示水平方向起始位置，上报 [Edge.Baseline](../arkts-apis/arkts-arkui-edge-e.md)表示水平方向末尾位置。由于[Edge.Center](../arkts-apis/arkts-arkui-edge-e.md)和[Edge.Baseline](../arkts-apis/arkts-arkui-edge-e.md)枚举值已经废弃，推荐使用 onReachStart、 onReachEnd事件监听是否滚动到边 界。<br>**起始版本：** 18 |

## onScrollEnd

```TypeScript
onScrollEnd(event: () => void)
```

滚动停止事件回调。触发该事件的条件：
1. 滚动组件触发滚动后停止，支持键鼠操作等其他触发滚动的输入设置。
2. 通过滚动控制器API接口调用后停止，带过渡动效。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** onScrollStop

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | () = & gt; void | 是 |  |

## onScrollFrameBegin

```TypeScript
onScrollFrameBegin(event: OnScrollFrameBeginCallback)
```

该接口回调时，事件参数传入即将发生的滚动量，事件处理函数中可根据应用场景计算实际需要的滚动量并作为事件处理函数的返回值返回，Scroll将按照返回值的实际滚动量进行滚动。支持[offsetRemain](arkts-arkui-onscrollframebeginhandlerresult-i.md)为负值。若通过onScrollFrameBegin事件和[scrollBy](arkts-arkui-scroller-c.md#scrollby)方法实现容器嵌套滚动，需设置子滚动节点的 [EdgeEffect](#edgeeffect)为None。如Scroll嵌套List滚动时，List组件的 edgeEffect属性需设置为EdgeEffect.None，否则抛滑List，会触发List的边缘回弹动画，导致嵌套滚动失效。满足以下任一条件时触发该事件：
1. 用户交互（如手指滑动、键鼠操作等）触发滚动。
2. Scroll惯性滚动。
3. 调用[fling](arkts-arkui-scroller-c.md#fling)接口触发滚动。
不触发该事件的条件：
1. 调用除[fling](arkts-arkui-scroller-c.md#fling)接口外的其他滚动控制接口。
2. 越界回弹。
3. 拖动滚动条。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | [OnScrollFrameBeginCallback](arkts-arkui-onscrollframebegincallback-t.md) | 是 | 每帧滚动开始回调函数。<br>**起始版本：** 18 |

## onScrollStart

```TypeScript
onScrollStart(event: VoidCallback)
```

滚动开始时触发。手指拖动Scroll或拖动Scroll的滚动条触发的滚动开始时，会触发该事件。使用[Scroller](arkts-arkui-scroller-c.md)滚动控制器触发的带动画的滚动，动画开始时会触发该事件。触发该事件的条件：
1. 滚动组件开始滚动时触发，支持键鼠操作等其他触发滚动的输入设置。
2. 通过滚动控制器API接口调用后开始，带过渡动效。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | [VoidCallback](../arkts-apis/arkts-arkui-voidcallback-t.md) | 是 | 滚动开始回调。<br>**起始版本：** 18 |

## onScrollStop

```TypeScript
onScrollStop(event: VoidCallback)
```

滚动停止时触发。手拖动Scroll或拖动Scroll的滚动条触发的滚动，手离开屏幕后滚动停止时会触发该事件。使用[Scroller](arkts-arkui-scroller-c.md)滚动控制器触发的带动画的滚动，动画停止时会触发该事件。触发该事件的条件：
1. 滚动组件触发滚动后停止，支持键鼠操作等其他触发滚动的输入设置。
2. 通过滚动控制器API接口调用后开始，带过渡动效。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | [VoidCallback](../arkts-apis/arkts-arkui-voidcallback-t.md) | 是 | 滚动停止回调。<br>**起始版本：** 18 |

## onWillScroll

```TypeScript
onWillScroll(handler: ScrollOnWillScrollCallback)
```

滚动事件回调，Scroll滚动前触发。回调当前帧将要滚动的偏移量和当前滚动状态和滚动操作来源，其中回调的偏移量为计算得到的将要滚动的偏移量值，并非最终实际滚动偏移。可以通过该回调返回值指定Scroll将要滚动的偏移。触发该事件的条件：
1. 滚动组件触发滚动时触发，支持键鼠操作等其他触发滚动的输入设置。
2. 通过滚动控制器API接口调用。
3. 越界回弹。

> **说明：**
> 
> 滚动事件的回调函数在滚动过程中会被频繁触发，因此应避免在该回调函数中执行耗时操作，以防止应用出现卡顿和丢帧的问题。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| handler | [ScrollOnWillScrollCallback](arkts-arkui-scrollonwillscrollcallback-t.md) | 是 | Scroll滚动前触发的回调。 |

## onZoomStart

```TypeScript
onZoomStart(event: VoidCallback)
```

手势缩放开始触发。

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | [VoidCallback](../arkts-apis/arkts-arkui-voidcallback-t.md) | 是 | 缩放开始回调。 |

## onZoomStop

```TypeScript
onZoomStop(event: VoidCallback)
```

手势缩放停止时触发。

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | [VoidCallback](../arkts-apis/arkts-arkui-voidcallback-t.md) | 是 | 缩放停止回调。 |

## scrollable

```TypeScript
scrollable(value: ScrollDirection)
```

设置滚动方向。该值被修改后会重置滚动偏移量。可根据布局选择竖直滚动、水平滚动或自由滚动。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [ScrollDirection](arkts-arkui-scrolldirection-e.md) | 是 | 滚动方向。默认值：ScrollDirection.Vertical |

## scrollBar

```TypeScript
scrollBar(barState: BarState)
```

设置滚动条状态。如果容器组件无法滚动，则滚动条不显示。如果容器组件的子组件大小为无穷大，则滚动条不支持拖动和伴随滚动。可用于控制滚动条是否常驻显示、自动显示或隐藏。从API version 10开始，当滚动组件存在圆角时，为避免滚动条被圆角截断，滚动条会自动计算距顶部和底部的避让距离。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| barState | [BarState](../arkts-apis/arkts-arkui-barstate-e.md) | 是 | 滚动条状态。默认值：BarState.Auto |

## scrollBarColor

```TypeScript
scrollBarColor(color: Color | number | string)
```

设置滚动条的颜色。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| color | Color \| number \| string | 是 | 滚动条的颜色。默认值：'#66182431'number为HEX格式颜色，支持rgb或者argb，取值范围： [0x0, 0xFFFFFFFF]，示例：0xffffff。string为rgb或者argb格式颜色，示例：'#ffffff'。 |

## scrollBarColor

```TypeScript
scrollBarColor(color: Color | number | string | Resource)
```

设置滚动条的颜色。与[scrollBarColor](#scrollbarcolor)相比，color参数开始支持 Resource类型。

**起始版本：** 22

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| color | Color \| number \| string \| Resource | 是 | 滚动条的颜色。默认值：'#66182431'number为HEX格式颜色，支持rgb或者argb，取值 范围：[0x0, 0xFFFFFFFF]，示例：0xffffff。string为rgb或者argb格式颜色，示例：'#ffffff'。 |

## scrollBarWidth

```TypeScript
scrollBarWidth(value: number | string)
```

设置滚动条的宽度，不支持百分比设置。宽度设置后，滚动条正常状态和按压状态宽度均为滚动条的宽度值。如果滚动条的宽度超过Scroll组件主轴方向的可视尺寸，则滚动条的宽度会变为默认值4vp。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | number \| string | 是 | 滚动条的宽度。默认值：4单位：vp 取值范围：设置为小于0的值时，按4vp处理。设置为0时，不显示滚动条。 |

## scrollBarWidth

```TypeScript
scrollBarWidth(value: number | string | Resource)
```

设置滚动条的宽度，不支持百分比设置。宽度设置后，滚动条正常状态和按压状态宽度均为滚动条的宽度值。如果滚动条的宽度超过Scroll组件主轴方向的可视尺寸，则滚动条的宽度会变为默认值4vp，支持Resource资源类型。未通过该接口设置时，设置滚动条的宽度为4vp。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | number \| string \| Resource | 是 | 滚动条的宽度。默认值：4单位：vp 取值范围： [0, +∞)。设置为小于0的值时，按4vp处理。设置为0时，不显示滚动条。 |

## scrollSnap

```TypeScript
scrollSnap(value: ScrollSnapOptions)
```

设置Scroll组件的限位滚动模式，用于实现分页滚动、卡片对齐等需要滚动结束后定位到指定位置的场景。限位动画期间[onWillScroll](#onwillscroll)事件上报的滚动操作来源类型为ScrollSource.FLING。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [ScrollSnapOptions](arkts-arkui-scrollsnapoptions-i.md) | 是 | Scroll组件的限位滚动模式。该对象包含snapAlign（对齐方式）、snapPagination（分页点）、enableSnapToStart（是否在 开头限位）和enableSnapToEnd（是否在末尾限位）等属性。 |

## zoomScale

```TypeScript
zoomScale(scale: number)
```

设置Scroll组件内容的缩放比例。

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| scale | number | 是 | 设置Scroll组件内容的缩放比例，该参数支持[!!](../../../ui/state-management/arkts-new-binding.md)双向绑定变量。 默认值：1 取值范围：(0, +∞)，小于或等于0时按默认值1处理。 |
