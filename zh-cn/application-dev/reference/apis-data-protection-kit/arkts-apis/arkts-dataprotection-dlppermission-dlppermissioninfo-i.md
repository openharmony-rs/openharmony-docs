# DLPPermissionInfo

表示DLP文件的权限信息。

**起始版本：** 10

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为10。

<!--Device-dlpPermission-export interface DLPPermissionInfo--><!--Device-dlpPermission-export interface DLPPermissionInfo-End-->

**系统能力：** SystemCapability.Security.DataLossPrevention

## dlpFileAccess

```TypeScript
dlpFileAccess: DLPFileAccess
```

表示DLP文件针对用户的授权类型，例如：只读。

**类型：** DLPFileAccess

**起始版本：** 10

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为10。

<!--Device-DLPPermissionInfo-dlpFileAccess: DLPFileAccess--><!--Device-DLPPermissionInfo-dlpFileAccess: DLPFileAccess-End-->

**系统能力：** SystemCapability.Security.DataLossPrevention

## flags

```TypeScript
flags: number
```

表示DLP文件的详细操作权限，取值范围由不同[ActionFlagType]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_的组合决定。

**类型：** number

**起始版本：** 10

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为10。

<!--Device-DLPPermissionInfo-flags: number--><!--Device-DLPPermissionInfo-flags: number-End-->

**系统能力：** SystemCapability.Security.DataLossPrevention

