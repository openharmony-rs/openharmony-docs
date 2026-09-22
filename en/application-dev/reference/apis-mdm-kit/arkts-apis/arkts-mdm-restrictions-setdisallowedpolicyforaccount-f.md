# setDisallowedPolicyForAccount

## Modules to Import

```TypeScript
import { restrictions } from '@kit.MDMKit';
```

## setDisallowedPolicyForAccount

```TypeScript
function setDisallowedPolicyForAccount(admin: Want, feature: string, disallow: boolean, accountId: number): void
```

Disallows a feature for a specified user.

**Since:** 14

**Deprecated since:** 26.0.0

**Substitutes:** [setDisallowedPolicyForAccount](#setdisallowedpolicyforaccount-1)(admin: Want, feature: FeatureForAccount, disallow: boolean, accountId: number)

**Required permissions:** ohos.permission.ENTERPRISE_MANAGE_RESTRICTIONS

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| admin | [Want](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-want-want-c.md) | Yes | EnterpriseAdminExtensionAbility. **Want** must contain the ability name of the EnterpriseAdminExtensionAbility and the bundle name of the application. |
| feature | string | Yes | Feature to set. <br>- **fingerprint**: device fingerprint authentication capability. Currently, this feature is supported only on PCs/2-in-1 devices. The rules for using this parameter are as follows: <br>1. If the device fingerprint authentication capability has been disabled through the [setDisallowedPolicy](arkts-mdm-restrictions-setdisallowedpolicy-f.md) API, calling this API with this parameter passed will throw a policy conflict. <br>2. After the device fingerprint authentication capability is enabled or disabled via this API for a specified user, any subsequent action via the [setDisallowedPolicy](arkts-mdm-restrictions-setdisallowedpolicy-f.md) API will override the previous setting. If [setDisallowedPolicy](arkts-mdm-restrictions-setdisallowedpolicy-f.md) enables the capability, all users gain access to the device fingerprint authentication. <br>- **print**&lt;sup&gt;20+&lt;/sup&gt;: device printing capability, which is supported only on PCs/2-in-1 devices for API versions earlier than 23, and on PCs/2-in-1 devices, smartphones, and tablets for API version 23 and later versions. If the device printing capability is disabled via this API, it remains disabled for specific users even if the [setDisallowedPolicy](arkts-mdm-restrictions-setdisallowedpolicy-f.md) API is used to enable it for those users. <br>- **mtpClient**&lt;sup&gt;20+&lt;/sup&gt;: Media Transfer Protocol (MTP) client capability (write only). Currently, this feature is supported only on PCs/2-in-1 devices. MTP allows users to linearly access media files on mobile devices. A policy conflict error will occur if this API is used to disable the MTP client capability after MTP client write has been disabled for specific users via the [setDisallowedPolicy](arkts-mdm-restrictions-setdisallowedpolicy-f.md) API. <br>- **usbStorageDeviceWrite**&lt;sup&gt;20+&lt;/sup&gt;: USB storage device write capability. Currently, this feature is supported only on enterprise PCs/2-in-1 devices. <br> If the USB storage device write permission of a user is disabled via this API in any of the following situations, a policy conflict will be reported: <br> 1. The device USB capability has been disabled via the [setDisallowedPolicy](arkts-mdm-restrictions-setdisallowedpolicy-f.md) API. <br> 2. USB storage device access policy has been set to read-only or disabled via the [setUsbStorageDeviceAccessPolicy](arkts-mdm-usbmanager-setusbstoragedeviceaccesspolicy-f.md) API. <br> 3. Storage USB devices have been disabled via the [addDisallowedUsbDevices](arkts-mdm-usbmanager-adddisallowedusbdevices-f.md) API. <br>- **diskRecoveryKey**&lt;sup&gt;20+&lt;/sup&gt;: recovery [key export](../../../security/UniversalKeystoreKit/huks-export-key-arkts.md) capability. Currently, this feature is supported only on PCs/2-in-1 devices. <br>- **sudo**&lt;sup&gt;20+&lt;/sup&gt;: superuser do (execution with superuser privileges). Currently, this feature is supported only on PCs/2-in-1 devices. If this feature is disabled, neither enterprise spaces nor personal spaces can perform operations with superuser privileges. <br>- **distributedTransmissionOutgoing**&lt;sup&gt;20+&lt;/sup&gt;: distributed one-way data transmission between devices (only data transmission to other devices is supported). A policy conflict occurs if this API is used to disable distributed one-way data transmission between devices after the distributed service has already been disabled via the [setDisallowedPolicyForAccount](arkts-mdm-restrictions-setdisallowedpolicyforaccount-f.md) API. <br>- **openFileBoost**&lt;sup&gt;23+&lt;/sup&gt;: file opening acceleration capability, which provides the file opening acceleration status awareness capability for apps. By integrating the corresponding APIs, apps can detect the acceleration status of files, and further implement features such as displaying unique UI identifiers for accelerated files, thereby optimizing user experience of file opening. Currently, this feature is supported only on PCs/2-in-1 devices. |
| disallow | boolean | Yes | Whether to disallow the feature. The value **true** means to disallow the feature; the value **false** means the opposite. |
| accountId | number | Yes | User ID, which must be greater than or equal to 0. <br>**accountId** can be obtained via APIs such as [getOsAccountLocalId](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-osaccount-accountmanager-i.md#getosaccountlocalid). |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [9200001](../errorcode-enterpriseDeviceManager.md#9200001-deviceadmin-not-enabled) | The application is not an administrator application of the device. |
| [9200002](../errorcode-enterpriseDeviceManager.md#9200002-permission-denied) | The administrator application does not have permission to manage the device. |
| [9200010](../errorcode-enterpriseDeviceManager.md#9200010-policy-conflict) | A conflict policy has been configured. |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API. |

**Examples**

```TypeScript
import { restrictions } from '@kit.MDMKit';
import { Want } from '@kit.AbilityKit';

let wantTemp: Want = {
  // Replace with actual values.
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};

try {
  // Replace parameters with actual values.
  restrictions.setDisallowedPolicyForAccount(wantTemp, 'fingerprint', true, 100);
  console.info('Succeeded in setting fingerprint disabled');
} catch (err) {
  console.error(`Failed to set fingerprint disabled. Code is ${err.code}, message is ${err.message}`);
}
```


<a id="setdisallowedpolicyforaccount-1"></a>

## setDisallowedPolicyForAccount

```TypeScript
function setDisallowedPolicyForAccount(admin: Want, feature: FeatureForAccount, disallow: boolean, accountId: number): void
```

Disallows a feature for a specified user.

**Since:** 26.0.0

**Required permissions:** ohos.permission.ENTERPRISE_MANAGE_RESTRICTIONS

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| admin | [Want](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-want-want-c.md) | Yes | EnterpriseAdminExtensionAbility. **Want** must contain the ability name of the EnterpriseAdminExtensionAbility and the bundle name of the application. |
| feature | [FeatureForAccount](arkts-mdm-restrictions-featureforaccount-e.md) | Yes | User feature to be disabled or enabled. <br>If SuperHub has been added to the user's list of non-disableable applications through the [addUserNonStopApps](arkts-mdm-applicationmanager-addusernonstopapps-f.md) API, setting this parameter to **SUPER_HUB** will cause a policy conflict and error code 9200010 will be reported. In this case, call the [removeUserNonStopApps](arkts-mdm-applicationmanager-removeusernonstopapps-f.md) API to remove SuperHub from the user's list of non-disableable applications to resolve the conflict. <br>When **feature** is **DISTRIBUTED_TRANSMISSION**, if the capability of distributed one-way data transmission between devices has been disabled via the [setDisallowedPolicyForAccount](arkts-mdm-restrictions-setdisallowedpolicyforaccount-f.md) API, calling this API to disable the distributed management service will result in a policy conflict and error code 9200010 will be reported. You can call the [setDisallowedPolicyForAccount](arkts-mdm-restrictions-setdisallowedpolicyforaccount-f.md) API to enable distributed one-way data transmission between devices to resolve the conflict. |
| disallow | boolean | Yes | Whether to disallow the feature. The value **true** means to disallow the feature; the value **false** means the opposite. |
| accountId | number | Yes | User ID, which must be greater than or equal to 0. <br>**accountId** can be obtained via APIs such as [getOsAccountLocalId](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-osaccount-accountmanager-i.md#getosaccountlocalid). <br>When **feature** is set to **SUPER_HUB**, this parameter can only be set to the ID of the current user. Otherwise, error code 9200012 will be reported. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [9200001](../errorcode-enterpriseDeviceManager.md#9200001-deviceadmin-not-enabled) | The application is not an administrator application of the device. |
| [9200002](../errorcode-enterpriseDeviceManager.md#9200002-permission-denied) | The administrator application does not have permission to manage the device. |
| [9200010](../errorcode-enterpriseDeviceManager.md#9200010-policy-conflict) | A conflict policy has been configured. |
| [9200012](../errorcode-enterpriseDeviceManager.md#9200012-parameter-verification-failed) | Parameter verification failed. |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Failed to call the API due to limited device capabilities. |

**Examples**

```TypeScript
import { restrictions } from '@kit.MDMKit';
import { Want } from '@kit.AbilityKit';

let wantTemp: Want = {
  // Replace with actual values.
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};

try {
  // Replace parameters with actual values.
  restrictions.setDisallowedPolicyForAccount(wantTemp, restrictions.FeatureForAccount.SUPER_HUB, true, 100);
  console.info('Succeeded in setting super hub disabled');
} catch (err) {
  console.error(`Failed to set super hub disabled. Code is ${err.code}, message is ${err.message}`);
}
```
