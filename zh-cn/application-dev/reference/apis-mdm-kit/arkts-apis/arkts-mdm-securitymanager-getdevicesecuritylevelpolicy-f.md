# getDeviceSecurityLevelPolicy

## 导入模块

```TypeScript
import { securityManager } from '@kit.MDMKit';
```

## getDeviceSecurityLevelPolicy

```TypeScript
function getDeviceSecurityLevelPolicy(admin: Want): DeviceSecurityLevelPolicy
```

查询DSL切换策略

**起始版本：** 26.0.0

**需要权限：** ohos.permission.ENTERPRISE_MANAGE_SECURITY

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-securityManager-function getDeviceSecurityLevelPolicy(admin: Want): DeviceSecurityLevelPolicy--><!--Device-securityManager-function getDeviceSecurityLevelPolicy(admin: Want): DeviceSecurityLevelPolicy-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| admin | [Want](../../apis-arkui/arkts-apis/arkts-arkui-want-t-sys.md) | 是 | 企业设备管理扩展组件 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| DeviceSecurityLevelPolicy | 返回DSL切换策略 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [9200001](../errorcode-enterpriseDeviceManager.md#9200001-应用没有激活成设备管理器) | The application is not an administrator application of the device. |
| [9200002](../errorcode-enterpriseDeviceManager.md#9200002-设备管理器权限不够) | The administrator application does not have permission to manage the device. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed.The application does not have the permission required to call the API. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported.Failed to call the API due to limited device capabilities. |

