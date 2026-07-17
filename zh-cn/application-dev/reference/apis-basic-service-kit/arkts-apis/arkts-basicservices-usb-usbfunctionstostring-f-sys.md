# usbFunctionsToString（系统接口）

## 导入模块

```TypeScript
import { usb } from '@kit.BasicServicesKit';
```

## usbFunctionsToString

```TypeScript
function usbFunctionsToString(funcs: FunctionType): string
```

在设备模式下，将数字掩码形式的USB功能列表转化为字符串。

**起始版本：** 9

**废弃版本：** 9

**替代接口：** [usbFunctionsToString](arkts-basicservices-usbmanager-usbfunctionstostring-f-sys.md#usbfunctionstostring-1)

<!--Device-usb-function usbFunctionsToString(funcs: FunctionType): string--><!--Device-usb-function usbFunctionsToString(funcs: FunctionType): string-End-->

**系统能力：** SystemCapability.USB.USBManager

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| funcs | [FunctionType](arkts-basicservices-usb-functiontype-e-sys.md) | 是 | 功能列表对应数字掩码。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 转化后的字符串形式的功能列表。 |

**示例：**

```TypeScript
let funcs = usb.FunctionType.ACM | usb.FunctionType.ECM;
let ret = usb.usbFunctionsToString(funcs);

```

