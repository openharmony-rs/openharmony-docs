# setAppClipboardPolicy

## setAppClipboardPolicy

```TypeScript
function setAppClipboardPolicy(admin: Want, tokenId: number, policy: ClipboardPolicy): void
```

设置设备剪贴板策略。

**起始版本：** 12

**需要权限：** ohos.permission.ENTERPRISE_MANAGE_SECURITY

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| admin | Want | 是 | 企业设备管理扩展组件。Want中必须包含企业设备管理扩展能力的abilityName和所在应用的bundleName。 |
| tokenId | number | 是 | 目标应用的身份标识。可通过[bundleManager.getApplicationInfo](../../apis-ability-kit/arkts-apis/arkts-ability-applicationinfo-i.md)获取accessTokenId。 |
| policy | ClipboardPolicy | 是 | 剪贴板策略。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [9200001](../errorcode-enterpriseDeviceManager.md#9200001-应用没有激活成设备管理器) | The application is not an administrator application of the device. |
| [9200002](../errorcode-enterpriseDeviceManager.md#9200002-设备管理器权限不够) | The administrator application does not have permission to manage the device. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed. The application does not have the permissionrequired to call the API. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types; 3. Parameter verification failed. |

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
  securityManager.setAppClipboardPolicy(wantTemp, tokenId, securityManager.ClipboardPolicy.IN_APP);
  console.info(`Succeeded in setting clipboard policy.`);
} catch(err) {
  console.error(`Failed to set clipboard policy. Code: ${err.code}, message: ${err.message}`);
}

```


## setAppClipboardPolicy

```TypeScript
function setAppClipboardPolicy(admin: Want, bundleName: string, accountId: number, policy: ClipboardPolicy): void
```

设置指定用户下指定应用的设备剪贴板策略。

**起始版本：** 18

**需要权限：** ohos.permission.ENTERPRISE_MANAGE_SECURITY

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| admin | Want | 是 | 企业设备管理扩展组件。Want中必须包含企业设备管理扩展能力的abilityName和所在应用的bundleName。 |
| bundleName | string | 是 | 被设置剪贴板策略的应用包名。 |
| accountId | number | 是 | 用户ID，指定具体用户，取值范围：大于等于0。accountId可以通过@ohos.account.osAccount中的[getOsAccountLocalId](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-accountmanager-i.md#getosaccountlocalid-2)等接口来获取。*@ohos.account.osAccount** to obtain the account ID. |
| policy | ClipboardPolicy | 是 | 剪贴板策略。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [9200001](../errorcode-enterpriseDeviceManager.md#9200001-应用没有激活成设备管理器) | The application is not an administrator application of the device. |
| [9200002](../errorcode-enterpriseDeviceManager.md#9200002-设备管理器权限不够) | The administrator application does not have permission to manage the device. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed. The application does not have the permissionrequired to call the API. |

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
  securityManager.setAppClipboardPolicy(wantTemp, bundleName, accountId, securityManager.ClipboardPolicy.IN_APP);
  console.info(`Succeeded in setting clipboard policy.`);
} catch(err) {
  console.error(`Failed to set clipboard policy. Code: ${err.code}, message: ${err.message}`);
}

```

