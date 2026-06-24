# usbFunctionsFromString（系统接口）

## usbFunctionsFromString

```TypeScript
function usbFunctionsFromString(funcs: string): number
```

���豸ģʽ�£����ַ�����ʽ��USB�����б�ת��Ϊ�������롣

**起始版本：** 9

**废弃版本：** 12

**替代接口：** getFunctionsFromString(funcs:

**系统能力：** SystemCapability.USB.USBManager

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| funcs | string | 是 | �ַ�����ʽ�Ĺ����б��� |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | ת����Ĺ����б���Ӧ���������롣 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes:<br/><br/>1.Mandatory parameters are left unspecified.<br/><br/>2.Incorrect parameter types. |

