# Value

```TypeScript
declare type Value = boolean | number | Uint8Array
```

Represents the value of each attribute in [AssetMap](arkts-assetstore-asset-assetmap-t.md).

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 14.

<!--Device-asset-declare type Value = boolean | number | Uint8Array--><!--Device-asset-declare type Value = boolean | number | Uint8Array-End-->

**System capability:** SystemCapability.Security.Asset

| Type | Description |
| --- | --- |
| boolean | The value type is Boolean. The value can be true or false. |
| number | Indicates that the value type is a number. The value can be an enumerated value or a number supported by the corresponding tag. |
| Uint8Array | Indicates that the value type is a byte array, and the content is defined by the service. |
