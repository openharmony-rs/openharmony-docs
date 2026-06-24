# removeReceiveSmsPolicyNumbers

## removeReceiveSmsPolicyNumbers

```TypeScript
function removeReceiveSmsPolicyNumbers(admin: Want, policy: adminManager.Policy, numbers: Array<string>): void
```

�Ƴ����ն��ŵ��������������

**起始版本：** 26.0.0

**需要权限：** ohos.permission.ENTERPRISE_MANAGE_TELEPHONY

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| admin | Want | 是 | ��ҵ�豸������չ��� |
| policy | adminManager.Policy | 是 | ����������������ԡ� |
| numbers | Array&lt;string&gt; | 是 | ͨ�������б�����ǰ��֧��ȫ����ƥ�䡣 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [9200001](../../errorcode-universal.md#9200001-The) | The application is not an administrator application of the device. |
| [9200002](../../errorcode-universal.md#9200002-The) | The administrator application does not have permission to manage the device. |
| [9200012](../../errorcode-universal.md#9200012-The) | The parameter validation failed. |
| [201](../../errorcode-universal.md#201-Permission) | Permission verification failed.<br/>The application does not have the permission required to call the API. |
| [203](../../errorcode-universal.md#203-This) | This function is prohibited by enterprise management policies. |
| [801](../../errorcode-universal.md#801-Capability) | Capability not supported.<br/>Failed to call the API due to limited device capabilities. |

