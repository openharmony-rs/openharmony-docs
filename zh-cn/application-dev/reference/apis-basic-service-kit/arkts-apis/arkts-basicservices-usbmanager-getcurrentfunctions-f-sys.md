# getCurrentFunctions（系统接口）

## 导入模块

```TypeScript
import { usbManager } from '@kit.BasicServicesKit';
```

## getCurrentFunctions

```TypeScript
function getCurrentFunctions(): FunctionType
```

在设备模式下，获取当前的USB功能列表的数字组合掩码。开发者模式关闭时，如果没有设备接入，接口可能返回`undefined`，注意需要对接口返回值做判空处理。

**起始版本：** 9

**废弃版本：** 12

**替代接口：** [getDeviceFunctions()](arkts-basicservices-usbmanager-getdevicefunctions-f-sys.md#getdevicefunctions-1)

<!--Device-usbManager-function getCurrentFunctions(): FunctionType--><!--Device-usbManager-function getCurrentFunctions(): FunctionType-End-->

**系统能力：** SystemCapability.USB.USBManager

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [FunctionType](arkts-basicservices-usb-functiontype-e-sys.md) | 当前的USB功能列表的数字组合掩码。 |

