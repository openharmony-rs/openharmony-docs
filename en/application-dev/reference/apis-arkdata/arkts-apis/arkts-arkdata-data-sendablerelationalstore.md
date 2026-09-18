# @ohos.data.sendableRelationalStore

The **sendableRelationalStore** module provides APIs for obtaining **ValuesBucket** of the sendable type from the query result set and transferring it between concurrent instances.

**Since:** 12

**System capability:** SystemCapability.DistributedDataManager.RelationalStore.Core

## Modules to Import

```TypeScript
import { sendableRelationalStore } from '@kit.ArkData';
```

## Summary

### Functions

| Name | Description |
| --- | --- |
| [fromSendableAsset](arkts-arkdata-sendablerelationalstore-fromsendableasset-f.md) | Converts the asset data that can be passed across threads into the data that cannot be passed across threads. |
| [fromSendableValues](arkts-arkdata-sendablerelationalstore-fromsendablevalues-f.md) | Converts the array data that can be passed across threads into the data that cannot be passed across threads. |
| [fromSendableValuesBucket](arkts-arkdata-sendablerelationalstore-fromsendablevaluesbucket-f.md) | Converts a KV pair that can be passed across threads into the data that cannot be passed across threads. |
| [toSendableAsset](arkts-arkdata-sendablerelationalstore-tosendableasset-f.md) | Converts the asset data that cannot be passed across threads into the data that can be passed across threads. |
| [toSendableValues](arkts-arkdata-sendablerelationalstore-tosendablevalues-f.md) | Converts the array data that cannot be passed across threads into the data that can be passed across threads. |
| [toSendableValuesBucket](arkts-arkdata-sendablerelationalstore-tosendablevaluesbucket-f.md) | Converts a key-value (KV) pair that cannot be passed across threads into the data that can be passed across threads. |

### Interfaces

| Name | Description |
| --- | --- |
| [Asset](arkts-arkdata-sendablerelationalstore-asset-i.md) | Represent the asset (such as a document, image, or video). **Asset** inherits from [lang.ISendable](../../apis-arkts/arkts-apis/arkts-arkts-lang-isendable-i.md) and is used to implement cross-thread transfer of asset data. The asset data does not support **Datashare** APIs. Use [sendableRelationalStore.toSendableAsset](arkts-arkdata-sendablerelationalstore-tosendableasset-f.md) to create an **Asset** instance. |

### Types

| Name | Description |
| --- | --- |
| [Assets](arkts-arkdata-sendablerelationalstore-assets-t.md) | Represent an array of [Assets](arkts-arkdata-sendablerelationalstore-asset-i.md), which allows assets to be passed across threads. |
| [NonSendableAsset](arkts-arkdata-sendablerelationalstore-nonsendableasset-t.md) | Represents the asset (such as a document, image, or video) that cannot be passed across threads. |
| [NonSendableBucket](arkts-arkdata-sendablerelationalstore-nonsendablebucket-t.md) | Represents the KV pair that cannot be passed across threads. |
| [NonSendableValues](arkts-arkdata-sendablerelationalstore-nonsendablevalues-t.md) | Represents the [ValueType](arkts-arkdata-relationalstore-valuetype-t.md) array that cannot be passed across threads. |
| [ValuesBucket](arkts-arkdata-sendablerelationalstore-valuesbucket-t.md) | Represents the KV pair of the [ValueType](arkts-arkdata-sendablerelationalstore-valuetype-t.md) data that can be passed across threads. |
| [ValueType](arkts-arkdata-sendablerelationalstore-valuetype-t.md) | Defines the types of the value in a KV pair. The type varies with the parameter function. |
