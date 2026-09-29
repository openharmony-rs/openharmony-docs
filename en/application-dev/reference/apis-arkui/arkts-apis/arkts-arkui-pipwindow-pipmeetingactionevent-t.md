# PiPMeetingActionEvent

```TypeScript
type PiPMeetingActionEvent = 'hangUp' | 'voiceStateChanged' | 'videoStateChanged' | 'micStateChanged'
```

Defines the PiP action event in a video meeting.

**Since:** 11

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 12.

<!--Device-PiPWindow-type PiPMeetingActionEvent = 'hangUp' | 'voiceStateChanged' | 'videoStateChanged' | 'micStateChanged'--><!--Device-PiPWindow-type PiPMeetingActionEvent = 'hangUp' | 'voiceStateChanged' | 'videoStateChanged' | 'micStateChanged'-End-->

**System capability:** SystemCapability.Window.SessionManager

| Type | Description |
| --- | --- |
| 'hangUp' | The video meeting is hung up. |
| 'voiceStateChanged' | The speaker is muted or unmuted. |
| 'videoStateChanged' | The camera is turned on or off. |
| 'micStateChanged' | The microphone is muted or unmuted. [since 12] |
