# AdvertiseSetting

Describes the settings for BLE advertising.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [AdvertiseSetting](arkts-connectivity-bluetoothmanager-advertisesetting-i.md)

**System capability:** SystemCapability.Communication.Bluetooth.Core

## Modules to Import

```TypeScript
import { bluetooth } from '@kit.ConnectivityKit';
```

## connectable

```TypeScript
connectable?: boolean
```

Indicates whether the BLE is connectable, default is `true`

**Type:** boolean

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [connectable](arkts-connectivity-bluetoothmanager-advertisesetting-i.md#connectable)

**System capability:** SystemCapability.Communication.Bluetooth.Core

## interval

```TypeScript
interval?: number
```

Minimum slot value for the advertising interval, which is `32` (20 ms) Maximum slot value for the advertising interval, which is `16777215` (10485.759375s) Default slot value for the advertising interval, which is `1600` (1s)

**Type:** number

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [interval](arkts-connectivity-bluetoothmanager-advertisesetting-i.md#interval)

**System capability:** SystemCapability.Communication.Bluetooth.Core

## txPower

```TypeScript
txPower?: number
```

Minimum transmission power level for advertising, which is `-127` Maximum transmission power level for advertising, which is `1` Default transmission power level for advertising, which is `-7`

**Type:** number

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [txPower](arkts-connectivity-bluetoothmanager-advertisesetting-i.md#txpower)

**System capability:** SystemCapability.Communication.Bluetooth.Core
