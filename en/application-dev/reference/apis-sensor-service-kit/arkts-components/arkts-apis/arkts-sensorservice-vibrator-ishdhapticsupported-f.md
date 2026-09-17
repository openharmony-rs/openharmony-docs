# isHdHapticSupported

## Modules to Import

```TypeScript
import { vibrator } from '@kit.SensorServiceKit';
```

## isHdHapticSupported

```TypeScript
function isHdHapticSupported(): boolean
```

Checks whether HD vibration is supported.

**Since:** 12

**System capability:** SystemCapability.Sensors.MiscDevice

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Boolean value indicating whether HD vibration is supported. The value **true** indicates that HD vibration is supported, and the value **false** indicates the opposite. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [14600101](../errorcode-vibrator.md#14600101-device-operation-failed) | Device operation failed. |

**Examples**

```TypeScript
import { vibrator } from '@kit.SensorServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

// Use try catch to capture possible exceptions.
try {
  // Check whether HD vibration is supported.
  let ret = vibrator.isHdHapticSupported();
  console.info(`The query result is ${ret}`);
} catch (error) {
  let e: BusinessError = error as BusinessError;
  console.error(`An unexpected error occurred. Code: ${e.code}, message: ${e.message}`);
}
```
