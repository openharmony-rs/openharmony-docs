# removeDisallowedWifiList

## removeDisallowedWifiList

```TypeScript
function removeDisallowedWifiList(admin: Want, list: Array<WifiAccessInfo>): void
```

�Ƴ�Wi-Fi�������������Ƴ����������еĲ���Wi-Fi����ǰ�豸���������ӽ���������ʣ���Wi-Fi�����Ƴ����������е�����Wi-Fi����ǰ�豸�������������Wi-Fi��

**起始版本：** 19

**需要权限：** ohos.permission.ENTERPRISE_MANAGE_WIFI

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| admin | Want | 是 | ��ҵ�豸������չ�����Want�б��������ҵ�豸������չ������abilityName������Ӧ�õ�bundleName�� |
| list | Array&lt;WifiAccessInfo&gt; | 是 | ���Ƴ���Wi-Fi�����������顣�����ܳ��Ȳ��ܳ���200�� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [9200001](../../errorcode-universal.md#9200001-The) | The application is not an administrator application of the device. |
| [9200002](../../errorcode-universal.md#9200002-The) | The administrator application does not have permission to manage the device. |
| [201](../../errorcode-universal.md#201-Permission) | Permission verification failed. The application does not have the permission<br/>required to call the API. |

**示例：**

```TypeScript
import { wifiManager } from '@kit.MDMKit';
import { Want } from '@kit.AbilityKit';

let wantTemp: Want = {
  // 需根据实际情况进行替换
  bundleName: 'com.example.edmtest',
  abilityName: 'EnterpriseAdminAbility'
};
try {
  let wifiIds: Array<wifiManager.WifiAccessInfo> = [{
    // 需根据实际情况进行替换
    ssid: "wifi_name",
    bssid: "68:77:24:77:A6:D8"
  }];
  wifiManager.removeDisallowedWifiList(wantTemp, wifiIds);
  console.info(`Succeeded in removing disallowed Wi-Fi list.`);
} catch (err) {
  console.error(`Failed to remove disallowed Wi-Fi list. Code: ${err.code}, message: ${err.message}`);
}

```

