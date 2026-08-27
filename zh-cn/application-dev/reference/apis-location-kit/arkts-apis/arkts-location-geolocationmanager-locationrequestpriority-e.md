# LocationRequestPriority

位置请求中位置信息优先级类型。

**起始版本：** 9

**系统能力：** SystemCapability.Location.Location.Core

## UNSET

```TypeScript
UNSET = 0x200
```

表示未设置优先级，表示[LocationRequestPriority](#locationrequestpriority)无效。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Location.Location.Core

## ACCURACY

```TypeScript
ACCURACY = 0x201
```

表示精度优先。定位精度优先策略主要以GNSS定位技术为主。我们会在GNSS提供稳定位置结果之前使用网络定位技术提供服务。在持续定位过程中，如果超过30秒无法获取GNSS定位结果则使用网络定位技术。对设备的硬件资源消耗较大，功耗较大。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Location.Location.Core

## LOW_POWER

```TypeScript
LOW_POWER = 0x202
```

表示低功耗优先。低功耗定位优先策略仅使用网络定位技术，在室内和户外场景均可提供定位服务，因为其依赖周边基站、可见WLAN、蓝牙设备的分布情况，定位结果的精度波动范围较大，推荐在对定位结果精度要求不高的场景下使用该策略，可以有效节省设备功耗。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Location.Location.Core

## FIRST_FIX

```TypeScript
FIRST_FIX = 0x203
```

表示快速获取位置优先，如果应用希望快速拿到一个位置，可以将优先级设置为该字段。快速定位优先策略会同时使用GNSS定位和网络定位技术，以便在室内和户外场景下均可以快速获取到位置结果；当各种定位技术都有提供位置结果时，系统会选择其中精度较好的结果返回给应用。因为对各种定位技术同时使用，对设备的硬件资源消耗较 大，功耗也较大。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Location.Location.Core
