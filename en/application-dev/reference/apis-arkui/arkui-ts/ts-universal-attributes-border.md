# Border Styling
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @zju_ljz-->
<!--Designer: @lanshouren-->
<!--Tester: @liuli0427-->
<!--Adviser: @HelloCrease-->

The border attributes are used to set border styles for components.

>  **NOTE**
>
>  The initial APIs of this module are supported since API version 7. Updates will be marked with a superscript to indicate their earliest API version.
>

## border

border(value: BorderOptions): T

Sets the border.

**Widget capability**: This API can be used in ArkTS widgets since API version 9.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type                                   | Mandatory| Description                                                        |
| ------ | --------------------------------------- | ---- | ------------------------------------------------------------ |
| value  | [BorderOptions](./ts-types.md#borderoptions) | Yes  | Unified border style.<br>**NOTE**<br>The default value is **0**, indicating that no border is displayed.<br>Since API version 9, the parent node's border is displayed above child node content.|

**Return value**

| Type| Description|
| --- | --- |
|  T | Current component.|


>  **NOTE**
>
>  When neither **color** nor **radius** is specified, set [borderColor](#bordercolor) and [borderRadius](#borderradius) after [border](#border) to ensure they take effect.

## borderStyle

borderStyle(value: BorderStyle | EdgeStyles): T

Sets the border style.

**Widget capability**: This API can be used in ArkTS widgets since API version 9.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type                                                        | Mandatory| Description                                              |
| ------ | ------------------------------------------------------------ | ---- | -------------------------------------------------- |
| value  | [BorderStyle](ts-appendix-enums.md#borderstyle) \| [EdgeStyles](./ts-types.md#edgestyles9)<sup>9+</sup> | Yes  | Border style.<br>Default value: **BorderStyle.Solid**|

**Return value**

| Type| Description|
| --- | --- |
|  T | Current component.|

## borderWidth

borderWidth(value: Length | EdgeWidths | LocalizedEdgeWidths): T

Sets the border width.

**Widget capability**: This API can be used in ArkTS widgets since API version 9.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type                                                        | Mandatory| Description                              |
| ------ | ------------------------------------------------------------ | ---- | ---------------------------------- |
| value  | [Length](ts-types.md#length) \| [EdgeWidths](./ts-types.md#edgewidths9)<sup>9+</sup> \| [LocalizedEdgeWidths](./ts-types.md#localizededgewidths12)<sup>12+</sup> | Yes  | Border width. This parameter cannot be set in percentage.|

**Return value**

| Type| Description|
| --- | --- |
|  T | Current component.|

## borderColor

borderColor(value: ResourceColor | EdgeColors | LocalizedEdgeColors): T

Sets the border color.

**Widget capability**: This API can be used in ArkTS widgets since API version 9.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type                                                        | Mandatory| Description                                        |
| ------ | ------------------------------------------------------------ | ---- | -------------------------------------------- |
| value  | [ResourceColor](ts-types.md#resourcecolor) \| [EdgeColors](./ts-types.md#edgecolors9)<sup>9+</sup> \| [LocalizedEdgeColors](./ts-types.md#localizededgecolors12)<sup>12+</sup> | Yes  | Border color.<br>Default value: **Color.Black**|

**Return value**

| Type| Description|
| --- | --- |
|  T | Current component.|

## borderRadius

borderRadius(value: Length | BorderRadiuses | LocalizedBorderRadiuses): T

Sets the border radius. The radius value is restricted by the component size, with the maximum value being half of the component's width or height.

**Widget capability**: This API can be used in ArkTS widgets since API version 9.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type                                                        | Mandatory| Description                                  |
| ------ | ------------------------------------------------------------ | ---- | -------------------------------------- |
| value  | [Length](ts-types.md#length) \| [BorderRadiuses](./ts-types.md#borderradiuses9)<sup>9+</sup> \| [LocalizedBorderRadiuses](./ts-types.md#localizedborderradiuses12)<sup>12+</sup> | Yes  | Border radius of the component. Percentage values relative to component width are supported. The maximum value is half the component's width or height. When combined with the [.clip](./ts-universal-attributes-sharp-clipping.md#clip12) attribute, this setting clips child components to prevent them from extending beyond the component's boundaries.|

**Return value**

| Type| Description|
| --- | --- |
|  T | Current component.|


## Example

### Example 1: Setting Basic Styles

This example shows how to set the border width, color, border radius, and styles such as dotted or dashed lines.

```ts
// xxx.ets
@Entry
@Component
struct BorderExample {
  build() {
    Column() {
      Flex({ justifyContent: FlexAlign.SpaceAround, alignItems: ItemAlign.Center }) {
        // Dashed border
        Text('dashed')
          .borderStyle(BorderStyle.Dashed).borderWidth(5).borderColor(0xAFEEEE).borderRadius(10)
          .width(120).height(120).textAlign(TextAlign.Center).fontSize(16)
        // Dotted border
        Text('dotted')
          .border({ width: 5, color: 0x317AF7, radius: 10, style: BorderStyle.Dotted })
          .width(120).height(120).textAlign(TextAlign.Center).fontSize(16)
      }.width('100%').height(150)

      Text('.border')
        .fontSize(50)
        .width(300)
        .height(300)
        .border({
          width: { left: 3, right: 6, top: 10, bottom: 15 },
          color: { left: '#e3bbbb', right: Color.Blue, top: Color.Red, bottom: Color.Green },
          radius: { topLeft: 10, topRight: 20, bottomLeft: 40, bottomRight: 80 },
          style: {
            left: BorderStyle.Dotted,
            right: BorderStyle.Dotted,
            top: BorderStyle.Solid,
            bottom: BorderStyle.Dashed
          }
        }).textAlign(TextAlign.Center)
    }
  }
}
```

![en-us_image_0000001211898466](figures/en-us_image_0000001211898466.gif)

### Example 2: Setting the Border Width Type and Border Color

In this example, the **width**, **radius**, and **color** properties of the **border** attribute use the **LocalizedEdgeWidths** and **LocalizedEdgeColors** types.

```ts
// xxx.ets
import { LengthMetrics } from '@kit.ArkUI';
@Entry
@Component
struct BorderExample {
  build() {
    Column() {
      Flex({ justifyContent: FlexAlign.SpaceAround, alignItems: ItemAlign.Center }) {
        // Dashed border
        Text('dashed')
          .borderStyle(BorderStyle.Dashed)
          .borderWidth(5)
          .borderColor(0xAFEEEE)
          .borderRadius(10)
          .width(120)
          .height(120)
          .textAlign(TextAlign.Center)
          .fontSize(16)
        // Dotted border
        Text('dotted')
          .border({ width: 5, color: 0x317AF7, radius: 10, style: BorderStyle.Dotted })
          .width(120)
          .height(120)
          .textAlign(TextAlign.Center)
          .fontSize(16)
      }.width('100%').height(150)

      Text('.border')
        .fontSize(50)
        .width(300)
        .height(300)
        .border({
          width: {
            start: LengthMetrics.vp(3),
            end: LengthMetrics.vp(6),
            top: LengthMetrics.vp(10),
            bottom: LengthMetrics.vp(15)
          },
          color: { start: '#e3bbbb', end: Color.Blue, top: Color.Red, bottom: Color.Green },
          radius: {
            topStart: LengthMetrics.vp(10),
            topEnd: LengthMetrics.vp(20),
            bottomStart: LengthMetrics.vp(40),
            bottomEnd: LengthMetrics.vp(80)
          },
          style: {
            left: BorderStyle.Dotted,
            right: BorderStyle.Dotted,
            top: BorderStyle.Solid,
            bottom: BorderStyle.Dashed
          }
        })
        .textAlign(TextAlign.Center)
    }
  }
}
```

The following shows how the example is represented with left-to-right scripts.

![en-us_image_border_ltr](figures/en-us_image_border_ltr.png)

The following shows how the example is represented with right-to-left scripts.

![en-us_image_border_rtl](figures/en-us_image_border_rtl.png)
