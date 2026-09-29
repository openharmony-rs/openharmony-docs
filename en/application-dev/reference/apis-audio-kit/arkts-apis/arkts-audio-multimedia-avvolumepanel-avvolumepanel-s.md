# AVVolumePanel

```TypeScript
export declare struct AVVolumePanel
```

A panel to set the system audio output volume.

**Since:** 12

**Decorator:** @Component

<!--Device-unnamed-export declare struct AVVolumePanel--><!--Device-unnamed-export declare struct AVVolumePanel-End-->

**System capability:** SystemCapability.Multimedia.Audio.Volume

## Modules to Import

```TypeScript
import { AVVolumePanel, AVVolumePanelParameter } from '@kit.AudioKit';
```

## volumeLevel

```TypeScript
volumeLevel?: number
```

Sets the device volume through the volume panel. The value should be between mininum and maxinum current device volume, otherwise it will be discarded.

**Type:** number

**Since:** 12

**Decorator:** @Prop

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-AVVolumePanel-volumeLevel?: number--><!--Device-AVVolumePanel-volumeLevel?: number-End-->

**System capability:** SystemCapability.Multimedia.Audio.Volume

## volumeParameter

```TypeScript
volumeParameter?: AVVolumePanelParameter
```

Sets the custom parameters of volume panel.

**Type:** [AVVolumePanelParameter](arkts-audio-multimedia-avvolumepanel-avvolumepanelparameter-c.md)

**Since:** 12

**Decorator:** @Prop

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-AVVolumePanel-volumeParameter?: AVVolumePanelParameter--><!--Device-AVVolumePanel-volumeParameter?: AVVolumePanelParameter-End-->

**System capability:** SystemCapability.Multimedia.Audio.Volume
