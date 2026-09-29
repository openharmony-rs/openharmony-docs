# SensorStatusEvent

```TypeScript
interface SensorStatusEvent
```

Defines the sensor status change event, which is used to describe the sensor online and offline events.

**Since:** 19

<!--Device-sensor-interface SensorStatusEvent--><!--Device-sensor-interface SensorStatusEvent-End-->

**System capability:** SystemCapability.Sensors.Sensor

## Modules to Import

```TypeScript
import { sensor } from '@kit.SensorServiceKit';
```

## deviceId

```TypeScript
deviceId: number
```

Device ID. The value **-1** indicates a local device, and other values indicate remote devices.

**Type:** number

**Since:** 19

<!--Device-SensorStatusEvent-deviceId: int--><!--Device-SensorStatusEvent-deviceId: int-End-->

**System capability:** SystemCapability.Sensors.Sensor

## deviceName

```TypeScript
deviceName: string
```

Device name, which identifies the source device of the sensor.

**Type:** string

**Since:** 19

<!--Device-SensorStatusEvent-deviceName: string--><!--Device-SensorStatusEvent-deviceName: string-End-->

**System capability:** SystemCapability.Sensors.Sensor

## isSensorOnline

```TypeScript
isSensorOnline: boolean
```

Whether a sensor is online. The value **true** indicates that the sensor is online, and the value **false** indicates that the sensor is offline.

**Type:** boolean

**Since:** 19

<!--Device-SensorStatusEvent-isSensorOnline: boolean--><!--Device-SensorStatusEvent-isSensorOnline: boolean-End-->

**System capability:** SystemCapability.Sensors.Sensor

## sensorId

```TypeScript
sensorId: number
```

Sensor type ID, corresponding to the enumerated values of [SensorId](arkts-sensorservice-sensor-sensorid-e.md).

**Type:** number

**Since:** 19

<!--Device-SensorStatusEvent-sensorId: int--><!--Device-SensorStatusEvent-sensorId: int-End-->

**System capability:** SystemCapability.Sensors.Sensor

## sensorIndex

```TypeScript
sensorIndex: number
```

Sensor index. Multiple instances of sensors of the same type may exist, which are distinguished by **sensorIndex**.

**Type:** number

**Since:** 19

<!--Device-SensorStatusEvent-sensorIndex: int--><!--Device-SensorStatusEvent-sensorIndex: int-End-->

**System capability:** SystemCapability.Sensors.Sensor

## timestamp

```TypeScript
timestamp: number
```

Timestamp when an event occurs. Period from the time when the device is powered on until the event occurs, in ms.

**Type:** number

**Since:** 19

<!--Device-SensorStatusEvent-timestamp: long--><!--Device-SensorStatusEvent-timestamp: long-End-->

**System capability:** SystemCapability.Sensors.Sensor
