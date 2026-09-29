# DeviceClass

```TypeScript
interface DeviceClass
```

描述蓝牙设备的类别。

从API version 9开始支持，从API version 10开始废弃。

**起始版本：** 9

**废弃版本：** 10

**替代接口：** [DeviceClass](arkts-connectivity-connection-deviceclass-i.md)

<!--Device-bluetoothManager-interface DeviceClass--><!--Device-bluetoothManager-interface DeviceClass-End-->

**系统能力：** SystemCapability.Communication.Bluetooth.Core

## 导入模块

```TypeScript
import { bluetoothManager } from '@kit.ConnectivityKit';
```

## classOfDevice

```TypeScript
classOfDevice: number
```

表示设备类别。

**类型：** number

**起始版本：** 9

**废弃版本：** 10

**替代接口：** [classOfDevice](arkts-connectivity-connection-deviceclass-i.md#classofdevice)

<!--Device-DeviceClass-classOfDevice: number--><!--Device-DeviceClass-classOfDevice: number-End-->

**系统能力：** SystemCapability.Communication.Bluetooth.Core

## majorClass

```TypeScript
majorClass: MajorClass
```

表示蓝牙设备主要类别的枚举。

**类型：** [MajorClass](arkts-connectivity-bluetoothmanager-majorclass-e.md)

**起始版本：** 9

**废弃版本：** 10

**替代接口：** [majorClass](arkts-connectivity-connection-deviceclass-i.md#majorclass)

<!--Device-DeviceClass-majorClass: MajorClass--><!--Device-DeviceClass-majorClass: MajorClass-End-->

**系统能力：** SystemCapability.Communication.Bluetooth.Core

## majorMinorClass

```TypeScript
majorMinorClass: MajorMinorClass
```

表示主要次要蓝牙设备类别的枚举。

**类型：** [MajorMinorClass](arkts-connectivity-bluetoothmanager-majorminorclass-e.md)

**起始版本：** 9

**废弃版本：** 10

**替代接口：** [majorMinorClass](arkts-connectivity-connection-deviceclass-i.md#majorminorclass)

<!--Device-DeviceClass-majorMinorClass: MajorMinorClass--><!--Device-DeviceClass-majorMinorClass: MajorMinorClass-End-->

**系统能力：** SystemCapability.Communication.Bluetooth.Core
