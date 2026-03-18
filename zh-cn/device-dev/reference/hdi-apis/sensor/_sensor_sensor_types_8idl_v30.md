# SensorTypes.idl

## 概述

定义传感器模块所使用的传感器类型，传感器信息，传感器数据结构等数据类型。

模块包路径：ohos.hdi.sensor.v3_0

**起始版本：**  5.1

**相关模块：**  [HdiSensor](_sensor_hdi_sensor_v30.md)

## 汇总

### 结构体

| 名称 | 描述 |
| -------- | -------- |
| struct&nbsp;&nbsp;[DeviceSensorInfo](_sensor_device_sensor_info_v30.md) | 定义设备信息的基本传感器。 |
| struct&nbsp;&nbsp;[HdfSensorInformation](_sensor_hdf_sensor_information_v30.md) | 定义基本传感器信息。 |
| struct&nbsp;&nbsp;[HdfSensorEvents](_sensor_hdf_sensor_events_v30.md) | 定义传感器报告的数据。 |
| struct&nbsp;&nbsp;[SdcSensorInfo](_sensor_sdc_sensor_info_v30.md) | 定义SDC向节点报告数据对象操作。 |
| struct&nbsp;&nbsp;[SensorPlugInfo](_sensor_sensor_plug_info_v30.md) | 定义信息报告，显示设备已插入。 |

### 枚举

| 名称 | 描述 |
| -------- | -------- |
| [Location](_sensor_hdi_sensor_v30.md#location) { [SENSOR_EXTERNAL](_sensor_hdi_sensor_v30.md) = 0, [LOCAL](_sensor_hdi_sensor_v30.md) = 1 } | 指示传感器是本地传感器还是外围传感器。 |
| [HdfSensorTypeTag](_sensor_hdi_sensor_v30.md#hdfsensortypetag) {<br/>[HDF_SENSOR_TYPE_NONE](_sensor_hdi_sensor_v30.md) = 0, [HDF_SENSOR_TYPE_ACCELEROMETER](_sensor_hdi_sensor_v30.md) = 1, [HDF_SENSOR_TYPE_GYROSCOPE](_sensor_hdi_sensor_v30.md) = 2, [HDF_SENSOR_TYPE_PHOTOPLETHYSMOGRAPH](_sensor_hdi_sensor_v30.md) = 3,<br/>[HDF_SENSOR_TYPE_ELECTROCARDIOGRAPH](_sensor_hdi_sensor_v30.md) = 4, [HDF_SENSOR_TYPE_AMBIENT_LIGHT](_sensor_hdi_sensor_v30.md) = 5, [HDF_SENSOR_TYPE_MAGNETIC_FIELD](_sensor_hdi_sensor_v30.md) = 6, [HDF_SENSOR_TYPE_CAPACITIVE](_sensor_hdi_sensor_v30.md) = 7,<br/>[HDF_SENSOR_TYPE_BAROMETER](_sensor_hdi_sensor_v30.md) = 8, [HDF_SENSOR_TYPE_TEMPERATURE](_sensor_hdi_sensor_v30.md) = 9, [HDF_SENSOR_TYPE_HALL](_sensor_hdi_sensor_v30.md) = 10, [HDF_SENSOR_TYPE_GESTURE](_sensor_hdi_sensor_v30.md) = 11,<br/>[HDF_SENSOR_TYPE_PROXIMITY](_sensor_hdi_sensor_v30.md) = 12, [HDF_SENSOR_TYPE_HUMIDITY](_sensor_hdi_sensor_v30.md) = 13, [HDF_SENSOR_TYPE_COLOR](_sensor_hdi_sensor_v30.md) = 14, [HDF_SENSOR_TYPE_SAR](_sensor_hdi_sensor_v30.md) = 15,<br/>[HDF_SENSOR_TYPE_AMBIENT_LIGHT1](_sensor_hdi_sensor_v30.md) = 16, [HDF_SENSOR_TYPE_MEDICAL_BEGIN](_sensor_hdi_sensor_v30.md) = 128, [HDF_SENSOR_TYPE_MEDICAL_END](_sensor_hdi_sensor_v30.md) = 160, [HDF_SENSOR_TYPE_PHYSICAL_MAX](_sensor_hdi_sensor_v30.md) = 255,<br/>[HDF_SENSOR_TYPE_ORIENTATION](_sensor_hdi_sensor_v30.md) = 256, [HDF_SENSOR_TYPE_GRAVITY](_sensor_hdi_sensor_v30.md) = 257, [HDF_SENSOR_TYPE_LINEAR_ACCELERATION](_sensor_hdi_sensor_v30.md) = 258, [HDF_SENSOR_TYPE_ROTATION_VECTOR](_sensor_hdi_sensor_v30.md) = 259,<br/>[HDF_SENSOR_TYPE_AMBIENT_TEMPERATURE](_sensor_hdi_sensor_v30.md) = 260, [HDF_SENSOR_TYPE_MAGNETIC_FIELD_UNCALIBRATED](_sensor_hdi_sensor_v30.md) = 261, [HDF_SENSOR_TYPE_GAME_ROTATION_VECTOR](_sensor_hdi_sensor_v30.md) = 262, [HDF_SENSOR_TYPE_GYROSCOPE_UNCALIBRATED](_sensor_hdi_sensor_v30.md) = 263,<br/>[HDF_SENSOR_TYPE_SIGNIFICANT_MOTION](_sensor_hdi_sensor_v30.md) = 264, [HDF_SENSOR_TYPE_PEDOMETER_DETECTION](_sensor_hdi_sensor_v30.md) = 265, [HDF_SENSOR_TYPE_PEDOMETER](_sensor_hdi_sensor_v30.md) = 266, [HDF_SENSOR_TYPE_POSTURE](_sensor_hdi_sensor_v30.md) = 267,<br/>[HDF_SENSOR_TYPE_HEADPOSTURE](_sensor_hdi_sensor_v30.md) = 268, [HDF_SENSOR_TYPE_DROP_DETECT](_sensor_hdi_sensor_v30.md) = 269, [HDF_SENSOR_TYPE_GEOMAGNETIC_ROTATION_VECTOR](_sensor_hdi_sensor_v30.md) = 277, [HDF_SENSOR_TYPE_HEART_RATE](_sensor_hdi_sensor_v30.md) = 278,<br/>[HDF_SENSOR_TYPE_DEVICE_ORIENTATION](_sensor_hdi_sensor_v30.md) = 279, [HDF_SENSOR_TYPE_WEAR_DETECTION](_sensor_hdi_sensor_v30.md) = 280, [HDF_SENSOR_TYPE_ACCELEROMETER_UNCALIBRATED](_sensor_hdi_sensor_v30.md) = 281, [HDF_SENSOR_TYPE_RPC](_sensor_hdi_sensor_v30.md) = 282,<br/>[HDF_SENSOR_TYPE_FUSION_PRESSURE](_sensor_hdi_sensor_v30.md) = 283, [HDF_SENSOR_TYPE_MAX](_sensor_hdi_sensor_v30.md)<br/>} | 传感器类型。 |
| [HdfSensorGroupType](_sensor_hdi_sensor_v30.md#hdfsensorgrouptype) { [HDF_TRADITIONAL_SENSOR_TYPE](_sensor_hdi_sensor_v30.md) = 0, [HDF_MEDICAL_SENSOR_TYPE](_sensor_hdi_sensor_v30.md) = 1, [HDF_SENSOR_GROUP_TYPE_MAX](_sensor_hdi_sensor_v30.md) } | 传感器的硬件服务组。 |
