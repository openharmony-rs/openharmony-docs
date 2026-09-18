# BluetoothAddressType

枚举，蓝牙子系统定义的地址类型。蓝牙设备的实际MAC地址属于用户的隐私信息，在发现设备的过程中，蓝牙子系统会给每个蓝牙外设分配一个虚拟MAC地址，并保存该虚拟MAC地址和外设实际MAC地址的映射关系。关于地址类型的详细介绍请参见蓝牙设备地址类型。

**起始版本：** 21

**系统能力：** SystemCapability.Communication.Bluetooth.Core

## VIRTUAL

```TypeScript
VIRTUAL = 1
```

虚拟MAC地址类型。

**起始版本：** 21

**系统能力：** SystemCapability.Communication.Bluetooth.Core

## REAL

```TypeScript
REAL = 2
```

实际MAC地址类型。

**起始版本：** 21

**系统能力：** SystemCapability.Communication.Bluetooth.Core
