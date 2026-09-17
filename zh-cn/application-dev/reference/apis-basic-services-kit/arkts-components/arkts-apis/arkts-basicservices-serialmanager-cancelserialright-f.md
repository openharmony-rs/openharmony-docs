# cancelSerialRight

## 导入模块

```TypeScript
import { serialManager } from '@kit.BasicServicesKit';
```

## cancelSerialRight

```TypeScript
function cancelSerialRight(portId: number): void
```

移除应用运行时访问串口设备的权限。此接口会调用close关闭已打开的串口。通常在需要主动释放权限、切换访问不同设备、或出于安全考虑时调用此接口。

**前置条件：**

- 需要先调用[getPortList](arkts-basicservices-serialmanager-getportlist-f.md)获取端口号  
- 需要先调用[requestSerialRight](arkts-basicservices-serialmanager-requestserialright-f.md)申请访问权限

**相关方法：**  
- [requestSerialRight](arkts-basicservices-serialmanager-requestserialright-f.md)：申请访问权限  
- [hasSerialRight](arkts-basicservices-serialmanager-hasserialright-f.md)：检查是否有访问权限

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
| [14400005](../errorcode-usb.md#14400005-数据库操作异常) |  |
| [31400001](../errorcode-usb.md#31400001-串口服务异常) |  |
| [31400002](../errorcode-usb.md#31400002-没有串口设备访问权限) |  |
| [31400003](../errorcode-usb.md#31400003-端口号不存在) |  |

**示例**

```TypeScript
> 说明：
> 
> 以下示例代码只是调用cancelSerialRight接口的必要流程，需要放入具体的方法中执行。实际调用时，设备开发者需要遵循设备相关协议进行调用。
```
