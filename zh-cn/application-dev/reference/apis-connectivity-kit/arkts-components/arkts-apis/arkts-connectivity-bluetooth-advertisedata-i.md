# AdvertiseData

```TypeScript
interface AdvertiseData
```

描述BLE广播数据包的内容。

从API version 7开始支持，从API version 9开始废弃。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [AdvertiseData](arkts-connectivity-bluetoothmanager-advertisedata-i.md)

<!--Device-bluetooth-interface AdvertiseData--><!--Device-bluetooth-interface AdvertiseData-End-->

**系统能力：** SystemCapability.Communication.Bluetooth.Core

## 导入模块

```TypeScript
import { bluetooth } from '@kit.ConnectivityKit';
```

## manufactureData

```TypeScript
manufactureData: Array<ManufactureData>
```

表示要广播的广播的制造商信息列表。

**类型：** Array&lt;[ManufactureData](arkts-connectivity-bluetooth-manufacturedata-i.md)&gt;

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [manufactureData](arkts-connectivity-bluetoothmanager-advertisedata-i.md#manufacturedata)

<!--Device-AdvertiseData-manufactureData: Array<ManufactureData>--><!--Device-AdvertiseData-manufactureData: Array<ManufactureData>-End-->

**系统能力：** SystemCapability.Communication.Bluetooth.Core

## serviceData

```TypeScript
serviceData: Array<ServiceData>
```

表示要广播的服务数据列表。

**类型：** Array&lt;[ServiceData](arkts-connectivity-bluetooth-servicedata-i.md)&gt;

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [serviceData](arkts-connectivity-bluetoothmanager-advertisedata-i.md#servicedata)

<!--Device-AdvertiseData-serviceData: Array<ServiceData>--><!--Device-AdvertiseData-serviceData: Array<ServiceData>-End-->

**系统能力：** SystemCapability.Communication.Bluetooth.Core

## serviceUuids

```TypeScript
serviceUuids: Array<string>
```

表示要广播的服务 UUID 列表。

**类型：** Array&lt;string&gt;

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [serviceUuids](arkts-connectivity-bluetoothmanager-advertisedata-i.md#serviceuuids)

<!--Device-AdvertiseData-serviceUuids: Array<string>--><!--Device-AdvertiseData-serviceUuids: Array<string>-End-->

**系统能力：** SystemCapability.Communication.Bluetooth.Core
