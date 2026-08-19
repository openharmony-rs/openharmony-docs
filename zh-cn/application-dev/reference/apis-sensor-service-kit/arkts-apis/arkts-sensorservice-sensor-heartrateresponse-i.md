# HeartRateResponse

心率传感器数据，继承于[Response](arkts-sensorservice-sensor-response-i.md)。

**继承/实现关系：** HeartRateResponse extends [Response](arkts-sensorservice-sensor-response-i.md)

**起始版本：** 23

<!--Device-sensor-interface HeartRateResponse--><!--Device-sensor-interface HeartRateResponse-End-->

**系统能力：** SystemCapability.Sensors.Sensor

## 导入模块

```TypeScript
import { sensor } from '@kit.SensorServiceKit';
```

## heartRate

```TypeScript
heartRate: double
```

用户的心率数值。单位：bpm（beats per minute，每分钟心跳次数）。

**类型：** double

**起始版本：** 23

<!--Device-HeartRateResponse-heartRate: double--><!--Device-HeartRateResponse-heartRate: double-End-->

**系统能力：** SystemCapability.Sensors.Sensor

