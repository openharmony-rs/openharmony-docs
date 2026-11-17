# VoiceContent (System API)

```TypeScript
export interface VoiceContent
```

Returns the notification voice broadcast content.

**Since:** 26.0.0

<!--Device-unnamed-export interface VoiceContent--><!--Device-unnamed-export interface VoiceContent-End-->

**System capability:** SystemCapability.Notification.Notification

**System API:** This is a system API.

## textContent

```TypeScript
readonly textContent?: string
```

Text content of the voice broadcast. In the Chinese mainland, it is intelligent broadcast content. Since API version 26.1.0, voice broadcast of notifications is supported outside the Chinese mainland. The fixed broadcast content contains only the application name and the notification body.

**Type:** string

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-VoiceContent-readonly textContent?: string--><!--Device-VoiceContent-readonly textContent?: string-End-->

**System capability:** SystemCapability.Notification.Notification

**System API:** This is a system API.
