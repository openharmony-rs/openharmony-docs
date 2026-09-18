# SyncResult

表示设备同步结果。

**起始版本：** 26.0.0

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

## 导入模块

```TypeScript
import { relationalStore } from '@kit.ArkData';
```

## code

```TypeScript
readonly code:SyncResultCode
```

表示同步结果的状态码。

**类型：** [SyncResultCode](arkts-arkdata-relationalstore-syncresultcode-e.md)

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

## device

```TypeScript
readonly device:string
```

表示同步的设备ID，可通过[getAvailableDeviceListSync](../../apis-distributed-service-kit/arkts-apis/arkts-distributedservice-distributeddevicemanager-devicemanager-i.md#getavailabledevicelistsync)等接口获取所有可信设备ID列表。

**类型：** string

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

## message

```TypeScript
readonly message:string
```

表示同步结果的信息。

**类型：** string

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core
