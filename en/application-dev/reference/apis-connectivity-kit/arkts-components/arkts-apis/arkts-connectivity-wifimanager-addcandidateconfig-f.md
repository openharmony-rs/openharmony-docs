# addCandidateConfig

## Modules to Import

```TypeScript
import { wifiManager } from '@kit.ConnectivityKit';
```

## addCandidateConfig

```TypeScript
function addCandidateConfig(config: WifiDeviceConfig): Promise<number>
```

Add a specified candidate hotspot configuration and returns the networkId. This method adds one configuration at a time. After this configuration is added, your device will determine whether to connect to the hotspot. The app must be in the foreground.

**Since:** 12

**Required permissions:** ohos.permission.SET_WIFI_INFO

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Communication.WiFi.STA

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| config | [WifiDeviceConfig](arkts-connectivity-wifimanager-wifideviceconfig-i.md) | Yes | candidate config. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;number&gt; | Returns `networkId` if the configuration is added; returns `-1` otherwise. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Invalid parameters. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3.Parameter verification failed. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. |
| [2501000](../errorcode-wifi.md#2501000-sta-internal-error) | Operation failed. |

**Examples**

```TypeScript
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


<a id="addcandidateconfig-1"></a>

## addCandidateConfig

```TypeScript
function addCandidateConfig(config: WifiDeviceConfig, callback: AsyncCallback<number>): void
```

Add a specified candidate hotspot configuration and returns the networkId. This method adds one configuration at a time. After this configuration is added, your device will determine whether to connect to the hotspot. The app must be in the foreground.

**Since:** 12

**Required permissions:** ohos.permission.SET_WIFI_INFO

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Communication.WiFi.STA

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| config | [WifiDeviceConfig](arkts-connectivity-wifimanager-wifideviceconfig-i.md) | Yes | candidate config. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;number&gt; | Yes | Indicates call back of addCandidateConfig. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Invalid parameters. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3.Parameter verification failed. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. |
| [2501000](../errorcode-wifi.md#2501000-sta-internal-error) | Operation failed. |

**Examples**

```TypeScript
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
