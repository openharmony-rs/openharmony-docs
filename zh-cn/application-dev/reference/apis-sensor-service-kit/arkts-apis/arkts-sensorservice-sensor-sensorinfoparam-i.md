# SensorInfoParam

传感器传入设置参数，多传感器情况下通过deviceId、sensorIndex控制指定传感器。

**起始版本：** 19

**ArkTS模式：** ArkTS-Dyn起始版本为19；ArkTS-Sta起始版本为23。

<!--Device-sensor-interface SensorInfoParam--><!--Device-sensor-interface SensorInfoParam-End-->

**系统能力：** SystemCapability.Sensors.Sensor

## deviceId

```TypeScript
deviceId?: int
```

指定目标传感器所属设备的ID。默认值：-1（表示本地设备）。可通过[sensor.on('sensorStatusChange')]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_或 [getSensorList]\_\_\_JSDOC\_LINK\_DESC\_USD\_1\_\_\_获取远程设备ID。

**类型：** int

**起始版本：** 19

**ArkTS模式：** ArkTS-Dyn起始版本为19；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

<!--Device-SensorInfoParam-deviceId?: int--><!--Device-SensorInfoParam-deviceId?: int-End-->

**系统能力：** SystemCapability.Sensors.Sensor

## sensorIndex

```TypeScript
sensorIndex?: int
```

指定目标传感器的索引，同一类型传感器可能有多个实例。默认值：0（表示设备上的默认传感器）。其它传感器索引需通过 [getSensorList]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_或 [sensor.on('sensorStatusChange')]\_\_\_JSDOC\_LINK\_DESC\_USD\_1\_\_\_获取。

**类型：** int

**起始版本：** 19

**ArkTS模式：** ArkTS-Dyn起始版本为19；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

<!--Device-SensorInfoParam-sensorIndex?: int--><!--Device-SensorInfoParam-sensorIndex?: int-End-->

**系统能力：** SystemCapability.Sensors.Sensor

