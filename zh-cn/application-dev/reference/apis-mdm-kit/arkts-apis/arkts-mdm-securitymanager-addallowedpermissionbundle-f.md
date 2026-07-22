# addAllowedPermissionBundle

## 导入模块

```TypeScript
import { securityManager } from '@kit.MDMKit';
```

## addAllowedPermissionBundle

```TypeScript
function addAllowedPermissionBundle(admin: Want, permission: string, applicationInstance: common.ApplicationInstance): void
```

添加允许使用已禁用指定权限的应用到权限使用例外名单，权限使用例外名单中的应用可以不受[setDisallowedPermission](arkts-mdm-securitymanager-setdisallowedpermission-f.md#setdisallowedpermission)的策略限制。

**起始版本：** 26.0.0

**需要权限：** ohos.permission.ENTERPRISE_MANAGE_SECURITY

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-securityManager-function addAllowedPermissionBundle(admin: Want, permission: string, applicationInstance: common.ApplicationInstance): void--><!--Device-securityManager-function addAllowedPermissionBundle(admin: Want, permission: string, applicationInstance: common.ApplicationInstance): void-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| admin | [Want](../../apis-arkui/arkts-apis/arkts-arkui-want-t-sys.md) | 是 | 企业设备管理扩展组件。Want中必须包含企业设备管理扩展能力的abilityName和所在应用的bundleName。 |
| permission | string | 是 | 权限名称。 |
| applicationInstance | common.ApplicationInstance | 是 | 需添加到权限使用例外名单的应用实例信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed.The application does not have the permission required to call the API. |
| [9200001](../errorcode-enterpriseDeviceManager.md#9200001-应用没有激活成设备管理器) | The application is not an administrator application of the device. |
| [9200002](../errorcode-enterpriseDeviceManager.md#9200002-设备管理器权限不够) | The administrator application does not have permission to manage the device. |
| [9200012](../errorcode-enterpriseDeviceManager.md#9200012-参数校验失败) | Parameter verification failed. |
| [9201015](../errorcode-enterpriseDeviceManager.md#9201015-指定应用未安装) | The application is not installed. |
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
let disallow: boolean = true;
let accountId: number = 100;
// 该应用已经申请了ohos.permission.CAMERA权限
let appInstance: common.ApplicationInstance = {
  appIdentifier: '123456789',
  appIndex: 0,
  accountId: 100
};
try {
  // 禁用ohos.permission.CAMERA权限
  securityManager.setDisallowedPermission(wantTemp, permission, disallow, accountId);
  // 设置指定应用可以继续使用ohos.permission.CAMERA权限
  securityManager.addAllowedPermissionBundle(wantTemp, permission, appInstance);
  console.info(`Succeeded in adding allowed permission bundle.`);
} catch(err) {
  console.error(`Failed to add allowed permission bundle. Code: ${err.code}, message: ${err.message}`);
}

```

