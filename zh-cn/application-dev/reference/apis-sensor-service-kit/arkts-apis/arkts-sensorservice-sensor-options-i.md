# Options

设置传感器上报频率及传感器选择参数。

**起始版本：** 8

**ArkTS模式：** ArkTS-Dyn起始版本为8；ArkTS-Sta起始版本为23。

<!--Device-sensor-interface Options--><!--Device-sensor-interface Options-End-->

**系统能力：** SystemCapability.Sensors.Sensor

## interval

```TypeScript
interval?: long | SensorFrequency
```

用于设置传感器数据上报的时间间隔。默认值：200000000ns（即200ms）。单位：ns（纳秒）。取值范围需参考各传感器的minSamplePeriod和maxSamplePeriod，可通过 [getSingleSensor]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_查询。建议根据实际业务需求设置合理 的上报频率，取值越小上报越频繁。当设置频率大于最大值时以最大值上报数据，小于最小值时以最小值上报数据。

**类型：** long \| SensorFrequency

**起始版本：** 8

**ArkTS模式：** ArkTS-Dyn起始版本为8；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-Options-interval?: long | SensorFrequency--><!--Device-Options-interval?: long | SensorFrequency-End-->

**系统能力：** SystemCapability.Sensors.Sensor

## sensorInfoParam

```TypeScript
sensorInfoParam?: SensorInfoParam
```

传感器传入设置参数，可指定deviceId、sensorIndex，用于多传感器场景下选择目标传感器。 从API version 19开始，该接口支持在原子化服务中使用。

**类型：** SensorInfoParam

**起始版本：** 19

**ArkTS模式：** ArkTS-Dyn起始版本为19；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

<!--Device-Options-sensorInfoParam?: SensorInfoParam--><!--Device-Options-sensorInfoParam?: SensorInfoParam-End-->

**系统能力：** SystemCapability.Sensors.Sensor

