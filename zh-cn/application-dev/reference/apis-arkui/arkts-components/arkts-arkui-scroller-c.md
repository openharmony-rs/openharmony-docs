# Scroller

可滚动容器组件的控制器，可以将此组件绑定至容器组件，然后通过它控制容器组件的滚动。同一个控制器不可以控制多个容器组件，目前支持绑定到ArcList、ArcScrollBar、List、Scroll、ScrollBar、Grid、WaterFlow上。

<p><strong>说明</strong><br>1、Scroller控制器与滚动容器组件的绑定发生在组件创建阶段。<br>2、Scroller控制器与滚动容器组件绑定后才可以正常调用Scroller方法，否则根据调用接口不同会不生效或者抛异常。<br>3、以aboutToAppear为例，aboutToAppear在创建自定义组件的新实例后，在执行其build()方法之前执行。因此如果滚动组件在自定义组件build内，在该自定义组件aboutToAppear执行时，内部滚动组件还没有创建，是不能正常调用上述Scroller方法的。<br>4、以onAppear为例，组件挂载显示后触发此回调。因此在滚动组件的onAppear回调执行时，滚动组件已经创建并已经和Scroller绑定成功，是可以正常调用Scroller方法的。</p>

**起始版本：** 7

<!--Device-unnamed-declare class Scroller--><!--Device-unnamed-declare class Scroller-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## constructor

```TypeScript
constructor()
```

Scroller的构造函数。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-Scroller-constructor()--><!--Device-Scroller-constructor()-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## contentSize

```TypeScript
contentSize(): SizeResult
```

获取内容大小。

**起始版本：** 22

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-Scroller-contentSize(): SizeResult--><!--Device-Scroller-contentSize(): SizeResult-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [SizeResult](arkts-arkui-sizeresult-i.md) | 滚动组件内容总大小，包括内容宽度和高度。<br/>单位：vp |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [100004](../errorcode-router.md#100004-命名路由页面跳转时输入的name错误) | Controller not bound to a component. |

## currentOffset

```TypeScript
currentOffset() : OffsetResult
```

获取当前滚动偏移量。

<p><strong>说明</strong><br>1. 当Scroller没有和组件绑定时，该接口会返回undefined，但是接口中没有声明，推荐使用offset函数。<br>2. Grid、List、WaterFlow组件有懒加载机制，组件内容没有加载并布局完成时，内容总偏移量通过估算得到，估算结果可能会有误差。其中List组件可以通过childrenMainSize属性解决估算不准确的问题，Grid与WaterFlow估算不准暂无解决方案。</p>

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-Scroller-currentOffset() : OffsetResult--><!--Device-Scroller-currentOffset() : OffsetResult-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [OffsetResult](arkts-arkui-offsetresult-i.md) | 返回当前的滚动总偏移量。当Scroller没有和组件绑定时，返回值为undefined。 |

## fling

```TypeScript
fling(velocity: number): void
```

滚动类组件根据传入的初始速度进行惯性滚动。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Scroller-fling(velocity: number): void--><!--Device-Scroller-fling(velocity: number): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| velocity | number | 是 | 初始速度，单位vp/s。<br><em>说明</em><br>设置为0时按异常值处理，不生效。正值表示向上方滚动，负值表示向下方滚动。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:<br> 1. Mandatory parameters are left unspecified.<br> 2. Incorrect parameters types.<br> 3. Parameter verification failed. |
| [100004](../errorcode-router.md#100004-命名路由页面跳转时输入的name错误) | Controller not bound to a component. |

## getFrameNode

```TypeScript
getFrameNode(): FrameNode | undefined
```

获取此控制器对应的FrameNode。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-Scroller-getFrameNode(): FrameNode | undefined--><!--Device-Scroller-getFrameNode(): FrameNode | undefined-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [FrameNode](../arkts-apis/arkts-arkui-framenode-c.md) | Returns the FrameNode bound to this scroller.If the scroller is not bound to a component, the return value is undefined. |

## getItemIndex

```TypeScript
getItemIndex(x: number, y: number): number
```

根据坐标获取子组件的索引。

<p><strong>说明</strong><br>坐标无效时返回<em>-1</em>。</p>

**起始版本：** 14

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本14开始，该接口支持在原子化服务API中使用。

<!--Device-Scroller-getItemIndex(x: number, y: number): number--><!--Device-Scroller-getItemIndex(x: number, y: number): number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| x | number | 是 | x轴坐标，单位为vp。 |
| y | number | 是 | y轴坐标，单位为vp。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 返回子组件的索引。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:<br> 1. Mandatory parameters are left unspecified.<br> 2. Incorrect parameters types.<br> 3. Parameter verification failed. |
| [100004](../errorcode-router.md#100004-命名路由页面跳转时输入的name错误) | Controller not bound to a component. |

## getItemRect

```TypeScript
getItemRect(index: number): RectResult
```

获取子组件相对于父组件的大小和位置。

<p><strong>说明</strong><br>index必须是显示区域内可见的子组件的索引，否则视为无效值。<br>非法值返回的大小和位置均为0。</p>

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Scroller-getItemRect(index: number): RectResult--><!--Device-Scroller-getItemRect(index: number): RectResult-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| index | number | 是 | 子组件的索引值。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [RectResult](arkts-arkui-rectresult-i.md) | 子组件的大小和相对于组件的位置。<br/>单位：vp。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:<br> 1. Mandatory parameters are left unspecified.<br> 2. Incorrect parameters types.<br> 3. Parameter verification failed. |
| [100004](../errorcode-router.md#100004-命名路由页面跳转时输入的name错误) | Controller not bound to a component. |

## isAtEnd

```TypeScript
isAtEnd(): boolean
```

检查是否已滚动到底部。

<p><strong>说明</strong><br>该接口支持ArcList、Scroll、List、Grid和WaterFlow组件。</p>

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-Scroller-isAtEnd(): boolean--><!--Device-Scroller-isAtEnd(): boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 返回是否已滚动到底部。true表示已经滚动到底部，false表示还没滚动到底部。 |

## offset

```TypeScript
offset() : OffsetResult | undefined
```

获取当前滚动偏移量。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-Scroller-offset() : OffsetResult | undefined--><!--Device-Scroller-offset() : OffsetResult | undefined-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [OffsetResult](arkts-arkui-offsetresult-i.md) | Returns the current scrolling offset.If the scroller not bound to a component, the return value is undefined. |

## scrollBy

```TypeScript
scrollBy(dx: Length, dy: Length)
```

滚动指定距离。

<p><strong>说明</strong><br>该接口支持ArcList、Scroll、List、Grid和WaterFlow组件。</p>

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-Scroller-scrollBy(dx: Length, dy: Length)--><!--Device-Scroller-scrollBy(dx: Length, dy: Length)-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| dx | [Length](../arkts-apis/arkts-arkui-length-t.md) | 是 | 水平方向滚动距离，不支持百分比形式。 |
| dy | [Length](../arkts-apis/arkts-arkui-length-t.md) | 是 | 竖直方向滚动距离，不支持百分比形式。 |

## scrollEdge

```TypeScript
scrollEdge(value: Edge, options?: ScrollEdgeOptions)
```

滚动到容器边缘，不区分滚动轴方向，Edge.Top和Edge.Start表现相同，Edge.Bottom和Edge.End表现相同。Scroll组件默认有动画，Grid、List、WaterFlow组件默认无动画。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-Scroller-scrollEdge(value: Edge, options?: ScrollEdgeOptions)--><!--Device-Scroller-scrollEdge(value: Edge, options?: ScrollEdgeOptions)-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [Edge](../arkts-apis/arkts-arkui-edge-e.md) | 是 | 滚动到的边缘位置。<br><em>原子化服务API</em>：该API可在原子化服务中使用，从API version 11开始。 |
| options | [ScrollEdgeOptions](arkts-arkui-scrolledgeoptions-i.md) | 否 | 设置滚动到边缘位置的模式。<br><em>原子化服务API</em>：该API可在原子化服务中使用，从API version 12开始。<br>**起始版本：** 12 |

## scrollPage

```TypeScript
scrollPage(value: ScrollPageOptions)
```

滚动到下一页或上一页。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-Scroller-scrollPage(value: ScrollPageOptions)--><!--Device-Scroller-scrollPage(value: ScrollPageOptions)-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [ScrollPageOptions](arkts-arkui-scrollpageoptions-i.md) | 是 | 翻页模式。<br>**起始版本：** 14 |

## scrollPage

```TypeScript
scrollPage(value: { next: boolean; direction?: Axis })
```

滚动到下一页或上一页。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [scrollPage](arkts-arkui-scroller-c.md#scrollpage)

<!--Device-Scroller-scrollPage(value: { next: boolean; direction?: Axis })--><!--Device-Scroller-scrollPage(value: { next: boolean; direction?: Axis })-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | { next: boolean; direction?: Axis } | 是 | next: Whether to turn to the next page.The value <em>true</em> means to scroll to the next page, and <em>false</em> means to scroll to the previous page.direction: Scrolling direction: horizontal or vertical. |

## scrollTo

```TypeScript
scrollTo(options: ScrollOptions)
```

滑动到指定位置。

<p><strong>说明</strong><br>scrollTo动画速度大于200vp/s时，滚动组件区域内的组件不响应点击事件。</p>

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-Scroller-scrollTo(options: ScrollOptions)--><!--Device-Scroller-scrollTo(options: ScrollOptions)-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [ScrollOptions](arkts-arkui-scrolloptions-i.md) | 是 | 滑动到指定位置的参数。<br>**起始版本：** 18 |

## scrollToIndex

```TypeScript
scrollToIndex(value: number, smooth?: boolean, align?: ScrollAlign, options?: ScrollToIndexOptions)
```

滑动到指定索引位置，支持设置额外偏移量。开启smooth动效时，会对经过的所有item进行加载和布局计算，当大量加载item时会导致性能问题，建议先调用scrollToIndex不带动画跳转到目标附近位置，再调用scrollToIndex带动画滚动到目标位置。

<p><strong>说明</strong><br>该接口仅对ArcList、Grid、List和WaterFlow组件生效。<br>在LazyForEach、ForEach、Repeat刷新数据源时，需确保在数据刷新完成之后再调用此接口。<br>从API version 11开始，在List中支持contentStartOffset和contentEndOffset。从API version 22开始，在Grid和Waterflow组件中支持设置contentStartOffset和contentEndOffset。<br>- 当滚动容器组件设置contentStartOffset时，如果ScrollAlign设置为START，滚动结束时，指定item首部会与滚动容器组件contentStartOffset处对齐。<br>- 当滚动容器组件设置contentEndOffset时，如果ScrollAlign设置为END，滚动结束时，指定item尾部会与滚动容器组件contentEndOffset处对齐。<br>- 当滚动容器组件设置contentStartOffset或contentEndOffset时，如果ScrollAlign设置为AUTO，且指定item完全处于显示区内，不做调整；否则依照滚动距离最短的原则，将指定item首部与滚动组件contentStartOffset处对齐，或指定item尾部与滚动组件contentEndOffset处对齐，使指定item完全显示。</p>

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-Scroller-scrollToIndex(value: number, smooth?: boolean, align?: ScrollAlign, options?: ScrollToIndexOptions)--><!--Device-Scroller-scrollToIndex(value: number, smooth?: boolean, align?: ScrollAlign, options?: ScrollToIndexOptions)-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | number | 是 | 要滑动到的目标元素在当前容器中的索引值。<br><em>说明</em><br>value值设置成负值或者大于当前容器子组件的最大索引值，视为异常值，本次跳转不生效。 |
| smooth | boolean | 否 | 设置滑动到列表项在列表中的索引值时是否有动效，true表示有动效，false表示没有动效。<br>**起始版本：** 7 - 11 |
| align | [ScrollAlign](arkts-arkui-scrollalign-e.md) | 否 | 指定滑动到的元素与当前容器的对齐方式。<br>**起始版本：** 7 - 11 |
| options | [ScrollToIndexOptions](arkts-arkui-scrolltoindexoptions-i.md) | 否 | 设置滑动到指定Index的选项，如额外偏移量。<br>默认值：<em>0</em>，单位：vp<br>**起始版本：** 12 |

