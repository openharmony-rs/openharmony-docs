# removeAllNotifications

## 导入模块

```TypeScript
import { applicationManager } from '@kit.MDMKit';
```

## removeAllNotifications

```TypeScript
function removeAllNotifications(accountId: number): void
```

删除指定用户的所有通知。

**起始版本：** 26.1.0

**需要权限：** ohos.permission.ENTERPRISE_MANAGE_NOTIFICATION

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-applicationManager-function removeAllNotifications(accountId: number): void--><!--Device-applicationManager-function removeAllNotifications(accountId: number): void-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| accountId | number | 是 | 用户帐号ID。<br>取值应≥0。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-api权限校验失败) | Permission verification failed. The application does not have the permission required to call the API. |
| [9200001](../errorcode-enterpriseDeviceManager.md#9200001-应用没有激活成设备管理器) | The application is not an administrator application of the device. |
| [9200002](../errorcode-enterpriseDeviceManager.md#9200002-设备管理器权限不够) | The administrator application does not have permission to manage the device. |
| [9200012](../errorcode-enterpriseDeviceManager.md#9200012-参数校验失败) | Parameter verification failed. |
| [9200016](../errorcode-enterpriseDeviceManager.md#9200016-服务超时) | Service timeout. |
