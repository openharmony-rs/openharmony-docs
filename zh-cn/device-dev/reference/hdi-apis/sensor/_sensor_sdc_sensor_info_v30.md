# SdcSensorInfo

## 概述

定义SDC向节点报告数据对象操作。

报告的传感器数据包括偏移量、类型、内存地址、最小速率级别、最大速率级别、保留值。

**起始版本：**  5.1

**相关模块：**  [HdiSensor](_sensor_hdi_sensor_v30.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -------- | -------- |
| unsigned long [offset](#offset) | 用于映射。 |
| int [ddrSize](#ddrsize) | 共享内存大小。 |
| int [minRateLevel](#minratelevel) | 支持的最低速率。 |
| int [maxRateLevel](#maxratelevel) | 支持的最大速率级别。 |
| unsigned long [memAddr](#memaddr) | 共享内存地址。 |
| struct [DeviceSensorInfo](_sensor_device_sensor_info_v30.md) [deviceSensorInfo](#devicesensorinfo) | 设备的传感器ID信息。 |
| int [reserved](#reserved) | 预留字段。 |

## 结构体成员变量说明

### ddrSize

```idl
int SdcSensorInfo::ddrSize
```

**描述**

共享内存大小。

### deviceSensorInfo

```idl
struct DeviceSensorInfo SdcSensorInfo::deviceSensorInfo
```

**描述**

设备的传感器ID信息。

### maxRateLevel

```idl
int SdcSensorInfo::maxRateLevel
```

**描述**

支持的最大速率级别。

### memAddr

```idl
unsigned long SdcSensorInfo::memAddr
```

**描述**

共享内存地址。

### minRateLevel

```idl
int SdcSensorInfo::minRateLevel
```

**描述**

支持的最低速率。

### offset

```idl
unsigned long SdcSensorInfo::offset
```

**描述**

用于映射。

### reserved

```idl
int SdcSensorInfo::reserved
```

**描述**

预留字段。
