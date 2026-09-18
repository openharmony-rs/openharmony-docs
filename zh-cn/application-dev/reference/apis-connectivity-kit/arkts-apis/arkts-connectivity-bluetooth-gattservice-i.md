# GattService

描述service的接口参数定义。

从API version 7开始支持，从API version 9开始废弃。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [GattService](arkts-connectivity-bluetoothmanager-gattservice-i.md)

**系统能力：** SystemCapability.Communication.Bluetooth.Core

## 导入模块

```TypeScript
import { bluetooth } from '@kit.ConnectivityKit';
```

## characteristics

```TypeScript
characteristics: Array<BLECharacteristic>
```

当前服务包含的特征列表。

**类型：** Array&lt;[BLECharacteristic](arkts-connectivity-bluetooth-blecharacteristic-i.md)&gt;

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [characteristics](arkts-connectivity-bluetoothmanager-gattservice-i.md#characteristics)

**系统能力：** SystemCapability.Communication.Bluetooth.Core

## includeServices

```TypeScript
includeServices?: Array<GattService>
```

当前服务依赖的其它服务。

**类型：** Array&lt;[GattService](arkts-connectivity-bluetooth-gattservice-i.md)&gt;

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [includeServices](arkts-connectivity-bluetoothmanager-gattservice-i.md#includeservices)

**系统能力：** SystemCapability.Communication.Bluetooth.Core

## isPrimary

```TypeScript
isPrimary: boolean
```

如果是主服务设置为true，否则设置为false。

**类型：** boolean

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [isPrimary](arkts-connectivity-bluetoothmanager-gattservice-i.md#isprimary)

**系统能力：** SystemCapability.Communication.Bluetooth.Core

## serviceUuid

```TypeScript
serviceUuid: string
```

特定服务（service）的UUID，例如：00001888-0000-1000-8000-00805f9b34fb。

**类型：** string

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [serviceUuid](arkts-connectivity-bluetoothmanager-gattservice-i.md#serviceuuid)

**系统能力：** SystemCapability.Communication.Bluetooth.Core
