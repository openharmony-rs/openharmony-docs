# oh_commonevent.h

## Overview

Defines key operation functions for publishing, subscribing to, and unsubscribing from common events, event callback data access, and ordered event control, enumerates error codes, and defines core data types.

**Library**: libohcommonevent.so

**System capability**: SystemCapability.Notification.CommonEvent

**Since**: 12

**Related module**: [OH_CommonEvent](capi-oh-commonevent.md)

## Summary

### Struct

| Name | typedef keyword | Description |
| -- | -- | -- |
| [CommonEvent_SubscribeInfo](capi-oh-commonevent-commonevent-subscribeinfo.md) | CommonEvent_SubscribeInfo | Defines a struct for the subscriber information of a common event. This struct is used to describe the configuration information of a subscriber. It is passed as a parameter when the API for creating a subscriber is called. |
| [CommonEvent_PublishInfo](capi-oh-commonevent-commonevent-publishinfo.md) | CommonEvent_PublishInfo | Defines the property object used for publishing a common event. This object encapsulates the property configuration required for publishing a common event. It is applicable to scenarios where an app needs to publish a custom common event and specify the publishing parameters. |
| [CommonEvent_RcvData](capi-oh-commonevent-commonevent-rcvdata.md) | CommonEvent_RcvData | Defines a struct for the common event data. When a common event triggers a callback, this struct is used to pass the received event data to the developer. |

### Enum

| Name | typedef keyword | Description |
| -- | -- | -- |
| [CommonEvent_ErrCode](#commonevent_errcode) | CommonEvent_ErrCode | Enumerates the error codes. |

### Function

| Name | typedef keyword | Description |
| -- | -- | -- |
| [typedef void (\*CommonEvent_ReceiveCallback)(const CommonEvent_RcvData *data)](#commonevent_receivecallback) | CommonEvent_ReceiveCallback | Defines the callback function of a common event. |
| [CommonEvent_SubscribeInfo* OH_CommonEvent_CreateSubscribeInfo(const char* events[], int32_t eventsNum)](#oh_commonevent_createsubscribeinfo) | - | Creates the subscriber information. |
| [CommonEvent_ErrCode OH_CommonEvent_SetPublisherPermission(CommonEvent_SubscribeInfo* info, const char* permission)](#oh_commonevent_setpublisherpermission) | - | Sets the permission of the publisher. |
| [CommonEvent_ErrCode OH_CommonEvent_SetPublisherBundleName(CommonEvent_SubscribeInfo* info, const char* bundleName)](#oh_commonevent_setpublisherbundlename) | - | Sets a bundle name of the publisher. |
| [void OH_CommonEvent_DestroySubscribeInfo(CommonEvent_SubscribeInfo* info)](#oh_commonevent_destroysubscribeinfo) | - | Destroys the subscriber information. |
| [CommonEvent_Subscriber* OH_CommonEvent_CreateSubscriber(const CommonEvent_SubscribeInfo* info, CommonEvent_ReceiveCallback callback)](#oh_commonevent_createsubscriber) | - | Creates a subscriber. |
| [void OH_CommonEvent_DestroySubscriber(CommonEvent_Subscriber* subscriber)](#oh_commonevent_destroysubscriber) | - | Destroys a subscriber. |
| [CommonEvent_ErrCode OH_CommonEvent_Subscribe(const CommonEvent_Subscriber* subscriber)](#oh_commonevent_subscribe) | - | Subscribes to a common event. |
| [CommonEvent_ErrCode OH_CommonEvent_UnSubscribe(const CommonEvent_Subscriber* subscriber)](#oh_commonevent_unsubscribe) | - | Unsubscribes from a common event. |
| [const char* OH_CommonEvent_GetEventFromRcvData(const CommonEvent_RcvData* rcvData)](#oh_commonevent_geteventfromrcvdata) | - | Obtains the name of a common event. |
| [int32_t OH_CommonEvent_GetCodeFromRcvData(const CommonEvent_RcvData* rcvData)](#oh_commonevent_getcodefromrcvdata) | - | Obtains the result code (integer type) of a common event. |
| [const char* OH_CommonEvent_GetDataStrFromRcvData(const CommonEvent_RcvData* rcvData)](#oh_commonevent_getdatastrfromrcvdata) | - | Obtains the result data (string type) of a common event. |
| [const char* OH_CommonEvent_GetBundleNameFromRcvData(const CommonEvent_RcvData* rcvData)](#oh_commonevent_getbundlenamefromrcvdata) | - | Obtains the bundle name of a common event. |
| [const CommonEvent_Parameters* OH_CommonEvent_GetParametersFromRcvData(const CommonEvent_RcvData* rcvData)](#oh_commonevent_getparametersfromrcvdata) | - | Obtains the additional information of a common event. |
| [CommonEvent_PublishInfo* OH_CommonEvent_CreatePublishInfo(bool ordered)](#oh_commonevent_createpublishinfo) | - | Creates a property object of a common event. |
| [void OH_CommonEvent_DestroyPublishInfo(CommonEvent_PublishInfo* info)](#oh_commonevent_destroypublishinfo) | - | Destroys a property object of a common event. |
| [CommonEvent_ErrCode OH_CommonEvent_SetPublishInfoBundleName(CommonEvent_PublishInfo* info, const char* bundleName)](#oh_commonevent_setpublishinfobundlename) | - | Sets the bundle name of a common event. |
| [CommonEvent_ErrCode OH_CommonEvent_SetPublishInfoPermissions(CommonEvent_PublishInfo* info, const char* permissions[], int32_t num)](#oh_commonevent_setpublishinfopermissions) | - | Sets permissions for a common event. |
| [CommonEvent_ErrCode OH_CommonEvent_SetPublishInfoCode(CommonEvent_PublishInfo* info, int32_t code)](#oh_commonevent_setpublishinfocode) | - | Sets the result code (integer type) of a common event. |
| [CommonEvent_ErrCode OH_CommonEvent_SetPublishInfoData(CommonEvent_PublishInfo* info, const char* data, size_t length)](#oh_commonevent_setpublishinfodata) | - | Sets the result data (string type) of a common event. |
| [CommonEvent_ErrCode OH_CommonEvent_SetPublishInfoParameters(CommonEvent_PublishInfo* info, CommonEvent_Parameters* param)](#oh_commonevent_setpublishinfoparameters) | - | Sets the additional information of a common event. |
| [CommonEvent_Parameters* OH_CommonEvent_CreateParameters()](#oh_commonevent_createparameters) | - | Creates an additional information object of a common event. |
| [void OH_CommonEvent_DestroyParameters(CommonEvent_Parameters* param)](#oh_commonevent_destroyparameters) | - | Destroys the additional information object of a common event. |
| [bool OH_CommonEvent_HasKeyInParameters(const CommonEvent_Parameters* para, const char* key)](#oh_commonevent_haskeyinparameters) | - | Checks whether the additional information of a common event contains a KV pair. |
| [int OH_CommonEvent_GetIntFromParameters(const CommonEvent_Parameters* para, const char* key, const int defaultValue)](#oh_commonevent_getintfromparameters) | - | Obtains the int data with a specific key from the additional information of a common event. |
| [CommonEvent_ErrCode OH_CommonEvent_SetIntToParameters(CommonEvent_Parameters* param, const char* key, int value)](#oh_commonevent_setinttoparameters) | - | Sets the int data with a specific key for the additional information of a common event. |
| [int32_t OH_CommonEvent_GetIntArrayFromParameters(const CommonEvent_Parameters* para, const char* key, int** array)](#oh_commonevent_getintarrayfromparameters) | - | Obtains the int array with a specific key from the additional information of a common event. |
| [CommonEvent_ErrCode OH_CommonEvent_SetIntArrayToParameters(CommonEvent_Parameters* param, const char* key, const int* value, size_t num)](#oh_commonevent_setintarraytoparameters) | - | Sets the int array with a specific key for the additional information of a common event. |
| [long OH_CommonEvent_GetLongFromParameters(const CommonEvent_Parameters* para, const char* key, const long defaultValue)](#oh_commonevent_getlongfromparameters) | - | Obtains the long data with a specific key from the additional information of a common event. |
| [CommonEvent_ErrCode OH_CommonEvent_SetLongToParameters(CommonEvent_Parameters* param, const char* key, long value)](#oh_commonevent_setlongtoparameters) | - | Sets the long data with a specific key for the additional information of a common event. |
| [int32_t OH_CommonEvent_GetLongArrayFromParameters(const CommonEvent_Parameters* para, const char* key, long** array)](#oh_commonevent_getlongarrayfromparameters) | - | Obtains the long array with a specific key from the additional information of a common event. |
| [CommonEvent_ErrCode OH_CommonEvent_SetLongArrayToParameters(CommonEvent_Parameters* param, const char* key, const long* value, size_t num)](#oh_commonevent_setlongarraytoparameters) | - | Sets the long array for the additional information of a common event. |
| [bool OH_CommonEvent_GetBoolFromParameters(const CommonEvent_Parameters* para, const char* key, const bool defaultValue)](#oh_commonevent_getboolfromparameters) | - | Obtains the Boolean data with a specific key from the additional information of a common event. |
| [CommonEvent_ErrCode OH_CommonEvent_SetBoolToParameters(CommonEvent_Parameters* param, const char* key, bool value)](#oh_commonevent_setbooltoparameters) | - | Sets the Boolean data with a specific key for the additional information of a common event. |
| [int32_t OH_CommonEvent_GetBoolArrayFromParameters(const CommonEvent_Parameters* para, const char* key, bool** array)](#oh_commonevent_getboolarrayfromparameters) | - | Obtains the Boolean array with a specific key from the additional information of a common event. |
| [CommonEvent_ErrCode OH_CommonEvent_SetBoolArrayToParameters(CommonEvent_Parameters* param, const char* key, const bool* value, size_t num)](#oh_commonevent_setboolarraytoparameters) | - | Sets the Boolean array with a specific key for the additional information of a common event. |
| [char OH_CommonEvent_GetCharFromParameters(const CommonEvent_Parameters* para, const char* key, const char defaultValue)](#oh_commonevent_getcharfromparameters) | - | Obtains the character data with a specific key from the additional information of a common event. |
| [CommonEvent_ErrCode OH_CommonEvent_SetCharToParameters(CommonEvent_Parameters* param, const char* key, char value)](#oh_commonevent_setchartoparameters) | - | Sets the character data with a specific key for the additional information of a common event. |
| [int32_t OH_CommonEvent_GetCharArrayFromParameters(const CommonEvent_Parameters* para, const char* key, char** array)](#oh_commonevent_getchararrayfromparameters) | - | Obtains the character array with a specific key from the additional information of a common event. |
| [CommonEvent_ErrCode OH_CommonEvent_SetCharArrayToParameters(CommonEvent_Parameters* param, const char* key, const char* value, size_t num)](#oh_commonevent_setchararraytoparameters) | - | Sets the character array with a specific key for the additional information of a common event. |
| [double OH_CommonEvent_GetDoubleFromParameters(const CommonEvent_Parameters* para, const char* key, const double defaultValue)](#oh_commonevent_getdoublefromparameters) | - | Obtains the double data with a specific key from the additional information of a common event. |
| [CommonEvent_ErrCode OH_CommonEvent_SetDoubleToParameters(CommonEvent_Parameters* param, const char* key, double value)](#oh_commonevent_setdoubletoparameters) | - | Sets the double data with a specific key for the additional information of a common event. |
| [int32_t OH_CommonEvent_GetDoubleArrayFromParameters(const CommonEvent_Parameters* para, const char* key, double** array)](#oh_commonevent_getdoublearrayfromparameters) | - | Obtains the double array with a specific key from the additional information of a common event. |
| [CommonEvent_ErrCode OH_CommonEvent_SetDoubleArrayToParameters(CommonEvent_Parameters* param, const char* key, const double* value, size_t num)](#oh_commonevent_setdoublearraytoparameters) | - | Sets the double array with a specific key for the additional information of a common event. |
| [CommonEvent_ErrCode OH_CommonEvent_Publish(const char* event)](#oh_commonevent_publish) | - | Publishes a common event. |
| [CommonEvent_ErrCode OH_CommonEvent_PublishWithInfo(const char* event, const CommonEvent_PublishInfo* info)](#oh_commonevent_publishwithinfo) | - | Publishes a common event with specified properties. |
| [bool OH_CommonEvent_IsOrderedCommonEvent(const CommonEvent_Subscriber* subscriber)](#oh_commonevent_isorderedcommonevent) | - | Checks whether a common event is an ordered one. |
| [bool OH_CommonEvent_FinishCommonEvent(CommonEvent_Subscriber* subscriber)](#oh_commonevent_finishcommonevent) | - | Finishes an ordered common event. |
| [bool OH_CommonEvent_GetAbortCommonEvent(const CommonEvent_Subscriber* subscriber)](#oh_commonevent_getabortcommonevent) | - | Checks whether an ordered common event is aborted. |
| [bool OH_CommonEvent_AbortCommonEvent(CommonEvent_Subscriber* subscriber)](#oh_commonevent_abortcommonevent) | - | Aborts an ordered common event when used with [OH_CommonEvent_FinishCommonEvent](capi-oh-commonevent-h.md#oh_commonevent_finishcommonevent). After the abort, the common event is not sent to the next subscriber. |
| [bool OH_CommonEvent_ClearAbortCommonEvent(CommonEvent_Subscriber* subscriber)](#oh_commonevent_clearabortcommonevent) | - | Clears the abort state of an ordered common event when used with [OH_CommonEvent_FinishCommonEvent](capi-oh-commonevent-h.md#oh_commonevent_finishcommonevent). After the clearance, the common event is sent to the next subscriber. |
| [int32_t OH_CommonEvent_GetCodeFromSubscriber(const CommonEvent_Subscriber* subscriber)](#oh_commonevent_getcodefromsubscriber) | - | Obtains the result code (integer type) of an ordered common event. |
| [bool OH_CommonEvent_SetCodeToSubscriber(CommonEvent_Subscriber* subscriber, int32_t code)](#oh_commonevent_setcodetosubscriber) | - | Sets the result code (integer type) of an ordered common event. |
| [const char* OH_CommonEvent_GetDataFromSubscriber(const CommonEvent_Subscriber* subscriber)](#oh_commonevent_getdatafromsubscriber) | - | Obtains the result data (string type) of an ordered common event. |
| [bool OH_CommonEvent_SetDataToSubscriber(CommonEvent_Subscriber* subscriber, const char* data, size_t length)](#oh_commonevent_setdatatosubscriber) | - | Sets the result data (string type) of an ordered common event. |

### Variable

| Name | Description |
| -- | -- |
| void CommonEvent_Subscriber | Defines a handle for the subscriber.<br>**Since**: 12 |
| void CommonEvent_Parameters | Defines a handler for the additional information of a common event.<br>**Since**: 12 |
| void (*CommonEvent_ReceiveCallback)(const CommonEvent_RcvData *data) | Defines the callback function of a common event.<br>**Since**: 12 |

## Enum type description

### CommonEvent_ErrCode

```c
enum CommonEvent_ErrCode
```

**Description**

Enumerates the error codes.

**Since**: 12

| Enum item | Description |
| -- | -- |
| COMMONEVENT_ERR_OK = 0 |  |
| COMMONEVENT_ERR_PERMISSION_ERROR = 201 |  |
| COMMONEVENT_ERR_INVALID_PARAMETER = 401 |  |
| COMMONEVENT_ERR_SENDING_LIMIT_EXCEEDED = 1500003 |  |
| COMMONEVENT_ERR_NOT_SYSTEM_SERVICE = 1500004 |  |
| COMMONEVENT_ERR_SENDING_REQUEST_FAILED = 1500007 |  |
| COMMONEVENT_ERR_INIT_UNDONE = 1500008 |  |
| COMMONEVENT_ERR_OBTAIN_SYSTEM_PARAMS = 1500009 |  |
| COMMONEVENT_ERR_SUBSCRIBER_NUM_EXCEEDED = 1500010 |  |
| COMMONEVENT_ERR_ALLOC_MEMORY_FAILED = 1500011 |  |


## Function description

### CommonEvent_ReceiveCallback()

```c
typedef void (*CommonEvent_ReceiveCallback)(const CommonEvent_RcvData *data)
```

**Description**

Defines the callback function of a common event.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [const CommonEvent_RcvData](capi-oh-commonevent-commonevent-rcvdata.md) \*data | Pointer to the callback data of a common event. |

### OH_CommonEvent_CreateSubscribeInfo()

```c
CommonEvent_SubscribeInfo* OH_CommonEvent_CreateSubscribeInfo(const char* events[], int32_t eventsNum)
```

**Description**

Creates the subscriber information.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| const char* events[] | Pointer to the common events. The actual number of subscribed common events is the smaller value between **eventsNum** and **events**. |
| int32_t eventsNum | Number of common events to subscribe to. The value is a non-negative integer and is the length of the **events** array. |

**Returns**:

| Type | Description |
| -- | -- |
| [CommonEvent_SubscribeInfo*](capi-oh-commonevent-commonevent-subscribeinfo.md) | Returns the subscriber information created if the operation is successful; returns      NULL otherwise. This pointer is internally managed and is released when      [OH_CommonEvent_DestroySubscribeInfo()](#oh_commonevent_destroysubscribeinfo) is called. |

### OH_CommonEvent_SetPublisherPermission()

```c
CommonEvent_ErrCode OH_CommonEvent_SetPublisherPermission(CommonEvent_SubscribeInfo* info, const char* permission)
```

**Description**

Sets the permission of the publisher.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [CommonEvent_SubscribeInfo](capi-oh-commonevent-commonevent-subscribeinfo.md)* info | Pointer to the subscriber information object for which the publisher permission is to be set. |
| const char* permission | Pointer to the permission name. The value is an array of permission names defined by the system. The subscriber can receive only the events from the publisher with this permission. If this parameter is not set, the subscriber can receive events from all publishers. |

**Returns**:

| Type | Description |
| -- | -- |
| [CommonEvent_ErrCode](capi-oh-commonevent-h.md#commonevent_errcode) | Returns an execution result.      <br>[COMMONEVENT_ERR_OK](capi-oh-commonevent-h.md#commonevent_errcode): Operation successful.      <br>[COMMONEVENT_ERR_INVALID_PARAMETER](capi-oh-commonevent-h.md#commonevent_errcode): Invalid parameter. |

### OH_CommonEvent_SetPublisherBundleName()

```c
CommonEvent_ErrCode OH_CommonEvent_SetPublisherBundleName(CommonEvent_SubscribeInfo* info, const char* bundleName)
```

**Description**

Sets a bundle name of the publisher.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [CommonEvent_SubscribeInfo](capi-oh-commonevent-commonevent-subscribeinfo.md)* info | Pointer to the subscriber information object for which the publisher permission is to be set. |
| const char* bundleName | Pointer to the bundle name. This parameter is used to specify that the subscriber receives only public events published by the publisher with the specified bundle name. If this parameter is not set, the subscriber can receive all public events published by the app. |

**Returns**:

| Type | Description |
| -- | -- |
| [CommonEvent_ErrCode](capi-oh-commonevent-h.md#commonevent_errcode) | Returns an execution result.      <br>[COMMONEVENT_ERR_OK](capi-oh-commonevent-h.md#commonevent_errcode): Operation successful.      <br>[COMMONEVENT_ERR_INVALID_PARAMETER](capi-oh-commonevent-h.md#commonevent_errcode): Invalid parameter. |

### OH_CommonEvent_DestroySubscribeInfo()

```c
void OH_CommonEvent_DestroySubscribeInfo(CommonEvent_SubscribeInfo* info)
```

**Description**

Destroys the subscriber information.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [CommonEvent_SubscribeInfo](capi-oh-commonevent-commonevent-subscribeinfo.md)* info | Pointer to the subscriber information. |

### OH_CommonEvent_CreateSubscriber()

```c
CommonEvent_Subscriber* OH_CommonEvent_CreateSubscriber(const CommonEvent_SubscribeInfo* info, CommonEvent_ReceiveCallback callback)
```

**Description**

Creates a subscriber.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [const CommonEvent_SubscribeInfo](capi-oh-commonevent-commonevent-subscribeinfo.md)* info | Pointer to the subscriber information. |
| [CommonEvent_ReceiveCallback](capi-oh-commonevent-h.md#commonevent_receivecallback) callback | Callback to be invoked when a common event is triggered. When a common event is successfully subscribed to, the common event data is returned by **data** when the event is triggered. |

**Returns**:

| Type | Description |
| -- | -- |
| CommonEvent_Subscriber* | Returns the subscriber created if the operation is successful; returns NULL      otherwise. This pointer is internally managed and is released when      [OH_CommonEvent_DestroySubscriber()](#oh_commonevent_destroysubscriber) is called. |

### OH_CommonEvent_DestroySubscriber()

```c
void OH_CommonEvent_DestroySubscriber(CommonEvent_Subscriber* subscriber)
```

**Description**

Destroys a subscriber.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| CommonEvent_Subscriber* subscriber | Pointer to the common event subscriber. |

### OH_CommonEvent_Subscribe()

```c
CommonEvent_ErrCode OH_CommonEvent_Subscribe(const CommonEvent_Subscriber* subscriber)
```

**Description**

Subscribes to a common event.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| const CommonEvent_Subscriber* subscriber | Pointer to the common event subscriber. |

**Returns**:

| Type | Description |
| -- | -- |
| [CommonEvent_ErrCode](capi-oh-commonevent-h.md#commonevent_errcode) | Returns an execution result.      <br>[COMMONEVENT_ERR_OK](capi-oh-commonevent-h.md#commonevent_errcode): Operation successful.      <br>[COMMONEVENT_ERR_INVALID_PARAMETER](capi-oh-commonevent-h.md#commonevent_errcode): Invalid parameter.      <br>[COMMONEVENT_ERR_SENDING_REQUEST_FAILED](capi-oh-commonevent-h.md#commonevent_errcode): Failed to send IPC requests.      <br>[COMMONEVENT_ERR_INIT_UNDONE](capi-oh-commonevent-h.md#commonevent_errcode): Services not initialized.      <br>[COMMONEVENT_ERR_SUBSCRIBER_NUM_EXCEEDED](capi-oh-commonevent-h.md#commonevent_errcode): The number of subscribers in the      process exceeds the system limit (200).      <br>[COMMONEVENT_ERR_ALLOC_MEMORY_FAILED](capi-oh-commonevent-h.md#commonevent_errcode): Failed to allocate memory. |

### OH_CommonEvent_UnSubscribe()

```c
CommonEvent_ErrCode OH_CommonEvent_UnSubscribe(const CommonEvent_Subscriber* subscriber)
```

**Description**

Unsubscribes from a common event.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| const CommonEvent_Subscriber* subscriber | Pointer to the common event subscriber. |

**Returns**:

| Type | Description |
| -- | -- |
| [CommonEvent_ErrCode](capi-oh-commonevent-h.md#commonevent_errcode) | Returns an execution result.      <br>[COMMONEVENT_ERR_OK](capi-oh-commonevent-h.md#commonevent_errcode): Operation successful.      <br>[COMMONEVENT_ERR_INVALID_PARAMETER](capi-oh-commonevent-h.md#commonevent_errcode): Invalid parameter.      <br>[COMMONEVENT_ERR_SENDING_REQUEST_FAILED](capi-oh-commonevent-h.md#commonevent_errcode): Failed to send IPC requests.      <br>[COMMONEVENT_ERR_INIT_UNDONE](capi-oh-commonevent-h.md#commonevent_errcode): Services not initialized. |

### OH_CommonEvent_GetEventFromRcvData()

```c
const char* OH_CommonEvent_GetEventFromRcvData(const CommonEvent_RcvData* rcvData)
```

**Description**

Obtains the name of a common event.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [const CommonEvent_RcvData](capi-oh-commonevent-commonevent-rcvdata.md)* rcvData | Pointer to the callback data of a common event. |

**Returns**:

| Type | Description |
| -- | -- |
| const char* | Name of a common event. This pointer is generated by the system and is released      immediately after the callback function      [CommonEvent_ReceiveCallback](#commonevent_receivecallback) ends. This parameter cannot      be used outside the callback function. |

### OH_CommonEvent_GetCodeFromRcvData()

```c
int32_t OH_CommonEvent_GetCodeFromRcvData(const CommonEvent_RcvData* rcvData)
```

**Description**

Obtains the result code (integer type) of a common event.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [const CommonEvent_RcvData](capi-oh-commonevent-commonevent-rcvdata.md)* rcvData | Pointer to the callback data of a common event. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Result code (integer type) of a common event. |

### OH_CommonEvent_GetDataStrFromRcvData()

```c
const char* OH_CommonEvent_GetDataStrFromRcvData(const CommonEvent_RcvData* rcvData)
```

**Description**

Obtains the result data (string type) of a common event.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [const CommonEvent_RcvData](capi-oh-commonevent-commonevent-rcvdata.md)* rcvData | Pointer to the callback data of a common event. |

**Returns**:

| Type | Description |
| -- | -- |
| const char* | Result data (string type) of a common event. This pointer is generated by the system      and is released immediately after the callback function      [CommonEvent_ReceiveCallback](#commonevent_receivecallback) ends. This parameter cannot      be used outside the callback function. |

### OH_CommonEvent_GetBundleNameFromRcvData()

```c
const char* OH_CommonEvent_GetBundleNameFromRcvData(const CommonEvent_RcvData* rcvData)
```

**Description**

Obtains the bundle name of a common event.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [const CommonEvent_RcvData](capi-oh-commonevent-commonevent-rcvdata.md)* rcvData | Pointer to the callback data of a common event. |

**Returns**:

| Type | Description |
| -- | -- |
| const char* | Bundle name obtained. This pointer is generated by the system and is released      immediately after the callback function      [CommonEvent_ReceiveCallback](#commonevent_receivecallback) ends. This parameter cannot      be used outside the callback function. |

### OH_CommonEvent_GetParametersFromRcvData()

```c
const CommonEvent_Parameters* OH_CommonEvent_GetParametersFromRcvData(const CommonEvent_RcvData* rcvData)
```

**Description**

Obtains the additional information of a common event.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [const CommonEvent_RcvData](capi-oh-commonevent-commonevent-rcvdata.md)* rcvData | Pointer to the callback data of a common event. |

**Returns**:

| Type | Description |
| -- | -- |
| const CommonEvent_Parameters* | Additional information obtained. |

### OH_CommonEvent_CreatePublishInfo()

```c
CommonEvent_PublishInfo* OH_CommonEvent_CreatePublishInfo(bool ordered)
```

**Description**

Creates a property object of a common event.

**Since**: 18

**Parameters**:

| Parameter | Description |
| -- | -- |
| bool ordered | Whether the common event is an ordered one. <br>- **true**: ordered common event. <br>- **false**: unordered common event. |

**Returns**:

| Type | Description |
| -- | -- |
| [CommonEvent_PublishInfo*](capi-oh-commonevent-commonevent-publishinfo.md) | Returns the property object if the operation is successful; returns NULL      otherwise. This pointer is internally managed and is released when      [OH_CommonEvent_DestroyPublishInfo()](#oh_commonevent_destroypublishinfo) is called. |

### OH_CommonEvent_DestroyPublishInfo()

```c
void OH_CommonEvent_DestroyPublishInfo(CommonEvent_PublishInfo* info)
```

**Description**

Destroys a property object of a common event.

**Since**: 18

**Parameters**:

| Parameter | Description |
| -- | -- |
| [CommonEvent_PublishInfo](capi-oh-commonevent-commonevent-publishinfo.md)* info | Pointer to the property object of the common event to destroy. |

### OH_CommonEvent_SetPublishInfoBundleName()

```c
CommonEvent_ErrCode OH_CommonEvent_SetPublishInfoBundleName(CommonEvent_PublishInfo* info, const char* bundleName)
```

**Description**

Sets the bundle name of a common event.

**Since**: 18

**Parameters**:

| Parameter | Description |
| -- | -- |
| [CommonEvent_PublishInfo](capi-oh-commonevent-commonevent-publishinfo.md)* info | Pointer to the property object of a common event. |
| const char* bundleName | Pointer to the bundle name to set. |

**Returns**:

| Type | Description |
| -- | -- |
| [CommonEvent_ErrCode](capi-oh-commonevent-h.md#commonevent_errcode) | Returns an execution result.      <br>[COMMONEVENT_ERR_OK](capi-oh-commonevent-h.md#commonevent_errcode): Operation successful.      <br>[COMMONEVENT_ERR_INVALID_PARAMETER](capi-oh-commonevent-h.md#commonevent_errcode): Invalid parameter. |

### OH_CommonEvent_SetPublishInfoPermissions()

```c
CommonEvent_ErrCode OH_CommonEvent_SetPublishInfoPermissions(CommonEvent_PublishInfo* info, const char* permissions[], int32_t num)
```

**Description**

Sets permissions for a common event.

**Since**: 18

**Parameters**:

| Parameter | Description |
| -- | -- |
| [CommonEvent_PublishInfo](capi-oh-commonevent-commonevent-publishinfo.md)* info | Pointer to the property object of a common event. |
| const char* permissions[] | Subscriber permissions. Only subscribers with the specified permissions can receive the common event. The valid number of permissions is the smaller value between **num** and **permissions**. |
| int32_t num | Number of permission names. The value is the length of the **permissions** array. |

**Returns**:

| Type | Description |
| -- | -- |
| [CommonEvent_ErrCode](capi-oh-commonevent-h.md#commonevent_errcode) | Returns an execution result.      <br>[COMMONEVENT_ERR_OK](capi-oh-commonevent-h.md#commonevent_errcode): Operation successful.      <br>[COMMONEVENT_ERR_INVALID_PARAMETER](capi-oh-commonevent-h.md#commonevent_errcode): Invalid parameter. |

### OH_CommonEvent_SetPublishInfoCode()

```c
CommonEvent_ErrCode OH_CommonEvent_SetPublishInfoCode(CommonEvent_PublishInfo* info, int32_t code)
```

**Description**

Sets the result code (integer type) of a common event.

**Since**: 18

**Parameters**:

| Parameter | Description |
| -- | -- |
| [CommonEvent_PublishInfo](capi-oh-commonevent-commonevent-publishinfo.md)* info | Pointer to the property object of a common event. |
| int32_t code | Result code to set. |

**Returns**:

| Type | Description |
| -- | -- |
| [CommonEvent_ErrCode](capi-oh-commonevent-h.md#commonevent_errcode) | Returns an execution result.      <br>[COMMONEVENT_ERR_OK](capi-oh-commonevent-h.md#commonevent_errcode): Operation successful.      <br>[COMMONEVENT_ERR_INVALID_PARAMETER](capi-oh-commonevent-h.md#commonevent_errcode): Invalid parameter. |

### OH_CommonEvent_SetPublishInfoData()

```c
CommonEvent_ErrCode OH_CommonEvent_SetPublishInfoData(CommonEvent_PublishInfo* info, const char* data, size_t length)
```

**Description**

Sets the result data (string type) of a common event.

**Since**: 18

**Parameters**:

| Parameter | Description |
| -- | -- |
| [CommonEvent_PublishInfo](capi-oh-commonevent-commonevent-publishinfo.md)* info | Pointer to the property object of a common event. |
| const char* data | Pointer to the result data to set. The value is a string. The valid data length is the smaller value between **length** and **data**. |
| size_t length | Length of the result data. The value is the length of the **data** string. |

**Returns**:

| Type | Description |
| -- | -- |
| [CommonEvent_ErrCode](capi-oh-commonevent-h.md#commonevent_errcode) | Returns an execution result.      <br>[COMMONEVENT_ERR_OK](capi-oh-commonevent-h.md#commonevent_errcode): Operation successful.      <br>[COMMONEVENT_ERR_INVALID_PARAMETER](capi-oh-commonevent-h.md#commonevent_errcode): Invalid parameter. |

### OH_CommonEvent_SetPublishInfoParameters()

```c
CommonEvent_ErrCode OH_CommonEvent_SetPublishInfoParameters(CommonEvent_PublishInfo* info, CommonEvent_Parameters* param)
```

**Description**

Sets the additional information of a common event.

**Since**: 18

**Parameters**:

| Parameter | Description |
| -- | -- |
| [CommonEvent_PublishInfo](capi-oh-commonevent-commonevent-publishinfo.md)* info | Pointer to the property object of a common event. |
| CommonEvent_Parameters* param | Pointer to the additional information to set. |

**Returns**:

| Type | Description |
| -- | -- |
| [CommonEvent_ErrCode](capi-oh-commonevent-h.md#commonevent_errcode) | Returns an execution result.      <br>[COMMONEVENT_ERR_OK](capi-oh-commonevent-h.md#commonevent_errcode): Operation successful.      <br>[COMMONEVENT_ERR_INVALID_PARAMETER](capi-oh-commonevent-h.md#commonevent_errcode): Invalid parameter. |

### OH_CommonEvent_CreateParameters()

```c
CommonEvent_Parameters* OH_CommonEvent_CreateParameters()
```

**Description**

Creates an additional information object of a common event.

**Since**: 18

**Returns**:

| Type | Description |
| -- | -- |
| CommonEvent_Parameters* | Returns additional information of the common event if operation is successful;      returns NULL otherwise. This pointer is internally managed and is released when      [OH_CommonEvent_DestroyParameters()](#oh_commonevent_destroyparameters) is called. |

### OH_CommonEvent_DestroyParameters()

```c
void OH_CommonEvent_DestroyParameters(CommonEvent_Parameters* param)
```

**Description**

Destroys the additional information object of a common event.

**Since**: 18

**Parameters**:

| Parameter | Description |
| -- | -- |
| CommonEvent_Parameters* param | Pointer to the additional information to destroy. |

### OH_CommonEvent_HasKeyInParameters()

```c
bool OH_CommonEvent_HasKeyInParameters(const CommonEvent_Parameters* para, const char* key)
```

**Description**

Checks whether the additional information of a common event contains a KV pair.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| const CommonEvent_Parameters* para | Pointer to the additional information to check. |
| const char* key | Pointer to the key. |

**Returns**:

| Type | Description |
| -- | -- |
| bool | Returns the check result.      <br>- true: The key exists.      <br>- false: The key does not exist. |

### OH_CommonEvent_GetIntFromParameters()

```c
int OH_CommonEvent_GetIntFromParameters(const CommonEvent_Parameters* para, const char* key, const int defaultValue)
```

**Description**

Obtains the int data with a specific key from the additional information of a common event.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| const CommonEvent_Parameters* para | Pointer to the additional information of a common event. |
| const char* key | Pointer to the key. |
| const int defaultValue | Default value, which is returned when the specified key does not exist. |

**Returns**:

| Type | Description |
| -- | -- |
| int | The int data obtained. |

### OH_CommonEvent_SetIntToParameters()

```c
CommonEvent_ErrCode OH_CommonEvent_SetIntToParameters(CommonEvent_Parameters* param, const char* key, int value)
```

**Description**

Sets the int data with a specific key for the additional information of a common event.

**Since**: 18

**Parameters**:

| Parameter | Description |
| -- | -- |
| CommonEvent_Parameters* param | Pointer to the additional information of a common event. |
| const char* key | Pointer to the key. |
| int value | The int data to set. |

**Returns**:

| Type | Description |
| -- | -- |
| [CommonEvent_ErrCode](capi-oh-commonevent-h.md#commonevent_errcode) | Returns an execution result.      <br>[COMMONEVENT_ERR_OK](capi-oh-commonevent-h.md#commonevent_errcode): Operation successful.      <br>[COMMONEVENT_ERR_INVALID_PARAMETER](capi-oh-commonevent-h.md#commonevent_errcode): Invalid parameter. |

### OH_CommonEvent_GetIntArrayFromParameters()

```c
int32_t OH_CommonEvent_GetIntArrayFromParameters(const CommonEvent_Parameters* para, const char* key, int** array)
```

**Description**

Obtains the int array with a specific key from the additional information of a common event.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| const CommonEvent_Parameters* para | Pointer to the additional information of a common event. |
| const char* key | Pointer to the key. |
| int** array | Output parameter, which is used to receive the int array. The array memory is allocated internally by the function, and the caller does not need to allocate it in advance. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Length of the array obtained. The default value is 0. |

### OH_CommonEvent_SetIntArrayToParameters()

```c
CommonEvent_ErrCode OH_CommonEvent_SetIntArrayToParameters(CommonEvent_Parameters* param, const char* key, const int* value, size_t num)
```

**Description**

Sets the int array with a specific key for the additional information of a common event.

**Since**: 18

**Parameters**:

| Parameter | Description |
| -- | -- |
| CommonEvent_Parameters* param | Pointer to the additional information of a common event. |
| const char* key | Pointer to the key. |
| const int* value | The int array to set. The actual number of elements is **num**. The length of the **value** array must be greater than **num**. Otherwise, out-of-bounds access may occur. |
| size_t num | Number of elements in the int array. |

**Returns**:

| Type | Description |
| -- | -- |
| [CommonEvent_ErrCode](capi-oh-commonevent-h.md#commonevent_errcode) | Returns an execution result.      <br>[COMMONEVENT_ERR_OK](capi-oh-commonevent-h.md#commonevent_errcode): Operation successful.      <br>[COMMONEVENT_ERR_INVALID_PARAMETER](capi-oh-commonevent-h.md#commonevent_errcode): Invalid parameter.      <br>[COMMONEVENT_ERR_ALLOC_MEMORY_FAILED](capi-oh-commonevent-h.md#commonevent_errcode): Failed to allocate memory. |

### OH_CommonEvent_GetLongFromParameters()

```c
long OH_CommonEvent_GetLongFromParameters(const CommonEvent_Parameters* para, const char* key, const long defaultValue)
```

**Description**

Obtains the long data with a specific key from the additional information of a common event.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| const CommonEvent_Parameters* para | Pointer to the additional information of a common event. |
| const char* key | Pointer to the key. |
| const long defaultValue | Default value, which is returned when the specified key does not exist. |

**Returns**:

| Type | Description |
| -- | -- |
| long | The long data obtained. |

### OH_CommonEvent_SetLongToParameters()

```c
CommonEvent_ErrCode OH_CommonEvent_SetLongToParameters(CommonEvent_Parameters* param, const char* key, long value)
```

**Description**

Sets the long data with a specific key for the additional information of a common event.

**Since**: 18

**Parameters**:

| Parameter | Description |
| -- | -- |
| CommonEvent_Parameters* param | Pointer to the additional information of a common event. |
| const char* key | Pointer to the key. |
| long value | The long data to set. |

**Returns**:

| Type | Description |
| -- | -- |
| [CommonEvent_ErrCode](capi-oh-commonevent-h.md#commonevent_errcode) | Returns an execution result.      <br>[COMMONEVENT_ERR_OK](capi-oh-commonevent-h.md#commonevent_errcode): Operation successful.      <br>[COMMONEVENT_ERR_INVALID_PARAMETER](capi-oh-commonevent-h.md#commonevent_errcode): Invalid parameter. |

### OH_CommonEvent_GetLongArrayFromParameters()

```c
int32_t OH_CommonEvent_GetLongArrayFromParameters(const CommonEvent_Parameters* para, const char* key, long** array)
```

**Description**

Obtains the long array with a specific key from the additional information of a common event.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| const CommonEvent_Parameters* para | Pointer to the additional information of a common event. |
| const char* key | Pointer to the key. |
| long** array | Output parameter, which is used to receive the long array. The array memory is allocated internally by the function, and the caller does not need to allocate it in advance. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Length of the array obtained. The default value is 0. |

### OH_CommonEvent_SetLongArrayToParameters()

```c
CommonEvent_ErrCode OH_CommonEvent_SetLongArrayToParameters(CommonEvent_Parameters* param, const char* key, const long* value, size_t num)
```

**Description**

Sets the long array for the additional information of a common event.

**Since**: 18

**Parameters**:

| Parameter | Description |
| -- | -- |
| CommonEvent_Parameters* param | Pointer to the additional information of a common event. |
| const char* key | Pointer to the key. |
| const long* value | Pointer to the long array to set. The actual number of elements is **num**. The length of the **value** array must be greater than **num**. Otherwise, out-of-bounds access may occur. |
| size_t num | Number of elements in the long array. |

**Returns**:

| Type | Description |
| -- | -- |
| [CommonEvent_ErrCode](capi-oh-commonevent-h.md#commonevent_errcode) | Returns an execution result.      <br>[COMMONEVENT_ERR_OK](capi-oh-commonevent-h.md#commonevent_errcode): Operation successful.      <br>[COMMONEVENT_ERR_INVALID_PARAMETER](capi-oh-commonevent-h.md#commonevent_errcode): Invalid parameter.      <br>[COMMONEVENT_ERR_ALLOC_MEMORY_FAILED](capi-oh-commonevent-h.md#commonevent_errcode): Failed to allocate memory. |

### OH_CommonEvent_GetBoolFromParameters()

```c
bool OH_CommonEvent_GetBoolFromParameters(const CommonEvent_Parameters* para, const char* key, const bool defaultValue)
```

**Description**

Obtains the Boolean data with a specific key from the additional information of a common event.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| const CommonEvent_Parameters* para | Pointer to the additional information of a common event. |
| const char* key | Pointer to the key. |
| const bool defaultValue | Default value, which is returned when the specified key does not exist. |

**Returns**:

| Type | Description |
| -- | -- |
| bool | The Boolean data obtained. |

### OH_CommonEvent_SetBoolToParameters()

```c
CommonEvent_ErrCode OH_CommonEvent_SetBoolToParameters(CommonEvent_Parameters* param, const char* key, bool value)
```

**Description**

Sets the Boolean data with a specific key for the additional information of a common event.

**Since**: 18

**Parameters**:

| Parameter | Description |
| -- | -- |
| CommonEvent_Parameters* param | Pointer to the additional information of a common event. |
| const char* key | Pointer to the key. |
| bool value | The Boolean data to set. |

**Returns**:

| Type | Description |
| -- | -- |
| [CommonEvent_ErrCode](capi-oh-commonevent-h.md#commonevent_errcode) | Returns an execution result.      <br>[COMMONEVENT_ERR_OK](capi-oh-commonevent-h.md#commonevent_errcode): Operation successful.      <br>[COMMONEVENT_ERR_INVALID_PARAMETER](capi-oh-commonevent-h.md#commonevent_errcode): Invalid parameter. |

### OH_CommonEvent_GetBoolArrayFromParameters()

```c
int32_t OH_CommonEvent_GetBoolArrayFromParameters(const CommonEvent_Parameters* para, const char* key, bool** array)
```

**Description**

Obtains the Boolean array with a specific key from the additional information of a common event.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| const CommonEvent_Parameters* para | Pointer to the additional information of a common event. |
| const char* key | Pointer to the key. |
| bool** array | Output parameter, which is used to receive the bool array. The array memory is allocated internally by the function, and the caller does not need to allocate it in advance. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Length of the array obtained. The default value is 0. |

### OH_CommonEvent_SetBoolArrayToParameters()

```c
CommonEvent_ErrCode OH_CommonEvent_SetBoolArrayToParameters(CommonEvent_Parameters* param, const char* key, const bool* value, size_t num)
```

**Description**

Sets the Boolean array with a specific key for the additional information of a common event.

**Since**: 18

**Parameters**:

| Parameter | Description |
| -- | -- |
| CommonEvent_Parameters* param | Pointer to the additional information of a common event. |
| const char* key | Pointer to the key. |
| const bool* value | Pointer to the Boolean array to set. The actual number of elements is **num**. The length of the **value** array must be greater than **num**. Otherwise, out-of-bounds access may occur. |
| size_t num | Number of elements in the Boolean array. |

**Returns**:

| Type | Description |
| -- | -- |
| [CommonEvent_ErrCode](capi-oh-commonevent-h.md#commonevent_errcode) | Returns an execution result.      <br>[COMMONEVENT_ERR_OK](capi-oh-commonevent-h.md#commonevent_errcode): Operation successful.      <br>[COMMONEVENT_ERR_INVALID_PARAMETER](capi-oh-commonevent-h.md#commonevent_errcode): Invalid parameter.      <br>[COMMONEVENT_ERR_ALLOC_MEMORY_FAILED](capi-oh-commonevent-h.md#commonevent_errcode): Failed to allocate memory. |

### OH_CommonEvent_GetCharFromParameters()

```c
char OH_CommonEvent_GetCharFromParameters(const CommonEvent_Parameters* para, const char* key, const char defaultValue)
```

**Description**

Obtains the character data with a specific key from the additional information of a common event.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| const CommonEvent_Parameters* para | Pointer to the additional information of a common event. |
| const char* key | Pointer to the key. |
| const char defaultValue | Default value, which is returned when the specified key does not exist. |

**Returns**:

| Type | Description |
| -- | -- |
| char | The character data obtained. |

### OH_CommonEvent_SetCharToParameters()

```c
CommonEvent_ErrCode OH_CommonEvent_SetCharToParameters(CommonEvent_Parameters* param, const char* key, char value)
```

**Description**

Sets the character data with a specific key for the additional information of a common event.

**Since**: 18

**Parameters**:

| Parameter | Description |
| -- | -- |
| CommonEvent_Parameters* param | Pointer to the additional information of a common event. |
| const char* key | Pointer to the key. |
| char value | The character data to set. |

**Returns**:

| Type | Description |
| -- | -- |
| [CommonEvent_ErrCode](capi-oh-commonevent-h.md#commonevent_errcode) | Returns an execution result.      <br>[COMMONEVENT_ERR_OK](capi-oh-commonevent-h.md#commonevent_errcode): Operation successful.      <br>[COMMONEVENT_ERR_INVALID_PARAMETER](capi-oh-commonevent-h.md#commonevent_errcode): Invalid parameter. |

### OH_CommonEvent_GetCharArrayFromParameters()

```c
int32_t OH_CommonEvent_GetCharArrayFromParameters(const CommonEvent_Parameters* para, const char* key, char** array)
```

**Description**

Obtains the character array with a specific key from the additional information of a common event.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| const CommonEvent_Parameters* para | Pointer to the additional information of a common event. |
| const char* key | Pointer to the key. |
| char** array | Output parameter, which is used to receive the character array. The array memory is allocated internally by the function, and the caller does not need to allocate it in advance. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Length of the array obtained. The default value is 0. |

### OH_CommonEvent_SetCharArrayToParameters()

```c
CommonEvent_ErrCode OH_CommonEvent_SetCharArrayToParameters(CommonEvent_Parameters* param, const char* key, const char* value, size_t num)
```

**Description**

Sets the character array with a specific key for the additional information of a common event.

**Since**: 18

**Parameters**:

| Parameter | Description |
| -- | -- |
| CommonEvent_Parameters* param | Pointer to the additional information of a common event. |
| const char* key | Pointer to the key. |
| const char* value | Pointer to the character array to set. The actual number of elements is the smaller value between **num** and the length of the **value** array. |
| size_t num | Number of elements in the character array. |

**Returns**:

| Type | Description |
| -- | -- |
| [CommonEvent_ErrCode](capi-oh-commonevent-h.md#commonevent_errcode) | Returns an execution result.      <br>[COMMONEVENT_ERR_OK](capi-oh-commonevent-h.md#commonevent_errcode): Operation successful.      <br>[COMMONEVENT_ERR_INVALID_PARAMETER](capi-oh-commonevent-h.md#commonevent_errcode): Invalid parameter. |

### OH_CommonEvent_GetDoubleFromParameters()

```c
double OH_CommonEvent_GetDoubleFromParameters(const CommonEvent_Parameters* para, const char* key, const double defaultValue)
```

**Description**

Obtains the double data with a specific key from the additional information of a common event.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| const CommonEvent_Parameters* para | Pointer to the additional information of a common event. |
| const char* key | Pointer to the key. |
| const double defaultValue | Default value, which is returned when the specified key does not exist. |

**Returns**:

| Type | Description |
| -- | -- |
| double | The double data obtained. |

### OH_CommonEvent_SetDoubleToParameters()

```c
CommonEvent_ErrCode OH_CommonEvent_SetDoubleToParameters(CommonEvent_Parameters* param, const char* key, double value)
```

**Description**

Sets the double data with a specific key for the additional information of a common event.

**Since**: 18

**Parameters**:

| Parameter | Description |
| -- | -- |
| CommonEvent_Parameters* param | Pointer to the additional information of a common event. |
| const char* key | Pointer to the key. |
| double value | The double data to set. |

**Returns**:

| Type | Description |
| -- | -- |
| [CommonEvent_ErrCode](capi-oh-commonevent-h.md#commonevent_errcode) | Returns an execution result.      <br>[COMMONEVENT_ERR_OK](capi-oh-commonevent-h.md#commonevent_errcode): Operation successful.      <br>[COMMONEVENT_ERR_INVALID_PARAMETER](capi-oh-commonevent-h.md#commonevent_errcode): Invalid parameter. |

### OH_CommonEvent_GetDoubleArrayFromParameters()

```c
int32_t OH_CommonEvent_GetDoubleArrayFromParameters(const CommonEvent_Parameters* para, const char* key, double** array)
```

**Description**

Obtains the double array with a specific key from the additional information of a common event.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| const CommonEvent_Parameters* para | Pointer to the additional information of a common event. |
| const char* key | Pointer to the key. |
| double** array | Output parameter, which is used to receive the double array. The array memory is allocated internally by the function, and the caller does not need to allocate it in advance. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Length of the array obtained. The default value is 0. |

### OH_CommonEvent_SetDoubleArrayToParameters()

```c
CommonEvent_ErrCode OH_CommonEvent_SetDoubleArrayToParameters(CommonEvent_Parameters* param, const char* key, const double* value, size_t num)
```

**Description**

Sets the double array with a specific key for the additional information of a common event.

**Since**: 18

**Parameters**:

| Parameter | Description |
| -- | -- |
| CommonEvent_Parameters* param | Pointer to the additional information of a common event. |
| const char* key | Pointer to the key. |
| const double* value | Pointer to the double array to set. The actual number of elements is **num**. The length of the **value** array must be greater than **num**. Otherwise, out-of-bounds access may occur. |
| size_t num | Number of elements in the double array. |

**Returns**:

| Type | Description |
| -- | -- |
| [CommonEvent_ErrCode](capi-oh-commonevent-h.md#commonevent_errcode) | Returns an execution result.      <br>[COMMONEVENT_ERR_OK](capi-oh-commonevent-h.md#commonevent_errcode): Operation successful.      <br>[COMMONEVENT_ERR_INVALID_PARAMETER](capi-oh-commonevent-h.md#commonevent_errcode): Invalid parameter.      <br>[COMMONEVENT_ERR_ALLOC_MEMORY_FAILED](capi-oh-commonevent-h.md#commonevent_errcode): Failed to allocate memory. |

### OH_CommonEvent_Publish()

```c
CommonEvent_ErrCode OH_CommonEvent_Publish(const char* event)
```

**Description**

Publishes a common event.

**Since**: 18

**Parameters**:

| Parameter | Description |
| -- | -- |
| const char* event | Pointer to the name of the common event. |

**Returns**:

| Type | Description |
| -- | -- |
| [CommonEvent_ErrCode](capi-oh-commonevent-h.md#commonevent_errcode) | Returns an execution result.      <br>[COMMONEVENT_ERR_OK](capi-oh-commonevent-h.md#commonevent_errcode): Operation successful.      <br>[COMMONEVENT_ERR_INVALID_PARAMETER](capi-oh-commonevent-h.md#commonevent_errcode): Invalid parameter.      <br>[COMMONEVENT_ERR_SENDING_LIMIT_EXCEEDED](capi-oh-commonevent-h.md#commonevent_errcode): Event sending frequency is too high.      <br>[COMMONEVENT_ERR_SENDING_REQUEST_FAILED](capi-oh-commonevent-h.md#commonevent_errcode): Failed to send IPC requests.      <br>[COMMONEVENT_ERR_INIT_UNDONE](capi-oh-commonevent-h.md#commonevent_errcode): Services not initialized. |

### OH_CommonEvent_PublishWithInfo()

```c
CommonEvent_ErrCode OH_CommonEvent_PublishWithInfo(const char* event, const CommonEvent_PublishInfo* info)
```

**Description**

Publishes a common event with specified properties.

**Since**: 18

**Parameters**:

| Parameter | Description |
| -- | -- |
| const char* event | Pointer to the name of the common event. |
| [const CommonEvent_PublishInfo](capi-oh-commonevent-commonevent-publishinfo.md)* info | Pointer to the property object of a common event. |

**Returns**:

| Type | Description |
| -- | -- |
| [CommonEvent_ErrCode](capi-oh-commonevent-h.md#commonevent_errcode) | Returns an execution result.      <br>[COMMONEVENT_ERR_OK](capi-oh-commonevent-h.md#commonevent_errcode): Operation successful.      <br>[COMMONEVENT_ERR_INVALID_PARAMETER](capi-oh-commonevent-h.md#commonevent_errcode): Invalid parameter.      <br>[COMMONEVENT_ERR_SENDING_LIMIT_EXCEEDED](capi-oh-commonevent-h.md#commonevent_errcode): Event sending frequency is too high.      <br>[COMMONEVENT_ERR_SENDING_REQUEST_FAILED](capi-oh-commonevent-h.md#commonevent_errcode): Failed to send IPC requests.      <br>[COMMONEVENT_ERR_INIT_UNDONE](capi-oh-commonevent-h.md#commonevent_errcode): Services not initialized. |

### OH_CommonEvent_IsOrderedCommonEvent()

```c
bool OH_CommonEvent_IsOrderedCommonEvent(const CommonEvent_Subscriber* subscriber)
```

**Description**

Checks whether a common event is an ordered one.

**Since**: 18

**Parameters**:

| Parameter | Description |
| -- | -- |
| const CommonEvent_Subscriber* subscriber | Pointer to the common event subscriber. |

**Returns**:

| Type | Description |
| -- | -- |
| bool | Returns true if the common event is an ordered one; returns false if the common event is an      unordered one. |

### OH_CommonEvent_FinishCommonEvent()

```c
bool OH_CommonEvent_FinishCommonEvent(CommonEvent_Subscriber* subscriber)
```

**Description**

Finishes an ordered common event.

**Since**: 18

**Parameters**:

| Parameter | Description |
| -- | -- |
| CommonEvent_Subscriber* subscriber | Pointer to the common event subscriber. |

**Returns**:

| Type | Description |
| -- | -- |
| bool | Returns true if the operation is successful; returns false otherwise. |

### OH_CommonEvent_GetAbortCommonEvent()

```c
bool OH_CommonEvent_GetAbortCommonEvent(const CommonEvent_Subscriber* subscriber)
```

**Description**

Checks whether an ordered common event is aborted.

**Since**: 18

**Parameters**:

| Parameter | Description |
| -- | -- |
| const CommonEvent_Subscriber* subscriber | Pointer to the common event subscriber. |

**Returns**:

| Type | Description |
| -- | -- |
| bool | Returns true if the ordered common event is in the abort state; returns false otherwise. |

### OH_CommonEvent_AbortCommonEvent()

```c
bool OH_CommonEvent_AbortCommonEvent(CommonEvent_Subscriber* subscriber)
```

**Description**

Aborts an ordered common event when used with [OH_CommonEvent_FinishCommonEvent](capi-oh-commonevent-h.md#oh_commonevent_finishcommonevent). After the abort, the common event is not sent to the next subscriber.

**Since**: 18

**Parameters**:

| Parameter | Description |
| -- | -- |
| CommonEvent_Subscriber* subscriber | Pointer to the common event subscriber. |

**Returns**:

| Type | Description |
| -- | -- |
| bool | Returns true if the operation is successful; returns false otherwise. |

### OH_CommonEvent_ClearAbortCommonEvent()

```c
bool OH_CommonEvent_ClearAbortCommonEvent(CommonEvent_Subscriber* subscriber)
```

**Description**

Clears the abort state of an ordered common event when used with [OH_CommonEvent_FinishCommonEvent](capi-oh-commonevent-h.md#oh_commonevent_finishcommonevent). After the clearance, the common event is sent to the next subscriber.

**Since**: 18

**Parameters**:

| Parameter | Description |
| -- | -- |
| CommonEvent_Subscriber* subscriber | Pointer to the common event subscriber. |

**Returns**:

| Type | Description |
| -- | -- |
| bool | Returns true if the operation is successful; returns false otherwise. |

### OH_CommonEvent_GetCodeFromSubscriber()

```c
int32_t OH_CommonEvent_GetCodeFromSubscriber(const CommonEvent_Subscriber* subscriber)
```

**Description**

Obtains the result code (integer type) of an ordered common event.

**Since**: 18

**Parameters**:

| Parameter | Description |
| -- | -- |
| const CommonEvent_Subscriber* subscriber | Pointer to the common event subscriber. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Returns the result code obtained if the operation is successful; returns 0 otherwise. |

### OH_CommonEvent_SetCodeToSubscriber()

```c
bool OH_CommonEvent_SetCodeToSubscriber(CommonEvent_Subscriber* subscriber, int32_t code)
```

**Description**

Sets the result code (integer type) of an ordered common event.

**Since**: 18

**Parameters**:

| Parameter | Description |
| -- | -- |
| CommonEvent_Subscriber* subscriber | Pointer to the common event subscriber. |
| int32_t code | Result code to set. |

**Returns**:

| Type | Description |
| -- | -- |
| bool | Returns true if the operation is successful; returns false otherwise. |

### OH_CommonEvent_GetDataFromSubscriber()

```c
const char* OH_CommonEvent_GetDataFromSubscriber(const CommonEvent_Subscriber* subscriber)
```

**Description**

Obtains the result data (string type) of an ordered common event.

**Since**: 18

**Parameters**:

| Parameter | Description |
| -- | -- |
| const CommonEvent_Subscriber* subscriber | Pointer to the common event subscriber. |

**Returns**:

| Type | Description |
| -- | -- |
| const char* | Returns the result data obtained if the operation is successful; returns NULL otherwise. |

### OH_CommonEvent_SetDataToSubscriber()

```c
bool OH_CommonEvent_SetDataToSubscriber(CommonEvent_Subscriber* subscriber, const char* data, size_t length)
```

**Description**

Sets the result data (string type) of an ordered common event.

**Since**: 18

**Parameters**:

| Parameter | Description |
| -- | -- |
| CommonEvent_Subscriber* subscriber | Pointer to the common event subscriber. |
| const char* data | Pointer to the result data to set. The effective data length is the smaller of **length** and the length of the **data** string |
| size_t length | Length of the data to be transferred, in bytes. The value is the length of the **data** string. |

**Returns**:

| Type | Description |
| -- | -- |
| bool | Returns true if the operation is successful; returns false otherwise. |


