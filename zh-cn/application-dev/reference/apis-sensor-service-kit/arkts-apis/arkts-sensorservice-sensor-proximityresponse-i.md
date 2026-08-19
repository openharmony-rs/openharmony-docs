# ProximityResponse

接近光传感器数据，继承于[Response](arkts-sensorservice-sensor-response-i.md)。

**继承/实现关系：** ProximityResponse extends [Response](arkts-sensorservice-sensor-response-i.md)

**起始版本：** 23

<!--Device-sensor-interface ProximityResponse--><!--Device-sensor-interface ProximityResponse-End-->

**系统能力：** SystemCapability.Sensors.Sensor

## 导入模块

```TypeScript
import { sensor } from '@kit.SensorServiceKit';
```

## distance

```TypeScript
distance: double
```

可见物体与设备显示器的接近程度。取值范围：0表示接近（物体靠近设备），大于0表示远离（物体远离设备）。

**类型：** double

**起始版本：** 23

<!--Device-ProximityResponse-distance: double--><!--Device-ProximityResponse-distance: double-End-->

**系统能力：** SystemCapability.Sensors.Sensor

