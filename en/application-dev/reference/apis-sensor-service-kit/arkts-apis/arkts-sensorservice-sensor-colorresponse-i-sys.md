# ColorResponse (System API)

```TypeScript
interface ColorResponse extends Response
```

Describes the color sensor data. It extends from [Response](arkts-sensorservice-sensor-response-i.md). This method is used to represent the response data reported by the color sensor, including the light intensity and color temperature information.

**Inheritance/Implementation:** ColorResponse extends [Response](arkts-sensorservice-sensor-response-i.md)

**Since:** 10

<!--Device-sensor-interface ColorResponse extends Response--><!--Device-sensor-interface ColorResponse extends Response-End-->

**System capability:** SystemCapability.Sensors.Sensor

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { sensor } from '@kit.SensorServiceKit';
```

## colorTemperature

```TypeScript
colorTemperature: number
```

Color temperature, in K (Kelvin). Value range: The value is the actually reported physical quantity, which is determined by the hardware sensor. In general, the color temperature of warm white light is 2700 to 3000 K, of neutral white light is 4000–5000 K, and of cool white light is above 6500 K.

**Type:** number

**Since:** 10

<!--Device-ColorResponse-colorTemperature: double--><!--Device-ColorResponse-colorTemperature: double-End-->

**System capability:** SystemCapability.Sensors.Sensor

**System API:** This is a system API.

## lightIntensity

```TypeScript
lightIntensity: number
```

Light intensity, in lux. Value range: The value is the actually reported physical quantity, which is determined by the hardware sensor. The typical indoor ambient light intensity ranges from 300 lux to 500 lux, and the outdoor sunlight intensity can reach over 10,000 lux.

**Type:** number

**Since:** 10

<!--Device-ColorResponse-lightIntensity: double--><!--Device-ColorResponse-lightIntensity: double-End-->

**System capability:** SystemCapability.Sensors.Sensor

**System API:** This is a system API.
