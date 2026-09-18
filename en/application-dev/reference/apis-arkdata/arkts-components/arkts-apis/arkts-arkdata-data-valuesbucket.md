# @ohos.data.ValuesBucket(Data Set)

**ValuesBucket** is a dataset in the form of key-value (KV) pairs that can be inserted in the database.



## Modules to Import

```TypeScript
import { ValueType, ValuesBucket } from '@kit.ArkData';
```

## Summary

### Types

| Name | Description |
| --- | --- |
| [ValuesBucket](arkts-arkdata-valuesbucket-t.md) | Defines the types of the key and value in a KV pair. This type is not multi-thread safe. If a **ValuesBucket** instance is operated by multiple threads at the same time in an application, use a lock for it. |
| [ValueType](arkts-arkdata-valuetype-t.md) | Defines the value types allowed in a **ValuesBucket** instance. |
