# PermissionStateChangeInfo

表示某次权限授权状态变化的详情。

**起始版本：** 18

**ArkTS模式：** ArkTS-Dyn起始版本为18；ArkTS-Sta起始版本为23。

<!--Device-abilityAccessCtrl-interface PermissionStateChangeInfo--><!--Device-abilityAccessCtrl-interface PermissionStateChangeInfo-End-->

**系统能力：** SystemCapability.Security.AccessToken

## change

```TypeScript
change: PermissionStateChangeType
```

权限授权状态变化类型。

**类型：** PermissionStateChangeType

**起始版本：** 18

**ArkTS模式：** ArkTS-Dyn起始版本为18；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-PermissionStateChangeInfo-change: PermissionStateChangeType--><!--Device-PermissionStateChangeInfo-change: PermissionStateChangeType-End-->

**系统能力：** SystemCapability.Security.AccessToken

## permissionName

```TypeScript
permissionName: Permissions
```

当前授权状态发生变化的权限名，合法的权限名取值可在\_\_\_MD\_LINK\_DESC\_USD\_0\_\_\_中查询。

**类型：** Permissions

**起始版本：** 18

**ArkTS模式：** ArkTS-Dyn起始版本为18；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-PermissionStateChangeInfo-permissionName: Permissions--><!--Device-PermissionStateChangeInfo-permissionName: Permissions-End-->

**系统能力：** SystemCapability.Security.AccessToken

## tokenID

```TypeScript
tokenID: int
```

被订阅的应用身份标识。该参数必须为大于0的整数，传入0时返回错误码12100001。 BundleInfo获取可参考：[bundleManager.getBundleInfoSync]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_。 获取。

**类型：** int

**起始版本：** 18

**ArkTS模式：** ArkTS-Dyn起始版本为18；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-PermissionStateChangeInfo-tokenID: int--><!--Device-PermissionStateChangeInfo-tokenID: int-End-->

**系统能力：** SystemCapability.Security.AccessToken

