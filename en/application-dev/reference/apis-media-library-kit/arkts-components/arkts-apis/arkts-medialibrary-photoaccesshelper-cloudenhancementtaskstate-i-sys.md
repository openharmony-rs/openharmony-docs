# CloudEnhancementTaskState (System API)

Represents the cloud enhancement task information, which includes the cloud enhancement task state and other information related to certain states.

**Since:** 13

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { photoAccessHelper } from '@kit.MediaLibraryKit';
```

## expectedDuration

```TypeScript
readonly expectedDuration?: number
```

Queuing time. This parameter is mandatory when **taskStage** is **CloudEnhancementTaskStage.TASK_STAGE_EXECUTING**.

**Type:** number

**Since:** 13

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**System API:** This is a system API.

## statusCode

```TypeScript
readonly statusCode?: number
```

Status code. This parameter is mandatory when **taskStage** is **CloudEnhancementTaskStage.TASK_STAGE_FAILED**.

**Type:** number

**Since:** 13

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**System API:** This is a system API.

## taskStage

```TypeScript
readonly taskStage: CloudEnhancementTaskStage
```

Cloud enhancement task state.

**Type:** [CloudEnhancementTaskStage](arkts-medialibrary-photoaccesshelper-cloudenhancementtaskstage-e-sys.md)

**Since:** 13

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**System API:** This is a system API.

## totalFileSize

```TypeScript
readonly totalFileSize?: number
```

Total file size. This parameter is mandatory when **taskStage** is **CloudEnhancementTaskStage.TASK_STAGE_UPLOADING** or **CloudEnhancementTaskStage.TASK_STAGE_DOWNLOADING**.

**Type:** number

**Since:** 13

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**System API:** This is a system API.

## transferredFileSize

```TypeScript
readonly transferredFileSize?: number
```

Size of the file transferred. This parameter is mandatory when **taskStage** is **CloudEnhancementTaskStage.TASK_STAGE_UPLOADING** or **CloudEnhancementTaskStage.TASK_STAGE_DOWNLOADING**.

**Type:** number

**Since:** 13

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**System API:** This is a system API.
