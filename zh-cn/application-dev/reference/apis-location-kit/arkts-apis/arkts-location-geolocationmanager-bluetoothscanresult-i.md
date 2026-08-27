# BluetoothScanResult

蓝牙扫描结果。

**起始版本：** 16

**系统能力：** SystemCapability.Location.Location.Core

## 导入模块

```TypeScript
```

## connectable

```TypeScript
connectable: boolean
```

表示扫描到的设备是否可连接。true表示可连接，false表示不可连接。

**类型：** boolean

**起始版本：** 16

**系统能力：** SystemCapability.Location.Location.Core

## data

```TypeScript
data?: ArrayBuffer
```

表示扫描到的设备发送的广播包。

**类型：** ArrayBuffer

**起始版本：** 16

**系统能力：** SystemCapability.Location.Location.Core

## deviceId

```TypeScript
deviceId: string
```

表示扫描到的设备地址。例如："XX:XX:XX:XX:XX:XX"。

**类型：** string

**起始版本：** 16

**系统能力：** SystemCapability.Location.Location.Core

## deviceName

```TypeScript
deviceName: string
```

表示扫描到的设备名称。

**类型：** string

**起始版本：** 16

**系统能力：** SystemCapability.Location.Location.Core

## rssi

```TypeScript
rssi: number
```

表示扫描到的设备的rssi值，单位dBm。

**类型：** number

**起始版本：** 16

**系统能力：** SystemCapability.Location.Location.Core
