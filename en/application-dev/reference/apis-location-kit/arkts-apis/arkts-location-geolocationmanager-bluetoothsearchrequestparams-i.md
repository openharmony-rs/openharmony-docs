# BluetoothSearchRequestParams

Indicates request parameters for Bluetooth search function.

**Since:** 26.0.0

**System capability:** SystemCapability.Location.Location.Core

## Modules to Import

```TypeScript
import { geoLocationManager } from '@kit.LocationKit';
```

## deviceIdArray

```TypeScript
deviceIdArray: Array<string>
```

Indicates the list of Bluetooth device ID that need to be search.

**Type:** Array&lt;string&gt;

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.Location.Location.Core

## rssiThreshold

```TypeScript
rssiThreshold?: number
```

Indicates the Bluetooth RSSI threshold, only search Bluetooth BSSID with RSSI greater than this threshold. The value range is all integers.

**Type:** number

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.Location.Location.Core
