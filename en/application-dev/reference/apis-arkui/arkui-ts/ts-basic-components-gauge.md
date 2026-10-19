# Gauge
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @Zhang-Dong-hui-->
<!--Designer: @xiangyuan6-->
<!--Tester: @jiaoaozihao-->
<!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=a9e64d9949bb7122908af3acb8cd44ce378cf9b7 translatedAt=2026-09-03T04:01:25.560Z pushedAt=2026-09-09T03:51:46.697Z -->

The **Gauge** component represents a gauge that displays data in a circular format. It is suitable for scenarios such as displaying task completion progress, performance metrics, and data proportions. It supports various visual configurations, including custom colors, start and end angles, pointer styles, and shadow effects, to intuitively present data status and improve users' understanding of and interaction with data.


>  **NOTE**
>
> - This component is supported since API version 8. Updates will be marked with a superscript to indicate their earliest API version.
>
> - This component supports [WithTheme](./ts-container-with-theme.md) since API version 26.0.0.
>
> - [startAngle](#startangle) and [endAngle](#endangle) only determine the arc path range and do not affect the component size. The smaller the angle difference, the smaller the proportion of the arc within the component, and the larger the blank space between the `min`/`max` markers and the arc.


## Child Components

This component can contain one child component.

> **NOTE**
>
> - Supported child component types: built-in and custom components, including [if/else](../../../ui/rendering-control/arkts-rendering-control-ifelse.md) but excluding [ForEach](../../../ui/rendering-control/arkts-rendering-control-foreach.md) and [LazyForEach](../../../ui/rendering-control/arkts-rendering-control-lazyforeach.md).
>
> - You are advised to use the **Text** component to build the current value and auxiliary text.
>
> - If the width and height of the child component are in percentage, the reference range is the rectangle that has the outer ring as its inscribed circle.


## APIs

Gauge(options: GaugeOptions)

Creates a gauge.

**Widget capability**: This API can be used in ArkTS widgets since API version 9.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| options |  [GaugeOptions](#gaugeoptions18)| Yes| Settings of the gauge.|

## GaugeOptions<sup>18+</sup>

Provides gauge options.

**Widget capability**: This API can be used in ArkTS widgets since API version 18.

**Atomic service API**: This API can be used in atomic services since API version 18.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name| Type| Read-Only| Optional| Description|
| -------- | -------- | -------- | -------- | -------- |
| value<sup>8+</sup> | number | No | No | Current value of the gauge, that is, the position to which the indicator points in the gauge. It is used as the initial value of the gauge when it is created.<br>Default value: **0**<br>**Widget capability:** This API can be used in ArkTS widgets since API version 9.<br>**Atomic service API:** This API can be used in atomic services since API version 11.<br>**NOTE**<br>If the value is not within the range defined by the **min** and **max** parameters, the value of **min** is used. |
| min<sup>8+</sup> | number | No | Yes | Minimum value of the current data segment.<br>Default value: **0**<br>**Widget capability:** This API can be used in ArkTS widgets since API version 9.<br>**Atomic service API:** This API can be used in atomic services since API version 11.<br>**NOTE**<br>If not passed, the default value is **0**.<br>If the value of **min** is greater than that of **max**, **min** is set to **0** and **max** is set to **100**.<br>Both **max** and **min** support negative numbers. |
| max<sup>8+</sup> | number | No | Yes | Maximum value of the current data segment.<br>Default value: **100**<br>**Widget capability:** This API can be used in ArkTS widgets since API version 9.<br>**Atomic service API:** This API can be used in atomic services since API version 11.<br>**NOTE**<br>If not passed, the default value is **100**.<br>If the value of **min** is greater than that of **max**, **min** is set to **0** and **max** is set to **100**.<br>Both **max** and **min** support negative numbers. |

## Attributes

In addition to the [universal attributes](ts-component-general-attributes.md), the following attributes are supported.

### value

value(value: number)

Sets the value of the gauge.

**Widget capability**: This API can be used in ArkTS widgets since API version 9.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type  | Mandatory| Description                                                        |
| ------ | ------ | ---- | ------------------------------------------------------------ |
| value  | number | Yes   | Value of the gauge. It can be dynamically changed.<br>**NOTE** <br>If the value is not within the range defined by **min** and **max**, the value of **min** is used as the actual value.<br>Default value: **0** |

### startAngle

startAngle(angle: number)

Sets the start angle of the gauge. If the difference between the start angle and the end angle is too small, an abnormal image will be drawn. Use proper start and end angles. It is recommended to use a single-color ring to adjust the data value by modifying the `value` parameter of **Gauge**. You can use the timer `setTimeout` to delay the loading of the value.

**Widget capability**: This API can be used in ArkTS widgets since API version 9.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type  | Mandatory| Description                                                        |
| ------ | ------ | ---- | ------------------------------------------------------------ |
| angle  | number | Yes   | Start angle of the gauge. The 0 o'clock is defined as 0 degrees. Clockwise rotation represents positive angles, and counterclockwise rotation represents negative angles. Values exceeding 360 degrees are equivalent to the remainder after division by 360 degrees.<br>Default value: **0**<br>Unit: deg<br>Drawing from the start position to the end position is performed only in the clockwise direction.<br>If the difference between the start angle and the end angle is too small, an abnormal image may be drawn. Use proper start and end angles. |

### endAngle

endAngle(angle: number)

Sets the end angle of the gauge. Ensure an appropriate difference between the start angle and end angle. If this difference is too small, the drawn chart may be abnormal. You are advised to use a monochrome ring to set the **value** attribute of the **Gauge**. You can also use **setTimeout** to delay value loading.

**Widget capability**: This API can be used in ArkTS widgets since API version 9.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type  | Mandatory| Description                                                        |
| ------ | ------ | ---- | ------------------------------------------------------------ |
| angle  | number | Yes   | End angle of the gauge. The 0 o'clock is defined as 0 degrees. Clockwise rotation represents positive angles, and counterclockwise rotation represents negative angles. Values exceeding 360 degrees are equivalent to the remainder after division by 360 degrees.<br>Default value: **360**<br>Unit: deg<br>Drawing from the start position to the end position is performed only in the clockwise direction.<br>If the difference between the start angle and end angle is too small, an abnormal image may be drawn. Use proper start and end angles. |

### colors

colors(colors: ResourceColor | LinearGradient | Array<[ResourceColor | LinearGradient, number]>)

Sets the colors of the gauge.

Since API version 11, this API follows the following rules:

If the data type is [ResourceColor](ts-types.md#resourcecolor), the ring is of the monochrome type.

If the data type is [LinearGradient](ts-basic-components-datapanel.md#lineargradient10), the ring is of the gradient type.

If the parameter type is Array, the ring is of the segmented gradient type. The first parameter indicates the color value or gradient object (**LinearGradient**). If it is set to a non-color value, the color of 0xFFE84026 is used. The second parameter indicates the color weight. If it is set to a negative number or a non-numeric value, the color weight is 0.

A ring of the gradient type contains a maximum of nine color segments. If there are more than nine segments, the excess is not displayed.

**Widget capability**: This API can be used in ArkTS widgets since API version 9.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type                                                        | Mandatory| Description                                                        |
| ------ | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| colors | [ResourceColor](ts-types.md#resourcecolor)&nbsp;\|&nbsp;[LinearGradient](ts-basic-components-datapanel.md#lineargradient10)&nbsp;\|&nbsp;Array&lt;[[ResourceColor](ts-types.md#resourcecolor)&nbsp;\|&nbsp;[LinearGradient](ts-basic-components-datapanel.md#lineargradient10)&nbsp;\,&nbsp;number]&gt; | Yes | Colors of the gauge. You can set colors for individual segments.<br>Default value since API version 9: **Color.Black**<br>Default value since API version 11:<br>If no color is passed or the array is empty, the ring type and colors cannot be determined, and the ring is a gradient ring with the colors "0xFF64BB5C", "0xFFF7CE00", and "0xFFE84026".<br>If a color is passed but the color value is invalid, the color "0xFFE84026" is used.<br>If the weight of a color is 0, the color is not displayed in the ring. If the weights of all colors are 0, the ring is not displayed.<br>Since API version 10, the **Array&lt;ResourceColor, number&gt;** type is supported.<br>Since API version 11, the **LinearGradient** and **Array&lt;LinearGradient, number&gt;** types are supported. |

### strokeWidth

strokeWidth(length: Length)

Sets the stroke width of the gauge.

**Widget capability**: This API can be used in ArkTS widgets since API version 9.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type                        | Mandatory| Description                                                        |
| ------ | ---------------------------- | ---- | ------------------------------------------------------------ |
| length | [Length](ts-types.md#length) | Yes | Stroke width of the gauge.<br>Default value: **4**<br>Unit: vp<br>**NOTE** <br>If the value is less than or equal to 0, the default value is used.<br>The maximum stroke width is the radius of the ring. If the value exceeds the maximum, the maximum value is used.<br>Percentage is not supported. |

### description<sup>11+</sup>

description(value: CustomBuilder)

Sets the description of the gauge.

**Widget capability**: This API can be used in ArkTS widgets since API version 23.

**Atomic service API**: This API can be used in atomic services since API version 12.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type                                       | Mandatory| Description                                                        |
| ------ | ------------------------------------------- | ---- | ------------------------------------------------------------ |
| value  | [CustomBuilder](ts-types.md#custombuilder8) | Yes   | Description.<br>**NOTE** <br>You need to customize the content – text or images recommended – in **@Builder**.<br>If the width and height of the custom content are in percentage, the reference range is a rectangle that is 44.4% of the diameter of the ring horizontally and 25.4% vertically (for images, it is 28.6% both horizontally and vertically), positioned 0 vp away from the bottom of the ring and centered horizontally.<br>If this parameter is set to null, no description is displayed.<br>If this parameter is not set, what's displayed is subject to the maximum and minimum value settings.<br>If either or both of the maximum and minimum values are set, they are displayed.<br>If neither maximum nor minimum values are set, no description is displayed.<br>The maximum and minimum values are displayed at the bottom of the ring and cannot be relocated. They may be blocked by the ring if the ring's start and end angles are not set properly. |

### trackShadow<sup>11+</sup>

trackShadow(value: GaugeShadowOptions)

Sets the shadow style of the gauge.

**Widget capability**: This API can be used in ArkTS widgets since API version 23.

**Atomic service API**: This API can be used in atomic services since API version 12.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type                                               | Mandatory| Description                                                        |
| ------ | --------------------------------------------------- | ---- | ------------------------------------------------------------ |
| value  | [GaugeShadowOptions](#gaugeshadowoptions11) | Yes   | Shadow effect. You can specify the blur radius and the offsets along the X-axis and Y-axis.<br>**NOTE** <br>The shadow color is the same as the ring color.<br>If this parameter is set to **null**, the shadow effect is disabled. |

### indicator<sup>11+</sup>

indicator(value: GaugeIndicatorOptions)

Sets the indicator style of the gauge.

**Widget capability**: This API can be used in ArkTS widgets since API version 23.

**Atomic service API**: This API can be used in atomic services since API version 12.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type                                                     | Mandatory| Description                                                 |
| ------ | --------------------------------------------------------- | ---- | ----------------------------------------------------- |
| value | [GaugeIndicatorOptions](#gaugeindicatoroptions11) | Yes | Indicator style.<br>**NOTE**<br>If this parameter is set to **null**, no indicator is displayed. |

### privacySensitive<sup>12+</sup>

privacySensitive(isPrivacySensitiveMode: Optional\<boolean\>)

Sets whether to enable privacy mode.

>**NOTE**
>
> This API can be called within [attributeModifier](ts-universal-attributes-attribute-modifier.md#attributemodifier) since API version 20.

**Widget capability**: This API can be used in ArkTS widgets since API version 12.

**Atomic service API**: This API can be used in atomic services since API version 12.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type                                                     | Mandatory| Description                                                 |
| ------ | --------------------------------------------------------- | ---- | ----------------------------------------------------- |
| isPrivacySensitiveMode  | Optional\<boolean\> | Yes   | Whether to enable privacy mode. In privacy mode, the gauge indicator points to **0**, the maximum and minimum values are masked, and the scale range is displayed in gray or the background color. The value **true** means to enable privacy mode, and **false** means the opposite.<br>**NOTE** <br>If this parameter is set to **null**, privacy mode is disabled.<!--Del--><br> For widgets, this property must be used with [FormComponent](./ts-basic-components-formcomponent-sys.md) and the [obscured](./ts-universal-attributes-obscured.md) attribute to display privacy masking effects.<!--DelEnd--> |

### contentModifier<sup>12+</sup>

contentModifier(modifier: ContentModifier\<GaugeConfiguration\>)

Creates a content modifier.

**Atomic service API**: This API can be used in atomic services since API version 12.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type                                         | Mandatory| Description                                            |
| ------ | --------------------------------------------- | ---- | ------------------------------------------------ |
| modifier  | [ContentModifier](./ts-universal-attributes-content-modifier.md#contentmodifiert)\<[GaugeConfiguration](#gaugeconfiguration12)> | Yes   | Content modifier to apply to the **Gauge** component.<br>**modifier**: content modifier. You need to customize a class to implement the **ContentModifier** API. |

## GaugeShadowOptions<sup>11+</sup>

Inherits from [MultiShadowOptions](ts-information-display-common.md#multishadowoptions) and has all attributes of **MultiShadowOptions**.

**Widget capability**: This API can be used in ArkTS widgets since API version 23.

**Atomic service API**: This API can be used in atomic services since API version 12.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

## GaugeIndicatorOptions<sup>11+</sup>

Provides gauge indicator options.

**Widget capability**: This API can be used in ArkTS widgets since API version 23.

**Atomic service API**: This API can be used in atomic services since API version 12.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name         | Type| Read-Only| Optional| Description|
| ------------- | ------- | ---- | -------- | -------- |
| icon | [ResourceStr](ts-types.md#resourcestr) | No | Yes | Image path of the icon.<br>**NOTE** <br>If this parameter is not set, the default style of the system is used, which is a triangle indicator.<br>Only icons in SVG format are supported. If an icon in another format is used, the default triangle indicator is used. |
| space | [Dimension](ts-types.md#dimension10) | No | Yes | Distance between the indicator and the outer edge of the ring.<br>Default value: **8**<br>Unit: vp<br>**NOTE** <br>Percentage is not supported.<br>For the default triangle indicator, the distance is the spacing between the black triangle and the outer edge of the ring.<br>If the value is less than 0, the default value is used.<br>If the value is greater than the ring radius, the default value is used.|

## GaugeConfiguration<sup>12+</sup>

You need a custom class to implement the **ContentModifier** API. Inherits from [CommonConfiguration](ts-universal-attributes-content-modifier.md#commonconfigurationt).

**Atomic service API**: This API can be used in atomic services since API version 12.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name         | Type| Read-Only| Optional| Description|
| ------------- | ------- | ---- | -------- | -------- |
| value | number | No| No| Current value.|
| min | number | No| No| Minimum value of the current data segment.|
| max | number | No| No| Maximum value of the current data segment.|


## Example
### Example 1: Implementing a Multi-color Gauge

This example demonstrates how to implement a multi-color gauge using the [colors](#colors) attribute.

```ts
@Entry
@Component
struct Gauge1 {
  @Builder
  descriptionBuilder() {
    Text('Description')
      .maxFontSize('30sp')
      .minFontSize('10.0vp')
      .fontColor('#fffa2a2d')
      .fontWeight(FontWeight.Medium)
      .width('100%')
      .height('100%')
      .textAlign(TextAlign.Center)
  }

  build() {
    Column() {
      Gauge({ value: 50, min: 1, max: 100 }) {
        Column() {
          Text('50')
            .fontWeight(FontWeight.Medium)
            .width('62%')
            .fontColor('#ff182431')
            .maxFontSize('60.0vp')
            .minFontSize('30.0vp')
            .textAlign(TextAlign.Center)
            .margin({ top: '35%' })
            .textOverflow({ overflow: TextOverflow.Ellipsis })
            .maxLines(1)
          Text('Auxiliary text')
            .maxFontSize('16.0fp')
            .minFontSize('10.0vp')
            .fontColor($r('sys.color.ohos_id_color_text_secondary'))
            .fontWeight(FontWeight.Regular)
            .width('67.4%')
            .height('9.5%')
            .textAlign(TextAlign.Center)
        }.width('100%').height('100%')
      }
      .value(50)
      .startAngle(210)
      .endAngle(150)
      .colors([[new LinearGradient([{ color: '#deb6fb', offset: 0 }, { color: '#ac49f5', offset: 1 }]), 9],
        [new LinearGradient([{ color: '#bbb7fc', offset: 0 }, { color: '#564af7', offset: 1 }]), 8],
        [new LinearGradient([{ color: '#f5b5c2', offset: 0 }, { color: '#e64566', offset: 1 }]), 7],
        [new LinearGradient([{ color: '#f8c5a6', offset: 0 }, { color: '#ed6f21', offset: 1 }]), 6],
        [new LinearGradient([{ color: '#fceb99', offset: 0 }, { color: '#f7ce00', offset: 1 }]), 5],
        [new LinearGradient([{ color: '#dbefa5', offset: 0 }, { color: '#a5d61d', offset: 1 }]), 4],
        [new LinearGradient([{ color: '#c1e4be', offset: 0 }, { color: '#64bb5c', offset: 1 }]), 3],
        [new LinearGradient([{ color: '#c0ece5', offset: 0 }, { color: '#61cfbe', offset: 1 }]), 2],
        [new LinearGradient([{ color: '#b5e0f4', offset: 0 }, { color: '#46b1e3', offset: 1 }]), 1]])
      .width('80%')
      .height('80%')
      .strokeWidth(18)
      .trackShadow({ radius: 7, offsetX: 7, offsetY: 7 })
      .description(this.descriptionBuilder)
      .padding(18)
    }.margin({ top: 40 }).width('100%').height('100%')
  }
}
```
![gauge](figures/gauge-image1.png)

### Example 2: Implementing a Single-Color Gauge

This example demonstrates how to implement a single-color gauge using the [colors](#colors) attribute.

```ts
@Entry
@Component
struct Gauge2 {
  @Builder
  descriptionBuilderImage() {
    Image($r('sys.media.ohos_ic_public_clock')).width(72).height(72)
  }

  build() {
    Column() {
      Gauge({ value: 50, min: 1, max: 100 }) {
        Column() {
          Text('50')
            .fontWeight(FontWeight.Medium)
            .width('62%')
            .fontColor('#ff182431')
            .maxFontSize('60.0vp')
            .minFontSize('30.0vp')
            .textAlign(TextAlign.Center)
            .margin({ top: '35%' })
            .textOverflow({ overflow: TextOverflow.Ellipsis })
            .maxLines(1)
        }.width('100%').height('100%')
      }
      .startAngle(210)
      .endAngle(150)
      .colors('#cca5d61d')
      .width('80%')
      .height('80%')
      .strokeWidth(18)
      .description(this.descriptionBuilderImage)
      .padding(18)
    }.margin({ top: 40 }).width('100%').height('100%')
  }
}
```
![gauge](figures/gauge-image2.png)

### Example 3: Configuring a Custom Description Area

This example illustrates how to configure a custom description area using the [description](#description11) attribute.

```ts
  @Entry
  @Component
  struct Gauge3 {
    @Builder
    descriptionBuilder() {
      Text('Description')
        .maxFontSize('30sp')
        .minFontSize('10.0vp')
        .fontColor('#fffa2a2d')
        .fontWeight(FontWeight.Medium)
        .width('100%')
        .height('100%')
        .textAlign(TextAlign.Center)
    }
  
    build() {
      Column() {
        Column() {
          Gauge({ value: 50, min: 1, max: 100 }) {
            Column() {
              Text('50')
                .fontWeight(FontWeight.Medium)
                .width('62%')
                .fontColor('#ff182431')
                .maxFontSize('60.0vp')
                .minFontSize('30.0vp')
                .textAlign(TextAlign.Center)
                .margin({ top: '35%' })
                .textOverflow({ overflow: TextOverflow.Ellipsis })
                .maxLines(1)
            }.width('100%').height('100%')
          }
          .startAngle(210)
          .endAngle(150)
          .colors([[new LinearGradient([{ color: '#deb6fb', offset: 0 }, { color: '#ac49f5', offset: 1 }]), 9],
            [new LinearGradient([{ color: '#bbb7fc', offset: 0 }, { color: '#564af7', offset: 1 }]), 8],
            [new LinearGradient([{ color: '#f5b5c2', offset: 0 }, { color: '#e64566', offset: 1 }]), 7],
            [new LinearGradient([{ color: '#f8c5a6', offset: 0 }, { color: '#ed6f21', offset: 1 }]), 6],
            [new LinearGradient([{ color: '#fceb99', offset: 0 }, { color: '#f7ce00', offset: 1 }]), 5],
            [new LinearGradient([{ color: '#dbefa5', offset: 0 }, { color: '#a5d61d', offset: 1 }]), 4],
            [new LinearGradient([{ color: '#c1e4be', offset: 0 }, { color: '#64bb5c', offset: 1 }]), 3],
            [new LinearGradient([{ color: '#c0ece5', offset: 0 }, { color: '#61cfbe', offset: 1 }]), 2],
            [new LinearGradient([{ color: '#b5e0f4', offset: 0 }, { color: '#46b1e3', offset: 1 }]), 1]])
          .width('80%')
          .height('80%')
          .strokeWidth(18)
          .description(this.descriptionBuilder)
          .trackShadow({ radius: 7, offsetX: 7, offsetY: 7 })
          .padding(18)
        }.margin({ top: 40 }).width('100%').height('100%')
      }
    }
  }
```
![gauge](figures/gauge-image3.png)

### Example 4: Configuring the Auxiliary Area

This example demonstrates how to configure the auxiliary area by setting child components.

```ts
@Entry
@Component
struct Gauge4 {
  build() {
    Column() {
      Gauge({ value: 50, min: 1, max: 100 }) {
        Column() {
          Text('50')
            .maxFontSize('72.0vp')
            .minFontSize('10.0vp')
            .fontColor('#ff182431')
            .width('40%')
            .textAlign(TextAlign.Center)
            .margin({ top: '35%' })
            .textOverflow({ overflow: TextOverflow.Ellipsis })
            .maxLines(1)
          Text('Auxiliary text')
            .maxFontSize('30.0vp')
            .minFontSize('18.0vp')
            .fontWeight(FontWeight.Medium)
            .fontColor($r('sys.color.ohos_id_color_text_secondary'))
            .width('62%')
            .height('15.9%')
            .textAlign(TextAlign.Center)
        }.width('100%').height('100%')
      }
      .startAngle(210)
      .endAngle(150)
      .colors([[new LinearGradient([{ color: '#deb6fb', offset: 0 }, { color: '#ac49f5', offset: 1 }]), 9],
        [new LinearGradient([{ color: '#bbb7fc', offset: 0 }, { color: '#564af7', offset: 1 }]), 8],
        [new LinearGradient([{ color: '#f5b5c2', offset: 0 }, { color: '#e64566', offset: 1 }]), 7],
        [new LinearGradient([{ color: '#f8c5a6', offset: 0 }, { color: '#ed6f21', offset: 1 }]), 6],
        [new LinearGradient([{ color: '#fceb99', offset: 0 }, { color: '#f7ce00', offset: 1 }]), 5],
        [new LinearGradient([{ color: '#dbefa5', offset: 0 }, { color: '#a5d61d', offset: 1 }]), 4],
        [new LinearGradient([{ color: '#c1e4be', offset: 0 }, { color: '#64bb5c', offset: 1 }]), 3],
        [new LinearGradient([{ color: '#c0ece5', offset: 0 }, { color: '#61cfbe', offset: 1 }]), 2],
        [new LinearGradient([{ color: '#b5e0f4', offset: 0 }, { color: '#46b1e3', offset: 1 }]), 1]])
      .width('80%')
      .height('80%')
      .strokeWidth(18)
      .description(null)
      .trackShadow({ radius: 7, offsetX: 7, offsetY: 7 })
      .padding(18)
    }.margin({ top: 40 }).width('100%').height('100%')
  }
}
```
![gauge](figures/gauge-image4.png)

### Example 5: Setting the Minimum and Maximum Values

This example shows how to set the minimum and maximum values of the gauge by configuring **min** and **max** in [GaugeOptions](#gaugeoptions18).

```ts
@Entry
@Component
struct Gauge5 {
  build() {
    Column() {
      Gauge({ value: 50, min: 1, max: 100 }) {
        Column() {
          Text('50')
            .maxFontSize('80sp')
            .minFontSize('60.0vp')
            .fontWeight(FontWeight.Medium)
            .fontColor('#ff182431')
            .width('40%')
            .height('30%')
            .textAlign(TextAlign.Center)
            .margin({ top: '22.2%' })
            .textOverflow({ overflow: TextOverflow.Ellipsis })
            .maxLines(1)
        }.width('100%').height('100%')
      }
      .startAngle(225)
      .endAngle(135)
      .colors(new LinearGradient([{ color: '#e84026', offset: 0 },
        { color: '#f7ce00', offset: 0.6 },
        { color: '#64bb5c', offset: 1 }]))
      .width('80%')
      .height('80%')
      .strokeWidth(18)
      .trackShadow({ radius: 7, offsetX: 7, offsetY: 7 })
      .padding(18)
    }.margin({ top: 40 }).width('100%').height('100%')
  }
}
```
![gauge](figures/gauge-image5.png)

### Example 6: Setting the Indicator

This example illustrates how to set the indicator of the gauge using the [indicator](#indicator11) attribute.

```ts
@Entry
@Component
struct Gauge6 {
  build() {
    Column() {
      Gauge({ value: 50, min: 1, max: 100 }) {
        Column() {
          Text('50')
            .maxFontSize('60sp')
            .minFontSize('30.0vp')
            .fontWeight(FontWeight.Medium)
            .fontColor('#ff182431')
            .width('62%')
            .textAlign(TextAlign.Center)
            .margin({ top: '35%' })
            .textOverflow({ overflow: TextOverflow.Ellipsis })
            .maxLines(1)
          Text('Auxiliary text')
            .maxFontSize('16sp')
            .minFontSize('10.0vp')
            .fontColor($r('sys.color.ohos_id_color_text_secondary'))
            .fontWeight(FontWeight.Regular)
            .width('67.4%')
            .height('9.5%')
            .textAlign(TextAlign.Center)
        }.width('100%').height('100%')
      }
      .startAngle(225)
      .endAngle(135)
      .colors(Color.Red)
      .width('80%')
      .height('80%')
      .indicator(null)
      .strokeWidth(18)
      .trackShadow({ radius: 7, offsetX: 7, offsetY: 7 })
      .padding(18)
    }.margin({ top: 40 }).width('100%').height('100%')
  }
}
```
![gauge](figures/gauge-image6.png)

### Example 7: Setting the Start and End Angles

This example demonstrates how to set the start and end angles of the gauge using the [startAngle](#startangle) and [endAngle](#endangle) attributes.

```ts
@Entry
@Component
struct Gauge7 {
  build() {
    Column() {
      Gauge({ value: 50, min: 1, max: 100 }) {
        Column() {
          Text('50')
            .maxFontSize('60sp')
            .minFontSize('30.0vp')
            .fontWeight(FontWeight.Medium)
            .fontColor('#ff182431')
            .width('62%')
            .textAlign(TextAlign.Center)
            .margin({ top: '35%' })
            .textOverflow({ overflow: TextOverflow.Ellipsis })
            .maxLines(1)
        }.width('100%').height('100%')
      }
      .startAngle(225)
      .endAngle(135)
      .colors(Color.Red)
      .width('80%')
      .height('80%')
      .indicator(null)
      .strokeWidth(18)
      .trackShadow({ radius: 7, offsetX: 7, offsetY: 7 })
      .padding(18)
    }.margin({ top: 40 }).width('100%').height('100%')
  }
}
```
![gauge](figures/gauge-image7.png)



### Example 8: Setting the Custom Content Area

This example shows how to customize the content area of the gauge using the [contentModifier](#contentmodifier12) attribute.

```ts
// xxx.ets
// The example implements the customization of the gauge's content area using a Builder, utilizing a circular chart, buttons, and text boxes. When the increase button is clicked, the indicator will shift to the right; conversely, when the decrease button is clicked, the indicator will shift to the left.
@Builder
function buildGauge(config: GaugeConfiguration) {
  Column({ space: 30 }) {
    Row() {
      Text('[ContentModifier] value: ' + JSON.stringify((config.contentModifier as MyGaugeStyle).value) +
        '  min: ' + JSON.stringify((config.contentModifier as MyGaugeStyle).min) +
        '  max: ' + JSON.stringify((config.contentModifier as MyGaugeStyle).max))
        .fontSize(12)
    }

    Text('[Config] value: ' + config.value + '  min: ' + config.min + '  max: ' + config.max).fontSize(12)
    Gauge({
      value: config.value,
      min: config.min,
      max: config.max
    }).width('50%')
  }
  .width('100%')
  .padding(20)
  .margin({ top: 5 })
  .alignItems(HorizontalAlign.Center)
}

class MyGaugeStyle implements ContentModifier<GaugeConfiguration> {
  value: number = 0
  min: number = 0
  max: number = 0

  constructor(value: number, min: number, max: number) {
    this.value = value;
    this.min = min;
    this.max = max;
  }

  applyContent(): WrappedBuilder<[GaugeConfiguration]> {
    return wrapBuilder(buildGauge);
  }
}

@Entry
@Component
struct RefreshExample {
  @State gaugeValue: number = 20
  @State gaugeMin: number = 0
  @State gaugeMax: number = 100

  build() {
    Column({ space: 20 }) {
      Gauge({
        value: this.gaugeValue,
        min: this.gaugeMin,
        max: this.gaugeMax
      })
        .contentModifier(new MyGaugeStyle(30, 10, 100))

      Column({ space: 20 }) {
        Row({ space: 20 }) {
          Button('Increase').onClick(() => {
            if (this.gaugeValue < this.gaugeMax) {
              this.gaugeValue += 1;
            }
          })
          Button('Decrease').onClick(() => {
            if (this.gaugeValue > this.gaugeMin) {
              this.gaugeValue -= 1;
            }
          })
        }
      }.width('100%')
    }.width('100%').margin({ top: 5 })
  }
}
```
![gauge](figures/gauge_builder.gif)


### Example 9: Securing Sensitive Information

This example shows how to call the [privacySensitive](#privacysensitive12) API. The actual privacy hiding effect requires support from the widget framework.

```ts
@Entry
@Component
struct GaugeExample {
  build() {
    Scroll() {
      Column({ space: 15 }) {
        Row() {
          Gauge({ value: 60, min: 20, max: 100 })
            .startAngle(225)
            .endAngle(135)
            .colors(Color.Red)
            .width('80%')
            .height('80%')
            .strokeWidth(18)
            .trackShadow({ radius: 7, offsetX: 7, offsetY: 7 })
            .padding(18)
            .privacySensitive(true)
        }
      }
    }
  }
}
```
![gauge](figures/gauge-privacysensitive.gif)

### Example 10: Implementing a Custom Indicator

This example demonstrates how to implement a custom indicator using [indicator](#indicator11). You can import an SVG image to replace the default indicator.

```ts
@Entry
@Component
struct Gauge2 {
  build() {
    Column() {
      Gauge({ value: 50, min: 1, max: 100 })
        // Replace $r('app.media.indicator') with the image resource file you use.
        .indicator({ space: 10, icon: $r('app.media.indicator') })
        .startAngle(210)
        .endAngle(150)
        .colors('#cca5d61d')
        .width('80%')
        .height('80%')
        .strokeWidth(18)
        .padding(18)
    }.margin({ top: 40 }).width('100%').height('100%')
  }
}
```
```xml
<svg width='200px' height='200px'>
    <path d='M 10,30 A 20,20 0,0,1 50,30 A 20,20 0,0,1 90,30 Q 90,60 50,90 Q 10,60 10,30 z'
          stroke='black' stroke-width='3' fill='white'>
    </path>
</svg>
```
![gauge](figures/gauge-image8.png)
