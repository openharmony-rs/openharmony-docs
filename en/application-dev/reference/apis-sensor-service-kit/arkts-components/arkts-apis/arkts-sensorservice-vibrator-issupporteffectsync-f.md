# isSupportEffectSync

## Modules to Import

```TypeScript
import { vibrator } from '@kit.SensorServiceKit';
```

## isSupportEffectSync

```TypeScript
function isSupportEffectSync(effectId: string): boolean
```

Checks whether the preset vibration effect is supported.

**Since:** 12

**System capability:** SystemCapability.Sensors.MiscDevice

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| effectId | string | Yes | Effect ID. The value is a string of a maximum of 64 characters. If the length exceeds 64 characters, the first 64 characters are used. |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Returned object. The value **true** means that the effect ID is supported, and the value **false** means the opposite. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br> 2. Incorrect parameter types; 3. Parameter verification failed. |
| [14600101](../errorcode-vibrator.md#14600101-device-operation-failed) | Device operation failed. |

**Examples**

```TypeScript
import { vibrator } from '@kit.SensorServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

// Use try catch to capture possible exceptions.
try {
  // Check whether the preset 'haptic.notice.success' is supported.
  let ret = vibrator.isSupportEffectSync('haptic.notice.success');
  console.info(`The query result is ${ret}`);
} catch (error) {
  let e: BusinessError = error as BusinessError;
  console.error(`An unexpected error occurred. Code: ${e.code}, message: ${e.message}`);
}
```
