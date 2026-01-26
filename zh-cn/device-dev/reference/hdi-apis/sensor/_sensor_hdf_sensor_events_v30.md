# HdfSensorEvents

## 概述

定义传感器报告的数据。

所报告的传感器数据包括传感器ID、传感器算法版本、数据生成时间、数据选项（例如测量范围和精度）、数据报告模式、数据地址和数据长度。

**起始版本：**  5.1

**相关模块：**  [HdiSensor](_sensor_hdi_sensor_v30.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -------- | -------- |
| struct [DeviceSensorInfo](_sensor_device_sensor_info_v30.md) [deviceSensorInfo](#devicesensorinfo) | 设备的传感器 ID 信息。 |
| int [version](#version) | 传感器算法版本。 |
| long [timestamp](#timestamp) | 传感器数据生成时间。 |
| unsigned int [option](#option) | 传感器数据选项，包括测量范围和精度。 |
| int [mode](#mode) | 传感器数据上报方式。 |
| unsigned char[] [data](#data) | 传感器数据。 |
| unsigned int [dataLen](#datalen) | 传感器数据长度。 |

## 结构体成员变量说明

### data

```
unsigned char [] HdfSensorEvents::data
```

**描述**

传感器数据。

### dataLen

```
unsigned int HdfSensorEvents::dataLen
```

**描述**

传感器数据长度。

### deviceSensorInfo

```
struct DeviceSensorInfo HdfSensorEvents::deviceSensorInfo
```

**描述**

设备的传感器ID信息。

### mode

```
int HdfSensorEvents::mode
```

**描述**

传感器数据上报方式。

### option

```
unsigned int HdfSensorEvents::option
```

**描述**

传感器数据选项，包括测量范围和精度。

### timestamp

```
long HdfSensorEvents::timestamp
```

**描述**

传感器数据生成时间。

### version

```
int HdfSensorEvents::version
```

**描述**

传感器算法版本。
