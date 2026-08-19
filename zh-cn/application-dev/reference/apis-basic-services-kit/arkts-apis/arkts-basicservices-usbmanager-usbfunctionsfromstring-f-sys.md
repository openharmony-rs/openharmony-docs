# usbFunctionsFromString（系统接口）

## 导入模块

```TypeScript
import { usbManager } from '@kit.BasicServicesKit';
import { serialManager } from '@kit.BasicServicesKit';
```

## usbFunctionsFromString

```TypeScript
function usbFunctionsFromString(funcs: string): number
```

在设备模式下，将字符串形式的USB功能列表转换为数字掩码。适用于需要将配置文件或用户输入的字符串形式USB功能列表转换为系统内部使用的数字掩码的场景，以便后续调用setDeviceFunctions等接口设置USB功能。

**起始版本：** 9

**废弃版本：** 12

**替代接口：** [getFunctionsFromString](arkts-basicservices-usbmanager-getfunctionsfromstring-f-sys.md)(funcs: string)

<!--Device-usbManager-function usbFunctionsFromString(funcs: string): number--><!--Device-usbManager-function usbFunctionsFromString(funcs: string): number-End-->

**系统能力：** SystemCapability.USB.USBManager

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| funcs | string | 是 | 字符串形式的功能列表，可用值包括：'none'、'acm'、'ecm'、'hdc'、'mtp'、'ptp'、'rndis'、'midi'、'audio_source'、'ncm' ，可通过英文逗号分隔多个功能。传入无效字符串时抛出异常。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 转换后的功能列表对应的数字掩码。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes:  <br>1.Mandatory parameters are left unspecified.  <br>2.Incorrect parameter types. |

