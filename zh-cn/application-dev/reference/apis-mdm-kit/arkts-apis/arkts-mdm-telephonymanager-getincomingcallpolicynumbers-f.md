# getIncomingCallPolicyNumbers

## 导入模块

```TypeScript
import { telephonyManager } from '@kit.MDMKit';
```

<a id="getincomingcallpolicynumbers"></a>
## getIncomingCallPolicyNumbers

```TypeScript
function getIncomingCallPolicyNumbers(admin: Want, policy: adminManager.Policy): Array<string>
```

获取通话呼入的允许或禁用名单。

**起始版本：** 20

**需要权限：** ohos.permission.ENTERPRISE_MANAGE_TELEPHONY

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-telephonyManager-function getIncomingCallPolicyNumbers(admin: Want, policy: adminManager.Policy): Array<string>--><!--Device-telephonyManager-function getIncomingCallPolicyNumbers(admin: Want, policy: adminManager.Policy): Array<string>-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| admin | [Want](../../apis-arkui/arkts-apis/arkts-arkui-want-t-sys.md) | 是 | 企业设备管理扩展组件。Want中必须包含企业设备管理扩展能力的abilityName和所在应用的bundleName。 |
| policy | adminManager.Policy | 是 | 允许或禁用名单策略。BLOCK_LIST为禁用名单，TRUST_LIST为允许名单。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;string&gt; | 通话呼入禁用或允许名单的号码数组。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [9200001](../errorcode-enterpriseDeviceManager.md#9200001-应用没有激活成设备管理器) | The application is not an administrator application of the device. |
| [9200002](../errorcode-enterpriseDeviceManager.md#9200002-设备管理器权限不够) | The administrator application does not have permission to manage the device. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed. The application does not have the permission required to call the API. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. Failed to call the API due to limited device capabilities. |

