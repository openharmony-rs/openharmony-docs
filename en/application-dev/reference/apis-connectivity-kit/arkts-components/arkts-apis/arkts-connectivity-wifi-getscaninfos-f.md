# getScanInfos

## Modules to Import

```TypeScript
import { wifi } from '@kit.ConnectivityKit';
```

## getScanInfos

```TypeScript
function getScanInfos(): Promise<Array<WifiScanInfo>>
```

Obtains the hotspot information that scanned.

**Since:** 6

**Deprecated since:** 9

**Substitutes:** [getScanInfoList](arkts-connectivity-wifimanager-getscaninfolist-f.md)

**Required permissions:** ohos.permission.GET_WIFI_INFO and (ohos.permission.GET_WIFI_PEERS_MAC or ohos.permission.LOCATION)

**System capability:** SystemCapability.Communication.WiFi.STA

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;Array&lt;[WifiScanInfo](arkts-connectivity-wifi-wifiscaninfo-i.md)&gt;&gt; | Returns information about scanned Wi-Fi hotspot if any. |

**Examples**

```TypeScript
import wifi from '@ohos.wifi';

wifi.getScanInfos().then(result => {
    let len = result.length;
    console.info("wifi received scan info: " + len);
    for (let i = 0; i < len; ++i) {
        console.info("ssid: " + result[i].ssid);
        console.info("bssid: " + result[i].bssid);
        console.info("capabilities: " + result[i].capabilities);
        console.info("securityType: " + result[i].securityType);
        console.info("rssi: " + result[i].rssi);
        console.info("band: " + result[i].band);
        console.info("frequency: " + result[i].frequency);
        console.info("channelWidth: " + result[i].channelWidth);
        console.info("timestamp: " + result[i].timestamp);
    }
});
```


## getScanInfos

```TypeScript
function getScanInfos(callback: AsyncCallback<Array<WifiScanInfo>>): void
```

Obtains the hotspot information that scanned.

**Since:** 6

**Deprecated since:** 9

**Substitutes:** [getScanInfoList](arkts-connectivity-wifimanager-getscaninfolist-f.md)

**Required permissions:** ohos.permission.GET_WIFI_INFO and (ohos.permission.GET_WIFI_PEERS_MAC or ohos.permission.LOCATION)

**System capability:** SystemCapability.Communication.WiFi.STA

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;Array&lt;[WifiScanInfo](arkts-connectivity-wifi-wifiscaninfo-i.md)&gt;&gt; | Yes |  |

**Examples**

See [getScanInfos](#getscaninfos)
