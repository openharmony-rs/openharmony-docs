# getTrafficPlanInfo (System API)

## Modules to Import

```TypeScript
import { statistics } from '@kit.NetworkKit';
```

## getTrafficPlanInfo

```TypeScript
function getTrafficPlanInfo(simId: number, planParam: TrafficPlanParam): Promise<number>
```

Get traffic plan info.

**Since:** 26.0.0

**Required permissions:** ohos.permission.GET_NETWORK_STATS

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Communication.NetManager.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| simId | number | Yes | The id of the specified sim card. |
| planParam | [TrafficPlanParam](arkts-network-statistics-trafficplanparam-e-sys.md) | Yes | The param of the specified traffic plan. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;number&gt; | The value of parameter. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Nonsystem applications use system APIs. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. |
| [2100001](../errorcode-net-connection.md#2100001-invalid-parameter-value) | Invalid parameter value, such as simId error. |
| [2100002](../errorcode-net-connection.md#2100002-service-connection-failure) | Failed to connect to the service. |
