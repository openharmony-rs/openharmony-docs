# setCurrentFunctions（系统接口）

## setCurrentFunctions

```TypeScript
function setCurrentFunctions(funcs: FunctionType): Promise<void>
```

���豸ģʽ�£����õ�ǰ��USB�����б���ʹ��Promise�첽�ص���

**起始版本：** 9

**废弃版本：** 12

**替代接口：** setDeviceFunctions(funcs:

**系统能力：** SystemCapability.USB.USBManager

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| funcs | FunctionType | 是 | �����б���Ӧ���������롣 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise���� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes:<br/><br/>1.Mandatory parameters are left unspecified.<br/><br/>2.Incorrect parameter types. |
| [14400002](../../errorcode-universal.md#14400002-Permission) | Permission denied. The HDC is disabled by the system. |

