# SerialConfigs

串口通信配置

**起始版本：** 26.0.0

<!--Device-serial-interface SerialConfigs--><!--Device-serial-interface SerialConfigs-End-->

**系统能力：** SystemCapability.BusManager.Serial

## 导入模块

```TypeScript
import { serial } from '@kit.BasicServicesKit';
```

## baudRate

```TypeScript
baudRate?: number
```

波特率取值限定为整数。取值约束:标准波特率。<br>单位:bps。<br>默认值:115200。

**类型：** number

**默认值：** 115200

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-SerialConfigs-baudRate?: int--><!--Device-SerialConfigs-baudRate?: int-End-->

**系统能力：** SystemCapability.BusManager.Serial

## dataBits

```TypeScript
dataBits?: DataBits
```

数据位<br>默认值:EIGHT。

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

校验位<br>默认值:NONE。

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

是否开启硬件自动流控<br>默认值:false。

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

停止位

<br>默认值:ONE。

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

是否启用XANY软件流控<br>默认值:false。

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

是否启用XOFF软件流控接收<br>默认值:false。

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

是否启用XON软件流控发送<br>默认值:false。

**类型：** boolean

**默认值：** false

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-SerialConfigs-xon?: boolean--><!--Device-SerialConfigs-xon?: boolean-End-->

**系统能力：** SystemCapability.BusManager.Serial

