# getBatteryStats (System API)

## Modules to Import

```TypeScript
import { batteryStats } from '@kit.BasicServicesKit';
```

## getBatteryStats

```TypeScript
function getBatteryStats(): Promise<Array<BatteryStatsInfo>>
```

Obtains the power consumption information list. This API uses a promise to return the result.

**Since:** 8

**System capability:** SystemCapability.PowerManager.BatteryStatistics

**System API:** This is a system API.

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;Array&lt;[BatteryStatsInfo](arkts-basicservices-batterystats-batterystatsinfo-i-sys.md)&gt;&gt; | Promise used to return the power consumption information list. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |
| [4600101](../errorcode-batteryStatistics.md#4600101-service-connection-failure) | Failed to connect to the service. |

**Examples**

```TypeScript
batteryStats.getBatteryStats()
.then((data: batteryStats.BatteryStatsInfo[]) => {
    console.info('battery statistics info: ' + data);
})
.catch((err: Error) => {
    console.error('get battery statistics failed, err: ' + err);
});
```


<a id="getbatterystats-1"></a>

## getBatteryStats

```TypeScript
function getBatteryStats(callback: AsyncCallback<Array<BatteryStatsInfo>>): void
```

Obtains the power consumption information list. This API uses an asynchronous callback to return the result.

**Since:** 8

**System capability:** SystemCapability.PowerManager.BatteryStatistics

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](arkts-basicservices-base-asynccallback-i.md)&lt;Array&lt;[BatteryStatsInfo](arkts-basicservices-batterystats-batterystatsinfo-i-sys.md)&gt;&gt; | Yes | Callback used to return the result. If the operation is successful, **err** is undefined and **data** is the obtained Array&lt;[BatteryStatsInfo](arkts-basicservices-batterystats-batterystatsinfo-i-sys.md)&gt;. Otherwise, **err** is an error object. **AsyncCallback** has encapsulated an API of the **BatteryStatsInfo** class. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Parameter verification failed. |
| [4600101](../errorcode-batteryStatistics.md#4600101-service-connection-failure) | Failed to connect to the service. |

**Examples**

```TypeScript
batteryStats.getBatteryStats((err: Error, data : batteryStats.BatteryStatsInfo[]) => {
    if (typeof err === 'undefined') {
        console.info('battery statistics info: ' + data);
    } else {
        console.error('get battery statistics failed, err: ' + err);
    }
});
```
