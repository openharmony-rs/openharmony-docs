# LightResponse

环境光传感器数据，继承于[Response](arkts-sensorservice-sensor-response-i.md)。

**继承/实现关系：** LightResponse extends [Response](arkts-sensorservice-sensor-response-i.md)

**起始版本：** 8

**系统能力：** SystemCapability.Sensors.Sensor

## 导入模块

```TypeScript
import { sensor } from '@kit.SensorServiceKit';
```

## colorTemperature

```TypeScript
colorTemperature?: number
```

色温。单位：K（开尔文）。可选参数，如果该参数不支持则返回固定值（固定值由传感器自定义），支持则返回正常数值。

**类型：** number

**起始版本：** 12

**系统能力：** SystemCapability.Sensors.Sensor

## infraredLuminance

```TypeScript
infraredLuminance?: number
```

红外亮度。单位：cd/m²（坎德拉每平方米）。可选参数，如果该参数不支持则返回固定值（固定值由传感器自定义），支持则返回正常数值。

**类型：** number

**起始版本：** 12

**系统能力：** SystemCapability.Sensors.Sensor

## intensity

```TypeScript
intensity: number
```

环境光强度。单位：lux（勒克斯）。

**类型：** number

**起始版本：** 8

**系统能力：** SystemCapability.Sensors.Sensor
