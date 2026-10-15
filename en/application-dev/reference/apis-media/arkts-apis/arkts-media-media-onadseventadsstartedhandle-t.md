# OnAdsEventAdsStartedHandle

```TypeScript
type OnAdsEventAdsStartedHandle = (adsId: string, duration: number) => void
```

Registers a callback invoked when the ad starts to play.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-media-type OnAdsEventAdsStartedHandle = (adsId: string, duration: int) => void--><!--Device-media-type OnAdsEventAdsStartedHandle = (adsId: string, duration: int) => void-End-->

**System capability:** SystemCapability.Multimedia.Media.AVPlayer

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| adsId | string | Yes | ID of the ad resource that is being played. |
| duration | number | Yes | Playback duration of an ad, in milliseconds.<br>The value must be an integer. |
