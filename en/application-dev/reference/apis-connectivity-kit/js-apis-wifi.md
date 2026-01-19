# @ohos.wifi (WLAN)
<!--Kit: Connectivity Kit-->
<!--Subsystem: Communication-->
<!--Owner: @qq_43802146-->
<!--Designer: @qq_43802146-->
<!--Tester: @furryfurry123-->
<!--Adviser: @zhang_yixin13-->

The **WLAN** module provides basic wireless local area network (WLAN) functions, peer-to-peer (P2P) functions, and WLAN message notification services. It allows applications to communicate with other devices over WLAN.

> **NOTE**
>
> The initial APIs of this module are supported since API version 6. Newly added APIs will be marked with a superscript to indicate their earliest API version.
> The APIs of this module are no longer maintained since API version 9. You are advised to use [@ohos.wifiManager (WLAN)](js-apis-wifiManager.md).


## Modules to Import

```ts
import wifi from '@ohos.wifi';
```


## wifi.isWifiActive<sup>(deprecated)</sup>

isWifiActive(): boolean

Checks whether WLAN is enabled.

> **NOTE**
>
> This API is supported since API version 6 and deprecated since API version 9. You are advised to use [wifiManager.isWifiActive](js-apis-wifiManager.md#wifimanageriswifiactive) instead.

**Required permissions**: ohos.permission.GET_WIFI_INFO

**System capability**: SystemCapability.Communication.WiFi.STA

**Return value**

  | Type| Description|
  | -------- | -------- |
  | boolean | Returns **true** if WLAN is enabled; returns **false** otherwise.|

**Example**

```ts
import wifi from '@ohos.wifi';

try {
	let isWifiActive = wifi.isWifiActive();
	console.info("isWifiActive:" + isWifiActive);
}catch(error){
	console.error("failed:" + JSON.stringify(error));
}
```

## wifi.scan<sup>(deprecated)</sup>

scan(): boolean

Starts a scan for WLAN.

> **NOTE**
>
> This API is supported since API version 6 and deprecated since API version 9. You are advised to use [wifiManager.scan](js-apis-wifiManager.md#wifimanagerscandeprecated) instead.

**Required permissions**: **ohos.permission.SET_WIFI_INFO** and **ohos.permission.LOCATION**

**System capability**: SystemCapability.Communication.WiFi.STA

**Return value**

  | Type| Description|
  | -------- | -------- |
  | boolean | Returns **true** if the operation is successful; returns **false** otherwise.|

**Example**

```ts
import wifi from '@ohos.wifi';

try {
	wifi.scan();
}catch(error){
	console.error("failed:" + JSON.stringify(error));
}
```

## wifi.getScanInfos<sup>(deprecated)</sup>

getScanInfos(): Promise&lt;Array&lt;WifiScanInfo&gt;&gt;

Obtains the scan result. This API uses a promise to return the result.

> **NOTE**
>
> This API is supported since API version 6 and deprecated since API version 9. You are advised to use [wifiManager.getScanInfos](js-apis-wifiManager.md#wifimanagergetscaninfolist10) instead.

**Required permissions**: ohos.permission.GET_WIFI_INFO and ohos.permission.LOCATION or ohos.permission.GET_WIFI_PEERS_MAC (
available only for system applications)

**System capability**: SystemCapability.Communication.WiFi.STA

**Return value**

  | Type| Description|
  | -------- | -------- |
  | Promise&lt;&nbsp;Array&lt;[WifiScanInfo](#wifiscaninfodeprecated)&gt;&nbsp;&gt; | Promise used to return the detected hotspots.|


## wifi.getScanInfos<sup>(deprecated)</sup>

getScanInfos(callback: AsyncCallback&lt;Array&lt;WifiScanInfo&gt;&gt;): void

Obtains the scan result. This API uses an asynchronous callback to return the result.

> **NOTE**
>
> This API is supported since API version 6 and deprecated since API version 9. You are advised to use [wifiManager.getScanInfos](js-apis-wifiManager.md#wifimanagergetscaninfolist10) instead.

**Required permissions**: ohos.permission.GET_WIFI_INFO and ohos.permission.LOCATION or ohos.permission.GET_WIFI_PEERS_MAC (
available only for system applications)

**System capability**: SystemCapability.Communication.WiFi.STA

**Parameters**

  | Name| Type| Mandatory| Description|
  | -------- | -------- | -------- | -------- |
  | callback | AsyncCallback&lt;&nbsp;Array&lt;[WifiScanInfo](#wifiscaninfodeprecated)&gt;&gt; | Yes| Callback used to return the result. If the operation is successful, **err** is **0** and **data** is the detected hotspots. Otherwise, **err** is a non-zero value and **data** is empty.|

**Example**

```ts
import wifi from '@ohos.wifi';

wifi.getScanInfos().then(result => {
    let len = result.length;
    console.log("wifi received scan info: " + len);
    for (let i = 0; i < len; ++i) {
        console.info("ssid: " + result[i].ssid);
        console.info("bssid: " + result[i].bssid);
        console.info("capabilities: " + result[i].capabilities);
        console.info("securityType: " + result[i].securityType);
        console.info("rssi: " + result[i].rssi);
        console.info("band: " + result[i].band);
        console.info("frequency: " + result[i].frequency);
        console.info("channelWidth: " + result[i].channelWidth);
        console.info("timestamp: " + result[i].timestamp);
    }
});
```


## WifiScanInfo<sup>(deprecated)</sup>

Represents WLAN hotspot information.

> **NOTE**
>
> This API is supported since API version 6 and deprecated since API version 9. You are advised to use [WifiScanInfo](js-apis-wifiManager.md#wifiscaninfo) instead.

**System capability**: SystemCapability.Communication.WiFi.STA


| Name| Type| Read-Only| Optional| Description|
| -------- | -------- | -------- | -------- | -------- |
| ssid | string | No| No| Service set identifier (SSID) of the hotspot, in UTF-8 format. The maximum length is 32 bytes.|
| bssid | string | No| No| Basic service set identifier (BSSID) of the hotspot, for example, **00:11:22:33:44:55**.|
| capabilities | string | No| No| Hotspot capabilities.|
| securityType | [WifiSecurityType](#wifisecuritytypedeprecated) | No| No| WLAN security type.|
| rssi | number | No| No| Received signal strength indicator (RSSI) of the hotspot, in dBm.|
| band | number | No| No| Frequency band of the WLAN access point (AP). The value **1** indicates 2.4 GHz, and the value **2** indicates 5 GHz.|
| frequency | number | No| No| Frequency of the WLAN AP.|
| channelWidth | number | No| No| Channel width of the WLAN AP.|
| timestamp | number | No| No| Timestamp.|


## WifiSecurityType<sup>(deprecated)</sup>

Enumerates the WLAN security types.

> **NOTE**
>
> This API is supported since API version 6 and deprecated since API version 9. You are advised to use [WifiSecurityType](js-apis-wifiManager.md#wifisecuritytype) instead.

**System capability**: SystemCapability.Communication.WiFi.Core

| Name| Value| Description|
| -------- | -------- | -------- |
| WIFI_SEC_TYPE_INVALID | 0 | Invalid security type.|
| WIFI_SEC_TYPE_OPEN | 1 | Open security type.|
| WIFI_SEC_TYPE_WEP | 2 | Wired Equivalent Privacy (WEP).|
| WIFI_SEC_TYPE_PSK | 3 | Pre-shared key (PSK).|
| WIFI_SEC_TYPE_SAE | 4 | Simultaneous Authentication of Equals (SAE).|


## WifiDeviceConfig<sup>(deprecated)</sup>

Represents the WLAN configuration.

> **NOTE**
>
> This API is supported since API version 6 and deprecated since API version 9. You are advised to use [WifiDeviceConfig](js-apis-wifiManager.md#wifideviceconfig) instead.

**System capability**: SystemCapability.Communication.WiFi.STA

| Name| Type| Read-Only| Optional| Description|
| -------- | -------- | -------- | -------- | -------- |
| ssid | string | No| No| Service set identifier (SSID) of the hotspot, in UTF-8 format. The maximum length is 32 bytes.|
| bssid | string | No| No| BSSID of the hotspot, for example, **00:11:22:33:44:55**.|
| preSharedKey | string | No| No| PSK of the hotspot. The maximum length is 64 bytes.|
| isHiddenSsid | boolean | No| No| Whether the network is hidden. The value **true** indicates that the network is hidden, and the value **false** indicates the opposite.|
| securityType | [WifiSecurityType](#wifisecuritytypedeprecated) | No| No| Security type.|



## wifi.addUntrustedConfig<sup>(deprecated)</sup>

addUntrustedConfig(config: WifiDeviceConfig): Promise&lt;boolean&gt;

Adds the configuration of an untrusted network. This API uses a promise to return the result.

> **NOTE**
>
> This API is supported since API version 7 and deprecated since API version 9. You are advised to use [wifiManager.addCandidateConfig](js-apis-wifiManager.md#wifimanageraddcandidateconfig) instead.

**Required permissions**: ohos.permission.SET_WIFI_INFO

**System capability**: SystemCapability.Communication.WiFi.STA

**Parameters**

  | Name| Type| Mandatory| Description|
  | -------- | -------- | -------- | -------- |
  | config | [WifiDeviceConfig](#wifideviceconfigdeprecated) | Yes| WLAN configuration to add.|

**Return value**

  | Type| Description|
  | -------- | -------- |
  | Promise&lt;boolean&gt; | Promise used to return the result. The value **true** means the operation is successful; the value **false** means the opposite.|

**Example**
```ts
import wifi from '@ohos.wifi';

try {
	let config:wifi.WifiDeviceConfig = {
		ssid : "****",
		bssid:  "****",
		preSharedKey: "****",
		isHiddenSsid: false,
		securityType: 0,
		creatorUid: 0,
		disableReason: 0,
		netId: 0,
		randomMacType: 0,
		randomMacAddr:  "****",
		ipType: 0,
		staticIp: {
			ipAddress: 0,
			gateway: 0,
			dnsServers: [],
			domains: []
		}
	}
	wifi.addUntrustedConfig(config).then(result => {
		console.info("result:" + JSON.stringify(result));
	});	
}catch(error){
	console.error("failed:" + JSON.stringify(error));
}
```

## wifi.addUntrustedConfig<sup>(deprecated)</sup>

addUntrustedConfig(config: WifiDeviceConfig, callback: AsyncCallback&lt;boolean&gt;): void

Adds the configuration of an untrusted network. This API uses an asynchronous callback to return the result.

> **NOTE**
>
> This API is supported since API version 7 and deprecated since API version 9. You are advised to use [wifiManager.addCandidateConfig](js-apis-wifiManager.md#wifimanageraddcandidateconfig-1) instead.

**Required permissions**: ohos.permission.SET_WIFI_INFO

**System capability**: SystemCapability.Communication.WiFi.STA

**Parameters**

  | Name| Type| Mandatory| Description|
  | -------- | -------- | -------- | -------- |
  | config | [WifiDeviceConfig](#wifideviceconfigdeprecated) | Yes| WLAN configuration to add.|
  | callback | AsyncCallback&lt;boolean&gt; | Yes| Callback used to return the result. If the operation is successful, **err** is **0** and **data** is **true**. If the operation fails, **data** is **false**. If **err** is not **0**, an error has occurred.|

**Example**
```ts
import wifi from '@ohos.wifi';

try {
	let config:wifi.WifiDeviceConfig = {
		ssid : "****",
		bssid:  "****",
		preSharedKey: "****",
		isHiddenSsid: false,
		securityType: 0,
		creatorUid: 0,
		disableReason: 0,
		netId: 0,
		randomMacType: 0,
		randomMacAddr:  "****",
		ipType: 0,
		staticIp: {
			ipAddress: 0,
			gateway: 0,
			dnsServers: [],
			domains: []
		}
	}
	wifi.addUntrustedConfig(config,(error,result) => {
		console.info("result:" + JSON.stringify(result));
	});	
}catch(error){
	console.error("failed:" + JSON.stringify(error));
}
```

## wifi.removeUntrustedConfig<sup>(deprecated)</sup>

removeUntrustedConfig(config: WifiDeviceConfig): Promise&lt;boolean&gt;

Removes the configuration of an untrusted network. This API uses a promise to return the result.

> **NOTE**
>
> This API is supported since API version 7 and deprecated since API version 9. You are advised to use [wifiManager.removeCandidateConfig](js-apis-wifiManager.md#wifimanagerremovecandidateconfig) instead.

**Required permissions**: ohos.permission.SET_WIFI_INFO

**System capability**: SystemCapability.Communication.WiFi.STA

**Parameters**

  | Name| Type| Mandatory| Description|
  | -------- | -------- | -------- | -------- |
  | config | [WifiDeviceConfig](#wifideviceconfigdeprecated) | Yes| WLAN configuration to remove.|

**Return value**

  | Type| Description|
  | -------- | -------- |
  | Promise&lt;boolean&gt; | Promise used to return the result. The value **true** means the operation is successful; the value **false** means the opposite.|

**Example**

```ts
import wifi from '@ohos.wifi';

try {
	let config:wifi.WifiDeviceConfig = {
		ssid : "****",
		bssid:  "****",
		preSharedKey: "****",
		isHiddenSsid: false,
		securityType: 0,
		creatorUid: 0,
		disableReason: 0,
		netId: 0,
		randomMacType: 0,
		randomMacAddr:  "****",
		ipType: 0,
		staticIp: {
			ipAddress: 0,
			gateway: 0,
			dnsServers: [],
			domains: []
		}
	}
	wifi.removeUntrustedConfig(config).then(result => {
		console.info("result:" + JSON.stringify(result));
	});	
}catch(error){
	console.error("failed:" + JSON.stringify(error));
}
```


## wifi.removeUntrustedConfig<sup>(deprecated)</sup>

removeUntrustedConfig(config: WifiDeviceConfig, callback: AsyncCallback&lt;boolean&gt;): void

Removes the configuration of an untrusted network. This API uses an asynchronous callback to return the result.

> **NOTE**
>
> This API is supported since API version 7 and deprecated since API version 9. You are advised to use [wifiManager.removeCandidateConfig](js-apis-wifiManager.md#wifimanagerremovecandidateconfig-1) instead.

**Required permissions**: ohos.permission.SET_WIFI_INFO

**System capability**: SystemCapability.Communication.WiFi.STA

**Parameters**

  | Name| Type| Mandatory| Description|
  | -------- | -------- | -------- | -------- |
  | config | [WifiDeviceConfig](#wifideviceconfigdeprecated) | Yes| WLAN configuration to remove.|
  | callback | AsyncCallback&lt;boolean&gt; | Yes| Callback used to return the result. If the operation is successful, **err** is **0** and **data** is **true**. If the operation fails, **data** is **false**. If **err** is not **0**, an error has occurred.|

**Example**
```ts
import wifi from '@ohos.wifi';

try {
	let config:wifi.WifiDeviceConfig = {
		ssid : "****",
		bssid:  "****",
		preSharedKey: "****",
		isHiddenSsid: false,
		securityType: 0,
		creatorUid: 0,
		disableReason: 0,
		netId: 0,
		randomMacType: 0,
		randomMacAddr:  "****",
		ipType: 0,
		staticIp: {
			ipAddress: 0,
			gateway: 0,
			dnsServers: [],
			domains: []
		}
	}
	wifi.removeUntrustedConfig(config,(error,result) => {
	console.info("result:" + JSON.stringify(result));
	});	
}catch(error){
	console.error("failed:" + JSON.stringify(error));
}
```

## wifi.getSignalLevel<sup>(deprecated)</sup>

getSignalLevel(rssi: number, band: number): number

Obtains the WLAN signal level.

> **NOTE**
>
> This API is supported since API version 6 and deprecated since API version 9. You are advised to use [wifiManager.getSignalLevel](js-apis-wifiManager.md#wifimanagergetsignallevel) instead.

**Required permissions**: ohos.permission.GET_WIFI_INFO

**System capability**: SystemCapability.Communication.WiFi.STA

**Parameters**

  | Name| Type| Mandatory| Description|
  | -------- | -------- | -------- | -------- |
  | rssi | number | Yes| RSSI of the hotspot, in dBm.|
  | band | number | Yes| Frequency band of the WLAN AP.|

**Return value**

  | Type| Description|
  | -------- | -------- |
  | number | Signal level obtained. The value range is [0, 4].|

**Example**
```ts
import wifi from '@ohos.wifi';

try {
	let rssi = 0;
	let band = 0;
	let level = wifi.getSignalLevel(rssi,band);
	console.info("level:" + JSON.stringify(level));
}catch(error){
	console.error("failed:" + JSON.stringify(error));
}

```

## wifi.getLinkedInfo<sup>(deprecated)</sup>

getLinkedInfo(): Promise&lt;WifiLinkedInfo&gt;

Obtains information about the WLAN connection. This API uses a promise to return the result.

> **NOTE**
>
> This API is supported since API version 6 and deprecated since API version 9. You are advised to use [wifiManager.getLinkedInfo](js-apis-wifiManager.md#wifimanagergetlinkedinfo) instead.

**Required permissions**: ohos.permission.GET_WIFI_INFO

**System capability**: SystemCapability.Communication.WiFi.STA

**Return value**

  | Type| Description|
  | -------- | -------- |
  | Promise&lt;[WifiLinkedInfo](#wifilinkedinfodeprecated)&gt; | Promise used to return the WLAN connection information.|


## wifi.getLinkedInfo<sup>(deprecated)</sup>

getLinkedInfo(callback: AsyncCallback&lt;WifiLinkedInfo&gt;): void

Obtains information about the WLAN connection. This API uses an asynchronous callback to return the result.

> **NOTE**
>
> This API is supported since API version 6 and deprecated since API version 9. You are advised to use [wifiManager.getLinkedInfo](js-apis-wifiManager.md#wifimanagergetlinkedinfo-1) instead.

**Required permissions**: ohos.permission.GET_WIFI_INFO

**System capability**: SystemCapability.Communication.WiFi.STA

**Parameters**

  | Name| Type| Mandatory| Description|
  | -------- | -------- | -------- | -------- |
  | callback | AsyncCallback&lt;[WifiLinkedInfo](#wifilinkedinfodeprecated)&gt; | Yes| Callback used to return the result. If the operation is successful, **err** is **0** and **data** is the WLAN connection information obtained. If **err** is not **0**, an error has occurred.|

**Example**
```ts
import wifi from '@ohos.wifi';

wifi.getLinkedInfo((err, data:wifi.WifiLinkedInfo) => {
    if (err) {
        console.error("get linked info error");
        return;
    }
    console.info("get wifi linked info: " + JSON.stringify(data));
});

wifi.getLinkedInfo().then(data => {
    console.info("get wifi linked info: " + JSON.stringify(data));
}).catch((error:number) => {
    console.info("get linked info error");
});
```


## WifiLinkedInfo<sup>(deprecated)</sup>

Represents the WLAN connection information.

> **NOTE**
>
> This API is supported since API version 6 and deprecated since API version 9. You are advised to use [WifiLinkedInfo](js-apis-wifiManager.md#wifilinkedinfo) instead.

**System capability**: SystemCapability.Communication.WiFi.STA

| Name| Type| Read-Only| Optional| Description|
| -------- | -------- | -------- | -------- | -------- |
| ssid | string | No| No| Service set identifier (SSID) of the hotspot, in UTF-8 format. The maximum length is 32 bytes.|
| bssid | string | No| No| BSSID of the hotspot, for example, **00:11:22:33:44:55**.|
| rssi | number | No| No| RSSI of the hotspot, in dBm.|
| band | number | No| No| Frequency band of the WLAN access point (AP). The value **1** indicates 2.4 GHz, and the value **2** indicates 5 GHz.|
| linkSpeed | number | No| No| Speed of the WLAN AP, in Mbit/s.|
| frequency | number | No| No| Frequency of the WLAN AP.|
| isHidden | boolean | No| No| Whether to hide the WLAN AP. The value **true** indicates that the network is hidden, and the value **false** indicates the opposite.|
| isRestricted | boolean | No| No| Whether to restrict data volume at the WLAN AP. The value **true** means to restrict data volume at the WLAN AP, and the value **false** indicates the opposite.|
| macAddress | string | No| No| MAC address of the device.|
| ipAddress | number | No| No| IP address of the device that sets up the WLAN connection.|
| connState | [ConnState](#connstatedeprecated) | No| No| WLAN connection state.|


## ConnState<sup>(deprecated)</sup>

Enumerates the WLAN connection states.

> **NOTE**
>
> This API is supported since API version 6 and deprecated since API version 9. You are advised to use [WifiLinkedInfo](js-apis-wifiManager.md#connstate) instead.

**System capability**: SystemCapability.Communication.WiFi.STA

| Name| Value| Description|
| -------- | -------- | -------- |
| SCANNING | 0 | The device is scanning for available APs.|
| CONNECTING | 1 | A WLAN connection is being established.|
| AUTHENTICATING | 2 | An authentication is being performed for a WLAN connection.|
| OBTAINING_IPADDR | 3 | The IP address of the WLAN connection is being acquired.|
| CONNECTED | 4 | A WLAN connection is established.|
| DISCONNECTING | 5 | The WLAN connection is being disconnected.|
| DISCONNECTED | 6 | The WLAN connection is disconnected.|
| UNKNOWN | 7 | Failed to set up the WLAN connection.|


## wifi.isConnected<sup>(deprecated)</sup>

isConnected(): boolean

Checks whether the WLAN is connected.

> **NOTE**
>
> This API is supported since API version 7 and deprecated since API version 9. You are advised to use [wifiManager.isConnected](js-apis-wifiManager.md#wifimanagerisconnected) instead.

**Required permissions**: ohos.permission.GET_WIFI_INFO

**System capability**: SystemCapability.Communication.WiFi.STA

**Return value**

  | Type| Description|
  | -------- | -------- |
  | boolean | Returns **true** if the WLAN is connected; returns **false** otherwise.|


## wifi.isFeatureSupported<sup>(deprecated)</sup>

isFeatureSupported(featureId: number): boolean

Checks whether the device supports the specified WLAN feature.

> **NOTE**
>
> This API is supported since API version 7 and deprecated since API version 9. You are advised to use [wifiManager.isFeatureSupported](js-apis-wifiManager.md#wifimanagerisfeaturesupported) instead.

**Required permissions**: ohos.permission.GET_WIFI_INFO

**System capability**: SystemCapability.Communication.WiFi.Core

**Parameters**


  | Name| Type| Mandatory| Description|
  | -------- | -------- | -------- | -------- |
  | featureId | number | Yes| Feature ID.|

**Return value**

  | Type| Description|
  | -------- | -------- |
  | boolean | Returns **true** if the feature is supported; returns **false** otherwise.|

**Example**
```ts
import wifi from '@ohos.wifi';

try {
	let featureId = 0;
	let ret = wifi.isFeatureSupported(featureId);
	console.info("isFeatureSupported:" + ret);
}catch(error){
	console.error("failed:" + JSON.stringify(error));
}

```


## wifi.getIpInfo<sup>(deprecated)</sup>

getIpInfo(): IpInfo

Obtains IP information.

> **NOTE**
>
> This API is supported since API version 7 and deprecated since API version 9. You are advised to use [wifiManager.getIpInfo](js-apis-wifiManager.md#wifimanagergetipinfo) instead.

**Required permissions**: ohos.permission.GET_WIFI_INFO

**System capability**: SystemCapability.Communication.WiFi.STA

**Return value**

  | Type| Description|
  | -------- | -------- |
  | [IpInfo](#ipinfodeprecated) | IP information obtained.|

**Example**
```ts
import wifi from '@ohos.wifi';

try {
	let info = wifi.getIpInfo();
	console.info("info:" + JSON.stringify(info));
}catch(error){
	console.error("failed:" + JSON.stringify(error));
}
```

## IpInfo<sup>(deprecated)</sup>

IP information obtained.

> **NOTE**
>
> This API is supported since API version 7 and deprecated since API version 9. You are advised to use [wifiManager.getIpInfo](js-apis-wifiManager.md#wifimanagergetipinfo) instead.

**System capability**: SystemCapability.Communication.WiFi.AP.Core

| Name| Type| Read-Only| Optional| Description|
| -------- | -------- | -------- | -------- | -------- |
| ipAddress | number | No| No| IP address.|
| gateway | number | No| No| Gateway.|
| netmask | number | No| No| Subnet mask.|
| primaryDns | number | No| No| IP address of the preferred DNS server.|
| secondDns | number | No| No| IP address of the alternate DNS server.|
| serverIp | number | No| No| IP address of the DHCP server.|
| leaseDuration | number | No| No| Lease duration of the IP address.|


## wifi.getCountryCode<sup>(deprecated)</sup>

getCountryCode(): string

Obtains the country code.

> **NOTE**
>
> This API is supported since API version 7 and deprecated since API version 9. You are advised to use [wifiManager.getCountryCode](js-apis-wifiManager.md#wifimanagergetcountrycode) instead.

**Required permissions**: ohos.permission.GET_WIFI_INFO

**System capability**: SystemCapability.Communication.WiFi.Core

**Return value**

  | Type| Description|
  | -------- | -------- |
  | string | Country code obtained.|

**Example**
```ts
import wifi from '@ohos.wifi';

try {
	let code = wifi.getCountryCode();
	console.info("code:" + code);
}catch(error){
	console.error("failed:" + JSON.stringify(error));
}
```


## wifi.getP2pLinkedInfo<sup>(deprecated)</sup>

getP2pLinkedInfo(): Promise&lt;WifiP2pLinkedInfo&gt;

Obtains P2P connection information. This API uses a promise to return the result.

> **NOTE**
>
> This API is supported since API version 8 and deprecated since API version 9. You are advised to use [wifiManager.getP2pLinkedInfo](js-apis-wifiManager.md#wifimanagergetp2plinkedinfo) instead.

**Required permissions**: ohos.permission.GET_WIFI_INFO

**System capability**: SystemCapability.Communication.WiFi.P2P

**Return value**

  | Type| Description|
  | -------- | -------- |
  | Promise&lt;[WifiP2pLinkedInfo](#wifip2plinkedinfodeprecated)&gt; | Promise used to return the P2P link information.|



## WifiP2pLinkedInfo<sup>(deprecated)</sup>

Represents the WLAN connection information.

> **NOTE**
>
> This API is supported since API version 8 and deprecated since API version 9. You are advised to use [WifiP2pLinkedInfo](js-apis-wifiManager.md#wifip2plinkedinfo) instead.

**System capability**: SystemCapability.Communication.WiFi.P2P

| Name| Type| Read-Only| Optional| Description|
| -------- | -------- | -------- | -------- | -------- |
| connectState | [P2pConnectState](#p2pconnectstatedeprecated) | No| No| P2P connection state.|
| isGroupOwner | boolean | No| No| Whether the device is the group owner. The value **true** indicates that the device is the group owner, and the value **false** indicates the opposite.|
| groupOwnerAddr | string | No| No| MAC address of the group.|


## P2pConnectState<sup>(deprecated)</sup>

Enumerates the P2P connection states.

> **NOTE**
>
> This API is supported since API version 8 and deprecated since API version 9. You are advised to use [P2pConnectState](js-apis-wifiManager.md#p2pconnectstate) instead.

**System capability**: SystemCapability.Communication.WiFi.P2P

| Name| Value| Description|
| -------- | -------- | -------- |
| DISCONNECTED | 0 | Disconnected.|
| CONNECTED | 1 | Connected.|


## wifi.getP2pLinkedInfo<sup>(deprecated)</sup>

getP2pLinkedInfo(callback: AsyncCallback&lt;WifiP2pLinkedInfo&gt;): void

Obtains P2P connection information. This API uses an asynchronous callback to return the result.

> **NOTE**
>
> This API is supported since API version 8 and deprecated since API version 9. You are advised to use [wifiManager.getP2pLinkedInfo](js-apis-wifiManager.md#wifimanagergetp2plinkedinfo-1) instead.

**Required permissions**: ohos.permission.GET_WIFI_INFO

**System capability**: SystemCapability.Communication.WiFi.P2P

**Parameters**

  | Name| Type| Mandatory| Description|
  | -------- | -------- | -------- | -------- |
  | callback | AsyncCallback&lt;[WifiP2pLinkedInfo](#wifip2plinkedinfodeprecated)&gt; | Yes| Callback used to return the result. If the operation is successful, **err** is **0** and **data** is the P2P link information. If **err** is not **0**, an error has occurred.|

**Example**
```ts
import wifi from '@ohos.wifi';

wifi.getP2pLinkedInfo((err, data:wifi.WifiP2pLinkedInfo) => {
   if (err) {
       console.error("get p2p linked info error");
       return;
   }
	console.info("get wifi p2p linked info: " + JSON.stringify(data));
});

wifi.getP2pLinkedInfo().then(data => {
	console.info("get wifi p2p linked info: " + JSON.stringify(data));
});
```

## wifi.getCurrentGroup<sup>(deprecated)</sup>

getCurrentGroup(): Promise&lt;WifiP2pGroupInfo&gt;

Obtains the current P2P group information. This API uses a promise to return the result.

> **NOTE**
>
> This API is supported since API version 8 and deprecated since API version 9. You are advised to use [wifiManager.getCurrentGroup](js-apis-wifiManager.md#wifimanagergetcurrentgroup) instead.

**Required permissions**: ohos.permission.GET_WIFI_INFO and ohos.permission.LOCATION

**System capability**: SystemCapability.Communication.WiFi.P2P

**Return value**

  | Type| Description|
  | -------- | -------- |
  | Promise&lt;[WifiP2pGroupInfo](#wifip2pgroupinfodeprecated)&gt; | Promise used to return the P2P group information obtained.|


## wifi.getCurrentGroup<sup>(deprecated)</sup>

getCurrentGroup(callback: AsyncCallback&lt;WifiP2pGroupInfo&gt;): void

Obtains the current P2P group information. This API uses an asynchronous callback to return the result.

> **NOTE**
>
> This API is supported since API version 8 and deprecated since API version 9. You are advised to use [wifiManager.getCurrentGroup](js-apis-wifiManager.md#wifimanagergetcurrentgroup-1) instead.

**Required permissions**: ohos.permission.GET_WIFI_INFO and ohos.permission.LOCATION

**System capability**: SystemCapability.Communication.WiFi.P2P

**Parameters**

  | Name| Type| Mandatory| Description|
  | -------- | -------- | -------- | -------- |
  | callback | AsyncCallback&lt;[WifiP2pGroupInfo](#wifip2pgroupinfodeprecated)&gt; | Yes| Callback used to return the result. If the operation is successful, **err** is **0** and **data** is the group information obtained. If **err** is not **0**, an error has occurred.|

**Example**
```ts
import wifi from '@ohos.wifi';

wifi.getCurrentGroup((err, data:wifi.WifiP2pGroupInfo) => {
   if (err) {
       console.error("get current P2P group error");
       return;
   }
	console.info("get current P2P group: " + JSON.stringify(data));
});

wifi.getCurrentGroup().then(data => {
	console.info("get current P2P group: " + JSON.stringify(data));
});
```

## wifi.getP2pPeerDevices<sup>(deprecated)</sup>

getP2pPeerDevices(): Promise&lt;WifiP2pDevice[]&gt;

Obtains the P2P peer device list. This API uses a promise to return the result.

> **NOTE**
>
> This API is supported since API version 8 and deprecated since API version 9. You are advised to use [wifiManager.getP2pPeerDevices](js-apis-wifiManager.md#wifimanagergetp2ppeerdevices) instead.

**Required permissions**: ohos.permission.GET_WIFI_INFO and ohos.permission.LOCATION

**System capability**: SystemCapability.Communication.WiFi.P2P

**Return value**

  | Type| Description|
  | -------- | -------- |
  | Promise&lt;[WifiP2pDevice[]](#wifip2pdevicedeprecated)&gt; | Promise used to return the peer device list.|


## wifi.getP2pPeerDevices<sup>(deprecated)</sup>

getP2pPeerDevices(callback: AsyncCallback&lt;WifiP2pDevice[]&gt;): void

Obtains the P2P peer device list. This API uses an asynchronous callback to return the result.

> **NOTE**
>
> This API is supported since API version 8 and deprecated since API version 9. You are advised to use [wifiManager.getP2pPeerDevices](js-apis-wifiManager.md#wifimanagergetp2ppeerdevices-1) instead.

**Required permissions**: ohos.permission.GET_WIFI_INFO and ohos.permission.LOCATION

**System capability**: SystemCapability.Communication.WiFi.P2P

**Parameters**

  | Name| Type| Mandatory| Description|
  | -------- | -------- | -------- | -------- |
  | callback | AsyncCallback&lt;[WifiP2pDevice[]](#wifip2pdevicedeprecated)&gt; | Yes| Callback used to return the result. If the operation is successful, **err** is **0** and **data** is the peer device list obtained. If **err** is not **0**, an error has occurred.|

**Example**
```ts
import wifi from '@ohos.wifi';

wifi.getP2pPeerDevices((err, data:wifi.WifiP2pDevice) => {
   if (err) {
       console.error("get P2P peer devices error");
       return;
   }
	console.info("get P2P peer devices: " + JSON.stringify(data));
});

wifi.getP2pPeerDevices().then(data => {
	console.info("get P2P peer devices: " + JSON.stringify(data));
});
```

## WifiP2pDevice<sup>(deprecated)</sup>

Represents the P2P device information.

> **NOTE**
>
> This API is supported since API version 8 and deprecated since API version 9. You are advised to use [WifiP2pDevice](js-apis-wifiManager.md#wifip2pdevice) instead.

**System capability**: SystemCapability.Communication.WiFi.P2P

| Name| Type| Read-Only| Optional| Description|
| -------- | -------- | -------- | -------- | -------- |
| deviceName | string | No| No| Device name.|
| deviceAddress | string | No| No| MAC address of the device.|
| primaryDeviceType | string | No| No| Type of the primary device.|
| deviceStatus | [P2pDeviceStatus](#p2pdevicestatusdeprecated) | No| No| Device status.|
| groupCapabilitys | number | No| No| Group capabilities.|


## P2pDeviceStatus<sup>(deprecated)</sup>

Enumerates the P2P device states.

> **NOTE**
>
> This API is supported since API version 8 and deprecated since API version 9. You are advised to use [P2pDeviceStatus](js-apis-wifiManager.md#p2pdevicestatus) instead.

**System capability**: SystemCapability.Communication.WiFi.P2P

| Name| Value| Description|
| -------- | -------- | -------- |
| CONNECTED | 0 | Connected.|
| INVITED | 1 | Invited.|
| FAILED | 2 | Failed.|
| AVAILABLE | 3 | Available.|
| UNAVAILABLE | 4 | Unavailable.|


## wifi.createGroup<sup>(deprecated)</sup>

createGroup(config: WifiP2PConfig): boolean

Creates a P2P group.

> **NOTE**
>
> This API is supported since API version 8 and deprecated since API version 9. You are advised to use [wifiManager.createGroup](js-apis-wifiManager.md#wifimanagercreategroup) instead.

**Required permissions**: ohos.permission.GET_WIFI_INFO

**System capability**: SystemCapability.Communication.WiFi.P2P

**Parameters**

  | Name| Type| Mandatory| Description|
  | -------- | -------- | -------- | -------- |
  | config | [WifiP2PConfig](#wifip2pconfigdeprecated) | Yes| Group configuration.|

**Return value**

  | Type| Description|
  | -------- | -------- |
  | boolean | Returns **true** if the operation is successful; returns **false** otherwise.|

**Example**
```ts
import wifi from '@ohos.wifi';

try {
	let config:wifi.WifiP2PConfig = {
		deviceAddress: "****",
		netId: 0,
		passphrase: "*****",
		groupName: "****",
		goBand: 0
	}
	wifi.createGroup(config);	
	
}catch(error){
	console.error("failed:" + JSON.stringify(error));
}
```

## WifiP2PConfig<sup>(deprecated)</sup>

Represents P2P group configuration.

> **NOTE**
>
> This API is supported since API version 8 and deprecated since API version 9. You are advised to use [WifiP2PConfig](js-apis-wifiManager.md#wifip2pconfig) instead.

**System capability**: SystemCapability.Communication.WiFi.P2P

| Name| Type| Read-Only| Optional| Description|
| -------- | -------- | -------- | -------- | -------- |
| deviceAddress | string | No| No| Device address.|
| netId | number | No| No| Network ID. The value **-1** indicates a temporary group, and **-2** indicates a persistent group.|
| passphrase | string | No| No| Passphrase of the group.|
| groupName | string | No| No| Group name.|
| goBand | [GroupOwnerBand](#groupownerbanddeprecated) | No| No| Frequency band of the group.|


## GroupOwnerBand<sup>(deprecated)</sup>

Enumerates the P2P group frequency bands.

> **NOTE**
>
> This API is supported since API version 8 and deprecated since API version 9. You are advised to use [GroupOwnerBand](js-apis-wifiManager.md#groupownerband) instead.

**System capability**: SystemCapability.Communication.WiFi.P2P

| Name| Value| Description|
| -------- | -------- | -------- |
| GO_BAND_AUTO | 0 | Auto.|
| GO_BAND_2GHZ | 1 | 2 GHz.|
| GO_BAND_5GHZ | 2 | 5 GHz.|


## wifi.removeGroup<sup>(deprecated)</sup>

removeGroup(): boolean

Removes this P2P group.

> **NOTE**
>
> This API is supported since API version 8 and deprecated since API version 9. You are advised to use [wifiManager.removeGroup](js-apis-wifiManager.md#wifimanagerremovegroup) instead.

**Required permissions**: ohos.permission.GET_WIFI_INFO

**System capability**: SystemCapability.Communication.WiFi.P2P

**Return value**

  | Type| Description|
  | -------- | -------- |
  | boolean | Returns **true** if the operation is successful; returns **false** otherwise.|

**Example**
```ts
import wifi from '@ohos.wifi';

try {
	wifi.removeGroup();	
}catch(error){
	console.error("failed:" + JSON.stringify(error));
}
```

## wifi.p2pConnect<sup>(deprecated)</sup>

p2pConnect(config: WifiP2PConfig): boolean

Sets up a P2P connection.

> **NOTE**
>
> This API is supported since API version 8 and deprecated since API version 9. You are advised to use [wifiManager.p2pConnect](js-apis-wifiManager.md#wifimanagerp2pconnect) instead.

**Required permissions**: ohos.permission.GET_WIFI_INFO and ohos.permission.LOCATION

**System capability**: SystemCapability.Communication.WiFi.P2P

**Parameters**


  | Name| Type| Mandatory| Description|
  | -------- | -------- | -------- | -------- |
  | config | [WifiP2PConfig](#wifip2pconfigdeprecated) | Yes| P2P group configuration.|

**Return value**

  | Type| Description|
  | -------- | -------- |
  | boolean | Returns **true** if the operation is successful; returns **false** otherwise.|


**Example**
```ts
import wifi from '@ohos.wifi';

let recvP2pConnectionChangeFunc = (result:wifi.WifiP2pLinkedInfo) => {
    console.info("p2p connection change receive event: " + JSON.stringify(result));
    wifi.getP2pLinkedInfo((err, data:wifi.WifiP2pLinkedInfo) => {
        if (err) {
            console.error('failed to get getP2pLinkedInfo: ' + JSON.stringify(err));
            return;
        }
        console.info("get getP2pLinkedInfo: " + JSON.stringify(data));
    });
}
wifi.on("p2pConnectionChange", recvP2pConnectionChangeFunc);

let recvP2pDeviceChangeFunc = (result:wifi.WifiP2pDevice) => {
    console.info("p2p device change receive event: " + JSON.stringify(result));
}
wifi.on("p2pDeviceChange", recvP2pDeviceChangeFunc);

let recvP2pPeerDeviceChangeFunc = (result:wifi.WifiP2pDevice[]) => {
    console.info("p2p peer device change receive event: " + JSON.stringify(result));
    wifi.getP2pPeerDevices((err, data:wifi.WifiP2pDevice[]) => {
        if (err) {
            console.error('failed to get peer devices: ' + JSON.stringify(err));
            return;
        }
        console.info("get peer devices: " + JSON.stringify(data));
        let len = data.length;
        for (let i = 0; i < len; ++i) {
            if (data[i].deviceName === "my_test_device") {
                console.info("p2p connect to test device: " + data[i].deviceAddress);
                let config:wifi.WifiP2PConfig = {
                    deviceAddress:data[i].deviceAddress,
                    netId:-2,
                    passphrase:"",
                    groupName:"",
                    goBand:0,
                }
                wifi.p2pConnect(config);
            }
        }
    });
}
wifi.on("p2pPeerDeviceChange", recvP2pPeerDeviceChangeFunc);

let recvP2pPersistentGroupChangeFunc = () => {
    console.info("p2p persistent group change receive event");

    wifi.getCurrentGroup((err, data:wifi.WifiP2pGroupInfo) => {
        if (err) {
            console.error('failed to get current group: ' + JSON.stringify(err));
            return;
        }
        console.info("get current group: " + JSON.stringify(data));
    });
}
wifi.on("p2pPersistentGroupChange", recvP2pPersistentGroupChangeFunc);

setTimeout(() => {wifi.off("p2pConnectionChange", recvP2pConnectionChangeFunc);}, 125 * 1000);
setTimeout(() => {wifi.off("p2pDeviceChange", recvP2pDeviceChangeFunc);}, 125 * 1000);
setTimeout(() => {wifi.off("p2pPeerDeviceChange", recvP2pPeerDeviceChangeFunc);}, 125 * 1000);
setTimeout(() => {wifi.off("p2pPersistentGroupChange", recvP2pPersistentGroupChangeFunc);}, 125 * 1000);
console.info("start discover devices -> " + wifi.startDiscoverDevices());
```

## wifi.p2pCancelConnect<sup>(deprecated)</sup>

p2pCancelConnect(): boolean

Cancels this P2P connection.

> **NOTE**
>
> This API is supported since API version 8 and deprecated since API version 9. You are advised to use [wifiManager.p2pCancelConnect](js-apis-wifiManager.md#wifimanagerp2pcancelconnect) instead.

**Required permissions**: ohos.permission.GET_WIFI_INFO

**System capability**: SystemCapability.Communication.WiFi.P2P

**Return value**

  | Type| Description|
  | -------- | -------- |
  | boolean | Returns **true** if the operation is successful; returns **false** otherwise.|

**Example**
```ts
import wifi from '@ohos.wifi';

try {
	wifi.p2pCancelConnect();	
}catch(error){
	console.error("failed:" + JSON.stringify(error));
}
```

## wifi.startDiscoverDevices<sup>(deprecated)</sup>

startDiscoverDevices(): boolean

Starts to discover devices.

> **NOTE**
>
> This API is supported since API version 8 and deprecated since API version 9. You are advised to use [wifiManager.startDiscoverDevices](js-apis-wifiManager.md#wifimanagerstartdiscoverdevices) instead.

**Required permissions**: ohos.permission.GET_WIFI_INFO and ohos.permission.LOCATION

**System capability**: SystemCapability.Communication.WiFi.P2P

**Return value**

  | Type| Description|
  | -------- | -------- |
  | boolean | Returns **true** if the operation is successful; returns **false** otherwise.|

**Example**
```ts
import wifi from '@ohos.wifi';

try {
	wifi.startDiscoverDevices();	
}catch(error){
	console.error("failed:" + JSON.stringify(error));
}
```

## wifi.stopDiscoverDevices<sup>(deprecated)</sup>

stopDiscoverDevices(): boolean

Stops discovering devices.

> **NOTE**
>
> This API is supported since API version 8 and deprecated since API version 9. You are advised to use [wifiManager.stopDiscoverDevices](js-apis-wifiManager.md#wifimanagerstopdiscoverdevices) instead.

**Required permissions**: ohos.permission.GET_WIFI_INFO

**System capability**: SystemCapability.Communication.WiFi.P2P

**Return value**

  | Type| Description|
  | -------- | -------- |
  | boolean | **true** if the operation is successful; **false** otherwise.|

**Example**
```ts
import wifi from '@ohos.wifi';

try {
	wifi.stopDiscoverDevices();	
}catch(error){
	console.error("failed:" + JSON.stringify(error));
}
```

## WifiP2pGroupInfo<sup>(deprecated)</sup>

Represents the P2P group information.

> **NOTE**
>
> This API is supported since API version 8 and deprecated since API version 9. You are advised to use [WifiP2pGroupInfo](js-apis-wifiManager.md#wifip2pgroupinfo) instead.

**System capability**: SystemCapability.Communication.WiFi.P2P

| Name| Type| Read-Only| Optional| Description|
| -------- | -------- | -------- | -------- | -------- |
| isP2pGo | boolean | No| No| Whether the device is the group owner. The value **true** indicates that the device is the group owner, and the value **false** indicates the opposite.|
| ownerInfo | [WifiP2pDevice](#wifip2pdevicedeprecated) | No| No| Device information of the group.|
| passphrase | string | No| No| Passphrase of the group.|
| interface | string | No| No| Interface name.|
| groupName | string | No| No| Group name.|
| networkId | number | No| No| Network ID.|
| frequency | number | No| No| Frequency of the group.|
| clientDevices | [WifiP2pDevice[]](#wifip2pdevicedeprecated) | No| No| List of connected devices.|
| goIpAddress | string | No| No| IP address of the group.|



## wifi.on('wifiStateChange')<sup>(deprecated)</sup>

on(type: 'wifiStateChange', callback: Callback&lt;number&gt;): void

Subscribes to WLAN state changes.

> **NOTE**
>
> This API is supported since API version 7 and deprecated since API version 9. You are advised to use [wifiManager.on](js-apis-wifiManager.md#wifimanageronwifistatechange) instead.

**Required permissions**: ohos.permission.GET_WIFI_INFO

**System capability**: SystemCapability.Communication.WiFi.STA

**Parameters**

  | Name| Type| Mandatory| Description|
  | -------- | -------- | -------- | -------- |
  | type | string | Yes| Event type, which has a fixed value of **wifiStateChange**.|
  | callback | Callback&lt;number&gt; | Yes| Callback used to return the WLAN state.|

**WLAN states** 

| Value| Description|
| -------- | -------- |
| 0 | Deactivated|
| 1 | Activated|
| 2 | Activating|
| 3 | Deactivating|


## wifi.off('wifiStateChange')<sup>(deprecated)</sup>

off(type: 'wifiStateChange', callback?: Callback&lt;number&gt;): void

Unsubscribes from WLAN state changes.

> **NOTE**
>
> This API is supported since API version 7 and deprecated since API version 9. You are advised to use [wifiManager.off](js-apis-wifiManager.md#wifimanageroffwifistatechange) instead.

**Required permissions**: ohos.permission.GET_WIFI_INFO

**System capability**: SystemCapability.Communication.WiFi.STA

**Parameters**

  | Name| Type| Mandatory| Description|
  | -------- | -------- | -------- | -------- |
  | type | string | Yes| Event type, which has a fixed value of **wifiStateChange**.|
  | callback | Callback&lt;number&gt; | No| Callback to unregister. If this parameter is not specified, all callbacks for the specified event will be unregistered.|

**Example**
```ts
import wifi from '@ohos.wifi';

let recvPowerNotifyFunc = (result:number) => {
    console.info("Receive power state change event: " + result);
}

// Register an event.
wifi.on("wifiStateChange", recvPowerNotifyFunc);

// Unregister an event.
wifi.off("wifiStateChange", recvPowerNotifyFunc);
```


## wifi.on('wifiConnectionChange')<sup>(deprecated)</sup>

on(type: 'wifiConnectionChange', callback: Callback&lt;number&gt;): void

Subscribes to WLAN connection state changes.

> **NOTE**
>
> This API is supported since API version 7 and deprecated since API version 9. You are advised to use [wifiManager.on](js-apis-wifiManager.md#wifimanageronwificonnectionchange) instead.

**Required permissions**: ohos.permission.GET_WIFI_INFO

**System capability**: SystemCapability.Communication.WiFi.STA

**Parameters**

  | Name| Type| Mandatory| Description|
  | -------- | -------- | -------- | -------- |
  | type | string | Yes| Event type, which has a fixed value of **wifiConnectionChange**.|
  | callback | Callback&lt;number&gt; | Yes| Callback used to return the WLAN connection state.|

**WLAN connection states**

| Value| Description|
| -------- | -------- |
| 0 | Disconnected.|
| 1 | Connected.|


## wifi.off('wifiConnectionChange')<sup>(deprecated)</sup>

off(type: 'wifiConnectionChange', callback?: Callback&lt;number&gt;): void

Unsubscribes from WLAN connection state changes.

> **NOTE**
>
> This API is supported since API version 7 and deprecated since API version 9. You are advised to use [wifiManager.off](js-apis-wifiManager.md#wifimanageroffwificonnectionchange) instead.

**Required permissions**: ohos.permission.GET_WIFI_INFO

**System capability**: SystemCapability.Communication.WiFi.STA

**Parameters**

  | Name| Type| Mandatory| Description|
  | -------- | -------- | -------- | -------- |
  | type | string | Yes| Event type, which has a fixed value of **wifiConnectionChange**.|
  | callback | Callback&lt;number&gt; | No| Callback to unregister. If this parameter is not specified, all callbacks for the specified event will be unregistered.|

**Example**
```ts
import wifi from '@ohos.wifi';

let recvWifiConnectionChangeFunc = (result:number) => {
    console.info("Receive wifi connection change event: " + result);
}

// Register an event.
wifi.on("wifiConnectionChange", recvWifiConnectionChangeFunc);

// Unregister an event.
wifi.off("wifiConnectionChange", recvWifiConnectionChangeFunc);
```

## wifi.on('wifiScanStateChange')<sup>(deprecated)</sup>

on(type: 'wifiScanStateChange', callback: Callback&lt;number&gt;): void

Subscribes to WLAN scan state changes.

> **NOTE**
>
> This API is supported since API version 7 and deprecated since API version 9. You are advised to use [wifiManager.on](js-apis-wifiManager.md#wifimanageronwifiscanstatechange) instead.

**Required permissions**: ohos.permission.GET_WIFI_INFO

**System capability**: SystemCapability.Communication.WiFi.STA

**Parameters**

  | Name| Type| Mandatory| Description|
  | -------- | -------- | -------- | -------- |
  | type | string | Yes| Event type, which has a fixed value of **wifiScanStateChange**.|
  | callback | Callback&lt;number&gt; | Yes| Callback used to return the WLAN scan state.|

**WLAN scan states**

| Value| Description|
| -------- | -------- |
| 0 | Scan failed.|
| 1 | Scan successful.|


## wifi.off('wifiScanStateChange')<sup>(deprecated)</sup>

off(type: 'wifiScanStateChange', callback?: Callback&lt;number&gt;): void

Unsubscribes from WLAN scan state changes.

> **NOTE**
>
> This API is supported since API version 7 and deprecated since API version 9. You are advised to use [wifiManager.off](js-apis-wifiManager.md#wifimanageroffwifiscanstatechange) instead.

**Required permissions**: ohos.permission.GET_WIFI_INFO

**System capability**: SystemCapability.Communication.WiFi.STA

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| type | string | Yes| Event type, which has a fixed value of **wifiScanStateChange**.|
| callback | Callback&lt;number&gt; | No| Callback to unregister. If this parameter is not specified, all callbacks for the specified event will be unregistered.|

**Example**
```ts
import wifi from '@ohos.wifi';

let recvWifiScanStateChangeFunc = (result:number) => {
    console.info("Receive Wifi scan state change event: " + result);
}

// Register an event.
wifi.on("wifiScanStateChange", recvWifiScanStateChangeFunc);

// Unregister an event.
wifi.off("wifiScanStateChange", recvWifiScanStateChangeFunc);
```

## wifi.on('wifiRssiChange')<sup>(deprecated)</sup>

on(type: 'wifiRssiChange', callback: Callback&lt;number&gt;): void

Subscribes to RSSI changes.

> **NOTE**
>
> This API is supported since API version 7 and deprecated since API version 9. You are advised to use [wifiManager.on](js-apis-wifiManager.md#wifimanageronwifirssichange) instead.

**Required permissions**: ohos.permission.GET_WIFI_INFO

**System capability**: SystemCapability.Communication.WiFi.STA

**Parameters**

  | Name| Type| Mandatory| Description|
  | -------- | -------- | -------- | -------- |
  | type | string | Yes| Event type, which has a fixed value of **wifiRssiChange**.|
  | callback | Callback&lt;number&gt; | Yes| Callback used to return the RSSI, in dBm.|


## wifi.off('wifiRssiChange')<sup>(deprecated)</sup>

off(type: 'wifiRssiChange', callback?: Callback&lt;number&gt;): void

Unsubscribes from RSSI changes.

> **NOTE**
>
> This API is supported since API version 7 and deprecated since API version 9. You are advised to use [wifiManager.off](js-apis-wifiManager.md#wifimanageroffwifirssichange) instead.

**Required permissions**: ohos.permission.GET_WIFI_INFO

**System capability**: SystemCapability.Communication.WiFi.STA

**Parameters**

  | Name| Type| Mandatory| Description|
  | -------- | -------- | -------- | -------- |
  | type | string | Yes| Event type, which has a fixed value of **wifiRssiChange**.|
  | callback | Callback&lt;number&gt; | No| Callback to unregister. If this parameter is not specified, all callbacks for the specified event will be unregistered.|

**Example**
```ts
import wifi from '@ohos.wifi';

let recvWifiRssiChangeFunc = (result:number) => {
    console.info("Receive wifi rssi change event: " + result);
}

// Register an event.
wifi.on("wifiRssiChange", recvWifiRssiChangeFunc);

// Unregister an event.
wifi.off("wifiRssiChange", recvWifiRssiChangeFunc);

```


## wifi.on('hotspotStateChange')<sup>(deprecated)</sup>

on(type: 'hotspotStateChange', callback: Callback&lt;number&gt;): void

Subscribes to hotspot state changes.

> **NOTE**
>
> This API is supported since API version 7 and deprecated since API version 9. You are advised to use [wifiManager.on](js-apis-wifiManager.md#wifimanageronhotspotstatechange) instead.

**Required permissions**: ohos.permission.GET_WIFI_INFO

**System capability**: SystemCapability.Communication.WiFi.AP.Core

**Parameters**

  | Name| Type| Mandatory| Description|
  | -------- | -------- | -------- | -------- |
  | type | string | Yes| Event type, which has a fixed value of **hotspotStateChange**.|
  | callback | Callback&lt;number&gt; | Yes| Callback used to return the hotspot state.|

**Hotspot states**

| Value| Description|
| -------- | -------- |
| 0 | Deactivated|
| 1 | Activated|
| 2 | Activating|
| 3 | Deactivating|

**Example**
```ts
import wifi from '@ohos.wifi';

let recvHotspotStateChangeFunc = (result:number) => {
    console.info("Receive hotspot state change event: " + result);
}

// Register an event.
wifi.on("hotspotStateChange", recvHotspotStateChangeFunc);

// Unregister an event.
wifi.off("hotspotStateChange", recvHotspotStateChangeFunc);
```

## wifi.off('hotspotStateChange')<sup>(deprecated)</sup>

off(type: 'hotspotStateChange', callback?: Callback&lt;number&gt;): void

Unsubscribes from hotspot state changes.

> **NOTE**
>
> This API is supported since API version 7 and deprecated since API version 9. You are advised to use [wifiManager.off](js-apis-wifiManager.md#wifimanageroffhotspotstatechange) instead.

**Required permissions**: ohos.permission.GET_WIFI_INFO

**System capability**: SystemCapability.Communication.WiFi.AP.Core

**Parameters**

  | Name| Type| Mandatory| Description|
  | -------- | -------- | -------- | -------- |
  | type | string | Yes| Event type, which has a fixed value of **hotspotStateChange**.|
  | callback | Callback&lt;number&gt; | No| Callback to unregister. If this parameter is not specified, all callbacks for the specified event will be unregistered.|



## wifi.on('p2pStateChange')<sup>(deprecated)</sup>

on(type: 'p2pStateChange', callback: Callback&lt;number&gt;): void

Subscribes to P2P state changes.

> **NOTE**
>
> This API is supported since API version 7 and deprecated since API version 9. You are advised to use [wifiManager.on](js-apis-wifiManager.md#wifimanageronp2pstatechange) instead.

**Required permissions**: ohos.permission.GET_WIFI_INFO

**System capability**: SystemCapability.Communication.WiFi.P2P

**Parameters**

  | Name| Type| Mandatory| Description|
  | -------- | -------- | -------- | -------- |
  | type | string | Yes| Event type, which has a fixed value of **p2pStateChange**.|
  | callback | Callback&lt;number&gt; | Yes| Callback used to return the P2P state.|

**P2P states**

| Value| Description|
| -------- | -------- |
| 1 | Available|
| 2 | Opening|
| 3 | Opened|
| 4 | Closing|
| 5 | Closed|

## wifi.off('p2pStateChange')<sup>(deprecated)</sup>

off(type: 'p2pStateChange', callback?: Callback&lt;number&gt;): void

Unsubscribes from P2P state changes.

> **NOTE**
>
> This API is supported since API version 7 and deprecated since API version 9. You are advised to use [wifiManager.off](js-apis-wifiManager.md#wifimanageroffp2pstatechange) instead.

**Required permissions**: ohos.permission.GET_WIFI_INFO

**System capability**: SystemCapability.Communication.WiFi.P2P

**Parameters**

  | Name| Type| Mandatory| Description|
  | -------- | -------- | -------- | -------- |
  | type | string | Yes| Event type, which has a fixed value of **p2pStateChange**.|
  | callback | Callback&lt;number&gt; | No| Callback to unregister. If this parameter is not specified, all callbacks for the specified event will be unregistered.|

**Example**
```ts
import wifi from '@ohos.wifi';

let recvP2pStateChangeFunc = (result:number) => {
    console.info("Receive p2p state change event: " + result);
}

// Register an event.
wifi.on("p2pStateChange", recvP2pStateChangeFunc);

// Unregister an event.
wifi.off("p2pStateChange", recvP2pStateChangeFunc);
```

## wifi.on('p2pConnectionChange')<sup>(deprecated)</sup>

on(type: 'p2pConnectionChange', callback: Callback&lt;WifiP2pLinkedInfo&gt;): void

Subscribes to P2P connection state changes.

> **NOTE**
>
> This API is supported since API version 8 and deprecated since API version 9. You are advised to use [wifiManager.on](js-apis-wifiManager.md#wifimanageronp2pconnectionchange) instead.

**Required permissions**: ohos.permission.GET_WIFI_INFO

**System capability**: SystemCapability.Communication.WiFi.P2P

**Parameters**

  | Name| Type| Mandatory| Description|
  | -------- | -------- | -------- | -------- |
  | type | string | Yes| Event type, which has a fixed value of **p2pConnectionChange**.|
  | callback | Callback&lt;[WifiP2pLinkedInfo](#wifip2plinkedinfodeprecated)&gt; | Yes| Callback used to return the P2P connection state.|


## wifi.off('p2pConnectionChange')<sup>(deprecated)</sup>

off(type: 'p2pConnectionChange', callback?: Callback&lt;WifiP2pLinkedInfo&gt;): void

Unsubscribes from P2P connection state changes.

> **NOTE**
>
> This API is supported since API version 8 and deprecated since API version 9. You are advised to use [wifiManager.off](js-apis-wifiManager.md#wifimanageroffp2pconnectionchange) instead.

**Required permissions**: ohos.permission.GET_WIFI_INFO

**System capability**: SystemCapability.Communication.WiFi.P2P

**Parameters**

  | Name| Type| Mandatory| Description|
  | -------- | -------- | -------- | -------- |
  | type | string | Yes| Event type, which has a fixed value of **p2pConnectionChange**.|
  | callback | Callback&lt;[WifiP2pLinkedInfo](#wifip2plinkedinfodeprecated)&gt; | No| Callback to unregister. If this parameter is not specified, all callbacks for the specified event will be unregistered.|

**Example**
```ts
import wifi from '@ohos.wifi';

let recvP2pConnectionChangeFunc = (result:wifi.WifiP2pLinkedInfo) => {
    console.info("Receive p2p connection change event: " + result);
}

// Register an event.
wifi.on("p2pConnectionChange", recvP2pConnectionChangeFunc);

// Unregister an event.
wifi.off("p2pConnectionChange", recvP2pConnectionChangeFunc);
```

## wifi.on('p2pDeviceChange')<sup>(deprecated)</sup>

on(type: 'p2pDeviceChange', callback: Callback&lt;WifiP2pDevice&gt;): void

Subscribes to P2P device state changes.

> **NOTE**
>
> This API is supported since API version 8 and deprecated since API version 9. You are advised to use [wifiManager.on](js-apis-wifiManager.md#wifimanageronp2pdevicechange) instead.

**Required permissions**: ohos.permission.GET_WIFI_INFO and ohos.permission.LOCATION

**System capability**: SystemCapability.Communication.WiFi.P2P

**Parameters**

  | Name| Type| Mandatory| Description|
  | -------- | -------- | -------- | -------- |
  | type | string | Yes| Event type, which has a fixed value of **p2pDeviceChange**.|
  | callback | Callback&lt;[WifiP2pDevice](#wifip2pdevicedeprecated)&gt; | Yes| Callback used to return the P2P device state.|


## wifi.off('p2pDeviceChange')<sup>(deprecated)</sup>

off(type: 'p2pDeviceChange', callback?: Callback&lt;WifiP2pDevice&gt;): void

Unsubscribes from P2P device state changes.

> **NOTE**
>
> This API is supported since API version 8 and deprecated since API version 9. You are advised to use [wifiManager.off](js-apis-wifiManager.md#wifimanageroffp2pdevicechange) instead.

**Required permissions**: ohos.permission.LOCATION

**System capability**: SystemCapability.Communication.WiFi.P2P

**Parameters**

  | Name| Type| Mandatory| Description|
  | -------- | -------- | -------- | -------- |
  | type | string | Yes| Event type, which has a fixed value of **p2pDeviceChange**.|
  | callback | Callback&lt;[WifiP2pDevice](#wifip2pdevicedeprecated)&gt; | No| Callback to unregister. If this parameter is not specified, all callbacks for the specified event will be unregistered.|

**Example**
```ts
import wifi from '@ohos.wifi';

let recvP2pDeviceChangeFunc = (result:wifi.WifiP2pDevice) => {
    console.info("Receive p2p device change event: " + result);
}

// Register an event.
wifi.on("p2pDeviceChange", recvP2pDeviceChangeFunc);

// Unregister an event.
wifi.off("p2pDeviceChange", recvP2pDeviceChangeFunc);
```

## wifi.on('p2pPeerDeviceChange')<sup>(deprecated)</sup>

on(type: 'p2pPeerDeviceChange', callback: Callback&lt;WifiP2pDevice[]&gt;): void

Subscribes to P2P peer device state changes.

> **NOTE**
>
> This API is supported since API version 8 and deprecated since API version 9. You are advised to use [wifiManager.on](js-apis-wifiManager.md#wifimanageronp2ppeerdevicechange) instead.

**Required permissions**: ohos.permission.GET_WIFI_INFO and ohos.permission.LOCATION

**System capability**: SystemCapability.Communication.WiFi.P2P

**Parameters**

  | Name| Type| Mandatory| Description|
  | -------- | -------- | -------- | -------- |
  | type | string | Yes| Event type, which has a fixed value of **p2pPeerDeviceChange**.|
  | callback | Callback&lt;[WifiP2pDevice[]](#wifip2pdevicedeprecated)&gt; | Yes| Callback used to return the P2P peer device state.|


## wifi.off('p2pPeerDeviceChange')<sup>(deprecated)</sup>

off(type: 'p2pPeerDeviceChange', callback?: Callback&lt;WifiP2pDevice[]&gt;): void

Unsubscribes from P2P peer device state changes.

> **NOTE**
>
> This API is supported since API version 8 and deprecated since API version 9. You are advised to use [wifiManager.off](js-apis-wifiManager.md#wifimanageroffp2ppeerdevicechange) instead.

**Required permissions**: ohos.permission.LOCATION

**System capability**: SystemCapability.Communication.WiFi.P2P

**Parameters**

  | Name| Type| Mandatory| Description|
  | -------- | -------- | -------- | -------- |
  | type | string | Yes| Event type, which has a fixed value of **p2pPeerDeviceChange**.|
  | callback | Callback&lt;[WifiP2pDevice[]](#wifip2pdevicedeprecated)&gt; | No| Callback to unregister. If this parameter is not specified, all callbacks for the specified event will be unregistered.|

**Example**
```ts
import wifi from '@ohos.wifi';

let recvP2pPeerDeviceChangeFunc = (result:wifi.WifiP2pDevice[]) => {
    console.info("Receive p2p peer device change event: " + result);
}

// Register an event.
wifi.on("p2pPeerDeviceChange", recvP2pPeerDeviceChangeFunc);

// Unregister an event.
wifi.off("p2pPeerDeviceChange", recvP2pPeerDeviceChangeFunc);
```

## wifi.on('p2pPersistentGroupChange')<sup>(deprecated)</sup>

on(type: 'p2pPersistentGroupChange', callback: Callback&lt;void&gt;): void

Subscribes to P2P persistent group state changes.

> **NOTE**
>
> This API is supported since API version 8 and deprecated since API version 9. You are advised to use [wifiManager.on](js-apis-wifiManager.md#wifimanageronp2ppersistentgroupchange) instead.

**Required permissions**: ohos.permission.GET_WIFI_INFO

**System capability**: SystemCapability.Communication.WiFi.P2P

**Parameters**

  | Name| Type| Mandatory| Description|
  | -------- | -------- | -------- | -------- |
  | type | string | Yes| Event type, which has a fixed value of **p2pPersistentGroupChange**.|
  | callback | Callback&lt;void&gt; | Yes| Callback used to return the P2P persistent group state.|


## wifi.off('p2pPersistentGroupChange')<sup>(deprecated)</sup>

off(type: 'p2pPersistentGroupChange', callback?: Callback&lt;void&gt;): void

Unsubscribes from P2P persistent group state changes.

> **NOTE**
>
> This API is supported since API version 8 and deprecated since API version 9. You are advised to use [wifiManager.off](js-apis-wifiManager.md#wifimanageroffp2ppersistentgroupchange) instead.

**Required permissions**: ohos.permission.GET_WIFI_INFO

**System capability**: SystemCapability.Communication.WiFi.P2P

**Parameters**

  | Name| Type| Mandatory| Description|
  | -------- | -------- | -------- | -------- |
  | type | string | Yes| Event type, which has a fixed value of **p2pPersistentGroupChange**.|
  | callback | Callback&lt;void&gt; | No| Callback to unregister. If this parameter is not specified, all callbacks for the specified event will be unregistered.|

**Example**
```ts
import wifi from '@ohos.wifi';

let recvP2pPersistentGroupChangeFunc = (result:void) => {
    console.info("Receive p2p persistent group change event: " + result);
}

// Register an event.
wifi.on("p2pPersistentGroupChange", recvP2pPersistentGroupChangeFunc);

// Unregister an event.
wifi.off("p2pPersistentGroupChange", recvP2pPersistentGroupChangeFunc);

```

## wifi.on('p2pDiscoveryChange')<sup>(deprecated)</sup>

on(type: 'p2pDiscoveryChange', callback: Callback&lt;number&gt;): void

Subscribes to P2P device discovery state changes.

> **NOTE**
>
> This API is supported since API version 8 and deprecated since API version 9. You are advised to use [wifiManager.on](js-apis-wifiManager.md#wifimanageronp2pdiscoverychange) instead.

**Required permissions**: ohos.permission.GET_WIFI_INFO

**System capability**: SystemCapability.Communication.WiFi.P2P

**Parameters**

  | Name| Type| Mandatory| Description|
  | -------- | -------- | -------- | -------- |
  | type | string | Yes| Event type, which has a fixed value of **p2pDiscoveryChange**.|
  | callback | Callback&lt;number&gt; | Yes| Callback used to return the P2P device discovery state.|

**P2P discovered device states**

| Value| Description|
| -------- | -------- |
| 0 | Initial state.|
| 1 | Discovered.|


## wifi.off('p2pDiscoveryChange')<sup>(deprecated)</sup>

off(type: 'p2pDiscoveryChange', callback?: Callback&lt;number&gt;): void

Unsubscribes from P2P device discovery state changes.

> **NOTE**
>
> This API is supported since API version 8 and deprecated since API version 9. You are advised to use [wifiManager.off](js-apis-wifiManager.md#wifimanageroffp2pdiscoverychange) instead.

**Required permissions**: ohos.permission.GET_WIFI_INFO

**System capability**: SystemCapability.Communication.WiFi.P2P

**Parameters**

  | Name| Type| Mandatory| Description|
  | -------- | -------- | -------- | -------- |
  | type | string | Yes| Event type, which has a fixed value of **p2pDiscoveryChange**.|
  | callback | Callback&lt;number&gt; | No| Callback to unregister. If this parameter is not specified, all callbacks for the specified event will be unregistered.|

**Example**
```ts
import wifi from '@ohos.wifi';

let recvP2pDiscoveryChangeFunc = (result:number) => {
    console.info("Receive p2p discovery change event: " + result);
}

// Register an event.
wifi.on("p2pDiscoveryChange", recvP2pDiscoveryChangeFunc);

// Unregister an event.
wifi.off("p2pDiscoveryChange", recvP2pDiscoveryChangeFunc);
```
