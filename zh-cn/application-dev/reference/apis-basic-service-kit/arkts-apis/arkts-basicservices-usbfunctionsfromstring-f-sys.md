# usbFunctionsFromString（系统接口）

## usbFunctionsFromString

```TypeScript
function usbFunctionsFromString(funcs: string): number
```

在设备模式下，将字符串形式的USB功能列表转化为数字掩码。

**起始版本：** 9

**废弃版本：** 12

**替代接口：** getFunctionsFromString(funcs:

**系统能力：** SystemCapability.USB.USBManager

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| funcs | string | 是 | 字符串形式的功能列表。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 转化后的功能列表对应的数字掩码。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:<br>1.Mandatory parameters are left unspecified.<br>2.Incorrect parameter types. |

