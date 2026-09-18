# ScanResult

扫描到符合过滤条件的广播报文后，上报的扫描数据。

**起始版本：** 10

**系统能力：** SystemCapability.Communication.Bluetooth.Core

## 导入模块

```TypeScript
import { ble } from '@kit.ConnectivityKit';
```

## address

```TypeScript
address?: BluetoothAddress
```

扫描到的蓝牙设备地址信息，包括地址与地址类型。若不设置此参数，则内容为undefined。

**类型：** [BluetoothAddress](arkts-connectivity-ble-bluetoothaddress-t.md)

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

## advertiseFlags

```TypeScript
advertiseFlags?: number
```

扫描到的设备广播标记位，从原始数据data字段中解析而来，在蓝牙协议中广播数据类型为0x01。若广播报文中携带标记位，则该字段有值，否则内容为undefined。

**类型：** number

**起始版本：** 22

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

## advertisingDataMap

```TypeScript
advertisingDataMap?: Map<number, Uint8Array>
```

扫描到的设备广播数据集，从原始数据data字段中解析而来。

Map的key表示广播数据类型，value表示对应数据类型的具体内容，如advertisingDataMap字段中key为0x0A的对应value含义为txPowerLevel值。若广播报文中携带任意广播数据内容，则该字段有值，否则内容为undefined。

**类型：** Map&lt;number, Uint8Array&gt;

**起始版本：** 22

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

## connectable

```TypeScript
connectable: boolean
```

扫描到的设备是否可连接。true表示可连接，false表示不可连接。

**类型：** boolean

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

## data

```TypeScript
data: ArrayBuffer
```

扫描到的设备发送的原始未解析的广播报文内容。

**类型：** ArrayBuffer

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

## deviceId

```TypeScript
deviceId: string
```

扫描到的蓝牙设备地址。例如："XX:XX:XX:XX:XX:XX"。

基于信息安全考虑，若应用开启扫描时没有在[ScanFilter](arkts-connectivity-ble-scanfilter-i.md)中配置[实际MAC地址](arkts-connectivity-common-bluetoothaddresstype-e.md)，则此处获取的设备地址为[虚拟MAC地址](arkts-connectivity-common-bluetoothaddresstype-e.md)。

若和该设备地址配对成功后，该地址不会变更。若该设备重启蓝牙开关，重新获取到的虚拟地址会立即变更。若取消配对，蓝牙子系统会根据该地址的实际使用情况，决策后续变更时机；若其他应用正在使用该地址，则不会立刻变更。若要持久化保存该地址，可使用[access.addPersistentDeviceId](arkts-connectivity-access-addpersistentdeviceid-f.md)方法。

**类型：** string

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

## deviceName

```TypeScript
deviceName: string
```

扫描到的设备名称，从原始数据data字段中解析而来，在蓝牙协议中广播数据类型为0x09。

**类型：** string

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

## manufacturerDataMap

```TypeScript
manufacturerDataMap?: Map<number, Uint8Array>
```

扫描到的设备制造商数据集合，从原始数据data字段中解析而来，在蓝牙协议中广播数据类型为0xFF。若广播报文中携带设备制造商数据，则该字段有值，否则内容为undefined。

Map的key表示制造商ID，value表示对应制造商数据的具体内容。

**类型：** Map&lt;number, Uint8Array&gt;

**起始版本：** 22

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

## rssi

```TypeScript
rssi: number
```

扫描到的设备信号强度，单位：dBm。

**类型：** number

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

## serviceDataMap

```TypeScript
serviceDataMap?: Map<string, Uint8Array>
```

扫描到的设备服务数据集合，从原始数据data字段中解析而来，在蓝牙协议中广播数据类型为0x16。若广播报文中携带设备服务数据，则该字段有值，否则内容为undefined。

Map的key表示服务UUID，value表示对应UUID服务的具体内容。

**类型：** Map&lt;string, Uint8Array&gt;

**起始版本：** 22

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

## serviceUuids

```TypeScript
serviceUuids?: string[]
```

扫描到的设备服务UUID集合，从原始数据data字段中解析而来，在蓝牙协议中，16-bit UUID的广播数据类型为0x03，32-bit UUID类型为0x05，128-bit UUID类型为0x07。若广播报文中携带设备服务UUID，则该字段有值，否则内容为undefined。

**类型：** string[]

**起始版本：** 22

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

## txPowerLevel

```TypeScript
txPowerLevel?: number
```

扫描到的设备广播发送功率，单位：dBm，从原始数据data字段中解析而来，在蓝牙协议中广播数据类型为0x0A。若广播报文中携带设备广播发送功率，则该字段有值，否则内容为undefined。

**类型：** number

**起始版本：** 22

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Communication.Bluetooth.Core
