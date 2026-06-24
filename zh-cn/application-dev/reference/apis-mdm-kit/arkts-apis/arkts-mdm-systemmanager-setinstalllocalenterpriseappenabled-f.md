# setInstallLocalEnterpriseAppEnabled

## setInstallLocalEnterpriseAppEnabled

```TypeScript
function setInstallLocalEnterpriseAppEnabled(admin: Want, isEnable: boolean): void
```

�����Ƿ�֧�ֱ��ذ�װ��ҵӦ�á�����Ϊ֧�ְ�װ�󣬾߱����ذ�װ������PC/2in1��ҵ�豸�ɱ���˫��Ӧ�ð�װ������װǩ��֤��ַ�����Ϊenterprise_normal����ҵӦ�á�

**起始版本：** 20

**需要权限：** ohos.permission.ENTERPRISE_MANAGE_SYSTEM

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| admin | Want | 是 | ��ҵ�豸������չ�����Want�б��������ҵ�豸������չ������abilityName������Ӧ�õ�bundleName�� |
| isEnable | boolean | 是 | �Ƿ�֧�ֱ��ذ�װ��ҵӦ�á�true��ʾ֧�֣�false��ʾ��֧�֡� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [9200001](../../errorcode-universal.md#9200001-The) | The application is not an administrator application of the device. |
| [9200002](../../errorcode-universal.md#9200002-The) | The administrator application does not have permission to manage the device. |
| [201](../../errorcode-universal.md#201-Permission) | Permission verification failed. The application does not have the permission<br/>required to call the API. |
| [801](../../errorcode-universal.md#801-Capability) | Capability not supported. Failed to call the API due to limited device<br/>capabilities. |

**示例：**

```TypeScript

import { systemManager } from '@kit.MDMKit';
import { Want } from '@kit.AbilityKit';

let wantTemp: Want = {
  // 需根据实际情况进行替换
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};
// 需根据实际情况进行替换
let isEnable: boolean = true;
try {
  systemManager.setInstallLocalEnterpriseAppEnabled(wantTemp, isEnable);
  console.info('Succeeded in setting InstallLocalEnterpriseAppEnabled.');
} catch (err) {
  console.error(`Failed to set installLocalEnterpriseAppEnabled. Code is ${err.code}, message is ${err.message}`);
}

```

