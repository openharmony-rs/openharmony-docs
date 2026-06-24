# getDisallowedPermissions

## getDisallowedPermissions

```TypeScript
function getDisallowedPermissions(admin: Want | null, accountId: number): Array<string>
```

��ȡָ���û��½��õ�Ȩ���б���

**起始版本：** 26.0.0

**需要权限：** ohos.permission.ENTERPRISE_MANAGE_SECURITY

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| admin | Want \| null | 是 | ��ҵ�豸������չ�����Want�б��������ҵ�豸������չ������abilityName������Ӧ�õ�bundleName��<br/>���豸�ж��MDMӦ��ʱ������admin<br/>��ѯ��Ӧadmin���õĲ��ԡ�����nullʱ��ѯ����ʵ����Ч�Ĳ��ԡ� |
| accountId | number | 是 | �û�ID��ָ�������û���ȡֵ��Χ�����ڵ���0��accountId����ͨ��@ohos.account.osAccount�е�<br/>[getOsAccountLocalId](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-osaccount-accountmanager-i.md#getOsAccountLocalId-2)�Ƚӿ�����ȡ�� |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;string&gt; | ���ؽ��õ�Ȩ���б��� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-Permission) | Permission verification failed.<br/>The application does not have the permission required to call the API. |
| [9200001](../../errorcode-universal.md#9200001-The) | The application is not an administrator application of the device. |
| [9200002](../../errorcode-universal.md#9200002-The) | The administrator application does not have permission to manage the device. |
| [9200012](../../errorcode-universal.md#9200012-Parameter) | Parameter verification failed. |

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
let accountId: number = 100;
try {
  let result: Array<string> = securityManager.getDisallowedPermissions(wantTemp, accountId);
  console.info(`Succeeded in getting disallowed permissions, result : ${JSON.stringify(result)}`);
} catch(err) {
  console.error(`Failed to get disallowed permissions. Code: ${err.code}, message: ${err.message}`);
}

```

