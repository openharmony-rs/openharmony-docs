# CompassResponse

罗盘数据改变后的回调函数的响应对象，包含设备面对的方向度数。

**起始版本：** 3

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为3。

**废弃版本：** 8

**替代接口：** [OrientationResponse](arkts-sensorservice-sensor-orientationresponse-i.md#OrientationResponse)

<!--Device-unnamed-export interface CompassResponse--><!--Device-unnamed-export interface CompassResponse-End-->

**系统能力：** SystemCapability.Sensors.Sensor.Lite

## direction

```TypeScript
direction: number
```

设备面对的方向度数。单位：度（°）。取值范围：[0, 360)，0表示朝北。取值为实际上报物理量。

**类型：** number

**起始版本：** 3

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为3。

**废弃版本：** 8

**替代接口：** [alpha](arkts-sensorservice-sensor-orientationresponse-i.md#alpha)

**模型约束：** 此接口仅可在FA模型下使用。

<!--Device-CompassResponse-direction: number--><!--Device-CompassResponse-direction: number-End-->

**系统能力：** SystemCapability.Sensors.Sensor.Lite

