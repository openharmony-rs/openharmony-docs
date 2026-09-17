# addAutoStartApps

## Modules to Import

```TypeScript
import { applicationManager } from '@kit.MDMKit';
```

## addAutoStartApps

```TypeScript
function addAutoStartApps(admin: Want, autoStartApps: Array<Want>): void
```

Adds the auto-start applications for the current user. Applications added to the auto-start list via this API cannot be manually disabled for auto-start by users on the device. However, they can be removed from the auto-start list using the [removeAutoStartApps](arkts-mdm-applicationmanager-removeautostartapps-f.md) API.

**Since:** 12

**Required permissions:** ohos.permission.ENTERPRISE_MANAGE_APPLICATION

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| admin | [Want](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-want-want-c.md) | Yes | EnterpriseAdminExtensionAbility. **Want** must contain the ability name of the EnterpriseAdminExtensionAbility and the bundle name of the application. |
| autoStartApps | Array&lt;[Want](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-want-want-c.md)&gt; | Yes | Array of auto-start applications. The maximum array length is 10. For example, if there are already 5 applications in the list, a maximum of 5 more can be added via this API. **Want** must contain **bundleName** and **abilityName**. The ability can be UIAbility or ServiceExtensionAbility. If the value of **exported** in the [abilities](../../../quick-start/module-configuration-file.md#abilities) tag is **false**, the ability cannot be started. Since API version 24, you can specify whether to hide the UI when applications automatically start upon device startup by setting **isHiddenStart** in the **parameters** attribute of Want. The value **true** indicates that yes, and the value **false** indicates no. The default value is **false**. If the **true** value is used, the applications must be integrated with the status bar. Otherwise, the auto- start setting fails. (If only one application is set to hide the UI upon auto-start but the application is not integrated with the status bar, error 401 is reported. This API returns success as long as one application is successfully set.) After the setting is successful, the applications do not display the UI but their UI processes exist. The capability of hiding the UI is available only on PCs/2-in-1 devices and tablets in PC mode. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [9200001](../errorcode-enterpriseDeviceManager.md#9200001-deviceadmin-not-enabled) | The application is not an administrator application of the device. |
| [9200002](../errorcode-enterpriseDeviceManager.md#9200002-permission-denied) | The administrator application does not have permission to manage the device. |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**Examples**

```TypeScript
import { applicationManager } from '@kit.MDMKit';
import { Want } from '@kit.AbilityKit';

let wantTemp: Want = {
  // Replace it as required.
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};
let autoStartApps: Array<Want> = [
  {
    // Replace it as required.
    bundleName: 'com.example.autoStartApplication',
    abilityName: 'EntryAbility',
    // The following parameters are optional.
    parameters: {
      // Since API version 24, you can configure whether to hide the UI when applications automatically start upon device startup. The value true indicates yes. If this parameter is set to true, the applications must be integrated with the status bar. Otherwise, the automatic startup setting fails and error 401 is reported.
      isHiddenStart: true 
    }
  }
];

try {
  applicationManager.addAutoStartApps(wantTemp, autoStartApps);
  console.info('Succeeded in adding auto start applications.');
} catch(err) {
  console.error(`Failed to add auto start applications. Code: ${err.code}, message: ${err.message}`);
}
```

```TypeScript
import { applicationManager } from '@kit.MDMKit';
import { Want } from '@kit.AbilityKit';

let wantTemp: Want = {
  // Replace it as required.
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};

let autoStartApps: Array<Want> = [
  // Replace it as required.
  {
    bundleName: 'com.example.autoStartApplication',
    abilityName: 'EntryAbility',
    // The following parameters are optional.
    parameters: {
      // Since API version 24, you can configure whether to hide the UI when applications automatically start upon device startup. The value true indicates yes. If this parameter is set to true, the applications must be integrated with the status bar. Otherwise, the automatic startup setting fails and error 401 is reported.
      isHiddenStart: true 
    }
  }
];

try {
  applicationManager.addAutoStartApps(wantTemp, autoStartApps, 100, true);
  console.info('Succeeded in adding auto start applications and set disallowModify.');
} catch(err) {
  console.error(`Failed to add auto start applications and set disallowModify. Code: ${err.code}, message: ${err.message}`);
}
```


## addAutoStartApps

```TypeScript
function addAutoStartApps(admin: Want, autoStartApps: Array<Want>, accountId: number, disallowModify: boolean): void
```

Adds a list of applications that automatically start upon device startup for a specified user, and sets whether to prohibit the user from manually canceling application auto-start.

Applications can be added to the auto-start list via this API and the [addAutoStartApps](arkts-mdm-applicationmanager-addautostartapps-f.md) API. Settings from both APIs can take effect simultaneously. For a single user, the auto-start list supports a maximum of 10 applications. For example, if there are already 3 applications in the current list, a maximum of 7 more can be added for the user via this API.

**Since:** 20

**Required permissions:** ohos.permission.ENTERPRISE_MANAGE_APPLICATION

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| admin | [Want](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-want-want-c.md) | Yes | EnterpriseAdminExtensionAbility. **Want** must contain the ability name of the EnterpriseAdminExtensionAbility and the bundle name of the application. |
| autoStartApps | Array&lt;[Want](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-want-want-c.md)&gt; | Yes | Array of auto-start applications. The array can contain a maximum of 10 applications. **Want** must contain **bundleName** and **abilityName**. The ability can be UIAbility or ServiceExtensionAbility. If the value of **exported** in the [abilities](../../../quick-start/module-configuration-file.md#abilities) tag is **false**, the ability cannot be started. Since API version 24, you can specify whether to hide the UI when applications automatically start upon device startup by setting **isHiddenStart** in the **parameters** attribute of Want. The value **true** indicates that yes, and the value **false** indicates no. The default value is **false**. If the **true** value is used, the applications must be integrated with the status bar. Otherwise, the auto- start setting fails. (If only one application is set to hide the UI upon auto-start but the application is not integrated with the status bar, error 401 is reported. This API returns success as long as one application is successfully set.) After the setting is successful, the applications do not display the UI but their UI processes exist. The capability of hiding the UI is available only on PCs/2-in-1 devices and tablets in PC mode. |
| accountId | number | Yes | Account ID, which must be greater than or equal to 0. <br> You can call [getOsAccountLocalId](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-osaccount-accountmanager-i.md#getosaccountlocalid) of @ ohos.account.osAccount to obtain the ID. |
| disallowModify | boolean | Yes | Whether to prohibit the user from manually disabling application auto-start. The value **true** indicates yes and the value **false** indicates no. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [9200001](../errorcode-enterpriseDeviceManager.md#9200001-deviceadmin-not-enabled) | The application is not an administrator application of the device. |
| [9200002](../errorcode-enterpriseDeviceManager.md#9200002-permission-denied) | The administrator application does not have permission to manage the device. |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API. |

**Examples**

See [addAutoStartApps](#addautostartapps)
