# AudioPlaybackCaptureMode

Defines mode for playback capture, each mode means different target streams to capture.

**Since:** 26.0.0

**System capability:** SystemCapability.Multimedia.Audio.PlaybackCapture

## MODE_DEFAULT

```TypeScript
MODE_DEFAULT = 0x0
```

Default mode. Capture most of the audio streams, except tone streams and privacy streams.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Audio.PlaybackCapture

## MODE_MEDIA

```TypeScript
MODE_MEDIA = 0x1
```

Media mode. Capture media, voice message and also unknown streams.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Audio.PlaybackCapture

## MODE_EXCLUDING_SELF

```TypeScript
MODE_EXCLUDING_SELF = 0x8000
```

Excluding self mode. Capture streams excluding the audio played by application itself.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Audio.PlaybackCapture
