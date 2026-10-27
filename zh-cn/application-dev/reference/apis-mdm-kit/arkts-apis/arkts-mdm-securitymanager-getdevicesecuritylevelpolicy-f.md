# getDeviceSecurityLevelPolicy

## 导入模块

```TypeScript
import { securityManager } from '@kit.MDMKit';
```

## getDeviceSecurityLevelPolicy

```TypeScript
function getDeviceSecurityLevelPolicy(): DeviceSecurityLevelPolicy
```

查询DSL切换策略

**起始版本：** 26.0.1

**需要权限：** ohos.permission.ENTERPRISE_MANAGE_SECURITY

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-securityManager-function getDeviceSecurityLevelPolicy(): DeviceSecurityLevelPolicy--><!--Device-securityManager-function getDeviceSecurityLevelPolicy(): DeviceSecurityLevelPolicy-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [DeviceSecurityLevelPolicy](arkts-mdm-securitymanager-devicesecuritylevelpolicy-e.md) | 返回DSL切换策略 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-api权限校验失败) | Permission verification failed. The application does not have the permission required to call the API. |
| [9200001](../errorcode-enterpriseDeviceManager.md#9200001-应用没有激活成设备管理器) | The application is not an administrator application of the device. |
| [9200002](../errorcode-enterpriseDeviceManager.md#9200002-设备管理器权限不够) | The administrator application does not have permission to manage the device. |
| [9200016](../errorcode-enterpriseDeviceManager.md#9200016-服务超时) | Service timeout. |

**示例**

```TypeScript
import { securityManager } from '@kit.MDMKit';

try {
  let policy = securityManager.getDeviceSecurityLevelPolicy();
  console.info('getDeviceSecurityLevelPolicy policy: ' + policy);
} catch (err) {
  console.error('getDeviceSecurityLevelPolicy fail: ' + JSON.stringify(err));
}
```
