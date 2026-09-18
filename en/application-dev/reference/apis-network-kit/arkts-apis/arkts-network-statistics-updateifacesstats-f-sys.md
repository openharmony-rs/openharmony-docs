# updateIfacesStats (System API)

## Modules to Import

```TypeScript
import { statistics } from '@kit.NetworkKit';
```

## updateIfacesStats

```TypeScript
function updateIfacesStats(iface: string, start: number, end: number, stats: NetStatsInfo): Promise<void>
```

Updates network interface statistics data.

**Since:** 26.0.0

**Required permissions:** ohos.permission.GET_NETWORK_STATS

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Communication.NetManager.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| iface | string | Yes | Network interface name. |
| start | number | Yes | Start timestamp for the statistics data to update. |
| end | number | Yes | End timestamp for the statistics data to update. |
| stats | [NetStatsInfo](arkts-network-statistics-netstatsinfo-i.md) | Yes | Network statistics information. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | The promise returned by the function. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Non-system applications use system APIs. |
| [2100001](../errorcode-net-connection.md#2100001-invalid-parameter-value) | Invalid parameter value. |
| [2100002](../errorcode-net-connection.md#2100002-service-connection-failure) | Failed to connect to the service. |
| [2100003](../errorcode-net-connection.md#2100003-system-internal-error) | System internal error. |
