# Custom Component Layout

<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @song-song-song-->
<!--Designer: @fenglinbailu-->
<!--Tester: @liuli0427-->
<!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=36e7207cad20c4ef453cb5bda48f835acde97674 translatedAt=2026-08-28T01:26:21.226Z pushedAt=2026-08-28T08:50:36.239Z -->

The custom layout of a custom component allows developers to precisely control the positions and sizes of child components through data calculation by using the onMeasureSize and onPlaceChildren APIs, achieving more flexible layout effects. It applies to scenarios such as implementing complex non-standard layouts, when built-in layout components cannot meet specific arrangement requirements, and when the positions and sizes of child components need to be calculated based on dynamic data.

> **NOTE**
>
> The initial APIs of this module are supported since API version 9. Newly added APIs will be marked with a superscript to indicate their earliest API version.
>
> Implementing either **onMeasureSize** or **onPlaceChildren** in a custom component is considered as implementing a custom layout. **onMeasureSize** measures and returns the size of the custom component, and **onPlaceChildren** lays out the positions of child components. To achieve a complete custom layout effect, you are advised to implement both methods: after **onMeasureSize** determines the component size, **onPlaceChildren** can correctly lay out child components based on that size. For details about the parameters, see the detailed description of the corresponding APIs.
>
> Since API version 20, in a custom component with a custom layout, if a child component sets the **fixAtIdealSize** property of the [LayoutPolicy](./ts-universal-attributes-size.md#layoutpolicy15) object, the size is not subject to the parent component constraints and is laid out completely according to the size range customized by the developer.
>
> Lazy loading (including [Repeat](../../../ui/rendering-control/arkts-new-rendering-control-repeat.md) and [LazyForEach](../../../ui/rendering-control/arkts-rendering-control-lazyforeach.md)) is not supported in a custom layout.

## onMeasureSize<sup>10+</sup>

onMeasureSize?(selfLayoutInfo: GeometryInfo, children: Array&lt;Measurable&gt;, constraint: ConstraintSizeOptions): SizeResult

When the custom component determines its size, ArkUI (ArkUI framework) passes the node information and size range of the custom component to the developer through **onMeasureSize**. State variables are not allowed to be changed in the **onMeasureSize** function.

> **NOTE**
>
> - When using custom layout methods, you are advised to implement both **onMeasureSize** and **onPlaceChildren**. Otherwise, layout exceptions may occur.
> - Lazy loading (including Repeat and **LazyForEach**) is not supported in a custom layout.
> - The size information set on the parent container (custom component), except **aspectRatio**, has a lower priority than the size information set by **onMeasureSize**.

**Atomic service API**: This API can be used in atomic services since API version 11.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name        | Type                                                      | Mandatory|Description                                                        |
| -------------- | ---------------------------------------------------------- | ---|------------------------------------------------------------ |
| selfLayoutInfo | [GeometryInfo](#geometryinfo10)                            | Yes | Layout information of the parent component (custom component).<br>**NOTE**<br>During the first layout, the attributes set on the component itself prevail.                                    |
| children       | Array&lt;[Measurable](#measurable10)&gt;                   | Yes | Measurement information obtained after calculating the child component size.<br>**NOTE**<br>If no size information is set for a child component, the child component retains its previous size. If the child component has never had a size set, its size defaults to 0. |
| constraint     | [ConstraintSizeOptions](ts-types.md#constraintsizeoptions) | Yes | Layout constraint information passed in by the parent component, including constraint conditions such as **minWidth**, **maxWidth**, **minHeight**, and **maxHeight**. Value principle: **minWidth** ≤ **maxWidth** and **minHeight** ≤ **maxHeight**. Unit: vp.                                       |

**Return value**

| Type                       | Description          |
| --------------------------- | -------------- |
| [SizeResult](#sizeresult10) | Size information of the custom component itself, including the measured width and height. |

## onPlaceChildren<sup>10+</sup>

onPlaceChildren?(selfLayoutInfo: GeometryInfo, children: Array&lt;Layoutable&gt;, constraint: ConstraintSizeOptions): void

When the custom component determines its position, the ArkUI framework passes the layout information of the child nodes of the custom component to the custom component through **onPlaceChildren**. State variables are not allowed to be changed in the **onPlaceChildren** function.

**Atomic service API**: This API can be used in atomic services since API version 11.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name           | Type                                                        |Mandatory| Description              |
|----------------|------------------------------------------------------------|---|------------------|
| selfLayoutInfo | [GeometryInfo](#geometryinfo10)                            | Yes | Layout information of the parent component (custom component).         |
| children       | Array&lt;[Layoutable](#layoutable10)&gt;                   |Yes|Array containing layout information for all child components after measurement.        |
| constraint     | [ConstraintSizeOptions](ts-types.md#constraintsizeoptions) | Yes | Layout constraint information passed in by the parent component, including constraint conditions such as **minWidth**, **maxWidth**, **minHeight**, and **maxHeight**. Value principle: **minWidth** ≤ **maxWidth**, **minHeight** ≤ **maxHeight**; unit: vp. |

**Example**

For an example, see [Custom Layout Code Example](#example-1-implementing-a-custom-layout).

## GeometryInfo<sup>10+</sup>

Provides layout information of the parent component (a custom component). Inherits from [SizeResult](#sizeresult10). In the **onMeasureSize** and **onPlaceChildren** methods, the **GeometryInfo** object can be obtained through the **selfLayoutInfo** parameter. It contains the border width, margin, and padding information of the parent component, which developers need to consider when calculating the layout of child components.

**Atomic service API**: This API can be used in atomic services since API version 11.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name| Type| Read-Only| Optional| Description|
| -------- | -------- | -------- | -------- | -------- |
| borderWidth | [EdgeWidth](ts-types.md) |No|No| Border width of the parent component.<br>Unit: vp.            |
| margin      | [Margin](ts-types.md#margin)       | No|No|Margin of the parent component. <br>Unit: vp.       |
| padding     | [Padding](ts-types.md#padding)   |No|No| Padding of the parent component.<br>Unit: vp. |

## Layoutable<sup>10+</sup>

Provides layout information of a child component. The **Layoutable** object is created and passed in by the ArkUI framework when **onPlaceChildren** is called. It contains the measurement result and unique identifier of the child component. Developers set the position of the child component through the **layout** method of **Layoutable**, and obtain the margin information of the child component through the **getMargin**, **getPadding**, and **getBorderWidth** methods for precise layout calculation.

**Atomic service API**: This API can be used in atomic services since API version 11.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

### Attributes

| Name        | Type      | Read-Only|Optional|  Description                                                     |
|--------------|---------------------------------- | ------|-----------------------------------------------------|---------------------|
| measureResult| [MeasureResult](#measureresult10) |   No|No| Size information of the child component after measurement.<br>**Atomic service API:** This API can be used in atomic services since API version 11.<br>Unit: vp     |
| uniqueId<sup>18+</sup>| number | No | Yes | Unique ID assigned by the system to the child component. It is used to uniquely identify the child component for subsequent operations (for example, obtaining the **FrameNode** through **getFrameNodeByUniqueId**). The value range is [0, +∞).<br>**Atomic service API:** This API can be used in atomic services since API version 18.<br>**Model restriction:** This API can be used only in the stage model.|

### layout<sup>10+</sup>

layout(position: Position): void

Call this method to set the position information of the child component.

**Atomic service API**: This API can be used in atomic services since API version 11.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name        | Type                                                   | Mandatory                |Description        |
|-----------------|---------------------------------------------------------|---------------------|-------------|
|   position      | [Position](ts-types.md#position)                        | Yes                  |   Absolute position, containing the x and y coordinates (with the origin at the upper left corner of the parent component, the x-axis pointing right as positive and the y-axis pointing down as positive). Unit: vp.   |

### getMargin<sup>12+</sup>

getMargin(): DirectionalEdgesT&lt;number&gt;

Obtains the margin information of the child component.

**Atomic service API**: This API can be used in atomic services since API version 12.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Return value**

| Type                         | Description                                       |
|------------------------------------|---------------------------------------------|
| [DirectionalEdgesT](./ts-types.md#directionaledgestt12)&lt;number&gt;  |  Margin object of the child component, containing the margin values in four directions. Unit: vp.   |

### getPadding<sup>12+</sup>

getPadding(): DirectionalEdgesT&lt;number&gt;

Obtains the padding information of the child component.

**Atomic service API**: This API can be used in atomic services since API version 12.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

 **Return value**

| Type                         | Description                                       |
|------------------------------------|---------------------------------------------|
| [DirectionalEdgesT](./ts-types.md#directionaledgestt12)&lt;number&gt;  |  Padding object of the child component, containing padding values in four directions. Unit: vp.  |

### getBorderWidth<sup>12+</sup>

getBorderWidth(): DirectionalEdgesT&lt;number&gt;

Obtains the **borderWidth** information of the child component.

**Atomic service API**: This API can be used in atomic services since API version 12.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Return value**

| Type                         | Description                                       |
|------------------------------------|---------------------------------------------|
| [DirectionalEdgesT](./ts-types.md#directionaledgestt12)&lt;number&gt;  |  Border width object of the child component, containing the border width values in four directions. Unit: vp.  |

## Measurable<sup>10+</sup>

Provides measurement information of a child component. The **Measurable** object is created and passed in by the ArkUI framework when **onMeasureSize** is called, and is used in the measurement phase. Unlike **Layoutable** (used in the layout phase), Measurable is mainly used to measure the size of a child component. Developers set constraint conditions and obtain measurement results through the **measure** method. **Measurable** and **Layoutable** are two representations of the same child component in different layout phases.

**Atomic service API**: This API can be used in atomic services since API version 11.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

### Attributes

**Atomic service API**: This API can be used in atomic services since API version 18.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name| Type| Read-Only| Optional| Description|
| -------- | -------- | -------- | -------- | -------- |
| uniqueId<sup>18+</sup>| number | No | Yes | Unique ID assigned by the system to the child component. It uniquely identifies the child component for subsequent operations (for example, obtaining the **FrameNode** through **getFrameNodeByUniqueId**). The value range is [0, +∞). The system automatically assigns a UniqueID to each child component. Developers can read it as needed and do not need to set it proactively.<br>**Model restriction:** This API can be used only in the stage model.|

### measure<sup>10+</sup>

 measure(constraint: ConstraintSizeOptions) : MeasureResult

Imposes size constraints on the child component and returns the measured layout information of the component.

 **Atomic service API**: This API can be used in atomic services since API version 11.

 **Model restriction**: This API can be used only in the stage model.

 **System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name        | Type                                                   | Mandatory                |Description        |
|-----------------|---------------------------------------------------------|---------------------|-------------|
|   constraint    | [ConstraintSizeOptions](ts-types.md#constraintsizeoptions)  | Yes            |   Constraint size, including constraint conditions such as **minWidth**, **maxWidth**, **minHeight**, and **maxHeight**, used to limit the size range of the child component. Value principle: **minWidth** ≤ **maxWidth**, **minHeight** ≤ **maxHeight**; unit: vp.  |

**Return value**

| Type                              | Description                    |
|------------------------------------|-------------------------|
| [MeasureResult](#measureresult10) | Layout information of the component after measurement, including the measured width and height. |

### getMargin<sup>12+</sup>

 getMargin(): DirectionalEdgesT&lt;number&gt;

Obtains the margin information of the child component.

**Atomic service API**: This API can be used in atomic services since API version 12.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Return value**

| Type                              | Description                    |
|------------------------------------|-------------------------|
| [DirectionalEdgesT](./ts-types.md#directionaledgestt12)&lt;number&gt; | Margin object of the child component, containing the margin values in four directions. Unit: vp. |

### getPadding<sup>12+</sup>

getPadding(): DirectionalEdgesT&lt;number&gt;

Obtains the padding information of the child component.

**Atomic service API**: This API can be used in atomic services since API version 12.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Return value**

| Type                              | Description                    |
|------------------------------------|-------------------------|
| [DirectionalEdgesT](./ts-types.md#directionaledgestt12)&lt;number&gt; | Padding object of the child component, containing padding values in four directions. Unit: vp. |

### getBorderWidth<sup>12+</sup>

getBorderWidth(): DirectionalEdgesT&lt;number&gt;

Obtains the **borderWidth** information of the child component.

**Atomic service API**: This API can be used in atomic services since API version 12.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Return value**

| Type                              | Description                    |
|------------------------------------|-------------------------|
| [DirectionalEdgesT](./ts-types.md#directionaledgestt12)&lt;number&gt; | Border width object of the child component, containing the border width values in four directions. Unit: vp. |

## MeasureResult<sup>10+</sup>

Provides the measurement result of the component. This API inherits from [SizeResult](#sizeresult10).

**Atomic service API**: This API can be used in atomic services since API version 11.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

## SizeResult<sup>10+</sup>

Provides the component size information.

> **NOTE**
>
> - When creating a custom layout in builder form, only **this.builder()** is allowed in the **build()** method of the custom component, which is the recommended usage in the example.
> - The size information set on the parent container (custom component), except **aspectRatio**, has a lower priority than the size information set by **onMeasureSize**.
> - The position information set on the child component (**offset**, **position**, **markAnchor**) has a higher priority than the position information set by **onPlaceChildren**. Other position setting attributes do not take effect.

**Atomic service API**: This API can be used in atomic services since API version 11.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name    | Type  |Read-Only|Optional| Description   |
|--------|--------|------|------|-------|
| width  | number | No|No|Width after measurement.<br>Unit: vp.<br>Value range: [0, +∞). |
| height | number | No|No|Height after measurement.<br>Unit: vp.<br>Value range: [0, +∞). |

## onLayout<sup>(deprecated)</sup>

onLayout?(children: Array&lt;LayoutChild&gt;, constraint: ConstraintSizeOptions): void

When the custom component determines the positions of its child components, the ArkUI framework passes the child node information of the custom component and its own size range to the custom component through **onLayout**. Developers can lay out child components in this method. State variables are not allowed to be changed in the **onLayout** function.

> **NOTE**
>
> This API is supported since API version 9 and deprecated since API version 10. You are advised to use [onPlaceChildren](#onplacechildren10) instead.

**Widget capability**: This API can be used in ArkTS widgets since API version 9.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name       | Type                                                        | Mandatory|Description              |
|------------|------------------------------------------------------------|------|------------------|
| children   | Array&lt;[LayoutChild](#layoutchilddeprecated)&gt;                | Yes | Child component layout information.        |
| constraint | [ConstraintSizeOptions](ts-types.md#constraintsizeoptions) | Yes | Constraint information of the parent component, including constraint conditions such as **minWidth**, **maxWidth**, **minHeight**, and **maxHeight**. Value principle: **minWidth** ≤ **maxWidth**, **minHeight** ≤ **maxHeight**; unit: vp. |

## onMeasure<sup>(deprecated)</sup>

onMeasure?(children: Array&lt;LayoutChild&gt;, constraint: ConstraintSizeOptions): void

When the custom component determines its size, the ArkUI framework passes the child node information of the custom component and its own size range to the custom component through **onMeasure**. Developers can measure child components in this method. State variables are not allowed to be changed in the **onMeasure** function.

> **NOTE**
>
> This API is supported since API version 9 and deprecated since API version 10. You are advised to use [onMeasureSize](#onmeasuresize10) instead.

**Widget capability**: This API can be used in ArkTS widgets since API version 9.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name       | Type                                                        |Mandatory| Description              |
|------------|------------------------------------------------------------|------|------------------|
| children   | Array&lt;[LayoutChild](#layoutchilddeprecated)&gt;                  | Yes |Child component layout information.        |
| constraint | [ConstraintSizeOptions](ts-types.md#constraintsizeoptions) | Yes | Constraint information of the parent component, including constraint conditions such as **minWidth**, **maxWidth**, **minHeight**, and **maxHeight**. Value principle: **minWidth** ≤ **maxWidth** and **minHeight** ≤ **maxHeight**. Unit: vp. |

## LayoutChild<sup>(deprecated)</sup>

Provides the child component layout information.

> **NOTE**
>
> This API is supported since API version 9 and deprecated since API version 10. You are advised to use [Measurable](#measurable10) or [Layoutable](#layoutable10) instead.

### Attributes

**Widget capability**: This API can be used in ArkTS widgets since API version 9.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name      | Type                                                    | Read-Only|Optional|Description                                  |
| ---------- | ------------------------------------------------------------ | ------|------|-------------------------------------- |
| name       | string                                                       | No|No|Name of the child component.                          |
| id         | string                                                       | No|No|ID of the child component.                            |
| constraint | [ConstraintSizeOptions](ts-types.md#constraintsizeoptions)   | No|No|Constraint size of the child component. Value principle: **minWidth** ≤ **maxWidth**, **minHeight** ≤ **maxHeight**. Unit: vp. |
| borderInfo | [LayoutBorderInfo](#layoutborderinfodeprecated)              | No|No|Provides the border information of the child component.                    |
| position   | [Position](ts-types.md#position)                             | No|No|Position coordinates of the child component. Unit: vp.                       |

### measure<sup>(deprecated)</sup>

measure(childConstraint: ConstraintSizeOptions)

Applies specified size constraints to child components.

> **NOTE**
>
> This API is supported since API version 9 and deprecated since API version 10. You are advised to use [Measurable](#measurable10) or [Layoutable](#layoutable10) instead.

**Widget capability**: This API can be used in ArkTS widgets since API version 9.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name       | Type    |Mandatory| Description              |
|------------|-----------|------|------------------|
| childConstraint   | [ConstraintSizeOptions](ts-types.md#constraintsizeoptions) | Yes  | Constraint information about the size range of the child component, including constraint conditions such as **minWidth**, **maxWidth**, **minHeight**, and **maxHeight**. Unit: vp.|

### layout<sup>(deprecated)</sup>

layout(childLayoutInfo: LayoutInfo)

Applies the specified layout constraints to the child component.

> **NOTE**
>
> This API is supported since API version 9 and deprecated since API version 10. You are advised to use [Measurable](#measurable10) or [Layoutable](#layoutable10) instead.

**Widget capability**: This API can be used in ArkTS widgets since API version 9.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name       | Type    |Mandatory| Description              |
|------------|-----------|------|------------------|
| childLayoutInfo   | [LayoutInfo](#layoutinfodeprecated) | Yes  |Layout information of the child component, including **position** (position coordinates) and **constraint** (constraint size). The position is used to set the **position** of the child component, and the constraint is used to pass **constraint** information to the child component.|

## LayoutBorderInfo<sup>(deprecated)</sup>

Provides the border information of the child component.

> **NOTE**
>
> This API is supported since API version 9 and deprecated since API version 10. You are advised to use [getBorderWidth](#getborderwidth12), [getMargin](#getmargin12), and [getPadding](#getpadding12) instead.

**Widget capability**: This API can be used in ArkTS widgets since API version 9.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name| Type| Read-Only| Optional| Description|
| -------- | -------- | -------- | -------- | -------- |
| borderWidth | [EdgeWidths](ts-types.md#edgewidths9) | No|No|Border width type, used to describe the width of the component border in different directions.<br>Unit: vp. |
| margin      | [Margin](ts-types.md#margin)         | No|No|Margin type, used to describe the margin of the component in different directions.<br>Unit: vp.   |
| padding     | [Padding](ts-types.md#padding)       | No|No|Padding type, used to describe the padding of the component in different directions.<br>Unit: vp.   |

## LayoutInfo<sup>(deprecated)</sup>

Provides the child component layout information.

> **NOTE**
>
> This API is supported since API version 9 and deprecated since API version 10. You are advised to use [Layoutable](#layoutable10) instead.

**Widget capability**: This API can be used in ArkTS widgets since API version 9.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name      | Type                                                  | Read-Only|Optional|Description            |
| ---------- | ---------------------------------------------------------- | ------|------|---------------- |
| position   | [Position](ts-types.md#position)                           |No|No| Position coordinates of the child component. Unit: vp. |
| constraint | [ConstraintSizeOptions](ts-types.md#constraintsizeoptions) | No | No | Constraint size of the child component. Value principle: **minWidth** ≤ **maxWidth**, **minHeight** ≤ **maxHeight**; unit: vp. |

## Example

### Example 1: Implementing a Custom Layout

This example demonstrates how to implement a custom layout.

```ts
// xxx.ets
@Entry
@Component
struct Index {
  build() {
    Column() {
      CustomLayout({ builder: ColumnChildren })
    }
  }
}

// Pass multiple components through the builder as the first-level child components of the custom component (that is, excluding container components such as Column).
@Builder
function ColumnChildren() {
  ForEach([1, 2, 3], (index: number) => { // LazyForEach is not supported.
    Text('S' + index)
      .fontSize(30)
      .width(100)
      .height(100)
      .borderWidth(2)
      .offset({ x: 10, y: 20 })
  })
}

@Component
struct CustomLayout {
  @Builder
  doNothingBuilder() {
  };

  @BuilderParam builder: () => void = this.doNothingBuilder;
  result: SizeResult = {
    width: 0,
    height: 0
  };

  // Step 1: Calculate the size of each child component.
  onMeasureSize(selfLayoutInfo: GeometryInfo, children: Array<Measurable>, constraint: ConstraintSizeOptions) {
    let size = 100;
    // Set the initial constraint baseline to 100 vp, and accumulate half of the child component width in each iteration to gradually increase the constraint.
    children.forEach((child) => {
      let result: MeasureResult = child.measure({
        minHeight: size,
        minWidth: size,
        maxWidth: size,
        maxHeight: size
      })
      size += result.width / 2;
    })
    this.result.width = 100;
    this.result.height = 400;
    return this.result;
  }
  // Step 2: Place each child component.
  onPlaceChildren(selfLayoutInfo: GeometryInfo, children: Array<Layoutable>, constraint: ConstraintSizeOptions) {
    // Calculate the child component positions in reverse from a fixed starting position to achieve a bottom-to-top reverse layout effect.
    let startPos = 300;
    children.forEach((child) => {
      let pos = startPos - child.measureResult.height;
      child.layout({ x: pos, y: pos })
    })
  }

  build() {
    this.builder()
  }
}
```

![custom_layout10.png](figures/custom_layout10.png)

### Example 2: Determining Whether to Participate in Layout Calculation

This example shows how to determine whether a component participates in layout calculation based on its position.

```ts
// xxx.ets
@Entry
@Component
struct Index {
  build() {
    Column() {
      CustomLayout({ builder: ColumnChildren })
    }
    .justifyContent(FlexAlign.Center)
    .width('100%')
    .height('100%')
  }
}

@Builder
function ColumnChildren() {
  ForEach([1, 2, 3], (item: number, index: number) => { // LazyForEach is not supported.
    Text('S' + item)
      .fontSize(20)
      .width(60 + 10 * index)
      .height(100)
      .borderWidth(2)
      .margin({ left:10 })
      .padding(10)
  })
}

@Component
struct CustomLayout {
  // Lay out only one row, and hide child components that are too large for the available space.
  @Builder
  doNothingBuilder() {
  };

  @BuilderParam builder: () => void = this.doNothingBuilder;
  result: SizeResult = {
    width: 0,
    height: 0
  };
  overFlowIndex: number = -1;

  onPlaceChildren(selfLayoutInfo: GeometryInfo, children: Array<Layoutable>, constraint: ConstraintSizeOptions) {
    let currentX = 0;
    let infinity = 100000;
    if (this.overFlowIndex == -1) {
      this.overFlowIndex = children.length;
    }
    for (let index = 0; index < children.length; ++index) {
      let child = children[index];
      if (index >= this.overFlowIndex) {
        // Hide any child component that extends beyond the area of its parent component by placing it in a distant position.
        child.layout({x: infinity, y: 0});
        continue;
      }
      child.layout({ x: currentX, y: 0 })
      let margin = child.getMargin();
      currentX += child.measureResult.width + margin.start + margin.end;
    }
  }

  onMeasureSize(selfLayoutInfo: GeometryInfo, children: Array<Measurable>, constraint: ConstraintSizeOptions) {
    let width = 0;
    let height = 0;
    this.overFlowIndex = -1;
    // Restrict the maximum width of the parent component to the smaller value between 200 vp and the maximum width from layout constraints.
    let maxWidth = Math.min(200, constraint.maxWidth as number);
    for (let index = 0; index < children.length; ++index) {
      let child = children[index];
      let childResult: MeasureResult = child.measure({
          minHeight: constraint.minHeight,
          minWidth: constraint.minWidth,
          maxWidth: constraint.maxWidth,
          maxHeight: constraint.maxHeight
      })
      let margin = child.getMargin();
      let newWidth = width + childResult.width + margin.start + margin.end;
      if (newWidth > maxWidth) {
        // Record the index of the component that should not be laid out.
        this.overFlowIndex = index;
        break;
      }
      // Update the parent component's cumulative width and height.
      width = newWidth;
      height = Math.max(height, childResult.height + margin.top + margin.bottom);
    }
    this.result.width = width;
    this.result.height = height;
    return this.result;
  }

  build() {
    this.builder()
  }
}
```

![custom_layout_demo2.png](figures/custom_layout_demo2.png)

### Example 3: Obtaining the Child Component FrameNode and Setting Related Attributes

This example shows how to obtain the [FrameNode](../js-apis-arkui-frameNode.md) of a child component using **uniqueId** and change its size and background color using the FrameNode API.

```ts
import { FrameNode, NodeController } from '@kit.ArkUI';
@Entry
@Component
struct Index {
  build() {
    Column() {
      CustomLayout()
    }
  }
}

class MyNodeController extends NodeController {
  private rootNode: FrameNode | null = null;
  makeNode(uiContext: UIContext): FrameNode | null {
    this.rootNode = new FrameNode(uiContext)
    return this.rootNode
  }
}

@Component
struct CustomLayout {
  @Builder
  childrenBuilder() {
    ForEach([1, 2, 3], (index: number) => { // LazyForEach is not supported currently.
      NodeContainer(new MyNodeController())
    })
  };

  @BuilderParam builder: () => void = this.childrenBuilder;
  result: SizeResult = {
    width: 0,
    height: 0
  };

  onPlaceChildren(selfLayoutInfo: GeometryInfo, children: Array<Layoutable>, constraint: ConstraintSizeOptions) {
    // Arrange child components horizontally with an interval of 10 vp.
    let prev = 0;
    children.forEach((child) => {
      let pos = prev + 10;
      prev = pos + child.measureResult.width
      child.layout({ x: pos, y: 0 })
    })
  }

  onMeasureSize(selfLayoutInfo: GeometryInfo, children: Array<Measurable>, constraint: ConstraintSizeOptions) {
    let size = 100;
    children.forEach((child) => {
      console.info('child uniqueId: ', child.uniqueId)
      const uiContext = this.getUIContext()
      if (uiContext) {
        let node: FrameNode | null = uiContext.getFrameNodeByUniqueId(child.uniqueId) // Obtain the FrameNode of the NodeContainer component.
        if (node) {
          node.getChild(0)!.commonAttribute.width(100)
          node.getChild(0)!.commonAttribute.height(100)
          node.getChild(0)!.commonAttribute.backgroundColor(Color.Pink) // Change the size and background color of the FrameNode.
        }
      }
      child.measure({ minHeight: size, minWidth: size, maxWidth: size, maxHeight: size })
    })
    this.result.width = 320;
    this.result.height = 100;
    return this.result;
  }

  build() {
    this.builder()
  }
}
```

![custom_layout_demo3.jpg](figures/custom_layout_demo3.jpg)

### Example 4: Allowing the Child Component to Ignore Parent Component Size Constraints

This example demonstrates how to use the **fixAtIdealSize** property of the [LayoutPolicy](./ts-universal-attributes-size.md#layoutpolicy15) object to allow the child component to ignore parent component size constraints.

```ts
@Entry
@Component
struct Index {
  @Builder
  ColumnChildrenText() {
    Text('=====Text=====Text=====Text=====Text=====Text=====Text=====Text=====Text' )
      .fontSize(16).fontColor(Color.Black)
      .borderWidth(2).backgroundColor('#fff8dc')
      .width(LayoutPolicy.fixAtIdealSize) // Set the child component's width to be unrestricted by the parent component.
      .height(LayoutPolicy.fixAtIdealSize)  // Set the child component's height to be unrestricted by the parent component.
  }

  build() {
    Column() {
      Column() {
        CustomLayoutText({ builder: this.ColumnChildrenText })
          .backgroundColor('#f0ffff').borderRadius(20).margin(10)
      }
      .width(300)
      .height(150)
      .margin(10)
      .backgroundColor(Color.Pink)
    }
    .width(350)
    .height(680)
    .margin(20)
    .alignItems(HorizontalAlign.Center)
  }
}

@Component
struct CustomLayoutText {
  @Builder
  doSomethingBuilder() {
  };

  @BuilderParam
  builder: () => void = this.doSomethingBuilder;
  result: SizeResult = {
    width: 0,
    height: 0
  };
  // The custom component implements custom layout.
  onPlaceChildren(selfLayoutInfo: GeometryInfo, children: Array<Layoutable>, constraint: ConstraintSizeOptions) {
    let posY = 20;
    children.forEach((child) => {
      let posX = (selfLayoutInfo.width - child.measureResult.width) / 2;
      child.layout({ x: posX, y: posY })
      posY += child.measureResult.height + 30;
    })
  }

  onMeasureSize(selfLayoutInfo: GeometryInfo, children: Array<Measurable>, constraint: ConstraintSizeOptions) {
    children.forEach((child) => {
      child.measure({ maxWidth: 335, maxHeight: 50 }) // Set the size limit of the child component of the custom component.
    })
    this.result.width = 200;
    this.result.height = 130;
    return this.result;
  }

  build() {
    this.builder()
  }
}
```

![custom_layout_demo4.jpg](figures/custom_layout_demo4.jpg)