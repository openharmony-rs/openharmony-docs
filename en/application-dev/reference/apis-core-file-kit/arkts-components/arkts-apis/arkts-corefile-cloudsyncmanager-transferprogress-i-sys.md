# TransferProgress (System API)

Defines the TransferProgress data structure.

**Since:** 26.0.0

**System capability:** SystemCapability.FileManagement.DistributedFileService.CloudSyncManager

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { cloudSyncManager } from '@kit.CoreFileKit';
```

## failedCount

```TypeScript
failedCount: number
```

failed count in TransferProgress. The value should be an integer. <br>Unit:Pcs.

**Type:** number

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.FileManagement.DistributedFileService.CloudSyncManager

**System API:** This is a system API.

## state

```TypeScript
state: TransferState
```

Describes the state type of transfer task.

**Type:** [TransferState](arkts-corefile-cloudsyncmanager-transferstate-e-sys.md)

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.FileManagement.DistributedFileService.CloudSyncManager

**System API:** This is a system API.

## stopReason

```TypeScript
stopReason: TransferStopReason
```

Describes the state type of transfer stop reason.

**Type:** [TransferStopReason](arkts-corefile-cloudsyncmanager-transferstopreason-e-sys.md)

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.FileManagement.DistributedFileService.CloudSyncManager

**System API:** This is a system API.

## successfulCount

```TypeScript
successfulCount: number
```

successful count in TransferProgress. The value should be an integer. <br>Unit:Pcs.

**Type:** number

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.FileManagement.DistributedFileService.CloudSyncManager

**System API:** This is a system API.

## totalCount

```TypeScript
totalCount: number
```

total count in TransferProgress. The value should be an integer. <br>Unit:Pcs.

**Type:** number

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.FileManagement.DistributedFileService.CloudSyncManager

**System API:** This is a system API.

## totalSize

```TypeScript
totalSize: number
```

Total size in TransferProgress. <br>Unit:Byte.

**Type:** number

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.FileManagement.DistributedFileService.CloudSyncManager

**System API:** This is a system API.

## transferredSize

```TypeScript
transferredSize: number
```

transferred size in TransferProgress. <br>Unit:Byte.

**Type:** number

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.FileManagement.DistributedFileService.CloudSyncManager

**System API:** This is a system API.
