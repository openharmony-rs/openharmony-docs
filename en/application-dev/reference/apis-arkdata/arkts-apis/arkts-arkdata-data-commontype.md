# @ohos.data.commonType(Common Data Types)

The commonType module defines common data types in data management. It provides basic data types such as asset status enum, asset information, and key-value pair storage to support unified data representation and transfer in distributed data management scenarios.

**Since:** 11

<!--Device-unnamed-declare namespace commonType--><!--Device-unnamed-declare namespace commonType-End-->

**System capability:** SystemCapability.DistributedDataManager.CommonType

## Modules to Import

```TypeScript
import { commonType } from '@kit.ArkData';
```

## Summary

### Interfaces

| Name | Description |
| --- | --- |
| [Asset](arkts-arkdata-commontype-asset-i.md) | Represents asset (such as a file, image, or video) information. For details, see the sample code in [Using Distributed Data Objects in Cross-Device Migration] (../../database/data-sync-of-distributed-data-object.md#using-distributed-data-objects-in-cross-device-migration). |

### Types

| Name | Description |
| --- | --- |
| [Assets](arkts-arkdata-commontype-assets-t.md) | Represents an array of Assets. |
| [ValuesBucket](arkts-arkdata-commontype-valuesbucket-t.md) | Defines the types of the key and value in a KV pair. This type is not concurrency-safe. If multiple threads in an application operate instances derived from this class at the same time, use a lock for protection. |
| [ValueType](arkts-arkdata-commontype-valuetype-t.md) | Enumerates the data field types, which are determined by API parameter functions. |

### Enums

| Name | Description |
| --- | --- |
| [AssetStatus](arkts-arkdata-commontype-assetstatus-e.md) | Enumerates the asset statuses. Use the enum name rather than the enum value. |
