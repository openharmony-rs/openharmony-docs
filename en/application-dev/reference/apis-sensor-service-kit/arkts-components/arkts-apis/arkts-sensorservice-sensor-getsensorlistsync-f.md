# getSensorListSync

## Modules to Import

```TypeScript
import { sensor } from '@kit.SensorServiceKit';
```

## getSensorListSync

```TypeScript
function getSensorListSync(): Array<Sensor>
```

Obtains information about all sensors on the device. This API returns the result synchronously.

**Since:** 12

**System capability:** SystemCapability.Sensors.Sensor

**Return value:**

| Type | Description |
| --- | --- |
| Array&lt;[Sensor](arkts-sensorservice-sensor-sensor-i.md)&gt; | List of sensor attributes. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [14500101](../errorcode-sensor.md#14500101-service-exception) | Service exception. Possible causes: 1. Sensor hdf service exception;<br> 2. Sensor service ipc exception;3. Sensor data channel exception. |

**Examples**

```TypeScript
import { sensor } from '@kit.SensorServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

// Use try catch to capture possible exceptions.
try {
  let ret = sensor.getSensorListSync()
  for (let i = 0; i < ret.length; i++) {
    console.info('Succeeded in getting sensor: ' + JSON.stringify(ret[i]));
  }
} catch(error) {
    let e: BusinessError = error as BusinessError;
    console.error(`Failed to get singleSensor . Code: ${e.code}, message: ${e.message}`);
}
```
