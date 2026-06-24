# removeFreezeExemptedApps

## removeFreezeExemptedApps

```TypeScript
function removeFreezeExemptedApps(admin: Want, applicationInstances: Array<common.ApplicationInstance>): void
```

Ϊָ���û�ɾ����̨������Ӧ��������ִ��ɾ������ʱ���������б��а���δ��װӦ�ã�ɾ���������ܳɹ�ִ�У��Ѱ�װ��Ӧ�ý���ɾ����δ��װ��Ӧ�ò�Ӱ��ɾ��������

**起始版本：** 22

**需要权限：** ohos.permission.ENTERPRISE_MANAGE_APPLICATION

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| admin | Want | 是 | ��ҵ�豸������չ�����Want�б��������ҵ�豸������չ������abilityName������Ӧ�õ�bundleName�� |
| applicationInstances | Array&lt;common.ApplicationInstance&gt; | 是 | ��̨������Ӧ���������顣 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [9200001](../../errorcode-universal.md#9200001-The) | The application is not an administrator application of the device. |
| [9200002](../../errorcode-universal.md#9200002-The) | The administrator application does not have permission to manage the device. |
| [9200012](../../errorcode-universal.md#9200012-Parameter) | Parameter verification failed. |
| [201](../../errorcode-universal.md#201-Permission) | Permission verification failed.<br/>The application does not have the permission required to call the API. |

**示例：**

```TypeScript
import { applicationManager, common } from '@kit.MDMKit';
import { Want } from '@kit.AbilityKit';

let wantTemp: Want = {
  // 需根据实际情况进行替换
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};

let applicationInstances: Array<common.ApplicationInstance> = [
  // 需根据实际情况进行替换
  {
    appIdentifier: '0123456789123456789',
    accountId: 100,
    appIndex: 0
  }
];

try {
  applicationManager.removeFreezeExemptedApps(wantTemp, applicationInstances);
  console.info('Succeeded in removing FreezeExempted applications.');
} catch(err) {
  console.error(`Failed to remove FreezeExempted applications. Code: ${err.code}, message: ${err.message}`);
}

```

