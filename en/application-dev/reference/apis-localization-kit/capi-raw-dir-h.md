# raw_dir.h

<!--Kit: Localization Kit-->
<!--Subsystem: Global-->
<!--Owner: @liule_123-->
<!--Designer: @buda_wy-->
<!--Tester: @lpw_work-->
<!--Adviser: @ningningW-->
<!-- md-trans-meta sourceCommit=d1ed4ce8d034cfba750330bf06dcd3a9995f70ce translatedAt=2026-11-04T03:50:41.891Z pushedAt=2026-11-04T10:13:14.879Z nl=1 -->

## Overview

Provides functions for rawfile directory operations, including iterating a directory, obtaining the number of files, obtaining file names, and closing a directory.

**File to include**: <rawfile/raw_dir.h>

**Library**: librawfile.z.so

**System capability**: SystemCapability.Global.ResourceManager

**Since**: 8

**Related module**: [rawfile](capi-rawfile.md)

## Summary

### Structs

| Name| typedef Keyword| Description|
| -- | -- | -- |
| [RawDir](capi-rawfile-rawdir.md) | RawDir | Represents an opened rawfile directory object, which can be used to iterate the directory and the files in it. It is obtained through the [OH_ResourceManager_OpenRawDir](capi-raw-file-manager-h.md#oh_resourcemanager_openrawdir) function, and must be closed and released by calling [OH_ResourceManager_CloseRawDir](capi-raw-dir-h.md#oh_resourcemanager_closerawdir) after use. |

### Functions

| Name | Description |
| -- | -- |
| [const char *OH_ResourceManager_GetRawFileName(RawDir *rawDir, int index)](#oh_resourcemanager_getrawfilename) | Obtains the name of a file in the rawfile directory by index. When you need to iterate the rawfile directory, you can use this function together with [OH_ResourceManager_GetRawFileCount](capi-raw-dir-h.md#oh_resourcemanager_getrawfilecount) to iterate the directory in a loop. |
| [int OH_ResourceManager_GetRawFileCount(RawDir *rawDir)](#oh_resourcemanager_getrawfilecount) | Obtains the number of subdirectories and files in the rawfile directory. When you need to iterate the rawfile directory, you can use this function together with [OH_ResourceManager_GetRawFileName](capi-raw-dir-h.md#oh_resourcemanager_getrawfilename) to iterate the directory in a loop. |
| [void OH_ResourceManager_CloseRawDir(RawDir *rawDir)](#oh_resourcemanager_closerawdir) | Closes an opened RawDir object and releases all related resources. After iterating the rawfile directory, you must call this function to close the directory and release resources. |

## Function Description

### OH_ResourceManager_GetRawFileName()

```c
const char *OH_ResourceManager_GetRawFileName(RawDir *rawDir, int index)
```

**Description**

Obtains the name of a file in the rawfile directory by index. When you need to iterate the rawfile directory, you can use this function together with [OH_ResourceManager_GetRawFileCount](capi-raw-dir-h.md#oh_resourcemanager_getrawfilecount) to iterate the directory in a loop.

**Since**: 8

**Parameters**

| Name| Description|
| -- | -- |
| [RawDir](capi-rawfile-rawdir.md) *rawDir | Input parameter. Pointer to the RawDir object, obtained through [OH_ResourceManager_OpenRawDir](capi-raw-file-manager-h.md#oh_resourcemanager_openrawdir). |
| int index | Input parameter. Index of the file in the rawfile directory. The value ranges from 0 to the total number of files minus 1. |

**Returns**

| Type | Description |
| -- | -- |
| const char * | Pointer to the file name string, which can be used as an input parameter of [OH_ResourceManager_OpenRawFile](capi-raw-file-manager-h.md#oh_resourcemanager_openrawfile).<br>     NULL is returned on failure. Possible causes include rawDir being NULL, index being out of the valid range, or the directory being empty.<br>     After [OH_ResourceManager_CloseRawDir](capi-raw-dir-h.md#oh_resourcemanager_closerawdir) is called, this pointer is released at the same time. If you need to save the file name, copy the string content in a timely manner. |

**Reference**

[OH_ResourceManager_OpenRawFile](capi-raw-file-manager-h.md#oh_resourcemanager_openrawfile)


### OH_ResourceManager_GetRawFileCount()

```c
int OH_ResourceManager_GetRawFileCount(RawDir *rawDir)
```

**Description**

Obtains the number of subdirectories and files in the rawfile directory. When you need to iterate the rawfile directory, you can use this function together with [OH_ResourceManager_GetRawFileName](capi-raw-dir-h.md#oh_resourcemanager_getrawfilename) to iterate the directory in a loop.

**Since**: 8

**Parameters**

| Name| Description|
| -- | -- |
| [RawDir](capi-rawfile-rawdir.md) *rawDir | Input parameter. Pointer to the RawDir object, obtained through [OH_ResourceManager_OpenRawDir](capi-raw-file-manager-h.md#oh_resourcemanager_openrawdir). |

**Returns**

| Type| Description|
| -- | -- |
| int | Number of rawfile subdirectories and files. Subdirectories and files in rawfile subdirectories are not counted recursively. Returns 0 if rawDir is NULL or the directory is empty. |

**Reference**

[OH_ResourceManager_GetRawFileName](capi-raw-dir-h.md#oh_resourcemanager_getrawfilename)


### OH_ResourceManager_CloseRawDir()

```c
void OH_ResourceManager_CloseRawDir(RawDir *rawDir)
```

**Description**

Closes an opened RawDir object and releases all related resources. After iterating the rawfile directory, you must call this function to close the directory and release resources.

**Since**: 8

**Parameters**

| Name| Description|
| -- | -- |
| [RawDir](capi-rawfile-rawdir.md) *rawDir | Input parameter. Pointer to the RawDir object, obtained through [OH_ResourceManager_OpenRawDir](capi-raw-file-manager-h.md#oh_resourcemanager_openrawdir). After the directory is closed, the pointer becomes invalid and cannot be used for other operations. |

**Reference**

[OH_ResourceManager_OpenRawDir](capi-raw-file-manager-h.md#oh_resourcemanager_openrawdir)


