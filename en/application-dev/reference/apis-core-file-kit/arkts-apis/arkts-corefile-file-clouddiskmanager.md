# @ohos.file.cloudDiskManager(Cloud Disk Management)

This module enables the File Manager to obtain the sync root information registered by third-party cloud disks.

**Since:** 21

<!--Device-unnamed-declare namespace cloudDiskManager--><!--Device-unnamed-declare namespace cloudDiskManager-End-->

**System capability:** SystemCapability.FileManagement.CloudDiskManager

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { cloudDiskManager } from '@kit.CoreFileKit';
```

## Summary

<!--Del-->
### Classes(System API)

| Name | Description |
| --- | --- |
| [CloudDiskSystemAccessor](arkts-corefile-clouddiskmanager-clouddisksystemaccessor-c-sys.md) | A class that enables the File Manager to access cloud disk system capabilities, such as hydrating and dehydrating files. |
| [SyncFolderAccessor](arkts-corefile-clouddiskmanager-syncfolderaccessor-c-sys.md) | A sync root management class that enables the File Manager to access the sync root information registered by third- party cloud disks. |
<!--DelEnd-->

<!--Del-->
### Interfaces(System API)

| Name | Description |
| --- | --- |
| [HydrateProgress](arkts-corefile-clouddiskmanager-hydrateprogress-i-sys.md) | Encapsulates the hydrate progress information. |
| [SyncFolder](arkts-corefile-clouddiskmanager-syncfolder-i-sys.md) | Encapsulates the sync root information. |
<!--DelEnd-->

<!--Del-->
### Enums(System API)

| Name | Description |
| --- | --- |
| [CallbackType](arkts-corefile-clouddiskmanager-callbacktype-e-sys.md) | Enumerates the callback types for cloud file data fetching. |
| [HydratePriority](arkts-corefile-clouddiskmanager-hydratepriority-e-sys.md) | Enumerates the priority levels of the hydrate task. |
| [HydrateProgressState](arkts-corefile-clouddiskmanager-hydrateprogressstate-e-sys.md) | Enumerates the states of the hydrate progress. |
| [SyncFolderState](arkts-corefile-clouddiskmanager-syncfolderstate-e-sys.md) | Enumerates the states of the sync root. |
<!--DelEnd-->
