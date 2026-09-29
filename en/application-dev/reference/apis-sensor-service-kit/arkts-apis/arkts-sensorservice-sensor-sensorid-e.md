# SensorId

```TypeScript
enum SensorId
```

Enumerates the sensor types.

**Since:** 9

<!--Device-sensor-enum SensorId--><!--Device-sensor-enum SensorId-End-->

**System capability:** SystemCapability.Sensors.Sensor

## ACCELEROMETER

```TypeScript
ACCELEROMETER = 1
```

Accelerometer sensor, which is used to measure the acceleration of the device. <br>**Atomic service API**: This API can be used in atomic services since API version 11.

**Since:** 9

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 11.

<!--Device-SensorId-ACCELEROMETER = 1--><!--Device-SensorId-ACCELEROMETER = 1-End-->

**System capability:** SystemCapability.Sensors.Sensor

## GYROSCOPE

```TypeScript
GYROSCOPE = 2
```

Gyroscope sensor, which is used to measure the angular velocity of the device. <br>**Atomic service API**: This API can be used in atomic services since API version 11.

**Since:** 9

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 11.

<!--Device-SensorId-GYROSCOPE = 2--><!--Device-SensorId-GYROSCOPE = 2-End-->

**System capability:** SystemCapability.Sensors.Sensor

## AMBIENT_LIGHT

```TypeScript
AMBIENT_LIGHT = 5
```

Ambient light sensor, which is used to measure the ambient light intensity.

**Since:** 9

<!--Device-SensorId-AMBIENT_LIGHT = 5--><!--Device-SensorId-AMBIENT_LIGHT = 5-End-->

**System capability:** SystemCapability.Sensors.Sensor

## MAGNETIC_FIELD

```TypeScript
MAGNETIC_FIELD = 6
```

Magnetic field sensor, which is used to measure the ambient magnetic field strength around the device.

**Since:** 9

<!--Device-SensorId-MAGNETIC_FIELD = 6--><!--Device-SensorId-MAGNETIC_FIELD = 6-End-->

**System capability:** SystemCapability.Sensors.Sensor

## BAROMETER

```TypeScript
BAROMETER = 8
```

Barometric pressure sensor, which is used to measure atmospheric pressure.

**Since:** 9

<!--Device-SensorId-BAROMETER = 8--><!--Device-SensorId-BAROMETER = 8-End-->

**System capability:** SystemCapability.Sensors.Sensor

## HALL

```TypeScript
HALL = 10
```

Hall effect sensor, which is used to detect whether there is a magnetic force around the device.

**Since:** 9

<!--Device-SensorId-HALL = 10--><!--Device-SensorId-HALL = 10-End-->

**System capability:** SystemCapability.Sensors.Sensor

## PROXIMITY

```TypeScript
PROXIMITY = 12
```

Proximity sensor, which is used to detect the proximity between an object and the device display.

**Since:** 9

<!--Device-SensorId-PROXIMITY = 12--><!--Device-SensorId-PROXIMITY = 12-End-->

**System capability:** SystemCapability.Sensors.Sensor

## HUMIDITY

```TypeScript
HUMIDITY = 13
```

Humidity sensor, which is used to measure the relative humidity of the environment.

**Since:** 9

<!--Device-SensorId-HUMIDITY = 13--><!--Device-SensorId-HUMIDITY = 13-End-->

**System capability:** SystemCapability.Sensors.Sensor

## ORIENTATION

```TypeScript
ORIENTATION = 256
```

Orientation sensor, which is used to measure the rotation angle of the device. <br>**Atomic service API**: This API can be used in atomic services since API version 11.

**Since:** 9

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 11.

<!--Device-SensorId-ORIENTATION = 256--><!--Device-SensorId-ORIENTATION = 256-End-->

**System capability:** SystemCapability.Sensors.Sensor

## GRAVITY

```TypeScript
GRAVITY = 257
```

Gravity sensor, which is used to measure the gravity acceleration of the device.

**Since:** 9

<!--Device-SensorId-GRAVITY = 257--><!--Device-SensorId-GRAVITY = 257-End-->

**System capability:** SystemCapability.Sensors.Sensor

## LINEAR_ACCELEROMETER

```TypeScript
LINEAR_ACCELEROMETER = 258
```

Linear acceleration sensor, which is used to measure the linear acceleration of the device excluding the effect of gravity.

**Since:** 9

<!--Device-SensorId-LINEAR_ACCELEROMETER = 258--><!--Device-SensorId-LINEAR_ACCELEROMETER = 258-End-->

**System capability:** SystemCapability.Sensors.Sensor

## ROTATION_VECTOR

```TypeScript
ROTATION_VECTOR = 259
```

Rotation vector sensor type, which is used to describe the rotation status of the device relative to a reference direction.

**Since:** 9

<!--Device-SensorId-ROTATION_VECTOR = 259--><!--Device-SensorId-ROTATION_VECTOR = 259-End-->

**System capability:** SystemCapability.Sensors.Sensor

## AMBIENT_TEMPERATURE

```TypeScript
AMBIENT_TEMPERATURE = 260
```

Ambient temperature sensor, which is used to measure the ambient temperature.

**Since:** 9

<!--Device-SensorId-AMBIENT_TEMPERATURE = 260--><!--Device-SensorId-AMBIENT_TEMPERATURE = 260-End-->

**System capability:** SystemCapability.Sensors.Sensor

## MAGNETIC_FIELD_UNCALIBRATED

```TypeScript
MAGNETIC_FIELD_UNCALIBRATED = 261
```

Uncalibrated magnetic field sensor, which is used to measure the uncalibrated ambient magnetic field strength and its bias.

**Since:** 9

<!--Device-SensorId-MAGNETIC_FIELD_UNCALIBRATED = 261--><!--Device-SensorId-MAGNETIC_FIELD_UNCALIBRATED = 261-End-->

**System capability:** SystemCapability.Sensors.Sensor

## GYROSCOPE_UNCALIBRATED

```TypeScript
GYROSCOPE_UNCALIBRATED = 263
```

Uncalibrated gyroscope sensor, which is used to measure the uncalibrated angular velocity of the device and its bias.

**Since:** 9

<!--Device-SensorId-GYROSCOPE_UNCALIBRATED = 263--><!--Device-SensorId-GYROSCOPE_UNCALIBRATED = 263-End-->

**System capability:** SystemCapability.Sensors.Sensor

## SIGNIFICANT_MOTION

```TypeScript
SIGNIFICANT_MOTION = 264
```

Significant motion sensor, which is used to detect whether the device is moving significantly.

**Since:** 9

<!--Device-SensorId-SIGNIFICANT_MOTION = 264--><!--Device-SensorId-SIGNIFICANT_MOTION = 264-End-->

**System capability:** SystemCapability.Sensors.Sensor

## PEDOMETER_DETECTION

```TypeScript
PEDOMETER_DETECTION = 265
```

Pedometer detection sensor, which is used to detect the step counting action of a user.

**Since:** 9

<!--Device-SensorId-PEDOMETER_DETECTION = 265--><!--Device-SensorId-PEDOMETER_DETECTION = 265-End-->

**System capability:** SystemCapability.Sensors.Sensor

## PEDOMETER

```TypeScript
PEDOMETER = 266
```

Step counter sensor, which is used to count the number of steps a user has taken.

**Since:** 9

<!--Device-SensorId-PEDOMETER = 266--><!--Device-SensorId-PEDOMETER = 266-End-->

**System capability:** SystemCapability.Sensors.Sensor

## HEART_RATE

```TypeScript
HEART_RATE = 278
```

Heart rate sensor, which is used to measure the heart rate of a user.

**Since:** 9

<!--Device-SensorId-HEART_RATE = 278--><!--Device-SensorId-HEART_RATE = 278-End-->

**System capability:** SystemCapability.Sensors.Sensor

## WEAR_DETECTION

```TypeScript
WEAR_DETECTION = 280
```

Wear detection sensor, which is used to detect whether the device is being worn.

**Since:** 9

<!--Device-SensorId-WEAR_DETECTION = 280--><!--Device-SensorId-WEAR_DETECTION = 280-End-->

**System capability:** SystemCapability.Sensors.Sensor

## ACCELEROMETER_UNCALIBRATED

```TypeScript
ACCELEROMETER_UNCALIBRATED = 281
```

Uncalibrated acceleration sensor, which is used to measure the uncalibrated acceleration of the device and its bias.

**Since:** 9

<!--Device-SensorId-ACCELEROMETER_UNCALIBRATED = 281--><!--Device-SensorId-ACCELEROMETER_UNCALIBRATED = 281-End-->

**System capability:** SystemCapability.Sensors.Sensor

## FUSION_PRESSURE

```TypeScript
FUSION_PRESSURE = 283
```

Fused pressure sensor, which is used to measure the fusion pressure value. This sensor is available only on smart watches.

**Since:** 22

<!--Device-SensorId-FUSION_PRESSURE = 283--><!--Device-SensorId-FUSION_PRESSURE = 283-End-->

**System capability:** SystemCapability.Sensors.Sensor
