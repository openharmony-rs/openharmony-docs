# PermissionRequestResult

PermissionRequestResult is the result object of a permission request. Developers need to first create an atManager instance, and then call the requestPermissionsFromUser method to request permissions. This method returns a PermissionRequestResult object, through which developers can determine the permission request result based on its properties. For details about the overall permission request process and atManager, see [@ohos.abilityAccessCtrl (Application Access Control)](arkts-ability-abilityaccessctrl-n.md).

**Since:** 9

**System capability:** SystemCapability.Security.AccessToken

## authResults

```TypeScript
authResults: Array<number>
```

Authorization result corresponding to each requested permission.

- -1: Not authorized. Starting from API version 12, you can combine this with dialogShownResults to further  
determine the reason: if dialogShownResults is true, it means the user explicitly denied the request this time; if false, it means the current state does not require a dialog to be shown, and the user usually needs to go to system settings to make changes.  
- 0: Authorized, the application can continue to access protected resources associated with this permission.  
- 2: Invalid request, usually indicating that the permission is not declared, the permission name is invalid, or  
the special request conditions for this permission are not met. Developers should check the permission name, the permission declaration in module.json, and the request conditions for the corresponding permission.

**Type:** Array&lt;number&gt;

**Since:** 9

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Security.AccessToken

## dialogShownResults

```TypeScript
dialogShownResults?: Array<boolean>
```

Indicates whether an authorization dialog was actually shown for each permission during this request process.

- true: The system has shown the authorization dialog.  
- false: The system did not show a dialog, usually because the current permission state, permission type, or system  
policy does not allow proceeding with the dialog authorization path.

When authResults is -1, combining it with this field can further distinguish between "rejected by the user this time" and "dialog is no longer shown currently". If this field is not returned, it means this result does not include the authorization dialog display status.

**Type:** Array&lt;boolean&gt;

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Security.AccessToken

## errorReasons

```TypeScript
errorReasons?: Array<number>
```

Reason code corresponding to each permission request. Mainly used to explain the specific reasons for authorization failure, invalid request, or inability to show a dialog. If this field is not returned, it means this result does not include reason codes.

- 0: This request is valid.  
- 1: Invalid permission name, please check the permission name format and value.  
- 2: Permission not declared, please declare this permission in module.json.  
- 3: The request conditions for the corresponding permission are not met, for example, some location permissions  
require additional prerequisites. Currently only applies to location permissions, including [ohos.permission.LOCATION](../../../security/AccessToken/permissions-for-all-user.md#ohospermissionlocation) and [ohos.permission.APPROXIMATELY_LOCATION](../../../security/AccessToken/permissions-for-all-user.md#ohospermissionapproximately_location).  
- 4: The user has not agreed to the privacy statement, please guide the user to agree to the privacy statement  
before requesting permissions.  
- 5: This permission does not support requesting via permission dialog; the request method may be restricted or  
controlled by system policy. Please use the authorization method supported by this permission.  
- 6: This permission is of the [manual_settings](../../../security/AccessToken/app-permission-mgmt-overview.md#manual_settings-manual-authorization) type and can only be authorized through the settings page. This reason code is supported starting from API version 21.  
- 12: Service exception, please try again later.

**Type:** Array&lt;number&gt;

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.Security.AccessToken

## permissions

```TypeScript
permissions: Array<string>
```

Array of permissions to be requested this time. **Atomic service API:** Starting from API version 11, this API supports use in atomic services.

**Type:** Array&lt;string&gt;

**Since:** 9

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Security.AccessToken
