# Basic Types

>**NOTE**
>
>The initial APIs of this module are supported since API version 7. Newly added APIs will be marked with a superscript to indicate their earliest API version.

## Resource

The **Resource** type is used to reference resources for setting component attributes. Resource files must be stored and managed in specific subdirectories. For examples of resource directories, see [Resource Categories](../../../quick-start/resource-categories-and-access.md#resource-categories).

**Widget capability**: This API can be used in ArkTS widgets since API version 9.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

You can use `$r` or `$rawfile` to create a **Resource** object, but its attribute values cannot be changed.

- `$r('belonging.type.name')`

  **belonging**: group to which the resource belongs, which can be **'sys'** or **'app'**.

  **type**: resource type, which can be '**boolean'**, **'color'**, **'float'**, **'intarray'**, **'integer'**, **'pattern'**, '**plural'**, **'strarray'**, **'string'**, or **'media'**.

  **name**: resource name, which is determined during resource definition.

- `$rawfile('filename')`

  **filename**: name of the file in the **resources/rawfile** directory of the project.

  **NOTE**<br>When referencing resources of the **Resource** type, make sure the data type is the same as that of the attribute method. For example, if an attribute method supports the **string | Resource** types, the data type of the **Resource** type must be string.

## Length

The **Length** type is used to represent a size unit.

**Widget capability**: This API can be used in ArkTS widgets since API version 9.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Type                   | Description                                    |
| --------------------- | -------------------------------------- |
| string                | String type. Specify the length [unit](ts-pixel-units.md) explicitly, for example, **'10px'**, or provide the length in percentage, for example, **'100%'**.<br>**NOTE**<br>If the unit is not specified, the default unit vp is used, in which case '10' is equivalent to 10 vp.|
| number                | Number type. The default unit is vp.                               |
| [Resource](#resource) | Size referenced from system or application resources.              |

## ResourceStr

The **ResourceStr** type is used to represent the types that can be used by input parameters of the string type.

**Widget capability**: This API can be used in ArkTS widgets since API version 9.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Type                   | Description                       |
| --------------------- | ------------------------- |
| string                | String type.                   |
| [Resource](#resource) | String referenced from system or application resources.|

## Padding

The **Padding** type is used to describe the paddings in different directions of a component.

**Widget capability**: This API can be used in ArkTS widgets since API version 9.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name    | Type               | Mandatory  | Description                  |
| ------ | ----------------- | ---- | -------------------- |
| top    | [Length](#length) | No   | Height of the padding on the top of the component. |
| right  | [Length](#length) | No   | Width of the padding on the right of the component.|
| bottom | [Length](#length) | No   | Height of the padding at the bottom of the component. |
| left   | [Length](#length) | No   | Width of the padding on the left of the component.|

## LocalizedPadding<sup>12+</sup>

The **Padding** type is used to describe the paddings in different directions of a component.

**Widget capability**: This API can be used in ArkTS widgets since API version 12.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name    | Type               | Mandatory  | Description                  |
| ------ | ----------------- | ---- | -------------------- |
| top    | [LengthMetrics](../js-apis-arkui-graphics.md#lengthmetrics12)<sup>12+</sup> | No   | Height of the padding on the top of the component. |
| end    | [LengthMetrics](../js-apis-arkui-graphics.md#lengthmetrics12)<sup>12+</sup> | No   | Width of the padding on the right of the component. <br>Width of the padding on the left of the component in RTL mode. |
| bottom | [LengthMetrics](../js-apis-arkui-graphics.md#lengthmetrics12)<sup>12+</sup> | No   | Height of the padding at the bottom of the component. |
| start  | [LengthMetrics](../js-apis-arkui-graphics.md#lengthmetrics12)<sup>12+</sup> | No   | Width of the padding on the left of the component.<br> Width of the padding on the right of the component in RTL mode. |

## Margin

The **Margin** type is used to describe the margins in different directions of a component.

**Widget capability**: This API can be used in ArkTS widgets since API version 9.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name    | Type               | Mandatory  | Description                  |
| ------ | ----------------- | ---- | -------------------- |
| top    | [Length](#length) | No   | Height of the margin above the component. |
| right  | [Length](#length) | No   | Width of the margin on the right of the component.|
| bottom | [Length](#length) | No   | Height of the margin below the component. |
| left   | [Length](#length) | No   | Width of the margin on the left of the component.|

## LocalizedMargin<sup>12+</sup>

The **Margin** type is used to describe the margins in different directions of a component.

**Widget capability**: This API can be used in ArkTS widgets since API version 12.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name    | Type               | Mandatory  | Description                  |
| ------ | ----------------- | ---- | -------------------- |
| top    | [LengthMetrics](../js-apis-arkui-graphics.md#lengthmetrics12)<sup>12+</sup> | No   | Height of the margin above the component. |
| end    | [LengthMetrics](../js-apis-arkui-graphics.md#lengthmetrics12)<sup>12+</sup> | No   | Width of the margin on the right of the component.<br>Width of the margin on the left of the component in RTL mode.|
| bottom | [LengthMetrics](../js-apis-arkui-graphics.md#lengthmetrics12)<sup>12+</sup> | No   | Height of the margin below the component. |
| start  | [LengthMetrics](../js-apis-arkui-graphics.md#lengthmetrics12)<sup>12+</sup> | No   | Width of the margin on the left of the component.<br>Width of the margin on the right of the component in RTL mode.|

## EdgeWidths<sup>9+</sup>

The **EdgeWidths** type is used to describe the edge widths in different directions of a component.

**Widget capability**: This API can be used in ArkTS widgets since API version 9.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name    | Type               | Mandatory  | Description      |
| ------ | ----------------- | ---- | -------- |
| top    | [Length](#length) | No   | Width of the top edge of the component.|
| right  | [Length](#length) | No   | Width of the right edge of the component.|
| bottom | [Length](#length) | No   | Width of the bottom edge of the component.|
| left   | [Length](#length) | No   | Width of the left edge of the component.|

## LocalizedEdgeWidths<sup>12+</sup>

The **EdgeWidths** type is used to describe the edge widths in different directions of a component.

**Widget capability**: This API can be used in ArkTS widgets since API version 12.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name    | Type               | Mandatory  | Description      |
| ------ | ----------------- | ---- | -------- |
| top    | [LengthMetrics](../js-apis-arkui-graphics.md#lengthmetrics12)<sup>12+</sup> | No   | Width of the top edge of the component.|
| end    | [LengthMetrics](../js-apis-arkui-graphics.md#lengthmetrics12)<sup>12+</sup> | No   | Width of the right edge of the component.<br>Width of the left edge of the component in RTL mode.|
| bottom | [LengthMetrics](../js-apis-arkui-graphics.md#lengthmetrics12)<sup>12+</sup> | No   | Width of the bottom edge of the component.|
| start  | [LengthMetrics](../js-apis-arkui-graphics.md#lengthmetrics12)<sup>12+</sup> | No   | Width of the left edge of the component.<br>Width of the right edge of the component in RTL mode.|

## BorderRadiuses<sup>9+</sup>

The **BorderRadiuses** type is used to describe the corner radius of a component's border.

**Widget capability**: This API can be used in ArkTS widgets since API version 9.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name         | Type               | Mandatory  | Description        |
| ----------- | ----------------- | ---- | ---------- |
| topLeft     | [Length](#length) | No   | Radius of the upper left corner of the component.|
| topRight    | [Length](#length) | No   | Radius of the upper right corner of the component.|
| bottomLeft  | [Length](#length) | No   | Radius of the lower left corner of the component.|
| bottomRight | [Length](#length) | No   | Radius of the lower right corner of the component.|

## LocalizedBorderRadiuses<sup>12+</sup>

The **LocalizedBorderRadiuses** type is used to describe the corner radius of a component's border.

**Widget capability**: This API can be used in ArkTS widgets since API version 12.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name         | Type               | Mandatory  | Description        |
| ----------- | ----------------- | ---- | ---------- |
| topStart    | [LengthMetrics](../js-apis-arkui-graphics.md#lengthmetrics12)<sup>12+</sup> | No   | Radius of the upper left corner of the component.<br>Radius of the upper left right of the component in RTL mode.|
| topEnd      | [LengthMetrics](../js-apis-arkui-graphics.md#lengthmetrics12)<sup>12+</sup> | No   | Radius of the upper right corner of the component.<br>Radius of the upper left corner of the component in RTL mode.|
| bottomStart | [LengthMetrics](../js-apis-arkui-graphics.md#lengthmetrics12)<sup>12+</sup> | No   | Radius of the lower left corner of the component.<br>Radius of the lower right corner of the component in RTL mode.|
| bottomEnd   | [LengthMetrics](../js-apis-arkui-graphics.md#lengthmetrics12)<sup>12+</sup> | No   | Radius of the lower right corner of the component.<br>Radius of the lower left corner of the component in RTL mode.|

## EdgeColors<sup>9+</sup>

The **EdgeColors** type is used to describe the edge colors of a component.

**Widget capability**: This API can be used in ArkTS widgets since API version 9.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name    | Type                             | Mandatory  | Description      |
| ------ | ------------------------------- | ---- | -------- |
| top    | [ResourceColor](#resourcecolor) | No   | Color of the top edge of the component.|
| right  | [ResourceColor](#resourcecolor) | No   | Color of the right edge of the component.|
| bottom | [ResourceColor](#resourcecolor) | No   | Color of the bottom edge of the component.|
| left   | [ResourceColor](#resourcecolor) | No   | Color of the left edge of the component.|

## LocalizedEdgeColors<sup>12+</sup>

The **EdgeColors** type is used to describe the edge colors of a component.

**Widget capability**: This API can be used in ArkTS widgets since API version 12.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name    | Type                             | Mandatory  | Description      |
| ------ | ------------------------------- | ---- | -------- |
| top    | [ResourceColor](#resourcecolor) | No   | Color of the top edge of the component.|
| end    | [ResourceColor](#resourcecolor) | No   | Color of the right edge of the component.<br>Color of the left edge of the component in RTL mode.|
| bottom | [ResourceColor](#resourcecolor) | No   | Color of the bottom edge of the component.|
| start  | [ResourceColor](#resourcecolor) | No   | Color of the left edge of the component.<br>Color of the right edge of the component in RTL mode.|

## EdgeStyles<sup>9+</sup>

The **EdgeStyles** type is used to describe the edge styles of a component.

**Widget capability**: This API can be used in ArkTS widgets since API version 9.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name    | Type                                      | Mandatory  | Description      |
| ------ | ---------------------------------------- | ---- | -------- |
| top    | [BorderStyle](ts-appendix-enums.md#borderstyle) | No   | Style of the top edge of the component.|
| right  | [BorderStyle](ts-appendix-enums.md#borderstyle) | No   | Style of the right edge of the component.|
| bottom | [BorderStyle](ts-appendix-enums.md#borderstyle) | No   | Style of the bottom edge of the component.|
| left   | [BorderStyle](ts-appendix-enums.md#borderstyle) | No   | Style of the left edge of the component.|

## Offset

The **Offset** type is used to describe the offset coordinates of a component in the layout.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name  | Type               | Mandatory  | Description      |
| ---- | ----------------- | ---- | -------- |
| dx   | [Length](#length) | Yes   | X coordinate of the offset.|
| dy   | [Length](#length) | Yes   | Y coordinate of the offset.|

## RectResult<sup>10+</sup>

The **RectResult** type is used to describe the position, width, and height of a component.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name     | Type    | Description|
| ------- | ------ | ----------------------- |
| x     | number | Horizontal coordinate.|
| y     | number | Vertical coordinate.|
| width | number | Content width.|
| height | number | Content height.|

## ResourceColor

The **ResourceColor** type is used to describe the color types of resources.

**Widget capability**: This API can be used in ArkTS widgets since API version 9.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Type                               | Description                                                        |
| ----------------------------------- | ------------------------------------------------------------ |
| [Color](ts-appendix-enums.md#color) | Color enums.                                                |
| number                              | Color in hexadecimal notation. RGB and ARGB are supported. Examples: **0xffffff** and **0xffff0000**. The number of input digits cannot be identified. The format is selected based on the value. For example, 0x00ffffff is parsed in RGB format.|
| string                              | Color in RGB or ARGB notation. Example: **'#ffffff'**, **'#ff000000'**, **'rgb(255, 100, 255)'**, **'rgba(255, 100, 255, 0.5)'**|
| [Resource](#resource)               | Color referenced from system or application resources.      |

## LengthConstrain

The **LengthConstrain** type is used to describe the maximum and minimum lengths of a component.

**Widget capability**: This API can be used in ArkTS widgets since API version 9.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name       | Type               | Mandatory  | Description     |
| --------- | ----------------- | ---- | ------- |
| minLength | [Length](#length) | Yes   | Minimum length of the component.|
| maxLength | [Length](#length) | Yes   | Maximum length of the component.|


## Font

The **Font** type is used to set the text style.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name  | Type                                                        | Mandatory| Description                                                        |
| ------ | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| size   | [Length](#length)                                            | No  | Font size. If the value is of the number type, the unit fp is used. Percentage strings are not supported.<br>Default value: **16.0**|
| weight | [FontWeight](ts-appendix-enums.md#fontweight) \| number \| string | No  | Font weight. For the number type, the value ranges from 100 to 900, at an interval of 100. A larger value indicates a thicker font.<br>Default value: **400** \| **FontWeight.Normal** |
| family | string \| [Resource](#resource)                              | No  | Font family of the text. Use commas (,) to separate multiple fonts. The priority of the fonts is the sequence in which they are placed. An example value is **'Arial, HarmonyOS Sans'**. The 'HarmonyOS Sans' font and [registered custom fonts](../js-apis-font.md) are supported.|
| style  | [FontStyle](ts-appendix-enums.md#fontstyle)                  | No  | Font style.<br>Default value: **FontStyle.Normal**            |

## Area<sup>8+</sup>

The **Area** type is used to describe the area information of a component.

**Widget capability**: This API can be used in ArkTS widgets since API version 9.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name            | Type                    | Description                            |
| -------------- | ---------------------- | ------------------------------ |
| width          | [Length](#length)      | Width of the component. The value is of the number type in vp when used as the return value.|
| height         | [Length](#length)      | Height of the component. The value is of the number type in vp when used as the return value.|
| position       | [Position](#position) | Position of the upper left corner of the component relative to that of its parent container.           |
| globalPosition | [Position](#position) | Position of the upper left corner of the component relative to that of the page where the component resides.            |

## Position

The **Position** type is used to represent coordinates of a point.

**Widget capability**: This API can be used in ArkTS widgets since API version 9.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name  | Type               | Mandatory  | Description                         |
| ---- | ----------------- | ---- | --------------------------- |
| x    | [Length](#length) | No   | X coordinate. The value is of the number type in vp when used as the return value.|
| y    | [Length](#length) | No   | Y coordinate. The value is of the number type in vp when used as the return value.|

## LocalizedPosition<sup>12+</sup>

The **LocalizedPosition** type is used to represent coordinates of a point.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name  | Type               | Mandatory  | Description                         |
| ---- | ----------------- | ---- | --------------------------- |
| start  | [LengthMetrics](../js-apis-arkui-graphics.md#lengthmetrics12) | No   | X-coordinate relative to the left for left-to-right (LTR) scripts; X-coordinate relative to the right for right-to-left (RTL) scripts. |
| top    | [LengthMetrics](../js-apis-arkui-graphics.md#lengthmetrics12) | No   | Y-coordinate.|

## Edges<sup>12+</sup>

The **Edges** type is used to describe the offset relative to the four edges. If both **top** and **bottom** are set, only **top** takes effect. If both **left** and **right** are set, only **left** takes effect.

**Widget capability**: This API can be used in ArkTS widgets since API version 12.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name  | Type    | Mandatory  | Description                         |
| ---- | ------ | ---- | --------------------------- |
| top    | [Dimension](#dimension10) | No   | Offset relative to the top edge.|
| bottom    | [Dimension](#dimension10) | No   | Offset relative to the bottom edge.|
| left    | [Dimension](#dimension10) | No   | Offset relative to the left edge.|
| right    | [Dimension](#dimension10) | No   | Offset relative to the right edge.|

## LocalizedEdges<sup>12+</sup>

The **LocalizedEdges** type is used to describe the offset relative to the four edges. If both **top** and** bottom **are set, only **top** takes effect. If both **start** and **end** are set, only **start** takes effect.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name  | Type    | Mandatory  | Description                         |
| ---- | ------ | ---- | --------------------------- |
| top    | [LengthMetrics](../js-apis-arkui-graphics.md#lengthmetrics12) | No   | Offset relative to the top edge.|
| bottom    | [LengthMetrics](../js-apis-arkui-graphics.md#lengthmetrics12) | No   | Offset relative to the bottom edge.|
| start    | [LengthMetrics](../js-apis-arkui-graphics.md#lengthmetrics12) | No   | Offset relative to the left in LTR mode; offset relative to the right in RTL mode.|
| end    | [LengthMetrics](../js-apis-arkui-graphics.md#lengthmetrics12) | No   | Offset relative to the right for in LTR mode; offset relative to the left in RTL mode.|

## ConstraintSizeOptions

The **ConstraintSizeOptions** type is used to set the size constraints of a component during component layout.

**Widget capability**: This API can be used in ArkTS widgets since API version 9.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name       | Type               | Mandatory  | Description     |
| --------- | ----------------- | ---- | ------- |
| minWidth  | [Length](#length) | No   | Minimum width of the component.|
| maxWidth  | [Length](#length) | No   | Maximum width of the component.|
| minHeight | [Length](#length) | No   | Minimum height of the component.|
| maxHeight | [Length](#length) | No   | Maximum height of the component.|

## SizeOptions

The **SizeOptions** type is used to set the width and height.

**Widget capability**: This API can be used in ArkTS widgets since API version 9.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name    | Type               | Mandatory  | Description   |
| ------ | ----------------- | ---- | ----- |
| width  | [Length](#length) | No   | Width of the component.|
| height | [Length](#length) | No   | Height of the component.|


## BorderOptions

The **BorderOptions** type is used to provide border information.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name  | Type                                                    | Mandatory| Description              |
| ------ | ------------------------------------------------------------ | ---- | ------------------ |
| width  | [Length](ts-types.md#length) \| [EdgeWidths](ts-universal-attributes-border.md#edgewidths9)<sup>9+</sup> \| [LocalizedEdgeWidths](ts-universal-attributes-border.md#localizededgewidths12)<sup>12+</sup> | No  | Border width.<br>**Atomic service API**: This API can be used in atomic services since API version 11.<br>**Widget capability**: This API can be used in ArkTS widgets since API version 9.    |
| color  | [ResourceColor](ts-types.md#resourcecolor) \| [EdgeColors](ts-universal-attributes-border.md#edgecolors9)<sup>9+</sup> \| [LocalizedEdgeColors](ts-universal-attributes-border.md#localizededgecolors12)<sup>12+</sup> | No  | Border color.<br>**Atomic service API**: This API can be used in atomic services since API version 11.<br>**Widget capability**: This API can be used in ArkTS widgets since API version 9.    |
| radius | [Length](ts-types.md#length) \| [BorderRadiuses](ts-universal-attributes-border.md#borderradiuses9)<sup>9+</sup> \| [LocalizedBorderRadiuses](ts-universal-attributes-border.md#localizedborderradiuses12)<sup>12+</sup> | No  | Border corner radius.<br>**Atomic service API**: This API can be used in atomic services since API version 11.<br>**Widget capability**: This API can be used in ArkTS widgets since API version 9.|
| style  | [BorderStyle](ts-appendix-enums.md#borderstyle) \| [EdgeStyles](ts-universal-attributes-border.md#edgestyles9)<sup>9+</sup> | No  | Border style.<br>**Atomic service API**: This API can be used in atomic services since API version 11.<br>**Widget capability**: This API can be used in ArkTS widgets since API version 9.    |
| dashGap<sup>12+</sup>  | [LengthMetrics](../js-apis-arkui-graphics.md#lengthmetrics12) \| [EdgeWidths](ts-universal-attributes-border.md#edgewidths9) \| [LocalizedEdgeWidths](ts-universal-attributes-border.md#localizededgewidths12) | No | Gap between dashed line segments. It takes effect when the border style is set to dashed.<br>Percentage values are not supported.<br>**Atomic service API**: This API can be used in atomic services since API version 12.<br>**Widget capability**: This API cannot be used in ArkTS widgets.|
| dashWidth<sup>12+</sup>  | [LengthMetrics](../js-apis-arkui-graphics.md#lengthmetrics12) \| [EdgeWidths](ts-universal-attributes-border.md#edgewidths9) \| [LocalizedEdgeWidths](ts-universal-attributes-border.md#localizededgewidths12) | No  | Width of dashed line segments. It takes effect when the border style is set to dashed.<br>Percentage values are not supported.<br>**Atomic service API**: This API can be used in atomic services since API version 12.<br>**Widget capability**: This API cannot be used in ArkTS widgets.    |

## ColorFilter<sup>9+</sup>

The **ColorFilter** type is used to create a color filter with a 4 x 5 matrix.

**Widget capability**: This API can be used in ArkTS widgets since API version 9.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name         | Type      | Mandatory  | Description                                      |
| ----------- | -------- | ---- | ---------------------------------------- |
| constructor | number[] | Yes   | Constructor for creating a color filter with a 4\*5 matrix. The input parameter is [m\*n], which is the matrix value in row m and column n. The matrix is row-first.|


## CustomBuilder<sup>8+</sup>

The **CustomBuilder** type is used to define custom UI descriptions in component attribute methods.

| Name           | Type                  | Description                                      |
| ------------- | ---------------------- | ---------------------------------------- |
| CustomBuilder | () =&gt; any \| void | Builder used to generate a custom UI component when used with the [@Builder](../../../ui/state-management/arkts-builder.md) decorator.|

## MarkStyle<sup>10+</sup>

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name       | Type                                      | Mandatory| Default Value     | Description                                                        |
| ----------- | ------------------------------------------ | ---- | ----------- | ------------------------------------------------------------ |
| strokeColor | [ResourceColor](ts-types.md#resourcecolor) | No  | Color.White | Color of the check mark.                                              |
| size        | [Length](ts-types.md#length)               | No  | -           | Size of the check mark, in vp. The default size is the same as the width of the check box component.<br>Percentage values are not supported. If an invalid value is set, the default value is used.|
| strokeWidth | [Length](ts-types.md#length)               | No  | 2           | Stroke width of the check mark, in vp. Percentage values are not supported. If an invalid value is set, the default value is used.|

## ModalTransition<sup>10+</sup>

The **ModalTransition** type is used to set the transition type for a full-screen modal.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name     | Description          |
| ------- | ------------ |
| NONE    | No transition animation for the modal.  |
| DEFAULT | Slide-up and slide-down animation for the modal. |
| ALPHA   | Opacity gradient animation for the modal.|

## Dimension<sup>10+</sup>

The **Dimension** type is used to represent a size unit.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Type                   | Description                                    |
| --------------------- | -------------------------------------- |
| [PX](#px10)               | Physical pixel unit type. The unit px must be included, for example, **'10px'**.|
| [VP](#vp10)                | Pixel unit type specific to the screen density. The unit vp can be included or omitted, for example, **10** or **'10vp'**.|
| [FP](#fp10)                | Font pixel unit type. The unit fp must be included, for example, **'10fp'**.|
| [LPX](#lpx10)              | Logical pixel unit type. The unit lpx must be included, for example, **'10lpx'**.|
| [Percentage](#percentage10)        | Percentage type. The unit % must be included, for example, **'10%'**.|
| [Resource](#resource) | Size referenced from system or application resources.|

## PX<sup>10+</sup>

The **PX** type is used to represent a length in px.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Type                   | Description                                    |
| --------------------- | -------------------------------------- |
| {number}px               | Physical pixel unit type. The unit px must be included, for example, **'10px'**.|

## VP<sup>10+</sup>

The **VP** type is used to represent a length in vp.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Type                   | Description                                    |
| --------------------- | -------------------------------------- |
| {number}vp\|number | Pixel unit type specific to the screen density. The unit vp can be included or omitted, for example, **10** or **'10vp'**.|

## FP<sup>10+</sup>

The **FP** type is used to represent a length in fp.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Type                   | Description                                    |
| --------------------- | -------------------------------------- |
| {number}fp               | Font pixel unit type. The unit fp must be included, for example, **'10fp'**.|

## LPX<sup>10+</sup>

The **LPX** type is used to represent a length in lpx.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Type                   | Description                                    |
| --------------------- | -------------------------------------- |
| {number}lpx               | Logical pixel unit type. The unit lpx must be included, for example, **'10lpx'**.|

## Percentage<sup>10+</sup>

The **Percentage** type is used to represent a length in percentage.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Type                   | Description                                    |
| --------------------- | -------------------------------------- |
| {number}%               | Percentage type. The unit % must be included, for example, **'10%'**.|

## Degree<sup>10+</sup>

The **Degree** type is used to represent a length in deg.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Type                   | Description                                    |
| --------------------- | -------------------------------------- |
| {number}deg               | Degree type. The unit deg must be included, for example, **'10deg'**.|

## MultiShadowOptions<sup>10+</sup>

The **MultiShadowOptions** type is used to describe the shadow style.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name         | Type| Mandatory| Description|
| ------------- | ------- | ---- | -------- |
| radius | number \| [Resource](#resource) | No| Shadow blur radius.<br>The default value varies by API version.<br>API version 10 and earlier versions: **5**<br>Since API version 11: **20**<br>Unit: vp<br>**NOTE**<br>A value less than or equal to 0 is handled as the default value.|
| offsetX | number \| [Resource](#resource) | No| X-axis offset.<br>Default value: **5**.<br>Unit: vp|
| offsetY | number \| [Resource](#resource) | No| Y-axis offset.<br>Default value: **5**.<br>Unit: vp|

## SafeAreaType<sup>10+</sup>

The **SafeAreaType** type is used to describe the types of expanded safe areas.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name    | Description                                      |
| -------- | ------------------------------------------ |
| SYSTEM   | Default non-safe area of the system, including the status bar and navigation bar.  |
| CUTOUT   | Non-safe area of the device, for example, the notch area.|
| KEYBOARD | Soft keyboard area.                              |

## SafeAreaEdge<sup>10+</sup>

The **SafeAreaEdge** type is used to define the edge for expanding the safe area.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name  | Description      |
| ------ | ---------- |
| TOP    | Top edge.|
| BOTTOM | Bottom edge.|
| START  | Start edge.|
| END    | End edge.|

## KeyboardAvoidMode<sup>12+</sup>

Enumerates modes in which a dialog box responds when the keyboard is displayed.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name   | Value  | Description                                            |
| ------- | ---- | ------------------------------------------------ |
| DEFAULT | 0    | Automatically avoids the soft keyboard and compresses the height when reaching the maximum limit.|
| NONE    | 1    | Does not avoid the soft keyboard.                                  |

## LayoutSafeAreaType<sup>12+</sup>

The **LayoutSafeAreaType** type is used to describe the types of expanded safe areas in layout.

| Name    | Description                                      |
| -------- | ------------------------------------------ |
| SYSTEM   | Default non-safe area of the system, including the status bar and navigation bar.  |

## LayoutSafeAreaEdge<sup>12+</sup>

The **LayoutSafeAreaEdge** type is used to define the edge for expanding the safe area.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name  | Value| Description      |
| ------ | --- | ---------- |
| TOP    | 0 | Top edge.<br>**Atomic service API**: This API can be used in atomic services since API version 12.|
| BOTTOM | 1 | Bottom edge.<br>**Atomic service API**: This API can be used in atomic services since API version 12.|
| START<sup>20+</sup>      | 2 | Start edge. This represents the left edge for in LTR mode and the right edge in RTL mode.<br>**Atomic service API**: This API can be used in atomic services since API version 20.|
| END<sup>20+</sup>        | 3 |End edge. This represents the right edge for in LTR mode and the left edge in RTL mode.<br>**Atomic service API**: This API can be used in atomic services since API version 20.|
| VERTICAL<sup>20+</sup>   | 4 |Vertical edges.<br>**Atomic service API**: This API can be used in atomic services since API version 20.|
| HORIZONTAL<sup>20+</sup> | 5 |Horizontal edges.<br>**Atomic service API**: This API can be used in atomic services since API version 20.|
| ALL<sup>20+</sup>        | 6 |All edges.<br>**Atomic service API**: This API can be used in atomic services since API version 20.|

## TouchPoint<sup>11+</sup>

The **TouchPoint** type is used to define the coordinates of the touch point.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name  | Type| Description      |
| ------ | ----------------------| ---------- |
| X | [Dimension](#dimension10) | X coordinate of the touch point.|
| Y | [Dimension](#dimension10) | Y coordinate of the touch point.|

## PixelRoundPolicy<sup>11+</sup>

The **PixelRoundPolicy** type is used to describe the direction of pixel rounding at the component level.

**Widget capability**: This API can be used in ArkTS widgets since API version 11.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name    | Type               | Mandatory  | Description                  |
| ------ | ----------------- | ---- | -------------------- |
| start | [PixelRoundCalcPolicy](ts-appendix-enums.md#pixelroundcalcpolicy11) | No| Rounding for alignment with the start edge.|
| top | [PixelRoundCalcPolicy](ts-appendix-enums.md#pixelroundcalcpolicy11) | No| Rounding for alignment with the top edge.|
| end | [PixelRoundCalcPolicy](ts-appendix-enums.md#pixelroundcalcpolicy11) | No| Rounding for alignment with the end edge.|
| bottom | [PixelRoundCalcPolicy](ts-appendix-enums.md#pixelroundcalcpolicy11) | No| Rounding for alignment with the bottom edge.|

## VoidCallback<sup>12+</sup>

type VoidCallback: () => void;

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

## Callback<sup>12+</sup>

Callback<T,V = void> = (data: T) => V;

The **Callback** type is used to represent the callback with parameters.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

## HoverCallback<sup>12+</sup>

The **HoverCallback** type is used to represent the callback for the hover event.

type HoverCallback = (isHover: boolean, event: HoverEvent) => void;

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name           | Type                 | Description                                      |
| ------------- | ---------------------- | ---------------------------------------- |
| HoverCallback | (isHover: boolean, event: HoverEvent) => void | Callback for the hover event.|

## VisibleAreaEventOptions<sup>12+</sup>

The **VisibleAreaEventOptions** type is used to describe visible area changes.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name| Type                                               | Mandatory| Description                                                        |
| ------ | --------------------------------------------------- | ---- | ------------------------------------------------------------ |
| ratios | Array&lt;number&gt;                                 | Yes  | Threshold array. Each threshold represents a ratio of the component's visible area (that is, the area of the component that is visible on screen; only the area within the parent component is counted) to the component's total area. The value range of the threshold is [0.0, 1.0]. If the threshold set exceeds this range, the value **0.0** or **1.0** will be used.|
| expectedUpdateInterval | number | No| Expected update interval, in milliseconds. You can set it as appropriate. Default value: **1000**|

## VisibleAreaChangeCallback<sup>12+</sup>

The **VisibleAreaChangeCallback** type is used to represent a callback for visible area changes of the component.

type VisibleAreaChangeCallback = (isExpanding: boolean, currentRatio: number) => void;

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name           | Type                  | Description                                      |
| ------------- | ---------------------- | ---------------------------------------- |
| VisibleAreaChangeCallback | (isExpanding: boolean, currentRatio: number) => void | Callback for visible area changes of the component.<br>- **isExpanding**: whether the ratio of the component's visible area to its total area is greater than the previous one. The value **true** means that the ratio is greater than the previous one, and **false** means the opposite.<br>- **currentRatio**: ratio of the component's visible area to its total area when this callback is invoked.|

## DividerStyleOptions<sup>12+</sup>

The **DividerStyleOptions** type is used to provide the information about the divider.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name    | Type                                     | Mandatory| Description             |
| ------ | --------------------------------------- |---|-----------------|
| strokeWidth  | [LengthMetrics](../js-apis-arkui-graphics.md#lengthmetrics12)<sup>12+</sup>  | No| Width of the divider.        |
| color  | [ResourceColor](#resourcecolor) | No | Color of the divider.        |
| startMargin | [LengthMetrics](../js-apis-arkui-graphics.md#lengthmetrics12)<sup>12+</sup> | No | Distance between the divider and the start edge of the menu.|
| endMargin  | [LengthMetrics](../js-apis-arkui-graphics.md#lengthmetrics12)<sup>12+</sup>| No | Distance between the divider and the end edge of the menu.|
| mode  | [DividerMode](ts-appendix-enums.md)<sup>19+</sup>| No | Mode of the divider.|

## TextContentControllerBase<sup>10+</sup>

The **TextContentControllerBase** type is used to represent the base controller for **TextInput**, **TextArea**, and **Search** components.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

### getTextContentRect<sup>10+</sup>

getTextContentRect(): RectResult

The **getTextContentRect** type is used to obtain the position of the edited text area relative to the component and its size. The unit of the return value is pixel.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Return value**

| Type      | Description      |
| -------------------  | -------- |
| [RectResult](#rectresult10) | Position of the edited text area relative to the component and its size.|

> **NOTE**
>
> - If no text is entered, the return value contains the position information, but the size is 0.
> - The position information is the offset of the first character relative to the editable area.
> - For the **Search** component, the returned position information is the offset of the first character relative to the search icon in the component.
> - If there is input, the width in the return value is the fixed width of the editable area.

### getTextContentLineCount<sup>10+</sup>

getTextContentLineCount(): number

The **getTextContentLineCount** type is used to obtain the number of lines of the edited text.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Return value**

| Type | Description      |
| ----- | -------- |
| number| Number of lines of the edited text.|

### getCaretOffset<sup>11+</sup>

getCaretOffset(): CaretOffset

The **getCaretOffset** type is used to obtain the position information of the caret.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Return value**

| Type                     | Description              |
| ----------------------- | ---------------- |
| [CaretOffset](#caretoffset11) | Position of the caret relative to the text box.|

> **NOTE**
>
> - If this API is called when the caret position is updated in the current frame, it will not take effect.
> - For the **Search** component, the returned position information is the offset of the first character relative to the search icon in the component.
> - If no text is entered in the **Search** component, the return value contains the position information relative to the component.
> - The location information in the return value is the location of the caret relative to the editable component.

### addText<sup>15+</sup>

addText(text: string, textOperationOptions?: TextContentControllerOptions): number

Inserts text at a specified position in the editable content. If no position is specified, the text is appended to the end of the existing content.
This API does not work when the text is being dragged.

**addText** only affects the UI performance within the application and has no effect on the internal logic of the input method application. Therefore, avoid calling this API for preview text.

**Atomic service API**: This API can be used in atomic services since API version 15.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name | Type  | Mandatory  | Description |
| ------- | ------ | ---- | ----- |
| text | string | Yes   | Text to insert.|
| textOperationOptions   | [TextContentControllerOptions](#textcontentcontrolleroptions15) | No   | Configuration option for inserting text. If this parameter is not provided, the text is appended to the end.|

**Return value**

| Type | Description      |
| ----- | -------- |
| number| New cursor position after insertion.|

### deleteText<sup>15+</sup>

deleteText(range?: TextRange): void

Deletes text within a specified range in the editable content.
This API does not work when the text is being dragged.

**deleteText** only affects the UI performance within the application and has no effect on the internal logic of the input method application. Therefore, avoid calling this API for preview text.

**Atomic service API**: This API can be used in atomic services since API version 15.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name | Type  | Mandatory  | Description |
| ------- | ------ | ---- | ----- |
| range | [TextRange](ts-text-common.md#textrange12) | No   | Range of the text to be deleted, including the start and end positions.<br>If the range is not specified, the entire text is deleted. If the start position is not specified, deletion starts from index 0. If the end position is not specified, deletion ends at the end of the text.|

### getSelection<sup>15+</sup>

getSelection(): TextRange

Obtains the current text selection range.

**Atomic service API**: This API can be used in atomic services since API version 15.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Return value**

| Type                     | Description              |
| ----------------------- | ---------------- |
| [TextRange](ts-text-common.md#textrange12) | Current text selection range, or cursor position if no text is selected.|

### clearPreviewText<sup>17+</sup>

clearPreviewText(): void

Clears the current preview text.

**Atomic service API**: This API can be used in atomic services since API version 17.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

## TextDecorationOptions<sup>12+</sup>

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name   | Type                                                   | Mandatory| Description                                                        |
| ------- | ----------------------------------------------------------- | ---- | ------------------------------------------------------------ |
| type  | [TextDecorationType](ts-appendix-enums.md#textdecorationtype) | Yes  | Type of the text decorative line.<br>**Atomic service API**: This API can be used in atomic services since API version 11.|
| color  |  [ResourceColor](#resourcecolor) | No  | Color of the text decorative line.<br>**Atomic service API**: This API can be used in atomic services since API version 11.|
| style | [TextDecorationStyle](ts-appendix-enums.md#textdecorationstyle12) | No  | Style of the text decorative line.<br>**Atomic service API**: This API can be used in atomic services since API version 12.|

## SelectionOptions<sup>12+</sup>

The **SelectionOptions** type is used to describe the configuration options for text selection.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name      | Type                                           | Mandatory| Description            |
| ---------- | ----------------------------------------------- | ---- | ---------------- |
| menuPolicy | [MenuPolicy](#menupolicy12) | No  | Menu display policy.|

## MenuPolicy<sup>12+</sup>

The **MenuPolicy** type is used to describe the menu display policy.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name   | Value  | Description                              |
| ------- | ---- | ---------------------------------- |
| DEFAULT | 0    | Whether the menu is displayed depends on the underlying default logic.|
| HIDE    | 1    | The menu is always hidden.                  |
| SHOW    | 2    | The menu is always displayed.                    |

## CaretOffset<sup>11+</sup>

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name  | Type    | Description            |
| ----- | ------ | -------------- |
| index | number | Index of the caret position.   |
| x     | number | X coordinate of the caret relative to the text box, in px.|
| y     | number | Y coordinate of the caret relative to the text box, in px.|

## InputCounterOptions<sup>11+</sup>

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name             | Type   | Description                                                        |
| ------------------- | ------- | ------------------------------------------------------------ |
| thresholdPercentage | number  | Threshold percentage for displaying the character counter. The character counter is displayed when the number of characters that have been entered is greater than the maximum number of characters multiplied by the threshold percentage value. When displayed, the character counter is in the following format: Number of characters that have been entered/Maximum number of characters allowed. It is visible when the number of characters entered is greater than the character limit multiplied by the threshold percentage value. Value range: [1, 100]<br>If the value is not an integer, it is rounded down to the nearest integer. If the value exceeds the valid value range, the character counter is not displayed. If the value is **undefined**, the character counter is displayed, but this parameter has no effect.|
| highlightBorder     | boolean | Whether to highlight the text box border and character counter subscript in red. If **options** is not set, the text box border and character counter subscript turn red when the number of characters entered reaches the limit. If the character counter is displayed and **thresholdPercentage** is set to a valid value, the text box border and character counter subscript turn red when the number of entered characters exceeds the limit. The value **true** (default) means to highlight the text box border and character counter subscript in red.|

## ChainWeightOptions<sup>14+</sup>

The **ChainWeightOptions** type is used to describe the layout weight of a component within a chain.

**Atomic service API**: This API can be used in atomic services since API version 14.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name  | Type    | Description            |
| ----- | ------ | -------------- |
| horizontal | number | Layout weight of the component in the horizontal direction. It is effective when set to a value greater than 0.<br> Default value: **0**<br> Invalid values are treated as **0**. |
| vertical     | number | Layout weight of the component in the vertical direction. It is effective when set to a value greater than 0.<br> Default value: **0**<br> Invalid values are treated as **0**.|

## Configuration

The **Configuration** type is used to describe the color mode and font scale.

**Widget capability**: This API can be used in ArkTS widgets since API version 9.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name     | Type  | Read Only| Optional| Description      |
| --------- | ------ | ---- | ---- | ---------- |
| colorMode | string | Yes  | No  | Color mode.|
| fontScale | number | Yes  | No  | Font scale.|

## LayoutPolicy<sup>15+</sup>

The **LayoutPolicy** type is used to set the layout policy.


**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name     | Type  | Read Only| Optional| Description|
| --------- | ------ | ---- | ---- |---------- |
| matchParent | [LayoutPolicy](ts-types.md#layoutpolicy15) | Yes| No  | The current component adapts to the parent container's layout, with its size equal to the parent container's content area.<br>**Widget capability**: This API can be used in ArkTS widgets since API version 15.<br>**Atomic service API**: This API can be used in atomic services since API version 15.|
| wrapContent<sup>20+</sup> | [LayoutPolicy](ts-types.md#layoutpolicy15) | Yes| No  | The current component adapts to the child component's layout, with its size equal to the child component and no larger than the parent container's content area.<br>**Widget capability**: This API can be used in ArkTS widgets since API version 20.<br>**Atomic service API**: This API can be used in atomic services since API version 20.|
| fixAtIdealSize<sup>20+</sup> | [LayoutPolicy](ts-types.md#layoutpolicy15) | Yes| No  | The current component adapts to the child component's layout, with its size equal to the child component and potentially exceeding the parent container's content area.<br>**Widget capability**: This API can be used in ArkTS widgets since API version 20.<br>**Atomic service API**: This API can be used in atomic services since API version 20.|

>  **NOTE**
>
> - For specific example code, see [Example 5: Setting the Layout Policy](./ts-universal-attributes-size.md#example-5-setting-the-layout-policy).
>
> - With **matchParent**, if the parent container has a fixed length, the component adjusts to the parent's size. If the parent container has no fixed length, the component waits for all sibling components to complete layout before adjusting.
> 
> - If multiple child components under the same parent container use **matchParent**, all of them will be resized to the parent's size. This potentially causes overflow rendering outside the bounds of the parent container if the parent container is [Flex](./ts-container-flex.md), [Row](./ts-container-row.md), [Column](./ts-container-column.md), or [RelativeContainer](./ts-container-relativecontainer.md).
> 
> - Setting **matchParent** will force the component to match the parent's size, overriding any other size constraints (except aspect ratio) set on the component.
>
> - Priority rules:<br>- **matchParent**: Aspect ratio > **matchParent** > [constraintSize](ts-universal-attributes-size.md#constraintsize)<br>- **wrapContent**: Aspect ratio > [constraintSize](ts-universal-attributes-size.md#constraintsize) > **wrapContent**<br>- **fixAtIdealSize**: Aspect ratio > [constraintSize](ts-universal-attributes-size.md#constraintsize) > **fixAtIdealSize**
>
> - A component with **matchParent** is resized to match the parent container's content area, which excludes the parent's padding, border, and safe area padding (**safeAreaPadding**).
>
>  **Use cases**:
> 
> - When using [custom layout for custom components](ts-custom-component-layout.md) with unknown child component content, set **LayoutPolicy.fixAtIdealSize** for the width or height to allow the child component to be bound only by the custom layout, ignoring parent size constraints.

## TextContentControllerOptions<sup>15+</sup>

The **TextContentControllerOptions** type is used to configure the insertion of text into a text box.

**Atomic service API**: This API can be used in atomic services since API version 15.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name     | Type  | Read Only| Optional| Description      |
| --------- | ------ | ---- | ---- | ---------- |
| offset | number | Yes  | Yes  | Position where the text will be inserted.|
