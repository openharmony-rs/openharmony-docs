# getAppPowerPercent (System API)

## Modules to Import

```TypeScript
import { batteryStats } from '@kit.BasicServicesKit';
```

## getAppPowerPercent

```TypeScript
function getAppPowerPercent(uid: number): number
```

Obtains the proportion of the power consumption of an application.

**Since:** 8

**System capability:** SystemCapability.PowerManager.BatteryStatistics

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| uid | number | Yes | Application UID. |

**Return value:**

| Type | Description |
| --- | --- |
| number | Proportion of the power consumption of an application with this UID, which ranges from 0.00 to 1.00. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Parameter verification failed. |
| [4600101](../errorcode-batteryStatistics.md#4600101-service-connection-failure) | Failed to connect to the service. |

**Examples**

```TypeScript
try {
    let percent = batteryStats.getAppPowerPercent(10021);
    console.info('battery statistics percent of app is: ' + percent);
} catch(err) {
    console.error('get battery statistics percent of app failed, err: ' + err);
}
```
