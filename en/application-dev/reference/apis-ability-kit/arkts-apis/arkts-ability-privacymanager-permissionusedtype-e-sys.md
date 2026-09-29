# PermissionUsedType (System API)

```TypeScript
enum PermissionUsedType
```

Enumerates the means for using a sensitive permission.

| Name | Value| Description |  
| ----------------------- | -- | ---------------- |  
| NORMAL_TYPE | 0 | The sensitive permission is used after authorization through a dialog box or a system settings page. |
| PICKER_TYPE | 1 | Indicates that a sensitive permission is used through a PICKER service, but this method does not grant the permission. |
| SECURITY_COMPONENT_TYPE | 2 | Indicates that a sensitive permission is used through security component authorization. A security component is a system-provided authorization component; after the user taps it, the application can temporarily obtain the corresponding permission. |

**Since:** 12

<!--Device-privacyManager-enum PermissionUsedType--><!--Device-privacyManager-enum PermissionUsedType-End-->

**System capability:** SystemCapability.Security.AccessToken

**System API:** This is a system API.

## NORMAL_TYPE

```TypeScript
NORMAL_TYPE = 0
```

Sensitive resources are accessed with the declared permission or permission granted by the user.

**Since:** 12

**Model restriction:** This API can be used in both the stage model and FA model.

<!--Device-PermissionUsedType-NORMAL_TYPE = 0--><!--Device-PermissionUsedType-NORMAL_TYPE = 0-End-->

**System capability:** SystemCapability.Security.AccessToken

**System API:** This is a system API.

## PICKER_TYPE

```TypeScript
PICKER_TYPE = 1
```

Sensitive resources are accessed through a picker.

**Since:** 12

**Model restriction:** This API can be used in both the stage model and FA model.

<!--Device-PermissionUsedType-PICKER_TYPE = 1--><!--Device-PermissionUsedType-PICKER_TYPE = 1-End-->

**System capability:** SystemCapability.Security.AccessToken

**System API:** This is a system API.

## SECURITY_COMPONENT_TYPE

```TypeScript
SECURITY_COMPONENT_TYPE = 2
```

Sensitive resources are accessed through a security component.

**Since:** 12

**Model restriction:** This API can be used in both the stage model and FA model.

<!--Device-PermissionUsedType-SECURITY_COMPONENT_TYPE = 2--><!--Device-PermissionUsedType-SECURITY_COMPONENT_TYPE = 2-End-->

**System capability:** SystemCapability.Security.AccessToken

**System API:** This is a system API.
