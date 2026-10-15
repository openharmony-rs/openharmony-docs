# OnAdsEventLoadingErrorHandle

```TypeScript
type OnAdsEventLoadingErrorHandle = (adsId: string, reason: BusinessError) => void
```

Registers a callback for the ad media resource loading failure event.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-media-type OnAdsEventLoadingErrorHandle = (adsId: string, reason: BusinessError) => void--><!--Device-media-type OnAdsEventLoadingErrorHandle = (adsId: string, reason: BusinessError) => void-End-->

**System capability:** SystemCapability.Multimedia.Media.AVPlayer

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| adsId | string | Yes | ID of the ad resource that fails to be loaded. |
| reason | [BusinessError](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-businesserror-i.md) | Yes | Cause of the loading failure. |
