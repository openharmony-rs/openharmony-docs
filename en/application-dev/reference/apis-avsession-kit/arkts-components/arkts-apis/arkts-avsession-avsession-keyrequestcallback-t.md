# KeyRequestCallback

```TypeScript
type KeyRequestCallback = (assetId: string, requestData: Uint8Array) => void
```

The callback of key request.

**Since:** 12

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 12.

<!--Device-avSession-type KeyRequestCallback = (assetId: string, requestData: Uint8Array) => void--><!--Device-avSession-type KeyRequestCallback = (assetId: string, requestData: Uint8Array) => void-End-->

**System capability:** SystemCapability.Multimedia.AVSession.AVCast

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| assetId | string | Yes | request key for current assetId |
| requestData | Uint8Array | Yes | media key request data sent to media key server |
