# UserActivityScenario

位置请求中的用户活动场景类型。

**起始版本：** 12

**系统能力：** SystemCapability.Location.Location.Core

## NAVIGATION

```TypeScript
NAVIGATION = 0x401
```

表示导航场景。适用于在户外获取设备实时位置的场景，如车载、步行导航。主要使用GNSS定位技术提供定位服务，功耗较高。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Location.Location.Core

## SPORT

```TypeScript
SPORT = 0x402
```

表示运动场景。适用于记录用户位置轨迹的场景，如运动类应用记录轨迹功能。主要使用GNSS定位技术提供定位服务，功耗较高。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Location.Location.Core

## TRANSPORT

```TypeScript
TRANSPORT = 0x403
```

表示出行场景。适用于用户出行场景，如打车、乘坐公共交通等场景。主要使用GNSS定位技术提供定位服务，功耗较高。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Location.Location.Core

## DAILY_LIFE_SERVICE

```TypeScript
DAILY_LIFE_SERVICE = 0x404
```

表示日常服务使用场景。适用于不需要定位用户精确位置的使用场景，如新闻资讯、网购、点餐类应用。该场景仅使用网络定位技术提供定位服务，功耗较低。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Location.Location.Core
