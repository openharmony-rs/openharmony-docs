# BluetoothTransport

枚举，表示设备传输类型。

**起始版本：** 10

**系统能力：** SystemCapability.Communication.Bluetooth.Core

## TRANSPORT_BR_EDR

```TypeScript
TRANSPORT_BR_EDR = 0
```

传统蓝牙（Basic Rate/Enhanced Data Rate，BR/EDR）设备传输方式。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

## TRANSPORT_LE

```TypeScript
TRANSPORT_LE = 1
```

低功耗蓝牙（Bluetooth Low Energy，BLE）设备传输方式。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

## TRANSPORT_DUAL

```TypeScript
TRANSPORT_DUAL = 2
```

同时支持传统蓝牙（BR/EDR）和低功耗蓝牙（BLE）的双模设备传输方式。设备可以根据需要选择使用传统蓝牙（BR/EDR）或低功耗蓝牙（BLE）进行通信。

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

## TRANSPORT_UNKNOWN

```TypeScript
TRANSPORT_UNKNOWN = 3
```

未知的设备传输方式。

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.Bluetooth.Core
