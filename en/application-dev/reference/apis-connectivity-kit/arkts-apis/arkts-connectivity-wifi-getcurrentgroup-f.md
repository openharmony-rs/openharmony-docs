# getCurrentGroup

## Modules to Import

```TypeScript
import { wifi } from '@kit.ConnectivityKit';
```

## getCurrentGroup

```TypeScript
function getCurrentGroup(): Promise<WifiP2pGroupInfo>
```

Obtains the current P2P group information. This API uses a promise to return the result.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [getCurrentGroup](arkts-connectivity-wifimanager-getcurrentgroup-f.md)

**Required permissions:** ohos.permission.GET_WIFI_INFO and ohos.permission.LOCATION

<!--Device-wifi-function getCurrentGroup(): Promise<WifiP2pGroupInfo>--><!--Device-wifi-function getCurrentGroup(): Promise<WifiP2pGroupInfo>-End-->

**System capability:** SystemCapability.Communication.WiFi.P2P

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[WifiP2pGroupInfo](arkts-connectivity-wifi-wifip2pgroupinfo-i.md)&gt; | Promise used to return the P2P group information obtained. |

**Examples**

```TypeScript
import wifi from '@ohos.wifi';

wifi.getCurrentGroup((err, data:wifi.WifiP2pGroupInfo) => {
   if (err) {
       console.error("get current P2P group error");
       return;
   }
  console.info("get current P2P group: " + JSON.stringify(data));
});

wifi.getCurrentGroup().then(data => {
  console.info("get current P2P group: " + JSON.stringify(data));
});
```


## getCurrentGroup

```TypeScript
function getCurrentGroup(callback: AsyncCallback<WifiP2pGroupInfo>): void
```

Obtains the current P2P group information. This API uses an asynchronous callback to return the result.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [getCurrentGroup](arkts-connectivity-wifimanager-getcurrentgroup-f.md)

**Required permissions:** ohos.permission.GET_WIFI_INFO and ohos.permission.LOCATION

<!--Device-wifi-function getCurrentGroup(callback: AsyncCallback<WifiP2pGroupInfo>): void--><!--Device-wifi-function getCurrentGroup(callback: AsyncCallback<WifiP2pGroupInfo>): void-End-->

**System capability:** SystemCapability.Communication.WiFi.P2P

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[WifiP2pGroupInfo](arkts-connectivity-wifi-wifip2pgroupinfo-i.md)&gt; | Yes | Callback used to return the result. |

**Examples**

See [getCurrentGroup](#getcurrentgroup)
