# LocationOptions

指示地理位置，用于传入经纬度和海拔信息以计算地磁场。

**起始版本：** 23

<!--Device-sensor-interface LocationOptions--><!--Device-sensor-interface LocationOptions-End-->

**系统能力：** SystemCapability.Sensors.Sensor

## 导入模块

```TypeScript
import { sensor } from '@kit.SensorServiceKit';
```

## altitude

```TypeScript
altitude: double
```

海拔高度。单位：m（米）。

**类型：** double

**起始版本：** 23

<!--Device-LocationOptions-altitude: double--><!--Device-LocationOptions-altitude: double-End-->

**系统能力：** SystemCapability.Sensors.Sensor

## latitude

```TypeScript
latitude: double
```

纬度。取值范围：[-90, 90]。单位：°（度）。

**类型：** double

**起始版本：** 23

<!--Device-LocationOptions-latitude: double--><!--Device-LocationOptions-latitude: double-End-->

**系统能力：** SystemCapability.Sensors.Sensor

## longitude

```TypeScript
longitude: double
```

经度。取值范围：[-180, 180]。单位：°（度）。

**类型：** double

**起始版本：** 23

<!--Device-LocationOptions-longitude: double--><!--Device-LocationOptions-longitude: double-End-->

**系统能力：** SystemCapability.Sensors.Sensor

