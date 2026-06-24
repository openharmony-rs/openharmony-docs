# setAdminRunningMode（系统接口）

## setAdminRunningMode

```TypeScript
function setAdminRunningMode(admin: Want, mode: RunningMode): void
```

�����豸����Ӧ�õ�����ģʽ��

**起始版本：** 19

**需要权限：** ohos.permission.MANAGE_ENTERPRISE_DEVICE_ADMIN

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| admin | Want | 是 | ��ҵ�豸������չ�����Want�б��������ҵ�豸������չ������abilityName������Ӧ�õ�bundleName�� |
| mode | RunningMode | 是 | ����ģʽ��ȡֵΪDEFAULT��ʾĬ���û�����ģʽ����Ӧ�����״ο�������û������С�ȡֵΪMULTI_USER��ʾ���û�����ģʽ����Ӧ���ܹ��ڶ���û���ͬʱ���С� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [9200001](../../errorcode-universal.md#9200001-The) | The application is not an administrator application of the device. |
| [201](../../errorcode-universal.md#201-Permission) | Permission verification failed. The application does not have the permission<br/>required to call the API. |
| [202](../../errorcode-universal.md#202-Permission) | Permission verification failed. A non-system application calls a system API. |

**示例：**

```TypeScript
import { adminManager } from '@kit.MDMKit';
import { Want } from '@kit.AbilityKit';

let admin: Want = {
  // 需根据实际情况进行替换
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};
try {
  adminManager.setAdminRunningMode(admin, adminManager.RunningMode.MULTI_USER);
  console.info(`Succeeded in setting admin running mode.`);
} catch(err) {
  console.error(`Failed to set admin running mode. Code: ${err.code}, message: ${err.message}`);
}

```

