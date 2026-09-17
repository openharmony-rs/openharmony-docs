# turnOnMobileData

## Modules to Import

```TypeScript
import { networkManager } from '@kit.MDMKit';
```

## turnOnMobileData

```TypeScript
function turnOnMobileData(admin: Want, isForce: boolean): void
```

Turns on mobile data.

**Since:** 20

**Required permissions:** ohos.permission.ENTERPRISE_MANAGE_NETWORK

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| admin | [Want](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-want-want-c.md) | Yes | EnterpriseAdminExtensionAbility. **Want** must contain the ability name of the EnterpriseAdminExtensionAbility and the bundle name of the application. |
| isForce | boolean | Yes | Whether to forcibly enable mobile data. <br>The value **true** means to forcibly enable mobile data. Once enabled, it cannot be turned off manually; it can only be disabled via the [turnOffMobileData](arkts-mdm-networkmanager-turnoffmobiledata-f.md) API. The value **false** means not to forcibly enable mobile data. It can be turned off manually. This API is suitable for enterprise network security management and control scenarios, such as preventing data leaks via mobile data networks, controlling network connection methods, reducing communication costs, and ensuring that devices use only enterprise networks. It helps enterprises control how devices access networks, mitigating security risks and preventing data exfiltration through mobile data networks. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [9200001](../errorcode-enterpriseDeviceManager.md#9200001-deviceadmin-not-enabled) | The application is not an administrator application of the device. |
| [9200002](../errorcode-enterpriseDeviceManager.md#9200002-permission-denied) | The administrator application does not have permission to manage the device. |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API. |

**Examples**

```TypeScript
import { networkManager } from '@kit.MDMKit';
import { Want } from '@kit.AbilityKit';

let wantTemp: Want = {
  // Replace with actual values.
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};
try {
  networkManager.turnOnMobileData(wantTemp, true);
  console.info(`Turn on mobile data succeeded`);
} catch (err) {
  console.error(`Failed to turn on mobile data. Code: ${err.code}, message: ${err.message}`);
}
```
