# DataPanel
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @Zhang-Dong-hui-->
<!--Designer: @xiangyuan6-->
<!--Tester: @jiaoaozihao-->
<!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=8aa8522c1582655206875d9c89c21656113a2dda translatedAt=2026-09-03T03:49:11.036Z -->

The **DataPanel** component is used to display the proportions of multiple data items in a proportion chart. It supports two display types: circular and linear. You can customize visual effects such as colors, shadows, and track backgrounds. It is applicable to data visualization scenarios such as storage capacity, task progress, and resource proportions, helping users intuitively understand data distribution.

>  **NOTE**
>
> - This component is supported since API version 7. Updates will be marked with a superscript to indicate their earliest API version.
>
> - This component supports [WithTheme](./ts-container-with-theme.md) since API version 26.0.0.


## Child Components

Not supported


## APIs

DataPanel(options: DataPanelOptions)

Creates a data panel component.

**Widget capability**: This API can be used in ArkTS widgets since API version 9.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| options | [DataPanelOptions](#datapaneloptions) | Yes | Data panel configuration options, used to set the data value list, maximum value, and type of the data panel. |

## DataPanelOptions

Defines data panel configuration options.

**Widget capability**: This API can be used in ArkTS widgets since API version 9.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name           | Type  | Read-Only| Optional| Description|
| ----------------- | -------- | ----- | -------- | -------- |
| values            | number[]   | No   | No  | Data value list. The array length ranges from 0 to 9. If more than 9 data values are provided, only the first 9 are used. If a data value is less than 0, it is set to 0. |
| max               | number     | No   | Yes   |   - When max is greater than 0, it indicates the maximum data value.<br>- When max is less than or equal to 0, max equals the sum of all values in the data value list, and the data is displayed proportionally.<br>Default Value: 100.|
| type<sup>8+</sup> | [DataPanelType](#datapaneltype8) | No | Yes | Type of the data panel (dynamic modification is not supported).<br>Optional values: DataPanelType.Line (linear data panel, suitable for displaying comparisons of multiple data segments in limited space) and DataPanelType.Circle (circular data panel, suitable for intuitively displaying data proportion relationships).<br>If not passed, the default value is DataPanelType.Circle.|


## DataPanelType<sup>8+</sup>

Enumerates data panel types.

**Widget capability**: This API can be used in ArkTS widgets since API version 9.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name| Value| Description|
| -------| - | ------------ |
| Line   | 0 | Linear data panel. |
| Circle | 4 | Circle data panel.|


## Attributes

In addition to the [universal attributes](ts-component-general-attributes.md), the following attributes are supported.

### closeEffect

closeEffect(value: boolean)

Sets whether to disable the rotation animation effect and shadow effect of the data proportion chart. If the [trackShadow](#trackshadow10) attribute is not set, this attribute controls the shadow effect. When **closeEffect** is **false** (shadow enabled), the default shadow effect is used. If the **trackShadow** attribute is set, the shadow effect is controlled by the value of the **trackShadow** attribute.

**Widget capability**: This API can be used in ArkTS widgets since API version 9.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type   | Mandatory| Description                                                  |
| ------ | ------- | ---- | ------------------------------------------------------ |
| value  | boolean | Yes   | Whether to disable the rotation animation effect and shadow effect of the data proportion chart.<br>Default value: false, which means the animation effect and shadow effect are enabled; true means the animation effect and shadow effect are disabled. |

### valueColors<sup>10+</sup>

valueColors(value: Array<ResourceColor | LinearGradient>)

Sets an array of data segment colors.

**Atomic service API**: This API can be used in atomic services since API version 11.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type                                                        | Mandatory| Description                                                       |
| ------ | ------------------------------------------------------------ | ---- | ----------------------------------------------------------- |
| value  | Array<[ResourceColor](ts-types.md#resourcecolor)&nbsp;\|&nbsp;[LinearGradient](#lineargradient10)> | Yes   | Color of each data segment. ResourceColor indicates a solid color, and LinearGradient indicates a gradient color. The default value is a gradient color. The default colors of the nine data segments are: [{ color: '#F7CE00', offset: 0 }, { color: '#F99B11', offset: 1 }], [{ color: '#F76223', offset: 0 }, { color: '#F2400A', offset: 1 }], [{ color: '#F772AC', offset: 0 }, { color: '#E65392', offset: 1 }], [{ color: '#A575EB', offset: 0 }, { color: '#A12DF7', offset: 1 }], [{ color: '#7B79F7', offset: 0 }, { color: '#4B48F7', offset: 1 }], [{ color: '#4B8AF3', offset: 0 }, { color: '#007DFF', offset: 1 }], [{ color: '#73C1E6', offset: 0 }, { color: '#4FB4E3', offset: 1 }], [{ color: '#A5D61D', offset: 0 }, { color: '#69D14F', offset: 1 }], [{ color: '#A2A2B0', offset: 0 }, { color: '#8E8E93', offset: 1 }].<br>**Note:**<br>If the number of colors set is less than the number of data segments, the remaining data segments automatically match the colors in the corresponding order in the default color list. If the number of colors set is greater than the number of data segments, the number of colors displayed is the same as the number of data segments, and the extra colors are ignored. |

### trackBackgroundColor<sup>10+</sup>

trackBackgroundColor(value: ResourceColor)

Sets the background color.

**Atomic service API**: This API can be used in atomic services since API version 11.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type                                      | Mandatory| Description                                                        |
| ------ | ------------------------------------------ | ---- | ------------------------------------------------------------ |
| value  | [ResourceColor](ts-types.md#resourcecolor) | Yes   | Track background color.<br>Default value: '#08182431', in hexadecimal ARGB format, where the first two digits indicate the transparency. |

### strokeWidth<sup>10+</sup>

strokeWidth(value: Length)

Sets the stroke width of the border. This attribute does not take effect when the data panel type is **DataPanelType.Line**.

**Atomic service API**: This API can be used in atomic services since API version 11.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type                        | Mandatory| Description                                                        |
| ------ | ---------------------------- | ---- | ------------------------------------------------------------ |
| value | [Length](ts-types.md#length) | Yes | Thickness of the ring.<br>Default value: 24<br>Unit: vp<br>When a string parameter is set, if no unit is specified, the default unit is px. For example, '10' is equivalent to '10px'.<br>**Note:**<br>This attribute does not take effect when the data panel type is DataPanelType.Line.<br>If a value less than 0 is set, the default value is used.<br>When value is greater than the ring radius, the ring thickness is automatically set to 12% of the ring radius. If value is too large, the ring may disappear. |


### trackShadow<sup>10+</sup>

trackShadow(value: DataPanelShadowOptions)

Sets the shadow style. If this attribute is set, the shadow effect is controlled by this attribute, and the control of **closeEffect** over the shadow effect no longer takes effect (the control of **closeEffect** over the rotation animation effect is not affected).

**Atomic service API**: This API can be used in atomic services since API version 11.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type                                                       | Mandatory| Description                                                 |
| ------ | ----------------------------------------------------------- | ---- | ----------------------------------------------------- |
| value  | [DataPanelShadowOptions](#datapanelshadowoptions10) | Yes   | Shadow style.<br>**Note:** <br>When set to null, the shadow is not enabled. |

### contentModifier<sup>12+</sup>

contentModifier(modifier: ContentModifier\<DataPanelConfiguration>)

Creates a content modifier.

**Atomic service API**: This API can be used in atomic services since API version 12.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type                                         | Mandatory| Description                                            |
| ------ | --------------------------------------------- | ---- | ------------------------------------------------ |
| modifier  | [ContentModifier](./ts-universal-attributes-content-modifier.md#contentmodifiert)\<[DataPanelConfiguration](#datapanelconfiguration12) | Yes   | Method for customizing the content area on the DataPanel component. After being set, the developer-defined content replaces the original content displayed by DataPanel.<br>modifier: content modifier. The developer needs to define a custom class to implement the ContentModifier interface. |


## DataPanelShadowOptions<sup>10+</sup>

Inherits from [MultiShadowOptions](ts-information-display-common.md#multishadowoptions) and has all properties of **MultiShadowOptions**.

**Atomic service API**: This API can be used in atomic services since API version 11.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name         | Type| Read-Only| Optional| Description|
| ------------- | ------- | ---- | -------- | -------- |
| colors | Array<[ResourceColor](ts-types.md#resourcecolor) \| [LinearGradient](#lineargradient10)> | No | Yes | Projection color of each data segment. <br>Default value: same as the value of **valueColors** <br>**Note:** <br>If the number of shadow colors set is less than the number of data segments, the number of shadow colors displayed equals the number of shadow colors set.<br>If the number of shadow colors set is greater than the number of data segments, the number of shadow colors displayed equals the number of data segments.|

## LinearGradient<sup>10+</sup>

### constructor

constructor(colorStops: ColorStop[])

Describes the linear gradient.

**Atomic service API**: This API can be used in atomic services since API version 11.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name        | Type| Mandatory| Description|
| ------------- | ------- | ---- | -------- |
| colorStops | [ColorStop](#colorstop10)[] | Yes| Gradient colors and color stops.|


## ColorStop<sup>10+</sup>

Color stop type, which is used to describe the color stops of a gradient color.

**Atomic service API**: This API can be used in atomic services since API version 11.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name         | Type| Read-Only| Optional| Description|
| ------------- | ------- | ---- | -------- | -------- |
| color | [ResourceColor](ts-types.md#resourcecolor) | No| No| Color value at the gradient color stop.|
| offset | [Length](ts-types.md#length) | No | No | Gradient color breakpoint (a ratio value between 0 and 1; if the value is less than 0, it is set to 0; if the value is greater than 1, it is set to 1).<br>**Note:** <br>If a string type is passed in and its content is a number, it is converted to the corresponding value.<br>For example, '10vp' is converted to 10, and '10%' is converted to 0.1. |

## DataPanelConfiguration<sup>12+</sup>

You need a custom class to implement the **ContentModifier** API. Inherits from [CommonConfiguration](ts-universal-attributes-content-modifier.md#commonconfigurationt).

**Atomic service API**: This API can be used in atomic services since API version 12.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name | Type   |    Read-Only   |    Optional  |  Description             |
| ------ | ------ | ------ |-------------------------------- |-------------------------------- |
| values | number[] | No | No | Data value of the current DataPanel.<br>The array length ranges from 0 to 9.<br>**Note:**<br>If the array length is greater than 9, only the first 9 items are used.|
| maxValue | number | No | No | Maximum value displayed by the DataPanel.<br>Default value: 100.<br>**Note:** <br>If the value is less than or equal to 0, maxValue is set to the sum of all items in the values array, and the values are displayed proportionally. |

## Example

### Example 1: Setting Data Panel Types

This example shows how to set the data panel type using the **type** attribute of [DataPanelOptions](#datapaneloptions).

```ts
// xxx.ets
@Entry
@Component
struct DataPanelExample {
  public valueArr: number[] = [10, 10, 10, 10, 10, 10, 10, 10, 10];

  build() {
    Column({ space: 5 }) {
      Row() {
        Stack() {
          // Single-segment circular data panel
          DataPanel({ values: [30], max: 100, type: DataPanelType.Circle }).width(168).height(168)
          Column() {
            Text('30').fontSize(35).fontColor('#182431')
            Text('1.0.0').fontSize(9.33).lineHeight(12.83).fontWeight(500).opacity(0.6)
          }

          Text('%')
            .fontSize(9.33)
            .lineHeight(12.83)
            .fontWeight(500)
            .opacity(0.6)
            .position({ x: 104.42, y: 78.17 })
        }.margin({ right: 44 })

        // Multi-segment circular data panel
        Stack() {
          DataPanel({ values: [50, 12, 8, 5], max: 100, type: DataPanelType.Circle }).width(168).height(168)
          Column() {
            Text('75').fontSize(35).fontColor('#182431')
            Text('Used: 98 GB/128 GB').fontSize(8.17).lineHeight(11.08).fontWeight(500).opacity(0.6)
          }

          Text('%')
            .fontSize(9.33)
            .lineHeight(12.83)
            .fontWeight(500)
            .opacity(0.6)
            .position({ x: 104.42, y: 78.17 })
        }
      }.margin({ bottom: 59 })

      // Linear data panel
      DataPanel({ values: this.valueArr, max: 100, type: DataPanelType.Line }).width(300).height(20)
    }.width('100%').margin({ top: 5 })
  }
}
```

![dataPanel](figures/dataPanel.PNG)

### Example 2: Setting Gradient Colors and Shadows

This example demonstrates how to set gradient colors and shadows using the [valueColors](#valuecolors10) and [trackShadow](#trackshadow10) for [LinearGradient](#lineargradient10).

```ts
// xxx.ets
@Entry
@Component
struct LinearGradientDataPanelExample {
  public values1: number[] = [20, 20, 20, 20];
  public color1: LinearGradient =
      new LinearGradient([{ color: '#65EEC9A3', offset: 0 }, { color: '#FFEF629F', offset: 1 }]);
  public color2: LinearGradient =
      new LinearGradient([{ color: '#FF67F9D4', offset: 0 }, { color: '#FFFF9554', offset: 1 }]);
  public colorShadow1: LinearGradient =
      new LinearGradient([{ color: '#65EEC9A3', offset: 0 }, { color: '#65EF629F', offset: 1 }]);
  public colorShadow2: LinearGradient =
      new LinearGradient([{ color: '#65e26709', offset: 0 }, { color: '#65efbd08', offset: 1 }]);
  public colorShadow3: LinearGradient =
      new LinearGradient([{ color: '#6572B513', offset: 0 }, { color: '#6508efa6', offset: 1 }]);
  public colorShadow4: LinearGradient =
      new LinearGradient([{ color: '#65ed08f5', offset: 0 }, { color: '#65ef0849', offset: 1 }]);
  @State shadowColorArray: Array<LinearGradient | ResourceColor> =
      [this.colorShadow1, this.colorShadow2, this.colorShadow3, this.colorShadow4];
  @State color3: string = '#00FF00';
  @State color4: string = '#20FF0000';
  @State colorArray: Array<LinearGradient | ResourceColor> = [this.color1, this.color2, this.color3, this.color4];
  @State bgColor: string = '#08182431';
  @State offsetX: number = 15;
  @State offsetY: number = 15;
  @State radius: number = 5;

  build() {
    Column({ space: 5 }) {
      Text('LinearGradient')
        .fontSize(9)
        .fontColor(0xCCCCCC)
        .textAlign(TextAlign.Start)
        .width('100%')
        .margin({ top: 20, left: 20 })
      DataPanel({ values: this.values1, max: 100, type: DataPanelType.Circle })
        .width(300)
        .height(300)
        .valueColors(this.colorArray)
        .trackShadow({
          radius: this.radius,
          colors: this.shadowColorArray,
          offsetX: this.offsetX,
          offsetY: this.offsetY
        })
        .strokeWidth(30)
        .trackBackgroundColor(this.bgColor)
    }.width('100%').margin({ top: 5 })
  }
}
```

![LinearGradientDataPanel](figures/LinearGradientDataPanel.PNG)

### Example 3: Disabling Animations and Shadows

This example uses the [closeEffect](#closeeffect) API to disable the rotation animation effect and shadow effect of the data proportion chart.

```ts
// xxx.ets
@Entry
@Component
struct LinearGradientDataPanelExample {
  public values1: number[] = [20, 20, 20, 20];
  public color1: LinearGradient =
    new LinearGradient([{ color: '#65EEC9A3', offset: 0 }, { color: '#FFEF629F', offset: 1 }]);
  public color2: LinearGradient =
    new LinearGradient([{ color: '#FF67F9D4', offset: 0 }, { color: '#FFFF9554', offset: 1 }]);
  @State color3: string = '#00FF00';
  @State color4: string = '#20FF0000';
  @State colorArray: Array<LinearGradient | ResourceColor> = [this.color1, this.color2, this.color3, this.color4];
  @State bgColor: string = '#08182431';

  build() {
    Column({ space: 5 }) {
      Text('LinearGradient')
        .fontSize(9)
        .fontColor(0xCCCCCC)
        .textAlign(TextAlign.Start)
        .width('100%')
        .margin({ top: 20, left: 20 })
      DataPanel({ values: this.values1, max: 100, type: DataPanelType.Circle })
        .width(300)
        .height(300)
        .valueColors(this.colorArray)
        .strokeWidth(30)
        .closeEffect(true)
        .trackBackgroundColor(this.bgColor)
    }.width('100%').margin({ top: 5 })
  }
}
```

![DataPanelCloseEffect](figures/DataPanelCloseEffect.png)

### Example 4: Setting the Custom Content Area

This example shows how to customize the content area of the data panel using the [contentModifier](#contentmodifier12) API.

```ts
// xxx.ets
@Builder
function buildDataPanel(config: DataPanelConfiguration) {
  Column() {
    Column() {
      ForEach(config.values, (item: number, index: number) => {
        ChildItem({ item: item, index: index, max: config.maxValue })
      }, (item: number, index: number) => item.toString())
    }.padding(10)

    Column() {
      Line().width('100%').backgroundColor('#ff373737').margin({ bottom: 5 })
    }.padding({ left: 20, right: 20 })

    Row() {
      Text('Length=' + config.values.length + '    ').margin({ left: 10 }).align(Alignment.Start)
      Text('Max=' + config.maxValue).margin({ left: 10 }).align(Alignment.Start)
    }
  }
}

class DataPanelBuilder implements ContentModifier<DataPanelConfiguration> {
  constructor() {
  }

  applyContent(): WrappedBuilder<[DataPanelConfiguration]> {
    return wrapBuilder(buildDataPanel)
  }
}

@Entry
@Component
struct Index {
  build() {
    Column() {
      Text('Data panel').margin({ top: 12 });
      Row() {
        DataPanel({ values: [12.3, 21.1, 13.4, 35.2, 26.0, 32.0], max: 140, type: DataPanelType.Circle })
          .width(400)
          .height(260)
          .constraintSize({ maxWidth: '100%' })
          .padding({ top: 10 })
          .contentModifier(new DataPanelBuilder())
      }.margin(15).backgroundColor('#fff5f5f5')
    }
  }
}

@Component
struct ChildItem {
  @Prop item: number;
  @Prop index: number;
  @Prop max: number;
  public color1: string = '#65ff00dd'
  public color2: string = '#6500ff99'
  public color3: string = '#65ffe600'
  public color4: string = '#6595ff00'
  public color5: string = '#65000dff'
  public color6: string = '#650099ff'
  public colorArray: Array<string> = [this.color1, this.color2, this.color3, this.color4, this.color5, this.color6];

  build() {
    RelativeContainer() {
      Row() {
        Rect()
          .height(25)
          .width(this.item * 600 / this.max)
          .foregroundColor((this.index < 0 || this.index >= this.colorArray.length) ? this.colorArray[0] :
            this.colorArray[this.index])
          .radius(5)
          .align(Alignment.Start)
        Text(' ' + this.item)
          .fontSize(17)
      }
    }.height(28)
  }
}
```
![ContentModifierDataPanel](figures/ContentModifierDataPanel.jpg)
