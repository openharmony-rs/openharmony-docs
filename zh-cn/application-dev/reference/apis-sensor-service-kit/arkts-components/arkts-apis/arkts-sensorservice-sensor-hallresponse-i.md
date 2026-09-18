# HallResponse

霍尔传感器数据，继承于[Response](arkts-sensorservice-sensor-response-i.md)。

**继承/实现关系：** HallResponse extends [Response](arkts-sensorservice-sensor-response-i.md)

**起始版本：** 8

**系统能力：** SystemCapability.Sensors.Sensor

## 导入模块

```TypeScript
import { sensor } from '@kit.SensorServiceKit';
```

## status

```TypeScript
status: number
```

霍尔开关状态，表示设备周围是否存在磁力吸引。取值范围：0（无磁力吸引，霍尔开关断开）或大于0（有磁力吸引，霍尔开关闭合）。

**类型：** number

**起始版本：** 8

**系统能力：** SystemCapability.Sensors.Sensor
