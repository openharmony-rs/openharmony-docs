# getAppClipboardPolicy

## getAppClipboardPolicy

```TypeScript
function getAppClipboardPolicy(admin: Want, tokenId?: number): string
```

��ȡ�豸��������ԡ�

**起始版本：** 12

**需要权限：** ohos.permission.ENTERPRISE_MANAGE_SECURITY

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| admin | Want | 是 | ��ҵ�豸������չ�����Want�б��������ҵ�豸������չ������abilityName������Ӧ�õ�bundleName�� |
| tokenId | number | 否 | Ŀ��Ӧ�õ����ݱ�ʶ����ͨ��<br/>[bundleManager.getApplicationInfo](../../apis-ability-kit/arkts-apis/arkts-ability-applicationinfo-i.md#ApplicationInfo)��ȡaccessTokenId�� |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | ����JSON�ַ�����ʽ���豸��������ԡ� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [9200001](../../errorcode-universal.md#9200001-The) | The application is not an administrator application of the device. |
| [9200002](../../errorcode-universal.md#9200002-The) | The administrator application does not have permission to manage the device. |
| [201](../../errorcode-universal.md#201-Permission) | Permission verification failed. The application does not have the permission<br/>required to call the API. |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br/>2. Incorrect parameter types; 3. Parameter verification failed. |

**示例：**

```TypeScript
import { securityManager } from '@kit.MDMKit';
import { Want } from '@kit.AbilityKit';

let wantTemp: Want = {
  // 需根据实际情况进行替换
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};
// 需根据实际情况进行替换
let tokenId: number = 586874394;
try {
  let result: string = securityManager.getAppClipboardPolicy(wantTemp, tokenId);
  console.info(`Succeeded in getting clipboard policy, result : ${result}`);
} catch(err) {
  console.error(`Failed to set clipboard policy. Code: ${err.code}, message: ${err.message}`);
}

```


## getAppClipboardPolicy

```TypeScript
function getAppClipboardPolicy(admin: Want, bundleName: string, accountId: number): string
```

��ȡָ���û���ָ��Ӧ�õ��豸��������ԡ�

**起始版本：** 18

**需要权限：** ohos.permission.ENTERPRISE_MANAGE_SECURITY

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| admin | Want | 是 | ��ҵ�豸������չ�����Want�б��������ҵ�豸������չ������abilityName������Ӧ�õ�bundleName�� |
| bundleName | string | 是 | �����ü�������Ե�Ӧ�ð����� |
| accountId | number | 是 | �û�ID��ָ�������û���ȡֵ��Χ�����ڵ���0��accountId����ͨ��@ohos.account.osAccount�е�<br/>[getOsAccountLocalId](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-osaccount-accountmanager-i.md#getOsAccountLocalId-2)�Ƚӿ�����ȡ��*@ohos.account.osAccount** to obtain the account ID. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | ����JSON�ַ�����ʽ���豸��������ԡ� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [9200001](../../errorcode-universal.md#9200001-The) | The application is not an administrator application of the device. |
| [9200002](../../errorcode-universal.md#9200002-The) | The administrator application does not have permission to manage the device. |
| [201](../../errorcode-universal.md#201-Permission) | Permission verification failed. The application does not have the permission<br/>required to call the API. |

**示例：**

```TypeScript
import { securityManager } from '@kit.MDMKit';
import { Want } from '@kit.AbilityKit';

let wantTemp: Want = {
  // 需根据实际情况进行替换
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};
// 需根据实际情况进行替换
let bundleName: string = 'com.example.myapplication';
let accountId: number = 100;
try {
  let result: string = securityManager.getAppClipboardPolicy(wantTemp, bundleName, accountId);
  console.info(`Succeeded in getting clipboard policy, result : ${result}`);
} catch(err) {
  console.error(`Failed to set clipboard policy. Code: ${err.code}, message: ${err.message}`);
}

```

