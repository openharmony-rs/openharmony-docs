# ListenerStatus

表示从UDMF获取数据时的状态码的枚举。

**起始版本：** 15

<!--Device-unifiedDataChannel-enum ListenerStatus--><!--Device-unifiedDataChannel-enum ListenerStatus-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## FINISHED

```TypeScript
FINISHED = 0
```

表示已完成。

**起始版本：** 15

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本15开始，该接口支持在原子化服务API中使用。

<!--Device-ListenerStatus-FINISHED = 0--><!--Device-ListenerStatus-FINISHED = 0-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## PROCESSING

```TypeScript
PROCESSING = 1
```

表示正在处理中。

**起始版本：** 15

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本15开始，该接口支持在原子化服务API中使用。

<!--Device-ListenerStatus-PROCESSING = 1--><!--Device-ListenerStatus-PROCESSING = 1-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## CANCELED

```TypeScript
CANCELED = 2
```

表明本次处理已被取消。

**起始版本：** 15

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本15开始，该接口支持在原子化服务API中使用。

<!--Device-ListenerStatus-CANCELED = 2--><!--Device-ListenerStatus-CANCELED = 2-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## INNER_ERROR

```TypeScript
INNER_ERROR = 200
```

表明发生了内部错误。

**起始版本：** 15

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本15开始，该接口支持在原子化服务API中使用。

<!--Device-ListenerStatus-INNER_ERROR = 200--><!--Device-ListenerStatus-INNER_ERROR = 200-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## INVALID_PARAMETERS

```TypeScript
INVALID_PARAMETERS = 201
```

表示 [GetDataParams](arkts-arkdata-unifieddatachannel-getdataparams-i.md) 包含无效参数。

**起始版本：** 15

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本15开始，该接口支持在原子化服务API中使用。

<!--Device-ListenerStatus-INVALID_PARAMETERS = 201--><!--Device-ListenerStatus-INVALID_PARAMETERS = 201-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## DATA_NOT_FOUND

```TypeScript
DATA_NOT_FOUND = 202
```

表示没有获取到数据。

**起始版本：** 15

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本15开始，该接口支持在原子化服务API中使用。

<!--Device-ListenerStatus-DATA_NOT_FOUND = 202--><!--Device-ListenerStatus-DATA_NOT_FOUND = 202-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## SYNC_FAILED

```TypeScript
SYNC_FAILED = 203
```

表示同步过程中出现错误。

**起始版本：** 15

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本15开始，该接口支持在原子化服务API中使用。

<!--Device-ListenerStatus-SYNC_FAILED = 203--><!--Device-ListenerStatus-SYNC_FAILED = 203-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## COPY_FILE_FAILED

```TypeScript
COPY_FILE_FAILED = 204
```

表示文件拷贝过程中出现错误。

**起始版本：** 15

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本15开始，该接口支持在原子化服务API中使用。

<!--Device-ListenerStatus-COPY_FILE_FAILED = 204--><!--Device-ListenerStatus-COPY_FILE_FAILED = 204-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

