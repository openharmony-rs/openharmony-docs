# setInstallLocalEnterpriseAppEnabledForAccount

## setInstallLocalEnterpriseAppEnabledForAccount

```TypeScript
function setInstallLocalEnterpriseAppEnabledForAccount(admin: Want, isEnable: boolean, accountId: number): void
```

����ָ���û����Ƿ�֧�ֱ��ذ�װ��ҵӦ�á��ھ߱����ذ�װ������PC/2in1��ҵ�豸���·�֧�ֱ�����ҵӦ�ò��Ժ��û���������������ļ�������ֱ��˫����ҵӦ�ð�װ��������ֱ�Ӱ�װ��ҵӦ�á�

��֧��enterprise_normal��enterprise_mdmǩ�����͵���ҵӦ�á�

> **˵����**
>
> ������������������PC/2in1��ҵ�豸�ڵ�ǰ�û��¼�֧�ֱ��ذ�װ��ҵӦ�ã�
>

<!--RP7--><!--RP7End-->

**起始版本：** 24

**需要权限：** ohos.permission.ENTERPRISE_MANAGE_SYSTEM

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| admin | Want | 是 | ��ҵ�豸������չ�����Want�б��������ҵ�豸������չ������abilityName������Ӧ�õ�bundleName�� |
| isEnable | boolean | 是 | �Ƿ�֧�ֱ��ذ�װ��ҵӦ�á�true��ʾ֧�֣�false��ʾ��֧�֡� |
| accountId | number | 是 | �û�ID��ȡֵ��Χ�����ڵ���0��<br/>accountId����ͨ��<br/>[getOsAccountLocalId](@ohos.account.osAccount:osAccount.AccountManager.getOsAccountLocalId(callback:<br/>AsyncCallback))<br/>�Ƚӿ�����ȡ<br/><br/>ȡֵӦΪ��0�������� |

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

import { systemManager } from '@kit.MDMKit';
import { Want } from '@kit.AbilityKit';

let wantTemp: Want = {
  // 需根据实际情况进行替换
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};
// 需根据实际情况进行替换
let isEnable: boolean = true;
let accountId: number = 100;
try {
  systemManager.setInstallLocalEnterpriseAppEnabledForAccount(wantTemp, isEnable, accountId);
  console.info('Succeeded in setting InstallLocalEnterpriseAppEnabledForAccount.');
} catch (err) {
  console.error(`Failed to set installLocalEnterpriseAppEnabledForAccount. Code is ${err.code}, message is ${err.message}`);
}

```

