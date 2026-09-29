# Sensor

```TypeScript
interface Sensor
```

Describes the sensor information.

**Since:** 9

<!--Device-sensor-interface Sensor--><!--Device-sensor-interface Sensor-End-->

**System capability:** SystemCapability.Sensors.Sensor

## Modules to Import

```TypeScript
import { sensor } from '@kit.SensorServiceKit';
```

## deviceId

```TypeScript
deviceId?: number
```

Device ID. The value is **-1** indicates the local device. Default value: **-1**.

**Type:** number

**Since:** 19

<!--Device-Sensor-deviceId?: int--><!--Device-Sensor-deviceId?: int-End-->

**System capability:** SystemCapability.Sensors.Sensor

## deviceName

```TypeScript
deviceName?: string
```

Device name, which identifies the source device of the sensor.

**Type:** string

**Since:** 19

<!--Device-Sensor-deviceName?: string--><!--Device-Sensor-deviceName?: string-End-->

**System capability:** SystemCapability.Sensors.Sensor

## firmwareVersion

```TypeScript
firmwareVersion:string
```

Sensor firmware version, which identifies the current version of the sensor firmware.

**Type:** string

**Since:** 9

<!--Device-Sensor-firmwareVersion:string--><!--Device-Sensor-firmwareVersion:string-End-->

**System capability:** SystemCapability.Sensors.Sensor

## hardwareVersion

```TypeScript
hardwareVersion:string
```

Sensor hardware version.

**Type:** string

**Since:** 9

<!--Device-Sensor-hardwareVersion:string--><!--Device-Sensor-hardwareVersion:string-End-->

**System capability:** SystemCapability.Sensors.Sensor

## isLocalSensor

```TypeScript
isLocalSensor?: boolean
```

Whether the sensor is a local sensor. The **true** indicates a local sensor, and **false** indicates a non-local sensor (that is, a sensor on a remote device). The default value is **true**.

**Type:** boolean

**Since:** 19

<!--Device-Sensor-isLocalSensor?: boolean--><!--Device-Sensor-isLocalSensor?: boolean-End-->

**System capability:** SystemCapability.Sensors.Sensor

## isMockSensor

```TypeScript
isMockSensor?: boolean
```

Indicates whether the sensor is a mock sensor. The value **true** indicates a mock sensor, and **false** indicates a real sensor. The default value is **false**.

**Type:** boolean

**Since:** 23

<!--Device-Sensor-isMockSensor?: boolean--><!--Device-Sensor-isMockSensor?: boolean-End-->

**System capability:** SystemCapability.Sensors.Sensor

## maxRange

```TypeScript
maxRange:number
```

Maximum measurement range of the sensor. The unit depends on the sensor type (for example, m/s² for an acceleration sensor).

**Type:** number

**Since:** 9

<!--Device-Sensor-maxRange:double--><!--Device-Sensor-maxRange:double-End-->

**System capability:** SystemCapability.Sensors.Sensor

## maxSamplePeriod

```TypeScript
maxSamplePeriod:number
```

Maximum sampling period of the sensor, in ns

**Type:** number

**Since:** 9

<!--Device-Sensor-maxSamplePeriod:long--><!--Device-Sensor-maxSamplePeriod:long-End-->

**System capability:** SystemCapability.Sensors.Sensor

## minSamplePeriod

```TypeScript
minSamplePeriod:number
```

Minimum sampling period of the sensor, in ns

**Type:** number

**Since:** 9

<!--Device-Sensor-minSamplePeriod:long--><!--Device-Sensor-minSamplePeriod:long-End-->

**System capability:** SystemCapability.Sensors.Sensor

## power

```TypeScript
power:number
```

Estimated power consumption of the sensor, in mA.

**Type:** number

**Since:** 9

<!--Device-Sensor-power:double--><!--Device-Sensor-power:double-End-->

**System capability:** SystemCapability.Sensors.Sensor

## precision

```TypeScript
precision:number
```

Precision of the sensor. The unit depends on the sensor type.

**Type:** number

**Since:** 9

<!--Device-Sensor-precision:double--><!--Device-Sensor-precision:double-End-->

**System capability:** SystemCapability.Sensors.Sensor

## sensorId

```TypeScript
sensorId:number
```

Sensor type ID, corresponding to the enumerated values of [SensorId](arkts-sensorservice-sensor-sensorid-e.md).

**Type:** number

**Since:** 9

<!--Device-Sensor-sensorId:int--><!--Device-Sensor-sensorId:int-End-->

**System capability:** SystemCapability.Sensors.Sensor

## sensorIndex

```TypeScript
sensorIndex?: number
```

Sensor index. Multiple instances of sensors of the same type may exist, which are distinguished by **sensorIndex**. The default value is **0**.

**Type:** number

**Since:** 19

<!--Device-Sensor-sensorIndex?: int--><!--Device-Sensor-sensorIndex?: int-End-->

**System capability:** SystemCapability.Sensors.Sensor

## sensorName

```TypeScript
sensorName:string
```

Sensor name, which identifies the type and model of the sensor.

**Type:** string

**Since:** 9

<!--Device-Sensor-sensorName:string--><!--Device-Sensor-sensorName:string-End-->

**System capability:** SystemCapability.Sensors.Sensor

## vendorName

```TypeScript
vendorName:string
```

Sensor vendor name, which identifies the sensor manufacturer.

**Type:** string

**Since:** 9

<!--Device-Sensor-vendorName:string--><!--Device-Sensor-vendorName:string-End-->

**System capability:** SystemCapability.Sensors.Sensor
