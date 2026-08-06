# OrientationResponse

方向传感器数据，继承于[Response]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_。

**继承/实现关系：** OrientationResponse extends [Response](arkts-sensorservice-sensor-response-i.md)

**起始版本：** 8

**ArkTS模式：** ArkTS-Dyn起始版本为8；ArkTS-Sta起始版本为23。

<!--Device-sensor-interface OrientationResponse extends Response--><!--Device-sensor-interface OrientationResponse extends Response-End-->

**系统能力：** SystemCapability.Sensors.Sensor

## alpha

```TypeScript
alpha: double
```

设备围绕Z轴的旋转角度，即方位角。单位：degree（度）；取值范围：[0, 360]。

**类型：** double

**起始版本：** 8

**ArkTS模式：** ArkTS-Dyn起始版本为8；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-OrientationResponse-alpha: double--><!--Device-OrientationResponse-alpha: double-End-->

**系统能力：** SystemCapability.Sensors.Sensor

## beta

```TypeScript
beta: double
```

设备围绕X轴的旋转角度，即俯仰角。单位：degree（度）；取值范围：[-180, 180]。

**类型：** double

**起始版本：** 8

**ArkTS模式：** ArkTS-Dyn起始版本为8；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-OrientationResponse-beta: double--><!--Device-OrientationResponse-beta: double-End-->

**系统能力：** SystemCapability.Sensors.Sensor

## gamma

```TypeScript
gamma: double
```

设备围绕Y轴的旋转角度，即翻转角。单位：degree（度）；取值范围：[-90, 90]。

**类型：** double

**起始版本：** 8

**ArkTS模式：** ArkTS-Dyn起始版本为8；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-OrientationResponse-gamma: double--><!--Device-OrientationResponse-gamma: double-End-->

**系统能力：** SystemCapability.Sensors.Sensor

