# turnOffWifi

## turnOffWifi

```TypeScript
function turnOffWifi(admin: Want): void
```

�ر�Wi-Fi���ء�

��������£�ͨ�����ӿڹر�Wi-Fi���أ�����ʾ"ϵͳ���ܱ�����"��

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
  wifiManager.turnOffWifi(wantTemp);
  console.info(`Succeeded in turning off Wi-Fi.`);
} catch (err) {
  console.error(`Failed to turn off Wi-Fi. Code: ${err.code}, message: ${err.message}`);
}

```

