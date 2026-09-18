# BluetoothAddress

Describe the type of Bluetooth address.

**Since:** 21

**System capability:** SystemCapability.Communication.Bluetooth.Core

## Modules to Import

```TypeScript
import { common } from '@kit.ConnectivityKit';
```

## address

```TypeScript
address: string
```

The string of the Bluetooth address.

**Type:** string

**Since:** 21

**System capability:** SystemCapability.Communication.Bluetooth.Core

## addressType

```TypeScript
addressType: BluetoothAddressType
```

The type of the Bluetooth address.

**Type:** [BluetoothAddressType](arkts-connectivity-common-bluetoothaddresstype-e.md)

**Since:** 21

**System capability:** SystemCapability.Communication.Bluetooth.Core

## rawAddressType

```TypeScript
rawAddressType?: BluetoothRawAddressType
```

Address type defined by the Bluetooth Core Specification. It is used only when the [addressType](#addresstype) is [REAL](arkts-connectivity-common-bluetoothaddresstype-e.md#real).

**Type:** [BluetoothRawAddressType](arkts-connectivity-common-bluetoothrawaddresstype-e.md)

**Since:** 23

**System capability:** SystemCapability.Communication.Bluetooth.Core
