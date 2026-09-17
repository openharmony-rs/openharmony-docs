# getLinkedInfo

## Modules to Import

```TypeScript
import { wifi } from '@kit.ConnectivityKit';
```

## getLinkedInfo

```TypeScript
function getLinkedInfo(): Promise<WifiLinkedInfo>
```

Obtains information about a Wi-Fi connection.

**Since:** 6

**Deprecated since:** 9

**Substitutes:** [getLinkedInfo](arkts-connectivity-wifimanager-getlinkedinfo-f.md)

**Required permissions:** ohos.permission.GET_WIFI_INFO

**System capability:** SystemCapability.Communication.WiFi.STA

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[WifiLinkedInfo](arkts-connectivity-wifi-wifilinkedinfo-i.md)&gt; | Returns Wi-Fi linked information. |

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

Obtains information about a Wi-Fi connection.

**Since:** 6

**Deprecated since:** 9

**Substitutes:** [getLinkedInfo](arkts-connectivity-wifimanager-getlinkedinfo-f.md)

**Required permissions:** ohos.permission.GET_WIFI_INFO

**System capability:** SystemCapability.Communication.WiFi.STA

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[WifiLinkedInfo](arkts-connectivity-wifi-wifilinkedinfo-i.md)&gt; | Yes |  |

**Examples**

See [getLinkedInfo](#getlinkedinfo)
