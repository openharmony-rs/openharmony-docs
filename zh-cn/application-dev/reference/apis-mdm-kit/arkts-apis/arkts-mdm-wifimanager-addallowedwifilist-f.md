# addAllowedWifiList

## addAllowedWifiList

```TypeScript
function addAllowedWifiList(admin: Want, list: Array<WifiAccessInfo>): void
```

����Wi-Fi������������������������ǰ�豸���������Ӹ������µ�Wi-Fi��

��������£����ñ��ӿڻᱨ���Գ�ͻ��

1. �Ѿ�ͨ��[setDisallowedPolicy](arkts-mdm-restrictions-setdisallowedpolicy-f.md#setDisallowedPolicy-1)�ӿڽ������豸Wi-Fi������ͨ��[setDisallowedPolicy](arkts-mdm-restrictions-setdisallowedpolicy-f.md#setDisallowedPolicy-1)���Wi-Fi���ú󣬿ɽ����ͻ��
2. �Ѿ�ͨ��[addDisallowedWifiList](arkts-mdm-wifimanager-adddisallowedwifilist-f.md#addDisallowedWifiList-1)�ӿ�������Wi-Fi����������ͨ��[removeDisallowedWifiList](arkts-mdm-wifimanager-removedisallowedwifilist-f.md#removeDisallowedWifiList-1)�Ƴ�Wi-Fi���������󣬿ɽ����ͻ��

**起始版本：** 19

**需要权限：** ohos.permission.ENTERPRISE_MANAGE_WIFI

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| admin | Want | 是 | ��ҵ�豸������չ�����Want�б��������ҵ�豸������չ������abilityName������Ӧ�õ�bundleName�� |
| list | Array&lt;WifiAccessInfo&gt; | 是 | Wi-Fi�����������顣�����ܳ��Ȳ��ܳ���200�����磬����ǰ������������������100��Wi-Fi�������֧��ͨ���ýӿ�������100���� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [9200001](../../errorcode-universal.md#9200001-The) | The application is not an administrator application of the device. |
| [9200002](../../errorcode-universal.md#9200002-The) | The administrator application does not have permission to manage the device. |
| [9200010](../../errorcode-universal.md#9200010-A) | A conflict policy has been configured. |
| [201](../../errorcode-universal.md#201-Permission) | Permission verification failed. The application does not have the permission<br/>required to call the API. |

**示例：**

```TypeScript
import { wifiManager } from '@kit.MDMKit';
import { Want } from '@kit.AbilityKit';

let wantTemp: Want = {
  // 需根据实际情况进行替换
  bundleName: 'com.example.edmtest',
  abilityName: 'com.example.edmtest.EnterpriseAdminAbility'
};
try {
  let wifiIds: Array<wifiManager.WifiAccessInfo> = [{
    // 需根据实际情况进行替换
    ssid: "wifi_name",
    bssid: "68:77:24:77:A6:D8"
  }];
  wifiManager.addAllowedWifiList(wantTemp, wifiIds);
  console.info(`Succeeded in adding allowed Wi-Fi list.`);
} catch (err) {
  console.error(`Failed to add allowed Wi-Fi list. Code: ${err.code}, message: ${err.message}`);
}

```

