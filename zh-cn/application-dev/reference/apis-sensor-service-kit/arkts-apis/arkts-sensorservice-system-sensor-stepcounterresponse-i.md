# StepCounterResponse

计步传感器数据改变后的回调函数的响应对象，包含计步传感器重启后累计记录的步数数据。

**起始版本：** 3

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为3。

**废弃版本：** 8

**替代接口：** [PedometerResponse](arkts-sensorservice-sensor-pedometerresponse-i.md#PedometerResponse)

**需要权限：** ohos.permission.ACTIVITY_MOTION

<!--Device-unnamed-export interface StepCounterResponse--><!--Device-unnamed-export interface StepCounterResponse-End-->

**系统能力：** SystemCapability.Sensors.Sensor.Lite

## steps

```TypeScript
steps: number
```

计步传感器重启后累计记录的步数。取值范围：大于等于0的整数，取值为实际上报物理量。传感器重启后步数从0重新开始累计。

**类型：** number

**起始版本：** 3

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为3。

**废弃版本：** 8

**替代接口：** [steps](arkts-sensorservice-sensor-pedometerresponse-i.md#steps)

**需要权限：** ohos.permission.ACTIVITY_MOTION

**模型约束：** 此接口仅可在FA模型下使用。

<!--Device-StepCounterResponse-steps: number--><!--Device-StepCounterResponse-steps: number-End-->

**系统能力：** SystemCapability.Sensors.Sensor.Lite

