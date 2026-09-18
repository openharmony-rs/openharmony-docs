# DiscoveryResult

扫描到设备后，上报的扫描结果。

**起始版本：** 18

**系统能力：** SystemCapability.Communication.Bluetooth.Core

## 导入模块

```TypeScript
import { connection } from '@kit.ConnectivityKit';
```

## deviceClass

```TypeScript
deviceClass: DeviceClass
```

扫描到的设备类型。

**类型：** [DeviceClass](arkts-connectivity-connection-deviceclass-i.md)

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

## deviceId

```TypeScript
deviceId: string
```

扫描到的设备地址。

基于信息安全考虑，此处获取的设备地址为虚拟MAC地址。

已配对的地址不会变更。若该设备重启蓝牙开关，重新获取到的虚拟地址会立即变更。若取消配对，蓝牙子系统会根据该地址的实际使用情况，决策后续变更时机；若其他应用正在使用该地址，则不会立刻变更。若要持久化保存该地址，可使用[access.addPersistentDeviceId](arkts-connectivity-access-addpersistentdeviceid-f.md)方法。

**类型：** string

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

## deviceName

```TypeScript
deviceName: string
```

扫描到的设备名称。

**类型：** string

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

## rssi

```TypeScript
rssi: number
```

扫描到的设备信号强度，单位：dBm。

**类型：** number

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.Bluetooth.Core
