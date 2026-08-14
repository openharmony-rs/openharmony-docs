# HallResponse

霍尔传感器数据，继承于[Response](arkts-sensorservice-sensor-response-i.md#Response)。

**继承/实现关系：** HallResponse extends [Response](arkts-sensorservice-sensor-response-i.md#Response)

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-sensor-interface HallResponse--><!--Device-sensor-interface HallResponse-End-->

**系统能力：** SystemCapability.Sensors.Sensor

## status

```TypeScript
status: double
```

霍尔开关状态，表示设备周围是否存在磁力吸引。取值范围：0（无磁力吸引，霍尔开关断开）或大于0（有磁力吸引，霍尔开关闭合）。

**类型：** double

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-HallResponse-status: double--><!--Device-HallResponse-status: double-End-->

**系统能力：** SystemCapability.Sensors.Sensor

