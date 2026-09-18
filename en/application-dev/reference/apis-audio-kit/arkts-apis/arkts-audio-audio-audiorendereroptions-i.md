# AudioRendererOptions

Describes audio renderer configurations.

**Since:** 8

**System capability:** SystemCapability.Multimedia.Audio.Renderer

## Modules to Import

```TypeScript
import { audio } from '@kit.AudioKit';
```

## privacyType

```TypeScript
privacyType?: AudioPrivacyType
```

Whether the audio stream can be recorded by other applications. The default value is **0**.

**Type:** [AudioPrivacyType](arkts-audio-audio-audioprivacytype-e.md)

**Since:** 10

**System capability:** SystemCapability.Multimedia.Audio.PlaybackCapture

## rendererInfo

```TypeScript
rendererInfo: AudioRendererInfo
```

Describes audio renderer information.

**Type:** [AudioRendererInfo](arkts-audio-audio-audiorendererinfo-i.md)

**Since:** 8

**System capability:** SystemCapability.Multimedia.Audio.Renderer

## streamInfo

```TypeScript
streamInfo: AudioStreamInfo
```

Describes audio stream information.

**Type:** [AudioStreamInfo](arkts-audio-audio-audiostreaminfo-i.md)

**Since:** 8

**System capability:** SystemCapability.Multimedia.Audio.Renderer
