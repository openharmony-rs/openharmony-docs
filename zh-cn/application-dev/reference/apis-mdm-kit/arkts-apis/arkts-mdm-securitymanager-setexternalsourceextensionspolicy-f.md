# setExternalSourceExtensionsPolicy

## setExternalSourceExtensionsPolicy

```TypeScript
function setExternalSourceExtensionsPolicy(admin: Want, policy: common.ManagedPolicy): void
```

�����ⲿ��Դ��չ����Ĺܿز��ԡ�

- DEFAULT��

Ĭ�ϣ���ʾ�޹ܿز��ԣ��û�����ͨ��������-��˽�밲ȫ-�߼����еġ������ⲿ��Դ����չ���򡱿����������Ƿ�������չ�������С�
- DISALLOW��

���á����ô˲��Ժ󣬽�ֹ�����ⲿ��Դ����չ���������е���չ����ɼ������У���չ����رպ��޷��������С��û��޷�����������-��˽�Ͱ�ȫ-�߼����еġ������ⲿ��Դ����չ���򡱿��ء�
- FORCE_OPEN��

ǿ�ƿ��������ô˲��Ժ����������ⲿ��Դ����չ�����û��޷��رա�����-��˽�Ͱ�ȫ-�߼����еġ������ⲿ��Դ����չ���򡱿��ء�

**起始版本：** 22

**需要权限：** ohos.permission.ENTERPRISE_MANAGE_SECURITY

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| admin | Want | 是 | ��ҵ�豸������չ�����Want�б��������ҵ�豸������չ������abilityName������Ӧ�õ�bundleName�� |
| policy | common.ManagedPolicy | 是 | �ܿز��ԡ� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [9200001](../../errorcode-universal.md#9200001-The) | The application is not an administrator application of the device. |
| [9200002](../../errorcode-universal.md#9200002-The) | The administrator application does not have permission to manage the device. |
| [9200010](../../errorcode-universal.md#9200010-A) | A conflict policy has been configured. |
| [9200012](../../errorcode-universal.md#9200012-Parameter) | Parameter verification failed. |
| [201](../../errorcode-universal.md#201-Permission) | Permission verification failed.<br/>The application does not have the permission required to call the API. |

**示例：**

```TypeScript
import { common, securityManager } from '@kit.MDMKit';
import { Want } from '@kit.AbilityKit';

let wantTemp: Want = {
  // 需根据实际情况进行替换
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};
try {
  securityManager.setExternalSourceExtensionsPolicy(wantTemp, common.ManagedPolicy.FORCE_OPEN);
  console.info(`Succeeded in setting managed policy.`);
} catch(err) {
  console.error(`Failed to set managed policy. Code: ${err.code}, message: ${err.message}`);
}

```

