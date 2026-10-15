# LazyColumnLayout properties/events

```TypeScript
export declare class LazyColumnLayoutAttribute extends CommonMethod<LazyColumnLayoutAttribute>
```

Defines the lazy column layout attribute.

**Inheritance/Implementation:** LazyColumnLayoutAttribute extends CommonMethod&lt;LazyColumnLayoutAttribute&gt;

**Since:** 26.0.0

<!--Device-unnamed-export declare class LazyColumnLayoutAttribute extends CommonMethod<LazyColumnLayoutAttribute>--><!--Device-unnamed-export declare class LazyColumnLayoutAttribute extends CommonMethod<LazyColumnLayoutAttribute>-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { LazyColumnLayout, LazyColumnLayoutAttribute } from '@kit.ArkUI';
```

## alignItems

```TypeScript
alignItems(value: HorizontalAlign | undefined)
```

Sets the alignment mode of the child components in the horizontal direction. If this API is not called, the default alignment mode is **HorizontalAlign.Center**.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-LazyColumnLayoutAttribute-alignItems(value: HorizontalAlign | undefined): LazyColumnLayoutAttribute--><!--Device-LazyColumnLayoutAttribute-alignItems(value: HorizontalAlign | undefined): LazyColumnLayoutAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [HorizontalAlign](../arkts-apis/arkts-arkui-horizontalalign-e.md) &#124; undefined | Yes | Alignment mode of child components in the horizontal direction.<br>If the input parameter is **undefined**, **HorizontalAlign.Center** is used. |

## footer

```TypeScript
footer(builder: CustomBuilder | undefined)
```

Sets the footer component of the current **LazyColumnLayout**. If not set through this API, no footer component is set by default.

> **NOTE:** 
> 
> The footer component is located at the bottom area of the container
> and is typically used to display supplementary information, loading status,
> or other elements fixed after the content.
> 
> When this component scrolls with the scrollable container into the viewport
> and the footer stick-to-bottom mode is set through [sticky](#sticky),
> the footer sticks to the bottom of the scrollable container's viewport.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-LazyColumnLayoutAttribute-footer(builder: CustomBuilder | undefined): LazyColumnLayoutAttribute--><!--Device-LazyColumnLayoutAttribute-footer(builder: CustomBuilder | undefined): LazyColumnLayoutAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| builder | [CustomBuilder](arkts-arkui-common-comp-custombuilder-t.md) &#124; undefined | Yes | Constructor of the footer component.<br>When the method parameter is **undefined**, the current **LazyColumnLayout** does not set a footer component. If a footer component already exists, it will also be removed. |

## header

```TypeScript
header(builder: CustomBuilder | undefined)
```

Sets the header component of the current **LazyColumnLayout**. If not set through this API, no header component is set by default.

> **NOTE:** 
> 
> The header component is located at the top area of the container and is typically used to display titles,
> group descriptions, or other elements fixed before the content.
> 
> When this component scrolls with the scrollable container into the viewport
> and the header stick-to-top mode is set through [sticky](#sticky),
> the header sticks to the top of the scrollable container's viewport.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-LazyColumnLayoutAttribute-header(builder: CustomBuilder | undefined): LazyColumnLayoutAttribute--><!--Device-LazyColumnLayoutAttribute-header(builder: CustomBuilder | undefined): LazyColumnLayoutAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| builder | [CustomBuilder](arkts-arkui-common-comp-custombuilder-t.md) &#124; undefined | Yes | Constructor of the header component.<br>When the method parameter is **undefined**, the current **LazyColumnLayout** does not set a header component. If a header component already exists, it will also be removed. |

## onVisibleIndexesChange

```TypeScript
onVisibleIndexesChange(callback: OnVisibleIndexesChangeCallback | undefined)
```

Triggered when the index of a child component in the viewport of **LazyColumnLayout** changes. It returns the start index and end index of the child components in the viewport. If not set through this API, the viewport index change is not monitored by default.

> **NOTE:** 
> 
> When the parent component sets the main axis dimension and lazy loading takes effect,
> **LazyColumnLayout** performs lazy loading based on the parent component's viewport.
> In this case, in the **onVisibleIndexesChange** callback,
> **start** returns the index of the child component at the start position of the current viewport,
> and **end** returns the index of the child component at the end position of the current viewport.
> 
> When the parent component does not set the main axis dimension, **LazyColumnLayout** is stretched by its content,
> causing all child components to be loaded and laid out. In this case, in the **onVisibleIndexesChange** callback,
> **start** returns **0**, and **end** returns the index of the last child component in the data source.
> 
> The parent component here refers to the nearest upper-level scrollable component of the current component.
> For the specific meaning in other documents, refer to the corresponding content.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-LazyColumnLayoutAttribute-onVisibleIndexesChange(callback: OnVisibleIndexesChangeCallback | undefined): LazyColumnLayoutAttribute--><!--Device-LazyColumnLayoutAttribute-onVisibleIndexesChange(callback: OnVisibleIndexesChangeCallback | undefined): LazyColumnLayoutAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [OnVisibleIndexesChangeCallback](arkts-arkui-common-comp-onvisibleindexeschangecallback-t.md) &#124; undefined | Yes | Callback invoked when the start and end index values of child components in the viewport change.<br>If the method parameter is **undefined**, the listening is canceled. |

## space

```TypeScript
space(space: LengthMetrics | undefined)
```

Sets the vertical spacing between child components. If this attribute is not set, the default spacing is **0vp**.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-LazyColumnLayoutAttribute-space(space: LengthMetrics | undefined): LazyColumnLayoutAttribute--><!--Device-LazyColumnLayoutAttribute-space(space: LengthMetrics | undefined): LazyColumnLayoutAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| space | LengthMetrics &#124; undefined | Yes | Spacing between child components in the vertical direction.<br>Value range: [0, +∞) <br>If set to a value less than 0, **0vp** is used. <br>If the method parameter is **undefined**, the value is restored to **0vp**. |

## sticky

```TypeScript
sticky(sticky: StickyStyle | undefined)
```

Sets the sticky style for [header](#header) and [footer](#footer).

When this component scrolls with the scrollable container into the viewport and the header stick-to-top or footer stick-to-bottom mode is set through **sticky**, the header sticks to the top of the scrollable container's viewport, and the footer sticks to the bottom of the scrollable container's viewport.

> **NOTE:** 
> 
> Due to floating-point calculation precision, after setting **sticky**, a small gap may occasionally appear during scrolling. This issue can be resolved by using [pixelRound](arkts-arkui-common-comp-commonmethod-c.md#pixelround) to round the current component's pixels downward.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-LazyColumnLayoutAttribute-sticky(sticky: StickyStyle | undefined): LazyColumnLayoutAttribute--><!--Device-LazyColumnLayoutAttribute-sticky(sticky: StickyStyle | undefined): LazyColumnLayoutAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| sticky | [StickyStyle](arkts-arkui-list-comp-stickystyle-e.md) &#124; undefined | Yes | Sticky style for the header and footer components. The **sticky** attribute can be set to **StickyStyle.Header** or **StickyStyle.Footer**, or to **StickyStyle.BOTH** to support both header stick-to-top and footer stick-to-bottom.<br>When the method parameter is **undefined**, the default value **StickyStyle.None** is restored. <br>If not set through this API, the header does not stick to the top and the footer does not stick to the bottom by default. |
