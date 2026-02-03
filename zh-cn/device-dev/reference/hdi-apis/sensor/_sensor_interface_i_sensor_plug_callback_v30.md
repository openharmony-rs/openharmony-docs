# ISensorPlugCallback

## 概述

定义用于报告传感器数据的回调函数。此回调函数需要在以下情况下注册 传感器用户订阅传感器数据。只有在传感器启用后，传感器数据订阅者才能接收数据。 详情请参见[ISensorInterface](_sensor_interface_i_sensor_interface_v30.md)。

**起始版本：**  5.1

**相关模块：**  [HdiSensor](_sensor_hdi_sensor_v30.md)

## 汇总

### Public 成员函数

| 名称 | 描述 |
| -------- | -------- |
| [OnSensorPlugEvent](#onsensorplugevent) ([in] struct [SensorPlugInfo](_sensor_sensor_plug_info_v30.md) sensorPlugInfo) | 定义传感器插入/拔出状态的功能。 |

## 成员函数说明

### OnSensorPlugEvent()

```idl
ISensorPlugCallback::OnSensorPlugEvent([in] struct SensorPlugInfo sensorPlugInfo)
```

**描述**

定义传感器插入/拔出状态的功能。

**起始版本：**  5.1

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| sensorPlugInfo | 传感器插拔信息。 |

**返回：**

如果操作成功，则返回0。

如果操作失败，则返回负数。
