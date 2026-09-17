# @ohos.geoLocationManager(位置服务)

位置服务提供GNSS定位、网络定位（蜂窝基站、WLAN、蓝牙定位技术）、地理编码、逆地理编码、国家码和地理围栏等基本功能。

使用位置服务时请打开设备“位置”开关。如果“位置”开关关闭并且代码未设置捕获异常，可能导致应用异常。

**起始版本：** 9

**系统能力：** 
- API版本11+：SystemCapability.Location.Location.Core

## 导入模块

```TypeScript
import { geoLocationManager } from '@kit.LocationKit';
```

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [addBeaconFence](arkts-location-geolocationmanager-addbeaconfence-f.md) | 添加一个beacon围栏，并订阅地理围栏事件。使用Promise异步回调。beacon围栏是指通过蓝牙beacon设备和手机应用配合，实现“虚拟围栏”的功能。当用户靠近或离开某个特定的beacon设备时，手机应用会收到通知。应用可以在入参[BeaconFenceRequest](arkts-location-geolocationmanager-beaconfencerequest-i.md)中传入回调函数用于接收围栏事件；也可以传入[FenceExtensionAbility](arkts-location-app-ability-fenceextensionability-fenceextensionability-c.md)名称，在系统识别到围栏事件发生时通知应用。单应用添加beacon围栏上限为10，超过上限会导致添加beacon围栏失败，并抛出3501601错误码。 |
| [addGnssGeofence](arkts-location-geolocationmanager-addgnssgeofence-f.md) | 添加一个GNSS地理围栏，并订阅地理围栏事件。使用Promise异步回调。调用该接口前建议先通过[geoLocationManager.isGnssFenceServiceSupported](arkts-location-geolocationmanager-isgnssfenceservicesupported-f.md)接口判断对应能力是否支持。GNSS地理围栏功能依赖GNSS定位芯片（仅部分型号支持），如果设备无此芯片或使用的芯片型号不支持该功能，则返回错误码801（Capability not supported）。单应用添加地理围栏上限为100，超过上限将移除剩余地理围栏中存活时间最短的围栏。 |
| [findMatchingWlan](arkts-location-geolocationmanager-findmatchingwlan-f.md) | 使用WLAN扫描结果与输入的WLAN BSSID列表进行匹配，匹配成功时返回对应的WLAN设备信息，匹配失败时返回空数组(数组长度为0)。使用Promise异步回调。 |
| [flushCachedGnssLocations](arkts-location-geolocationmanager-flushcachedgnsslocations-f.md) | 读取并清空GNSS芯片所有缓存位置。该接口功能由GNSS定位芯片提供（仅部分型号支持），如果设备无此芯片或使用的芯片型号不支持该功能，则返回错误码801（Capability not supported）。使用callback异步回调。调用该接口前建议先通过[geoLocationManager.isCachedGnssServiceSupported](arkts-location-geolocationmanager-iscachedgnssservicesupported-f.md)接口判断对应能力是否支持。 |
| [flushCachedGnssLocations](arkts-location-geolocationmanager-flushcachedgnsslocations-f.md) | 读取并清空GNSS芯片所有缓存位置。该接口功能由GNSS定位芯片提供（仅部分型号支持），如果设备无此芯片或使用的芯片型号不支持该功能，则返回错误码801（Capability not supported）。使用Promise异步回调。调用该接口前建议先通过[geoLocationManager.isCachedGnssServiceSupported](arkts-location-geolocationmanager-iscachedgnssservicesupported-f.md)接口判断对应能力是否支持。 |
| [getActiveGeoFences](arkts-location-geolocationmanager-getactivegeofences-f.md) | 查询当前有效的围栏信息。使用Promise异步回调。调用该接口前建议先通过[geoLocationManager.isGnssFenceServiceSupported](arkts-location-geolocationmanager-isgnssfenceservicesupported-f.md)接口判断对应能力是否支持。 |
| [getAddressesFromLocation](arkts-location-geolocationmanager-getaddressesfromlocation-f.md) | 调用逆地理编码服务，将坐标转换为地理描述，使用callback异步回调。 |
| [getAddressesFromLocation](arkts-location-geolocationmanager-getaddressesfromlocation-f.md) | 调用逆地理编码服务，将坐标转换为地理描述，使用Promise异步回调。 |
| [getAddressesFromLocationName](arkts-location-geolocationmanager-getaddressesfromlocationname-f.md) | 调用地理编码服务，将地理描述转换为具体坐标，使用callback异步回调。 |
| [getAddressesFromLocationName](arkts-location-geolocationmanager-getaddressesfromlocationname-f.md) | 调用地理编码服务，将地理描述转换为具体坐标，使用Promise异步回调。 |
| [getCachedGnssLocationsSize](arkts-location-geolocationmanager-getcachedgnsslocationssize-f.md) | 获取GNSS芯片缓存位置的个数。该接口功能由GNSS定位芯片提供（仅部分型号支持），如果设备无此芯片或使用的芯片型号不支持该功能，则返回错误码801（Capability not supported）。使用callback异步回调。调用该接口前建议先通过[geoLocationManager.isCachedGnssServiceSupported](arkts-location-geolocationmanager-iscachedgnssservicesupported-f.md)接口判断对应能力是否支持。 |
| [getCachedGnssLocationsSize](arkts-location-geolocationmanager-getcachedgnsslocationssize-f.md) | 获取GNSS芯片缓存位置的个数。该接口功能由GNSS定位芯片提供（仅部分型号支持），如果设备无此芯片或使用的芯片型号不支持该功能，则返回错误码801（Capability not supported）。使用Promise异步回调。调用该接口前建议先通过[geoLocationManager.isCachedGnssServiceSupported](arkts-location-geolocationmanager-iscachedgnssservicesupported-f.md)接口判断对应能力是否支持。 |
| [getCountryCode](arkts-location-geolocationmanager-getcountrycode-f.md) | 查询当前的国家码。使用callback异步回调。 |
| [getCountryCode](arkts-location-geolocationmanager-getcountrycode-f.md) | 查询当前的国家码。使用Promise异步回调。 |
| [getCurrentDistrict](arkts-location-geolocationmanager-getcurrentdistrict-f.md) | 获取当前设备所在区域的信息。使用Promise异步回调。 |
| [getCurrentLocation](arkts-location-geolocationmanager-getcurrentlocation-f.md) | 获取当前位置，使用callback异步回调。 |
| [getCurrentLocation](arkts-location-geolocationmanager-getcurrentlocation-f.md) | 获取当前位置，使用callback异步回调。 |
| [getCurrentLocation](arkts-location-geolocationmanager-getcurrentlocation-f.md) | 获取当前位置，使用Promise异步回调。 |
| [getCurrentWifiBssidForLocating](arkts-location-geolocationmanager-getcurrentwifibssidforlocating-f.md) | 获取连接的Wi-Fi AP（Access Point）的Bssid（Basic Service Set Identifier）信息。如果当前设备未连接Wi-Fi，调用该接口将抛出错误码3301900。建议参考示例代码，通过try-catch结构捕获异常。 |
| [getDistanceBetweenLocations](arkts-location-geolocationmanager-getdistancebetweenlocations-f.md) | 获取两个位置之间的直线距离。 |
| [getGeofenceSupportedCoordTypes](arkts-location-geolocationmanager-getgeofencesupportedcoordtypes-f.md) | 获取地理围栏功能支持的坐标系列表。调用该接口前建议先通过[geoLocationManager.isGnssFenceServiceSupported](arkts-location-geolocationmanager-isgnssfenceservicesupported-f.md)接口判断对应能力是否支持。 |
| [getLastLocation](arkts-location-geolocationmanager-getlastlocation-f.md) | 获取上一次位置。 |
| [getPoiInfo](arkts-location-geolocationmanager-getpoiinfo-f.md) | 获取当前位置附近的POI信息。使用Promise异步回调。 |
| [getPostProcessingTrack](arkts-location-geolocationmanager-getpostprocessingtrack-f.md) | 根据传入的[sportsType](arkts-location-geolocationmanager-sportstype-e.md)获取特定运动模式下的后处理轨迹。在调用此接口之前，需要先调用geoLocationManager.on('locationChange')，并在[ContinuousLocationRequest](arkts-location-geolocationmanager-continuouslocationrequest-i.md)入参中的[SportsType](arkts-location-geolocationmanager-sportstype-e.md)配置正确的运动模式。当前仅支持滑雪模式。记录的运动轨迹会在24小时之后清除。 |
| [isBeaconFenceSupported](arkts-location-geolocationmanager-isbeaconfencesupported-f.md) | 判断当前设备是否支持beacon围栏。 |
| [isCachedGnssServiceSupported](arkts-location-geolocationmanager-iscachedgnssservicesupported-f.md) | 判断是否支持GNSS batching功能。 |
| [isGeocoderAvailable](arkts-location-geolocationmanager-isgeocoderavailable-f.md) | 判断地理编码与逆地理编码服务状态。 |
| [isGnssFenceServiceSupported](arkts-location-geolocationmanager-isgnssfenceservicesupported-f.md) | 判断是否支持围栏功能。 |
| [isGnssServiceSupported](arkts-location-geolocationmanager-isgnssservicesupported-f.md) | 判断是否支持GNSS功能。 |
| [isLocationEnabled](arkts-location-geolocationmanager-islocationenabled-f.md) | 判断位置服务是否已经开启。 |
| [isPoiServiceSupported](arkts-location-geolocationmanager-ispoiservicesupported-f.md) | 查询系统（即软件）是否支持POI服务。 |
| [isWlanBssidMatched](arkts-location-geolocationmanager-iswlanbssidmatched-f.md) | 判断指定的BSSID是否存在于最新的WLAN扫描结果里。使用Promise异步回调。 |
| [off](arkts-location-geolocationmanager-off-f.md#offlocationchange) | 关闭位置变化订阅，并删除对应的定位请求。 |
| [off](arkts-location-geolocationmanager-off-f.md#offlocationerror) | 取消订阅持续定位过程中的错误码。 |
| [off](arkts-location-geolocationmanager-off-f.md#offlocationenabledchange) | 取消订阅位置服务状态变化。 |
| [off](arkts-location-geolocationmanager-off-f.md#offcachedgnsslocationschange) | 取消订阅缓存GNSS定位结果上报事件。该接口功能由GNSS定位芯片提供（仅部分型号支持），如果设备无此芯片或使用的芯片型号不支持该功能，则返回错误码801（Capability not supported）。调用该接口前建议先通过[geoLocationManager.isCachedGnssServiceSupported](arkts-location-geolocationmanager-iscachedgnssservicesupported-f.md)接口判断对应能力是否支持。 |
| [off](arkts-location-geolocationmanager-off-f.md#offsatellitestatuschange) | 取消订阅GNSS卫星状态信息上报事件。调用该接口前建议先通过[geoLocationManager.isGnssServiceSupported](arkts-location-geolocationmanager-isgnssservicesupported-f.md)接口判断对应能力是否支持。 |
| [off](arkts-location-geolocationmanager-off-f.md#offnmeamessage) | 取消订阅GNSS NMEA信息上报事件。调用该接口前建议先通过[geoLocationManager.isGnssServiceSupported](arkts-location-geolocationmanager-isgnssservicesupported-f.md)接口判断对应能力是否支持。 |
| [off](arkts-location-geolocationmanager-off-f.md#offgnssfencestatuschange) | 删除一个围栏，并取消订阅该围栏事件。该接口功能由GNSS定位芯片提供（仅部分型号支持），如果设备无此芯片或使用的芯片型号不支持该功能，则返回错误码801（Capability not supported）。调用该接口前建议先通过[geoLocationManager.isGnssFenceServiceSupported](arkts-location-geolocationmanager-isgnssfenceservicesupported-f.md)接口判断对应能力是否支持。 |
| [off](arkts-location-geolocationmanager-off-f.md#offcountrycodechange) | 取消订阅国家码变化事件。 |
| [off](arkts-location-geolocationmanager-off-f.md#offbluetoothscanresultchange) | 取消订阅蓝牙扫描信息上报事件并停止蓝牙扫描。 |
| [offLocationChange](arkts-location-geolocationmanager-offlocationchange-f.md) | 关闭位置变化订阅，并删除对应的定位请求。 |
| [on](arkts-location-geolocationmanager-on-f.md#onlocationchange) | 开启位置变化订阅，并发起定位请求。使用callback异步回调。 |
| [on](arkts-location-geolocationmanager-on-f.md#onlocationerror) | 订阅持续定位过程中的错误码。使用callback异步回调。 |
| [on](arkts-location-geolocationmanager-on-f.md#onlocationenabledchange) | 订阅位置服务状态变化。使用callback异步回调。 |
| [on](arkts-location-geolocationmanager-on-f.md#oncachedgnsslocationschange) | 订阅缓存GNSS定位结果上报事件。该接口功能由GNSS定位芯片提供（仅部分型号支持），如果设备无此芯片或使用的芯片型号不支持该功能，则返回错误码801（Capability not supported）。使用callback异步回调。调用该接口前建议先通过[geoLocationManager.isCachedGnssServiceSupported](arkts-location-geolocationmanager-iscachedgnssservicesupported-f.md)接口判断对应能力是否支持。 |
| [on](arkts-location-geolocationmanager-on-f.md#onsatellitestatuschange) | 订阅GNSS卫星状态信息上报事件。使用callback异步回调。调用该接口前建议先通过[geoLocationManager.isGnssServiceSupported](arkts-location-geolocationmanager-isgnssservicesupported-f.md)接口判断对应能力是否支持。 |
| [on](arkts-location-geolocationmanager-on-f.md#onnmeamessage) | 订阅GNSS NMEA信息上报事件。使用callback异步回调。调用该接口前建议先通过[geoLocationManager.isGnssServiceSupported](arkts-location-geolocationmanager-isgnssservicesupported-f.md)接口判断对应能力是否支持。 |
| [on](arkts-location-geolocationmanager-on-f.md#ongnssfencestatuschange) | 添加一个围栏，并订阅地理围栏事件。该接口功能由GNSS定位芯片提供（仅部分型号支持），如果设备无此芯片或使用的芯片型号不支持该功能，则返回错误码801（Capability not supported）。调用该接口前建议先通过[geoLocationManager.isGnssFenceServiceSupported](arkts-location-geolocationmanager-isgnssfenceservicesupported-f.md)接口判断对应能力是否支持。单应用添加地理围栏上限为100，超过上限将移除剩余地理围栏中存活时间最短的围栏。 |
| [on](arkts-location-geolocationmanager-on-f.md#oncountrycodechange) | 订阅国家码信息变化事件。使用callback异步回调。 |
| [on](arkts-location-geolocationmanager-on-f.md#onbluetoothscanresultchange) | 订阅蓝牙扫描信息上报事件，使用callback异步回调。 |
| [onLocationChange](arkts-location-geolocationmanager-onlocationchange-f.md) | 开启位置变化订阅，并发起定位请求。使用callback异步回调。 |
| [removeBeaconFence](arkts-location-geolocationmanager-removebeaconfence-f.md) | 删除beacon围栏，并取消订阅地理围栏事件。使用Promise异步回调。 |
| [removeGnssGeofence](arkts-location-geolocationmanager-removegnssgeofence-f.md) | 删除一个GNSS地理围栏，并取消订阅该地理围栏事件。使用Promise异步回调。GNSS地理围栏功能依赖GNSS定位芯片（仅部分型号支持），如果设备无此芯片或使用的芯片型号不支持该功能，则返回错误码801（Capability not supported）。调用该接口前建议先通过[geoLocationManager.isGnssFenceServiceSupported](arkts-location-geolocationmanager-isgnssfenceservicesupported-f.md)接口判断对应能力是否支持。 |
| [sendCommand](arkts-location-geolocationmanager-sendcommand-f.md) | 给位置服务子系统的各个部件发送扩展命令。使用callback异步回调。 |
| [sendCommand](arkts-location-geolocationmanager-sendcommand-f.md) | 给位置服务子系统的各个部件发送扩展命令。使用Promise异步回调。 |
| [startBluetoothSearch](arkts-location-geolocationmanager-startbluetoothsearch-f.md) | 启动蓝牙扫描并查找指定的蓝牙设备，仅当扫描到的蓝牙设备满足入参BluetoothSearchRequestParams指定的条件时，才通过callback异步返回该蓝牙设备信息。 |
| [stopBluetoothSearch](arkts-location-geolocationmanager-stopbluetoothsearch-f.md) | 停止蓝牙扫描，该回调函数需要与startBluetoothSearch接口传入的回调函数保持一致。若无此参数，则取消当前类型的所有订阅。 |

<!--Del-->
### 函数（系统接口）

| 名称 | 说明 |
| --- | --- |
| [addFusionFence](arkts-location-geolocationmanager-addfusionfence-f-sys.md) | 添加一个融合围栏，并订阅围栏事件。使用Promise异步回调。 |
| [disableLocation](arkts-location-geolocationmanager-disablelocation-f-sys.md) | 关闭位置服务。 |
| [disableLocationByUserId](arkts-location-geolocationmanager-disablelocationbyuserid-f-sys.md) | 关闭指定系统账号的定位开关。 |
| [disableLocationMock](arkts-location-geolocationmanager-disablelocationmock-f-sys.md) | 去使能位置模拟功能。 |
| [disableReverseGeocodingMock](arkts-location-geolocationmanager-disablereversegeocodingmock-f-sys.md) | 去使能逆地理编码模拟功能。 |
| [enableLocation](arkts-location-geolocationmanager-enablelocation-f-sys.md) | 打开位置服务，使用callback异步回调。 |
| [enableLocation](arkts-location-geolocationmanager-enablelocation-f-sys.md) | 打开位置服务，使用Promise异步回调。 |
| [enableLocationByUserId](arkts-location-geolocationmanager-enablelocationbyuserid-f-sys.md) | 打开指定系统账号的定位开关，使用Promise异步回调。 |
| [enableLocationMock](arkts-location-geolocationmanager-enablelocationmock-f-sys.md) | 使能位置模拟功能。 |
| [enableReverseGeocodingMock](arkts-location-geolocationmanager-enablereversegeocodingmock-f-sys.md) | 使能逆地理编码模拟功能。 |
| [getLocatingRequiredData](arkts-location-geolocationmanager-getlocatingrequireddata-f-sys.md) | 单次获取定位业务所需数据，包含WiFi蓝牙扫描信息，使用Promise方式异步返回结果。 |
| [getLocationIconStatus](arkts-location-geolocationmanager-getlocationiconstatus-f-sys.md) | 获取当前的定位图标状态。 |
| [isFusionFenceSupported](arkts-location-geolocationmanager-isfusionfencesupported-f-sys.md) | 判断系统是否支持融合围栏能力。 |
| [isLocationEnabledByUserId](arkts-location-geolocationmanager-islocationenabledbyuserid-f-sys.md) | 判断指定系统账号的位置开关是否开启。 |
| [isLocationPrivacyConfirmed](arkts-location-geolocationmanager-islocationprivacyconfirmed-f-sys.md) | 查询用户是否同意定位服务隐私申明，是否同意启用定位服务。只有系统应用才能调用。 |
| [off](arkts-location-geolocationmanager-off-f-sys.md#offlocatingrequireddatachange) | 取消订阅定位业务所需数据的变化，并停止WiFi和蓝牙扫描。 |
| [off](arkts-location-geolocationmanager-off-f-sys.md#offlocationiconstatuschange) | 订阅定位图标状态变化。使用callback异步回调。 |
| [on](arkts-location-geolocationmanager-on-f-sys.md#onlocatingrequireddatachange) | 订阅定位业务所需数据的变化，主要包含WiFi和蓝牙扫描信息；根据入参决定是否启动WiFi和蓝牙扫描。使用callback异步回调。 |
| [on](arkts-location-geolocationmanager-on-f-sys.md#onlocationiconstatuschange) | 订阅定位图标状态变化。使用callback异步回调。 |
| [removeFusionFence](arkts-location-geolocationmanager-removefusionfence-f-sys.md) | 删除一个融合围栏，并取消订阅该围栏事件。使用Promise异步回调。 |
| [setLocationPrivacyConfirmStatus](arkts-location-geolocationmanager-setlocationprivacyconfirmstatus-f-sys.md) | 设置用户勾选定位服务隐私申明的状态，记录用户是否同意启用定位服务。只有系统应用才能调用。 |
| [setLocationSwitchIgnored](arkts-location-geolocationmanager-setlocationswitchignored-f-sys.md) | 设置应用获取位置信息是否受位置开关控制。设置为true后，允许应用在位置开关关闭的场景获取到位置信息，有效时间为从调用接口成功开始的两分钟。 |
| [setMockedLocations](arkts-location-geolocationmanager-setmockedlocations-f-sys.md) | 设置模拟的位置信息，后面会以该接口中携带的时间间隔上报模拟位置。 |
| [setReverseGeocodingMockInfo](arkts-location-geolocationmanager-setreversegeocodingmockinfo-f-sys.md) | 设置逆地理编码模拟功能的配置信息，包含了位置和地名的对应关系，后续进行逆地理编码查询时如果位置信息位于配置信息中，就返回对应的地名。该接口需要在调用geoLocationManager.enableReverseGeocodingMock之后才能调用。 |
<!--DelEnd-->

### 接口

| 名称 | 说明 |
| --- | --- |
| [BeaconFence](arkts-location-geolocationmanager-beaconfence-i.md) | beacon围栏的参数配置。 |
| [BeaconFenceRequest](arkts-location-geolocationmanager-beaconfencerequest-i.md) | beacon围栏请求参数。transitionCallback与fenceExtensionAbilityName任选其一，都不填则参数无效。 |
| [BeaconManufactureData](arkts-location-geolocationmanager-beaconmanufacturedata-i.md) | beacon设备制造商数据。 |
| [BluetoothScanResult](arkts-location-geolocationmanager-bluetoothscanresult-i.md) | 蓝牙扫描结果。 |
| [BluetoothSearchRequestParams](arkts-location-geolocationmanager-bluetoothsearchrequestparams-i.md) | 蓝牙扫描请求参数。 |
| [CachedGnssLocationsRequest](arkts-location-geolocationmanager-cachedgnsslocationsrequest-i.md) | 请求订阅GNSS缓存位置上报功能接口的配置参数。 |
| [ContinuousLocationRequest](arkts-location-geolocationmanager-continuouslocationrequest-i.md) | 持续定位的请求参数。 |
| [CountryCode](arkts-location-geolocationmanager-countrycode-i.md) | 国家码信息，包含国家码字符串和国家码的来源信息。 |
| [CurrentLocationRequest](arkts-location-geolocationmanager-currentlocationrequest-i.md) | 当前位置信息请求参数。 |
| [DistrictInfo](arkts-location-geolocationmanager-districtinfo-i.md) | 表示区域信息。 |
| [DistrictRequestParams](arkts-location-geolocationmanager-districtrequestparams-i.md) | 表示获取区县信息的请求参数。 |
| [GeoAddress](arkts-location-geolocationmanager-geoaddress-i.md) | 地理编码地址信息。 |
| [GeoCodeRequest](arkts-location-geolocationmanager-geocoderequest-i.md) | 地理编码请求参数。 |
| [Geofence](arkts-location-geolocationmanager-geofence-i.md) | GNSS围栏的配置参数。目前只支持圆形围栏。 |
| [GeofenceRequest](arkts-location-geolocationmanager-geofencerequest-i.md) | 请求添加GNSS围栏消息中携带的参数，包括定位场景和围栏信息。 |
| [GeofenceTransition](arkts-location-geolocationmanager-geofencetransition-i.md) | 地理围栏事件信息；包含地理围栏ID和具体的地理围栏事件。 |
| [GnssGeofenceRequest](arkts-location-geolocationmanager-gnssgeofencerequest-i.md) | GNSS地理围栏请求参数。 |
| [Location](arkts-location-geolocationmanager-location-i.md) | 位置信息。 |
| [LocationCommand](arkts-location-geolocationmanager-locationcommand-i.md) | 扩展命令参数。 |
| [LocationRequest](arkts-location-geolocationmanager-locationrequest-i.md) | 位置信息请求参数。 |
| [MatchingWlanInfo](arkts-location-geolocationmanager-matchingwlaninfo-i.md) | 匹配的WLAN信息结构体。 |
| [Poi](arkts-location-geolocationmanager-poi-i.md) | POI(Point of Interest, 兴趣点)信息。 |
| [PoiInfo](arkts-location-geolocationmanager-poiinfo-i.md) | POI信息结构体。 |
| [Point](arkts-location-geolocationmanager-point-i.md) | 表示一个位置点。 |
| [ReverseGeoCodeRequest](arkts-location-geolocationmanager-reversegeocoderequest-i.md) | 逆地理编码请求参数。 |
| [SatelliteStatusInfo](arkts-location-geolocationmanager-satellitestatusinfo-i.md) | 卫星状态信息。 |
| [SingleLocationRequest](arkts-location-geolocationmanager-singlelocationrequest-i.md) | 单次定位的请求参数。 |

<!--Del-->
### 接口（系统接口）

| 名称 | 说明 |
| --- | --- |
| [BluetoothScanInfo](arkts-location-geolocationmanager-bluetoothscaninfo-i-sys.md) | 蓝牙扫描信息。 |
| [CellFence](arkts-location-geolocationmanager-cellfence-i-sys.md) | CELL围栏信息。 |
| [CellInfo](arkts-location-geolocationmanager-cellinfo-i-sys.md) | 蜂窝小区信息。 |
| [FusionFenceRequestParams](arkts-location-geolocationmanager-fusionfencerequestparams-i-sys.md) | 融合围栏请求信息。 |
| [FusionFenceTransition](arkts-location-geolocationmanager-fusionfencetransition-i-sys.md) | 融合围栏回调事件信息。 |
| [GeoAddress](arkts-location-geolocationmanager-geoaddress-i-sys.md) | 地理编码地址信息。 |
| [GnssFence](arkts-location-geolocationmanager-gnssfence-i-sys.md) | GNSS围栏信息。 |
| [LocatingRequiredData](arkts-location-geolocationmanager-locatingrequireddata-i-sys.md) | 表示定位业务所需的数据，包含WiFi或蓝牙扫描结果，APP拿到这些数据之后可以用于网络定位等业务。 |
| [LocatingRequiredDataConfig](arkts-location-geolocationmanager-locatingrequireddataconfig-i-sys.md) | 订阅定位业务所需数据的变化，主要包含WiFi和蓝牙扫描信息；根据入参决定是否启动WiFi和蓝牙扫描。使用callback异步回调。 |
| [LocationMockConfig](arkts-location-geolocationmanager-locationmockconfig-i-sys.md) | 位置模拟功能的配置参数，包含了模拟位置上报的时间间隔和模拟位置数组。 |
| [ReverseGeocodingMockInfo](arkts-location-geolocationmanager-reversegeocodingmockinfo-i-sys.md) | 逆地理编码模拟功能的配置信息，包含一个位置信息和一个地名信息。 |
| [WifiFence](arkts-location-geolocationmanager-wififence-i-sys.md) | Wi-Fi围栏信息。 |
| [WifiScanInfo](arkts-location-geolocationmanager-wifiscaninfo-i-sys.md) | WiFi扫描信息，包含扫描到的WiFi热点的ssid、bssid和rssi等信息。 |
| [WirelessSignalFeature](arkts-location-geolocationmanager-wirelesssignalfeature-i-sys.md) | Wi-Fi指纹信息。 |
<!--DelEnd-->

### 枚举

| 名称 | 说明 |
| --- | --- |
| [BeaconFenceInfoType](arkts-location-geolocationmanager-beaconfenceinfotype-e.md) | beacon围栏信息类型。当前仅支持设备制造商数据过滤。 |
| [CoordinateSystemType](arkts-location-geolocationmanager-coordinatesystemtype-e.md) | 坐标系类型。 |
| [CountryCodeType](arkts-location-geolocationmanager-countrycodetype-e.md) | 国家码来源类型。 |
| [GeofenceTransitionEvent](arkts-location-geolocationmanager-geofencetransitionevent-e.md) | 地理围栏事件。 |
| [LocatingPriority](arkts-location-geolocationmanager-locatingpriority-e.md) | 单次位置请求中的优先级类型。 |
| [LocationError](arkts-location-geolocationmanager-locationerror-e.md) | 持续定位过程中的错误信息。 |
| [LocationRequestPriority](arkts-location-geolocationmanager-locationrequestpriority-e.md) | 位置请求中位置信息优先级类型。 |
| [LocationRequestScenario](arkts-location-geolocationmanager-locationrequestscenario-e.md) | 位置请求中定位场景类型。 |
| [LocationSourceType](arkts-location-geolocationmanager-locationsourcetype-e.md) | 定位结果的来源。 |
| [PowerConsumptionScenario](arkts-location-geolocationmanager-powerconsumptionscenario-e.md) | 位置请求中的功耗场景类型。 |
| [SatelliteAdditionalInfo](arkts-location-geolocationmanager-satelliteadditionalinfo-e.md) | 卫星附加信息类型。 |
| [SatelliteConstellationCategory](arkts-location-geolocationmanager-satelliteconstellationcategory-e.md) | 卫星星座类型。 |
| [SportsType](arkts-location-geolocationmanager-sportstype-e.md) | 运动类型。 |
| [UserActivityScenario](arkts-location-geolocationmanager-useractivityscenario-e.md) | 位置请求中的用户活动场景类型。 |

<!--Del-->
### 枚举（系统接口）

| 名称 | 说明 |
| --- | --- |
| [FusionFenceScene](arkts-location-geolocationmanager-fusionfencescene-e-sys.md) | 融合围栏场景。 |
| [FusionFenceType](arkts-location-geolocationmanager-fusionfencetype-e-sys.md) | 融合围栏类型采用二进制标记，该类型在使用时是将支持的围栏类型所在bit位置为1。例如支持GNSS和CELLULAR围栏，则值为0011（二进制），转换为十进制为3；全部四种围栏都支持，则值为1111（二进制），转换为十进制为15。 |
| [GeofenceTransitionEvent](arkts-location-geolocationmanager-geofencetransitionevent-e-sys.md) | 地理围栏事件。 |
| [GnssFenceType](arkts-location-geolocationmanager-gnssfencetype-e-sys.md) | GNSS围栏类型。 |
| [LocatingRequiredDataType](arkts-location-geolocationmanager-locatingrequireddatatype-e-sys.md) | 定位业务所需数据的类型。 |
| [LocationIconStatus](arkts-location-geolocationmanager-locationiconstatus-e-sys.md) | 定位图标状态。 |
| [LocationPrivacyType](arkts-location-geolocationmanager-locationprivacytype-e-sys.md) | 定位服务隐私协议类型。 |
| [WifiFingerprintType](arkts-location-geolocationmanager-wififingerprinttype-e-sys.md) | Wi-Fi指纹算法类型。 |
<!--DelEnd-->
