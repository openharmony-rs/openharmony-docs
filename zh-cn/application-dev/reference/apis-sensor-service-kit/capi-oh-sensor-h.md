# oh_sensor.h
<!--Kit: Sensor Service Kit-->
<!--Subsystem: Sensors-->
<!--Owner: @dilligencer-->
<!--Designer: @butterls-->
<!--Tester: @murphy84-->
<!--Adviser: @hu-zhiqiong-->

## 概述

声明操作传感器的API，包括获取传感器信息和订阅取消订阅传感器数据。

**引用文件：** <sensors/oh_sensor.h>

**库：** libohsensor.so

**系统能力：** SystemCapability.Sensors.Sensor

**起始版本：** 11

**相关模块：** [Sensor](capi-sensor.md)

## 汇总

### 函数

| 名称 | 描述 |
| -- | -- |
| [Sensor_Result OH_Sensor_GetInfos(Sensor_Info **infos, uint32_t *count)](#oh_sensor_getinfos) | 获取设备上所有传感器的信息。 |
| [Sensor_Result OH_Sensor_Subscribe(const Sensor_SubscriptionId *id, const Sensor_SubscriptionAttribute *attribute, const Sensor_Subscriber *subscriber)](#oh_sensor_subscribe) | 订阅传感器数据。系统将以指定的频率向用户报告传感器数据。订阅加速度传感器，需要申请ohos.permission.ACCELEROMETER权限；订阅陀螺仪传感器，需要申请ohos.permission.GYROSCOPE权限；订阅计步器相关传感器时，需要申请ohos.permission.ACTIVITY_MOTION权限；订阅与健康相关的传感器时，比如心率传感器，需要申请ohos.permission.READ_HEALTH_DATA权限，否则订阅失败。订阅其余传感器不需要申请权限。 |
| [Sensor_Result OH_Sensor_Unsubscribe(const Sensor_SubscriptionId *id, const Sensor_Subscriber *subscriber)](#oh_sensor_unsubscribe) | 取消订阅传感器数据。取消订阅加速度计传感器，需要申请ohos.permission.ACCELEROMETER权限；取消订阅陀螺仪传感器，需要申请ohos.permission.GYROSCOPE权限；取消订阅计步器相关传感器时，需要申请ohos.permission.ACTIVITY_MOTION权限；取消订阅与健康相关的传感器时，需要申请ohos.permission.READ_HEALTH_DATA权限，否则取消订阅失败。取消订阅其余传感器不需要申请权限。 |

## 函数说明

### OH_Sensor_GetInfos()

```c
Sensor_Result OH_Sensor_GetInfos(Sensor_Info **infos, uint32_t *count)
```

**描述**

获取设备上所有传感器的信息。

**起始版本：** 11

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [Sensor_Info](capi-sensor-sensor-info.md) **infos | - 双指针指向设备上所有传感器的信息。请参考[Sensor_Info](capi-sensor-sensor-info.md)。 |
| uint32_t *count | - 指向设备上传感器数量的指针。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [Sensor_Result](capi-oh-sensor-type-h.md#sensor_result) | 如果操作成功返回<b>SENSOR_SUCCESS</b>；否则返回[Sensor_Result](capi-oh-sensor-type-h.md#sensor_result)中定义的错误代码。<br> [SENSOR_PARAMETER_ERROR](capi-oh-sensor-type-h.md#sensor_result)参数检查失败。例如，参数无效；或传入的参数类型不正确。<br> [SENSOR_SERVICE_EXCEPTION](capi-oh-sensor-type-h.md#sensor_result)传感器服务异常。 |

### OH_Sensor_Subscribe()

```c
Sensor_Result OH_Sensor_Subscribe(const Sensor_SubscriptionId *id, const Sensor_SubscriptionAttribute *attribute, const Sensor_Subscriber *subscriber)
```

**描述**

订阅传感器数据。系统将以指定的频率向用户报告传感器数据。订阅加速度传感器，需要申请ohos.permission.ACCELEROMETER权限；订阅陀螺仪传感器，需要申请ohos.permission.GYROSCOPE权限；订阅计步器相关传感器时，需要申请ohos.permission.ACTIVITY_MOTION权限；订阅与健康相关的传感器时，比如心率传感器，需要申请ohos.permission.READ_HEALTH_DATA权限，否则订阅失败。订阅其余传感器不需要申请权限。

**需要权限：** ohos.permission.ACCELEROMETER or ohos.permission.GYROSCOPE or
            ohos.permission.ACTIVITY_MOTION or ohos.permission.READ_HEALTH_DATA

**起始版本：** 11

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [const Sensor_SubscriptionId](capi-sensor-sensor-subscriptionid.md) *id | - 指向传感器订阅ID的指针。请参考[Sensor_SubscriptionId](capi-sensor-sensor-subscriptionid.md)。 |
| [const Sensor_SubscriptionAttribute](capi-sensor-sensor-subscriptionattribute.md) *attribute | - 指向订阅属性的指针，该属性用于指定数据报告频率。请参考[Sensor_SubscriptionAttribute](capi-sensor-sensor-subscriptionattribute.md)。 |
| [const Sensor_Subscriber](capi-sensor-sensor-subscriber.md) *subscriber | - 指向订阅者信息的指针，该信息用于指定的回调函数报告传感器数据。请参考[Sensor_Subscriber](capi-sensor-sensor-subscriber.md)。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [Sensor_Result](capi-oh-sensor-type-h.md#sensor_result) | 如果操作成功返回<b>SENSOR_SUCCESS</b>；否则返回[Sensor_Result](capi-oh-sensor-type-h.md#sensor_result)中定义的错误代码。<br> [SENSOR_PERMISSION_DENIED](capi-oh-sensor-type-h.md#sensor_result)权限验证失败。<br> [SENSOR_PARAMETER_ERROR](capi-oh-sensor-type-h.md#sensor_result)参数检查失败。例如，参数无效；或传入的参数类型不正确。<br> [SENSOR_SERVICE_EXCEPTION](capi-oh-sensor-type-h.md#sensor_result)传感器服务异常。 |

### OH_Sensor_Unsubscribe()

```c
Sensor_Result OH_Sensor_Unsubscribe(const Sensor_SubscriptionId *id, const Sensor_Subscriber *subscriber)
```

**描述**

取消订阅传感器数据。取消订阅加速度计传感器，需要申请ohos.permission.ACCELEROMETER权限；取消订阅陀螺仪传感器，需要申请ohos.permission.GYROSCOPE权限；取消订阅计步器相关传感器时，需要申请ohos.permission.ACTIVITY_MOTION权限；取消订阅与健康相关的传感器时，需要申请ohos.permission.READ_HEALTH_DATA权限，否则取消订阅失败。取消订阅其余传感器不需要申请权限。

**需要权限：** ohos.permission.ACCELEROMETER or ohos.permission.GYROSCOPE or
            ohos.permission.ACTIVITY_MOTION or ohos.permission.READ_HEALTH_DATA

**起始版本：** 11

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [const Sensor_SubscriptionId](capi-sensor-sensor-subscriptionid.md) *id | - 指向传感器订阅ID的指针。请参考[Sensor_SubscriptionId](capi-sensor-sensor-subscriptionid.md)。 |
| [const Sensor_Subscriber](capi-sensor-sensor-subscriber.md) *subscriber | - 指向订阅者信息的指针，该信息用于指定的回调函数报告传感器数据。请参考[Sensor_Subscriber](capi-sensor-sensor-subscriber.md)。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [Sensor_Result](capi-oh-sensor-type-h.md#sensor_result) | 如果操作成功返回<b>SENSOR_SUCCESS</b>；否则返回[Sensor_Result](capi-oh-sensor-type-h.md#sensor_result)中定义的错误代码。<br>[SENSOR_PERMISSION_DENIED](capi-oh-sensor-type-h.md#sensor_result)权限验证失败。<br>[SENSOR_PARAMETER_ERROR](capi-oh-sensor-type-h.md#sensor_result)参数检查失败。例如，参数无效；或传入的参数类型不正确。<br>[SENSOR_SERVICE_EXCEPTION](capi-oh-sensor-type-h.md#sensor_result)传感器服务异常。 |


