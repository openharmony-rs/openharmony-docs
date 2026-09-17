# SourceType

Enumerates the types of audio streams captured.

**Since:** 8

**System capability:** SystemCapability.Multimedia.Audio.Core

## SOURCE_TYPE_INVALID

```TypeScript
SOURCE_TYPE_INVALID = -1
```

Invalid audio source.

**Since:** 8

**System capability:** SystemCapability.Multimedia.Audio.Core

## SOURCE_TYPE_MIC

```TypeScript
SOURCE_TYPE_MIC = 0
```

Mic source.

**Since:** 8

**System capability:** SystemCapability.Multimedia.Audio.Core

## SOURCE_TYPE_VOICE_RECOGNITION

```TypeScript
SOURCE_TYPE_VOICE_RECOGNITION = 1
```

Voice recognition source.

**Since:** 9

**System capability:** SystemCapability.Multimedia.Audio.Core

## SOURCE_TYPE_PLAYBACK_CAPTURE

```TypeScript
SOURCE_TYPE_PLAYBACK_CAPTURE = 2
```

Playback capture source type.

**Since:** 10

**Deprecated since:** 12

**Substitutes:** OH_AVScreenCapture in native interface.

**System capability:** SystemCapability.Multimedia.Audio.PlaybackCapture

## SOURCE_TYPE_VOICE_COMMUNICATION

```TypeScript
SOURCE_TYPE_VOICE_COMMUNICATION = 7
```

Voice communication source. (The 3A algorithm is not enabled if recording is started independently. It is enabled when the AudioRenderer of the [STREAM_USAGE_VOICE_COMMUNICATION](arkts-audio-audio-streamusage-e.md) or [STREAM_USAGE_VIDEO_COMMUNICATION](arkts-audio-audio-streamusage-e.md) type is also used to start playback.)

**Since:** 8

**System capability:** SystemCapability.Multimedia.Audio.Core

## SOURCE_TYPE_VOICE_MESSAGE

```TypeScript
SOURCE_TYPE_VOICE_MESSAGE = 10
```

Voice message source.

**Since:** 12

**System capability:** SystemCapability.Multimedia.Audio.Core

## SOURCE_TYPE_CAMCORDER

```TypeScript
SOURCE_TYPE_CAMCORDER = 13
```

Camcorder source type.

**Since:** 13

**System capability:** SystemCapability.Multimedia.Audio.Core

## SOURCE_TYPE_UNPROCESSED

```TypeScript
SOURCE_TYPE_UNPROCESSED = 14
```

Unprocessed source type.

**Since:** 14

**System capability:** SystemCapability.Multimedia.Audio.Core

## SOURCE_TYPE_LIVE

```TypeScript
SOURCE_TYPE_LIVE = 17
```

Live broadcast source type.

**Since:** 20

**System capability:** SystemCapability.Multimedia.Audio.Core
