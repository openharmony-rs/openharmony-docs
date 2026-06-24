# removeKeyEventPolicies

## removeKeyEventPolicies

```TypeScript
function removeKeyEventPolicies(admin: Want, keyCodes: Array<KeyCode>): void
```

ɾ�������¼��������ԡ�

**起始版本：** 23

**需要权限：** ohos.permission.ENTERPRISE_MANAGE_SYSTEM

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| admin | Want | 是 | ��ҵ�豸������չ�����Want�б��������ҵ�豸������չ������abilityName������Ӧ�õ�bundleName�� |
| keyCodes | Array&lt;KeyCode&gt; | 是 | �������롣֧��һ��ɾ�������������ԣ�ɾ����֧�ְ���ʱ����9200012�����롣 |

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
import { Want } from '@kit.AbilityKit';
import { systemManager } from '@kit.MDMKit';

let wantTemp: Want = {
  // 需根据实际情况进行替换
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};

let keyCodes: Array<systemManager.KeyCode> = [
  systemManager.KeyCode.POWER, systemManager.KeyCode.VOLUME_UP,
];

try {
  systemManager.removeKeyEventPolicies(wantTemp, keyCodes);
  console.info('Succeeded in removing key event policies.');
} catch (err) {
  console.error(`Failed to remove key event policies. Code is ${err.code}, message is ${err.message}`);
}

```

