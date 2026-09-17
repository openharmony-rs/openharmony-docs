# Value

```TypeScript
declare type Value = boolean | number | Uint8Array
```

Represents the value of each attribute in [AssetMap](arkts-assetstore-asset-assetmap-t.md).

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 14.

**System capability:** SystemCapability.Security.Asset

| Type | Description |
| --- | --- |
| boolean | The value is a boolean value, with a range of true or false. |
| number | The value is a number, and the value range is the enumerated value or number corresponding to the tag. |
| Uint8Array | The value is a byte array, and the content is defined by the service. |
