# BluetoothAddress

描述蓝牙设备地址信息的参数结构，包括地址与地址类型。

**起始版本：** 21

**系统能力：** SystemCapability.Communication.Bluetooth.Core

## 导入模块

```TypeScript
import { common } from '@kit.ConnectivityKit';
```

## address

```TypeScript
address: string
```

表示蓝牙设备的地址，例如："XX:XX:XX:XX:XX:XX"。

**类型：** string

**起始版本：** 21

**系统能力：** SystemCapability.Communication.Bluetooth.Core

## addressType

```TypeScript
addressType: BluetoothAddressType
```

表示地址类型为蓝牙设备的实际MAC地址或虚拟MAC地址。

**类型：** [BluetoothAddressType](arkts-connectivity-common-bluetoothaddresstype-e.md)

**起始版本：** 21

**系统能力：** SystemCapability.Communication.Bluetooth.Core

## rawAddressType

```TypeScript
rawAddressType?: BluetoothRawAddressType
```

表示地址类型为蓝牙协议定义的Public类型或Random类型。默认值请参见相关接口说明，未传入时使用系统默认地址类型。

**类型：** [BluetoothRawAddressType](arkts-connectivity-common-bluetoothrawaddresstype-e.md)

**起始版本：** 23

**系统能力：** SystemCapability.Communication.Bluetooth.Core
