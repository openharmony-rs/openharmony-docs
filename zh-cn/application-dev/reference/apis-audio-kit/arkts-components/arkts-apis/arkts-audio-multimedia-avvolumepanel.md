# @ohos.multimedia.avVolumePanel(音量面板)

## 导入模块

```TypeScript
import { AVVolumePanel, AVVolumePanelParameter } from '@kit.AudioKit';
```

## 汇总

### 类

| 名称 | 说明 |
| --- | --- |
| [AVVolumePanelParameter](arkts-audio-multimedia-avvolumepanel-avvolumepanelparameter-c.md) | 音量面板参数设置。 |

### 结构体

| 名称 | 说明 |
| --- | --- |
| [AVVolumePanel](arkts-audio-multimedia-avvolumepanel-avvolumepanel-s.md) | 音量面板，可用于在当前应用内展示音量调节面板。 |

## 示例

音量面板功能的示例说明参考如下。需要实际修改volume值或者按压音量按键体验调节音量效果。

```TypeScript
import { AVVolumePanel } from '@kit.AudioKit';

@Entry
@Component
struct Index {

  @State volume: number = 0;

  build() {
    Row() {
      Column() {
        AVVolumePanel({
          volumeLevel: this.volume,
          volumeParameter: {
            position: {
              x: 100,
              y: 200
            }
          }
        })
      }
    }.width('50%').height('50%')
  }
}
```
