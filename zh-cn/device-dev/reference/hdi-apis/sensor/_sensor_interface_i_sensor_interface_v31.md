# ISensorInterface

## 概述

定义对传感器执行基本操作的功能。

这些操作包括获取传感器信息、订阅或取消订阅传感器数据、启用或禁用传感器、设置传感器数据报告模式以及设置传感器选项，例如精度和测量范围。

**相关模块：**  [HdiSensor](_sensor_hdi_sensor_v31.md)

## 汇总

### Public 成员函数

| 名称 | 描述 |
| -------- | -------- |
| [EnableWithCallbackId](#enablewithcallbackid) ([in] struct DeviceSensorInfo deviceSensorInfo, [in] unsigned int callbackId) | 启用传感器列表中根据指定传感器 ID 可用的传感器。 用户只有在传感器启用后才能获取传感器数据。 |
| [DisableWithCallbackId](#disablewithcallbackid) ([in] struct DeviceSensorInfo deviceSensorInfo, [in] unsigned int callbackId) | 禁用已启用的传感器。 |
| [SetBatchWithCallbackId](#setbatchwithcallbackid) ([in] struct DeviceSensorInfo deviceSensorInfo, [in] unsigned int callbackId, [in] long samplingInterval, [in] long reportInterval) | 设置带有回调 ID 的批次。 |
| [RegisterWithCallbackId](#registerwithcallbackid) ([in] int groupId, [in] ISensorCallback callbackObj, [in] unsigned int callbackId) | 注册用于向订阅者报告传感器数据的回调函数。 |
| [UnregisterWithCallbackId](#unregisterwithcallbackid) ([in] int groupId, [in] ISensorCallback callbackObj, [in] unsigned int callbackId) | 取消注册用于报告传感器数据的回调函数。 |

## 成员函数说明

### DisableWithCallbackId()

```
ISensorInterface::DisableWithCallbackId([in] struct DeviceSensorInfo deviceSensorInfo, [in] unsigned int callbackId)
```

**描述**

禁用已启用的传感器。

**起始版本：**  6.0

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| deviceSensorInfo | 设备传感器信息，， 详情请参见 **SensorTypeTag**。 |
| callbackId | 表示该操作是在绑定到 Register 的回调对象上进行的。 |

**返回：**

如果操作成功，则返回0。

如果操作失败，则返回负数。

### EnableWithCallbackId()

```
ISensorInterface::EnableWithCallbackId([in] struct DeviceSensorInfo deviceSensorInfo, [in] unsigned int callbackId)
```

**描述**

启用传感器列表中根据指定传感器 ID 可用的传感器。 用户只有在传感器启用后才能获取传感器数据。

**起始版本：**  6.0

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| deviceSensorInfo | 设备传感器信息， 详情请参见 **SensorTypeTag**。 |
| callbackId | 表示该操作是在绑定到 Register 的回调对象上进行的。 |

**返回：**

如果操作成功，则返回0。

如果操作失败，则返回负数。

### RegisterWithCallbackId()

```
ISensorInterface::RegisterWithCallbackId([in] int groupId, [in] ISensorCallback callbackObj, [in] unsigned int callbackId)
```

**描述**

注册用于向订阅者报告传感器数据的回调函数。

sensorId 枚举值范围为 128-160，这意味着已订阅医疗传感器服务。 只需成功订阅一次，无需重复订阅。 sensorId 枚举值范围不在 128-160 之间，这意味着传统传感器已订阅，且订阅成功一次。

**起始版本：**  6.0

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| groupId | 组ID。 |
| callbackObj | 要注册的回调函数。有关详细信息，请参阅 **ISensorCallback**。 |
| callbackId | 表示该操作是在绑定到 Register 的回调对象上进行的。 |

**返回：**

如果操作成功，则返回0。

如果操作失败，则返回负数。

### SetBatchWithCallbackId()

```
ISensorInterface::SetBatchWithCallbackId([in] struct DeviceSensorInfo deviceSensorInfo, [in] unsigned int callbackId, [in] long samplingInterval, [in] long reportInterval)
```

**描述**

设置带有回调 ID 的批次。

**起始版本：**  6.0

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| deviceSensorInfo | 设备传感器信息， 详情请参见 **SensorTypeTag**。 |
| callbackId | 表示该操作是在绑定到 Register 的回调对象上进行的。 |
| samplingInterval | 指示要设置的传感器数据采样间隔，单位为纳秒。 |
| reportInterval | 表示传感器数据报告间隔，单位为纳秒。 |

**返回：**

如果操作成功，则返回0。

如果操作失败，则返回负数。

### UnregisterWithCallbackId()

```
ISensorInterface::UnregisterWithCallbackId([in] int groupId, [in] ISensorCallback callbackObj, [in] unsigned int callbackId)
```

**描述**

取消注册用于报告传感器数据的回调函数。

sensorId 枚举值范围为 128-160，这意味着已订阅医疗传感器服务。 只需成功订阅一次，无需重复订阅。 sensorId 枚举值范围不在 128-160 之间，这意味着传统传感器已订阅，且订阅成功一次。

**起始版本：**  6.0

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| groupId | 组ID。 |
| callbackObj | 要注册的回调函数。有关详细信息，请参阅 **ISensorCallback**。 |
| callbackId | 表示该操作是在绑定到 Register 的回调对象上进行的。 |

**返回：**

如果操作成功，则返回0。

如果操作失败，则返回负数。
