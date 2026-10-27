# removeUserExtendCredential

## 导入模块

```TypeScript
import { securityManager } from '@kit.MDMKit';
```

## removeUserExtendCredential

```TypeScript
function removeUserExtendCredential(info: RemoveCredentialInfo, accountId: number): void
```

移除扩展用户认证凭据

**起始版本：** 26.0.1

**需要权限：** ohos.permission.ENTERPRISE_MANAGE_SECURITY

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-securityManager-function removeUserExtendCredential(info: RemoveCredentialInfo, accountId: number): void--><!--Device-securityManager-function removeUserExtendCredential(info: RemoveCredentialInfo, accountId: number): void-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| info | [RemoveCredentialInfo](arkts-mdm-securitymanager-removecredentialinfo-i.md) | 是 | 移除用户凭据所需信息。 |
| accountId | number | 是 | 用户ID，取值范围：大于等于0。accountId可以通过getOsAccountLocalId等接口来获取。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-api权限校验失败) | Permission verification failed. The application does not have the permission required to call the API. |
| [801](../../errorcode-universal.md#801-api功能在部分设备不支持) | Capability not supported. Failed to call the API due to limited device capabilities. |
| [9200001](../errorcode-enterpriseDeviceManager.md#9200001-应用没有激活成设备管理器) | The application is not an administrator application of the device. |
| [9200002](../errorcode-enterpriseDeviceManager.md#9200002-设备管理器权限不够) | The administrator application does not have permission to manage the device. |
| [9200012](../errorcode-enterpriseDeviceManager.md#9200012-参数校验失败) | Parameter verification failed. |
| [9200016](../errorcode-enterpriseDeviceManager.md#9200016-服务超时) | Service timeout. |
| [9201052](../errorcode-enterpriseDeviceManager.md#9201052-会话超期) | USB key session timed out. |

**示例**

```TypeScript
import { securityManager } from '@kit.MDMKit';

let accountId: number = 100;
let credentialId: Uint8Array = new Uint8Array([1, 2, 3, 4]);
let info: securityManager.RemoveCredentialInfo = {
  credentialId: credentialId
};
try {
  securityManager.removeUserExtendCredential(info, accountId);
  console.info('Succeeded in removing credential.');
} catch(err) {
  console.error(`Failed to remove credential. Code: ${err.code}, message: ${err.message}`);
}
```
