# off

## Modules to Import

```TypeScript
import { wifiManager } from '@kit.ConnectivityKit';
```

## off('wifiStateChange')

```TypeScript
function off(type: 'wifiStateChange', callback?: Callback<number>): void
```

Unsubscribe Wi-Fi status change events.

All callback functions will be deregistered If there is no specific callback parameter.

**Since:** 12

**Required permissions:** ohos.permission.GET_WIFI_INFO

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Communication.WiFi.STA

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'wifiStateChange' | Yes | event name. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;number&gt; | No | the callback of off |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. |
| [2501000](../errorcode-wifi.md#2501000-sta-internal-error) | Operation failed. |

**Examples**

```TypeScript
import { wifiManager } from '@kit.ConnectivityKit';
  
  let recvPowerNotifyFunc = (result:number) => {
      console.info("Receive power state change event: " + result);
  }
  
  // Register event
  wifiManager.on("wifiStateChange", recvPowerNotifyFunc);
  
  // Unregister event
  wifiManager.off("wifiStateChange", recvPowerNotifyFunc);
```


## off('wifiConnectionChange')

```TypeScript
function off(type: 'wifiConnectionChange', callback?: Callback<number>): void
```

Unsubscribe Wi-Fi connection change events. All callback functions will be deregistered If there is no specific callback parameter.

**Since:** 12

**Required permissions:** ohos.permission.GET_WIFI_INFO

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Communication.WiFi.STA

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'wifiConnectionChange' | Yes | event name. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;number&gt; | No | the callback of off |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. |
| [2501000](../errorcode-wifi.md#2501000-sta-internal-error) | Operation failed. |

**Examples**

```TypeScript
import { wifiManager } from '@kit.ConnectivityKit';
  
  let recvWifiConnectionChangeFunc = (result:number) => {
      console.info("Receive wifi connection change event: " + result);
  }
  
  // Register event
  wifiManager.on("wifiConnectionChange", recvWifiConnectionChangeFunc);
  
  // Unregister event
  wifiManager.off("wifiConnectionChange", recvWifiConnectionChangeFunc);
```


## off('wifiScanStateChange')

```TypeScript
function off(type: 'wifiScanStateChange', callback?: Callback<number>): void
```

Unsubscribe Wi-Fi scan status change events. All callback functions will be deregistered If there is no specific callback parameter.

**Since:** 12

**Required permissions:** ohos.permission.GET_WIFI_INFO

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Communication.WiFi.STA

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'wifiScanStateChange' | Yes | event name. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;number&gt; | No | the callback of off |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. |
| [2501000](../errorcode-wifi.md#2501000-sta-internal-error) | Operation failed. |

**Examples**

```TypeScript
import { wifiManager } from '@kit.ConnectivityKit';
  
  let recvWifiScanStateChangeFunc = (result:number) => {
      console.info("Receive Wifi scan state change event: " + result);
  }
  
  // Register event
  wifiManager.on("wifiScanStateChange", recvWifiScanStateChangeFunc);
  
  // Unregister event
  wifiManager.off("wifiScanStateChange", recvWifiScanStateChangeFunc);
```


## off('wifiRssiChange')

```TypeScript
function off(type: 'wifiRssiChange', callback?: Callback<number>): void
```

Unsubscribe Wi-Fi rssi change events. All callback functions will be deregistered If there is no specific callback parameter.

**Since:** 9

**Required permissions:** ohos.permission.GET_WIFI_INFO

**System capability:** SystemCapability.Communication.WiFi.STA

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'wifiRssiChange' | Yes | event name. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;number&gt; | No | the callback of off |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. |
| [2501000](../errorcode-wifi.md#2501000-sta-internal-error) | Operation failed. |

**Examples**

```TypeScript
import { wifiManager } from '@kit.ConnectivityKit';
  
  let recvWifiRssiChangeFunc = (result:number) => {
      console.info("Receive wifi rssi change event: " + result);
  }
  
  // Register event
  wifiManager.on("wifiRssiChange", recvWifiRssiChangeFunc);
  
  // Unregister event
  wifiManager.off("wifiRssiChange", recvWifiRssiChangeFunc);
```


## off('hotspotStateChange')

```TypeScript
function off(type: 'hotspotStateChange', callback?: Callback<number>): void
```

Unsubscribe Wi-Fi hotspot state change events. All callback functions will be deregistered If there is no specific callback parameter.

**Since:** 9

**Required permissions:** ohos.permission.GET_WIFI_INFO

**System capability:** SystemCapability.Communication.WiFi.AP.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'hotspotStateChange' | Yes | event name. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;number&gt; | No | the callback of off |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. |
| [2601000](../errorcode-wifi.md#2601000-hotspot-module-error) | Operation failed. |

**Examples**

```TypeScript
import { wifiManager } from '@kit.ConnectivityKit';
  
  let recvHotspotStateChangeFunc = (result:number) => {
      console.info("Receive hotspot state change event: " + result);
  }
  
  // Register event
  wifiManager.on("hotspotStateChange", recvHotspotStateChangeFunc);
  
  // Unregister event
  wifiManager.off("hotspotStateChange", recvHotspotStateChangeFunc);
```


## off('p2pStateChange')

```TypeScript
function off(type: 'p2pStateChange', callback?: Callback<number>): void
```

Unsubscribe P2P status change events.

**Since:** 9

**Required permissions:** ohos.permission.GET_WIFI_INFO

**System capability:** SystemCapability.Communication.WiFi.P2P

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'p2pStateChange' | Yes | event name. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;number&gt; | No | the callback of off |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. |
| [2801000](../errorcode-wifi.md#2801000-p2p-module-error) | Operation failed. |

**Examples**

```TypeScript
import { wifiManager } from '@kit.ConnectivityKit';
  
  let recvP2pStateChangeFunc = (result:number) => {
      console.info("Receive p2p state change event: " + result);
  }
  
  // Register event
  wifiManager.on("p2pStateChange", recvP2pStateChangeFunc);
  
  // Unregister event
  wifiManager.off("p2pStateChange", recvP2pStateChangeFunc);
```


## off('p2pConnectionChange')

```TypeScript
function off(type: 'p2pConnectionChange', callback?: Callback<WifiP2pLinkedInfo>): void
```

Unsubscribe P2P connection change events.

**Since:** 9

**Required permissions:** ohos.permission.GET_WIFI_INFO

**System capability:** SystemCapability.Communication.WiFi.P2P

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'p2pConnectionChange' | Yes | event name. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[WifiP2pLinkedInfo](arkts-connectivity-wifimanager-wifip2plinkedinfo-i.md)&gt; | No | the callback of off |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Invalid parameters. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. |
| [2801000](../errorcode-wifi.md#2801000-p2p-module-error) | Operation failed. |

**Examples**

```TypeScript
import { wifiManager } from '@kit.ConnectivityKit';
  
  let recvP2pConnectionChangeFunc = (result:wifiManager.WifiP2pLinkedInfo) => {
      console.info("Receive p2p connection change event: " + result);
  }
  
  // Register event
  wifiManager.on("p2pConnectionChange", recvP2pConnectionChangeFunc);
  
  // Unregister event
  wifiManager.off("p2pConnectionChange", recvP2pConnectionChangeFunc);
```


## off('p2pDeviceChange')

```TypeScript
function off(type: 'p2pDeviceChange', callback?: Callback<WifiP2pDevice>): void
```

Unsubscribe P2P local device change events.

**Since:** 10

**System capability:** SystemCapability.Communication.WiFi.P2P

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'p2pDeviceChange' | Yes | event name. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[WifiP2pDevice](arkts-connectivity-wifimanager-wifip2pdevice-i.md)&gt; | No | the callback of off |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Invalid parameters. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. |
| [2801000](../errorcode-wifi.md#2801000-p2p-module-error) | Operation failed. |

**Examples**

```TypeScript
import { wifiManager } from '@kit.ConnectivityKit';
  
  let recvP2pDeviceChangeFunc = (result:wifiManager.WifiP2pDevice) => {
      console.info("Receive p2p device change event: " + result);
  }
  
  // Register event
  wifiManager.on("p2pDeviceChange", recvP2pDeviceChangeFunc);
  
  // Unregister event
  wifiManager.off("p2pDeviceChange", recvP2pDeviceChangeFunc);
```


## off('p2pPeerDeviceChange')

```TypeScript
function off(type: 'p2pPeerDeviceChange', callback?: Callback<WifiP2pDevice[]>): void
```

Unsubscribe P2P peer device change events.

**Since:** 10

**System capability:** SystemCapability.Communication.WiFi.P2P

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'p2pPeerDeviceChange' | Yes | event name. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[WifiP2pDevice](arkts-connectivity-wifimanager-wifip2pdevice-i.md)[]&gt; | No | the callback of off |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Invalid parameters. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. |
| [2801000](../errorcode-wifi.md#2801000-p2p-module-error) | Operation failed. |

**Examples**

```TypeScript
import { wifiManager } from '@kit.ConnectivityKit';
  
  let recvP2pPeerDeviceChangeFunc = (result:wifiManager.WifiP2pDevice[]) => {
      console.info("Receive p2p peer device change event: " + result);
  }
  
  // Register event
  wifiManager.on("p2pPeerDeviceChange", recvP2pPeerDeviceChangeFunc);
  
  // Unregister event
  wifiManager.off("p2pPeerDeviceChange", recvP2pPeerDeviceChangeFunc);
```


## off('p2pPersistentGroupChange')

```TypeScript
function off(type: 'p2pPersistentGroupChange', callback?: Callback<void>): void
```

Unsubscribe P2P persistent group change events.

**Since:** 9

**Required permissions:** ohos.permission.GET_WIFI_INFO

**System capability:** SystemCapability.Communication.WiFi.P2P

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'p2pPersistentGroupChange' | Yes | event name. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;void&gt; | No | the callback of off |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Invalid parameters. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. |
| [2801000](../errorcode-wifi.md#2801000-p2p-module-error) | Operation failed. |

**Examples**

```TypeScript
import { wifiManager } from '@kit.ConnectivityKit';
  
  let recvP2pPersistentGroupChangeFunc = (result:void) => {
      console.info("Receive p2p persistent group change event: " + result);
  }
  
  // Register event
  wifiManager.on("p2pPersistentGroupChange", recvP2pPersistentGroupChangeFunc);
  
  // Unregister event
  wifiManager.off("p2pPersistentGroupChange", recvP2pPersistentGroupChangeFunc);
```


## off('p2pDiscoveryChange')

```TypeScript
function off(type: 'p2pDiscoveryChange', callback?: Callback<number>): void
```

Unsubscribe P2P discovery events.

**Since:** 9

**Required permissions:** ohos.permission.GET_WIFI_INFO

**System capability:** SystemCapability.Communication.WiFi.P2P

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'p2pDiscoveryChange' | Yes | event name. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;number&gt; | No | the callback of off |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. |
| [2801000](../errorcode-wifi.md#2801000-p2p-module-error) | Operation failed. |

**Examples**

```TypeScript
import { wifiManager } from '@kit.ConnectivityKit';
  
  let recvP2pDiscoveryChangeFunc = (result:number) => {
      console.info("Receive p2p discovery change event: " + result);
  }
  
  // Register event
  wifiManager.on("p2pDiscoveryChange", recvP2pDiscoveryChangeFunc);
  
  // Unregister event
  wifiManager.off("p2pDiscoveryChange", recvP2pDiscoveryChangeFunc);
```
