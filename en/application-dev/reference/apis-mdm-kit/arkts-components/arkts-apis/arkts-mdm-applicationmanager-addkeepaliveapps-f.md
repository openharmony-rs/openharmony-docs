# addKeepAliveApps

## Modules to Import

```TypeScript
import { applicationManager } from '@kit.MDMKit';
```

## addKeepAliveApps

```TypeScript
function addKeepAliveApps(admin: Want, bundleNames: Array<string>, accountId: number): void
```

Adds applications to the keep-alive list; once added, the application processes will be kept alive automatically. After the device is powered on or the application is killed, the system will proactively restart these application processes.

For applications added to the keep-alive list via this API, users cannot manually revoke their keep-alive status on the device. However, you can call the [removeKeepAliveApps](arkts-mdm-applicationmanager-removekeepaliveapps-f.md) API to remove them from the keep-alive list.

If applications are disallowed to run by calling [addDisallowedRunningBundlesSync](arkts-mdm-applicationmanager-adddisallowedrunningbundlessync-f.md), they cannot be kept alive. Otherwise, error code 9200010 will be reported.

To use similar functions on phones or tablets, call [addUserNonStopApps](arkts-mdm-applicationmanager-addusernonstopapps-f.md) or [addFreezeExemptedApps](arkts-mdm-applicationmanager-addfreezeexemptedapps-f.md). For details, see the relevant documents.

**Since:** 14

**Required permissions:** ohos.permission.ENTERPRISE_MANAGE_APPLICATION

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| admin | [Want](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-want-want-c.md) | Yes | EnterpriseAdminExtensionAbility. **Want** must contain the ability name of the EnterpriseAdminExtensionAbility and the bundle name of the application. |
| bundleNames | Array&lt;string&gt; | Yes | Array of application bundle names, which specifies the applications to be kept alive. A maximum of 5 applications are supported. |
| accountId | number | Yes | Account ID, which must be greater than or equal to 0. <br> You can call [getOsAccountLocalId](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-osaccount-accountmanager-i.md#getosaccountlocalid) of @ ohos.account.osAccount to obtain the ID. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [9200001](../errorcode-enterpriseDeviceManager.md#9200001-deviceadmin-not-enabled) | The application is not an administrator application of the device. |
| [9200002](../errorcode-enterpriseDeviceManager.md#9200002-permission-denied) | The administrator application does not have permission to manage the device. |
| [9200010](../errorcode-enterpriseDeviceManager.md#9200010-policy-conflict) | A conflict policy has been configured. |
| [9201005](../errorcode-enterpriseDeviceManager.md#9201005-failed-to-add-an-application-kept-alive) | Add keep alive applications failed. |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed.The application does not have the permission required to call the API |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error.Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types;3.Parameter verification failed. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Failed to call the API due to limited device capabilities. |

**Examples**

```TypeScript
import { applicationManager } from '@kit.MDMKit';
import { Want } from '@kit.AbilityKit';

let wantTemp: Want = {
  // Replace it as required.
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};
// Replace it as required.
let bundleNames: Array<string> = ['com.example.myapplication'];

try {
  applicationManager.addKeepAliveApps(wantTemp, bundleNames, 100);
  console.info('Succeeded in adding keep alive apps.');
} catch (err) {
  console.error(`Failed to add keep alive apps. Code is ${err.code}, message is ${err.message}`);
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

// Replace it as required.
let bundleNames: Array<string> = ['com.example.myapplication'];

try {
  applicationManager.addKeepAliveApps(wantTemp, bundleNames, 100, true);
  console.info('Succeeded in adding keep alive apps and set disallowModify.');
} catch (err) {
  console.error(`Failed to add keep alive apps and set disallowModify. Code is ${err.code}, message is ${err.message}`);
}
```


## addKeepAliveApps

```TypeScript
function addKeepAliveApps(admin: Want, bundleNames: Array<string>, accountId: number, disallowModify: boolean): void
```

Adds applications to the keep-alive list; once added, the application processes will be kept alive automatically. You can also set whether to disable manual keep-alive cancellation. After the device is powered on or the application is killed, the system will proactively restart these application processes.

Applications can be added to the keep-alive list via this API and the [addKeepAliveApps](arkts-mdm-applicationmanager-addkeepaliveapps-f.md) API. Settings from both APIs can take effect simultaneously. For a single user, the keep-alive list supports a maximum of 5 applications. For example, if there are already 3 applications in the current list, a maximum of 2 more can be added for the user via this API.

If applications are disallowed to run by calling [addDisallowedRunningBundlesSync](arkts-mdm-applicationmanager-adddisallowedrunningbundlessync-f.md), they cannot be kept alive. Otherwise, error code 9200010 will be reported.

To use similar functions on phones or tablets, call [addUserNonStopApps](arkts-mdm-applicationmanager-addusernonstopapps-f.md) or [addFreezeExemptedApps](arkts-mdm-applicationmanager-addfreezeexemptedapps-f.md). For details, see the relevant documents.

**Since:** 20

**Required permissions:** ohos.permission.ENTERPRISE_MANAGE_APPLICATION

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| admin | [Want](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-want-want-c.md) | Yes | EnterpriseAdminExtensionAbility. **Want** must contain the ability name of the EnterpriseAdminExtensionAbility and the bundle name of the application. |
| bundleNames | Array&lt;string&gt; | Yes | Array of application bundle names, which specifies the applications to be kept alive. A maximum of 5 applications are supported. <br>Applications must be installed under user 1 (a user who supports single-instance running of third-party applications) and have integrated [background services](../../../application-models/app-service-extension-ability.md#implementing-a-background-service). Otherwise, the error code 9201005 will be reported. |
| accountId | number | Yes | Account ID, which must be greater than or equal to 0. <br> You can call [getOsAccountLocalId](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-osaccount-accountmanager-i.md#getosaccountlocalid) of @ ohos.account.osAccount to obtain the ID. |
| disallowModify | boolean | Yes | Whether to restrict users from manually canceling the keep-alive status. The value **true** indicates that users are not allowed to manually cancel the keep-alive status, and the value **false** indicates the opposite. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [9200001](../errorcode-enterpriseDeviceManager.md#9200001-deviceadmin-not-enabled) | The application is not an administrator application of the device. |
| [9200002](../errorcode-enterpriseDeviceManager.md#9200002-permission-denied) | The administrator application does not have permission to manage the device. |
| [9200010](../errorcode-enterpriseDeviceManager.md#9200010-policy-conflict) | A conflict policy has been configured. |
| [9201005](../errorcode-enterpriseDeviceManager.md#9201005-failed-to-add-an-application-kept-alive) | Add keep alive applications failed. |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed.The application does not have the permission required to call the API |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Failed to call the API due to limited device capabilities. |

**Examples**

See [addKeepAliveApps](#addkeepaliveapps)
