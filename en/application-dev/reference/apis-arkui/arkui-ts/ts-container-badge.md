# Badge
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @Zhang-Dong-hui-->
<!--Designer: @xiangyuan6-->
<!--Tester:@jiaoaozihao-->
<!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=45d7a7f3a546f09d883db6316888aa64247d94c0 translatedAt=2026-11-17T03:45:19.116Z pushedAt=2026-11-19T08:20:04.840Z nl=1 -->

A badge container component that can be attached to a single component for information reminders. It supports three badge formats: number, string, and dot. You can customize the badge style (text color, size, badge color, and size) and display position. It is suitable for scenarios where users need to be reminded of new or unread messages, such as unread message counts and new feature prompts, helping users quickly identify and focus on important information and improving user experience.

>  **NOTE**
>
> This component is supported since API version 7. Updates will be marked with a superscript to indicate their earliest API version.


## Child Components

This component supports only one child component.

>  **NOTE**
>
> - Child component types: system components and custom components, with support for rendering control types ([if/else](../../../ui/rendering-control/arkts-rendering-control-ifelse.md), [ForEach](../../../ui/rendering-control/arkts-rendering-control-foreach.md), and [LazyForEach](../../../ui/rendering-control/arkts-rendering-control-lazyforeach.md)).
>
> - The width and height of a custom component are 0 by default. You need to set the width and height for it; otherwise, the badge component will not display.
>
> - When there are multiple child components, only the last child component is displayed on the UI, but state updates of the remaining child components still trigger the re-layout and re-rendering of the **Badge** and all child components it includes.
>
> - The Badge does not affect the layout of child components, that is, it does not actively avoid the component content.


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
| value | [BadgeParamWithNumber](#badgeparamwithnumber)| Yes | Parameter of the number badge component, used to configure the Badge component created based on a number, including attributes such as message count, display position, and style.|

### Badge

Badge(value: BadgeParamWithString)

Creates a badge with the given string.

**Widget capability**: This API can be used in ArkTS widgets since API version 9.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

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
| position | [BadgePosition](#badgeposition)\|[Position<sup>10+</sup>](ts-types.md#position)  | No | Yes | Badge display position.<br>Default value: **BadgePosition.RightTop** <br>**Note:** <br> **Position**, as an input parameter, does not support setting percentage; when set to an invalid value, it is handled as **(0,0)**, where **(0,0)** is the upper-left corner of the component.<br>When **BadgePosition** is used as an input parameter, it follows the [Direction](ts-appendix-enums.md#direction) attribute to control the mirrored display.|
| style | [BadgeStyle](#badgestyle) | No | No | The **Badge** component can set styles, supporting setting the text color, size, badge color, and badge size. |


## BadgeParamWithNumber

Inherits from [BadgeParam](#badgeparam) and has all attributes of **BadgeParam**.

**Widget capability**: This API can be used in ArkTS widgets since API version 9.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name| Type| Read-Only| Optional| Description|
| -------- | -------- | -------- | -------- | -------- |
| count | number | No | No | Number of reminder messages.<br>**NOTE**<br>When the value is less than or equal to 0 and less than **maxCount**, the badge is not displayed.<br>Value range: [-2147483648, 2147483647]. If the value is out of range, 4294967296 is added to or subtracted from it to keep it within the range. If the value is not an integer, the decimal part is discarded, for example, 5.5 becomes 5. |
| maxCount | number | No | Yes | Maximum number of messages. When the number exceeds the maximum, only **maxCount+** is displayed. For example, when **maxCount** is 99, `99+` is displayed.<br>Default value: **99**<br>Value range: [-2147483648, 2147483647]. If the value is out of range, 4294967296 is added to or subtracted from it to keep it within the range. If the value is not an integer, the decimal part is discarded, for example, 5.5 becomes 5. |

## BadgeParamWithString

Inherits from [BadgeParam](#badgeparam) and has all attributes of **BadgeParam**.

**Widget capability**: This API can be used in ArkTS widgets since API version 9.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name| Type| Read-Only| Optional| Description|
| -------- | -------- | -------- | -------- | -------- |
| value | [ResourceStr](ts-types.md#resourcestr) | No | No | Text string of the prompt content.<br>**Note:** <br>When value is an empty string, the text is not displayed and only the dot badge is displayed.<br>Since API version 20, the ResourceStr type is supported. |

## BadgePosition

Enumerates the badge display positions.

**Widget capability**: This API can be used in ArkTS widgets since API version 9.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name| Value| Description|
| -------- | -------- |-------- |
| RightTop | - | The badge is displayed in the upper right corner. |
| Right | - | The badge is displayed in the vertical center on the right. |
| Left | - | The badge is displayed in the vertical center on the left. |

## BadgeStyle

Defines the style of a badge, including the text color, size, font weight, badge color, and badge size.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name                     | Type                                                        | Read-Only| Optional| Description                                                        |
| ------------------------- | ------------------------------------------------------------ | ---- | ---- | ------------------------------------------------------------ |
| color                     | [ResourceColor](ts-types.md#resourcecolor)                   | No   | Yes   | Text color.<br>Default value: **Color.White**<br>**Widget capability**: This API can be used in ArkTS widgets since API version 9.<br>**Atomic service API**: This API can be used in atomic services since API version 11. |
| fontSize                  | number&nbsp;\|&nbsp;[ResourceStr](ts-types.md#resourcestr)   | No   | Yes   | Text size. The string type supports only the string form of a number value, which can carry a unit. The supported units are "px", "vp", "fp", and "lpx", for example, "10" and "10fp". When no unit is carried, the default unit is "fp".<br>Default value: 10vp<br>Default unit: fp<br>Value range: greater than 0; when the value is 0, the text is not displayed; when the value is less than 0, the default value is used.<br>**NOTE**<br>1. This parameter does not support setting percentage. When set to a percentage, the default value is used.<br>2. The ResourceStr type is supported since API version 20.<br>**Widget capability**: This API can be used in ArkTS widgets since API version 9.<br>**Atomic service API**: This API can be used in atomic services since API version 11. |
| badgeSize                 | number&nbsp;\|&nbsp;[ResourceStr](ts-types.md#resourcestr)   | No   | Yes   | Badge size. The string type supports only the string form of a number value, which can carry a unit. The supported units are "px", "vp", "fp", and "lpx", for example, "16" and "16fp". When no unit is carried, the default unit is "fp".<br>Default value: 16vp<br>Default unit: fp<br>Value range: greater than 0; when the value is 0, the **Badge** is not displayed; when the value is less than 0, the default value is used.<br>**NOTE**<br>1. This parameter does not support setting percentage. When set to a percentage, the default value is used.<br>2. The **ResourceStr** type is supported since API version 20.<br>3. When **fontSize** is set and **badgeSize** is less than **fontSize**, **badgeSize** takes effect as **fontSize**.<br>**Widget capability**: This API can be used in ArkTS widgets since API version 9.<br>**Atomic service API**: This API can be used in atomic services since API version 11. |
| badgeColor                | [ResourceColor](ts-types.md#resourcecolor)                   | No   | Yes   | Badge color.<br>Default value: **Color.Red**<br>**Widget capability**: This API can be used in ArkTS widgets since API version 9.<br>**Atomic service API**: This API can be used in atomic services since API version 11. |
| fontWeight<sup>10+</sup>  | number&nbsp;\|&nbsp;[FontWeight](ts-appendix-enums.md#fontweight)&nbsp;\|&nbsp;[ResourceStr](ts-types.md#resourcestr) | No   | Yes   | Font weight of the text. The value range of the number type is [100, 900], with an interval of 100. The larger the value, the bolder the font. When the number type is set to a value outside the value range, the default value 400 is used. The string type supports only the string form of a number value, for example, "400", as well as "bold", "bolder", "lighter", "regular", and "medium", which correspond to the respective enum values in **FontWeight**.<br>Default value: **FontWeight.Normal**<br>**NOTE**<br>This parameter does not support setting percentage. When set to a percentage, the default value is used. The ResourceStr type is supported since API version 20.<br>**Atomic service API**: This API can be used in atomic services since API version 11.<br>**Model restriction:** This API can be used only under the stage model. |
| borderColor<sup>10+</sup> | [ResourceColor](ts-types.md#resourcecolor)                   | No   | Yes   | Board stroke color.<br>Default value: **Color.Red**<br>**Atomic service API**: This API can be used in atomic services since API version 11.<br>**Model restriction:** This API can be used only under the stage model.     |
| borderWidth<sup>10+</sup> | [Length](ts-types.md#length)                                 | No   | Yes   | Board stroke width.<br>Default value: **1**<br>Unit: vp<br>**NOTE**<br>This parameter does not support setting percentage. When set to a percentage, the default value is used.<br>**Atomic service API**: This API can be used in atomic services since API version 11.<br>**Model restriction:** This API can be used only under the stage model. |
| outerBorderColor<sup>22+</sup> | [ResourceColor](ts-types.md#resourcecolor)                   | No   | Yes   | Board outer stroke color.<br>Default value: **Color.White**<br>**Atomic service API**: This API can be used in atomic services since API version 22.<br>**Model restriction:** This API can be used only under the stage model.   |
| outerBorderWidth<sup>22+</sup> | [LengthMetrics](../js-apis-arkui-graphics.md#lengthmetrics12)                   | No   | Yes   | Board outer stroke width.<br>Default value: **0**<br>Unit: vp<br>This parameter does not support setting percentage. When set to a percentage, the default value is used.<br>**Atomic service API**: This API can be used in atomic services since API version 22.<br>**Model restriction:** This API can be used only under the stage model. |
| enableAutoAvoidance<sup>22+</sup> | boolean                                 | No   | Yes   | Whether to avoid the badge text when it extends.<br>**true** indicates avoidance, and **false** indicates no avoidance.<br>Default value: **false**<br> **NOTE**<br>1. The avoidance effect is that the badge text extends and is displayed within the component.<br>2. When the width of the outer stroke is greater than 0, the extension start point of the badge is the inner side of the outer stroke.<br>3. When **position** is set to a specific coordinate value, the badge does not perform avoidance.<br>**Atomic service API**: This API can be used in atomic services since API version 22.<br>**Model restriction:** This API can be used only under the stage model.|

> **NOTE**
> When `borderWidth` is greater than 0 and the colors of `borderColor` and `badgeColor` are different, the badge is drawn first and then the border. Because edge pixels are anti-aliased, semi-transparent pixels are generated, and border lines in the `badgeColor` color appear at the four corners. To implement such a scenario, you are advised to use the [Text](ts-basic-components-text.md) component and set [outline](ts-universal-attributes-outline.md#outline) instead of the Badge component.

## Attributes

The [universal attributes](ts-component-general-attributes.md) are supported.

## Events

The [universal events](ts-component-general-events.md) are supported.

## Examples

### Example 1: Setting the Badge Content

This example uses the input parameter **count** of [BadgeParamWithNumber](#badgeparamwithnumber) and the input parameter **value** of [BadgeParamWithString](#badgeparamwithstring) to display different effects of the badge component when null, a character, or a number is passed in.

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

### Example 3: Setting the Outer Border and Text Extension Mode

Since API version 22, this example uses the **outerBorderColor** and **outerBorderWidth** attributes to set the outer border, and uses the **enableAutoAvoidance** attribute to set whether to avoid the badge text extension.

```ts
// This example implements the custom outer border and text extension direction of the Badge component.
import { LengthMetrics } from '@kit.ArkUI';

@Entry
@Component
struct Index {
  @State badgeValue: string = '1234';
  @State textAvoid: boolean[] = [false, true];
  @State textAvoidIndex: number = 0;
  @State textAvoidString: string [] = ['false', 'true'];
  build() {
    Column() {
      Badge({
        value: this.badgeValue,
        style: {
          badgeSize: 30,
          fontSize: 20,
          outerBorderColor : Color.Pink,
          outerBorderWidth : LengthMetrics.vp(5),
          enableAutoAvoidance : this.textAvoid[this.textAvoidIndex]
        },
        position: BadgePosition.RightTop
      }) {
        // Replace $r('app.media.startIcon') with the image resource file you use.
        Image($r('app.media.startIcon'))
          .width(80)
          .height(80)
      }
      .direction(Direction.Ltr)
      .margin({ top: 20, bottom: 20 })
      Button('enableAutoAvoidance : ' + this.textAvoidString[this.textAvoidIndex])
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
