# PowerConsumptionScenario

位置请求中的功耗场景类型。

**起始版本：** 12

**系统能力：** SystemCapability.Location.Location.Core

## HIGH_POWER_CONSUMPTION

```TypeScript
HIGH_POWER_CONSUMPTION = 0x601
```

高功耗。以GNSS定位技术为主。我们会在GNSS提供稳定位置结果之前使用网络定位技术提供服务；在持续定位时，如果超过30秒无法获取GNSS定位结果则会使用网络定位技术获取位置。对设备的硬件资源消耗较大，功耗较大。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Location.Location.Core

## LOW_POWER_CONSUMPTION

```TypeScript
LOW_POWER_CONSUMPTION = 0x602
```

低功耗。适用于对用户位置精度要求不高的使用场景，如新闻资讯、网购、点餐类应用。该场景仅使用网络定位技术提供定位服务，功耗较低。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Location.Location.Core

## NO_POWER_CONSUMPTION

```TypeScript
NO_POWER_CONSUMPTION = 0x603
```

无功耗。这种场景下不会主动触发定位，会在其他应用定位时，才给当前应用返回位置。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Location.Location.Core
