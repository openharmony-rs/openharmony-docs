# @ohos.wifiManager (WLAN)
<!--Kit: Connectivity Kit-->
<!--Subsystem: Communication-->
<!--Owner: @qq_43802146-->
<!--Designer: @qq_43802146-->
<!--Tester: @furryfurry123-->
<!--Adviser: @zhang_yixin13-->
<!-- md-trans-meta sourceCommit=794bdfcc42df83dd7fb4cf55998b1aff80916ceb translatedAt=2026-08-27T04:13:16.091Z pushedAt=2026-08-28T11:40:46.121Z -->

This module provides basic Wi-Fi functionalities (such as wireless access, wireless encryption, and wireless roaming), basic peer-to-peer (P2P) services, and Wi-Fi notification services. It allows applications to interact with other devices through Wi-Fi.

> **NOTE**
> The initial APIs of this module are supported since API version 9. Newly added APIs will be marked with a superscript to indicate their earliest API version.


## Modules to Import

```ts
import { wifiManager } from '@kit.ConnectivityKit';
```


## wifiManager.isWifiActive

isWifiActive(): boolean

Checks whether Wi-Fi is activated.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Communication.WiFi.STA

**Return value**

  | Type | Description |
  | -------- | -------- |
  | boolean | **true**: Wi-Fi is activated. **false**: Wi-Fi is not activated. |

**Error codes**

For details about the error codes, see [Wi-Fi Error Codes](errorcode-wifi.md) and [Universal Error Codes](../errorcode-universal.md).

| ID | Error message |
| -------- | -------- |
| 801 | Capability not supported.          |
| 2501000  | Operation failed.|

**Example**

```ts
  import { wifiManager } from '@kit.ConnectivityKit';

  try {
    let isWifiActive = wifiManager.isWifiActive();
    console.info("isWifiActive:" + isWifiActive);
  }catch(error){
    console.error("failed:" + JSON.stringify(error));
  }
```

## wifiManager.enableWifi<sup>15+</sup>

enableWifi(): void

Enables Wi-Fi.

**Required permissions:** ohos.permission.SET_WIFI_INFO and (ohos.permission.MANAGE_WIFI_CONNECTION, available to system applications only, or ohos.permission.MANAGE_ENTERPRISE_WIFI_CONNECTION, available to enterprise applications only)

**System capability**: SystemCapability.Communication.WiFi.STA

**Error codes**

For details about the error codes, see [Wi-Fi Error Codes](errorcode-wifi.md) and [Universal Error Codes](../errorcode-universal.md).

| ID | Error Message |
| -------- | -------- |
| 201 | Permission denied.          |
| 801  | Capability not supported.|
| 2501000 | Operation failed.          |
| 2501003  | Operation failed because the service is being closed.|

**Example**

```ts
  import { wifiManager } from '@kit.ConnectivityKit';
  
  try {
    wifiManager.enableWifi();
  }catch(error){
    console.error("failed:" + JSON.stringify(error));
  }
```

## wifiManager.disableWifi<sup>20+</sup>

disableWifi(): void

Disables Wi-Fi.

**Required permissions:** ohos.permission.SET_WIFI_INFO and (ohos.permission.MANAGE_WIFI_CONNECTION, System applications only, or ohos.permission.MANAGE_ENTERPRISE_WIFI_CONNECTION, Enterprise applications only)

**System capability**: SystemCapability.Communication.WiFi.STA

**Error codes**

For details about the error codes, see [Wi-Fi Error Codes](errorcode-wifi.md) and [Universal Error Codes](../errorcode-universal.md).

| ID | Error message |
| -------- | -------- |
| 201 | Permission denied.                 |
| 801 | Capability not supported.          |
| 2501000  | Operation failed.|
| 2501004  | Operation failed because the service is being opened. |

**Example**

```ts
  import { wifiManager } from '@kit.ConnectivityKit';

  try {
    wifiManager.disableWifi();
  }catch(error){
    console.error(`disableWifi failed. ${error.message}`);
  }
```

## **wifiManager.scan**<sup>(deprecated)</sup>

scan(): void

Starts Wi-Fi scanning. Wi-Fi must be enabled before this method is called.

> **NOTE**
> This API is supported since API version 9 and deprecated since API version 10. You are advised to use [wifiManager.startScan](#wifimanagerstartscan21) instead.

**Required permissions**: ohos.permission.SET_WIFI_INFO, ohos.permission.LOCATION, and ohos.permission.APPROXIMATELY_LOCATION

**System capability**: SystemCapability.Communication.WiFi.STA

**Error codes**

For details about the error codes, see [Wi-Fi Error Codes](errorcode-wifi.md) and [Universal Error Codes](../errorcode-universal.md).

| ID | Error message |
| -------- | -------- |
| 201 | Permission denied.                 |
| 801 | Capability not supported.          |
| 2501000  | Operation failed.|

**Example**

```ts
  import { wifiManager } from '@kit.ConnectivityKit';

  try {
    wifiManager.scan();
  }catch(error){
    console.error("failed:" + JSON.stringify(error));
  }
```

## wifiManager.startScan<sup>21+</sup>

startScan(): void

Starts Wi-Fi scanning.

- When the application is running in the foreground, it can scan at most four times within two minutes.
- When running in the background, it can scan at most once within thirty minutes.
- Subscribe to the scan state change event through [on('wifiScanStateChange')](#wifimanageronwifiscanstatechange) to listen for scan completion notifications.

**Required permissions**: ohos.permission.SET_WIFI_INFO

**System capability**: SystemCapability.Communication.WiFi.STA

**Error codes**

For details about the error codes, see [Wi-Fi Error Codes](errorcode-wifi.md) and [Universal Error Codes](../errorcode-universal.md).

| ID | Error message |
| -------- | -------- |
| 201 | Permission denied.                 |
| 801 | Capability not supported.          |
| 2501000  | Operation failed.|

**Example**

```ts
  import { wifiManager } from '@kit.ConnectivityKit';

  try {
    wifiManager.startScan();
  }catch(error){
    console.error("failed:" + JSON.stringify(error));
  }
```

## wifiManager.getScanResults<sup>(deprecated)</sup>

getScanResults(): Promise&lt;Array&lt;WifiScanInfo&gt;&gt;

Obtains the scan results. This API uses a promise to return the result.

- The promise is used to return an array of **WifiScanInfo** objects, and each object indicates the scanning information about a Wi-Fi network.

> **NOTE**
> This API is supported since API version 9 and deprecated since API version 10. You are advised to use [wifiManager.getScanInfoList](#wifimanagergetscaninfolist10) instead.

**Required permissions:** ohos.permission.GET_WIFI_INFO and (ohos.permission.GET_WIFI_PEERS_MAC or (ohos.permission.LOCATION and ohos.permission.APPROXIMATELY_LOCATION))

**System capability**: SystemCapability.Communication.WiFi.STA

**Return value**

| Type | Description |
| -------- | -------- |
| Promise&lt;&nbsp;Array&lt;[WifiScanInfo](#wifiscaninfo)&gt;&nbsp;&gt; | Promise object. Returns the list of scanned hotspots. |

**Error codes**

For details about the error codes, see [Wi-Fi Error Codes](errorcode-wifi.md) and [Universal Error Codes](../errorcode-universal.md).

| ID | Error message |
| -------- | -------- |
| 201 | Permission denied.                 |
| 801 | Capability not supported.          |
| 2501000  | Operation failed.|

## wifiManager.getScanResults<sup>(deprecated)</sup>

getScanResults(callback: AsyncCallback&lt;Array&lt;WifiScanInfo&gt;&gt;): void

Get scan results. This API uses an asynchronous callback to return the result.

- The callback is used to return an array of **WifiScanInfo** objects, and each object indicates the scanning information about a Wi-Fi network.

> **NOTE**
> This API is supported since API version 9 and deprecated since API version 10. You are advised to use [wifiManager.getScanInfoList](#wifimanagergetscaninfolist10) instead.

**Required permissions**: ohos.permission.GET_WIFI_INFO and (ohos.permission.GET_WIFI_PEERS_MAC or (ohos.permission.LOCATION and ohos.permission.APPROXIMATELY_LOCATION))

**System capability**: SystemCapability.Communication.WiFi.STA

**Parameters**
| Name | Type | Mandatory | Description |
| -------- | -------- | -------- | -------- |
| callback | AsyncCallback&lt;&nbsp;Array&lt;[WifiScanInfo](#wifiscaninfo)&gt;&gt; | Yes | Callback used to return the result. If the operation is successful, **err** is **0** and **data** is the detected hotspot. Otherwise, **err** is a non-zero value and **data** is empty. |

**Error codes**

For details about the error codes, see [Wi-Fi Error Codes](errorcode-wifi.md) and [Universal Error Codes](../errorcode-universal.md).

| ID | Error Message |
| -------- | -------- |
| 201 | Permission denied.                 |
| 801 | Capability not supported.          |
| 2501000  | Operation failed.|

**Example**
```ts
  import { wifiManager } from '@kit.ConnectivityKit';
  
  wifiManager.getScanResults((err, result) => {
      if (err) {
          console.error("get scan info error");
          return;
      }
  
      let len = result.length;
      console.info("wifi received scan info: " + len);
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
  
  wifiManager.getScanResults().then(result => {
      let len = result.length;
      console.info("wifi received scan info: " + len);
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
  }).catch((err:number) => {
      console.error("failed:" + JSON.stringify(err));
  });
```

## wifiManager.getScanResultsSync<sup>(deprecated)</sup>

getScanResultsSync(): &nbsp;Array&lt;[WifiScanInfo](#wifiscaninfo)&gt;

Obtains the scanning result. This API returns an array of **WifiScanInfo** objects synchronously. Each object indicates the scanning information about a Wi-Fi network.

> **NOTE**
>
> This API is supported since API version 9 and deprecated since API version 10. You are advised to use [wifiManager.getScanInfoList](#wifimanagergetscaninfolist10) instead.

**Required permissions**: ohos.permission.GET_WIFI_INFO and (ohos.permission.GET_WIFI_PEERS_MAC or (ohos.permission.LOCATION and ohos.permission.APPROXIMATELY_LOCATION))

**System capability**: SystemCapability.Communication.WiFi.STA

**Return value**

| Type | Description |
| -------- | -------- |
| &nbsp;Array&lt;[WifiScanInfo](#wifiscaninfo)&gt; | Scan result array. |

**Error codes**

For details about the error codes, see [Wi-Fi Error Codes](errorcode-wifi.md) and [Universal Error Codes](../errorcode-universal.md).

| ID | Error message |
| -------- | -------- |
| 201 | Permission denied.                 |
| 801 | Capability not supported.          |
| 2501000  | Operation failed.|

**Example**

```ts
  import { wifiManager } from '@kit.ConnectivityKit';

  try {
    let scanInfoList = wifiManager.getScanResultsSync();
    console.info("scanInfoList:" + JSON.stringify(scanInfoList));
    let len = scanInfoList.length;
        console.info("wifi received scan info: " + len);
    if(len > 0){
      for (let i = 0; i < len; ++i) {
        console.info("ssid: " + scanInfoList[i].ssid);
        console.info("bssid: " + scanInfoList[i].bssid);
        console.info("capabilities: " + scanInfoList[i].capabilities);
        console.info("securityType: " + scanInfoList[i].securityType);
        console.info("rssi: " + scanInfoList[i].rssi);
        console.info("band: " + scanInfoList[i].band);
        console.info("frequency: " + scanInfoList[i].frequency);
        console.info("channelWidth: " + scanInfoList[i].channelWidth);
        console.info("timestamp: " + scanInfoList[i].timestamp);
      }
    }  
  }catch(error){
    console.error("failed:" + JSON.stringify(error));
  }
  
```

## wifiManager.getScanInfoList<sup>10+</sup>

getScanInfoList(): Array&lt;WifiScanInfo&gt;

Obtains the cached scan results within the last 30 seconds.

**Required permissions**: ohos.permission.GET_WIFI_INFO

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Communication.WiFi.STA

**Return value**

| Type | Description |
| -------- | -------- |
| Array&lt;[WifiScanInfo](#wifiscaninfo)&gt; | Returns the list of scanned hotspots. If the application has applied for the ohos.permission.GET_WIFI_PEERS_MAC permission, the bssid in the returned result is the real device address; otherwise, it is a random device address. |

**Error codes**

For details about the error codes, see [Wi-Fi Error Codes](errorcode-wifi.md) and [Universal Error Codes](../errorcode-universal.md).

| ID | Error message |
| -------- | -------- |
| 201 | Permission denied.                 |
| 801 | Capability not supported.          |
| 2501000  | Operation failed.|

**Example**

```ts
  import { wifiManager } from '@kit.ConnectivityKit';

  try {
    let scanInfoList = wifiManager.getScanInfoList();
    console.info("scanInfoList:" + JSON.stringify(scanInfoList));
    let len = scanInfoList.length;
        console.info("wifi received scan info: " + len);
    if(len > 0){
      for (let i = 0; i < len; ++i) {
        console.info("ssid: " + scanInfoList[i].ssid);
        console.info("bssid: " + scanInfoList[i].bssid);
        console.info("capabilities: " + scanInfoList[i].capabilities);
        console.info("securityType: " + scanInfoList[i].securityType);
        console.info("rssi: " + scanInfoList[i].rssi);
        console.info("band: " + scanInfoList[i].band);
        console.info("frequency: " + scanInfoList[i].frequency);
        console.info("channelWidth: " + scanInfoList[i].channelWidth);
        console.info("timestamp: " + scanInfoList[i].timestamp);
        console.info("supportedWifiCategory: " + scanInfoList[i].supportedWifiCategory);
        console.info("isHiLinkNetwork: " + scanInfoList[i].isHiLinkNetwork);
      }
    }  
  }catch(error){
    console.error("failed:" + JSON.stringify(error));
  }
  
```

## WifiScanInfo

Represents the Wi-Fi hotspot information.

**System capability**: SystemCapability.Communication.WiFi.STA


| Name | Type | Read-Only | Optional | Description |
| -------- | -------- | -------- | -------- | -------- |
| ssid | string | No | No | Service set identifier (SSID) of the hotspot, in UTF-8 format. The maximum length is 32 bytes.<br>**Atomic service API**: This API can be used in atomic services since API version 12. |
| bssid | string | No | No | Basic service set identifier (BSSID) of the hotspot, for example, **00:11:22:33:44:55**.<br>**Atomic service API**: This API can be used in atomic services since API version 12. |
| bssidType<sup>10+</sup>| [DeviceAddressType](#deviceaddresstype10) | No | No | BSSID type of the hotspot.<br>**Atomic service API**: This API can be used in atomic services since API version 12. |
| capabilities | string | No | No | Hotspot capabilities. |
| securityType | [WifiSecurityType](#wifisecuritytype) | No | No | Wi-Fi encryption type.<br>**Atomic service API**: This API can be used in atomic services since API version 12. |
| rssi | number | No | No | Received signal strength indicator (RSSI) of the hotspot, in dBm.<br>**Atomic service API**: This API can be used in atomic services since API version 12. |
| band | number | No | No | Frequency band of the Wi-Fi access point. The value **1** indicates 2.4 GHz, and the value **2** indicates 5 GHz. |
| frequency | number | No | No | Frequency of the Wi-Fi access point.<br>**Atomic service API**: This API can be used in atomic services since API version 12. |
| channelWidth | number | No | No | Bandwidth of the Wi-Fi access point. For details, see [WifiChannelWidth](#wifichannelwidth). |
| centerFrequency0 | number | No | No | Center frequency of the hotspot. |
| centerFrequency1 | number | No | No | Center frequency of the hotspot. If the hotspot uses two non-overlapping Wi-Fi channels, two center frequencies, namely **centerFrequency0** and **centerFrequency1**, are returned. |
| infoElems | Array&lt;[WifiInfoElem](#wifiinfoelem)&gt; | No | No | Information elements. |
| timestamp | number | No | No | Timestamp. |
| supportedWifiCategory<sup>12+</sup> | [WifiCategory](#wificategory12) | No | No | Highest Wi-Fi category supported by the hotspot. |
| isHiLinkNetwork<sup>12+</sup> | boolean | No | No| Whether HiLink is supported by the hotspot. The value **true** indicates that HiLink is supported, and the value **false** indicates the opposite. |

## DeviceAddressType<sup>10+</sup>

Enumerates the Wi-Fi device address (MAC/BSSID) types. It is the unique address of a Wi-Fi device or access point.

The **DeviceAddressType** parameter is required in Wi-Fi related operations, such as connecting to a specified Wi-Fi network and obtaining the device information.

**System capability**: SystemCapability.Communication.WiFi.Core

**Atomic service API**: This API can be used in atomic services since API version 12.

| Name | Value | Description |
| -------- | -------- | -------- |
| RANDOM_DEVICE_ADDRESS | 0 | Random device address. |
| REAL_DEVICE_ADDRESS | 1 | Real device address. |

## WifiSecurityType

Represents the encryption type enumeration.

**System capability**: SystemCapability.Communication.WiFi.Core

| Name | Value | Description |
| -------- | -------- | -------- |
| WIFI_SEC_TYPE_INVALID | 0 | Invalid encryption type. |
| WIFI_SEC_TYPE_OPEN | 1 | Open encryption type.<br>**Atomic service API**: Since API version 12, this API is supported in atomic services. |
| WIFI_SEC_TYPE_WEP | 2 | Wired&nbsp;Equivalent&nbsp;Privacy&nbsp;(WEP) encryption type. This encryption type is not supported for candidate networks (add network configuration information). |
| WIFI_SEC_TYPE_PSK | 3 | Pre-shared&nbsp;key&nbsp;(PSK) encryption type. |
| WIFI_SEC_TYPE_SAE | 4 | Simultaneous&nbsp;Authentication&nbsp;of&nbsp;Equals&nbsp;(SAE) encryption type. |
| WIFI_SEC_TYPE_EAP | 5 | EAP authentication (EAP) encryption type. |
| WIFI_SEC_TYPE_EAP_SUITE_B | 6 | Suite-B 192-bit encryption type. |
| WIFI_SEC_TYPE_OWE | 7 | Opportunistic&nbsp; Wireless&nbsp; Encryption&nbsp;(OWE) encryption type. |
| WIFI_SEC_TYPE_WAPI_CERT | 8 | WAPI-Cert encryption type. |
| WIFI_SEC_TYPE_WAPI_PSK | 9 | WAPI-PSK encryption type. |


## WifiBandType<sup>10+</sup>

Represents an enumeration of the Wi-Fi band types.

**System capability**: SystemCapability.Communication.WiFi.STA

| Name | Value | Description |
| -------- | -------- | -------- |
| WIFI_BAND_NONE | 0 | Invalid band type. |
| WIFI_BAND_2G | 1 | 2.4G band type. |
| WIFI_BAND_5G | 2 | 5G band type. |
| WIFI_BAND_6G | 3 | 6G band type. |
| WIFI_BAND_60G | 4 | 60G band type. |

## WifiStandard<sup>10+</sup>

Enumerates the Wi-Fi standards.

**System capability**: SystemCapability.Communication.WiFi.STA

| Name | Value | Description |
| -------- | -------- | -------- |
| WIFI_STANDARD_UNDEFINED | 0 | Invalid Wi-Fi standard type. |
| WIFI_STANDARD_11A | 1 | 802.11a Wi-Fi standard type. |
| WIFI_STANDARD_11B | 2 | 802.11b Wi-Fi standard type. |
| WIFI_STANDARD_11G | 3 | 802.11g Wi-Fi standard type. |
| WIFI_STANDARD_11N | 4 | 802.11n Wi-Fi standard type. |
| WIFI_STANDARD_11AC | 5 | 802.11ac Wi-Fi standard type. |
| WIFI_STANDARD_11AX | 6 | 802.11ax Wi-Fi standard type. |
| WIFI_STANDARD_11AD | 7 | 802.11ad Wi-Fi standard type. |

## WifiInfoElem

Represents the Wi-Fi hotspot information.

**System capability**: SystemCapability.Communication.WiFi.STA


| Name | Type | Read-Only | Optional | Description |
| -------- | -------- | -------- | -------- | -------- |
| eid | number | No | No | Element ID. |
| content | Uint8Array | No | No | Element content. |


## WifiChannelWidth

Enumerates the bandwidth types.

**System capability**: SystemCapability.Communication.WiFi.STA


| Name | Value | Description |
| -------- | -------- | -------- |
| WIDTH_20MHZ | 0 | 20MHZ. |
| WIDTH_40MHZ | 1 | 40MHZ. |
| WIDTH_80MHZ | 2 | 80MHZ. |
| WIDTH_160MHZ | 3 | 160MHZ. |
| WIDTH_80MHZ_PLUS | 4 | 80MHZ<sup>+</sup>. |
| WIDTH_INVALID | 5 | Invalid value. |

## WifiDeviceConfig

Represents the Wi-Fi configuration information.

**System capability**: SystemCapability.Communication.WiFi.STA

<!--Table: 15%; 19%; 8%; 8%; 50%-->
| Name | Type | Read-Only | Optional | Description |
| -------- | -------- | -------- | -------- | -------- |
| ssid | string | No | No | Service set identifier (SSID) of the hotspot, in UTF-8 format. The maximum length is 32 bytes.<br>**Atomic service API**: This API can be used in atomic services since API version 12. |
| bssid | string | No | Yes | Basic service set identifier (BSSID) of the hotspot, for example, **00:11:22:33:44:55**.<br>**Atomic service API**: This API can be used in atomic services since API version 12. |
| bssidType<sup>10+</sup> | [DeviceAddressType](#deviceaddresstype10) | No | Yes | BSSID type of the hotspot.<br>**Atomic service API**: This API can be used in atomic services since API version 12. |
| preSharedKey | string | No | No | PSK of the hotspot, which cannot exceed 64 bytes.<br>When **securityType** is **WIFI_SEC_TYPE_OPEN**, this parameter must be an empty string. When **securityType** is any other value, this parameter cannot be empty.<br>When **securityType** is **WIFI_SEC_TYPE_WEP**, the PSK must be of 5, 10, 13, 26, 16, or 32 bytes. If the PSK length is 10, 26, 16, or 32 bytes, the PSK must be a hexadecimal number.<br>When **securityType** is **WIFI_SEC_TYPE_SAE**, the minimum PSK length is 1 byte.<br>When **securityType** is **WIFI_SEC_TYPE_PSK**, the minimum PSK length is 8 bytes.<br>**Atomic service API**: This API can be used in atomic services since API version 12. |
| isHiddenSsid | boolean | No | Yes | Whether the network is hidden. The value **true** indicates that the network is hidden; the value **false** indicates the opposite. |
| securityType | [WifiSecurityType](#wifisecuritytype)| No | No | Security type.<br>**Atomic service API**: This API can be used in atomic services since API version 12. |
| netId<sup>22+</sup> | number | No | Yes | Network ID allocated. |
| eapConfig<sup>10+</sup> | [WifiEapConfig](#wifieapconfig10) | No | Yes | EAP configuration. This parameter is mandatory only when **securityType** is **WIFI_SEC_TYPE_EAP**. |
| wapiConfig<sup>12+</sup> | [WifiWapiConfig](#wifiwapiconfig12) | No | Yes | WAPI configuration. This parameter is mandatory only when **securityType** is **WIFI_SEC_TYPE_WAPI_CERT** or **WIFI_SEC_TYPE_WAPI_PSK**. |
| showNoInternetDialog | boolean | No | Yes | Whether to display a dialog box when no Internet connection is detected during the first network detection. **false**: The default network is switched to the cellular network and no dialog box is displayed. **true**: A dialog box is displayed, indicating no Internet connection and prompting the user to select the default network. The default value is **true**.<br>**Model restriction:** This API can be used only in the stage model.<br>**Initial version:** 26.0.0 |

## WifiEapConfig<sup>10+</sup>

Extensible Authentication Protocol configuration information.

- **WifiEapConfig** is a class used to configure the EAP authentication type of the Wi-Fi network.
- It contains configuration items such as the EAP authentication method, phase 2 authentication method, identity, password, and certificate.

**System capability**: SystemCapability.Communication.WiFi.STA

| Name | Type | Read-Only | Optional | Description |
| -------- | -------- | -------- | -------- | -------- |
| eapMethod | [EapMethod](#eapmethod10) | No | No | EAP authentication method. |
| phase2Method | [Phase2Method](#phase2method10) | No | No | Phase 2 authentication method. Required to fill only when **eapMethod** is **EAP_PEAP** or **EAP_TTLS**. |
| identity | string | No | No | Identity. When **eapMethod** is **EAP_PEAP**, **EAP_TLS**, or **EAP_PWD**, this field cannot be an empty string. |
| anonymousIdentity | string | No | No | Anonymous identity. Not used yet. |
| password | string | No | No | Password. When **eapMethod** is **EAP_PEAP** or **EAP_PWD**, this field cannot be an empty string, with a maximum length of 128 bytes. |
| caCertAlias | string | No | No | CA certificate alias. |
| caPath | string | No | No | CA certificate path. |
| clientCertAlias | string | No | No | Client certificate alias. |
| certEntry | Uint8Array | No | No | CA certificate content. When **eapMethod** is **EAP_TLS**, if this field is empty, **clientCertAlias** cannot be empty. |
| certPassword | string | No | No | CA certificate password, with a maximum length of 128 bytes. |
| altSubjectMatch | string | No | No | Alternative subject match. |
| domainSuffixMatch | string | No | No | Domain suffix match. |
| realm | string | No | No | Realm of the pass credential. |
| plmn | string | No | No | Direct credential provider of the public land mobile network. |
| eapSubId | number | No | No | Sub ID of the SIM card. |


## WifiWapiConfig<sup>12+</sup>

WAPI (Wireless LAN Authentication and Privacy Infrastructure) authentication protocol configuration.

When a user connects to a wireless network through the WAPI authentication protocol, the connection can be established by configuring parameters or certificates in the following ways.
- Method 1: Configure a certificate for connection. The key fields in **WifiDeviceConfig** are configured as follows:
  - **preSharedKey** does not need to be passed.
  - Set **securityType** to **WIFI_SEC_TYPE_WAPI_CERT**.
  - In **wapiConfig**:
    - **wapiAsCert** passes the text content of the AS certificate.
    - **wapiUserCert** passes the text content of the user certificate.
- Method 2: Configure **preSharedKey** for connection. The key fields in **WifiDeviceConfig** are configured as follows:
   - **preSharedKey** is the password configured on the router.
   - **securityType** is set to **WIFI_SEC_TYPE_WAPI_PSK**.

**System capability**: SystemCapability.Communication.WiFi.STA

| Name | Type | Read-Only | Optional | Description |
| -------- | -------- | -------- | -------- | -------- |
| wapiPskType | [WapiPskType](#wapipsktype12)| No | No | Encryption type. |
| wapiAsCert | string | No | No | AS certificate (Authentication Server Certificate). |
| wapiUserCert | string | No | No | User certificate. |

## WifiCapability

Wi-Fi capability.

**Since**: 26.0.0

**System capability**: SystemCapability.Communication.WiFi.STA

**Model restriction:** This API can be used only in the stage model.

| Name | Value | Description |
| -------- | -------- | -------- |
| WIFI_AUTO_ENABLE | 0 | Wi-Fi auto-enable capability. |

## WapiPskType<sup>12+</sup>

Enumerates the WAPI authentication modes.

**System capability**: SystemCapability.Communication.WiFi.Core

| Name | Value | Description |
| -------- | -------- | -------- |
| WAPI_PSK_ASCII | 0 | ASCII type. |
| WAPI_PSK_HEX | 1 | HEX type. |

## EapMethod<sup>10+</sup>

Represents an enumeration of EAP authentication methods.

**System capability**: SystemCapability.Communication.WiFi.STA

| Name | Value | Description |
| -------- | -------- | -------- |
| EAP_NONE | 0 | Not specified. |
| EAP_PEAP | 1 | PEAP type. |
| EAP_TLS | 2 | TLS type. |
| EAP_TTLS | 3 | TTLS type. |
| EAP_PWD | 4 | PWD type. |
| EAP_SIM | 5 | SIM type. |
| EAP_AKA | 6 | AKA type. |
| EAP_AKA_PRIME | 7 | AKA Prime type. |
| EAP_UNAUTH_TLS | 8 | UNAUTH TLS type. |

## Phase2Method<sup>10+</sup>

Represents the enumeration of phase 2 authentication methods.

**System capability**: SystemCapability.Communication.WiFi.STA

| Name | Value | Description |
| -------- | -------- | -------- |
| PHASE2_NONE | 0 | Not specified. |
| PHASE2_PAP | 1 | PAP type. |
| PHASE2_MSCHAP | 2 | MSCHAP type. |
| PHASE2_MSCHAPV2 | 3 | MSCHAPV2 type. |
| PHASE2_GTC | 4 | GTC type. |
| PHASE2_SIM | 5 | SIM type. |
| PHASE2_AKA | 6 | AKA type. |
| PHASE2_AKA_PRIME | 7 | AKA Prime type. |

## WifiCategory<sup>12+</sup>

Enumerates the highest Wi-Fi category supported by the hotspot. This method can be used to identify and distinguish hotspots of different Wi-Fi technology standards.

**System capability**: SystemCapability.Communication.WiFi.STA

| Name | Value | Description |
| -------- | -------- | -------- |
| DEFAULT | 1 | Default. Wi-Fi category below Wi-Fi 6. |
| WIFI6 | 2 | Wi-Fi 6. |
| WIFI6_PLUS | 3 | Wi-Fi 6+. |
| WIFI7<sup>15+</sup> | 4 | Wi-Fi 7. |
| WIFI7_PLUS<sup>15+</sup> | 5 | Wi-Fi 7+. |

## ConnectSettings

Represents the Wi-Fi connection settings information.

**Since**: 26.0.0

**System capability**: SystemCapability.Communication.WiFi.STA

**Atomic service API**: This API can be used in atomic services since API version 26.0.0.

**Model restriction:** This API can be used only in the stage model.


| Name | Type | Read-Only | Optional | Description |
| -------- | -------- | -------- | -------- | -------- |
| networkId | number | No | No | ID of the candidate network configuration. |
| withUserAction | boolean | No | Yes | Whether to prompt the user for trust confirmation during connection. The value **true** means the function is the same as that of **connectToCandidateConfigWithUserAction**, and **false** means the user is not prompted for trust confirmation. The default value is **false**. |
| userActionTimeout | number | No | Yes | Display duration of the trust confirmation dialog box that prompts the user, in seconds. The valid value ranges from 1 to 30 seconds, and the default value is 10 seconds. |
| addNetworkToSystem | boolean | No | Yes | Whether to add the network to the system. The value **true** means the suggested network is added to the system network, and **false** means the suggested network is retained. The default value is **false**. |


## wifiManager.addCandidateConfig

addCandidateConfig(config: WifiDeviceConfig): Promise&lt;number&gt;

Adds the candidate network configuration. This API uses a promise to return the result. Before using this API, ensure that Wi-Fi is enabled.

- You can pass a [WifiDeviceConfig](#wifideviceconfig) object to configure the Wi-Fi network, such as the SSID, password, and security type.
- This API uses a promise to return the configuration ID to distinguish and manage different Wi-Fi settings. This ID is a number.

**Required permissions**: ohos.permission.SET_WIFI_INFO

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Communication.WiFi.STA

**Parameters**

| Name | Type | Mandatory | Description |
| -------- | -------- | -------- | -------- |
| config | [WifiDeviceConfig](#wifideviceconfig) | Yes | Wi-Fi configuration information. The value of **bssidType** is a random device address by default. |

**Return value**

  | Type | Description |
  | -------- | -------- |
  | Promise&lt;number&gt; | Promise object. Represents the network configuration ID. |

**Error codes**

For details about the error codes, see [Wi-Fi Error Codes](errorcode-wifi.md) and [Universal Error Codes](../errorcode-universal.md).

| ID | Error message |
| -------- | ---------------------------- |
| 201 | Permission denied.                 |
| 401 | Invalid parameters. Possible causes: 1. Mandatory parameters are left unspecified.<br>2. Incorrect parameter types. 3. Parameter verification failed.|
| 801 | Capability not supported.          |
| 2501000  | Operation failed.|

**Example**
```ts
  import { wifiManager } from '@kit.ConnectivityKit';
  
  try {
    let config:wifiManager.WifiDeviceConfig = {
      ssid : "****",
      preSharedKey : "****",
      securityType : 0
    }
    wifiManager.addCandidateConfig(config).then(result => {
      console.info("result:" + JSON.stringify(result));
    }).catch((err:number) => {
      console.error("failed:" + JSON.stringify(err));
    });
  }catch(error){
    console.error("failed:" + JSON.stringify(error));
  }
```

## wifiManager.addCandidateConfig

addCandidateConfig(config: WifiDeviceConfig, callback: AsyncCallback&lt;number&gt;): void

Adds a candidate network configuration. This API uses an asynchronous callback to return the result.

- Adds the specified Wi-Fi as a candidate network. Automatic reconnection with the candidate network cannot be triggered without connection records. You can call [connectToCandidateConfig](#wifimanagerconnecttocandidateconfig) or [connectToCandidateConfigWithUserAction](#wifimanagerconnecttocandidateconfigwithuseraction20) to connect to the candidate network. After the connection is confirmed, automatic reconnection can be implemented.
- Candidate networks are added on the application level and are isolated from system network configurations. They are not displayed on the system Wi-Fi page.

**Required permissions**: ohos.permission.SET_WIFI_INFO

**System capability**: SystemCapability.Communication.WiFi.STA

**Atomic service API**: This API can be used in atomic services since API version 12.

**Parameters**

| Name | Type | Mandatory | Description |
| -------- | -------- | -------- | -------- |
| config | [WifiDeviceConfig](#wifideviceconfig) | Yes | Wi-Fi configuration information. The value of **bssidType** is a random device address by default. |
| callback | AsyncCallback&lt;number&gt; | Yes | Callback used to return the result. If **error** is **0**, the operation is successful. **data** indicates the ID of the network configuration to add. If **data** is **-1**, the network configuration fails to be added.<br /> If the value of **error** is not **0**, an error has occurred during the operation. |

**Error codes**

For details about the error codes, see [Wi-Fi Error Codes](errorcode-wifi.md) and [Universal Error Codes](../errorcode-universal.md).

| ID | Error Message |
| -------- | ---------------------------- |
| 201 | Permission denied.                 |
| 401 | Invalid parameters. Possible causes: 1. Mandatory parameters are left unspecified.<br>2. Incorrect parameter types. 3. Parameter verification failed.|
| 801 | Capability not supported.          |
| 2501000  | Operation failed.|

**Example**
```ts
  import { wifiManager } from '@kit.ConnectivityKit';

  try {
    let config:wifiManager.WifiDeviceConfig = {
      ssid : "****",
      preSharedKey : "****",
      securityType : 0
    }
    wifiManager.addCandidateConfig(config,(error,result) => {
      console.info("result:" + JSON.stringify(result));
    });  
  }catch(error){
    console.error("failed:" + JSON.stringify(error));
  }
```

## wifiManager.removeCandidateConfig

removeCandidateConfig(networkId: number): Promise&lt;void&gt;

Removes a candidate network configuration. This API uses an asynchronous callback to return the result.

- This API can be used to delete the configuration of the candidate Wi-Fi network with the specified network ID from the system to release system resources.
- Only candidate configurations added through [addCandidateConfig](#wifimanageraddcandidateconfig) can be removed. After removal, the candidate network will no longer be automatically connected by the system.

**Required permissions**: ohos.permission.SET_WIFI_INFO

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Communication.WiFi.STA

**Parameters**

  | Name | Type | Mandatory | Description |
  | -------- | -------- | -------- | -------- |
  | networkId | number | Yes | Network configuration ID. |

**Return value**

  | Type | Description |
  | -------- | -------- |
  | Promise&lt;void&gt; | Promise object that returns no result. |

**Error codes**

For details about the error codes, see [Wi-Fi Error Codes](errorcode-wifi.md) and [Universal Error Codes](../errorcode-universal.md).

| ID | Error Message |
| -------- | ---------------------------- |
| 201 | Permission denied.                 |
| 401 | Invalid parameters. Possible causes: 1. Mandatory parameters are left unspecified.<br>2. Incorrect parameter types. 3. Parameter verification failed.|
| 801 | Capability not supported.          |
| 2501000  | Operation failed.|
| 2501001  | Wi-Fi STA disabled. |

**Example**

```ts
  import { wifiManager } from '@kit.ConnectivityKit';

  try {
    let networkId = 0;
    wifiManager.removeCandidateConfig(networkId).then(result => {
      console.info("result:" + JSON.stringify(result));
    }).catch((err:number) => {
      console.error("failed:" + JSON.stringify(err));
    });
  }catch(error){
    console.error("failed:" + JSON.stringify(error));
  }
```

## wifiManager.removeCandidateConfig

removeCandidateConfig(networkId: number, callback: AsyncCallback&lt;void&gt;): void

Removes the specified candidate network configuration. This API uses an asynchronous callback to return the result.

- This API can be used to delete the configuration of the candidate Wi-Fi network with the specified network ID from the system to release system resources.
- Only candidate configurations added through [addCandidateConfig](#wifimanageraddcandidateconfig) can be removed. After removal, the candidate network will no longer be automatically connected by the system.

**Required permissions**: ohos.permission.SET_WIFI_INFO

**System capability**: SystemCapability.Communication.WiFi.STA

**Atomic service API**: This API can be used in atomic services since API version 12.

**Parameters**

  | Name | Type | Mandatory | Description |
  | -------- | -------- | -------- | -------- |
  | networkId | number | Yes | ID of the network configuration to remove. |
  | callback | AsyncCallback&lt;void&gt; | Yes | Callback used to return the result. If the operation is successful, **error** is **0**. If the operation fails, **error** is not **0**. |

**Error codes**

For details about the error codes, see [Wi-Fi Error Codes](errorcode-wifi.md) and [Universal Error Codes](../errorcode-universal.md).

| ID | Error Message |
| -------- | ---------------------------- |
| 201 | Permission denied.                 |
| 401 | Invalid parameters. Possible causes: 1. Mandatory parameters are left unspecified.<br>2. Incorrect parameter types. 3. Parameter verification failed. |
| 801 | Capability not supported.          |
| 2501000  | Operation failed.|
| 2501001  | Wi-Fi STA disabled. |

**Example**
```ts
  import { wifiManager } from '@kit.ConnectivityKit';

  try {
    let networkId = 0;
    wifiManager.removeCandidateConfig(networkId,(error,result) => {
    console.info("result:" + JSON.stringify(result));
    });  
  }catch(error){
    console.error("failed:" + JSON.stringify(error));
  }
```

## wifiManager.removeDevice<sup>15+</sup>

removeDevice(id: number): void

Removes a network configuration.

- Deletes the saved Wi-Fi network configuration information according to the network configuration ID.
- After removal, the corresponding network configuration is no longer available, and the device will no longer automatically connect to that network.

**Required permissions:** ohos.permission.SET_WIFI_INFO and (ohos.permission.MANAGE_WIFI_CONNECTION, available to system applications only, or ohos.permission.MANAGE_ENTERPRISE_WIFI_CONNECTION, available to enterprise applications only)

**System capability**: SystemCapability.Communication.WiFi.STA

**Parameters**

  | Name | Type | Mandatory | Description |
  | -------- | -------- | -------- | -------- |
  | id | number | Yes | Network configuration ID. |

**Error codes**

For details about the error codes, see [Wi-Fi Error Codes](errorcode-wifi.md) and [Universal Error Codes](../errorcode-universal.md).

| ID | Error Message |
| -------- | ---------------------------- |
| 201 | Permission denied.                 |
| 401 | Invalid parameters. Possible causes: 1. Mandatory parameters are left unspecified.<br>2. Incorrect parameter types. 3. Parameter verification failed. |
| 801 | Capability not supported.          |
| 2501000  | Operation failed.|
| 2501001  | Wi-Fi STA disabled. |

**Example**
```ts
  import { wifiManager } from '@kit.ConnectivityKit';
  
    try {
      let id = 0;
      wifiManager.removeDevice(id);  
    }catch(error){
      console.error("failed:" + JSON.stringify(error));
    }
```

## wifiManager.getCandidateConfigs

getCandidateConfigs(): &nbsp;Array&lt;WifiDeviceConfig&gt;

Obtains candidate network configurations.

- A candidate network refers to a network that has been connected to or manually added.
- This API obtains the configurations of all Wi-Fi networks that have been saved but are not connected to by the current application.
- This API is used to display a list of networks that can be connected to.

**Required permissions:**

Since API 10: ohos.permission.GET_WIFI_INFO

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Communication.WiFi.STA

**Return value**

  | Type | Description |
  | -------- | -------- |
  | &nbsp;Array&lt;[WifiDeviceConfig](#wifideviceconfig)&gt; | Array of candidate network configurations. |

**Error codes**

For details about the error codes, see [Wi-Fi Error Codes](errorcode-wifi.md) and [Universal Error Codes](../errorcode-universal.md).

| ID | Error Message |
| -------- | ---------------------------- |
| 201 | Permission denied.                 |
| 801 | Capability not supported.          |
| 2501000  | Operation failed.| 

**Example**

```ts
  import { wifiManager } from '@kit.ConnectivityKit';

  try {
    let configs = wifiManager.getCandidateConfigs();
    console.info("configs:" + JSON.stringify(configs));
    let len = configs.length;
        console.info("result len: " + len);
    if(len > 0){
      for (let i = 0; i < len; ++i) {
        console.info("ssid: " + configs[i].ssid);
        console.info("bssid: " + configs[i].bssid);
      }
    }  
  }catch(error){
    console.error("failed:" + JSON.stringify(error));
  }
  
```

## wifiManager.connectToCandidateConfig

connectToCandidateConfig(networkId: number): void

Connects to a candidate network added by the application.

**Required permissions**: ohos.permission.SET_WIFI_INFO

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Communication.WiFi.STA

**Parameters**

  | Name | Type | Mandatory | Description |
  | -------- | -------- | -------- | -------- |
  | networkId | number | Yes | ID of the candidate network configuration. |

**Error codes**

For details about the error codes, see [Wi-Fi Error Codes](errorcode-wifi.md) and [Universal Error Codes](../errorcode-universal.md).

| ID | Error Message |
| -------- | ---------------------------- |
| 201 | Permission denied.                 |
| 401 | Invalid parameters. Possible causes: 1. Mandatory parameters are left unspecified.<br>2. Incorrect parameter types. 3. Parameter verification failed. |
| 801 | Capability not supported.          |
| 2501000  | Operation failed.|
| 2501001  | Wi-Fi STA disabled.|

**Example**
```ts
  import { wifiManager } from '@kit.ConnectivityKit';

  try {
    let networkId = 0; // Candidate network ID, generated when the candidate network is added.
    wifiManager.connectToCandidateConfig(networkId);
  }catch(error){
    console.error("failed:" + JSON.stringify(error));
  }
  
```

## wifiManager.connectToCandidateConfig

connectToCandidateConfig(settings: ConnectSettings): Promise&lt;void&gt;

The application uses this API to connect to a candidate network added by itself, with support for custom parameters.

**Since**: 26.0.0

**Required permissions**: ohos.permission.SET_WIFI_INFO

**Atomic service API**: This API can be used in atomic services since API version 26.0.0.

**System capability**: SystemCapability.Communication.WiFi.STA

**Model restriction:** This API can be used only in the stage model.

**Parameters**

  | Name | Type | Mandatory | Description |
  | -------- | -------- | -------- | -------- |
  | settings | [ConnectSettings](#connectsettings) | Yes | Wi-Fi connection settings. |

 **Return value**

  | Type | Description |
  | -------- | -------- |
  | Promise&lt;void&gt; | Promise object, with no return result. |

**Error codes**

For details about the error codes, see [Wi-Fi Error Codes](errorcode-wifi.md) and [Universal Error Codes](../errorcode-universal.md).

| ID | Error Message |
| -------- | ---------------------------- |
| 201 | Permission denied.                 |
| 801 | Capability not supported.          |
| 2501000  | Operation failed.|
| 2501001  | Wi-Fi STA disabled.|
| 2501005  | The user does not respond.|
| 2501006  | The user refused the action.|
| 2501007  | Parameter validation failed.|

**Example**
```ts
  import { wifiManager } from '@kit.ConnectivityKit';

  try {
    let setting:wifiManager.ConnectSettings = { networkId: 0 }; // Candidate network ID, generated when adding a candidate network.
    wifiManager.connectToCandidateConfig(setting);
  }catch(error){
    console.error("failed:" + JSON.stringify(error));
  }
  
```

## wifiManager.connectToCandidateConfigWithUserAction<sup>20+</sup>

connectToCandidateConfigWithUserAction(networkId: number): Promise&lt;void&gt;

This API is used by an application to connect to a candidate network added by the user, and prompts the user for trust confirmation during connection. It uses a Promise for asynchronous callback.

- When this API is called, the system prompts the user to confirm whether to trust and connect to the specified candidate network.
- User confirmation is a necessary step in the connection process. The connection operation will not be performed until the user's confirmation is obtained.
- You are advised to trigger a Wi-Fi scan by calling the **startScan** API before initiating a connection, and then connect to the candidate network after the updated scan result is detected by using the [wifiManager.on('wifiScanStateChange')](#wifimanageronwifiscanstatechange) method. This improves the connection success rate.

> **NOTE**
> When [wifiManager.connectToCandidateConfig](#wifimanagerconnecttocandidateconfig) is called to connect to a candidate network, the user response result is not returned.

**Required permissions**: ohos.permission.SET_WIFI_INFO

**Atomic service API**: This API can be used in atomic services since API version 20.

**System capability**: SystemCapability.Communication.WiFi.STA

**Parameters**

  | Name | Type | Mandatory | Description |
  | -------- | -------- | -------- | -------- |
  | networkId | number | Yes | ID of the candidate network configuration. The ID cannot be less than 0. |

**Return value**

  | Type | Description |
  | -------- | -------- |
  | Promise&lt;void&gt; | Promise object, with no return result. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Wi-Fi Error Codes](errorcode-wifi.md).

| ID | Error message |
| -------- | ---------------------------- |
| 201 | Permission denied.                 |
| 801 | Capability not supported.          |
| 2501000  | Operation failed.|
| 2501001  | Wi-Fi STA disabled.|
| 2501005  | The user does not respond.|
| 2501006  | The user refused the action.|
| 2501007  | Parameter validation failed.|

**Example**
```ts
  import { wifiManager } from '@kit.ConnectivityKit';
  
  try {
    let networkId = 0; // Candidate network ID, generated when adding a candidate network.
    wifiManager.connectToCandidateConfigWithUserAction(networkId).then(result => {
      console.info("result:" + JSON.stringify(result));
    }).catch((err:number) => {
      console.error("failed:" + JSON.stringify(err));
    });
  }catch(error){  
    console.error("failed:" + JSON.stringify(error));
  }
```

## wifiManager.addDeviceConfig<sup>15+</sup>

addDeviceConfig(config: WifiDeviceConfig): Promise&lt;number&gt;

Adds network configuration. This API uses a promise to return the result.

**Required permissions**: ohos.permission.SET_WIFI_INFO and ohos.permission.SET_WIFI_CONFIG

**System capability**: SystemCapability.Communication.WiFi.STA

**Parameters**

| Name | Type | Mandatory | Description |
| -------- | -------- | -------- | -------- |
| config | [WifiDeviceConfig](#wifideviceconfig) | Yes | Wi-Fi configuration information. The value of **bssidType** is a random device address by default. |

**Return value**

  | Type | Description |
  | -------- | -------- |
  | Promise&lt;number&gt; | Promise object. Represents the network configuration ID. |

**Error codes**

For details about the error codes, see [Wi-Fi Error Codes](errorcode-wifi.md) and [Universal Error Codes](../errorcode-universal.md).

| ID | Error message |
| -------- | ---------------------------- |
| 201 | Permission denied.                 |
| 401 | Invalid parameters. Possible causes: 1. Mandatory parameters are left unspecified.<br>2. Incorrect parameter types. 3. Parameter verification failed.|
| 801 | Capability not supported.          |
| 2501000  | Operation failed.|
| 2501001  | Wi-Fi STA disabled.|

**Example**
```ts
  import { wifiManager } from '@kit.ConnectivityKit';
  
  try {
    let config:wifiManager.WifiDeviceConfig = {
      ssid : "****",
      preSharedKey : "****",
      securityType : 0
    }
    wifiManager.addDeviceConfig(config).then(result => {
      console.info("result:" + JSON.stringify(result));
    }).catch((err:number) => {
      console.error("failed:" + JSON.stringify(err));
    });
  }catch(error){  
    console.error("failed:" + JSON.stringify(error));
  }
```

## wifiManager.addDeviceConfig<sup>15+</sup>

addDeviceConfig(config: WifiDeviceConfig, callback: AsyncCallback&lt;number&gt;): void

Adds a network configuration. This API uses an asynchronous callback to return the result.

**Required permissions**: ohos.permission.SET_WIFI_INFO and ohos.permission.SET_WIFI_CONFIG

**System capability**: SystemCapability.Communication.WiFi.STA

**Parameters**

| Name | Type | Mandatory | Description |
| -------- | -------- | -------- | -------- |
| config | [WifiDeviceConfig](#wifideviceconfig) | Yes | Wi-Fi configuration information. The value of **bssidType** is a random device address by default. |
| callback | AsyncCallback&lt;number&gt; | Yes | Callback used to return the result. If the operation is successful, **error** is **0** and **data** is the network configuration ID. If **data** is **-1**, the candidate network configuration fails to be added. If **err** is not **0**, an error has occurred. |

**Error codes**

For details about the error codes, see [Wi-Fi Error Codes](errorcode-wifi.md) and [Universal Error Codes](../errorcode-universal.md).

| ID | Error message |
| -------- | ---------------------------- |
| 201 | Permission denied.                 |
| 401 | Invalid parameters. Possible causes: 1. Mandatory parameters are left unspecified.<br>2. Incorrect parameter types. 3. Parameter verification failed.|
| 801 | Capability not supported.          |
| 2501000  | Operation failed.|
| 2501001  | Wi-Fi STA disabled.|

**Example**
```ts
  import { wifiManager } from '@kit.ConnectivityKit';
  
    try {
      let config:wifiManager.WifiDeviceConfig = {
        ssid : "****",
        preSharedKey : "****",
        securityType : 0
      }
      wifiManager.addDeviceConfig(config,(error,result) => {
        console.info("result:" + JSON.stringify(result));
      });
    }catch(error){
      console.error("failed:" + JSON.stringify(error));
    }

```

## wifiManager.getDeviceConfigs<sup>15+</sup>

getDeviceConfigs(): &nbsp;Array&lt;WifiDeviceConfig&gt;

Obtains the network configuration.

**Required permissions**: ohos.permission.GET_WIFI_INFO and ohos.permission.GET_WIFI_CONFIG

**System capability**: SystemCapability.Communication.WiFi.STA

**Return value**

  | Type | Description |
  | -------- | -------- |
  | &nbsp;Array&lt;[WifiDeviceConfig](#wifideviceconfig)&gt; | Array of network configurations. |

**Error codes**

For details about the error codes, see [Wi-Fi Error Codes](errorcode-wifi.md) and [Universal Error Codes](../errorcode-universal.md).

| ID | Error message |
| -------- | ---------------------------- |
| 201 | Permission denied.                 |
| 801 | Capability not supported.          |
| 2501000  | Operation failed.| 

**Example**

```ts
  import { wifiManager } from '@kit.ConnectivityKit';
  
    try {
      let configs = wifiManager.getDeviceConfigs();
      console.info("configs:" + JSON.stringify(configs));
    }catch(error){
      console.error("failed:", error.code, error.message);
    }
  
```

## wifiManager.connectToNetwork<sup>15+</sup>

connectToNetwork(networkId: number): void

Connects the application to a hotspot using this API.

**Required permissions:** ohos.permission.MANAGE_WIFI_CONNECTION, available to system applications only, or ohos.permission.MANAGE_ENTERPRISE_WIFI_CONNECTION, available to enterprise applications only

**System capability**: SystemCapability.Communication.WiFi.STA

**Parameters**

  | Name | Type | Mandatory | Description |
  | -------- | -------- | -------- | -------- |
  | networkId | number | Yes | ID of the candidate network configuration. |

**Error codes**

For details about the error codes, see [Wi-Fi Error Codes](errorcode-wifi.md) and [Universal Error Codes](../errorcode-universal.md).

| ID | Error message |
| -------- | ---------------------------- |
| 201 | Permission denied.                 |
| 401 | Invalid parameters. Possible causes: 1. Mandatory parameters are left unspecified.<br>2. Incorrect parameter types. 3. Parameter verification failed. |
| 801 | Capability not supported.          |
| 2501000  | Operation failed.|
| 2501001  | Wi-Fi STA disabled.|

**Example**
```ts
  import { wifiManager } from '@kit.ConnectivityKit';
  
    try {
      let networkId = 0;
      wifiManager.connectToNetwork(networkId);
    }catch(error){
      console.error("failed:" + JSON.stringify(error));
    }
  
```

## wifiManager.getSignalLevel

getSignalLevel(rssi: number, band: number): number

Queries the Wi-Fi signal strength.

**Required permissions**: ohos.permission.GET_WIFI_INFO

**System capability**: SystemCapability.Communication.WiFi.STA

**Parameters**

  | Name | Type | Mandatory | Description |
  | -------- | -------- | -------- | -------- |
  | rssi | number | Yes | RSSI of the hotspot, in dBm. |
  | band | number | Yes | Frequency band of the Wi-Fi access point. The value **1** indicates 2.4 GHz, and the value **2** indicates 5 GHz. |

**Return value**

  | Type | Description |
  | -------- | -------- |
  | number | Signal strength, ranging from [0,&nbsp;4]. |

**Error codes**

For details about the error codes, see [Wi-Fi Error Codes](errorcode-wifi.md) and [Universal Error Codes](../errorcode-universal.md).

| ID | Error message |
| -------- | -------- |
| 201 | Permission denied.                 |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br>2. Incorrect parameter types. |
| 801 | Capability not supported.          |
| 2501000  | Operation failed.|

**Example**
```ts
  import { wifiManager } from '@kit.ConnectivityKit';

  try {
    let rssi = 0;
    let band = 0;
    let level = wifiManager.getSignalLevel(rssi,band);
    console.info("level:" + JSON.stringify(level));
  }catch(error){
    console.error("failed:" + JSON.stringify(error));
  }

```

## wifiManager.getLinkedInfo

getLinkedInfo(): Promise&lt;WifiLinkedInfo&gt;

Obtains Wi-Fi connection information. This API uses an asynchronous callback to return the result.

**Required permissions**: ohos.permission.GET_WIFI_INFO

> **NOTE**
> - If **macType** is set to **1** (device MAC address), you also need to apply for the **ohos.permission.GET_WIFI_LOCAL_MAC** permission to obtain the value of **macAddress**. (For API versions 8 to 15, this permission is available only to system applications. For API version 16 and later, this permission is available to common applications on PCs/2-in-1 devices, and is available only to system applications on other devices.) If the **ohos.permission.GET_WIFI_LOCAL_MAC** permission is not granted, no value is returned for **macAddress**.
> - If the application has the **ohos.permission.GET_WIFI_PEERS_MAC** permission, **bssid** in the return value is a real BSSID; otherwise, **bssid** is a random device address.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Communication.WiFi.STA

**Return value**

  | Type | Description |
  | -------- | -------- |
  | Promise&lt;[WifiLinkedInfo](#wifilinkedinfo)&gt; | Promise used to return the Wi-Fi connection information. |

**Error codes**

For details about the error codes, see [Wi-Fi Error Codes](errorcode-wifi.md) and [Universal Error Codes](../errorcode-universal.md).

| ID | Error Message |
| -------- | -------- |
| 201 | Permission denied.                 |
| 801 | Capability not supported.          |
| 2501000  | Operation failed.|
| 2501001  | Wi-Fi STA disabled.|

## wifiManager.getLinkedInfo

getLinkedInfo(callback: AsyncCallback&lt;WifiLinkedInfo&gt;): void

Obtains Wi-Fi connection information. This API uses an asynchronous callback to return the result.

**Required permissions**: ohos.permission.GET_WIFI_INFO

> **NOTE**
> - If **macType** is set to **1** (device MAC address), you also need to apply for the ohos.permission.GET_WIFI_LOCAL_MAC permission to obtain the value of **macAddress**. (For API versions 8 to 15, this permission is available only to system applications. For API version 16 and later, this permission is available to common applications on PCs/2-in-1 devices, and is available only to system applications on other devices.) If the ohos.permission.GET_WIFI_LOCAL_MAC permission is not granted, no value is returned for **macAddress**.
> - If the application has the ohos.permission.GET_WIFI_PEERS_MAC permission, **bssid** in the return value is a real BSSID; otherwise, **bssid** is a random device address.

**System capability**: SystemCapability.Communication.WiFi.STA

**Parameters**

  | Name | Type | Mandatory | Description |
  | -------- | -------- | -------- | -------- |
  | callback | AsyncCallback&lt;[WifiLinkedInfo](#wifilinkedinfo)&gt; | Yes | Callback used to return the result. If the operation is successful, **error** is **0** and **data** is the Wi-Fi connection information obtained. If the operation fails, **error** is not **0**. |

**Error codes**

For details about the error codes, see [Wi-Fi Error Codes](errorcode-wifi.md) and [Universal Error Codes](../errorcode-universal.md).

| ID | Error message |
| -------- | -------- |
| 201 | Permission denied.                 |
| 401 | Invalid parameters. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |
| 801 | Capability not supported.          |
| 2501000  | Operation failed.|
| 2501001  | Wi-Fi STA disabled.|

**Example**
```ts
import { wifiManager } from '@kit.ConnectivityKit';

wifiManager.getLinkedInfo().then((data: wifiManager.WifiLinkedInfo) => {
    console.info("get wifi linked info: " + JSON.stringify(data));
}).catch((error: Error) => {
    console.error("get linked info error: ", error);
});

```

## wifiManager.getLinkedInfoSync<sup>18+</sup>

getLinkedInfoSync(): WifiLinkedInfo

Obtains Wi-Fi connection information. This API uses the synchronous method to return the result.

**Required permissions**: ohos.permission.GET_WIFI_INFO

> **NOTE**
> - If **macType** is set to **1** (device MAC address), you also need to apply for the ohos.permission.GET_WIFI_LOCAL_MAC permission to obtain the value of **macAddress**. (For API versions 8 to 15, this permission is available only to system applications. For API version 16 and later, this permission is available to common applications on PCs/2-in-1 devices, and is available only to system applications on other devices.) If the ohos.permission.GET_WIFI_LOCAL_MAC permission is not granted, no value is returned for **macAddress**.
> - If the application has the ohos.permission.GET_WIFI_PEERS_MAC permission, **bssid** in the return value is a real BSSID; otherwise, **bssid** is a random device address.

**System capability**: SystemCapability.Communication.WiFi.STA

**Return value**

  | Type | Description |
  | -------- | -------- |
  | [WifiLinkedInfo](#wifilinkedinfo) | Wi-Fi connection information. |

**Error codes**

For details about the error codes, see [Wi-Fi Error Codes](errorcode-wifi.md) and [Universal Error Codes](../errorcode-universal.md).

| ID | Error message |
| -------- | -------- |
| 201 | Permission denied.                 |
| 801 | Capability not supported.          |
| 2501000  | Operation failed.|
| 2501001  | Wi-Fi STA disabled.|

**Example**
```ts
  import { wifiManager } from '@kit.ConnectivityKit';
  try {
    let linkInfo = wifiManager.getLinkedInfoSync();
    console.info("get linked info:" + JSON.stringify(linkInfo));
  } catch(error) {
    console.error("get linked info failed:" + JSON.stringify(error));
  }
```

## WifiLinkedInfo

Provides information about a Wi-Fi connection.

**System capability**: SystemCapability.Communication.WiFi.STA

<!--Table: 20%; 15%; 8%; 8%; 49%-->
| Name | Type | Read-Only | Optional | Description |
| -------- | -------- | -------- | -------- | -------- |
| ssid | string | No | No | Service set identifier (SSID) of the hotspot, which is used to obtain the public name (name of the wireless network) of the Wi-Fi hotspot connected to the current device. The encoding format is UTF-8.<br>**Atomic service API:** This API can be used in atomic services since API version 12. |
| bssid | string | No | No | Basic service set identifier (BSSID) of the hotspot, which is the MAC address of the wireless network.<br>**Atomic service API:** This API can be used in atomic services since API version 12. |
| rssi | number | No | No | Received signal strength indicator (RSSI) of the hotspot, in dBm.<br>Received signal strength indicator (RSSI), in dBm. The standard value range ranges from –127 dBm to 0 dBm. In normal usage scenarios, the RSSI value ranges from –100 dBm (weak signal) to –30 dBm (strong signal). A value close to 0 dBm indicates an extremely strong signal.<br>**Atomic service API:** This API can be used in atomic services since API version 12. |
| band | number | No | No | Frequency band of the Wi-Fi access point. The value **1** indicates 2.4 GHz, and the value **2** indicates 5 GHz. |
| linkSpeed | number | No | No | Uplink speed of the Wi-Fi access point, in Mbit/s. |
| rxLinkSpeed<sup>10+</sup> | number | No | No | Downlink speed of the Wi-Fi access point, in Mbit/s |
| maxSupportedTxLinkSpeed<sup>10+</sup> | number | No | No | Maximum uplink speed supported, in Mbit/s |
| maxSupportedRxLinkSpeed<sup>10+</sup> | number | No | No | Maximum downlink speed supported, in Mbit/s |
| frequency | number | No | No | Frequency of the Wi-Fi access point.<br>**Atomic service API:** This API can be used in atomic services since API version 12. |
| isHidden | boolean | No | No | Whether the Wi-Fi access point is hidden. The value **true** indicates that the Wi-Fi access point is hidden; the value **false** indicates the opposite. |
| isRestricted | boolean | No | No | Whether data volume is restricted at the Wi-Fi access point. The value **true** indicates that data volume is restricted, and the value **false** indicates the opposite. |
| macType | number | No | No | MAC address type. The value **0** indicates a random MAC address, and the value **1** indicates device MAC address. |
| macAddress | string | No | No | MAC address of the device. |
| ipAddress | number | No | No | IP address of the Wi-Fi connection.<br>1. You can view the IP address in Wi-Fi connection information and in **Settings** > **About phone** > **Status**.<br>2. The **ipAddress** value is of the number type and needs to be converted to an IP address in dotted decimal notation (for example, **192.168.1.1**). For details, see [How do I obtain the IP address of the current device after it is connected to a Wi-Fi network?](https://developer.huawei.com/consumer/en/doc/harmonyos-faqs/faqs-connectivity-4).|
| connState | [ConnState](#connstate) | No | No | Wi-Fi connection status. |
| channelWidth<sup>10+</sup> | [WifiChannelWidth](#wifichannelwidth) | No | No | Channel bandwidth of the connected hotspot. |
| wifiStandard<sup>10+</sup> | [WifiStandard](#wifistandard10) | No | No | Highest Wi-Fi standard supported by the router. |
| supportedWifiCategory<sup>12+</sup> | [WifiCategory](#wificategory12) | No | No | Latest protocol version supported by the device after Wi-Fi is connected. |
| isHiLinkNetwork<sup>12+</sup> | boolean | No | No | Whether HiLink is supported by the hotspot. The value **true** indicates that HiLink is supported, and the value **false** indicates the opposite. |
| wifiLinkType<sup>18+</sup> | [WifiLinkType](#wifilinktype18) | No | Yes | Wi-Fi 7 connection type. |

## WifiLinkType<sup>18+</sup>

Enumerates the Wi-Fi 7 connection types.

**System capability**: SystemCapability.Communication.WiFi.STA

| Name | Value | Description |
| -------- | -------- | -------- |
| DEFAULT_LINK | 0 | Default connection type. |
| WIFI7_SINGLE_LINK | 1 | Wi-Fi 7 single-link connection. |
| WIFI7_MLSR | 2 | Wi-Fi 7 multi-link single-radio (MLSR) connection. |
| WIFI7_EMLSR | 3 | Wi-Fi 7 enhanced multi-link single-radio (EMLSR) connection. |
| WIFI7_STR | 4 | Wi-Fi 7 simultaneous transmit and receive (STR) connection. |

## ConnState

Enumerates the Wi-Fi connection statuses.

**System capability**: SystemCapability.Communication.WiFi.STA

| Name | Value | Description |
| -------- | -------- | -------- |
| SCANNING | 0 | The device is searching for available APs. |
| CONNECTING | 1 | A Wi-Fi connection is being established. |
| AUTHENTICATING | 2 | The Wi-Fi connection is being authenticated. |
| OBTAINING_IPADDR | 3 | The IP address of the Wi-Fi connection is being obtained. |
| CONNECTED | 4 | The Wi-Fi connection is established. |
| DISCONNECTING | 5 | The Wi-Fi connection is being disconnected. |
| DISCONNECTED | 6 | The Wi-Fi connection is disconnected. |
| UNKNOWN | 7 | The Wi-Fi connection fails to be established. |

## wifiManager.isConnected

isConnected(): boolean

Checks whether the Wi-Fi connection is established.

**Required permissions**: ohos.permission.GET_WIFI_INFO

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Communication.WiFi.STA

**Return value**

  | Type | Description |
  | -------- | -------- |
  | boolean | true: connected, &nbsp;false: not connected. |

**Error codes**

For details about the error codes, see [Wi-Fi Error Codes](errorcode-wifi.md) and [Universal Error Codes](../errorcode-universal.md).

| ID | Error message |
| -------- | -------- |
| 201 | Permission denied.                 |
| 801 | Capability not supported.          |
| 2501000  | Operation failed.|

**Example**
```ts
  import { wifiManager } from '@kit.ConnectivityKit';

  try {
    let ret = wifiManager.isConnected();
    console.info("isConnected:" + ret);
  }catch(error){
    console.error("failed:" + JSON.stringify(error));
  }

```

## wifiManager.disconnect<sup>15+</sup>

disconnect(): void

Disconnects the Wi-Fi connection.

**Required permissions:** ohos.permission.SET_WIFI_INFO and (ohos.permission.MANAGE_WIFI_CONNECTION, System applications only, or
   ohos.permission.MANAGE_ENTERPRISE_WIFI_CONNECTION, Enterprise applications only)

**System capability**: SystemCapability.Communication.WiFi.STA

**Error codes**

For details about the error codes, see [Wi-Fi Error Codes](errorcode-wifi.md) and [Universal Error Codes](../errorcode-universal.md).

| ID | Error message |
| -------- | -------- |
| 201 | Permission denied.                 |
| 801 | Capability not supported.          |
| 2501000  | Operation failed.|
| 2501001  | Wi-Fi STA disabled.|

**Example**
```ts
  import { wifiManager } from '@kit.ConnectivityKit';

  try {
    wifiManager.disconnect();
  }catch(error){
    console.error("failed:" + JSON.stringify(error));
  }

```

## wifiManager.isFeatureSupported

isFeatureSupported(featureId: number): boolean

Checks whether the device supports the specified Wi-Fi feature.

**Required permissions**: ohos.permission.GET_WIFI_INFO

**System capability**: SystemCapability.Communication.WiFi.Core

**Parameters**

  | Name | Type | Mandatory | Description |
  | -------- | -------- | -------- | -------- |
  | featureId | number | Yes | Feature ID value. |

**Feature ID value enumeration:**

| Enumeration Value | Description |
| -------- | -------- |
| 0x0001 | Infrastructure mode feature. |
| 0x0002 | 5&nbsp;GHz bandwidth feature. |
| 0x0004 | GAS/ANQP feature. |
| 0x0008 | Wi-Fi Direct feature. |
| 0x0010 | Soft&nbsp;AP feature. |
| 0x0040 | Wi-Fi&nbsp;Aware networking feature. |
| 0x8000 | AP&nbsp;STA coexistence feature. |
| 0x8000000 | WPA3-Personal&nbsp;SAE feature. |
| 0x10000000 | WPA3-Enterprise&nbsp;Suite-B. |
| 0x20000000 | Enhanced open feature. |

**Return value**

  | Type | Description |
  | -------- | -------- |
  | boolean | true: supported, &nbsp;false: not supported. |

**Error codes**

For details about the error codes, see [Wi-Fi Error Codes](errorcode-wifi.md) and [Universal Error Codes](../errorcode-universal.md).

| ID | Error Message |
| -------- | -------- |
| 201 | Permission denied.                 |
| 401 | Invalid parameters. Possible causes: 1. Mandatory parameters are left unspecified.<br>2. Incorrect parameter types. |
| 801 | Capability not supported.          |
| 2401000  | Operation failed.|

**Example**
```ts
  import { wifiManager } from '@kit.ConnectivityKit';

  try {
    let featureId = 0;
    let ret = wifiManager.isFeatureSupported(featureId);
    console.info("isFeatureSupported:" + ret);
  }catch(error){
    console.error("failed:" + JSON.stringify(error));
  }

```

## wifiManager.getDeviceMacAddress<sup>15+</sup>

getDeviceMacAddress(): string[]

Obtains the MAC address of the device.

**Required permissions**: ohos.permission.GET_WIFI_LOCAL_MAC and ohos.permission.GET_WIFI_INFO

The **ohos.permission.GET_WIFI_LOCAL_MAC** permission is available only to system applications from API 8 to API 15. Starting from API 16, it is available to common applications on PC/2-in-1 devices, while on other devices it remains available only to system applications.

**System capability**: SystemCapability.Communication.WiFi.STA

**Return value**

  | Type | Description |
  | -------- | -------- |
  | string[] | MAC address. |

**Error codes**

For details about the error codes, see [Wi-Fi Error Codes](errorcode-wifi.md) and [Universal Error Codes](../errorcode-universal.md).

| ID | Error Message |
| -------- | -------- |
| 201 | Permission denied.                 |
| 801 | Capability not supported.          |
| 2501000  | Operation failed.|
| 2501001  | Wi-Fi STA disabled.|

**Example**
```ts
  import { wifiManager } from '@kit.ConnectivityKit';

  try {
    let ret = wifiManager.getDeviceMacAddress();
    console.info("deviceMacAddress:" + JSON.stringify(ret));
  }catch(error){
    console.error("failed:" + JSON.stringify(error));
  }

```


## wifiManager.getIpInfo

getIpInfo(): IpInfo

Obtains IPv4 information.

**Required permissions**: ohos.permission.GET_WIFI_INFO

**System capability**: SystemCapability.Communication.WiFi.STA

**Return value**

  | Type | Description |
  | -------- | -------- |
  | [IpInfo](#ipinfo) | IP information. |

**Error codes**

For details about the error codes, see [Wi-Fi Error Codes](errorcode-wifi.md) and [Universal Error Codes](../errorcode-universal.md).

| ID | Error message |
| -------- | -------- |
| 201 | Permission denied.                 |
| 801 | Capability not supported.          |
| 2501000  | Operation failed.|

**Example**
```ts
  import { wifiManager } from '@kit.ConnectivityKit';

  try {
    let info = wifiManager.getIpInfo();
    console.info("info:" + JSON.stringify(info));
  }catch(error){
    console.error("failed:" + JSON.stringify(error));
  }
```

## IpInfo

IPv4 information.

**System capability**: SystemCapability.Communication.WiFi.STA

| Name | Type | Read-Only | Optional | Description |
| -------- | -------- | -------- | -------- | -------- |
| ipAddress | number | No | No | IP address. (The **ipAddress** value is of the number type and needs to be converted to the common IP address format. For details, see [How do I obtain the IP address of the current device after it is connected to a Wi-Fi network?](https://developer.huawei.com/consumer/en/doc/harmonyos-faqs/faqs-connectivity-4). |
| gateway | number | No | No | Gateway. |
| netmask | number | No | No | Netmask. |
| primaryDns | number | No | No | IP address of the primary DNS server. |
| secondDns | number | No | No | IP address of the secondary DNS server. |
| serverIp | number | No | No | IP address of the DHCP server. |
| leaseDuration | number | No | No | IP address lease duration, in seconds. |


## wifiManager.getIpv6Info<sup>10+</sup>

getIpv6Info(): Ipv6Info

Obtains IPv6 information.

**Required permissions**: ohos.permission.GET_WIFI_INFO

**System capability**: SystemCapability.Communication.WiFi.STA

**Return value**

| Type | Description |
| -------- | -------- |
| [Ipv6Info](#ipv6info10) | IPv6 information. |

**Error codes**

For details about the error codes, see [Wi-Fi Error Codes](errorcode-wifi.md) and [Universal Error Codes](../errorcode-universal.md).

| ID | Error message |
| -------- | -------- |
| 201 | Permission denied.                 |
| 801 | Capability not supported.          |
| 2501000  | Operation failed.|

**Example**
```ts
  import { wifiManager } from '@kit.ConnectivityKit';

  try {
    let info = wifiManager.getIpv6Info();
    console.info("info:" + JSON.stringify(info));
  }catch(error){
    console.error("failed:" + JSON.stringify(error));
  }
```
## Ipv6Info<sup>10+</sup>

IPv6 information.

**System capability**: SystemCapability.Communication.WiFi.STA

| Name | Type | Read-Only | Optional | Description |
| -------- | -------- | -------- | -------- | -------- |
| linkIpv6Address | string | No | No | Link IPv6 address. |
| globalIpv6Address | string | No | No | Global IPv6 address. |
| randomGlobalIpv6Address | string | No | No | Random global IPv6 address. Reserved field, not supported yet. |
| uniqueIpv6Address<sup>12+</sup> | string | No | Yes | Unique local IPv6 address. |
| randomUniqueIpv6Address<sup>12+</sup> | string | No | Yes | Random unique local IPv6 address. |
| gateway | string | No | No | Gateway. |
| netmask | string | No | No | Netmask. |
| primaryDNS | string | No | No | IPv6 address of the primary DNS server. |
| secondDNS | string | No | No | IPv6 address of the secondary DNS server. |

## wifiManager.getCountryCode

getCountryCode(): string

Obtains the country code.

**Required permissions**: ohos.permission.GET_WIFI_INFO

**System capability**: SystemCapability.Communication.WiFi.Core

**Return value**

  | Type | Description |
  | -------- | -------- |
  | string | Country code. |

**Error codes**

For details about the error codes, see [Wi-Fi Error Codes](errorcode-wifi.md) and [Universal Error Codes](../errorcode-universal.md).

| ID | Error message |
| -------- | -------- |
| 201 | Permission denied.                 |
| 801 | Capability not supported.          |
| 2401000  | Operation failed.|

**Example**
```ts
  import { wifiManager } from '@kit.ConnectivityKit';

  try {
    let code = wifiManager.getCountryCode();
    console.info("code:" + code);
  }catch(error){
    console.error("failed:" + JSON.stringify(error));
  }
```

## wifiManager.isBandTypeSupported<sup>10+</sup>

isBandTypeSupported(bandType: WifiBandType): boolean

Checks whether the current band is supported.

**Required permissions**: ohos.permission.GET_WIFI_INFO.

**System capability**: SystemCapability.Communication.WiFi.STA

**Parameters**

  | Name | Type | Mandatory | Description |
  | -------- | -------- | -------- | -------- |
  | bandType | [WifiBandType](#wifibandtype10) | Yes | Wi-Fi band type. |

**Return value**

  | Type | Description |
  | -------- | -------- |
  | boolean | true: supported, &nbsp;false: not supported. |

**Error codes**

For details about the error codes, see [Wi-Fi Error Codes](errorcode-wifi.md) and [Universal Error Codes](../errorcode-universal.md).

| ID | Error Message |
| -------- | -------- |
| 201 | Permission denied.                 |
| 801 | Capability not supported.          |
| 2501000  | Operation failed.|

**Example**
```ts
  import { wifiManager } from '@kit.ConnectivityKit';

  try {
    let type = 0;
    let isBandTypeSupported = wifiManager.isBandTypeSupported(type);
    console.info("isBandTypeSupported:" + isBandTypeSupported);    
  }catch(error){
    console.error("failed:" + JSON.stringify(error));
  }
```


## wifiManager.isMeteredHotspot<sup>11+</sup>

isMeteredHotspot(): boolean

Queries whether the Wi-Fi network currently connected to the device is a mobile hotspot.

**Required permissions**: ohos.permission.GET_WIFI_INFO

**System capability**: SystemCapability.Communication.WiFi.STA

**Return value**

  | Type | Description |
  | -------- | -------- |
  | boolean | **true**: The Wi-Fi network is a mobile hotspot. **false**: The Wi-Fi network is not a mobile hotspot. |

**Error codes**

For details about the error codes, see [Wi-Fi Error Codes](errorcode-wifi.md) and [Universal Error Codes](../errorcode-universal.md).

| ID | Error message |
| -------- | -------- |
| 201 | Permission denied.                 |
| 801 | Capability not supported.          |
| 2501000  | Operation failed.|
| 2501001  | Wi-Fi STA disabled. |

**Example**

```ts
  import { wifiManager } from '@kit.ConnectivityKit';

  try {
    let isMeteredHotspot = wifiManager.isMeteredHotspot();
    console.info("isMeteredHotspot:" + isMeteredHotspot);
  }catch(error){
    console.error("failed:" + JSON.stringify(error));
  }
```


## wifiManager.isHotspotActive<sup>15+</sup>

isHotspotActive(): boolean

Checks whether the hotspot is enabled.

**Required permissions**: ohos.permission.GET_WIFI_INFO

**System capability**: SystemCapability.Communication.WiFi.AP.Core

**Return value**

  | Type | Description |
  | -------- | -------- |
  | boolean | Whether the hotspot is enabled. **true**: enabled, &nbsp;**false**: disabled.|

**Error codes**

For details about the error codes, see [Wi-Fi Error Codes](errorcode-wifi.md) and [Universal Error Codes](../errorcode-universal.md).

| ID | Error message |
| -------- | -------- |
| 201 | Permission denied.                 |
| 801 | Capability not supported.          |
| 2601000  | Operation failed. |

**Example**
```ts
  import { wifiManager } from '@kit.ConnectivityKit';

  try {
    let ret = wifiManager.isHotspotActive();
    console.info("result:" + ret);    
  } catch(error) {
    console.error("failed:" + JSON.stringify(error));
  }
```


## wifiManager.getP2pLinkedInfo

getP2pLinkedInfo(): Promise&lt;WifiP2pLinkedInfo&gt;

Obtains P2P connection information. This API uses an asynchronous callback to return the result.

**Required permissions**: ohos.permission.GET_WIFI_INFO

To obtain **groupOwnerAddr**, the application must also have the **ohos.permission.GET_WIFI_LOCAL_MAC** permission (available only to system applications from API 8 to API 15. Starting from API 16, it is available to normal applications on PC/2-in-1 devices, and remains available only to system applications on other devices). Without this permission, **groupOwnerAddr** returns an all-zero address.

**System capability**: SystemCapability.Communication.WiFi.P2P

**Return value**

  | Type | Description |
  | -------- | -------- |
  | Promise&lt;[WifiP2pLinkedInfo](#wifip2plinkedinfo)&gt; | Promise object. Represents the P2P connection information. |

**Error codes**

For details about the error codes, see [Wi-Fi Error Codes](errorcode-wifi.md) and [Universal Error Codes](../errorcode-universal.md).

| ID | Error message |
| -------- | -------- |
| 201 | Permission denied.                 |
| 801 | Capability not supported.          |
| 2801000  | Operation failed. |


## wifiManager.getP2pLinkedInfo

getP2pLinkedInfo(callback: AsyncCallback&lt;WifiP2pLinkedInfo&gt;): void

Obtains the P2P connection information. This API uses an asynchronous callback to return the result.

**Required permissions**: ohos.permission.GET_WIFI_INFO

To obtain **groupOwnerAddr**, the application must also have the **ohos.permission.GET_WIFI_LOCAL_MAC** permission (from API 8 to API 15, this permission is available only to system applications. Starting from API 16, it is available to normal applications on PC/2-in-1 devices, while on other devices it remains available only to system applications). Without this permission, **groupOwnerAddr** returns an all-zero address.

**System capability**: SystemCapability.Communication.WiFi.P2P

**Parameters**

  | Parameter | Type | Mandatory | Description |
  | -------- | -------- | -------- | -------- |
  | callback | AsyncCallback&lt;[WifiP2pLinkedInfo](#wifip2plinkedinfo)&gt; | Yes | Callback function. If the operation is successful, **err** is 0 and **data** represents the P2P connection information. If **err** is not 0, an error occurs during processing. |

**Error codes**

For details about the error codes, see [Wi-Fi Error Codes](errorcode-wifi.md) and [Universal Error Codes](../errorcode-universal.md).

| ID | Error message |
| -------- | -------- |
| 201 | Permission denied.                 |
| 801 | Capability not supported.          |
| 2801000  | Operation failed. |
| 2801001  | Wi-Fi STA disabled. |

**Example**
```ts
  import { wifiManager } from '@kit.ConnectivityKit';

  wifiManager.getP2pLinkedInfo((err, data:wifiManager.WifiP2pLinkedInfo) => {
    if (err) {
        console.error("get p2p linked info error");
        return;
    }
    console.info("get wifi p2p linked info: " + JSON.stringify(data));
  });

  wifiManager.getP2pLinkedInfo().then(data => {
    console.info("get wifi p2p linked info: " + JSON.stringify(data));
  });
```


## WifiP2pLinkedInfo

Provides information about a Wi-Fi connection.

**System capability**: SystemCapability.Communication.WiFi.P2P

| Name | Type | Read-Only | Optional | Description |
| -------- | -------- | -------- | -------- | -------- |
| connectState | [P2pConnectState](#p2pconnectstate) | No | No | P2P connection status. |
| isGroupOwner | boolean | No | No | **true** indicates that the device is the group owner, and **false** indicates otherwise. |
| groupOwnerAddr | string | No | No | Group IP address. |


## P2pConnectState

Enumerates the P2P connection states.

**System capability**: SystemCapability.Communication.WiFi.P2P

| Name | Value | Description |
| -------- | -------- | -------- |
| DISCONNECTED | 0 | Disconnected state. |
| CONNECTED | 1 | Connection status. |

## wifiManager.getCurrentGroup

getCurrentGroup(): Promise&lt;WifiP2pGroupInfo&gt;

Obtains the current P2P group information. This API uses a promise to return the result.

**Required permissions:**

Since API 10: ohos.permission.GET_WIFI_INFO

**System capability**: SystemCapability.Communication.WiFi.P2P

**Return value**

| Type | Description |
| -------- | -------- |
| Promise&lt;[WifiP2pGroupInfo](#wifip2pgroupinfo)&gt; | Promise object. Represents the current group information. If the application has the ohos.permission.GET_WIFI_PEERS_MAC permission, the deviceAddress in the returned result is the real device address; otherwise, it is a random device address. |

**Error codes**

For details about the error codes, see [Wi-Fi Error Codes](errorcode-wifi.md) and [Universal Error Codes](../errorcode-universal.md).

| ID | Error message |
| -------- | -------- |
| 201 | Permission denied.                 |
| 801 | Capability not supported.          |
| 2801000  | Operation failed. |

## wifiManager.getCurrentGroup

getCurrentGroup(callback: AsyncCallback&lt;WifiP2pGroupInfo&gt;): void

Obtains the current P2P group information. This API uses an asynchronous callback to return the result.

**Required permissions:**

From API 10: ohos.permission.GET_WIFI_INFO

**System capability**: SystemCapability.Communication.WiFi.P2P

**Parameters**

| Name | Type | Mandatory | Description |
| -------- | -------- | -------- | -------- |
| callback | AsyncCallback&lt;[WifiP2pGroupInfo](#wifip2pgroupinfo)&gt; | Yes | Callback used to return the result. If the operation is successful, **err** is **0** and **data** is the group information obtained. If the operation fails, **err** is not **0**. If the application has the **ohos.permission.GET_WIFI_PEERS_MAC** permission, **deviceAddress** in the return value is a real device address; otherwise, **deviceAddress** is a random device address. |

**Error codes**

For details about the error codes, see [Wi-Fi Error Codes](errorcode-wifi.md) and [Universal Error Codes](../errorcode-universal.md).

| ID | Error Message |
| -------- | -------- |
| 201 | Permission denied.                 |
| 801 | Capability not supported.          |
| 2801000  | Operation failed. |

**Example**
```ts
  import { wifiManager } from '@kit.ConnectivityKit';
  // The current group information can be obtained only after the P2P group is created or the connection is successful.
  wifiManager.getCurrentGroup((err, data:wifiManager.WifiP2pGroupInfo) => {
    if (err) {
        console.error("get current P2P group error");
        return;
    }
    console.info("get current P2P group: " + JSON.stringify(data));
  });

  wifiManager.getCurrentGroup().then(data => {
    console.info("get current P2P group: " + JSON.stringify(data));
  });
```

## wifiManager.getP2pPeerDevices

getP2pPeerDevices(): Promise&lt;WifiP2pDevice[]&gt;

Obtains the list of P2P peer devices. This API uses an asynchronous callback to return the result.

**Required permissions:**

From API 10: ohos.permission.GET_WIFI_INFO

**System capability**: SystemCapability.Communication.WiFi.P2P

**Return value**

| Type | Description |
| -------- | -------- |
| Promise&lt;[WifiP2pDevice[]](#wifip2pdevice)&gt; | Promise object. Represents the list of peer devices. If the application has the ohos.permission.GET_WIFI_PEERS_MAC permission, the deviceAddress in the returned result is the real device address; otherwise, it is a random device address. |

**Error codes**

For details about the error codes, see [Wi-Fi Error Codes](errorcode-wifi.md) and [Universal Error Codes](../errorcode-universal.md).

| ID | Error message |
| -------- | -------- |
| 201 | Permission denied.                 |
| 801 | Capability not supported.          |
| 2801000  | Operation failed. |

## wifiManager.getP2pPeerDevices

getP2pPeerDevices(callback: AsyncCallback&lt;WifiP2pDevice[]&gt;): void

Obtains the P2P peer device list information. This API uses an asynchronous callback.

**Required permissions:**

Since API 10: ohos.permission.GET_WIFI_INFO

**System capability**: SystemCapability.Communication.WiFi.P2P

**Parameters**

| Name | Type | Mandatory | Description |
| -------- | -------- | -------- | -------- |
| callback | AsyncCallback&lt;[WifiP2pDevice[]](#wifip2pdevice)&gt; | Yes | Callback function. If the operation is successful, **err** is 0 and **data** represents the peer device list information. If **err** is not 0, an error occurs during processing. If the application has applied for the ohos.permission.GET_WIFI_PEERS_MAC permission, the **deviceAddress** in the returned result is the real device address; otherwise, it is a random device address. |

**Error codes**

For details about the error codes, see [Wi-Fi Error Codes](errorcode-wifi.md) and [Universal Error Codes](../errorcode-universal.md).

| ID | Error message |
| -------- | -------- |
| 201 | Permission denied.                 |
| 801 | Capability not supported.          |
| 2801000  | Operation failed. |
| 2801001  | Wi-Fi STA disabled. |

**Example**
```ts
  import { wifiManager } from '@kit.ConnectivityKit';
  // The P2P peer device list information can be obtained only after the P2P discovery phase is complete.
  wifiManager.getP2pPeerDevices((err, data:wifiManager.WifiP2pDevice[]) => {
    if (err) {
        console.error("get P2P peer devices error");
        return;
    }
    console.info("get P2P peer devices: " + JSON.stringify(data));
  });

  wifiManager.getP2pPeerDevices().then(data => {
    console.info("get P2P peer devices: " + JSON.stringify(data));
  });
```

## WifiP2pDevice

Represents P2P device information.

**System capability**: SystemCapability.Communication.WiFi.P2P

| Name | Type | Read-Only | Optional | Description |
| -------- | -------- | -------- | -------- | -------- |
| deviceName | string | No | No | Device name. |
| deviceAddress | string | No | No | Device MAC address. |
| deviceAddressType<sup>10+</sup> | [DeviceAddressType](#deviceaddresstype10) | No | Yes | Device MAC address type. |
| primaryDeviceType | string | No | No | Primary device type. |
| deviceStatus | [P2pDeviceStatus](#p2pdevicestatus) | No | No | Device status. |
| groupCapabilities | number | No | No | Group capabilities. |


## P2pDeviceStatus

Enumerates the device status.

**System capability**: SystemCapability.Communication.WiFi.P2P

| Name | Value | Description |
| -------- | -------- | -------- |
| CONNECTED | 0 | Connection status. |
| INVITED | 1 | Invited status. |
| FAILED | 2 | Failed status. |
| AVAILABLE | 3 | Available status. |
| UNAVAILABLE | 4 | Unavailable status. |


## wifiManager.getP2pLocalDevice

getP2pLocalDevice(): Promise&lt;WifiP2pDevice&gt;

Obtains the local P2P device information. This API uses an asynchronous callback to return the result.

**Required permissions:** 

From API 11: ohos.permission.GET_WIFI_INFO

**System capability**: SystemCapability.Communication.WiFi.P2P

**Return value**

  | Type | Description |
  | -------- | -------- |
  | Promise&lt;[WifiP2pDevice](#wifip2pdevice)&gt; | Promise object. Represents the local device information. |

**Error codes**

For details about the error codes, see [Wi-Fi Error Codes](errorcode-wifi.md) and [Universal Error Codes](../errorcode-universal.md).

| ID | Error Message |
| -------- | -------- |
| 201 | Permission denied.                 |
| 801 | Capability not supported.          |
| 2801000  | Operation failed. |

## wifiManager.getP2pLocalDevice

getP2pLocalDevice(callback: AsyncCallback&lt;WifiP2pDevice&gt;): void

Obtains the local P2P device information. This API uses an asynchronous callback to return the result.

**Required permissions:**

From API 11: ohos.permission.GET_WIFI_INFO

**System capability**: SystemCapability.Communication.WiFi.P2P

**Parameters**

  | Name | Type | Mandatory | Description |
  | -------- | -------- | -------- | -------- |
  | callback | AsyncCallback&lt;[WifiP2pDevice](#wifip2pdevice)&gt; | Yes | Callback used to return the result. If the operation is successful, **err** is **0** and **data** is the local device information obtained. If the operation fails, **err** is not **0**. |

**Error codes**

| ID | Error message |
| -------- | -------- |
| 201 | Permission denied.                 |
| 801 | Capability not supported.          |
| 2801000  | Operation failed. |
| 2801001  | Wi-Fi STA disabled. |

**Example**
```ts
  import { wifiManager } from '@kit.ConnectivityKit';
  // The local device information can be obtained only after a P2P group is created or a connection is established.
  wifiManager.getP2pLocalDevice((err, data:wifiManager.WifiP2pDevice) => {
    if (err) {
        console.error("get P2P local device error");
        return;
    }
    console.info("get P2P local device: " + JSON.stringify(data));
  });

  wifiManager.getP2pLocalDevice().then(data => {
    console.info("get P2P local device: " + JSON.stringify(data));
  });
```

## wifiManager.createGroup

createGroup(config: WifiP2PConfig): void

Creates a P2P group. After a group is created, you can call [removeGroup](#wifimanagerremovegroup) to remove the group.

**Required permissions**: ohos.permission.GET_WIFI_INFO

**System capability**: SystemCapability.Communication.WiFi.P2P

**Parameters**

| Name | Type | Mandatory | Description |
| -------- | -------- | -------- | -------- |
| config | [WifiP2PConfig](#wifip2pconfig) | Yes | Group configuration information. If **DeviceAddressType** is not specified, it defaults to the random device address type. |

**Error codes**

For details about the error codes, see [Wi-Fi Error Codes](errorcode-wifi.md) and [Universal Error Codes](../errorcode-universal.md).

| ID | Error Message |
| -------- | -------- |
| 201 | Permission denied.                 |
| 401 | Invalid parameters. Possible causes: 1. Incorrect parameter types.<br>2. Parameter verification failed. |
| 801 | Capability not supported.          |
| 2801000  | Operation failed. |
| 2801001  | Wi-Fi STA disabled. |

**Example**
```ts
  import { wifiManager } from '@kit.ConnectivityKit';

  try {
    let config:wifiManager.WifiP2PConfig = {
      deviceAddress: "****",
      netId: 0,
      passphrase: "*****",
      groupName: "****",
      goBand: 0
    }
    wifiManager.createGroup(config);  
    
  }catch(error){
    console.error("failed:" + JSON.stringify(error));
  }
```

## WifiP2PConfig

Represents the P2P configuration information.

**System capability**: SystemCapability.Communication.WiFi.P2P

| Name | Type | Read-Only | Optional | Description |
| -------- | -------- | -------- | -------- | -------- |
| deviceAddress | string | No | No | Device address. |
| deviceAddressType<sup>10+</sup>| [DeviceAddressType](#deviceaddresstype10) | No | Yes | Device address type. |
| netId | number | No | No | Network ID. When creating a group, -1 indicates creating a temporary group, and -2 indicates creating a permanent group. |
| passphrase | string | No | No | Group key. |
| groupName | string | No | No | Group name. |
| goBand | [GroupOwnerBand](#groupownerband) | No | No | Group bandwidth. |
| goFreq<sup>23+</sup> | number | No | Yes | Group frequency. If both the group bandwidth and group frequency are added, when the frequency is valid (a frequency within the range of 2400 MHz to 2500 MHz or 4900 MHz to 5900 MHz is considered valid), the frequency takes precedence; otherwise, the bandwidth takes precedence. |


## GroupOwnerBand

Enumerates the group owner bandwidth.

**System capability**: SystemCapability.Communication.WiFi.P2P

| Name | Value | Description |
| -------- | -------- | -------- |
| GO_BAND_AUTO | 0 | Auto. |
| GO_BAND_2GHZ | 1 | 2.4 GHz. |
| GO_BAND_5GHZ | 2 | 5 GHz. |


## wifiManager.removeGroup

removeGroup(): void

Removes a group.

**Required permissions**: ohos.permission.GET_WIFI_INFO

**System capability**: SystemCapability.Communication.WiFi.P2P

**Error codes**

For details about the error codes, see [Wi-Fi Error Codes](errorcode-wifi.md) and [Universal Error Codes](../errorcode-universal.md).

| ID | Error message |
| -------- | -------- |
| 201 | Permission denied.                 |
| 801 | Capability not supported.          |
| 2801000  | Operation failed. |
| 2801001  | Wi-Fi STA disabled. |

**Example**
```ts
  import { wifiManager } from '@kit.ConnectivityKit';

  try {
    wifiManager.removeGroup();  
  }catch(error){
    console.error("failed:" + JSON.stringify(error));
  }
```

## wifiManager.p2pConnect

p2pConnect(config: WifiP2PConfig): void

Sets up a P2P connection. You can call [p2pCancelConnect](#wifimanagerp2pcancelconnect) to cancel the connection.

**Required permissions:**

From API 10: ohos.permission.GET_WIFI_INFO

**System capability**: SystemCapability.Communication.WiFi.P2P

**Parameters**

| Name | Type | Mandatory | Description |
| -------- | -------- | -------- | -------- |
| config | [WifiP2PConfig](#wifip2pconfig) | Yes | Connection configuration information. If **DeviceAddressType** is not specified, it defaults to the random device address type. |

**Error codes**

For details about the error codes, see [Wi-Fi Error Codes](errorcode-wifi.md) and [Universal Error Codes](../errorcode-universal.md).

| ID | Error Message |
| -------- | -------- |
| 201 | Permission denied.                 |
| 401 | Invalid parameters. Possible causes: 1. Incorrect parameter types.<br>2. Parameter verification failed. |
| 801 | Capability not supported.          |
| 2801000  | Operation failed. |
| 2801001  | Wi-Fi STA disabled. |

**Example**
```ts
  import { wifiManager } from '@kit.ConnectivityKit';
  
  let recvP2pConnectionChangeFunc = (result:wifiManager.WifiP2pLinkedInfo) => {
      console.info("p2p connection change receive event: " + JSON.stringify(result));
      wifiManager.getP2pLinkedInfo((err, data:wifiManager.WifiP2pLinkedInfo) => {
          if (err) {
              console.error('failed to get getP2pLinkedInfo: ' + JSON.stringify(err));
              return;
          }
          console.info("get getP2pLinkedInfo: " + JSON.stringify(data));
      });
  }
  wifiManager.on("p2pConnectionChange", recvP2pConnectionChangeFunc);
  
  let recvP2pDeviceChangeFunc = (result:wifiManager.WifiP2pDevice) => {
      console.info("p2p device change receive event: " + JSON.stringify(result));
  }
  wifiManager.on("p2pDeviceChange", recvP2pDeviceChangeFunc);
  
  let recvP2pPeerDeviceChangeFunc = (result:wifiManager.WifiP2pDevice[]) => {
      console.info("p2p peer device change receive event: " + JSON.stringify(result));
      wifiManager.getP2pPeerDevices((err, data:wifiManager.WifiP2pDevice[]) => {
          if (err) {
              console.error('failed to get peer devices: ' + JSON.stringify(err));
              return;
          }
          console.info("get peer devices: " + JSON.stringify(data));
          let len = data.length;
          for (let i = 0; i < len; ++i) {
              if (data[i].deviceName === "my_test_device") {
                  console.info("p2p connect to test device: " + data[i].deviceAddress);
                  let config:wifiManager.WifiP2PConfig = {
                      deviceAddress:data[i].deviceAddress,
                      netId:-2,
                      passphrase:"",
                      groupName:"",
                      goBand:0,
                  }
                  wifiManager.p2pConnect(config);
              }
          }
      });
  }
  wifiManager.on("p2pPeerDeviceChange", recvP2pPeerDeviceChangeFunc);
  
  let recvP2pPersistentGroupChangeFunc = () => {
      console.info("p2p persistent group change receive event");
  
      wifiManager.getCurrentGroup((err, data:wifiManager.WifiP2pGroupInfo) => {
          if (err) {
              console.error('failed to get current group: ' + JSON.stringify(err));
              return;
          }
          console.info("get current group: " + JSON.stringify(data));
      });
  }
  wifiManager.on("p2pPersistentGroupChange", recvP2pPersistentGroupChangeFunc);
  
  setTimeout(() => {wifiManager.off("p2pConnectionChange", recvP2pConnectionChangeFunc);}, 125 * 1000);
  setTimeout(() =>  {wifiManager.off("p2pDeviceChange", recvP2pDeviceChangeFunc);}, 125 * 1000);
  setTimeout(() =>  {wifiManager.off("p2pPeerDeviceChange", recvP2pPeerDeviceChangeFunc);}, 125 * 1000);
  setTimeout(() =>  {wifiManager.off("p2pPersistentGroupChange", recvP2pPersistentGroupChangeFunc);}, 125 * 1000);
  console.info("start discover devices -> " + wifiManager.startDiscoverDevices());
```

## wifiManager.p2pCancelConnect

p2pCancelConnect(): void

Cancels a P2P connection during the connection process.

**Required permissions**: ohos.permission.GET_WIFI_INFO 

**System capability**: SystemCapability.Communication.WiFi.P2P

**Error codes**

For details about the error codes, see [Wi-Fi Error Codes](errorcode-wifi.md) and [Universal Error Codes](../errorcode-universal.md).

| ID | Error message |
| -------- | -------- |
| 201 | Permission denied.                 |
| 801 | Capability not supported.          |
| 2801000  | Operation failed. |
| 2801001  | Wi-Fi STA disabled. |

**Example**
```ts
  import { wifiManager } from '@kit.ConnectivityKit';

  try {
    wifiManager.p2pCancelConnect();  
  }catch(error){
    console.error("failed:" + JSON.stringify(error));
  }
```

## wifiManager.startDiscoverDevices

startDiscoverDevices(): void

Starts to discover devices. You can call [stopDiscoverDevices](#wifimanagerstopdiscoverdevices) to stop discovering devices and release resources.

**Required permissions:**

Since API 10: ohos.permission.GET_WIFI_INFO

**System capability**: SystemCapability.Communication.WiFi.P2P

**Error codes**

For details about the error codes, see [Wi-Fi Error Codes](errorcode-wifi.md) and [Universal Error Codes](../errorcode-universal.md).

| ID | Error message |
| -------- | -------- |
| 201 | Permission denied.                 |
| 801 | Capability not supported.          |
| 2801000  | Operation failed. |
| 2801001  | Wi-Fi STA disabled. |

**Example**
```ts
  import { wifiManager } from '@kit.ConnectivityKit';

  try {
    wifiManager.startDiscoverDevices();  
  }catch(error){
    console.error("failed:" + JSON.stringify(error));
  }
```

## wifiManager.stopDiscoverDevices

stopDiscoverDevices(): void

Stops device discovery.

**Required permissions**: ohos.permission.GET_WIFI_INFO

**System capability**: SystemCapability.Communication.WiFi.P2P

**Error codes**

For details about the error codes, see [Wi-Fi Error Codes](errorcode-wifi.md) and [Universal Error Codes](../errorcode-universal.md).

| ID | Error message |
| -------- | -------- |
| 201 | Permission denied.                 |
| 801 | Capability not supported.          |
| 2801000  | Operation failed. |
| 2801001  | Wi-Fi STA disabled. |

**Example**
```ts
  import { wifiManager } from '@kit.ConnectivityKit';

  try {
    wifiManager.stopDiscoverDevices();  
  }catch(error){
    console.error("failed:" + JSON.stringify(error));
  }
```

## wifiManager.getMultiLinkedInfo<sup>18+</sup>

getMultiLinkedInfo(): &nbsp;Array&lt;WifiLinkedInfo&gt;

Obtains Wi-Fi connection information for multi-link operation (MLO).

**Required permissions**: ohos.permission.GET_WIFI_INFO

> **NOTE**
> - If **macType** is set to **1** (device MAC address), you also need to apply for the ohos.permission.GET_WIFI_LOCAL_MAC permission to obtain the value of **macAddress**. (For API versions 8 to 15, this permission is available only to system applications. For API version 16 and later, this permission is available to common applications on PCs/2-in-1 devices, and is available only to system applications on other devices.) If the ohos.permission.GET_WIFI_LOCAL_MAC permission is not granted, no value is returned for **macAddress**.
> - If the application has the ohos.permission.GET_WIFI_PEERS_MAC permission, **bssid** in the return value is a real BSSID; otherwise, **bssid** is a random device address.

**System capability**: SystemCapability.Communication.WiFi.STA

**Return value**

  | Type | Description |
  | -------- | -------- |
  | &nbsp;Array&lt;[WifiLinkedInfo](#wifilinkedinfo)&gt; | Wi-Fi connection information. |

**Error codes**

For details about the error codes, see [Wi-Fi Error Codes](errorcode-wifi.md) and [Universal Error Codes](../errorcode-universal.md).

| ID | Error Message |
| -------- | -------- |
| 201 | Permission denied. |
| 801 | Capability not supported. |
| 2501000  | Operation failed. |
| 2501001  | Wi-Fi STA disabled. |

**Example**
```ts
import { wifiManager } from '@kit.ConnectivityKit';

  try {
    let linkedInfo = wifiManager.getMultiLinkedInfo();
    console.info("linkedInfo:" + JSON.stringify(linkedInfo));
  }catch(error){
    console.error("failed:" + JSON.stringify(error));
  }
```

## WifiP2pGroupInfo

Represents the P2P group information.

**System capability**: SystemCapability.Communication.WiFi.P2P

| Name | Type | Read-Only | Optional | Description |
| -------- | -------- | -------- | -------- | -------- |
| isP2pGo | boolean | No | No | Whether the device is the group owner. **true** indicates it is the group owner, and **false** indicates it is not. |
| ownerInfo | [WifiP2pDevice](#wifip2pdevice) | No | No | Device information of the group. |
| passphrase | string | No | No | Group key. |
| interface | string | No | No | Interface name. |
| groupName | string | No | No | Group name. |
| networkId | number | No | No | Network ID. |
| frequency | number | No | No | Frequency of the group. |
| clientDevices | [WifiP2pDevice[]](#wifip2pdevice) | No | No | Information about the list of connected devices. |
| goIpAddress | string | No | No | Group IP address. |


## wifiManager.on('wifiStateChange')

on(type: 'wifiStateChange', callback: Callback&lt;number&gt;): void

Subscribes to Wi-Fi state changes. When the service exits, call **off(type: 'wifiStateChange', callback?: Callback\<number>)** to unregister the callback registered. This API uses an asynchronous callback to return the result.

**Required permissions**: ohos.permission.GET_WIFI_INFO

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Communication.WiFi.STA

**Parameters**

  | Name | Type | Mandatory | Description |
  | -------- | -------- | -------- | -------- |
  | type | string | Yes | Fixed value **"wifiStateChange"**. |
  | callback | Callback&lt;number&gt; | Yes | Callback function for state changes. Returns **0**: inactive, **1**: active, **2**: activating, **3**: deactivating. |

**Error codes**

For details about the error codes, see [Wi-Fi Error Codes](errorcode-wifi.md) and [Universal Error Codes](../errorcode-universal.md).

| ID | Error message |
| -------- | ---------------------------- |
| 201 | Permission denied.                 |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |
| 801 | Capability not supported.          |
| 2501000  | Operation failed.|

**Enumerated values of the state change event:**

| Value | Description |
| -------- | -------- |
| 0 | Inactive. |
| 1 | Active. |
| 2 | Activating. |
| 3 | Deactivating. |


## wifiManager.off('wifiStateChange')

off(type: 'wifiStateChange', callback?: Callback&lt;number&gt;): void

Unsubscribes from Wi-Fi status change events. This API uses an asynchronous callback to return the result.

**Required permissions**: ohos.permission.GET_WIFI_INFO

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Communication.WiFi.STA

**Parameters**

  | Name | Type | Mandatory | Description |
  | -------- | -------- | -------- | -------- |
  | type | string | Yes | Fixed value **"wifiStateChange"**. |
  | callback | Callback&lt;number&gt; | No | Callback function for the state change event. If this parameter is not specified, all callbacks associated with the event are unregistered. |

**Error codes**

For details about the error codes, see [Wi-Fi Error Codes](errorcode-wifi.md) and [Universal Error Codes](../errorcode-universal.md).

| ID | Error Message |
| -------- | ---------------------------- |
| 201 | Permission denied.                 |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |
| 801 | Capability not supported.          |
| 2501000  | Operation failed.|

**Example**
```ts
  import { wifiManager } from '@kit.ConnectivityKit';
  
  let recvPowerNotifyFunc = (result:number) => {
      console.info("Receive power state change event: " + result);
  }
  
  // Register event
  wifiManager.on("wifiStateChange", recvPowerNotifyFunc);
  
  // Unregister event
  wifiManager.off("wifiStateChange", recvPowerNotifyFunc);
```


## wifiManager.on('wifiConnectionChange')

on(type: 'wifiConnectionChange', callback: Callback&lt;number&gt;): void

Subscribes to Wi-Fi connection state changes. When the service exits, call **off(type: 'wifiConnectionChange', callback?: Callback&amp;lt;number&amp;gt;)** to unregister the callback registered. This API uses an asynchronous callback to return the result.

**Required permissions**: ohos.permission.GET_WIFI_INFO

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Communication.WiFi.STA

**Parameters**

  | Name | Type | Mandatory | Description |
  | -------- | -------- | -------- | -------- |
  | type | string | Yes | Fixed value **"wifiConnectionChange"**. |
  | callback | Callback&lt;number&gt; | Yes | Callback for the status change. Returns **0**: disconnected, **1**: connected.|

**Enumerations of the connection status change event:**

| Value | Description |
| -------- | -------- |
| 0 | Disconnected. |
| 1 | Connected. |

**Error codes**

For details about the error codes, see [Wi-Fi Error Codes](errorcode-wifi.md) and [Universal Error Codes](../errorcode-universal.md).

| ID | Error Message |
| -------- | ---------------------------- |
| 201 | Permission denied.                 |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |
| 801 | Capability not supported.          |
| 2501000  | Operation failed.|

## wifiManager.off('wifiConnectionChange')

off(type: 'wifiConnectionChange', callback?: Callback&lt;number&gt;): void

Unsubscribes from Wi-Fi connection status change events. This API uses an asynchronous callback to return the result.

**Required permissions**: ohos.permission.GET_WIFI_INFO

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Communication.WiFi.STA

**Parameters**

  | Name | Type | Mandatory | Description |
  | -------- | -------- | -------- | -------- |
  | type | string | Yes | Fixed value **"wifiConnectionChange"**. |
  | callback | Callback&lt;number&gt; | No | Callback function for the connection status change. If **callback** is not specified, all callback functions associated with this event are unregistered. |

**Error codes**

For details about the error codes, see [Wi-Fi Error Codes](errorcode-wifi.md) and [Universal Error Codes](../errorcode-universal.md).

| ID | Error message |
| -------- | ---------------------------- |
| 201 | Permission denied.                 |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |
| 801 | Capability not supported.          |
| 2501000  | Operation failed.|

**Example**
```ts
  import { wifiManager } from '@kit.ConnectivityKit';
  
  let recvWifiConnectionChangeFunc = (result:number) => {
      console.info("Receive wifi connection change event: " + result);
  }
  
  // Register event
  wifiManager.on("wifiConnectionChange", recvWifiConnectionChangeFunc);
  
  // Unregister event
  wifiManager.off("wifiConnectionChange", recvWifiConnectionChangeFunc);
```

## wifiManager.on('wifiScanStateChange')

on(type: 'wifiScanStateChange', callback: Callback&lt;number&gt;): void

Registers the scan status change event. When the service exits, call the off(type: 'wifiScanStateChange', callback?: Callback&lt;number&gt;) API to remove the previously registered callback. Uses an asynchronous callback.

**Required permissions**: ohos.permission.GET_WIFI_INFO

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Communication.WiFi.STA

**Parameters**

  | Name | Type | Mandatory | Description |
  | -------- | -------- | -------- | -------- |
  | type | string | Yes | Event type, which has a fixed value of **wifiScanStateChange**. |
  | callback | Callback&lt;number&gt; | Yes | Callback for status changes. The value **0** indicates that the scan fails, and the value **1** indicates that the scan is successful. |

**Enumerations of the scan status change event:**

| Value | Description |
| -------- | -------- |
| 0 | Scan failed. |
| 1 | Scan succeeded. |

**Error codes**

For details about the error codes, see [Wi-Fi Error Codes](errorcode-wifi.md) and [Universal Error Codes](../errorcode-universal.md).

| ID | Error Message |
| -------- | ---------------------------- |
| 201 | Permission denied.                 |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |
| 801 | Capability not supported.          |
| 2501000  | Operation failed.|

## wifiManager.off('wifiScanStateChange')

off(type: 'wifiScanStateChange', callback?: Callback&lt;number&gt;): void

Unregisters the scan state change event. This API uses an asynchronous callback.

**Required permissions**: ohos.permission.GET_WIFI_INFO

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Communication.WiFi.STA

**Parameters**

| Name | Type | Mandatory | Description |
| -------- | -------- | -------- | -------- |
| type | string | Yes | Fixed value **"wifiScanStateChange"**. |
| callback | Callback&lt;number&gt; | No | Callback function for the state change. If **callback** is not specified, all callback functions associated with this event are unregistered. |

**Error codes**

For details about the error codes, see [Wi-Fi Error Codes](errorcode-wifi.md) and [Universal Error Codes](../errorcode-universal.md).

| ID | Error Message |
| -------- | ---------------------------- |
| 201 | Permission denied.                 |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |
| 801 | Capability not supported.          |
| 2501000  | Operation failed.|

**Example**
```ts
  import { wifiManager } from '@kit.ConnectivityKit';
  
  let recvWifiScanStateChangeFunc = (result:number) => {
      console.info("Receive Wifi scan state change event: " + result);
  }
  
  // Register event
  wifiManager.on("wifiScanStateChange", recvWifiScanStateChangeFunc);
  
  // Unregister event
  wifiManager.off("wifiScanStateChange", recvWifiScanStateChangeFunc);
```

## wifiManager.on('wifiRssiChange')

on(type: 'wifiRssiChange', callback: Callback&lt;number&gt;): void

Subscribes to Wi-Fi received signal strength indicator (RSSI) changes. When the service exits, you need to call **off(type: 'wifiRssiChange', callback?: Callback&amp;lt;number&amp;gt;)** to remove the registered callback. This API uses an asynchronous callback to return the result.

**Required permissions**: ohos.permission.GET_WIFI_INFO

**System capability**: SystemCapability.Communication.WiFi.STA

**Parameters**

  | Name | Type | Mandatory | Description |
  | -------- | -------- | -------- | -------- |
  | type | string | Yes | Fixed value **"wifiRssiChange"**. |
  | callback | Callback&lt;number&gt; | Yes | Callback function for the status change, which returns the RSSI value in dBm. |

**Error codes**

For details about the error codes, see [Wi-Fi Error Codes](errorcode-wifi.md) and [Universal Error Codes](../errorcode-universal.md).

| ID | Error message |
| -------- | ---------------------------- |
| 201 | Permission denied.                 |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |
| 801 | Capability not supported.          |
| 2501000  | Operation failed.|

## wifiManager.off('wifiRssiChange')

off(type: 'wifiRssiChange', callback?: Callback&lt;number&gt;): void

Unsubscribes from Wi-Fi RSSI changes. This API uses an asynchronous callback to return the result.

**Required permissions**: ohos.permission.GET_WIFI_INFO

**System capability**: SystemCapability.Communication.WiFi.STA

**Parameters**

| Name | Type | Mandatory | Description |
| -------- | -------- | -------- | -------- |
| type | string | Yes | Fixed value **"wifiRssiChange"**. |
| callback | Callback&lt;number&gt; | No | Callback function for the status change. If **callback** is not specified, all callback functions associated with this event are unregistered. |

**Error codes**

For details about the error codes, see [Wi-Fi Error Codes](errorcode-wifi.md) and [Universal Error Codes](../errorcode-universal.md).

| ID | Error message |
| -------- | ---------------------------- |
| 201 | Permission denied.                 |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |
| 801 | Capability not supported.          |
| 2501000  | Operation failed.|

**Example**
```ts
  import { wifiManager } from '@kit.ConnectivityKit';
  
  let recvWifiRssiChangeFunc = (result:number) => {
      console.info("Receive wifi rssi change event: " + result);
  }
  
  // Register event
  wifiManager.on("wifiRssiChange", recvWifiRssiChangeFunc);
  
  // Unregister event
  wifiManager.off("wifiRssiChange", recvWifiRssiChangeFunc);
```

## wifiManager.on('hotspotStateChange')

on(type: 'hotspotStateChange', callback: Callback&lt;number&gt;): void

Registers the hotspot state change event. When the service exits, call **off(type: 'hotspotStateChange', callback?: Callback&lt;number&gt;)** to remove the previously registered callback. This API uses an asynchronous callback.

**Required permissions**: ohos.permission.GET_WIFI_INFO

**System capability**: SystemCapability.Communication.WiFi.AP.Core

**Parameters**

| Name | Type | Mandatory | Description |
| -------- | -------- | -------- | -------- |
| type | string | Yes | Event type, which has a fixed value of **hotspotStateChange**. |
| callback | Callback&lt;number&gt; | Yes | Callback for status changes. The parameter can be set to **0** (not activated), **1** (activated),**2** (activating), or **3** (deactivating). |

**Enumerations of the hotspot state change event:**

| Value | Description |
| -------- | -------- |
| 0 | Inactive. |
| 1 | Active. |
| 2 | Activating. |
| 3 | Deactivating. |

**Error codes**

For details about the error codes, see [Wi-Fi Error Codes](errorcode-wifi.md) and [Universal Error Codes](../errorcode-universal.md).

| ID | Error message |
| -------- | ---------------------------- |
| 201 | Permission denied.                 |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |
| 801 | Capability not supported.          |
| 2601000  | Operation failed. |

## wifiManager.off('hotspotStateChange')

off(type: 'hotspotStateChange', callback?: Callback&lt;number&gt;): void

Unregisters the hotspot state change event. This API uses an asynchronous callback.

**Required permissions**: ohos.permission.GET_WIFI_INFO

**System capability**: SystemCapability.Communication.WiFi.AP.Core

**Parameters**

| Name | Type | Mandatory | Description |
| -------- | -------- | -------- | -------- |
| type | string | Yes | Fixed value **"hotspotStateChange"**. |
| callback | Callback&lt;number&gt; | No | Callback function for the state change. If **callback** is not specified, all callback functions associated with this event are unregistered. |

**Error codes**

For details about the error codes, see [Wi-Fi Error Codes](errorcode-wifi.md) and [Universal Error Codes](../errorcode-universal.md).

| ID | Error message |
| -------- | ---------------------------- |
| 201 | Permission denied.                 |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |
| 801 | Capability not supported.          |
| 2601000  | Operation failed. |

**Example**
```ts
  import { wifiManager } from '@kit.ConnectivityKit';
  
  let recvHotspotStateChangeFunc = (result:number) => {
      console.info("Receive hotspot state change event: " + result);
  }
  
  // Register event
  wifiManager.on("hotspotStateChange", recvHotspotStateChangeFunc);
  
  // Unregister event
  wifiManager.off("hotspotStateChange", recvHotspotStateChangeFunc);
```


## wifiManager.on('p2pStateChange')

on(type: 'p2pStateChange', callback: Callback&lt;number&gt;): void

Registers the P2P state change event. When the service exits, call the off(type: 'p2pStateChange', callback?: Callback&lt;number&gt;) API to remove the previously registered callback. Uses an asynchronous callback.

**Required permissions**: ohos.permission.GET_WIFI_INFO

**System capability**: SystemCapability.Communication.WiFi.P2P

**Parameters**

| Name | Type | Mandatory | Description |
| -------- | -------- | -------- | -------- |
| type | string | Yes | Fixed value "p2pStateChange". |
| callback | Callback&lt;number&gt; | Yes | State change callback function. Returns 1: idle, 2: starting, 3: started, 4: closing, 5: closed. |

**Enumerations of the P2P state change event:**

| Value | Description |
| -------- | -------- |
| 1 | Idle. |
| 2 | Starting. |
| 3 | Started. |
| 4 | Closing. |
| 5 | Closed. |

**Error codes**

For details about the error codes, see [Wi-Fi Error Codes](errorcode-wifi.md) and [Universal Error Codes](../errorcode-universal.md).

| ID | Error message |
| -------- | ---------------------------- |
| 201 | Permission denied.                 |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |
| 801 | Capability not supported.          |
| 2801000  | Operation failed. |

## wifiManager.off('p2pStateChange')

off(type: 'p2pStateChange', callback?: Callback&lt;number&gt;): void

Unregisters the P2P state change event. This API uses an asynchronous callback to return the result.

**Required permissions**: ohos.permission.GET_WIFI_INFO

**System capability**: SystemCapability.Communication.WiFi.P2P

**Parameters**

  | Name | Type | Mandatory | Description |
  | -------- | -------- | -------- | -------- |
  | type | string | Yes | Fixed value **"p2pStateChange"**. |
  | callback | Callback&lt;number&gt; | No | Callback function for the state change. If **callback** is not specified, all callback functions associated with this event are unregistered. |

**Error codes**

For details about the error codes, see [Wi-Fi Error Codes](errorcode-wifi.md) and [Universal Error Codes](../errorcode-universal.md).

| ID | Error Message |
| -------- | ---------------------------- |
| 201 | Permission denied.                 |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |
| 801 | Capability not supported.          |
| 2801000  | Operation failed. |

**Example**
```ts
  import { wifiManager } from '@kit.ConnectivityKit';
  
  let recvP2pStateChangeFunc = (result:number) => {
      console.info("Receive p2p state change event: " + result);
  }
  
  // Register event
  wifiManager.on("p2pStateChange", recvP2pStateChangeFunc);
  
  // Unregister event
  wifiManager.off("p2pStateChange", recvP2pStateChangeFunc);
```

## wifiManager.on('p2pConnectionChange')

on(type: 'p2pConnectionChange', callback: Callback&lt;WifiP2pLinkedInfo&gt;): void

Registers the P2P connection status change event. When the service exits, call the **off(type: 'p2pConnectionChange', callback?: Callback&lt;WifiP2pLinkedInfo&gt;)** API to remove the previously registered callback. Uses **callback** for asynchronous callback.

**Required permissions**: ohos.permission.GET_WIFI_INFO

**System capability**: SystemCapability.Communication.WiFi.P2P

**Parameters**

  | Name | Type | Mandatory | Description |
  | -------- | -------- | -------- | -------- |
  | type | string | Yes | Fixed value "p2pConnectionChange". |
  | callback | Callback&lt;[WifiP2pLinkedInfo](#wifip2plinkedinfo)&gt; | Yes | Callback function for status changes. Returns the P2P connection information. |

**Error codes**

For details about the error codes, see [Wi-Fi Error Codes](errorcode-wifi.md) and [Universal Error Codes](../errorcode-universal.md).

| ID | Error Message |
| -------- | ---------------------------- |
| 201 | Permission denied.                 |
| 401 | Invalid parameters. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |
| 801 | Capability not supported.          |
| 2801000  | Operation failed. |

## wifiManager.off('p2pConnectionChange')

off(type: 'p2pConnectionChange', callback?: Callback&lt;WifiP2pLinkedInfo&gt;): void

Unregisters the P2P connection status change event, using an asynchronous callback.

**Required permissions**: ohos.permission.GET_WIFI_INFO

**System capability**: SystemCapability.Communication.WiFi.P2P

**Parameters**

  | Name | Type | Mandatory | Description |
  | -------- | -------- | -------- | -------- |
  | type | string | Yes | Fixed value "p2pConnectionChange". |
  | callback | Callback&lt;[WifiP2pLinkedInfo](#wifip2plinkedinfo)&gt; | No | Callback function for status changes. If callback is not specified, all callback functions associated with this event are unregistered. |

**Error codes**

For details about the error codes, see [Wi-Fi Error Codes](errorcode-wifi.md) and [Universal Error Codes](../errorcode-universal.md).

| ID | Error Message |
| -------- | ---------------------------- |
| 201 | Permission denied.                 |
| 401 | Invalid parameters. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |
| 801 | Capability not supported.          |
| 2801000  | Operation failed. |

**Example**
```ts
  import { wifiManager } from '@kit.ConnectivityKit';
  
  let recvP2pConnectionChangeFunc = (result:wifiManager.WifiP2pLinkedInfo) => {
      console.info("Receive p2p connection change event: " + result);
  }
  
  // Register event
  wifiManager.on("p2pConnectionChange", recvP2pConnectionChangeFunc);
  
  // Unregister event
  wifiManager.off("p2pConnectionChange", recvP2pConnectionChangeFunc);
```

## wifiManager.on('p2pDeviceChange')

on(type: 'p2pDeviceChange', callback: Callback&lt;WifiP2pDevice&gt;): void

Registers the P2P device state change event. When the service exits, call off(type: 'p2pDeviceChange', callback?: Callback&lt;WifiP2pDevice&gt;) to remove the previously registered callback. This API uses an asynchronous callback.

**Required permissions:**

From API 10: ohos.permission.GET_WIFI_INFO

**System capability:** SystemCapability.Communication.WiFi.P2P

**Parameters**

  | Name | Type | Mandatory | Description |
  | -------- | -------- | -------- | -------- |
  | type | string | Yes | Fixed value "p2pDeviceChange". |
  | callback | Callback&lt;[WifiP2pDevice](#wifip2pdevice)&gt; | Yes | Callback function for the state change. Returns the P2P device information.|

**Error codes**

For details about the error codes, see [Wi-Fi Error Codes](errorcode-wifi.md) and [Universal Error Codes](../errorcode-universal.md).

| ID | Error Message |
| -------- | ---------------------------- |
| 201 | Permission denied.                 |
| 401 | Invalid parameters. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |
| 801 | Capability not supported.          |
| 2801000  | Operation failed. |

## wifiManager.off('p2pDeviceChange')

off(type: 'p2pDeviceChange', callback?: Callback&lt;WifiP2pDevice&gt;): void

Unregisters the P2P device status change event. This API uses an asynchronous callback to return the result.

**System capability**: SystemCapability.Communication.WiFi.P2P

**Parameters**

  | Name | Type | Mandatory | Description |
  | -------- | -------- | -------- | -------- |
  | type | string | Yes | Fixed value **"p2pDeviceChange"**. |
  | callback | Callback&lt;[WifiP2pDevice](#wifip2pdevice)&gt; | No | Callback for the status change. If **callback** is not specified, all callbacks associated with this event are unregistered. |

**Error codes**

For details about the error codes, see [Wi-Fi Error Codes](errorcode-wifi.md) and [Universal Error Codes](../errorcode-universal.md).

| ID | Error Message |
| -------- | ---------------------------- |
| 201 | Permission denied.                 |
| 401 | Invalid parameters. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |
| 801 | Capability not supported.          |
| 2801000  | Operation failed. |

**Example**
```ts
  import { wifiManager } from '@kit.ConnectivityKit';
  
  let recvP2pDeviceChangeFunc = (result:wifiManager.WifiP2pDevice) => {
      console.info("Receive p2p device change event: " + result);
  }
  
  // Register event
  wifiManager.on("p2pDeviceChange", recvP2pDeviceChangeFunc);
  
  // Unregister event
  wifiManager.off("p2pDeviceChange", recvP2pDeviceChangeFunc);
```

## wifiManager.on('p2pPeerDeviceChange')

on(type: 'p2pPeerDeviceChange', callback: Callback&lt;WifiP2pDevice[]&gt;): void

Registers the P2P peer device status change event. When the service exits, call off(type: 'p2pPeerDeviceChange', callback?: Callback&lt;WifiP2pDevice[]&gt;) to remove the previously registered callback. This API uses an asynchronous callback.

**Required permissions:**

Since API 10: ohos.permission.GET_WIFI_INFO

**System capability**: SystemCapability.Communication.WiFi.P2P

**Parameters**

| Name | Type | Mandatory | Description |
| -------- | -------- | -------- | -------- |
| type | string | Yes | Fixed value **"p2pPeerDeviceChange"**. |
| callback | Callback&lt;[WifiP2pDevice[]](#wifip2pdevice)&gt; | Yes | Callback function for the status change. If the application has the ohos.permission.GET_WIFI_PEERS_MAC permission, **deviceAddress** in the returned result is the real device address; otherwise, it is a random device address. |

**Error codes**

For details about the error codes, see [Wi-Fi Error Codes](errorcode-wifi.md) and [Universal Error Codes](../errorcode-universal.md).

| ID | Error Message |
| -------- | ---------------------------- |
| 201 | Permission denied.                 |
| 401 | Invalid parameters. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |
| 801 | Capability not supported.          |
| 2801000  | Operation failed. |

## wifiManager.off('p2pPeerDeviceChange')

off(type: 'p2pPeerDeviceChange', callback?: Callback&lt;WifiP2pDevice[]&gt;): void

Unregisters the P2P peer device status change event. This API uses an asynchronous callback to return the result.

**System capability**: SystemCapability.Communication.WiFi.P2P

**Parameters**

| Name | Type | Mandatory | Description |
| -------- | -------- | -------- | -------- |
| type | string | Yes | Fixed value **"p2pPeerDeviceChange"**. |
| callback | Callback&lt;[WifiP2pDevice[]](#wifip2pdevice)&gt; | No | Callback function for the status change. If **callback** is not specified, all callback functions associated with this event are unregistered. If the application has the **ohos.permission.GET_WIFI_PEERS_MAC** permission, the **deviceAddress** in the returned result is the real device address; otherwise, it is a random device address. |

**Error codes**

For details about the error codes, see [Wi-Fi Error Codes](errorcode-wifi.md) and [Universal Error Codes](../errorcode-universal.md).

| ID | Error Message |
| -------- | ---------------------------- |
| 201 | Permission denied.                 |
| 401 | Invalid parameters. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |
| 801 | Capability not supported.          |
| 2801000  | Operation failed. |

**Example**
```ts
  import { wifiManager } from '@kit.ConnectivityKit';
  
  let recvP2pPeerDeviceChangeFunc = (result:wifiManager.WifiP2pDevice[]) => {
      console.info("Receive p2p peer device change event: " + result);
  }
  
  // Register event
  wifiManager.on("p2pPeerDeviceChange", recvP2pPeerDeviceChangeFunc);
  
  // Unregister event
  wifiManager.off("p2pPeerDeviceChange", recvP2pPeerDeviceChangeFunc);
```

## wifiManager.on('p2pPersistentGroupChange')

on(type: 'p2pPersistentGroupChange', callback: Callback&lt;void&gt;): void

Registers the P2P persistent group status change event. When the service exits, call off(type: 'p2pPersistentGroupChange', callback?: Callback&lt;void&gt;) to remove the previously registered callback. Uses an asynchronous callback.

**Required permissions**: ohos.permission.GET_WIFI_INFO

**System capability**: SystemCapability.Communication.WiFi.P2P

**Parameters**

  | Name | Type | Mandatory | Description |
  | -------- | -------- | -------- | -------- |
  | type | string | Yes | Fixed value "p2pPersistentGroupChange". |
  | callback | Callback&lt;void&gt; | Yes | Callback function for the status change. |

**Error codes**

For details about the error codes, see [Wi-Fi Error Codes](errorcode-wifi.md) and [Universal Error Codes](../errorcode-universal.md).

| ID | Error Message |
| -------- | ---------------------------- |
| 201 | Permission denied.                 |
| 401 | Invalid parameters. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |
| 801 | Capability not supported.          |
| 2801000  | Operation failed. |

## wifiManager.off('p2pPersistentGroupChange')

off(type: 'p2pPersistentGroupChange', callback?: Callback&lt;void&gt;): void

Unregisters the P2P persistent group status change event. This API uses an asynchronous callback.

**Required permissions**: ohos.permission.GET_WIFI_INFO

**System capability**: SystemCapability.Communication.WiFi.P2P

**Parameters**

| Name | Type | Mandatory | Description |
| -------- | -------- | -------- | -------- |
| type | string | Yes | Fixed value **"p2pPersistentGroupChange"**. |
| callback | Callback&lt;void&gt; | No | Callback function for the status change. If **callback** is not specified, all callback functions associated with this event are unregistered. |

**Error codes**

For details about the error codes, see [Wi-Fi Error Codes](errorcode-wifi.md) and [Universal Error Codes](../errorcode-universal.md).

| ID | Error Message |
| -------- | ---------------------------- |
| 201 | Permission denied.                 |
| 401 | Invalid parameters. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |
| 801 | Capability not supported.          |
| 2801000  | Operation failed. |

**Example**
```ts
  import { wifiManager } from '@kit.ConnectivityKit';
  
  let recvP2pPersistentGroupChangeFunc = (result:void) => {
      console.info("Receive p2p persistent group change event: " + result);
  }
  
  // Register event
  wifiManager.on("p2pPersistentGroupChange", recvP2pPersistentGroupChangeFunc);
  
  // Unregister event
  wifiManager.off("p2pPersistentGroupChange", recvP2pPersistentGroupChangeFunc);
```

## wifiManager.on('p2pDiscoveryChange')

on(type: 'p2pDiscoveryChange', callback: Callback&lt;number&gt;): void

Registers the P2P discovery device status change event. When the service exits, call off(type: 'p2pDiscoveryChange', callback?: Callback&lt;number&gt;) to remove the previously registered callback. Uses callback for asynchronous callback.

**Required permissions**: ohos.permission.GET_WIFI_INFO

**System capability**: SystemCapability.Communication.WiFi.P2P

**Parameters**

  | Name | Type | Mandatory | Description |
  | -------- | -------- | -------- | -------- |
  | type | string | Yes | Fixed to the string "p2pDiscoveryChange". |
  | callback | Callback&lt;number&gt; | Yes | Callback function for status changes. Returns 0: no status change, 1: status changed. |

**Enumerations of the P2P discovery device status change event:**

| Value | Description |
| -------- | -------- |
| 0 | Initial state. |
| 1 | Discovery succeeded. |

**Error codes**

For details about the error codes, see [Wi-Fi Error Codes](errorcode-wifi.md) and [Universal Error Codes](../errorcode-universal.md).

| ID | Error Message |
| -------- | ---------------------------- |
| 201 | Permission denied.                 |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |
| 801 | Capability not supported.          |
| 2801000  | Operation failed. |

## wifiManager.off('p2pDiscoveryChange')

off(type: 'p2pDiscoveryChange', callback?: Callback&lt;number&gt;): void

Unregisters the event for device discovery status changes. This API uses an asynchronous callback.

**Required permissions**: ohos.permission.GET_WIFI_INFO

**System capability**: SystemCapability.Communication.WiFi.P2P

**Parameters**

  | Name | Type | Mandatory | Description |
  | -------- | -------- | -------- | -------- |
  | type | string | Yes | Fixed value **"p2pDiscoveryChange"**. |
  | callback | Callback&lt;number&gt; | No | Callback for status changes. If this parameter is not specified, all callbacks associated with this event are unregistered. |

**Error codes**

For details about the error codes, see [Wi-Fi Error Codes](errorcode-wifi.md) and [Universal Error Codes](../errorcode-universal.md).

| ID | Error Message |
| -------- | ---------------------------- |
| 201 | Permission denied.                 |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |
| 801 | Capability not supported.          |
| 2801000  | Operation failed. |

**Example**
```ts
  import { wifiManager } from '@kit.ConnectivityKit';
  
  let recvP2pDiscoveryChangeFunc = (result:number) => {
      console.info("Receive p2p discovery change event: " + result);
  }
  
  // Register event
  wifiManager.on("p2pDiscoveryChange", recvP2pDiscoveryChangeFunc);
  
  // Unregister event
  wifiManager.off("p2pDiscoveryChange", recvP2pDiscoveryChangeFunc);
```

## wifiManager.isWlanSupported

isWlanSupported(): boolean

Checks whether the Wi-Fi network is available.

**System capability**: SystemCapability.Communication.WiFi.Core

**Since**: 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Return value**

  | Type | Description |
  | -------- | -------- |
  | boolean | Whether Wi-Fi is available. The value **true** indicates that Wi-Fi is available, and&nbsp;**false** indicates that Wi-Fi is unavailable. |

**Error codes**

For details about the error codes, see [Wi-Fi Error Codes](errorcode-wifi.md).

| ID | Error message |
| -------- | -------- |
| 2401000  | Operation failed. |
