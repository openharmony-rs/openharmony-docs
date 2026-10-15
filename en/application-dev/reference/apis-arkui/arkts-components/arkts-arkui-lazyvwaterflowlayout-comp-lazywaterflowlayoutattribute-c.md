# LazyWaterFlowLayoutAttribute

```TypeScript
export declare class LazyWaterFlowLayoutAttribute<T> extends CommonMethod<T>
```

Defines the lazy waterflow layout attribute.

**Inheritance/Implementation:** LazyWaterFlowLayoutAttribute extends CommonMethod&lt;T&gt;

**Since:** 26.0.0

<!--Device-unnamed-export declare class LazyWaterFlowLayoutAttribute<T> extends CommonMethod<T>--><!--Device-unnamed-export declare class LazyWaterFlowLayoutAttribute<T> extends CommonMethod<T>-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { LazyVWaterFlowLayout, LazyVWaterFlowLayoutAttribute, LazyWaterFlowLayoutAttribute } from '@kit.ArkUI';
```

## columnsGap

```TypeScript
columnsGap(value: LengthMetrics | undefined): T
```

Sets the gap between columns. The default value is **LengthMetrics.vp(0)**. If a value less than 0 is set, **LengthMetrics.vp(0)** is used. When used together with the **repeat(auto-stretch, track-size)** mode of [columnsTemplate](#columnstemplate), this value serves as the minimum column spacing, and the system automatically calculates the actual column gap and number of columns.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-LazyWaterFlowLayoutAttribute-columnsGap(value: LengthMetrics | undefined): T--><!--Device-LazyWaterFlowLayoutAttribute-columnsGap(value: LengthMetrics | undefined): T-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | LengthMetrics &#124; undefined | Yes | Gap between columns.<br>(0)<br>**. <br>When the method input parameter is **undefined**, it is restored to the default value (**LengthMetrics.vp(0)**). <br>Value range: [0, +∞)<br>When set to a value less than 0, it is treated as **LengthMetrics.vp(0). Default value: **LengthMetrics.vp**. |

**Return value:**

| Type | Description |
| --- | --- |
| T | Current **LazyVWaterFlowLayout** component itself, used to support chained calls. |

## footer

```TypeScript
footer(builder: CustomBuilder | undefined): T
```

Sets the footer component of the current **LazyVWaterFlowLayout**. If this API is not used, no footer component is set by default. The sticky style of the footer component takes effect only after being set through the [sticky](#sticky) attribute.

> **NOTE:** 
> 
> The footer component is located at the bottom area of the container,
> typically used to display supplementary information, loading status,
> or other elements fixed behind the content.
> 
> When this component scrolls into the visible area with the scroll container,
> and the footer sticky style is set through [sticky](#sticky),
> the footer will stick to the bottom of the visible area of the scroll container.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-LazyWaterFlowLayoutAttribute-footer(builder: CustomBuilder | undefined): T--><!--Device-LazyWaterFlowLayoutAttribute-footer(builder: CustomBuilder | undefined): T-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| builder | [CustomBuilder](arkts-arkui-common-comp-custombuilder-t.md) &#124; undefined | Yes | Footer component constructor.<br>When the input parameter is **undefined**, no footer component is set. If a footer component already exists, it will be removed. |

**Return value:**

| Type | Description |
| --- | --- |
| T | Current **LazyVWaterFlowLayout** component itself, used to support chained calls. |

## header

```TypeScript
header(builder: CustomBuilder | undefined): T
```

Sets the header component of the current **LazyVWaterFlowLayout**. If this API is not used, no header component is set by default. The sticky style of the header component takes effect only after being set through the [sticky](#sticky) attribute.

> **NOTE:** 
> 
> The header component is located at the top area of the container, typically used to display titles,
> group descriptions, or other elements fixed in front of the content.
> 
> When this component scrolls into the visible area with the scroll container,
> and the header sticky style is set through [sticky](#sticky),
> the header will stick to the top of the visible area of the scroll container.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-LazyWaterFlowLayoutAttribute-header(builder: CustomBuilder | undefined): T--><!--Device-LazyWaterFlowLayoutAttribute-header(builder: CustomBuilder | undefined): T-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| builder | [CustomBuilder](arkts-arkui-common-comp-custombuilder-t.md) &#124; undefined | Yes | Constructor of the header component.<br>When the input parameter is **undefined**, no header component is set. If a header component already exists, it is also removed. |

**Return value:**

| Type | Description |
| --- | --- |
| T | Returns the current **LazyVWaterFlowLayout** component itself, used to support chained calls. |

## onVisibleIndexesChange

```TypeScript
onVisibleIndexesChange(callback: OnVisibleIndexesChangeCallback | undefined): T
```

Sets the **onVisibleIndexesChange** callback. When the indexes of child components in the visible area of **LazyVWaterFlowLayout** change, the callback is triggered, returning the start index and end index of the child components in the visible area.

> **NOTE:** 
> 
> When the parent component sets the main axis dimension, **LazyVWaterFlowLayout** performs lazy loading
> based on the visible area of the parent component. In this case, in the **onVisibleIndexesChange** callback,
> **start** returns the index of the child component at the start position of the current visible area,
> and **end** returns the index of the child component at the end position of the current visible area.
> 
> When the parent component does not set the main axis dimension,
> **LazyVWaterFlowLayout** is stretched by its content, causing all child components to be loaded and laid out.
> In this case, in the **onVisibleIndexesChange** callback, **start** returns 0,
> and **end** returns the index of the last child component in the data source.
> 
> When the lazy loading feature of this component becomes invalid
> due to the parent component configuration conditions mentioned above,
> all child components are loaded and laid out. In this case, in the **onVisibleIndexesChange** callback,
> **start** returns 0, and **end** returns the index of the last child component in the data source.
> 
> The parent component here refers to the nearest **List**, **Scroll**,
> or **WaterFlow** component found upward from the current component. **FlowItem**, **LazyColumnLayout**,
> custom components, and **NodeContainer** serve only as intermediate wrapping layers
> and are not considered parent components here.
> For specific meanings in other documents, refer to the corresponding content.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-LazyWaterFlowLayoutAttribute-onVisibleIndexesChange(callback: OnVisibleIndexesChangeCallback | undefined): T--><!--Device-LazyWaterFlowLayoutAttribute-onVisibleIndexesChange(callback: OnVisibleIndexesChangeCallback | undefined): T-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [OnVisibleIndexesChangeCallback](arkts-arkui-common-comp-onvisibleindexeschangecallback-t.md) &#124; undefined | Yes | Callback invoked when the index of a child component in the visible area changes.<br>When the method input parameter is **undefined**, the listening is canceled. |

**Return value:**

| Type | Description |
| --- | --- |
| T | Returns the current **LazyVWaterFlowLayout** component itself, used to support chained calls. |

## rowsGap

```TypeScript
rowsGap(value: LengthMetrics | undefined): T
```

Sets the gap between rows. The default value is **LengthMetrics.vp(0)**. If a value less than 0 is set, **LengthMetrics.vp(0)** is used.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-LazyWaterFlowLayoutAttribute-rowsGap(value: LengthMetrics | undefined): T--><!--Device-LazyWaterFlowLayoutAttribute-rowsGap(value: LengthMetrics | undefined): T-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | LengthMetrics &#124; undefined | Yes | Gap between rows.<br>(0)<br>** is used. <br>If the method input parameter is **undefined**, the default value (**LengthMetrics.vp(0)**) is restored. <br>Value range: [0, +∞)<br>If set to a value less than 0, **LengthMetrics.vp(0). Default value: **LengthMetrics.vp**. |

**Return value:**

| Type | Description |
| --- | --- |
| T | Current **LazyVWaterFlowLayout** component itself, used to support chained calls. |

## sticky

```TypeScript
sticky(sticky: StickyStyle | undefined): T
```

Sets the sticky style of [header](#header) and [footer](#footer).

When this component scrolls into the visible area with the scroll container, and the optional **sticky** attribute is set for header stick-to-top or footer stick-to-bottom, the header will stick to the top of the visible area of the scroll container, and the footer will stick to the bottom of the visible area of the scroll container. If **sticky** is not set, the header component does not stick to the top and the footer component does not stick to the bottom by default.

> **NOTE:** 
> 
> Due to floating-point calculation precision, gaps may appear during scrolling after **sticky** is set. You can use [pixelRound](arkts-arkui-common-comp-commonmethod-c.md#pixelround) to specify downward pixel rounding for the current component to resolve this issue.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-LazyWaterFlowLayoutAttribute-sticky(sticky: StickyStyle | undefined): T--><!--Device-LazyWaterFlowLayoutAttribute-sticky(sticky: StickyStyle | undefined): T-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| sticky | [StickyStyle](arkts-arkui-list-comp-stickystyle-e.md) &#124; undefined | Yes | Sticky style of the header component and footer component. The **sticky** attribute can be set to **StickyStyle.Header** (header component sticks to the top), **StickyStyle.Footer** (footer component sticks to the bottom), **StickyStyle.BOTH** (both header sticks to the top and footer sticks to the bottom), or **StickyStyle.None** (sticky style disabled).<br>When the input parameter is **undefined**, the default value **StickyStyle.None** is restored. <br>If this API is not used, the header component does not stick to the top and the footer component does not stick to the bottom by default. |

**Return value:**

| Type | Description |
| --- | --- |
| T | Returns the current **LazyVWaterFlowLayout** component itself, used to support chained calls. |
