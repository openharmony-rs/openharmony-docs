# raw_dir.h

## Overview

Provides functions related to `rawfile` directory operations, including directory traversal, file count retrieval, file name retrieval, and directory closing.

**Library**: librawfile.z.so

**System capability**: SystemCapability.Global.ResourceManager

**Since**: 8

**Related module**: [rawfile](capi-rawfile.md)

## Summary

### Struct

| Name | typedef keyword | Description |
| -- | -- | -- |
| [RawDir](capi-rawfile-rawdir.md) | RawDir | `RawDir` represents an opened rawfile directory object, which can be used to traverse the directory and files within it. It is obtained through {@link OH_ResourceManager_OpenRawDir}, and must be closed and released through<br>{@link OH_ResourceManager_CloseRawDir} after use. |

### Macro

| Name | Description |
| -- | -- |
| GLOBAL_RAW_DIR_H | Provides functions related to `rawfile` directory operations, including directory traversal, file count retrieval, file name retrieval, and directory closing.<br>**Since**: 8<br>**System capability**: SystemCapability.Global.ResourceManager |

### Function

| Name | Description |
| -- | -- |
| [const char *OH_ResourceManager_GetRawFileName(RawDir *rawDir, int index)](#oh_resourcemanager_getrawfilename) | Obtains the file name in the `rawfile` directory by index. When you need to traverse the `rawfile` directory, you can use this function together with [OH_ResourceManager_GetRawFileCount](capi-raw-dir-h.md#oh_resourcemanager_getrawfilecount) to iterate through the directory in a loop. |
| [int OH_ResourceManager_GetRawFileCount(RawDir *rawDir)](#oh_resourcemanager_getrawfilecount) | Obtains the number of subdirectories and files under `rawfile`. When traversal of the `rawfile` directory is needed, this function can be used with [OH_ResourceManager_GetRawFileName](capi-raw-dir-h.md#oh_resourcemanager_getrawfilename) to iterate through the directory in a loop. |
| [void OH_ResourceManager_CloseRawDir(RawDir *rawDir)](#oh_resourcemanager_closerawdir) | Closes an opened `RawDir` object and releases all associated resources. After traversing the `rawfile` directory, this function must be called to close the directory and release resources. |

## Function description

### OH_ResourceManager_GetRawFileName()

```c
const char *OH_ResourceManager_GetRawFileName(RawDir *rawDir, int index)
```

**Description**

Obtains the file name in the `rawfile` directory by index. When you need to traverse the `rawfile` directory, you can use this function together with [OH_ResourceManager_GetRawFileCount](capi-raw-dir-h.md#oh_resourcemanager_getrawfilecount) to iterate through the directory in a loop.

**System capability**: SystemCapability.Global.ResourceManager

**Since**: 8

**Parameters**:

| Parameter | Description |
| -- | -- |
| [RawDir](capi-rawfile-rawdir.md) *rawDir | Input parameter. Pointer to a `RawDir` object, which is obtained through {@link OH_ResourceManager_OpenRawDir}. |
| int index | Input parameter. Index of the file in the `rawfile` directory, ranging from [0, total file count - 1]. |

**Returns**:

| Type | Description |
| -- | -- |
| const char * | Pointer to the file name string, which can be used as an input parameter of      {@link OH_ResourceManager_OpenRawFile}.      <br>`NULL` is returned upon failure. Possible causes include `rawDir` being `NULL`, `index` being out of the      valid range, or the directory being empty.      <br>After [OH_ResourceManager_CloseRawDir](capi-raw-dir-h.md#oh_resourcemanager_closerawdir) is called, this pointer is also released. If the file name      needs to be preserved, you must copy the string content in a timely manner. |

**Reference**:

{@link OH_ResourceManager_OpenRawFile}


### OH_ResourceManager_GetRawFileCount()

```c
int OH_ResourceManager_GetRawFileCount(RawDir *rawDir)
```

**Description**

Obtains the number of subdirectories and files under `rawfile`. When traversal of the `rawfile` directory is needed, this function can be used with [OH_ResourceManager_GetRawFileName](capi-raw-dir-h.md#oh_resourcemanager_getrawfilename) to iterate through the directory in a loop.

**System capability**: SystemCapability.Global.ResourceManager

**Since**: 8

**Parameters**:

| Parameter | Description |
| -- | -- |
| [RawDir](capi-rawfile-rawdir.md) *rawDir | Input parameter. Pointer to a `RawDir` object, which is obtained through {@link OH_ResourceManager_OpenRawDir}. |

**Returns**:

| Type | Description |
| -- | -- |
| int | Number of rawfile subdirectories and files, without recursively counting files and directories within      `rawfile` subdirectories. `0` is returned if `rawDir` is `NULL` or the directory is empty. |

**Reference**:

[OH_ResourceManager_GetRawFileName](capi-raw-dir-h.md#oh_resourcemanager_getrawfilename)


### OH_ResourceManager_CloseRawDir()

```c
void OH_ResourceManager_CloseRawDir(RawDir *rawDir)
```

**Description**

Closes an opened `RawDir` object and releases all associated resources. After traversing the `rawfile` directory, this function must be called to close the directory and release resources.

**System capability**: SystemCapability.Global.ResourceManager

**Since**: 8

**Parameters**:

| Parameter | Description |
| -- | -- |
| [RawDir](capi-rawfile-rawdir.md) *rawDir | Input parameter. Pointer to a `RawDir` object, which is obtained through {@link OH_ResourceManager_OpenRawDir}. After the release, the pointer becomes invalid and cannot be used for other operations. |

**Reference**:

{@link OH_ResourceManager_OpenRawDir}



