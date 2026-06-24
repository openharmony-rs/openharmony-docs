# getValueForAccount

## getValueForAccount

```TypeScript
function getValueForAccount(admin: Want, item: SettingsItem, accountId: number): string
```

��ȡָ���û����豸���ò��ԡ��ýӿڿ��Ի�ȡָ���û�������Ӧ���е�ĳ�������������ȡ�û�100���豸���Ƶȡ�

**起始版本：** 24

**需要权限：** ohos.permission.ENTERPRISE_MANAGE_SETTINGS

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| admin | Want | 是 | ��ҵ�豸������չ�����Want�б��������ҵ�豸������չ������abilityName������Ӧ�õ�bundleName�� |
| item | SettingsItem | 是 | �豸���ò������͡� |
| accountId | number | 是 | �û�ID��ȡֵ��Χ�����ڵ���0��<br/>accountId����ͨ��<br/>[getOsAccountLocalId](@ohos.account.osAccount:osAccount.AccountManager.getOsAccountLocalId(callback:<br/>AsyncCallback))<br/>�Ƚӿ�����ȡ<br/><br/>ȡֵ��ΧΪȫ�������� |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | Policy type value.<br/><br/>When **item** is set to [SettingsItem.DEVICE_NAME](arkts-mdm-devicesettings-settingsitem-e.md#SettingsItem), this API returns the<br/>device name of the current user. If the device name of another user is queried, error code 9200012 is returned.<br/><br/>When **item** is set to [SettingsItem.FLOATING_NAVIGATION](arkts-mdm-devicesettings-settingsitem-e.md#SettingsItem),<br/>this API returns the three-key navigation switch state for the specified user.<br/><br/>When **item** is set to [SettingsItem.FLOATING_NAVIGATION](arkts-mdm-devicesettings-settingsitem-e.md#SettingsItem),<br/>this API can be called properly on phones and tablets but returns error code 801 on other devices. |

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
import { deviceSettings } from '@kit.MDMKit';
import { Want } from '@kit.AbilityKit';

let wantTemp: Want = {
  // 需根据实际情况进行替换
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};

try {
  // 需根据实际情况进行替换
  let accountId = 100;
  let result: string = deviceSettings.getValueForAccount(wantTemp, deviceSettings.SettingsItem.DEVICE_NAME, accountId);
  console.info(`Succeeded in getting device name, result : ${result}`);
} catch (err) {
  console.error(`Failed to get device name. Code: ${err.code}, message: ${err.message}`);
}

```

