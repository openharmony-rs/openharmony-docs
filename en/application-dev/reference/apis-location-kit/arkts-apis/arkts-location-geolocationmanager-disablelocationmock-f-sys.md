# disableLocationMock (System API)

## Modules to Import

```TypeScript
import { geoLocationManager } from '@kit.LocationKit';
```

## disableLocationMock

```TypeScript
function disableLocationMock(): void
```

Disable the geographical location simulation function.

**Since:** 9

**Required permissions:** 
- API version 20 and later: ohos.permission.MOCK_LOCATION
- API versions 9 to 19: N/A

**System capability:** SystemCapability.Location.Location.Core

**System API:** This is a system API.

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Failed to call ${geoLocationManager.disableLocationMock} due to limited device capabilities. |
| [3301000](../errorcode-geoLocationManager.md#3301000-location-service-unavailable) | The location service is unavailable. |
| [3301100](../errorcode-geoLocationManager.md#3301100-positioning-failed-because-the-location-switch-is-turned-off) | The location switch is off. |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API.<br>**Applicable version:** 20 and later |

**Examples**

```TypeScript
import { geoLocationManager } from '@kit.LocationKit';

try {
  geoLocationManager.disableLocationMock();
} catch (err) {
  console.error("errCode:" + err.code + ", message:" + err.message);
}
```
