# ScanFilter

扫描过滤参数。

从API version 7开始支持，从API version 9开始废弃。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [ScanFilter](arkts-connectivity-bluetoothmanager-scanfilter-i.md)

**系统能力：** SystemCapability.Communication.Bluetooth.Core

## 导入模块

```TypeScript
import { bluetooth } from '@kit.ConnectivityKit';
```

## deviceId

```TypeScript
deviceId?: string
```

表示过滤的BLE设备地址，例如："XX:XX:XX:XX:XX:XX"。

**类型：** string

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [deviceId](arkts-connectivity-bluetoothmanager-scanfilter-i.md#deviceid)

**系统能力：** SystemCapability.Communication.Bluetooth.Core

## name

```TypeScript
name?: string
```

表示过滤的BLE设备名。

**类型：** string

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [name](arkts-connectivity-bluetoothmanager-scanfilter-i.md#name)

**系统能力：** SystemCapability.Communication.Bluetooth.Core

## serviceUuid

```TypeScript
serviceUuid?: string
```

表示过滤包含该UUID服务的设备，例如：00001888-0000-1000-8000-00805f9b34fb。

**类型：** string

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [serviceUuid](arkts-connectivity-bluetoothmanager-scanfilter-i.md#serviceuuid)

**系统能力：** SystemCapability.Communication.Bluetooth.Core
