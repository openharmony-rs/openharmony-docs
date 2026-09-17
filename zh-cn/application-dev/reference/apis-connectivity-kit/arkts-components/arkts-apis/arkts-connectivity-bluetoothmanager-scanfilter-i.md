# ScanFilter

扫描过滤参数。

从API version 9开始支持，从API version 10开始废弃。

**起始版本：** 9

**废弃版本：** 10

**替代接口：** [ScanFilter](arkts-connectivity-ble-scanfilter-i.md)

**系统能力：** SystemCapability.Communication.Bluetooth.Core

## 导入模块

```TypeScript
import { bluetoothManager } from '@kit.ConnectivityKit';
```

## deviceId

```TypeScript
deviceId?: string
```

表示过滤的BLE设备地址，例如："XX:XX:XX:XX:XX:XX"。

**类型：** string

**起始版本：** 9

**废弃版本：** 10

**替代接口：** [deviceId](arkts-connectivity-ble-scanfilter-i.md#deviceid)

**系统能力：** SystemCapability.Communication.Bluetooth.Core

## manufactureData

```TypeScript
manufactureData?: ArrayBuffer
```

表示过滤包含该制造商相关数据的设备，例如：[0x1F,0x2F,0x3F]。

**类型：** ArrayBuffer

**起始版本：** 9

**废弃版本：** 10

**替代接口：** [manufactureData](arkts-connectivity-ble-scanfilter-i.md#manufacturedata)

**系统能力：** SystemCapability.Communication.Bluetooth.Core

## manufactureDataMask

```TypeScript
manufactureDataMask?: ArrayBuffer
```

表示过滤包含该制造商相关数据掩码的设备，例如：[0xFF,0xFF,0xFF]。

**类型：** ArrayBuffer

**起始版本：** 9

**废弃版本：** 10

**替代接口：** [manufactureDataMask](arkts-connectivity-ble-scanfilter-i.md#manufacturedatamask)

**系统能力：** SystemCapability.Communication.Bluetooth.Core

## manufactureId

```TypeScript
manufactureId?: number
```

表示过滤包含该制造商ID的设备，例如：0x0006。

**类型：** number

**起始版本：** 9

**废弃版本：** 10

**替代接口：** [manufactureId](arkts-connectivity-ble-scanfilter-i.md#manufactureid)

**系统能力：** SystemCapability.Communication.Bluetooth.Core

## name

```TypeScript
name?: string
```

表示过滤的BLE设备名。

**类型：** string

**起始版本：** 9

**废弃版本：** 10

**替代接口：** [name](arkts-connectivity-ble-scanfilter-i.md#name)

**系统能力：** SystemCapability.Communication.Bluetooth.Core

## serviceData

```TypeScript
serviceData?: ArrayBuffer
```

表示过滤包含该服务相关数据的设备，例如：[0x90,0x00,0xF1,0xF2]。

**类型：** ArrayBuffer

**起始版本：** 9

**废弃版本：** 10

**替代接口：** [serviceData](arkts-connectivity-ble-scanfilter-i.md#servicedata)

**系统能力：** SystemCapability.Communication.Bluetooth.Core

## serviceDataMask

```TypeScript
serviceDataMask?: ArrayBuffer
```

表示过滤包含该服务相关数据掩码的设备，例如：[0xFF,0xFF,0xFF,0xFF]。

**类型：** ArrayBuffer

**起始版本：** 9

**废弃版本：** 10

**替代接口：** [serviceDataMask](arkts-connectivity-ble-scanfilter-i.md#servicedatamask)

**系统能力：** SystemCapability.Communication.Bluetooth.Core

## serviceSolicitationUuid

```TypeScript
serviceSolicitationUuid?: string
```

表示过滤包含该UUID服务请求的设备，例如：00001888-0000-1000-8000-00805F9B34FB。

**类型：** string

**起始版本：** 9

**废弃版本：** 10

**替代接口：** [serviceSolicitationUuid](arkts-connectivity-ble-scanfilter-i.md#servicesolicitationuuid)

**系统能力：** SystemCapability.Communication.Bluetooth.Core

## serviceSolicitationUuidMask

```TypeScript
serviceSolicitationUuidMask?: string
```

表示过滤包含该UUID服务请求掩码的设备，例如：FFFFFFFF-FFFF-FFFF-FFFF-FFFFFFFFFFFF。

**类型：** string

**起始版本：** 9

**废弃版本：** 10

**替代接口：** [serviceSolicitationUuidMask](arkts-connectivity-ble-scanfilter-i.md#servicesolicitationuuidmask)

**系统能力：** SystemCapability.Communication.Bluetooth.Core

## serviceUuid

```TypeScript
serviceUuid?: string
```

表示过滤包含该UUID服务的设备，例如：00001888-0000-1000-8000-00805f9b34fb。

**类型：** string

**起始版本：** 9

**废弃版本：** 10

**替代接口：** [serviceUuid](arkts-connectivity-ble-scanfilter-i.md#serviceuuid)

**系统能力：** SystemCapability.Communication.Bluetooth.Core

## serviceUuidMask

```TypeScript
serviceUuidMask?: string
```

表示过滤包含该UUID服务掩码的设备，例如：FFFFFFFF-FFFF-FFFF-FFFF-FFFFFFFFFFFF。

**类型：** string

**起始版本：** 9

**废弃版本：** 10

**替代接口：** [serviceUuidMask](arkts-connectivity-ble-scanfilter-i.md#serviceuuidmask)

**系统能力：** SystemCapability.Communication.Bluetooth.Core
