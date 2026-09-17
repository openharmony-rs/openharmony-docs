# getMonthTrafficStats (System API)

## Modules to Import

```TypeScript
import { statistics } from '@kit.NetworkKit';
```

## getMonthTrafficStats

```TypeScript
function getMonthTrafficStats(simId: number): Promise<number>
```

Get this month traffic data of the cellular network.

**Since:** 23

**Required permissions:** ohos.permission.GET_NETWORK_STATS

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Communication.NetManager.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| simId | number | Yes | The id of the specified sim card. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;number&gt; | The statistics of the simId in this month. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Nonsystem applications use system APIs. |
| [2100001](../errorcode-net-connection.md#2100001-invalid-parameter-value) | Invalid parameter value. |
| [2100002](../errorcode-net-connection.md#2100002-service-connection-failure) | Failed to connect to the service. |
