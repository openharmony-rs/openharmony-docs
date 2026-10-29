# DiscoveryResult

```TypeScript
interface DiscoveryResult
```

Describes the contents of the discovery results

**Since:** 18

<!--Device-connection-interface DiscoveryResult--><!--Device-connection-interface DiscoveryResult-End-->

**System capability:** SystemCapability.Communication.Bluetooth.Core

## Modules to Import

```TypeScript
import { connection } from '@kit.ConnectivityKit';
```

## deviceClass

```TypeScript
deviceClass: DeviceClass
```

The class of the device

**Type:** [DeviceClass](arkts-connectivity-connection-deviceclass-i.md)

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

<!--Device-DiscoveryResult-deviceClass: DeviceClass--><!--Device-DiscoveryResult-deviceClass: DeviceClass-End-->

**System capability:** SystemCapability.Communication.Bluetooth.Core

## deviceId

```TypeScript
deviceId: string
```

Identify of the discovered device

**Type:** string

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

<!--Device-DiscoveryResult-deviceId: string--><!--Device-DiscoveryResult-deviceId: string-End-->

**System capability:** SystemCapability.Communication.Bluetooth.Core

## deviceName

```TypeScript
deviceName: string
```

The local name of the device

**Type:** string

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

<!--Device-DiscoveryResult-deviceName: string--><!--Device-DiscoveryResult-deviceName: string-End-->

**System capability:** SystemCapability.Communication.Bluetooth.Core

## rssi

```TypeScript
rssi: number
```

RSSI of the remote device

**Type:** number

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

<!--Device-DiscoveryResult-rssi: int--><!--Device-DiscoveryResult-rssi: int-End-->

**System capability:** SystemCapability.Communication.Bluetooth.Core

## transport

```TypeScript
transport?: BluetoothTransport
```

The transport of the discovered device.

**Type:** [BluetoothTransport](arkts-connectivity-connection-bluetoothtransport-e.md)

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-DiscoveryResult-transport?: BluetoothTransport--><!--Device-DiscoveryResult-transport?: BluetoothTransport-End-->

**System capability:** SystemCapability.Communication.Bluetooth.Core
