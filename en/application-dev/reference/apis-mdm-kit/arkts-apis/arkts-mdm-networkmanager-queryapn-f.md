# queryApn

## Modules to Import

```TypeScript
import { networkManager } from '@kit.MDMKit';
```

## queryApn

```TypeScript
function queryApn(admin: Want, apnInfo: Record<string, string>): Array<string>
```

Queries the APN ID. This API is suitable for enterprise mobile network configuration audit scenarios, such as finding APNs with specific configurations, verifying whether an APN configuration exists, and providing APN ID parameters for APN management operations. It helps enterprises locate and manage APN configurations, and supplies the necessary parameter information for updating and deleting APNs.

**Since:** 20

**Required permissions:** ohos.permission.ENTERPRISE_MANAGE_APN

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| admin | [Want](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-want-want-c.md) | Yes | EnterpriseAdminExtensionAbility. **Want** must contain the ability name of the EnterpriseAdminExtensionAbility and the bundle name of the application. |
| apnInfo | Record&lt;string, string&gt; | Yes | APN information. After the setting, the system filters the APN configurations based on the specified conditions and returns the list of APN IDs that meet the conditions.<br>- **apnName**: APN identifier, which is optional. <br>- **mcc**: 3-digit mobile country code (MCC), which is optional. <br>- **mnc**: 2-digit or 3-digit mobile network code (MNC), which is optional. <br>- **apn**: access point name, which is optional. <br>- **type**: APN service type, which is optional. <br>- **user**: user name for APN authentication, which is optional. <br>- **proxy**: address of the proxy server for a common data connection, which is optional. <br>- **mmsproxy**: dedicated proxy address of the MMS service, which is optional. <br>- **authType**: authentication protocol type of the APN, which is optional. |

**Return value:**

| Type | Description |
| --- | --- |
| Array&lt;string&gt; | APN ID obtained. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [9200001](../errorcode-enterpriseDeviceManager.md#9200001-deviceadmin-not-enabled) | The application is not an administrator application of the device. |
| [9200002](../errorcode-enterpriseDeviceManager.md#9200002-permission-denied) | The administrator application does not have permission to manage the device. |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API. |

**Examples**

```TypeScript
import { Want } from '@kit.AbilityKit';
import { networkManager } from '@kit.MDMKit';

let wantTemp: Want = {
  // Replace with actual values.
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility',
};
let apnInfo: Record<string, string> = {
  // Replace with actual values.
  "apnName": "CTNET",
  "apn": "CTNET",
  "mnc": "11",
  "mcc": "460",
};
try {
  let queryResult: Array<string> = networkManager.queryApn(wantTemp, apnInfo);
  console.info(`Succeeded in querying apn, result : ${JSON.stringify(queryResult)}`);
} catch (err) {
  console.error(`Failed to query apn. Code: ${err.code}, message: ${err.message}`);
}
```


<a id="queryapn-1"></a>

## queryApn

```TypeScript
function queryApn(admin: Want, apnId: string): Record<string, string>
```

Queries the APN parameter information. This API is suitable for enterprise mobile network configuration audit scenarios, such as checking the configuration parameters of a specific APN, verifying whether the APN configuration is correct, and auditing mobile network access point settings. It helps enterprises review and validate APN configurations to ensure that mobile network settings meet requirements.

**Since:** 20

**Required permissions:** ohos.permission.ENTERPRISE_MANAGE_APN

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| admin | [Want](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-want-want-c.md) | Yes | EnterpriseAdminExtensionAbility. **Want** must contain the ability name of the EnterpriseAdminExtensionAbility and the bundle name of the application. |
| apnId | string | Yes | Specified APN ID. After the setting, the system queries the detailed parameter settings corresponding to the APN ID. You can obtain device information using [networkManager.queryApn](arkts-mdm-networkmanager-queryapn-f.md). |

**Return value:**

| Type | Description |
| --- | --- |
| Record&lt;string, string&gt; | APN parameter information of the specified APN ID.<br>- **apnName**: APN identifier. <br>- **mcc**: 3-digit mobile country code (MCC). <br>- **mnc**: 2-digit or 3-digit mobile network code (MNC). <br>- **apn**: access point name. <br>- **type**: APN service type. <br>- **user**: user name for APN authentication. <br>- **proxy**: address of the proxy server for a common data connection. <br>- **mmsproxy**: dedicated proxy address of the MMS service. <br>- **authType**: authentication protocol type of the APN. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [9200001](../errorcode-enterpriseDeviceManager.md#9200001-deviceadmin-not-enabled) | The application is not an administrator application of the device. |
| [9200002](../errorcode-enterpriseDeviceManager.md#9200002-permission-denied) | The administrator application does not have permission to manage the device. |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API. |

**Examples**

```TypeScript
import { Want } from '@kit.AbilityKit';
import { networkManager } from '@kit.MDMKit';

let wantTemp: Want = {
  // Replace with actual values.
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility',
};
let apnId: string = "1"; // Replace it as required.
try {
  let queryResult: Record<string, string> = networkManager.queryApn(wantTemp, apnId);
  console.info(`Succeeded in querying apn, result : ${JSON.stringify(queryResult)}`);
} catch (err) {
  console.error(`Failed to query apn. Code: ${err.code}, message: ${err.message}`);
}
```
