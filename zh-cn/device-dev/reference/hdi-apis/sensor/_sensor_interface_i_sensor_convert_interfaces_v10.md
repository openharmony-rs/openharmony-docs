# ISensorConvertInterfaces

## 概述

**相关模块：**  [HdiSensor](_sensor_convert_hdi_sensor_v10.md)

## 汇总

### Public 成员函数

| 名称 | 描述 |
| -------- | -------- |
| [ConvertSensorData](#convertsensordata) ([in] struct [HdfDeviceStatusPolicy](_sensor_hdf_device_status_policy_v10.md) status, [in] struct [HdfSensorData](_sensor_hdf_sensor_data_v10.md) inSensorData, [out] struct [HdfSensorData](_sensor_hdf_sensor_data_v10.md) outSensorData) | 用于转换传感器数据。 |

## 成员函数说明

### ConvertSensorData()

```
ISensorConvertInterfaces::ConvertSensorData([in] struct HdfDeviceStatusPolicy status, [in] struct HdfSensorData inSensorData, [out] struct HdfSensorData outSensorData)
```

**描述**

用于转换传感器数据。

**起始版本：**  6.1

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| status | 传感器转换策略，详情见 [HdfDeviceStatusPolicy](_sensor_hdf_device_status_policy_v10.md)。 |
| inSensorData | 待转换的传感器数据，详情见 [HdfSensorData](_sensor_hdf_sensor_data_v10.md)。 |
| outSensorData | 转换之后的传感器数据，详情见 [HdfSensorData](_sensor_hdf_sensor_data_v10.md)。 |

**返回：**

如果操作成功，则返回0。

如果操作失败，则返回负值。
