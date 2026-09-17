# setCalibrationTraffic (System API)

## Modules to Import

```TypeScript
import { statistics } from '@kit.NetworkKit';
```

## setCalibrationTraffic

```TypeScript
function setCalibrationTraffic(simId: number, remainTraffic: number, totalTraffic?: number): Promise<void>
```

Sets traffic calibration data. You can use this API to set traffic data during traffic calibration. This API uses a promise to return the result.

**Since:** 26.0.0

**Required permissions:** ohos.permission.GET_NETWORK_STATS

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Communication.NetManager.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| simId | number | Yes | SIM card ID. |
| remainTraffic | number | Yes | Remaining traffic, in bytes. |
| totalTraffic | number | No | Total traffic, in bytes. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Nonsystem applications use system APIs. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. |
| [2100001](../errorcode-net-connection.md#2100001-invalid-parameter-value) | Invalid parameter value, such as simId error. |
| [2100002](../errorcode-net-connection.md#2100002-service-connection-failure) | Failed to connect to the service. |
| [2100003](../errorcode-net-connection.md#2100003-system-internal-error) | System internal error, such as nullptr. |

**Examples**

```TypeScript
import { connection, statistics } from '@kit.NetworkKit';

let simId:number = 1;
let remainData:number = 600*1024*1024;   // The remaining traffic is 600 MB.
let totalData:number = 1024*1024*1024;   // The total traffic is 1 GB.
statistics.setCalibrationTraffic(simId, remainData, totalData).then(() => {
  console.info(`setCalibrationTraffic succ`);
}).catch((error: BusinessError) => {
  console.info(`setCalibrationTraffic error. code:${error.code}, message:${error.message}`);
});
```
