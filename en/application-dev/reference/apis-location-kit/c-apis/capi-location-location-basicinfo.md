# Location_BasicInfo

```c
typedef struct Location_BasicInfo {...} Location_BasicInfo
```

## Overview

Defines the location information.

<!--Device-struct Location_BasicInfo {...}--><!--Device-struct Location_BasicInfo {...}-End-->

**System capability**: SystemCapability.Location.Location.Core

**Since**: 13

**Related module**: [Location](capi-location-kit-location.md)

**Header file**: [oh_location_type.h](capi-oh-location-type-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| double latitude | Indicates latitude information, with positive values indicating north latitude and negative values indicating south latitude. The value range is -90 to 90. Only supports WGS84 coordinate system.<br><!--Device-double latitude--><!--Device-double latitude-End--> |
| double longitude | Indicates longitude information, positive values indicate east longitude, and negative values indicate west longitude. The value range is -180 to 180. Only supports WGS84 coordinate system.<br><!--Device-double longitude--><!--Device-double longitude-End--> |
| double altitude | Altitude in meters.<br><!--Device-double altitude--><!--Device-double altitude-End--> |
| double accuracy | Horizontal location accuracy in meters.<br><!--Device-double accuracy--><!--Device-double accuracy-End--> |
| double speed | Speed in meters per second.<br><!--Device-double speed--><!--Device-double speed-End--> |
| double direction | Heading in degrees. The value range is 0 to 360.<br><!--Device-double direction--><!--Device-double direction-End--> |
| int64_t timeForFix | Timestamp for the location fix. Number of milliseconds since January 1, 1970.<br><!--Device-int64_t timeForFix--><!--Device-int64_t timeForFix-End--> |
| int64_t timeSinceBoot | Time since the system was booted, and include deep sleep. The unit is nanosecond.<br><!--Device-int64_t timeSinceBoot--><!--Device-int64_t timeSinceBoot-End--> |
| double altitudeAccuracy | Vertical position accuracy in meters.<br><!--Device-double altitudeAccuracy--><!--Device-double altitudeAccuracy-End--> |
| double speedAccuracy | Speed accuracy in meter per seconds.<br><!--Device-double speedAccuracy--><!--Device-double speedAccuracy-End--> |
| double directionAccuracy | Direction accuracy in degrees. The value range is 0 to 360.<br><!--Device-double directionAccuracy--><!--Device-double directionAccuracy-End--> |
| int64_t uncertaintyOfTimeSinceBoot | Time uncertainty in nanosecond.<br><!--Device-int64_t uncertaintyOfTimeSinceBoot--><!--Device-int64_t uncertaintyOfTimeSinceBoot-End--> |
| [Location_SourceType](capi-oh-location-type-h.md#location_sourcetype) locationSourceType | Indicates the source of the location result.<br><!--Device-Location_SourceType locationSourceType--><!--Device-Location_SourceType locationSourceType-End--> |


