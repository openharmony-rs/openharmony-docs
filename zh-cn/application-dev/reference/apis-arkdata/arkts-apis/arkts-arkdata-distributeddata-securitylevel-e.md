# SecurityLevel

数据库的安全级别枚举。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** SecurityLevel

<!--Device-distributedData-enum SecurityLevel--><!--Device-distributedData-enum SecurityLevel-End-->

**系统能力：** SystemCapability.DistributedDataManager.KVStore.Core

## NO_LEVEL

```TypeScript
NO_LEVEL = 0
```

表示数据库不设置安全级别(已废弃)。

**起始版本：** 7

**废弃版本：** 9

<!--Device-SecurityLevel-NO_LEVEL = 0--><!--Device-SecurityLevel-NO_LEVEL = 0-End-->

**系统能力：** SystemCapability.DistributedDataManager.KVStore.DistributedKVStore

## S0

```TypeScript
S0 = 1
```

表示数据库的安全级别为公共级别(已废弃)。

**起始版本：** 7

**废弃版本：** 9

<!--Device-SecurityLevel-S0 = 1--><!--Device-SecurityLevel-S0 = 1-End-->

**系统能力：** SystemCapability.DistributedDataManager.KVStore.Core

## S1

```TypeScript
S1 = 2
```

表示数据库的安全级别为低级别，当数据泄露时会产生较低影响。例如，包含壁纸等系统数据的数据库。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** S1

<!--Device-SecurityLevel-S1 = 2--><!--Device-SecurityLevel-S1 = 2-End-->

**系统能力：** SystemCapability.DistributedDataManager.KVStore.Core

## S2

```TypeScript
S2 = 3
```

表示数据库的安全级别为中级别，当数据泄露时会产生较大影响。例如，包含录音、视频等用户生成数据或通话记录等信息的数据库。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** S2

<!--Device-SecurityLevel-S2 = 3--><!--Device-SecurityLevel-S2 = 3-End-->

**系统能力：** SystemCapability.DistributedDataManager.KVStore.Core

## S3

```TypeScript
S3 = 5
```

表示数据库的安全级别为高级别，当数据泄露时会产生重大影响。例如，包含用户运动、健康、位置等信息的数据库。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** S3

<!--Device-SecurityLevel-S3 = 5--><!--Device-SecurityLevel-S3 = 5-End-->

**系统能力：** SystemCapability.DistributedDataManager.KVStore.Core

## S4

```TypeScript
S4 = 6
```

表示数据库的安全级别为关键级别，当数据泄露时会产生严重影响。例如，包含认证凭据、财务数据等信息的数据库。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** S4

<!--Device-SecurityLevel-S4 = 6--><!--Device-SecurityLevel-S4 = 6-End-->

**系统能力：** SystemCapability.DistributedDataManager.KVStore.Core

