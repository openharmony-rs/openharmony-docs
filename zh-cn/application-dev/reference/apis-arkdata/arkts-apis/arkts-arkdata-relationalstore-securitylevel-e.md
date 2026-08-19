# SecurityLevel

数据库的安全级别枚举。请使用枚举名称而非枚举值。数据库的安全级别仅支持由低向高设置，不支持由高向低设置。 > **说明：** > > 若需要进行同步操作，数据库安全级别应不高于对端设备安全级别，具体可见 > [跨设备同步访问控制机制](../../../database/sync-app-data-across-devices-overview.md#跨设备同步访问控制机制)。

**起始版本：** 23

<!--Device-relationalStore-enum SecurityLevel--><!--Device-relationalStore-enum SecurityLevel-End-->

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

## S1

```TypeScript
S1 = 1
```

表示数据库的安全级别为低级别，当数据泄露时会产生较低影响。例如，包含壁纸等系统数据的数据库。

**起始版本：** 23

<!--Device-SecurityLevel-S1 = 1--><!--Device-SecurityLevel-S1 = 1-End-->

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

## S2

```TypeScript
S2 = 2
```

表示数据库的安全级别为中级别，当数据泄露时会产生较大影响。例如，包含录音、视频等用户生成数据或通话记录等信息的数据库。

**起始版本：** 23

<!--Device-SecurityLevel-S2 = 2--><!--Device-SecurityLevel-S2 = 2-End-->

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

## S3

```TypeScript
S3 = 3
```

表示数据库的安全级别为高级别，当数据泄露时会产生重大影响。例如，包含用户运动、健康、位置等信息的数据库。

**起始版本：** 23

<!--Device-SecurityLevel-S3 = 3--><!--Device-SecurityLevel-S3 = 3-End-->

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

## S4

```TypeScript
S4 = 4
```

表示数据库的安全级别为关键级别，当数据泄露时会产生严重影响。例如，包含认证凭据、财务数据等信息的数据库。

**起始版本：** 23

<!--Device-SecurityLevel-S4 = 4--><!--Device-SecurityLevel-S4 = 4-End-->

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

