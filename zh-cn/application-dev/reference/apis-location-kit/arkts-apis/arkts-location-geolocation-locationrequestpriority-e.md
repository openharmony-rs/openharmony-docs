# LocationRequestPriority

位置请求中位置信息优先级类型。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [LocationRequestPriority](arkts-location-geolocationmanager-locationrequestpriority-e.md)

**需要权限：** ohos.permission.LOCATION

**系统能力：** SystemCapability.Location.Location.Core

## UNSET

```TypeScript
UNSET = 0x200
```

表示未设置优先级，表示LocationRequestPriority无效。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [UNSET](arkts-location-geolocationmanager-locationrequestpriority-e.md#unset)

**系统能力：** SystemCapability.Location.Location.Core

## ACCURACY

```TypeScript
ACCURACY
```

表示精度优先。 定位精度优先策略主要以GNSS定位技术为主，在开阔场景下可以提供米级的定位精度，具体性能指标依赖用户设备的定位硬件能力，但在室内等强遮蔽定位场景下，无法提供准确的位置服务。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [ACCURACY](arkts-location-geolocationmanager-locationrequestpriority-e.md#accuracy)

**系统能力：** SystemCapability.Location.Location.Core

## LOW_POWER

```TypeScript
LOW_POWER
```

表示低功耗优先。 低功耗定位优先策略主要使用基站定位和WLAN、蓝牙定位技术，也可以同时提供室内和户外场景下的位置服务， 因为其依赖周边基站、可见WLAN、蓝牙设备的分布情况，定位结果的精度波动范围较大， 如果对定位结果精度要求不高，或者使用场景多在有基站、可见WLAN、蓝牙设备高密度分布的情况下，推荐使用，可以有效节省设备功耗。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [LOW_POWER](arkts-location-geolocationmanager-locationrequestpriority-e.md#low_power)

**系统能力：** SystemCapability.Location.Location.Core

## FIRST_FIX

```TypeScript
FIRST_FIX
```

表示快速获取位置优先，如果应用希望快速拿到一个位置，可以将优先级设置为该字段。 快速定位优先策略会同时使用GNSS定位、基站定位和WLAN、蓝牙定位技术， 以便室内和户外场景下，通过此策略都可以获得位置结果，当各种定位技术都有提供位置结果时，系统会选择其中精度较好的结果返回给应用。 因为对各种定位技术同时使用，对设备的硬件资源消耗较大，功耗也较大。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [FIRST_FIX](arkts-location-geolocationmanager-locationrequestpriority-e.md#first_fix)

**系统能力：** SystemCapability.Location.Location.Core
