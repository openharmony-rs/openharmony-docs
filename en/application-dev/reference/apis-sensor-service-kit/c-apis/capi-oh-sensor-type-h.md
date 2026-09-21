# oh_sensor_type.h

## Overview

Declares the common sensor attributes.

**Library**: libohsensor.so

**System capability**: SystemCapability.Sensors.Sensor

**Since**: 11

**Related module**: [Sensor](capi-sensor.md)

## Summary

### Struct

| Name | typedef keyword | Description |
| -- | -- | -- |
| [Sensor_Info](capi-sensor-sensor-info.md) | Sensor_Info | Defines a struct for the sensor information. |
| [Sensor_Event](capi-sensor-sensor-event.md) | Sensor_Event | Defines a struct for the sensor data information. |
| [Sensor_SubscriptionId](capi-sensor-sensor-subscriptionid.md) | Sensor_SubscriptionId | Defines a struct for the sensor subscription ID, which uniquely identifies a sensor. |
| [Sensor_SubscriptionAttribute](capi-sensor-sensor-subscriptionattribute.md) | Sensor_SubscriptionAttribute | Defines a struct for the sensor subscription attribute. |
| [Sensor_Subscriber](capi-sensor-sensor-subscriber.md) | Sensor_Subscriber | Defines a struct the sensor subscriber information. |

### Enum

| Name | typedef keyword | Description |
| -- | -- | -- |
| [Sensor_Type](#sensor_type) | Sensor_Type | Enumerates the sensor types. |
| [Sensor_Result](#sensor_result) | Sensor_Result | Enumerates the sensor result codes. |
| [Sensor_Accuracy](#sensor_accuracy) | Sensor_Accuracy | Enumerates the accuracy levels of data reported by a sensor. |

### Function

| Name | typedef keyword | Description |
| -- | -- | -- |
| [Sensor_Info **OH_Sensor_CreateInfos(uint32_t count)](#oh_sensor_createinfos) | - | Creates an instance array using a given number. For details, see [Sensor_Info](capi-sensor-sensor-info.md). |
| [int32_t OH_Sensor_DestroyInfos(Sensor_Info **sensors, uint32_t count)](#oh_sensor_destroyinfos) | - | Destroys the sensor instance array and reclaims the memory. For details, see [Sensor_Info](capi-sensor-sensor-info.md). |
| [int32_t OH_SensorInfo_GetName(Sensor_Info* sensor, char *sensorName, uint32_t *length)](#oh_sensorinfo_getname) | - | Obtains the sensor name. |
| [int32_t OH_SensorInfo_GetVendorName(Sensor_Info* sensor, char *vendorName, uint32_t *length)](#oh_sensorinfo_getvendorname) | - | Obtains the sensor's vendor name. |
| [int32_t OH_SensorInfo_GetType(Sensor_Info* sensor, Sensor_Type *sensorType)](#oh_sensorinfo_gettype) | - | Obtains the sensor type. |
| [int32_t OH_SensorInfo_GetResolution(Sensor_Info* sensor, float *resolution)](#oh_sensorinfo_getresolution) | - | Obtains the sensor resolution. |
| [int32_t OH_SensorInfo_GetMinSamplingInterval(Sensor_Info* sensor, int64_t *minSamplingInterval)](#oh_sensorinfo_getminsamplinginterval) | - | Obtains the minimum data reporting interval of a sensor. |
| [int32_t OH_SensorInfo_GetMaxSamplingInterval(Sensor_Info* sensor, int64_t *maxSamplingInterval)](#oh_sensorinfo_getmaxsamplinginterval) | - | Obtains the maximum data reporting interval of a sensor. |
| [int32_t OH_SensorEvent_GetType(Sensor_Event* sensorEvent, Sensor_Type *sensorType)](#oh_sensorevent_gettype) | - | Obtains the sensor type. |
| [int32_t OH_SensorEvent_GetTimestamp(Sensor_Event* sensorEvent, int64_t *timestamp)](#oh_sensorevent_gettimestamp) | - | Obtains the timestamp of sensor data. |
| [int32_t OH_SensorEvent_GetAccuracy(Sensor_Event* sensorEvent, Sensor_Accuracy *accuracy)](#oh_sensorevent_getaccuracy) | - | Obtains the accuracy of sensor data. |
| [int32_t OH_SensorEvent_GetData(Sensor_Event* sensorEvent, float **data, uint32_t *length)](#oh_sensorevent_getdata) | - | Obtains sensor data. The data length and content depend on the sensor type. The format of the sensor data reported is as follows: SENSOR_TYPE_ACCELEROMETER: data[0], data[1], and data[2], indicating the acceleration around the x, y, and z axes of the device, respectively, in m/s2. SENSOR_TYPE_GYROSCOPE: data[0], data[1], and data[2], indicating the angular velocity of rotation around the x, y, and z axes of the device, respectively, in rad/s. SENSOR_TYPE_AMBIENT_LIGHT: data[0], indicating the ambient light intensity, in lux. Since api version 12, two additional data will be returned, where data[1] indicating the color temperature, in kelvin; data[2] indicating the infrared luminance, in cd/m2. SENSOR_TYPE_MAGNETIC_FIELD: data[0], data[1], and data[2], indicating the magnetic field strength around the x, y, and z axes of the device, respectively, in μT. SENSOR_TYPE_BAROMETER: data[0], indicating the atmospheric pressure, in hPa. SENSOR_TYPE_HALL: data[0], indicating the opening/closing state of the flip cover. The value <b>0</b> means that the flip cover is opened, and a value greater than <b>0</b> means that the flip cover is closed. SENSOR_TYPE_PROXIMITY: data[0], indicates the approaching state. The value <b>0</b> means the two objects are close to each other, and a value greater than <b>0</b> means that they are far away from each other. SENSOR_TYPE_ORIENTATION: data[0], data[1], and data[2], indicating the rotation angles of a device around the z, x, and y axes, respectively, in degree. SENSOR_TYPE_GRAVITY: data[0], data[1], and data[2], indicating the gravitational acceleration around the x, y, and z axes of a device, respectively, in m/s2. SENSOR_TYPE_ROTATION_VECTOR: data[0], data[1] and data[2], indicating the rotation angles of a device around the x, y, and z axes, respectively, in degree. data[3] indicates the rotation vector. SENSOR_TYPE_PEDOMETER_DETECTION: data[0], indicating the pedometer detection status. The value <b>1</b> means that the number of detected steps changes. SENSOR_TYPE_PEDOMETER: data[0], indicating the number of steps a user has walked. SENSOR_TYPE_HEART_RATE: data[0], indicating the heart rate value. SENSOR_TYPE_LINEAR_ACCELERATION: Supported from api version 13. data[0], data[1], and data[2], indicating the linear acceleration around the x, y, and z axes of the device, respectively, in m/s2. SENSOR_TYPE_GAME_ROTATION_VECTOR: Supported from api version 13. data[0], data[1] and data[2], indicating the rotation angles of a device around the x, y, and z axes, respectively, in degree. data[3] indicates the rotation vector. |
| [Sensor_SubscriptionId *OH_Sensor_CreateSubscriptionId(void)](#oh_sensor_createsubscriptionid) | - | Creates a [Sensor_SubscriptionId](capi-sensor-sensor-subscriptionid.md) instance. |
| [int32_t OH_Sensor_DestroySubscriptionId(Sensor_SubscriptionId *id)](#oh_sensor_destroysubscriptionid) | - | Destroys a [Sensor_SubscriptionId](capi-sensor-sensor-subscriptionid.md) instance and reclaims the memory. |
| [int32_t OH_SensorSubscriptionId_GetType(Sensor_SubscriptionId* id, Sensor_Type *sensorType)](#oh_sensorsubscriptionid_gettype) | - | Obtains the sensor type. |
| [int32_t OH_SensorSubscriptionId_SetType(Sensor_SubscriptionId* id, const Sensor_Type sensorType)](#oh_sensorsubscriptionid_settype) | - | Sets the sensor type. |
| [Sensor_SubscriptionAttribute *OH_Sensor_CreateSubscriptionAttribute(void)](#oh_sensor_createsubscriptionattribute) | - | Creates a [Sensor_SubscriptionAttribute](capi-sensor-sensor-subscriptionattribute.md) instance. |
| [int32_t OH_Sensor_DestroySubscriptionAttribute(Sensor_SubscriptionAttribute *attribute)](#oh_sensor_destroysubscriptionattribute) | - | Destroys a [Sensor_SubscriptionAttribute](capi-sensor-sensor-subscriptionattribute.md) instance and reclaims the memory. |
| [int32_t OH_SensorSubscriptionAttribute_SetSamplingInterval(Sensor_SubscriptionAttribute* attribute, const int64_t samplingInterval)](#oh_sensorsubscriptionattribute_setsamplinginterval) | - | Sets the sensor data reporting interval. |
| [int32_t OH_SensorSubscriptionAttribute_GetSamplingInterval(Sensor_SubscriptionAttribute* attribute, int64_t *samplingInterval)](#oh_sensorsubscriptionattribute_getsamplinginterval) | - | Obtains the sensor data reporting interval. |
| [typedef void (\*Sensor_EventCallback)(Sensor_Event *event)](#sensor_eventcallback) | Sensor_EventCallback | Defines the callback function used to report sensor data. |
| [Sensor_Subscriber *OH_Sensor_CreateSubscriber(void)](#oh_sensor_createsubscriber) | - | Creates a [Sensor_Subscriber](capi-sensor-sensor-subscriber.md) instance. |
| [int32_t OH_Sensor_DestroySubscriber(Sensor_Subscriber *subscriber)](#oh_sensor_destroysubscriber) | - | Destroys a [Sensor_Subscriber](capi-sensor-sensor-subscriber.md) instance and reclaims the memory. |
| [int32_t OH_SensorSubscriber_SetCallback(Sensor_Subscriber* subscriber, const Sensor_EventCallback callback)](#oh_sensorsubscriber_setcallback) | - | Sets a callback function to report sensor data. |
| [int32_t OH_SensorSubscriber_GetCallback(Sensor_Subscriber* subscriber, Sensor_EventCallback *callback)](#oh_sensorsubscriber_getcallback) | - | Obtains the callback function used to report sensor data. |

### Variable

| Name | Description |
| -- | -- |
| void (*Sensor_EventCallback)(Sensor_Event *event) | Defines the callback function used to report sensor data.<br>**Since**: 11 |

## Enum type description

### Sensor_Type

```c
enum Sensor_Type
```

**Description**

Enumerates the sensor types.

**System capability**: SystemCapability.Sensors.Sensor

**Since**: 11

| Enum item | Description |
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

**Description**

Enumerates the sensor result codes.

**System capability**: SystemCapability.Sensors.Sensor

**Since**: 11

| Enum item | Description |
| -- | -- |
| SENSOR_SUCCESS = 0 |  |
| SENSOR_PERMISSION_DENIED = 201 |  |
| SENSOR_PARAMETER_ERROR = 401 |  |
| SENSOR_SERVICE_EXCEPTION = 14500101 |  |

### Sensor_Accuracy

```c
enum Sensor_Accuracy
```

**Description**

Enumerates the accuracy levels of data reported by a sensor.

**System capability**: SystemCapability.Sensors.Sensor

**Since**: 11

| Enum item | Description |
| -- | -- |
| SENSOR_ACCURACY_UNRELIABLE = 0 |  |
| SENSOR_ACCURACY_LOW = 1 |  |
| SENSOR_ACCURACY_MEDIUM = 2 |  |
| SENSOR_ACCURACY_HIGH = 3 |  |


## Function description

### OH_Sensor_CreateInfos()

```c
Sensor_Info **OH_Sensor_CreateInfos(uint32_t count)
```

**Description**

Creates an instance array using a given number. For details, see [Sensor_Info](capi-sensor-sensor-info.md).

**System capability**: SystemCapability.Sensors.Sensor

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| uint32_t count | Number of instances to be created. For details, see [Sensor_Info](capi-sensor-sensor-info.md). |

**Returns**:

| Type | Description |
| -- | -- |
| [Sensor_Info **](capi-sensor-sensor-info.md) | Double pointer to the [Sensor_Info](capi-sensor-sensor-info.md) instance array if the operation is successful; NULL otherwise. |

### OH_Sensor_DestroyInfos()

```c
int32_t OH_Sensor_DestroyInfos(Sensor_Info **sensors, uint32_t count)
```

**Description**

Destroys the sensor instance array and reclaims the memory. For details, see [Sensor_Info](capi-sensor-sensor-info.md).

**System capability**: SystemCapability.Sensors.Sensor

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| [Sensor_Info](capi-sensor-sensor-info.md) **sensors | Double pointer to the [Sensor_Info](capi-sensor-sensor-info.md) instance array. |
| uint32_t count | Number of [Sensor_Info](capi-sensor-sensor-info.md) instances to be destroyed. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | SENSOR_SUCCESS if the operation is successful; an error code defined in [Sensor_Result](capi-oh-sensor-type-h.md#sensor_result) otherwise. |

### OH_SensorInfo_GetName()

```c
int32_t OH_SensorInfo_GetName(Sensor_Info* sensor, char *sensorName, uint32_t *length)
```

**Description**

Obtains the sensor name.

**System capability**: SystemCapability.Sensors.Sensor

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| [Sensor_Info](capi-sensor-sensor-info.md)* sensor | Pointer to the sensor information. |
| char *sensorName | Pointer to the sensor data. |
| uint32_t *length | Pointer to the length, in bytes. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | SENSOR_SUCCESS if the operation is successful; an error code defined in [Sensor_Result](capi-oh-sensor-type-h.md#sensor_result) otherwise. |

### OH_SensorInfo_GetVendorName()

```c
int32_t OH_SensorInfo_GetVendorName(Sensor_Info* sensor, char *vendorName, uint32_t *length)
```

**Description**

Obtains the sensor's vendor name.

**System capability**: SystemCapability.Sensors.Sensor

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| [Sensor_Info](capi-sensor-sensor-info.md)* sensor | Pointer to the sensor information. |
| char *vendorName | Pointer to the vendor name. |
| uint32_t *length | Pointer to the length, in bytes. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | SENSOR_SUCCESS if the operation is successful; an error code defined in [Sensor_Result](capi-oh-sensor-type-h.md#sensor_result) otherwise. |

### OH_SensorInfo_GetType()

```c
int32_t OH_SensorInfo_GetType(Sensor_Info* sensor, Sensor_Type *sensorType)
```

**Description**

Obtains the sensor type.

**System capability**: SystemCapability.Sensors.Sensor

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| [Sensor_Info](capi-sensor-sensor-info.md)* sensor | Pointer to the sensor information. |
| [Sensor_Type](capi-oh-sensor-type-h.md#sensor_type) *sensorType | Pointer to the sensor type. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | SENSOR_SUCCESS if the operation is successful; an error code defined in [Sensor_Result](capi-oh-sensor-type-h.md#sensor_result) otherwise. |

### OH_SensorInfo_GetResolution()

```c
int32_t OH_SensorInfo_GetResolution(Sensor_Info* sensor, float *resolution)
```

**Description**

Obtains the sensor resolution.

**System capability**: SystemCapability.Sensors.Sensor

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| [Sensor_Info](capi-sensor-sensor-info.md)* sensor | Pointer to the sensor information. |
| float *resolution | Pointer to the sensor resolution [Sensor_Accuracy](capi-oh-sensor-type-h.md#sensor_accuracy). |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | SENSOR_SUCCESS if the operation is successful; an error code defined in [Sensor_Result](capi-oh-sensor-type-h.md#sensor_result) otherwise. |

### OH_SensorInfo_GetMinSamplingInterval()

```c
int32_t OH_SensorInfo_GetMinSamplingInterval(Sensor_Info* sensor, int64_t *minSamplingInterval)
```

**Description**

Obtains the minimum data reporting interval of a sensor.

**System capability**: SystemCapability.Sensors.Sensor

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| [Sensor_Info](capi-sensor-sensor-info.md)* sensor | Pointer to the sensor information. |
| int64_t *minSamplingInterval | Pointer to the minimum data reporting interval, in nanoseconds. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | SENSOR_SUCCESS if the operation is successful; an error code defined in [Sensor_Result](capi-oh-sensor-type-h.md#sensor_result) otherwise. |

### OH_SensorInfo_GetMaxSamplingInterval()

```c
int32_t OH_SensorInfo_GetMaxSamplingInterval(Sensor_Info* sensor, int64_t *maxSamplingInterval)
```

**Description**

Obtains the maximum data reporting interval of a sensor.

**System capability**: SystemCapability.Sensors.Sensor

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| [Sensor_Info](capi-sensor-sensor-info.md)* sensor | Pointer to the sensor information. |
| int64_t *maxSamplingInterval | Pointer to the maximum data reporting interval, in nanoseconds. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | SENSOR_SUCCESS if the operation is successful; an error code defined in [Sensor_Result](capi-oh-sensor-type-h.md#sensor_result) otherwise. |

### OH_SensorEvent_GetType()

```c
int32_t OH_SensorEvent_GetType(Sensor_Event* sensorEvent, Sensor_Type *sensorType)
```

**Description**

Obtains the sensor type.

**System capability**: SystemCapability.Sensors.Sensor

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| [Sensor_Event](capi-sensor-sensor-event.md)* sensorEvent | Pointer to the sensor data information. |
| [Sensor_Type](capi-oh-sensor-type-h.md#sensor_type) *sensorType | Pointer to the sensor type. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | SENSOR_SUCCESS if the operation is successful; an error code defined in [Sensor_Result](capi-oh-sensor-type-h.md#sensor_result) otherwise. |

### OH_SensorEvent_GetTimestamp()

```c
int32_t OH_SensorEvent_GetTimestamp(Sensor_Event* sensorEvent, int64_t *timestamp)
```

**Description**

Obtains the timestamp of sensor data.

**System capability**: SystemCapability.Sensors.Sensor

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| [Sensor_Event](capi-sensor-sensor-event.md)* sensorEvent | Pointer to the sensor data information. |
| int64_t *timestamp | Pointer to the timestamp. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | SENSOR_SUCCESS if the operation is successful; an error code defined in [Sensor_Result](capi-oh-sensor-type-h.md#sensor_result) otherwise. |

### OH_SensorEvent_GetAccuracy()

```c
int32_t OH_SensorEvent_GetAccuracy(Sensor_Event* sensorEvent, Sensor_Accuracy *accuracy)
```

**Description**

Obtains the accuracy of sensor data.

**System capability**: SystemCapability.Sensors.Sensor

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| [Sensor_Event](capi-sensor-sensor-event.md)* sensorEvent | Pointer to the sensor data information. |
| [Sensor_Accuracy](capi-oh-sensor-type-h.md#sensor_accuracy) *accuracy | Pointer to the accuracy. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | SENSOR_SUCCESS if the operation is successful; an error code defined in [Sensor_Result](capi-oh-sensor-type-h.md#sensor_result) otherwise. |

### OH_SensorEvent_GetData()

```c
int32_t OH_SensorEvent_GetData(Sensor_Event* sensorEvent, float **data, uint32_t *length)
```

**Description**

Obtains sensor data. The data length and content depend on the sensor type. The format of the sensor data reported is as follows: SENSOR_TYPE_ACCELEROMETER: data[0], data[1], and data[2], indicating the acceleration around the x, y, and z axes of the device, respectively, in m/s2. SENSOR_TYPE_GYROSCOPE: data[0], data[1], and data[2], indicating the angular velocity of rotation around the x, y, and z axes of the device, respectively, in rad/s. SENSOR_TYPE_AMBIENT_LIGHT: data[0], indicating the ambient light intensity, in lux. Since api version 12, two additional data will be returned, where data[1] indicating the color temperature, in kelvin; data[2] indicating the infrared luminance, in cd/m2. SENSOR_TYPE_MAGNETIC_FIELD: data[0], data[1], and data[2], indicating the magnetic field strength around the x, y, and z axes of the device, respectively, in μT. SENSOR_TYPE_BAROMETER: data[0], indicating the atmospheric pressure, in hPa. SENSOR_TYPE_HALL: data[0], indicating the opening/closing state of the flip cover. The value <b>0</b> means that the flip cover is opened, and a value greater than <b>0</b> means that the flip cover is closed. SENSOR_TYPE_PROXIMITY: data[0], indicates the approaching state. The value <b>0</b> means the two objects are close to each other, and a value greater than <b>0</b> means that they are far away from each other. SENSOR_TYPE_ORIENTATION: data[0], data[1], and data[2], indicating the rotation angles of a device around the z, x, and y axes, respectively, in degree. SENSOR_TYPE_GRAVITY: data[0], data[1], and data[2], indicating the gravitational acceleration around the x, y, and z axes of a device, respectively, in m/s2. SENSOR_TYPE_ROTATION_VECTOR: data[0], data[1] and data[2], indicating the rotation angles of a device around the x, y, and z axes, respectively, in degree. data[3] indicates the rotation vector. SENSOR_TYPE_PEDOMETER_DETECTION: data[0], indicating the pedometer detection status. The value <b>1</b> means that the number of detected steps changes. SENSOR_TYPE_PEDOMETER: data[0], indicating the number of steps a user has walked. SENSOR_TYPE_HEART_RATE: data[0], indicating the heart rate value. SENSOR_TYPE_LINEAR_ACCELERATION: Supported from api version 13. data[0], data[1], and data[2], indicating the linear acceleration around the x, y, and z axes of the device, respectively, in m/s2. SENSOR_TYPE_GAME_ROTATION_VECTOR: Supported from api version 13. data[0], data[1] and data[2], indicating the rotation angles of a device around the x, y, and z axes, respectively, in degree. data[3] indicates the rotation vector.

**System capability**: SystemCapability.Sensors.Sensor

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| [Sensor_Event](capi-sensor-sensor-event.md)* sensorEvent | - Pointer to the sensor data information. |
| float **data | - Double pointer to the sensor data. |
| uint32_t *length | - Pointer to the array length. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Returns <b>SENSOR_SUCCESS</b> if the operation is successful;  returns an error code defined in [Sensor_Result](capi-oh-sensor-type-h.md#sensor_result) otherwise. |

### OH_Sensor_CreateSubscriptionId()

```c
Sensor_SubscriptionId *OH_Sensor_CreateSubscriptionId(void)
```

**Description**

Creates a [Sensor_SubscriptionId](capi-sensor-sensor-subscriptionid.md) instance.

**System capability**: SystemCapability.Sensors.Sensor

**Since**: 11

**Returns**:

| Type | Description |
| -- | -- |
| [Sensor_SubscriptionId *](capi-sensor-sensor-subscriptionid.md) | Pointer to the [Sensor_SubscriptionId](capi-sensor-sensor-subscriptionid.md) instance if the operation is successful; NULL otherwise. |

### OH_Sensor_DestroySubscriptionId()

```c
int32_t OH_Sensor_DestroySubscriptionId(Sensor_SubscriptionId *id)
```

**Description**

Destroys a [Sensor_SubscriptionId](capi-sensor-sensor-subscriptionid.md) instance and reclaims the memory.

**System capability**: SystemCapability.Sensors.Sensor

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| [Sensor_SubscriptionId](capi-sensor-sensor-subscriptionid.md) *id | Pointer to the [Sensor_SubscriptionId](capi-sensor-sensor-subscriptionid.md) instance. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | SENSOR_SUCCESS if the operation is successful; an error code defined in [Sensor_Result](capi-oh-sensor-type-h.md#sensor_result) otherwise. |

### OH_SensorSubscriptionId_GetType()

```c
int32_t OH_SensorSubscriptionId_GetType(Sensor_SubscriptionId* id, Sensor_Type *sensorType)
```

**Description**

Obtains the sensor type.

**System capability**: SystemCapability.Sensors.Sensor

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| [Sensor_SubscriptionId](capi-sensor-sensor-subscriptionid.md)* id | Pointer to the sensor subscription ID. |
| [Sensor_Type](capi-oh-sensor-type-h.md#sensor_type) *sensorType | Pointer to the sensor type. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | SENSOR_SUCCESS if the operation is successful; an error code defined in [Sensor_Result](capi-oh-sensor-type-h.md#sensor_result) otherwise. |

### OH_SensorSubscriptionId_SetType()

```c
int32_t OH_SensorSubscriptionId_SetType(Sensor_SubscriptionId* id, const Sensor_Type sensorType)
```

**Description**

Sets the sensor type.

**System capability**: SystemCapability.Sensors.Sensor

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| [Sensor_SubscriptionId](capi-sensor-sensor-subscriptionid.md)* id | Pointer to the sensor subscription ID. |
| [const Sensor_Type](capi-oh-sensor-type-h.md#sensor_type) sensorType | Sensor type to set. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | SENSOR_SUCCESS if the operation is successful; an error code defined in [Sensor_Result](capi-oh-sensor-type-h.md#sensor_result) otherwise. |

### OH_Sensor_CreateSubscriptionAttribute()

```c
Sensor_SubscriptionAttribute *OH_Sensor_CreateSubscriptionAttribute(void)
```

**Description**

Creates a [Sensor_SubscriptionAttribute](capi-sensor-sensor-subscriptionattribute.md) instance.

**System capability**: SystemCapability.Sensors.Sensor

**Since**: 11

**Returns**:

| Type | Description |
| -- | -- |
| [Sensor_SubscriptionAttribute *](capi-sensor-sensor-subscriptionattribute.md) | Pointer to the [Sensor_SubscriptionAttribute](capi-sensor-sensor-subscriptionattribute.md) instance if the operation is successful; NULL  otherwise. |

### OH_Sensor_DestroySubscriptionAttribute()

```c
int32_t OH_Sensor_DestroySubscriptionAttribute(Sensor_SubscriptionAttribute *attribute)
```

**Description**

Destroys a [Sensor_SubscriptionAttribute](capi-sensor-sensor-subscriptionattribute.md) instance and reclaims the memory.

**System capability**: SystemCapability.Sensors.Sensor

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| [Sensor_SubscriptionAttribute](capi-sensor-sensor-subscriptionattribute.md) *attribute | Pointer to the [Sensor_SubscriptionAttribute](capi-sensor-sensor-subscriptionattribute.md) instance. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | SENSOR_SUCCESS if the operation is successful; an error code defined in [Sensor_Result](capi-oh-sensor-type-h.md#sensor_result) otherwise. |

### OH_SensorSubscriptionAttribute_SetSamplingInterval()

```c
int32_t OH_SensorSubscriptionAttribute_SetSamplingInterval(Sensor_SubscriptionAttribute* attribute, const int64_t samplingInterval)
```

**Description**

Sets the sensor data reporting interval.

**System capability**: SystemCapability.Sensors.Sensor

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| [Sensor_SubscriptionAttribute](capi-sensor-sensor-subscriptionattribute.md)* attribute | Pointer to the sensor subscription attribute. |
| const int64_t samplingInterval | Data reporting interval to set, in nanoseconds. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | SENSOR_SUCCESS if the operation is successful; an error code defined in [Sensor_Result](capi-oh-sensor-type-h.md#sensor_result) otherwise. |

### OH_SensorSubscriptionAttribute_GetSamplingInterval()

```c
int32_t OH_SensorSubscriptionAttribute_GetSamplingInterval(Sensor_SubscriptionAttribute* attribute, int64_t *samplingInterval)
```

**Description**

Obtains the sensor data reporting interval.

**System capability**: SystemCapability.Sensors.Sensor

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| [Sensor_SubscriptionAttribute](capi-sensor-sensor-subscriptionattribute.md)* attribute | Pointer to the sensor subscription attribute. |
| int64_t *samplingInterval | Pointer to the data reporting interval, in nanoseconds. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | SENSOR_SUCCESS if the operation is successful; an error code defined in [Sensor_Result](capi-oh-sensor-type-h.md#sensor_result) otherwise. |

### Sensor_EventCallback()

```c
typedef void (*Sensor_EventCallback)(Sensor_Event *event)
```

**Description**

Defines the callback function used to report sensor data.

**System capability**: SystemCapability.Sensors.Sensor

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| [Sensor_Event](capi-sensor-sensor-event.md) \*event | Pointer to the sensor data information. |

### OH_Sensor_CreateSubscriber()

```c
Sensor_Subscriber *OH_Sensor_CreateSubscriber(void)
```

**Description**

Creates a [Sensor_Subscriber](capi-sensor-sensor-subscriber.md) instance.

**System capability**: SystemCapability.Sensors.Sensor

**Since**: 11

**Returns**:

| Type | Description |
| -- | -- |
| [Sensor_Subscriber *](capi-sensor-sensor-subscriber.md) | Pointer to the [Sensor_Subscriber](capi-sensor-sensor-subscriber.md) instance if the operation is successful; NULL otherwise. |

### OH_Sensor_DestroySubscriber()

```c
int32_t OH_Sensor_DestroySubscriber(Sensor_Subscriber *subscriber)
```

**Description**

Destroys a [Sensor_Subscriber](capi-sensor-sensor-subscriber.md) instance and reclaims the memory.

**System capability**: SystemCapability.Sensors.Sensor

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| [Sensor_Subscriber](capi-sensor-sensor-subscriber.md) *subscriber | Pointer to the [Sensor_Subscriber](capi-sensor-sensor-subscriber.md) instance. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | SENSOR_SUCCESS if the operation is successful; an error code defined in [Sensor_Result](capi-oh-sensor-type-h.md#sensor_result) otherwise. |

### OH_SensorSubscriber_SetCallback()

```c
int32_t OH_SensorSubscriber_SetCallback(Sensor_Subscriber* subscriber, const Sensor_EventCallback callback)
```

**Description**

Sets a callback function to report sensor data.

**System capability**: SystemCapability.Sensors.Sensor

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| [Sensor_Subscriber](capi-sensor-sensor-subscriber.md)* subscriber | Pointer to the sensor subscriber information. |
| [const Sensor_EventCallback](capi-oh-sensor-type-h.md#sensor_eventcallback) callback | Sets the callback function. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | SENSOR_SUCCESS if the operation is successful; an error code defined in [Sensor_Result](capi-oh-sensor-type-h.md#sensor_result) otherwise. |

### OH_SensorSubscriber_GetCallback()

```c
int32_t OH_SensorSubscriber_GetCallback(Sensor_Subscriber* subscriber, Sensor_EventCallback *callback)
```

**Description**

Obtains the callback function used to report sensor data.

**System capability**: SystemCapability.Sensors.Sensor

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| [Sensor_Subscriber](capi-sensor-sensor-subscriber.md)* subscriber | Pointer to the sensor subscriber information. |
| [Sensor_EventCallback](capi-oh-sensor-type-h.md#sensor_eventcallback) *callback | Pointer to the callback function. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | SENSOR_SUCCESS if the operation is successful; an error code defined in [Sensor_Result](capi-oh-sensor-type-h.md#sensor_result) otherwise. |


