# off (System API)

## Modules to Import

```TypeScript
import { wifi } from '@kit.ConnectivityKit';
```

## off('streamChange')

```TypeScript
function off(type: 'streamChange', callback?: Callback<number>): void
```

Unsubscribe Wi-Fi stream change events.

<p>All callback functions will be deregistered If there is no specific callback parameter.</p>

**Since:** 7

**Deprecated since:** 9

**Substitutes:** streamChange

**Required permissions:** ohos.permission.MANAGE_WIFI_CONNECTION

**System capability:** SystemCapability.Communication.WiFi.STA

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'streamChange' | Yes | event name. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;number&gt; | No | the callback of on, 1: stream down, 2: stream up, 3: stream bidirectional |


## off('hotspotStaJoin')

```TypeScript
function off(type: 'hotspotStaJoin', callback?: Callback<StationInfo>): void
```

Unsubscribe Wi-Fi hotspot sta join events.

<p>All callback functions will be deregistered If there is no specific callback parameter.</p>

**Since:** 7

**Deprecated since:** 9

**Substitutes:** hotspotStaJoin

**Required permissions:** ohos.permission.MANAGE_WIFI_HOTSPOT

**System capability:** SystemCapability.Communication.WiFi.AP.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'hotspotStaJoin' | Yes | event name. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[StationInfo](arkts-connectivity-wifi-stationinfo-i-sys.md)&gt; | No | the callback of on |


## off('hotspotStaLeave')

```TypeScript
function off(type: 'hotspotStaLeave', callback?: Callback<StationInfo>): void
```

Unsubscribe Wi-Fi hotspot sta leave events.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** hotspotStaLeave

**Required permissions:** ohos.permission.MANAGE_WIFI_HOTSPOT

**System capability:** SystemCapability.Communication.WiFi.AP.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'hotspotStaLeave' | Yes | event name. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[StationInfo](arkts-connectivity-wifi-stationinfo-i-sys.md)&gt; | No | the callback of on |
