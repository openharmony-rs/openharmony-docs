# ValuesBucket

```TypeScript
export type ValuesBucket = Record<string, ValueType | Uint8Array | null>
```

Defines the types of the key and value in a KV pair. This type is not multi-thread safe. If a **ValuesBucket** instance is operated by multiple threads at the same time in an application, use a lock for it.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedDataManager.DataShare.Core

**Type:** Record&lt;string, [ValueType](arkts-arkdata-valuetype-t.md) | Uint8Array | null&gt;
