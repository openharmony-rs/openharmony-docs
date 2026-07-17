# ErrorCode（系统接口）

表示端云同步过程的状态。请使用枚举名而非枚举值。

**起始版本：** 11

<!--Device-cloudExtension-export enum ErrorCode--><!--Device-cloudExtension-export enum ErrorCode-End-->

**系统能力：** SystemCapability.DistributedDataManager.CloudSync.Server

**系统接口：** 此接口为系统接口。

## SUCCESS

```TypeScript
SUCCESS = 0
```

表示端云同步过程成功。

**起始版本：** 11

<!--Device-ErrorCode-SUCCESS = 0--><!--Device-ErrorCode-SUCCESS = 0-End-->

**系统能力：** SystemCapability.DistributedDataManager.CloudSync.Server

**系统接口：** 此接口为系统接口。

## UNKNOWN_ERROR

```TypeScript
UNKNOWN_ERROR = 1
```

表示端云同步过程中遇到未知错误。

**起始版本：** 11

<!--Device-ErrorCode-UNKNOWN_ERROR = 1--><!--Device-ErrorCode-UNKNOWN_ERROR = 1-End-->

**系统能力：** SystemCapability.DistributedDataManager.CloudSync.Server

**系统接口：** 此接口为系统接口。

## NETWORK_ERROR

```TypeScript
NETWORK_ERROR = 2
```

表示端云同步过程中遇到网络错误。

**起始版本：** 11

<!--Device-ErrorCode-NETWORK_ERROR = 2--><!--Device-ErrorCode-NETWORK_ERROR = 2-End-->

**系统能力：** SystemCapability.DistributedDataManager.CloudSync.Server

**系统接口：** 此接口为系统接口。

## CLOUD_DISABLED

```TypeScript
CLOUD_DISABLED = 3
```

表示云同步开关未开启，请检查云空间同步开关状态。

**起始版本：** 11

<!--Device-ErrorCode-CLOUD_DISABLED = 3--><!--Device-ErrorCode-CLOUD_DISABLED = 3-End-->

**系统能力：** SystemCapability.DistributedDataManager.CloudSync.Server

**系统接口：** 此接口为系统接口。

## LOCKED_BY_OTHERS

```TypeScript
LOCKED_BY_OTHERS = 4
```

表示有其他设备正在进行端云同步，本设备无法进行端云同步。请确保无其他设备占用端云资源后，再使用本设备进行端云同步任务。

**起始版本：** 11

<!--Device-ErrorCode-LOCKED_BY_OTHERS = 4--><!--Device-ErrorCode-LOCKED_BY_OTHERS = 4-End-->

**系统能力：** SystemCapability.DistributedDataManager.CloudSync.Server

**系统接口：** 此接口为系统接口。

## RECORD_LIMIT_EXCEEDED

```TypeScript
RECORD_LIMIT_EXCEEDED = 5
```

表示本次端云同步需要同步的条目或大小超出最大值。由云端配置最大值。

**起始版本：** 11

<!--Device-ErrorCode-RECORD_LIMIT_EXCEEDED = 5--><!--Device-ErrorCode-RECORD_LIMIT_EXCEEDED = 5-End-->

**系统能力：** SystemCapability.DistributedDataManager.CloudSync.Server

**系统接口：** 此接口为系统接口。

## NO_SPACE_FOR_ASSET

```TypeScript
NO_SPACE_FOR_ASSET = 6
```

表示云空间剩余空间小于待同步的资产大小。

**起始版本：** 11

<!--Device-ErrorCode-NO_SPACE_FOR_ASSET = 6--><!--Device-ErrorCode-NO_SPACE_FOR_ASSET = 6-End-->

**系统能力：** SystemCapability.DistributedDataManager.CloudSync.Server

**系统接口：** 此接口为系统接口。

