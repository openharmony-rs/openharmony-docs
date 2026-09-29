# SyncFolder (System API)

```TypeScript
interface SyncFolder
```

Encapsulates the sync root information.

**Since:** 21

<!--Device-cloudDiskManager-interface SyncFolder--><!--Device-cloudDiskManager-interface SyncFolder-End-->

**System capability:** SystemCapability.FileManagement.CloudDiskManager

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { cloudDiskManager } from '@kit.CoreFileKit';
```

## bundleName

```TypeScript
bundleName: string
```

Bundle name of the sync root.

**Type:** string

**Since:** 21

<!--Device-SyncFolder-bundleName: string--><!--Device-SyncFolder-bundleName: string-End-->

**System capability:** SystemCapability.FileManagement.CloudDiskManager

**System API:** This is a system API.

## customAlias

```TypeScript
customAlias?: string
```

Custom alias displayed in the File Manager list. The default value is **undefined**.

**Type:** string

**Since:** 21

<!--Device-SyncFolder-customAlias?: string--><!--Device-SyncFolder-customAlias?: string-End-->

**System capability:** SystemCapability.FileManagement.CloudDiskManager

**System API:** This is a system API.

## displayNameResId

```TypeScript
displayNameResId?: number
```

Resource ID, which can be mapped to the alias displayed in the File Manager list. The default value is **undefined**.

**Type:** number

**Since:** 21

<!--Device-SyncFolder-displayNameResId?: int--><!--Device-SyncFolder-displayNameResId?: int-End-->

**System capability:** SystemCapability.FileManagement.CloudDiskManager

**System API:** This is a system API.

## isSupportPlaceHolder

```TypeScript
isSupportPlaceHolder?: boolean
```

Whether the synchronization root supports placeholders. Value constraint: true indicates that the synchronization root supports placeholders. false indicates that the synchronization root does not support placeholders. Default value: false.

**Type:** boolean

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

<!--Device-SyncFolder-isSupportPlaceHolder?: boolean--><!--Device-SyncFolder-isSupportPlaceHolder?: boolean-End-->

**System capability:** SystemCapability.FileManagement.CloudDiskManager

**System API:** This is a system API.

## path

```TypeScript
path: string
```

URI of the sync root.

**Type:** string

**Since:** 21

<!--Device-SyncFolder-path: string--><!--Device-SyncFolder-path: string-End-->

**System capability:** SystemCapability.FileManagement.CloudDiskManager

**System API:** This is a system API.

## state

```TypeScript
state: SyncFolderState
```

State of the sync root.

**Type:** [SyncFolderState](arkts-corefile-clouddiskmanager-syncfolderstate-e-sys.md)

**Since:** 21

<!--Device-SyncFolder-state: SyncFolderState--><!--Device-SyncFolder-state: SyncFolderState-End-->

**System capability:** SystemCapability.FileManagement.CloudDiskManager

**System API:** This is a system API.
