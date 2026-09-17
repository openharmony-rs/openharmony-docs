# close

## 导入模块

```TypeScript
import { serialManager } from '@kit.BasicServicesKit';
```

## close

```TypeScript
function close(portId: number): void
```

关闭串口。需要先调用[requestSerialRight](arkts-basicservices-serialmanager-requestserialright-f.md)申请权限，再调用[open](arkts-basicservices-serialmanager-open-f.md)打开串口。通常在应用退出时、设备断开连接时、需要释放串口资源时调用此接口。关闭串口不会移除访问权限，如需移除权限请调用cancelSerialRight。

**配对调用：**  
- 与[open](arkts-basicservices-serialmanager-open-f.md)方法成对使用  
- 打开串口后，使用完毕必须调用本方法关闭串口释放资源

**前置条件：**  
- 需要先调用[getPortList](arkts-basicservices-serialmanager-getportlist-f.md)获取端口号  
- 需要先调用[requestSerialRight](arkts-basicservices-serialmanager-requestserialright-f.md)申请访问权限  
- 需要先调用[open](arkts-basicservices-serialmanager-open-f.md)打开串口

**起始版本：** 19

**系统能力：** SystemCapability.USB.USBManager.Serial

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| portId | number | 是 | 端口号，来自[getPortList](arkts-basicservices-serialmanager-getportlist-f.md)返回的[SerialPort](arkts-basicservices-serialmanager-serialport-i.md)对象，必须使用getPortList返回的有效端口号，传入无效值时抛出错误码31400003异常。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) |  |
| [31400001](../errorcode-usb.md#31400001-串口服务异常) |  |
| [31400003](../errorcode-usb.md#31400003-端口号不存在) |  |
| [31400005](../errorcode-usb.md#31400005-设备未打开) |  |

**示例**

```TypeScript
> 说明：
> 
> 以下示例代码只是调用close接口的必要流程，需要放入具体的方法中执行。实际调用时，设备开发者需要遵循设备相关协议进行调用。
```
