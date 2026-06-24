# setEthernetConfig

## setEthernetConfig

```TypeScript
function setEthernetConfig(admin: Want, networkInterface: string, config: InterfaceConfig): void
```

�����ض���̫������ӿڵ�IP��ַ��

**起始版本：** 23

**需要权限：** ohos.permission.ENTERPRISE_MANAGE_NETWORK

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| admin | Want | 是 | ��ҵ�豸������չ����� |
| networkInterface | string | 是 | Ҫ���õ�����ӿ����� |
| config | InterfaceConfig | 是 | Ҫ���õ�����ӿ�������Ϣ�� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [9200001](../../errorcode-universal.md#9200001-The) | The application is not an administrator application of the device. |
| [9200002](../../errorcode-universal.md#9200002-The) | The administrator application does not have permission to manage the device. |
| [9200012](../../errorcode-universal.md#9200012-Parameter) | Parameter verification failed. |
| [9201010](../../errorcode-universal.md#9201010-Ethernet) | Ethernet configuration failed. Ethernet device not connected. |
| [201](../../errorcode-universal.md#201-Permission) | Permission verification failed.<br/>The application does not have the permission required to call the API. |

**示例：**

```TypeScript
import { Want } from '@kit.AbilityKit';
import { networkManager } from '@kit.MDMKit';

let wantTemp: Want = {
  // 需根据实际情况进行替换
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility',
};
let config: networkManager.InterfaceConfig = {
  // 需根据实际情况进行替换
  "ipSetMode": networkManager.IpSetMode.STATIC,
  "ipAddress": "192.168.1.121",
  "gateway": "192.168.1.1",
  "netMask": "255.255.255.0",
  "dnsServers": "192.168.1.1"
}
let networkInterface: string = "eth0"; // 需根据实际情况进行替换
try {
  networkManager.setEthernetConfig(wantTemp, networkInterface, config);
  console.info('Succeeded in setting ethernet config.');
} catch (err) {
  console.error(`Failed to set ethernet config. Code: ${err.code}, message: ${err.message}`);
}

```

