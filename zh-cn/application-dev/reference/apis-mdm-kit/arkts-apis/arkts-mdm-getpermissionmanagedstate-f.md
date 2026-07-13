# getPermissionManagedState

## getPermissionManagedState

```TypeScript
function getPermissionManagedState(
    admin: Want,
    applicationInstance: ApplicationInstance,
    permission: string
  ): PermissionManagedState
```

获取指定应用的指定[user_grant权限](permissions:Permissions)的管理策略。

**起始版本：** 20

**需要权限：** ohos.permission.ENTERPRISE_MANAGE_USER_GRANT_PERMISSION

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| admin | Want | 是 | 企业设备管理扩展组件。Want中必须包含企业设备管理扩展能力的abilityName和所在应用的bundleName。 |
| applicationInstance | ApplicationInstance | 是 | 指定应用实例。 |
| permission | string | 是 | 需要获取管理策略的权限名称，仅支持user_grant权限。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| PermissionManagedState | 应用权限的管理策略。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [9200001](../errorcode-enterpriseDeviceManager.md#9200001-应用没有激活成设备管理器) | The application is not an administrator application of the device. |
| [9200002](../errorcode-enterpriseDeviceManager.md#9200002-设备管理器权限不够) | The administrator application does not have permission to manage the device. |
| [9200012](../errorcode-enterpriseDeviceManager.md#9200012-参数校验失败) | The parameter validation failed. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed.The application does not have the permission required to call the API. |

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

