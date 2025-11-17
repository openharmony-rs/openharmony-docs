# bundle_manager_common.h
<!--Kit: Ability Kit-->
<!--Subsystem: BundleManager-->
<!--Owner: @wanghang904-->
<!--Designer: @hanfeng6-->
<!--Tester: @kongjing2-->
<!--Adviser: @Brilliantry_Rui-->

## Overview

The file declares the error codes defined by BundleManager.

**File to include**: <bundle/bundle_manager_common.h>

**Library**: libbundle_ndk.z.so

**System capability**: SystemCapability.BundleManager.BundleFramework.Core

**Since**: 21

**Related module**: [Native_Bundle](capi-native-bundle.md)

## Summary

### Enums

| Name| typedef Keyword| Description|
| -- | -- | -- |
| [BundleManager_ErrorCode](#bundlemanager_errorcode) | BundleManager_ErrorCode | Enumerates the error codes.|

## Enum Description

### BundleManager_ErrorCode

```
enum BundleManager_ErrorCode
```

**Description**

Enumerates the error codes.

**Since**: 21

| Value| Description|
| -- | -- |
| BUNDLE_MANAGER_ERROR_CODE_NO_ERROR = 0 | Operation success.|
| BUNDLE_MANAGER_ERROR_CODE_PERMISSION_DENIED = 201 | No access permission.|
| BUNDLE_MANAGER_ERROR_CODE_PARAM_INVALID = 401 | Invalid parameter.|
