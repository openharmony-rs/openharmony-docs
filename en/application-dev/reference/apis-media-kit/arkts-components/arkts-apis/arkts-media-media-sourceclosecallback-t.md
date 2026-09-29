# SourceCloseCallback

```TypeScript
type SourceCloseCallback = (uuid: number) => void
```

This callback function is implemented by applications to release related resources.

> **NOTE:** 
> 
> The client must return the handle immediately after processing the request.

**Since:** 18

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 18.

<!--Device-media-type SourceCloseCallback = (uuid: long) => void--><!--Device-media-type SourceCloseCallback = (uuid: long) => void-End-->

**System capability:** SystemCapability.Multimedia.Media.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| uuid | number | Yes | ID for the resource handle. |
