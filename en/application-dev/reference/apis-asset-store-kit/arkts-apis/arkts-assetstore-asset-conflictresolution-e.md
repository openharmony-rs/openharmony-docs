# ConflictResolution

```TypeScript
enum ConflictResolution
```

Enumerates the policies for resolving conflicts (for example, a duplicate alias) when an asset is added.

**Since:** 11

<!--Device-asset-enum ConflictResolution--><!--Device-asset-enum ConflictResolution-End-->

**System capability:** SystemCapability.Security.Asset

## OVERWRITE

```TypeScript
OVERWRITE = 0
```

Overwrites the original asset.

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 14.

<!--Device-ConflictResolution-OVERWRITE = 0--><!--Device-ConflictResolution-OVERWRITE = 0-End-->

**System capability:** SystemCapability.Security.Asset

## THROW_ERROR

```TypeScript
THROW_ERROR = 1
```

Throws an exception for the service to perform subsequent processing.

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 14.

<!--Device-ConflictResolution-THROW_ERROR = 1--><!--Device-ConflictResolution-THROW_ERROR = 1-End-->

**System capability:** SystemCapability.Security.Asset
