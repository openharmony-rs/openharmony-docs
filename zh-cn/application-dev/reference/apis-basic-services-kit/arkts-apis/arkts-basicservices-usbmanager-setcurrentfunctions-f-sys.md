# setCurrentFunctions（系统接口）

## 导入模块

```TypeScript
import { usbManager } from '@kit.BasicServicesKit';
import { serialManager } from '@kit.BasicServicesKit';
```

## setCurrentFunctions

```TypeScript
function setCurrentFunctions(funcs: FunctionType): Promise<void>
```

在设备模式下，设置当前的USB功能列表。使用Promise异步回调。调用成功后，设备的USB功能将切换为指定的功能列表。适用于系统应用需要动态切换设备USB功能、配置设备工作模式的场景。

**起始版本：** 9

**废弃版本：** 12

**替代接口：** [setDeviceFunctions](arkts-basicservices-usbmanager-setdevicefunctions-f-sys.md)(funcs: FunctionType)

<!--Device-usbManager-function setCurrentFunctions(funcs: FunctionType): Promise<void>--><!--Device-usbManager-function setCurrentFunctions(funcs: FunctionType): Promise<void>-End-->

**系统能力：** SystemCapability.USB.USBManager

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| funcs | FunctionType | 是 | 功能列表对应的数字掩码，可通过位运算组合多个功能。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象。调用成功时无返回值，调用失败时抛出异常。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes:  <br>1.Mandatory parameters are left unspecified.  <br>2.Incorrect parameter types. |
| [14400002](../errorcode-usb.md#14400002-hdc功能被禁用) | Permission denied. The HDC is disabled by the system. |

