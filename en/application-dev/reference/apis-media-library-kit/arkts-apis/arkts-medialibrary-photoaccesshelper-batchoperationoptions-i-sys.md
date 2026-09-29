# BatchOperationOptions (System API)

```TypeScript
interface BatchOperationOptions
```

Batch operation options

**Since:** 26.0.0

<!--Device-photoAccessHelper-interface BatchOperationOptions--><!--Device-photoAccessHelper-interface BatchOperationOptions-End-->

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { photoAccessHelper } from '@kit.MediaLibraryKit';
```

## countProgressListener

```TypeScript
countProgressListener?: ProgressListener
```

count progress of batch operations.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-BatchOperationOptions-countProgressListener?: ProgressListener--><!--Device-BatchOperationOptions-countProgressListener?: ProgressListener-End-->

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**System API:** This is a system API.

## resultListener

```TypeScript
resultListener?: ResultListener
```

the result of batch operations.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-BatchOperationOptions-resultListener?: ResultListener--><!--Device-BatchOperationOptions-resultListener?: ResultListener-End-->

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**System API:** This is a system API.

## sizeProgressListener

```TypeScript
sizeProgressListener?: ProgressListener
```

size progress of batch operations.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-BatchOperationOptions-sizeProgressListener?: ProgressListener--><!--Device-BatchOperationOptions-sizeProgressListener?: ProgressListener-End-->

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**System API:** This is a system API.

## mode

```TypeScript
mode?: number
```

the mode of Automatic renaming.

**Type:** number

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-BatchOperationOptions-mode?: int--><!--Device-BatchOperationOptions-mode?: int-End-->

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**System API:** This is a system API.

## taskSignal

```TypeScript
taskSignal?: TaskSignal
```

interrupting of batch operations.

**Type:** [TaskSignal](arkts-medialibrary-photoaccesshelper-tasksignal-c-sys.md)

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-BatchOperationOptions-taskSignal?: TaskSignal--><!--Device-BatchOperationOptions-taskSignal?: TaskSignal-End-->

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**System API:** This is a system API.
