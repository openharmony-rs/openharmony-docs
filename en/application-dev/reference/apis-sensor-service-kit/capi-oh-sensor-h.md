# oh_sensor.h
<!--Kit: Sensor Service Kit-->
<!--Subsystem: Sensors-->
<!--Owner: @dilligencer-->
<!--Designer: @andeszhang-->
<!--Tester: @zhaofangyuan-->
<!--Adviser: @hu-zhiqiong-->
<!-- md-trans-meta sourceCommit=78f85b66cc5fc42d50e25c207f47a6006c136e0a translatedAt=2026-09-02T07:28:03.118Z pushedAt=2026-09-05T10:04:16.905Z -->

## Overview

Declares the APIs for the sensor service, including obtaining sensor information and subscribing to and unsubscribing from sensor data.

**File to include**: <sensors/oh_sensor.h>

**Library**: libohsensor.so

**System capability**: SystemCapability.Sensors.Sensor

**Since**: 11

**Related module**: [Sensor](capi-sensor.md)

## Summary

### Functions

| Name| Description|
| -- | -- |
| [Sensor_Result OH_Sensor_GetInfos(Sensor_Info \*\*infos, uint32_t \*count)](#oh_sensor_getinfos) | Obtains information about all sensors on the device. Use scenarios: When an app is launched, it queries the list of sensors supported by the device, displays or hides related functions based on the sensor capabilities, and selects appropriate sensors for subscription. After the call is successful, the sensor information array is returned through the pointer **infos**, and the number of sensors is returned through the pointer **count**. |
| [Sensor_Result OH_Sensor_Subscribe(const Sensor_SubscriptionId \*id, const Sensor_SubscriptionAttribute \*attribute, const Sensor_Subscriber \*subscriber)](#oh_sensor_subscribe) | Subscribes to sensor data. The system will report sensor data to the subscriber at the specified frequency. The subscription is implemented through the event callback mechanism. Use scenarios: Health and fitness apps monitor users' step count and heart rate in real time. Game apps use the accelerometer to implement gravity sensing. Navigation apps use the gyroscope sensor to assist in positioning. Permission description: To subscribe to data of acceleration sensors, request the **ohos.permission.ACCELEROMETER** permission. To subscribe to data of gyroscope sensors, request the **ohos.permission.GYROSCOPE** permission. To subscribe to data of pedometer-related sensors, request the **ohos.permission.ACTIVITY_MOTION** permission. To subscribe to data of health-related sensors, such as heart rate sensors, request the **ohos.permission.READ_HEALTH_DATA** permission. Otherwise, the subscription fails. You do not need to request any permission to subscribe to data of other types of sensors. |
| [Sensor_Result OH_Sensor_Unsubscribe(const Sensor_SubscriptionId \*id, const Sensor_Subscriber \*subscriber)](#oh_sensor_unsubscribe) | Unsubscribes from sensor data. This operation will stop the reporting of sensor data. To unsubscribe from data of acceleration sensors, request the **ohos.permission.ACCELEROMETER** permission. To unsubscribe from data of gyroscope sensors, request the **ohos.permission.GYROSCOPE** permission. To unsubscribe from data of pedometer-related sensors, request the **ohos.permission.ACTIVITY_MOTION** permission. To unsubscribe from data of health-related sensors (such as the heart rate sensor), request the **ohos.permission.READ_HEALTH_DATA** permission. Otherwise, the unsubscription fails. |

## Function Description

### OH_Sensor_GetInfos()

```c
Sensor_Result OH_Sensor_GetInfos(Sensor_Info **infos, uint32_t *count)
```

**Description**

Obtains information about all sensors on the device. Use scenarios: When an app is launched, it queries the list of sensors supported by the device, displays or hides related functions based on the sensor capabilities, and selects appropriate sensors for subscription. After the call is successful, the sensor information array is returned through the pointer **infos**, and the number of sensors is returned through the pointer **count**.

**Since**: 11

**Parameters**

| Name| Description|
| -- | -- |
| Sensor_Info \*\*infos | Double pointers to the information about all sensors on the device. This is an output parameter. The caller does not need to allocate memory in advance. Memory is allocated inside the function. After using the memory, the caller needs to call the corresponding deallocation function to free the memory. After the function is called, **\*infos** points to the sensor information array. For details, see [Sensor_Info](capi-sensor-sensor-info.md). This parameter must not be null. |
| uint32_t \*count | Pointer to the number of sensors on the device. This is an output parameter. The caller only needs to pass a pointer to a **uint32_t** variable. After the function is called, the variable pointed to by **count** will be set to the number of sensors. This parameter must not be null. |

**Returns**

| Type| Description|
| -- | -- |
| [Sensor_Result](capi-oh-sensor-type-h.md#sensor_result) | Enumerated values of [Sensor_Result](capi-oh-sensor-type-h.md#sensor_result):<br> **SENSOR_SUCCESS**: The sensor information is successfully obtained.<br> [SENSOR_PARAMETER_ERROR](capi-oh-sensor-type-h.md#sensor_result): The parameter verification fails. For example, the passed **infos** or **count** is a null pointer.<br> [SENSOR_SERVICE_EXCEPTION](capi-oh-sensor-type-h.md#sensor_result): The sensor service is abnormal. For example, the sensor service is not started or an internal error occurs.<br>For other possible error codes, refer to [Sensor_Result](capi-oh-sensor-type-h.md#sensor_result). |

### OH_Sensor_Subscribe()

```c
Sensor_Result OH_Sensor_Subscribe(const Sensor_SubscriptionId *id, const Sensor_SubscriptionAttribute *attribute, const Sensor_Subscriber *subscriber)
```

**Description**

Subscribes to sensor data. The system will report sensor data to the subscriber at the specified frequency. The subscription is implemented through the event callback mechanism. Use scenarios: Health and fitness apps monitor users' step count and heart rate in real time. Game apps use the accelerometer to implement gravity sensing. Navigation apps use the gyroscope sensor to assist in positioning.

Permission description: To subscribe to data of acceleration sensors, request the **ohos.permission.ACCELEROMETER** permission. To subscribe to data of gyroscope sensors, request the **ohos.permission.GYROSCOPE** permission. To subscribe to data of pedometer-related sensors, request the **ohos.permission.ACTIVITY_MOTION** permission. To subscribe to data of health-related sensors, such as heart rate sensors, request the **ohos.permission.READ_HEALTH_DATA** permission. Otherwise, the subscription fails. You do not need to request any permission to subscribe to data of other types of sensors.

**Required permissions:** ohos.permission.ACCELEROMETER, ohos.permission.GYROSCOPE, ohos.permission.ACTIVITY_MOTION, or ohos.permission.READ_HEALTH_DATA

**Since**: 11

**Parameters**

| Name| Description|
| -- | -- |
| const [Sensor_SubscriptionId](capi-sensor-sensor-subscriptionid.md) \*id | Pointer to the sensor subscription ID. This is an input parameter. This is the ID of the sensor type to be subscribed to. Different sensor types correspond to different IDs, such as the acceleration sensor, gyroscope sensor, and heart rate sensor. For details, see [Sensor_SubscriptionId](capi-sensor-sensor-subscriptionid.md). The caller must ensure that the data pointed to by the ID is valid. This parameter must not be null. |
| const [Sensor_SubscriptionAttribute](capi-sensor-sensor-subscriptionattribute.md) \*attribute | Pointer to the subscription attribute, in Hz, which is used to specify the data reporting frequency. This is an input parameter. The caller needs to create a **Sensor_SubscriptionAttribute** object, set the required data reporting frequency, and then pass the object to this function. The frequency value must be within the range supported by the sensor. The specific range varies depending on the sensor type. High frequencies (above 100 Hz) are suitable for scenarios that require real-time data monitoring (such as gaming), while low frequencies (1–10 Hz) are suitable for power-saving scenarios where high-frequency data is not required (such as background monitoring). Select a proper data reporting frequency based on your requirements. If the data reporting frequency is not set, the default value will be used. For details, see [Sensor_SubscriptionAttribute](capi-sensor-sensor-subscriptionattribute.md). This parameter must not be null. |
| const [Sensor_Subscriber](capi-sensor-sensor-subscriber.md) \*subscriber | Pointer to the subscriber information, including the callback used to report sensor data. This is an input parameter. Before calling this function, the caller must set the callback function. The system will call the callback function at the frequency specified in the subscription attributes. Before the subscription is canceled, the callback function must remain valid and should not be modified or released. For details, see [Sensor_Subscriber](capi-sensor-sensor-subscriber.md). This parameter must not be null. Note: The callback function is executed in the sensor service thread. Do not perform time-consuming operations or block the call in the callback function. Otherwise, the real-time performance of sensor data reporting may be affected. |

**Returns**

| Type| Description|
| -- | -- |
| [Sensor_Result](capi-oh-sensor-type-h.md#sensor_result) | Enumerated values of [Sensor_Result](capi-oh-sensor-type-h.md#sensor_result):<br> **SENSOR_SUCCESS**: The sensor data is successfully subscribed to.<br> [SENSOR_PERMISSION_DENIED](capi-oh-sensor-type-h.md#sensor_result): The permission verification fails. This error is returned when the permission required for subscribing to the sensor is missing. For details about the permissions required for different sensors, see the function description. Request the permissions and try again.<br> [SENSOR_PARAMETER_ERROR](capi-oh-sensor-type-h.md#sensor_result): The parameter verification fails. For example, the passed **id**, **attribute**, or **subscriber** is a null pointer.<br> [SENSOR_SERVICE_EXCEPTION](capi-oh-sensor-type-h.md#sensor_result): The sensor service is abnormal. For example, the sensor service is not started or an internal error occurs.<br>For other possible error codes, refer to [Sensor_Result](capi-oh-sensor-type-h.md#sensor_result). |

### OH_Sensor_Unsubscribe()

```c
Sensor_Result OH_Sensor_Unsubscribe(const Sensor_SubscriptionId *id, const Sensor_Subscriber *subscriber)
```

**Description**

Unsubscribes from sensor data. This operation will stop the reporting of sensor data.

To unsubscribe from data of acceleration sensors, request the **ohos.permission.ACCELEROMETER** permission. To unsubscribe from data of gyroscope sensors, request the **ohos.permission.GYROSCOPE** permission. To unsubscribe from data of pedometer-related sensors, request the **ohos.permission.ACTIVITY_MOTION** permission. To unsubscribe from data of health-related sensors (such as the heart rate sensor), request the **ohos.permission.READ_HEALTH_DATA** permission. Otherwise, the unsubscription fails. You do not need to request any permission to unsubscribe from data of other types of sensors.

**Required permissions:** ohos.permission.ACCELEROMETER, ohos.permission.GYROSCOPE, ohos.permission.ACTIVITY_MOTION, or ohos.permission.READ_HEALTH_DATA

**Since**: 11

**Parameters**

| Name| Description|
| -- | -- |
| const [Sensor_SubscriptionId](capi-sensor-sensor-subscriptionid.md) \*id | Pointer to the sensor subscription ID. This is an input parameter. This is the ID of the subscription to be canceled. It must be the same as the subscription ID used when **OH_Sensor_Subscribe** is called. Otherwise, **SENSOR_PARAMETER_ERROR** may be returned. Different sensor types correspond to different IDs, such as the acceleration sensor, gyroscope sensor, and heart rate sensor. For details, see [Sensor_SubscriptionId](capi-sensor-sensor-subscriptionid.md). This parameter must not be null. |
| const [Sensor_Subscriber](capi-sensor-sensor-subscriber.md) \*subscriber | Pointer to the subscriber information, including the callback used to report sensor data. This is an input parameter. This subscriber must be the same as the one when **OH_Sensor_Subscribe** is called. Otherwise, **SENSOR_PARAMETER_ERROR** may be returned. After the subscription is canceled successfully, the callback function will no longer be called. For details, see [Sensor_Subscriber](capi-sensor-sensor-subscriber.md). This parameter must not be null. |

**Returns**

| Type| Description|
| -- | -- |
| [Sensor_Result](capi-oh-sensor-type-h.md#sensor_result) | Enumerated values of [Sensor_Result](capi-oh-sensor-type-h.md#sensor_result):<br> **SENSOR_SUCCESS**: The subscription to sensor data is successfully canceled.<br> [SENSOR_PERMISSION_DENIED](capi-oh-sensor-type-h.md#sensor_result): The permission verification fails. This error is returned when the permission required for unsubscribing from the sensor is missing. For details about the permissions required for different sensors, see the function description. Request the permissions and try again.<br> [SENSOR_PARAMETER_ERROR](capi-oh-sensor-type-h.md#sensor_result): The parameter verification fails. For example, the passed **id** or **subscriber** is a null pointer.<br> [SENSOR_SERVICE_EXCEPTION](capi-oh-sensor-type-h.md#sensor_result): The sensor service is abnormal. For example, the sensor service is not started or an internal error occurs.<br>For other possible error codes, refer to [Sensor_Result](capi-oh-sensor-type-h.md#sensor_result). |
