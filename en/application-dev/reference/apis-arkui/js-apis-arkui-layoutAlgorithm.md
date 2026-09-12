# LayoutAlgorithm
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @zju_ljz-->
<!--Designer: @fenglinbailu-->
<!--Tester: @liuli0427-->
<!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=75a7d62c0702c21a06ca0119552a942305a023cc translatedAt=2026-08-29T09:33:01.878Z pushedAt=2026-08-31T11:35:40.228Z -->

Provides layout algorithms supported by the [DynamicLayout](./arkui-ts/ts-container-dynamiclayout.md) component.

**LayoutAlgorithm** is the base type of layout algorithms for the dynamic layout container. It provides multiple layout algorithm implementations, including linear layout, stack layout, and grid layout. You can select an appropriate layout algorithm based on the actual scenario, or inherit **CustomLayoutAlgorithm** to implement a custom layout.

> **NOTE**
>
> - The initial APIs of this module are supported since API version 24. Newly added APIs will be marked with a superscript to indicate their earliest API version.
>
> - The APIs of this module can be used only in the stage model.

## Modules to Import

```ts
import { LayoutAlgorithm, CustomLayoutAlgorithm, RowLayoutAlgorithm, ColumnLayoutAlgorithm, StackLayoutAlgorithm, GridLayoutAlgorithm } from '@kit.ArkUI';
```

## LayoutAlgorithm

Basic layout algorithm of the [DynamicLayout](./arkui-ts/ts-container-dynamiclayout.md) container.

> **NOTE**
>
> This type of variable can be assigned a specific layout algorithm class object, such as an object of the [CustomLayoutAlgorithm](#customlayoutalgorithm) or [RowLayoutAlgorithm](#rowlayoutalgorithm) class.

**Model restriction**: This API can be used only in the stage model.

**Widget capability**: This API can be used in ArkTS widgets since API version 24.

**Atomic service API**: This API can be used in atomic services since API version 24.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

## CustomLayoutAlgorithm

A custom layout algorithm class, which allows you to implement custom measurement and layout logic. It is suitable for complex layout scenarios that require fine-grained control over child component sizes and positions, such as waterfall flow layout, irregular grid layout, and dynamic flow layout. By overriding **onMeasure** and **onLayout**, you can implement layout strategies that are not covered by the built-in layout algorithms.

**Decorator**: [\@ObservedV2](../../ui/state-management/arkts-new-observedV2-and-trace.md)

> **NOTE**
>
> The object of the **CustomLayoutAlgorithm** class can be used as the input parameter of the [DynamicLayout](./arkui-ts/ts-container-dynamiclayout.md) component to specify a layout algorithm.

### onMeasure
onMeasure(self: FrameNode, constraint: LayoutConstraint): void

Customizes the size of the child component to be measured. When the size of the dynamic layout component is determined, the ArkUI framework will transfer the FrameNode and layout constraint of the component to you through **onMeasure**. State variables should not be changed in this callback.

> **NOTE**
>
> - **onMeasure** and [onLayout](#onlayout) usually need to be used together to complete the full custom layout process. The framework first calls **onMeasure** to measure the child component size, and then calls **onLayout** to set the child component position.
> - In this API, you can call [getChild()](js-apis-arkui-frameNode.md#getchild12) of [FrameNode](js-apis-arkui-frameNode.md#framenode-1) to obtain the child component FrameNode, call [measure()](js-apis-arkui-frameNode.md#measure12) of [FrameNode](js-apis-arkui-frameNode.md#framenode-1) to measure the child component size. For details, see [Example 1: Implementing Waterfall Layout Using a Custom Layout Algorithm](./arkui-ts/ts-container-dynamiclayout.md#example-1-implementing-waterfall-layout-using-a-custom-layout-algorithm).

**Model restriction**: This API can be used only in the stage model.

**Widget capability**: This API can be used in ArkTS widgets since API version 24.

**Atomic service API**: This API can be used in atomic services since API version 24.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type| Mandatory| Description|
| ---- | ---- | ---- | ---- |
| self | [FrameNode](js-apis-arkui-frameNode.md#framenode-1) | Yes | Entity node of the dynamic layout component in the component tree, which is used to obtain the child component FrameNode and measure the child component size.|
| constraint | [LayoutConstraint](js-apis-arkui-frameNode.md#layoutconstraint12) | Yes| Layout constraint used by the dynamic layout component for measurement.|

### onLayout
onLayout(self: FrameNode, position: Position): void

Customizes the position of the child component to be arranged. When the position of the dynamic layout component is determined, the ArkUI framework will transfer the FrameNode and layout position of the component to you through **onLayout**. State variables should not be changed in this callback.

> **NOTE**
>
> - **onLayout** and [onMeasure](#onmeasure) usually need to be used together to complete the full custom layout process. The framework first calls **onMeasure** to measure the child component size, and then calls **onLayout** to set the child component position.
> - In this API, you can call [getChild()](js-apis-arkui-frameNode.md#getchild12) of [FrameNode](js-apis-arkui-frameNode.md#framenode-1) to obtain the child component FrameNode, call [layout()](js-apis-arkui-frameNode.md#layout12) of [FrameNode](js-apis-arkui-frameNode.md#framenode-1) to set the child component position. For details, see [Example 1: Implementing Waterfall Layout Using a Custom Layout Algorithm](./arkui-ts/ts-container-dynamiclayout.md#example-1-implementing-waterfall-layout-using-a-custom-layout-algorithm).

**Model restriction**: This API can be used only in the stage model.

**Widget capability**: This API can be used in ArkTS widgets since API version 24.

**Atomic service API**: This API can be used in atomic services since API version 24.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type| Mandatory| Description|
| ---- | ---- | ---- | ---- |
| self | [FrameNode](js-apis-arkui-frameNode.md#framenode-1) | Yes | Entity node of the dynamic layout component in the component tree, which is used to obtain the child component FrameNode and set the child component position. |
| position | [Position](js-apis-arkui-graphics.md#position) | Yes| Position information used in layout of the dynamic layout component.|

**Example**

For details, see [Example 1: Implementing Waterfall Layout Using a Custom Layout Algorithm](./arkui-ts/ts-container-dynamiclayout.md#example-1-implementing-waterfall-layout-using-a-custom-layout-algorithm).

## RowLayoutAlgorithm

A horizontal linear layout algorithm class, which is used to implement horizontal linear arrangement of child components. It is suitable for scenarios where child components need to be arranged horizontally, such as horizontal lists, toolbars, tab bars, and action button groups. It supports setting the spacing between child components, vertical alignment mode, horizontal alignment mode, and arrangement direction, which provides layout capabilities similar to the **Row** component.

**Decorator**: [\@ObservedV2](../../ui/state-management/arkts-new-observedV2-and-trace.md)

> **NOTE**
>
> The object of the **RowLayoutAlgorithm** class can be used as the input parameter of the [DynamicLayout](./arkui-ts/ts-container-dynamiclayout.md) component to specify a layout algorithm.

### Attributes

**Model restriction**: This API can be used only in the stage model.

**Widget capability**: This API can be used in ArkTS widgets since API version 24.

**Atomic service API**: This API can be used in atomic services since API version 24.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name| Type| Read-Only| Optional| Description|
| ---- | ---- | ---- | ---- | ---- |
| space | [LengthMetrics](js-apis-arkui-graphics.md#lengthmetrics12) | No | Yes | Horizontal spacing between child components in a horizontal layout. Value range: a non-negative number.<br> Default value: **LengthMetrics.vp(0)** <br> Invalid values are treated as the default value.<br>Decorator: [@Trace](../../ui/state-management/arkts-new-observedV2-and-trace.md) |
| alignItems | [VerticalAlign](./arkui-ts/ts-appendix-enums.md#verticalalign) | No | Yes | Vertical alignment mode of all child components.<br> Default value: **VerticalAlign.Center** <br> Invalid values are treated as the default value.<br>Decorator: [@Trace](../../ui/state-management/arkts-new-observedV2-and-trace.md) |
| justifyContent | [FlexAlign](./arkui-ts/ts-appendix-enums.md#flexalign) | No | Yes | Horizontal alignment mode of all child components.<br> Default value: **FlexAlign.Start** <br> Invalid values are treated as the default value.<br>Decorator: [@Trace](../../ui/state-management/arkts-new-observedV2-and-trace.md) |
| isReverse | boolean | No | Yes | Whether to reverse the horizontal arrangement of child components. **true** indicates to reverse the horizontal arrangement of child components. The horizontal direction is affected by the common attribute [direction](./arkui-ts/ts-universal-attributes-location.md#direction). If the [direction](./arkui-ts/ts-universal-attributes-location.md#direction) attribute takes effect, the child components are arranged based on **direction** and then are reversed based on **isReverse**. **false** indicates to arrange child components in the horizontal direction in normal order.<br>Default value: **false** <br> Invalid values are treated as the default value.<br>Decorator: [@Trace](../../ui/state-management/arkts-new-observedV2-and-trace.md) |

### constructor

constructor(option?: RowLayoutAlgorithmOptions)

Constructs the horizontal linear layout algorithm class.

**Model restriction**: This API can be used only in the stage model.

**Widget capability**: This API can be used in ArkTS widgets since API version 24.

**Atomic service API**: This API can be used in atomic services since API version 24.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type| Mandatory| Description|
| ---- | ---- | ---- | ---- |
| option | [RowLayoutAlgorithmOptions](#rowlayoutalgorithmoptions) | No | Input parameters for constructing the horizontal linear layout algorithm, which are used to set the spacing, main axis alignment mode, cross axis alignment mode, and main axis arrangement direction of the layout algorithm. If not passed, the default value of each attribute is used.|

**Example**

For details, see [Example 2: Switching the Layout Algorithm](./arkui-ts/ts-container-dynamiclayout.md#example-2-switching-the-layout-algorithm).

## RowLayoutAlgorithmOptions

Sets the spacing, main axis alignment method, cross axis alignment method, and main axis arrangement direction of the horizontal linear layout algorithm.

**Model restriction**: This API can be used only in the stage model.

**Widget capability**: This API can be used in ArkTS widgets since API version 24.

**Atomic service API**: This API can be used in atomic services since API version 24.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name| Type| Read-Only| Optional| Description|
| ---- | ---- | ---- | ---- | ---- |
| space | [LengthMetrics](js-apis-arkui-graphics.md#lengthmetrics12) | No | Yes | Horizontal spacing between child components in a horizontal layout.<br>Value range: a non-negative number.<br>Default value: **LengthMetrics.vp(0)**<br>Invalid values are treated as the default value.|
| alignItems | [VerticalAlign](./arkui-ts/ts-appendix-enums.md#verticalalign) | No | Yes | Vertical alignment mode of all child components.<br>Default value: **VerticalAlign.Center**<br>Invalid values are treated as the default value.|
| justifyContent | [FlexAlign](./arkui-ts/ts-appendix-enums.md#flexalign) | No | Yes | Horizontal alignment mode of all child components.<br>Default value: **FlexAlign.Start**<br>Invalid values are treated as the default value.|
| isReverse | boolean | No | Yes | Whether to reverse the horizontal arrangement of child components. **true** indicates to reverse the horizontal arrangement of child components. The horizontal direction is affected by the common attribute [direction](./arkui-ts/ts-universal-attributes-location.md#direction). If the [direction](./arkui-ts/ts-universal-attributes-location.md#direction) attribute takes effect, the child components are arranged based on **direction** and then are reversed based on **isReverse**. **false** indicates to arrange child components in the horizontal direction in normal order.<br>Default value: **false**<br>Invalid values are treated as the default value.|

## ColumnLayoutAlgorithm

A vertical linear layout algorithm class, which is used to implement vertical linear arrangement of child components. It is suitable for scenarios where child components need to be arranged vertically, such as vertical lists, vertically stacked form items, and vertical menus. It supports setting the spacing between child components, horizontal alignment mode, vertical alignment mode, and arrangement direction, which provides layout capabilities similar to the **Column** component.

**Decorator**: [\@ObservedV2](../../ui/state-management/arkts-new-observedV2-and-trace.md)

> **NOTE**
>
> The object of the **ColumnLayoutAlgorithm** class can be used as the input parameter of the [DynamicLayout](./arkui-ts/ts-container-dynamiclayout.md) component to specify a layout algorithm.

### Attributes

**Model restriction**: This API can be used only in the stage model.

**Widget capability**: This API can be used in ArkTS widgets since API version 24.

**Atomic service API**: This API can be used in atomic services since API version 24.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name| Type| Read-Only| Optional| Description|
| ---- | ---- | ---- | ---- | ---- |
| space | [LengthMetrics](js-apis-arkui-graphics.md#lengthmetrics12) | No | Yes | Vertical spacing between child components in a vertical layout.<br>Value range: a non-negative number.<br>Default value: **LengthMetrics.vp(0)**<br>Invalid values are treated as the default value.<br>Decorator: [@Trace](../../ui/state-management/arkts-new-observedV2-and-trace.md) |
| alignItems | [HorizontalAlign](./arkui-ts/ts-appendix-enums.md#horizontalalign) | No | Yes | Horizontal alignment mode of all child components.<br>Default value: **HorizontalAlign.Center**<br>Invalid values are treated as the default value.<br>Decorator: [@Trace](../../ui/state-management/arkts-new-observedV2-and-trace.md) |
| justifyContent | [FlexAlign](./arkui-ts/ts-appendix-enums.md#flexalign) | No | Yes | Vertical alignment mode of all child components.<br>Default value: **FlexAlign.Start**<br>Invalid values are treated as the default value.<br>Decorator: [@Trace](../../ui/state-management/arkts-new-observedV2-and-trace.md) |
| isReverse | boolean | No | Yes | Whether to reverse the vertical arrangement of child components. **true** indicates to reverse the vertical arrangement of child components. The vertical direction is not affected by the common attribute **direction**. **false** indicates to arrange child components in the vertical direction in normal order.<br>Default value: **false**<br>Invalid values are treated as the default value.<br>Decorator: [@Trace](../../ui/state-management/arkts-new-observedV2-and-trace.md) |

### constructor

constructor(option?: ColumnLayoutAlgorithmOptions)

Constructs the vertical linear layout algorithm class.

**Model restriction**: This API can be used only in the stage model.

**Widget capability**: This API can be used in ArkTS widgets since API version 24.

**Atomic service API**: This API can be used in atomic services since API version 24.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type| Mandatory| Description|
| ---- | ---- | ---- | ---- |
| option | [ColumnLayoutAlgorithmOptions](#columnlayoutalgorithmoptions) | No | Input parameters for constructing the vertical linear layout algorithm, which are used to set the spacing, main axis alignment method, cross axis alignment method, and main axis arrangement direction of the layout algorithm. If not passed, the default value of each attribute is used.|

**Example**

For details, see [Example 2: Switching the Layout Algorithm](./arkui-ts/ts-container-dynamiclayout.md#example-2-switching-the-layout-algorithm).

## ColumnLayoutAlgorithmOptions

Sets the spacing, main axis alignment method, cross axis alignment method, and main axis arrangement direction of the vertical linear layout algorithm.

**Model restriction**: This API can be used only in the stage model.

**Widget capability**: This API can be used in ArkTS widgets since API version 24.

**Atomic service API**: This API can be used in atomic services since API version 24.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name| Type| Read-Only| Optional| Description|
| ---- | ---- | ---- | ---- | ---- |
| space | [LengthMetrics](js-apis-arkui-graphics.md#lengthmetrics12) | No | Yes | Vertical spacing between child components in a vertical layout.<br>Value range: a non-negative number.<br>Default value: **LengthMetrics.vp(0)**<br>Invalid values are treated as the default value.|
| alignItems | [HorizontalAlign](./arkui-ts/ts-appendix-enums.md#horizontalalign) | No | Yes | Horizontal alignment mode of all child components.<br>Default value: **HorizontalAlign.Center**<br>Invalid values are treated as the default value.|
| justifyContent | [FlexAlign](./arkui-ts/ts-appendix-enums.md#flexalign) | No | Yes | Vertical alignment mode of all child components.<br>Default value: **FlexAlign.Start**<br>Invalid values are treated as the default value.|
| isReverse | boolean | No | Yes | Whether to reverse the vertical arrangement of child components. **true** indicates to reverse the vertical arrangement of child components. The vertical direction is not affected by the common attribute **direction**. **false** indicates to arrange child components in the vertical direction in normal order.<br>Default value: **false**<br>Invalid values are treated as the default value.|

## StackLayoutAlgorithm

A stack layout algorithm class, which is used to implement stacked arrangement of child components. It is suitable for scenarios where child components need to be displayed in a stacking manner, such as stacked layers, floating buttons, content areas with backgrounds, and card stack effects. It supports setting the alignment mode of child components within the stack container, which provides layout capabilities similar to the **Stack** component.

**Decorator**: [\@ObservedV2](../../ui/state-management/arkts-new-observedV2-and-trace.md)

> **NOTE**
>
> The object of the **StackLayoutAlgorithm** class can be used as the input parameter of the [DynamicLayout](./arkui-ts/ts-container-dynamiclayout.md) component to specify a layout algorithm.

### Attributes

**Model restriction**: This API can be used only in the stage model.

**Widget capability**: This API can be used in ArkTS widgets since API version 24.

**Atomic service API**: This API can be used in atomic services since API version 24.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name| Type| Read-Only| Optional| Description|
| ---- | ---- | ---- | ---- | ---- |
| alignContent | [LocalizedAlignment](./arkui-ts/ts-appendix-enums.md#localizedalignment20) | No | Yes | Alignment mode of child components in the stack layout algorithm.<br> Default value: **LocalizedAlignment.CENTER** <br> Invalid values are treated as the default value.<br>Decorator: [@Trace](../../ui/state-management/arkts-new-observedV2-and-trace.md) |

### constructor

constructor(option?: StackLayoutAlgorithmOptions)

Constructs the stack layout algorithm class.

**Model restriction**: This API can be used only in the stage model.

**Widget capability**: This API can be used in ArkTS widgets since API version 24.

**Atomic service API**: This API can be used in atomic services since API version 24.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type| Mandatory| Description|
| ---- | ---- | ---- | ---- |
| option | [StackLayoutAlgorithmOptions](#stacklayoutalgorithmoptions) | No | Input parameters for constructing the stack layout algorithm, which are used to set the nine-box grid alignment mode. If not passed, the default value of each attribute is used. |

**Example**

For details, see [Example 2: Switching the Layout Algorithm](./arkui-ts/ts-container-dynamiclayout.md#example-2-switching-the-layout-algorithm).

## StackLayoutAlgorithmOptions

Sets the alignment method of the stack layout algorithm.

**Model restriction**: This API can be used only in the stage model.

**Widget capability**: This API can be used in ArkTS widgets since API version 24.

**Atomic service API**: This API can be used in atomic services since API version 24.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name| Type| Read-Only| Optional| Description|
| ---- | ---- | ---- | ---- | ---- |
| alignContent | [LocalizedAlignment](./arkui-ts/ts-appendix-enums.md#localizedalignment20) | No | Yes | Alignment mode of child components in the stack layout algorithm.<br> Default value: **LocalizedAlignment.CENTER**<br> Invalid values are treated as the default value. |

## GridLayoutAlgorithm

A grid layout algorithm class, which is used to implement grid arrangement of child components. It is suitable for scenarios where child components need to be arranged in a grid format, such as grid menus, photo grids, app lists, and product displays. It supports setting the column count template, column spacing, and row spacing, which provides layout capabilities similar to the **Grid** component.

**Decorator**: [\@ObservedV2](../../ui/state-management/arkts-new-observedV2-and-trace.md)

> **NOTE**
>
> The object of the **GridLayoutAlgorithm** class can be used as the input parameter of the [DynamicLayout](./arkui-ts/ts-container-dynamiclayout.md) component to specify a layout algorithm.

### Attributes

**Model restriction**: This API can be used only in the stage model.

**Atomic service API**: This API can be used in atomic services since API version 24.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name| Type| Read-Only| Optional| Description|
| ---- | ---- | ---- | ---- | ---- |
| columnsTemplate | string \| [ItemFillPolicy](./arkui-ts/ts-types.md#itemfillpolicy22) | No | Yes | Column template of the current grid layout, defining the width and number of columns. The string type must conform to the template format, for example, **'1fr'** indicates a single-column layout, **'1fr 1fr 1fr'** indicates a three-column equal-width layout, and **'1fr 2fr'** indicates a two-column layout where the second column is twice as wide as the first. When **ItemFillPolicy** is used, adaptive column count can be implemented.<br> Default value: **'1fr'**<br> Invalid values are treated as the default value.<br>**Decorator:** [@Trace](../../ui/state-management/arkts-new-observedV2-and-trace.md) |
| columnsGap | [LengthMetrics](js-apis-arkui-graphics.md#lengthmetrics12) | No | Yes | Spacing between columns. Value range: a non-negative number.<br> Default value: **LengthMetrics.vp(0)**<br> Invalid values are treated as the default value.<br>**Decorator:** [@Trace](../../ui/state-management/arkts-new-observedV2-and-trace.md) |
| rowsGap | [LengthMetrics](js-apis-arkui-graphics.md#lengthmetrics12) | No | Yes | Spacing between rows. Value range: a non-negative number.<br> Default value: **LengthMetrics.vp(0)**<br> Invalid values are treated as the default value.<br>**Decorator:** [@Trace](../../ui/state-management/arkts-new-observedV2-and-trace.md) |

### constructor

constructor(option?: GridLayoutAlgorithmOptions)

Constructs the grid layout algorithm class.

**Model restriction**: This API can be used only in the stage model.

**Atomic service API**: This API can be used in atomic services since API version 24.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type| Mandatory| Description|
| ---- | ---- | ---- | ---- |
| option | [GridLayoutAlgorithmOptions](#gridlayoutalgorithmoptions) | No | Input parameters for constructing the grid layout algorithm, which are used to set the number of columns, column spacing, and row spacing of the grid layout. If not passed, the default value of each attribute is used.|

**Example**

For details, see [Example 2: Switching the Layout Algorithm](./arkui-ts/ts-container-dynamiclayout.md#example-2-switching-the-layout-algorithm).

## GridLayoutAlgorithmOptions

Sets the column count template, column spacing, and row spacing of the grid layout algorithm.

**Model restriction**: This API can be used only in the stage model.

**Atomic service API**: This API can be used in atomic services since API version 24.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name| Type| Read-Only| Optional| Description|
| ---- | ---- | ---- | ---- | ---- |
| columnsTemplate | string \| [ItemFillPolicy](./arkui-ts/ts-types.md#itemfillpolicy22) | No | Yes | Column template of the current grid layout, defining the width and number of columns. The string type must conform to the template format, for example, **'1fr'** indicates a single-column layout, **'1fr 1fr 1fr'** indicates a three-column equal-width layout, and **'1fr 2fr'** indicates a two-column layout where the second column is twice as wide as the first. When **ItemFillPolicy** is used, adaptive column count can be achieved.<br> Default value: **'1fr'** <br> Invalid values are treated as the default value.|
| columnsGap | [LengthMetrics](js-apis-arkui-graphics.md#lengthmetrics12) | No | Yes | Spacing between columns. Value range: a non-negative number.<br> Default value: **LengthMetrics.vp(0)** <br> Invalid values are treated as the default value.|
| rowsGap | [LengthMetrics](js-apis-arkui-graphics.md#lengthmetrics12) | No | Yes | Spacing between rows. Value range: a non-negative number.<br> Default value: **LengthMetrics.vp(0)** <br> Invalid values are treated as the default value.|