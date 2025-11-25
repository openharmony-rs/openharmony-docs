# Basic Types
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @jiangtao92-->
<!--Designer: @piggyguy-->
<!--Tester: @songyanhong-->
<!--Adviser: @HelloCrease-->

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

>  **NOTE**
>
>  When referencing a resource type, ensure that the data type in the resource type object is the same as the type of the attribute method that uses the resource type as the parameter. For example, if an attribute method supports setting string | Resource, the data type must be string when Resource is used.
>
>  When referencing a resource type, ensure that the resource type object is used in the supported mode. Otherwise, the attribute effect of the resource type as a parameter is the same as that of not setting the attribute.

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

| Name| Type| Read-Only| Optional| Description|
| -------- | -------- | -------- | -------- | -------- |
| top    | [Length](#length) | No| Yes   | Height of the padding on the top of the component. |
| right  | [Length](#length) | No| Yes   | Width of the padding on the right of the component.|
| bottom | [Length](#length) | No| Yes   | Height of the padding at the bottom of the component. |
| left   | [Length](#length) | No| Yes   | Width of the padding on the left of the component.|

## LocalizedPadding<sup>12+</sup>

The **Padding** type is used to describe the paddings in different directions of a component.

**Widget capability**: This API can be used in ArkTS widgets since API version 12.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name| Type| Read-Only| Optional| Description|
| -------- | -------- | -------- | -------- | -------- |
| top    | [LengthMetrics](../js-apis-arkui-graphics.md#lengthmetrics12)<sup>12+</sup> | No| Yes   | Height of the padding on the top of the component. |
| end    | [LengthMetrics](../js-apis-arkui-graphics.md#lengthmetrics12)<sup>12+</sup> | No| Yes   | Width of the padding on the right of the component.<br> <br>Width of the padding on the left of the component in RTL mode.|
| bottom | [LengthMetrics](../js-apis-arkui-graphics.md#lengthmetrics12)<sup>12+</sup> | No| Yes   | Height of the padding at the bottom of the component. |
| start  | [LengthMetrics](../js-apis-arkui-graphics.md#lengthmetrics12)<sup>12+</sup> | No| Yes   | Width of the padding on the left of the component.<br> <br>Width of the padding on the right of the component in RTL mode.|

## Margin

The **Margin** type is used to describe the margins in different directions of a component.

**Widget capability**: This API can be used in ArkTS widgets since API version 9.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name    | Type               | Read-Only |  Optional  | Description                  |
| ------ | ----------------- | ---- | -------------------- | -------- |
| top    | [Length](#length) | No  |  Yes| Height of the margin above the component. |
| right  | [Length](#length) | No  |  Yes| Width of the margin on the right of the component.|
| bottom | [Length](#length) | No  |  Yes| Height of the margin below the component. |
| left   | [Length](#length) | No  |  Yes| Width of the margin on the left of the component.|

## LocalizedMargin<sup>12+</sup>

The **Margin** type is used to describe the margins in different directions of a component.

**Widget capability**: This API can be used in ArkTS widgets since API version 12.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name    | Type               | Read-Only |  Optional  | Description                  |
| ------ | ----------------- | ---- | -------------------- | -------- |
| top    | [LengthMetrics](../js-apis-arkui-graphics.md#lengthmetrics12)<sup>12+</sup> | No | Yes | Height of the margin above the component. |
| end    | [LengthMetrics](../js-apis-arkui-graphics.md#lengthmetrics12)<sup>12+</sup> | No  | Yes| Width of the margin on the right of the component.<br> <br>Width of the margin on the left of the component in RTL mode.|
| bottom | [LengthMetrics](../js-apis-arkui-graphics.md#lengthmetrics12)<sup>12+</sup> | No  | Yes| Height of the margin below the component. |
| start  | [LengthMetrics](../js-apis-arkui-graphics.md#lengthmetrics12)<sup>12+</sup> | No | Yes | Width of the margin on the left of the component.<br> <br>Width of the margin on the right of the component in RTL mode.|

## EdgeWidths<sup>9+</sup>

The **EdgeWidths** type is used to describe the edge widths in different directions of a component.
To reference this object, at least one parameter must be passed.

**Widget capability**: This API can be used in ArkTS widgets since API version 9.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name  | Type|Read-Only|Optional| Description            |
| ------ | ---- |------|------| ---------------- |
| top    | [Length](#length) | No|Yes   | Width of the top edge of the component.|
| right  | [Length](#length) | No|Yes   | Width of the right edge of the component.|
| bottom | [Length](#length) | No|Yes   | Width of the bottom edge of the component.|
| left   | [Length](#length) | No|Yes   | Width of the left edge of the component.|

## LocalizedEdgeWidths<sup>12+</sup>

The **EdgeWidths** type is used to describe the edge widths in different directions of a component.
To reference this object, at least one parameter must be passed.

**Widget capability**: This API can be used in ArkTS widgets since API version 12.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name  | Type|Read-Only|Optional| Description            |
| ------ | ---- |------|------| ---------------- |
| top    | [LengthMetrics](../js-apis-arkui-graphics.md#lengthmetrics12)<sup>12+</sup> | No|Yes  | Width of the top edge of the component.|
| end    | [LengthMetrics](../js-apis-arkui-graphics.md#lengthmetrics12)<sup>12+</sup> | No|Yes  | Width of the right edge of the component.<br>Width of the left edge of the component in RTL mode.|
| bottom | [LengthMetrics](../js-apis-arkui-graphics.md#lengthmetrics12)<sup>12+</sup> | No|Yes  | Width of the bottom edge of the component.|
| start  | [LengthMetrics](../js-apis-arkui-graphics.md#lengthmetrics12)<sup>12+</sup> | No|Yes  | Width of the left edge of the component.<br>Width of the right edge of the component in RTL mode.|

## BorderRadiuses<sup>9+</sup>

The **BorderRadiuses** type is used to describe the corner radius of a component's border.
To reference this object, at least one parameter must be passed.

**Widget capability**: This API can be used in ArkTS widgets since API version 9.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name| Type| Read-Only| Optional| Description|
| -------- | -------- | -------- | -------- | -------- |
| topLeft     | [Length](#length) | No|Yes   | Radius of the upper left corner of the component.|
| topRight    | [Length](#length) | No|Yes   | Radius of the upper right corner of the component.|
| bottomLeft  | [Length](#length) | No|Yes   | Radius of the lower left corner of the component.|
| bottomRight | [Length](#length) | No|Yes   | Radius of the lower right corner of the component.|

## LocalizedBorderRadiuses<sup>12+</sup>

The **LocalizedBorderRadiuses** type is used to describe the corner radius of a component's border.
To reference this object, at least one parameter must be passed.

**Widget capability**: This API can be used in ArkTS widgets since API version 12.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name| Type| Read-Only| Optional| Description|
| -------- | -------- | -------- | -------- | -------- |
| topStart    | [LengthMetrics](../js-apis-arkui-graphics.md#lengthmetrics12)<sup>12+</sup> | No|Yes   | Radius of the upper left corner of the component.<br>Radius of the upper left right of the component in RTL mode.|
| topEnd      | [LengthMetrics](../js-apis-arkui-graphics.md#lengthmetrics12)<sup>12+</sup> | No|Yes   | Radius of the upper right corner of the component.<br>Radius of the upper left corner of the component in RTL mode.|
| bottomStart | [LengthMetrics](../js-apis-arkui-graphics.md#lengthmetrics12)<sup>12+</sup> | No|Yes   | Radius of the lower left corner of the component.<br>Radius of the lower right corner of the component in RTL mode.|
| bottomEnd   | [LengthMetrics](../js-apis-arkui-graphics.md#lengthmetrics12)<sup>12+</sup> | No|Yes   | Radius of the lower right corner of the component.<br>Radius of the lower left corner of the component in RTL mode.|

## EdgeColors<sup>9+</sup>

The **EdgeColors** type is used to describe the edge colors of a component.
To reference this object, at least one parameter must be passed.

**Widget capability**: This API can be used in ArkTS widgets since API version 9.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name  | Type|Read-Only|Optional| Description            |
| ------ | ---- |------|------| ---------------- |
| top    | [ResourceColor](#resourcecolor) | No|Yes   | Color of the top edge of the component.|
| right  | [ResourceColor](#resourcecolor) | No|Yes   | Color of the right edge of the component.|
| bottom | [ResourceColor](#resourcecolor) | No|Yes   | Color of the bottom edge of the component.|
| left   | [ResourceColor](#resourcecolor) | No|Yes   | Color of the left edge of the component.|

## LocalizedEdgeColors<sup>12+</sup>

The **EdgeColors** type is used to describe the edge colors of a component.
To reference this object, at least one parameter must be passed.

**Widget capability**: This API can be used in ArkTS widgets since API version 12.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name  | Type|Read-Only|Optional| Description            |
| ------ | ---- |------|------| ---------------- |
| top    | [ResourceColor](#resourcecolor) | No|Yes   | Color of the top edge of the component.|
| end    | [ResourceColor](#resourcecolor) | No|Yes   | Color of the right edge of the component.<br>Color of the left edge of the component in RTL mode.|
| bottom | [ResourceColor](#resourcecolor) | No|Yes   | Color of the bottom edge of the component.|
| start  | [ResourceColor](#resourcecolor) | No|Yes   | Color of the left edge of the component.<br>Color of the right edge of the component in RTL mode.|

## EdgeStyles<sup>9+</sup>

The **EdgeStyles** type is used to describe the edge styles of a component.
To reference this object, at least one parameter must be passed.

**Widget capability**: This API can be used in ArkTS widgets since API version 9.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name| Type| Read-Only| Optional| Description|
| -------- | -------- | -------- | -------- | -------- |
| top    | [BorderStyle](ts-appendix-enums.md#borderstyle) | No|Yes   | Style of the top edge of the component.|
| right  | [BorderStyle](ts-appendix-enums.md#borderstyle) | No|Yes   | Style of the right edge of the component.|
| bottom | [BorderStyle](ts-appendix-enums.md#borderstyle) | No|Yes   | Style of the bottom edge of the component.|
| left   | [BorderStyle](ts-appendix-enums.md#borderstyle) | No|Yes   | Style of the left edge of the component.|

## Offset

The **Offset** type is used to describe the offset coordinates of a component in the layout.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name  | Type               | Read-Only |  Optional  | Description      |
| ---- | ----------------- | ---- | -------- | -------- |
| dx   | [Length](#length) | No |  No   | X coordinate of the offset.|
| dy   | [Length](#length) | No |  No   | Y coordinate of the offset.|

## RectResult<sup>10+</sup>

The **RectResult** type is used to describe the position, width, and height of a component.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name     | Type  | Read-Only| Optional | Description|
| ------- | ------ | ----- | -------- | ---------- |
| x     | number | No| No| Horizontal coordinate.|
| y     | number |  No| No| Vertical coordinate.|
| width | number | No| No| Content width.|
| height | number | No| No| Content height.|

## ResourceColor

type ResourceColor = [Color](ts-appendix-enums.md#color) | number | string | [Resource](#resource)

The **ResourceColor** type is used to describe the color types of resources.

**Widget capability**: This API can be used in ArkTS widgets since API version 9.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Type                               | Description                                                        |
| ----------------------------------- | ------------------------------------------------------------ |
| [Color](ts-appendix-enums.md#color) | Color enums.                                                |
| number                              | Color in hexadecimal notation. RGB and ARGB are supported. Examples: **0xffffff** and **0xffff0000**. If the number type is used, the format of the color value depends on the value. For example, 0x00ffffff is parsed as an RGB color value.|
| string                              | Color in RGB or ARGB notation. Example: **'#ffffff'**, **'#ff000000'**, **'rgb(255, 100, 255)'**, **'rgba(255, 100, 255, 0.5)'**|
| [Resource](#resource)               | Color referenced from system or application resources.      |

## LengthConstrain

The **LengthConstrain** type is used to describe the maximum and minimum lengths of a component.

**Widget capability**: This API can be used in ArkTS widgets since API version 9.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name       | Type               | Read-Only |  Optional  | Description     |
| --------- | ----------------- | ---- | ------- | -------- |
| minLength | [Length](#length) | No |  No   | Minimum length of the component.|
| maxLength | [Length](#length) | No |  No   | Maximum length of the component.|


## Font

The **Font** type is used to set the text style.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name  | Type                                                        | Read-Only |  Optional| Description                                                        |
| ------ | ------------------------------------------------------------ | ---- | -------- | ------------------------------------------------------------ |
| size   | [Length](#length)                                            | No  |  Yes | Font size. If the value is of the number type, the unit fp is used. Percentage strings are not supported.<br>Default value: **16.0**|
| weight | [FontWeight](ts-appendix-enums.md#fontweight) \| number \| string | No |  Yes| Font weight. For the number type, the value ranges from 100 to 900, at an interval of 100. A larger value indicates a thicker font.<br>Default value: **400** \| **FontWeight.Normal** |
| family | string \| [Resource](#resource)                              | No  |  Yes | Font family of the text. Use commas (,) to separate multiple fonts. The priority of the fonts is the sequence in which they are placed. An example value is **'Arial, HarmonyOS Sans'**. Currently, the HarmonyOS Sans font and custom font [loadFontSync](../../apis-arkgraphics2d/js-apis-graphics-text.md#loadfontsync) are supported.|
| style  | [FontStyle](ts-appendix-enums.md#fontstyle)                  | No  |  Yes | Font style.<br>Default value: **FontStyle.Normal**            |

## Area<sup>8+</sup>

Area type, which is used to store the area information of an element.

**Widget capability**: This API can be used in ArkTS widgets since API version 9.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name            | Type                    | Description                            |
| -------------- | ---------------------- | ------------------------------ |
| width          | [Length](#length)      | Width of the target element.<br>Unit: vp|
| height         | [Length](#length)      | Height of the target element.<br>Unit: vp|
| position       | [Position](#position) | Position of the upper left corner of the component relative to that of its parent container.           |
| globalPosition | [Position](#position) | Position of the upper left corner of the component relative to that of the page where the component resides.            |

## Position

The **Position** type is used to represent coordinates of a point.

**Widget capability**: This API can be used in ArkTS widgets since API version 9.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name  | Type               | Read-Only |  Optional  | Description                         |
| ---- | ----------------- | ---- | -------- | --------------------------- |
| x    | [Length](#length) | No  |  Yes| X-coordinate<br>Unit: vp|
| y    | [Length](#length) | No  |  Yes| Y-coordinate.<br>Unit: vp|

## LocalizedPosition<sup>12+</sup>

The **LocalizedPosition** type is used to represent coordinates of a point.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name  | Type               | Read-Only |  Optional  | Description                         |
| ---- | ----------------- | ---- | -------- | --------------------------- |
| start  | [LengthMetrics](../js-apis-arkui-graphics.md#lengthmetrics12) | No |  Yes | X-coordinate relative to the left for left-to-right (LTR) scripts; X-coordinate relative to the right for right-to-left (RTL) scripts. |
| top    | [LengthMetrics](../js-apis-arkui-graphics.md#lengthmetrics12) | No  |  Yes| Y-coordinate.|

## Edges<sup>12+</sup>

The **Edges** type is used to describe the offset relative to the four edges. If both **top** and **bottom** are set, only **top** takes effect. If both **left** and **right** are set, only **left** takes effect.

**Widget capability**: This API can be used in ArkTS widgets since API version 12.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name  | Type    | Read-Only |  Optional  | Description                         |
| ---- | ------ | ---- | -------- | --------------------------- |
| top    | [Dimension](#dimension10) | No | Yes | Offset relative to the top edge.|
| bottom    | [Dimension](#dimension10) | No | Yes | Offset relative to the bottom edge.|
| left    | [Dimension](#dimension10) | No  | Yes| Offset relative to the left edge.|
| right    | [Dimension](#dimension10) | No |  Yes | Offset relative to the right edge.|

## LocalizedEdges<sup>12+</sup>

The **LocalizedEdges** type is used to describe the offset relative to the four edges. If both **top** and** bottom **are set, only **top** takes effect. If both **start** and **end** are set, only **start** takes effect.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name  | Type    | Read-Only |  Optional  | Description                         |
| ---- | ------ | ---- | -------- | --------------------------- |
| top    | [LengthMetrics](../js-apis-arkui-graphics.md#lengthmetrics12) | No |  Yes | Offset relative to the top edge.|
| bottom    | [LengthMetrics](../js-apis-arkui-graphics.md#lengthmetrics12) | No  | Yes| Offset relative to the bottom edge.|
| start    | [LengthMetrics](../js-apis-arkui-graphics.md#lengthmetrics12) | No  | Yes| Offset relative to the left in LTR mode; offset relative to the right in RTL mode.|
| end    | [LengthMetrics](../js-apis-arkui-graphics.md#lengthmetrics12) | No |  Yes | Offset relative to the right for in LTR mode; offset relative to the left in RTL mode.|

## ConstraintSizeOptions

Describes the size constraints of a component during layout.

**Widget capability**: This API can be used in ArkTS widgets since API version 9.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name| Type| Read-Only| Optional| Description|
| -------- | -------- | -------- | -------- | -------- |
| minWidth  | [Length](#length) | No|Yes   | Minimum width of the component.|
| maxWidth  | [Length](#length) | No|Yes   | Maximum width of the component.|
| minHeight | [Length](#length) | No|Yes   | Minimum height of the component.|
| maxHeight | [Length](#length) | No|Yes   | Maximum height of the component.|

>  **NOTE**
>
>  In the [Row](./ts-container-row.md), [Column](./ts-container-column.md), and [RelativeContainer](./ts-container-relativecontainer.md) components, setting **width** and **height** to **auto** means that the size adapts to the size of their child components. In the [TextInput](./ts-basic-components-textinput.md) component, setting **width** to **auto** means that the width adapts to the width of the text content.

## SizeOptions

Describes the width and height of a component during layout.

**Widget capability**: This API can be used in ArkTS widgets since API version 9.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name| Type| Read-Only| Optional| Description|
| -------- | -------- | -------- | -------- | -------- |
| width  | [Length](#length) | No|Yes  | Width of the component.|
| height | [Length](#length) | No|Yes  | Height of the component.|


## BorderOptions

The **BorderOptions** type is used to provide border information.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name  | Type|Read-Only|Optional| Description            |
| ------ | ---- |------|------| ---------------- |
| width  | [EdgeWidths](./ts-types.md#edgewidths9)<sup>9+</sup> \| [Length](ts-types.md#length) \| [LocalizedEdgeWidths](./ts-types.md#localizededgewidths12)<sup>12+</sup> | No|Yes  | Border width.<br>**Atomic service API**: This API can be used in atomic services since API version 11.<br>**Widget capability**: This API can be used in ArkTS widgets since API version 9.    |
| color  | [EdgeColors](./ts-types.md#edgecolors9)<sup>9+</sup> \| [ResourceColor](ts-types.md#resourcecolor) \| [LocalizedEdgeColors](#localizededgecolors12)<sup>12+</sup> | No|Yes  | Border color.<br>**Atomic service API**: This API can be used in atomic services since API version 11.<br>**Widget capability**: This API can be used in ArkTS widgets since API version 9.    |
| radius | [BorderRadiuses](#borderradiuses9)<sup>9+</sup> \| [Length](ts-types.md#length) \| [LocalizedBorderRadiuses](#localizedborderradiuses12)<sup>12+</sup> | No|Yes  | Border corner radius.<br>**Atomic service API**: This API can be used in atomic services since API version 11.<br>**Widget capability**: This API can be used in ArkTS widgets since API version 9.|
| style  | [EdgeStyles](#edgestyles9)<sup>9+</sup> \| [BorderStyle](ts-appendix-enums.md#borderstyle) | No|Yes  | Border style.<br>**Atomic service API**: This API can be used in atomic services since API version 11.<br>**Widget capability**: This API can be used in ArkTS widgets since API version 9.   |
| dashGap<sup>12+</sup>  | [EdgeWidths](#edgewidths9) \| [LengthMetrics](../js-apis-arkui-graphics.md#lengthmetrics12) \| [LocalizedEdgeWidths](#localizededgewidths12) | No|Yes | Gap between dashed line segments. It takes effect when the border style is set to dashed.<br>Percentage values are not supported.<br>**Atomic service API**: This API can be used in atomic services since API version 12.<br>**Widget capability**: This API cannot be used in ArkTS widgets.|
| dashWidth<sup>12+</sup>  | [EdgeWidths](#edgewidths9) \| [LengthMetrics](../js-apis-arkui-graphics.md#lengthmetrics12) \| [LocalizedEdgeWidths](#localizededgewidths12) | No|Yes  | Width of dashed line segments. It takes effect when the border style is set to dashed.<br>Percentage values are not supported.<br>**Atomic service API**: This API can be used in atomic services since API version 12.<br>**Widget capability**: This API cannot be used in ArkTS widgets.    |

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
| CustomBuilder | (() =&gt; any) \| void | Builder used to generate a custom UI component when used with the [@Builder](../../../ui/state-management/arkts-builder.md) decorator.|

## MarkStyle<sup>10+</sup>

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name       | Type                                      | Read-Only |  Optional| Default Value     | Description                                                        |
| ----------- | ------------------------------------------ | ---- | -------- | ----------- | ------------------------------------------------------------ |
| strokeColor | [ResourceColor](ts-types.md#resourcecolor) | No |  Yes | Color.White | Color of the check mark.                                              |
| size        | [Length](ts-types.md#length)               | No |  Yes | -           | Size of the check mark, in vp. The default size is the same as the width of the check box component.<br>Percentage values are not supported. If an invalid value is set, the default value is used.|
| strokeWidth | [Length](ts-types.md#length)               | No |  Yes | 2           | Stroke width of the check mark, in vp. Percentage values are not supported. If an invalid value is set, the default value is used.|

## ModalTransition<sup>10+</sup>

The **ModalTransition** type is used to set the transition type for a full-screen modal.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name     | Description          |
| ------- | ------------ |
| NONE    | No transition animation for the modal.  |
| DEFAULT | Slide-up and slide-down animation for the modal. |
| ALPHA   | Opacity gradient animation for the modal.|

## OutlineOptions<sup>11+</sup>

Outer outline options.

**Atomic service API**: This API can be used in atomic services since API version 12.

**Widget capability**: This API can be used in ArkTS widgets since API version 11.

| Name  | Type                  | Read-Only  |   Optional                            | Description                                                        |
| ------ | ----------------------|----------------- | --------------------- | ------------------------------------------------------------ |
| width  | [Dimension](#dimension10) \| [EdgeOutlineWidths](#edgeoutlinewidths11)| No| Yes| Width of the outline. Percentage values are not supported.<br>Default value: **0**.<br>**width** must be set to display the outline effect.|
| color  | [ResourceColor](#resourcecolor) \| [EdgeColors](#edgecolors9) \| [LocalizedEdgeColors](#localizededgecolors12)<sup>12+</sup> | No| Yes| Color of the outline.<br>Default value: **Color.Black**.                  |
| radius | [Dimension](#dimension10) \| [OutlineRadiuses](#outlineradiuses11)| No| Yes| Radius of the outline corners. Percentage values are not supported.<br>Default value: **0**<br>Maximum effective value: Component width/2 + outlineWidth or component height/2 + outlineWidth|
| style  | [OutlineStyle](ts-universal-attributes-outline.md#outlinestyle11)  \| [EdgeOutlineStyles](#edgeoutlinestyles11)| No| Yes| Outline style.<br>Default value: **OutlineStyle.SOLID**           |

## EdgeOutlineWidths<sup>11+</sup>

To reference this object, at least one parameter must be passed.

**Atomic service API**: This API can be used in atomic services since API version 12.

**Widget capability**: This API can be used in ArkTS widgets since API version 11.

| Name    | Type                        | Read-Only| Optional  | Description     |
| ------ | ---------------------------- | -- | -- | ------- |
| left   | [Dimension](#dimension10) | No| Yes  | Thickness of the left outline.|
| right  | [Dimension](#dimension10) | No| Yes   | Thickness of the right outline.|
| top    | [Dimension](#dimension10) | No| Yes  | Width of the top outline.|
| bottom | [Dimension](#dimension10) | No| Yes | Thickness of the bottom outline.|

## OutlineRadiuses<sup>11+</sup>

To reference this object, at least one parameter must be passed.

**Atomic service API**: This API can be used in atomic services since API version 12.

**Widget capability**: This API can be used in ArkTS widgets since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name         | Type                        | Read-Only| Optional  | Description      |
| ----------- | -------------------- | -------- | ---- | -------- |
| topLeft     | [Dimension](ts-types.md#dimension10) | No| Yes  | Radius of the upper left corner.|
| topRight    | [Dimension](ts-types.md#dimension10) | No| Yes  | Radius of the upper right corner.|
| bottomLeft  | [Dimension](ts-types.md#dimension10) | No| Yes  | Radius of the lower left corner.|
| bottomRight | [Dimension](ts-types.md#dimension10) | No| Yes  | Radius of the lower right corner.|

## EdgeOutlineStyles<sup>11+</sup>

To reference this object, at least one parameter must be passed.

**Atomic service API**: This API can be used in atomic services since API version 12.

**Widget capability**: This API can be used in ArkTS widgets since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name    | Type                                    | Read-Only| Optional | Description     |
| ------ | ---------------------------------------- | -- | -- | ------- |
| left   | [OutlineStyle](ts-universal-attributes-outline.md#outlinestyle11)| No| Yes  | Style of the left outline.|
| right  | [OutlineStyle](ts-universal-attributes-outline.md#outlinestyle11)| No| Yes  | Style of the right outline.|
| top    | [OutlineStyle](ts-universal-attributes-outline.md#outlinestyle11)| No| Yes  | Style of the top outline.|
| bottom | [OutlineStyle](ts-universal-attributes-outline.md#outlinestyle11)| No | Yes | Style of the bottom outline.|

## Dimension<sup>10+</sup>

The **Length** type is used to represent a size unit.

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

## TouchPoint<sup>11+</sup>

The **TouchPoint** type is used to define the coordinates of the touch point.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name  | Type| Description      |
| ------ | ----------------------| ---------- |
| X | [Dimension](#dimension10) | X coordinate of the touch point.|
| Y | [Dimension](#dimension10) | Y coordinate of the touch point.|

## VoidCallback<sup>12+</sup>

type VoidCallback: () => void;

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

## Callback<sup>12+</sup>

Callback<T,V = void> = (data: T) => V;

The **Callback** type is used to represent the callback with parameters.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

## DividerStyleOptions<sup>12+</sup>

The **DividerStyleOptions** type is used to provide the information about the divider.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name    | Type                                     | Read-Only| Optional| Description             |
| ------ | --------------------------------------- |---| -------- |-----------------|
| strokeWidth  | [LengthMetrics](../js-apis-arkui-graphics.md#lengthmetrics12)<sup>12+</sup>  | No| Yes| Width of the divider.        |
| color  | [ResourceColor](#resourcecolor) | No | Yes| Color of the divider.        |
| startMargin | [LengthMetrics](../js-apis-arkui-graphics.md#lengthmetrics12)<sup>12+</sup> | No | Yes| Distance between the divider and the start edge of the menu.|
| endMargin  | [LengthMetrics](../js-apis-arkui-graphics.md#lengthmetrics12)<sup>12+</sup>| No | Yes| Distance between the divider and the end edge of the menu.|
| mode  | [DividerMode](ts-appendix-enums.md#dividermode19)<sup>19+</sup>| No | Yes| Mode of the divider.|

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

| Name     | Type  | Read-Only| Optional| Description      |
| --------- | ------ | ---- | ---- | ---------- |
| colorMode | string | Yes  | No  | Color mode.|
| fontScale | number | Yes  | No  | Font scale.|

## AccessibilityOptions<sup>14+</sup>

**Atomic service API**: This API can be used in atomic services since API version 14.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name                  | Type   | Read-Only| Optional| Description                                                        |
| ---------------------- | ------- | ---- | ---- | ------------------------------------------------------------ |
| accessibilityPreferred | boolean | No| Yes  | Whether to prioritize the accessibility text of child components during a deep traversal. The value **true** means to prioritize the accessibility text of child components.<br>If the accessibility text is empty, the text is selected. The combined text is set to the parent node whose accessibilityText and text are empty.<br>The value **false** means not to prioritize the accessibility text of child components.<br>Default value: **false**.|

## ScrollBarMargin<sup>20+</sup>

Scroll bar margin.

**Atomic service API**: This API can be used in atomic services since API version 20.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name | Type                                                        | Read-Only| Optional| Description                                  |
| ----- | ------------------------------------------------------------ | ---- | -- | -------------------------------------- |
| start | [LengthMetrics](../js-apis-arkui-graphics.md#lengthmetrics12) | No  | Yes| Start margin of the scroll bar.<br>Default value: **0**, in vp|
| end   | [LengthMetrics](../js-apis-arkui-graphics.md#lengthmetrics12) | No  | Yes| Margin at the end of the scroll bar.<br>Default value: **0**, in vp|

## DirectionalEdgesT\<T><sup>12+</sup>

Edge width type, which is used to describe the width of the component edge in different directions. Globalization is supported.

**Widget capability**: This API can be used in ArkTS widgets since API version 12.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name  | Type|Read-Only|Optional| Description            |
| ------ | ---- |------|------| ---------------- |
| start   | T    |No|No| Start edge. It is the left edge if the direction is left-to-right and the right edge if the direction is right-to-left.|
| end    | T    | No|No|End edge. It is the right edge if the direction is left-to-right and the left edge if the direction is right-to-left.|
| top  | T    | No|No|Top edge.|
| bottom | T    | No|No|Bottom edge.|

## Bias

Defines the offset of the component under the anchor constraints.
<br>In the horizontal direction, the value of **Bias** is the ratio of the distance from the component to the left anchor D<sub>start</sub> to the total distance between the component and the horizontal anchors D<sub>start</sub> + D<sub>end</sub>. In a mirrored language layout, D<sub>start</sub> is the distance from the component to the right anchor. The width of the component is represented by D<sub>width</sub>.
<br>![bias_horizontal_example.png](figures/bias_horizontal_example.png)
<br>Similarly, in the vertical direction, the value of **Bias** is the ratio of the distance from the component to the top anchor D<sub>top</sub> to the total distance between the component and the vertical anchors D<sub>top</sub> + D<sub>bottom</sub>. The height of the component is represented by D<sub>height</sub>.
<br>![bias_vertical_example.png](figures/bias_vertical_example.png)


**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name| Type| Read-Only| Optional| Description|
| -------- | -------- | -------- | -------- | -------- |
| horizontal  | number | No|Yes| Bias value in the horizontal direction.<br>This parameter is valid only when the width attribute of the child component has a correct value and two horizontal anchors are available. The value must be greater than or equal to 0.<br>Default value: **0.5**|
| vertical  | number | No|Yes| Returns the bias value in the vertical direction.<br>This parameter is valid only when the height attribute of the child component has a correct value and two vertical anchors are available. The value must be greater than or equal to 0.<br>Default value: **0.5**|
