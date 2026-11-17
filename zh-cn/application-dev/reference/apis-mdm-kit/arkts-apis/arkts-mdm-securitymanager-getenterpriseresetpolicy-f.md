# getEnterpriseResetPolicy

## 导入模块

```TypeScript
import { securityManager } from '@kit.MDMKit';
```

## getEnterpriseResetPolicy

```TypeScript
function getEnterpriseResetPolicy(): EnterpriseResetPolicy
```

获取企业复位策略。同步返回策略。

**起始版本：** 26.1.0

**需要权限：** ohos.permission.ENTERPRISE_MANAGE_SECURITY

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-securityManager-function getEnterpriseResetPolicy(): EnterpriseResetPolicy--><!--Device-securityManager-function getEnterpriseResetPolicy(): EnterpriseResetPolicy-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [EnterpriseResetPolicy](arkts-mdm-securitymanager-enterpriseresetpolicy-e.md) | 企业重置策略。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-api权限校验失败) | Permission verification failed. The application does not have the permission required to call the API. |
| [9200001](../errorcode-enterpriseDeviceManager.md#9200001-应用没有激活成设备管理器) | The application is not an administrator application of the device. |
| [9200002](../errorcode-enterpriseDeviceManager.md#9200002-设备管理器权限不够) | The administrator application does not have permission to manage the device. |
| [9200016](../errorcode-enterpriseDeviceManager.md#9200016-服务超时) | Service timeout. |
