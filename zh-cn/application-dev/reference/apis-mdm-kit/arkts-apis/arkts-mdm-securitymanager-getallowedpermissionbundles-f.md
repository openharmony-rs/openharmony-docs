# getAllowedPermissionBundles

## getAllowedPermissionBundles

```TypeScript
function getAllowedPermissionBundles(admin: Want | null, permission: string, accountId: number): Array<common.ApplicationInstance>
```

获取权限使用例外名单的应用列表。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**需要权限：** ohos.permission.ENTERPRISE_MANAGE_SECURITY

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-securityManager-function getAllowedPermissionBundles(admin: Want | null, permission: string, accountId: number): Array<common.ApplicationInstance>--><!--Device-securityManager-function getAllowedPermissionBundles(admin: Want | null, permission: string, accountId: number): Array<common.ApplicationInstance>-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| admin | \_\_\_MD\_LINK\_USD\_0\_\_\_ \| null | 是 | 企业设备管理扩展组件。Want中必须包含企业设备管理扩展能力的abilityName和所在应用的bundleName。当admin为null时，表示获取所有企业设备管理应用下发的权限使用例外应用名单，返回合并后的结果。 |
| permission | string | 是 | 权限名称。 |
| accountId | number | 是 | 用户ID，指定具体用户，取值范围：大于等于0。accountId可以通过@ohos.account.osAccount中的[getOsAccountLocalId]\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_JSDOC\_\_\_ESCAPED\_UNDERSCORE\_\_\_LINK\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_等接口来获取。*@ohos.account.osAccount** to obtain the user ID. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;common.ApplicationInstance&gt; | 返回权限使用例外名单列表。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed.The application does not have the permission required to call the API. |
| [9200001](../errorcode-enterpriseDeviceManager.md#9200001-应用没有激活成设备管理器) | The application is not an administrator application of the device. |
| [9200002](../errorcode-enterpriseDeviceManager.md#9200002-设备管理器权限不够) | The administrator application does not have permission to manage the device. |
| [9200012](../errorcode-enterpriseDeviceManager.md#9200012-参数校验失败) | Parameter verification failed. |

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
let accountId: number = 100;
try {
  let result: Array<common.ApplicationInstance> = securityManager.getAllowedPermissionBundles(wantTemp, permission, accountId);
  console.info(`Succeeded in getting allowed permission bundles, result : ${JSON.stringify(result)}`);
} catch(err) {
  console.error(`Failed to get allowed permission bundles. Code: ${err.code}, message: ${err.message}`);
}
```

