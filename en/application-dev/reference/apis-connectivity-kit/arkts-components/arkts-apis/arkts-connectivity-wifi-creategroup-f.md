# createGroup

## Modules to Import

```TypeScript
import { wifi } from '@kit.ConnectivityKit';
```

## createGroup

```TypeScript
function createGroup(config: WifiP2PConfig): boolean
```

Creates a P2P group.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** createP2pGroup

**Required permissions:** ohos.permission.GET_WIFI_INFO

**System capability:** SystemCapability.Communication.WiFi.P2P

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| config | [WifiP2PConfig](arkts-connectivity-wifi-wifip2pconfig-i.md) | Yes | Indicates the configuration for creating a group. |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Returns `true` if the operation is successful, returns `false` otherwise. |

**Examples**

```TypeScript
import wifi from '@ohos.wifi';

try {
  let config:wifi.WifiP2PConfig = {
    deviceAddress: "****",
    netId: 0,
    passphrase: "*****",
    groupName: "****",
    goBand: 0
  }
  wifi.createGroup(config);  
  
}catch(error){
  console.error("failed:" + JSON.stringify(error));
}
```
