# GeomagneticResponse

设置地磁响应对象，用于描述指定地理位置的地磁场信息。

**起始版本：** 8

**系统能力：** SystemCapability.Sensors.Sensor

## 导入模块

```TypeScript
import { sensor } from '@kit.SensorServiceKit';
```

## deflectionAngle

```TypeScript
deflectionAngle: number
```

磁偏角，即地磁北方向与正北方向在水平面上的角度。单位：°（度）。

**类型：** number

**起始版本：** 8

**系统能力：** SystemCapability.Sensors.Sensor

## geomagneticDip

```TypeScript
geomagneticDip: number
```

磁倾角，即地球磁场线与水平面的夹角。单位：°（度）。

**类型：** number

**起始版本：** 8

**系统能力：** SystemCapability.Sensors.Sensor

## levelIntensity

```TypeScript
levelIntensity: number
```

水平磁场强度，即地磁场在水平面上的总强度。单位：nT（纳特斯拉）。

**类型：** number

**起始版本：** 8

**系统能力：** SystemCapability.Sensors.Sensor

## totalIntensity

```TypeScript
totalIntensity: number
```

总磁场强度，即地磁场三维空间的总强度。单位：nT（纳特斯拉）。

**类型：** number

**起始版本：** 8

**系统能力：** SystemCapability.Sensors.Sensor

## x

```TypeScript
x: number
```

地磁场X方向分量（北分量）。单位：nT（纳特斯拉）。

**类型：** number

**起始版本：** 8

**系统能力：** SystemCapability.Sensors.Sensor

## y

```TypeScript
y: number
```

地磁场Y方向分量（东分量）。单位：nT（纳特斯拉）。

**类型：** number

**起始版本：** 8

**系统能力：** SystemCapability.Sensors.Sensor

## z

```TypeScript
z: number
```

地磁场Z方向分量（垂直分量）。单位：nT（纳特斯拉）。

**类型：** number

**起始版本：** 8

**系统能力：** SystemCapability.Sensors.Sensor
