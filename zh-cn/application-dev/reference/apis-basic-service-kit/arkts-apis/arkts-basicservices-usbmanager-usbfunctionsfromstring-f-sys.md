# usbFunctionsFromString（系统接口）

## usbFunctionsFromString

```TypeScript
function usbFunctionsFromString(funcs: string): number
```

在设备模式下，将字符串形式的USB功能列表转化为数字掩码。

**起始版本：** 9

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为9。

**废弃版本：** 12

**替代接口：** [getFunctionsFromString](arkts-basicservices-usbmanager-getfunctionsfromstring-f-sys.md#getFunctionsFromString)(funcs: string)

<!--Device-usbManager-function usbFunctionsFromString(funcs: string): number--><!--Device-usbManager-function usbFunctionsFromString(funcs: string): number-End-->

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
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes:  &lt;br&gt;1.Mandatory parameters are left unspecified.  &lt;br&gt;2.Incorrect parameter types. |

