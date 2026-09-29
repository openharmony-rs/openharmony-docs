# SensorId

```TypeScript
enum SensorId
```

Enumerates the sensor types.

**Since:** 9

<!--Device-sensor-enum SensorId--><!--Device-sensor-enum SensorId-End-->

**System capability:** SystemCapability.Sensors.Sensor

## COLOR

```TypeScript
COLOR = 14
```

Color sensor. Subscribes to or unsubscribes from the color sensor data. The reported data is a [ColorResponse](arkts-sensorservice-sensor-colorresponse-i-sys.md) object, which contains the light intensity and color temperature information.

**Since:** 10

<!--Device-SensorId-COLOR = 14--><!--Device-SensorId-COLOR = 14-End-->

**System capability:** SystemCapability.Sensors.Sensor

**System API:** This is a system API.

## SAR

```TypeScript
SAR = 15
```

Sodium Adsorption Ratio (SAR) sensor. Subscribes to or unsubscribes from the SAR sensor data. The reported data is a [SarResponse](arkts-sensorservice-sensor-sarresponse-i-sys.md) object, which contains the SAR information.

**Since:** 10

<!--Device-SensorId-SAR = 15--><!--Device-SensorId-SAR = 15-End-->

**System capability:** SystemCapability.Sensors.Sensor

**System API:** This is a system API.
