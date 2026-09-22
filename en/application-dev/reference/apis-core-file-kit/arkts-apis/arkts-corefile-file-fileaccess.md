# @ohos.file.fileAccess(User File Access and Management)

The **fileAccess** module provides a framework for accessing and operating user files based on [extension](../../../application-models/extensionability-overview.md). This module interacts with a variety of file management services, such as the storage management service, and provides a set of unified file access and management APIs for system applications. The storage management service manages both the directories of the built-in storage and resources on external devices, such as shared disks, USB flash drives, and SD cards.

> **NOTE:** 
> 
> - Currently, the APIs of this module can be called only by **FilePicker** and **FileManager**.

**Since:** 9

**Deprecated since:** 23

**Substitutes:** [fileIo](arkts-corefile-fileio-n.md)

**System capability:** SystemCapability.FileManagement.UserFileService

## Modules to Import

```TypeScript
import { fileAccess } from '@kit.CoreFileKit';
```

## Summary

<!--Del-->
### Functions(System API)

| Name | Description |
| --- | --- |
| [createFileAccessHelper](arkts-corefile-fileaccess-createfileaccesshelper-f-sys.md#createfileaccesshelper) | Creates a **Helper** object to bind with all file management services in the system. This API returns the result synchronously. |
| [createFileAccessHelper](arkts-corefile-fileaccess-createfileaccesshelper-f-sys.md#createfileaccesshelper-1) | Creates a **Helper** object to bind with the specified Wants. This API returns the result synchronously. The **Helper** object provides file access and management capabilities. |
| [getFileAccessAbilityInfo](arkts-corefile-fileaccess-getfileaccessabilityinfo-f-sys.md#getfileaccessabilityinfo) | Obtains information about all Wants with **extension** set to **fileAccess** in the system. A Want contains information for starting an ability. This API uses an asynchronous callback to return the result. |
| [getFileAccessAbilityInfo](arkts-corefile-fileaccess-getfileaccessabilityinfo-f-sys.md#getfileaccessabilityinfo-1) | Obtains information about all Wants with **extension** set to **fileAccess** in the system. A Want contains information for starting an ability. This API uses a promise to return the result. |
<!--DelEnd-->

<!--Del-->
### Interfaces(System API)

| Name | Description |
| --- | --- |
| [CopyResult](arkts-corefile-fileaccess-copyresult-i-sys.md) | Defines the information returned when the file copy operation fails. If the copy operation is successful, no information is returned. |
| [FileAccessHelper](arkts-corefile-fileaccess-fileaccesshelper-i-sys.md) | Provides a **FileAccessHelper** object. |
| [FileInfo](arkts-corefile-fileaccess-fileinfo-i-sys.md) | Provides APIs for managing file or directory attribute information. |
| [FileIterator](arkts-corefile-fileaccess-fileiterator-i-sys.md) | Provides the **FileIterator** object. |
| [MoveResult](arkts-corefile-fileaccess-moveresult-i-sys.md) | Represents the information returned when the move operation fails. If the operation is successful, no information is returned. |
| [NotifyMessage](arkts-corefile-fileaccess-notifymessage-i-sys.md) | Represents the notification message. |
| [RootInfo](arkts-corefile-fileaccess-rootinfo-i-sys.md) | Provides APIs for managing the device's root attribute information. |
| [RootIterator](arkts-corefile-fileaccess-rootiterator-i-sys.md) | Provides an iterator object of the device root directory. |
<!--DelEnd-->

<!--Del-->
### Enums(System API)

| Name | Description |
| --- | --- |
| [FileKey](arkts-corefile-fileaccess-filekey-e-sys.md) | Property elements that support the file queries. |
| [NotifyType](arkts-corefile-fileaccess-notifytype-e-sys.md) | Enumerates the notification types. |
| [OPENFLAGS](arkts-corefile-fileaccess-openflags-e-sys.md) | Enumerates the file open modes. |
<!--DelEnd-->

<!--Del-->
### Constants(System API)

| Name | Description |
| --- | --- |
| [DEVICES_URI](arkts-corefile-fileaccess-con-sys.md#devices_uri) | Indicates the root uri of the device |
<!--DelEnd-->
