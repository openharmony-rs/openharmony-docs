# getP2pLinkedInfo

## Modules to Import

```TypeScript
import { wifi } from '@kit.ConnectivityKit';
```

## getP2pLinkedInfo

```TypeScript
function getP2pLinkedInfo(): Promise<WifiP2pLinkedInfo>
```

Obtains P2P connection information. This API uses a promise to return the result.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [getP2pLinkedInfo](arkts-connectivity-wifimanager-getp2plinkedinfo-f.md)

**Required permissions:** ohos.permission.GET_WIFI_INFO

<!--Device-wifi-function getP2pLinkedInfo(): Promise<WifiP2pLinkedInfo>--><!--Device-wifi-function getP2pLinkedInfo(): Promise<WifiP2pLinkedInfo>-End-->

**System capability:** SystemCapability.Communication.WiFi.P2P

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[WifiP2pLinkedInfo](arkts-connectivity-wifi-wifip2plinkedinfo-i.md)&gt; | Promise used to return the P2P link information. |

**Examples**

```TypeScript
import wifi from '@ohos.wifi';

wifi.getP2pLinkedInfo((err, data:wifi.WifiP2pLinkedInfo) => {
   if (err) {
       console.error("get p2p linked info error");
       return;
   }
  console.info("get wifi p2p linked info: " + JSON.stringify(data));
});

wifi.getP2pLinkedInfo().then(data => {
  console.info("get wifi p2p linked info: " + JSON.stringify(data));
});
```


## getP2pLinkedInfo

```TypeScript
function getP2pLinkedInfo(callback: AsyncCallback<WifiP2pLinkedInfo>): void
```

Obtains P2P connection information. This API uses an asynchronous callback to return the result.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [getP2pLinkedInfo](arkts-connectivity-wifimanager-getp2plinkedinfo-f.md)

**Required permissions:** ohos.permission.GET_WIFI_INFO

<!--Device-wifi-function getP2pLinkedInfo(callback: AsyncCallback<WifiP2pLinkedInfo>): void--><!--Device-wifi-function getP2pLinkedInfo(callback: AsyncCallback<WifiP2pLinkedInfo>): void-End-->

**System capability:** SystemCapability.Communication.WiFi.P2P

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[WifiP2pLinkedInfo](arkts-connectivity-wifi-wifip2plinkedinfo-i.md)&gt; | Yes | Callback used to return the result. |

**Examples**

See [getP2pLinkedInfo](#getp2plinkedinfo)
