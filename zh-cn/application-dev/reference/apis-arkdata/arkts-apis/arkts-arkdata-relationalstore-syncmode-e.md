# SyncMode

指数据库同步模式。请使用枚举名称而非枚举值。

**起始版本：** 9

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

## SYNC_MODE_PUSH

```TypeScript
SYNC_MODE_PUSH = 0
```

表示数据从本地设备推送到远程设备。

**起始版本：** 9

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

## SYNC_MODE_PULL

```TypeScript
SYNC_MODE_PULL = 1
```

表示数据从远程设备拉至本地设备。

**起始版本：** 9

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

## SYNC_MODE_TIME_FIRST

```TypeScript
SYNC_MODE_TIME_FIRST
```

表示数据从修改时间较近的一端同步到修改时间较远的一端。

**起始版本：** 10

**系统能力：** SystemCapability.DistributedDataManager.CloudSync.Client

## SYNC_MODE_NATIVE_FIRST

```TypeScript
SYNC_MODE_NATIVE_FIRST
```

表示数据从本地设备同步到云端。

**起始版本：** 10

**系统能力：** SystemCapability.DistributedDataManager.CloudSync.Client

## SYNC_MODE_CLOUD_FIRST

```TypeScript
SYNC_MODE_CLOUD_FIRST
```

表示数据从云端同步到本地设备。

**起始版本：** 10

**系统能力：** SystemCapability.DistributedDataManager.CloudSync.Client
