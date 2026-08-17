# ProximityResponse

距离感应数据改变后的回调函数的响应对象，包含可见物体相对于设备显示屏的接近或远离状态数据。 **设备行为差异**：该接口在Wearable、Lite Wearable中可正常调用，在其他设备类型中无效果。

**起始版本：** 3

**ArkTS模式：** 起始版本为3。

**废弃版本：** 8

**替代接口：** [ProximityResponse](arkts-sensorservice-sensor-proximityresponse-i.md#proximityresponse)

<!--Device-unnamed-export interface ProximityResponse--><!--Device-unnamed-export interface ProximityResponse-End-->

**系统能力：** SystemCapability.Sensors.Sensor.Lite

## distance

```TypeScript
distance: number
```

可见物体相对于设备显示屏的接近或远离状态。取值说明：0表示物体接近屏幕（近状态），大于0表示物体远离屏幕（远状态）。具体远状态数值由硬件传感器决定。

**类型：** number

**起始版本：** 3

**ArkTS模式：** 起始版本为3。

**废弃版本：** 8

**替代接口：** [distance](arkts-sensorservice-sensor-proximityresponse-i.md#distance)

**模型约束：** 此接口仅可在FA模型下使用。

<!--Device-ProximityResponse-distance: number--><!--Device-ProximityResponse-distance: number-End-->

**系统能力：** SystemCapability.Sensors.Sensor.Lite

