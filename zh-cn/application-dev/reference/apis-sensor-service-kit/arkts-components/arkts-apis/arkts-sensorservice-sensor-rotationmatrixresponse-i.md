# RotationMatrixResponse

设置旋转矩阵响应对象，用于描述旋转矩阵和倾斜矩阵的计算结果。

**起始版本：** 8

**系统能力：** SystemCapability.Sensors.Sensor

## 导入模块

```TypeScript
import { sensor } from '@kit.SensorServiceKit';
```

## inclination

```TypeScript
inclination: Array<number>
```

倾斜矩阵，长度为9的一维数组，表示地磁倾斜变换矩阵。

**类型：** Array&lt;number&gt;

**起始版本：** 8

**系统能力：** SystemCapability.Sensors.Sensor

## rotation

```TypeScript
rotation: Array<number>
```

旋转矩阵，长度为9的一维数组，表示设备在三维空间中的旋转状态。

**类型：** Array&lt;number&gt;

**起始版本：** 8

**系统能力：** SystemCapability.Sensors.Sensor
