# off

## 导入模块

```TypeScript
import { geoLocationManager } from '@kit.LocationKit';
```

## off('locationChange')

```TypeScript
function off(type: 'locationChange', callback?: Callback<Location>): void
```

关闭位置变化订阅，并删除对应的定位请求。

**起始版本：** 9

**需要权限：** 
- API版本25+：N/A
- API版本9-24：ohos.permission.APPROXIMATELY_LOCATION

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Location.Location.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'locationChange' | 是 | 设置事件类型。type为“locationChange”，表示位置变化。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[Location](arkts-location-geolocationmanager-location-i.md)&gt; | 否 | 需要取消订阅的回调函数。该回调函数需要与on接口传入的回调函数保持一致，否则会取消订阅失败且不会返回任何错误码。若无此参数，则取消当前类型的所有订阅。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed. The application does not have the permission required to call the API. Introduced in API 9 and will not be threw above API 24.<br>**适用版本：** 9 - 24 |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. Failed to call &#36;{geoLocationManager.off('locationChange')} due to limited device capabilities. |
| [3301000](../errorcode-geoLocationManager.md#3301000-位置服务不可用) | The location service is unavailable. |
| [3301100](../errorcode-geoLocationManager.md#3301100-位置功能的开关未开启导致功能失败) | The location switch is off. Introduced in API 9 and will not be threw above API 17.<br>**适用版本：** 9 - 17 |
| [3301200](../errorcode-geoLocationManager.md#3301200-定位失败未获取到定位结果) | Failed to obtain the geographical location. Introduced in API 9 and will not be threw above API 17.<br>**适用版本：** 9 - 17 |


## off('locationError')

```TypeScript
function off(type: 'locationError', callback?: Callback<LocationError>): void
```

取消订阅持续定位过程中的错误码。

**起始版本：** 12

**需要权限：** ohos.permission.APPROXIMATELY_LOCATION

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Location.Location.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'locationError' | 是 | 设置事件类型。type为“locationError”，表示持续定位过程中的错误码变化。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[LocationError](arkts-location-geolocationmanager-locationerror-e.md)&gt; | 否 | 需要取消订阅的回调函数。该回调函数需要与on接口传入的回调函数保持一致。若无此参数，则取消当前类型的所有订阅。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed. The application does not have the permission required to call the API. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. Failed to call &#36;{geoLocationManager.off('locationError')} due to limited device capabilities. |
| [3301000](../errorcode-geoLocationManager.md#3301000-位置服务不可用) | The location service is unavailable. |


## off('locationEnabledChange')

```TypeScript
function off(type: 'locationEnabledChange', callback?: Callback<boolean>): void
```

取消订阅位置服务状态变化。

**起始版本：** 9

**系统能力：** SystemCapability.Location.Location.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'locationEnabledChange' | 是 | 设置事件类型。type为“locationEnabledChange”，表示位置服务状态。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;boolean&gt; | 否 | 需要取消订阅的回调函数。返回true表示位置信息开关已经开启；返回false表示位置信息开关已经关闭。该回调函数需要与on接口传入的回调函数保持一致。若无此参数，则取消当前类型的所有订阅。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. Failed to call &#36;{geoLocationManager.off('locationEnabledChange')} due to limited device capabilities. |
| [3301000](../errorcode-geoLocationManager.md#3301000-位置服务不可用) | The location service is unavailable. |


## off('cachedGnssLocationsChange')

```TypeScript
function off(type: 'cachedGnssLocationsChange', callback?: Callback<Array<Location>>): void
```

取消订阅缓存GNSS定位结果上报事件。该接口功能由GNSS定位芯片提供（仅部分型号支持），如果设备无此芯片或使用的芯片型号不支持该功能，则返回错误码801（Capability not supported）。调用该接口前建议先通过[geoLocationManager.isCachedGnssServiceSupported](arkts-location-geolocationmanager-iscachedgnssservicesupported-f.md)接口判断对应能力是否支持。

**起始版本：** 9

**需要权限：** ohos.permission.APPROXIMATELY_LOCATION

**系统能力：** SystemCapability.Location.Location.Gnss

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'cachedGnssLocationsChange' | 是 | 设置事件类型。type为“cachedGnssLocationsChange”，表示GNSS缓存定位结果上报。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;Array&lt;[Location](arkts-location-geolocationmanager-location-i.md)&gt;&gt; | 否 | 需要取消订阅的回调函数。该回调函数需要与on接口传入的回调函数保持一致。若无此参数，则取消当前类型的所有订阅。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed. The application does not have the permission required to call the API. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. Failed to call &#36;{geoLocationManager.off('cachedGnssLocationsChange')} due to limited device capabilities. |
| [3301000](../errorcode-geoLocationManager.md#3301000-位置服务不可用) | The location service is unavailable. |
| [3301100](../errorcode-geoLocationManager.md#3301100-位置功能的开关未开启导致功能失败) | The location switch is off. |
| [3301200](../errorcode-geoLocationManager.md#3301200-定位失败未获取到定位结果) | Failed to obtain the geographical location.<br>**适用版本：** 9 - 17 |


## off('satelliteStatusChange')

```TypeScript
function off(type: 'satelliteStatusChange', callback?: Callback<SatelliteStatusInfo>): void
```

取消订阅GNSS卫星状态信息上报事件。调用该接口前建议先通过[geoLocationManager.isGnssServiceSupported](arkts-location-geolocationmanager-isgnssservicesupported-f.md)接口判断对应能力是否支持。

**起始版本：** 9

**需要权限：** ohos.permission.APPROXIMATELY_LOCATION

**系统能力：** SystemCapability.Location.Location.Gnss

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'satelliteStatusChange' | 是 | 设置事件类型。type为“satelliteStatusChange”，表示订阅GNSS卫星状态信息上报。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[SatelliteStatusInfo](arkts-location-geolocationmanager-satellitestatusinfo-i.md)&gt; | 否 | 需要取消订阅的回调函数。该回调函数需要与on接口传入的回调函数保持一致。若无此参数，则取消当前类型的所有订阅。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed. The application does not have the permission required to call the API. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. Failed to call &#36;{geoLocationManager.off('satelliteStatusChange')} due to limited device capabilities. |
| [3301000](../errorcode-geoLocationManager.md#3301000-位置服务不可用) | The location service is unavailable. |
| [3301100](../errorcode-geoLocationManager.md#3301100-位置功能的开关未开启导致功能失败) | The location switch is off. |


## off('nmeaMessage')

```TypeScript
function off(type: 'nmeaMessage', callback?: Callback<string>): void
```

取消订阅GNSS NMEA信息上报事件。调用该接口前建议先通过[geoLocationManager.isGnssServiceSupported](arkts-location-geolocationmanager-isgnssservicesupported-f.md)接口判断对应能力是否支持。

**起始版本：** 9

**需要权限：** ohos.permission.LOCATION and ohos.permission.APPROXIMATELY_LOCATION

**系统能力：** SystemCapability.Location.Location.Gnss

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'nmeaMessage' | 是 | 设置事件类型。type为“nmeaMessage”，表示订阅GNSS NMEA信息上报。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;string&gt; | 否 | 需要取消订阅的回调函数。该回调函数需要与on接口传入的回调函数保持一致。若无此参数，则取消当前类型的所有订阅。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed. The application does not have the permission required to call the API. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. Failed to call &#36;{geoLocationManager.off('nmeaMessage')} due to limited device capabilities. |
| [3301000](../errorcode-geoLocationManager.md#3301000-位置服务不可用) | The location service is unavailable. |
| [3301100](../errorcode-geoLocationManager.md#3301100-位置功能的开关未开启导致功能失败) | The location switch is off. |


## off('gnssFenceStatusChange')

```TypeScript
function off(type: 'gnssFenceStatusChange', request: GeofenceRequest, want: WantAgent): void
```

删除一个围栏，并取消订阅该围栏事件。该接口功能由GNSS定位芯片提供（仅部分型号支持），如果设备无此芯片或使用的芯片型号不支持该功能，则返回错误码801（Capability not supported）。调用该接口前建议先通过[geoLocationManager.isGnssFenceServiceSupported](arkts-location-geolocationmanager-isgnssfenceservicesupported-f.md)接口判断对应能力是否支持。

**起始版本：** 9

**需要权限：** 
- API版本25+：N/A
- API版本9-24：ohos.permission.APPROXIMATELY_LOCATION

**系统能力：** SystemCapability.Location.Location.Geofence

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'gnssFenceStatusChange' | 是 | 设置事件类型。type为“gnssFenceStatusChange”，表示订阅围栏事件上报。 |
| request | [GeofenceRequest](arkts-location-geolocationmanager-geofencerequest-i.md) | 是 | 围栏的配置参数。 |
| want | [WantAgent](../../apis-ability-kit/arkts-apis/arkts-ability-wantagent-depr-t.md) | 是 | 用于接收地理围栏事件上报（进出围栏）。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed. The application does not have the permission required to call the API.<br>**适用版本：** 9 - 24 |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. Failed to call &#36;{geoLocationManager.off('gnssFenceStatusChange')} due to limited device capabilities. |
| [3301000](../errorcode-geoLocationManager.md#3301000-位置服务不可用) | The location service is unavailable. |
| [3301100](../errorcode-geoLocationManager.md#3301100-位置功能的开关未开启导致功能失败) | The location switch is off. |
| [3301600](../errorcode-geoLocationManager.md#3301600-地理围栏操作失败) | Failed to operate the geofence. |


## off('countryCodeChange')

```TypeScript
function off(type: 'countryCodeChange', callback?: Callback<CountryCode>): void
```

取消订阅国家码变化事件。

**起始版本：** 9

**系统能力：** SystemCapability.Location.Location.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'countryCodeChange' | 是 | 设置事件类型。type为“countryCodeChange”，表示取消订阅国家码信息变化事件。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[CountryCode](arkts-location-geolocationmanager-countrycode-i.md)&gt; | 否 | 需要取消订阅的回调函数。该回调函数需要与on接口传入的回调函数保持一致。若无此参数，则取消当前类型的所有订阅。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. Failed to call &#36;{geoLocationManager.off('countryCodeChange')} due to limited device capabilities. |
| [3301000](../errorcode-geoLocationManager.md#3301000-位置服务不可用) | The location service is unavailable. |
| [3301500](../errorcode-geoLocationManager.md#3301500-区域信息包含国家码查询失败) | Failed to query the area information. |


## off('bluetoothScanResultChange')

```TypeScript
function off(type: 'bluetoothScanResultChange', callback?: Callback<BluetoothScanResult>): void
```

取消订阅蓝牙扫描信息上报事件并停止蓝牙扫描。

**起始版本：** 16

**需要权限：** ohos.permission.LOCATION and ohos.permission.APPROXIMATELY_LOCATION

**系统能力：** SystemCapability.Location.Location.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'bluetoothScanResultChange' | 是 | 设置事件类型。type为“bluetoothScanResultChange”，表示停止订阅蓝牙扫描信息上报事件。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[BluetoothScanResult](arkts-location-geolocationmanager-bluetoothscanresult-i.md)&gt; | 否 | 需要取消订阅的回调函数。该回调函数需要与on接口传入的回调函数保持一致。若无此参数，则取消当前类型的所有订阅。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed. The application does not have the permission required to call the API. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. Failed to call &#36;{geoLocationManager.off('bluetoothScanResultChange')} due to limited device capabilities. |
| [3301000](../errorcode-geoLocationManager.md#3301000-位置服务不可用) | The location service is unavailable. |
