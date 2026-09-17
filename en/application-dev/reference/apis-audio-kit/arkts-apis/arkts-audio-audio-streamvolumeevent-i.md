# StreamVolumeEvent

Describes the event received by the application when the audio stream volume is changed.

**Since:** 20

**System capability:** SystemCapability.Multimedia.Audio.Volume

## Modules to Import

```TypeScript
import { audio } from '@kit.AudioKit';
```

## previousVolume

```TypeScript
previousVolume?: number
```

Volume level before change.

**Type:** number

**Since:** 23

**System capability:** SystemCapability.Multimedia.Audio.Volume

## streamUsage

```TypeScript
streamUsage: StreamUsage
```

Audio stream for which the volume changes.

**Type:** [StreamUsage](arkts-audio-audio-streamusage-e.md)

**Since:** 20

**System capability:** SystemCapability.Multimedia.Audio.Volume

## updateUi

```TypeScript
updateUi: boolean
```

Whether to show the volume change in UI. **true** to show, **false** otherwise.

**Type:** boolean

**Since:** 20

**System capability:** SystemCapability.Multimedia.Audio.Volume

## volume

```TypeScript
volume: number
```

Volume.

**Type:** number

**Since:** 20

**System capability:** SystemCapability.Multimedia.Audio.Volume
