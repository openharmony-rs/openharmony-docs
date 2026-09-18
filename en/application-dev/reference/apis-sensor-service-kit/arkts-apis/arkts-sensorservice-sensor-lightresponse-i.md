# LightResponse

Describes the ambient light sensor data. It extends from [Response](arkts-sensorservice-sensor-response-i.md).

**Inheritance/Implementation:** LightResponse extends [Response](arkts-sensorservice-sensor-response-i.md)

**Since:** 8

**System capability:** SystemCapability.Sensors.Sensor

## Modules to Import

```TypeScript
import { sensor } from '@kit.SensorServiceKit';
```

## colorTemperature

```TypeScript
colorTemperature?: number
```

Color temperature, in Kelvin. This parameter is optional. If this parameter is not supported, a fixed value (customized by the sensor) is returned. If this parameter is supported, a normal value is returned.

**Type:** number

**Since:** 12

**System capability:** SystemCapability.Sensors.Sensor

## infraredLuminance

```TypeScript
infraredLuminance?: number
```

Infrared luminance, in cd/m?. This parameter is optional. If this parameter is not supported, a fixed value (customized by the sensor) is returned. If this parameter is supported, a normal value is returned.

**Type:** number

**Since:** 12

**System capability:** SystemCapability.Sensors.Sensor

## intensity

```TypeScript
intensity: number
```

Illumination, in lux.

**Type:** number

**Since:** 8

**System capability:** SystemCapability.Sensors.Sensor
