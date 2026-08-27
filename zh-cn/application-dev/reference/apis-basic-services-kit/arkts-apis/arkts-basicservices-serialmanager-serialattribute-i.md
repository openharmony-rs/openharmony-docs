# SerialAttribute

串口的配置参数。

**起始版本：** 19

**系统能力：** SystemCapability.USB.USBManager.Serial

## 导入模块

```TypeScript
import { serialManager } from '@kit.BasicServicesKit';
```

## baudRate

```TypeScript
baudRate: BaudRates
```

串口波特率，表示数据传输速率，单位：比特/秒

**类型：** [BaudRates](arkts-basicservices-serialmanager-baudrates-e.md)

**起始版本：** 19

**系统能力：** SystemCapability.USB.USBManager.Serial

## dataBits

```TypeScript
dataBits?: DataBits
```

串口数据位，表示报文中的有效数据位数，默认值为8，单位：比特

**类型：** DataBits

**默认值：** DATABIT_8

**起始版本：** 19

**系统能力：** SystemCapability.USB.USBManager.Serial

## parity

```TypeScript
parity?: Parity
```

串口奇偶校验，用于检测数据传输错误，默认值为PARITY_NONE（无奇偶校验）。

**类型：** Parity

**默认值：** PARITY_NONE

**起始版本：** 19

**系统能力：** SystemCapability.USB.USBManager.Serial

## stopBits

```TypeScript
stopBits?: StopBits
```

串口停止位，表示报文结束标志，默认值为1，单位：比特

**类型：** StopBits

**默认值：** STOPBIT_1

**起始版本：** 19

**系统能力：** SystemCapability.USB.USBManager.Serial
