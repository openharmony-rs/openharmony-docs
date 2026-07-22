# usbFunctionsFromString（系统接口）

## 导入模块

```TypeScript
import { usb } from '@kit.BasicServicesKit';
```

## usbFunctionsFromString

```TypeScript
function usbFunctionsFromString(funcs: string): number
```

在设备模式下，将字符串形式的USB功能列表转化为数字掩码。

**起始版本：** 9

**废弃版本：** 9

**替代接口：** [usbFunctionsFromString](arkts-basicservices-usbmanager-usbfunctionsfromstring-f-sys.md#usbfunctionsfromstring)

<!--Device-usb-function usbFunctionsFromString(funcs: string): number--><!--Device-usb-function usbFunctionsFromString(funcs: string): number-End-->

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

**示例：**

```TypeScript
let funcs = "acm";
let ret = usb.usbFunctionsFromString(funcs);

```

