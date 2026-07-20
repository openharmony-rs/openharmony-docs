# PermissionUsedType（系统接口）

表示通过何种方式使用敏感权限的枚举。

| 名称 | 值 | 说明 |  
| ----------------------- | -- | ---------------- |  
| NORMAL_TYPE | 0 | 表示通过弹窗授权或设置授权来使用敏感权限。 |  
| PICKER_TYPE | 1 | 表示通过某个PICKER服务来使用敏感权限，但此方式不会授予权限。 |  
| SECURITY_COMPONENT_TYPE | 2 | 表示通过安全控件授权的方式来使用敏感权限。安全控件是系统提供的授权控件，用户点击后应用可临时获取对应权限。 |

**起始版本：** 12

<!--Device-privacyManager-enum PermissionUsedType--><!--Device-privacyManager-enum PermissionUsedType-End-->

**系统能力：** SystemCapability.Security.AccessToken

**系统接口：** 此接口为系统接口。

## NORMAL_TYPE

```TypeScript
NORMAL_TYPE = 0
```

**起始版本：** 12

<!--Device-PermissionUsedType-NORMAL_TYPE = 0--><!--Device-PermissionUsedType-NORMAL_TYPE = 0-End-->

**系统能力：** SystemCapability.Security.AccessToken

**系统接口：** 此接口为系统接口。

## PICKER_TYPE

```TypeScript
PICKER_TYPE = 1
```

**起始版本：** 12

<!--Device-PermissionUsedType-PICKER_TYPE = 1--><!--Device-PermissionUsedType-PICKER_TYPE = 1-End-->

**系统能力：** SystemCapability.Security.AccessToken

**系统接口：** 此接口为系统接口。

## SECURITY_COMPONENT_TYPE

```TypeScript
SECURITY_COMPONENT_TYPE = 2
```

**起始版本：** 12

<!--Device-PermissionUsedType-SECURITY_COMPONENT_TYPE = 2--><!--Device-PermissionUsedType-SECURITY_COMPONENT_TYPE = 2-End-->

**系统能力：** SystemCapability.Security.AccessToken

**系统接口：** 此接口为系统接口。

