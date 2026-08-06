# HallResponse

霍尔传感器数据，继承于[Response]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_。

**继承/实现关系：** HallResponse extends [Response](arkts-sensorservice-sensor-response-i.md)

**起始版本：** 8

**ArkTS模式：** ArkTS-Dyn起始版本为8；ArkTS-Sta起始版本为23。

<!--Device-sensor-interface HallResponse extends Response--><!--Device-sensor-interface HallResponse extends Response-End-->

**系统能力：** SystemCapability.Sensors.Sensor

## status

```TypeScript
status: double
```

霍尔开关状态，表示设备周围是否存在磁力吸引。取值范围：0（无磁力吸引，霍尔开关断开）或大于0（有磁力吸引，霍尔开关闭合）。

**类型：** double

**起始版本：** 8

**ArkTS模式：** ArkTS-Dyn起始版本为8；ArkTS-Sta起始版本为23。

<!--Device-HallResponse-status: double--><!--Device-HallResponse-status: double-End-->

**系统能力：** SystemCapability.Sensors.Sensor

