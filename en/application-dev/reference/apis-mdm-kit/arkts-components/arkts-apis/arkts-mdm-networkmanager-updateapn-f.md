# updateApn

## Modules to Import

```TypeScript
import { networkManager } from '@kit.MDMKit';
```

## updateApn

```TypeScript
function updateApn(admin: Want, apnInfo: Record<string, string>, apnId: string): void
```

Updates the APN. This API is suitable for enterprise mobile network configuration management scenarios, such as modifying APN configuration parameters, adjusting carrier settings, and optimizing mobile network connection performance. It helps enterprises flexibly adjust mobile network configurations and ensure that the mobile network connection parameters of devices meet actual requirements.

**Since:** 20

**Required permissions:** ohos.permission.ENTERPRISE_MANAGE_APN

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| admin | [Want](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-want-want-c.md) | Yes | EnterpriseAdminExtensionAbility. **Want** must contain the ability name of the EnterpriseAdminExtensionAbility and the bundle name of the application. |
| apnInfo | Record&lt;string, string&gt; | Yes | APN information to be updated. After the setting, the system uses the updated parameters to modify the corresponding APN configuration, affecting the network connection mode and data transmission path.<br>- **apnName**: APN identifier, which is optional. <br>- **mcc**: 3-digit mobile country code (MCC), which is optional. <br>- **mnc**: 2-digit or 3-digit mobile network code (MNC), which is optional. <br>- **APN**: access point name, which is optional. <br>- **type**: APN service type, which is optional. <br>- **user**: user name for APN authentication, which is optional. <br>- **password**: password for APN authentication, which is optional. <br>- **proxy**: address of the proxy server for a common data connection, which is optional. <br>- **mmsproxy**: dedicated proxy address of the MMS service, which is optional. <br>- **authType**: authentication protocol type of the APN, which is optional. |
| apnId | string | Yes | APN ID to be updated. You can obatin the device APN information via [networkManager.queryApn](arkts-mdm-networkmanager-queryapn-f.md). |

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
let apnId: string = "1"; // Replace it as required.
try {
  networkManager.updateApn(wantTemp, apnInfo, apnId);
  console.info(`Succeeded in updating apn.`);
} catch (err) {
  console.error(`Failed to update apn. Code: ${err.code}, message: ${err.message}`);
}
```
