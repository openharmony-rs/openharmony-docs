# HdiSensor

## 概述

传感器设备驱动对传感器服务提供通用的接口能力。

模块提供传感器服务对传感器驱动访问统一接口，服务获取驱动对象或者代理后，通过其提供的各类方法，实现获取传感器设备信息、订阅/取消订阅传感器数据、 使能/去使能传感器、设置传感器模式、设置传感器精度、量程等可选配置等。

模块提供传感器服务对传感器驱动访问统一接口，服务获取驱动对象或者代理后，通过其提供的各类方法， 以传感器ID区分访问不同类型传感器设备，实现获取传感器设备信息、订阅/取消订阅传感器数据、 使能/去使能传感器、设置传感器模式、设置传感器精度、量程等可选配置等。

**起始版本：**  6.0

**起始版本：**  6.0

## 汇总

### 文件

| 名称 | 描述 |
| -------- | -------- |
| [ISensorInterface.idl](_sensor_i_sensor_interface_8idl_v31.md) | Sensor模块对外通用的接口声明文件，提供获取传感器设备信息、订阅/取消订阅传感器数据、 使能/去使能传感器、设置传感器模式、设置传感器精度，量程等可选配置接口定义。 |
| [SensorTypes.idl](_sensor_sensor_types_8idl_v31.md) | 定义传感器模块所使用的传感器类型，传感器信息，传感器数据结构等数据类型。 |

### 结构体

| 名称 | 描述 |
| -------- | -------- |
| interface&nbsp;&nbsp;[ISensorInterface](_sensor_interface_i_sensor_interface_v31.md) | 定义对传感器执行基本操作的功能。 |

### 枚举

| 名称 | 描述 |
| -------- | -------- |
| [CallbackId](#callbackid) {<br/>CALLBACK_ID_BEGIN = 100000, GPS_CALLBACK_ID_BEGIN = 100001, GPS_CALLBACK_ID_END = 100010, THP_CALLBACK_ID_BEGIN = 100011,<br/>THP_CALLBACK_ID_END = 100020, CALLBACK_ID_END<br/>} | 回调函数的ID。 |

## 枚举类型说明

### CallbackId

```
enum CallbackId
```

**描述**

回调函数的ID。

**起始版本：**  6.0

| 枚举值 | 描述 |
| -------- | -------- |
| CALLBACK_ID_BEGIN | 最小回调ID。 |
| GPS_CALLBACK_ID_BEGIN | GPS的起始回调ID。 |
| GPS_CALLBACK_ID_END | GPS的结束回调ID。 |
| THP_CALLBACK_ID_BEGIN | thp的开始回调ID。 |
| THP_CALLBACK_ID_END | thp的结束回调ID。 |
| CALLBACK_ID_END | 最大回调ID。 |
