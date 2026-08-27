# LocationRequestScenario

位置请求中定位场景类型。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [LocationRequestScenario](arkts-location-geolocationmanager-locationrequestscenario-e.md)

**需要权限：** ohos.permission.LOCATION

**系统能力：** SystemCapability.Location.Location.Core

## UNSET

```TypeScript
UNSET = 0x300
```

表示未设置场景信息。 表示LocationRequestScenario字段无效。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [UNSET](arkts-location-geolocationmanager-locationrequestscenario-e.md#unset)

**系统能力：** SystemCapability.Location.Location.Core

## NAVIGATION

```TypeScript
NAVIGATION
```

表示导航场景。 适用于在户外定位设备实时位置的场景，如车载、步行导航。 在此场景下，为保证系统提供位置结果精度最优，主要使用GNSS定位技术提供定位服务。 此场景默认以最小1秒间隔上报定位结果。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [NAVIGATION](arkts-location-geolocationmanager-locationrequestscenario-e.md#navigation)

**系统能力：** SystemCapability.Location.Location.Core

## TRAJECTORY_TRACKING

```TypeScript
TRAJECTORY_TRACKING
```

表示运动轨迹记录场景。 适用于记录用户位置轨迹的场景，如运动类应用记录轨迹功能。主要使用GNSS定位技术提供定位服务。 此场景默认以最小1秒间隔上报定位结果。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [TRAJECTORY_TRACKING](arkts-location-geolocationmanager-locationrequestscenario-e.md#trajectory_tracking)

**系统能力：** SystemCapability.Location.Location.Core

## CAR_HAILING

```TypeScript
CAR_HAILING
```

表示打车场景。 适用于用户出行打车时定位当前位置的场景，如网约车类应用。 此场景默认以最小1秒间隔上报定位结果。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [CAR_HAILING](arkts-location-geolocationmanager-locationrequestscenario-e.md#car_hailing)

**系统能力：** SystemCapability.Location.Location.Core

## DAILY_LIFE_SERVICE

```TypeScript
DAILY_LIFE_SERVICE
```

表示日常服务使用场景。 适用于不需要定位用户精确位置的使用场景，如新闻资讯、网购、点餐类应用，做推荐、推送时定位用户大致位置即可。 此场景默认以最小1秒间隔上报定位结果。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [DAILY_LIFE_SERVICE](arkts-location-geolocationmanager-locationrequestscenario-e.md#daily_life_service)

**系统能力：** SystemCapability.Location.Location.Core

## NO_POWER

```TypeScript
NO_POWER
```

表示无功耗功场景，这种场景下不会主动触发定位，会在其他应用定位时，才给当前应用返回位置。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [NO_POWER](arkts-location-geolocationmanager-locationrequestscenario-e.md#no_power)

**系统能力：** SystemCapability.Location.Location.Core
