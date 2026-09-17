# OnSeiMessageHandle

```TypeScript
type OnSeiMessageHandle = (messages: Array<SeiMessage>, playbackPosition?: number) => void
```

Describes the handle used to obtain SEI messages. This is used when in subscriptions to SEI message events, and the callback returns detailed SEI information.

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.Multimedia.Media.AVPlayer

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| messages | Array&lt;[SeiMessage](arkts-media-media-seimessage-i.md)&gt; | Yes | Array of SEI messages. |
| playbackPosition | number | No | Current playback position, in milliseconds. |
