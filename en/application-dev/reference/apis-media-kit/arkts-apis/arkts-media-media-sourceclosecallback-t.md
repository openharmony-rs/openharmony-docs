# SourceCloseCallback

```TypeScript
type SourceCloseCallback = (uuid: number) => void
```

This callback function is implemented by applications to release related resources.

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
