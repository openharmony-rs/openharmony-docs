# WirelessSignalFeature (System API)

```TypeScript
export interface WirelessSignalFeature
```

Indicates wireless signal feature.

**Since:** 26.0.0

<!--Device-geoLocationManager-export interface WirelessSignalFeature--><!--Device-geoLocationManager-export interface WirelessSignalFeature-End-->

**System capability:** SystemCapability.Location.Location.Geofence

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { geoLocationManager } from '@kit.LocationKit';
```

## mac

```TypeScript
mac: Array<string>
```

Indicates MAC array.

**Type:** Array&lt;string&gt;

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-WirelessSignalFeature-mac: Array<string>--><!--Device-WirelessSignalFeature-mac: Array<string>-End-->

**System capability:** SystemCapability.Location.Location.Geofence

**System API:** This is a system API.

## rssiAvg

```TypeScript
rssiAvg: number
```

Indicates average RSSI value. The value range is all integers.

**Type:** number

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-WirelessSignalFeature-rssiAvg: int--><!--Device-WirelessSignalFeature-rssiAvg: int-End-->

**System capability:** SystemCapability.Location.Location.Geofence

**System API:** This is a system API.

## rssiStandardDeviation

```TypeScript
rssiStandardDeviation: number
```

Indicates RSSI standard deviation.

**Type:** number

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-WirelessSignalFeature-rssiStandardDeviation: double--><!--Device-WirelessSignalFeature-rssiStandardDeviation: double-End-->

**System capability:** SystemCapability.Location.Location.Geofence

**System API:** This is a system API.
