# ListenerStatus

```TypeScript
enum ListenerStatus
```

Enumerates the status codes returned when data is obtained from the UDMF.

**Since:** 15

<!--Device-unifiedDataChannel-enum ListenerStatus--><!--Device-unifiedDataChannel-enum ListenerStatus-End-->

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

## FINISHED

```TypeScript
FINISHED = 0
```

The task is completed.

**Since:** 15

**Model restriction:** This API can be used only in the stage model.

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 15.

<!--Device-ListenerStatus-FINISHED = 0--><!--Device-ListenerStatus-FINISHED = 0-End-->

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

## PROCESSING

```TypeScript
PROCESSING = 1
```

The task is being processed.

**Since:** 15

**Model restriction:** This API can be used only in the stage model.

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 15.

<!--Device-ListenerStatus-PROCESSING = 1--><!--Device-ListenerStatus-PROCESSING = 1-End-->

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

## CANCELED

```TypeScript
CANCELED = 2
```

The task is canceled.

**Since:** 15

**Model restriction:** This API can be used only in the stage model.

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 15.

<!--Device-ListenerStatus-CANCELED = 2--><!--Device-ListenerStatus-CANCELED = 2-End-->

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

## INNER_ERROR

```TypeScript
INNER_ERROR = 200
```

An internal error occurs.

**Since:** 15

**Model restriction:** This API can be used only in the stage model.

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 15.

<!--Device-ListenerStatus-INNER_ERROR = 200--><!--Device-ListenerStatus-INNER_ERROR = 200-End-->

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

## INVALID_PARAMETERS

```TypeScript
INVALID_PARAMETERS = 201
```

[GetDataParams](arkts-arkdata-unifieddatachannel-getdataparams-i.md) contains invalid parameters.

**Since:** 15

**Model restriction:** This API can be used only in the stage model.

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 15.

<!--Device-ListenerStatus-INVALID_PARAMETERS = 201--><!--Device-ListenerStatus-INVALID_PARAMETERS = 201-End-->

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

## DATA_NOT_FOUND

```TypeScript
DATA_NOT_FOUND = 202
```

No data is obtained.

**Since:** 15

**Model restriction:** This API can be used only in the stage model.

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 15.

<!--Device-ListenerStatus-DATA_NOT_FOUND = 202--><!--Device-ListenerStatus-DATA_NOT_FOUND = 202-End-->

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

## SYNC_FAILED

```TypeScript
SYNC_FAILED = 203
```

Failed to sync data.

**Since:** 15

**Model restriction:** This API can be used only in the stage model.

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 15.

<!--Device-ListenerStatus-SYNC_FAILED = 203--><!--Device-ListenerStatus-SYNC_FAILED = 203-End-->

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

## COPY_FILE_FAILED

```TypeScript
COPY_FILE_FAILED = 204
```

Failed to copy data.

**Since:** 15

**Model restriction:** This API can be used only in the stage model.

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 15.

<!--Device-ListenerStatus-COPY_FILE_FAILED = 204--><!--Device-ListenerStatus-COPY_FILE_FAILED = 204-End-->

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core
