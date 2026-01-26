# ISensorInterface

## 概述

提供Sensor设备基本控制操作接口。

操作包括获取传感器设备信息、订阅/取消订阅传感器数据、使能/去使能传感器、设置传感器模式、设置传感器精度、量程等可选配置接口定义。

**起始版本：**  5.1

**相关模块：**  [HdiSensor](_sensor_hdi_sensor_v30.md)

## 汇总

### Public 成员函数

| 名称 | 描述 |
| -------- | -------- |
| [GetAllSensorInfo](#getallsensorinfo) ([out] struct [HdfSensorInformation](_sensor_hdf_sensor_information_v30.md)[] info) | 获取系统中所有传感器的信息。 |
| [GetDeviceSensorInfo](#getdevicesensorinfo) ([in] int deviceId, [out] struct [HdfSensorInformation](_sensor_hdf_sensor_information_v30.md)[] info) | 获取设备中传感器信息。 |
| [Enable](#enable) ([in] struct [DeviceSensorInfo](_sensor_device_sensor_info_v30.md) deviceSensorInfo) | 根据指定的传感器 ID，启用传感器列表中可用的传感器。 订阅者只有在传感器启用后才能获取传感器数据。 |
| [Disable](#disable) ([in] struct [DeviceSensorInfo](_sensor_device_sensor_info_v30.md) deviceSensorInfo) | 禁用已启用的传感器。 |
| [SetBatch](#setbatch) ([in] struct [DeviceSensorInfo](_sensor_device_sensor_info_v30.md) deviceSensorInfo, [in] long samplingInterval, [in] long reportInterval) | 设置指定传感器的数据采样间隔和数据报告间隔。 |
| [SetMode](#setmode) ([in] struct [DeviceSensorInfo](_sensor_device_sensor_info_v30.md) deviceSensorInfo, [in] int mode) | 设置指定传感器的数据报告模式。 |
| [SetOption](#setoption) ([in] struct [DeviceSensorInfo](_sensor_device_sensor_info_v30.md) deviceSensorInfo, [in] unsigned int option) | 设置指定传感器的选项，包括其测量范围和精度。 |
| [Register](#register) ([in] int groupId, [in] [ISensorCallback](_sensor_interface_i_sensor_callback_v30.md) callbackObj) | 注册用于向订阅者报告传感器数据的回调函数。 |
| [Unregister](#unregister) ([in] int groupId, [in] [ISensorCallback](_sensor_interface_i_sensor_callback_v30.md) callbackObj) | 取消注册用于报告传感器数据的回调函数。 |
| [ReadData](#readdata) ([in] struct [DeviceSensorInfo](_sensor_device_sensor_info_v30.md) deviceSensorInfo, [out] struct [HdfSensorEvents](_sensor_hdf_sensor_events_v30.md)[] event) | 读取小型系统中的传感器事件数据。 |
| [SetSdcSensor](#setsdcsensor) ([in] struct [DeviceSensorInfo](_sensor_device_sensor_info_v30.md) deviceSensorInfo, [in] boolean enabled, [in] int rateLevel) | 设置SDC传感器。 |
| [GetSdcSensorInfo](#getsdcsensorinfo) ([out] struct [SdcSensorInfo](_sensor_sdc_sensor_info_v30.md)[] sdcSensorInfo) | 获取SDC传感器信息。 |
| [RegisterAsync](#registerasync) ([in] int groupId, [in] [ISensorCallback](_sensor_interface_i_sensor_callback_v30.md) callbackObj) | 注册用于向订阅者报告传感器数据的回调函数。 |
| [UnregisterAsync](#unregisterasync) ([in] int groupId, [in] [ISensorCallback](_sensor_interface_i_sensor_callback_v30.md) callbackObj) | 取消注册用于向订阅者报告传感器数据的回调函数。 |
| [RegSensorPlugCallBack](#regsensorplugcallback) ([in] [ISensorPlugCallback](_sensor_interface_i_sensor_plug_callback_v30.md) callbackObj) | 注册用于报告传感器插拔状态的回调函数。 |
| [UnRegSensorPlugCallBack](#unregsensorplugcallback) ([in] [ISensorPlugCallback](_sensor_interface_i_sensor_plug_callback_v30.md) callbackObj) | 取消注册用于报告传感器插拔状态的回调函数。 |

## 成员函数说明

### Disable()

```
ISensorInterface::Disable([in] struct DeviceSensorInfo deviceSensorInfo)
```

**描述**

禁用已启用的传感器。

**起始版本：**  5.1

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| deviceSensorInfo | 设备传感器信息。 |

**返回：**

如果操作成功，则返回0。

如果操作失败，则返回负数。

### Enable()

```
ISensorInterface::Enable([in] struct DeviceSensorInfo deviceSensorInfo)
```

**描述**

根据指定的传感器 ID，启用传感器列表中可用的传感器。 订阅者只有在传感器启用后才能获取传感器数据。

**起始版本：**  5.1

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| deviceSensorInfo | 设备传感器信息。 |

**返回：**

如果操作成功，则返回0。

如果操作失败，则返回负数。

### GetAllSensorInfo()

```
ISensorInterface::GetAllSensorInfo([out] struct HdfSensorInformation[] info)
```

**描述**

获取系统中所有传感器的信息。

**起始版本：**  5.1

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| info | 系统中所有传感器信息的向量。 传感器信息通常包括传感器名称、传感器供应商、固件版本、 硬件版本、传感器类型 ID、传感器 ID、最大测量范围、精度和功耗。详情请参阅：[HdfSensorInformation](_sensor_hdf_sensor_information_v30.md)。 |

**返回：**

如果操作成功，则返回0。

如果操作失败，则返回负数。

### GetDeviceSensorInfo()

```
ISensorInterface::GetDeviceSensorInfo([in] int deviceId, [out] struct HdfSensorInformation[] info)
```

**描述**

获取设备中传感器信息。

**起始版本：**  5.1

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| info | 系统中所有传感器信息的向量。 传感器信息通常包括传感器名称、传感器供应商、固件版本、 硬件版本、传感器类型 ID、传感器 ID、最大测量范围、精度和功耗。详情请参阅：[HdfSensorInformation](_sensor_hdf_sensor_information_v30.md)。 |
| deviceId | 设备ID。 |

**返回：**

如果操作成功，则返回0。

如果操作失败，则返回负数。

### GetSdcSensorInfo()

```
ISensorInterface::GetSdcSensorInfo([out] struct SdcSensorInfo[] sdcSensorInfo)
```

**描述**

获取SDC传感器信息。

**起始版本：**  5.1

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| sdcSensorInfos | 表示 SDC 类型的数据。 |

**返回：**

如果操作成功，则返回0。

如果操作失败，则返回负数。

### ReadData()

```
ISensorInterface::ReadData([in] struct DeviceSensorInfo deviceSensorInfo, [out] struct HdfSensorEvents[] event)
```

**描述**

读取小型系统中的传感器事件数据。

**起始版本：**  5.1

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| deviceSensorInfo | 设备传感器相关信息。 |
| event | 表示系统中传感器事件数据的向量。 传感器事件数据包括传感器ID、传感器算法版本、数据生成时间、数据选项（例如测量范围和精度）、数据报告模式、数据地址和数据长度。 有关详细信息，请参阅 [HdfSensorEvents](_sensor_hdf_sensor_events_v30.md)。 |

**返回：**

如果操作成功，则返回0。

如果操作失败，则返回负数。

### Register()

```
ISensorInterface::Register([in] int groupId, [in] ISensorCallback callbackObj)
```

**描述**

注册用于向订阅者报告传感器数据的回调函数。

sensorId 枚举值范围为 128-160，这意味着已订阅医疗传感器服务。 只需成功订阅一次，无需重复订阅。 sensorId 枚举值范围不在 128-160 之间，这意味着传统传感器已订阅，且订阅成功一次。

**起始版本：**  5.1

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| callbackObj | 要注册的回调函数。有关详细信息，请参阅 [ISensorCallback](_sensor_interface_i_sensor_callback_v30.md)。 |
| groupId | 组ID。 |

**返回：**

如果操作成功，则返回0。

如果操作失败，则返回负数。

### RegisterAsync()

```
ISensorInterface::RegisterAsync([in] int groupId, [in] ISensorCallback callbackObj)
```

**描述**

注册用于向订阅者报告传感器数据的回调函数。

sensorId 枚举值范围为 128-160，这意味着已订阅医疗传感器服务。 只需成功订阅一次，无需重复订阅。 sensorId 枚举值范围不在 128-160 之间，这意味着传统传感器已订阅，且订阅成功一次。

**起始版本：**  5.1

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| callbackObj | 要注册的回调函数。有关详细信息，请参阅 [ISensorCallback](_sensor_interface_i_sensor_callback_v30.md)。 |
| groupId | 组ID。 |

**返回：**

如果操作成功，则返回0。

如果操作失败，则返回负数。

### RegSensorPlugCallBack()

```
ISensorInterface::RegSensorPlugCallBack([in] ISensorPlugCallback callbackObj)
```

**描述**

注册用于报告传感器插拔状态的回调函数。

sensorId 枚举值范围为 128-160，这意味着已订阅医疗传感器服务。 只需成功订阅一次，无需重复订阅。 sensorId 枚举值范围不在 128-160 之间，这意味着传统传感器已订阅，且订阅成功一次。

**起始版本：**  5.1

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| callbackObj | 要注册的回调函数。有关详细信息，请参阅 [ISensorCallback](_sensor_interface_i_sensor_callback_v30.md)。 |

**返回：**

如果操作成功，则返回0。

如果操作失败，则返回负数。

### SetBatch()

```
ISensorInterface::SetBatch([in] struct DeviceSensorInfo deviceSensorInfo, [in] long samplingInterval, [in] long reportInterval)
```

**描述**

设置指定传感器的数据采样间隔和数据报告间隔。

**起始版本：**  5.1

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| deviceSensorInfo | 设备传感器信息。 |
| samplingInterval | 采样间隔。 |
| reportInterval | 报告间隔。 |

**返回：**

如果操作成功，则返回0。

如果操作失败，则返回负数。

### SetMode()

```
ISensorInterface::SetMode([in] struct DeviceSensorInfo deviceSensorInfo, [in] int mode)
```

**描述**

设置指定传感器的数据报告模式。

**起始版本：**  5.1

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| deviceSensorInfo | 设备传感器信息。 |
| mode | 模式。 |

**返回：**

如果操作成功，则返回0。

如果操作失败，则返回负数。

### SetOption()

```
ISensorInterface::SetOption([in] struct DeviceSensorInfo deviceSensorInfo, [in] unsigned int option)
```

**描述**

设置指定传感器的选项，包括其测量范围和精度。

**起始版本：**  5.1

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| deviceSensorInfo | 设备传感器信息。 |
| option | 选项。 |

**返回：**

如果操作成功，则返回0。

如果操作失败，则返回负数。

### SetSdcSensor()

```
ISensorInterface::SetSdcSensor([in] struct DeviceSensorInfo deviceSensorInfo, [in] boolean enabled, [in] int rateLevel)
```

**描述**

设置SDC传感器。

**起始版本：**  5.1

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| deviceSensorInfo | 设备传感器相关信息。 |
| enabled | 设备传感器是否已启用。 |
| rateLevel | 费率等级。 |

**返回：**

如果操作成功，则返回0。

如果操作失败，则返回负数。

### Unregister()

```
ISensorInterface::Unregister([in] int groupId, [in] ISensorCallback callbackObj)
```

**描述**

取消注册用于报告传感器数据的回调函数。

sensorId 枚举值范围为 128-160，这意味着已订阅医疗传感器服务。 只需成功订阅一次，无需重复订阅。 sensorId 枚举值范围不在 128-160 之间，这意味着传统传感器已订阅，且订阅成功一次。

**起始版本：**  5.1

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| callbackObj | 要注册的回调函数。有关详细信息，请参阅 [ISensorCallback](_sensor_interface_i_sensor_callback_v30.md)。 |
| groupId | 组ID。 |

**返回：**

如果操作成功，则返回0。

如果操作失败，则返回负数。

### UnregisterAsync()

```
ISensorInterface::UnregisterAsync([in] int groupId, [in] ISensorCallback callbackObj)
```

**描述**

取消注册用于向订阅者报告传感器数据的回调函数。

sensorId 枚举值范围为 128-160，这意味着已订阅医疗传感器服务。 只需成功订阅一次，无需重复订阅。 sensorId 枚举值范围不在 128-160 之间，这意味着传统传感器已订阅，且订阅成功一次。

**起始版本：**  5.1

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| callbackObj | 要注册的回调函数。有关详细信息，请参阅 [ISensorCallback](_sensor_interface_i_sensor_callback_v30.md)。 |
| groupId | 组ID。 |

**返回：**

如果操作成功，则返回0。

如果操作失败，则返回负数。

### UnRegSensorPlugCallBack()

```
ISensorInterface::UnRegSensorPlugCallBack([in] ISensorPlugCallback callbackObj)
```

**描述**

取消注册用于报告传感器插拔状态的回调函数。

sensorId 枚举值范围为 128-160，这意味着已订阅医疗传感器服务。 只需成功订阅一次，无需重复订阅。 sensorId 枚举值范围不在 128-160 之间，这意味着传统传感器已订阅，且订阅成功一次。

**起始版本：**  5.1

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| callbackObj | 要注册的回调函数。有关详细信息，请参阅 [ISensorCallback](_sensor_interface_i_sensor_callback_v30.md)。 |

**返回：**

如果操作成功，则返回0。

如果操作失败，则返回负数。
