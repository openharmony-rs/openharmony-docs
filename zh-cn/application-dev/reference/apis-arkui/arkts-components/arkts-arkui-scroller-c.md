# Scroller

可滚动容器组件的控制器，可以将此组件绑定至容器组件，然后通过它控制容器组件的滚动。同一个控制器不可以控制多个容器组件，目前支持绑定到ArcList、ArcScrollBar、List、Scroll、ScrollBar、Grid、 WaterFlow上。 > **说明：** > > 1. Scroller控制器与滚动容器组件的绑定发生在组件创建阶段。 > 2. Scroller控制器与滚动容器组件绑定后才可以正常调用Scroller方法，否则根据调用接口不同会不生效或者抛异常。 > 3. 以[aboutToAppear](../../../reference/apis-arkui/arkui-ts/ts-custom-component-lifecycle.md#abouttoappear)为例， > aboutToAppear在创建自定义组件的新实例后，在执行其build()方法之前执行。因此如果滚动组件在自定义组件build内，在该自定义组件aboutToAppear执行时，内部滚动组件还没有创建，是不能正常调用上述 > Scroller方法的。 > 4. 以onAppear为例，组件挂载显示后触发此回调。因此在滚动组件的onAppear回调执行时，滚动组件已经创建并已经和Scroller绑定成功，是可以正常调用 > Scroller方法的。

## 导入对象 ```ts scroller: Scroller = new Scroller(); ```

**起始版本：** 7

<!--Device-unnamed-declare class Scroller--><!--Device-unnamed-declare class Scroller-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
```

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

获取滚动组件内容总大小。 > **说明：** > > - Grid、List、WaterFlow和Scroll组件主轴方向内容大小为所有子组件布局后的总大小，交叉轴方向内容大小为组件自身交叉轴方向大小减去padding和border后的大小。 > > - Grid、List、WaterFlow组件有懒加载机制，该接口依赖已布局的子节点进行估算。如果组件内容没有布局完成且子组件高度不一致，估算结果可能会有误差，开发者需要适配。例如，List组件可以通过 > childrenMainSize属性解决估算不准问题。 > > - 如果应用动态增删子节点，则需要应用动态获取内容总大小，来保证接口获取结果的即时性。 > > - 当Scroll组件设置scrollable为ScrollDirection.FREE自由滚动模式时，获取到的内容总大小为子组件缩放后的总大小。 > > - 当Scroll组件设置scrollable为ScrollDirection.None不可滚动时，获取到的内容总大小为0。 > > - 当Grid组件同时设置columnsTemplate和rowsTemplate，或columnsTemplate和rowsTemplate都不设置时即为不可滚动场景，此时获取到的内容总大小高度为0，宽度为Grid组件内容区 > 宽度。

**起始版本：** 22

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-Scroller-contentSize(): SizeResult--><!--Device-Scroller-contentSize(): SizeResult-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| SizeResult | 滚动组件内容总大小。主轴方向内容大小为所有子组件布局后的总大小，交叉轴方向内容大小为组件自身交叉轴方向大小减去padding和border后的大小。<br/>单位：vp |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [100004](../errorcode-router.md#100004-命名路由页面跳转时输入的name错误) | Controller not bound to a component. |

## currentOffset

```TypeScript
currentOffset() : OffsetResult
```

获取当前的滚动总偏移量。 > **说明：** > > 1. 当Scroller没有和组件绑定时，该接口会返回undefined，但是接口中没有声明。推荐使用[offset](#offset)函数，其返回类型显式包含undefined。 > > 2. Grid、List、WaterFlow组件有懒加载机制，组件内容没有加载并布局完成时，内容总偏移量通过估算得到，估算结果可能会有误差。其中List组件可以通过 > childrenMainSize属性解决估算不准确的问题，Grid与WaterFlow估算不准暂无解决方案。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-Scroller-currentOffset() : OffsetResult--><!--Device-Scroller-currentOffset() : OffsetResult-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [OffsetResult](arkts-arkui-offsetresult-i.md) | 返回当前的滚动总偏移量。xOffset表示水平滚动总偏移量，yOffset表示竖直滚动总偏移量。<br/> |

## fling

```TypeScript
fling(velocity: number): void
```

滚动类组件根据传入的初始速度进行惯性滚动，可用于模拟抛滑效果。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Scroller-fling(velocity: number): void--><!--Device-Scroller-fling(velocity: number): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| velocity | number | 是 | 惯性滚动的初始速度值。单位：vp/s<br/>**说明：**<br/>velocity值设置为0时，本次滚动不生效且不会产生滚动动画。如果值为正数，则向顶部滚动；如果值为负 数，则向底部滚动。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: <br> 1. Mandatory parameters are left unspecified. <br> 2. Incorrect parameters types. <br> 3. Parameter verification failed. |
| [100004](../errorcode-router.md#100004-命名路由页面跳转时输入的name错误) | Controller not bound to a component. |

## getFrameNode

```TypeScript
getFrameNode(): FrameNode | undefined
```

获取与当前Scroller绑定的FrameNode。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-Scroller-getFrameNode(): FrameNode | undefined--><!--Device-Scroller-getFrameNode(): FrameNode | undefined-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| FrameNode | 当Scroller已绑定到Scroll、List、Grid、WaterFlow等滚动类组件时，返回对应组件的FrameNode；如果Scroller未绑定组件， 则返回undefined。 |

## getItemIndex

```TypeScript
getItemIndex(x: number, y: number): number
```

通过坐标获取子组件的索引。 > **说明：** > > 支持List、Grid、WaterFlow组件。

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
| number | 返回坐标命中的子组件索引。坐标未命中子组件时，返回-1。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: <br> 1. Mandatory parameters are left unspecified. <br> 2. Incorrect parameters types. <br> 3. Parameter verification failed. |
| [100004](../errorcode-router.md#100004-命名路由页面跳转时输入的name错误) | Controller not bound to a component. |

## getItemRect

```TypeScript
getItemRect(index: number): RectResult
```

获取子组件的大小及相对容器组件的位置。 > **说明：** > > 支持ArcList、Scroll、List、Grid、WaterFlow组件。

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
| RectResult | 子组件的大小和相对于组件的位置。<br/>单位：vp。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: <br> 1. Mandatory parameters are left unspecified. <br> 2. Incorrect parameters types. <br> 3. Parameter verification failed. |
| [100004](../errorcode-router.md#100004-命名路由页面跳转时输入的name错误) | Controller not bound to a component. |

## isAtEnd

```TypeScript
isAtEnd(): boolean
```

查询组件是否滚动到底部。 > **说明：** > > 支持ArcList、Scroll、List、Grid、WaterFlow组件。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-Scroller-isAtEnd(): boolean--><!--Device-Scroller-isAtEnd(): boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | true表示组件已经滚动到底部，false表示组件还没滚动到底部。 |

## offset

```TypeScript
offset() : OffsetResult | undefined
```

获取当前的滚动总偏移量。除接口声明有undefined以外，其他与[currentOffset](#currentoffset)接口保持一致。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-Scroller-offset() : OffsetResult | undefined--><!--Device-Scroller-offset() : OffsetResult | undefined-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [OffsetResult](arkts-arkui-offsetresult-i.md) | 返回当前的滚动总偏移量。xOffset表示水平滚动总偏移量，yOffset表示竖直滚动总偏移量。当Scroller没有和组件绑定时，该接口会返回 undefined。 |

## scrollBy

```TypeScript
scrollBy(dx: Length, dy: Length)
```

滑动指定距离。 > **说明：** > > - 支持ArcList、Scroll、List、Grid、WaterFlow组件。 > > - 各组件行为存在差异： > > - ArcList和List组件会对所有经过的item进行加载和布局。 > > - Grid组件和SLIDING_WINDOW模式的WaterFlow组件在跳转距离较大（大于2倍组件主轴高度）时，会直接估算出要显示的item。跳转指一帧滑动。 > > - ALWAYS_TOP_DOWN模式的WaterFlow组件向后跳转（即dx或dy为正值时）会加载和布局所有经过的item，向前跳转（即dx或dy为负值时）会直接跳转 > 到对应位置。跳转指一帧滑动。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-Scroller-scrollBy(dx: Length, dy: Length)--><!--Device-Scroller-scrollBy(dx: Length, dy: Length)-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| dx | Length | 是 | 水平方向滚动距离，不支持百分比形式。 <br/>取值范围：(-∞, +∞) |
| dy | Length | 是 | 竖直方向滚动距离，不支持百分比形式。 <br/>取值范围：(-∞, +∞) |

## scrollEdge

```TypeScript
scrollEdge(value: Edge, options?: ScrollEdgeOptions)
```

滚动到容器边缘，不区分滚动轴方向，Edge.Top和Edge.Start表现相同，Edge.Bottom和Edge.End表现相同。可用于返回顶部、跳转到内容末尾等场景。 Scroll组件默认有动画，Grid、List、WaterFlow组件默认无动画。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-Scroller-scrollEdge(value: Edge, options?: ScrollEdgeOptions)--><!--Device-Scroller-scrollEdge(value: Edge, options?: ScrollEdgeOptions)-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | Edge | 是 | 滚动到的边缘位置。 |
| options | [ScrollEdgeOptions](arkts-arkui-scrolledgeoptions-i.md) | 否 | 设置滚动到边缘位置的模式。 <br>&lt;em&gt;原子化服务API&lt;/em&gt;：该API可在原子化服务中使用，从API version 12开始。<br>**起始版本：** 12 |

## scrollPage

```TypeScript
scrollPage(value: ScrollPageOptions)
```

滚动到下一页或者上一页。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-Scroller-scrollPage(value: ScrollPageOptions)--><!--Device-Scroller-scrollPage(value: ScrollPageOptions)-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [ScrollPageOptions](arkts-arkui-scrollpageoptions-i.md) | 是 | 设置翻页模式。包含next（是否向下翻页）和animation（是否开启翻页动画）字段，用于指定翻页行为。<br>**起始版本：** 14 |

## scrollPage

```TypeScript
scrollPage(value: { next: boolean; direction?: Axis })
```

滚动到下一页或者上一页。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [scrollPage](#scrollpage)

<!--Device-Scroller-scrollPage(value: { next: boolean; direction?: Axis })--><!--Device-Scroller-scrollPage(value: { next: boolean; direction?: Axis })-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | { next: boolean; direction?: Axis } | 是 | next：是否向下翻页。true表示向下翻页，false表示向上翻页。 <br> direction：设置滚动方向为水平或竖直方向。 |

## scrollTo

```TypeScript
scrollTo(options: ScrollOptions)
```

滑动到指定位置，可用于目录跳转、返回顶部、搜索结果定位等场景。 > **说明：** > > - scrollTo动画速度大于200vp/s时，滚动组件区域内的组件不响应点击事件。 > > - 各组件行为存在差异： > > - ArcList和List组件会对所有经过的item进行加载和布局。 > > - Grid组件和SLIDING_WINDOW模式的WaterFlow组件在跳转距离较大（大于2倍组件主轴高度）时，会直接估 > 算出要显示的item。跳转指一帧滑动。 > > - ALWAYS_TOP_DOWN模式的WaterFlow组件向后跳转（即dx或dy为正值时）会加载和布局所有经过的item，向前跳转（即dx或dy为负值时）会直接跳转 > 到对应位置。跳转指一帧滑动。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-Scroller-scrollTo(options: ScrollOptions)--><!--Device-Scroller-scrollTo(options: ScrollOptions)-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [ScrollOptions](arkts-arkui-scrolloptions-i.md) | 是 | 滑动到指定位置的参数，包含xOffset、yOffset、animation、canOverScroll等字段，用于指定滚动目标位置和滚动行 为。<br>**起始版本：** 18 |

## scrollToIndex

```TypeScript
scrollToIndex(value: number, smooth?: boolean, align?: ScrollAlign, options?: ScrollToIndexOptions)
```

滑动到指定Index，支持设置滑动额外偏移量。 开启smooth动画时，会对经过的所有item进行加载和布局计算。当大量加载item时会导致性能问题，开发者应先调用scrollToIndex不带动画跳转到目标附近位置，再调用scrollToIndex带动画滚动到目标位置，以优化 性能。 > **说明：** > > 1. 仅支持ArcList、Grid、List、WaterFlow组件。 > > 2. 在LazyForEach、ForEach、Repeat刷新数据源时，需确保在数据刷新完成之后再 > 调用此接口。 > > 3. 从API version 11开始，在List中支持contentStartOffset和 > contentEndOffset。从API version 22开始，在Grid和WaterFlow组件中支持设置 > [contentStartOffset](../../../reference/apis-arkui/arkui-ts/ts-container-scrollable-common.md#contentstartoffset22) > 和 > [contentEndOffset](../../../reference/apis-arkui/arkui-ts/ts-container-scrollable-common.md#contentendoffset22)。 > > - 当滚动容器组件设置contentStartOffset时，如果ScrollAlign设置为START，滚动结束时，指定item首部会与滚动容器组件contentStartOffset处对齐。 > > - 当滚动容器组件设置contentEndOffset时，如果ScrollAlign设置为END，滚动结束时，指定item尾部会与滚动容器组件contentEndOffset处对齐。 > > - 当滚动容器组件设置contentStartOffset或contentEndOffset时，如果ScrollAlign设置为AUTO，且指定item完全处于显示区内，不做调整；否则依照滚动距离最短的原则，将指定item首部 > 与滚动组件contentStartOffset处对齐，或指定item尾部与滚动组件contentEndOffset处对齐，使指定item完全显示。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-Scroller-scrollToIndex(value: number, smooth?: boolean, align?: ScrollAlign, options?: ScrollToIndexOptions)--><!--Device-Scroller-scrollToIndex(value: number, smooth?: boolean, align?: ScrollAlign, options?: ScrollToIndexOptions)-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | number | 是 | 要滑动到的目标元素在当前容器中的索引值。 <br/>**说明：** <br/>value值设置成负值或者大于当前容器子组件的最大索引值，视为异常值，本次跳转不生效。 |
| smooth | boolean | 否 | 设置滑动到列表项在列表中的索引值时是否有动画，true表示有动画，false表示没有动画。不传入时默认无动画。<br/>默认值：false。<br>**起始版本：** 12 |
| align | [ScrollAlign](arkts-arkui-scrollalign-e.md) | 否 | 指定滑动到的元素与当前容器的对齐方式，可根据期望item首部、尾部或居中显示选择对应对齐方式。<br/>默认值：List为ScrollAlign.START， Grid为ScrollAlign.AUTO，WaterFlow为ScrollAlign.START。<br/>**说明：** <br/>仅List、Grid、WaterFlow组件支持该参数。<br>**起始版本：** 12 |
| options | [ScrollToIndexOptions](arkts-arkui-scrolltoindexoptions-i.md) | 否 | 设置滑动到指定Index的选项，包含extraOffset字段，用于指定滚动后的额外偏移量。<br/>不传入时无额外偏移量。&lt;br/ &gt;<br>**起始版本：** 12 |

