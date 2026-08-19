# OrientationResponse

方向传感器数据，继承于[Response](arkts-sensorservice-sensor-response-i.md)。

**继承/实现关系：** OrientationResponse extends [Response](arkts-sensorservice-sensor-response-i.md)

**起始版本：** 23

<!--Device-sensor-interface OrientationResponse--><!--Device-sensor-interface OrientationResponse-End-->

**系统能力：** SystemCapability.Sensors.Sensor

## 导入模块

```TypeScript
import { sensor } from '@kit.SensorServiceKit';
```

## alpha

```TypeScript
alpha: double
```

设备围绕Z轴的旋转角度，即方位角。单位：°（度）；取值范围：[0, 360]。

**类型：** double

**起始版本：** 23

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-OrientationResponse-alpha: double--><!--Device-OrientationResponse-alpha: double-End-->

**系统能力：** SystemCapability.Sensors.Sensor

## beta

```TypeScript
beta: double
```

设备围绕X轴的旋转角度，即俯仰角。单位：°（度）；取值范围：[-180, 180]。

**类型：** double

**起始版本：** 23

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-OrientationResponse-beta: double--><!--Device-OrientationResponse-beta: double-End-->

**系统能力：** SystemCapability.Sensors.Sensor

## gamma

```TypeScript
gamma: double
```

设备围绕Y轴的旋转角度，即翻转角。单位：°（度）；取值范围：[-90, 90]。

**类型：** double

**起始版本：** 23

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-OrientationResponse-gamma: double--><!--Device-OrientationResponse-gamma: double-End-->

**系统能力：** SystemCapability.Sensors.Sensor

