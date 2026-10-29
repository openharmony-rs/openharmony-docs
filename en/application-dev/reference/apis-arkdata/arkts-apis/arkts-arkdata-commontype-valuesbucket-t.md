# ValuesBucket

```TypeScript
type ValuesBucket = Record<string, ValueType>
```

Defines the types of the key and value in a KV pair. This type is not concurrency-safe. If multiple threads in an application operate instances derived from this class at the same time, use a lock for protection.

**Type:** Record&lt;string, [ValueType](arkts-arkdata-commontype-valuetype-t.md)&gt;

**Since:** 11

<!--Device-commonType-type ValuesBucket = Record<string, ValueType>--><!--Device-commonType-type ValuesBucket = Record<string, ValueType>-End-->

**System capability:** SystemCapability.DistributedDataManager.CommonType
