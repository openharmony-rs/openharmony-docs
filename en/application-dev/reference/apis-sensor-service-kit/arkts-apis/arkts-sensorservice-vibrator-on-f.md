# on

## Modules to Import

```TypeScript
import { vibrator } from '@kit.SensorServiceKit';
```

## on('vibratorStateChange')

```TypeScript
function on(type: 'vibratorStateChange', callback: Callback<VibratorStatusEvent>): void
```

Enables listening for vibrator status changes.

**Since:** 19

**System capability:** SystemCapability.Sensors.MiscDevice

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'vibratorStateChange' | Yes | Event type. The value **vibratorStateChange** indicates a vibrator online/ offline event. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[VibratorStatusEvent](arkts-sensorservice-vibrator-vibratorstatusevent-i.md)&gt; | Yes | Callback used to return the vibrator status change event. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [14600101](../errorcode-vibrator.md#14600101-device-operation-failed) | Device operation failed. |

**Examples**

```TypeScript
import { vibrator } from '@kit.SensorServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

// Callback
const vibratorStateChangeCallback = (data: vibrator.VibratorStatusEvent) => {
  console.info('vibrator state callback info:', JSON.stringify(data));
}

// Use try catch to capture possible exceptions.
try {
  // Subscribe to vibratorStateChange events.
  vibrator.on('vibratorStateChange', vibratorStateChangeCallback);
} catch (error) {
  let e: BusinessError = error as BusinessError;
  console.error(`An unexpected error occurred. Code: ${e.code}, message: ${e.message}`);
}
```
