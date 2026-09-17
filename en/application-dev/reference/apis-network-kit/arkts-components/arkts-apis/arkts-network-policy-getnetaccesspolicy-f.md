# getNetAccessPolicy

## Modules to Import

```TypeScript
import { policy } from '@kit.NetworkKit';
```

## getNetAccessPolicy

```TypeScript
function getNetAccessPolicy(): Promise<NetAccessPolicy>
```

Queries the network access policy of an application (whether cellular or Wi-Fi network access is allowed). You can check the policy by choosing **Settings**  
> **Mobile network**
> **Manage data usage**
> **Network access**. This API uses a promise to return the result.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Communication.NetManager.Core

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[NetAccessPolicy](arkts-network-policy-netaccesspolicy-i.md)&gt; | Promise used to return the network access policy of the application. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [2100002](../errorcode-net-connection.md#2100002-service-connection-failure) | Failed to connect to the service. |
| [2100003](../errorcode-net-connection.md#2100003-system-internal-error) | System internal error, such as nullptr。 |

**Examples**

```TypeScript
import { policy } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';

policy.getNetAccessPolicy().then((policyInfo: policy.NetAccessPolicy) => {
  console.info(`getNetAccessPolicy success. WiFi: ${policyInfo.allowWiFi}, Cellular: ${policyInfo.allowCellular}`);
}).catch((err: BusinessError) => {
  console.error(`getNetAccessPolicy fail. error info: ${err.code} - ${err.message}`);
});
```
