# KeyRequestCallback

```TypeScript
type KeyRequestCallback = (assetId: string, requestData: Uint8Array) => void
```

The callback of key request.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Multimedia.AVSession.AVCast

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| assetId | string | Yes | request key for current assetId |
| requestData | Uint8Array | Yes | media key request data sent to media key server |
