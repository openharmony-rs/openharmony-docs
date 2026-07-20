# PermissionUsedRequest（系统接口）

表示使用记录的查询请求。

**起始版本：** 9

<!--Device-privacyManager-interface PermissionUsedRequest--><!--Device-privacyManager-interface PermissionUsedRequest-End-->

**系统能力：** SystemCapability.Security.AccessToken

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { privacyManager } from '@kit.AbilityKit';
```

## beginTime

```TypeScript
beginTime?: number
```

查询的起始时间。单位为：毫秒。默认值：0，表示不限制起始时间。

**类型：** number

**默认值：** 0

**起始版本：** 9

<!--Device-PermissionUsedRequest-beginTime?: long--><!--Device-PermissionUsedRequest-beginTime?: long-End-->

**系统能力：** SystemCapability.Security.AccessToken

**系统接口：** 此接口为系统接口。

## bundleName

```TypeScript
bundleName?: string
```

目标应用的包名。

默认值：查询所有应用。

**类型：** string

**起始版本：** 9

<!--Device-PermissionUsedRequest-bundleName?: string--><!--Device-PermissionUsedRequest-bundleName?: string-End-->

**系统能力：** SystemCapability.Security.AccessToken

**系统接口：** 此接口为系统接口。

## deviceId

```TypeScript
deviceId?: string
```

目标应用所在设备的ID。

默认值：本端设备ID。

**类型：** string

**起始版本：** 9

<!--Device-PermissionUsedRequest-deviceId?: string--><!--Device-PermissionUsedRequest-deviceId?: string-End-->

**系统能力：** SystemCapability.Security.AccessToken

**系统接口：** 此接口为系统接口。

## endTime

```TypeScript
endTime?: number
```

查询的终止时间，不早于beginTime，否则返回错误码12100001。单位为：毫秒。默认值：0，表示不限制终止时间。

**类型：** number

**默认值：** 0

**起始版本：** 9

<!--Device-PermissionUsedRequest-endTime?: long--><!--Device-PermissionUsedRequest-endTime?: long-End-->

**系统能力：** SystemCapability.Security.AccessToken

**系统接口：** 此接口为系统接口。

## flag

```TypeScript
flag: PermissionUsageFlag
```

指定查询方式。设置为FLAG_PERMISSION_USAGE_SUMMARY时返回汇总信息；设置为FLAG_PERMISSION_USAGE_DETAIL时返回明细记录。

**类型：** PermissionUsageFlag

**起始版本：** 9

<!--Device-PermissionUsedRequest-flag: PermissionUsageFlag--><!--Device-PermissionUsedRequest-flag: PermissionUsageFlag-End-->

**系统能力：** SystemCapability.Security.AccessToken

**系统接口：** 此接口为系统接口。

## isRemote

```TypeScript
isRemote?: boolean
```

指定是否查询远端设备。false表示查询本端设备的权限使用记录，true表示查询远端设备记录。

默认值：false。

**类型：** boolean

**默认值：** false

**起始版本：** 9

<!--Device-PermissionUsedRequest-isRemote?: boolean--><!--Device-PermissionUsedRequest-isRemote?: boolean-End-->

**系统能力：** SystemCapability.Security.AccessToken

**系统接口：** 此接口为系统接口。

## permissionNames

```TypeScript
permissionNames?: Array<Permissions>
```

需要查询的权限集合。默认值：空，表示查询所有权限的使用记录。

**类型：** Array&lt;Permissions&gt;

**起始版本：** 9

<!--Device-PermissionUsedRequest-permissionNames?: Array<Permissions>--><!--Device-PermissionUsedRequest-permissionNames?: Array<Permissions>-End-->

**系统能力：** SystemCapability.Security.AccessToken

**系统接口：** 此接口为系统接口。

## tokenId

```TypeScript
tokenId?: number
```

目标应用的身份标识。目标应用的身份标识。可通过应用BundleInfo中的ApplicationInfo中的[accessTokenId](arkts-ability-applicationinfo-i.md#accesstokenid)字段获取。该参数必须为大于0的整数，传入0时返回错误码12100001。<br>BundleInfo获取可参考：[bundleManager.getBundleInfoSync](arkts-ability-bundlemanager-getbundleinfosync-f.md#getbundleinfosync-1)。

默认值：0，查询所有应用。

**类型：** number

**起始版本：** 9

<!--Device-PermissionUsedRequest-tokenId?: int--><!--Device-PermissionUsedRequest-tokenId?: int-End-->

**系统能力：** SystemCapability.Security.AccessToken

**系统接口：** 此接口为系统接口。

