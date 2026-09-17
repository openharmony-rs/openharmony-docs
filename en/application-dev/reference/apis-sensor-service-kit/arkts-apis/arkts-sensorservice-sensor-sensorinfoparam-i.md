# SensorInfoParam

Defines sensor parameters, including **deviceId** and **sensorIndex**.

**Since:** 19

**System capability:** SystemCapability.Sensors.Sensor

## Modules to Import

```TypeScript
import { sensor } from '@kit.SensorServiceKit';
```

## deviceId

```TypeScript
deviceId?: number
```

Device ID. The default value is -1, indicating the local device. You can use [getSensorList](arkts-sensorservice-sensor-getsensorlist-f.md) or [sensorStatusChange](arkts-sensorservice-sensor-on-f.md#onsensorstatuschange) to obtain the device ID.

**Type:** number

**Since:** 19

**Atomic service API:** This API can be used in atomic services since API version 19.

**System capability:** SystemCapability.Sensors.Sensor

## sensorIndex

```TypeScript
sensorIndex?: number
```

Sensor index. The default value is **0**, indicating the default sensor on the device. You can use [getSensorList](arkts-sensorservice-sensor-getsensorlist-f.md) or [sensorStatusChange](arkts-sensorservice-sensor-on-f.md#onsensorstatuschange) to obtain the sensor index.

**Type:** number

**Since:** 19

**Atomic service API:** This API can be used in atomic services since API version 19.

**System capability:** SystemCapability.Sensors.Sensor
