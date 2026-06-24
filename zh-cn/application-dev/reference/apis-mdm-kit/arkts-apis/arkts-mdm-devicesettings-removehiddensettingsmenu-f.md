# removeHiddenSettingsMenu

## removeHiddenSettingsMenu

```TypeScript
function removeHiddenSettingsMenu(admin: Want, menusToHidden: Array<SettingsMenu>): void
```

��������ӵ�ǰ�û��µ������������б����Ƴ��������������б��е��������ڵ�ǰ�û������ò˵��лᱻ���أ����غ󲻿��������õ������������������ͨ��ĳ�ַ�ʽ������������������Ҳ�޷��򿪡����Ƴ���ʣ��������������б�Ϊ�գ����������ȫ
����ʾ�����ýӿں󼴿���Ч��������������Ӧ�á�

**起始版本：** 24

**需要权限：** ohos.permission.ENTERPRISE_MANAGE_SETTINGS

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| admin | Want | 是 | ��ҵ�豸������չ�����Want�б��������ҵ�豸������չ������abilityName������Ӧ�õ�bundleName�� |
| menusToHidden | Array&lt;SettingsMenu&gt; | 是 | ���ص��������б�<br/><br/>��󳤶�Ϊ43�Ҳ���Ϊ�ա� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [9200001](../../errorcode-universal.md#9200001-The) | The application is not an administrator application of the device. |
| [9200002](../../errorcode-universal.md#9200002-The) | The administrator application does not have permission to manage the device. |
| [9200012](../../errorcode-universal.md#9200012-Parameter) | Parameter verification failed. |
| [9200016](../../errorcode-universal.md#9200016-Service) | Service timeout. |
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

let menusToHidden: Array<deviceSettings.SettingsMenu> = [
  // 需根据实际情况进行替换或增加
  deviceSettings.SettingsMenu.ACCOUNT_ID,
  deviceSettings.SettingsMenu.WIFI,
]

try {
  deviceSettings.removeHiddenSettingsMenu(wantTemp, menusToHidden);
  console.info('Succeeded in removing hidden settings menu.');
} catch (err) {
  console.error(`Failed to remove hidden settings menu. Code: ${err.code}, message: ${err.message}`);
}

```

