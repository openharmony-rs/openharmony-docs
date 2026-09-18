# BatchResult

Result object containing batch operation,including [batchAdd](arkts-assetstore-asset-batchadd-f.md) and [batchUpdate](arkts-assetstore-asset-batchupdate-f.md).

**Since:** 26.0.0

**System capability:** SystemCapability.Security.Asset

## Modules to Import

```TypeScript
import { asset } from '@kit.AssetStoreKit';
```

## failedCount

```TypeScript
failedCount: number
```

Failed count of the batch operation, 0 means all success.

**Type:** number

**Since:** 26.0.0

**System capability:** SystemCapability.Security.Asset

## failedErrorInfos

```TypeScript
failedErrorInfos: Array<BatchErrInfo>
```

An array of error details for assets that failed in the batch operation, including [failedCount](#failedcount) items, which is an empty array if all succeed.

**Type:** Array&lt;[BatchErrInfo](arkts-assetstore-asset-batcherrinfo-i.md)&gt;

**Since:** 26.0.0

**System capability:** SystemCapability.Security.Asset
