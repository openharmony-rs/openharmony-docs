# AudioRendererInfo

Describes audio renderer information.

**Since:** 8

**System capability:** SystemCapability.Multimedia.Audio.Core

## Modules to Import

```TypeScript
import { audio } from '@kit.AudioKit';
```

## content

```TypeScript
content?: ContentType
```

Audio content type.

**Type:** [ContentType](arkts-audio-audio-contenttype-e.md)

**Since:** 8

**Deprecated since:** 10

**Substitutes:** usage

**System capability:** SystemCapability.Multimedia.Audio.Core

## rendererFlags

```TypeScript
rendererFlags: number
```

Flags that control the renderer behavior.

Set this parameter to **0**.

**Type:** number

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Multimedia.Audio.Core

## usage

```TypeScript
usage: StreamUsage
```

Audio stream usage.

**Type:** [StreamUsage](arkts-audio-audio-streamusage-e.md)

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Multimedia.Audio.Core

## volumeMode

```TypeScript
volumeMode?: AudioVolumeMode
```

Audio volume mode config. If volumeMode is set to [APP_INDIVIDUAL](arkts-audio-audio-audiovolumemode-e.md#app_individual), this audio renderer will be affected by app volume percentage set by [setAppVolumePercentage](arkts-audio-audio-audiovolumemanager-i.md#setappvolumepercentage)

**Type:** [AudioVolumeMode](arkts-audio-audio-audiovolumemode-e.md)

**Since:** 19

**System capability:** SystemCapability.Multimedia.Audio.Volume
