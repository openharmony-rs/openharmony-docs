# raw_dir.h

<!--Kit: Localization Kit-->
<!--Subsystem: Global-->
<!--Owner: @liule_123-->
<!--Designer: @buda_wy-->
<!--Tester: @lpw_work-->
<!--Adviser: @ningningW-->
<!-- md-trans-meta sourceCommit=cc8fe8b0f1b2859346994908b98ebf9b3df1ff9d translatedAt=2026-07-17T00:20:49.320Z pushedAt=2026-07-17T08:50:18.993Z -->

## Overview

Provides functions related to `rawfile` directory operations, including directory traversal, file count retrieval, file name retrieval, and directory closing.

**File to include**: <rawfile/raw_dir.h>

**Library**: librawfile.z.so

**System capability**: SystemCapability.Global.ResourceManager

**Since**: 8

**Related module**: [rawfile](capi-rawfile.md)

## Summary

### Structs

| Name| typedef Keyword| Description|
| -- | -- | -- |
| [RawDir](capi-rawfile-rawdir.md) | RawDir | An opened `rawfile` directory object, which can be used for traversing the directory and accessing files in the directory. It is obtained through [OH_ResourceManager_OpenRawDir](capi-raw-file-manager-h.md#oh_resourcemanager_openrawdir), and must be closed and released through [OH_ResourceManager_CloseRawDir](capi-raw-dir-h.md#oh_resourcemanager_closerawdir) after use. |

### Functions

| Name | Description |
| -- | -- |
| [const char *OH_ResourceManager_GetRawFileName(RawDir *rawDir, int index)](#oh_resourcemanager_getrawfilename) | Obtains the file name in the `rawfile` directory by index. When you need to traverse the `rawfile` directory, you can use this function together with [OH_ResourceManager_GetRawFileCount](capi-raw-dir-h.md#oh_resourcemanager_getrawfilecount) to iterate through the directory in a loop. |
| [int OH_ResourceManager_GetRawFileCount(RawDir *rawDir)](#oh_resourcemanager_getrawfilecount) | Obtains the number of subdirectories and files under `rawfile`. When traversal of the `rawfile` directory is needed, this function can be used with [OH_ResourceManager_GetRawFileName](capi-raw-dir-h.md#oh_resourcemanager_getrawfilename) to iterate through the directory in a loop. |
| [void OH_ResourceManager_CloseRawDir(RawDir *rawDir)](#oh_resourcemanager_closerawdir) | Closes an opened `RawDir` object and releases all associated resources. After traversing the `rawfile` directory, this function must be called to close the directory and release resources. |

## Function Description

### OH_ResourceManager_GetRawFileName()

```c
const char *OH_ResourceManager_GetRawFileName(RawDir *rawDir, int index)
```

**Description**

Obtains the file name in the `rawfile` directory by index. When you need to traverse the `rawfile` directory, you can use this function together with [OH_ResourceManager_GetRawFileCount](capi-raw-dir-h.md#oh_resourcemanager_getrawfilecount) to iterate through the directory in a loop.

**Since**: 8

**Parameters**

| Name| Description|
| -- | -- |
| [RawDir](capi-rawfile-rawdir.md) *rawDir | Input parameter. Pointer to a `RawDir` object, which is obtained through [OH_ResourceManager_OpenRawDir](capi-raw-file-manager-h.md#oh_resourcemanager_openrawdir). |
| int index | Input parameter. Index of the file in the `rawfile` directory, ranging from [0, total file count - 1]. |

**Returns**

| Type | Description |
| -- | -- |
| const char * | Pointer to the file name string, which can be used as an input parameter of [OH_ResourceManager_OpenRawFile](capi-raw-file-manager-h.md#oh_resourcemanager_openrawfile).<br>     `NULL` is returned upon failure. Possible causes include `rawDir` being `NULL`, `index` being out of the valid range, or the directory being empty.<br>     After [OH_ResourceManager_CloseRawDir](capi-raw-dir-h.md#oh_resourcemanager_closerawdir) is called, this pointer is also released. If the file name needs to be preserved, you must copy the string content in a timely manner. |

**Reference**

[OH_ResourceManager_OpenRawFile](capi-raw-file-manager-h.md#oh_resourcemanager_openrawfile)

### OH_ResourceManager_GetRawFileCount()

```c
int OH_ResourceManager_GetRawFileCount(RawDir *rawDir)
```

**Description**

Obtains the number of subdirectories and files under `rawfile`. When traversal of the `rawfile` directory is needed, this function can be used with [OH_ResourceManager_GetRawFileName](capi-raw-dir-h.md#oh_resourcemanager_getrawfilename) to iterate through the directory in a loop.

**Since**: 8

**Parameters**

| Name| Description|
| -- | -- |
| [RawDir](capi-rawfile-rawdir.md) *rawDir | Input parameter. Pointer to a `RawDir` object, which is obtained through [OH_ResourceManager_OpenRawDir](capi-raw-file-manager-h.md#oh_resourcemanager_openrawdir). |

**Returns**

| Type| Description|
| -- | -- |
| int | Number of rawfile subdirectories and files, without recursively counting files and directories within `rawfile` subdirectories. `0` is returned if `rawDir` is `NULL` or the directory is empty. |

**Reference**

[OH_ResourceManager_GetRawFileName](capi-raw-dir-h.md#oh_resourcemanager_getrawfilename)

### OH_ResourceManager_CloseRawDir()

```c
void OH_ResourceManager_CloseRawDir(RawDir *rawDir)
```

**Description**

Closes an opened `RawDir` object and releases all associated resources. After traversing the `rawfile` directory, this function must be called to close the directory and release resources.

**Since**: 8

**Parameters**

| Name| Description|
| -- | -- |
| [RawDir](capi-rawfile-rawdir.md) *rawDir | Input parameter. Pointer to a `RawDir` object, which is obtained through [OH_ResourceManager_OpenRawDir](capi-raw-file-manager-h.md#oh_resourcemanager_openrawdir). After the release, the pointer becomes invalid and cannot be used for other operations. |

**Reference**

[OH_ResourceManager_OpenRawDir](capi-raw-file-manager-h.md#oh_resourcemanager_openrawdir)