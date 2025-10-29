# oh_sensor_type.h
<!--Kit: Sensor Service Kit-->
<!--Subsystem: Sensors-->
<!--Owner: @dilligencer-->
<!--Designer: @butterls-->
<!--Tester: @murphy84-->
<!--Adviser: @hu-zhiqiong-->

## Overview

Declares the common sensor attributes.

**Reference file**: <sensors/oh_sensor_type.h>

**Library**: libohsensor.so

**System capability**: SystemCapability.Sensors.Sensor

**Since**: 11

**Related Module**: [Sensor](capi-sensor.md)

## Summary

### Structs

| Name| typedef Keyword| Description|
| -- | -- | -- |
| [Sensor_Info](capi-sensor-sensor-info.md) | Sensor_Info | Defines a struct for the sensor information.|
| [Sensor_Event](capi-sensor-sensor-event.md) | Sensor_Event | Defines a struct for the sensor data information.|
| [Sensor_SubscriptionId](capi-sensor-sensor-subscriptionid.md) | Sensor_SubscriptionId | Defines a struct for the sensor subscription ID, which uniquely identifies a sensor.|
| [Sensor_SubscriptionAttribute](capi-sensor-sensor-subscriptionattribute.md) | Sensor_SubscriptionAttribute | Defines a struct for the sensor subscription attribute.|
| [Sensor_Subscriber](capi-sensor-sensor-subscriber.md) | Sensor_Subscriber | Defines a struct for the sensor subscriber information.|

### Enumeration

| Name| typedef Keyword| Description|
| -- | -- | -- |
| [Sensor_Type](#sensor_type) | Sensor_Type | Enumerates the sensor types.|
| [Sensor_Result](#sensor_result) | Sensor_Result | Enumerates the sensor result codes.|
| [Sensor_Accuracy](#sensor_accuracy) | Sensor_Accuracy | Enumerates the accuracy levels of data reported by a sensor.|

### Functions

| Name| typedef Keyword| Description|
| -- | -- | -- |
| [Sensor_Info **OH_Sensor_CreateInfos(uint32_t count)](#oh_sensor_createinfos) | - | Creates an instance array using a given number. For details, see [Sensor_Info](capi-sensor-sensor-info.md).|
| [int32_t OH_Sensor_DestroyInfos(Sensor_Info **sensors, uint32_t count)](#oh_sensor_destroyinfos) | - | Destroys the instance array and reclaims the memory. For details, see [Sensor_Info](capi-sensor-sensor-info.md).|
| [int32_t OH_SensorInfo_GetName(Sensor_Info* sensor, char *sensorName, uint32_t *length)](#oh_sensorinfo_getname) | - | Obtains the sensor name.|
| [int32_t OH_SensorInfo_GetVendorName(Sensor_Info* sensor, char *vendorName, uint32_t *length)](#oh_sensorinfo_getvendorname) | - | Obtains the sensor's vendor name.|
| [int32_t OH_SensorInfo_GetType(Sensor_Info* sensor, Sensor_Type *sensorType)](#oh_sensorinfo_gettype) | - | Obtains the sensor type.|
| [int32_t OH_SensorInfo_GetResolution(Sensor_Info* sensor, float *resolution)](#oh_sensorinfo_getresolution) | - | Obtains the sensor resolution.|
| [int32_t OH_SensorInfo_GetMinSamplingInterval(Sensor_Info* sensor, int64_t *minSamplingInterval)](#oh_sensorinfo_getminsamplinginterval) | - | Obtains the minimum data reporting interval of a sensor.|
| [int32_t OH_SensorInfo_GetMaxSamplingInterval(Sensor_Info* sensor, int64_t *maxSamplingInterval)](#oh_sensorinfo_getmaxsamplinginterval) | - | Obtains the maximum data reporting interval of a sensor.|
| [int32_t OH_SensorEvent_GetType(Sensor_Event* sensorEvent, Sensor_Type *sensorType)](#oh_sensorevent_gettype) | - | Obtains the sensor type.|
| [int32_t OH_SensorEvent_GetTimestamp(Sensor_Event* sensorEvent, int64_t *timestamp)](#oh_sensorevent_gettimestamp) | - | Obtains the timestamp of sensor data.|
| [int32_t OH_SensorEvent_GetAccuracy(Sensor_Event* sensorEvent, Sensor_Accuracy *accuracy)](#oh_sensorevent_getaccuracy) | - | Obtains the accuracy of sensor data.|
| [int32_t OH_SensorEvent_GetData(Sensor_Event* sensorEvent, float **data, uint32_t *length)](#oh_sensorevent_getdata) | - | Obtains sensor data. The data length and content depend on the sensor type. The format of the sensor data reported is as follows:<br> - SENSOR_TYPE_ACCELEROMETER: data[0], data[1], and data[2], indicating the acceleration around the x, y, and z axes of a device, respectively, in m/s². - SENSOR_TYPE_GYROSCOPE: data[0], data[1], and data[2], indicating the angular velocity of rotation around the x, y, and z axes of a device, respectively, in rad/s.<br> - SENSOR_TYPE_AMBIENT_LIGHT: data[0], indicating the ambient light intensity, in lux. Two additional data values are returned since API version 12. data[1] indicates the color temperature, in kelvin, and data[2] indicates the infrared luminance, in cd/m².<br> - SENSOR_TYPE_MAGNETIC_FIELD: data[0], data[1], and data[2], indicating the magnetic field strength around the x, y, and z axes of a device, respectively, in μT.<br> - SENSOR_TYPE_BAROMETER: data[0], indicating the atmospheric pressure, in hPa.<br> - SENSOR_TYPE_HALL: data[0], indicating the opening/closing state of the flip cover. The value **0** means that the flip cover is opened, and a value greater than 0 means that the flip cover is closed.<br> - SENSOR_TYPE_PROXIMITY: data[0], indicates the approaching state. The value **0** means the two objects are close to each other, and a value greater than 0 means that they are far away from each other.<br> - SENSOR_TYPE_ORIENTATION: data[0], data[1], and data[2], indicating the rotation angles of a device around the z, x, and y axes, respectively, in degree.<br> - SENSOR_TYPE_GRAVITY: data[0], data[1], and data[2], indicating the gravitational acceleration around the x, y, and z axes of a device, respectively, in m/s2.<br> - SENSOR_TYPE_ROTATION_VECTOR: data[0], data[1] and data[2], indicating the rotation angles of a device around the x, y, and z axes, respectively, in degree. data[3] indicates the rotation vector.<br> - SENSOR_TYPE_PEDOMETER_DETECTION: data[0], indicating the pedometer detection status. The value **1** means that the number of detected steps changes.<br> - SENSOR_TYPE_PEDOMETER: data[0], indicating the number of steps a user has walked.<br> - SENSOR_TYPE_HEART_RATE: data[0], indicating the heart rate value.<br> - SENSOR_TYPE_LINEAR_ACCELERATION: data[0], data[1], and data[2], indicating the linear acceleration of the device on the x, y, and z axes, respectively, in m/s2. This field is supported since API version 13.<br> - SENSOR_TYPE_GAME_ROTATION_VECTOR: data[0], data[1], and data[2], indicating the rotation angles of the device around the x, y, and z axes, respectively, in degree; data[3], indicating the rotation vector. This field is supported since API version 13.<br>|
| [Sensor_SubscriptionId *OH_Sensor_CreateSubscriptionId(void)](#oh_sensor_createsubscriptionid) | - | Creates a [Sensor_SubscriptionId](capi-sensor-sensor-subscriptionid.md) instance.|
| [int32_t OH_Sensor_DestroySubscriptionId(Sensor_SubscriptionId *id)](#oh_sensor_destroysubscriptionid) | - | Destroys a [Sensor_SubscriptionId](capi-sensor-sensor-subscriptionid.md) instance and reclaims the memory.|
| [int32_t OH_SensorSubscriptionId_GetType(Sensor_SubscriptionId* id, Sensor_Type *sensorType)](#oh_sensorsubscriptionid_gettype) | - | Obtains the sensor type.|
| [int32_t OH_SensorSubscriptionId_SetType(Sensor_SubscriptionId* id, const Sensor_Type sensorType)](#oh_sensorsubscriptionid_settype) | - | Sets the sensor type.|
| [Sensor_SubscriptionAttribute *OH_Sensor_CreateSubscriptionAttribute(void)](#oh_sensor_createsubscriptionattribute) | - | Creates a [Sensor_SubscriptionAttribute](capi-sensor-sensor-subscriptionattribute.md) instance.|
| [int32_t OH_Sensor_DestroySubscriptionAttribute(Sensor_SubscriptionAttribute *attribute)](#oh_sensor_destroysubscriptionattribute) | - | Destroys a [Sensor_SubscriptionAttribute](capi-sensor-sensor-subscriptionattribute.md) instance and reclaims the memory.|
| [int32_t OH_SensorSubscriptionAttribute_SetSamplingInterval(Sensor_SubscriptionAttribute* attribute, const int64_t samplingInterval)](#oh_sensorsubscriptionattribute_setsamplinginterval) | - | Sets the sensor data reporting interval.|
| [int32_t OH_SensorSubscriptionAttribute_GetSamplingInterval(Sensor_SubscriptionAttribute* attribute, int64_t *samplingInterval)](#oh_sensorsubscriptionattribute_getsamplinginterval) | - | Obtains the sensor data reporting interval.|
| [typedef void (\*Sensor_EventCallback)(Sensor_Event *event)](#sensor_eventcallback) | Sensor_EventCallback | Defines the callback function used to report sensor data.|
| [Sensor_Subscriber *OH_Sensor_CreateSubscriber(void)](#oh_sensor_createsubscriber) | - | Creates a [Sensor_Subscriber](capi-sensor-sensor-subscriber.md) instance.|
| [int32_t OH_Sensor_DestroySubscriber(Sensor_Subscriber *subscriber)](#oh_sensor_destroysubscriber) | - | Destroys a [Sensor_Subscriber](capi-sensor-sensor-subscriber.md) instance and reclaims the memory.|
| [int32_t OH_SensorSubscriber_SetCallback(Sensor_Subscriber* subscriber, const Sensor_EventCallback callback)](#oh_sensorsubscriber_setcallback) | - | Sets a callback function to report sensor data.|
| [int32_t OH_SensorSubscriber_GetCallback(Sensor_Subscriber* subscriber, Sensor_EventCallback *callback)](#oh_sensorsubscriber_getcallback) | - | Obtains the callback function used to report sensor data.|

## Enum Description

### Sensor_Type

```
enum Sensor_Type
```

**Description**

Enumerates the sensor types.

**Since**: 11

| Enum Item| Description|
| -- | -- |
| SENSOR_TYPE_ACCELEROMETER = 1 | Acceleration sensor.|
| SENSOR_TYPE_GYROSCOPE = 2 | Gyroscope sensor.|
| SENSOR_TYPE_AMBIENT_LIGHT = 5 | Ambient light sensor.|
| SENSOR_TYPE_MAGNETIC_FIELD = 6 | Magnetic field sensor.|
| SENSOR_TYPE_BAROMETER = 8 | Barometer sensor|
| SENSOR_TYPE_HALL = 10 | Hall effect sensor.|
| SENSOR_TYPE_PROXIMITY = 12 | Proximity sensor.|
| SENSOR_TYPE_ORIENTATION = 256 | Orientation sensor.|
| SENSOR_TYPE_GRAVITY = 257 | Gravity sensor.|
| SENSOR_TYPE_LINEAR_ACCELERATION = 258 | Linear acceleration sensor.|
| SENSOR_TYPE_ROTATION_VECTOR = 259 | Rotation vector sensor.|
| SENSOR_TYPE_GAME_ROTATION_VECTOR = 262 | Game rotation vector sensor|
| SENSOR_TYPE_PEDOMETER_DETECTION = 265 | Pedometer detection sensor.|
| SENSOR_TYPE_PEDOMETER = 266 | Pedometer sensor.|
| SENSOR_TYPE_HEART_RATE = 278 | Heart rate sensor.|

### Sensor_Result

```
enum Sensor_Result
```

**Description**

Enumerates the sensor result codes.

**Since**: 11

| Enum Item| Description|
| -- | -- |
| SENSOR_SUCCESS = 0 | Operation success.|
| SENSOR_PERMISSION_DENIED = 201 | Permission verification failed.|
| SENSOR_PARAMETER_ERROR = 401 | An error occurs during parameter verification. For example, a mandatory parameter is not passed in, or the parameter type passed in is incorrect.|
| SENSOR_SERVICE_EXCEPTION = 14500101 | The sensor service is abnormal.|

### Sensor_Accuracy

```
enum Sensor_Accuracy
```

**Description**

Enumerates the accuracy levels of data reported by a sensor.

**Since**: 11

| Enum Item| Description|
| -- | -- |
| SENSOR_ACCURACY_UNRELIABLE = 0 | The sensor data is unreliable. It is possible that the sensor does not contact with the device to measure.|
| SENSOR_ACCURACY_LOW = 1 | The sensor data is at a low accuracy level. The data must be calibrated based on the environment before being used.|
| SENSOR_ACCURACY_MEDIUM = 2 | The sensor data is at a medium accuracy level. You are advised to calibrate the data based on the environment before using it.|
| SENSOR_ACCURACY_HIGH = 3 | The sensor data is at a high accuracy level. The data can be used directly.|


## Function Description

### OH_Sensor_CreateInfos()

```
Sensor_Info **OH_Sensor_CreateInfos(uint32_t count)
```

**Description**

Creates an instance array using the given number. For details, see [Sensor_Info](capi-sensor-sensor-info.md).

**Since**: 11

**Parameters**

| Name| Description|
| -- | -- |
| uint32_t count | Number of instances to be created. For details, see [Sensor_Info](capi-sensor-sensor-info.md).|

**Returns**

| Type| Description|
| -- | -- |
| [Sensor_Info **](capi-sensor-sensor-info.md) | Double pointer to the [Sensor_Info](capi-sensor-sensor-info.md) instance array if the operation is successful; NULL otherwise.|

### OH_Sensor_DestroyInfos()

```
int32_t OH_Sensor_DestroyInfos(Sensor_Info **sensors, uint32_t count)
```

**Description**

Destroys the sensor instance array and reclaims the memory. For details, see [Sensor_Info](capi-sensor-sensor-info.md).

**Since**: 11

**Parameters**

| Name| Description|
| -- | -- |
| [Sensor_Info](capi-sensor-sensor-info.md) **sensors | Double pointer to the [Sensor_Info](capi-sensor-sensor-info.md) instance array.|
| uint32_t count | Number of [Sensor_Info](capi-sensor-sensor-info.md) instances to be destroyed.|

**Returns**

| Type| Description|
| -- | -- |
| int32_t | **SENSOR_SUCCESS** if the operation is successful; an error code defined in [Sensor_Result](capi-oh-sensor-type-h.md#sensor_result) otherwise. The error code can be:|

### OH_SensorInfo_GetName()

```
int32_t OH_SensorInfo_GetName(Sensor_Info* sensor, char *sensorName, uint32_t *length)
```

**Description**

Obtains the sensor name.

**Since**: 11

**Parameters**

| Name| Description|
| -- | -- |
| [Sensor_Info](capi-sensor-sensor-info.md)* sensor | Pointer to the sensor information.|
| char *sensorName | Pointer to the sensor data.|
| uint32_t *length | Pointer to the length, in bytes.|

**Returns**

| Type| Description|
| -- | -- |
| int32_t | **SENSOR_SUCCESS** if the operation is successful; an error code defined in [Sensor_Result](capi-oh-sensor-type-h.md#sensor_result) otherwise. The error code can be:|

### OH_SensorInfo_GetVendorName()

```
int32_t OH_SensorInfo_GetVendorName(Sensor_Info* sensor, char *vendorName, uint32_t *length)
```

**Description**

Obtains the sensor's vendor name.

**Since**: 11

**Parameters**

| Name| Description|
| -- | -- |
| [Sensor_Info](capi-sensor-sensor-info.md)* sensor | Pointer to the sensor information.|
| char *vendorName | Pointer to the vendor name.|
| uint32_t *length | Pointer to the length, in bytes.|

**Returns**

| Type| Description|
| -- | -- |
| int32_t | **SENSOR_SUCCESS** if the operation is successful; an error code defined in [Sensor_Result](capi-oh-sensor-type-h.md#sensor_result) otherwise. The error code can be:|

### OH_SensorInfo_GetType()

```
int32_t OH_SensorInfo_GetType(Sensor_Info* sensor, Sensor_Type *sensorType)
```

**Description**

Obtains the sensor type.

**Since**: 11

**Parameters**

| Name| Description|
| -- | -- |
| [Sensor_Info](capi-sensor-sensor-info.md)* sensor | Pointer to the sensor information.|
| [Sensor_Type](capi-oh-sensor-type-h.md#sensor_type) *sensorType | Pointer to the sensor type.|

**Returns**

| Type| Description|
| -- | -- |
| int32_t | **SENSOR_SUCCESS** if the operation is successful; an error code defined in [Sensor_Result](capi-oh-sensor-type-h.md#sensor_result) otherwise. The error code can be:|

### OH_SensorInfo_GetResolution()

```
int32_t OH_SensorInfo_GetResolution(Sensor_Info* sensor, float *resolution)
```

**Description**

Obtains the sensor resolution.

**Since**: 11

**Parameters**

| Name| Description|
| -- | -- |
| [Sensor_Info](capi-sensor-sensor-info.md)* sensor | Pointer to the sensor information.|
| float *resolution | Pointer to the sensor resolution.|

**Returns**

| Type| Description|
| -- | -- |
| int32_t | **SENSOR_SUCCESS** if the operation is successful; an error code defined in [Sensor_Result](capi-oh-sensor-type-h.md#sensor_result) otherwise. The error code can be:|

### OH_SensorInfo_GetMinSamplingInterval()

```
int32_t OH_SensorInfo_GetMinSamplingInterval(Sensor_Info* sensor, int64_t *minSamplingInterval)
```

**Description**

Obtains the minimum data reporting interval of a sensor.

**Since**: 11

**Parameters**

| Name| Description|
| -- | -- |
| [Sensor_Info](capi-sensor-sensor-info.md)* sensor | Pointer to the sensor information.|
| int64_t *minSamplingInterval | Pointer to the minimum data reporting interval, in nanoseconds.|

**Returns**

| Type| Description|
| -- | -- |
| int32_t | **SENSOR_SUCCESS** if the operation is successful; an error code defined in [Sensor_Result](capi-oh-sensor-type-h.md#sensor_result) otherwise. The error code can be:|

### OH_SensorInfo_GetMaxSamplingInterval()

```
int32_t OH_SensorInfo_GetMaxSamplingInterval(Sensor_Info* sensor, int64_t *maxSamplingInterval)
```

**Description**

Obtains the maximum data reporting interval of a sensor.

**Since**: 11

**Parameters**

| Name| Description|
| -- | -- |
| [Sensor_Info](capi-sensor-sensor-info.md)* sensor | Pointer to the sensor information.|
| int64_t *maxSamplingInterval | Pointer to the maximum data reporting interval, in nanoseconds.|

**Returns**

| Type| Description|
| -- | -- |
| int32_t | **SENSOR_SUCCESS** if the operation is successful; an error code defined in [Sensor_Result](capi-oh-sensor-type-h.md#sensor_result) otherwise. The error code can be:|

### OH_SensorEvent_GetType()

```
int32_t OH_SensorEvent_GetType(Sensor_Event* sensorEvent, Sensor_Type *sensorType)
```

**Description**

Obtains the sensor type.

**Since**: 11

**Parameters**

| Name| Description|
| -- | -- |
| [Sensor_Event](capi-sensor-sensor-event.md)* sensorEvent | Pointer to the sensor data information.|
| [Sensor_Type](capi-oh-sensor-type-h.md#sensor_type) *sensorType | Pointer to the sensor type.|

**Returns**

| Type| Description|
| -- | -- |
| int32_t | **SENSOR_SUCCESS** if the operation is successful; an error code defined in [Sensor_Result](capi-oh-sensor-type-h.md#sensor_result) otherwise. The error code can be:|

### OH_SensorEvent_GetTimestamp()

```
int32_t OH_SensorEvent_GetTimestamp(Sensor_Event* sensorEvent, int64_t *timestamp)
```

**Description**

Obtains the timestamp of sensor data.

**Since**: 11

**Parameters**

| Name| Description|
| -- | -- |
| [Sensor_Event](capi-sensor-sensor-event.md)* sensorEvent | Pointer to the sensor data information.|
| int64_t *timestamp | Pointer to the timestamp.|

**Returns**

| Type| Description|
| -- | -- |
| int32_t | **SENSOR_SUCCESS** if the operation is successful; an error code defined in [Sensor_Result](capi-oh-sensor-type-h.md#sensor_result) otherwise. The error code can be:|

### OH_SensorEvent_GetAccuracy()

```
int32_t OH_SensorEvent_GetAccuracy(Sensor_Event* sensorEvent, Sensor_Accuracy *accuracy)
```

**Description**

Obtains the accuracy of sensor data.

**Since**: 11

**Parameters**

| Name| Description|
| -- | -- |
| [Sensor_Event](capi-sensor-sensor-event.md)* sensorEvent | Pointer to the sensor data information.|
| [Sensor_Accuracy](capi-oh-sensor-type-h.md#sensor_accuracy) *accuracy | Pointer to the accuracy.|

**Returns**

| Type| Description|
| -- | -- |
| int32_t | **SENSOR_SUCCESS** if the operation is successful; an error code defined in [Sensor_Result](capi-oh-sensor-type-h.md#sensor_result) otherwise. The error code can be:|

### OH_SensorEvent_GetData()

```
int32_t OH_SensorEvent_GetData(Sensor_Event* sensorEvent, float **data, uint32_t *length)
```

**Description**

Obtains sensor data. The data length and content depend on the sensor type. The format of the sensor data reported is as follows:<br> - SENSOR_TYPE_ACCELEROMETER: data[0], data[1], and data[2], indicating the acceleration around the x, y, and z axes of a device, respectively, in m/s². - SENSOR_TYPE_GYROSCOPE: data[0], data[1], and data[2], indicating the angular velocity of rotation around the x, y, and z axes of a device, respectively, in rad/s.<br> - SENSOR_TYPE_AMBIENT_LIGHT: data[0], indicating the ambient light intensity, in lux. Two additional data values are returned since API version 12. data[1] indicates the color temperature, in kelvin, and data[2] indicates the infrared luminance, in cd/m².<br> - SENSOR_TYPE_MAGNETIC_FIELD: data[0], data[1], and data[2], indicating the magnetic field strength around the x, y, and z axes of a device, respectively, in μT.<br> - SENSOR_TYPE_BAROMETER: data[0], indicating the atmospheric pressure, in hPa.<br> - SENSOR_TYPE_HALL: data[0], indicating the opening/closing state of the flip cover. The value **0** means that the flip cover is opened, and a value greater than 0 means that the flip cover is closed.<br> - SENSOR_TYPE_PROXIMITY: data[0], indicates the approaching state. The value **0** means the two objects are close to each other, and a value greater than 0 means that they are far away from each other.<br> - SENSOR_TYPE_ORIENTATION: data[0], data[1], and data[2], indicating the rotation angles of a device around the z, x, and y axes, respectively, in degree.<br> - SENSOR_TYPE_GRAVITY: data[0], data[1], and data[2], indicating the gravitational acceleration around the x, y, and z axes of a device, respectively, in m/s2.<br> - SENSOR_TYPE_ROTATION_VECTOR: data[0], data[1] and data[2], indicating the rotation angles of a device around the x, y, and z axes, respectively, in degree. data[3] indicates the rotation vector.<br> - SENSOR_TYPE_PEDOMETER_DETECTION: data[0], indicating the pedometer detection status. The value **1** means that the number of detected steps changes.<br> - SENSOR_TYPE_PEDOMETER: data[0], indicating the number of steps a user has walked.<br> - SENSOR_TYPE_HEART_RATE: data[0], indicating the heart rate value.<br> - SENSOR_TYPE_LINEAR_ACCELERATION: data[0], data[1], and data[2], indicating the linear acceleration of the device on the x, y, and z axes, respectively, in m/s2. This field is supported since API version 13.<br> - SENSOR_TYPE_GAME_ROTATION_VECTOR: data[0], data[1], and data[2], indicating the rotation angles of the device around the x, y, and z axes, respectively, in degree; data[3], indicating the rotation vector. This field is supported since API version 13.<br>

**Since**: 11

**Parameters**

| Name| Description|
| -- | -- |
| [Sensor_Event](capi-sensor-sensor-event.md)* sensorEvent | Pointer to the sensor data information.|
| float **data | Double pointer to the sensor data.|
| uint32_t *length | Pointer to the array length.|

**Returns**

| Type| Description|
| -- | -- |
| int32_t | **SENSOR_SUCCESS** if the operation is successful; an error code defined in [Sensor_Result](capi-oh-sensor-type-h.md#sensor_result) otherwise. The error code can be:|

### OH_Sensor_CreateSubscriptionId()

```
Sensor_SubscriptionId *OH_Sensor_CreateSubscriptionId(void)
```

**Description**

Creates a [Sensor_SubscriptionId](capi-sensor-sensor-subscriptionid.md) instance.

**Since**: 11

**Returns**

| Type| Description|
| -- | -- |
| [Sensor_SubscriptionId *](capi-sensor-sensor-subscriptionid.md) | Pointer to the [Sensor_SubscriptionId](capi-sensor-sensor-subscriptionid.md) instance if the operation is successful; NULL otherwise.|

### OH_Sensor_DestroySubscriptionId()

```
int32_t OH_Sensor_DestroySubscriptionId(Sensor_SubscriptionId *id)
```

**Description**

Destroys a [Sensor_SubscriptionId](capi-sensor-sensor-subscriptionid.md) instance and reclaims the memory.

**Since**: 11

**Parameters**

| Name| Description|
| -- | -- |
| [Sensor_SubscriptionId](capi-sensor-sensor-subscriptionid.md) *id | Pointer to the [Sensor_SubscriptionId](capi-sensor-sensor-subscriptionid.md) instance.|

**Returns**

| Type| Description|
| -- | -- |
| int32_t | **SENSOR_SUCCESS** if the operation is successful; an error code defined in [Sensor_Result](capi-oh-sensor-type-h.md#sensor_result) otherwise. The error code can be:|

### OH_SensorSubscriptionId_GetType()

```
int32_t OH_SensorSubscriptionId_GetType(Sensor_SubscriptionId* id, Sensor_Type *sensorType)
```

**Description**

Obtains the sensor type.

**Since**: 11

**Parameters**

| Name| Description|
| -- | -- |
| [Sensor_SubscriptionId](capi-sensor-sensor-subscriptionid.md)* id | Pointer to the sensor subscription ID.|
| [Sensor_Type](capi-oh-sensor-type-h.md#sensor_type) *sensorType | Pointer to the sensor type.|

**Returns**

| Type| Description|
| -- | -- |
| int32_t | **SENSOR_SUCCESS** if the operation is successful; an error code defined in [Sensor_Result](capi-oh-sensor-type-h.md#sensor_result) otherwise. The error code can be:|

### OH_SensorSubscriptionId_SetType()

```
int32_t OH_SensorSubscriptionId_SetType(Sensor_SubscriptionId* id, const Sensor_Type sensorType)
```

**Description**

Sets the sensor type.

**Since**: 11

**Parameters**

| Name| Description|
| -- | -- |
| [Sensor_SubscriptionId](capi-sensor-sensor-subscriptionid.md)* id | Pointer to the sensor subscription ID.|
| [const Sensor_Type](capi-oh-sensor-type-h.md#sensor_type) sensorType | Sensor type to set.|

**Returns**

| Type| Description|
| -- | -- |
| int32_t | **SENSOR_SUCCESS** if the operation is successful; an error code defined in [Sensor_Result](capi-oh-sensor-type-h.md#sensor_result) otherwise.|

### OH_Sensor_CreateSubscriptionAttribute()

```
Sensor_SubscriptionAttribute *OH_Sensor_CreateSubscriptionAttribute(void)
```

**Description**

Creates a [Sensor_SubscriptionAttribute](capi-sensor-sensor-subscriptionattribute.md) instance.

**Since**: 11

**Returns**

| Type| Description|
| -- | -- |
| [Sensor_SubscriptionAttribute *](capi-sensor-sensor-subscriptionattribute.md) | Pointer to the [Sensor_SubscriptionAttribute](capi-sensor-sensor-subscriptionattribute.md) instance if the operation is successful; NULL otherwise.|

### OH_Sensor_DestroySubscriptionAttribute()

```
int32_t OH_Sensor_DestroySubscriptionAttribute(Sensor_SubscriptionAttribute *attribute)
```

**Description**

Destroys the [Sensor_SubscriptionAttribute](capi-sensor-sensor-subscriptionattribute.md) instance and reclaims the memory.

**Since**: 11

**Parameters**

| Name| Description|
| -- | -- |
| [Sensor_SubscriptionAttribute](capi-sensor-sensor-subscriptionattribute.md) *attribute | Pointer to the [Sensor_SubscriptionAttribute](capi-sensor-sensor-subscriptionattribute.md) instance.|

**Returns**

| Type| Description|
| -- | -- |
| int32_t | **SENSOR_SUCCESS** if the operation is successful; an error code defined in [Sensor_Result](capi-oh-sensor-type-h.md#sensor_result) otherwise.|

### OH_SensorSubscriptionAttribute_SetSamplingInterval()

```
int32_t OH_SensorSubscriptionAttribute_SetSamplingInterval(Sensor_SubscriptionAttribute* attribute, const int64_t samplingInterval)
```

**Description**

Sets the sensor data reporting interval.

**Since**: 11

**Parameters**

| Name| Description|
| -- | -- |
| [Sensor_SubscriptionAttribute](capi-sensor-sensor-subscriptionattribute.md)* attribute | Pointer to the sensor subscription attribute.|
| const int64_t samplingInterval | Data reporting interval to set, in nanoseconds.|

**Returns**

| Type| Description|
| -- | -- |
| int32_t | **SENSOR_SUCCESS** if the operation is successful; an error code defined in [Sensor_Result](capi-oh-sensor-type-h.md#sensor_result) otherwise. The error code can be:|

### OH_SensorSubscriptionAttribute_GetSamplingInterval()

```
int32_t OH_SensorSubscriptionAttribute_GetSamplingInterval(Sensor_SubscriptionAttribute* attribute, int64_t *samplingInterval)
```

**Description**

Obtains the sensor data reporting interval.

**Since**: 11

**Parameters**

| Name| Description|
| -- | -- |
| [Sensor_SubscriptionAttribute](capi-sensor-sensor-subscriptionattribute.md)* attribute | Pointer to the sensor subscription attribute.|
| int64_t *samplingInterval | Pointer to the data reporting interval, in nanoseconds.|

**Returns**

| Type| Description|
| -- | -- |
| int32_t | **SENSOR_SUCCESS** if the operation is successful; an error code defined in [Sensor_Result](capi-oh-sensor-type-h.md#sensor_result) otherwise. The error code can be:|

### Sensor_EventCallback()

```
typedef void (*Sensor_EventCallback)(Sensor_Event *event)
```

**Description**

Defines the callback function used to report sensor data.

**Since**: 11

### OH_Sensor_CreateSubscriber()

```
Sensor_Subscriber *OH_Sensor_CreateSubscriber(void)
```

**Description**

Creates a [Sensor_Subscriber](capi-sensor-sensor-subscriber.md) instance.

**Since**: 11

**Returns**

| Type| Description|
| -- | -- |
| [Sensor_Subscriber *](capi-sensor-sensor-subscriber.md) | Pointer to the [Sensor_Subscriber](capi-sensor-sensor-subscriber.md) instance if the operation is successful; NULL otherwise.|

### OH_Sensor_DestroySubscriber()

```
int32_t OH_Sensor_DestroySubscriber(Sensor_Subscriber *subscriber)
```

**Description**

Destroys a [Sensor_Subscriber](capi-sensor-sensor-subscriber.md) instance and reclaims the memory.

**Since**: 11

**Parameters**

| Name| Description|
| -- | -- |
| [Sensor_Subscriber](capi-sensor-sensor-subscriber.md) *subscriber | Pointer to the [Sensor_Subscriber](capi-sensor-sensor-subscriber.md) instance.|

**Returns**

| Type| Description|
| -- | -- |
| int32_t | **SENSOR_SUCCESS** if the operation is successful; an error code defined in [Sensor_Result](capi-oh-sensor-type-h.md#sensor_result) otherwise.|

### OH_SensorSubscriber_SetCallback()

```
int32_t OH_SensorSubscriber_SetCallback(Sensor_Subscriber* subscriber, const Sensor_EventCallback callback)
```

**Description**

Sets a callback function to report sensor data.

**Since**: 11

**Parameters**

| Name| Description|
| -- | -- |
| [Sensor_Subscriber](capi-sensor-sensor-subscriber.md)* subscriber | Pointer to the sensor subscriber information.|
| [const Sensor_EventCallback](capi-oh-sensor-type-h.md#sensor_eventcallback) callback | Sets the callback function.|

**Returns**

| Type| Description|
| -- | -- |
| int32_t | **SENSOR_SUCCESS** if the operation is successful; an error code defined in [Sensor_Result](capi-oh-sensor-type-h.md#sensor_result) otherwise. The error code can be:|

### OH_SensorSubscriber_GetCallback()

```
int32_t OH_SensorSubscriber_GetCallback(Sensor_Subscriber* subscriber, Sensor_EventCallback *callback)
```

**Description**

Obtains the callback function used to report sensor data.

**Since**: 11

**Parameters**

| Name| Description|
| -- | -- |
| [Sensor_Subscriber](capi-sensor-sensor-subscriber.md)* subscriber | Pointer to the sensor subscriber information.|
| [Sensor_EventCallback](capi-oh-sensor-type-h.md#sensor_eventcallback) *callback | Pointer to the callback function.|

**Returns**

| Type| Description|
| -- | -- |
| int32_t | **SENSOR_SUCCESS** if the operation is successful; an error code defined in [Sensor_Result](capi-oh-sensor-type-h.md#sensor_result) otherwise. The error code can be:|
