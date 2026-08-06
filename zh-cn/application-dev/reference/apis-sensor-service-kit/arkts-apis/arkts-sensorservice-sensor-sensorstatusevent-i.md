# SensorStatusEvent

设备状态变化事件数据，用于描述传感器上下线事件的信息。

**起始版本：** 19

**ArkTS模式：** ArkTS-Dyn起始版本为19；ArkTS-Sta起始版本为23。

<!--Device-sensor-interface SensorStatusEvent--><!--Device-sensor-interface SensorStatusEvent-End-->

**系统能力：** SystemCapability.Sensors.Sensor

## deviceId

```TypeScript
deviceId: int
```

设备ID。-1表示本地设备，其它值表示远程设备。

**类型：** int

**起始版本：** 19

**ArkTS模式：** ArkTS-Dyn起始版本为19；ArkTS-Sta起始版本为23。

<!--Device-SensorStatusEvent-deviceId: int--><!--Device-SensorStatusEvent-deviceId: int-End-->

**系统能力：** SystemCapability.Sensors.Sensor

## deviceName

```TypeScript
deviceName: string
```

设备名称，标识传感器的来源设备。

**类型：** string

**起始版本：** 19

**ArkTS模式：** ArkTS-Dyn起始版本为19；ArkTS-Sta起始版本为23。

<!--Device-SensorStatusEvent-deviceName: string--><!--Device-SensorStatusEvent-deviceName: string-End-->

**系统能力：** SystemCapability.Sensors.Sensor

## isSensorOnline

```TypeScript
isSensorOnline: boolean
```

传感器是否上线。true表示传感器上线，false表示传感器下线。

**类型：** boolean

**起始版本：** 19

**ArkTS模式：** ArkTS-Dyn起始版本为19；ArkTS-Sta起始版本为23。

<!--Device-SensorStatusEvent-isSensorOnline: boolean--><!--Device-SensorStatusEvent-isSensorOnline: boolean-End-->

**系统能力：** SystemCapability.Sensors.Sensor

## sensorId

```TypeScript
sensorId: int
```

传感器类型ID，对应[SensorId]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_枚举值。

**类型：** int

**起始版本：** 19

**ArkTS模式：** ArkTS-Dyn起始版本为19；ArkTS-Sta起始版本为23。

<!--Device-SensorStatusEvent-sensorId: int--><!--Device-SensorStatusEvent-sensorId: int-End-->

**系统能力：** SystemCapability.Sensors.Sensor

## sensorIndex

```TypeScript
sensorIndex: int
```

传感器索引，同一类型传感器可能有多个实例，通过sensorIndex区分。

**类型：** int

**起始版本：** 19

**ArkTS模式：** ArkTS-Dyn起始版本为19；ArkTS-Sta起始版本为23。

<!--Device-SensorStatusEvent-sensorIndex: int--><!--Device-SensorStatusEvent-sensorIndex: int-End-->

**系统能力：** SystemCapability.Sensors.Sensor

## timestamp

```TypeScript
timestamp: long
```

事件发生的时间戳。从设备开机开始计时到事件发生的时间。单位：ms（毫秒）。

**类型：** long

**起始版本：** 19

**ArkTS模式：** ArkTS-Dyn起始版本为19；ArkTS-Sta起始版本为23。

<!--Device-SensorStatusEvent-timestamp: long--><!--Device-SensorStatusEvent-timestamp: long-End-->

**系统能力：** SystemCapability.Sensors.Sensor

