# getSendSmsPolicyNumbers

## getSendSmsPolicyNumbers

```TypeScript
function getSendSmsPolicyNumbers(admin: Want | null, policy: adminManager.Policy): Array<string>
```

查询发送短信的允许或禁用名单

**起始版本：** 26.0.0

**需要权限：** ohos.permission.ENTERPRISE_MANAGE_TELEPHONY

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| admin | Want \| null | 是 | 企业设备管理扩展组件 |
| policy | adminManager.Policy | 是 | 允许或禁用名单策略。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;string&gt; | phone numbers in the trust/block list. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [9200001](../errorcode-enterpriseDeviceManager.md#9200001-应用没有激活成设备管理器) | The application is not an administrator application of the device. |
| [9200002](../errorcode-enterpriseDeviceManager.md#9200002-设备管理器权限不够) | The administrator application does not have permission to manage the device. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed.The application does not have the permission required to call the API. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported.Failed to call the API due to limited device capabilities. |

