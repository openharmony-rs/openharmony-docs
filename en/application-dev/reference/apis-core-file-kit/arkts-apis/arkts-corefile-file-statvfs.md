# @ohos.file.statvfs(File System Space Statistics)

This module provides APIs for obtaining file system information, including the total size and free size of a file system, in bytes.

**Since:** 9

**System capability:** SystemCapability.FileManagement.File.FileIO

## Modules to Import

```TypeScript
import { statfs } from '@kit.CoreFileKit';
```

## Summary

### Functions

| Name | Description |
| --- | --- |
| [getFreeSize](arkts-corefile-statfs-getfreesize-f.md#getfreesize) | Obtains the free size of the specified file system, in bytes. This API uses a promise to return the result. |
| [getFreeSize](arkts-corefile-statfs-getfreesize-f.md#getfreesize-1) | Obtains the free size of the specified file system, in bytes. This API uses an asynchronous callback to return the result. |
| [getFreeSizeSync](arkts-corefile-statfs-getfreesizesync-f.md) | Obtains the free size of the specified file system, in bytes. This API returns the result synchronously. |
| [getTotalSize](arkts-corefile-statfs-gettotalsize-f.md#gettotalsize) | Obtains the total size of the specified file system, in bytes. This API uses a promise to return the result. |
| [getTotalSize](arkts-corefile-statfs-gettotalsize-f.md#gettotalsize-1) | Obtains the total size of the specified file system, in bytes. This API uses an asynchronous callback to return the result. |
| [getTotalSizeSync](arkts-corefile-statfs-gettotalsizesync-f.md) | Obtains the total size of the specified file system, in bytes. This API returns the result synchronously. |
