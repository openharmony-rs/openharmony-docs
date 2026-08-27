# Badge

信息标记容器组件，可以附加在单个组件上用于信息提醒。支持数字、字符串和圆点三种标记形式，可自定义标记样式（文本颜色、大小、标记颜色和大小）和显示位置。适用于需要提示用户有新消息或未读消息的场景，例如未读消息计数、新功能提示等，帮助用户 快速识别和关注重要信息，提升用户体验。

## 子组件

支持单个子组件。

> **说明：**
> 
> - 子组件类型：系统组件和自定义组件，支持渲染控制类型（[if/else](../../../ui/rendering-control/arkts-rendering-control-ifelse.md)、
> ForEach和LazyForEach）。
> 
> - 自定义组件宽高默认为0，需要给其设置宽高，否则标记组件将不显示。
> 
> - 当存在多个子组件时，只有最后一个子组件会在界面上显示，但其余子组件的状态更新仍会触发Badge及其包含的所有子组件重新布局渲染。
> 
> - 不影响子组件布局，即不会主动规避子组件内容。

## Badge

```TypeScript
Badge(value: BadgeParamWithNumber)
```

根据数字创建标记组件。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数:**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [BadgeParamWithNumber](arkts-arkui-badgeparamwithnumber-i.md) | 是 | 数字标记组件参数，用于配置根据数字创建的Badge组件，包含消息数、显示位置和样式等属性。 |

## Badge

```TypeScript
Badge(value: BadgeParamWithString)
```

根据字符串创建标记组件。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数:**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [BadgeParamWithString](arkts-arkui-badgeparamwithstring-i.md) | 是 | 字符串标记组件参数。 |

## 汇总

### 接口

| 名称 | 说明 |
| --- | --- |
| [BadgeParam](arkts-arkui-badgeparam-i.md) | 包含用于创建Badge组件的基础参数。 |
| [BadgeParamWithNumber](arkts-arkui-badgeparamwithnumber-i.md) | BadgeParamWithNumber继承自[BadgeParam](arkts-arkui-badgeparam-i.md)，具有BadgeParam的全部属性。 |
| [BadgeParamWithString](arkts-arkui-badgeparamwithstring-i.md) | BadgeParamWithNumber继承自[BadgeParam](arkts-arkui-badgeparam-i.md)，具有BadgeParam的全部属性。 |
| [BadgeStyle](arkts-arkui-badgestyle-i.md) | Badge的样式。包括文本颜色、大小、字重、标记颜色和标记大小。 |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [BadgePosition](arkts-arkui-badgeposition-e.md) | 标记显示位置。 |

## 示例

该示例通过[BadgeParamWithNumber](#badgeparamwithnumber对象说明)的入参count、[BadgeParamWithString](#badgeparamwithstring对象说明)的入参value，实现了传入空值、字符、数字时标记组件展现不同的效果。

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
      // 红点类型的标记组件
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

      // 根据字符创建的标记组件
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

        // 根据数字创建的标记组件
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

该示例通过count属性，实现了设置数字0和1时标记组件的隐藏和显示效果。

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

从API version 22开始，该示例使用outerBorderColor和outerBorderWidth属性设置外描边，通过enableAutoAvoidance属性控制增加角标文本延伸显示时是否避让。

```TypeScript
// 该示例实现了Badge组件自定义外描边和文本延伸方向
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
        // $r('app.media.startIcon')需要替换为开发者所需的图像资源文件。
        Image($r('app.media.startIcon'))
          .width(80)
          .height(80)
      }
      .direction(Direction.Ltr)
      .margin({ top: 20, bottom: 20 })
      Button('enableAutoAvoidance ： ' + this.textAvoidString[this.textAvoidIndex])
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
