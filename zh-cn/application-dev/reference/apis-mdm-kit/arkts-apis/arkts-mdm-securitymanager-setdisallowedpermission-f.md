# setDisallowedPermission

## 导入模块

```TypeScript
import { securityManager } from '@kit.MDMKit';
```

## setDisallowedPermission

```TypeScript
function setDisallowedPermission(admin: Want, permission: string, disallow: boolean, accountId: number): void
```

禁用指定用户下的指定权限，禁用后指定用户下的所有应用申请和使用指定权限时默认拒绝。

**起始版本：** 26.0.0

**需要权限：** ohos.permission.ENTERPRISE_MANAGE_SECURITY

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-securityManager-function setDisallowedPermission(admin: Want, permission: string, disallow: boolean, accountId: number): void--><!--Device-securityManager-function setDisallowedPermission(admin: Want, permission: string, disallow: boolean, accountId: number): void-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| admin | [Want](../../apis-arkui/arkts-apis/arkts-arkui-want-t-sys.md) | 是 | 企业设备管理扩展组件。Want中必须包含企业设备管理扩展能力的abilityName和所在应用的bundleName。 |
| permission | string | 是 | 权限名称。 |
| disallow | boolean | 是 | 是否禁用。true表示禁用，false表示取消禁用。 |
| accountId | number | 是 | 用户ID，指定具体用户，取值范围：大于等于0。accountId可以通过@ohos.account.osAccount中的[getOsAccountLocalId](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-osaccount-accountmanager-i.md#getosaccountlocalid)等接口来获取。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed.The application does not have the permission required to call the API. |
| [9200001](../errorcode-enterpriseDeviceManager.md#9200001-应用没有激活成设备管理器) | The application is not an administrator application of the device. |
| [9200002](../errorcode-enterpriseDeviceManager.md#9200002-设备管理器权限不够) | The administrator application does not have permission to manage the device. |
| [9200012](../errorcode-enterpriseDeviceManager.md#9200012-参数校验失败) | Parameter verification failed. |
| [9201045](../errorcode-enterpriseDeviceManager.md#9201045-指定权限不可被禁用) | This permission cannot be disallowed. |

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

