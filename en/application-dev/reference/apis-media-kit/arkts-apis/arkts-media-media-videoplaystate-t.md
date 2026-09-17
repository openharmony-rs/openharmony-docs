# VideoPlayState

```TypeScript
type VideoPlayState = 'idle' | 'prepared' | 'playing' | 'paused' | 'stopped' | 'error'
```

Describes the video playback state. You can obtain the state through the **state** property.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [AVPlayerState](arkts-media-media-avplayerstate-t.md)

**System capability:** SystemCapability.Multimedia.Media.VideoPlayer

| Type | Description |
| --- | --- |
| 'idle' | The video player is idle. |
| 'prepared' | Video playback is being prepared. |
| 'playing' | Video playback is in progress. |
| 'paused' | Video playback is paused. |
| 'stopped' | Video playback is stopped. |
| 'error' | Video playback is in the error state. |
