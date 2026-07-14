# ValuesBucket

```TypeScript
type ValuesBucket = Record<string, ValueType>
```

用于存储键值对的类型。该类型不是多线程安全的，如果应用中存在多线程同时操作该类派生出的实例，注意加锁保护。

**起始版本：** 11

**系统能力：** SystemCapability.DistributedDataManager.CommonType

**属性类型：** Record<string, ValueType>

