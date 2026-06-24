# getStringFromFunctions（系统接口）

## getStringFromFunctions

```TypeScript
function getStringFromFunctions(funcs: FunctionType): string
```

���豸ģʽ�£�������������ʽ��USB�����б�ת��Ϊ�ַ�����

**起始版本：** 12

**需要权限：** ohos.permission.MANAGE_USB_CONFIG

**系统能力：** SystemCapability.USB.USBManager

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| funcs | FunctionType | 是 | �����б���Ӧ���������롣 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | ת������ַ�����ʽ�Ĺ����б��� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-Permission) | Permission verification failed. The application does not have the permission required to<br/>call the API.&lt;br&gt;**适用版本：** 18+ |
| [202](../../errorcode-universal.md#202-Permission) | Permission denied. Normal application do not have permission to use system api. |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes:<br/><br/>1.Mandatory parameters are left unspecified.<br/><br/>2.Incorrect parameter types. |
| [801](../../errorcode-universal.md#801-Capability) | Capability not supported.&lt;br&gt;**适用版本：** 18+ |

