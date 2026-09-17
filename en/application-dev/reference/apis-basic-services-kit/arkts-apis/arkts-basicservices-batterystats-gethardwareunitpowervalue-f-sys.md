# getHardwareUnitPowerValue (System API)

## Modules to Import

```TypeScript
import { batteryStats } from '@kit.BasicServicesKit';
```

## getHardwareUnitPowerValue

```TypeScript
function getHardwareUnitPowerValue(type: ConsumptionType): number
```

Obtains the power consumption of a hardware unit according to the consumption type, in unit of mAh.

**Since:** 8

**System capability:** SystemCapability.PowerManager.BatteryStatistics

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | [ConsumptionType](arkts-basicservices-batterystats-consumptiontype-e-sys.md) | Yes | Power consumption type. The value must be an enum. |

**Return value:**

| Type | Description |
| --- | --- |
| number | Power consumption of the hardware unit corresponding to the power consumption type, in unit of mAh. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Parameter verification failed. |
| [4600101](../errorcode-batteryStatistics.md#4600101-service-connection-failure) | Failed to connect to the service. |

**Examples**

```TypeScript
try {
    let value = batteryStats.getHardwareUnitPowerValue(batteryStats.ConsumptionType.CONSUMPTION_TYPE_SCREEN);
    console.info('battery statistics value of hardware is: ' + value);
} catch(err) {
    console.error('get battery statistics percent of hardware failed, err: ' + err);
}
```
