# getCurrentWifiBssidForLocating

## Modules to Import

```TypeScript
import { geoLocationManager } from '@kit.LocationKit';
```

## getCurrentWifiBssidForLocating

```TypeScript
function getCurrentWifiBssidForLocating(): string
```

Obtains the BSSID of the connected Wi-Fi hotspot.

**Since:** 14

**Required permissions:** ohos.permission.LOCATION and ohos.permission.APPROXIMATELY_LOCATION

**System capability:** SystemCapability.Location.Location.Core

**Return value:**

| Type | Description |
| --- | --- |
| string | Returns the BSSID of the connected Wi-Fi hotspot. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Failed to call ${geoLocationManager.getCurrentWifiBssidForLocating()} due to limited device capabilities. |
| [3301000](../errorcode-geoLocationManager.md#3301000-location-service-unavailable) | The location service is unavailable. |
| [3301100](../errorcode-geoLocationManager.md#3301100-positioning-failed-because-the-location-switch-is-turned-off) | The location switch is off. |
| [3301900](../errorcode-geoLocationManager.md#3301900-failed-to-obtain-the-mac-address-of-the-wi-fi-hotspot) | Failed to obtain the BSSID of the Wi-Fi hotspot. The Wi-Fi network is not connected. |

**Examples**

```TypeScript
import { geoLocationManager } from '@kit.LocationKit';

try {
  let bssid: string = geoLocationManager.getCurrentWifiBssidForLocating();
  console.info("get wifi bssid:" + bssid);
} catch (error) {
  console.error("getCurrentWifiBssidForLocating: errCode" + error.code + ", errMessage" + error.message);
}
```
