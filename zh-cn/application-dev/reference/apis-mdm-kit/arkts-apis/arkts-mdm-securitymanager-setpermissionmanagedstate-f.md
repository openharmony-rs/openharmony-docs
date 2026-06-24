# setPermissionManagedState

## setPermissionManagedState

```TypeScript
function setPermissionManagedState(
    admin: Want,
    applicationInstance: ApplicationInstance,
    permissions: Array<string>,
    managedState: PermissionManagedState
  ): void
```

����ָ��Ӧ�õ�[user_grantȨ��](permissions:Permissions)�Ĺ������ԡ�

**起始版本：** 20

**需要权限：** ohos.permission.ENTERPRISE_MANAGE_USER_GRANT_PERMISSION

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| admin | Want | 是 | ��ҵ�豸������չ�����Want�б��������ҵ�豸������չ������abilityName������Ӧ�õ�bundleName�� |
| applicationInstance | ApplicationInstance | 是 | ָ��Ӧ��ʵ���� |
| permissions | Array&lt;string&gt; | 是 | ��Ҫ������Ȩ�������б�����֧��[user_grantȨ��](permissions:Permissions)��Ȩ�������б���<br/>[Ӧ��Ȩ����](../../../../security/AccessToken/app-permission-group-list.md)Ϊ��λ���б���Ӧ����Ӧ����<br/>[module.json5](../../../../quick-start/module-configuration-file.md)��������ͬһȨ�����ڵ�����Ȩ�ޡ����磺Ӧ�������module.json5��������Ҫ<br/>ohos.permission.READ_CALENDAR��ohos.permission.WRITE_CALENDARȨ�ޣ������Ȩ�������б�����ͬʱ����ohos.permission.READ_CALENDAR��<br/>ohos.permission.WRITE_CALENDAR����Ȩ�ޡ� |
| managedState | PermissionManagedState | 是 | Ӧ��Ȩ�޵Ĺ������ԡ� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [9200001](../../errorcode-universal.md#9200001-The) | The application is not an administrator application of the device. |
| [9200002](../../errorcode-universal.md#9200002-The) | The administrator application does not have permission to manage the device. |
| [9200010](../../errorcode-universal.md#9200010-A) | A conflict policy has been configured. |
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
let permissionsTemp: Array<string> = ['ohos.permission.CAMERA', 'ohos.permission.LOCATION'];
try {
  securityManager.setPermissionManagedState(wantTemp, appInstanceTemp, permissionsTemp, securityManager.PermissionManagedState.GRANTED);
  console.info('Succeeded in setting permission managed state.');
} catch(err) {
  console.error(`Failed to set permission managed state.  Code: ${err.code}, message: ${err.message}`);
}

```

