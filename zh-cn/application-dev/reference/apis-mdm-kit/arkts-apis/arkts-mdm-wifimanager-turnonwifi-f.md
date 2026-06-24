# turnOnWifi

## turnOnWifi

```TypeScript
function turnOnWifi(admin: Want, isForce: boolean): void
```

��Wi-Fi���ء�

��������£�ͨ�����ӿڴ�Wi-Fi���أ����ʧ�ܲ���ʾ"ϵͳ���ܱ�����"��

?�Ѿ�ͨ��
[setDisallowedPolicy](arkts-mdm-restrictions-setdisallowedpolicy-f.md#setDisallowedPolicy-1)
�ӿڽ�����Wi-Fi����ͨ��
[setDisallowedPolicy](arkts-mdm-restrictions-setdisallowedpolicy-f.md#setDisallowedPolicy-1)
�ӿ�����Wi-Fi�����"ϵͳ���ܱ�����"������

**起始版本：** 20

**需要权限：** ohos.permission.ENTERPRISE_MANAGE_WIFI

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| admin | Want | 是 | ��ҵ�豸������չ�����Want�б��������ҵ�豸������չ������abilityName������Ӧ�õ�bundleName�� |
| isForce | boolean | 是 | �Ƿ�ǿ�ƴ�Wi-Fi���ܡ�<br/>true��ʾǿ�ƿ���Wi-Fi��ǿ�ƿ�����֧���û����豸���ֶ��ر�Wi-Fi���أ��������<br/>[turnOffWifi](arkts-mdm-wifimanager-turnoffwifi-f.md#turnOffWifi-1)�ӿڹرա�false��ʾ��ǿ�ƿ���Wi-Fi����ʱ�û��������豸���ֶ������ر�Wi-Fi���ء� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [9200001](../../errorcode-universal.md#9200001-The) | The application is not an administrator application of the device. |
| [9200002](../../errorcode-universal.md#9200002-The) | The administrator application does not have permission to manage the device. |
| [201](../../errorcode-universal.md#201-Permission) | Permission verification failed. The application does not have the permission<br/>required to call the API. |
| [203](../../errorcode-universal.md#203-This) | This function is prohibited by enterprise management policies. |

**示例：**

```TypeScript
import { Want } from '@kit.AbilityKit';
import { wifiManager } from '@kit.MDMKit';

let wantTemp: Want = {
  // 需根据实际情况进行替换
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};

try {
  wifiManager.turnOnWifi(wantTemp, true);
  console.info(`Succeeded in turning on Wi-Fi.`);
} catch (err) {
  console.error(`Failed to turn on Wi-Fi. Code: ${err.code}, message: ${err.message}`);
}

```

