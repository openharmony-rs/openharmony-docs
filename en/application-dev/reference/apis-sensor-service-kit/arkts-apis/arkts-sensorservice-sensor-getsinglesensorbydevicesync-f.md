# getSingleSensorByDeviceSync

## Modules to Import

```TypeScript
import { sensor } from '@kit.SensorServiceKit';
```

## getSingleSensorByDeviceSync

```TypeScript
function getSingleSensorByDeviceSync(type: SensorId, deviceId?: number): Array<Sensor>
```

Obtains information about the sensor of a specific type. If peripherals exist and no device ID is specified, the obtained sensors will be all local and peripheral sensors that match the specified sensor type. If no peripherals exist, only local sensors are obtained.

**Since:** 19

<!--Device-sensor-function getSingleSensorByDeviceSync(type: SensorId, deviceId?: int): Array<Sensor>--><!--Device-sensor-function getSingleSensorByDeviceSync(type: SensorId, deviceId?: int): Array<Sensor>-End-->

**System capability:** SystemCapability.Sensors.Sensor

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | [SensorId](arkts-sensorservice-sensor-sensorid-e.md) | Yes | Sensor type. |
| deviceId | number | No | Device ID. The default value is **-1**, indicating the local device. You can use [getSensorList](arkts-sensorservice-sensor-getsensorlist-f.md) or [sensorStatusChange](arkts-sensorservice-sensor-on-f.md#onsensorstatuschange) to obtain the device ID. |

**Return value:**

| Type | Description |
| --- | --- |
| Array&lt;[Sensor](arkts-sensorservice-sensor-sensor-i.md)&gt; | Sensor attribute list. |

**Examples**

```TypeScript
import { sensor } from '@kit.SensorServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  const deviceId = 1;
  // The second deviceId is optional.
  const sensorList: sensor.Sensor[] = sensor.getSingleSensorByDeviceSync(sensor.SensorId.ACCELEROMETER, deviceId);
  console.info(`sensorList length: ${sensorList.length}`);
  console.info(`sensorList Json: ${JSON.stringify(sensorList)}`);
} catch (error) {
  let e: BusinessError = error as BusinessError;
  console.error(`Failed to get sensorList. Code: ${e.code}, message: ${e.message}`);
}
```
