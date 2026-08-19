# getSerialPortList

## 导入模块

```TypeScript
import { serial } from '@kit.BasicServicesKit';
```

## getSerialPortList

```TypeScript
function getSerialPortList(): Promise<SerialPort[]>
```

查询串口设备列表，返回[SerialPort](arkts-basicservices-serial-serialport-i.md)对象数组。使用Promise异步回调。用于需要识别可用串口设备的场景，如工业设备连接、物联网设备管理、嵌入式系统调试等场景。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-serial-function getSerialPortList(): Promise<SerialPort[]>--><!--Device-serial-function getSerialPortList(): Promise<SerialPort[]>-End-->

**系统能力：** SystemCapability.BusManager.Serial

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;SerialPort[]&gt; | Promise对象，返回串口设备列表。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [35700001](../errorcode-busmanager-serial.md#35700001-服务异常) | Service error. |
| [203](../../errorcode-universal.md#203-企业管理策略禁止使用此系统功能) | This function is prohibited by enterprise management policies. |

