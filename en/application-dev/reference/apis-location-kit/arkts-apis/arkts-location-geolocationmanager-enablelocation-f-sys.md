# enableLocation (System API)

## Modules to Import

```TypeScript
import { geoLocationManager } from '@kit.LocationKit';
```

## enableLocation

```TypeScript
function enableLocation(callback: AsyncCallback<void>): void
```

Enable location switch.

**Since:** 9

**Required permissions:** 
- API version 20 and later: ohos.permission.MANAGE_SECURE_SETTINGS and ohos.permission.CONTROL_LOCATION_SWITCH
- API versions 9 to 19: ohos.permission.MANAGE_SECURE_SETTINGS

**System capability:** SystemCapability.Location.Location.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Indicates the callback for reporting the error message. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Failed to call ${geoLocationManager.enableLocation} due to limited device capabilities. |
| [3301000](../errorcode-geoLocationManager.md#3301000-location-service-unavailable) | The location service is unavailable. |

**Examples**

```TypeScript
import { geoLocationManager } from '@kit.LocationKit';

try {
  geoLocationManager.enableLocation((err) => {
    if (err) {
      console.error('enableLocation: err=' + JSON.stringify(err));
    }
  });
} catch (err) {
  console.error("errCode:" + err.code + ", message:" + err.message);
}
```


<a id="enablelocation-1"></a>

## enableLocation

```TypeScript
function enableLocation(): Promise<void>
```

Enable location switch.

**Since:** 9

**Required permissions:** 
- API version 20 and later: ohos.permission.MANAGE_SECURE_SETTINGS and ohos.permission.CONTROL_LOCATION_SWITCH
- API versions 9 to 19: ohos.permission.MANAGE_SECURE_SETTINGS

**System capability:** SystemCapability.Location.Location.Core

**System API:** This is a system API.

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | The promise returned by the function. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Failed to call ${geoLocationManager.enableLocation} due to limited device capabilities. |
| [3301000](../errorcode-geoLocationManager.md#3301000-location-service-unavailable) | The location service is unavailable. |

**Examples**

```TypeScript
import { geoLocationManager } from '@kit.LocationKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  geoLocationManager.enableLocation().then(() => {
    console.info('promise, enableLocation succeed');
  })
    .catch((error: BusinessError) => {
      console.error('promise, enableLocation: error=' + JSON.stringify(error));
    });
} catch (err) {
  console.error("errCode:" + err.code + ", message:" + err.message);
}
```
