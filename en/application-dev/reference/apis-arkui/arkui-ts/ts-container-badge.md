# Badge
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @Zhang-Dong-hui-->
<!--Designer: @xiangyuan6-->
<!--Tester:@jiaoaozihao-->
<!--Adviser: @Brilliantry_Rui-->

The **Badge** component is a container that can be attached to another component for notification and reminder purposes.

>  **NOTE**
>
> This component is supported since API version 7. Updates will be marked with a superscript to indicate their earliest API version.


## Child Components

This component supports only one child component.

>  **NOTE**
>
> - Allowed child component types: built-in and custom components, including rendering control types ([if/else](../../../ui/rendering-control/arkts-rendering-control-ifelse.md), [ForEach](../../../ui/rendering-control/arkts-rendering-control-foreach.md), and [LazyForEach](../../../ui/rendering-control/arkts-rendering-control-lazyforeach.md)).
>
> - A custom component defaults to a width and height of 0. You must explicitly set its width and height; otherwise, the **Badge** component will not be displayed.
>
> - When there are multiple child components, only the last child component is displayed on the UI. However, the status update of other child components will still cause the badge and its child components to be re-rendered.
>
> - Child component layout is independent and does not automatically adjust to avoid overlapping with the badge.


## APIs

### Badge

Badge(value: BadgeParamWithNumber)

Creates a badge with the given numerical value.

**Widget capability**: This API can be used in ArkTS widgets since API version 9.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| value |  [BadgeParamWithNumber](#badgeparamwithnumber)| Yes| Options of the numeric badge.|

### Badge

Badge(value: BadgeParamWithString)

Creates a badge with the given string.

**Widget capability**: This API can be used in ArkTS widgets since API version 9.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

This component supports the scaling effect for visibility transition since API version 12.

**Parameters**

| Name| Type                                             | Mandatory| Description            |
| ------ | ----------------------------------------------------- | ---- | -------------------- |
| value  | [BadgeParamWithString](#badgeparamwithstring) | Yes  | Options of the string-type badge.|

## BadgeParam

Provides basic parameters for creating a badge.

**Widget capability**: This API can be used in ArkTS widgets since API version 9.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name| Type| Read-Only| Optional| Description|
| -------- | -------- | -------- | -------- | -------- |
| position | [BadgePosition](#badgeposition)\|[Position<sup>10+</sup>](ts-types.md#position) | No| Yes| Position to display the badge relative to the parent component.<br>Default value: **BadgePosition.RightTop**<br>**NOTE**<br> With the **Position** type, percentage values are not supported. If an invalid value is set, the default value **(0,0)**, which indicates the upper left corner of the component, will be used.<br>With the **BadgePosition** type, the position is mirrored based on the [Direction](ts-appendix-enums.md#direction) property.|
| style | [BadgeStyle](#badgestyle) | No| No| Style of the badge, including the font color, font size, badge color, and badge size.|


## BadgeParamWithNumber

Inherits from [BadgeParam](#badgeparam) and has all attributes of **BadgeParam**.

**Widget capability**: This API can be used in ArkTS widgets since API version 9.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name| Type| Read-Only| Optional| Description|
| -------- | -------- | -------- | -------- | -------- |
| count | number | No| No| Number of notifications.<br>**NOTE**<br>If the value is less than or equal to 0 and less than the value of **maxCount**, no badge is displayed.<br>Value range: [-2147483648,2147483647]. If the value is out of the range, 4294967296 is added or subtracted so that the value is within the range. If the value is not an integer, it is rounded off to the nearest integer. For example, 5.5 is rounded off to 5.|
| maxCount | number | No| Yes| Maximum number of messages. When the number of messages exceeds the maximum, only the number of messages plus the value of maxCount is displayed. For example, if the value of maxCount is 99, 99+ is displayed.<br>Default value: **99**<br>Value range: [-2147483648,2147483647]. If the value is out of the range, 4294967296 is added or subtracted so that the value is within the range. If the value is not an integer, it is rounded off to the nearest integer. For example, 5.5 is rounded off to 5.|

## BadgeParamWithString

Inherits from [BadgeParam](#badgeparam) and has all attributes of **BadgeParam**.

**Widget capability**: This API can be used in ArkTS widgets since API version 9.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name| Type| Read-Only| Optional| Description|
| -------- | -------- | -------- | -------- | -------- |
| value | [ResourceStr](ts-types.md#resourcestr) | No| No| Prompt content.<br>**NOTE**<br>The ResourceStr type is supported since API version 20.|

## BadgePosition

Enumerates the display positions of a badge.

**Widget capability**: This API can be used in ArkTS widgets since API version 9.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name| Value| Description|
| -------- | -------- |-------- |
| RightTop | - | The badge is displayed in the upper right corner of the parent component.|
| Right | - | The badge is vertically centered on the right of the parent component.|
| Left | - | The badge is vertically centered on the left of the parent component.|

## BadgeStyle

Describes the badge style. It includes the text color, size, font weight, dot color, and size.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name                     | Type                                                        | Read-Only| Optional| Description                                                        |
| ------------------------- | ------------------------------------------------------------ | ---- | ---- | ------------------------------------------------------------ |
| color                     | [ResourceColor](ts-types.md#resourcecolor)                   | No  | Yes  | Font color.<br>Default value: **Color.White**<br>**Widget capability**: This API can be used in ArkTS widgets since API version 9.<br>**Atomic service API**: This API can be used in atomic services since API version 11.|
| fontSize                  | number&nbsp;\|&nbsp;[ResourceStr](ts-types.md#resourcestr)   | No  | Yes  | Font size. For the string type, only numeric string values with optional units, for example, **"10"** or **"10fp"**, are supported.<br>Default value: **10**<br>Unit: fp<br>Value range: greater than 0. If the value is 0, no text is displayed. If the value is less than 0, the default value is used.<br>**NOTE**<br>Percentage values are not supported. If a percentage value is set, the default value is used. The ResourceStr type is supported since API version 20.<br>**Widget capability**: This API can be used in ArkTS widgets since API version 9.<br>**Atomic service API**: This API can be used in atomic services since API version 11.|
| badgeSize                 | number&nbsp;\|&nbsp;[ResourceStr](ts-types.md#resourcestr)   | No  | Yes  | Badge size. For the string type, numeric string values with optional units, for example, **"16"** or **"16fp"**, are supported.<br>Default value: **16**<br>Unit: vp<br>Value range: greater than 0. If the value is 0, no badge is displayed. If the value is less than 0, the default value is used.<br>**NOTE**<br>Percentage values are not supported. If a percentage value is set, the default value is used. The ResourceStr type is supported since API version 20.<br>**Widget capability**: This API can be used in ArkTS widgets since API version 9.<br>**Atomic service API**: This API can be used in atomic services since API version 11.|
| badgeColor                | [ResourceColor](ts-types.md#resourcecolor)                   | No  | Yes  | Badge color.<br>Default value: **Color.Red**<br>**Widget capability**: This API can be used in ArkTS widgets since API version 9.<br>**Atomic service API**: This API can be used in atomic services since API version 11.|
| fontWeight<sup>10+</sup>  | number \|[FontWeight](ts-appendix-enums.md#fontweight) \|&nbsp;[ResourceStr](ts-types.md#resourcestr) | No  | Yes  | Font weight of the text. For the number type, the value ranges from 100 to 900, at an interval of 100. A larger value indicates a bolder font. For the number type, if the value is not within the range, the default value **400** is used. For the string type, only strings that represent a number, for example, **400**, and the following enumerated values of **FontWeight** are supported: **bold**, **bolder**, **lighter**, **regular**, and **medium**.<br>Default value: **FontWeight.Normal**<br>**NOTE**<br>Percentage values are not supported. If a percentage value is set, the default value is used. The ResourceStr type is supported since API version 20.<br>**Atomic service API**: This API can be used in atomic services since API version 11.|
| borderColor<sup>10+</sup> | [ResourceColor](ts-types.md#resourcecolor)                   | No  | Yes  | Border color of the background.<br>Default value: **Color.Red**<br>**Atomic service API**: This API can be used in atomic services since API version 11.    |
| borderWidth<sup>10+</sup> | [Length](ts-types.md#length)                                 | No  | Yes  | Border width of the background.<br>Default value: **1**<br>Unit: vp<br>**NOTE**<br>Percentage values are not supported. If a percentage value is set, the default value is used.<br>**Atomic service API**: This API can be used in atomic services since API version 11.|
| outerBorderColor<sup>22+</sup> | [ResourceColor](ts-types.md#resourcecolor)                   | No  | Yes  | Color of the background outline.<br>Default value: **Color.White**<br>**Atomic service API**: This API can be used in atomic services since API version 22.  |
| outerBorderWidth<sup>22+</sup> | [LengthMetrics](../js-apis-arkui-graphics.md#lengthmetrics12)                   | No  | Yes  | Stroke width of the background outline.<br>Default value: **0**<br>Unit: vp<br>Percentage values are not supported. If a percentage value is set, the default value is used.<br>**Atomic service API**: This API can be used in atomic services since API version 22.|
| enableAutoAvoidance<sup>22+</sup> | boolean                                 | No  | Yes  | Whether to avoid overlapping when the badge text is extended.<br>true indicates that the text is avoided, and false indicates that the text is not avoided.<br>Default value: **false**<br> **NOTE**<br>1. The avoidance effect is that the badge text is extended to the inside of the component.<br>2. When the width of the outline is greater than 0, the extension start point of the badge is the inner side of the outline.<br>3. When position is set to a specific coordinate value, the badge does not avoid overlapping.<br>**Atomic service API**: This API can be used in atomic services since API version 22.|

> **NOTE**
> When **borderWidth** is set to a value greater than 0 and **borderColor** is different from **badgeColor**, the badge is rendered first, followed by the stroke. Edge pixels are anti-aliased, which produces semi-transparent pixels. This causes the stroke in **badgeColor** to become visible at the four corners. If this visual effect is intended, it is recommended that you use the [Text](ts-basic-components-text.md) component with its [outline](ts-universal-attributes-outline.md) attribute instead of the **Badge** component.

## Attributes

The [universal attributes](ts-component-general-attributes.md) are supported.

## Events

The [universal events](ts-component-general-events.md) are supported.

## Example

### Example 1: Setting the Badge Content

This example uses the value parameter of the [BadgeParamWithNumber](#badgeparamwithnumber) and the count parameter of the [BadgeParamWithString](#badgeparamwithstring) to display different effects when the Badge component receives an empty value, a character, or a number.

```ts
// xxx.ets
@Entry
@Component
struct BadgeExample {
  @Builder
  tabBuilder(index: number) {
    Column() {
      if (index === 2) {
        Badge({
          value: '',
          style: { badgeSize: 6, badgeColor: '#FA2A2D' }
        }) {
          Image('/common/public_icon_off.svg')
            .width(24)
            .height(24)
        }
        .width(24)
        .height(24)
        .margin({ bottom: 4 })
      } else {
        Image('/common/public_icon_off.svg')
          .width(24)
          .height(24)
          .margin({ bottom: 4 })
      }
      Text('Tab')
        .fontColor('#182431')
        .fontSize(10)
        .fontWeight(500)
        .lineHeight(14)
    }.width('100%').height('100%').justifyContent(FlexAlign.Center)
  }

  @Builder
  itemBuilder(value: string) {
    Row() {
      Image('common/public_icon.svg').width(32).height(32).opacity(0.6)
      Text(value)
        .width(177)
        .height(21)
        .margin({ left: 15, right: 76 })
        .textAlign(TextAlign.Start)
        .fontColor('#182431')
        .fontWeight(500)
        .fontSize(16)
        .opacity(0.9)
      Image('common/public_icon_arrow_right.svg').width(12).height(24).opacity(0.6)
    }.width('100%').padding({ left: 12, right: 12 }).height(56)
  }

  build() {
    Column() {
      // Badge of the red dot type
      Text('dotsBadge').fontSize(18).fontColor('#182431').fontWeight(500).margin(24)
      Tabs() {
        TabContent()
          .tabBar(this.tabBuilder(0))
        TabContent()
          .tabBar(this.tabBuilder(1))
        TabContent()
          .tabBar(this.tabBuilder(2))
        TabContent()
          .tabBar(this.tabBuilder(3))
      }
      .width(360)
      .height(56)
      .backgroundColor('#F1F3F5')

      // Create a badge with the given string.
      Column() {
        Text('stringBadge').fontSize(18).fontColor('#182431').fontWeight(500).margin(24)
        List({ space: 12 }) {
          ListItem() {
            Text('list1').fontSize(14).fontColor('#182431').margin({ left: 12 })
          }
          .width('100%')
          .height(56)
          .backgroundColor('#FFFFFF')
          .borderRadius(24)
          .align(Alignment.Start)

          ListItem() {
            Badge({
              value: 'New',
              position: BadgePosition.Right,
              style: { badgeSize: 16, badgeColor: '#FA2A2D' }
            }) {
              Text('list2').width(27).height(19).fontSize(14).fontColor('#182431')
            }.width(49.5).height(19)
            .margin({ left: 12 })
          }
          .width('100%')
          .height(56)
          .backgroundColor('#FFFFFF')
          .borderRadius(24)
          .align(Alignment.Start)
        }.width(336)

        // Create a badge with the given numerical value.
        Text('numberBadge').fontSize(18).fontColor('#182431').fontWeight(500).margin(24)
        List() {
          ListItem() {
            this.itemBuilder('list1')
          }

          ListItem() {
            Row() {
              Image('common/public_icon.svg').width(32).height(32).opacity(0.6)
              Badge({
                count: 1,
                position: BadgePosition.Right,
                style: { badgeSize: 16, badgeColor: '#FA2A2D' }
              }) {
                Text('list2')
                  .width(177)
                  .height(21)
                  .textAlign(TextAlign.Start)
                  .fontColor('#182431')
                  .fontWeight(500)
                  .fontSize(16)
                  .opacity(0.9)
              }.width(240).height(21).margin({ left: 15, right: 11 })

              Image('common/public_icon_arrow_right.svg').width(12).height(24).opacity(0.6)
            }.width('100%').padding({ left: 12, right: 12 }).height(56)
          }

          ListItem() {
            this.itemBuilder('list3')
          }

          ListItem() {
            this.itemBuilder('list4')
          }
        }
        .width(336)
        .height(232)
        .backgroundColor('#FFFFFF')
        .borderRadius(24)
        .padding({ top: 4, bottom: 4 })
        .divider({
          strokeWidth: 0.5,
          color: 'rgba(0,0,0,0.1)',
          startMargin: 60,
          endMargin: 12
        })
      }.width('100%').backgroundColor('#F1F3F5').padding({ bottom: 12 })
    }.width('100%')
  }
}
```

![badge](figures/badge.png)

### Example 2: Controlling the Badge Visibility with Numbers

This example shows how to use the **count** property to toggle the visibility of the **Badge** component. Specifically, when the **count** property is set to **0**, the badge is hidden; when it is set to **1**, the badge becomes visible.

```ts
// This example implements scaling when the badge visibility changes.
@Entry
@Component
struct Index {
  @State badgeCount: number = 1;

  build() {
    Column({ space: 40 }) {
      Badge({
        count: this.badgeCount,
        style: {},
        position: BadgePosition.RightTop,
      }) {
        Image($r('app.media.startIcon'))
          .width(50)
          .height(50)
      }
      .width(55)

      Button('count 0').onClick(() => {
        this.badgeCount = 0;
      })
      Button('count 1').onClick(() => {
        this.badgeCount = 1;
      })
    }
    .margin({ top: 20 })
  }
}
```

![badgeScale](figures/badgeScale.gif)

### Example 3 (Setting the outer border and text extension mode)

In API version 22 and later versions, this example uses the outerBorderColor and outerBorderWidth attributes to set the outer border, and uses the enableAutoAvoidance attribute to control whether to avoid the corner text extension.

```ts
// This example implements the custom outer border and text extension direction of the badge component.
import { LengthMetrics } from '@kit.ArkUI';

@Entry
@Component
struct Index {
  @State badgeValue: string = '1234';
  @State textAvoid:boolean[] = [false, true];
  @State textAvoidIndex: number = 0;
  @State textAvoidString: string [] = ["false", "true"];
  build() {
    Column() {
      Badge({
        value: this.badgeValue,
        style: {
          badgeSize : 30,
          fontSize:20,
          outerBorderColor : Color.Pink,
          outerBorderWidth : LengthMetrics.vp(5),
          enableAutoAvoidance : this.textAvoid[this.textAvoidIndex]
        },
        position:BadgePosition.RightTop
      }) {
        // Replace $r('app.media.startIcon') with the image resource file you use.
        Image($r("app.media.startIcon"))
          .width(80)
          .height(80)
      }
      .direction(Direction.Ltr)
      .margin({ top: 20, bottom: 20 })
      Button("enableAutoAvoidance : " + this.textAvoidString[this.textAvoidIndex])
        .onClick(() => {
          this.textAvoidIndex = (this.textAvoidIndex + 1) % this.textAvoidString.length;
        })
    }
    .width('100%')
    .height('80%')
    .alignItems(HorizontalAlign.Center)
    .justifyContent(FlexAlign.Center)
  }
}
```

![badge2.png](figures/badge2.png)
