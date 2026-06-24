# getInstallLocalEnterpriseAppEnabled

## getInstallLocalEnterpriseAppEnabled

```TypeScript
function getInstallLocalEnterpriseAppEnabled(admin: Want | null): boolean
```

��ѯ�Ƿ�֧�ֱ��ذ�װ��ҵӦ�á�

**起始版本：** 20

**需要权限：** ohos.permission.ENTERPRISE_MANAGE_SYSTEM

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| admin | Want \| null | 是 | ��ҵ�豸������չ�����Want�б��������ҵ�豸������չ������abilityName������Ӧ�õ�bundleName��<br/>API version 24֮ǰ�����ñ��ӿڲ�ѯϵͳ��<br/>ǰ�Ƿ�֧�ֱ��ذ�װ��ҵӦ�á����豸�ж��MDMӦ��ʱ������admin��ѯ��Ӧadmin���õĲ��ԡ���API version 24��ʼ��admin����֧�ִ���null������nullʱ��ѯ����ʵ����Ч�Ĳ���<br/>�� [since 20 - 23] |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | �Ƿ�֧�ֱ��ذ�װ��ҵӦ�ã�trueΪ֧�֣�falseΪ��֧�֡� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [9200001](../../errorcode-universal.md#9200001-The) | The application is not an administrator application of the device. |
| [9200002](../../errorcode-universal.md#9200002-The) | The administrator application does not have permission to manage the device. |
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
try {
  let isEnable: boolean = systemManager.getInstallLocalEnterpriseAppEnabled(wantTemp);
  console.info('Succeeded in getting installLocalEnterpriseAppEnabled.');
} catch (err) {
  console.error(`Failed to get installLocalEnterpriseAppEnabled. Code is ${err.code}, message is ${err.message}`);
}

```

