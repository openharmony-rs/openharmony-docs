# Outline Styling
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @CCFFWW-->
<!--Designer: @CCFFWW-->
<!--Tester: @lxl007-->
<!--Adviser: @Brilliantry_Rui-->

You can set outline attributes for components. Drawn outside the component, the outline does not affect the component's layout or increase its size.

![outlineTest](figures/outlineTest.PNG)

>  **NOTE**
>
>  The initial APIs of this module are supported since API version 11. Updates will be marked with a superscript to indicate their earliest API version.

## outline

outline(value: OutlineOptions): T

Sets the outline attributes in one declaration.

**Widget capability**: This API can be used in ArkTS widgets since API version 11.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type                                     | Mandatory| Description        |
| ------ | ----------------------------------------- | ---- | ------------ |
| value  | [OutlineOptions](ts-types.md#outlineoptions11) | Yes  | Outline attributes.|

**Return value**

| Type  | Description                    |
| ------ | ------------------------ |
| T | Current component.|

## outline<sup>18+</sup>

outline(options: Optional\<OutlineOptions>): T

Sets the outline attributes in one declaration. Compared with [outline](#outline), this API supports the **undefined** type for the **options** parameter.

**Widget capability**: This API can be used in ArkTS widgets since API version 18.

**Atomic service API**: This API can be used in atomic services since API version 18.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type                                     | Mandatory| Description|
| ------ | ----------------------------------------- | ---- | ---- |
| options | [Optional](ts-universal-attributes-custom-property.md#optionalt12)\<[OutlineOptions](ts-types.md#outlineoptions11)>| Yes  |   Outline attributes.<br>If **options** is **undefined**, the component reverts to its original style with no outline.  |

**Return value**

| Type  | Description                    |
| ------ | ------------------------ |
| T | Current component.|

## OutlineStyle<sup>11+</sup>

Outline attributes.

**Widget capability**: This API can be used in ArkTS widgets since API version 11.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name    | Value| Description                           |
| ------ | ------ | ----------------------- |
| SOLID  | 0 | Solid border.                     |
| DASHED | 1 | Dashed border.                |
| DOTTED | 2 | Dotted border. The radius of a dot is half of **outlineWidth**.|

## outlineStyle

outlineStyle(value: OutlineStyle | EdgeOutlineStyles): T

Sets the outline style. If this API is not used, a solid line is displayed by default.

**Widget capability**: This API can be used in ArkTS widgets since API version 11.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type                                                        | Mandatory| Description                                                 |
| ------ | ------------------------------------------------------------ | ---- | ----------------------------------------------------- |
| value  | [OutlineStyle](#outlinestyle11)&nbsp;\|&nbsp;[EdgeOutlineStyles](ts-types.md#edgeoutlinestyles11) | Yes  | Outline style.|

**Return value**

| Type  | Description                    |
| ------ | ------------------------ |
| T | Current component.|

## outlineStyle<sup>18+</sup>

outlineStyle(style: Optional\<OutlineStyle | EdgeOutlineStyles>): T

Sets the outline style. If this API is not used, a solid line is displayed by default. Compared with [outlineStyle](#outlinestyle), this API supports the **undefined** type for the **style** parameter.

**Widget capability**: This API can be used in ArkTS widgets since API version 18.

**Atomic service API**: This API can be used in atomic services since API version 18.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type                                                        | Mandatory| Description                                                        |
| ------ | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| style  | [Optional](ts-universal-attributes-custom-property.md#optionalt12)\<[OutlineStyle](#outlinestyle11)&nbsp;\|&nbsp;[EdgeOutlineStyles](ts-types.md#edgeoutlinestyles11)> | Yes  | Outline style.<br>If **style** is **undefined**, the component reverts to its original style with no outline.|

**Return value**

| Type  | Description                    |
| ------ | ------------------------ |
| T | Current component.|

## outlineWidth

outlineWidth(value: Dimension | EdgeOutlineWidths): T

Sets the thickness of the outline. If this API is not used, there will be no change by default.

**Widget capability**: This API can be used in ArkTS widgets since API version 11.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type                                                        | Mandatory| Description                                                 |
| ------ | ------------------------------------------------------------ | ---- | ----------------------------------------------------- |
| value  | [Dimension](ts-types.md#dimension10)&nbsp;\|&nbsp;[EdgeOutlineWidths](ts-types.md#edgeoutlinewidths11) | Yes  | Outline thickness. Percentage values are not supported.|

**Return value**

| Type  | Description                    |
| ------ | ------------------------ |
| T | Current component.|

## outlineWidth<sup>18+</sup>

outlineWidth(width: Optional\<Dimension | EdgeOutlineWidths>): T

Sets the thickness of the outline. If this API is not used, there will be no change by default. Compared with [outlineWidth](#outlinewidth), this API supports the **undefined** type for the **width** parameter.

**Widget capability**: This API can be used in ArkTS widgets since API version 18.

**Atomic service API**: This API can be used in atomic services since API version 18.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type                                                        | Mandatory| Description                                                        |
| ------ | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| width  | [Optional](ts-universal-attributes-custom-property.md#optionalt12)\<[Dimension](ts-types.md#dimension10)&nbsp;\|&nbsp;[EdgeOutlineWidths](ts-types.md#edgeoutlinewidths11)> | Yes  | Outline thickness. Percentage values are not supported.<br>If **width** is **undefined**, the component reverts to its original style with no outline width.|

**Return value**

| Type  | Description                    |
| ------ | ------------------------ |
| T | Current component.|

## outlineColor

outlineColor(value: ResourceColor | EdgeColors | LocalizedEdgeColors): T

Sets the color of the outline. If this API is not used, the default color black will be applied.

**Widget capability**: This API can be used in ArkTS widgets since API version 11.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type                                                        | Mandatory| Description                                            |
| ------ | ------------------------------------------------------------ | ---- | ------------------------------------------------ |
| value  | [ResourceColor](ts-types.md#resourcecolor)&nbsp;\|&nbsp;[EdgeColors](ts-types.md#edgecolors9)&nbsp;\|&nbsp;[LocalizedEdgeColors](ts-types.md#localizededgecolors12)<sup>12+</sup> | Yes  | Outline color.|

**Return value**

| Type  | Description                    |
| ------ | ------------------------ |
| T | Current component.|

## outlineColor<sup>18+</sup>

outlineColor(color: Optional\<ResourceColor | EdgeColors | LocalizedEdgeColors>): T

Sets the color of the outline. If this API is not used, the default color black will be applied. Compared with [outlineColor](#outlinecolor), this API supports the **undefined** type for the **color** parameter.

**Widget capability**: This API can be used in ArkTS widgets since API version 18.

**Atomic service API**: This API can be used in atomic services since API version 18.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type                                                        | Mandatory| Description                                                        |
| ------ | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| color  | [Optional](ts-universal-attributes-custom-property.md#optionalt12)\<[ResourceColor](ts-types.md#resourcecolor)&nbsp;\|&nbsp;[EdgeColors](ts-types.md#edgecolors9)&nbsp;\|&nbsp;[LocalizedEdgeColors](ts-types.md#localizededgecolors12)> | Yes  | Outline color.<br>If **color** is **undefined**, the component reverts to its original style with the outline color of **Color.Black**.|

**Return value**

| Type  | Description                    |
| ------ | ------------------------ |
| T | Current component.|

## outlineRadius

outlineRadius(value: Dimension | OutlineRadiuses): T

Sets the radius of the outline corners. If this API is not used, there will be no change by default.

**Widget capability**: This API can be used in ArkTS widgets since API version 11.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type                                                        | Mandatory| Description                                                        |
| ------ | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| value  | [Dimension](ts-types.md#dimension10)&nbsp;\|&nbsp;[OutlineRadiuses](ts-types.md#outlineradiuses11) | Yes  | Radius of the outline corners. Percentage values are not supported.<br>Maximum effective value: Component width/2 + outlineWidth or component height/2 + outlineWidth|

**Return value**

| Type  | Description                    |
| ------ | ------------------------ |
| T | Current component.|

## outlineRadius<sup>18+</sup>

outlineRadius(radius: Optional\<Dimension | OutlineRadiuses>): T

Sets the radius of the outline corners. If this API is not used, there will be no change by default. Compared with [outlineRadius](#outlineradius), this API supports the **undefined** type for the **radius** parameter.

**Widget capability**: This API can be used in ArkTS widgets since API version 18.

**Atomic service API**: This API can be used in atomic services since API version 18.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type                                                        | Mandatory| Description                                                        |
| ------ | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| radius | [Optional](ts-universal-attributes-custom-property.md#optionalt12)\<[Dimension](ts-types.md#dimension10)&nbsp;\|&nbsp;[OutlineRadiuses](ts-types.md#outlineradiuses11)> | Yes  | Radius of the outline corners. Percentage values are not supported.<br>Maximum effective value: Component width/2 + outlineWidth or component height/2 + outlineWidth<br>If **radius** is **undefined**, the component reverts to its original style with the outline corner radius of 0.|

**Return value**

| Type  | Description                    |
| ------ | ------------------------ |
| T | Current component.|

## Example

### Example 1: Creating Outlines

This example demonstrates how to create component outlines using [outline](#outline).

```ts
// xxx.ets
@Entry
@Component
struct OutlineExample {
  build() {
    Column() {
      Flex({ justifyContent: FlexAlign.SpaceAround, alignItems: ItemAlign.Center }) {
        // Dashed line
        Text('DASHED')
          .backgroundColor(Color.Pink)
          .outlineStyle(OutlineStyle.DASHED).outlineWidth(5).outlineColor(0xAFEEEE).outlineRadius(10)
          .width(120).height(120).textAlign(TextAlign.Center).fontSize(16)
        // Dotted line
        Text('DOTTED')
          .backgroundColor(Color.Pink)
          .outline({ width: 5, color: 0x317AF7, radius: 10, style: OutlineStyle.DOTTED })
          .width(120).height(120).textAlign(TextAlign.Center).fontSize(16)
      }.width('100%').height(150)

      Text('.outline')
        .backgroundColor(Color.Pink)
        .fontSize(50)
        .width(300)
        .height(300)
        .outline({
          width: { left: 3, right: 6, top: 10, bottom: 15 },
          color: { left: '#e3bbbb', right: Color.Blue, top: Color.Red, bottom: Color.Green },
          radius: { topLeft: 10, topRight: 20, bottomLeft: 40, bottomRight: 80 },
          style: {
            left: OutlineStyle.DOTTED,
            right: OutlineStyle.DOTTED,
            top: OutlineStyle.SOLID,
            bottom: OutlineStyle.DASHED
          }
        }).textAlign(TextAlign.Center)
    }
  }
}
```

![en-us_image_0000001219982706](figures/en-us_image_0000001219982706.png)

### Example 2: Using the LocalizedEdgeColors Type

This example demonstrates how to set the **color** attribute of the [outline](#outline) attribute to the [LocalizedEdgeColors](ts-types.md#localizededgecolors12) type.

```ts
// xxx.ets

@Entry
@Component
struct OutlineExample {
  build() {
    Column() {
      Flex({ justifyContent: FlexAlign.SpaceAround, alignItems: ItemAlign.Center }) {
        // Dashed line
        Text('DASHED')
          .backgroundColor(Color.Pink)
          .outlineStyle(OutlineStyle.DASHED).outlineWidth(5).outlineColor(0xAFEEEE).outlineRadius(10)
          .width(120).height(120).textAlign(TextAlign.Center).fontSize(16)
        // Dotted line
        Text('DOTTED')
          .backgroundColor(Color.Pink)
          .outline({ width: 5, color: 0x317AF7, radius: 10, style: OutlineStyle.DOTTED })
          .width(120).height(120).textAlign(TextAlign.Center).fontSize(16)
      }.width('100%').height(150)

      Text('.outline')
        .backgroundColor(Color.Pink)
        .fontSize(50)
        .width(300)
        .height(300)
        .outline({
          width: { left: 3, right: 6, top: 10, bottom: 15 },
          color: { start: '#e3bbbb', end: Color.Blue, top: Color.Red, bottom: Color.Green },
          radius: { topLeft: 10, topRight: 20, bottomLeft: 40, bottomRight: 80 },
          style: {
            left: OutlineStyle.DOTTED,
            right: OutlineStyle.DOTTED,
            top: OutlineStyle.SOLID,
            bottom: OutlineStyle.DASHED
          }
        }).textAlign(TextAlign.Center)
    }
  }
}
```

The following shows how the example is represented with left-to-right scripts.

![en-us_image_outling_ltr](figures/en-us_image_outling_ltr.png)

The following shows how the example is represented with right-to-left scripts.

![en-us_image_outling_rtl](figures/en-us_image_outling_rtl.png)
