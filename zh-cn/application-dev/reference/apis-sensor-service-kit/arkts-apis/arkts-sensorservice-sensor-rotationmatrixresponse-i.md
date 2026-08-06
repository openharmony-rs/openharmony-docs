# RotationMatrixResponse

设置旋转矩阵响应对象，用于描述旋转矩阵和倾斜矩阵的计算结果。

**起始版本：** 8

**ArkTS模式：** ArkTS-Dyn起始版本为8；ArkTS-Sta起始版本为23。

<!--Device-sensor-interface RotationMatrixResponse--><!--Device-sensor-interface RotationMatrixResponse-End-->

**系统能力：** SystemCapability.Sensors.Sensor

## inclination

```TypeScript
inclination: Array<double>
```

倾斜矩阵，长度为9的一维数组，表示地磁倾斜变换矩阵。

**类型：** Array&lt;double&gt;

**起始版本：** 8

**ArkTS模式：** ArkTS-Dyn起始版本为8；ArkTS-Sta起始版本为23。

<!--Device-RotationMatrixResponse-inclination: Array<double>--><!--Device-RotationMatrixResponse-inclination: Array<double>-End-->

**系统能力：** SystemCapability.Sensors.Sensor

## rotation

```TypeScript
rotation: Array<double>
```

旋转矩阵，长度为9的一维数组，表示设备在三维空间中的旋转状态。

**类型：** Array&lt;double&gt;

**起始版本：** 8

**ArkTS模式：** ArkTS-Dyn起始版本为8；ArkTS-Sta起始版本为23。

<!--Device-RotationMatrixResponse-rotation: Array<double>--><!--Device-RotationMatrixResponse-rotation: Array<double>-End-->

**系统能力：** SystemCapability.Sensors.Sensor

