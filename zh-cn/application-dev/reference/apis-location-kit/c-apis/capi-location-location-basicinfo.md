# Location_BasicInfo

```c
typedef struct Location_BasicInfo {...} Location_BasicInfo
```

## 概述

定义位置基本信息的结构体。

<!--Device-struct Location_BasicInfo {...}--><!--Device-struct Location_BasicInfo {...}-End-->

**系统能力：** SystemCapability.Location.Location.Core

**起始版本：** 13

**相关模块：** [Location](capi-location-kit-location.md)

**所在头文件：** [oh_location_type.h](capi-oh-location-type-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| double latitude | 表示纬度信息，正值表示北纬，负值表示南纬。取值范围为-90到90。仅支持WGS84坐标系。<br><!--Device-double latitude--><!--Device-double latitude-End--> |
| double longitude | 表示经度信息，正值表示东经，负值表示西经。取值范围为-180到180。仅支持WGS84坐标系。<br><!--Device-double longitude--><!--Device-double longitude-End--> |
| double altitude | 表示高度信息，单位米。<br><!--Device-double altitude--><!--Device-double altitude-End--> |
| double accuracy | 表示精度信息，单位米。<br><!--Device-double accuracy--><!--Device-double accuracy-End--> |
| double speed | 表示速度信息，单位米每秒。<br><!--Device-double speed--><!--Device-double speed-End--> |
| double direction | 表示航向信息。单位是“度”，取值范围为0到360。<br><!--Device-double direction--><!--Device-double direction-End--> |
| int64_t timeForFix | 表示位置时间戳，UTC格式。<br><!--Device-int64_t timeForFix--><!--Device-int64_t timeForFix-End--> |
| int64_t timeSinceBoot | 表示获取位置的时间戳，值表示从本次开机到获取位置所经过的时间，单位为纳秒。<br><!--Device-int64_t timeSinceBoot--><!--Device-int64_t timeSinceBoot-End--> |
| double altitudeAccuracy | 表示高度信息的精度，单位米。<br><!--Device-double altitudeAccuracy--><!--Device-double altitudeAccuracy-End--> |
| double speedAccuracy | 表示速度信息的精度，单位米每秒。<br><!--Device-double speedAccuracy--><!--Device-double speedAccuracy-End--> |
| double directionAccuracy | 表示航向信息的精度。单位是“度”，取值范围为0到360。<br><!--Device-double directionAccuracy--><!--Device-double directionAccuracy-End--> |
| int64_t uncertaintyOfTimeSinceBoot | 表示位置时间戳的不确定度，单位为纳秒。<br><!--Device-int64_t uncertaintyOfTimeSinceBoot--><!--Device-int64_t uncertaintyOfTimeSinceBoot-End--> |
| [Location_SourceType](capi-oh-location-type-h.md#location_sourcetype) locationSourceType | 表示定位结果的来源。详细定义请参考Location_SourceType。<br><!--Device-Location_SourceType locationSourceType--><!--Device-Location_SourceType locationSourceType-End--> |


