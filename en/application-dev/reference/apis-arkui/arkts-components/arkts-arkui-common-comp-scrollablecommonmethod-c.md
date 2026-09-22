# ScrollableCommonMethod

```TypeScript
declare class ScrollableCommonMethod<T> extends CommonMethod<T>
```

CommonScrollableMethod

@extends CommonMethod&lt;T&gt;

**Inheritance/Implementation:** ScrollableCommonMethod extends CommonMethod<T>

**Since:** 12

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## autoAdjustScrollBarMargin

```TypeScript
autoAdjustScrollBarMargin(enable: boolean | undefined): T
```

Set the scroll bar auto adjust the margin to avoid the padding, safeAreaPadding, and contentStartOffset/contentEndOffset of the component.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| enable | boolean &#124; undefined | Yes | Whether to enable automatic adjustment of scroll bar margin.<br>Default value: false. |

**Return value:**

| Type | Description |
| --- | --- |
| T |  |

## backToTop

```TypeScript
backToTop(backToTop: boolean): T
```

Sets whether to enable the back-to-top feature for a scrollable component when the status bar is touched.

**Since:** 15

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 15.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| backToTop | boolean | Yes | Whether to enable the back-to-top feature for a scrollable component when the status bar is touched.<br>Default value: &lt;em&gt;false&lt;/em&gt; |

**Return value:**

| Type | Description |
| --- | --- |
| T |  |

## clipContent

```TypeScript
clipContent(clip: ContentClipMode | RectShape): T
```

Sets the content clipping area for this scrollable component.

**Since:** 14

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 14.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| clip | [ContentClipMode](arkts-arkui-common-comp-contentclipmode-e.md) &#124; [RectShape](arkts-arkui-common-comp-rectshape-t.md) | Yes | A value from enum ContentClipMode or a customized clip rect. |

**Return value:**

| Type | Description |
| --- | --- |
| T |  |

## contentEndOffset

```TypeScript
contentEndOffset(offset: number | Resource): T
```

Sets the offset from the end of the content to the boundary of the scrollable display area.

**Since:** 22

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 22.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| offset | number &#124; [Resource](../arkts-apis/arkts-arkui-resource-t.md) | Yes | Offset from the end of the content to the boundary of the scrollable display area.<br>Default value: &lt;em&gt;0&lt;/em&gt; <br>Unit: vp |

**Return value:**

| Type | Description |
| --- | --- |
| T |  |

## contentStartOffset

```TypeScript
contentStartOffset(offset: number | Resource): T
```

Sets the offset from the start of the content to the boundary of the scrollable display area.

**Since:** 22

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 22.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| offset | number &#124; [Resource](../arkts-apis/arkts-arkui-resource-t.md) | Yes | Offset from the start of the content to the boundary of the scrollable display area.<br>Default value: &lt;em&gt;0&lt;/em&gt; <br>Unit: vp |

**Return value:**

| Type | Description |
| --- | --- |
| T |  |

## digitalCrownSensitivity

```TypeScript
digitalCrownSensitivity(sensitivity: Optional<CrownSensitivity>): T
```

Set the sensitivity of rotating crown.

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| sensitivity | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;[CrownSensitivity](../arkts-apis/arkts-arkui-crownsensitivity-e.md)&gt; | Yes | The sensitivity of rotating crown, default value is { MEDIUM }. |

**Return value:**

| Type | Description |
| --- | --- |
| T | The component instance. |

## edgeEffect

```TypeScript
edgeEffect(edgeEffect: EdgeEffect, options?: EdgeEffectOptions): T
```

Sets the effect used when the scroll boundary is reached.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| edgeEffect | [EdgeEffect](../arkts-apis/arkts-arkui-edgeeffect-e.md) | Yes | Effect used when the scroll boundary is reached. The spring and shadow effects are supported.<br>Default value: &lt;em&gt;EdgeEffect.None&lt;/em&gt; for the &lt;em&gt;Grid&lt;/em&gt;, &lt;em&gt;Scroll&lt;/em&gt;, and &lt;em&gt;WaterFlow&lt;/em&gt; components and &lt;em&gt;EdgeEffect.Spring&lt;/em&gt; for the &lt;em&gt;List&lt;/em&gt; component |
| options | [EdgeEffectOptions](arkts-arkui-common-comp-edgeeffectoptions-i.md) | No | Whether to enable the scroll effect when the component content is smaller than the component itself. The value &lt;em&gt;{ alwaysEnabled: true }&lt;/em&gt; means to enable the scroll effect, and &lt;em&gt;{ alwaysEnabled: false }&lt;/em&gt; means the opposite.<br>Default value:<br>&lt;em&gt;{ alwaysEnabled: false }&lt;/em&gt; for the &lt;em&gt;List&lt;/em&gt;, &lt;em&gt;Grid&lt;/em&gt;, and &lt;em&gt;WaterFlow &lt;/em&gt; components, and &lt;em&gt;{ alwaysEnabled: true }&lt;/em&gt; for the &lt;em&gt;Scroll&lt;/em&gt; component |

**Return value:**

| Type | Description |
| --- | --- |
| T |  |

## enableScrollInteraction

```TypeScript
enableScrollInteraction(value: boolean): T
```

Sets whether to support scroll gestures.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | boolean | Yes | Whether to support scroll gestures.<br>Default value: &lt;em&gt;true&lt;/em&gt; |

**Return value:**

| Type | Description |
| --- | --- |
| T |  |

## enableScrollWithMouse

```TypeScript
enableScrollWithMouse(enabled: boolean | undefined): T
```

Enable left mouse button press-and-drag scrolling.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| enabled | boolean &#124; undefined | Yes | Enable left mouse button press-and-drag scrolling.<br>Default value: false. |

**Return value:**

| Type | Description |
| --- | --- |
| T |  |

## fadingEdge

```TypeScript
fadingEdge(enabled: Optional<boolean>, options?: FadingEdgeOptions): T
```

Called when setting whether to enable fading Edge effect.

**Since:** 14

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 14.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| enabled | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;boolean&gt; | Yes | Whether to turn on the edge fade effect |
| options | [FadingEdgeOptions](arkts-arkui-common-comp-fadingedgeoptions-i.md) | No | The options of fadingEdge. |

**Return value:**

| Type | Description |
| --- | --- |
| T |  |

## flingSpeedLimit

```TypeScript
flingSpeedLimit(speedLimit: number): T
```

Sets the maximum initial velocity at the start of the fling animation that occurs after gesture-driven scrolling ends.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| speedLimit | number | Yes | Maximum initial velocity at the start of the fling animation.<br>Default value: &lt;em&gt;9000&lt;/em&gt; <br>Unit: vp/s <br>Value range: (0, +∞). If this parameter is set to a value less than or equal to 0, the default value is used. |

**Return value:**

| Type | Description |
| --- | --- |
| T |  |

## friction

```TypeScript
friction(value: number | Resource): T
```

Sets the friction coefficient.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | number &#124; [Resource](../arkts-apis/arkts-arkui-resource-t.md) | Yes | Friction coefficient. |

**Return value:**

| Type | Description |
| --- | --- |
| T |  |

## nestedScroll

```TypeScript
nestedScroll(value: NestedScrollOptions): T
```

Sets the nested scrolling options.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [NestedScrollOptions](arkts-arkui-common-comp-nestedscrolloptions-i.md) | Yes | options for nested scrolling. |

**Return value:**

| Type | Description |
| --- | --- |
| T |  |

## onDidScroll

```TypeScript
onDidScroll(handler: OnScrollCallback): T
```

Triggered when the scrollable component scrolls.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**Widget capability:** This API can be used in ArkTS widgets since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| handler | [OnScrollCallback](arkts-arkui-common-comp-onscrollcallback-t.md) | Yes | Callback triggered when the scrollable component scrolls. |

**Return value:**

| Type | Description |
| --- | --- |
| T |  |

## onDidStopDragging

```TypeScript
onDidStopDragging(handler: OnDidStopDraggingCallback): T
```

Called when the scrollable did end dragging.

**Since:** 21

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 21.

**Widget capability:** This API can be used in ArkTS widgets since API version 21.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| handler | [OnDidStopDraggingCallback](arkts-arkui-common-comp-ondidstopdraggingcallback-t.md) | Yes | callback of end dragging. |

**Return value:**

| Type | Description |
| --- | --- |
| T |  |

## onDidStopFling

```TypeScript
onDidStopFling(handler: VoidCallback): T
```

Called when the scrollable did end fling.

**Since:** 21

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 21.

**Widget capability:** This API can be used in ArkTS widgets since API version 21.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| handler | [VoidCallback](../arkts-apis/arkts-arkui-voidcallback-t.md) | Yes | callback of end fling. |

**Return value:**

| Type | Description |
| --- | --- |
| T |  |

## onReachEnd

```TypeScript
onReachEnd(event: () => void): T
```

Triggered when the scrollable component reaches the end position.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| event | () =&gt; void | Yes | Callback function, triggered when the scrollable reaches the end position. |

**Return value:**

| Type | Description |
| --- | --- |
| T |  |

## onReachStart

```TypeScript
onReachStart(event: () => void): T
```

Triggered when the scrollable component reaches the start position.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| event | () =&gt; void | Yes | Callback function, triggered when the scrollable reaches the start position. |

**Return value:**

| Type | Description |
| --- | --- |
| T |  |

## onScroll

```TypeScript
onScroll(event: (scrollOffset: number, scrollState: ScrollState) => void): T
```

Triggered when the scrollable component scrolls.

**Since:** 11

**Deprecated since:** 12

**Substitutes:** [onDidScroll](#ondidscroll)

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| event | (scrollOffset: number, scrollState: ScrollState) =&gt; void | Yes | callback of scrollable, scrollOffset is offset per frame scrolling, ScrollState is current scroll state. |

**Return value:**

| Type | Description |
| --- | --- |
| T |  |

## onScrollStart

```TypeScript
onScrollStart(event: () => void): T
```

Triggered when the scrollable component starts scrolling initiated by the user's finger dragging the component or its scrollbar.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| event | () =&gt; void | Yes | Callback function, triggered when the scrollable starts scrolling. |

**Return value:**

| Type | Description |
| --- | --- |
| T |  |

## onScrollStop

```TypeScript
onScrollStop(event: () => void): T
```

Triggered when scrolling stops after the user's finger leaves the screen.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| event | () =&gt; void | Yes | Callback function, triggered when the scrollable stops scrolling. |

**Return value:**

| Type | Description |
| --- | --- |
| T |  |

## onWillScroll

```TypeScript
onWillScroll(handler: Optional<OnWillScrollCallback>): T
```

Called when the scrollable will scroll.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| handler | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;[OnWillScrollCallback](arkts-arkui-common-comp-onwillscrollcallback-t.md)&gt; | Yes | callback of scrollable. |

**Return value:**

| Type | Description |
| --- | --- |
| T |  |

## onWillStartDragging

```TypeScript
onWillStartDragging(handler: VoidCallback): T
```

Called when the scrollable will start dragging.

**Since:** 21

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 21.

**Widget capability:** This API can be used in ArkTS widgets since API version 21.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| handler | [VoidCallback](../arkts-apis/arkts-arkui-voidcallback-t.md) | Yes | callback of start dragging. |

**Return value:**

| Type | Description |
| --- | --- |
| T |  |

## onWillStartFling

```TypeScript
onWillStartFling(handler: VoidCallback): T
```

Called when the scrollable will start fling.

**Since:** 21

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 21.

**Widget capability:** This API can be used in ArkTS widgets since API version 21.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| handler | [VoidCallback](../arkts-apis/arkts-arkui-voidcallback-t.md) | Yes | callback of start fling. |

**Return value:**

| Type | Description |
| --- | --- |
| T |  |

## onWillStopDragging

```TypeScript
onWillStopDragging(handler: OnWillStopDraggingCallback): T
```

Called when the scrollable will end dragging.

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

**Widget capability:** This API can be used in ArkTS widgets since API version 20.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| handler | [OnWillStopDraggingCallback](arkts-arkui-common-comp-onwillstopdraggingcallback-t.md) | Yes | callback of end dragging. |

**Return value:**

| Type | Description |
| --- | --- |
| T |  |

## scrollBar

```TypeScript
scrollBar(barState: BarState): T
```

Sets the scrollbar state.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| barState | [BarState](../arkts-apis/arkts-arkui-barstate-e.md) | Yes | Scrollbar state.<br>Default value: &lt;em&gt;BarState.Auto&lt;/em&gt; for the &lt;em&gt;List&lt;/em&gt;, &lt;em &gt;Grid&lt;/em&gt;, and &lt;em&gt;Scroll&lt;/em&gt; components and &lt;em&gt;BarState.Off&lt;/em&gt; for the &lt;em&gt;WaterFlow&lt;/em&gt; component |

**Return value:**

| Type | Description |
| --- | --- |
| T |  |

## scrollBarColor

```TypeScript
scrollBarColor(color: Color | number | string): T
```

Sets the scrollbar color.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| color | [Color](../arkts-apis/arkts-arkui-color-e.md) &#124; number &#124; string | Yes | Scrollbar color.<br>Default value: &lt;em&gt;'\#182431'&lt;/em&gt; (40% opacity) <br>A number value indicates a HEX color in RGB or ARGB format, for example, &lt;em&gt;0xffffff&lt;/em&gt;. A string value indicates a color in RGB or ARGB format, for example, &lt;em&gt;'# ffffff'&lt;/em&gt;. |

**Return value:**

| Type | Description |
| --- | --- |
| T |  |

<a id="scrollbarcolor-1"></a>

## scrollBarColor

```TypeScript
scrollBarColor(color: Color | number | string | Resource): T
```

Sets the scrollbar color.

**Since:** 22

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 22.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| color | [Color](../arkts-apis/arkts-arkui-color-e.md) &#124; number &#124; string &#124; [Resource](../arkts-apis/arkts-arkui-resource-t.md) | Yes | Scrollbar color.<br>Default value: &lt;em&gt;'\#182431'&lt;/em&gt; (40% opacity) <br>A number value indicates a HEX color in RGB or ARGB format, for example, &lt;em&gt;0xffffff&lt;/em&gt;. A string value indicates a color in RGB or ARGB format, for example, &lt;em&gt;'#ffffff'&lt;/em&gt;. |

**Return value:**

| Type | Description |
| --- | --- |
| T |  |

## scrollBarHeight

```TypeScript
scrollBarHeight(height: LengthMetrics | undefined): T
```

Sets the scrollbar track height.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| height | LengthMetrics &#124; undefined | Yes | Scrollbar track height.<br>The value must be greater than or equal to 0, If set to undefined or a value less than 0, the default value is used. If set to 0, the scrollbar is not displayed. <br> Default value: adaptive to the height of the scrollable component. |

**Return value:**

| Type | Description |
| --- | --- |
| T |  |

## scrollBarMargin

```TypeScript
scrollBarMargin(margin: ScrollBarMargin): T
```

Margin of the scrollbar.

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| margin | [ScrollBarMargin](../arkts-apis/arkts-arkui-scrollbarmargin-i.md) | Yes | Margin of the scrollbar. |

**Return value:**

| Type | Description |
| --- | --- |
| T |  |

## scrollBarWidth

```TypeScript
scrollBarWidth(value: number | string): T
```

Sets the scrollbar width.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | number &#124; string | Yes | Scrollbar width.<br>Default value: &lt;em&gt;4&lt;/em&gt; <br>Unit: vp <br>If this parameter is set to a value less than or equal to 0, the default value is used. The value &lt;em&gt;0&lt;/em&gt; means not to show the scrollbar. |

**Return value:**

| Type | Description |
| --- | --- |
| T |  |

<a id="scrollbarwidth-1"></a>

## scrollBarWidth

```TypeScript
scrollBarWidth(value: number | string | Resource): T
```

Sets the scrollbar width.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | number &#124; string &#124; [Resource](../arkts-apis/arkts-arkui-resource-t.md) | Yes | Scrollbar width.<br>Unit: vp <br>Default value: &lt;em&gt;4&lt;/em&gt; <br>If this parameter is set to a value less than 0, the default value is used. The value &lt;em&gt;0&lt;/em&gt; means not to show the scrollbar. |

**Return value:**

| Type | Description |
| --- | --- |
| T |  |
