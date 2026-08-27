# SensorId

表示当前支持订阅或取消订阅的传感器类型。

**起始版本：** 9

**系统能力：** SystemCapability.Sensors.Sensor

## ACCELEROMETER

```TypeScript
ACCELEROMETER = 1
```

加速度传感器类型，用于测量设备的加速度。从API version 11开始，该接口支持在原子化服务中使用。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Sensors.Sensor

## GYROSCOPE

```TypeScript
GYROSCOPE = 2
```

陀螺仪传感器类型，用于测量设备的旋转角速度。从API version 11开始，该接口支持在原子化服务中使用。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Sensors.Sensor

## AMBIENT_LIGHT

```TypeScript
AMBIENT_LIGHT = 5
```

环境光传感器类型，用于测量环境光照强度。

**起始版本：** 9

**系统能力：** SystemCapability.Sensors.Sensor

## MAGNETIC_FIELD

```TypeScript
MAGNETIC_FIELD = 6
```

磁场传感器类型，用于测量设备周围的环境磁场强度。

**起始版本：** 9

**系统能力：** SystemCapability.Sensors.Sensor

## BAROMETER

```TypeScript
BAROMETER = 8
```

气压计传感器类型，用于测量大气压力。

**起始版本：** 9

**系统能力：** SystemCapability.Sensors.Sensor

## HALL

```TypeScript
HALL = 10
```

霍尔传感器类型，用于检测设备周围是否存在磁力吸引。

**起始版本：** 9

**系统能力：** SystemCapability.Sensors.Sensor

## PROXIMITY

```TypeScript
PROXIMITY = 12
```

接近光传感器类型，用于检测物体与设备显示器的接近程度。

**起始版本：** 9

**系统能力：** SystemCapability.Sensors.Sensor

## HUMIDITY

```TypeScript
HUMIDITY = 13
```

湿度传感器类型，用于测量环境的相对湿度。

**起始版本：** 9

**系统能力：** SystemCapability.Sensors.Sensor

## ORIENTATION

```TypeScript
ORIENTATION = 256
```

方向传感器类型，用于测量设备的旋转方向角度。从API version 11开始，该接口在支持原子化服务中使用。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Sensors.Sensor

## GRAVITY

```TypeScript
GRAVITY = 257
```

重力传感器类型，用于测量设备的重力加速度。

**起始版本：** 9

**系统能力：** SystemCapability.Sensors.Sensor

## LINEAR_ACCELEROMETER

```TypeScript
LINEAR_ACCELEROMETER = 258
```

线性加速度传感器类型，用于测量设备排除重力后的线性加速度。

**起始版本：** 9

**系统能力：** SystemCapability.Sensors.Sensor

## ROTATION_VECTOR

```TypeScript
ROTATION_VECTOR = 259
```

旋转矢量传感器类型，用于描述设备相对于参考方向的旋转状态。

**起始版本：** 9

**系统能力：** SystemCapability.Sensors.Sensor

## AMBIENT_TEMPERATURE

```TypeScript
AMBIENT_TEMPERATURE = 260
```

环境温度传感器类型，用于测量环境的温度。

**起始版本：** 9

**系统能力：** SystemCapability.Sensors.Sensor

## MAGNETIC_FIELD_UNCALIBRATED

```TypeScript
MAGNETIC_FIELD_UNCALIBRATED = 261
```

未校准磁场传感器类型，用于测量未校准的环境磁场强度及其偏量。

**起始版本：** 9

**系统能力：** SystemCapability.Sensors.Sensor

## GYROSCOPE_UNCALIBRATED

```TypeScript
GYROSCOPE_UNCALIBRATED = 263
```

未校准陀螺仪传感器类型，用于测量未校准的设备旋转角速度及其偏量。

**起始版本：** 9

**系统能力：** SystemCapability.Sensors.Sensor

## SIGNIFICANT_MOTION

```TypeScript
SIGNIFICANT_MOTION = 264
```

有效运动传感器类型，用于检测设备是否存在大幅度运动。

**起始版本：** 9

**系统能力：** SystemCapability.Sensors.Sensor

## PEDOMETER_DETECTION

```TypeScript
PEDOMETER_DETECTION = 265
```

计步检测传感器类型，用于检测用户的计步动作。

**起始版本：** 9

**系统能力：** SystemCapability.Sensors.Sensor

## PEDOMETER

```TypeScript
PEDOMETER = 266
```

计步传感器类型，用于统计用户的行走步数。

**起始版本：** 9

**系统能力：** SystemCapability.Sensors.Sensor

## HEART_RATE

```TypeScript
HEART_RATE = 278
```

心率传感器类型，用于测量用户的心率数值。

**起始版本：** 9

**系统能力：** SystemCapability.Sensors.Sensor

## WEAR_DETECTION

```TypeScript
WEAR_DETECTION = 280
```

佩戴检测传感器类型，用于检测设备是否被佩戴。

**起始版本：** 9

**系统能力：** SystemCapability.Sensors.Sensor

## ACCELEROMETER_UNCALIBRATED

```TypeScript
ACCELEROMETER_UNCALIBRATED = 281
```

未校准加速度传感器类型，用于测量未校准的设备加速度及其偏量。

**起始版本：** 9

**系统能力：** SystemCapability.Sensors.Sensor

## FUSION_PRESSURE

```TypeScript
FUSION_PRESSURE = 283
```

融合压力传感器类型，用于测量融合压力值。仅智能表有该传感器。

**起始版本：** 22

**系统能力：** SystemCapability.Sensors.Sensor
