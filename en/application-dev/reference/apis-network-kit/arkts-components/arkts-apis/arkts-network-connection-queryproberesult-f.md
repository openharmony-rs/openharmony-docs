# queryProbeResult

## Modules to Import

```TypeScript
import { connection } from '@kit.NetworkKit';
```

## queryProbeResult

```TypeScript
function queryProbeResult(destination: string, duration: number): Promise<ProbeResultInfo>
```

Queries network probe results. If an exception (for example, network disconnection) occurs and the request fails to be sent, the API immediately returns the result without performing subsequent probe. This API uses a promise to return the result.

> **NOTE:** 
> 
> This API is used to perform network probe on a target host for a period of time to obtain the packet loss rate
> and RTT information.

**Since:** 26.0.0

**Required permissions:** ohos.permission.INTERNET

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Communication.NetManager.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| destination | string | Yes | Target domain name or IP address, for example, www.example.com or 8.8.8.8. |
| duration | number | Yes | Probe duration, in seconds. The value range is [1, 1000]. The probe interval is one second. If no exception (such as network disconnection) occurs, the probe result is returned when the probe duration expires. This field indicates the total probe duration. If the value is too large, application thread resources may be occupied for a long time. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[ProbeResultInfo](arkts-network-connection-proberesultinfo-i.md)&gt; | Promise used to return the probe result. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [2100001](../errorcode-net-connection.md#2100001-invalid-parameter-value) | Invalid parameter value. |
| [2100003](../errorcode-net-connection.md#2100003-system-internal-error) | Internal error. |

**Examples**

```TypeScript
import { connection } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';

let dest: string = "www.example.com";
let duration: number = 10;

connection.queryProbeResult(dest, duration).then((data: connection.ProbeResultInfo) => {
    console.info(`LossRate: ${data.lossRate}, RTT: ${data.rtt}`);
}).catch((err: BusinessError) => {
    console.error(JSON.stringify(err));
});
```
