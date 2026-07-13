# removeOutgoingCallPolicyNumbers

## removeOutgoingCallPolicyNumbers

```TypeScript
function removeOutgoingCallPolicyNumbers(admin: Want, policy: adminManager.Policy, numbers: Array<string>): void
```

移除通话呼出的允许或禁用名单，若在该名单尚未设置时进行移除，则会移除失败。

以下情况下，通过本接口移除通话呼出的允许或禁用名单，会报策略冲突：

已经通过
[setDisallowedPolicy](arkts-mdm-setdisallowedpolicy-f.md#setdisallowedpolicy-1)
接口禁用了设备通话能力，再通过本接口移除通话呼出的禁用或允许名单，返回203错误码。通过
[setDisallowedPolicy](arkts-mdm-setdisallowedpolicy-f.md#setdisallowedpolicy-1)
接口解除禁用设备通话能力后，可解除冲突。

**起始版本：** 20

**需要权限：** ohos.permission.ENTERPRISE_MANAGE_TELEPHONY

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| admin | Want | 是 | 企业设备管理扩展组件。Want中必须包含企业设备管理扩展能力的abilityName和所在应用的bundleName。 |
| policy | adminManager.Policy | 是 | 允许或禁用名单策略。BLOCK_LIST为禁用名单，TRUST_LIST为允许名单。 |
| numbers | Array&lt;string&gt; | 是 | 待移除的通话号码数组。数组总长度不能超过1000。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [9200001](../errorcode-enterpriseDeviceManager.md#9200001-应用没有激活成设备管理器) | The application is not an administrator application of the device. |
| [9200002](../errorcode-enterpriseDeviceManager.md#9200002-设备管理器权限不够) | The administrator application does not have permission to manage the device. |
| [9200012](../errorcode-enterpriseDeviceManager.md#9200012-参数校验失败) | The parameter validation failed. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed.The application does not have the permission required to call the API. |
| [203](../../errorcode-universal.md#203-企业管理策略禁止使用此系统功能) | This function is prohibited by enterprise management policies. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. Failed to call the API due to limited devicecapabilities. |

**示例：**

```TypeScript
import { Want } from '@kit.AbilityKit';
import { telephonyManager } from '@kit.MDMKit';
import { adminManager } from '@kit.MDMKit';

let wantTemp: Want = {
  // 需根据实际情况进行替换
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};
try {
  let policy: adminManager.Policy = adminManager.Policy.BLOCK_LIST;
  let numbers: Array<string> = [
    // 需根据实际情况进行替换
    "13112345678"
  ];
  telephonyManager.removeOutgoingCallPolicyNumbers(wantTemp, policy, numbers);
  console.info('Succeeded in removing outgoing call policy.');
} catch (err) {
  console.error(`Failed to remove outgoing call policy. Code: ${err.code}, message: ${err.message}`);
}

```

