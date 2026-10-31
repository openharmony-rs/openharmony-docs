# OH_AVRecorder_Location
<!--Kit: Media Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @gcw_dyOv3Sds-->
<!--Designer: @chris2981-->
<!--Tester: @xdlinc-->
<!--Adviser: @zzs911-->
<!-- md-trans-meta sourceCommit=ca13aab0e0ebd0cc27873ac695d82b2fc147ea27 translatedAt=2026-09-15T16:30:49.857Z pushedAt=2026-09-18T08:59:38.826Z -->

```c
typedef struct OH_AVRecorder_Location {...} OH_AVRecorder_Location
```

## Overview

Describes the geographical location information about a media asset and supports the annotation of latitude and longitude during audio and video recording. This struct uses the [OH_AVRecorder_Prepare](capi-avrecorder-h.md#oh_avrecorder_prepare) API of AVRecorder to write the latitude and longitude information into the metadata of the recording file. You need to set the latitude and longitude parameters of this structure before recording. During recording, the geographical location information is automatically embedded into the generated media file. This struct is applicable to scenarios where geographical locations need to be embedded in the recording result, such as marking the shooting location during video shooting, marking the track location in activity record apps, and recording the itinerary coordinates in travel diary apps. This facilitates subsequent retrieval and classification management of media resources by location.

**Since**: 18

**Related module**: [AVRecorder](capi-avrecorder.md)

**Header file**: [avrecorder_base.h](capi-avrecorder-base-h.md)

## Summary

### Member Variables

| Name| Description|
| -- | -- |
| float latitude | Latitude. The value range is [-90,90], in degrees (°). This parameter must be used together with longitude to provide complete geographical location information. If the value is out of the range, an error occurs. |
| float longitude | Longitude. The value range is [-180,180], in degrees (°). This parameter must be used together with latitude to provide complete geographical location information. If the value is out of the range, an error occurs. |


