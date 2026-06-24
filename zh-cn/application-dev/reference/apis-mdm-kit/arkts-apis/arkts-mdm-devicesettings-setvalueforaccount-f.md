# setValueForAccount

## setValueForAccount

```TypeScript
function setValueForAccount(admin: Want, item: SettingsItem, accountId: number, value: string): void
```

����ָ���û����豸���ò��ԡ��ýӿڿ�������ָ���û�������Ӧ���е�ĳ�����������������û�100���豸���Ƶȡ�

**起始版本：** 24

**需要权限：** ohos.permission.ENTERPRISE_MANAGE_SETTINGS

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| admin | Want | 是 | ��ҵ�豸������չ�����Want�б��������ҵ�豸������չ������abilityName������Ӧ�õ�bundleName�� |
| item | SettingsItem | 是 | �豸���ò������͡� |
| accountId | number | 是 | �û�ID��ȡֵ��Χ�����ڵ���0��<br/>accountId����ͨ��<br/>[getOsAccountLocalId](@ohos.account.osAccount:osAccount.AccountManager.getOsAccountLocalId(callback:<br/>AsyncCallback))<br/>�Ƚӿ�����ȡ<br/><br/>ȡֵ��ΧΪȫ��������<br/><br/>-�û�ID��������ڵ���0��<br/>�����Ե���<br/>[getOsAccountLocalId](@Ohos.account.osAccount:osAccount.AccountManager.getOsAccountLocalId(�ص���<br/>AsyncCallback��ȡ�û�ID�� |
| value | string | 是 | ��������ֵ��<br/>��itemΪ[SettingsItem.DEVICE_NAME]{@link deviceSettings.SettingsItem)ʱ��valueΪ�豸��<br/>�Ƶ��ַ����� �ַ������ȷ�Χ�����ڵ���1��С�ڵ���100��ֻ�������õ�ǰ�û����豸���ƣ����������û����豸���Ʒ���9200012�����롣<br/>��itemΪ<br/>[SettingsItem.FLOATING_NAVIGATION](arkts-mdm-devicesettings-settingsitem-e.md#SettingsItem)ʱ��valueΪ���������Ŀ���״̬��<br/>- '0'����ʾ��������������ͨ���ӿ�<br/>[enterKioskMode](../../apis-ability-kit/arkts-apis/arkts-ability-kioskmanager-enterkioskmode-f.md#enterKioskMode-1)����Kioskģʽ�£�����������ʾ�����ײ����ƿ�����������<br/>�������غ͵ײ����ƿ���ͬʱ����ʱ�����������Ż���ʾ���ײ����ƿ�ͨ���ӿ�<br/>[applicationManager.setKioskFeatures](|

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [9200001](../../errorcode-universal.md#9200001-The) | The application is not an administrator application of the device. |
| [9200002](../../errorcode-universal.md#9200002-The) | The administrator application does not have permission to manage the device. |
| [9200012](../../errorcode-universal.md#9200012-Parameter) | Parameter verification failed. |
| [201](../../errorcode-universal.md#201-Permission) | Permission verification failed.<br/>The application does not have the permission required to call the API. |
| [801](../../errorcode-universal.md#801-Capability) | Capability not supported.<br/>Failed to call the API due to limited device capabilities. |

**示例：**

```TypeScript
import { deviceSettings ) from '@kit.MDMKit';
import { Want } from '@kit.AbilityKit';

let wantTemp: Want = {
  // 需根据实际情况进行替换
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};

try {
  // 需根据实际情况进行替换
  let accountId = 100;
  let deviceName: string = "deviceName"
  deviceSettings.setValueForAccount(wantTemp, deviceSettings.SettingsItem.DEVICE_NAME, accountId, deviceName);
  console.info('Succeeded in setting device name.');
} catch (err) {
  console.error(`Failed to set device name. Code: ${err.code}, message: ${err.message}`);
}

```

