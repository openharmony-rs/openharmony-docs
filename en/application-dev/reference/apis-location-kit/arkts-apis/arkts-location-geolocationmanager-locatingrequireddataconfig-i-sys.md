# LocatingRequiredDataConfig (System API)

Describes the request parameters for obtaining the data required for locating.

**Since:** 10

**System capability:** SystemCapability.Location.Location.Core

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { geoLocationManager } from '@kit.LocationKit';
```

## arfcn

```TypeScript
arfcn?: number[]
```

Indicates absolute radio frequency channel number (ARFCN). Querying Cell Information by Specified ARFCN.

**Type:** number[]

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Location.Location.Core

**System API:** This is a system API.

## needStartScan

```TypeScript
needStartScan: boolean
```

Indicates whether to start scanning.

**Type:** boolean

**Since:** 10

**System capability:** SystemCapability.Location.Location.Core

**System API:** This is a system API.

## plmnId

```TypeScript
plmnId?: number[]
```

Indicates PLMN number of the SIM card.

**Type:** number[]

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Location.Location.Core

**System API:** This is a system API.

## scanInterval

```TypeScript
scanInterval?: number
```

Indicates the interval between scans. The unit is millisecond. This parameter needs to be set only when scanning information is continuously monitored.

**Type:** number

**Since:** 10

**System capability:** SystemCapability.Location.Location.Core

**System API:** This is a system API.

## scanTimeout

```TypeScript
scanTimeout?: number
```

Indicates the timeout period of a single scan. The unit is millisecond. The default value is 10000. This parameter needs to be set only when getLocatingRequiredData is used.

**Type:** number

**Since:** 10

**System capability:** SystemCapability.Location.Location.Core

**System API:** This is a system API.

## slotId

```TypeScript
slotId?: number
```

Indicates SIM card slot number. The value should be an integer.

**Type:** number

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Location.Location.Core

**System API:** This is a system API.

## type

```TypeScript
type: LocatingRequiredDataType
```

Indicates the type of locating required data.

**Type:** [LocatingRequiredDataType](arkts-location-geolocationmanager-locatingrequireddatatype-e-sys.md)

**Since:** 10

**System capability:** SystemCapability.Location.Location.Core

**System API:** This is a system API.
