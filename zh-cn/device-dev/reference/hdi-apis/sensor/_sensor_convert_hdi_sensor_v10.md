# HdiSensor

## 概述

传感器设备驱动对传感器服务提供通用的接口能力。

模块提供传感器服务对传感器驱动访问统一接口，服务获取驱动对象或者代理后，通过其提供的各类方法，实现获取传感器设备信息、订阅/取消订阅传感器数据、 使能/去使能传感器、设置传感器模式、设置传感器精度、量程等可选配置等。

**起始版本：**  6.1

## 汇总

### 文件

| 名称 | 描述 |
| -------- | -------- |
| [ISensorConvertInterfaces.idl](_sensor_i_sensor_convert_interfaces_8idl_v10.md) | Sensor模块对外通用的接口声明文件，提供获取传感器设备信息、订阅/取消订阅传感器数据、 使能/去使能传感器、设置传感器模式、设置传感器精度，量程等可选配置接口定义。 |
| [ISensorConvertTypes.idl](_sensor_i_sensor_convert_types_8idl_v10.md) | 定义传感器模块所使用的传感器类型，传感器信息，传感器数据结构等数据类型。 |

### 结构体

| 名称 | 描述 |
| -------- | -------- |
| interface&nbsp;&nbsp;[ISensorConvertInterfaces](_sensor_interface_i_sensor_convert_interfaces_v10.md) | 操作包括获取传感器设备信息转换等可选配置接口定义。 |
| struct&nbsp;&nbsp;[HdfSensorData](_sensor_hdf_sensor_data_v10.md) | 传感器参数数据。 |
| struct&nbsp;&nbsp;[HdfDeviceStatusPolicy](_sensor_hdf_device_status_policy_v10.md) | 设备传感器状态策略。 |
