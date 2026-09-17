# getAppPowerValue (System API)

## Modules to Import

```TypeScript
import { batteryStats } from '@kit.BasicServicesKit';
```

## getAppPowerValue

```TypeScript
function getAppPowerValue(uid: number): number
```

Obtains the power consumption of an application, in unit of mAh.

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
| number | Power consumption of the application with this UID, in unit of mAh. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Parameter verification failed. |
| [4600101](../errorcode-batteryStatistics.md#4600101-service-connection-failure) | Failed to connect to the service. |

**Examples**

```TypeScript
try {
    let value = batteryStats.getAppPowerValue(10021);
    console.info('battery statistics value of app is: ' + value);
} catch(err) {
    console.error('get battery statistics value of app failed, err: ' + err);
}
```
