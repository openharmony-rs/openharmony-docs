# Sensor

指示传感器信息。

**起始版本：** 9

**系统能力：** SystemCapability.Sensors.Sensor

## 导入模块

```TypeScript
```

## deviceId

```TypeScript
deviceId?: number
```

设备ID。-1表示本地设备，其它值表示远程设备。

**类型：** number

**起始版本：** 19

**系统能力：** SystemCapability.Sensors.Sensor

## deviceName

```TypeScript
deviceName?: string
```

设备名称，标识传感器的来源设备。

**类型：** string

**起始版本：** 19

**系统能力：** SystemCapability.Sensors.Sensor

## firmwareVersion

```TypeScript
firmwareVersion:string
```

传感器固件版本号，标识传感器固件的当前版本。

**类型：** string

**起始版本：** 9

**系统能力：** SystemCapability.Sensors.Sensor

## hardwareVersion

```TypeScript
hardwareVersion:string
```

传感器硬件版本号，标识传感器硬件的当前版本。

**类型：** string

**起始版本：** 9

**系统能力：** SystemCapability.Sensors.Sensor

## isLocalSensor

```TypeScript
isLocalSensor?: boolean
```

是否为本地传感器。true表示本地传感器，false表示非本地传感器（即远程设备上的传感器）。默认值：true。

**类型：** boolean

**起始版本：** 19

**系统能力：** SystemCapability.Sensors.Sensor

## isMockSensor

```TypeScript
isMockSensor?: boolean
```

是否为模拟传感器。true表示模拟传感器，false表示真实传感器。默认值：false。

**类型：** boolean

**起始版本：** 23

**系统能力：** SystemCapability.Sensors.Sensor

## maxRange

```TypeScript
maxRange:number
```

传感器最大测量范围。单位：取决于具体传感器类型（如加速度传感器为m/s²）。

**类型：** number

**起始版本：** 9

**系统能力：** SystemCapability.Sensors.Sensor

## maxSamplePeriod

```TypeScript
maxSamplePeriod:number
```

传感器最大采样周期。单位：ns（纳秒）。

**类型：** number

**起始版本：** 9

**系统能力：** SystemCapability.Sensors.Sensor

## minSamplePeriod

```TypeScript
minSamplePeriod:number
```

传感器最小采样周期。单位：ns（纳秒）。

**类型：** number

**起始版本：** 9

**系统能力：** SystemCapability.Sensors.Sensor

## power

```TypeScript
power:number
```

传感器估计功耗。单位：mA（毫安）。

**类型：** number

**起始版本：** 9

**系统能力：** SystemCapability.Sensors.Sensor

## precision

```TypeScript
precision:number
```

传感器精度。单位：取决于具体传感器类型。

**类型：** number

**起始版本：** 9

**系统能力：** SystemCapability.Sensors.Sensor

## sensorId

```TypeScript
sensorId:number
```

传感器类型ID，对应[SensorId](arkts-sensorservice-sensor-sensorid-e.md)枚举值。

**类型：** number

**起始版本：** 9

**系统能力：** SystemCapability.Sensors.Sensor

## sensorIndex

```TypeScript
sensorIndex?: number
```

传感器索引，同一类型传感器可能有多个实例，通过sensorIndex区分。

**类型：** number

**起始版本：** 19

**系统能力：** SystemCapability.Sensors.Sensor

## sensorName

```TypeScript
sensorName:string
```

传感器名称，标识传感器的类型和型号。

**类型：** string

**起始版本：** 9

**系统能力：** SystemCapability.Sensors.Sensor

## vendorName

```TypeScript
vendorName:string
```

传感器厂商名称，标识传感器的制造商。

**类型：** string

**起始版本：** 9

**系统能力：** SystemCapability.Sensors.Sensor
