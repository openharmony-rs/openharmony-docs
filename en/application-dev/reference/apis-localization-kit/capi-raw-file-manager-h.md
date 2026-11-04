# raw_file_manager.h

<!--Kit: Localization Kit-->
<!--Subsystem: Global-->
<!--Owner: @liule_123-->
<!--Designer: @buda_wy-->
<!--Tester: @lpw_work-->
<!--Adviser: @ningningW-->
<!-- md-trans-meta sourceCommit=d1ed4ce8d034cfba750330bf06dcd3a9995f70ce translatedAt=2026-11-03T13:30:29.803Z pushedAt=2026-11-04T08:47:59.711Z nl=1 -->

## Overview

This module can be used to create and release NativeResourceManager objects, and open rawfile files and directories.

**File to include**: \<rawfile/raw_file_manager.h>

**Library**: librawfile.z.so

**System capability**: SystemCapability.Global.ResourceManager

**Since**: 8

**Related module**: [rawfile](capi-rawfile.md)

## Summary

### Structs

| Name | typedef Keyword | Description |
| -- | -- | -- |
| [NativeResourceManager](capi-rawfile-nativeresourcemanager.md) | NativeResourceManager | Represents the ResourceManager object on the native layer. NativeResourceManager encapsulates the native implementation of the JavaScript ResourceManager and can be obtained by calling [OH_ResourceManager_InitNativeResourceManager()](#oh_resourcemanager_initnativeresourcemanager). |

### Functions

| Name| Description|
| -- | -- |
| [NativeResourceManager *OH_ResourceManager_InitNativeResourceManager(napi_env env, napi_value jsResMgr)](#oh_resourcemanager_initnativeresourcemanager) | Initializes a NativeResourceManager object.<br> |
| [void OH_ResourceManager_ReleaseNativeResourceManager(NativeResourceManager *resMgr)](#oh_resourcemanager_releasenativeresourcemanager) | Releases a NativeResourceManager object and its associated resources. |
| [RawDir *OH_ResourceManager_OpenRawDir(const NativeResourceManager *mgr, const char *dirName)](#oh_resourcemanager_openrawdir) | Opens a rawfile directory. |
| [RawFile *OH_ResourceManager_OpenRawFile(const NativeResourceManager *mgr, const char *fileName)](#oh_resourcemanager_openrawfile) | Opens a rawfile and returns a RawFile object for reading the rawfile content. |
| [RawFile64 *OH_ResourceManager_OpenRawFile64(const NativeResourceManager *mgr, const char *fileName)](#oh_resourcemanager_openrawfile64) | Opens a rawfile and returns a RawFile object for reading the rawfile content. Files larger than 2 GB are supported. |
| [bool OH_ResourceManager_IsRawDir(const NativeResourceManager *mgr, const char *path)](#oh_resourcemanager_israwdir) | Checks whether the specified path is a subdirectory of rawfile. Used to determine whether the corresponding path is a directory before traversing directories, or whether it is a file before opening a file. |

## Function Description

### OH_ResourceManager_InitNativeResourceManager()

```c
NativeResourceManager *OH_ResourceManager_InitNativeResourceManager(napi_env env, napi_value jsResMgr)
```

**Description**

Initializes a NativeResourceManager object.<br>

**Since**: 8

**Parameters**

| Name| Description|
| -- | -- |
| napi_env env | Input parameter. Pointer to the JavaScript Native Interface (napi) environment. |
| napi_value jsResMgr | Input parameter. Reference to the JavaScript ResourceManager object. |

**Returns**

| Type                         | Description|
|-----------------------------| -- |
| [NativeResourceManager *](capi-rawfile-nativeresourcemanager.md) | Returns a pointer to the NativeResourceManager object. If the call fails, returns NULL, possibly because the parameter env or jsResMgr is invalid.<br>     The memory of this pointer is allocated by this function. After use, you must call [OH_ResourceManager_ReleaseNativeResourceManager](capi-raw-file-manager-h.md#oh_resourcemanager_releasenativeresourcemanager) to release it. |

### OH_ResourceManager_ReleaseNativeResourceManager()

```c
void OH_ResourceManager_ReleaseNativeResourceManager(NativeResourceManager *resMgr)
```

**Description**

Releases a NativeResourceManager object and its associated resources.

**Since**: 8

**Parameters**

| Name| Description|
| -- | -- |
| [NativeResourceManager](capi-rawfile-nativeresourcemanager.md) *resMgr | Input parameter. Pointer to the NativeResourceManager object to be released. After release, the resMgr pointer becomes invalid and cannot be used for other operations. |

### OH_ResourceManager_OpenRawDir()

```c
RawDir *OH_ResourceManager_OpenRawDir(const NativeResourceManager *mgr, const char *dirName)
```

**Description**

Opens a rawfile directory.

**Since**: 8

**Parameters**

| Name| Description|
| -- | -- |
| [const NativeResourceManager](capi-rawfile-nativeresourcemanager.md) *mgr | Input parameter. Pointer to the NativeResourceManager object. |
| const char *dirName | Input parameter. Path of the directory to be opened. Path relative to the rawfile root directory, for example "images/icons". When it is an empty string, the rawfile root directory is opened. |

**Returns**

| Type          | Description|
|--------------| -- |
| [RawDir *](capi-rawfile-rawdir.md) | Returns a pointer to the RawDir object. If the call fails or mgr is null, NULL is returned. After use, you must call [OH_ResourceManager_CloseRawDir](capi-raw-dir-h.md#oh_resourcemanager_closerawdir) to release it. |

**Reference**

[OH_ResourceManager_InitNativeResourceManager](capi-raw-file-manager-h.md#oh_resourcemanager_initnativeresourcemanager)

[OH_ResourceManager_CloseRawDir](capi-raw-dir-h.md#oh_resourcemanager_closerawdir)

### OH_ResourceManager_OpenRawFile()

```c
RawFile *OH_ResourceManager_OpenRawFile(const NativeResourceManager *mgr, const char *fileName)
```

**Description**

Opens a rawfile file and returns a RawFile object for reading the rawfile file content.

**Since**: 8

**Parameters**

| Name| Description|
| -- | -- |
| [const NativeResourceManager](capi-rawfile-nativeresourcemanager.md) *mgr | Input parameter. Pointer to the NativeResourceManager object. |
| const char *fileName | Input parameter. Path of the file to be opened. The path is relative to the rawfile root directory, for example, "images/icons/1.png". |

**Returns**

| Type| Description|
| -- | -- |
| [RawFile *](capi-rawfile-rawfile.md) | Returns a pointer to the RawFile object. If the call fails or the input parameter is null, NULL is returned. After use, you must call [OH_ResourceManager_CloseRawFile](capi-raw-file-h.md#oh_resourcemanager_closerawfile) to release it. |

**Reference**

[OH_ResourceManager_InitNativeResourceManager](capi-raw-file-manager-h.md#oh_resourcemanager_initnativeresourcemanager)

[OH_ResourceManager_CloseRawFile](capi-raw-file-h.md#oh_resourcemanager_closerawfile)

### OH_ResourceManager_OpenRawFile64()

```c
RawFile64 *OH_ResourceManager_OpenRawFile64(const NativeResourceManager *mgr, const char *fileName)
```

**Description**

Opens a rawfile file and returns a RawFile object for reading the rawfile file content. Files larger than 2 GB are supported.

**Since**: 11

**Parameters**

| Name| Description|
| -- | -- |
| [const NativeResourceManager](capi-rawfile-nativeresourcemanager.md) *mgr | Input parameter. Pointer to the NativeResourceManager object. |
| const char *fileName | Input parameter. Path of the file to be opened. Path relative to the rawfile root directory, for example, "images/icons/1.png". |

**Returns**

| Type             | Description|
|-----------------| -- |
| [RawFile64 *](capi-rawfile-rawfile64.md) | Returns a pointer to the RawFile object. If the call fails or the input parameter is null, NULL is returned. After use, you must call [OH_ResourceManager_CloseRawFile64](capi-raw-file-h.md#oh_resourcemanager_closerawfile64) to release it. |

**Reference**

[OH_ResourceManager_InitNativeResourceManager](capi-raw-file-manager-h.md#oh_resourcemanager_initnativeresourcemanager)

[OH_ResourceManager_CloseRawFile64](capi-raw-file-h.md#oh_resourcemanager_closerawfile64)

### OH_ResourceManager_IsRawDir()

```c
bool OH_ResourceManager_IsRawDir(const NativeResourceManager *mgr, const char *path)
```

**Description**

Checks whether the specified path is a subdirectory of a rawfile. It is used to determine whether the corresponding path is a directory before traversing directories, or whether the corresponding path is a file before opening a file.

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [const NativeResourceManager](capi-rawfile-nativeresourcemanager.md) *mgr | Input parameter. Pointer to the NativeResourceManager object. |
| const char *path | Path to be determined. Path relative to the rawfile root directory, for example, "images/icons". |

**Returns**

| Type| Description|
| -- | -- |
| bool | **true** if the path is a subdirectory in the **rawfile** directory; **false** otherwise.|


