# 点击音效

设置组件是否启用默认点击音效。

>  **说明：**
>
> - 本模块同时支持ArkTS-Dyn、ArkTS-Sta。
>
> - 从API version 24开始支持。后续版本如有新增内容，则采用上角标单独标记该内容的起始版本。

## enableClickSoundEffect

ArkTS-Dyn: enableClickSoundEffect(enabled: boolean | undefined): T

ArkTS-Sta: enableClickSoundEffect(enabled: boolean | undefined): this

设置组件是否启用默认点击音效。是否能够发音依赖设备声音相关的设置，如静音模式下不会播放音效。

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API version 24开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**设备行为差异**：该接口在TV中可正常调用，在其他设备中无效果。

**ArkTS-Dyn起始版本：** 24

**ArkTS-Sta起始版本：** 24

**参数：**

| 参数名 | 类型                                                  | 必填 | 说明                                                         |
| ------ | ----------------------------------------------------- | ---- | ------------------------------------------------------------ |
| enabled  | ArkTS-Dyn: boolean&nbsp;\|&nbsp;undefined <br/>ArkTS-Sta: boolean&nbsp;\|&nbsp;undefined | 是   | 设置此组件是否启用默认点击音效。<br/>true表示启用默认点击音效；false表示禁用默认点击音效。<br/>值为undefined时，启用默认点击音效。 |

**返回值：**

| 类型   | 说明                     |
| ------ | ------------------------ |
| T | 返回当前组件。 |

## 示例
### 示例1（启用默认点击音效）

该示例通过配置enableClickSoundEffect属性，实现组件禁用默认点击音效，开发者可以在onClick回调中调用音频相关接口自定义发音。自定义发音可参考[SoundPool播放短音频指南](../../../media/media/using-soundpool-for-playback.md)。

从API version 24开始，新增[enableClickSoundEffect](#enableclicksoundeffect)属性。
ArkTS-Dyn示例：
```ts
@Entry
@Component
struct Index {
  build() {
    Column() {
      Button('点击')
        .fontSize('20dp')
        .height('60')
        .width('200')
        .enableClickSoundEffect(false)
        .onClick(() => {
          // 此处自定义发音，参考SoundPool播放短音频指南
        })
    }
    .width('100%')
    .height('100%')
    .justifyContent(FlexAlign.Center)
    .alignItems(HorizontalAlign.Center)
  }
}
```

ArkTS-Sta示例：
```ts
import {
  Entry, Column, Component, ClickEvent, Button, FlexAlign, HorizontalAlign
} from '@ohos.arkui.component'

@Entry
@Component
struct Example {
  build() {
    Column() {
      Button('点击')
        .fontSize('20dp')
        .height('60')
        .width('200')
        .enableClickSoundEffect(false)
        .onClick(() => {
          // 此处自定义发音，参考SoundPool播放短音频指南
        })
    }
    .width('100%')
    .height('100%')
    .justifyContent(FlexAlign.Center)
    .alignItems(HorizontalAlign.Center)
  }
}
```