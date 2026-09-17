# AdvertiseData

描述BLE广播数据包的内容。

从API version 9开始支持，从API version 10开始废弃。

**起始版本：** 9

**废弃版本：** 10

**替代接口：** [AdvertiseData](arkts-connectivity-ble-advertisedata-i.md)

**系统能力：** SystemCapability.Communication.Bluetooth.Core

## 导入模块

```TypeScript
import { bluetoothManager } from '@kit.ConnectivityKit';
```

## manufactureData

```TypeScript
manufactureData: Array<ManufactureData>
```

表示要广播的广播的制造商信息列表。

**类型：** Array&lt;[ManufactureData](arkts-connectivity-bluetoothmanager-manufacturedata-i.md)&gt;

**起始版本：** 9

**废弃版本：** 10

**替代接口：** [manufactureData](arkts-connectivity-ble-advertisedata-i.md#manufacturedata)

**系统能力：** SystemCapability.Communication.Bluetooth.Core

## serviceData

```TypeScript
serviceData: Array<ServiceData>
```

表示要广播的服务数据列表。

**类型：** Array&lt;[ServiceData](arkts-connectivity-bluetoothmanager-servicedata-i.md)&gt;

**起始版本：** 9

**废弃版本：** 10

**替代接口：** [serviceData](arkts-connectivity-ble-advertisedata-i.md#servicedata)

**系统能力：** SystemCapability.Communication.Bluetooth.Core

## serviceUuids

```TypeScript
serviceUuids: Array<string>
```

表示要广播的服务 UUID 列表。

**类型：** Array&lt;string&gt;

**起始版本：** 9

**废弃版本：** 10

**替代接口：** [serviceUuids](arkts-connectivity-ble-advertisedata-i.md#serviceuuids)

**系统能力：** SystemCapability.Communication.Bluetooth.Core
