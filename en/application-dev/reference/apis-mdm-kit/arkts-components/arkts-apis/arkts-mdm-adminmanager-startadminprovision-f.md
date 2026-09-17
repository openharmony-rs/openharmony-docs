# startAdminProvision

## Modules to Import

```TypeScript
import { adminManager } from '@kit.MDMKit';
```

## startAdminProvision

```TypeScript
function startAdminProvision(admin: Want, type: AdminType, context: common.Context, parameters: Record<string, string>): void
```

Enables the device administrator application to open a page for the BYOD administrator to perform activation.

**Since:** 15

**Required permissions:** ohos.permission.START_PROVISIONING_MESSAGE

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| admin | [Want](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-want-want-c.md) | Yes | EnterpriseAdminExtensionAbility. **Want** must contain the ability name of the EnterpriseAdminExtensionAbility and the bundle name of the application. |
| type | [AdminType](arkts-mdm-adminmanager-admintype-e.md) | Yes | Type of the activated device administrator application. Only the **ADMIN_TYPE_BYOD** type is supported. |
| context | [common.Context](../../apis-ability-kit/arkts-apis/arkts-ability-common-context-t.md) | Yes | Context information of the administrator application. |
| parameters | Record&lt;string, string&gt; | Yes | Custom parameters. The key value must contain **activateId** and may optionally include **customizedInfo** and **localDeactivationPolicy**.<br>- **activateId**: project activation ID. <br>- **customizedInfo**: enterprise-defined information. <br>- **localDeactivationPolicy**: local deactivation delay (unit: hour). This parameter is supported since API version 22. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**Examples**

```TypeScript
import { adminManager } from '@kit.MDMKit';
import { common, Want } from '@kit.AbilityKit';

let wantTemp: Want = {
  // Replace with actual values.
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};
let recordParameters: Record<string, string> = {
  // Replace with actual values.
  "activateId": "activateId testValue",
  "customizedInfo": "customizedInfo testValue"
};
// Obtain the context from the component and ensure that the return value of this.getUIContext().getHostContext() is UIAbilityContext.
const context = this.getUIContext().getHostContext() as common.UIAbilityContext;
try {
  console.info('context:' + JSON.stringify(context));
  adminManager.startAdminProvision(wantTemp, adminManager.AdminType.ADMIN_TYPE_BYOD, context, recordParameters);
  console.info('startAdminProvision::success');
} catch (error) {
  console.error('startAdminProvision::errorCode: ' + error.code + ' errorMessage: ' + error.message);
}
```
