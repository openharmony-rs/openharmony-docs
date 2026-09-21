# @ohos.multimedia.avVolumePanel(Defines a panel to set the system audio output volume.)

## Modules to Import

```TypeScript
import { AVVolumePanel, AVVolumePanelParameter } from '@kit.AudioKit';
```

## Summary

### Classes

| Name | Description |
| --- | --- |
| [AVVolumePanelParameter](arkts-audio-multimedia-avvolumepanel-avvolumepanelparameter-c.md) | Declare custom parameters used for volume panel. |

### Structs

| Name | Description |
| --- | --- |
| [AVVolumePanel](arkts-audio-multimedia-avvolumepanel-avvolumepanel-s.md) | A panel to set the system audio output volume. |

## Examples

To see how the volume panel works, refer to the sample code below. To experience the volume adjustment, you'll need to change the volume value or press the volume buttons.

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
