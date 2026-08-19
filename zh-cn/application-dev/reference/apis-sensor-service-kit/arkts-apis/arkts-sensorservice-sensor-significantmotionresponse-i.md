# SignificantMotionResponse

有效运动传感器数据，继承于[Response](arkts-sensorservice-sensor-response-i.md)。

**继承/实现关系：** SignificantMotionResponse extends [Response](arkts-sensorservice-sensor-response-i.md)

**起始版本：** 23

<!--Device-sensor-interface SignificantMotionResponse--><!--Device-sensor-interface SignificantMotionResponse-End-->

**系统能力：** SystemCapability.Sensors.Sensor

## 导入模块

```TypeScript
import { sensor } from '@kit.SensorServiceKit';
```

## scalar

```TypeScript
scalar: double
```

表示剧烈运动程度。取值范围：1（检测到有效运动），表示设备在三个物理轴（x、y和z）上存在大幅度运动时上报为1。

**类型：** double

**起始版本：** 23

<!--Device-SignificantMotionResponse-scalar: double--><!--Device-SignificantMotionResponse-scalar: double-End-->

**系统能力：** SystemCapability.Sensors.Sensor

