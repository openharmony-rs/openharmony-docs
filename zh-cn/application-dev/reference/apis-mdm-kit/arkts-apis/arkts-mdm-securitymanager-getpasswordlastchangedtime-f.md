# getPasswordLastChangedTime

## 导入模块

```TypeScript
import { securityManager } from '@kit.MDMKit';
```

## getPasswordLastChangedTime

```TypeScript
function getPasswordLastChangedTime(accountId: number): number
```

根据账号ID获取最近一次修改密码时间。同步返回时间。企业可以通过该接口查询最近一次修改密码时间，用于密码策略审计和合规性检查。

**起始版本：** 26.1.0

**需要权限：** ohos.permission.ENTERPRISE_MANAGE_SECURITY

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-securityManager-function getPasswordLastChangedTime(accountId: number): number--><!--Device-securityManager-function getPasswordLastChangedTime(accountId: number): number-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| accountId | number | 是 | 用户ID，必须大于等于0。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 最近一次修改密码时间戳，单位为毫秒。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-api权限校验失败) | Permission verification failed. The application does not have the permission required to call the API. |
| [9200001](../errorcode-enterpriseDeviceManager.md#9200001-应用没有激活成设备管理器) | The application is not an administrator application of the device. |
| [9200002](../errorcode-enterpriseDeviceManager.md#9200002-设备管理器权限不够) | The administrator application does not have permission to manage the device. |
| [9200012](../errorcode-enterpriseDeviceManager.md#9200012-参数校验失败) | Parameter verification failed. |
| [9200016](../errorcode-enterpriseDeviceManager.md#9200016-服务超时) | Service timeout. |
