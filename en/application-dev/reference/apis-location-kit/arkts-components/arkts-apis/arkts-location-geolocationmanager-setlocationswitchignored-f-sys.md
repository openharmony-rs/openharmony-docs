# setLocationSwitchIgnored (System API)

## Modules to Import

```TypeScript
import { geoLocationManager } from '@kit.LocationKit';
```

## setLocationSwitchIgnored

```TypeScript
function setLocationSwitchIgnored(isIgnored: boolean): void
```

Set the app locating behavior not controlled by the location switch.

**Since:** 18

**Required permissions:** ohos.permission.LOCATION_SWITCH_IGNORED

**System capability:** SystemCapability.Location.Location.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| isIgnored | boolean | Yes | True indicates that the location behavior of the app is not controlled by the location switch. Otherwise, it's the opposite. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Failed to call ${geoLocationManager.setLocationSwitchIgnored} due to limited device capabilities. |
| [3301000](../errorcode-geoLocationManager.md#3301000-location-service-unavailable) | The location service is unavailable. |

**Examples**

```TypeScript
import { geoLocationManager } from '@kit.LocationKit';

try {
  let isIgnored: boolean = true;
  geoLocationManager.setLocationSwitchIgnored(isIgnored);
} catch (err) {
  console.error("errCode:" + err.code + ", message:" + err.message);
}
```
