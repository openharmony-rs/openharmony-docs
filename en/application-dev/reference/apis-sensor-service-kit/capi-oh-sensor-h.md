# oh_sensor.h
<!--Kit: Sensor Service Kit-->
<!--Subsystem: Sensors-->
<!--Owner: @dilligencer-->
<!--Designer: @butterls-->
<!--Tester: @murphy84-->
<!--Adviser: @hu-zhiqiong-->

## Overview

The **oh_sensor.h** file declares the APIs for operating sensors, including obtaining sensor information and subscribing to and unsubscribing from sensor data.

**Library**: libohsensor.so

**System capability**: SystemCapability.Sensors.Sensor

**Since**: 11

**Related Module**: [Sensor](capi-sensor.md)

## Summary

### Functions

| Name| Description|
| -- | -- |
| [Sensor_Result OH_Sensor_GetInfos(Sensor_Info **infos, uint32_t *count)](#oh_sensor_getinfos) | Obtains information about all sensors on the device.|
| [Sensor_Result OH_Sensor_Subscribe(const Sensor_SubscriptionId *id, const Sensor_SubscriptionAttribute *attribute, const Sensor_Subscriber *subscriber)](#oh_sensor_subscribe) | Subscribes to sensor data. The system will report sensor data to the subscriber at the specified frequency. To subscribe to data of acceleration sensors, request the **ohos.permission.ACCELEROMETER** permission. To subscribe to data of gyroscope sensors, request the **ohos.permission.GYROSCOPE** permission. To subscribe to data of pedometer-related sensors, request the **ohos.permission.ACTIVITY_MOTION** permission. To subscribe to data of health-related sensors, such as heart rate sensors, request the **ohos.permission.READ_HEALTH_DATA** permission. Otherwise, the subscription fails. You do not need to request any permission to subscribe to data of other types of sensors.|
| [Sensor_Result OH_Sensor_Unsubscribe(const Sensor_SubscriptionId *id, const Sensor_Subscriber *subscriber)](#oh_sensor_unsubscribe) | Unsubscribes from sensor data. To unsubscribe from data of acceleration sensors, request the **ohos.permission.ACCELEROMETER** permission. To unsubscribe from data of gyroscope sensors, request the **ohos.permission.GYROSCOPE** permission. To unsubscribe from data of pedometer-related sensors, request the **ohos.permission.ACTIVITY_MOTION** permission. To unsubscribe from data of health-related sensors, request the **ohos.permission.READ_HEALTH_DATA** permission. Otherwise, the unsubscription fails. You do not need to request any permission to unsubscribe from data of other types of sensors.|

## Function Description

### OH_Sensor_GetInfos()

```
Sensor_Result OH_Sensor_GetInfos(Sensor_Info **infos, uint32_t *count)
```

**Description**

Obtains information about all sensors on the device.

**Since**: 11

**Parameters**

| Name| Description|
| -- | -- |
| [Sensor_Info](capi-sensor-sensor-info.md) **infos | Double pointer to the information about all sensors on the device. For details, see [Sensor_Info](capi-sensor-sensor-info.md).|
| uint32_t *count | Pointer to the number of sensors on the device.|

**Returns**

| Type| Description|
| -- | -- |
| [Sensor_Result](capi-oh-sensor-type-h.md#sensor_result) | **SENSOR_SUCCESS** if the operation is successful; an error code defined in [Sensor_Result](capi-oh-sensor-type-h.md#sensor_result) otherwise. The error code can be:<br> - [SENSOR_PARAMETER_ERROR](capi-oh-sensor-type-h.md#sensor_result) if the parameter verification fails. For example, the parameter is invalid or the parameter type is incorrect.<br> - [SENSOR_SERVICE_EXCEPTION](capi-oh-sensor-type-h.md#sensor_result) if the sensor service is abnormal.|

### OH_Sensor_Subscribe()

```
Sensor_Result OH_Sensor_Subscribe(const Sensor_SubscriptionId *id, const Sensor_SubscriptionAttribute *attribute, const Sensor_Subscriber *subscriber)
```

**Description**

Subscribes to sensor data. The system will report sensor data to the subscriber at the specified frequency. To subscribe to data of acceleration sensors, request the **ohos.permission.ACCELEROMETER** permission. To subscribe to data of gyroscope sensors, request the **ohos.permission.GYROSCOPE** permission. To subscribe to data of pedometer-related sensors, request the **ohos.permission.ACTIVITY_MOTION** permission. To subscribe to data of health-related sensors, such as heart rate sensors, request the **ohos.permission.READ_HEALTH_DATA** permission. Otherwise, the subscription fails. You do not need to request any permission to subscribe to data of other types of sensors.

**Required permissions:** ohos.permission.ACCELEROMETER or ohos.permission.GYROSCOPE or
            ohos.permission.ACTIVITY_MOTION or ohos.permission.READ_HEALTH_DATA

**Since**: 11

**Parameters**

| Name| Description|
| -- | -- |
| [const Sensor_SubscriptionId](capi-sensor-sensor-subscriptionid.md) *id | Pointer to the sensor subscription ID. For details, see [Sensor_SubscriptionId](capi-sensor-sensor-subscriptionid.md).|
| [const Sensor_SubscriptionAttribute](capi-sensor-sensor-subscriptionattribute.md) *attribute | Pointer to the subscription attribute, which is used to specify the data reporting frequency. For details, see [Sensor_SubscriptionAttribute](capi-sensor-sensor-subscriptionattribute.md).|
| [const Sensor_Subscriber](capi-sensor-sensor-subscriber.md) *subscriber | Pointer to the subscriber information, which is used by the callback function to report sensor data. For details, see [Sensor_Subscriber](capi-sensor-sensor-subscriber.md).|

**Returns**

| Type| Description|
| -- | -- |
| [Sensor_Result](capi-oh-sensor-type-h.md#sensor_result) | **SENSOR_SUCCESS** if the operation is successful; an error code defined in [Sensor_Result](capi-oh-sensor-type-h.md#sensor_result) otherwise. The error code can be:<br> - [SENSOR_PERMISSION_DENIED](capi-oh-sensor-type-h.md#sensor_result) if the permission verification fails.<br> - [SENSOR_PARAMETER_ERROR](capi-oh-sensor-type-h.md#sensor_result) if the parameter verification fails. For example, the parameter is invalid or the parameter type is incorrect.<br> - [SENSOR_SERVICE_EXCEPTION](capi-oh-sensor-type-h.md#sensor_result) if the sensor service is abnormal.|

### OH_Sensor_Unsubscribe()

```
Sensor_Result OH_Sensor_Unsubscribe(const Sensor_SubscriptionId *id, const Sensor_Subscriber *subscriber)
```

**Description**

Unsubscribes from sensor data. To unsubscribe from data of acceleration sensors, request the **ohos.permission.ACCELEROMETER** permission. To unsubscribe from data of gyroscope sensors, request the **ohos.permission.GYROSCOPE** permission. To unsubscribe from data of pedometer-related sensors, request the **ohos.permission.ACTIVITY_MOTION** permission. To unsubscribe from data of health-related sensors, request the **ohos.permission.READ_HEALTH_DATA** permission. Otherwise, the unsubscription fails. You do not need to request any permission to unsubscribe from data of other types of sensors.

**Required permissions:** ohos.permission.ACCELEROMETER or ohos.permission.GYROSCOPE or
            ohos.permission.ACTIVITY_MOTION or ohos.permission.READ_HEALTH_DATA

**Since**: 11

**Parameters**

| Name| Description|
| -- | -- |
| [const Sensor_SubscriptionId](capi-sensor-sensor-subscriptionid.md) *id | Pointer to the sensor subscription ID. For details, see [Sensor_SubscriptionId](capi-sensor-sensor-subscriptionid.md).|
| [const Sensor_Subscriber](capi-sensor-sensor-subscriber.md) *subscriber | Pointer to the subscriber information, which is used by the callback function to report sensor data. For details, see [Sensor_Subscriber](capi-sensor-sensor-subscriber.md).|

**Returns**

| Type| Description|
| -- | -- |
| [Sensor_Result](capi-oh-sensor-type-h.md#sensor_result) | **SENSOR_SUCCESS** if the operation is successful; an error code defined in [Sensor_Result](capi-oh-sensor-type-h.md#sensor_result) otherwise. The error code can be:<br>- [SENSOR_PERMISSION_DENIED](capi-oh-sensor-type-h.md#sensor_result) if the permission verification fails.<br>- [SENSOR_PARAMETER_ERROR](capi-oh-sensor-type-h.md#sensor_result) if the parameter verification fails. For example, the parameter is invalid or the parameter type is incorrect.<br>- [SENSOR_SERVICE_EXCEPTION](capi-oh-sensor-type-h.md#sensor_result) if the sensor service is abnormal.|
