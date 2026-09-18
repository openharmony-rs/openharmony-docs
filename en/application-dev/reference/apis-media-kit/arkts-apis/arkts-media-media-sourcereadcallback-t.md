# SourceReadCallback

```TypeScript
type SourceReadCallback = (uuid: number, requestedOffset: number, requestedLength: number) => void
```

This callback function is implemented by applications to handle resource read requests. When data is available, applications should push it to the player using the [respondData](arkts-media-media-mediasourceloadingrequest-i.md#responddata) API of the corresponding MediaSourceLoadingRequest object.

> **NOTE:** 
> 
> The client must return the handle immediately after processing the request.

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.Multimedia.Media.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| uuid | number | Yes | ID for the resource handle. |
| requestedOffset | number | Yes | Offset of the current media data relative to the start of the resource. |
| requestedLength | number | Yes | Length of the current request. The value **-1** indicates reaching the end of the resource. After pushing the data, call [finishLoading](arkts-media-media-mediasourceloadingrequest-i.md#finishloading) to notify the player that the push is complete. |
