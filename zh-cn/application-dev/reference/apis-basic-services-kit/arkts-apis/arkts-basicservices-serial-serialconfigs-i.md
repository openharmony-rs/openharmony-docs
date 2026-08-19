# SerialConfigs

串口通信配置参数。

**起始版本：** 26.0.0

<!--Device-serial-interface SerialConfigs--><!--Device-serial-interface SerialConfigs-End-->

**系统能力：** SystemCapability.BusManager.Serial

## 导入模块

```TypeScript
import { serial } from '@kit.BasicServicesKit';
```

## baudRate

```TypeScript
baudRate?: int
```

波特率。值为正整数，非标准波特率的具体支持情况依赖于硬件。单位：bit/s。默认值：115200。

**类型：** int

**默认值：** 115200

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-SerialConfigs-baudRate?: int--><!--Device-SerialConfigs-baudRate?: int-End-->

**系统能力：** SystemCapability.BusManager.Serial

## dataBits

```TypeScript
dataBits?: DataBits
```

数据位。默认值：EIGHT（8数据位，标准通信）。FIVE/SIX/SEVEN用于老旧设备或特殊协议。

**类型：** DataBits

**默认值：** EIGHT

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-SerialConfigs-dataBits?: DataBits--><!--Device-SerialConfigs-dataBits?: DataBits-End-->

**系统能力：** SystemCapability.BusManager.Serial

## parity

```TypeScript
parity?: Parity
```

校验位。默认值：NONE（无校验）。EVEN/ODD用于数据准确性要求高的场景；MARK/SPACE用于特殊通信协议。

**类型：** Parity

**默认值：** NONE

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-SerialConfigs-parity?: Parity--><!--Device-SerialConfigs-parity?: Parity-End-->

**系统能力：** SystemCapability.BusManager.Serial

## rtscts

```TypeScript
rtscts?: boolean
```

是否启用RTS/CTS硬件自动流控。RTS/CTS硬件流控是一种通过硬件信号实现的自动数据流控制机制，RTS和CTS信号线协同工作以防止缓冲区溢出。 启用后，系统会自动控制RTS和CTS信号来管理数据流量。默认值：false。true表示启用，false表示未启用。

**类型：** boolean

**默认值：** false

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-SerialConfigs-rtscts?: boolean--><!--Device-SerialConfigs-rtscts?: boolean-End-->

**系统能力：** SystemCapability.BusManager.Serial

## stopBits

```TypeScript
stopBits?: StopBits
```

停止位。默认值：ONE。1个停止位用于标准通信场景；2个停止位用于低速通信或与老旧设备通信时增加信号稳定性。

**类型：** StopBits

**默认值：** ONE

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-SerialConfigs-stopBits?: StopBits--><!--Device-SerialConfigs-stopBits?: StopBits-End-->

**系统能力：** SystemCapability.BusManager.Serial

## xany

```TypeScript
xany?: boolean
```

是否启用XANY（Any Character Resume，任意字符恢复模式）控制流。XANY是软件流控协议中的一种扩展模式，需在xon或xoff启用时才能生效。 当启用XANY时，任何字符都可以作为恢复发送的信号，而不仅仅是XON字符；若未启用软件流控（xon/xoff），xany设置无效。默认值：false。true表示启用，false表示未启用。

**类型：** boolean

**默认值：** false

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-SerialConfigs-xany?: boolean--><!--Device-SerialConfigs-xany?: boolean-End-->

**系统能力：** SystemCapability.BusManager.Serial

## xoff

```TypeScript
xoff?: boolean
```

是否启用XOFF（Xmitter Off，传输停止控制字符）控制发送流。XOFF是软件流控协议中的一个控制字符（ASCII值为19），当接收端缓冲区即将溢出时发送XOFF字符通知发送端暂停发送数据。 默认值：false。true表示启用，false表示未启用。

**类型：** boolean

**默认值：** false

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-SerialConfigs-xoff?: boolean--><!--Device-SerialConfigs-xoff?: boolean-End-->

**系统能力：** SystemCapability.BusManager.Serial

## xon

```TypeScript
xon?: boolean
```

是否启用XON（Xmitter On，传输继续控制字符）控制发送流。XON是软件流控协议中的一个控制字符（ASCII值为17），当接收端缓冲区有空间时发送XON字符通知发送端恢复发送数据。 默认值：false。true表示启用，false表示未启用。

**类型：** boolean

**默认值：** false

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-SerialConfigs-xon?: boolean--><!--Device-SerialConfigs-xon?: boolean-End-->

**系统能力：** SystemCapability.BusManager.Serial

