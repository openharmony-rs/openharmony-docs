# GattSetting

```TypeScript
interface GattSetting
```

Describes the setting for Gatt Connection.

**Since:** 26.0.0

<!--Device-ble-interface GattSetting--><!--Device-ble-interface GattSetting-End-->

**System capability:** SystemCapability.Communication.Bluetooth.Core

## Modules to Import

```TypeScript
import { ble } from '@kit.ConnectivityKit';
```

## autoConnect

```TypeScript
autoConnect?: boolean
```

Indicates whether to automatically connect to the remote device, default is `false`

**Type:** boolean

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 26.0.0.

<!--Device-GattSetting-autoConnect?: boolean--><!--Device-GattSetting-autoConnect?: boolean-End-->

**System capability:** SystemCapability.Communication.Bluetooth.Core

## transport

```TypeScript
transport?: BluetoothTransport
```

Transport of the connection, default is `TRANSPORT_LE`

**Type:** [BluetoothTransport](arkts-connectivity-ble-bluetoothtransport-t.md)

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 26.0.0.

<!--Device-GattSetting-transport?: BluetoothTransport--><!--Device-GattSetting-transport?: BluetoothTransport-End-->

**System capability:** SystemCapability.Communication.Bluetooth.Core
