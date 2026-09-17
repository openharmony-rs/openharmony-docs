# setPacFileUrl

## Modules to Import

```TypeScript
import { connection } from '@kit.NetworkKit';
```

## setPacFileUrl

```TypeScript
function setPacFileUrl(pacFileUrl: string): void
```

Sets the URL of the Proxy Auto-Configuration Script (PAC) and enables the PAC proxy capability, for example, http:/ /127.0.0.1:21998/PacProxyScript.pac. You can call [findProxyForUrl](arkts-network-connection-findproxyforurl-f.md) to parse the URL and obtain the proxy information.

> **NOTE:** 
> 
> 1. This API can parse scripts and enable the PAC proxy capability on **PC/2in1&lt;sup&gt;20+&lt;/sup&gt;**,
> **Phone&lt;sup&gt;23+&lt;/sup&gt;**, **Tablet&lt;sup&gt;23+&lt;/sup&gt;** and **TV&lt;sup&gt;23+&lt;/sup&gt;** devices. For wearable devices, only
> the script address is saved, and the PAC proxy capability is not enabled.

> 2. This API does not verify the URL authenticity. If the URL is incorrect when the PAC proxy is enabled, the proxy fails to be enabled and error code 2100002 is returned.

**Since:** 20

**Required permissions:** ohos.permission.SET_PAC_URL

**System capability:** SystemCapability.Communication.NetManager.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| pacFileUrl | string | Yes | URL of the current PAC script. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [2100002](../errorcode-net-connection.md#2100002-service-connection-failure) | Failed to connect to the service. |

**Examples**

```TypeScript
import { connection } from '@kit.NetworkKit';

let pacFileUrl = "http://example.com/proxy.pac";
connection.setPacFileUrl(pacFileUrl);
```
