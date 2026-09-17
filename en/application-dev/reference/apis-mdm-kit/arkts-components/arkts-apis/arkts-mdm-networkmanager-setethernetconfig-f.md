# setEthernetConfig

## Modules to Import

```TypeScript
import { networkManager } from '@kit.MDMKit';
```

## setEthernetConfig

```TypeScript
function setEthernetConfig(admin: Want, networkInterface: string, config: InterfaceConfig): void
```

Sets the IP address of a specific Ethernet interface. This API is suitable for enterprise network management scenarios, such as configuring static IP addresses for devices, centrally managing IP address allocation for enterprise network devices, and setting network parameters. It helps enterprises centrally manage network configurations and ensures that device network parameters comply with enterprise network management policies.

**Since:** 23

**Required permissions:** ohos.permission.ENTERPRISE_MANAGE_NETWORK

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| admin | [Want](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-want-want-c.md) | Yes | EnterpriseAdminExtensionAbility. **Want** must contain the ability name of the EnterpriseAdminExtensionAbility and the bundle name of the application. |
| networkInterface | string | Yes | Network interface name to set. |
| config | [InterfaceConfig](arkts-mdm-networkmanager-interfaceconfig-i.md) | Yes | Network interface configuration to set. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [9200001](../errorcode-enterpriseDeviceManager.md#9200001-deviceadmin-not-enabled) | The application is not an administrator application of the device. |
| [9200002](../errorcode-enterpriseDeviceManager.md#9200002-permission-denied) | The administrator application does not have permission to manage the device. |
| [9200012](../errorcode-enterpriseDeviceManager.md#9200012-parameter-verification-failed) | Parameter verification failed. |
| [9201010](../errorcode-enterpriseDeviceManager.md#9201010-failed-to-configure-the-ethernet-network-interface) | Ethernet configuration failed. Ethernet device not connected. |
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
let config: networkManager.InterfaceConfig = {
  // Replace with actual values.
  "ipSetMode": networkManager.IpSetMode.STATIC,
  "ipAddress": "192.168.1.121",
  "gateway": "192.168.1.1",
  "netMask": "255.255.255.0",
  "dnsServers": "192.168.1.1"
}
let networkInterface: string = "eth0"; // Replace it as required.
try {
  networkManager.setEthernetConfig(wantTemp, networkInterface, config);
  console.info('Succeeded in setting ethernet config.');
} catch (err) {
  console.error(`Failed to set ethernet config. Code: ${err.code}, message: ${err.message}`);
}
```
