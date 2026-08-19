# getAttribute

## 导入模块

```TypeScript
import { serialManager } from '@kit.BasicServicesKit';
```

## getAttribute

```TypeScript
function getAttribute(portId: int): Readonly<SerialAttribute>
```

获取指定串口的配置参数。需先调用[open](arkts-basicservices-serialmanager-open-f.md)打开串口后才能获取配置。通常在设备初始化后、需要查看当前通信参数配置、调试串口通信问题时调用此接口。 **前置条件：** - 需要先调用[getPortList](arkts-basicservices-serialmanager-getportlist-f.md)获取端口号 - 需要先调用[requestSerialRight](arkts-basicservices-serialmanager-requestserialright-f.md)申请访问权限 - 需要先调用[open](arkts-basicservices-serialmanager-open-f.md)打开串口

**起始版本：** 23

<!--Device-serialManager-function getAttribute(portId: int): Readonly<SerialAttribute>--><!--Device-serialManager-function getAttribute(portId: int): Readonly<SerialAttribute>-End-->

**系统能力：** SystemCapability.USB.USBManager.Serial

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| portId | int | 是 | 端口号，来自[getPortList](arkts-basicservices-serialmanager-getportlist-f.md)返回的 [SerialPort](arkts-basicservices-serialmanager-serialport-i.md)对象，必须使用getPortList返回的有效端口号，传入无效值时抛出错误码31400003异常。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Readonly&lt;[SerialAttribute](arkts-basicservices-serialmanager-serialattribute-i.md)&gt; | 返回串口的配置参数对象，包含波特率、数据位、校验位、停止位等配置信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) |  |
| [31400005](../errorcode-usb.md#31400005-设备未打开) |  |
| [31400003](../errorcode-usb.md#31400003-端口号不存在) |  |
| [31400001](../errorcode-usb.md#31400001-串口服务异常) |  |

