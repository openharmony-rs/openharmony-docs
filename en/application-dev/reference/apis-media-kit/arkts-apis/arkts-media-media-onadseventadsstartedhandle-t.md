# OnAdsEventAdsStartedHandle

```TypeScript
type OnAdsEventAdsStartedHandle = (adsId: string, duration: number) => void
```

Describes the callback function of the ad content playback start event.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Media.AVPlayer

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| adsId | string | Yes | ID of the ad resource that is being played. |
| duration | number | Yes | Playing duration of the advertisement, in milliseconds.<br>The value should be an integer. |
