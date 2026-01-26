# ISensorCallback

## 概述

定义用于上报传感器数据的回调函数。

传感器用户订阅传感器数据，只在使能传感器后，传感器数据订阅者才能接收传感器数据。详见[ISensorInterface](_sensor_interface_i_sensor_interface_v30.md)。

**起始版本：**  5.1

**相关模块：**  [HdiSensor](_sensor_hdi_sensor_v30.md)

## 汇总

### Public 成员函数

| 名称 | 描述 |
| -------- | -------- |
| [OnDataEvent](#ondataevent) ([in] struct [HdfSensorEvents](_sensor_hdf_sensor_events_v30.md) event) | 定义用于报告传感器数据的功能。 |
| [OnDataEventAsync](#ondataeventasync) ([in] struct [HdfSensorEvents](_sensor_hdf_sensor_events_v30.md)[] events) | 定义用于报告传感器数据的功能。 |

## 成员函数说明

### OnDataEvent()

```
ISensorCallback::OnDataEvent([in] struct HdfSensorEvents event)
```

**描述**

定义用于报告传感器数据的功能。

**起始版本：**  5.1

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| event | 系统中传感器事件的信息。 |

**返回：**

如果操作成功，则返回0。

如果操作失败，则返回负数。

### OnDataEventAsync()

```
ISensorCallback::OnDataEventAsync([in] struct HdfSensorEvents[] events)
```

**描述**

定义用于报告传感器数据的功能。

**起始版本：**  5.1

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| event | 系统中传感器事件的信息。 |

**返回：**

如果操作成功，则返回0。

如果操作失败，则返回负数。
