# LightResponse

```TypeScript
interface LightResponse extends Response
```

Describes the ambient light sensor data. It extends from [Response](arkts-sensorservice-sensor-response-i.md).

**Inheritance/Implementation:** LightResponse extends [Response](arkts-sensorservice-sensor-response-i.md)

**Since:** 8

<!--Device-sensor-interface LightResponse extends Response--><!--Device-sensor-interface LightResponse extends Response-End-->

**System capability:** SystemCapability.Sensors.Sensor

## Modules to Import

```TypeScript
import { sensor } from '@kit.SensorServiceKit';
```

## colorTemperature

```TypeScript
colorTemperature?: number
```

Color temperature, in K (Kelvin). This parameter is optional. If this parameter is not supported, a fixed value (customized by the sensor) is returned. If this parameter is supported, a normal value is returned.

**Type:** number

**Since:** 12

<!--Device-LightResponse-colorTemperature?: double--><!--Device-LightResponse-colorTemperature?: double-End-->

**System capability:** SystemCapability.Sensors.Sensor

## infraredLuminance

```TypeScript
infraredLuminance?: number
```

Infrared luminance. in cd/m². This parameter is optional. If this parameter is not supported, a fixed value (customized by the sensor) is returned. If this parameter is supported, a normal value is returned.

**Type:** number

**Since:** 12

<!--Device-LightResponse-infraredLuminance?: double--><!--Device-LightResponse-infraredLuminance?: double-End-->

**System capability:** SystemCapability.Sensors.Sensor

## intensity

```TypeScript
intensity: number
```

Ambient light intensity, in lux.

**Type:** number

**Since:** 8

<!--Device-LightResponse-intensity: double--><!--Device-LightResponse-intensity: double-End-->

**System capability:** SystemCapability.Sensors.Sensor
