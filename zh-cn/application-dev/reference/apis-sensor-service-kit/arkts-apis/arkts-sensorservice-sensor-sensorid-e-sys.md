# SensorId

表示当前支持订阅或取消订阅的传感器类型。

**起始版本：** 9

**ArkTS模式：** ArkTS-Dyn起始版本为9；ArkTS-Sta起始版本为23。

<!--Device-sensor-enum SensorId--><!--Device-sensor-enum SensorId-End-->

**系统能力：** SystemCapability.Sensors.Sensor

## COLOR

```TypeScript
COLOR = 14
```

颜色传感器。用于订阅/取消订阅颜色传感器数据，上报数据为[ColorResponse]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_对象，包含光照强度和色温信息。

**起始版本：** 10

**ArkTS模式：** ArkTS-Dyn起始版本为10；ArkTS-Sta起始版本为23。

<!--Device-SensorId-COLOR = 14--><!--Device-SensorId-COLOR = 14-End-->

**系统能力：** SystemCapability.Sensors.Sensor

**系统接口：** 此接口为系统接口。

## SAR

```TypeScript
SAR = 15
```

吸收比率传感器。用于订阅/取消订阅吸收比率传感器数据，上报数据为[SarResponse]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_对象，包含电磁波吸收率信息。

**起始版本：** 10

**ArkTS模式：** ArkTS-Dyn起始版本为10；ArkTS-Sta起始版本为23。

<!--Device-SensorId-SAR = 15--><!--Device-SensorId-SAR = 15-End-->

**系统能力：** SystemCapability.Sensors.Sensor

**系统接口：** 此接口为系统接口。

