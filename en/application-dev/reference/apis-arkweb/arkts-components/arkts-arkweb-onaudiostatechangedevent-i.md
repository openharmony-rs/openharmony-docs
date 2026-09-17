# OnAudioStateChangedEvent

Defines the callback information triggered when the audio playback status on the web page changes, including the playback status. It is suitable for scenarios where monitoring audio playback behavior is required, improving audio management visibility and user experience.

**Since:** 12

**System capability:** SystemCapability.Web.Webview.Core

## playing

```TypeScript
playing: boolean
```

Audio playback status on the current page. The value **true** means that audio is being played, and **false** means the opposite.

**Type:** boolean

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Web.Webview.Core
