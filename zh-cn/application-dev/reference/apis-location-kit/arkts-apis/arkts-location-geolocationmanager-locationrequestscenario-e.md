# LocationRequestScenario

位置请求中定位场景类型。

**起始版本：** 9

**系统能力：** SystemCapability.Location.Location.Core

## UNSET

```TypeScript
UNSET = 0x300
```

表示未设置场景信息。表示[LocationRequestScenario](#locationrequestscenario)字段无效。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Location.Location.Core

## NAVIGATION

```TypeScript
NAVIGATION = 0x301
```

表示导航场景。适用于在户外获取设备实时位置的场景，如车载、步行导航。主要使用GNSS定位技术提供定位服务，功耗较高。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Location.Location.Core

## TRAJECTORY_TRACKING

```TypeScript
TRAJECTORY_TRACKING = 0x302
```

表示运动轨迹记录场景。适用于记录用户位置轨迹的场景，如运动类应用记录轨迹功能。主要使用GNSS定位技术提供定位服务，功耗较高。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Location.Location.Core

## CAR_HAILING

```TypeScript
CAR_HAILING = 0x303
```

表示打车场景。适用于用户出行打车时定位当前位置的场景，如网约车类应用。主要使用GNSS定位技术提供定位服务，功耗较高。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Location.Location.Core

## DAILY_LIFE_SERVICE

```TypeScript
DAILY_LIFE_SERVICE = 0x304
```

表示日常服务使用场景。适用于不需要定位用户精确位置的使用场景，如新闻资讯、网购、点餐类应用。该场景仅使用网络定位技术提供定位服务，功耗较低。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Location.Location.Core

## NO_POWER

```TypeScript
NO_POWER = 0x305
```

表示无功耗功场景，这种场景下不会主动触发定位，会在其他应用定位时，才给当前应用返回位置。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Location.Location.Core
