# SensorInfoParam

传感器传入设置参数，多传感器情况下通过deviceId、sensorIndex控制指定传感器。

**起始版本：** 19

**系统能力：** SystemCapability.Sensors.Sensor

## 导入模块

```TypeScript
```

## deviceId

```TypeScript
deviceId?: number
```

指定目标传感器所属设备的ID。默认值：-1（表示本地设备）。可通过[sensor.on('sensorStatusChange')](arkts-sensorservice-sensor-on-f.md#onsensorstatuschange)或 [getSensorList](arkts-sensorservice-sensor-getsensorlist-f.md)获取远程设备ID。

**类型：** number

**起始版本：** 19

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Sensors.Sensor

## sensorIndex

```TypeScript
sensorIndex?: number
```

指定目标传感器的索引，同一类型传感器可能有多个实例。默认值：0（表示设备上的默认传感器）。其它传感器索引需通过 [getSensorList](arkts-sensorservice-sensor-getsensorlist-f.md)或 [sensor.on('sensorStatusChange')](arkts-sensorservice-sensor-on-f.md#onsensorstatuschange)获取。

**类型：** number

**起始版本：** 19

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Sensors.Sensor
