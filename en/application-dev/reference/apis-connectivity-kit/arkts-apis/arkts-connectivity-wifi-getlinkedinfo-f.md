# getLinkedInfo

## Modules to Import

```TypeScript
import { wifi } from '@kit.ConnectivityKit';
```

## getLinkedInfo

```TypeScript
function getLinkedInfo(): Promise<WifiLinkedInfo>
```

Obtains Wi-Fi connection information. This API uses a promise to return the result.

**Since:** 6

**Deprecated since:** 9

**Substitutes:** [getLinkedInfo](arkts-connectivity-wifimanager-getlinkedinfo-f.md)

**Required permissions:** ohos.permission.GET_WIFI_INFO

<!--Device-wifi-function getLinkedInfo(): Promise<WifiLinkedInfo>--><!--Device-wifi-function getLinkedInfo(): Promise<WifiLinkedInfo>-End-->

**System capability:** SystemCapability.Communication.WiFi.STA

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[WifiLinkedInfo](arkts-connectivity-wifi-wifilinkedinfo-i.md)&gt; | Promise used to return the Wi-Fi connection information. |

**Examples**

```TypeScript
import wifi from '@ohos.wifi';

wifi.getLinkedInfo((err, data:wifi.WifiLinkedInfo) => {
    if (err) {
        console.error("get linked info error");
        return;
    }
    console.info("get wifi linked info: " + JSON.stringify(data));
});

wifi.getLinkedInfo().then(data => {
    console.info("get wifi linked info: " + JSON.stringify(data));
}).catch((error:number) => {
    console.info("get linked info error");
});
```


## getLinkedInfo

```TypeScript
function getLinkedInfo(callback: AsyncCallback<WifiLinkedInfo>): void
```

Obtains Wi-Fi connection information. This API uses an asynchronous callback to return the result.

**Since:** 6

**Deprecated since:** 9

**Substitutes:** [getLinkedInfo](arkts-connectivity-wifimanager-getlinkedinfo-f.md)

**Required permissions:** ohos.permission.GET_WIFI_INFO

<!--Device-wifi-function getLinkedInfo(callback: AsyncCallback<WifiLinkedInfo>): void--><!--Device-wifi-function getLinkedInfo(callback: AsyncCallback<WifiLinkedInfo>): void-End-->

**System capability:** SystemCapability.Communication.WiFi.STA

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[WifiLinkedInfo](arkts-connectivity-wifi-wifilinkedinfo-i.md)&gt; | Yes | Callback used to return the result. |

**Examples**

See [getLinkedInfo](#getlinkedinfo)
