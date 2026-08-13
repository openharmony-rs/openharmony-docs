# usbFunctionsToString（系统接口）

## usbFunctionsToString

```TypeScript
function usbFunctionsToString(funcs: FunctionType): string
```

在设备模式下，将数字掩码形式的USB功能列表转化为字符串。

**起始版本：** 9

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为9。

**废弃版本：** 12

**替代接口：** [getStringFromFunctions](arkts-basicservices-usbmanager-getstringfromfunctions-f-sys.md#getStringFromFunctions)(funcs: FunctionType)

<!--Device-usbManager-function usbFunctionsToString(funcs: FunctionType): string--><!--Device-usbManager-function usbFunctionsToString(funcs: FunctionType): string-End-->

**系统能力：** SystemCapability.USB.USBManager

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| funcs | FunctionType | 是 | 功能列表对应的数字掩码。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 转化后的字符串形式的功能列表。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes:  &lt;br&gt;1.Mandatory parameters are left unspecified.  &lt;br&gt;2.Incorrect parameter types. |

