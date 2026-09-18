# Location_BasicInfo

```c
typedef struct Location_BasicInfo {...} Location_BasicInfo
```

## Overview

Defines the location information.

**Since**: 13

**Related module**: [Location](capi-location.md)

**Header file**: [oh_location_type.h](capi-oh-location-type-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| double latitude | Indicates latitude information, with positive values indicating north latitude and negative values indicating south latitude. The value range is -90 to 90. Only supports WGS84 coordinate system. |
| double longitude | Indicates longitude information, positive values indicate east longitude, and negative values indicate west longitude. The value range is -180 to 180. Only supports WGS84 coordinate system. |
| double altitude | Altitude in meters. |
| double accuracy | Horizontal location accuracy in meters. |
| double speed | Speed in meters per second. |
| double direction | Heading in degrees. The value range is 0 to 360. |
| int64_t timeForFix | Timestamp for the location fix. Number of milliseconds since January 1, 1970. |
| int64_t timeSinceBoot | Time since the system was booted, and include deep sleep. The unit is nanosecond. |
| double altitudeAccuracy | Vertical position accuracy in meters. |
| double speedAccuracy | Speed accuracy in meter per seconds. |
| double directionAccuracy | Direction accuracy in degrees. The value range is 0 to 360. |
| int64_t uncertaintyOfTimeSinceBoot | Time uncertainty in nanosecond. |
| [Location_SourceType](capi-oh-location-type-h.md#location_sourcetype) locationSourceType | Indicates the source of the location result. |


