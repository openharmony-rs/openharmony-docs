# PermissionUsingOptions（系统接口）

权限使用可选参数集。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

<!--Device-privacyManager-interface PermissionUsingOptions--><!--Device-privacyManager-interface PermissionUsingOptions-End-->

**系统能力：** SystemCapability.Security.AccessToken

**系统接口：** 此接口为系统接口。

## enhancedIdentity

```TypeScript
enhancedIdentity?: string
```

扩展身份，用于标识调用方的附加身份信息。当需要区分同一应用下不同调用来源的权限使用记录时传入此字段。长度不超过48个字符，调用 [startUsingPermission]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_或 [stopUsingPermission]\_\_\_JSDOC\_LINK\_DESC\_USD\_1\_\_\_时传入超长值会返回错误码12100001。 默认值：空字符串。

**类型：** string

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-PermissionUsingOptions-enhancedIdentity?: string--><!--Device-PermissionUsingOptions-enhancedIdentity?: string-End-->

**系统能力：** SystemCapability.Security.AccessToken

**系统接口：** 此接口为系统接口。

