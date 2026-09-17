# Sensor

Describes the sensor information.

**Since:** 9

**System capability:** SystemCapability.Sensors.Sensor

## Modules to Import

```TypeScript
import { sensor } from '@kit.SensorServiceKit';
```

## deviceId

```TypeScript
deviceId?: number
```

Device ID.

**Type:** number

**Since:** 19

**System capability:** SystemCapability.Sensors.Sensor

## deviceName

```TypeScript
deviceName?: string
```

Device name.

**Type:** string

**Since:** 19

**System capability:** SystemCapability.Sensors.Sensor

## firmwareVersion

```TypeScript
firmwareVersion:string
```

Firmware version of the sensor.

**Type:** string

**Since:** 9

**System capability:** SystemCapability.Sensors.Sensor

## hardwareVersion

```TypeScript
hardwareVersion:string
```

Hardware version of the sensor.

**Type:** string

**Since:** 9

**System capability:** SystemCapability.Sensors.Sensor

## isLocalSensor

```TypeScript
isLocalSensor?: boolean
```

Whether the sensor is a local sensor. The value **true** indicates a local sensor, and the value **false** indicates the opposite.

**Type:** boolean

**Since:** 19

**System capability:** SystemCapability.Sensors.Sensor

## isMockSensor

```TypeScript
isMockSensor?: boolean
```

Whether the sensor is a mock sensor. The value **true** indicates a mock sensor, and the value **false** indicates the opposite.

**Type:** boolean

**Since:** 23

**System capability:** SystemCapability.Sensors.Sensor

## maxRange

```TypeScript
maxRange:number
```

Maximum measurement range of the sensor.

**Type:** number

**Since:** 9

**System capability:** SystemCapability.Sensors.Sensor

## maxSamplePeriod

```TypeScript
maxSamplePeriod:number
```

Maximum sampling period.

**Type:** number

**Since:** 9

**System capability:** SystemCapability.Sensors.Sensor

## minSamplePeriod

```TypeScript
minSamplePeriod:number
```

Minimum sampling period.

**Type:** number

**Since:** 9

**System capability:** SystemCapability.Sensors.Sensor

## power

```TypeScript
power:number
```

Estimated sensor power, in mA.

**Type:** number

**Since:** 9

**System capability:** SystemCapability.Sensors.Sensor

## precision

```TypeScript
precision:number
```

Precision of the sensor.

**Type:** number

**Since:** 9

**System capability:** SystemCapability.Sensors.Sensor

## sensorId

```TypeScript
sensorId:number
```

Sensor type ID.

**Type:** number

**Since:** 9

**System capability:** SystemCapability.Sensors.Sensor

## sensorIndex

```TypeScript
sensorIndex?: number
```

Sensor index.

**Type:** number

**Since:** 19

**System capability:** SystemCapability.Sensors.Sensor

## sensorName

```TypeScript
sensorName:string
```

Sensor name.

**Type:** string

**Since:** 9

**System capability:** SystemCapability.Sensors.Sensor

## vendorName

```TypeScript
vendorName:string
```

Vendor of the sensor.

**Type:** string

**Since:** 9

**System capability:** SystemCapability.Sensors.Sensor
