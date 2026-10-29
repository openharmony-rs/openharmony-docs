# @ohos.arkui.advanced.PopupV2

PopupV2用于显示特定样式的气泡，适用于提示信息、操作确认或信息通知等需要用户关注或响应的场景。

该组件基于[状态管理（V2）](../../../ui/state-management/arkts-state-management-overview.md#state-management-v2)实现，
 相较于[状态管理（V1）](../../../ui/state-management/arkts-state-management-overview.md#state-management-v1)，状态管理（V2）
 增强了对数据对象的深度观察与管理能力，
 不再局限于组件层级。借助状态管理（V2），开发者可以通过该组件更灵活地控制显示特定样式的气泡，实现更高效的用户界面刷新。

## 子组件

无

## 导入模块

```TypeScript
import { PopupV2, PopupV2InitInfo, PopupV2Button } from '@kit.ArkUI';
```

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [PopupV2](arkts-arkui-arkui-advanced-popupv2-popupv2-f.md#popupv2-1) | PopupV2用于显示特定样式的气泡，适用于提示信息、操作确认或信息通知等需要用户关注或响应的场景。 |

### 接口

| 名称 | 说明 |
| --- | --- |
| [PopupV2Button](arkts-arkui-arkui-advanced-popupv2-popupv2button-i.md) | PopupV2Button定义按钮的相关属性和事件。 |
| [PopupV2InitInfo](arkts-arkui-arkui-advanced-popupv2-popupv2initinfo-i.md) | 定义PopupV2的具体样式参数。 |

## 示例

### 示例1（设置气泡样式）

该示例通过配置[titleModifier](arkts-arkui-arkui-advanced-popupv2-popupv2initinfo-i.md)、[messageModifier](arkts-arkui-arkui-advanced-popupv2-popupv2initinfo-i.md)、[PopupV2Button](arkts-arkui-arkui-advanced-popupv2-popupv2button-i.md)实现气泡样式。

从API版本26.0.0开始，新增titleModifier、messageModifier、PopupV2Button。



```TypeScript
// xxx.ets
import { PopupV2, PopupV2Button, ImageModifier, TextModifier } from '@kit.ArkUI';

@Entry
@ComponentV2
struct PopupExample {

  build() {
    Row() {
      // PopupV2自定义高级组件
      PopupV2 ({
        // 请开发者替换为实际的资源文件
        icon:  $r('app.media.startIcon'),
        iconModifier: new ImageModifier().width(32).height(32).fillColor(Color.White).borderRadius(16),
        title: 'This is a popupv2',
        titleModifier: new TextModifier().fontSize(20).fontColor(Color.Black).fontWeight(FontWeight.Normal),
        message:  'This is the message',
        messageModifier: new TextModifier().fontSize(15).fontColor(Color.Black),
        showClose: false,
        onClose: () => {
          console.info('close Button click');
        },
        buttons: [{
          text: 'confirm',
          action: () => {
            console.info('confirm button click');
          },
          buttonTextModifier: new TextModifier().fontSize(15).fontColor(Color.Black)
        },
          {
            text: 'cancel',
            action: () => {
              console.info('cancel button click');
            },
            buttonTextModifier: new TextModifier().fontSize(15).fontColor(Color.Black)
          }] as [PopupV2Button | undefined, PopupV2Button | undefined]
      })
    }
    .width(300)
    .height(200)
    .borderWidth(2)
    .justifyContent(FlexAlign.Center)
  }
}
```

### 示例2（设置布局方向）

该示例通过配置[direction](arkts-arkui-arkui-advanced-popupv2-popupv2initinfo-i.md)实现镜像布局效果，适用于国际化场景下的RTL（从右到左）布局需求。

从API版本26.0.0开始，新增direction参数。



```TypeScript
// xxx.ets
import { PopupV2, PopupV2Button, ImageModifier, TextModifier } from '@kit.ArkUI';

@Entry
@ComponentV2
struct PopupExample {

  build() {
    Column() {
      // PopupV2自定义高级组件
      PopupV2 ({
        direction: Direction.Rtl,
        // 请开发者替换为实际的资源文件
        icon:  $r('app.media.startIcon'),
        iconModifier: new ImageModifier().width(32).height(32).fillColor(Color.White).borderRadius(16),
        title: 'This is a popupv2',
        titleModifier: new TextModifier().fontSize(20).fontColor(Color.Black).fontWeight(FontWeight.Normal),
        message:  'This is the message',
        messageModifier: new TextModifier().fontSize(15).fontColor(Color.Black),
        showClose: true,
        onClose: () => {
          console.info('close Button click');
        },
        buttons: [{
          text: 'confirm',
          action: () => {
            console.info('confirm button click');
          },
          buttonTextModifier: new TextModifier().fontSize(15).fontColor(Color.Black)
        },
          {
            text: 'cancel',
            action: () => {
              console.info('cancel button click');
            },
            buttonTextModifier: new TextModifier().fontSize(15).fontColor(Color.Black)
          }] as [PopupV2Button | undefined, PopupV2Button | undefined]
      })
    }
    .width('100%')
    .height('100%')
    .justifyContent(FlexAlign.Center)
  }
}
```

### 示例3（设置自定义宽度）

该示例通过配置[maxWidth](arkts-arkui-arkui-advanced-popupv2-popupv2initinfo-i.md)实现自定义宽度效果，适用于内容较长的消息通知等需要调整显示宽度的场景。

从API版本26.0.0开始，新增maxWidth参数。

```TypeScript
// xxx.ets
import { PopupV2, PopupV2Button, ImageModifier, TextModifier } from '@kit.ArkUI';

@Entry
@ComponentV2
struct PopupExample {

  build() {
    Row() {
      // PopupV2自定义高级组件
      PopupV2 ({
        maxWidth: '50%',
        // 请开发者替换为实际的资源文件
        icon:  $r('app.media.startIcon'),
        iconModifier: new ImageModifier().width(32).height(32).fillColor(Color.White).borderRadius(16),
        title: 'This is a popupv2',
        titleModifier: new TextModifier().fontSize(20).fontColor(Color.Black).fontWeight(FontWeight.Normal),
        message:  'This is the message, This is the message, This is the message, This is the message',
        messageModifier: new TextModifier().fontSize(15).fontColor(Color.Black),
        showClose: true,
        onClose: () => {
          console.info('close Button click');
        },
        buttons: [{
          text: 'confirm',
          action: () => {
            console.info('confirm button click');
          },
          buttonTextModifier: new TextModifier().fontSize(15).fontColor(Color.Black)
        },
          {
            text: 'cancel',
            action: () => {
              console.info('cancel button click');
            },
            buttonTextModifier: new TextModifier().fontSize(15).fontColor(Color.Black)
          }] as [PopupV2Button | undefined, PopupV2Button | undefined]
      })
    }
    .width(400)
    .height(200)
    .borderWidth(2)
    .justifyContent(FlexAlign.Center)
  }
}
```
