# OnFrameFetched

```TypeScript
type OnFrameFetched = (frameInfo: FrameInfo, err?: BusinessError<void>) => void
```

Describes the callback invoked when thumbnails are obtained in batches.

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Media.AVMetadataExtractor

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| frameInfo | [FrameInfo](arkts-media-media-frameinfo-i.md) | Yes | Thumbnail information. |
| err | [BusinessError](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-businesserror-i.md)&lt;void&gt; | No | Error that occurs when the thumbnail is obtained. The default value is **null**. |
