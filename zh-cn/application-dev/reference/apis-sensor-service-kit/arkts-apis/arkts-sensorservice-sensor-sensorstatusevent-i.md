# SensorStatusEvent

设备状态变化事件数据，用于描述传感器上下线事件的信息。

**起始版本：** 19

**系统能力：** SystemCapability.Sensors.Sensor

## 导入模块

```TypeScript
```

## deviceId

```TypeScript
deviceId: number
```

设备ID。-1表示本地设备，其它值表示远程设备。

**类型：** number

**起始版本：** 19

**系统能力：** SystemCapability.Sensors.Sensor

## deviceName

```TypeScript
deviceName: string
```

设备名称，标识传感器的来源设备。

**类型：** string

**起始版本：** 19

**系统能力：** SystemCapability.Sensors.Sensor

## isSensorOnline

```TypeScript
isSensorOnline: boolean
```

传感器是否上线。true表示传感器上线，false表示传感器下线。

**类型：** boolean

**起始版本：** 19

**系统能力：** SystemCapability.Sensors.Sensor

## sensorId

```TypeScript
sensorId: number
```

传感器类型ID，对应[SensorId](arkts-sensorservice-sensor-sensorid-e.md)枚举值。

**类型：** number

**起始版本：** 19

**系统能力：** SystemCapability.Sensors.Sensor

## sensorIndex

```TypeScript
sensorIndex: number
```

传感器索引，同一类型传感器可能有多个实例，通过sensorIndex区分。

**类型：** number

**起始版本：** 19

**系统能力：** SystemCapability.Sensors.Sensor

## timestamp

```TypeScript
timestamp: number
```

事件发生的时间戳。从设备开机开始计时到事件发生的时间。单位：ms（毫秒）。

**类型：** number

**起始版本：** 19

**系统能力：** SystemCapability.Sensors.Sensor
