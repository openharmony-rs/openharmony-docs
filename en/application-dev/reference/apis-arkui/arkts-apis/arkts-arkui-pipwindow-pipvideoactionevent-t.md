# PiPVideoActionEvent

```TypeScript
type PiPVideoActionEvent = 'playbackStateChanged' | 'nextVideo' | 'previousVideo' | 'fastForward' | 'fastBackward'
```

Defines the PiP action event during video playback.

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Window.SessionManager

| Type | Description |
| --- | --- |
| 'playbackStateChanged' | The playback status changes. |
| 'nextVideo' | Plays the next video. |
| 'previousVideo' | Plays the previous video. |
| 'fastForward' | Fast forwards the video. This value is supported since API version 12. [since 12] |
| 'fastBackward' | Rewinds the video. This value is supported since API version 12. [since 12] |
