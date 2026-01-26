# HdfSensorInformation

## 概述

定义基本传感器信息。

传感器信息包括传感器名称、供应商、固件版本、硬件版本、传感器类型ID、传感器ID、最大测量范围、精度和功率。

**起始版本：**  5.1

**相关模块：**  [HdiSensor](_sensor_hdi_sensor_v30.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -------- | -------- |
| String [sensorName](#sensorname) | 传感器名称。 |
| String [vendorName](#vendorname) | 传感器供应商。 |
| String [firmwareVersion](#firmwareversion) | 传感器固件版本。 |
| String [hardwareVersion](#hardwareversion) | 传感器硬件版本。 |
| float [maxRange](#maxrange) | 传感器的最大测量范围。 |
| float [accuracy](#accuracy) | 传感器精度。 |
| float [power](#power) | 传感器电源。 |
| long [minDelay](#mindelay) | 允许的最小采样周期（以微秒为单位）。 |
| long [maxDelay](#maxdelay) | 允许的最大采样周期（以微秒为单位）。 |
| unsigned int [fifoMaxEventCount](#fifomaxeventcount) | 该传感器可批量处理的事件最大数量。 |
| struct [DeviceSensorInfo](_sensor_device_sensor_info_v30.md) [deviceSensorInfo](#devicesensorinfo) | 设备的传感器ID信息。 |
| unsigned int [reserved](#reserved) | 第一个 uint8 表示 is_mock_sensor，其余的待定。 |

## 结构体成员变量说明

### accuracy

```
float HdfSensorInformation::accuracy
```

**描述**

传感器精度。

### deviceSensorInfo

```
struct DeviceSensorInfo HdfSensorInformation::deviceSensorInfo
```

**描述**

设备的传感器ID信息。

### fifoMaxEventCount

```
unsigned int HdfSensorInformation::fifoMaxEventCount
```

**描述**

该传感器可批量处理的事件最大数量。

### firmwareVersion

```
String HdfSensorInformation::firmwareVersion
```

**描述**

传感器固件版本。

### hardwareVersion

```
String HdfSensorInformation::hardwareVersion
```

**描述**

传感器硬件版本。

### maxDelay

```
long HdfSensorInformation::maxDelay
```

**描述**

允许的最大采样周期（以微秒为单位）。

### maxRange

```
float HdfSensorInformation::maxRange
```

**描述**

传感器的最大测量范围。

### minDelay

```
long HdfSensorInformation::minDelay
```

**描述**

允许的最小采样周期（以微秒为单位）。

### power

```
float HdfSensorInformation::power
```

**描述**

传感器电源。

### reserved

```
unsigned int HdfSensorInformation::reserved
```

**描述**

第一个 uint8 表示 is_mock_sensor，其余的待定。


### sensorName

```
String HdfSensorInformation::sensorName
```

**描述**

传感器名称。

### vendorName

```
String HdfSensorInformation::vendorName
```

**描述**

传感器供应商。