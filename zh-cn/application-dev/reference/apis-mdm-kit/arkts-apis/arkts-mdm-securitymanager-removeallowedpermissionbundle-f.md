# removeAllowedPermissionBundle

## 导入模块

```TypeScript
import { securityManager } from '@kit.MDMKit';
```

<a id="removeallowedpermissionbundle"></a>
## removeAllowedPermissionBundle

```TypeScript
function removeAllowedPermissionBundle(admin: Want, permission: string, applicationInstance: common.ApplicationInstance): void
```

从权限使用例外名单中移除指定应用，移除后该应用则不能继续使用对应的权限。

**起始版本：** 26.0.0

**需要权限：** ohos.permission.ENTERPRISE_MANAGE_SECURITY

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-securityManager-function removeAllowedPermissionBundle(admin: Want, permission: string, applicationInstance: common.ApplicationInstance): void--><!--Device-securityManager-function removeAllowedPermissionBundle(admin: Want, permission: string, applicationInstance: common.ApplicationInstance): void-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| admin | [Want](../../apis-arkui/arkts-apis/arkts-arkui-want-t-sys.md) | 是 | 企业设备管理扩展组件。Want中必须包含企业设备管理扩展能力的abilityName和所在应用的bundleName。 |
| permission | string | 是 | 权限名称。 |
| applicationInstance | common.ApplicationInstance | 是 | 需从权限使用例外名单移除的应用实例信息。the application need to be removed from the list of applications allowed to grant the permission. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed.The application does not have the permission required to call the API. |
| [9200001](../errorcode-enterpriseDeviceManager.md#9200001-应用没有激活成设备管理器) | The application is not an administrator application of the device. |
| [9200002](../errorcode-enterpriseDeviceManager.md#9200002-设备管理器权限不够) | The administrator application does not have permission to manage the device. |
| [9200012](../errorcode-enterpriseDeviceManager.md#9200012-参数校验失败) | Parameter verification failed. |
| [9201044](../errorcode-enterpriseDeviceManager.md#9201044-指定权限未被禁用) | This permission is not disallowed.Applications cannot be added to or removed from the trustlist. |

**示例：**

```TypeScript
import { securityManager, common } from '@kit.MDMKit';
import { Want } from '@kit.AbilityKit';

let wantTemp: Want = {
  // 需根据实际情况进行替换
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};
// 需根据实际情况进行替换
let permission: string = 'ohos.permission.CAMERA';
let appInstance: common.ApplicationInstance = {
  appIdentifier: '736498586',
  appIndex: 0,
  accountId: 100
};
try {
  securityManager.removeAllowedPermissionBundle(wantTemp, permission, appInstance);
  console.info(`Succeeded in removing allowed permission bundle.`);
} catch(err) {
  console.error(`Failed to remove allowed permission bundle. Code: ${err.code}, message: ${err.message}`);
}

```

