# Scroller

可滚动容器组件的控制器，可以将此组件绑定至容器组件，然后通过它控制容器组件的滚动。同一个控制器不可以控制多个容器组件，目前支持绑定到ArcList、 ArcScrollBar、List、Scroll、ScrollBar、 Grid、WaterFlow上。 > **说明：** > > 1、Scroller控制器与滚动容器组件的绑定发生在组件创建阶段。 > 2、Scroller控制器与滚动容器组件绑定后才可以正常调用Scroller方法，否则根据调用接口不同会不生效或者抛异常。 > 3、以[aboutToAppear](../../../reference/apis-arkui/arkui-ts/ts-custom-component-lifecycle.md#abouttoappear)为例， > aboutToAppear在创建自定义组件的新实例后，在执行其build()方法之前执行。因此如果滚动组件在自定义组件build内，在该自定义组件aboutToAppear执行时，内部滚动组件还没有创建，是不能正常调用上述 > Scroller方法的。 > 4、以onAppear为例，组件挂载显示后触发此回调。因此在滚动组件的onAppear回调执行时，滚动组件已经创建并已经和Scroller绑定成功，是可以正常调用 > Scroller方法的。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-unnamed-export declare class Scroller--><!--Device-unnamed-export declare class Scroller-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## constructor

```TypeScript
constructor()
```

Scroller的构造函数。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Scroller-constructor()--><!--Device-Scroller-constructor()-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## contentSize

```TypeScript
contentSize() : SizeResult
```

获取滚动组件内容总大小。 > **说明：** > > - Grid、List、WaterFlow和Scroll组件主轴方向内容大小为所有子组件布局后的总大小，交叉轴方向内容大小为组件自身交叉轴方向大小减去padding和border后的大小。 > > - Grid、List、WaterFlow组件有懒加载机制，该接口依赖已布局的子节点进行估算。如果组件内容没有布局完成且子组件高度不一致，估算结果可能会有误差，需要开发者去适配，比如List组件可以通过 > childrenMainSize属性解决估算不准问题。 > > - 如果应用动态增删子节点，则需要应用动态获取内容总大小，来保证接口获取结果的即时性。 > > - 当Scroll组件设置scrollable为ScrollDirection.FREE自由滚动模式时，获取到的内容总大小为子组件缩放后的总大小。 > > - 当Scroll组件设置scrollable为ScrollDirection.None不可滚动时，获取到的内容总大小为0。 > > - 当Grid组件同时设置columnsTemplate和rowsTemplate，或columnsTemplate和rowsTemplate都不设置时即为不可滚动场景，此时获取到的内容总大小高度为0，宽度为Grid组件内 > 容区宽度。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Scroller-contentSize() : SizeResult--><!--Device-Scroller-contentSize() : SizeResult-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [SizeResult](../../apis-arkui/arkts-components/arkts-arkui-sizeresult-i.md) | 滚动组件内容总大小，包括内容宽度和高度。<br/>单位：vp |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [100004](../../apis-arkui/errorcode-router.md#100004-命名路由页面跳转时输入的name错误) | Controller not bound to a component. |

## currentOffset

```TypeScript
currentOffset(): OffsetResult | undefined
```

获取当前的滚动总偏移量。 > **说明：** > > 1. 当Scroller没有和组件绑定时，该接口会返回undefined，但是接口中没有声明，推荐使用[offset](#offset)函数。 > > 2. Grid、List、WaterFlow组件有懒加载机制，组件内容没有加载并布局完成时，内容总偏移量通过估算得到，估算结果可能会有误差。其中List组件可以通过 > childrenMainSize属性解决估算不准确的问题，Grid与WaterFlow估算不准暂无解决方案。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Scroller-currentOffset(): OffsetResult | undefined--><!--Device-Scroller-currentOffset(): OffsetResult | undefined-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [OffsetResult](arkts-na-scroll-offsetresult-i.md) | Returns the current scrolling offset. If the scroller not bound to a component, the return value is undefined. |

## fling

```TypeScript
fling(velocity: double): void
```

滚动类组件根据传入的初始速度进行惯性滚动。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Scroller-fling(velocity: double): void--><!--Device-Scroller-fling(velocity: double): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| velocity | double | 是 | 惯性滚动的初始速度值。单位：vp/s<br/>**说明：**<br/>velocity值设置为0，视为异常值，本次滚动不生效。如果值为正数，则向顶部滚动；如果值为负数， 则向底部滚动。<br/>。 <br>取值范围：(-∞, +∞)。 <br> &lt;em&gt;注意&lt;/em&gt; <br>如果指定的值为0，则视为无效，此实例的滚动将不会 生效。 正值表示向顶部滚动，负值表示向 底的意思。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: <br> 1. Mandatory parameters are left unspecified. <br> 2. Incorrect parameters types. <br> 3. Parameter verification failed. |
| [100004](../../apis-arkui/errorcode-router.md#100004-命名路由页面跳转时输入的name错误) | Controller not bound to a component. |

## getFrameNode

```TypeScript
getFrameNode(): FrameNode | undefined
```

获取与当前Scroller绑定的FrameNode。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Scroller-getFrameNode(): FrameNode | undefined--><!--Device-Scroller-getFrameNode(): FrameNode | undefined-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| FrameNode | Returns the FrameNode bound to this scroller. If the scroller is not bound to a component, the return value is undefined. |

## getItemIndex

```TypeScript
getItemIndex(x: double, y: double): int
```

通过坐标获取子组件的索引。 > **说明：** > > 支持List、Grid、WaterFlow组件。 > > 非法值返回的索引为-1。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Scroller-getItemIndex(x: double, y: double): int--><!--Device-Scroller-getItemIndex(x: double, y: double): int-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| x | double | 是 | x轴坐标，单位为vp。 |
| y | double | 是 | y轴坐标，单位为vp。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| int | 返回子组件的索引。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: <br> 1. Mandatory parameters are left unspecified. <br> 2. Incorrect parameters types. <br> 3. Parameter verification failed. |
| [100004](../../apis-arkui/errorcode-router.md#100004-命名路由页面跳转时输入的name错误) | Controller not bound to a component. |

## getItemRect

```TypeScript
getItemRect(index: int): RectResult
```

获取子组件的大小及相对容器组件的位置。 > **说明：** > > 支持ArcList、Scroll、List、Grid、WaterFlow组件。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Scroller-getItemRect(index: int): RectResult--><!--Device-Scroller-getItemRect(index: int): RectResult-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| index | int | 是 | 子组件的索引值。**说明：**<br/>index必须是当前显示区域显示的子组件的索引值，否则视为非法值。非法值返回的大小和位置均为0。 <br>取值限定为整数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [RectResult](../../apis-arkui/arkts-components/arkts-arkui-rectresult-i.md) | 子组件的大小和相对于组件的位置。<br/>单位：vp。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: <br> 1. Mandatory parameters are left unspecified. <br> 2. Incorrect parameters types. <br> 3. Parameter verification failed. |
| [100004](../../apis-arkui/errorcode-router.md#100004-命名路由页面跳转时输入的name错误) | Controller not bound to a component. |

## isAtEnd

```TypeScript
isAtEnd(): boolean
```

查询组件是否滚动到底部。 > **说明：** > > 支持ArcList、Scroll、List、Grid、WaterFlow组件。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Scroller-isAtEnd(): boolean--><!--Device-Scroller-isAtEnd(): boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | true表示组件已经滚动到底部，false表示组件还没滚动到底部。 |

## offset

```TypeScript
offset(): OffsetResult | undefined
```

获取当前的滚动总偏移量。除接口声明有undefined以外，其他与[currentOffset](#currentoffset)接口保持一致。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Scroller-offset(): OffsetResult | undefined--><!--Device-Scroller-offset(): OffsetResult | undefined-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [OffsetResult](arkts-na-scroll-offsetresult-i.md) | Returns the current scrolling offset. If the scroller not bound to a component, the return value is undefined. |

## scrollBy

```TypeScript
scrollBy(dx: Length, dy: Length): void
```

滑动指定距离。 > **说明：** > - 支持ArcList、Scroll、List、Grid、WaterFlow组件。 > > - 各组件行为存在差异： > > - ArcList和List组件会对所有经过的item进行加载和布局。 > > - Grid组件和[SLIDING_WINDOW]模式的WaterFlow组件在跳转距离较大（大于2倍组件主轴高度）时，会直接估算出要显示的item。 > > - [ALWAYS_TOP_DOWN]模式的WaterFlow组件向后跳转（即dx或dy为正值时）会加载和布局所有经过的item，向前跳转（即dx或dy为负值时）会直接跳转到对应位置。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Scroller-scrollBy(dx: Length, dy: Length): void--><!--Device-Scroller-scrollBy(dx: Length, dy: Length): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| dx | [Length](../../apis-arkui/arkts-apis/arkts-arkui-length-t.md) | 是 |  |
| dy | [Length](../../apis-arkui/arkts-apis/arkts-arkui-length-t.md) | 是 |  |

## scrollEdge

```TypeScript
scrollEdge(value: Edge, options?: ScrollEdgeOptions): void
```

滚动到容器边缘，不区分滚动轴方向，Edge.Top和Edge.Start表现相同，Edge.Bottom和Edge.End表现相同。 Scroll组件默认有动画，Grid、List、WaterFlow组件默认无动画。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Scroller-scrollEdge(value: Edge, options?: ScrollEdgeOptions): void--><!--Device-Scroller-scrollEdge(value: Edge, options?: ScrollEdgeOptions): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [Edge](../../apis-arkui/arkts-apis/arkts-arkui-edge-e.md) | 是 | 滚动到的边缘位置。 |
| options | [ScrollEdgeOptions](arkts-na-scroll-scrolledgeoptions-i.md) | 否 | 设置滚动到边缘位置的模式。 |

## scrollPage

```TypeScript
scrollPage(value: ScrollPageOptions): void
```

滚动到下一页或者上一页。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Scroller-scrollPage(value: ScrollPageOptions): void--><!--Device-Scroller-scrollPage(value: ScrollPageOptions): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [ScrollPageOptions](arkts-na-scroll-scrollpageoptions-i.md) | 是 |  |

## scrollTo

```TypeScript
scrollTo(options: ScrollOptions): void
```

滑动到指定位置。 > **说明：** > - scrollTo动画速度大于200vp/s时，滚动组件区域内的组件不响应点击事件。 > > - 各组件行为存在差异： > > - ArcList和List组件会对所有经过的item进行加载和布局。 > > - Grid组件和[SLIDING_WINDOW]模式的WaterFlow组件在跳转距离较大（大于2倍组件主轴高度）时，会直接估算出要显示的item。 > > - [ALWAYS_TOP_DOWN]模式的WaterFlow组件向后跳转（即dx或dy为正值时）会加载和布局所有经过的item，向前跳转（即dx或dy为负值时）会直接跳转到对应位置。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Scroller-scrollTo(options: ScrollOptions): void--><!--Device-Scroller-scrollTo(options: ScrollOptions): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [ScrollOptions](arkts-na-scroll-scrolloptions-i.md) | 是 | 滑动到指定位置的参数。 |

## scrollToIndex

```TypeScript
scrollToIndex(value: int, smooth?: boolean, align?: ScrollAlign, options?: ScrollToIndexOptions): void
```

滑动到指定Index，支持设置滑动额外偏移量。 开启smooth动效时，会对经过的所有item进行加载和布局计算，当大量加载item时会导致性能问题，建议先调用scrollToIndex不带动画跳转到目标附近位置，再调用scrollToIndex带动画滚动到目标位置。 > **说明：** > > 1.仅支持ArcList、Grid、List、WaterFlow组件。 > > 2.在LazyForEach、ForEach、Repeat刷新数据源时，需确保在数据刷新完成之后再调用此接 > 口。 > > 3.从API version 11开始，在List中支持 > [contentStartOffset](../../../reference/apis-arkui/arkui-ts/ts-container-list.md#contentstartoffset11)和 > [contentEndOffset](../../../reference/apis-arkui/arkui-ts/ts-container-list.md#contentendoffset11)。从API > version 22开始，在Grid和Waterflow组件中支持设置 > [contentStartOffset](../../../reference/apis-arkui/arkui-ts/ts-container-scrollable-common.md#contentstartoffset22) > 和 > [contentEndOffset](../../../reference/apis-arkui/arkui-ts/ts-container-scrollable-common.md#contentendoffset22)。 > > - 当滚动容器组件设置contentStartOffset时，如果ScrollAlign设置为START，滚动结束时，指定item首部会与滚动容器组件contentStartOffset处对齐。 > > - 当滚动容器组件设置contentEndOffset时，如果ScrollAlign设置为END，滚动结束时，指定item尾部会与滚动容器组件contentEndOffset处对齐。 > > - 当滚动容器组件设置contentStartOffset或contentEndOffset时，如果ScrollAlign设置为AUTO，且指定item完全处于显示区内，不做调整；否则依照滚动距离最短的原则，将指定item > 首部与滚动组件contentStartOffset处对齐，或指定item尾部与滚动组件contentEndOffset处对齐，使指定item完全显示。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Scroller-scrollToIndex(value: int, smooth?: boolean, align?: ScrollAlign, options?: ScrollToIndexOptions): void--><!--Device-Scroller-scrollToIndex(value: int, smooth?: boolean, align?: ScrollAlign, options?: ScrollToIndexOptions): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | int | 是 | 要滑动到的目标元素在当前容器中的索引值。 <br/>**说明：** <br/>value值设置成负值或者大于当前容器子组件的最大索引值，视为异常值，本次跳转不生效。 <br>取值限定为整数。 |
| smooth | boolean | 否 | 设置滑动到列表项在列表中的索引值时是否有动效，true表示有动效，false表示没有动效。<br/>。 <br>默认值：false。 |
| align | [ScrollAlign](arkts-na-scroll-scrollalign-e.md) | 否 | 指定滑动到的元素与当前容器的对齐方式。<br/>List中的默认值为：ScrollAlign.START。Grid中默认值为：ScrollAlign.AUTO。 WaterFlow中的默认值为：ScrollAlign.START。<br/>**说明：** <br/>仅List、Grid、WaterFlow组件支持该参数。 |
| options | [ScrollToIndexOptions](arkts-na-scroll-scrolltoindexoptions-i.md) | 否 | 设置滑动到指定Index的选项，如额外偏移量。<br/>。 <br>单位为：vp。默认值：0，单位：vp。 |

