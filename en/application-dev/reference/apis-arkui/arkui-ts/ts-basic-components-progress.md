# Progress
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @liyujie43-->
<!--Designer: @weixin_52725220-->
<!--Tester: @xiong0104-->
<!--Adviser: @HelloCrease-->

The **Progress** component represents a progress indicator that displays the progress of content loading or an operation.

>  **NOTE**
>
>  This component is supported since API version 7. Updates will be marked with a superscript to indicate their earliest API version.


## Child Components

Not supported

## APIs

Progress(options: ProgressOptions)

Creates a progress indicator.

**Widget capability**: This API can be used in ArkTS widgets since API version 9.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| options |  [ProgressOptions](#progressoptions)| Yes| Options of the progress indicator, which vary by progress indicator type.|

## ProgressOptions

Progress bar option.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name                       | Type                               | Read-Only| Optional| Description                                    |
| -------------------------- | ----------------------------------- | ---- | ---------------------------------------- | ---------------------------------------- |
| value                      | number                              | No  | No  | Current progress. If the value is less than 0, the value **0** is used. If the value is greater than that of **total**, the value of **total** is used.<br>Default value: **0**<br>Value range: [0, total]<br>**Widget capability**: This API can be used in ArkTS widgets since API version 9.|
| total                      | number                              | No  | Yes  | Total progress. If this parameter is set to a value less than or equal to 0, the value **100** is used.<br>Default value: **100**<br>Value range: 0–2147483647<br>**Widget capability**: This API can be used in ArkTS widgets since API version 9.|
| type<sup>8+</sup>          | [ProgressType](#progresstype8)   | No  | Yes  | Style of the progress indicator.<br>Default value: **ProgressType.Linear**<br>**Widget capability**: This API can be used in ArkTS widgets since API version 9.<br>Note: Different types must correspond to different [style](#style8) attribute settings. For details about the mapping, see [ProgressStyleMap](#progressstylemap10).|
| style<sup>(deprecated)</sup> | [ProgressStyle](#progressstyle) | No  | Yes  | Style of the progress indicator.<br>This parameter is deprecated since API version 8. You are advised to use **type** instead.<br>Default value: **ProgressStyle.Linear**|

## ProgressType<sup>8+</sup>

Progress bar type.

**Widget capability**: This API can be used in ArkTS widgets since API version 9.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name                    | Value| Description                                    |
| ---------------------- | - | ---------------------------------------- |
| Linear                 | 0 | Linear style. Since API version 9, when the height is greater than the width, the progress bar is displayed vertically.  |
| Ring      | 1 | Circular style without scale. The circular ring is gradually displayed until it is completely filled.                |
| Eclipse  | 2 | Eclipse style, which visualizes the progress in a way similar to the moon waxing from new to full.        |
| ScaleRing | 3 | Determinate ring style, which is similar to the clock scale. Since API version 9, when the scale outer circle overlaps, the progress bar automatically converts to a circular style without scale.|
| Capsule   | 4 | Capsule style. At both ends, the progress indicator works in a same manner as the eclipse style. In the middle part of the capsule, the progress indicator works in a same manner as the linear style. When the height is greater than the width, the progress bar is displayed vertically.|

##  ProgressStyle

Progress bar style.

**Widget capability**: This API can be used in ArkTS widgets since API version 9.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name       | Value| Description                                    |
| --------- | - | ---------------------------------------- |
| Linear    | - | Linear style.                                   |
| Ring<sup>8+</sup>      | - | The ring gradually displays until it is completely filled.                |
| Eclipse   | - | Eclipse style, which visualizes the progress in a way similar to the moon waxing from new to full.        |
| ScaleRing<sup>8+</sup> | - | Determinate ring style, which is similar to the clock scale.              |
| Capsule<sup>8+</sup>   | - | Capsule style. At both ends, the progress indicator works in a same manner as the eclipse style. In the middle part of the capsule, the progress indicator works in a same manner as the linear style. When the height is greater than the width, the progress bar is displayed vertically.|

##  ProgressStyleMap<sup>10+</sup>

Mapping table of progress bar types and styles.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name       | Type                                     |
| --------- | ---------------------------------------- |
| ProgressType.Linear | [LinearStyleOptions<sup>10+</sup>](#linearstyleoptions10)  \|  [ProgressStyleOptions](#progressstyleoptions8)  |
| ProgressType.Ring | [RingStyleOptions<sup>10+</sup>](#ringstyleoptions10)  \|  [ProgressStyleOptions](#progressstyleoptions8)  |
| ProgressType.Eclipse | [EclipseStyleOptions<sup>10+</sup>](#eclipsestyleoptions10)   \|  [ProgressStyleOptions](#progressstyleoptions8)  |
| ProgressType.ScaleRing| [ScaleRingStyleOptions<sup>10+</sup>](#scaleringstyleoptions10)  \|  [ProgressStyleOptions](#progressstyleoptions8)  |
| ProgressType.Capsule | [CapsuleStyleOptions<sup>10+</sup>](#capsulestyleoptions10)  \|  [ProgressStyleOptions](#progressstyleoptions8)  |

## Attributes

In addition to the [universal attributes](ts-component-general-attributes.md), the following attributes are supported.

> **NOTE**
>
> This component overrides the universal attribute [backgroundColor](ts-universal-attributes-background.md). If the attribute is directly applied to the **Progress** component, it changes the background color of the progress indicator itself. To set the background color of the entire Progress component, you need to add backgroundColor to the outer container and use the container to wrap the Progress component.

### value

value(value: number)

Current progress. If the value is less than 0, the value **0** is used. If the value is greater than that of **total**, the value of **total** is used. Invalid values do not take effect.

**Widget capability**: This API can be used in ArkTS widgets since API version 9.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type  | Mandatory| Description        |
| ------ | ------ | ---- | ------------ |
| value  | number | Yes  | Current progress.<br> Default value: **0**|

### color

color(value: ResourceColor | LinearGradient)

Sets the foreground color of the progress indicator.

**LinearGradient** is supported for the **Ring** type since API version 10. You are not advised to set the transparency for the ring type. If you need to set the transparency, you are advised to use [DataPanel](ts-basic-components-datapanel.md).

**Widget capability**: This API can be used in ArkTS widgets since API version 9, except that **LinearGradient** is not supported.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type                                                        | Mandatory| Description                                                        |
| ------ | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| value  | [ResourceColor](ts-types.md#resourcecolor) \| [LinearGradient](ts-basic-components-datapanel.md#lineargradient10) | Yes  | Foreground color of the progress indicator.<br>Default value:<br>- Capsule:<br>   API version 9 or earlier: **'\#ff007dff'**<br>   API version 10: **'\#33006cde'**<br>   API version 11 or later: **'\#33007dff'**<br>- Ring:<br>   API version 9 or earlier: **'\#ff007dff'**<br>   API version 10 or later: start: **'\#ff86c1ff'**, end: **'\#ff254ff7'**<br>- Other styles: **'\#ff007dff'**|

### style<sup>8+</sup>

style(value: ProgressStyleOptions \| CapsuleStyleOptions \| RingStyleOptions \| LinearStyleOptions \| ScaleRingStyleOptions \| EclipseStyleOptions)

Sets the component style.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type                                                        | Mandatory| Description                                                        |
| ------ | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| value  | [ProgressStyleOptions<sup>8+</sup>](#progressstyleoptions8) \| [CapsuleStyleOptions<sup>10+</sup>](#capsulestyleoptions10) \| <br>[RingStyleOptions<sup>10+</sup>](#ringstyleoptions10) \| [LinearStyleOptions<sup>10+</sup>](#linearstyleoptions10) \| <br>[ScaleRingStyleOptions<sup>10+</sup>](#scaleringstyleoptions10) \| [EclipseStyleOptions<sup>10+</sup>](#eclipsestyleoptions10) | Yes  | Component style.<br>- **CapsuleStyleOptions**: capsule style.<br>- **RingStyleOptions**: ring style.<br>- **LinearStyleOptions**: linear style.<br>- **ScaleRingStyleOptions**: determinate ring style.<br>- **EclipseStyleOptions**: eclipse style.<br>- ProgressStyleOptions: strokeWidth, scaleCount, and scaleWidth of the progress bar. This parameter is valid only for the progress bar that supports these style settings.|

### contentModifier<sup>12+</sup>
contentModifier(modifier:ContentModifier\<ProgressConfiguration\>)

Creates a content modifier.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**
| Name| Type  | Mandatory| Description        |
| ------ | ------ | ---- | ------------ |
| modifier | [ContentModifier\<ProgressConfiguration\>](#progressconfiguration12) | Yes  | Content modifier to apply to the current component.<br>**modifier**: content modifier. You need a custom class to implement the **ContentModifier** API.|

### privacySensitive<sup>12+</sup>

privacySensitive(isPrivacySensitiveMode: Optional\<boolean\>)

Sets whether to enable privacy mode.

**Widget capability**: This API can be used in ArkTS widgets since API version 12.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type                                                     | Mandatory| Description                                                 |
| ------ | --------------------------------------------------------- | ---- | ----------------------------------------------------- |
| isPrivacySensitiveMode  | [Optional\<boolean\>] | Yes  | Whether to enable privacy mode, in which the progress is cleared and the text is obscured. The value **true** means to enable privacy mode, and **false** means the opposite.<br>**NOTE**<br>The value null indicates insensitive.<!--Del--><br>For widgets, this property must be used with [FormComponent](./ts-basic-components-formcomponent-sys.md) and the [obscured](./ts-universal-attributes-obscured.md) attribute to display privacy masking effects.<!--DelEnd--> |

## ProgressConfiguration<sup>12+</sup>

Configure the progress bar. Inherited from [CommonConfiguration](ts-universal-attributes-content-modifier.md#commonconfigurationt)

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name| Type | Read-Only| Optional|Description        |
| ------ | ------ | ------- |------------|------------|
| value  | number | No| No| Current progress. Values less than 0 are adjusted to **0**. Values greater than the value of **total** are capped at the value of **total**.<br>Default value: **0**<br>Value range: [0, total]|
| total  | number | No| No| Indicates the total progress.<br>Value range: (0, 2147483647]  |

## CommonProgressStyleOptions<sup>10+</sup>

Common style options of the progress bar.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name         | Type                     | Read-Only| Optional| Description                                                                                       |
| ------------ | ---------------------------- | ---- | ------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------ |
| enableSmoothEffect | boolean | No| Yes| Whether to enable the smooth effect. If this option is enabled, the progress changes from the current value to the specified value, and the page displays the progress change animation. Otherwise, the progress changes from the current value to the specified value, and no animation is displayed on the page.<br>Default value: **true**<br>**true**: Enable the smooth effect.<br>**false**: Disable the smooth effect.|

## ScanEffectOptions<sup>10+</sup>

Light sweeping effect options.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name         | Type| Read-Only| Optional| Description|
| ------------- | ------- | ---- | -------- | -------- |
| enableScanEffect | boolean | No| Yes| Whether to enable the scan effect.<br>Default value: **false**<br>**true**: Enable the scan effect.<br>**false**: Disable the scan effect. Only the Linear, Ring, and Capsule progress bars are supported.|

## ProgressStyleOptions<sup>8+</sup>

Progress bar style options.

Inherits [CommonProgressStyleOptions](#commonprogressstyleoptions10).

**Widget capability**: This API can be used in ArkTS widgets since API version 9.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name         | Type                     | Read-Only| Optional| Description                                                                                       |
| ------------ | ---------------------------- | ---- | ------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------ |
| strokeWidth  | [Length](ts-types.md#length) | No | Yes | Stroke width of the progress indicator. It cannot be set in percentage.<br>Default value: **4.0vp**                                           |
| scaleCount   | number                       | No | Yes | Number of divisions on the ring-style process indicator.<br>Default value: **120**<br>Value range: [2, min(width, height)/scaleWidth/2/π]. If the value is out of the range, the progress bar is displayed as a ring without scales. By default, the minimum width and height are 77 vp.                    |
| scaleWidth   | [Length](ts-types.md#length) | No | Yes | Width of the ring progress bar scale. The value cannot be set in percentage. If the scale width is greater than the progress bar width, the default width is used.<br>Default value: **2.0vp**|

## CapsuleStyleOptions<sup>10+</sup>

Capsule style options.

Inherits from [ScanEffectOptions](#scaneffectoptions10) and [CommonProgressStyleOptions](#commonprogressstyleoptions10).

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name         | Type| Read-Only| Optional| Description|
| ------------- | ------- | ---- | -------- | -------- |
| borderColor | [ResourceColor](ts-types.md#resourcecolor) | No| Yes| Border color.<br>Default value:<br>API version 10: **'\#33006cde'**<br>API version 11 or later: **'\#33007dff'**|
| borderWidth | [Length](ts-types.md#length) | No| Yes| Border width. It cannot be set in percentage.<br>Default value: **1vp**|
| content | [ResourceStr](ts-types.md#resourcestr) | No| Yes| Text content, which can be customized .<br>The Resource type is supported since API version 20.|
| font | [Font](ts-types.md#font) | No| Yes| Text style.<br>Default value:<br>- Font size (cannot be set in percentage): **12fp**<br>- Other attributes: following the settings of the **Text** component.|
| fontColor | [ResourceColor](ts-types.md#resourcecolor) | No| Yes| Font color.<br>Default value: **'\#ff182431'**|
| showDefaultPercentage | boolean | No| Yes| Whether to display the percentage text. After this function is enabled, the progress percentage is displayed on the progress bar. This attribute does not take effect when the **content** attribute is set.<br>Default value: **false**.<br>**true**: Show the percentage of the current progress.<br>**false**: Do not show the percentage of the current progress.|
| borderRadius<sup>18+</sup> |  [LengthMetrics](../js-apis-arkui-graphics.md#lengthmetrics12) | No| Yes| Corner radius. The value cannot be set in percentage.<br>Value range: [0, height/2]<br> Default value: height/2<br>If an invalid value is set, the default value is used.|

## RingStyleOptions<sup>10+</sup>

Ring style option without scales.

Inherits from [ScanEffectOptions](#scaneffectoptions10) and [CommonProgressStyleOptions](#commonprogressstyleoptions10).

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name          | Type                     | Read-Only| Optional| Description                                                                                       |
| ------------- | ---------------------------- | ---- | ------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------ |
| strokeWidth   | [Length](ts-types.md#length) | No | Yes | Stroke width of the progress indicator. It cannot be set in percentage. When the width is greater than or equal to the radius, the width is changed to half of the radius by default.<br>Default value: **4.0vp**|
| shadow        | boolean                      | No | Yes | Whether to enable the shadow effect.<br>Default value: **false**.<br>**true**: Enable the shadow effect.<br>**false**: Disable the shadow effect.                                                            |
| status        | [ProgressStatus<sup>10+</sup>](#progressstatus10) | No| Yes| // Set the progress state. When this parameter is set to ProgressStatus.LOADING, the update check animation is enabled. In this case, the progress value setting does not take effect. When this parameter is set from ProgressStatus.LOADING to ProgressStatus.PROGRESSING, the update check animation stops at the end.<br>Default value: ProgressStatus.PROGRESSING|

## LinearStyleOptions<sup>10+</sup>

Linear style options.

Inherits from [ScanEffectOptions](#scaneffectoptions10) and [CommonProgressStyleOptions](#commonprogressstyleoptions10).

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name          | Type                     | Read-Only| Optional| Description                                                                                       |
| ------------- | ---------------------------- | ---- | ------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------ |
| strokeWidth   | [Length](ts-types.md#length) | No | Yes | Stroke width of the progress indicator. It cannot be set in percentage.<br>Default value: **4.0vp**|
| strokeRadius   | [PX](ts-types.md#px10)    \| [VP](ts-types.md#vp10)    \| [LPX](ts-types.md#lpx10)    \| [Resource](ts-types.md#resource)| No | Yes | Sets the radius of the rounded corners of the linear progress bar.<br>Value range: [0, strokeWidth/2] Default value: **strokeWidth/2**|

## ScaleRingStyleOptions<sup>10+</sup>

Ring style with scale options.

Inherits [CommonProgressStyleOptions](#commonprogressstyleoptions10).

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name         | Type                     | Read-Only| Optional| Description                                                                                       |
| ------------ | ---------------------------- | ---- | ------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------ |
| strokeWidth  | [Length](ts-types.md#length) | No | Yes | Stroke width of the progress indicator. It cannot be set in percentage.<br>Default value: **4.0vp**                                           |
| scaleCount   | number                       | No | Yes | Number of divisions on the ring-style process indicator.<br>Default value: **120**<br>Value range: [2, min(width, height)/scaleWidth/2/π]. If the value is out of the range, the progress bar is displayed as a ring without scales. By default, the minimum width and height are 77 vp.                    |
| scaleWidth   | [Length](ts-types.md#length) | No | Yes | Width of the ring progress bar scale. The value cannot be a percentage. If the scale width is greater than the progress bar width, the default width is used.<br>Default value: **2.0vp**|

## EclipseStyleOptions<sup>10+</sup>

Options of the circle style. Eclipse style, which visualizes the progress in a way similar to the moon waxing from new to full.

Inherits [CommonProgressStyleOptions](#commonprogressstyleoptions10).

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

## ProgressStatus<sup>10+</sup>

Current status of the progress bar.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name                   | Value    | Description     |
| ----------------------- | ---------------- | ---------------- |
| LOADING  | - | Loading.|
| PROGRESSING | - | The progress is being updated.|

## Events

The [universal events](ts-component-general-events.md) are supported.

## Example

### Example 1: Setting Progress Indicator Types

This example demonstrates how to set different types of progress indicators using the **type** attribute.

```ts
// xxx.ets
@Entry
@Component
struct ProgressExample {
  build() {
    Column({ space: 15 }) {
      Text('Linear Progress').fontSize(9).fontColor(0xCCCCCC).width('90%')
      Progress({ value: 10, type: ProgressType.Linear }).width(200)
      Progress({ value: 20, total: 150, type: ProgressType.Linear }).color(Color.Grey).value(50).width(200)


      Text('Eclipse Progress').fontSize(9).fontColor(0xCCCCCC).width('90%')
      Row({ space: 40 }) {
        Progress({ value: 10, type: ProgressType.Eclipse }).width(100)
        Progress({ value: 20, total: 150, type: ProgressType.Eclipse }).color(Color.Grey).value(50).width(100)
      }

      Text('ScaleRing Progress').fontSize(9).fontColor(0xCCCCCC).width('90%')
      Row({ space: 40 }) {
        Progress({ value: 10, type: ProgressType.ScaleRing }).width(100)
        Progress({ value: 20, total: 150, type: ProgressType.ScaleRing })
          .color(Color.Grey).value(50).width(100)
          .style({ strokeWidth: 15, scaleCount: 15, scaleWidth: 5 })
      }

      // scaleCount vs. scaleWidth
      Row({ space: 40 }) {
        Progress({ value: 20, total: 150, type: ProgressType.ScaleRing })
          .color(Color.Grey).value(50).width(100)
          .style({ strokeWidth: 20, scaleCount: 20, scaleWidth: 5 })
        Progress({ value: 20, total: 150, type: ProgressType.ScaleRing })
          .color(Color.Grey).value(50).width(100)
          .style({ strokeWidth: 20, scaleCount: 30, scaleWidth: 3 })
      }

      Text('Ring Progress').fontSize(9).fontColor(0xCCCCCC).width('90%')
      Row({ space: 40 }) {
        Progress({ value: 10, type: ProgressType.Ring }).width(100)
        Progress({ value: 20, total: 150, type: ProgressType.Ring })
          .color(Color.Grey).value(50).width(100)
          .style({ strokeWidth: 20 })
      }

      Text('Capsule Progress').fontSize(9).fontColor(0xCCCCCC).width('90%')
      Row({ space: 40 }) {
        Progress({ value: 10, type: ProgressType.Capsule }).width(100).height(50)
        Progress({ value: 20, total: 150, type: ProgressType.Capsule })
          .color(Color.Grey)
          .value(50)
          .width(100)
          .height(50)
      }
    }.width('100%').margin({ top: 30 })
  }
}
```

![progress](figures/arkts-progress.png)

### Example 2: Setting Ring Progress Indicator Attributes

This example demonstrates how to set attributes of a ring progress indicator using the **strokeWidth** and **shadow** properties in the [style](#style8) API.

```ts
// xxx.ets
@Entry
@Component
struct ProgressExample {
  private gradientColor: LinearGradient = new LinearGradient([{ color: Color.Yellow, offset: 0.5 },
    { color: Color.Orange, offset: 1.0 }])

  build() {
    Column({ space: 15 }) {
      Text('Gradient Color').fontSize(9).fontColor(0xCCCCCC).width('90%')
      Progress({ value: 70, total: 100, type: ProgressType.Ring })
        .width(100).style({ strokeWidth: 20 })
        .color(this.gradientColor)

      Text('Shadow').fontSize(9).fontColor(0xCCCCCC).width('90%')
      Progress({ value: 70, total: 100, type: ProgressType.Ring })
        .width(120).color(Color.Orange)
        .style({ strokeWidth: 20, shadow: true })
    }.width('100%').padding({ top: 5 })
  }
}
```
![ringProgressStyleEffect](figures/arkts-ringProgressStyleEffect.png)

### Example 3: Setting the Animation for the Ring Progress Indicator

This example demonstrates how to enable or disable animations for a ring progress indicator using the **status** and **enableScanEffect** properties in the [style](#style8) API.

```ts
// xxx.ets
@Entry
@Component
struct ProgressExample {
  build() {
    Column({ space: 15 }) {
      Text('Loading Effect').fontSize(9).fontColor(0xCCCCCC).width('90%')
      Progress({ value: 0, total: 100, type: ProgressType.Ring })
        .width(100).color(Color.Blue)
        .style({ strokeWidth: 20, status: ProgressStatus.LOADING })

      Text('Scan Effect').fontSize(9).fontColor(0xCCCCCC).width('90%')
      Progress({ value: 30, total: 100, type: ProgressType.Ring })
        .width(100).color(Color.Orange)
        .style({ strokeWidth: 20, enableScanEffect: true })
    }.width('100%').padding({ top: 5 })
  }
}
```
![ringProgressAnimation](figures/arkts-ringProgressAnimation.gif)

### Example 4: Setting Capsule Progress Indicator Attributes

This example demonstrates how to set attributes for a capsule progress indicator using properties such as **borderColor**, **borderWidth**, and **content** in the [style](#style8) API.

```ts
// xxx.ets
@Entry
@Component
struct ProgressExample {
  build() {
    Column({ space: 15 }) {
      Row({ space: 40 }) {
        Progress({ value: 100, total: 100, type: ProgressType.Capsule }).width(100).height(50)
          .style({
            borderColor: Color.Blue,
            borderWidth: 1,
            content: 'Installing...',
            font: { size: 13, style: FontStyle.Normal },
            fontColor: Color.Gray,
            enableScanEffect: false,
            showDefaultPercentage: false
          })
      }
    }.width('100%').padding({ top: 5 })
  }
}
```
![capsuleProgressStyleEffect](figures/arkts-capsuleProgressStyleEffect.png)

### Example 5: Setting the Smooth Effect

This example demonstrates how to enable or disable the smooth effect for the progress animation using the **enableSmoothEffect** property in the [style](#style8) API.

```ts
// xxx.ets
@Entry
@Component
struct Index {
  @State value: number = 0;

  build() {
    Column({ space: 10 }) {
      Text('enableSmoothEffect: true')
        .fontSize(9)
        .fontColor(0xCCCCCC)
        .width('90%')
        .margin(5)
        .margin({ top: 20 })
      Progress({ value: this.value, total: 100, type: ProgressType.Linear })
        .style({ strokeWidth: 10, enableSmoothEffect: true })

      Text('enableSmoothEffect: false').fontSize(9).fontColor(0xCCCCCC).width('90%').margin(5)
      Progress({ value: this.value, total: 100, type: ProgressType.Linear })
        .style({ strokeWidth: 10, enableSmoothEffect: false })

      Button('value +10').onClick(() => {
        this.value += 10;
      })
        .width(75)
        .height(15)
        .fontSize(9)
    }
    .width('50%')
    .height('100%')
    .margin({ left: 20 })
  }
}

```
![progressSmoothEffect](figures/arkts-progressSmoothEffect.gif)

### Example 6: Setting the Custom Content Area

This example implements a custom progress indicator using the [contentModifier](#contentmodifier12) API. This progress indicator displays a star shape with a total progress of **3**, and the current value can be incremented or decremented through buttons. The achieved progress is filled with a custom color.

```ts
// xxx.ets
class MyProgressModifier implements ContentModifier<ProgressConfiguration> {
  color: Color = Color.White;

  constructor(color: Color) {
    this.color = color;
  }

  applyContent(): WrappedBuilder<[ProgressConfiguration]> {
    return wrapBuilder(myProgress);
  }
}

@Builder
function myProgress(config: ProgressConfiguration) {

  Column({ space: 30 }) {
    Text("Current progress: " + config.value + "/" + config.total).fontSize(20)
    Row() {
      Flex({ justifyContent: FlexAlign.SpaceBetween }) {
        Path()
          .width('30%')
          .height('30%')
          .commands('M108 0 L141 70 L218 78.3 L162 131 L175 205 L108 170 L41.2 205 L55 131 L1 78 L75 68 L108 0 Z')
          .fill(config.enabled && config.value >= 1 ? (config.contentModifier as MyProgressModifier).color :
          Color.White)
          .stroke(Color.Black)
          .strokeWidth(3)
        Path()
          .width('30%')
          .height('30%')
          .commands('M108 0 L141 70 L218 78.3 L162 131 L175 205 L108 170 L41.2 205 L55 131 L1 78 L75 68 L108 0 Z')
          .fill(config.enabled && config.value >= 2 ? (config.contentModifier as MyProgressModifier).color :
          Color.White)
          .stroke(Color.Black)
          .strokeWidth(3)
        Path()
          .width('30%')
          .height('30%')
          .commands('M108 0 L141 70 L218 78.3 L162 131 L175 205 L108 170 L41.2 205 L55 131 L1 78 L75 68 L108 0 Z')
          .fill(config.enabled && config.value >= 3 ? (config.contentModifier as MyProgressModifier).color :
          Color.White)
          .stroke(Color.Black)
          .strokeWidth(3)
      }.width('100%')
    }
  }.margin({ bottom: 100 })
}

@Entry
@Component
struct Index {
  @State currentValue: number = 0;
  modifier = new MyProgressModifier(Color.Red);
  @State myModifier: (MyProgressModifier | undefined) = this.modifier;

  build() {
    Column() {
      Progress({ value: this.currentValue, total: 3, type: ProgressType.Ring }).contentModifier(this.modifier)
      Button('Progress++').onClick(() => {
        if (this.currentValue < 3) {
          this.currentValue += 1;
        }
      }).width('30%')
      Button('Progress--').onClick(() => {
        if (this.currentValue > 0) {
          this.currentValue -= 1;
        }
      }).width('30%')
    }.width('100%').height('100%')
  }
}

```
![progressCustom](figures/arkts-progressCustom.gif)

### Example 7: Securing Sensitive Information

This example illustrates how to secure sensitive information using the [privacySensitive](#privacysensitive12) attribute. Note that the display requires widget framework support.

```ts
@Entry
@Component
struct ProgressExample {
  build() {
    Row() {
      Column({ space: 15 }) {
        Progress({ value: 33, total: 100, type: ProgressType.Capsule }).width(300).height(50)
          .color(Color.Blue)
          .style({
            borderWidth: 5,
            font: { size: 13, style: FontStyle.Normal },
            enableScanEffect: false,
            showDefaultPercentage: true
          })
          .privacySensitive(true)
        Progress({ value: 33, total: 100, type: ProgressType.Capsule }).width(300).height(50)
          .color(Color.Blue)
          .style({
            borderWidth: 5,
            content: 'Installing...',
            font: { size: 13, style: FontStyle.Normal },
            enableScanEffect: false,
          })
          .privacySensitive(true)
      }
    }
  }
}
```
![progressSensitive](figures/progress-privacysensitive.gif)

### Example 8: Setting Capsule Progress Indicator Border Radius

This example demonstrates how to set the border corner radius of a capsule progress indicator using the **borderRadius** property.

```ts
import { LengthMetrics } from '@kit.ArkUI';

@Entry
@Component
struct ProgressExample {
  build() {
    Column({ space: 15 }) {
      Text('Capsule Progress').fontSize(9).width('90%')
      Row({ space: 15 }) {
        Progress({ value: 30, total: 100, type: ProgressType.Capsule })
          .style({ content: "Default radius", borderWidth: 5 })
          .width(100)
          .height(60)
      }

      Row({ space: 15 }) {
        Progress({ value: 30, total: 100, type: ProgressType.Capsule })
          .style({ content: "Radius 20 vp", borderWidth: 5, borderRadius: LengthMetrics.vp(20) })
          .width(100)
          .height(60)
      }
    }
    .width('100%')
    .margin({ top: 30 })
  }
}

```
![capsuleProgressBorderRadius](figures/arkts-capsuleProgressBorderRadius.png)
