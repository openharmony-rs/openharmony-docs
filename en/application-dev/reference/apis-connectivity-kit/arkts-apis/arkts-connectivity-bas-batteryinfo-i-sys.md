# BatteryInfo (System API)

```TypeScript
interface BatteryInfo
```

Describe the contents of the battery information.

**Since:** 26.0.0

<!--Device-bas-interface BatteryInfo--><!--Device-bas-interface BatteryInfo-End-->

**System capability:** SystemCapability.Communication.Bluetooth.Core

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { bas } from '@kit.ConnectivityKit';
```

## batteryLevel

```TypeScript
batteryLevel: number
```

battery value of the device. `-1` means no power information.

**Type:** number

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-BatteryInfo-batteryLevel: int--><!--Device-BatteryInfo-batteryLevel: int-End-->

**System capability:** SystemCapability.Communication.Bluetooth.Core

**System API:** This is a system API.

## deviceId

```TypeScript
deviceId: BluetoothAddress
```

Identify of the discovery device.

**Type:** BluetoothAddress

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-BatteryInfo-deviceId: BluetoothAddress--><!--Device-BatteryInfo-deviceId: BluetoothAddress-End-->

**System capability:** SystemCapability.Communication.Bluetooth.Core

**System API:** This is a system API.
