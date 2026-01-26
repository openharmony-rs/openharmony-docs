# SensorPlugInfo

## 概述

定义信息报告，显示设备已插入。

报告的信息包含设备ID、设备名称、插头状态。

**起始版本：**  5.1

**相关模块：**  [HdiSensor](_sensor_hdi_sensor_v30.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -------- | -------- |
| struct [DeviceSensorInfo](_sensor_device_sensor_info_v30.md) [deviceSensorInfo](#devicesensorinfo) | 设备的传感器ID信息。 |
| String [deviceName](#devicename) | 设备名称。 |
| int [status](#status) | 设备插拔状态。 |
| int [reserved](#reserved) | 预留字段。 |

## 结构体成员变量说明

### deviceName

```
String SensorPlugInfo::deviceName
```

**描述**

设备名称。

### deviceSensorInfo

```
struct DeviceSensorInfo SensorPlugInfo::deviceSensorInfo
```

**描述**

设备的传感器ID信息。

### reserved

```
int SensorPlugInfo::reserved
```

**描述**

预留字段。

### status

```
int SensorPlugInfo::status
```

**描述**

设备插拔状态。
