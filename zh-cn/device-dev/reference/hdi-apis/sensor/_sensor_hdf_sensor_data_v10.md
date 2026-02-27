# HdfSensorData

## 概述

**相关模块：**  [HdiSensor](_sensor_convert_hdi_sensor_v10.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -------- | -------- |
| int [sensorTypeId](#sensortypeid) | 传感器类型ID。 |
| int [version](#version) | 传感器算法版本。 |
| long [timestamp](#timestamp) | 传感器数据报告的时间。 |
| int [option](#option) | 传感器数据选项，包括测量范围和精度。 |
| int [mode](#mode) | 传感器数据上报模式。 |
| int [deviceId](#deviceid) | 设备ID。 |
| int [sensorId](#sensorid) | 传感器ID。 |
| int [location](#location) | 该设备室本地还是外部设备。 |
| unsigned char[] [data](#data) | 传感器数据。 |

## 结构体成员变量说明

### data

```
unsigned char [] HdfSensorData::data
```

**描述**

传感器数据。

### deviceId

```
int HdfSensorData::deviceId
```

**描述**

设备ID。

### location

```
int HdfSensorData::location
```

**描述**

该设备室本地还是外部设备。

### mode

```
int HdfSensorData::mode
```

**描述**

传感器数据上报模式。

### option

```
int HdfSensorData::option
```

**描述**

传感器数据选项，包括测量范围和精度。

### sensorId

```
int HdfSensorData::sensorId
```

**描述**

传感器ID。

### sensorTypeId

```
int HdfSensorData::sensorTypeId
```

**描述**

传感器类型ID。

### timestamp

```
long HdfSensorData::timestamp
```

**描述**

传感器数据报告的时间。

### version

```
int HdfSensorData::version
```

**描述**

传感器算法版本。
