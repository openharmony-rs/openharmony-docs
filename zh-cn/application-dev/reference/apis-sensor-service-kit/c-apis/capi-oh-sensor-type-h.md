# oh_sensor_type.h

## 概述

定义常用传感器属性。

**库：** libohsensor.so

**系统能力：** SystemCapability.Sensors.Sensor

**起始版本：** 11

**相关模块：** [Sensor](capi-sensor.md)

## 汇总

### 结构体

| 名称 | typedef关键字 | 描述 |
| -- | -- | -- |
| [Sensor_Info](capi-sensor-sensor-info.md) | Sensor_Info | 定义传感器信息结构体，用于存储传感器的基本属性和数据信息，包括传感器类型、版本、标识等关键字段。开发者通过该结构体可获取传感器的完整描述信息，用于传感器的初始化和数据查询。 |
| [Sensor_Event](capi-sensor-sensor-event.md) | Sensor_Event | 定义传感器事件的数据结构，包含传感器类型、时间戳和传感器数据等信息。 |
| [Sensor_SubscriptionId](capi-sensor-sensor-subscriptionid.md) | Sensor_SubscriptionId | 定义传感器订阅ID结构体，用于唯一标识传感器订阅请求。该结构体用于标识一个传感器订阅操作，包含传感器类型、订阅的具体订阅条件等信息。开发者可以通过传感器订阅ID来管理传感器的订阅生命周期，包括激活、去激活和查询订阅状态等操作。<br>在订阅传感器数据时，作为订阅请求的参数，用于标识订阅关系，在查询已订阅的传感器信息时，用于获取对应的订阅状态和数据，在取消传感器订阅时，用于指定需要取消的订阅。 |
| [Sensor_SubscriptionAttribute](capi-sensor-sensor-subscriptionattribute.md) | Sensor_SubscriptionAttribute | 定义传感器订阅属性结构体，用于指定传感器订阅的相关参数，包括订阅的传感器类型、采样间隔等。该属性适用于传感器数据订阅场景，帮助开发者根据业务需求配置订阅方式，提供灵活的传感器数据获取能力。该属性用于指定传感器订阅的具体参数，如采样率、数据上报间隔等，用于配置传感器的数据采集和上报行为。用于运动健康应用中的步数和心率数据订阅，环境监测应用中的温湿度数据实时采集，设备控制应用中的状态变化监听等。 |
| [Sensor_Subscriber](capi-sensor-sensor-subscriber.md) | Sensor_Subscriber | 用于注册传感器数据订阅的订阅者信息结构体，包含订阅回调函数和用户数据。使用该结构体可以指定传感器订阅者的参数，订阅成功后，将接收传感器的数据更新。 |

### 枚举

| 名称 | typedef关键字 | 描述 |
| -- | -- | -- |
| [Sensor_Type](#sensor_type) | Sensor_Type | 枚举传感器类型。 |
| [Sensor_Result](#sensor_result) | Sensor_Result | 定义传感器错误码。 |
| [Sensor_Accuracy](#sensor_accuracy) | Sensor_Accuracy | 枚举传感器报告的数据的精度级别。 |

### 函数

| 名称 | typedef关键字 | 描述 |
| -- | -- | -- |
| [Sensor_Info **OH_Sensor_CreateInfos(uint32_t count)](#oh_sensor_createinfos) | - | 用给定的数字创建一个实例数组，请参考[Sensor_Info](capi-sensor-sensor-info.md)。创建成功后，返回指向count个Sensor_Info实例的指针数组。<br>调用此方法创建的实例数组，在使用完毕后必须调用OH_Sensor_DestroyInfos()销毁并回收内存，否则会导致资源泄漏。 |
| [int32_t OH_Sensor_DestroyInfos(Sensor_Info **sensors, uint32_t count)](#oh_sensor_destroyinfos) | - | 销毁实例数组并回收内存，请参考[Sensor_Info](capi-sensor-sensor-info.md)。调用成功后，实例数组占用的内存被释放，sensors指针及其指向的所有Sensor_Info实例不能再使用。 |
| [int32_t OH_SensorInfo_GetName(Sensor_Info* sensor, char *sensorName, uint32_t *length)](#oh_sensorinfo_getname) | - | 获取传感器名称。获取成功后，sensorName参数中会填充传感器名称的字符串，length参数中会返回字符串的长度（包含结束符）。 |
| [int32_t OH_SensorInfo_GetVendorName(Sensor_Info* sensor, char *vendorName, uint32_t *length)](#oh_sensorinfo_getvendorname) | - | 获取传感器的厂商名称。获取成功后，vendorName参数中会填充传感器厂商名称的字符串，length参数中会返回字符串的长度（包含结束符）。 |
| [int32_t OH_SensorInfo_GetType(Sensor_Info* sensor, Sensor_Type *sensorType)](#oh_sensorinfo_gettype) | - | 获取[Sensor_Type](capi-oh-sensor-type-h.md#sensor_type)。获取成功后，sensorType参数中会填充传感器的类型值。 |
| [int32_t OH_SensorInfo_GetResolution(Sensor_Info* sensor, float *resolution)](#oh_sensorinfo_getresolution) | - | 获取传感器分辨率。获取成功后，resolution参数中会填充传感器的分辨率值。 |
| [int32_t OH_SensorInfo_GetMinSamplingInterval(Sensor_Info* sensor, int64_t *minSamplingInterval)](#oh_sensorinfo_getminsamplinginterval) | - | 获取传感器的最小数据上报间隔。获取成功后，minSamplingInterval参数中会填充传感器的最小数据上报间隔值，单位为纳秒。 |
| [int32_t OH_SensorInfo_GetMaxSamplingInterval(Sensor_Info* sensor, int64_t *maxSamplingInterval)](#oh_sensorinfo_getmaxsamplinginterval) | - | 获取传感器的最大数据上报间隔。获取成功后，maxSamplingInterval参数中会填充传感器的最大数据上报间隔值，单位为纳秒。 |
| [int32_t OH_SensorEvent_GetType(Sensor_Event* sensorEvent, Sensor_Type *sensorType)](#oh_sensorevent_gettype) | - | 获取传感器类型。 |
| [int32_t OH_SensorEvent_GetTimestamp(Sensor_Event* sensorEvent, int64_t *timestamp)](#oh_sensorevent_gettimestamp) | - | 获取传感器数据的时间戳。 |
| [int32_t OH_SensorEvent_GetAccuracy(Sensor_Event* sensorEvent, Sensor_Accuracy *accuracy)](#oh_sensorevent_getaccuracy) | - | 获取传感器数据的精度。 |
| [int32_t OH_SensorEvent_GetData(Sensor_Event* sensorEvent, float **data, uint32_t *length)](#oh_sensorevent_getdata) | - | 数据的长度和内容依赖于监听的传感器类型，传感器上报的数据格式如下所示：SENSOR_TYPE_ACCELEROMETER: data[0]、data[1]、data[2]分别表示设备x、y、z轴的加速度分量，单位m/s²。SENSOR_TYPE_GYROSCOPE: data[0]、data[1]、data[2]分别表示设备x、y、z轴的旋转角速度，单位弧度/s。SENSOR_TYPE_AMBIENT_LIGHT: data[0]表示环境光强度，单位勒克斯；从API版本12开始，data[1]表示色温，单位为开尔文；data[2]表示红外亮度，单位cd/m²。SENSOR_TYPE_MAGNETIC_FIELD: data[0]、data[1]、data[2]分别表示设备x、y、z轴的地磁分量，单位微特斯拉。SENSOR_TYPE_BAROMETER：data[0]表示气压值，单位hPa。SENSOR_TYPE_HALL: data[0]表示皮套吸合状态，0表示打开，大于0表示吸附。SENSOR_TYPE_PROXIMITY：data[0]表示接近状态，0表示接近，大于0表示远离。SENSOR_TYPE_ORIENTATION:data[0]、data[1]、data[2]分别表示设备绕z、x、y轴的角度，单位度。SENSOR_TYPE_GRAVITY：data[0]、data[1]、data[2]分别表示设备x、y、z轴的重力加速度分量，单位m/s²。SENSOR_TYPE_ROTATION_VECTOR:data[0]、data[1]、data[2]分别表示设备x、y、z轴的旋转角度，单位度；data[3]表示旋转向量元素。SENSOR_TYPE_PEDOMETER_DETECTION:data[0]表示步数检测状态，1表示检测到了步数变化。SENSOR_TYPE_PEDOMETER:data[0]表示步数。SENSOR_TYPE_HEART_RATE：data[0]表示心率数值。SENSOR_TYPE_LINEAR_ACCELERATION：从API版本13开始支持。data[0]、data[1]、data[2]分别表示设备x、y、z轴的线性加速度，单位为m/s²。SENSOR_TYPE_GAME_ROTATION_VECTOR：从API版本13开始支持。data[0]、data[1]、data[2]分别表示设备x、y、z轴的旋转角度，单位为度；data[3]表示旋转向量。 |
| [Sensor_SubscriptionId *OH_Sensor_CreateSubscriptionId(void)](#oh_sensor_createsubscriptionid) | - | 创建一个[Sensor_SubscriptionId](capi-sensor-sensor-subscriptionid.md)实例。<br>调用此方法创建的实例，在使用完毕后必须调用OH_Sensor_DestroySubscriptionId()销毁并回收内存，否则会导致资源泄漏。 |
| [int32_t OH_Sensor_DestroySubscriptionId(Sensor_SubscriptionId *id)](#oh_sensor_destroysubscriptionid) | - | 销毁[Sensor_SubscriptionId](capi-sensor-sensor-subscriptionid.md)实例并回收内存。 |
| [int32_t OH_SensorSubscriptionId_GetType(Sensor_SubscriptionId* id, Sensor_Type *sensorType)](#oh_sensorsubscriptionid_gettype) | - | 获取传感器类型。 |
| [int32_t OH_SensorSubscriptionId_SetType(Sensor_SubscriptionId* id, const Sensor_Type sensorType)](#oh_sensorsubscriptionid_settype) | - | 设置传感器类型。调用成功后，订阅ID的类型被设置为指定的sensorType值。 |
| [Sensor_SubscriptionAttribute *OH_Sensor_CreateSubscriptionAttribute(void)](#oh_sensor_createsubscriptionattribute) | - | 创建[Sensor_SubscriptionAttribute](capi-sensor-sensor-subscriptionattribute.md)实例。<br>调用此方法创建的实例，在使用完毕后必须调用OH_Sensor_DestroySubscriptionAttribute()销毁并回收内存，否则会导致资源泄漏。 |
| [int32_t OH_Sensor_DestroySubscriptionAttribute(Sensor_SubscriptionAttribute *attribute)](#oh_sensor_destroysubscriptionattribute) | - | 销毁[Sensor_SubscriptionAttribute](capi-sensor-sensor-subscriptionattribute.md)实例并回收内存。 |
| [int32_t OH_SensorSubscriptionAttribute_SetSamplingInterval(Sensor_SubscriptionAttribute* attribute, const int64_t samplingInterval)](#oh_sensorsubscriptionattribute_setsamplinginterval) | - | 设置传感器数据报告间隔。调用成功后，订阅属性的采样间隔被设置为指定的samplingInterval值，后续传感器数据上报将按照此间隔进行。 |
| [int32_t OH_SensorSubscriptionAttribute_GetSamplingInterval(Sensor_SubscriptionAttribute* attribute, int64_t *samplingInterval)](#oh_sensorsubscriptionattribute_getsamplinginterval) | - | 获取传感器数据报告间隔。 |
| [typedef void (\*Sensor_EventCallback)(Sensor_Event *event)](#sensor_eventcallback) | Sensor_EventCallback | 定义用于报告传感器数据的回调函数。 |
| [Sensor_Subscriber *OH_Sensor_CreateSubscriber(void)](#oh_sensor_createsubscriber) | - | 创建一个[Sensor_Subscriber](capi-sensor-sensor-subscriber.md)实例。<br>调用此方法创建的实例，在使用完毕后必须调用OH_Sensor_DestroySubscriber()销毁并回收内存，否则会导致资源泄漏。 |
| [int32_t OH_Sensor_DestroySubscriber(Sensor_Subscriber *subscriber)](#oh_sensor_destroysubscriber) | - | 销毁[Sensor_Subscriber](capi-sensor-sensor-subscriber.md)实例并回收内存。 |
| [int32_t OH_SensorSubscriber_SetCallback(Sensor_Subscriber* subscriber, const Sensor_EventCallback callback)](#oh_sensorsubscriber_setcallback) | - | 设置一个回调函数来报告传感器数据。调用成功后，订阅者将使用指定的回调函数来报告传感器数据。 |
| [int32_t OH_SensorSubscriber_GetCallback(Sensor_Subscriber* subscriber, Sensor_EventCallback *callback)](#oh_sensorsubscriber_getcallback) | - | 获取用于报告传感器数据的回调函数。 |

## 枚举类型说明

### Sensor_Type

```c
enum Sensor_Type
```

**描述**

枚举传感器类型。

**起始版本：** 11

| 枚举项 | 描述 |
| -- | -- |
| SENSOR_TYPE_ACCELEROMETER = 1 |  |
| SENSOR_TYPE_GYROSCOPE = 2 |  |
| SENSOR_TYPE_AMBIENT_LIGHT = 5 |  |
| SENSOR_TYPE_MAGNETIC_FIELD = 6 |  |
| SENSOR_TYPE_BAROMETER = 8 |  |
| SENSOR_TYPE_HALL = 10 |  |
| SENSOR_TYPE_PROXIMITY = 12 |  |
| SENSOR_TYPE_ORIENTATION = 256 |  |
| SENSOR_TYPE_GRAVITY = 257 |  |
| SENSOR_TYPE_LINEAR_ACCELERATION = 258 |  |
| SENSOR_TYPE_ROTATION_VECTOR = 259 |  |
| SENSOR_TYPE_GAME_ROTATION_VECTOR = 262 |  |
| SENSOR_TYPE_PEDOMETER_DETECTION = 265 |  |
| SENSOR_TYPE_PEDOMETER = 266 |  |
| SENSOR_TYPE_HEART_RATE = 278 |  |

### Sensor_Result

```c
enum Sensor_Result
```

**描述**

定义传感器错误码。

**起始版本：** 11

| 枚举项 | 描述 |
| -- | -- |
| SENSOR_SUCCESS = 0 |  |
| SENSOR_PERMISSION_DENIED = 201 |  |
| SENSOR_PARAMETER_ERROR = 401 |  |
| SENSOR_SERVICE_EXCEPTION = 14500101 |  |

### Sensor_Accuracy

```c
enum Sensor_Accuracy
```

**描述**

枚举传感器报告的数据的精度级别。

**起始版本：** 11

| 枚举项 | 描述 |
| -- | -- |
| SENSOR_ACCURACY_UNRELIABLE = 0 |  |
| SENSOR_ACCURACY_LOW = 1 |  |
| SENSOR_ACCURACY_MEDIUM = 2 |  |
| SENSOR_ACCURACY_HIGH = 3 |  |


## 函数说明

### OH_Sensor_CreateInfos()

```c
Sensor_Info **OH_Sensor_CreateInfos(uint32_t count)
```

**描述**

用给定的数字创建一个实例数组，请参考[Sensor_Info](capi-sensor-sensor-info.md)。创建成功后，返回指向count个Sensor_Info实例的指针数组。<br>调用此方法创建的实例数组，在使用完毕后必须调用OH_Sensor_DestroyInfos()销毁并回收内存，否则会导致资源泄漏。

**起始版本：** 11

**参数：**

| 参数项 | 描述 |
| -- | -- |
| uint32_t count | 要创建的实例的数量，请参考 [Sensor_Info](capi-sensor-sensor-info.md)。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [Sensor_Info **](capi-sensor-sensor-info.md) | 如果操作成功，返回指向[Sensor_Info](capi-sensor-sensor-info.md)实例数组的双指针，数组中包含count个Sensor_Info实例，用于存储传感器信息；否则返回<b>NULL</b>。 |

### OH_Sensor_DestroyInfos()

```c
int32_t OH_Sensor_DestroyInfos(Sensor_Info **sensors, uint32_t count)
```

**描述**

销毁实例数组并回收内存，请参考[Sensor_Info](capi-sensor-sensor-info.md)。调用成功后，实例数组占用的内存被释放，sensors指针及其指向的所有Sensor_Info实例不能再使用。

**起始版本：** 11

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [Sensor_Info](capi-sensor-sensor-info.md) **sensors | 指向[Sensor_Info](capi-sensor-sensor-info.md)实例数组的双指针。 |
| uint32_t count | 要销毁的[Sensor_Info](capi-sensor-sensor-info.md)实例的数量。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 返回操作结果，如果成功返回<b>SENSOR_SUCCESS</b>，表示所有实例已成功销毁；否则返回[Sensor_Result](capi-oh-sensor-type-h.md#sensor_result)中定义的错误代码。 |

### OH_SensorInfo_GetName()

```c
int32_t OH_SensorInfo_GetName(Sensor_Info* sensor, char *sensorName, uint32_t *length)
```

**描述**

获取传感器名称。获取成功后，sensorName参数中会填充传感器名称的字符串，length参数中会返回字符串的长度（包含结束符）。

**起始版本：** 11

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [Sensor_Info](capi-sensor-sensor-info.md)* sensor | 指向传感器信息的指针。 |
| char *sensorName | 指向传感器名称的指针。 |
| uint32_t *length | 指向长度的指针，以字节为单位。调用前应设置为缓冲区大小，调用后返回实际名称长度。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 返回操作结果，如果成功返回<b>SENSOR_SUCCESS</b>，表示传感器名称已成功获取；否则返回[Sensor_Result](capi-oh-sensor-type-h.md#sensor_result)中定义的错误代码。 |

### OH_SensorInfo_GetVendorName()

```c
int32_t OH_SensorInfo_GetVendorName(Sensor_Info* sensor, char *vendorName, uint32_t *length)
```

**描述**

获取传感器的厂商名称。获取成功后，vendorName参数中会填充传感器厂商名称的字符串，length参数中会返回字符串的长度（包含结束符）。

**起始版本：** 11

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [Sensor_Info](capi-sensor-sensor-info.md)* sensor | 指向传感器信息的指针。 |
| char *vendorName | 指向厂商名称的指针。 |
| uint32_t *length | 指向长度的指针，以字节为单位。调用前应设置为缓冲区大小，调用后返回实际厂商名称长度。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 返回操作结果，如果成功返回<b>SENSOR_SUCCESS</b>，表示传感器厂商名称已成功获取；否则返回[Sensor_Result](capi-oh-sensor-type-h.md#sensor_result)中定义的错误代码。 |

### OH_SensorInfo_GetType()

```c
int32_t OH_SensorInfo_GetType(Sensor_Info* sensor, Sensor_Type *sensorType)
```

**描述**

获取[Sensor_Type](capi-oh-sensor-type-h.md#sensor_type)。获取成功后，sensorType参数中会填充传感器的类型值。

**起始版本：** 11

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [Sensor_Info](capi-sensor-sensor-info.md)* sensor | 指向传感器信息的指针。 |
| [Sensor_Type](capi-oh-sensor-type-h.md#sensor_type) *sensorType | 指向传感器类型的指针。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 返回操作结果，如果成功返回<b>SENSOR_SUCCESS</b>，表示传感器类型已成功获取；否则返回[Sensor_Result](capi-oh-sensor-type-h.md#sensor_result)中定义的错误代码。 |

### OH_SensorInfo_GetResolution()

```c
int32_t OH_SensorInfo_GetResolution(Sensor_Info* sensor, float *resolution)
```

**描述**

获取传感器分辨率。获取成功后，resolution参数中会填充传感器的分辨率值。

**起始版本：** 11

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [Sensor_Info](capi-sensor-sensor-info.md)* sensor | 指向传感器信息的指针。 |
| float *resolution | 指向传感器分辨率的指针。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 返回操作结果，如果成功返回<b>SENSOR_SUCCESS</b>，表示传感器分辨率已成功获取；否则返回[Sensor_Result](capi-oh-sensor-type-h.md#sensor_result)中定义的错误代码。 |

### OH_SensorInfo_GetMinSamplingInterval()

```c
int32_t OH_SensorInfo_GetMinSamplingInterval(Sensor_Info* sensor, int64_t *minSamplingInterval)
```

**描述**

获取传感器的最小数据上报间隔。获取成功后，minSamplingInterval参数中会填充传感器的最小数据上报间隔值，单位为纳秒。

**起始版本：** 11

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [Sensor_Info](capi-sensor-sensor-info.md)* sensor | 指向传感器信息的指针。 |
| int64_t *minSamplingInterval | 指向最小数据报告间隔的指针，以纳秒为单位。该值表示传感器支持的最快数据上报间隔，小于该值的设置可能导致数据丢失或性能下降。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 返回操作结果，如果成功返回<b>SENSOR_SUCCESS</b>，表示最小数据上报间隔已成功获取；否则返回[Sensor_Result](capi-oh-sensor-type-h.md#sensor_result)中定义的错误代码。 |

### OH_SensorInfo_GetMaxSamplingInterval()

```c
int32_t OH_SensorInfo_GetMaxSamplingInterval(Sensor_Info* sensor, int64_t *maxSamplingInterval)
```

**描述**

获取传感器的最大数据上报间隔。获取成功后，maxSamplingInterval参数中会填充传感器的最大数据上报间隔值，单位为纳秒。

**起始版本：** 11

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [Sensor_Info](capi-sensor-sensor-info.md)* sensor | 指向传感器信息的指针。 |
| int64_t *maxSamplingInterval | 指向最大数据报告间隔的指针，以纳秒为单位。该值表示传感器支持的最慢数据上报间隔，大于该值的设置可能导致数据更新不及时。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 返回操作结果，如果成功返回<b>SENSOR_SUCCESS</b>，表示最大数据上报间隔已成功获取；否则返回[Sensor_Result](capi-oh-sensor-type-h.md#sensor_result)中定义的错误代码。 |

### OH_SensorEvent_GetType()

```c
int32_t OH_SensorEvent_GetType(Sensor_Event* sensorEvent, Sensor_Type *sensorType)
```

**描述**

获取传感器类型。

**起始版本：** 11

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [Sensor_Event](capi-sensor-sensor-event.md)* sensorEvent | 指向传感器数据信息的指针。 |
| [Sensor_Type](capi-oh-sensor-type-h.md#sensor_type) *sensorType | 指向传感器类型的指针。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 返回操作结果，如果成功返回<b>SENSOR_SUCCESS</b>，表示传感器事件类型已成功获取；否则返回[Sensor_Result](capi-oh-sensor-type-h.md#sensor_result)中定义的错误代码。 |

### OH_SensorEvent_GetTimestamp()

```c
int32_t OH_SensorEvent_GetTimestamp(Sensor_Event* sensorEvent, int64_t *timestamp)
```

**描述**

获取传感器数据的时间戳。

**起始版本：** 11

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [Sensor_Event](capi-sensor-sensor-event.md)* sensorEvent | 指向传感器数据信息的指针。 |
| int64_t *timestamp | 指向时间戳的指针，单位为纳秒，表示传感器数据采集的时间。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 返回操作结果，如果成功返回<b>SENSOR_SUCCESS</b>，表示时间戳已成功获取；否则返回[Sensor_Result](capi-oh-sensor-type-h.md#sensor_result)中定义的错误代码。 |

### OH_SensorEvent_GetAccuracy()

```c
int32_t OH_SensorEvent_GetAccuracy(Sensor_Event* sensorEvent, Sensor_Accuracy *accuracy)
```

**描述**

获取传感器数据的精度。

**起始版本：** 11

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [Sensor_Event](capi-sensor-sensor-event.md)* sensorEvent | 指向传感器数据信息的指针。 |
| [Sensor_Accuracy](capi-oh-sensor-type-h.md#sensor_accuracy) *accuracy | 指向精度的指针。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 返回操作结果，如果成功返回<b>SENSOR_SUCCESS</b>，表示传感器数据精度已成功获取；否则返回[Sensor_Result](capi-oh-sensor-type-h.md#sensor_result)中定义的错误代码。 |

### OH_SensorEvent_GetData()

```c
int32_t OH_SensorEvent_GetData(Sensor_Event* sensorEvent, float **data, uint32_t *length)
```

**描述**

数据的长度和内容依赖于监听的传感器类型，传感器上报的数据格式如下所示：SENSOR_TYPE_ACCELEROMETER: data[0]、data[1]、data[2]分别表示设备x、y、z轴的加速度分量，单位m/s²。SENSOR_TYPE_GYROSCOPE: data[0]、data[1]、data[2]分别表示设备x、y、z轴的旋转角速度，单位弧度/s。SENSOR_TYPE_AMBIENT_LIGHT: data[0]表示环境光强度，单位勒克斯；从API版本12开始，data[1]表示色温，单位为开尔文；data[2]表示红外亮度，单位cd/m²。SENSOR_TYPE_MAGNETIC_FIELD: data[0]、data[1]、data[2]分别表示设备x、y、z轴的地磁分量，单位微特斯拉。SENSOR_TYPE_BAROMETER：data[0]表示气压值，单位hPa。SENSOR_TYPE_HALL: data[0]表示皮套吸合状态，0表示打开，大于0表示吸附。SENSOR_TYPE_PROXIMITY：data[0]表示接近状态，0表示接近，大于0表示远离。SENSOR_TYPE_ORIENTATION:data[0]、data[1]、data[2]分别表示设备绕z、x、y轴的角度，单位度。SENSOR_TYPE_GRAVITY：data[0]、data[1]、data[2]分别表示设备x、y、z轴的重力加速度分量，单位m/s²。SENSOR_TYPE_ROTATION_VECTOR:data[0]、data[1]、data[2]分别表示设备x、y、z轴的旋转角度，单位度；data[3]表示旋转向量元素。SENSOR_TYPE_PEDOMETER_DETECTION:data[0]表示步数检测状态，1表示检测到了步数变化。SENSOR_TYPE_PEDOMETER:data[0]表示步数。SENSOR_TYPE_HEART_RATE：data[0]表示心率数值。SENSOR_TYPE_LINEAR_ACCELERATION：从API版本13开始支持。data[0]、data[1]、data[2]分别表示设备x、y、z轴的线性加速度，单位为m/s²。SENSOR_TYPE_GAME_ROTATION_VECTOR：从API版本13开始支持。data[0]、data[1]、data[2]分别表示设备x、y、z轴的旋转角度，单位为度；data[3]表示旋转向量。

**起始版本：** 11

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [Sensor_Event](capi-sensor-sensor-event.md)* sensorEvent | - 传感器数据信息。 |
| float **data | - 出参，传感器数据数组指针。数据格式依赖传感器类型，具体格式参考函数描述。 |
| uint32_t *length | - 出参，数据数组的长度，表示data数组中有效数据的个数。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 返回操作结果，如果成功返回<b>SENSOR_SUCCESS</b>，表示传感器数据已成功获取；否则返回[Sensor_Result](capi-oh-sensor-type-h.md#sensor_result)中定义的错误代码。 |

### OH_Sensor_CreateSubscriptionId()

```c
Sensor_SubscriptionId *OH_Sensor_CreateSubscriptionId(void)
```

**描述**

创建一个[Sensor_SubscriptionId](capi-sensor-sensor-subscriptionid.md)实例。<br>调用此方法创建的实例，在使用完毕后必须调用OH_Sensor_DestroySubscriptionId()销毁并回收内存，否则会导致资源泄漏。

**起始版本：** 11

**返回：**

| 类型 | 说明 |
| -- | -- |
| [Sensor_SubscriptionId *](capi-sensor-sensor-subscriptionid.md) | 如果操作成功，返回指向[Sensor_SubscriptionId](capi-sensor-sensor-subscriptionid.md)实例的指针，该实例可用于标识传感器订阅；否则返回<b>NULL</b>。 |

### OH_Sensor_DestroySubscriptionId()

```c
int32_t OH_Sensor_DestroySubscriptionId(Sensor_SubscriptionId *id)
```

**描述**

销毁[Sensor_SubscriptionId](capi-sensor-sensor-subscriptionid.md)实例并回收内存。

**起始版本：** 11

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [Sensor_SubscriptionId](capi-sensor-sensor-subscriptionid.md) *id | 指向[Sensor_SubscriptionId](capi-sensor-sensor-subscriptionid.md)实例的指针。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 返回操作结果，如果成功返回<b>SENSOR_SUCCESS</b>，表示订阅ID实例已成功销毁；否则返回[Sensor_Result](capi-oh-sensor-type-h.md#sensor_result)中定义的错误代码。 |

### OH_SensorSubscriptionId_GetType()

```c
int32_t OH_SensorSubscriptionId_GetType(Sensor_SubscriptionId* id, Sensor_Type *sensorType)
```

**描述**

获取传感器类型。

**起始版本：** 11

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [Sensor_SubscriptionId](capi-sensor-sensor-subscriptionid.md)* id | 指向传感器订阅ID的指针。 |
| [Sensor_Type](capi-oh-sensor-type-h.md#sensor_type) *sensorType | 指向传感器类型的指针。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 返回操作结果，如果成功返回<b>SENSOR_SUCCESS</b>，表示传感器订阅类型已成功获取；否则返回[Sensor_Result](capi-oh-sensor-type-h.md#sensor_result)中定义的错误代码。 |

### OH_SensorSubscriptionId_SetType()

```c
int32_t OH_SensorSubscriptionId_SetType(Sensor_SubscriptionId* id, const Sensor_Type sensorType)
```

**描述**

设置传感器类型。调用成功后，订阅ID的类型被设置为指定的sensorType值。

**起始版本：** 11

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [Sensor_SubscriptionId](capi-sensor-sensor-subscriptionid.md)* id | 指向传感器订阅ID的指针。 |
| [const Sensor_Type](capi-oh-sensor-type-h.md#sensor_type) sensorType | 要设置的传感器类型，用于指定订阅的传感器类型。取值范围为[Sensor_Type](capi-oh-sensor-type-h.md#sensor_type)枚举中定义的传感器类型，如SENSOR_TYPE_ACCELEROMETER(加速度传感器)等。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 返回操作结果，如果成功返回<b>SENSOR_SUCCESS</b>，表示传感器订阅类型已成功设置；否则返回[Sensor_Result](capi-oh-sensor-type-h.md#sensor_result)中定义的错误代码。 |

### OH_Sensor_CreateSubscriptionAttribute()

```c
Sensor_SubscriptionAttribute *OH_Sensor_CreateSubscriptionAttribute(void)
```

**描述**

创建[Sensor_SubscriptionAttribute](capi-sensor-sensor-subscriptionattribute.md)实例。<br>调用此方法创建的实例，在使用完毕后必须调用OH_Sensor_DestroySubscriptionAttribute()销毁并回收内存，否则会导致资源泄漏。

**起始版本：** 11

**返回：**

| 类型 | 说明 |
| -- | -- |
| [Sensor_SubscriptionAttribute *](capi-sensor-sensor-subscriptionattribute.md) | 如果操作成功，返回指向[Sensor_SubscriptionAttribute](capi-sensor-sensor-subscriptionattribute.md)实例的指针，该实例可用于配置传感器订阅属性；否则返回<b>NULL</b>。 |

### OH_Sensor_DestroySubscriptionAttribute()

```c
int32_t OH_Sensor_DestroySubscriptionAttribute(Sensor_SubscriptionAttribute *attribute)
```

**描述**

销毁[Sensor_SubscriptionAttribute](capi-sensor-sensor-subscriptionattribute.md)实例并回收内存。

**起始版本：** 11

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [Sensor_SubscriptionAttribute](capi-sensor-sensor-subscriptionattribute.md) *attribute | 指向[Sensor_SubscriptionAttribute](capi-sensor-sensor-subscriptionattribute.md)实例的指针。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 返回操作结果，如果成功返回<b>SENSOR_SUCCESS</b>，表示订阅属性实例已成功销毁；否则返回[Sensor_Result](capi-oh-sensor-type-h.md#sensor_result)中定义的错误代码。 |

### OH_SensorSubscriptionAttribute_SetSamplingInterval()

```c
int32_t OH_SensorSubscriptionAttribute_SetSamplingInterval(Sensor_SubscriptionAttribute* attribute, const int64_t samplingInterval)
```

**描述**

设置传感器数据报告间隔。调用成功后，订阅属性的采样间隔被设置为指定的samplingInterval值，后续传感器数据上报将按照此间隔进行。

**起始版本：** 11

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [Sensor_SubscriptionAttribute](capi-sensor-sensor-subscriptionattribute.md)* attribute | 指向传感器订阅属性的指针。 |
| const int64_t samplingInterval | 要设置的数据报告间隔，以纳秒为单位。该值决定了传感器数据上报的频率，值越小上报频率越高，过小可能导致系统性能压力，需根据传感器类型选择合适范围。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 返回操作结果，如果成功返回<b>SENSOR_SUCCESS</b>，表示传感器数据报告间隔已成功设置；否则返回[Sensor_Result](capi-oh-sensor-type-h.md#sensor_result)中定义的错误代码。 |

### OH_SensorSubscriptionAttribute_GetSamplingInterval()

```c
int32_t OH_SensorSubscriptionAttribute_GetSamplingInterval(Sensor_SubscriptionAttribute* attribute, int64_t *samplingInterval)
```

**描述**

获取传感器数据报告间隔。

**起始版本：** 11

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [Sensor_SubscriptionAttribute](capi-sensor-sensor-subscriptionattribute.md)* attribute | 指向传感器订阅属性的指针。 |
| int64_t *samplingInterval | 指向数据报告间隔的指针，以纳秒为单位。该值为当前设置的传感器数据上报间隔，可用于判断数据上报的频率，一般范围需参考传感器具体要求。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 返回操作结果，如果成功返回<b>SENSOR_SUCCESS</b>，表示传感器数据报告间隔已成功获取；否则返回[Sensor_Result](capi-oh-sensor-type-h.md#sensor_result)中定义的错误代码。 |

### Sensor_EventCallback()

```c
typedef void (*Sensor_EventCallback)(Sensor_Event *event)
```

**描述**

定义用于报告传感器数据的回调函数。

**起始版本：** 11

**参数：**

| 参数项 | 描述 |
| -- | -- |
| (Sensor_Event \*event | 指向传感器数据信息的指针。 |

### OH_Sensor_CreateSubscriber()

```c
Sensor_Subscriber *OH_Sensor_CreateSubscriber(void)
```

**描述**

创建一个[Sensor_Subscriber](capi-sensor-sensor-subscriber.md)实例。<br>调用此方法创建的实例，在使用完毕后必须调用OH_Sensor_DestroySubscriber()销毁并回收内存，否则会导致资源泄漏。

**起始版本：** 11

**返回：**

| 类型 | 说明 |
| -- | -- |
| [Sensor_Subscriber *](capi-sensor-sensor-subscriber.md) | 如果操作成功，返回指向[Sensor_Subscriber](capi-sensor-sensor-subscriber.md)实例的指针，该实例可用于订阅传感器数据；否则返回<b>NULL</b>。 |

### OH_Sensor_DestroySubscriber()

```c
int32_t OH_Sensor_DestroySubscriber(Sensor_Subscriber *subscriber)
```

**描述**

销毁[Sensor_Subscriber](capi-sensor-sensor-subscriber.md)实例并回收内存。

**起始版本：** 11

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [Sensor_Subscriber](capi-sensor-sensor-subscriber.md) *subscriber | 指向[Sensor_Subscriber](capi-sensor-sensor-subscriber.md)实例的指针。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 返回操作结果，如果成功返回<b>SENSOR_SUCCESS</b>，表示订阅者实例已成功销毁；否则返回[Sensor_Result](capi-oh-sensor-type-h.md#sensor_result)中定义的错误代码。 |

### OH_SensorSubscriber_SetCallback()

```c
int32_t OH_SensorSubscriber_SetCallback(Sensor_Subscriber* subscriber, const Sensor_EventCallback callback)
```

**描述**

设置一个回调函数来报告传感器数据。调用成功后，订阅者将使用指定的回调函数来报告传感器数据。

**起始版本：** 11

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [Sensor_Subscriber](capi-sensor-sensor-subscriber.md)* subscriber | 指向传感器订阅者信息的指针。 |
| [const Sensor_EventCallback](capi-oh-sensor-type-h.md#sensor_eventcallback) callback | 要设置的回调函数，用于接收传感器数据上报。回调函数签名为void (*Sensor_EventCallback)(Sensor_Event *event)，其中event参数包含传感器数据的详细信息，如数据类型、时间戳、精度和传感器数据值。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 返回操作结果，如果成功返回<b>SENSOR_SUCCESS</b>，表示回调函数已成功设置；否则返回[Sensor_Result](capi-oh-sensor-type-h.md#sensor_result)中定义的错误代码。 |

### OH_SensorSubscriber_GetCallback()

```c
int32_t OH_SensorSubscriber_GetCallback(Sensor_Subscriber* subscriber, Sensor_EventCallback *callback)
```

**描述**

获取用于报告传感器数据的回调函数。

**起始版本：** 11

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [Sensor_Subscriber](capi-sensor-sensor-subscriber.md)* subscriber | 指向传感器订阅者信息的指针。 |
| [Sensor_EventCallback](capi-oh-sensor-type-h.md#sensor_eventcallback) *callback | 指向回调函数的指针。该值为当前设置的回调函数指针，若未设置则为NULL。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 返回操作结果，如果成功返回<b>SENSOR_SUCCESS</b>，表示回调函数已成功获取；否则返回[Sensor_Result](capi-oh-sensor-type-h.md#sensor_result)中定义的错误代码。 |


