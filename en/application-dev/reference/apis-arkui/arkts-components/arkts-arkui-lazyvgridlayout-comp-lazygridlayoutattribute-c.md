# LazyGridLayoutAttribute

```TypeScript
declare class LazyGridLayoutAttribute<T> extends CommonMethod<T>
```

Defines the lazy grid layout attribute.

**Inheritance/Implementation:** LazyGridLayoutAttribute extends CommonMethod&lt;T&gt;

**Since:** 19

<!--Device-unnamed-declare class LazyGridLayoutAttribute<T> extends CommonMethod<T>--><!--Device-unnamed-declare class LazyGridLayoutAttribute<T> extends CommonMethod<T>-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## columnsGap

```TypeScript
columnsGap(value: LengthMetrics): T
```

Sets the gap between columns. The default value is **0vp**. If a value less than 0 is set, the default value is used. When [columnsTemplate](#columnstemplate) is set to **auto-stretch** mode, **columnsGap** serves as the minimum column gap, and the actual column gap is automatically calculated by the system.

**Since:** 19

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 19.

<!--Device-LazyGridLayoutAttribute-columnsGap(value: LengthMetrics): T--><!--Device-LazyGridLayoutAttribute-columnsGap(value: LengthMetrics): T-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | LengthMetrics | Yes | Spacing between columns.<br>Value range: [0, +∞) |

**Return value:**

| Type | Description |
| --- | --- |
| T | Current **LazyVGridLayout** component itself, which supports chained calls. |

## footer

```TypeScript
footer(builder: CustomBuilder | undefined): T
```

Sets the footer component of the current **LazyVGridLayout**.

> **NOTE:** 
> 
> The footer component is located at the bottom of the container
> and is typically used to display supplementary information,
> loading status, or other elements fixed after the content.
> 
> When this component scrolls into the visible area along with the scroll container
> and the footer stick-to-bottom mode is set through [sticky](#sticky),
> the footer sticks to the bottom of the visible area of the scroll container.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-LazyGridLayoutAttribute-footer(builder: CustomBuilder | undefined): T--><!--Device-LazyGridLayoutAttribute-footer(builder: CustomBuilder | undefined): T-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| builder | [CustomBuilder](arkts-arkui-common-comp-custombuilder-t.md) &#124; undefined | Yes | Footer component constructor.<br>When the method input parameter is **undefined**, the current **LazyVGridLayout** does not set a footer component. If a footer component already exists, it will also be removed. |

**Return value:**

| Type | Description |
| --- | --- |
| T | Returns the current **LazyVGridLayout** component itself for chained calls. |

## header

```TypeScript
header(builder: CustomBuilder | undefined): T
```

Sets the header component of the current **LazyVGridLayout**.

> **NOTE:** 
> 
> The header component is located at the top of the container and is typically used to display titles,
> group descriptions, or other elements fixed before the content.
> 
> When this component scrolls into the visible area along with the scroll container
> and the header stick-to-top mode is set through [sticky](#sticky),
> the header sticks to the top of the visible area of the scroll container.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-LazyGridLayoutAttribute-header(builder: CustomBuilder | undefined): T--><!--Device-LazyGridLayoutAttribute-header(builder: CustomBuilder | undefined): T-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| builder | [CustomBuilder](arkts-arkui-common-comp-custombuilder-t.md) &#124; undefined | Yes | Constructor of the header component.<br>When the method input parameter is **undefined**, the current **LazyVGridLayout** does not set a header component. If a header component already exists, it is also removed. |

**Return value:**

| Type | Description |
| --- | --- |
| T | Returns the current **LazyVGridLayout** component itself for chained calls. |

## onVisibleIndexesChange

```TypeScript
onVisibleIndexesChange(callback: OnVisibleIndexesChangeCallback | undefined): T
```

Sets the **onVisibleIndexesChange** callback. When the index values of child components of **LazyVGridLayout** within the visible area change, the callback is triggered, returning the start index and end index of the child components in the visible area.

> **NOTE:** 
> 
> When the parent component sets the main axis dimension,
> **LazyVGridLayout** performs lazy loading based on the visible area of the parent component.
> In this case, in the **onVisibleIndexesChange** callback,
> **start** returns the index of the child component at the start position of the current visible area,
> and **end** returns the index of the child component at the end position of the current visible area.
> 
> When the parent component does not set the main axis dimension,
> **LazyVGridLayout** is stretched by its content, causing all child components to be loaded and laid out.
> In this case, in the **onVisibleIndexesChange** callback, **start** returns **0**,
> and **end** returns the index of the last child component in the data source.
> 
> When the lazy loading feature of this component becomes ineffective
> due to the parent component configuration conditions mentioned above,
> all child components are loaded and laid out. In this case, in the **onVisibleIndexesChange** callback,
> **start** returns **0**, and **end** returns the index of the last child component in the data source.
> 
> The parent component here refers to the nearest upper-level scroll component of the current component.
> For specific meanings in other documents, refer to the corresponding content.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-LazyGridLayoutAttribute-onVisibleIndexesChange(callback: OnVisibleIndexesChangeCallback | undefined): T--><!--Device-LazyGridLayoutAttribute-onVisibleIndexesChange(callback: OnVisibleIndexesChangeCallback | undefined): T-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [OnVisibleIndexesChangeCallback](arkts-arkui-common-comp-onvisibleindexeschangecallback-t.md) &#124; undefined | Yes | Callback for the **onVisibleIndexesChange** event. When the method input parameter is **undefined**, the listening is canceled. |

**Return value:**

| Type | Description |
| --- | --- |
| T | Returns the current **LazyVGridLayout** component itself for chained calls. |

## rowsGap

```TypeScript
rowsGap(value: LengthMetrics): T
```

Sets the gap between rows. The default value is **0vp**. If a value less than 0 is set, the default value is used.

**Since:** 19

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 19.

<!--Device-LazyGridLayoutAttribute-rowsGap(value: LengthMetrics): T--><!--Device-LazyGridLayoutAttribute-rowsGap(value: LengthMetrics): T-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | LengthMetrics | Yes | Spacing between rows.<br>Value range: [0, +∞) |

**Return value:**

| Type | Description |
| --- | --- |
| T | Current **LazyVGridLayout** component itself, used to support chained calls. |

## sticky

```TypeScript
sticky(sticky: StickyStyle | undefined): T
```

Sets the sticky style of [header](#header) and [footer](#footer).

When this component scrolls into the visible area along with the scroll container and the header stick-to-top or footer stick-to-bottom mode is set through **sticky**, the header sticks to the top of the visible area of the scroll container, and the footer sticks to the bottom of the visible area of the scroll container.

> **NOTE:** 
> 
> Due to floating-point calculation precision issues, gaps may appear during scrolling after **sticky** is set. This can be resolved by using [pixelRound](arkts-arkui-common-comp-commonmethod-c.md#pixelround) to round the current component's pixels downward.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-LazyGridLayoutAttribute-sticky(sticky: StickyStyle | undefined): T--><!--Device-LazyGridLayoutAttribute-sticky(sticky: StickyStyle | undefined): T-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| sticky | [StickyStyle](arkts-arkui-list-comp-stickystyle-e.md) &#124; undefined | Yes | Sticky style of the header and footer components. The **sticky** attribute can be set to **StickyStyle.Header** or **StickyStyle.Footer**, or to **StickyStyle.BOTH** to support both header stick-to-top and footer stick-to-bottom.<br>When the method input parameter is **undefined**, the default value **StickyStyle.None** is restored. <br>When not set through this API, the header does not stick to the top and the footer does not stick to the bottom by default. |

**Return value:**

| Type | Description |
| --- | --- |
| T | Returns the current **LazyVGridLayout** component itself for chained calls. |
