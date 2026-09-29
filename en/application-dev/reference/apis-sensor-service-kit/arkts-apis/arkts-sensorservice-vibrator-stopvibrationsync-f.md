# stopVibrationSync

## Modules to Import

```TypeScript
import { vibrator } from '@kit.SensorServiceKit';
```

## stopVibrationSync

```TypeScript
function stopVibrationSync(): void
```

Stops any form of vibration.

**Atomic service API**: This API can be used in atomic services since API version 12.

**Since:** 12

**Required permissions:** ohos.permission.VIBRATE

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 12.

<!--Device-vibrator-function stopVibrationSync(): void--><!--Device-vibrator-function stopVibrationSync(): void-End-->

**System capability:** SystemCapability.Sensors.MiscDevice

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission<br> required to call the API. |
| [14600101](../errorcode-vibrator.md#14600101-device-operation-failed) | Device operation failed. |

**Examples**

```TypeScript
import { vibrator } from '@kit.SensorServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

// Use try catch to capture possible exceptions.
try {
  // Stop any form of vibration.
  vibrator.stopVibrationSync()
  console.info('Succeed in stopping vibration');
} catch (error) {
  let e: BusinessError = error as BusinessError;
  console.error(`An unexpected error occurred. Code: ${e.code}, message: ${e.message}`);
}
```
