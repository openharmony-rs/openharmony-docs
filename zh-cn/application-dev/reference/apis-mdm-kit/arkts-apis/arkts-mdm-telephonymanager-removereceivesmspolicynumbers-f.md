# removeReceiveSmsPolicyNumbers

## 导入模块

```TypeScript
import { telephonyManager } from '@kit.MDMKit';
```

## removeReceiveSmsPolicyNumbers

```TypeScript
function removeReceiveSmsPolicyNumbers(admin: Want, policy: adminManager.Policy, numbers: Array<string>): void
```

移除接收短信的允许或禁用名单

**起始版本：** 26.0.0

**需要权限：** ohos.permission.ENTERPRISE_MANAGE_TELEPHONY

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-telephonyManager-function removeReceiveSmsPolicyNumbers(admin: Want, policy: adminManager.Policy, numbers: Array<string>): void--><!--Device-telephonyManager-function removeReceiveSmsPolicyNumbers(admin: Want, policy: adminManager.Policy, numbers: Array<string>): void-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| admin | [Want](../../apis-arkui/arkts-apis/arkts-arkui-want-t-sys.md) | 是 | 企业设备管理扩展组件 |
| policy | adminManager.Policy | 是 | 允许或禁用名单策略。 |
| numbers | [Array](../../apis-arkts/arkts-apis/arkts-arkts-collections-array-c.md)<string> | 是 | 通话号码列表，当前仅支持全号码匹配。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [9200001](../errorcode-enterpriseDeviceManager.md#9200001-应用没有激活成设备管理器) | The application is not an administrator application of the device. |
| [9200002](../errorcode-enterpriseDeviceManager.md#9200002-设备管理器权限不够) | The administrator application does not have permission to manage the device. |
| [9200012](../errorcode-enterpriseDeviceManager.md#9200012-参数校验失败) | The parameter validation failed. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed.The application does not have the permission required to call the API. |
| [203](../../errorcode-universal.md#203-企业管理策略禁止使用此系统功能) | This function is prohibited by enterprise management policies. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported.Failed to call the API due to limited device capabilities. |

