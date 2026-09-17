# getMacAddress

## Modules to Import

```TypeScript
import { ethernet } from '@kit.NetworkKit';
```

## getMacAddress

```TypeScript
function getMacAddress(): Promise<Array<MacAddressInfo>>
```

Obtains the names and MAC addresses of all Ethernet NICs. This API uses a promise to return the result.

**Required permission**: ohos.permission.GET_ETHERNET_LOCAL_MAC

**Since:** 14

**Required permissions:** ohos.permission.GET_ETHERNET_LOCAL_MAC

**System capability:** SystemCapability.Communication.NetManager.Ethernet

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;Array&lt;[MacAddressInfo](arkts-network-ethernet-macaddressinfo-i.md)&gt;&gt; | Promise used to return the result. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [2200002](../errorcode-net-ethernet.md#2200002-service-connection-failure) | Operation failed. Cannot connect to service. |
| [2201005](../errorcode-net-ethernet.md#2201005-device-information-not-exist) | Device information does not exist. |

**Examples**

```TypeScript
import { ethernet } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';

ethernet.getMacAddress().then((data: Array<ethernet.MacAddressInfo>) => {
  console.info("getMacAddress promise data = " + JSON.stringify(data));
}).catch((error: BusinessError) => {
  console.error("getMacAddress promise error = " + JSON.stringify(error));
});
```
