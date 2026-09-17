# getP2pGroups (System API)

## Modules to Import

```TypeScript
import { wifiManager } from '@kit.ConnectivityKit';
```

## getP2pGroups

```TypeScript
function getP2pGroups(): Promise<Array<WifiP2pGroupInfo>>
```

Obtain information about the groups.

**Since:** 10

**Required permissions:** ohos.permission.GET_WIFI_INFO

**System capability:** SystemCapability.Communication.WiFi.P2P

**System API:** This is a system API.

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;Array&lt;[WifiP2pGroupInfo](arkts-connectivity-wifimanager-wifip2pgroupinfo-i.md)&gt;&gt; | Returns the information about own device info. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | System API is not allowed called by Non-system application. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. |
| [2801000](../errorcode-wifi.md#2801000-p2p-module-error) | Operation failed. |

**Examples**

```TypeScript
import { wifiManager } from '@kit.ConnectivityKit';
import { BusinessError } from '@kit.BasicServicesKit';

wifiManager.getP2pGroups((err: BusinessError, data:wifiManager.WifiP2pGroupInfo[]) => {
if (err) {
    console.error("get P2P groups error");
    return;
}
  console.info("get P2P groups: " + JSON.stringify(data));
});

wifiManager.getP2pGroups().then(data => {
  console.info("get P2P groups: " + JSON.stringify(data));
});
```


## getP2pGroups

```TypeScript
function getP2pGroups(callback: AsyncCallback<Array<WifiP2pGroupInfo>>): void
```

Obtain information about the groups.

**Since:** 10

**Required permissions:** ohos.permission.GET_WIFI_INFO

**System capability:** SystemCapability.Communication.WiFi.P2P

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;Array&lt;[WifiP2pGroupInfo](arkts-connectivity-wifimanager-wifip2pgroupinfo-i.md)&gt;&gt; | Yes | Indicates callback of function. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | System API is not allowed called by Non-system application. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. |
| [2801000](../errorcode-wifi.md#2801000-p2p-module-error) | Operation failed. |
| [2801001](../errorcode-wifi.md#2801001-p2p-module-error) | Wi-Fi STA disabled. |

**Examples**

See [getP2pGroups](#getp2pgroups)
