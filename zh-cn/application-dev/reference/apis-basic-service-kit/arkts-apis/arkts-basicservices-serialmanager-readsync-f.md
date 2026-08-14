# readSync

## readSync

```TypeScript
function readSync(portId: int, buffer: Uint8Array, timeout?: int): int
```

从串口设备同步读取数据。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-serialManager-function readSync(portId: int, buffer: Uint8Array, timeout?: int): int--><!--Device-serialManager-function readSync(portId: int, buffer: Uint8Array, timeout?: int): int-End-->

**系统能力：** SystemCapability.USB.USBManager.Serial

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| portId | int | 是 | 目标设备的端口号，来自[getPortList](arkts-basicservices-serialmanager-getportlist-f.md#getPortList)获取的串口参数SerialPort。 |
| buffer | Uint8Array | 是 | 读取数据的缓冲区，最大长度为8192比特。 |
| timeout | int | 否 | 超时时间（单位：毫秒）。API在目标端口缓冲区无数据时，等待指定时间后返回。默认值0表示不等待直接返回。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| int | 返回读取数据长度。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| [31400007](../../apis-basic-services-kit/errorcode-usb.md#31400007-io异常) | I/O exception. Possible causes:  &lt;br&gt;1. The transfer was canceled.  &lt;br&gt;2. The device offered more data than allowed. |
| [31400006](../../apis-basic-services-kit/errorcode-usb.md#31400006-传输超时) | Data transfer timed out. |
| [31400005](../../apis-basic-services-kit/errorcode-usb.md#31400005-设备未打开) | The serial port device is not opened. Call the open API first. |
| [31400003](../../apis-basic-services-kit/errorcode-usb.md#31400003-端口号不存在) | PortId does not exist. |
| [31400001](../../apis-basic-services-kit/errorcode-usb.md#31400001-串口服务异常) | Serial port management exception. |

