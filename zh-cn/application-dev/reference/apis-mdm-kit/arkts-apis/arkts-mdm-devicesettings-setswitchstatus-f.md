# setSwitchStatus

## setSwitchStatus

```TypeScript
function setSwitchStatus(admin: Want, key: SwitchKey, status: SwitchStatus): void
```

���ÿ��ص�״̬��֧������������������Wi-Fi��״̬Ϊ������رգ�������Ϻ��û������ֶ����ء�֧������������״̬Ϊǿ�ƿ�����������Ϻ��û��������ֶ����ء����Ѿ�ͨ��
[setDisallowedPolicy](arkts-mdm-restrictions-setdisallowedpolicy-f.md#setDisallowedPolicy-1)
�ӿڽ�����ĳ�����أ���ͨ�����ӿ�����������ص�״̬���׳�������203����ͨ��
[setDisallowedPolicy](arkts-mdm-restrictions-setdisallowedpolicy-f.md#setDisallowedPolicy-1)
�ӿڽ���ÿ��ؽ��ò��ԡ����豸�ж��MDMӦ��ʱ����MDMӦ�����ÿ���״̬�����ڳ�ͻ��������õĲ�����Ч������(�û����ֶ��������ر�)���ر�(�û����ֶ��������ر�)��ǿ�ƿ���(�û������ֶ��ر�)����״̬���������л���Ҳ�����ڳ�ͻ��

**起始版本：** 26.0.0

**需要权限：** ohos.permission.ENTERPRISE_MANAGE_SETTINGS or ohos.permission.PERSONAL_MANAGE_RESTRICTIONS

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| admin | Want | 是 | ��ҵ�豸������չ�����Want�б��������ҵ�豸������չ������abilityName������Ӧ�õ�bundleName�� |
| key | SwitchKey | 是 | ���ص����ƣ�Ӧ������Ȩ�� ohos.permission.PERSONAL_MANAGE_RESTRICTIONS ��ͨ���ӿ�<br/>[startAdminProvision](arkts-mdm-adminmanager-startadminprovision-f.md#startAdminProvision-1)����Ϊ�Դ��豸����Ӧ�ã�����ʹ�ô˽ӿ���<br/>�����¿��أ�������������Wi-Fi�� |
| status | SwitchStatus | 是 | ���ص�״̬��Ӧ������Ȩ�� ohos.permission.PERSONAL_MANAGE_RESTRICTIONS ��ͨ���ӿ�<br/>[startAdminProvision](arkts-mdm-adminmanager-startadminprovision-f.md#startAdminProvision-1)����Ϊ�Դ��豸����Ӧ�ã�����ʹ�ô˽ӿ���<br/>������״̬��ON��OFF������ΪFORCE_ON״̬ʱ�ᱨ������9200002�� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [9200001](../../errorcode-universal.md#9200001-The) | The application is not an administrator application of the device. |
| [9200002](../../errorcode-universal.md#9200002-The) | The administrator application does not have permission to manage the device. |
| [9200012](../../errorcode-universal.md#9200012-Parameter) | Parameter verification failed. |
| [9201042](../../errorcode-universal.md#9201042-Failed) | Failed to toggle the switch state. |
| [201](../../errorcode-universal.md#201-Permission) | Permission verification failed.<br/>The application does not have the permission required to call the API. |
| [203](../../errorcode-universal.md#203-This) | This function is prohibited by enterprise management policies. |
| [801](../../errorcode-universal.md#801-Capability) | Capability not supported.<br/>Failed to call the API due to limited device capabilities. |

**示例：**

```TypeScript
import { deviceSettings } from '@kit.MDMKit';
import { Want } from '@kit.AbilityKit';

let wantTemp: Want = {
  // 需根据实际情况进行替换
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};

try {
  // 需根据实际情况进行替换
  let key: deviceSettings.SwitchKey = deviceSettings.SwitchKey.BLUETOOTH;
  let status: deviceSettings.SwitchStatus  = deviceSettings.SwitchStatus.ON;
  deviceSettings.setSwitchStatus(wantTemp, key, status);
  console.info(`Succeeded in setting switch status.`);
} catch (err) {
  console.error(`Failed to set switch status. Code: ${err.code}, message: ${err.message}`);
}

```

