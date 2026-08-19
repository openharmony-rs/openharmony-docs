# PedometerDetectionResponse

计步检测传感器数据，继承于[Response](arkts-sensorservice-sensor-response-i.md)。

**继承/实现关系：** PedometerDetectionResponse extends [Response](arkts-sensorservice-sensor-response-i.md)

**起始版本：** 23

<!--Device-sensor-interface PedometerDetectionResponse--><!--Device-sensor-interface PedometerDetectionResponse-End-->

**系统能力：** SystemCapability.Sensors.Sensor

## 导入模块

```TypeScript
import { sensor } from '@kit.SensorServiceKit';
```

## scalar

```TypeScript
scalar: double
```

计步检测标量。取值范围：1（检测到计步事件，表示用户产生了计步行走的动作）或0（未检测到计步事件，表示用户没有发生运动）。

**类型：** double

**起始版本：** 23

<!--Device-PedometerDetectionResponse-scalar: double--><!--Device-PedometerDetectionResponse-scalar: double-End-->

**系统能力：** SystemCapability.Sensors.Sensor

