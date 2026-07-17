# SecurityLevel

数据库的安全级别枚举。

> **说明：**  
>  
> 在单设备使用场景下，KV数据库支持修改securityLevel参数进行安全等级升级。升级操作需要注意以下几点：  
>  
> * 该操作不支持跨设备同步的数据库。不同安全等级的数据库之间不能进行数据同步。若需升级数据库的安全等级，建议重新创建更高安全等级的数据库。  
>  
> * 关闭当前数据库后，修改securityLevel参数以重新设置数据库的安全等级，然后调用  
> [getKVStore](arkts-arkdata-distributedkvstore-kvmanager-i.md#getkvstore-1)  
> 接口重新打开数据库。  
>  
> * 该操作仅支持升级，例如从S2到S3，不支持降级，例如从S3到S2。

**起始版本：** 9

<!--Device-distributedKVStore-enum SecurityLevel--><!--Device-distributedKVStore-enum SecurityLevel-End-->

**系统能力：** SystemCapability.DistributedDataManager.KVStore.Core

## S1

```TypeScript
S1
```

表示数据库的安全级别为低级别，数据的泄露、篡改、破坏、销毁可能会给个人或组织导致有限的不利影响。

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-SecurityLevel-S1--><!--Device-SecurityLevel-S1-End-->

**系统能力：** SystemCapability.DistributedDataManager.KVStore.Core

## S2

```TypeScript
S2
```

表示数据库的安全级别为中级别，数据的泄露、篡改、破坏、销毁可能会给个人或组织导致严重的不利影响。

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-SecurityLevel-S2--><!--Device-SecurityLevel-S2-End-->

**系统能力：** SystemCapability.DistributedDataManager.KVStore.Core

## S3

```TypeScript
S3
```

表示数据库的安全级别为高级别，数据的泄露、篡改、破坏、销毁可能会给个人或组织导致严峻的不利影响。

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-SecurityLevel-S3--><!--Device-SecurityLevel-S3-End-->

**系统能力：** SystemCapability.DistributedDataManager.KVStore.Core

## S4

```TypeScript
S4
```

表示数据库的安全级别为关键级别，业界法律法规中定义的特殊数据类型，涉及个人的最私密领域的信息，一旦泄露、篡改、破坏、销毁可能会给个人或组织造成重大的不利影响。

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-SecurityLevel-S4--><!--Device-SecurityLevel-S4-End-->

**系统能力：** SystemCapability.DistributedDataManager.KVStore.Core

