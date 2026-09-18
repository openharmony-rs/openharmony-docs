# on

## 导入模块

```TypeScript
import { geolocation } from '@kit.LocationKit';
```

## on('locationChange')

```TypeScript
function on(type: 'locationChange', request: LocationRequest, callback: Callback<Location>): void
```

开启位置变化订阅，并发起定位请求。使用callback异步回调。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** locationChange

**需要权限：** ohos.permission.LOCATION

**系统能力：** SystemCapability.Location.Location.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'locationChange' | 是 | 设置事件类型。type为“locationChange”，表示位置变化。 |
| request | [LocationRequest](arkts-location-geolocation-locationrequest-i.md) | 是 | 设置位置请求参数。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[Location](arkts-location-geolocation-location-i.md)&gt; | 是 | 回调函数，返回位置信息。 |


## on('locationServiceState')

```TypeScript
function on(type: 'locationServiceState', callback: Callback<boolean>): void
```

订阅位置服务状态变化。使用callback异步回调。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** locationEnabledChange

**需要权限：** ohos.permission.LOCATION

**系统能力：** SystemCapability.Location.Location.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'locationServiceState' | 是 | 设置事件类型。type为“locationServiceState”，表示位置服务状态。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;boolean&gt; | 是 | 回调函数。返回true表示打开位置服务；返回false表示关闭位置服务。 |


## on('cachedGnssLocationsReporting')

```TypeScript
function on(type: 'cachedGnssLocationsReporting', request: CachedGnssLocationsRequest, callback: Callback<Array<Location>>): void
```

订阅缓存GNSS定位结果上报事件。使用callback异步回调。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** cachedGnssLocationsChange

**需要权限：** ohos.permission.LOCATION

**系统能力：** SystemCapability.Location.Location.Gnss

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'cachedGnssLocationsReporting' | 是 | 设置事件类型。type为“cachedGnssLocationsReporting”，表示GNSS缓存定位结果上报。 |
| request | [CachedGnssLocationsRequest](arkts-location-geolocation-cachedgnsslocationsrequest-i.md) | 是 | GNSS缓存功能配置参数。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;Array&lt;[Location](arkts-location-geolocation-location-i.md)&gt;&gt; | 是 | 回调函数，返回GNSS缓存位置。 |


## on('gnssStatusChange')

```TypeScript
function on(type: 'gnssStatusChange', callback: Callback<SatelliteStatusInfo>): void
```

订阅GNSS卫星状态信息上报事件。使用callback异步回调。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** satelliteStatusChange

**需要权限：** ohos.permission.LOCATION

**系统能力：** SystemCapability.Location.Location.Gnss

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'gnssStatusChange' | 是 | 设置事件类型。type为“gnssStatusChange”，表示订阅GNSS卫星状态信息上报。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[SatelliteStatusInfo](arkts-location-geolocation-satellitestatusinfo-i.md)&gt; | 是 | 回调函数，返回GNSS卫星状态信息。 |


## on('nmeaMessageChange')

```TypeScript
function on(type: 'nmeaMessageChange', callback: Callback<string>): void
```

订阅GNSS NMEA信息上报事件。使用callback异步回调。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** nmeaMessage

**需要权限：** ohos.permission.LOCATION

**系统能力：** SystemCapability.Location.Location.Gnss

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'nmeaMessageChange' | 是 | 设置事件类型。type为“nmeaMessageChange”，表示订阅GNSS NMEA信息上报。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;string&gt; | 是 | 回调函数，返回GNSS NMEA信息。 |


## on('fenceStatusChange')

```TypeScript
function on(type: 'fenceStatusChange', request: GeofenceRequest, want: WantAgent): void
```

添加一个围栏，并订阅地理围栏事件。使用callback异步回调。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** gnssFenceStatusChange

**需要权限：** ohos.permission.LOCATION

**系统能力：** SystemCapability.Location.Location.Geofence

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'fenceStatusChange' | 是 | 设置事件类型。type为“fenceStatusChange”，表示订阅围栏事件上报。 |
| request | [GeofenceRequest](arkts-location-geolocation-geofencerequest-i.md) | 是 | 围栏的配置参数。 |
| want | [WantAgent](../../apis-ability-kit/arkts-apis/arkts-ability-wantagent-depr-t.md) | 是 | 用于接收地理围栏事件上报（进出围栏）。 |
