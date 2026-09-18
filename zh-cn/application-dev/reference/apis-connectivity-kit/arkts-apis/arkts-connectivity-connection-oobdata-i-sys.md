# OobData（系统接口）

用于OOB配对的数据对象。

**起始版本：** 23

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { connection } from '@kit.ConnectivityKit';
```

## confirmationHash

```TypeScript
confirmationHash: Uint8Array
```

确认哈希值，长度为16个Byte。

**类型：** Uint8Array

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**系统接口：** 此接口为系统接口。

## deviceId

```TypeScript
deviceId: BluetoothAddress
```

蓝牙设备的地址信息。

在使用OobData时，[BluetoothAddress](arkts-connectivity-common-bluetoothaddress-i.md)中的address、addressType和rawAddressType均为必选参数，且addressType必须设置为REAL。

**类型：** [BluetoothAddress](arkts-connectivity-connection-bluetoothaddress-t.md)

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**系统接口：** 此接口为系统接口。

## deviceName

```TypeScript
deviceName?: string
```

蓝牙设备的名称。若不设置该值，则默认值为空字符串。

**类型：** string

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**系统接口：** 此接口为系统接口。

## deviceRole

```TypeScript
deviceRole?: DeviceRole
```

蓝牙设备在连接过程中的角色。若不设置该值，则默认值为DEVICE_ROLE_PERIPHERAL_ONLY。

**类型：** [DeviceRole](arkts-connectivity-connection-devicerole-e-sys.md)

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**系统接口：** 此接口为系统接口。

## randomizerHash

```TypeScript
randomizerHash?: Uint8Array
```

随机哈希值，长度为16个Byte。若不设置该值，则默认值为全0。

**类型：** Uint8Array

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**系统接口：** 此接口为系统接口。
