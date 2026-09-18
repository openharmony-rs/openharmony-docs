# getCurrentGroup

## Modules to Import

```TypeScript
import { wifi } from '@kit.ConnectivityKit';
```

## getCurrentGroup

```TypeScript
function getCurrentGroup(): Promise<WifiP2pGroupInfo>
```

Obtains information about the current group.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [getCurrentGroup](arkts-connectivity-wifimanager-getcurrentgroup-f.md)

**Required permissions:** ohos.permission.GET_WIFI_INFO and ohos.permission.LOCATION

**System capability:** SystemCapability.Communication.WiFi.P2P

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[WifiP2pGroupInfo](arkts-connectivity-wifi-wifip2pgroupinfo-i.md)&gt; | Returns the current group information. |

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

Obtains information about the current group.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [getCurrentGroup](arkts-connectivity-wifimanager-getcurrentgroup-f.md)

**Required permissions:** ohos.permission.GET_WIFI_INFO and ohos.permission.LOCATION

**System capability:** SystemCapability.Communication.WiFi.P2P

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[WifiP2pGroupInfo](arkts-connectivity-wifi-wifip2pgroupinfo-i.md)&gt; | Yes |  |

**Examples**

See [getCurrentGroup](#getcurrentgroup)
