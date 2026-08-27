# @ohos.geolocation

位置服务提供GNSS定位、网络定位、地理编码、逆地理编码、国家码和地理围栏等基本功能。@namespace geolocation

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [geoLocationManager](arkts-geolocationmanager.md)

**需要权限：** ohos.permission.LOCATION

**系统能力：** SystemCapability.Location.Location.Core

## 导入模块

```TypeScript
import { geolocation } from '@kit.LocationKit';
```

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [flushCachedGnssLocations](arkts-location-geolocation-flushcachedgnsslocations-f.md) | 读取并清空GNSS芯片所有缓存位置。使用callback异步回调。 |
| [flushCachedGnssLocations](arkts-location-geolocation-flushcachedgnsslocations-f.md) | 读取并清空GNSS芯片所有缓存位置。使用Promise异步回调。 |
| [getAddressesFromLocation](arkts-location-geolocation-getaddressesfromlocation-f.md) | 调用逆地理编码服务，将坐标转换为地理描述，使用callback异步回调。 |
| [getAddressesFromLocation](arkts-location-geolocation-getaddressesfromlocation-f.md) | 调用逆地理编码服务，将坐标转换为地理描述，使用Promise异步回调。 |
| [getAddressesFromLocationName](arkts-location-geolocation-getaddressesfromlocationname-f.md) | 调用地理编码服务，将地理描述转换为具体坐标，使用callback异步回调。 |
| [getAddressesFromLocationName](arkts-location-geolocation-getaddressesfromlocationname-f.md) | 调用地理编码服务，将地理描述转换为具体坐标，使用Promise异步回调。 |
| [getCachedGnssLocationsSize](arkts-location-geolocation-getcachedgnsslocationssize-f.md) | 获取GNSS芯片缓存位置的个数。使用callback异步回调。 |
| [getCachedGnssLocationsSize](arkts-location-geolocation-getcachedgnsslocationssize-f.md) | 获取GNSS芯片缓存位置的个数。使用Promise异步回调。 |
| [getCurrentLocation](arkts-location-geolocation-getcurrentlocation-f.md) | 获取当前位置，使用callback异步回调。 |
| [getCurrentLocation](arkts-location-geolocation-getcurrentlocation-f.md) | 获取当前位置，使用callback异步回调。 |
| [getCurrentLocation](arkts-location-geolocation-getcurrentlocation-f.md) | 获取当前位置，使用Promise异步回调。 |
| [getLastLocation](arkts-location-geolocation-getlastlocation-f.md) | 获取上一次位置，使用callback异步回调。 |
| [getLastLocation](arkts-location-geolocation-getlastlocation-f.md) | 获取上一次位置，使用Promise异步回调。 |
| [isGeoServiceAvailable](arkts-location-geolocation-isgeoserviceavailable-f.md) | 判断（逆）地理编码服务状态，使用callback异步回调。 |
| [isGeoServiceAvailable](arkts-location-geolocation-isgeoserviceavailable-f.md) | 判断（逆）地理编码服务状态，使用Promise异步回调。 |
| [isLocationEnabled](arkts-location-geolocation-islocationenabled-f.md) | 判断位置服务是否已经打开，使用callback异步回调。 |
| [isLocationEnabled](arkts-location-geolocation-islocationenabled-f.md) | 判断位置服务是否已经开启，使用Promise异步回调。 |
| [off](arkts-location-geolocation-off-f.md#offlocationchange) | 关闭位置变化订阅，并删除对应的定位请求。 |
| [off](arkts-location-geolocation-off-f.md#offlocationservicestate) | 取消订阅位置服务状态变化。 |
| [off](arkts-location-geolocation-off-f.md#offcachedgnsslocationsreporting) | 取消订阅缓存GNSS定位结果上报事件。 |
| [off](arkts-location-geolocation-off-f.md#offgnssstatuschange) | 取消订阅GNSS卫星状态信息上报事件。 |
| [off](arkts-location-geolocation-off-f.md#offnmeamessagechange) | 取消订阅GNSS NMEA信息上报事件。 |
| [off](arkts-location-geolocation-off-f.md#offfencestatuschange) | 删除一个围栏，并取消订阅该围栏事件。 |
| [on](arkts-location-geolocation-on-f.md#onlocationchange) | 开启位置变化订阅，并发起定位请求。使用callback异步回调。 |
| [on](arkts-location-geolocation-on-f.md#onlocationservicestate) | 订阅位置服务状态变化。使用callback异步回调。 |
| [on](arkts-location-geolocation-on-f.md#oncachedgnsslocationsreporting) | 订阅缓存GNSS定位结果上报事件。使用callback异步回调。 |
| [on](arkts-location-geolocation-on-f.md#ongnssstatuschange) | 订阅GNSS卫星状态信息上报事件。使用callback异步回调。 |
| [on](arkts-location-geolocation-on-f.md#onnmeamessagechange) | 订阅GNSS NMEA信息上报事件。使用callback异步回调。 |
| [on](arkts-location-geolocation-on-f.md#onfencestatuschange) | 添加一个围栏，并订阅地理围栏事件。使用callback异步回调。 |
| [requestEnableLocation](arkts-location-geolocation-requestenablelocation-f.md) | 请求打开位置服务，使用callback异步回调。 |
| [requestEnableLocation](arkts-location-geolocation-requestenablelocation-f.md) | 请求打开位置服务，使用Promise异步回调。 |
| [sendCommand](arkts-location-geolocation-sendcommand-f.md) | 给位置服务子系统的各个部件发送扩展命令。使用callback异步回调。 |
| [sendCommand](arkts-location-geolocation-sendcommand-f.md) | 给位置服务子系统的各个部件发送扩展命令。使用Promise异步回调。 |

### 接口

| 名称 | 说明 |
| --- | --- |
| [CachedGnssLocationsRequest](arkts-location-geolocation-cachedgnsslocationsrequest-i.md) | 请求订阅GNSS缓存位置上报功能接口的配置参数。@interface CachedGnssLocationsRequest |
| [CurrentLocationRequest](arkts-location-geolocation-currentlocationrequest-i.md) | 当前位置信息请求参数。@interface CurrentLocationRequest |
| [GeoAddress](arkts-location-geolocation-geoaddress-i.md) | 地理编码地址信息。@interface GeoAddress |
| [GeoCodeRequest](arkts-location-geolocation-geocoderequest-i.md) | 地理编码请求参数。@interface GeoCodeRequest |
| [Geofence](arkts-location-geolocation-geofence-i.md) | GNSS围栏的配置参数。目前只支持圆形围栏。@interface Geofence |
| [GeofenceRequest](arkts-location-geolocation-geofencerequest-i.md) | 请求添加GNSS围栏消息中携带的参数，包括定位场景和围栏信息。@interface GeofenceRequest |
| [Location](arkts-location-geolocation-location-i.md) | 位置信息。@interface Location |
| [LocationCommand](arkts-location-geolocation-locationcommand-i.md) | 扩展命令参数。@interface LocationCommand |
| [LocationRequest](arkts-location-geolocation-locationrequest-i.md) | 位置信息请求参数。@interface LocationRequest |
| [ReverseGeoCodeRequest](arkts-location-geolocation-reversegeocoderequest-i.md) | 逆地理编码请求参数。@interface ReverseGeoCodeRequest |
| [SatelliteStatusInfo](arkts-location-geolocation-satellitestatusinfo-i.md) | 卫星状态信息。@interface SatelliteStatusInfo |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [GeoLocationErrorCode](arkts-location-geolocation-geolocationerrorcode-e.md) | 位置服务中的错误码信息。 |
| [LocationPrivacyType](arkts-location-geolocation-locationprivacytype-e.md) | 定位服务隐私协议类型。 |
| [LocationRequestPriority](arkts-location-geolocation-locationrequestpriority-e.md) | 位置请求中位置信息优先级类型。 |
| [LocationRequestScenario](arkts-location-geolocation-locationrequestscenario-e.md) | 位置请求中定位场景类型。 |
