# SarResponse（系统接口）

吸收比率传感器数据，继承于[Response](arkts-sensorservice-sensor-response-i.md#Response)。用于表示吸收比率传感器上报的响应数据，包含电磁波吸收率信息。

**继承/实现关系：** SarResponse extends [Response](arkts-sensorservice-sensor-response-i.md#Response)

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-sensor-interface SarResponse--><!--Device-sensor-interface SarResponse-End-->

**系统能力：** SystemCapability.Sensors.Sensor

**系统接口：** 此接口为系统接口。

## absorptionRatio

```TypeScript
absorptionRatio: double
```

表示具体的吸收率。单位：W/kg。取值范围：取值为实际上报物理量，由硬件传感器决定。

**类型：** double

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-SarResponse-absorptionRatio: double--><!--Device-SarResponse-absorptionRatio: double-End-->

**系统能力：** SystemCapability.Sensors.Sensor

**系统接口：** 此接口为系统接口。

