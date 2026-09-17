# queryTraceRoute

## Modules to Import

```TypeScript
import { connection } from '@kit.NetworkKit';
```

## queryTraceRoute

```TypeScript
function queryTraceRoute(destination: string, option?: TraceRouteOptions): Promise<TraceRouteInfo[]>
```

Queries the network route tracing information. This API uses a promise to return the result.

> **NOTE:** 
> 
> To call this API, the application needs to apply for the precise location permission. &lt;!--RP1--&gt;According to
> [Applying for Location Permissions (ArkTS)](../../../device/location/location-permission-guidelines.md)<!--RP1 > End-->, the caller needs to apply for both **ohos.permission.APPROXIMATELY_LOCATION** and
> **ohos.permission.LOCATION**.

**Since:** 26.0.0

**Required permissions:** ohos.permission.INTERNET and ohos.permission.ACCESS_NET_TRACE_INFO and ohos.permission.LOCATION and ohos.permission.APPROXIMATELY_LOCATION

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Communication.NetManager.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| destination | string | Yes | Target domain name or IP address, for example, www.example.com or 8.8.8.8. |
| option | [TraceRouteOptions](arkts-network-connection-tracerouteoptions-i.md) | No | Options for route tracing. If this parameter is not specified, the default configuration is used. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[TraceRouteInfo](arkts-network-connection-tracerouteinfo-i.md)[]&gt; | Promise used to return the array of route tracing information. |

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
let options: connection.TraceRouteOptions = {
    maxJumpNumber: 30,
    packetsType: connection.PacketsType.NETCONN_PACKETS_ICMP
};

connection.queryTraceRoute(dest, options).then((data: connection.TraceRouteInfo[]) => {
    console.info(JSON.stringify(data));
}).catch((err: BusinessError) => {
    console.error(JSON.stringify(err));
});
```
