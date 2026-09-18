# AudioRendererTargetParams (System API)

Options for setting the render target of an audio renderer. This parameter takes effect only when the target is non-PLAYBACK. In other cases, this parameter does not need to be specified and does not take effect even if specified. Both uid and streamId must be specified.

**Since:** 26.0.0

**System capability:** SystemCapability.Multimedia.Audio.Renderer

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { audio } from '@kit.AudioKit';
```

## streamId

```TypeScript
streamId: number
```

The stream ID of the [SOURCE_TYPE_VOICE_COMMUNICATION](arkts-audio-audio-sourcetype-e.md#source_type_voice_communication) capture stream identified by uid. This stream is the injection target for the render stream. It is valid only when the target is non-PLAYBACK.

**Type:** number

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Audio.Renderer

**System API:** This is a system API.

## uid

```TypeScript
uid: number
```

The application UID of the target capture stream into which the render stream is injected. It is valid only when the target is non-PLAYBACK. The value should be an integer.

**Type:** number

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Audio.Renderer

**System API:** This is a system API.
