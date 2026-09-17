# CloudData (System API)

Represents the cloud data.

**Since:** 11

**System capability:** SystemCapability.DistributedDataManager.CloudSync.Server

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { cloudExtension } from '@kit.ArkData';
```

## hasMore

```TypeScript
hasMore: boolean
```

Whether there is data to be queried on the server. The value true means there is data to be queried on the server; the value false means the opposite.

**Type:** boolean

**Since:** 11

**System capability:** SystemCapability.DistributedDataManager.CloudSync.Server

**System API:** This is a system API.

## nextCursor

```TypeScript
nextCursor: string
```

Cursor for data query.

**Type:** string

**Since:** 11

**System capability:** SystemCapability.DistributedDataManager.CloudSync.Server

**System API:** This is a system API.

## values

```TypeScript
values: Array<Record<string, CloudType>>
```

Array of data to be queried, which consists of the data value and ExtensionValue.

**Type:** Array&lt;Record&lt;string, [CloudType](arkts-arkdata-cloudextension-cloudtype-t-sys.md)&gt;&gt;

**Since:** 11

**System capability:** SystemCapability.DistributedDataManager.CloudSync.Server

**System API:** This is a system API.
