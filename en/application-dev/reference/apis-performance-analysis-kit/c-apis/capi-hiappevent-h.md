# hiappevent.h

## Overview

The **HiAppEvent** module provides event subscription and event logging function definitions. Before performing application event logging, you must construct a parameter list object to store the input event parameters and specify the event domain, event name, and event type. <p>Event domain: domain associated with the application event. <p>Event name: name of the application event. <p>Event type: fault, statistics, security, or behavior. <p> Parameter list: a linked list used to store event parameters. Each parameter consists of a parameter name and a parameter value.

**Library**: libhiappevent_ndk.z.so

**System capability**: SystemCapability.HiviewDFX.HiAppEvent

**Since**: 8

**Related module**: [HiAppEvent](capi-hiappevent.md)

## Summary

### Struct

| Name | typedef keyword | Description |
| -- | -- | -- |
| [HiAppEvent_AppEventInfo](capi-hiappevent-hiappevent-appeventinfo.md) | HiAppEvent_AppEventInfo | Defines a struct for the information about a single event, including the domain, name, type, and custom parameter list in JSON string format. |
| [HiAppEvent_AppEventGroup](capi-hiappevent-hiappevent-appeventgroup.md) | HiAppEvent_AppEventGroup | Defines the information of an event group, including its name, the array of event information grouped by name, and the length of the event array. |
| [OH_HiAppEvent_ExternalLog](capi-hiappevent-oh-hiappevent-externallog.md) | OH_HiAppEvent_ExternalLog | The OH_HiAppEvent_ExternalLog structure is used to describe external log information, including the file path, the generation timestamp, file size, and type of system event. |
| [ParamListNode*](capi-hiappevent-paramlistnode8h.md) | ParamList | Defines the event parameter list node. |
| [HiAppEvent_Watcher](capi-hiappevent-hiappevent-watcher.md) | HiAppEvent_Watcher | Defines the watcher for application events. |
| [HiAppEvent_Processor](capi-hiappevent-hiappevent-processor.md) | HiAppEvent_Processor | Defines a processor for application events. |
| [HiAppEvent_Config](capi-hiappevent-hiappevent-config.md) | HiAppEvent_Config | Defines the configuration object used to set the conditions for triggering system events. |

### Enum

| Name | typedef keyword | Description |
| -- | -- | -- |
| [HiAppEvent_ErrorCode](#hiappevent_errorcode) | HiAppEvent_ErrorCode | Enumerates the error codes used in the HiAppEvent module. |
| [EventType](#eventtype) | EventType | Enumerates the event types. You are advised to select different event types based on application scenarios. |
| [OH_HiAppEvent_FrameworkType](#oh_hiappevent_frameworktype) | OH_HiAppEvent_FrameworkType | Enumerates the application framework types. You are advised to select an application framework type based on the actual application scenario. |
| [OH_HiAppEvent_SysEvent](#oh_hiappevent_sysevent) | OH_HiAppEvent_SysEvent | System event types.<br> You are advised to select system event types based on their respective usage scenarios. |

### Function

| Name | typedef keyword | Description |
| -- | -- | -- |
| [typedef void (\*OH_HiAppEvent_OnReceive)(const char* domain, const struct HiAppEvent_AppEventGroup* appEventGroups, uint32_t groupLen)](#oh_hiappevent_onreceive) | OH_HiAppEvent_OnReceive | Passes event content to the caller. Note: The lifecycle of the object pointed by the pointer in the callback is limited to the callback function. Do not use the pointer outside of the callback function. If the information needs to be cached, perform a deep copy of the content pointed by the pointer. |
| [typedef void (\*OH_HiAppEvent_OnTrigger)(int row, int size)](#oh_hiappevent_ontrigger) | OH_HiAppEvent_OnTrigger | Invoked if the event received by the watcher meets the conditions specified by [OH_HiAppEvent_SetTriggerCondition](capi-hiappevent-h.md#oh_hiappevent_settriggercondition). When the **OH_HiAppEvent_OnReceive** callback is not set in the watcher, the event received by the watcher will be saved. After the callback is complete, if a newly saved event meets the specified condition, the callback is invoked again. |
| [typedef void (\*OH_HiAppEvent_OnTake)(const char* const *events, uint32_t eventLen)](#oh_hiappevent_ontake) | OH_HiAppEvent_OnTake | Passes the events received by the watcher to the caller when [OH_HiAppEvent_TakeWatcherData](capi-hiappevent-h.md#oh_hiappevent_takewatcherdata) is used to obtain the events. Note: The lifecycle of the object pointed by the pointer in the callback is limited to the callback function. Do not use the pointer outside of the callback function. If the information needs to be cached, perform a deep copy of the content pointed by the pointer. |
| [ParamList OH_HiAppEvent_CreateParamList(void)](#oh_hiappevent_createparamlist) | - | Creates a pointer to a parameter list object. Note: If the created pointer to a parameter list object is no longer used, destroy it by calling [OH_HiAppEvent_DestroyParamList](capi-hiappevent-h.md#oh_hiappevent_destroyparamlist). |
| [void OH_HiAppEvent_DestroyParamList(ParamList list)](#oh_hiappevent_destroyparamlist) | - | Destroys a pointer to a parameter list object and releases its allocated memory. |
| [ParamList OH_HiAppEvent_AddBoolParam(ParamList list, const char* name, bool boolean)](#oh_hiappevent_addboolparam) | - | Adds an event parameter of the Boolean type to the parameter list. |
| [ParamList OH_HiAppEvent_AddBoolArrayParam(ParamList list, const char* name, const bool* booleans, int arrSize)](#oh_hiappevent_addboolarrayparam) | - | Adds an event parameter of the Boolean array type to the parameter list. |
| [ParamList OH_HiAppEvent_AddInt8Param(ParamList list, const char* name, int8_t num)](#oh_hiappevent_addint8param) | - | Adds an event parameter of the int8_t type to the parameter list. |
| [ParamList OH_HiAppEvent_AddInt8ArrayParam(ParamList list, const char* name, const int8_t* nums, int arrSize)](#oh_hiappevent_addint8arrayparam) | - | Adds an event parameter of the int8_t array type to the parameter list. |
| [ParamList OH_HiAppEvent_AddInt16Param(ParamList list, const char* name, int16_t num)](#oh_hiappevent_addint16param) | - | Adds an event parameter of the int16_t type to the parameter list. |
| [ParamList OH_HiAppEvent_AddInt16ArrayParam(ParamList list, const char* name, const int16_t* nums, int arrSize)](#oh_hiappevent_addint16arrayparam) | - | Adds an event parameter of the int16_t array type to the parameter list. |
| [ParamList OH_HiAppEvent_AddInt32Param(ParamList list, const char* name, int32_t num)](#oh_hiappevent_addint32param) | - | Adds an event parameter of the int32_t type to the parameter list. |
| [ParamList OH_HiAppEvent_AddInt32ArrayParam(ParamList list, const char* name, const int32_t* nums, int arrSize)](#oh_hiappevent_addint32arrayparam) | - | Adds an event parameter of the int32_t array type to the parameter list. |
| [ParamList OH_HiAppEvent_AddInt64Param(ParamList list, const char* name, int64_t num)](#oh_hiappevent_addint64param) | - | Adds an event parameter of the int64_t type to the parameter list. |
| [ParamList OH_HiAppEvent_AddInt64ArrayParam(ParamList list, const char* name, const int64_t* nums, int arrSize)](#oh_hiappevent_addint64arrayparam) | - | Adds an event parameter of the int64_t array type to the parameter list. |
| [ParamList OH_HiAppEvent_AddFloatParam(ParamList list, const char* name, float num)](#oh_hiappevent_addfloatparam) | - | Adds an event parameter of the float type to the parameter list. |
| [ParamList OH_HiAppEvent_AddFloatArrayParam(ParamList list, const char* name, const float* nums, int arrSize)](#oh_hiappevent_addfloatarrayparam) | - | Adds an event parameter of the float array type to the parameter list. |
| [ParamList OH_HiAppEvent_AddDoubleParam(ParamList list, const char* name, double num)](#oh_hiappevent_adddoubleparam) | - | Adds an event parameter of the Double type to the parameter list. |
| [ParamList OH_HiAppEvent_AddDoubleArrayParam(ParamList list, const char* name, const double* nums, int arrSize)](#oh_hiappevent_adddoublearrayparam) | - | Adds an event parameter of the double array type to the parameter list. |
| [ParamList OH_HiAppEvent_AddStringParam(ParamList list, const char* name, const char* str)](#oh_hiappevent_addstringparam) | - | Adds a parameter of the string type to the parameter list. |
| [ParamList OH_HiAppEvent_AddStringArrayParam(ParamList list, const char* name, const char * const *strs, int arrSize)](#oh_hiappevent_addstringarrayparam) | - | Adds a parameter of the string array type to the parameter list. |
| [int OH_HiAppEvent_Write(const char* domain, const char* name, enum EventType type, const ParamList list)](#oh_hiappevent_write) | - | Logs application events whose parameters are of the list type. Before application event logging, use this API to verify parameters of the events. If the verification is successful, the API writes the events to the event file. |
| [bool OH_HiAppEvent_Configure(const char* name, const char* value)](#oh_hiappevent_configure) | - | Configures the application event logging function. This function is used to configure the event logging function and the storage quota of the event file directory. |
| [HiAppEvent_Watcher* OH_HiAppEvent_CreateWatcher(const char* name)](#oh_hiappevent_createwatcher) | - | Creates a watcher for application events. Note: If a created watcher is no longer used, destroy it by calling [OH_HiAppEvent_DestroyWatcher](capi-hiappevent-h.md#oh_hiappevent_destroywatcher). |
| [void OH_HiAppEvent_DestroyWatcher(HiAppEvent_Watcher* watcher)](#oh_hiappevent_destroywatcher) | - | Destroys a created watcher. Note: If a created watcher is no longer used, destroy it to release memory to prevent memory leaks. After the watcher is destroyed, set its pointer to null. |
| [int OH_HiAppEvent_SetTriggerCondition(HiAppEvent_Watcher* watcher, int row, int size, int timeOut)](#oh_hiappevent_settriggercondition) | - | Sets the trigger condition of the [OH_HiAppEvent_OnTrigger](capi-hiappevent-h.md#oh_hiappevent_ontrigger) callback. You can set the trigger condition by the number and size of new events received by the watcher, and **onTrigger**<br>timeout interval. Ensure that at least one of the trigger conditions is set on the caller side. |
| [int OH_HiAppEvent_SetAppEventFilter(HiAppEvent_Watcher* watcher, const char* domain, uint8_t eventTypes, const char* const *names, int namesLen)](#oh_hiappevent_setappeventfilter) | - | Sets the type of events to listen for. This function can be called repeatedly. You can add multiple filtering conditions instead of replacing them. The watcher will receive notifications of events that meet any of the filtering conditions. |
| [int OH_HiAppEvent_SetWatcherOnTrigger(HiAppEvent_Watcher* watcher, OH_HiAppEvent_OnTrigger onTrigger)](#oh_hiappevent_setwatcherontrigger) | - | Sets the **onTrigger** callback. If **OnReceive** is not set or is set to **nullptr**, the application events received by the watcher will be saved. If the saved application events meet the trigger conditions of the **onTrigger** callback, the **onTrigger**<br>callback will be called. |
| [int OH_HiAppEvent_SetWatcherOnReceive(HiAppEvent_Watcher* watcher, OH_HiAppEvent_OnReceive onReceive)](#oh_hiappevent_setwatcheronreceive) | - | Sets the **onReceive** callback. When the listener detects the corresponding event, the onReceive callback is called. |
| [int OH_HiAppEvent_TakeWatcherData(HiAppEvent_Watcher* watcher, uint32_t eventNum, OH_HiAppEvent_OnTake onTake)](#oh_hiappevent_takewatcherdata) | - | Obtains the event saved by the watcher. |
| [int OH_HiAppEvent_AddWatcher(HiAppEvent_Watcher* watcher)](#oh_hiappevent_addwatcher) | - | Adds a watcher. Once a watcher is added, it starts to listen for system messages.<br> > **NOTE**<br>> > The [OH_HiAppEvent_AddWatcher](capi-hiappevent-h.md#oh_hiappevent_addwatcher) API involves I/O operations. In performance-sensitive service scenarios, > you need to determine whether to call this API in the main thread or a child thread based on the actual service > requirements. > The name passed to the [OH_HiAppEvent_AddWatcher](capi-hiappevent-h.md#oh_hiappevent_addwatcher) API should be unique. If the same name is passed, the > previous subscription will be overwritten. |
| [int OH_HiAppEvent_RemoveWatcher(HiAppEvent_Watcher* watcher)](#oh_hiappevent_removewatcher) | - | Removes a watcher. Once a watcher is removed, it stops listening for system messages. Note: This API only enables the watcher to stop listening for system messages. It does not destroy the watcher. The watcher still resides in the memory until the [OH_HiAppEvent_DestroyWatcher](capi-hiappevent-h.md#oh_hiappevent_destroywatcher) API is called. |
| [void OH_HiAppEvent_ClearData()](#oh_hiappevent_cleardata) | - | Clears the events saved by all watchers. |
| [HiAppEvent_Processor* OH_HiAppEvent_CreateProcessor(const char* name)](#oh_hiappevent_createprocessor) | - | Creates a processor for application events. Note: If a created processor is no longer used, destroy it by calling [OH_HiAppEvent_DestroyProcessor](capi-hiappevent-h.md#oh_hiappevent_destroyprocessor). |
| [int OH_HiAppEvent_SetReportRoute(HiAppEvent_Processor* processor, const char* appId, const char* routeInfo)](#oh_hiappevent_setreportroute) | - | Sets the report route for the processor. |
| [int OH_HiAppEvent_SetReportPolicy(HiAppEvent_Processor* processor, int periodReport, int batchReport, bool onStartReport, bool onBackgroundReport)](#oh_hiappevent_setreportpolicy) | - | Sets the report policy for the processor. |
| [int OH_HiAppEvent_SetReportEvent(HiAppEvent_Processor* processor, const char* domain, const char* name, bool isRealTime)](#oh_hiappevent_setreportevent) | - | Sets the report event for the processor. |
| [int OH_HiAppEvent_SetCustomConfig(HiAppEvent_Processor* processor, const char* key, const char* value)](#oh_hiappevent_setcustomconfig) | - | Sets the custom extension parameters of the processor. |
| [int OH_HiAppEvent_SetConfigId(HiAppEvent_Processor* processor, int configId)](#oh_hiappevent_setconfigid) | - | Sets the configuration ID of the processor. |
| [int OH_HiAppEvent_SetConfigName(HiAppEvent_Processor* processor, const char* configName)](#oh_hiappevent_setconfigname) | - | Sets the configuration name of the processor. |
| [int OH_HiAppEvent_SetReportUserId(HiAppEvent_Processor* processor, const char* const * userIdNames, int size)](#oh_hiappevent_setreportuserid) | - | Sets the report user ID of the processor. |
| [int OH_HiAppEvent_SetReportUserProperty(HiAppEvent_Processor* processor, const char* const * userPropertyNames, int size)](#oh_hiappevent_setreportuserproperty) | - | Sets the report user property of the processor. |
| [int64_t OH_HiAppEvent_AddProcessor(HiAppEvent_Processor* processor)](#oh_hiappevent_addprocessor) | - | Adds a processor. You can add a processor to migrate event data to the cloud. You can preset the implementation of the processor on the device and set its properties based on its constraints. Note that the configuration information of **Processor** must be provided by the data processor. Yet, as no data processor is preset in the device for interaction for the moment, migrating events to the cloud is unavailable. |
| [void OH_HiAppEvent_DestroyProcessor(HiAppEvent_Processor* processor)](#oh_hiappevent_destroyprocessor) | - | Destroys a processor. Note: If a processor is no longer used, destroy it to release memory to prevent memory leaks. After the processor is destroyed, set its pointer to null. |
| [int OH_HiAppEvent_RemoveProcessor(int64_t processorId)](#oh_hiappevent_removeprocessor) | - | Removes a processor. Once a processor is removed, it stops reporting events. Note: This API only stops the processor reporting events but does not destroy the processor. You can call [OH_HiAppEvent_DestroyProcessor](capi-hiappevent-h.md#oh_hiappevent_destroyprocessor) to destroy the processor and release the memory. |
| [HiAppEvent_Config* OH_HiAppEvent_CreateConfig(void)](#oh_hiappevent_createconfig) | - | Creates a pointer to the configuration object that sets the conditions for triggering system events. Note: If the created pointer to the configuration object that sets the conditions for triggering system events is no longer used, destroy it by calling [OH_HiAppEvent_DestroyConfig](capi-hiappevent-h.md#oh_hiappevent_destroyconfig). |
| [void OH_HiAppEvent_DestroyConfig(HiAppEvent_Config* config)](#oh_hiappevent_destroyconfig) | - | Destroys a configuration object. Note: If a configuration object is no longer used, destroy it to release memory to prevent memory leaks. After the object is destroyed, set its pointer to null. |
| [int OH_HiAppEvent_SetConfigItem(HiAppEvent_Config* config, const char* itemName, const char* itemValue)](#oh_hiappevent_setconfigitem) | - | Sets the items in the configuration object. |
| [int OH_HiAppEvent_SetEventConfig(const char* name, HiAppEvent_Config* config)](#oh_hiappevent_seteventconfig) | - | Sets event configuration parameters. Configuration items vary depending on events. Currently, only the following events are supported: **MAIN_THREAD_JANK**. (For details about the parameter configuration, see {@link Main Thread Jank Event Overview}.)<br>**MAIN_THREAD_JANK_V2**. (For details about the parameter configuration, see<br>{@link Main Thread Jank Event Overview}.)<br>**EVENT_APP_CRASH**. (For details about the parameter configuration, see {@link Crash Event Overview}.) This event is supported since API version 24. |
| [int OH_HiAppEvent_ReportFrameworkMemAnomaly(enum OH_HiAppEvent_FrameworkType frameworkType, const char* frameworkVersion, const char* description)](#oh_hiappevent_reportframeworkmemanomaly) | - | Reports information about abnormal memory usage of the application framework. <br>This API can be called once every minute at most. If the frequency limit is exceeded, the error code **HIAPPEVENT_REPORT_FREQUENCY_EXCEEDED** will be returned. <br>When the application detects that the memory usage of the application framework is abnormal and the operation is successful after this API is called: <br>1. If you have subscribed to the application event whose domain is **HIVIEWDFX** and name is **FW_MEM_ANOMALY**, the application will receive a callback containing the information about the abnormal memory usage of the application framework. <br>2. If you have not subscribed to this application event, the application will not receive the callback containing the information about the abnormal memory usage of the application framework. |
| [typedef void (\*OH_HiAppEvent_ExternalLogCapacityReachedCallback)(OH_HiAppEvent_ExternalLog* externalLogArr, uint32_t arrLen)](#oh_hiappevent_externallogcapacityreachedcallback) | OH_HiAppEvent_ExternalLogCapacityReachedCallback | The parameter of OH_HiAppEvent_RegExternalLogCapacityReachedCallback function which acts as the callback function when external log directory capacity is reached. |
| [int OH_HiAppEvent_RegExternalLogCapacityReachedCallback(OH_HiAppEvent_ExternalLogCapacityReachedCallback callback)](#oh_hiappevent_regexternallogcapacityreachedcallback) | - | The interface to set the callback when external log directory capacity is reached. |

### Variable

| Name | Description |
| -- | -- |
| void (*OH_HiAppEvent_OnReceive)( const char* domain, const struct HiAppEvent_AppEventGroup* appEventGroups, uint32_t groupLen) | Passes event content to the caller. Note: The lifecycle of the object pointed by the pointer in the callback is limited to the callback function. Do not use the pointer outside of the callback function. If the information needs to be cached, perform a deep copy of the content pointed by the pointer.<br>**Since**: 12 |
| void (*OH_HiAppEvent_OnTrigger)(int row, int size) | Invoked if the event received by the watcher meets the conditions specified by [OH_HiAppEvent_SetTriggerCondition](capi-hiappevent-h.md#oh_hiappevent_settriggercondition). When the **OH_HiAppEvent_OnReceive** callback is not set in the watcher, the event received by the watcher will be saved. After the callback is complete, if a newly saved event meets the specified condition, the callback is invoked again.<br>**Since**: 12 |
| void (*OH_HiAppEvent_OnTake)(const char* const *events, uint32_t eventLen) | Passes the events received by the watcher to the caller when [OH_HiAppEvent_TakeWatcherData](capi-hiappevent-h.md#oh_hiappevent_takewatcherdata) is used to obtain the events. Note: The lifecycle of the object pointed by the pointer in the callback is limited to the callback function. Do not use the pointer outside of the callback function. If the information needs to be cached, perform a deep copy of the content pointed by the pointer.<br>**Since**: 12 |
| void (*OH_HiAppEvent_ExternalLogCapacityReachedCallback)( OH_HiAppEvent_ExternalLog* externalLogArr, uint32_t arrLen) | The parameter of OH_HiAppEvent_RegExternalLogCapacityReachedCallback function which acts as the callback function when external log directory capacity is reached.<br>**Since**: 26.1.0 |

## Enum type description

### HiAppEvent_ErrorCode

```c
enum HiAppEvent_ErrorCode
```

**Description**

Enumerates the error codes used in the HiAppEvent module.

**Since**: 15

| Enum item | Description |
| -- | -- |
| HIAPPEVENT_SUCCESS = 0 |  |
| HIAPPEVENT_INVALID_PARAM_VALUE_LENGTH = 4 |  |
| HIAPPEVENT_PROCESSOR_IS_NULL = -7 |  |
| HIAPPEVENT_PROCESSOR_NOT_FOUND = -8 |  |
| HIAPPEVENT_INVALID_PARAM_VALUE = -9 |  |
| HIAPPEVENT_EVENT_CONFIG_IS_NULL = -10 |  |
| HIAPPEVENT_OPERATE_FAILED = -100 |  |
| HIAPPEVENT_INVALID_UID = -200 |  |
| HIAPPEVENT_REPORT_FREQUENCY_EXCEEDED = -300 |  |

### EventType

```c
enum EventType
```

**Description**

Enumerates the event types. You are advised to select different event types based on application scenarios.

**Since**: 8

| Enum item | Description |
| -- | -- |
| FAULT = 1 | Fault event type |
| STATISTIC = 2 | Statistic event type |
| SECURITY = 3 | Security event type |
| BEHAVIOR = 4 | Behavior event type |

### OH_HiAppEvent_FrameworkType

```c
enum OH_HiAppEvent_FrameworkType
```

**Description**

Enumerates the application framework types. You are advised to select an application framework type based on the actual application scenario.

**Since**: 26.0.0

| Enum item | Description |
| -- | -- |
| OH_FLUTTER_DART = 0 |  |
| OH_REACT_NATIVE_HERMES = 1 |  |
| OH_KMP_KOTLIN = 2 |  |

### OH_HiAppEvent_SysEvent

```c
enum OH_HiAppEvent_SysEvent
```

**Description**

System event types.<br> You are advised to select system event types based on their respective usage scenarios.

**Since**: 26.1.0

| Enum item | Description |
| -- | -- |
| OH_APP_CRASH = 1 |  |
| OH_APP_FREEZE = 2 |  |
| OH_RESOURCE_OVERLIMIT = 3 |  |
| OH_ADDRESS_SANITIZER = 4 |  |
| OH_APP_HICOLLIE = 5 |  |
| OH_CPU_USAGE_HIGH = 6 |  |


## Function description

### OH_HiAppEvent_OnReceive()

```c
typedef void (*OH_HiAppEvent_OnReceive)(const char* domain, const struct HiAppEvent_AppEventGroup* appEventGroups, uint32_t groupLen)
```

**Description**

Passes event content to the caller. Note: The lifecycle of the object pointed by the pointer in the callback is limited to the callback function. Do not use the pointer outside of the callback function. If the information needs to be cached, perform a deep copy of the content pointed by the pointer.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| const char\* domain | Domain of the received application event. |
| [const struct HiAppEvent_AppEventGroup](capi-hiappevent-hiappevent-appeventgroup.md)\* appEventGroups | Event group array. |
| uint32_t groupLen | Length of the event group array. |

### OH_HiAppEvent_OnTrigger()

```c
typedef void (*OH_HiAppEvent_OnTrigger)(int row, int size)
```

**Description**

Invoked if the event received by the watcher meets the conditions specified by [OH_HiAppEvent_SetTriggerCondition](capi-hiappevent-h.md#oh_hiappevent_settriggercondition). When the **OH_HiAppEvent_OnReceive** callback is not set in the watcher, the event received by the watcher will be saved. After the callback is complete, if a newly saved event meets the specified condition, the callback is invoked again.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| int row | Number of events newly received by the watcher. |
| int size | Total size of events newly received by the watcher, in bytes. The size of a single event is the length of the JSON string converted from the event. |

### OH_HiAppEvent_OnTake()

```c
typedef void (*OH_HiAppEvent_OnTake)(const char* const *events, uint32_t eventLen)
```

**Description**

Passes the events received by the watcher to the caller when [OH_HiAppEvent_TakeWatcherData](capi-hiappevent-h.md#oh_hiappevent_takewatcherdata) is used to obtain the events. Note: The lifecycle of the object pointed by the pointer in the callback is limited to the callback function. Do not use the pointer outside of the callback function. If the information needs to be cached, perform a deep copy of the content pointed by the pointer.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| const char\* const \*events | The event JSON string array. |
| uint32_t eventLen | Size of the event array. |

### OH_HiAppEvent_CreateParamList()

```c
ParamList OH_HiAppEvent_CreateParamList(void)
```

**Description**

Creates a pointer to a parameter list object. Note: If the created pointer to a parameter list object is no longer used, destroy it by calling [OH_HiAppEvent_DestroyParamList](capi-hiappevent-h.md#oh_hiappevent_destroyparamlist).

**Since**: 8

**Returns**:

| Type | Description |
| -- | -- |
| [ParamList](capi-hiappevent-paramlistnode8h.md) | Pointer to the parameter list object. |

### OH_HiAppEvent_DestroyParamList()

```c
void OH_HiAppEvent_DestroyParamList(ParamList list)
```

**Description**

Destroys a pointer to a parameter list object and releases its allocated memory.

**Since**: 8

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ParamList](capi-hiappevent-paramlistnode8h.md) list | Pointer to the parameter list object. |

### OH_HiAppEvent_AddBoolParam()

```c
ParamList OH_HiAppEvent_AddBoolParam(ParamList list, const char* name, bool boolean)
```

**Description**

Adds an event parameter of the Boolean type to the parameter list.

**Since**: 8

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ParamList](capi-hiappevent-paramlistnode8h.md) list | Pointer to the parameter list to which parameters need to be added. |
| const char* name | Name of the parameter to be added. |
| bool boolean | Value of the parameter to be added. |

**Returns**:

| Type | Description |
| -- | -- |
| [ParamList](capi-hiappevent-paramlistnode8h.md) | Pointer to the parameter list that contains the parameters added. |

### OH_HiAppEvent_AddBoolArrayParam()

```c
ParamList OH_HiAppEvent_AddBoolArrayParam(ParamList list, const char* name, const bool* booleans, int arrSize)
```

**Description**

Adds an event parameter of the Boolean array type to the parameter list.

**Since**: 8

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ParamList](capi-hiappevent-paramlistnode8h.md) list | Pointer to the parameter list to which parameters need to be added. |
| const char* name | Name of the parameter to be added. |
| const bool* booleans | Value of the parameter to be added. |
| int arrSize | Size of the parameter array to be added. |

**Returns**:

| Type | Description |
| -- | -- |
| [ParamList](capi-hiappevent-paramlistnode8h.md) | Pointer to the parameter list that contains the parameters added. |

### OH_HiAppEvent_AddInt8Param()

```c
ParamList OH_HiAppEvent_AddInt8Param(ParamList list, const char* name, int8_t num)
```

**Description**

Adds an event parameter of the int8_t type to the parameter list.

**Since**: 8

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ParamList](capi-hiappevent-paramlistnode8h.md) list | Pointer to the parameter list to which parameters need to be added. |
| const char* name | Name of the parameter to be added. |
| int8_t num | Value of the parameter to be added. |

**Returns**:

| Type | Description |
| -- | -- |
| [ParamList](capi-hiappevent-paramlistnode8h.md) | Pointer to the parameter list that contains the parameters added. |

### OH_HiAppEvent_AddInt8ArrayParam()

```c
ParamList OH_HiAppEvent_AddInt8ArrayParam(ParamList list, const char* name, const int8_t* nums, int arrSize)
```

**Description**

Adds an event parameter of the int8_t array type to the parameter list.

**Since**: 8

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ParamList](capi-hiappevent-paramlistnode8h.md) list | Pointer to the parameter list to which parameters need to be added. |
| const char* name | Name of the parameter to be added. |
| const int8_t* nums | Value of the parameter to be added. |
| int arrSize | Size of the parameter array to be added. |

**Returns**:

| Type | Description |
| -- | -- |
| [ParamList](capi-hiappevent-paramlistnode8h.md) | Pointer to the parameter list that contains the parameters added. |

### OH_HiAppEvent_AddInt16Param()

```c
ParamList OH_HiAppEvent_AddInt16Param(ParamList list, const char* name, int16_t num)
```

**Description**

Adds an event parameter of the int16_t type to the parameter list.

**Since**: 8

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ParamList](capi-hiappevent-paramlistnode8h.md) list | Pointer to the parameter list to which parameters need to be added. |
| const char* name | Name of the parameter to be added. |
| int16_t num | Value of the parameter to be added. |

**Returns**:

| Type | Description |
| -- | -- |
| [ParamList](capi-hiappevent-paramlistnode8h.md) | Pointer to the parameter list that contains the parameters added. |

### OH_HiAppEvent_AddInt16ArrayParam()

```c
ParamList OH_HiAppEvent_AddInt16ArrayParam(ParamList list, const char* name, const int16_t* nums, int arrSize)
```

**Description**

Adds an event parameter of the int16_t array type to the parameter list.

**Since**: 8

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ParamList](capi-hiappevent-paramlistnode8h.md) list | Pointer to the parameter list to which parameters need to be added. |
| const char* name | Name of the parameter to be added. |
| const int16_t* nums | Value of the parameter to be added. |
| int arrSize | Size of the parameter array to be added. |

**Returns**:

| Type | Description |
| -- | -- |
| [ParamList](capi-hiappevent-paramlistnode8h.md) | Pointer to the parameter list that contains the parameters added. |

### OH_HiAppEvent_AddInt32Param()

```c
ParamList OH_HiAppEvent_AddInt32Param(ParamList list, const char* name, int32_t num)
```

**Description**

Adds an event parameter of the int32_t type to the parameter list.

**Since**: 8

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ParamList](capi-hiappevent-paramlistnode8h.md) list | Pointer to the parameter list to which parameters need to be added. |
| const char* name | Name of the parameter to be added. |
| int32_t num | Value of the parameter to be added. |

**Returns**:

| Type | Description |
| -- | -- |
| [ParamList](capi-hiappevent-paramlistnode8h.md) | Pointer to the parameter list that contains the parameters added. |

### OH_HiAppEvent_AddInt32ArrayParam()

```c
ParamList OH_HiAppEvent_AddInt32ArrayParam(ParamList list, const char* name, const int32_t* nums, int arrSize)
```

**Description**

Adds an event parameter of the int32_t array type to the parameter list.

**Since**: 8

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ParamList](capi-hiappevent-paramlistnode8h.md) list | Pointer to the parameter list to which parameters need to be added. |
| const char* name | Name of the parameter to be added. |
| const int32_t* nums | Value of the parameter to be added. |
| int arrSize | Size of the parameter array to be added. |

**Returns**:

| Type | Description |
| -- | -- |
| [ParamList](capi-hiappevent-paramlistnode8h.md) | Pointer to the parameter list that contains the parameters added. |

### OH_HiAppEvent_AddInt64Param()

```c
ParamList OH_HiAppEvent_AddInt64Param(ParamList list, const char* name, int64_t num)
```

**Description**

Adds an event parameter of the int64_t type to the parameter list.

**Since**: 8

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ParamList](capi-hiappevent-paramlistnode8h.md) list | Pointer to the parameter list to which parameters need to be added. |
| const char* name | Name of the parameter to be added. |
| int64_t num | Value of the parameter to be added. |

**Returns**:

| Type | Description |
| -- | -- |
| [ParamList](capi-hiappevent-paramlistnode8h.md) | Pointer to the parameter list that contains the parameters added. |

### OH_HiAppEvent_AddInt64ArrayParam()

```c
ParamList OH_HiAppEvent_AddInt64ArrayParam(ParamList list, const char* name, const int64_t* nums, int arrSize)
```

**Description**

Adds an event parameter of the int64_t array type to the parameter list.

**Since**: 8

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ParamList](capi-hiappevent-paramlistnode8h.md) list | Pointer to the parameter list to which parameters need to be added. |
| const char* name | Name of the parameter to be added. |
| const int64_t* nums | Value of the parameter to be added. |
| int arrSize | Size of the parameter array to be added. |

**Returns**:

| Type | Description |
| -- | -- |
| [ParamList](capi-hiappevent-paramlistnode8h.md) | Pointer to the parameter list that contains the parameters added. |

### OH_HiAppEvent_AddFloatParam()

```c
ParamList OH_HiAppEvent_AddFloatParam(ParamList list, const char* name, float num)
```

**Description**

Adds an event parameter of the float type to the parameter list.

**Since**: 8

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ParamList](capi-hiappevent-paramlistnode8h.md) list | Pointer to the parameter list to which parameters need to be added. |
| const char* name | Name of the parameter to be added. |
| float num | Value of the parameter to be added. |

**Returns**:

| Type | Description |
| -- | -- |
| [ParamList](capi-hiappevent-paramlistnode8h.md) | Pointer to the parameter list that contains the parameters added. |

### OH_HiAppEvent_AddFloatArrayParam()

```c
ParamList OH_HiAppEvent_AddFloatArrayParam(ParamList list, const char* name, const float* nums, int arrSize)
```

**Description**

Adds an event parameter of the float array type to the parameter list.

**Since**: 8

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ParamList](capi-hiappevent-paramlistnode8h.md) list | Pointer to the parameter list to which parameters need to be added. |
| const char* name | Name of the parameter to be added. |
| const float* nums | Value of the parameter to be added. |
| int arrSize | Size of the parameter array to be added. |

**Returns**:

| Type | Description |
| -- | -- |
| [ParamList](capi-hiappevent-paramlistnode8h.md) | Pointer to the parameter list that contains the parameters added. |

### OH_HiAppEvent_AddDoubleParam()

```c
ParamList OH_HiAppEvent_AddDoubleParam(ParamList list, const char* name, double num)
```

**Description**

Adds an event parameter of the Double type to the parameter list.

**Since**: 8

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ParamList](capi-hiappevent-paramlistnode8h.md) list | Pointer to the parameter list to which parameters need to be added. |
| const char* name | Name of the parameter to be added. |
| double num | Value of the parameter to be added. |

**Returns**:

| Type | Description |
| -- | -- |
| [ParamList](capi-hiappevent-paramlistnode8h.md) | Pointer to the parameter list that contains the parameters added. |

### OH_HiAppEvent_AddDoubleArrayParam()

```c
ParamList OH_HiAppEvent_AddDoubleArrayParam(ParamList list, const char* name, const double* nums, int arrSize)
```

**Description**

Adds an event parameter of the double array type to the parameter list.

**Since**: 8

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ParamList](capi-hiappevent-paramlistnode8h.md) list | Pointer to the parameter list to which parameters need to be added. |
| const char* name | Name of the parameter to be added. |
| const double* nums | Value of the parameter to be added. |
| int arrSize | Size of the parameter array to be added. |

**Returns**:

| Type | Description |
| -- | -- |
| [ParamList](capi-hiappevent-paramlistnode8h.md) | Pointer to the parameter list that contains the parameters added. |

### OH_HiAppEvent_AddStringParam()

```c
ParamList OH_HiAppEvent_AddStringParam(ParamList list, const char* name, const char* str)
```

**Description**

Adds a parameter of the string type to the parameter list.

**Since**: 8

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ParamList](capi-hiappevent-paramlistnode8h.md) list | Pointer to the parameter list to which parameters need to be added. |
| const char* name | Name of the parameter to be added. |
| const char* str | Value of the parameter to be added. |

**Returns**:

| Type | Description |
| -- | -- |
| [ParamList](capi-hiappevent-paramlistnode8h.md) | Pointer to the parameter list that contains the parameters added. |

### OH_HiAppEvent_AddStringArrayParam()

```c
ParamList OH_HiAppEvent_AddStringArrayParam(ParamList list, const char* name, const char * const *strs, int arrSize)
```

**Description**

Adds a parameter of the string array type to the parameter list.

**Since**: 8

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ParamList](capi-hiappevent-paramlistnode8h.md) list | Pointer to the parameter list to which parameters need to be added. |
| const char* name | Name of the parameter to be added. |
| const char * const *strs | Value of the parameter to be added. |
| int arrSize | Size of the parameter array to be added. |

**Returns**:

| Type | Description |
| -- | -- |
| [ParamList](capi-hiappevent-paramlistnode8h.md) | Pointer to the parameter list that contains the parameters added. |

### OH_HiAppEvent_Write()

```c
int OH_HiAppEvent_Write(const char* domain, const char* name, enum EventType type, const ParamList list)
```

**Description**

Logs application events whose parameters are of the list type. Before application event logging, use this API to verify parameters of the events. If the verification is successful, the API writes the events to the event file.

**Since**: 8

**Parameters**:

| Parameter | Description |
| -- | -- |
| const char* domain | Event domain. You can customize event domains as required. The value is a string that contains a maximum of 32 characters, including digits (0 to 9), letters (a to z) (A to Z), and underscore (\_). It must start with a letter and cannot end with an underscore (\_). |
| const char* name | Event name. You can customize event names as required. The value is a string that contains a maximum of 48 characters, including digits (0 to 9), letters (a to z) (A to Z), underscore (\_), and dollar sign (`$`). It must start with a letter or dollar sign (`$`) and end with a digit or letter. |
| enum EventType type | Event type. For details, see [EventType](capi-hiappevent-h.md#eventtype). |
| [const ParamList](capi-hiappevent-paramlistnode8h.md) list | List of event parameters, each of which consists of a parameter name and a parameter value. The specifications are as follows: <br>1. The value is a string that contains a maximum of 32 characters, including digits (0 to 9), letters (a to z)(A to Z),underscore (_), and dollar sign (`$`). It must start with a letter or dollar sign (`$`) and end with a digit or letter. <br>2. The parameter value can be a string, number, Boolean, or array. The length of a string must be less than 8 * 1024 characters. If this limit is exceeded, excess characters will be truncated. The element type of an array parameter can only be a string, number, or Boolean, and the number of elements must be less than 100. If this limit is exceeded, excess elements will be discarded. <br>3. The maximum number of parameters is 32. If this limit is exceeded, excess parameters will be discarded. |

**Returns**:

| Type | Description |
| -- | -- |
| int | If the event parameters are successfully verified, 0 is returned and the event is written into the event      file.      If an event contains invalid parameters, a positive value is returned. The event is written into the event file      after the invalid parameters are discarded.      If the event parameter fails to be verified, a negative value is returned and the event is not written to the      event file.      <br>0: Parameter verification successful.      <br>-1: Invalid event name.      <br>-4: Invalid event domain name.      <br>-99: Application event logging disabled.      <br>1: Invalid event parameter name.      <br>4: Invalid event parameter string length.      <br>5: Invalid number of event parameters.      <br>6: Invalid event parameter array length.      <br>8: Duplicate event parameter name. |

### OH_HiAppEvent_Configure()

```c
bool OH_HiAppEvent_Configure(const char* name, const char* value)
```

**Description**

Configures the application event logging function. This function is used to configure the event logging function and the storage quota of the event file directory.

**Since**: 8

**Parameters**:

| Parameter | Description |
| -- | -- |
| const char* name | Configuration item name The value can be {@link DISABLE} or {@link MAX_STORAGE}. |
| const char* value | Configuration item value. If the configuration item name is {@link DISABLE}, the value can be **true**<br>    or **false**.<br>    If the configuration item name is {@link MAX_STORAGE}, the quota value consists of only digits and a unit (including b\|k\|kb\|m\|mb\|g\|gb\|t\|tb, which are case-insensitive). The quota value must start with a digit. You can determine whether to pass the unit. If the unit is left empty, **b**(that is, byte) is used by default. |

**Returns**:

| Type | Description |
| -- | -- |
| bool | Configuration result. The value true indicates that the configuration is successful, and the      value false indicates the opposite. |

### OH_HiAppEvent_CreateWatcher()

```c
HiAppEvent_Watcher* OH_HiAppEvent_CreateWatcher(const char* name)
```

**Description**

Creates a watcher for application events. Note: If a created watcher is no longer used, destroy it by calling [OH_HiAppEvent_DestroyWatcher](capi-hiappevent-h.md#oh_hiappevent_destroywatcher).

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| const char* name | Pointer to the watcher name. |

**Returns**:

| Type | Description |
| -- | -- |
| [HiAppEvent_Watcher*](capi-hiappevent-hiappevent-watcher.md) | Pointer to the new watcher if the API is called successfully; NULL if the name parameter is      invalid. |

### OH_HiAppEvent_DestroyWatcher()

```c
void OH_HiAppEvent_DestroyWatcher(HiAppEvent_Watcher* watcher)
```

**Description**

Destroys a created watcher. Note: If a created watcher is no longer used, destroy it to release memory to prevent memory leaks. After the watcher is destroyed, set its pointer to null.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [HiAppEvent_Watcher](capi-hiappevent-hiappevent-watcher.md)* watcher | Pointer to the watcher (that is, the pointer returned by [OH_HiAppEvent_CreateWatcher](capi-hiappevent-h.md#oh_hiappevent_createwatcher)). |

### OH_HiAppEvent_SetTriggerCondition()

```c
int OH_HiAppEvent_SetTriggerCondition(HiAppEvent_Watcher* watcher, int row, int size, int timeOut)
```

**Description**

Sets the trigger condition of the [OH_HiAppEvent_OnTrigger](capi-hiappevent-h.md#oh_hiappevent_ontrigger) callback. You can set the trigger condition by the number and size of new events received by the watcher, and **onTrigger**<br>timeout interval. Ensure that at least one of the trigger conditions is set on the caller side.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [HiAppEvent_Watcher](capi-hiappevent-hiappevent-watcher.md)* watcher | Pointer to the watcher (that is, the pointer returned by [OH_HiAppEvent_CreateWatcher](capi-hiappevent-h.md#oh_hiappevent_createwatcher)). |
| int row | Row count. If the input value is greater than 0 and the number of newly received events is greater than or equal to the value of this parameter, the configured **onTrigger** callback is called. If the input value is less than or equal to 0, the number of received events is not used as the condition to trigger the **onTrigger** callback. |
| int size | Size value, Unit: bytes. If the input value is greater than 0 and the size of the newly received event is greater than or equal to the value of this parameter, the configured **onTrigger** callback is called. The size of a single event is the length of the JSON string converted from the event. If the input value is less than or equal to 0, the size of received events is not used as the condition to trigger the **onTrigger** callback. |
| int timeOut | Timeout interval, in seconds. The actual value is the value of **timeOut** multiplied by 30 seconds. If the value of **timeOut** is greater than 0, the system checks for new events every **timeOut** * 30 seconds. If a new event is detected, the **onTrigger** callback is triggered, and the timer restarts. If the value of **timeOut** is less than or equal to 0, the **onTrigger** callback is not enabled. |

**Returns**:

| Type | Description |
| -- | -- |
| int | 0 if the API is called successfully; -5 if the pointer to an input parameter is null. |

### OH_HiAppEvent_SetAppEventFilter()

```c
int OH_HiAppEvent_SetAppEventFilter(HiAppEvent_Watcher* watcher, const char* domain, uint8_t eventTypes, const char* const *names, int namesLen)
```

**Description**

Sets the type of events to listen for. This function can be called repeatedly. You can add multiple filtering conditions instead of replacing them. The watcher will receive notifications of events that meet any of the filtering conditions.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [HiAppEvent_Watcher](capi-hiappevent-hiappevent-watcher.md)* watcher | Pointer to the watcher (that is, the pointer returned by [OH_HiAppEvent_CreateWatcher](capi-hiappevent-h.md#oh_hiappevent_createwatcher)). |
| const char* domain | Domain of events to be listened for. |
| uint8_t eventTypes | Types of events to be listened for. The bitwise AND matching mode is used. Multiple types of events can be listened for. If the first bit is **1** (the value is **1**), fault events can be listened for. <br>If the second bit is **1** (the value is **2**), statistics events can be listened for. <br>If the third bit is **1** (the value is **4**), security events can be listened for. <br>If the fourth digit is **1** (the value is **8**), events of the listening behavior type can be listened for. <br>If four digits are **1** (the value is **15**) or 0 (the value is **0**), events of all types can be listened for. |
| const char* const *names | Array of the event names. |
| int namesLen | Length of the event name array. |

**Returns**:

| Type | Description |
| -- | -- |
| int | 0 if the API is called successfully; -1 if the names parameter is invalid; -4 if the       domain parameter is invalid; -5 if the pointer to an input parameter is null. |

### OH_HiAppEvent_SetWatcherOnTrigger()

```c
int OH_HiAppEvent_SetWatcherOnTrigger(HiAppEvent_Watcher* watcher, OH_HiAppEvent_OnTrigger onTrigger)
```

**Description**

Sets the **onTrigger** callback. If **OnReceive** is not set or is set to **nullptr**, the application events received by the watcher will be saved. If the saved application events meet the trigger conditions of the **onTrigger** callback, the **onTrigger**<br>callback will be called.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [HiAppEvent_Watcher](capi-hiappevent-hiappevent-watcher.md)* watcher | Pointer to the watcher (that is, the pointer returned by [OH_HiAppEvent_CreateWatcher](capi-hiappevent-h.md#oh_hiappevent_createwatcher)). |
| [OH_HiAppEvent_OnTrigger](capi-hiappevent-h.md#oh_hiappevent_ontrigger) onTrigger | Callback to be set. |

**Returns**:

| Type | Description |
| -- | -- |
| int | 0 if the API is called successfully; -5 if the pointer to an input parameter is null. |

### OH_HiAppEvent_SetWatcherOnReceive()

```c
int OH_HiAppEvent_SetWatcherOnReceive(HiAppEvent_Watcher* watcher, OH_HiAppEvent_OnReceive onReceive)
```

**Description**

Sets the **onReceive** callback. When the listener detects the corresponding event, the onReceive callback is called.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [HiAppEvent_Watcher](capi-hiappevent-hiappevent-watcher.md)* watcher | Pointer to the watcher (that is, the pointer returned by [OH_HiAppEvent_CreateWatcher](capi-hiappevent-h.md#oh_hiappevent_createwatcher)). |
| [OH_HiAppEvent_OnReceive](capi-hiappevent-h.md#oh_hiappevent_onreceive) onReceive | Pointer to the callback function. |

**Returns**:

| Type | Description |
| -- | -- |
| int | 0 if the API is called successfully; -5 if the pointer to an input parameter is null. |

### OH_HiAppEvent_TakeWatcherData()

```c
int OH_HiAppEvent_TakeWatcherData(HiAppEvent_Watcher* watcher, uint32_t eventNum, OH_HiAppEvent_OnTake onTake)
```

**Description**

Obtains the event saved by the watcher.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [HiAppEvent_Watcher](capi-hiappevent-hiappevent-watcher.md)* watcher | Pointer to the watcher (that is, the pointer returned by [OH_HiAppEvent_CreateWatcher](capi-hiappevent-h.md#oh_hiappevent_createwatcher)). |
| uint32_t eventNum | If the input value is less than or equal to **0**, all saved events are obtained. If the input value is greater than **0**, events are sorted by time in descending order and a specified number of saved events are obtained. |
| [OH_HiAppEvent_OnTake](capi-hiappevent-h.md#oh_hiappevent_ontake) onTake | Pointer to the callback. The event information is returned through this callback. |

**Returns**:

| Type | Description |
| -- | -- |
| int | 0 if the API is called successfully; -5 if the pointer to an input parameter is null; -6 if      [OH_HiAppEvent_AddWatcher](capi-hiappevent-h.md#oh_hiappevent_addwatcher) has not been called to add a watcher. |

### OH_HiAppEvent_AddWatcher()

```c
int OH_HiAppEvent_AddWatcher(HiAppEvent_Watcher* watcher)
```

**Description**

Adds a watcher. Once a watcher is added, it starts to listen for system messages.<br> > **NOTE**<br>> > The [OH_HiAppEvent_AddWatcher](capi-hiappevent-h.md#oh_hiappevent_addwatcher) API involves I/O operations. In performance-sensitive service scenarios, > you need to determine whether to call this API in the main thread or a child thread based on the actual service > requirements. > The name passed to the [OH_HiAppEvent_AddWatcher](capi-hiappevent-h.md#oh_hiappevent_addwatcher) API should be unique. If the same name is passed, the > previous subscription will be overwritten.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [HiAppEvent_Watcher](capi-hiappevent-hiappevent-watcher.md)* watcher | Pointer to the watcher (that is, the pointer returned by [OH_HiAppEvent_CreateWatcher](capi-hiappevent-h.md#oh_hiappevent_createwatcher)). |

**Returns**:

| Type | Description |
| -- | -- |
| int | 0 if the API is called successfully; -5 if the pointer to an input parameter is null. |

### OH_HiAppEvent_RemoveWatcher()

```c
int OH_HiAppEvent_RemoveWatcher(HiAppEvent_Watcher* watcher)
```

**Description**

Removes a watcher. Once a watcher is removed, it stops listening for system messages. Note: This API only enables the watcher to stop listening for system messages. It does not destroy the watcher. The watcher still resides in the memory until the [OH_HiAppEvent_DestroyWatcher](capi-hiappevent-h.md#oh_hiappevent_destroywatcher) API is called.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [HiAppEvent_Watcher](capi-hiappevent-hiappevent-watcher.md)* watcher | Pointer to the watcher (that is, the pointer returned by [OH_HiAppEvent_CreateWatcher](capi-hiappevent-h.md#oh_hiappevent_createwatcher)). |

**Returns**:

| Type | Description |
| -- | -- |
| int | 0 if the API is called successfully; -5 if the pointer to an input parameter is null; -6 if      [OH_HiAppEvent_AddWatcher](capi-hiappevent-h.md#oh_hiappevent_addwatcher) has not been called to add a watcher. |

### OH_HiAppEvent_ClearData()

```c
void OH_HiAppEvent_ClearData()
```

**Description**

Clears the events saved by all watchers.

**Since**: 12

### OH_HiAppEvent_CreateProcessor()

```c
HiAppEvent_Processor* OH_HiAppEvent_CreateProcessor(const char* name)
```

**Description**

Creates a processor for application events. Note: If a created processor is no longer used, destroy it by calling [OH_HiAppEvent_DestroyProcessor](capi-hiappevent-h.md#oh_hiappevent_destroyprocessor).

**Since**: 18

**Parameters**:

| Parameter | Description |
| -- | -- |
| const char* name | Processor name, which can contain only letters, digits, underscores (_), and dollar signs ($). It cannot start with a digit and cannot exceed 256 characters. |

**Returns**:

| Type | Description |
| -- | -- |
| [HiAppEvent_Processor*](capi-hiappevent-hiappevent-processor.md) | Pointer to the new processor if the API is called successfully; NULL if the name parameter is      invalid. |

### OH_HiAppEvent_SetReportRoute()

```c
int OH_HiAppEvent_SetReportRoute(HiAppEvent_Processor* processor, const char* appId, const char* routeInfo)
```

**Description**

Sets the report route for the processor.

**Since**: 18

**Parameters**:

| Parameter | Description |
| -- | -- |
| [HiAppEvent_Processor](capi-hiappevent-hiappevent-processor.md)* processor | Pointer to the processor, that is, the pointer returned by [OH_HiAppEvent_CreateProcessor](capi-hiappevent-h.md#oh_hiappevent_createprocessor). |
| const char* appId | Application ID of the processor. |
| const char* routeInfo | Server location information. The default value is an empty string. The string length cannot exceed 8 KB. Otherwise, the default value is used. |

**Returns**:

| Type | Description |
| -- | -- |
| int | <ul>          <li>[HIAPPEVENT_SUCCESS](capi-hiappevent-h.md#hiappevent_errorcode) Operation successful.</li>          <li>[HIAPPEVENT_PROCESSOR_IS_NULL](capi-hiappevent-h.md#hiappevent_errorcode) The processor parameter is empty.</li>          <li>[HIAPPEVENT_INVALID_PARAM_VALUE](capi-hiappevent-h.md#hiappevent_errorcode) Invalid parameter value.</li>          <li>[HIAPPEVENT_INVALID_UID](capi-hiappevent-h.md#hiappevent_errorcode) Invalid user ID.</li>          <li>[HIAPPEVENT_INVALID_PARAM_VALUE_LENGTH](capi-hiappevent-h.md#hiappevent_errorcode) Invalid parameter value length.</li>          </ul>      For details, see [HiAppEvent_ErrorCode](capi-hiappevent-h.md#hiappevent_errorcode). |

### OH_HiAppEvent_SetReportPolicy()

```c
int OH_HiAppEvent_SetReportPolicy(HiAppEvent_Processor* processor, int periodReport, int batchReport, bool onStartReport, bool onBackgroundReport)
```

**Description**

Sets the report policy for the processor.

**Since**: 18

**Parameters**:

| Parameter | Description |
| -- | -- |
| [HiAppEvent_Processor](capi-hiappevent-hiappevent-processor.md)* processor | Pointer to the processor, that is, the pointer returned by [OH_HiAppEvent_CreateProcessor](capi-hiappevent-h.md#oh_hiappevent_createprocessor). |
| int periodReport | Period for reporting events, in seconds. The input value must be greater than or equal to 0. |
| int batchReport | Threshold for reporting events. When the number of events reaches the threshold, an event is reported. The value range is [0, 1000]. |
| bool onStartReport | Whether to report events during startup. **true**: yes; **false**: no. |
| bool onBackgroundReport | Whether to report events after an application switches to the background. **true**: yes; **false**: no. |

**Returns**:

| Type | Description |
| -- | -- |
| int | <ul>          <li>[HIAPPEVENT_SUCCESS](capi-hiappevent-h.md#hiappevent_errorcode) Operation successful.</li>          <li>[HIAPPEVENT_PROCESSOR_IS_NULL](capi-hiappevent-h.md#hiappevent_errorcode) The processor parameter is empty.</li>          <li>[HIAPPEVENT_INVALID_PARAM_VALUE](capi-hiappevent-h.md#hiappevent_errorcode) Invalid parameter value.</li>          <li>[HIAPPEVENT_INVALID_UID](capi-hiappevent-h.md#hiappevent_errorcode) Invalid user ID.</li>          </ul>      For details, see [HiAppEvent_ErrorCode](capi-hiappevent-h.md#hiappevent_errorcode). |

### OH_HiAppEvent_SetReportEvent()

```c
int OH_HiAppEvent_SetReportEvent(HiAppEvent_Processor* processor, const char* domain, const char* name, bool isRealTime)
```

**Description**

Sets the report event for the processor.

**Since**: 18

**Parameters**:

| Parameter | Description |
| -- | -- |
| [HiAppEvent_Processor](capi-hiappevent-hiappevent-processor.md)* processor | Pointer to the processor, that is, the pointer returned by [OH_HiAppEvent_CreateProcessor](capi-hiappevent-h.md#oh_hiappevent_createprocessor). |
| const char* domain | Domain of the report event. |
| const char* name | Name of the report event. |
| bool isRealTime | Whether to report events in real time. The value **true** means to report events in real time, and **false** means the opposite. |

**Returns**:

| Type | Description |
| -- | -- |
| int | <ul>          <li>[HIAPPEVENT_SUCCESS](capi-hiappevent-h.md#hiappevent_errorcode) Operation successful.</li>          <li>[HIAPPEVENT_PROCESSOR_IS_NULL](capi-hiappevent-h.md#hiappevent_errorcode) The processor parameter is empty.</li>          <li>[HIAPPEVENT_INVALID_PARAM_VALUE](capi-hiappevent-h.md#hiappevent_errorcode) Invalid parameter value.</li>          <li>[HIAPPEVENT_INVALID_UID](capi-hiappevent-h.md#hiappevent_errorcode) Invalid user ID.</li>          </ul>      For details, see [HiAppEvent_ErrorCode](capi-hiappevent-h.md#hiappevent_errorcode). |

### OH_HiAppEvent_SetCustomConfig()

```c
int OH_HiAppEvent_SetCustomConfig(HiAppEvent_Processor* processor, const char* key, const char* value)
```

**Description**

Sets the custom extension parameters of the processor.

**Since**: 18

**Parameters**:

| Parameter | Description |
| -- | -- |
| [HiAppEvent_Processor](capi-hiappevent-hiappevent-processor.md)* processor | Pointer to the processor, that is, the pointer returned by [OH_HiAppEvent_CreateProcessor](capi-hiappevent-h.md#oh_hiappevent_createprocessor). |
| const char* key | Parameter name, which contains a maximum of 32 characters. |
| const char* value | Parameter value, which contains a maximum of 1024 characters. |

**Returns**:

| Type | Description |
| -- | -- |
| int | <ul>          <li>[HIAPPEVENT_SUCCESS](capi-hiappevent-h.md#hiappevent_errorcode) Operation successful.</li>          <li>[HIAPPEVENT_PROCESSOR_IS_NULL](capi-hiappevent-h.md#hiappevent_errorcode) The processor parameter is empty.</li>          <li>[HIAPPEVENT_INVALID_PARAM_VALUE](capi-hiappevent-h.md#hiappevent_errorcode) Invalid parameter value.</li>          <li>[HIAPPEVENT_INVALID_UID](capi-hiappevent-h.md#hiappevent_errorcode) Invalid user ID.</li>          <li>[HIAPPEVENT_INVALID_PARAM_VALUE_LENGTH](capi-hiappevent-h.md#hiappevent_errorcode) Invalid parameter value length.</li>          </ul>      For details, see [HiAppEvent_ErrorCode](capi-hiappevent-h.md#hiappevent_errorcode). |

### OH_HiAppEvent_SetConfigId()

```c
int OH_HiAppEvent_SetConfigId(HiAppEvent_Processor* processor, int configId)
```

**Description**

Sets the configuration ID of the processor.

**Since**: 18

**Parameters**:

| Parameter | Description |
| -- | -- |
| [HiAppEvent_Processor](capi-hiappevent-hiappevent-processor.md)* processor | Pointer to the processor, that is, the pointer returned by [OH_HiAppEvent_CreateProcessor](capi-hiappevent-h.md#oh_hiappevent_createprocessor). |
| int configId | Configuration ID of the processor, which is a natural number. |

**Returns**:

| Type | Description |
| -- | -- |
| int | <ul>          <li>[HIAPPEVENT_SUCCESS](capi-hiappevent-h.md#hiappevent_errorcode) Operation successful.</li>          <li>[HIAPPEVENT_PROCESSOR_IS_NULL](capi-hiappevent-h.md#hiappevent_errorcode) The processor parameter is empty.</li>          <li>[HIAPPEVENT_INVALID_PARAM_VALUE](capi-hiappevent-h.md#hiappevent_errorcode) Invalid parameter value.</li>          <li>[HIAPPEVENT_INVALID_UID](capi-hiappevent-h.md#hiappevent_errorcode) Invalid user ID.</li>          </ul>      For details, see [HiAppEvent_ErrorCode](capi-hiappevent-h.md#hiappevent_errorcode). |

### OH_HiAppEvent_SetConfigName()

```c
int OH_HiAppEvent_SetConfigName(HiAppEvent_Processor* processor, const char* configName)
```

**Description**

Sets the configuration name of the processor.

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| [HiAppEvent_Processor](capi-hiappevent-hiappevent-processor.md)* processor | Pointer to the processor, that is, the pointer returned by [OH_HiAppEvent_CreateProcessor](capi-hiappevent-h.md#oh_hiappevent_createprocessor). |
| const char* configName | Configuration name of the data processor, which can contain only letters, digits, underscores (_), and dollar signs ($). It cannot start with a digit and cannot exceed 256 characters. |

**Returns**:

| Type | Description |
| -- | -- |
| int | <ul>          <li>[HIAPPEVENT_SUCCESS](capi-hiappevent-h.md#hiappevent_errorcode) Operation successful.</li>          <li>[HIAPPEVENT_PROCESSOR_IS_NULL](capi-hiappevent-h.md#hiappevent_errorcode) The processor parameter is empty.</li>          <li>[HIAPPEVENT_INVALID_PARAM_VALUE](capi-hiappevent-h.md#hiappevent_errorcode) Invalid parameter value.</li>          <li>[HIAPPEVENT_INVALID_UID](capi-hiappevent-h.md#hiappevent_errorcode) Invalid user ID.</li>          <li>[HIAPPEVENT_INVALID_PARAM_VALUE_LENGTH](capi-hiappevent-h.md#hiappevent_errorcode) Invalid parameter value length.</li>          </ul>      For details, see [HiAppEvent_ErrorCode](capi-hiappevent-h.md#hiappevent_errorcode). |

### OH_HiAppEvent_SetReportUserId()

```c
int OH_HiAppEvent_SetReportUserId(HiAppEvent_Processor* processor, const char* const * userIdNames, int size)
```

**Description**

Sets the report user ID of the processor.

**Since**: 18

**Parameters**:

| Parameter | Description |
| -- | -- |
| [HiAppEvent_Processor](capi-hiappevent-hiappevent-processor.md)* processor | Pointer to the processor, that is, the pointer returned by [OH_HiAppEvent_CreateProcessor](capi-hiappevent-h.md#oh_hiappevent_createprocessor). |
| const char* const * userIdNames | Name array of user IDs that can be reported by the processor. |
| int size | Length of the name array of user IDs. |

**Returns**:

| Type | Description |
| -- | -- |
| int | <ul>          <li>[HIAPPEVENT_SUCCESS](capi-hiappevent-h.md#hiappevent_errorcode) Operation successful.</li>          <li>[HIAPPEVENT_PROCESSOR_IS_NULL](capi-hiappevent-h.md#hiappevent_errorcode) The processor parameter is empty.</li>          <li>[HIAPPEVENT_INVALID_PARAM_VALUE](capi-hiappevent-h.md#hiappevent_errorcode) Invalid parameter value.</li>          <li>[HIAPPEVENT_INVALID_UID](capi-hiappevent-h.md#hiappevent_errorcode) Invalid user ID.</li>          <li>[HIAPPEVENT_INVALID_PARAM_VALUE_LENGTH](capi-hiappevent-h.md#hiappevent_errorcode) Invalid parameter value length.</li>          </ul>      For details, see [HiAppEvent_ErrorCode](capi-hiappevent-h.md#hiappevent_errorcode). |

### OH_HiAppEvent_SetReportUserProperty()

```c
int OH_HiAppEvent_SetReportUserProperty(HiAppEvent_Processor* processor, const char* const * userPropertyNames, int size)
```

**Description**

Sets the report user property of the processor.

**Since**: 18

**Parameters**:

| Parameter | Description |
| -- | -- |
| [HiAppEvent_Processor](capi-hiappevent-hiappevent-processor.md)* processor | Pointer to the processor, that is, the pointer returned by [OH_HiAppEvent_CreateProcessor](capi-hiappevent-h.md#oh_hiappevent_createprocessor). |
| const char* const * userPropertyNames | Name array of user properties that can be reported by the processor. |
| int size | Length of the name array of user properties. |

**Returns**:

| Type | Description |
| -- | -- |
| int | <ul>          <li>[HIAPPEVENT_SUCCESS](capi-hiappevent-h.md#hiappevent_errorcode) Operation successful.</li>          <li>[HIAPPEVENT_PROCESSOR_IS_NULL](capi-hiappevent-h.md#hiappevent_errorcode) The processor parameter is empty.</li>          <li>[HIAPPEVENT_INVALID_PARAM_VALUE](capi-hiappevent-h.md#hiappevent_errorcode) Invalid parameter value.</li>          <li>[HIAPPEVENT_INVALID_UID](capi-hiappevent-h.md#hiappevent_errorcode) Invalid user ID.</li>          <li>[HIAPPEVENT_INVALID_PARAM_VALUE_LENGTH](capi-hiappevent-h.md#hiappevent_errorcode) Invalid parameter value length.</li>          </ul>      For details, see [HiAppEvent_ErrorCode](capi-hiappevent-h.md#hiappevent_errorcode). |

### OH_HiAppEvent_AddProcessor()

```c
int64_t OH_HiAppEvent_AddProcessor(HiAppEvent_Processor* processor)
```

**Description**

Adds a processor. You can add a processor to migrate event data to the cloud. You can preset the implementation of the processor on the device and set its properties based on its constraints. Note that the configuration information of **Processor** must be provided by the data processor. Yet, as no data processor is preset in the device for interaction for the moment, migrating events to the cloud is unavailable.

**Since**: 18

**Parameters**:

| Parameter | Description |
| -- | -- |
| [HiAppEvent_Processor](capi-hiappevent-hiappevent-processor.md)* processor | Pointer to the processor, that is, the pointer returned by [OH_HiAppEvent_CreateProcessor](capi-hiappevent-h.md#oh_hiappevent_createprocessor). |

**Returns**:

| Type | Description |
| -- | -- |
| int64_t | <ul>          <li>Unique ID if set is successful. The value is greater than 0.</li>          <li>[HIAPPEVENT_PROCESSOR_IS_NULL](capi-hiappevent-h.md#hiappevent_errorcode): The processor parameter is empty.</li>          <li>[HIAPPEVENT_INVALID_PARAM_VALUE](capi-hiappevent-h.md#hiappevent_errorcode): Invalid parameter value.</li>          <li>[HIAPPEVENT_OPERATE_FAILED](capi-hiappevent-h.md#hiappevent_errorcode): Failed to find or register the data processor name.</li>          <li>[HIAPPEVENT_INVALID_UID](capi-hiappevent-h.md#hiappevent_errorcode): Invalid user ID.</li>          </ul>      For details, see [HiAppEvent_ErrorCode](capi-hiappevent-h.md#hiappevent_errorcode). |

### OH_HiAppEvent_DestroyProcessor()

```c
void OH_HiAppEvent_DestroyProcessor(HiAppEvent_Processor* processor)
```

**Description**

Destroys a processor. Note: If a processor is no longer used, destroy it to release memory to prevent memory leaks. After the processor is destroyed, set its pointer to null.

**Since**: 18

**Parameters**:

| Parameter | Description |
| -- | -- |
| [HiAppEvent_Processor](capi-hiappevent-hiappevent-processor.md)* processor | Pointer to the processor, that is, the pointer returned by [OH_HiAppEvent_CreateProcessor](capi-hiappevent-h.md#oh_hiappevent_createprocessor). |

### OH_HiAppEvent_RemoveProcessor()

```c
int OH_HiAppEvent_RemoveProcessor(int64_t processorId)
```

**Description**

Removes a processor. Once a processor is removed, it stops reporting events. Note: This API only stops the processor reporting events but does not destroy the processor. You can call [OH_HiAppEvent_DestroyProcessor](capi-hiappevent-h.md#oh_hiappevent_destroyprocessor) to destroy the processor and release the memory.

**Since**: 18

**Parameters**:

| Parameter | Description |
| -- | -- |
| int64_t processorId | Unique ID of a processor. |

**Returns**:

| Type | Description |
| -- | -- |
| int | <ul>          <li>[HIAPPEVENT_SUCCESS](capi-hiappevent-h.md#hiappevent_errorcode): Operation successful.</li>          <li>[HIAPPEVENT_PROCESSOR_NOT_FOUND](capi-hiappevent-h.md#hiappevent_errorcode): Failed to find the processor.</li>          <li>[HIAPPEVENT_OPERATE_FAILED](capi-hiappevent-h.md#hiappevent_errorcode): Operation failed.</li>          <li>[HIAPPEVENT_INVALID_UID](capi-hiappevent-h.md#hiappevent_errorcode): Invalid user ID.</li>          </ul>      For details, see [HiAppEvent_ErrorCode](capi-hiappevent-h.md#hiappevent_errorcode). |

### OH_HiAppEvent_CreateConfig()

```c
HiAppEvent_Config* OH_HiAppEvent_CreateConfig(void)
```

**Description**

Creates a pointer to the configuration object that sets the conditions for triggering system events. Note: If the created pointer to the configuration object that sets the conditions for triggering system events is no longer used, destroy it by calling [OH_HiAppEvent_DestroyConfig](capi-hiappevent-h.md#oh_hiappevent_destroyconfig).

**Since**: 15

**Returns**:

| Type | Description |
| -- | -- |
| [HiAppEvent_Config*](capi-hiappevent-hiappevent-config.md) | Pointer to the configuration object that sets the conditions for triggering system events. |

### OH_HiAppEvent_DestroyConfig()

```c
void OH_HiAppEvent_DestroyConfig(HiAppEvent_Config* config)
```

**Description**

Destroys a configuration object. Note: If a configuration object is no longer used, destroy it to release memory to prevent memory leaks. After the object is destroyed, set its pointer to null.

**Since**: 15

**Parameters**:

| Parameter | Description |
| -- | -- |
| [HiAppEvent_Config](capi-hiappevent-hiappevent-config.md)* config | Pointer to the configuration object, that is, the pointer returned by the [OH_HiAppEvent_CreateConfig](capi-hiappevent-h.md#oh_hiappevent_createconfig) API. |

### OH_HiAppEvent_SetConfigItem()

```c
int OH_HiAppEvent_SetConfigItem(HiAppEvent_Config* config, const char* itemName, const char* itemValue)
```

**Description**

Sets the items in the configuration object.

**Since**: 15

**Parameters**:

| Parameter | Description |
| -- | -- |
| [HiAppEvent_Config](capi-hiappevent-hiappevent-config.md)* config | Pointer to the configuration object, that is, the pointer returned by the [OH_HiAppEvent_CreateConfig](capi-hiappevent-h.md#oh_hiappevent_createconfig) API. |
| const char* itemName | Name of the configuration item. |
| const char* itemValue | Value of the configuration item. |

**Returns**:

| Type | Description |
| -- | -- |
| int | <ul>          <li>[HIAPPEVENT_SUCCESS](capi-hiappevent-h.md#hiappevent_errorcode) Operation successful.</li>          <li>[HIAPPEVENT_EVENT_CONFIG_IS_NULL](capi-hiappevent-h.md#hiappevent_errorcode) The input pointer to the configuration object is null.</li>          <li>[HIAPPEVENT_INVALID_PARAM_VALUE](capi-hiappevent-h.md#hiappevent_errorcode) Invalid configuration item.</li>          </ul>      For details, see [HiAppEvent_ErrorCode](capi-hiappevent-h.md#hiappevent_errorcode). |

### OH_HiAppEvent_SetEventConfig()

```c
int OH_HiAppEvent_SetEventConfig(const char* name, HiAppEvent_Config* config)
```

**Description**

Sets event configuration parameters. Configuration items vary depending on events. Currently, only the following events are supported: **MAIN_THREAD_JANK**. (For details about the parameter configuration, see {@link Main Thread Jank Event Overview}.)<br>**MAIN_THREAD_JANK_V2**. (For details about the parameter configuration, see<br>{@link Main Thread Jank Event Overview}.)<br>**EVENT_APP_CRASH**. (For details about the parameter configuration, see {@link Crash Event Overview}.) This event is supported since API version 24.

**Since**: 15

**Parameters**:

| Parameter | Description |
| -- | -- |
| const char* name | Name of the system event. |
| [HiAppEvent_Config](capi-hiappevent-hiappevent-config.md)* config | Pointer to the configuration object, that is, the pointer returned by the [OH_HiAppEvent_CreateConfig](capi-hiappevent-h.md#oh_hiappevent_createconfig) API. |

**Returns**:

| Type | Description |
| -- | -- |
| int | <ul>          <li>[HIAPPEVENT_SUCCESS](capi-hiappevent-h.md#hiappevent_errorcode) Operation successful.</li>          <li>[HIAPPEVENT_INVALID_PARAM_VALUE](capi-hiappevent-h.md#hiappevent_errorcode) Invalid parameter.</li>          </ul>      For details, see [HiAppEvent_ErrorCode](capi-hiappevent-h.md#hiappevent_errorcode). |

### OH_HiAppEvent_ReportFrameworkMemAnomaly()

```c
int OH_HiAppEvent_ReportFrameworkMemAnomaly(enum OH_HiAppEvent_FrameworkType frameworkType, const char* frameworkVersion, const char* description)
```

**Description**

Reports information about abnormal memory usage of the application framework. <br>This API can be called once every minute at most. If the frequency limit is exceeded, the error code **HIAPPEVENT_REPORT_FREQUENCY_EXCEEDED** will be returned. <br>When the application detects that the memory usage of the application framework is abnormal and the operation is successful after this API is called: <br>1. If you have subscribed to the application event whose domain is **HIVIEWDFX** and name is **FW_MEM_ANOMALY**, the application will receive a callback containing the information about the abnormal memory usage of the application framework. <br>2. If you have not subscribed to this application event, the application will not receive the callback containing the information about the abnormal memory usage of the application framework.

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| enum OH_HiAppEvent_FrameworkType frameworkType | Application framework type. |
| const char* frameworkVersion | Pointer to the application framework version. |
| const char* description | Description of the abnormal memory usage of the application framework. |

**Returns**:

| Type | Description |
| -- | -- |
| int | <ul>          <li>[HIAPPEVENT_SUCCESS](capi-hiappevent-h.md#hiappevent_errorcode) Operation succeeded.</li>          <li>[HIAPPEVENT_INVALID_PARAM_VALUE](capi-hiappevent-h.md#hiappevent_errorcode) Invalid parameter value.</li>          <li>[HIAPPEVENT_OPERATE_FAILED](capi-hiappevent-h.md#hiappevent_errorcode) System/application event write failed, or timestamp retrieval              failed.</li>          <li>[HIAPPEVENT_REPORT_FREQUENCY_EXCEEDED](capi-hiappevent-h.md#hiappevent_errorcode) The reporting frequency exceeds the limit.</li>          </ul>      For details, see [HiAppEvent_ErrorCode](capi-hiappevent-h.md#hiappevent_errorcode). |

### OH_HiAppEvent_ExternalLogCapacityReachedCallback()

```c
typedef void (*OH_HiAppEvent_ExternalLogCapacityReachedCallback)(OH_HiAppEvent_ExternalLog* externalLogArr, uint32_t arrLen)
```

**Description**

The parameter of OH_HiAppEvent_RegExternalLogCapacityReachedCallback function which acts as the callback function when external log directory capacity is reached.

**Since**: 26.1.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_HiAppEvent_ExternalLog](capi-hiappevent-oh-hiappevent-externallog.md)\* externalLogArr | The array of external log info. |
| uint32_t arrLen | The length of externalLogArr. |

### OH_HiAppEvent_RegExternalLogCapacityReachedCallback()

```c
int OH_HiAppEvent_RegExternalLogCapacityReachedCallback(OH_HiAppEvent_ExternalLogCapacityReachedCallback callback)
```

**Description**

The interface to set the callback when external log directory capacity is reached.

**Since**: 26.1.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_HiAppEvent_ExternalLogCapacityReachedCallback](capi-hiappevent-h.md#oh_hiappevent_externallogcapacityreachedcallback) callback | The callback function when external log directory capacity is reached. |

**Returns**:

| Type | Description |
| -- | -- |
| int | set callback result.          [HIAPPEVENT_SUCCESS](capi-hiappevent-h.md#hiappevent_errorcode) The operation is successful.          [HIAPPEVENT_OPERATE_FAILED](capi-hiappevent-h.md#hiappevent_errorcode) The operation failed. |


