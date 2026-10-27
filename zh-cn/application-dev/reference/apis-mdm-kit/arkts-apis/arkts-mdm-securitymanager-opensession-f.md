# openSession

## 导入模块

```TypeScript
import { securityManager } from '@kit.MDMKit';
```

## openSession

```TypeScript
function openSession(accountId: number): Promise<Uint8Array>
```

开启指定用户的凭据变更会话

**起始版本：** 26.0.1

**需要权限：** ohos.permission.ENTERPRISE_MANAGE_SECURITY

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-securityManager-function openSession(accountId: number): Promise<Uint8Array>--><!--Device-securityManager-function openSession(accountId: number): Promise<Uint8Array>-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| accountId | number | 是 | 系统账号ID。<br>取值范围:[0, +∞) |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Uint8Array&gt; | Promise用于返回挑战值。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-api权限校验失败) | Permission verification failed. The application does not have the permission required to call the API. |
| [801](../../errorcode-universal.md#801-api功能在部分设备不支持) | Capability not supported. Failed to call the API due to limited device capabilities. |
| [9200001](../errorcode-enterpriseDeviceManager.md#9200001-应用没有激活成设备管理器) | The application is not an administrator application of the device. |
| [9200002](../errorcode-enterpriseDeviceManager.md#9200002-设备管理器权限不够) | The administrator application does not have permission to manage the device. |
| [9200012](../errorcode-enterpriseDeviceManager.md#9200012-参数校验失败) | Parameter verification failed. |
| [9200016](../errorcode-enterpriseDeviceManager.md#9200016-服务超时) | Service timeout. |

**示例**

```TypeScript
import { securityManager } from '@kit.MDMKit';
import { BusinessError } from '@kit.BasicServicesKit';

// 开发者需替换为实际的账户ID
let accountId: number = 100;
securityManager.openSession(accountId).then((challenge: Uint8Array) => {
  console.info(`Succeeded in opening session, challenge: ${JSON.stringify(challenge)}`);
}).catch((err: BusinessError) => {
  console.error(`Failed to open session. Code: ${err.code}, message: ${err.message}`);
});
```
