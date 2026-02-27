# DeviceSensorInfo

## 概述

定义设备信息的基本传感器。

传感器信息包括设备ID、传感器类型ID、传感器ID。

**起始版本：**  5.1

**相关模块：**  [HdiSensor](_sensor_hdi_sensor_v30.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -------- | -------- |
| int [deviceId](#deviceid) | 设备ID。 |
| int [sensorType](#sensortype) | 传感器类型ID（详见 **SensorTypeTag**）。 |
| int [sensorId](#sensorid) | 传感器ID，由传感器驱动程序开发人员定义。 |
| int [location](#location) | 该设备是本地设备还是外部设备。 |

## 结构体成员变量说明

### deviceId

```idl
int DeviceSensorInfo::deviceId
```

**描述**

设备ID。

### location

```idl
int DeviceSensorInfo::location
```

**描述**

该设备是本地设备还是外部设备。

### sensorId

```idl
int DeviceSensorInfo::sensorId
```

**描述**

传感器ID，由传感器驱动程序开发人员定义。

### sensorType

```idl
int DeviceSensorInfo::sensorType
```

**描述**

传感器类型ID（详见 **SensorTypeTag**）。