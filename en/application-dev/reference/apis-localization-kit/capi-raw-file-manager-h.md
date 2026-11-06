# raw_file_manager.h

<!--Kit: Localization Kit-->
<!--Subsystem: Global-->
<!--Owner: @liule_123-->
<!--Designer: @buda_wy-->
<!--Tester: @lpw_work-->
<!--Adviser: @ningningW-->

## Overview

This module allows you to create and release `NativeResourceManager` objects, and open rawfiles and directories.

**File to include**: \<rawfile/raw_file_manager.h>

**Library**: librawfile.z.so

**System capability**: SystemCapability.Global.ResourceManager

**Since**: 8

**Related module**: [rawfile](capi-rawfile.md)

## Summary

### Structs

| Name| typedef Keyword| Description|
| -- | -- | -- |
| [NativeResourceManager](capi-rawfile-nativeresourcemanager.md) | NativeResourceManager | `ResourceManager` object at the native layer. `NativeResourceManager` encapsulates the Native implementation of JavaScript ResourceManager, and can be obtained through [OH_ResourceManager_InitNativeResourceManager](#oh_resourcemanager_initnativeresourcemanager).|

### Functions

| Name| Description|
| -- | -- |
| [NativeResourceManager *OH_ResourceManager_InitNativeResourceManager(napi_env env, napi_value jsResMgr)](#oh_resourcemanager_initnativeresourcemanager) | Initializes a `NativeResourceManager` object.<br>|
| [void OH_ResourceManager_ReleaseNativeResourceManager(NativeResourceManager *resMgr)](#oh_resourcemanager_releasenativeresourcemanager) | Releases a `NativeResourceManager` object and its associated resources.|
| [RawDir *OH_ResourceManager_OpenRawDir(const NativeResourceManager *mgr, const char *dirName)](#oh_resourcemanager_openrawdir) | Opens the `rawfile` directory.|
| [RawFile *OH_ResourceManager_OpenRawFile(const NativeResourceManager *mgr, const char *fileName)](#oh_resourcemanager_openrawfile) | Opens a rawfile and returns a `RawFile` object for reading the rawfile content.|
| [RawFile64 *OH_ResourceManager_OpenRawFile64(const NativeResourceManager *mgr, const char *fileName)](#oh_resourcemanager_openrawfile64) | Opens a rawfile and returns a `RawFile` object for reading the rawfile content. Files larger than 2 GB are supported.|
| [bool OH_ResourceManager_IsRawDir(const NativeResourceManager *mgr, const char *path)](#oh_resourcemanager_israwdir) | Checks whether the specified path is a subdirectory of `rawfile`. It is used to determine whether the specified path is a directory before traversing it, or whether the specified path is a file before opening it.|

## Function Description

### OH_ResourceManager_InitNativeResourceManager()

```c
NativeResourceManager *OH_ResourceManager_InitNativeResourceManager(napi_env env, napi_value jsResMgr)
```

**Description**

Initializes a `NativeResourceManager` object.<br>

**Since**: 8

**Parameters**

| Name| Description|
| -- | -- |
| napi_env env | Input parameter. Pointer to the JavaScript Native Interface (napi) environment.|
| napi_value jsResMgr | Input parameter. Reference to the JavaScript `ResourceManager` object.|

**Returns**

| Type| Description|
| -- | -- |
| [NativeResourceManager *](capi-rawfile-nativeresourcemanager.md) | Pointer to the `NativeResourceManager` object. If the initialization fails, `NULL` is returned. The possible cause is that the `env` or `jsResMgr` parameter is invalid.<br>     The memory is allocated by this function and must be released through [OH_ResourceManager_ReleaseNativeResourceManager](capi-raw-file-manager-h.md#oh_resourcemanager_releasenativeresourcemanager) after use.|

### OH_ResourceManager_ReleaseNativeResourceManager()

```c
void OH_ResourceManager_ReleaseNativeResourceManager(NativeResourceManager *resMgr)
```

**Description**

Releases a `NativeResourceManager` object and its associated resources.

**Since**: 8

**Parameters**

| Name| Description|
| -- | -- |
| [NativeResourceManager](capi-rawfile-nativeresourcemanager.md) *resMgr | Input parameter. Pointer to the `NativeResourceManager` object to be released. After the release, the `resMgr` pointer becomes invalid and cannot be used for other operations.|

### OH_ResourceManager_OpenRawDir()

```c
RawDir *OH_ResourceManager_OpenRawDir(const NativeResourceManager *mgr, const char *dirName)
```

**Description**

Opens the `rawfile` directory.

**Since**: 8

**Parameters**

| Name| Description|
| -- | -- |
| [const NativeResourceManager](capi-rawfile-nativeresourcemanager.md) *mgr | Input parameter. Pointer to the `NativeResourceManager` object.|
| const char *dirName | Input parameter. Path of the directory to be opened. Path relative to the `rawfile` root directory, for example, `images/icons`. If the value is an empty string, the `rawfile` root directory is opened.|

**Returns**

| Type| Description|
| -- | -- |
| [RawDir *](capi-rawfile-rawdir.md) | Pointer to the `RawDir` object. If the call fails or `mgr` is null, `NULL` is returned. After use, call [OH_ResourceManager_CloseRawDir](capi-raw-dir-h.md#oh_resourcemanager_closerawdir) to release it.|

**Reference**

[OH_ResourceManager_InitNativeResourceManager](capi-raw-file-manager-h.md#oh_resourcemanager_initnativeresourcemanager)

[OH_ResourceManager_CloseRawDir](capi-raw-dir-h.md#oh_resourcemanager_closerawdir)

### OH_ResourceManager_OpenRawFile()

```c
RawFile *OH_ResourceManager_OpenRawFile(const NativeResourceManager *mgr, const char *fileName)
```

**Description**

Opens a rawfile and returns a `RawFile` object for reading the rawfile content.

**Since**: 8

**Parameters**

| Name| Description|
| -- | -- |
| [const NativeResourceManager](capi-rawfile-nativeresourcemanager.md) *mgr | Input parameter. Pointer to the `NativeResourceManager` object.|
| const char *fileName | Input parameter. Path of the file to be opened. Path relative to the `rawfile` root directory, for example, `images/icons/1.png`.|

**Returns**

| Type| Description|
| -- | -- |
| [RawFile *](capi-rawfile-rawfile.md) | Pointer to the `RawFile` object. If the call fails or the input parameter is null, `NULL` is returned. After use, call [OH_ResourceManager_CloseRawFile](capi-raw-file-h.md#oh_resourcemanager_closerawfile) to release it.|

**Reference**

[OH_ResourceManager_InitNativeResourceManager](capi-raw-file-manager-h.md#oh_resourcemanager_initnativeresourcemanager)

[OH_ResourceManager_CloseRawFile](capi-raw-file-h.md#oh_resourcemanager_closerawfile)

### OH_ResourceManager_OpenRawFile64()

```c
RawFile64 *OH_ResourceManager_OpenRawFile64(const NativeResourceManager *mgr, const char *fileName)
```

**Description**

Opens a rawfile and returns a `RawFile` object for reading the rawfile content. Files larger than 2 GB are supported.

**Since**: 11

**Parameters**

| Name| Description|
| -- | -- |
| [const NativeResourceManager](capi-rawfile-nativeresourcemanager.md) *mgr | Input parameter. Pointer to the `NativeResourceManager` object.|
| const char *fileName | Input parameter. Path of the file to be opened. Path relative to the `rawfile` root directory, for example, `images/icons/1.png`.|

**Returns**

| Type| Description|
| -- | -- |
| [RawFile64 *](capi-rawfile-rawfile64.md) | Pointer to the `RawFile` object. If the call fails or the input parameter is null, `NULL` is returned. After use, call [OH_ResourceManager_CloseRawFile64](capi-raw-file-h.md#oh_resourcemanager_closerawfile64) to release it.|

**Reference**

[OH_ResourceManager_InitNativeResourceManager](capi-raw-file-manager-h.md#oh_resourcemanager_initnativeresourcemanager)

[OH_ResourceManager_CloseRawFile64](capi-raw-file-h.md#oh_resourcemanager_closerawfile64)

### OH_ResourceManager_IsRawDir()

```c
bool OH_ResourceManager_IsRawDir(const NativeResourceManager *mgr, const char *path)
```

**Description**

Checks whether the specified path is a subdirectory of `rawfile`. It is used to determine whether the specified path is a directory before traversing it, or whether the specified path is a file before opening it.

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [const NativeResourceManager](capi-rawfile-nativeresourcemanager.md) *mgr | Input parameter. Pointer to the `NativeResourceManager` object.|
| const char *path | Path to be checked. Path relative to the `rawfile` root directory, for example, `images/icons`.|

**Returns**

| Type| Description|
| -- | -- |
| bool | **true** if the path is a subdirectory in the **rawfile** directory; **false** otherwise.|
