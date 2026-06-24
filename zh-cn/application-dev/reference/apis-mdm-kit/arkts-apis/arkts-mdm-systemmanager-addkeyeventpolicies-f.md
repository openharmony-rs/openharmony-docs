# addKeyEventPolicies

## addKeyEventPolicies

```TypeScript
function addKeyEventPolicies(admin: Want, keyPolicies: Array<KeyEventPolicy>): void
```

���Ӱ����¼��������ԡ�ϵͳ���������¼�ʱ����ƥ���·��İ����¼����ԣ���ͨ��
[EnterpriseAdminExtensionAbility.onKeyEvent](arkts-mdm-enterpriseadminextensionability-c.md#onKeyEvent-1)
�ص�֪ͨMDMӦ�ã���Я��ƥ����Եİ����¼���Ϣ��

**起始版本：** 23

**需要权限：** ohos.permission.ENTERPRISE_MANAGE_SYSTEM

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| admin | Want | 是 | ��ҵ�豸������չ�����Want�б��������ҵ�豸������չ������abilityName������Ӧ�õ�bundleName�� |
| keyPolicies | Array&lt;KeyEventPolicy&gt; | 是 | �������ԡ�֧��������������Դ���������ӡ����������������������ˡ���ҳ������򿪣���������֧���������Ϊ��ϼ�����������֧����ϡ���ϼ���<br/>����Ӧ���<br/>[�����¼��ص�](arkts-mdm-enterpriseadminextensionability-c.md#onKeyEvent-1)�ӿڡ� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [9200001](../../errorcode-universal.md#9200001-The) | The application is not an administrator application of the device. |
| [9200002](../../errorcode-universal.md#9200002-The) | The administrator application does not have permission to manage the device. |
| [9200010](../../errorcode-universal.md#9200010-A) | A conflict policy has been configured. |
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

let keypolicy: Array<systemManager.KeyEventPolicy> = [
  {
    "keyCode": systemManager.KeyCode.POWER,
    "keyPolicy": systemManager.KeyPolicy.CUSTOM
  },
  {
    "keyCode": systemManager.KeyCode.VOLUME_UP,
    "keyPolicy": systemManager.KeyPolicy.CUSTOM
  }
];

try {
  systemManager.addKeyEventPolicies(wantTemp, keypolicy);
  console.info('Succeeded in adding key event policies.');
} catch (err) {
  console.error(`Failed to add key event policies. Code is ${err.code}, message is ${err.message}`);
}

```

