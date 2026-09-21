# Badge

The **Badge** component is a container that can be attached to another component for notification and reminder purposes.

## Child Components

This component supports only one child component.

> **NOTE:** 
> 
> - Allowed child component types: built-in and custom components, including rendering control types ([if/else](../../../ui/rendering-control/arkts-rendering-control-ifelse.md), [ForEach](arkts-arkui-foreach-comp-attribute.md#foreachattribute), and [LazyForEach](arkts-arkui-lazyforeach-comp.md#lazy_for_each)).
> 
> - A custom component defaults to a width and height of 0. You must explicitly set its width and height; otherwise,the **Badge** component will not be displayed.
> 
> - When there are multiple child components, only the last child component is displayed on the UI. However, the status update of other child components will still cause the badge and its child components to be re-rendered.
> 
> - Child component layout is independent and does not automatically adjust to avoid overlapping with the badge.

## Badge

```TypeScript
Badge(value: BadgeParamWithNumber)
```

Creates a badge with the given numerical value.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [BadgeParamWithNumber](arkts-arkui-badge-comp-badgeparamwithnumber-i.md) | Yes | Options of the numeric badge. |

## Badge

```TypeScript
Badge(value: BadgeParamWithString)
```

Creates a badge with the given string.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [BadgeParamWithString](arkts-arkui-badge-comp-badgeparamwithstring-i.md) | Yes | Options of the string-type badge. |

## Summary

### Interfaces

| Name | Description |
| --- | --- |
| [BadgeParam](arkts-arkui-badge-comp-badgeparam-i.md) | Provides basic parameters for creating a badge. |
| [BadgeParamWithNumber](arkts-arkui-badge-comp-badgeparamwithnumber-i.md) | Inherits from [BadgeParam](arkts-arkui-badge-comp-badgeparam-i.md) and has all attributes of **BadgeParam**. |
| [BadgeParamWithString](arkts-arkui-badge-comp-badgeparamwithstring-i.md) | Inherits from [BadgeParam](arkts-arkui-badge-comp-badgeparam-i.md) and has all attributes of **BadgeParam**. |
| [BadgeStyle](arkts-arkui-badge-comp-badgestyle-i.md) | Describes the badge style. It includes the font color, font size, badge color, badge size, etc. |

### Enums

| Name | Description |
| --- | --- |
| [BadgePosition](arkts-arkui-badge-comp-badgeposition-e.md) | Enumerates the display positions of a badge. |

## Examples

### Example 1: Setting Badge Component Content

This example uses the input parameter count of [BadgeParamWithNumber](arkts-arkui-badge-comp-badgeparamwithnumber-i.md) and the input parameter value of [BadgeParamWithString](arkts-arkui-badge-comp-badgeparamwithstring-i.md) to display different effects of the badge component when null, a character, or a number is passed in.



```TypeScript
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
      // Badge component of the dot type.
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

      // Badge component created based on a character.
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

        // Badge component created based on a number.
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

### Example 2: Setting a Number to Control Badge Display

This example uses the count attribute to hide and show the badge component when the number is set to 0 and 1.



```TypeScript
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

### Example 3: Setting the Outer Border and Text Extension Mode

Since API version 22, this example uses the outerBorderColor and outerBorderWidth attributes to set the outer border, and uses the enableAutoAvoidance attribute to control whether to avoid obstacles when the badge text is extended for display.

```TypeScript
// This example implements custom outer border and text extension direction for the Badge component.
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
        // $r('app.media.startIcon') needs to be replaced with the image resource file required by the developer.
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
