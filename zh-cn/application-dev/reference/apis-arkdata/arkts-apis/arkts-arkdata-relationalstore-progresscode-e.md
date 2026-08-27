# ProgressCode

表示端云同步过程的状态码。请使用枚举名称而非枚举值。

**起始版本：** 10

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

## SUCCESS

```TypeScript
SUCCESS = 0
```

表示端云同步过程成功。

**起始版本：** 10

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

## UNKNOWN_ERROR

```TypeScript
UNKNOWN_ERROR = 1
```

表示端云同步过程遇到未知错误。

**起始版本：** 10

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

## NETWORK_ERROR

```TypeScript
NETWORK_ERROR = 2
```

表示端云同步过程遇到网络错误。

**起始版本：** 10

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

## CLOUD_DISABLED

```TypeScript
CLOUD_DISABLED = 3
```

表示云端不可用。

**起始版本：** 10

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

## LOCKED_BY_OTHERS

```TypeScript
LOCKED_BY_OTHERS = 4
```

表示有其他设备正在端云同步，本设备无法进行端云同步。请确保无其他设备占用云端资源后，再使用本设备进行端云同步任务。

**起始版本：** 10

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

## RECORD_LIMIT_EXCEEDED

```TypeScript
RECORD_LIMIT_EXCEEDED = 5
```

表示本次端云同步需要同步的条目或大小超出最大值。由云端配置最大值。

**起始版本：** 10

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

## NO_SPACE_FOR_ASSET

```TypeScript
NO_SPACE_FOR_ASSET = 6
```

表示云空间剩余空间小于待同步的资产大小。

**起始版本：** 10

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

## BLOCKED_BY_NETWORK_STRATEGY

```TypeScript
BLOCKED_BY_NETWORK_STRATEGY = 7
```

表示端云同步被网络策略限制。

**起始版本：** 12

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

## STOP_CLOUD_SYNC

```TypeScript
STOP_CLOUD_SYNC = 8
```

表示端云同步被停止。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core
