# setActivationLockDisabled

## setActivationLockDisabled

```TypeScript
function setActivationLockDisabled(admin: Want, isDisabled: boolean, credential?: string): Promise<void>
```

����/�����豸���������豸�����������ú󣬽��޷�ʹ�ò����豸���ܡ��ù���ֻ�������ض��豸<!--RP5--><!--RP5End-->��

**起始版本：** 24

**需要权限：** ohos.permission.ENTERPRISE_MANAGE_SYSTEM

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| admin | Want | 是 | ��ҵ�豸������չ�����Want�б��������ҵ�豸������չ������abilityName������Ӧ�õ�bundleName�� |
| isDisabled | boolean | 是 | �Ƿ���ü�������true��ʾ���ã�false��ʾ���á� |
| credential | string | 否 | ����ƾ�ݡ������ý���ʱ�ò���������д��Чƾ������������ʱΪ�ա� |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | �޷��ؽ����Promise���󡣵����ý���/����ʧ��ʱ�����׳�������� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [9200001](../../errorcode-universal.md#9200001-The) | The application is not an administrator application of the device. |
| [9200002](../../errorcode-universal.md#9200002-The) | The administrator application does not have permission to manage the device. |
| [9200012](../../errorcode-universal.md#9200012-Parameter) | Parameter verification failed. |
| [9200016](../../errorcode-universal.md#9200016-Service) | Service timeout. |
| [9201011](../../errorcode-universal.md#9201011-The) | The credential of the activation lock is invalid. |
| [9201012](../../errorcode-universal.md#9201012-Failed) | Failed to enable or disable the activation lock. |
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
// 需根据实际情况进行替换
let credential: string = "XXX";
let isDisabled: boolean = true;
systemManager.setActivationLockDisabled(wantTemp, isDisabled, credential).then(() => {
  console.info('Succeeded in setting activation lock status.');
}).catch((err: BusinessError) => {
  console.error(`Failed to set activation lock status. Code: ${err.code}, message: ${err.message}`);
});

```

