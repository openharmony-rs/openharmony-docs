# usbFunctionsToString（系统接口）

## 导入模块

```TypeScript
import { usbManager } from '@kit.BasicServicesKit';
import { serialManager } from '@kit.BasicServicesKit';
```

## usbFunctionsToString

```TypeScript
function usbFunctionsToString(funcs: FunctionType): string
```

在设备模式下，将数字掩码形式的USB功能列表转换为字符串。适用于需要将当前USB功能状态以字符串形式显示或保存的场景，如在日志中记录当前功能配置、在UI界面展示当前功能等。

**起始版本：** 9

**废弃版本：** 12

**替代接口：** [getStringFromFunctions](arkts-basicservices-usbmanager-getstringfromfunctions-f-sys.md)(funcs: FunctionType)

<!--Device-usbManager-function usbFunctionsToString(funcs: FunctionType): string--><!--Device-usbManager-function usbFunctionsToString(funcs: FunctionType): string-End-->

**系统能力：** SystemCapability.USB.USBManager

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| funcs | FunctionType | 是 | 功能列表对应的数字掩码，可通过位运算组合多个功能。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 转换后的字符串形式的功能列表。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes:  <br>1.Mandatory parameters are left unspecified.  <br>2.Incorrect parameter types. |

