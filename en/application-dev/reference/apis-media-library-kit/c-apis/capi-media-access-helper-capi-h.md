# media_access_helper_capi.h

## Overview

The file declares the APIs for album management.

**Library**: libmedia_asset_manager.so

**System capability**: SystemCapability.FileManagement.PhotoAccessHelper.Core

**Since**: 12

**Related module**: [MediaAssetManager](capi-mediaassetmanager.md)

## Summary

### Function

| Name | Description |
| -- | -- |
| [MediaLibrary_ErrorCode OH_MediaAccessHelper_ApplyChanges(OH_MediaAssetChangeRequest* changeRequest)](#oh_mediaaccesshelper_applychanges) | Applies changes to an asset or album. |

## Function description

### OH_MediaAccessHelper_ApplyChanges()

```c
MediaLibrary_ErrorCode OH_MediaAccessHelper_ApplyChanges(OH_MediaAssetChangeRequest* changeRequest)
```

**Description**

Applies changes to an asset or album.

**Required permission**: ohos.permission.WRITE_IMAGEVIDEO

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_MediaAssetChangeRequest* changeRequest | Change request. |

**Returns**:

| Type | Description |
| -- | -- |
| MediaLibrary_ErrorCode | MEDIA_LIBRARY_OK if the method call succeeds.      <br>MEDIA_LIBRARY_PARAMETER_ERROR Parameter error. Possible causes:      <br>1. Mandatory parameters are left unspecified.      <br>2. Incorrect parameter types.      <br>3. Parameter verification failed.      <br>MEDIA_LIBRARY_PERMISSION_DENIED Permission is denied.      <br>MEDIA_LIBRARY_INTERNAL_SYSTEM_ERROR if internal system error. |


