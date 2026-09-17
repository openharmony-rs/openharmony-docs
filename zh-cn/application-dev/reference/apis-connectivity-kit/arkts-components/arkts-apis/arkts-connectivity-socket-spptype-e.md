# SppType

枚举，蓝牙套接字链路类型。

不同类型的蓝牙设备需要选取不同的链路类型。针对低功耗蓝牙（BLE）设备，必须使用L2CAP链路类型。针对传统蓝牙（BR/EDR）设备，建议优先采用RFCOMM链路进行连接。其优势在于可通过UUID服务动态协商信道（即设备通过查询服务UUID自动确定通信频道的过程），同时具备更高的安全性和可靠性。

**起始版本：** 10

**系统能力：** SystemCapability.Communication.Bluetooth.Core

## SPP_RFCOMM

```TypeScript
SPP_RFCOMM = 0
```

基于传统蓝牙（BR/EDR）的RFCOMM链路。

**起始版本：** 10

**系统能力：** SystemCapability.Communication.Bluetooth.Core

## SPP_L2CAP

```TypeScript
SPP_L2CAP = 1
```

基于传统蓝牙（BR/EDR）的L2CAP链路。

**起始版本：** 20

**系统能力：** SystemCapability.Communication.Bluetooth.Core

## SPP_L2CAP_BLE

```TypeScript
SPP_L2CAP_BLE = 2
```

基于低功耗蓝牙（BLE）的L2CAP链路。

**起始版本：** 20

**系统能力：** SystemCapability.Communication.Bluetooth.Core
