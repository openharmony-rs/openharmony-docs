# setDisallowedPermission

## setDisallowedPermission

```TypeScript
function setDisallowedPermission(admin: Want, permission: string, disallow: boolean, accountId: number): void
```

����ָ���û��µ�ָ��Ȩ�ޣ����ú�ָ���û��µ�����Ӧ�������ʹ��ָ��Ȩ��ʱĬ�Ͼܾ���

**起始版本：** 26.0.0

**需要权限：** ohos.permission.ENTERPRISE_MANAGE_SECURITY

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| admin | Want | 是 | ��ҵ�豸������չ�����Want�б��������ҵ�豸������չ������abilityName������Ӧ�õ�bundleName�� |
| permission | string | 是 | Ȩ�����ơ� |
| disallow | boolean | 是 | �Ƿ���á�true��ʾ���ã�false��ʾȡ�����á� |
| accountId | number | 是 | �û�ID��ָ�������û���ȡֵ��Χ�����ڵ���0��accountId����ͨ��@ohos.account.osAccount�е�<br/>[getOsAccountLocalId](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-osaccount-accountmanager-i.md#getOsAccountLocalId-2)�Ƚӿ�����ȡ�� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-Permission) | Permission verification failed.<br/>The application does not have the permission required to call the API. |
| [9200001](../../errorcode-universal.md#9200001-The) | The application is not an administrator application of the device. |
| [9200002](../../errorcode-universal.md#9200002-The) | The administrator application does not have permission to manage the device. |
| [9200012](../../errorcode-universal.md#9200012-Parameter) | Parameter verification failed. |
| [9201045](../../errorcode-universal.md#9201045-This) | This permission cannot be disallowed. |

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
let permission: string = 'ohos.permission.CAMERA';
let disallow: boolean = true;
let accountId: number = 100;
try {
  securityManager.setDisallowedPermission(wantTemp, permission, disallow, accountId);
  console.info(`Succeeded in setting disallowed permission.`);
} catch(err) {
  console.error(`Failed to set disallowed permission. Code: ${err.code}, message: ${err.message}`);
}

```

