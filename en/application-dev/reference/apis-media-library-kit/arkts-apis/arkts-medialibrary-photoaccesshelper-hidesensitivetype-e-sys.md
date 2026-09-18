# HideSensitiveType (System API)

Enumerates the types of data masking applied to media resources when accessed by an application.

**Since:** 12

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**System API:** This is a system API.

## HIDE_LOCATION_AND_SHOOTING_PARAM

```TypeScript
HIDE_LOCATION_AND_SHOOTING_PARAM = 0
```

Masks geographic location and capture parameters.

**Since:** 12

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**System API:** This is a system API.

## HIDE_LOCATION_ONLY

```TypeScript
HIDE_LOCATION_ONLY = 1
```

Masks geographic location information only.

**Since:** 12

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**System API:** This is a system API.

## HIDE_SHOOTING_PARAM_ONLY

```TypeScript
HIDE_SHOOTING_PARAM_ONLY = 2
```

Masks capture parameters only.

**Since:** 12

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**System API:** This is a system API.

## NO_HIDE_SENSITIVE_TYPE

```TypeScript
NO_HIDE_SENSITIVE_TYPE = 3
```

No data masking is applied.

**Since:** 12

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**System API:** This is a system API.

## DEFAULT

```TypeScript
DEFAULT = 4
```

Applies data masking based on the [ohos.permission.MEDIA_LOCATION](../../../security/AccessToken/permissions-for-all-user.md#ohospermissionmedia_location) permission. The specifications are as follows:

- If this permission is available, no masking is applied.  
- If this permission is unavailable, geographic location is masked.

**Since:** 23

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**System API:** This is a system API.
