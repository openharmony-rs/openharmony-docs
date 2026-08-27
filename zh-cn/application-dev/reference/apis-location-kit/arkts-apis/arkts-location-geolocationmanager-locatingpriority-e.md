# LocatingPriority

单次位置请求中的优先级类型。

**起始版本：** 12

**系统能力：** SystemCapability.Location.Location.Core

## PRIORITY_ACCURACY

```TypeScript
PRIORITY_ACCURACY = 0x501
```

表示精度优先。定位精度优先策略会同时使用GNSS定位和网络定位技术，并把一段时间内精度较好的结果返回给应用；这个时间段长度为 [SingleLocationRequest](arkts-location-geolocationmanager-singlelocationrequest-i.md).locatingTimeoutMs与“30秒”中的较小者。对设备的硬件资源消耗较大，功耗较大。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Location.Location.Core

## PRIORITY_LOCATING_SPEED

```TypeScript
PRIORITY_LOCATING_SPEED = 0x502
```

表示快速获取位置优先，如果应用希望快速拿到一个位置，可以将优先级设置为该类型。快速定位优先策略会同时使用GNSS定位和网络定位技术，以便在室内和户外场景下均可以快速获取到位置结果，我们会把最先拿到的定位结果返回给应用。对设备的硬件资源消耗较大，功耗也较大。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Location.Location.Core
