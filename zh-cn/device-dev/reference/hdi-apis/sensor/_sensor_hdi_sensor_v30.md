# HdiSensor

## 概述

传感器设备驱动对传感器服务提供通用的接口能力。

模块提供传感器服务对传感器驱动访问统一接口，服务获取驱动对象或者代理后，通过其提供的各类方法，实现获取传感器设备信息、订阅/取消订阅传感器数据、 使能/去使能传感器、设置传感器模式、设置传感器精度、量程等可选配置等。

模块提供传感器服务对传感器驱动访问统一接口，服务获取驱动对象或者代理后，通过其提供的各类方法， 以传感器ID区分访问不同类型传感器设备，实现获取传感器设备信息、订阅/取消订阅传感器数据、 使能/去使能传感器、设置传感器模式、设置传感器精度、量程等可选配置等。

**起始版本：**  5.1

**起始版本：**  5.1

## 汇总

### 文件

| 名称 | 描述 |
| -------- | -------- |
| [ISensorCallback.idl](_sensor_i_sensor_callback_8idl_v30.md) | Sensor模块为Sensor服务提供数据上报的回调函数。 |
| [ISensorInterface.idl](_sensor_i_sensor_interface_8idl_v30.md) | Sensor模块对外通用的接口声明文件，提供获取传感器设备信息、订阅/取消订阅传感器数据、 使能/去使能传感器、设置传感器模式、设置传感器精度，量程等可选配置接口定义。 |
| [ISensorPlugCallback.idl](_sensor_i_sensor_plug_callback_8idl_v30.md) | 传感器插拔回调。 |
| [SensorTypes.idl](_sensor_sensor_types_8idl_v30.md) | 定义传感器模块所使用的传感器类型，传感器信息，传感器数据结构等数据类型。 |

### 结构体

| 名称 | 描述 |
| -------- | -------- |
| interface&nbsp;&nbsp;[ISensorCallback](_sensor_interface_i_sensor_callback_v30.md) | 定义用于上报传感器数据的回调函数。 |
| interface&nbsp;&nbsp;[ISensorInterface](_sensor_interface_i_sensor_interface_v30.md) | 提供Sensor设备基本控制操作接口。 |
| interface&nbsp;&nbsp;[ISensorPlugCallback](_sensor_interface_i_sensor_plug_callback_v30.md) | 定义用于报告传感器数据的回调函数。此回调函数需要在以下情况下注册 传感器用户订阅传感器数据。只有在传感器启用后，传感器数据订阅者才能接收数据。 详情请参见[ISensorInterface](_sensor_interface_i_sensor_interface_v30.md)。 |
| struct&nbsp;&nbsp;[DeviceSensorInfo](_sensor_device_sensor_info_v30.md) | 定义设备信息的基本传感器。 |
| struct&nbsp;&nbsp;[HdfSensorInformation](_sensor_hdf_sensor_information_v30.md) | 定义基本传感器信息。 |
| struct&nbsp;&nbsp;[HdfSensorEvents](_sensor_hdf_sensor_events_v30.md) | 定义传感器报告的数据。 |
| struct&nbsp;&nbsp;[SdcSensorInfo](_sensor_sdc_sensor_info_v30.md) | 定义SDC向节点报告数据对象操作。 |
| struct&nbsp;&nbsp;[SensorPlugInfo](_sensor_sensor_plug_info_v30.md) | 定义信息报告，显示设备已插入。 |

### 枚举

| 名称 | 描述 |
| -------- | -------- |
| [Location](#location) { SENSOR_EXTERNAL = 0, LOCAL = 1 } | 指示传感器是本地传感器还是外围传感器。 |
| [HdfSensorTypeTag](#hdfsensortypetag) {<br/>HDF_SENSOR_TYPE_NONE = 0, HDF_SENSOR_TYPE_ACCELEROMETER = 1, HDF_SENSOR_TYPE_GYROSCOPE = 2, HDF_SENSOR_TYPE_PHOTOPLETHYSMOGRAPH = 3,<br/>HDF_SENSOR_TYPE_ELECTROCARDIOGRAPH = 4, HDF_SENSOR_TYPE_AMBIENT_LIGHT = 5, HDF_SENSOR_TYPE_MAGNETIC_FIELD = 6, HDF_SENSOR_TYPE_CAPACITIVE = 7,<br/>HDF_SENSOR_TYPE_BAROMETER = 8, HDF_SENSOR_TYPE_TEMPERATURE = 9, HDF_SENSOR_TYPE_HALL = 10, HDF_SENSOR_TYPE_GESTURE = 11,<br/>HDF_SENSOR_TYPE_PROXIMITY = 12, HDF_SENSOR_TYPE_HUMIDITY = 13, HDF_SENSOR_TYPE_COLOR = 14, HDF_SENSOR_TYPE_SAR = 15,<br/>HDF_SENSOR_TYPE_AMBIENT_LIGHT1 = 16, HDF_SENSOR_TYPE_MEDICAL_BEGIN = 128, HDF_SENSOR_TYPE_MEDICAL_END = 160, HDF_SENSOR_TYPE_PHYSICAL_MAX = 255,<br/>HDF_SENSOR_TYPE_ORIENTATION = 256, HDF_SENSOR_TYPE_GRAVITY = 257, HDF_SENSOR_TYPE_LINEAR_ACCELERATION = 258, HDF_SENSOR_TYPE_ROTATION_VECTOR = 259,<br/>HDF_SENSOR_TYPE_AMBIENT_TEMPERATURE = 260, HDF_SENSOR_TYPE_MAGNETIC_FIELD_UNCALIBRATED = 261, HDF_SENSOR_TYPE_GAME_ROTATION_VECTOR = 262, HDF_SENSOR_TYPE_GYROSCOPE_UNCALIBRATED = 263,<br/>HDF_SENSOR_TYPE_SIGNIFICANT_MOTION = 264, HDF_SENSOR_TYPE_PEDOMETER_DETECTION = 265, HDF_SENSOR_TYPE_PEDOMETER = 266, HDF_SENSOR_TYPE_POSTURE = 267,<br/>HDF_SENSOR_TYPE_HEADPOSTURE = 268, HDF_SENSOR_TYPE_DROP_DETECT = 269, HDF_SENSOR_TYPE_GEOMAGNETIC_ROTATION_VECTOR = 277, HDF_SENSOR_TYPE_HEART_RATE = 278,<br/>HDF_SENSOR_TYPE_DEVICE_ORIENTATION = 279, HDF_SENSOR_TYPE_WEAR_DETECTION = 280, HDF_SENSOR_TYPE_ACCELEROMETER_UNCALIBRATED = 281, HDF_SENSOR_TYPE_RPC = 282,<br/>HDF_SENSOR_TYPE_FUSION_PRESSURE = 283, HDF_SENSOR_TYPE_MAX<br/>} | 传感器类型。 |
| [HdfSensorGroupType](#hdfsensorgrouptype) { HDF_TRADITIONAL_SENSOR_TYPE = 0, HDF_MEDICAL_SENSOR_TYPE = 1, HDF_SENSOR_GROUP_TYPE_MAX } | 传感器的硬件服务组。 |

## 枚举类型说明

### HdfSensorGroupType

```idl
enum HdfSensorGroupType
```

**描述**

传感器的硬件服务组。

**起始版本：**  5.1

| 枚举值 | 描述 |
| -------- | -------- |
| HDF_TRADITIONAL_SENSOR_TYPE | 传统传感器类型，sensorId枚举值范围为128-160。 |
| HDF_MEDICAL_SENSOR_TYPE | 医疗传感器类型，sensorId 枚举值范围不在 128-160 之间。 |
| HDF_SENSOR_GROUP_TYPE_MAX | 最大传感器组类型。 |

### HdfSensorTypeTag

```idl
enum HdfSensorTypeTag
```

**描述**

传感器类型。

**起始版本：**  5.1

| 枚举值 | 描述 |
| -------- | -------- |
| HDF_SENSOR_TYPE_NONE | 空传感器类型，用于测试。 |
| HDF_SENSOR_TYPE_ACCELEROMETER | 加速度传感器。 |
| HDF_SENSOR_TYPE_GYROSCOPE | 陀螺仪传感器。 |
| HDF_SENSOR_TYPE_PHOTOPLETHYSMOGRAPH | 心率传感器。 |
| HDF_SENSOR_TYPE_ELECTROCARDIOGRAPH | 心电传感器。 |
| HDF_SENSOR_TYPE_AMBIENT_LIGHT | 环境光传感器。 |
| HDF_SENSOR_TYPE_MAGNETIC_FIELD | 地磁传感器。 |
| HDF_SENSOR_TYPE_CAPACITIVE | 电容传感器。 |
| HDF_SENSOR_TYPE_BAROMETER | 气压计传感器。 |
| HDF_SENSOR_TYPE_TEMPERATURE | 温度传感器。 |
| HDF_SENSOR_TYPE_HALL | 霍尔传感器。 |
| HDF_SENSOR_TYPE_GESTURE | 手势传感器。 |
| HDF_SENSOR_TYPE_PROXIMITY | 接近光传感器。 |
| HDF_SENSOR_TYPE_HUMIDITY | 湿度传感器。 |
| HDF_SENSOR_TYPE_COLOR | 颜色传感器。 |
| HDF_SENSOR_TYPE_SAR | SAR传感器。 |
| HDF_SENSOR_TYPE_AMBIENT_LIGHT1 | 辅助环境光传感器。 |
| HDF_SENSOR_TYPE_MEDICAL_BEGIN | 医疗传感器ID枚举值范围的开始。 |
| HDF_SENSOR_TYPE_MEDICAL_END | 医疗传感器ID枚举值范围的结束。 |
| HDF_SENSOR_TYPE_PHYSICAL_MAX | 物理传感器最大类型。 |
| HDF_SENSOR_TYPE_ORIENTATION | 方向传感器。 |
| HDF_SENSOR_TYPE_GRAVITY | 重力传感器。 |
| HDF_SENSOR_TYPE_LINEAR_ACCELERATION | 线性加速度传感器。 |
| HDF_SENSOR_TYPE_ROTATION_VECTOR | 旋转矢量传感器。 |
| HDF_SENSOR_TYPE_AMBIENT_TEMPERATURE | 环境温度传感器。 |
| HDF_SENSOR_TYPE_MAGNETIC_FIELD_UNCALIBRATED | 未校准磁场传感器。 |
| HDF_SENSOR_TYPE_GAME_ROTATION_VECTOR | 游戏旋转矢量传感器。 |
| HDF_SENSOR_TYPE_GYROSCOPE_UNCALIBRATED | 未校准陀螺仪传感器。 |
| HDF_SENSOR_TYPE_SIGNIFICANT_MOTION | 大幅度动作传感器。 |
| HDF_SENSOR_TYPE_PEDOMETER_DETECTION | 计步器检测传感器。 |
| HDF_SENSOR_TYPE_PEDOMETER | 计步器传感器。 |
| HDF_SENSOR_TYPE_POSTURE | 姿态传感器 |
| HDF_SENSOR_TYPE_HEADPOSTURE | 头部姿势传感器 |
| HDF_SENSOR_TYPE_DROP_DETECT | 跌落检测传感器 |
| HDF_SENSOR_TYPE_GEOMAGNETIC_ROTATION_VECTOR | 地磁旋转矢量传感器。 |
| HDF_SENSOR_TYPE_HEART_RATE | 心率传感器。 |
| HDF_SENSOR_TYPE_DEVICE_ORIENTATION | 设备方向传感器。 |
| HDF_SENSOR_TYPE_WEAR_DETECTION | 佩戴检测传感器。 |
| HDF_SENSOR_TYPE_ACCELEROMETER_UNCALIBRATED | 未校准加速度传感器。 |
| HDF_SENSOR_TYPE_RPC | 无线电功率控制传感器。 |
| HDF_SENSOR_TYPE_FUSION_PRESSURE | 融合压力传感器。 |
| HDF_SENSOR_TYPE_MAX | 传感器类型最大个数标识。 |

### Location

```idl
enum Location
```

**描述**

指示传感器是本地传感器还是外围传感器。

**起始版本：**  5.1

| 枚举值 | 描述 |
| -------- | -------- |
| SENSOR_EXTERNAL | 表明该传感器是外围传感器。 |
| LOCAL | 表示该传感器位于本地。 |