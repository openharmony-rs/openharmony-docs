# RotationVectorResponse

旋转矢量传感器数据，继承于[Response](arkts-sensorservice-sensor-response-i.md)。

**继承/实现关系：** RotationVectorResponse extends [Response](arkts-sensorservice-sensor-response-i.md)

**起始版本：** 23

<!--Device-sensor-interface RotationVectorResponse--><!--Device-sensor-interface RotationVectorResponse-End-->

**系统能力：** SystemCapability.Sensors.Sensor

## 导入模块

```TypeScript
import { sensor } from '@kit.SensorServiceKit';
```

## w

```TypeScript
w: double
```

旋转矢量的标量分量，描述设备相对于某个参考方向的旋转状态。单位：rad（弧度）。

**类型：** double

**起始版本：** 23

<!--Device-RotationVectorResponse-w: double--><!--Device-RotationVectorResponse-w: double-End-->

**系统能力：** SystemCapability.Sensors.Sensor

## x

```TypeScript
x: double
```

旋转矢量的x轴分量，表示设备旋转状态在x轴方向的投影。

**类型：** double

**起始版本：** 23

<!--Device-RotationVectorResponse-x: double--><!--Device-RotationVectorResponse-x: double-End-->

**系统能力：** SystemCapability.Sensors.Sensor

## y

```TypeScript
y: double
```

旋转矢量的y轴分量，表示设备旋转状态在y轴方向的投影。

**类型：** double

**起始版本：** 23

<!--Device-RotationVectorResponse-y: double--><!--Device-RotationVectorResponse-y: double-End-->

**系统能力：** SystemCapability.Sensors.Sensor

## z

```TypeScript
z: double
```

旋转矢量的z轴分量，表示设备旋转状态在z轴方向的投影。

**类型：** double

**起始版本：** 23

<!--Device-RotationVectorResponse-z: double--><!--Device-RotationVectorResponse-z: double-End-->

**系统能力：** SystemCapability.Sensors.Sensor

