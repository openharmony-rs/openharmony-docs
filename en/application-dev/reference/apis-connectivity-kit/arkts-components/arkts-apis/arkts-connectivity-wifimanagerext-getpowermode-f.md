# getPowerMode

## Modules to Import

```TypeScript
import { wifiManagerExt } from '@kit.ConnectivityKit';
```

## getPowerMode

```TypeScript
function getPowerMode(): Promise<PowerMode>
```

Obtains the current Wi-Fi power mode.

**Since:** 9

**Required permissions:** ohos.permission.GET_WIFI_INFO

**System capability:** SystemCapability.Communication.WiFi.AP.Extension

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[PowerMode](arkts-connectivity-wifimanagerext-powermode-e.md)&gt; |  |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. |
| [2701000](../errorcode-wifi.md#2701000-ap-extension-module-error) | Operation failed. |

**Examples**

```TypeScript
import { wifiManagerExt } from '@kit.ConnectivityKit';

async function getWifiPowerMode() {
  try {
    // 1. Use the await keyword to wait for promise parsing to complete.
    let model = await wifiManagerExt.getPowerMode();
    
    console.info("model info: " + model);
  } catch (error) {
    // 2. Capture the error when the promise is rejected.
    console.error("failed: " + JSON.stringify(error));
  }
}
```


<a id="getpowermode-1"></a>

## getPowerMode

```TypeScript
function getPowerMode(callback: AsyncCallback<PowerMode>): void
```

Obtains the current Wi-Fi power mode.

**Since:** 9

**Required permissions:** ohos.permission.GET_WIFI_INFO

**System capability:** SystemCapability.Communication.WiFi.AP.Extension

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[PowerMode](arkts-connectivity-wifimanagerext-powermode-e.md)&gt; | Yes | the callback of model |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. |
| [2701000](../errorcode-wifi.md#2701000-ap-extension-module-error) | Operation failed. |

**Examples**

```TypeScript
import { wifiManagerExt } from '@kit.ConnectivityKit';

  wifiManagerExt.getPowerMode((err, data:wifiManagerExt.PowerMode) => {
      if (err) {
          console.error("Failed to get linked information");
          return;
      }
      console.info("get power mode info: " + JSON.stringify(data));
  });

  wifiManagerExt.getPowerMode().then(data => {
      console.info("get power mode info: " + JSON.stringify(data));
  }).catch((error:number) => {
      console.error("get power mode error");
  });
```
