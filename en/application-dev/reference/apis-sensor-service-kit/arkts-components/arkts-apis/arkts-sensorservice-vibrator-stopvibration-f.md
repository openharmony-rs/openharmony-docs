# stopVibration

## Modules to Import

```TypeScript
import { vibrator } from '@kit.SensorServiceKit';
```

## stopVibration

```TypeScript
function stopVibration(stopMode: VibratorStopMode): Promise<void>
```

Stops vibration in the specified mode. This API uses a promise to return the result.

**Since:** 9

**Required permissions:** ohos.permission.VIBRATE

**System capability:** SystemCapability.Sensors.MiscDevice

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| stopMode | [VibratorStopMode](arkts-sensorservice-vibrator-vibratorstopmode-e.md) | Yes | Vibration stop mode:<br>- **VIBRATOR_STOP_MODE_TIME**: used to stop vibration of the specified duration.<br>- **VIBRATOR_STOP_MODE_PRESET**: used to stop vibration of the preset effect.<br>To stop custom vibration, use [vibrator.stopVibration&lt;sup&gt;10+&lt;/sup&gt;](arkts-sensorservice-vibrator-stopvibration-f.md). |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns the result. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br> 2. Incorrect parameter types; 3. Parameter verification failed. |

**Examples**

Stop vibration of the specified duration.

```TypeScript
import { vibrator } from '@kit.SensorServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

// Use try catch to capture possible exceptions.
try {
  // Start vibration of the specified duration.
  vibrator.startVibration({
    type: 'time',
    duration: 1000,
  }, {
    id: 0,
    usage: 'alarm' // The switch control is subject to the selected type.
  }).then(() => {
    console.info('Succeed in starting vibration');
  }, (error: BusinessError) => {
    console.error(`Failed to start vibration. Code: ${error.code}, message: ${error.message}`);
  });
} catch (err) {
  let e: BusinessError = err as BusinessError;
  console.error(`An unexpected error occurred. Code: ${e.code}, message: ${e.message}`);
}

try {
  // Stop vibration in VIBRATOR_STOP_MODE_TIME mode.
  vibrator.stopVibration(vibrator.VibratorStopMode.VIBRATOR_STOP_MODE_TIME).then(() => {
    console.info('Succeed in stopping vibration');
  }, (error: BusinessError) => {
    console.error(`Failed to stop vibration. Code: ${error.code}, message: ${error.message}`);
  });
} catch (err) {
  let e: BusinessError = err as BusinessError;
  console.error(`An unexpected error occurred. Code: ${e.code}, message: ${e.message}`);
}
```

Stop preset vibration.

```TypeScript
import { vibrator } from '@kit.SensorServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  // Start vibration based on a preset effect.
  vibrator.startVibration({
    type: 'preset',
    effectId: 'haptic.notice.success',
    count: 1,
  }, {
    id: 0,
    usage: 'notification' // The switch control is subject to the selected type.
  }).then(() => {
    console.info('Succeed in starting vibration');
  }, (error: BusinessError) => {
    console.error(`Failed to start vibration. Code: ${error.code}, message: ${error.message}`);
  });
} catch (err) {
  let e: BusinessError = err as BusinessError;
  console.error(`An unexpected error occurred. Code: ${e.code}, message: ${e.message}`);
}

try {
  // Stop vibration in VIBRATOR_STOP_MODE_PRESET mode.
  vibrator.stopVibration(vibrator.VibratorStopMode.VIBRATOR_STOP_MODE_PRESET).then(() => {
    console.info('Succeed in stopping vibration');
  }, (error: BusinessError) => {
    console.error(`Failed to stop vibration. Code: ${error.code}, message: ${error.message}`);
  });
} catch (err) {
  let e: BusinessError = err as BusinessError;
  console.error(`An unexpected error occurred. Code: ${e.code}, message: ${e.message}`);
}
```


<a id="stopvibration-1"></a>

## stopVibration

```TypeScript
function stopVibration(stopMode: VibratorStopMode, callback: AsyncCallback<void>): void
```

Stops vibration in the specified mode. This API uses an asynchronous callback to return the result.

**Since:** 9

**Required permissions:** ohos.permission.VIBRATE

**System capability:** SystemCapability.Sensors.MiscDevice

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| stopMode | [VibratorStopMode](arkts-sensorservice-vibrator-vibratorstopmode-e.md) | Yes | Mode to stop the vibration. The options are as follows:<br>- **VIBRATOR_STOP_MODE_TIME**: used to stop vibration of the specified duration.<br>- **VIBRATOR_STOP_MODE_PRESET**: used to stop vibration of the preset effect.<br>To stop custom vibration, use [vibrator.stopVibration&lt;sup&gt;10+&lt;/sup&gt;](#stopvibration-2). |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. If the vibration stops, **err** is **undefined**; otherwise, **err** is an error object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br> 2. Incorrect parameter types; 3. Parameter verification failed. |

**Examples**

Stop vibration of the specified duration.

```TypeScript
import { vibrator } from '@kit.SensorServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

// Use try catch to capture possible exceptions.
try {
  // Start vibration of the specified duration.
  vibrator.startVibration({
    type: 'time',
    duration: 1000,
  }, {
    id: 0,
    usage: 'alarm' // The switch control is subject to the selected type.
  }, (error: BusinessError) => {
    if (error) {
      console.error(`Failed to start vibration. Code: ${error.code}, message: ${error.message}`);
      return;
    }
    console.info('Succeed in starting vibration');
  });
} catch (err) {
  let e: BusinessError = err as BusinessError;
  console.error(`An unexpected error occurred. Code: ${e.code}, message: ${e.message}`);
}

try {
  // Stop vibration in VIBRATOR_STOP_MODE_TIME mode.
  vibrator.stopVibration(vibrator.VibratorStopMode.VIBRATOR_STOP_MODE_TIME, (error: BusinessError) => {
    if (error) {
      console.error(`Failed to stop vibration. Code: ${error.code}, message: ${error.message}`);
      return;
    }
    console.info('Succeed in stopping vibration');
  })
} catch (err) {
  let e: BusinessError = err as BusinessError;
  console.error(`An unexpected error occurred. Code: ${e.code}, message: ${e.message}`);
}
```

Stop preset vibration.

```TypeScript
import { vibrator } from '@kit.SensorServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  // Start vibration based on a preset effect.
  vibrator.startVibration({
    type: 'preset',
    effectId: 'haptic.notice.success',
    count: 1,
  }, {
    id: 0,
    usage: 'notification' // The switch control is subject to the selected type.
  }, (error: BusinessError) => {
    if (error) {
      console.error(`Failed to start vibration. Code: ${error.code}, message: ${error.message}`);
      return;
    }
    console.info('Succeed in starting vibration');
  });
} catch (err) {
  let e: BusinessError = err as BusinessError;
  console.error(`An unexpected error occurred. Code: ${e.code}, message: ${e.message}`);
}

try {
  // Stop vibration in VIBRATOR_STOP_MODE_PRESET mode.
  vibrator.stopVibration(vibrator.VibratorStopMode.VIBRATOR_STOP_MODE_PRESET, (error: BusinessError) => {
    if (error) {
      console.error(`Failed to stop vibration. Code: ${error.code}, message: ${error.message}`);
      return;
    }
    console.info('Succeed in stopping vibration');
  })
} catch (err) {
  let e: BusinessError = err as BusinessError;
  console.error(`An unexpected error occurred. Code: ${e.code}, message: ${e.message}`);
}
```


<a id="stopvibration-2"></a>

## stopVibration

```TypeScript
function stopVibration(callback: AsyncCallback<void>): void
```

Stops vibration in all modes. This API uses an asynchronous callback to return the result.

**Since:** 10

**Required permissions:** ohos.permission.VIBRATE

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Sensors.MiscDevice

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. If the vibration stops, **err** is **undefined**; otherwise, **err** is an error object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |

**Examples**

```TypeScript
import { vibrator } from '@kit.SensorServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

// Use try catch to capture possible exceptions.
try {
  // Stop vibration in all modes.
  vibrator.stopVibration((error: BusinessError) => {
    if (error) {
      console.error(`Failed to stop vibration. Code: ${error.code}, message: ${error.message}`);
      return;
    }
    console.info('Succeed in stopping vibration');
  })
} catch (error) {
  let e: BusinessError = error as BusinessError;
  console.error(`An unexpected error occurred. Code: ${e.code}, message: ${e.message}`);
}
```


<a id="stopvibration-3"></a>

## stopVibration

```TypeScript
function stopVibration(): Promise<void>
```

Stops vibration in all modes. This API uses a promise to return the result.

**Since:** 10

**Required permissions:** ohos.permission.VIBRATE

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Sensors.MiscDevice

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns the result. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |

**Examples**

```TypeScript
import { vibrator } from '@kit.SensorServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

// Use try catch to capture possible exceptions.
try {
  // Stop vibration in all modes.
  vibrator.stopVibration().then(() => {
    console.info('Succeed in stopping vibration');
  }, (error: BusinessError) => {
    console.error(`Failed to stop vibration. Code: ${error.code}, message: ${error.message}`);
  });
} catch (error) {
  let e: BusinessError = error as BusinessError;
  console.error(`An unexpected error occurred. Code: ${e.code}, message: ${e.message}`);
}
```


<a id="stopvibration-4"></a>

## stopVibration

```TypeScript
function stopVibration(param?: VibratorInfoParam): Promise<void>
```

Stops vibration based on the specified vibrator parameters. If no parameters are passed, this API stops all vibrators of the local device by default. This API uses a promise to return the result.

**Since:** 19

**Required permissions:** ohos.permission.VIBRATE

**System capability:** SystemCapability.Sensors.MiscDevice

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| param | [VibratorInfoParam](arkts-sensorservice-vibrator-vibratorinfoparam-i.md) | No | Vibrator parameters, such as the specified device and vibrator. If this parameter is left unspecified, this API applies to all vibrators of the local device by default. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns the result. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [14600101](../errorcode-vibrator.md#14600101-device-operation-failed) | Device operation failed. |

**Examples**

```TypeScript
import { vibrator } from '@kit.SensorServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

function vibratorDemo() {
  // Query information about all vibrators.
  const vibratorInfoList: vibrator.VibratorInfo[] = vibrator.getVibratorInfoSync();
  // Obtain the target vibrator based on the actual service logic. The following example shows how to obtain the local vibrator. You need to adjust the filtering logic as required.
  const targetVibrator = vibratorInfoList.find((vibrator: vibrator.VibratorInfo) => {
    return vibrator.isLocalVibrator;
  });
  if (!targetVibrator) {
    return;
  }
  // Call vibrator.startVibration to start vibration.
  // ...

  // Use try catch to capture possible exceptions.
  try {
    // Stop the vibration based on the actual service scenario.
    vibrator.stopVibration({ deviceId: targetVibrator.deviceId, vibratorId: targetVibrator.vibratorId }).then(() => {
      console.info('Succeed in stopping vibration');
    }, (error: BusinessError) => {
      console.error(`Failed to stop vibration. Code: ${error.code}, message: ${error.message}`);
    });
  } catch (error) {
    let e: BusinessError = error as BusinessError;
    console.error(`An unexpected error occurred. Code: ${e.code}, message: ${e.message}`);
  }
}
```
