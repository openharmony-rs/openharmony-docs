# getPermissionManagedState

## getPermissionManagedState

```TypeScript
function getPermissionManagedState(
    admin: Want,
    applicationInstance: ApplicationInstance,
    permission: string
  ): PermissionManagedState
```

��ȡָ��Ӧ�õ�ָ��[user_grantȨ��](permissions:Permissions)�Ĺ������ԡ�

**起始版本：** 20

**需要权限：** ohos.permission.ENTERPRISE_MANAGE_USER_GRANT_PERMISSION

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| admin | Want | 是 | ��ҵ�豸������չ�����Want�б��������ҵ�豸������չ������abilityName������Ӧ�õ�bundleName�� |
| applicationInstance | ApplicationInstance | 是 | ָ��Ӧ��ʵ���� |
| permission | string | 是 | ��Ҫ��ȡ�������Ե�Ȩ�����ƣ���֧��user_grantȨ�ޡ� |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| PermissionManagedState | Ӧ��Ȩ�޵Ĺ������ԡ� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [9200001](../../errorcode-universal.md#9200001-The) | The application is not an administrator application of the device. |
| [9200002](../../errorcode-universal.md#9200002-The) | The administrator application does not have permission to manage the device. |
| [9200012](../../errorcode-universal.md#9200012-The) | The parameter validation failed. |
| [201](../../errorcode-universal.md#201-Permission) | Permission verification failed.<br/>The application does not have the permission required to call the API. |

**示例：**

```TypeScript
import { Want } from '@kit.AbilityKit';
import { securityManager } from '@kit.MDMKit';

let wantTemp: Want = {
  // 需根据实际情况进行替换
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};
let appInstanceTemp: securityManager.ApplicationInstance = {
  // 需根据实际情况进行替换
  appIdentifier: '736498586',
  appIndex: 0,
  accountId: 100
};
let permissionTemp: string = 'ohos.permission.ENTERPRISE_MANAGE_USER_GRANT_PERMISSION';
try {
  let result: securityManager.PermissionManagedState = securityManager.getPermissionManagedState(wantTemp, appInstanceTemp, permissionTemp);
  console.info(`Succeeded in getting permission managed state, result : ${result}`);
} catch(err) {
  console.error(`Failed to get permission managed state. Code: ${err.code}, message: ${err.message}`);
}

```

