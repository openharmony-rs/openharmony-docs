# PiPCallActionEvent

```TypeScript
type PiPCallActionEvent = 'hangUp' | 'micStateChanged' | 'videoStateChanged' | 'voiceStateChanged'
```

Defines the PiP action event in a video call.

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Window.SessionManager

| Type | Description |
| --- | --- |
| 'hangUp' | The video call is hung up. |
| 'micStateChanged' | The microphone is muted or unmuted. |
| 'videoStateChanged' | The camera is turned on or off. |
| 'voiceStateChanged' | The speaker is muted or unmuted. [since 12] |
