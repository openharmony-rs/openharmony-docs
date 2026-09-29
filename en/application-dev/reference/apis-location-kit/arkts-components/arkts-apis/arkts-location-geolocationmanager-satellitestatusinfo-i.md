# SatelliteStatusInfo

```TypeScript
export interface SatelliteStatusInfo
```

Satellite status information.

**Since:** 9

<!--Device-geoLocationManager-export interface SatelliteStatusInfo--><!--Device-geoLocationManager-export interface SatelliteStatusInfo-End-->

**System capability:** SystemCapability.Location.Location.Gnss

## Modules to Import

```TypeScript
import { geoLocationManager } from '@kit.LocationKit';
```

## altitudes

```TypeScript
altitudes: Array<number>
```

Satellite altitude array.

**Type:** Array&lt;number&gt;

**Since:** 9

<!--Device-SatelliteStatusInfo-altitudes: Array<double>--><!--Device-SatelliteStatusInfo-altitudes: Array<double>-End-->

**System capability:** SystemCapability.Location.Location.Gnss

## azimuths

```TypeScript
azimuths: Array<number>
```

Satellite azimuth array.

**Type:** Array&lt;number&gt;

**Since:** 9

<!--Device-SatelliteStatusInfo-azimuths: Array<double>--><!--Device-SatelliteStatusInfo-azimuths: Array<double>-End-->

**System capability:** SystemCapability.Location.Location.Gnss

## carrierFrequencies

```TypeScript
carrierFrequencies: Array<number>
```

Satellite carrier frequency array.

**Type:** Array&lt;number&gt;

**Since:** 9

<!--Device-SatelliteStatusInfo-carrierFrequencies: Array<double>--><!--Device-SatelliteStatusInfo-carrierFrequencies: Array<double>-End-->

**System capability:** SystemCapability.Location.Location.Gnss

## carrierToNoiseDensitys

```TypeScript
carrierToNoiseDensitys: Array<number>
```

Carrier to noise density array.

**Type:** Array&lt;number&gt;

**Since:** 9

<!--Device-SatelliteStatusInfo-carrierToNoiseDensitys: Array<double>--><!--Device-SatelliteStatusInfo-carrierToNoiseDensitys: Array<double>-End-->

**System capability:** SystemCapability.Location.Location.Gnss

## satelliteAdditionalInfo

```TypeScript
satelliteAdditionalInfo?: Array<number>
```

Satellite additional information array.

**Type:** Array&lt;number&gt;

**Since:** 12

<!--Device-SatelliteStatusInfo-satelliteAdditionalInfo?: Array<int>--><!--Device-SatelliteStatusInfo-satelliteAdditionalInfo?: Array<int>-End-->

**System capability:** SystemCapability.Location.Location.Gnss

## satelliteConstellation

```TypeScript
satelliteConstellation?: Array<SatelliteConstellationCategory>
```

Satellite constellation type array.

**Type:** Array&lt;[SatelliteConstellationCategory](arkts-location-geolocationmanager-satelliteconstellationcategory-e.md)&gt;

**Since:** 12

<!--Device-SatelliteStatusInfo-satelliteConstellation?: Array<SatelliteConstellationCategory>--><!--Device-SatelliteStatusInfo-satelliteConstellation?: Array<SatelliteConstellationCategory>-End-->

**System capability:** SystemCapability.Location.Location.Gnss

## satelliteIds

```TypeScript
satelliteIds: Array<number>
```

Satellite ID array.

**Type:** Array&lt;number&gt;

**Since:** 9

<!--Device-SatelliteStatusInfo-satelliteIds: Array<int>--><!--Device-SatelliteStatusInfo-satelliteIds: Array<int>-End-->

**System capability:** SystemCapability.Location.Location.Gnss

## satellitesNumber

```TypeScript
satellitesNumber: number
```

Number of satellites.

**Type:** number

**Since:** 9

<!--Device-SatelliteStatusInfo-satellitesNumber: int--><!--Device-SatelliteStatusInfo-satellitesNumber: int-End-->

**System capability:** SystemCapability.Location.Location.Gnss
