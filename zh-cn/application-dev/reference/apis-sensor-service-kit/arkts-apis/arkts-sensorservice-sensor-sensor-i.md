# Sensor

指示传感器信息。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-sensor-interface Sensor--><!--Device-sensor-interface Sensor-End-->

**系统能力：** SystemCapability.Sensors.Sensor

## deviceId

```TypeScript
deviceId?: int
```

设备ID。-1表示本地设备，其它值表示远程设备。

**类型：** int

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-Sensor-deviceId?: int--><!--Device-Sensor-deviceId?: int-End-->

**系统能力：** SystemCapability.Sensors.Sensor

## deviceName

```TypeScript
deviceName?: string
```

设备名称，标识传感器的来源设备。

**类型：** string

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-Sensor-deviceName?: string--><!--Device-Sensor-deviceName?: string-End-->

**系统能力：** SystemCapability.Sensors.Sensor

## firmwareVersion

```TypeScript
firmwareVersion:string
```

传感器固件版本号，标识传感器固件的当前版本。

**类型：** string

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-Sensor-firmwareVersion:string--><!--Device-Sensor-firmwareVersion:string-End-->

**系统能力：** SystemCapability.Sensors.Sensor

## hardwareVersion

```TypeScript
hardwareVersion:string
```

传感器硬件版本号，标识传感器硬件的当前版本。

**类型：** string

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-Sensor-hardwareVersion:string--><!--Device-Sensor-hardwareVersion:string-End-->

**系统能力：** SystemCapability.Sensors.Sensor

## isLocalSensor

```TypeScript
isLocalSensor?: boolean
```

是否为本地传感器。true表示本地传感器，false表示非本地传感器（即远程设备上的传感器）。默认值：true。

**类型：** boolean

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-Sensor-isLocalSensor?: boolean--><!--Device-Sensor-isLocalSensor?: boolean-End-->

**系统能力：** SystemCapability.Sensors.Sensor

## isMockSensor

```TypeScript
isMockSensor?: boolean
```

是否为模拟传感器。true表示模拟传感器，false表示真实传感器。默认值：false。

**类型：** boolean

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-Sensor-isMockSensor?: boolean--><!--Device-Sensor-isMockSensor?: boolean-End-->

**系统能力：** SystemCapability.Sensors.Sensor

## maxRange

```TypeScript
maxRange:double
```

传感器最大测量范围。单位：取决于具体传感器类型（如加速度传感器为m/s²）。

**类型：** double

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-Sensor-maxRange:double--><!--Device-Sensor-maxRange:double-End-->

**系统能力：** SystemCapability.Sensors.Sensor

## maxSamplePeriod

```TypeScript
maxSamplePeriod:long
```

传感器最大采样周期。单位：ns（纳秒）。

**类型：** long

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-Sensor-maxSamplePeriod:long--><!--Device-Sensor-maxSamplePeriod:long-End-->

**系统能力：** SystemCapability.Sensors.Sensor

## minSamplePeriod

```TypeScript
minSamplePeriod:long
```

传感器最小采样周期。单位：ns（纳秒）。

**类型：** long

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-Sensor-minSamplePeriod:long--><!--Device-Sensor-minSamplePeriod:long-End-->

**系统能力：** SystemCapability.Sensors.Sensor

## power

```TypeScript
power:double
```

传感器估计功耗。单位：mA（毫安）。

**类型：** double

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-Sensor-power:double--><!--Device-Sensor-power:double-End-->

**系统能力：** SystemCapability.Sensors.Sensor

## precision

```TypeScript
precision:double
```

传感器精度。单位：取决于具体传感器类型。

**类型：** double

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-Sensor-precision:double--><!--Device-Sensor-precision:double-End-->

**系统能力：** SystemCapability.Sensors.Sensor

## sensorId

```TypeScript
sensorId:int
```

传感器类型ID，对应[SensorId](arkts-sensorservice-sensor-sensorid-e.md#SensorId)枚举值。

**类型：** int

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-Sensor-sensorId:int--><!--Device-Sensor-sensorId:int-End-->

**系统能力：** SystemCapability.Sensors.Sensor

## sensorIndex

```TypeScript
sensorIndex?: int
```

传感器索引，同一类型传感器可能有多个实例，通过sensorIndex区分。

**类型：** int

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-Sensor-sensorIndex?: int--><!--Device-Sensor-sensorIndex?: int-End-->

**系统能力：** SystemCapability.Sensors.Sensor

## sensorName

```TypeScript
sensorName:string
```

传感器名称，标识传感器的类型和型号。

**类型：** string

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-Sensor-sensorName:string--><!--Device-Sensor-sensorName:string-End-->

**系统能力：** SystemCapability.Sensors.Sensor

## vendorName

```TypeScript
vendorName:string
```

传感器厂商名称，标识传感器的制造商。

**类型：** string

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-Sensor-vendorName:string--><!--Device-Sensor-vendorName:string-End-->

**系统能力：** SystemCapability.Sensors.Sensor

