# getHotspotBlockList (System API)

## Modules to Import

```TypeScript
import { wifiManager } from '@kit.ConnectivityKit';
```

## getHotspotBlockList

```TypeScript
function getHotspotBlockList(): Array<StationInfo>
```

Get all the stations in the block list. If does't have the permission of ohos.permission.GET_WIFI_PEERS_MAC, return random bssid.

**Since:** 11

**Required permissions:** ohos.permission.GET_WIFI_INFO and ohos.permission.MANAGE_WIFI_HOTSPOT

**System capability:** SystemCapability.Communication.WiFi.AP.Core

**System API:** This is a system API.

**Return value:**

| Type | Description |
| --- | --- |
| Array&lt;[StationInfo](arkts-connectivity-wifimanager-stationinfo-i-sys.md)&gt; | stations in the block list. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | System API is not allowed called by Non-system application. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Invalid parameters. Possible causes: 1. Mandatory parameters are left unspecified. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. |
| [2601000](../errorcode-wifi.md#2601000-hotspot-module-error) | Operation failed. |

**Examples**

```TypeScript
import { wifiManager } from '@kit.ConnectivityKit';

try {
  let data = wifiManager.getHotspotBlockList();
  console.info("result:" + JSON.stringify(data));
} catch (error) {
  console.error("failed:" + JSON.stringify(error));
}
```
