# OobData (System API)

```TypeScript
interface OobData
```

Out Of Band data used in Bluetooth device pairing.

**Since:** 23

<!--Device-connection-interface OobData--><!--Device-connection-interface OobData-End-->

**System capability:** SystemCapability.Communication.Bluetooth.Core

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { connection } from '@kit.ConnectivityKit';
```

## confirmationHash

```TypeScript
confirmationHash: Uint8Array
```

Confirmation data in OOB pairing, with a size of 16 octets.

**Type:** Uint8Array

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

<!--Device-OobData-confirmationHash: Uint8Array--><!--Device-OobData-confirmationHash: Uint8Array-End-->

**System capability:** SystemCapability.Communication.Bluetooth.Core

**System API:** This is a system API.

## deviceId

```TypeScript
deviceId: BluetoothAddress
```

The address of remote Bluetooth device.

**Type:** [BluetoothAddress](arkts-connectivity-connection-bluetoothaddress-t.md)

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

<!--Device-OobData-deviceId: BluetoothAddress--><!--Device-OobData-deviceId: BluetoothAddress-End-->

**System capability:** SystemCapability.Communication.Bluetooth.Core

**System API:** This is a system API.

## deviceName

```TypeScript
deviceName?: string
```

The name of the remote Bluetooth device.

**Type:** string

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

<!--Device-OobData-deviceName?: string--><!--Device-OobData-deviceName?: string-End-->

**System capability:** SystemCapability.Communication.Bluetooth.Core

**System API:** This is a system API.

## deviceRole

```TypeScript
deviceRole?: DeviceRole
```

The role of the remote Bluetooth device.

**Type:** [DeviceRole](arkts-connectivity-connection-devicerole-e-sys.md)

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

<!--Device-OobData-deviceRole?: DeviceRole--><!--Device-OobData-deviceRole?: DeviceRole-End-->

**System capability:** SystemCapability.Communication.Bluetooth.Core

**System API:** This is a system API.

## randomizerHash

```TypeScript
randomizerHash?: Uint8Array
```

Randomizer data in OOB pairing, with a size of 16 octets.

**Type:** Uint8Array

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

<!--Device-OobData-randomizerHash?: Uint8Array--><!--Device-OobData-randomizerHash?: Uint8Array-End-->

**System capability:** SystemCapability.Communication.Bluetooth.Core

**System API:** This is a system API.
