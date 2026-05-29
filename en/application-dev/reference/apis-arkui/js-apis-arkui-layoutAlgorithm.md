# LayoutAlgorithm
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @zju_ljz-->
<!--Designer: @lanshouren-->
<!--Tester: @liuli0427-->
<!--Adviser: @Brilliantry_Rui-->

Provides layout algorithms supported by the [DynamicLayout](./arkui-ts/ts-container-dynamiclayout.md) component.

> **NOTE**
>
> The initial APIs of this module are supported since API version 24. Newly added APIs will be marked with a superscript to indicate their earliest API version.

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

Custom layout algorithm class.

> **NOTE**
>
> The object of the **CustomLayoutAlgorithm** class can be assigned to a variable of the **LayoutAlgorithm** type as the input parameter of the [DynamicLayout](./arkui-ts/ts-container-dynamiclayout.md) component to specify the layout algorithm.

**Decorator**: \@ObservedV2

### onMeasure
onMeasure(self: FrameNode, constraint: LayoutConstraint): void

Customizes the size of the child component to be measured. When the size of the dynamic layout component is determined, the ArkUI framework will transfer the FrameNode and layout constraint of the component to you through **onMeasure**. State variables should not be changed in this callback.

> **NOTE**
>
> In this callback, you can call [getChild()](js-apis-arkui-frameNode.md#getchild12) of [FrameNode](js-apis-arkui-frameNode.md#framenode-1) to obtain the child component **FrameNode** and call [measure()](js-apis-arkui-frameNode.md#measure12) of [FrameNode](js-apis-arkui-frameNode.md#framenode-1) to measure the size of the child component. For details, see [Example 1: Implementing Waterfall Layout Using a Custom Layout Algorithm](./arkui-ts/ts-container-dynamiclayout.md#example-1-implementing-waterfall-layout-using-a-custom-layout-algorithm).

**Decorator**: \@ObservedV2

**Model restriction**: This API can be used only in the stage model.

**Widget capability**: This API can be used in ArkTS widgets since API version 24.

**Atomic service API**: This API can be used in atomic services since API version 24.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type| Mandatory| Description|
| ---- | ---- | ---- | ---- |
| self | [FrameNode](js-apis-arkui-frameNode.md#framenode-1) | Yes| Entity node of the dynamic layout component in the component tree.|
| constraint | [LayoutConstraint](js-apis-arkui-frameNode.md#layoutconstraint12) | Yes| Layout constraint used by the dynamic layout component for measurement.|

### onLayout
onLayout(self: FrameNode, position: Position): void

Customizes the position of the child component to be arranged. When the position of the dynamic layout component is determined, the ArkUI framework will transfer the FrameNode and layout position of the component to you through **onLayout**. State variables should not be changed in this callback.

> **NOTE**
>
> In this callback, you can call [getChild()](js-apis-arkui-frameNode.md#getchild12) of [FrameNode](js-apis-arkui-frameNode.md#framenode-1) to obtain the child component **FrameNode** and call [layout()](js-apis-arkui-frameNode.md#layout12) of [FrameNode](js-apis-arkui-frameNode.md#framenode-1) to set the position of the child component. For details, see [Example 1: Implementing Waterfall Layout Using a Custom Layout Algorithm](./arkui-ts/ts-container-dynamiclayout.md#example-1-implementing-waterfall-layout-using-a-custom-layout-algorithm).

**Decorator**: \@ObservedV2

**Model restriction**: This API can be used only in the stage model.
  
**Widget capability**: This API can be used in ArkTS widgets since API version 24.

**Atomic service API**: This API can be used in atomic services since API version 24.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type| Mandatory| Description|
| ---- | ---- | ---- | ---- |
| self | [FrameNode](js-apis-arkui-frameNode.md#framenode-1) | Yes| Entity node of the dynamic layout component in the component tree.|
| position | [Position](js-apis-arkui-graphics.md#position) | Yes| Position information used in layout of the dynamic layout component.|

**Example**

For details, see [Example 1: Implementing Waterfall Layout Using a Custom Layout Algorithm](./arkui-ts/ts-container-dynamiclayout.md#example-1-implementing-waterfall-layout-using-a-custom-layout-algorithm).

## RowLayoutAlgorithm

Horizontal linear layout algorithm class.

> **NOTE**
>
> The object of the **RowLayoutAlgorithm** class can be assigned to a variable of the **LayoutAlgorithm** type as the input parameter of the [DynamicLayout](./arkui-ts/ts-container-dynamiclayout.md) component to specify the layout algorithm.

**Decorator**: \@ObservedV2

### Attributes

**Decorator**: \@ObservedV2

**Model restriction**: This API can be used only in the stage model.

**Widget capability**: This API can be used in ArkTS widgets since API version 24.

**Atomic service API**: This API can be used in atomic services since API version 24.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name| Type| Read-Only| Optional| Description|
| ---- | ---- | ---- | ---- | ---- |
| space | [LengthMetrics](js-apis-arkui-graphics.md#lengthmetrics12) | No| Yes| Horizontal spacing between elements in a horizontal layout.<br> Default value: **LengthMetrics.vp(0)**<br> Invalid values are treated as the default value.<br>Decorator: @Trace|
| alignItems | [VerticalAlign](./arkui-ts/ts-appendix-enums.md#verticalalign) | No| Yes| Vertical alignment mode of all child components.<br> Default value: **VerticalAlign.Center**<br> Invalid values are treated as the default value.<br>Decorator: @Trace|
| justifyContent | [FlexAlign](./arkui-ts/ts-appendix-enums.md#flexalign) | No| Yes| Horizontal alignment mode of all child components.<br> Default value: **FlexAlign.Start**<br> Invalid values are treated as the default value.<br>Decorator: @Trace|
| isReverse | boolean | No| Yes| Whether to reverse the horizontal arrangement of child components. **true** indicates to reverse the horizontal arrangement of child components. The horizontal direction is affected by the common attribute [direction](./arkui-ts/ts-universal-attributes-location.md#direction). If the [direction](./arkui-ts/ts-universal-attributes-location.md#direction) attribute takes effect, the arrangement is reversed again. **false** indicates to arrange child components in the horizontal direction in normal order.<br>Default value: **false**<br> Invalid values are treated as the default value.<br>Decorator: @Trace|

### constructor

constructor(option?: RowLayoutAlgorithmOptions)

Constructs the horizontal linear layout algorithm class.

**Decorator**: \@ObservedV2

**Model restriction**: This API can be used only in the stage model.

**Widget capability**: This API can be used in ArkTS widgets since API version 24.

**Atomic service API**: This API can be used in atomic services since API version 24.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type| Mandatory| Description|
| ---- | ---- | ---- | ---- |
| option | [RowLayoutAlgorithmOptions](#rowlayoutalgorithmoptions)| No| Input parameters for constructing the horizontal linear layout algorithm, which are used to set the spacing, main axis alignment method, cross axis alignment method, and main axis arrangement direction of the layout algorithm.|

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
| space | [LengthMetrics](js-apis-arkui-graphics.md#lengthmetrics12) | No| Yes| Horizontal spacing between elements in a horizontal layout.<br> Default value: **LengthMetrics.vp(0)**<br> Invalid values are treated as the default value.|
| alignItems | [VerticalAlign](./arkui-ts/ts-appendix-enums.md#verticalalign) | No| Yes| Vertical alignment mode of all child components.<br> Default value: **VerticalAlign.Center**<br> Invalid values are treated as the default value.|
| justifyContent | [FlexAlign](./arkui-ts/ts-appendix-enums.md#flexalign) | No| Yes| Horizontal alignment mode of all child components.<br> Default value: **FlexAlign.Start**<br> Invalid values are treated as the default value.|
| isReverse | boolean | No| Yes| Whether to reverse the horizontal arrangement of child components. **true** indicates to reverse the horizontal arrangement of child components. The horizontal direction is affected by the common attribute [direction](./arkui-ts/ts-universal-attributes-location.md#direction). If the [direction](./arkui-ts/ts-universal-attributes-location.md#direction) attribute takes effect, the arrangement is reversed again. **false** indicates to arrange child components in the horizontal direction in normal order.<br>Default value: **false**<br> Invalid values are treated as the default value.|

## ColumnLayoutAlgorithm

Vertical linear layout algorithm class.

> **NOTE**
>
> The object of the **ColumnLayoutAlgorithm** class can be assigned to a variable of the **LayoutAlgorithm** type as the input parameter of the [DynamicLayout](./arkui-ts/ts-container-dynamiclayout.md) component to specify the layout algorithm.

**Decorator**: \@ObservedV2

### Attributes

**Decorator**: \@ObservedV2

**Model restriction**: This API can be used only in the stage model.

**Widget capability**: This API can be used in ArkTS widgets since API version 24.

**Atomic service API**: This API can be used in atomic services since API version 24.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name| Type| Read-Only| Optional| Description|
| ---- | ---- | ---- | ---- | ---- |
| space | [LengthMetrics](js-apis-arkui-graphics.md#lengthmetrics12) | No| Yes| Vertical spacing between elements in a vertical layout.<br> Default value: **LengthMetrics.vp(0)**<br> Invalid values are treated as the default value.<br>Decorator: @Trace|
| alignItems | [HorizontalAlign](./arkui-ts/ts-appendix-enums.md#horizontalalign) | No| Yes| Horizontal alignment mode of all child components.<br> Default value: **HorizontalAlign.Center**<br>  Invalid values are treated as the default value.<br>Decorator: @Trace|
| justifyContent | [FlexAlign](./arkui-ts/ts-appendix-enums.md#flexalign) | No| Yes| Vertical alignment mode of all child components.<br> Default value: **FlexAlign.Start**<br> Invalid values are treated as the default value.<br>Decorator: @Trace|
| isReverse | boolean | No| Yes| Whether to reverse the vertical arrangement of child components. **true** indicates to reverse the vertical arrangement of child components. **false** indicates to arrange child components in the vertical direction in normal order.<br>Default value: **false**<br> Invalid values are treated as the default value.<br>Decorator: @Trace|

### constructor 

constructor(option?: ColumnLayoutAlgorithmOptions)

Constructs the vertical linear layout algorithm class.

**Decorator**: \@ObservedV2

**Model restriction**: This API can be used only in the stage model.

**Widget capability**: This API can be used in ArkTS widgets since API version 24.

**Atomic service API**: This API can be used in atomic services since API version 24.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type| Mandatory| Description|
| ---- | ---- | ---- | ---- |
| option | [ColumnLayoutAlgorithmOptions](#columnlayoutalgorithmoptions)| No| Input parameters for constructing the vertical linear layout algorithm, which are used to set the spacing, main axis alignment method, cross axis alignment method, and main axis arrangement direction of the layout algorithm.|

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
| space | [LengthMetrics](js-apis-arkui-graphics.md#lengthmetrics12) | No| Yes| Vertical spacing between elements in a vertical layout.<br> Default value: **LengthMetrics.vp(0)**<br> Invalid values are treated as the default value.|
| alignItems | [HorizontalAlign](./arkui-ts/ts-appendix-enums.md#horizontalalign) | No| Yes| Horizontal alignment mode of all child components.<br> Default value: **HorizontalAlign.Center**<br>  Invalid values are treated as the default value.|
| justifyContent | [FlexAlign](./arkui-ts/ts-appendix-enums.md#flexalign) | No| Yes| Vertical alignment mode of all child components.<br> Default value: **FlexAlign.Start**<br> Invalid values are treated as the default value.|
| isReverse | boolean | No| Yes| Whether to reverse the vertical arrangement of child components. **true** indicates to reverse the vertical arrangement of child components. **false** indicates to arrange child components in the vertical direction in normal order.<br>Default value: **false**<br> Invalid values are treated as the default value.|

## StackLayoutAlgorithm

Stack layout algorithm class.

> **NOTE**
>
> The object of the **StackLayoutAlgorithm** class can be assigned to a variable of the **LayoutAlgorithm** type as the input parameter of the [DynamicLayout](./arkui-ts/ts-container-dynamiclayout.md) component to specify the layout algorithm.


**Decorator**: \@ObservedV2

### Attributes

**Decorator**: \@ObservedV2

**Model restriction**: This API can be used only in the stage model.

**Widget capability**: This API can be used in ArkTS widgets since API version 24.

**Atomic service API**: This API can be used in atomic services since API version 24.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name| Type| Read-Only| Optional| Description|
| ---- | ---- | ---- | ---- | ---- |
| alignContent | [LocalizedAlignment](./arkui-ts/ts-appendix-enums.md#localizedalignment20) | No| Yes| Alignment mode of child components in the stack layout algorithm.<br> Default value: **LocalizedAlignment.CENTER**.<br> Invalid values are treated as the default value.<br>Decorator: @Trace|

### constructor

constructor(option?: StackLayoutAlgorithmOptions)

Constructs the stack layout algorithm class.

**Decorator**: \@ObservedV2

**Model restriction**: This API can be used only in the stage model.

**Widget capability**: This API can be used in ArkTS widgets since API version 24.

**Atomic service API**: This API can be used in atomic services since API version 24.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type| Mandatory| Description|
| ---- | ---- | ---- | ---- |
| option | [StackLayoutAlgorithmOptions](#stacklayoutalgorithmoptions)| No| Input parameters for constructing the stack layout algorithm, which are used to set the nine-box grid alignment mode.|

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
| alignContent | [LocalizedAlignment](./arkui-ts/ts-appendix-enums.md#localizedalignment20) | No| Yes| Alignment mode of child components in the stack layout algorithm.<br> Default value: **LocalizedAlignment.CENTER**.<br> Invalid values are treated as the default value.|

## GridLayoutAlgorithm

Grid layout algorithm class.

> **NOTE**
>
> The object of the **GridLayoutAlgorithm** class can be assigned to a variable of the **LayoutAlgorithm** type as the input parameter of the [DynamicLayout](./arkui-ts/ts-container-dynamiclayout.md) component to specify the layout algorithm.

**Decorator**: \@ObservedV2

### Attributes

**Decorator**: \@ObservedV2

**Model restriction**: This API can be used only in the stage model.

**Atomic service API**: This API can be used in atomic services since API version 24.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name| Type| Read-Only| Optional| Description|
| ---- | ---- | ---- | ---- | ---- |
| columnsTemplate | string \| [ItemFillPolicy](./arkui-ts/ts-types.md#itemfillpolicy22) | No| Yes| Number of columns in the grid layout.<br> Default value: **'1fr'**<br> Invalid values are treated as the default value.<br>Decorator: @Trace|
| columnsGap | [LengthMetrics](js-apis-arkui-graphics.md#lengthmetrics12) | No| Yes| Spacing between columns.<br> Default value: **LengthMetrics.vp(0)**<br> Invalid values are treated as the default value.<br>Decorator: @Trace|
| rowsGap | [LengthMetrics](js-apis-arkui-graphics.md#lengthmetrics12) | No| Yes| Spacing between rows.<br> Default value: **LengthMetrics.vp(0)**<br> Invalid values are treated as the default value.<br>Decorator: @Trace|

### constructor

constructor(option?: GridLayoutAlgorithmOptions)

Constructs the grid layout algorithm class.

**Decorator**: \@ObservedV2

**Model restriction**: This API can be used only in the stage model.

**Atomic service API**: This API can be used in atomic services since API version 24.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type| Mandatory| Description|
| ---- | ---- | ---- | ---- |
| option | [GridLayoutAlgorithmOptions](#gridlayoutalgorithmoptions)| No| Input parameters for constructing the grid layout algorithm, which are used to set the number of columns, column spacing, and row spacing of the grid layout.|

**Example**

For details, see [Example 2: Switching the Layout Algorithm](./arkui-ts/ts-container-dynamiclayout.md#example-2-switching-the-layout-algorithm).

## GridLayoutAlgorithmOptions

Sets the number of columns, column spacing, and row spacing of the grid layout algorithm.

**Model restriction**: This API can be used only in the stage model.

**Atomic service API**: This API can be used in atomic services since API version 24.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name| Type| Read-Only| Optional| Description|
| ---- | ---- | ---- | ---- | ---- |
| columnsTemplate | string \| [ItemFillPolicy](./arkui-ts/ts-types.md#itemfillpolicy22) | No| Yes| Number of columns in the grid layout.<br> Default value: **'1fr'**<br> Invalid values are treated as the default value.|
| columnsGap | [LengthMetrics](js-apis-arkui-graphics.md#lengthmetrics12) | No| Yes| Spacing between columns.<br> Default value: **LengthMetrics.vp(0)**<br> Invalid values are treated as the default value.|
| rowsGap | [LengthMetrics](js-apis-arkui-graphics.md#lengthmetrics12) | No| Yes| Spacing between rows.<br> Default value: **LengthMetrics.vp(0)**<br> Invalid values are treated as the default value.|
