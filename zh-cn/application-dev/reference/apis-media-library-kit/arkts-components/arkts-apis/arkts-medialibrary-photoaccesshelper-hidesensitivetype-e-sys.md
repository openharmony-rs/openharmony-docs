# HideSensitiveType（系统接口）

枚举，应用访问媒体资源时，对媒体资源进行信息脱敏的类型。

**起始版本：** 12

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

## HIDE_LOCATION_AND_SHOOTING_PARAM

```TypeScript
HIDE_LOCATION_AND_SHOOTING_PARAM = 0
```

脱敏地理位置和拍摄参数。

**起始版本：** 12

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

## HIDE_LOCATION_ONLY

```TypeScript
HIDE_LOCATION_ONLY = 1
```

脱敏地理位置信息。

**起始版本：** 12

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

## HIDE_SHOOTING_PARAM_ONLY

```TypeScript
HIDE_SHOOTING_PARAM_ONLY = 2
```

脱敏拍摄参数。

**起始版本：** 12

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

## NO_HIDE_SENSITIVE_TYPE

```TypeScript
NO_HIDE_SENSITIVE_TYPE = 3
```

不脱敏。

**起始版本：** 12

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

## DEFAULT

```TypeScript
DEFAULT = 4
```

根据[ohos.permission.MEDIA_LOCATION](../../../security/AccessToken/permissions-for-all-user.md#ohospermissionmedia_location)权限进行脱敏。规格为：

- 有ohos.permission.MEDIA_LOCATION权限：不脱敏。  
- 无ohos.permission.MEDIA_LOCATION权限：脱敏地理位置信息。

**起始版本：** 23

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。
