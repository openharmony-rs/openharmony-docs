# setHdcDisabled (System API)

## Modules to Import

```TypeScript
import { restrictions } from '@kit.MDMKit';
```

## setHdcDisabled

```TypeScript
function setHdcDisabled(admin: Want, disabled: boolean, callback: AsyncCallback<void>): void
```

Enables or disables [HDC](../../../../device-dev/subsystems/subsys-toolchain-hdc-guide.md). This API uses an asynchronous callback to return the result.

**Since:** 10

**Deprecated since:** 26.0.0

**Substitutes:** [setDisallowedPolicy](arkts-mdm-restrictions-setdisallowedpolicy-f.md)(admin: Want, feature: FeatureForDevice, disallow: boolean)

**Required permissions:** ohos.permission.ENTERPRISE_RESTRICT_POLICY

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| admin | [Want](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-want-want-c.md) | Yes | EnterpriseAdminExtensionAbility. **Want** must contain the ability name of the EnterpriseAdminExtensionAbility and the bundle name of the application. |
| disabled | boolean | Yes | Operation to perform. The value **true** means to disable HDC; the value **false** means the opposite. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback invoked to return the result.<br>If the operation is successful, **err** is **null**. Otherwise, **err** is an error object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [9200001](../errorcode-enterpriseDeviceManager.md#9200001-deviceadmin-not-enabled) | The application is not an administrator application of the device. |
| [9200002](../errorcode-enterpriseDeviceManager.md#9200002-permission-denied) | The administrator application does not have permission to manage the device. |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**Examples**

```TypeScript
import { restrictions } from '@kit.MDMKit';
import { Want } from '@kit.AbilityKit';

let wantTemp: Want = {
  // Replace with actual values.
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};

restrictions.setHdcDisabled(wantTemp, true, (err) => {
  if (err) {
    console.error(`Failed to set hdc disabled. Code is ${err.code}, message is ${err.message}`);
    return;
  }
  console.info('Succeeded in setting hdc disabled');
})
```

```TypeScript
import { restrictions } from '@kit.MDMKit';
import { Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let wantTemp: Want = {
  // Replace with actual values.
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};

restrictions.setHdcDisabled(wantTemp, true).then(() => {
  console.info('Succeeded in setting hdc disabled');
}).catch((err: BusinessError) => {
  console.error(`Failed to set hdc disabled. Code is ${err.code}, message is ${err.message}`);
})
```


## setHdcDisabled

```TypeScript
function setHdcDisabled(admin: Want, disabled: boolean): Promise<void>
```

Enables or disables HDC on a device. This API uses a promise to return the result.

**Since:** 10

**Deprecated since:** 26.0.0

**Substitutes:** [setDisallowedPolicy](arkts-mdm-restrictions-setdisallowedpolicy-f.md)(admin: Want, feature: FeatureForDevice, disallow: boolean)

**Required permissions:** ohos.permission.ENTERPRISE_RESTRICT_POLICY

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| admin | [Want](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-want-want-c.md) | Yes | EnterpriseAdminExtensionAbility. **Want** must contain the ability name of the EnterpriseAdminExtensionAbility and the bundle name of the application. |
| disabled | boolean | Yes | Operation to perform. The value **true** means to disable HDC; the value **false** means the opposite. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. An error object is thrown when the HDC fails to be disabled or enabled. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [9200001](../errorcode-enterpriseDeviceManager.md#9200001-deviceadmin-not-enabled) | The application is not an administrator application of the device. |
| [9200002](../errorcode-enterpriseDeviceManager.md#9200002-permission-denied) | The administrator application does not have permission to manage the device. |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**Examples**

See [setHdcDisabled](#sethdcdisabled)
