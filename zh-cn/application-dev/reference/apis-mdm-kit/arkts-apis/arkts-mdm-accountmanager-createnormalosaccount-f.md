# createNormalOsAccount

## createNormalOsAccount

```TypeScript
function createNormalOsAccount(admin: Want, name: string): Promise<osAccount.OsAccountInfo>
```

������ͨϵͳ�˺�

**起始版本：** 26.0.0

**需要权限：** ohos.permission.ENTERPRISE_MANAGE_LOCAL_ACCOUNTS

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| admin | Want | 是 | ��ҵ�豸������չ����� |
| name | string | 是 | ϵͳ�˺����ơ� |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;osAccount.OsAccountInfo&gt; | Returns the information about the added OS account. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [9200001](../../errorcode-universal.md#9200001-The) | The application is not an administrator application of the device. |
| [9200002](../../errorcode-universal.md#9200002-The) | The administrator application does not have permission to manage the device. |
| [9200012](../../errorcode-universal.md#9200012-Parameter) | Parameter verification failed. |
| [9201003](../../errorcode-universal.md#9201003-Failed) | Failed to add an OS account. |
| [9201040](../../errorcode-universal.md#9201040-The) | The number of accounts reaches the upper limit. |
| [201](../../errorcode-universal.md#201-Permission) | Permission verification failed.<br/>The application does not have the permission required to call the API. |
| [204](../../errorcode-universal.md#204-Access) | Access denied due to user access control policy. Possible causes:<br/>1. The operation is restricted by the OS-account constraint.<br/>2. The required privilege for the operation has not been granted. |
| [801](../../errorcode-universal.md#801-Capability) | Capability not supported.<br/>Failed to call the API due to limited device capabilities. |

