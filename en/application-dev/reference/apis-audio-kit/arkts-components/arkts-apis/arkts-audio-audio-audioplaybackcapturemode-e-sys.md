# AudioPlaybackCaptureMode

Defines mode for playback capture, each mode means different target streams to capture.

**Since:** 26.0.0

**System capability:** SystemCapability.Multimedia.Audio.PlaybackCapture

## MODE_ONLY_VOIP

```TypeScript
MODE_ONLY_VOIP = 0x4000
```

Only voip mode. Capture only voice/video communication streams. If [playbackCaptureUid](arkts-audio-audio-audiocaptureroptions-i-sys.md#playbackcaptureuid) is set, only the voice/video communication stream of the specified application is captured. The [playbackCaptureUid](arkts-audio-audio-audiocaptureroptions-i-sys.md#playbackcaptureuid) takes effect only when this mode is set. This mode requires the `ohos.permission.CAPTURE_VOICE_DOWNLINK_AUDIO` permission; otherwise [createAudioCapturer](arkts-audio-audio-createaudiocapturer-f.md) fails.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Audio.PlaybackCapture

**System API:** This is a system API.
