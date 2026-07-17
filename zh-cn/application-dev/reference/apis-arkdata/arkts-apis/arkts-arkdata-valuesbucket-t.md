# ValuesBucket

```TypeScript
export type ValuesBucket = Record<string, ValueType | Uint8Array | null>
```

用于存储键值对的类型。该类型不是多线程安全的，如果应用中存在多线程同时操作该类派生出的实例，注意加锁保护。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-unnamed-export type ValuesBucket = Record<string, ValueType | Uint8Array | null>--><!--Device-unnamed-export type ValuesBucket = Record<string, ValueType | Uint8Array | null>-End-->

**系统能力：** SystemCapability.DistributedDataManager.DataShare.Core

**属性类型：** Record<string, ValueType | Uint8Array | null>

