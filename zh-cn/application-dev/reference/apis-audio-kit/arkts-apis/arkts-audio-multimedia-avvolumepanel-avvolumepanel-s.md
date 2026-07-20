# AVVolumePanel

音量面板，可用于在当前应用内展示音量调节面板。

**起始版本：** 12

**装饰器类型：** @Component

<!--Device-unnamed-export declare struct AVVolumePanel--><!--Device-unnamed-export declare struct AVVolumePanel-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Volume

## 导入模块

```TypeScript
import { AVVolumePanelParameter, AVVolumePanel } from '@kit.AudioKit';
```

## volumeLevel

```TypeScript
volumeLevel?: number
```

通过音量面板设置的音量值。

该值应介于当前设备音量的最小值和最大值之间。

如果该值大于当前设备音量的最大值，则视为设置最大音量值。

如果该值小于当前设备音量的最小值，则视为设置最小音量值。

获取设备的最大值、最小值和当前值，可参考[AudioVolumeGroupManager](arkts-audio-audio-audiovolumegroupmanager-i.md)。

**类型：** number

**起始版本：** 12

**装饰器类型：** @Prop

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-AVVolumePanel-volumeLevel?: number--><!--Device-AVVolumePanel-volumeLevel?: number-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Volume

## volumeParameter

```TypeScript
volumeParameter?: AVVolumePanelParameter
```

设置音量面板的自定义参数。

如果不设置该参数，则为系统音量条。

**类型：** AVVolumePanelParameter

**起始版本：** 12

**装饰器类型：** @Prop

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-AVVolumePanel-volumeParameter?: AVVolumePanelParameter--><!--Device-AVVolumePanel-volumeParameter?: AVVolumePanelParameter-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Volume

