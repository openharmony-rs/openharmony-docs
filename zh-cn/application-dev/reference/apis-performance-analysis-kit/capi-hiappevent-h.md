# hiappevent.h

## 概述

HiAppEvent模块的应用事件打点函数定义。在执行应用事件打点之前，开发者必须先构造一个参数列表对象来存储输入的事件参数，并指定事件领域、事件名称和事件类型。<p>事件领域：用于标识事件打点的领域的字符串。<p>事件名称：用于标识事件打点的名称的字符串。<p>事件类型：故障、统计、安全、行为。<p>参数列表：用于存储事件参数的链表，每个参数由参数名和参数值组成。

**引用文件：** &lt;hiappevent/hiappevent.h&gt;

**库：** libhiappevent_ndk.z.so

**系统能力：** SystemCapability.HiviewDFX.HiAppEvent

**起始版本：** 8

**相关模块：** [HiAppEvent](capi-hiappevent.md)

## 汇总

### 结构体

| 名称 | typedef关键字 | 描述 |
| -- | -- | -- |
| [HiAppEvent_AppEventInfo](capi-hiappevent-hiappevent-appeventinfo.md) | HiAppEvent_AppEventInfo | 单个事件信息，包含事件领域，事件名称，事件类型和json格式字符串表示的事件中携带的自定义参数列表。 |
| [HiAppEvent_AppEventGroup](capi-hiappevent-hiappevent-appeventgroup.md) | HiAppEvent_AppEventGroup | 一组事件信息，包含事件组的名称，按名称分组的单个事件信息数组，事件数组的长度。 |
| [ParamListNode*](capi-hiappevent-paramlistnode8h.md) | ParamList | 事件参数列表节点。 |
| [HiAppEvent_Watcher](capi-hiappevent-hiappevent-watcher.md) | HiAppEvent_Watcher | 用于接收app事件的监听器。 |
| [HiAppEvent_Processor](capi-hiappevent-hiappevent-processor.md) | HiAppEvent_Processor | 用于处理app事件上报的处理者。 |
| [HiAppEvent_Config](capi-hiappevent-hiappevent-config.md) | HiAppEvent_Config | 用于设置系统事件触发条件的配置对象。 |

### 枚举

| 名称 | typedef关键字 | 描述 |
| -- | -- | -- |
| [HiAppEvent_ErrorCode](#hiappevent_errorcode) | HiAppEvent_ErrorCode | 错误码定义。 |
| [EventType](#eventtype) | - | 事件类型。建议开发者根据不同的使用场景选择不同的事件类型。 |

### 函数

| 名称 | typedef关键字 | 描述 |
| -- | -- | -- |
| [typedef void (\*OH_HiAppEvent_OnReceive)(const char* domain, const struct HiAppEvent_AppEventGroup* appEventGroups, uint32_t groupLen)](#oh_hiappevent_onreceive) | OH_HiAppEvent_OnReceive | 监听器接收到事件后，将触发该回调，将事件内容传递给调用方。注意：回调中的指针所指对象的生命周期仅限于该回调函数内，请勿在该回调函数外直接使用该指针，若需缓存该信息，请对指针指向的内容进行深拷贝。 |
| [typedef void (\*OH_HiAppEvent_OnTrigger)(int row, int size)](#oh_hiappevent_ontrigger) | OH_HiAppEvent_OnTrigger | 监听器收到事件后，若监听器中未设置OH_HiAppEvent_OnReceive回调，将保存该事件。<br> 当保存的事件满足通过OH_HiAppEvent_SetTriggerCondition设定的条件后，将触发该回调。回调结束后，当新保存的事件消息再次满足设定的条件后，将再次进行回调。 |
| [typedef void (\*OH_HiAppEvent_OnTake)(const char* const *events, uint32_t eventLen)](#oh_hiappevent_ontake) | OH_HiAppEvent_OnTake | 使用OH_HiAppEvent_TakeWatcherData获取监听器接收到的事件时，监听器接收到的事件将通过该回调函数传递给调用者。注意：回调中的指针所指对象的生命周期仅限于该回调函数内，请勿在该回调函数外直接使用该指针。若需缓存该信息，请对指针指向的内容进行深拷贝。 |
| [ParamList OH_HiAppEvent_CreateParamList(void)](#oh_hiappevent_createparamlist) | - | 创建一个指向参数列表对象的指针。 |
| [void OH_HiAppEvent_DestroyParamList(ParamList list)](#oh_hiappevent_destroyparamlist) | - | 销毁一个指向参数列表对象的指针，释放其分配内存。 |
| [ParamList OH_HiAppEvent_AddBoolParam(ParamList list, const char* name, bool boolean)](#oh_hiappevent_addboolparam) | - | 添加一个布尔参数到参数列表中。 |
| [ParamList OH_HiAppEvent_AddBoolArrayParam(ParamList list, const char* name, const bool* booleans, int arrSize)](#oh_hiappevent_addboolarrayparam) | - | 添加一个布尔数组参数到参数列表中。 |
| [ParamList OH_HiAppEvent_AddInt8Param(ParamList list, const char* name, int8_t num)](#oh_hiappevent_addint8param) | - | 添加一个int8_t参数到参数列表中。 |
| [ParamList OH_HiAppEvent_AddInt8ArrayParam(ParamList list, const char* name, const int8_t* nums, int arrSize)](#oh_hiappevent_addint8arrayparam) | - | 添加一个int8_t数组参数到参数列表中。 |
| [ParamList OH_HiAppEvent_AddInt16Param(ParamList list, const char* name, int16_t num)](#oh_hiappevent_addint16param) | - | 添加一个int16_t参数到参数列表中。 |
| [ParamList OH_HiAppEvent_AddInt16ArrayParam(ParamList list, const char* name, const int16_t* nums, int arrSize)](#oh_hiappevent_addint16arrayparam) | - | 添加一个int16_t数组参数到参数列表中。 |
| [ParamList OH_HiAppEvent_AddInt32Param(ParamList list, const char* name, int32_t num)](#oh_hiappevent_addint32param) | - | 添加一个int32_t参数到参数列表中。 |
| [ParamList OH_HiAppEvent_AddInt32ArrayParam(ParamList list, const char* name, const int32_t* nums, int arrSize)](#oh_hiappevent_addint32arrayparam) | - | 添加一个int32_t数组参数到参数列表中。 |
| [ParamList OH_HiAppEvent_AddInt64Param(ParamList list, const char* name, int64_t num)](#oh_hiappevent_addint64param) | - | 添加一个int64_t参数到参数列表中。 |
| [ParamList OH_HiAppEvent_AddInt64ArrayParam(ParamList list, const char* name, const int64_t* nums, int arrSize)](#oh_hiappevent_addint64arrayparam) | - | 添加一个int64_t数组参数到参数列表中。 |
| [ParamList OH_HiAppEvent_AddFloatParam(ParamList list, const char* name, float num)](#oh_hiappevent_addfloatparam) | - | 添加一个float参数到参数列表中。 |
| [ParamList OH_HiAppEvent_AddFloatArrayParam(ParamList list, const char* name, const float* nums, int arrSize)](#oh_hiappevent_addfloatarrayparam) | - | 添加一个float数组参数到参数列表中。 |
| [ParamList OH_HiAppEvent_AddDoubleParam(ParamList list, const char* name, double num)](#oh_hiappevent_adddoubleparam) | - | 添加一个double参数到参数列表中。 |
| [ParamList OH_HiAppEvent_AddDoubleArrayParam(ParamList list, const char* name, const double* nums, int arrSize)](#oh_hiappevent_adddoublearrayparam) | - | 添加一个double数组参数到参数列表中。 |
| [ParamList OH_HiAppEvent_AddStringParam(ParamList list, const char* name, const char* str)](#oh_hiappevent_addstringparam) | - | 添加一个字符串参数到参数列表中。 |
| [ParamList OH_HiAppEvent_AddStringArrayParam(ParamList list, const char* name, const char * const *strs, int arrSize)](#oh_hiappevent_addstringarrayparam) | - | 添加一个字符串数组参数到参数列表中。 |
| [int OH_HiAppEvent_Write(const char* domain, const char* name, enum EventType type, const ParamList list)](#oh_hiappevent_write) | - | 实现对参数为列表类型的应用事件打点。在应用事件打点前，该接口会先对该事件的参数进行校验。如果校验成功，则接口会将事件写入事件文件。 |
| [bool OH_HiAppEvent_Configure(const char* name, const char* value)](#oh_hiappevent_configure) | - | 实现应用事件打点的配置功能。应用事件打点配置接口，用于配置事件打点开关、事件文件目录存储配额大小等功能。 |
| [HiAppEvent_Watcher* OH_HiAppEvent_CreateWatcher(const char* name)](#oh_hiappevent_createwatcher) | - | 创建一个用于监听app事件的监听器。注意：创建的监听器不再使用后必须通过调用OH_HiAppEvent_DestroyWatcher接口进行销毁。 |
| [void OH_HiAppEvent_DestroyWatcher(HiAppEvent_Watcher* watcher)](#oh_hiappevent_destroywatcher) | - | 销毁已创建的监听器。注意：已创建的监听器不再使用后，需要将其销毁，释放内存，防止内存泄漏，销毁后需将对应指针置空。 |
| [int OH_HiAppEvent_SetTriggerCondition(HiAppEvent_Watcher* watcher, int row, int size, int timeOut)](#oh_hiappevent_settriggercondition) | - | 用于设置监听器OH_HiAppEvent_OnTrigger回调的触发条件。<br> 分别可以从监视器新接收事件数量、新接收事件大小、onTrigger触发超时时间，设置触发条件。调用方应至少保证从一个方面设置触发条件。 |
| [int OH_HiAppEvent_SetAppEventFilter(HiAppEvent_Watcher* watcher, const char* domain, uint8_t eventTypes,const char* const *names, int namesLen)](#oh_hiappevent_setappeventfilter) | - | 用于设置监听器需要监听的事件的类型。该函数可以重复调用，可添加多个过滤规则，而非替换，监听器将收到满足任一过滤规则的事件的通知。 |
| [int OH_HiAppEvent_SetWatcherOnTrigger(HiAppEvent_Watcher* watcher, OH_HiAppEvent_OnTrigger onTrigger)](#oh_hiappevent_setwatcherontrigger) | - | 用于设置监听器onTrigger回调的接口。<br> 如果未设置OnReceive回调或已将其设置为nullptr，则将保存观察者接收到的应用事件。当保存的应用事件满足onTrigger回调的触发条件时，将调用onTrigger回调。 |
| [int OH_HiAppEvent_SetWatcherOnReceive(HiAppEvent_Watcher* watcher, OH_HiAppEvent_OnReceive onReceive)](#oh_hiappevent_setwatcheronreceive) | - | 用于设置监听器onReceive回调函数的接口。当监听器监听到相应事件后，onReceive回调函数将被调用。 |
| [int OH_HiAppEvent_TakeWatcherData(HiAppEvent_Watcher* watcher, uint32_t eventNum, OH_HiAppEvent_OnTake onTake)](#oh_hiappevent_takewatcherdata) | - | 用于获取监听器收到后保存的事件。 |
| [int OH_HiAppEvent_AddWatcher(HiAppEvent_Watcher* watcher)](#oh_hiappevent_addwatcher) | - | 添加监听器的接口，监听器开始监听系统消息。 |
| [int OH_HiAppEvent_RemoveWatcher(HiAppEvent_Watcher* watcher)](#oh_hiappevent_removewatcher) | - | 移除监听器的接口，监听器停止监听系统消息。注意：该接口仅仅使监听器停止监听系统消息，并未销毁该监听器，该监听器依然常驻内存，直至调用OH_HiAppEvent_DestroyWatcher接口，内存才会释放。 |
| [void OH_HiAppEvent_ClearData()](#oh_hiappevent_cleardata) | - | 清除所有监视器保存的所有事件。 |
| [HiAppEvent_Processor* OH_HiAppEvent_CreateProcessor(const char* name)](#oh_hiappevent_createprocessor) | - | 创建一个用于处理app事件上报的处理者。注意：创建的处理者不再使用后必须通过调用OH_HiAppEvent_DestroyProcessor接口进行销毁。 |
| [int OH_HiAppEvent_SetReportRoute(HiAppEvent_Processor* processor, const char* appId, const char* routeInfo)](#oh_hiappevent_setreportroute) | - | 设置处理者事件上报路由的接口。 |
| [int OH_HiAppEvent_SetReportPolicy(HiAppEvent_Processor* processor, int periodReport, int batchReport,bool onStartReport, bool onBackgroundReport)](#oh_hiappevent_setreportpolicy) | - | 设置处理者事件上报策略的接口。 |
| [int OH_HiAppEvent_SetReportEvent(HiAppEvent_Processor* processor, const char* domain, const char* name,bool isRealTime)](#oh_hiappevent_setreportevent) | - | 设置处理者上报事件的接口。 |
| [int OH_HiAppEvent_SetCustomConfig(HiAppEvent_Processor* processor, const char* key, const char* value)](#oh_hiappevent_setcustomconfig) | - | 设置处理者自定义扩展参数的接口。 |
| [int OH_HiAppEvent_SetConfigId(HiAppEvent_Processor* processor, int configId)](#oh_hiappevent_setconfigid) | - | 设置处理者配置id的接口。 |
| [int OH_HiAppEvent_SetConfigName(HiAppEvent_Processor* processor, const char* configName)](#oh_hiappevent_setconfigname) | - | 设置处理者的配置名称的接口。 |
| [int OH_HiAppEvent_SetReportUserId(HiAppEvent_Processor* processor, const char* const * userIdNames, int size)](#oh_hiappevent_setreportuserid) | - | 设置处理者用户ID的接口。 |
| [int OH_HiAppEvent_SetReportUserProperty(HiAppEvent_Processor* processor, const char* const * userPropertyNames,int size)](#oh_hiappevent_setreportuserproperty) | - | 设置处理者用户属性的接口。 |
| [int64_t OH_HiAppEvent_AddProcessor(HiAppEvent_Processor* processor)](#oh_hiappevent_addprocessor) | - | 添加数据处理者的接口。开发者可添加数据处理者，用于提供事件上云功能。数据处理者的实现可预置在设备中，开发者可根据数据处理者的约束设置属性。注意：Processor的配置信息需要由数据处理者提供，目前设备内暂未预置可供交互的数据处理者，因此当前事件上云功能不可用。 |
| [void OH_HiAppEvent_DestroyProcessor(HiAppEvent_Processor* processor)](#oh_hiappevent_destroyprocessor) | - | 销毁已创建的数据处理者。注意：已创建的处理者不再使用后，需要将其销毁，释放内存，防止内存泄漏，销毁后需将对应指针置空。 |
| [int OH_HiAppEvent_RemoveProcessor(int64_t processorId)](#oh_hiappevent_removeprocessor) | - | 移除数据处理者的接口，处理者停止上报事件。注意：该接口仅仅使处理者停止上报事件，并未销毁该处理者，该处理者依然常驻内存，直至调用OH_HiAppEvent_DestroyProcessor接口，内存才会释放。 |
| [HiAppEvent_Config* OH_HiAppEvent_CreateConfig(void)](#oh_hiappevent_createconfig) | - | 创建一个指向设置系统事件触发条件的配置对象的指针。 |
| [void OH_HiAppEvent_DestroyConfig(HiAppEvent_Config* config)](#oh_hiappevent_destroyconfig) | - | 销毁已创建的配置对象。注意：已创建的配置对象不再使用后，需要将其销毁，释放内存，防止内存泄漏，销毁后需要将对应指针置空。 |
| [int OH_HiAppEvent_SetConfigItem(HiAppEvent_Config* config, const char* itemName, const char* itemValue)](#oh_hiappevent_setconfigitem) | - | 设置配置对象中的配置项。 |
| [int OH_HiAppEvent_SetEventConfig(const char* name, HiAppEvent_Config* config)](#oh_hiappevent_seteventconfig) | - | 设定系统事件订阅触发条件。 |

## 枚举类型说明

### HiAppEvent_ErrorCode

```
enum HiAppEvent_ErrorCode
```

**描述**

错误码定义。

**起始版本：** 15

| 枚举项 | 描述                      |
| -- |-------------------------|
| HIAPPEVENT_SUCCESS = 0 | 操作成功。                   |
| HIAPPEVENT_INVALID_PARAM_VALUE_LENGTH = 4 | 参数值长度无效。<br>**起始版本：** 18 |
| HIAPPEVENT_PROCESSOR_IS_NULL = -7 | 事件处理者为空。<br>**起始版本：** 18                        |
| HIAPPEVENT_PROCESSOR_NOT_FOUND = -8 | 事件处理者不存在。<br>**起始版本：** 18                        |
| HIAPPEVENT_INVALID_PARAM_VALUE = -9 | 参数值无效。                  |
| HIAPPEVENT_EVENT_CONFIG_IS_NULL = -10 | 事件配置为空。                 |
| HIAPPEVENT_OPERATE_FAILED = -100 | 操作失败。<br>**起始版本：** 18                        |
| HIAPPEVENT_INVALID_UID = -200 | 无效的用户标识。<br>**起始版本：** 18                        |

### EventType

```
enum EventType
```

**描述**

事件类型。建议开发者根据不同的使用场景选择不同的事件类型。

**起始版本：** 8

| 枚举项 | 描述 |
| -- | -- |
| FAULT = 1 | 故障事件类型。 |
| STATISTIC = 2 | 统计事件类型。 |
| SECURITY = 3 | 安全事件类型。 |
| BEHAVIOR = 4 | 行为事件类型。 |


## 函数说明

### OH_HiAppEvent_OnReceive()

```
typedef void (*OH_HiAppEvent_OnReceive)(const char* domain, const struct HiAppEvent_AppEventGroup* appEventGroups, uint32_t groupLen)
```

**描述**

监听器接收到事件后，将触发该回调，将事件内容传递给调用方。注意：回调中的指针所指对象的生命周期仅限于该回调函数内，请勿在该回调函数外直接使用该指针，若需缓存该信息，请对指针指向的内容进行深拷贝。

**起始版本：** 12


**参数：**

| 参数项 | 描述 |
| -- | -- |
| const char* domain | 接收到的app事件的领域。 |
| [ const struct HiAppEvent_AppEventGroup](capi-hiappevent-hiappevent-appeventgroup.md)* appEventGroups | 按照不同事件名称分组的事件组数组。 |
|  uint32_t groupLen | 事件组数组的长度。 |

### OH_HiAppEvent_OnTrigger()

```
typedef void (*OH_HiAppEvent_OnTrigger)(int row, int size)
```

**描述**

监听器收到事件后，若监听器中未设置OH_HiAppEvent_OnReceive回调，将保存该事件。<br> 当保存的事件满足通过OH_HiAppEvent_SetTriggerCondition设定的条件后，将触发该回调。回调结束后，当新保存的事件消息再次满足设定的条件后，将再次进行回调。

**起始版本：** 12


**参数：**

| 参数项 | 描述 |
| -- | -- |
| int row | 监听器新接收到的事件消息的数量。 |
|  int size | 监听器新接收的事件消息的大小总和（单个事件大小计算方式为：将消息转换为json字符串后，字符串的长度）。 |

### OH_HiAppEvent_OnTake()

```
typedef void (*OH_HiAppEvent_OnTake)(const char* const *events, uint32_t eventLen)
```

**描述**

使用OH_HiAppEvent_TakeWatcherData获取监听器接收到的事件时，监听器接收到的事件将通过该回调函数传递给调用者。注意：回调中的指针所指对象的生命周期仅限于该回调函数内，请勿在该回调函数外直接使用该指针。若需缓存该信息，请对指针指向的内容进行深拷贝。

**起始版本：** 12


**参数：**

| 参数项 | 描述 |
| -- | -- |
| const char* const *events | json字符串格式的事件数组。 |
|  uint32_t eventLen | 事件数组大小。 |

### OH_HiAppEvent_CreateParamList()

```
ParamList OH_HiAppEvent_CreateParamList(void)
```

**描述**

创建一个指向参数列表对象的指针。

**起始版本：** 8

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ParamList](capi-hiappevent-paramlistnode8h.md) | 指向参数列表对象的指针。 |

### OH_HiAppEvent_DestroyParamList()

```
void OH_HiAppEvent_DestroyParamList(ParamList list)
```

**描述**

销毁一个指向参数列表对象的指针，释放其分配内存。

**起始版本：** 8


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ParamList](capi-hiappevent-paramlistnode8h.md) list | 参数列表对象指针。 |

### OH_HiAppEvent_AddBoolParam()

```
ParamList OH_HiAppEvent_AddBoolParam(ParamList list, const char* name, bool boolean)
```

**描述**

添加一个布尔参数到参数列表中。

**起始版本：** 8


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ParamList](capi-hiappevent-paramlistnode8h.md) list | 需要添加参数的参数列表指针。 |
| const char* name | 需要添加的参数名称。 |
| bool boolean | 需要添加的布尔参数值。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ParamList](capi-hiappevent-paramlistnode8h.md) | 添加参数后的参数列表指针。 |

### OH_HiAppEvent_AddBoolArrayParam()

```
ParamList OH_HiAppEvent_AddBoolArrayParam(ParamList list, const char* name, const bool* booleans, int arrSize)
```

**描述**

添加一个布尔数组参数到参数列表中。

**起始版本：** 8


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ParamList](capi-hiappevent-paramlistnode8h.md) list | 需要添加参数的参数列表指针。 |
| const char* name | 需要添加的参数名称。 |
| const bool* booleans | 需要添加的布尔数组参数值。 |
| int arrSize | 需要添加的参数数组大小。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ParamList](capi-hiappevent-paramlistnode8h.md) | 添加参数后的参数列表指针。 |

### OH_HiAppEvent_AddInt8Param()

```
ParamList OH_HiAppEvent_AddInt8Param(ParamList list, const char* name, int8_t num)
```

**描述**

添加一个int8_t参数到参数列表中。

**起始版本：** 8


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ParamList](capi-hiappevent-paramlistnode8h.md) list | 需要添加参数的参数列表指针。 |
| const char* name | 需要添加的参数名称。 |
| int8_t num | 需要添加的int8_t参数值。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ParamList](capi-hiappevent-paramlistnode8h.md) | 添加参数后的参数列表指针。 |

### OH_HiAppEvent_AddInt8ArrayParam()

```
ParamList OH_HiAppEvent_AddInt8ArrayParam(ParamList list, const char* name, const int8_t* nums, int arrSize)
```

**描述**

添加一个int8_t数组参数到参数列表中。

**起始版本：** 8


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ParamList](capi-hiappevent-paramlistnode8h.md) list | 需要添加参数的参数列表指针。 |
| const char* name | 需要添加的参数名称。 |
| const int8_t* nums | 需要添加的int8_t数组参数值。 |
| int arrSize | 需要添加的参数数组大小。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ParamList](capi-hiappevent-paramlistnode8h.md) | 添加参数后的参数列表指针。 |

### OH_HiAppEvent_AddInt16Param()

```
ParamList OH_HiAppEvent_AddInt16Param(ParamList list, const char* name, int16_t num)
```

**描述**

添加一个int16_t参数到参数列表中。

**起始版本：** 8


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ParamList](capi-hiappevent-paramlistnode8h.md) list | 需要添加参数的参数列表指针。 |
| const char* name | 需要添加的参数名称。 |
| int16_t num | 需要添加的int16_t参数值。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ParamList](capi-hiappevent-paramlistnode8h.md) | 添加参数后的参数列表指针。 |

### OH_HiAppEvent_AddInt16ArrayParam()

```
ParamList OH_HiAppEvent_AddInt16ArrayParam(ParamList list, const char* name, const int16_t* nums, int arrSize)
```

**描述**

添加一个int16_t数组参数到参数列表中。

**起始版本：** 8


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ParamList](capi-hiappevent-paramlistnode8h.md) list | 需要添加参数的参数列表指针。 |
| const char* name | 需要添加的参数名称。 |
| const int16_t* nums | 需要添加的int16_t数组参数值。 |
| int arrSize | 需要添加的参数数组大小。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ParamList](capi-hiappevent-paramlistnode8h.md) | 添加参数后的参数列表指针。 |

### OH_HiAppEvent_AddInt32Param()

```
ParamList OH_HiAppEvent_AddInt32Param(ParamList list, const char* name, int32_t num)
```

**描述**

添加一个int32_t参数到参数列表中。

**起始版本：** 8


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ParamList](capi-hiappevent-paramlistnode8h.md) list | 需要添加参数的参数列表指针。 |
| const char* name | 需要添加的参数名称。 |
| int32_t num | 需要添加的int32_t参数值。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ParamList](capi-hiappevent-paramlistnode8h.md) | 添加参数后的参数列表指针。 |

### OH_HiAppEvent_AddInt32ArrayParam()

```
ParamList OH_HiAppEvent_AddInt32ArrayParam(ParamList list, const char* name, const int32_t* nums, int arrSize)
```

**描述**

添加一个int32_t数组参数到参数列表中。

**起始版本：** 8


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ParamList](capi-hiappevent-paramlistnode8h.md) list | 需要添加参数的参数列表指针。 |
| const char* name | 需要添加的参数名称。 |
| const int32_t* nums | 需要添加的int32_t数组参数值。 |
| int arrSize | 需要添加的参数数组大小。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ParamList](capi-hiappevent-paramlistnode8h.md) | 添加参数后的参数列表指针。 |

### OH_HiAppEvent_AddInt64Param()

```
ParamList OH_HiAppEvent_AddInt64Param(ParamList list, const char* name, int64_t num)
```

**描述**

添加一个int64_t参数到参数列表中。

**起始版本：** 8


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ParamList](capi-hiappevent-paramlistnode8h.md) list | 需要添加参数的参数列表指针。 |
| const char* name | 需要添加的参数名称。 |
| int64_t num | 需要添加的int64_t参数值。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ParamList](capi-hiappevent-paramlistnode8h.md) | 添加参数后的参数列表指针。 |

### OH_HiAppEvent_AddInt64ArrayParam()

```
ParamList OH_HiAppEvent_AddInt64ArrayParam(ParamList list, const char* name, const int64_t* nums, int arrSize)
```

**描述**

添加一个int64_t数组参数到参数列表中。

**起始版本：** 8


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ParamList](capi-hiappevent-paramlistnode8h.md) list | 需要添加参数的参数列表指针。 |
| const char* name | 需要添加的参数名称。 |
| const int64_t* nums | 需要添加的int64_t数组参数值。 |
| int arrSize | 需要添加的参数数组大小。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ParamList](capi-hiappevent-paramlistnode8h.md) | 添加参数后的参数列表指针。 |

### OH_HiAppEvent_AddFloatParam()

```
ParamList OH_HiAppEvent_AddFloatParam(ParamList list, const char* name, float num)
```

**描述**

添加一个float参数到参数列表中。

**起始版本：** 8


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ParamList](capi-hiappevent-paramlistnode8h.md) list | 需要添加参数的参数列表指针。 |
| const char* name | 需要添加的参数名称。 |
| float num | 需要添加的float参数值。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ParamList](capi-hiappevent-paramlistnode8h.md) | 添加参数后的参数列表指针。 |

### OH_HiAppEvent_AddFloatArrayParam()

```
ParamList OH_HiAppEvent_AddFloatArrayParam(ParamList list, const char* name, const float* nums, int arrSize)
```

**描述**

添加一个float数组参数到参数列表中。

**起始版本：** 8


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ParamList](capi-hiappevent-paramlistnode8h.md) list | 需要添加参数的参数列表指针。 |
| const char* name | 需要添加的参数名称。 |
| const float* nums | 需要添加的float数组参数值。 |
| int arrSize | 需要添加的参数数组大小。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ParamList](capi-hiappevent-paramlistnode8h.md) | 添加参数后的参数列表指针。 |

### OH_HiAppEvent_AddDoubleParam()

```
ParamList OH_HiAppEvent_AddDoubleParam(ParamList list, const char* name, double num)
```

**描述**

添加一个double参数到参数列表中。

**起始版本：** 8


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ParamList](capi-hiappevent-paramlistnode8h.md) list | 需要添加参数的参数列表指针。 |
| const char* name | 需要添加的参数名称。 |
| double num | 需要添加的double参数值。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ParamList](capi-hiappevent-paramlistnode8h.md) | 添加参数后的参数列表指针。 |

### OH_HiAppEvent_AddDoubleArrayParam()

```
ParamList OH_HiAppEvent_AddDoubleArrayParam(ParamList list, const char* name, const double* nums, int arrSize)
```

**描述**

添加一个double数组参数到参数列表中。

**起始版本：** 8


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ParamList](capi-hiappevent-paramlistnode8h.md) list | 需要添加参数的参数列表指针。 |
| const char* name | 需要添加的参数名称。 |
| const double* nums | 需要添加的double数组参数值。 |
| int arrSize | 需要添加的参数数组大小。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ParamList](capi-hiappevent-paramlistnode8h.md) | 添加参数后的参数列表指针。 |

### OH_HiAppEvent_AddStringParam()

```
ParamList OH_HiAppEvent_AddStringParam(ParamList list, const char* name, const char* str)
```

**描述**

添加一个字符串参数到参数列表中。

**起始版本：** 8


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ParamList](capi-hiappevent-paramlistnode8h.md) list | 需要添加参数的参数列表指针。 |
| const char* name | 需要添加的参数名称。 |
| const char* str | 需要添加的字符串参数值。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ParamList](capi-hiappevent-paramlistnode8h.md) | 添加参数后的参数列表指针。 |

### OH_HiAppEvent_AddStringArrayParam()

```
ParamList OH_HiAppEvent_AddStringArrayParam(ParamList list, const char* name, const char * const *strs, int arrSize)
```

**描述**

添加一个字符串数组参数到参数列表中。

**起始版本：** 8


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ParamList](capi-hiappevent-paramlistnode8h.md) list | 需要添加参数的参数列表指针。 |
| const char* name | 需要添加的参数名称。 |
| const char * const *strs | 需要添加的字符串数组参数值。 |
| int arrSize | 需要添加的参数数组大小。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ParamList](capi-hiappevent-paramlistnode8h.md) | 添加参数后的参数列表指针。 |

### OH_HiAppEvent_Write()

```
int OH_HiAppEvent_Write(const char* domain, const char* name, enum EventType type, const ParamList list)
```

**描述**

实现对参数为列表类型的应用事件打点。在应用事件打点前，该接口会先对该事件的参数进行校验。如果校验成功，则接口会将事件写入事件文件。

**起始版本：** 8


**参数：**

| 参数项 | 描述 |
| -- | -- |
| const char* domain | 事件领域。开发者可以根据需要自定义事件领域。<br> 事件领域名称支持数字、字母、下划线字符，需要以字母开头且不能以下划线结尾，长度非空且不超过32个字符。 |
| const char* name | 事件名称。开发者可以根据需要自定义事件名称。<br> 首字符必须为字母字符或$字符，中间字符必须为数字字符、字母字符或下划线字符，结尾字符必须为数字字符或字母字符，长度非空且不超过48个字符。 |
| enum [EventType](capi-hiappevent-h.md#eventtype) type | 事件类型，在[EventType](capi-hiappevent-h.md#eventtype)中定义。 |
| [const ParamList](capi-hiappevent-paramlistnode8h.md) list | 事件参数列表，每个参数由参数名和参数值组成，其规格定义如下：<br> 1、参数名为字符串类型。<br> 首字符必须为字母字符或$字符，中间字符必须为数字字符、字母字符或下划线字符，结尾字符必须为数字字符或字母字符，长度非空且不超过32个字符。<br> 2、参数值支持字符串、数值、布尔、数组类型。字符串类型参数长度需在8*1024个字符以内，超出会做丢弃处理；<br> 数组类型参数中的元素类型只能为字符串、数值、布尔中的一种，且元素个数需在100以内，超出会做丢弃处理。<br> 3、参数个数需在32个以内，超出的参数会做丢弃处理。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int | 如果事件参数校验成功，则返回0，将事件写入事件文件；<br>         如果事件中存在无效参数，则返回正值，丢弃无效参数后将事件写入事件文件；<br>         如果事件参数校验失败，则返回负值，并且事件将不会写入事件文件。<br>          0 事件参数校验成功。<br>          -1 非法的事件名称。<br>          -4 非法的事件领域名称。<br>          -99 打点功能被关闭。<br>          1 非法的事件参数名称。<br>          4 非法的事件参数字符串长度。<br>          5 非法的事件参数数量。<br>          6 非法的事件参数数组长度。<br>          8 重复的事件参数名称。 |

### OH_HiAppEvent_Configure()

```
bool OH_HiAppEvent_Configure(const char* name, const char* value)
```

**描述**

实现应用事件打点的配置功能。应用事件打点配置接口，用于配置事件打点开关、事件文件目录存储配额大小等功能。

**起始版本：** 8


**参数：**

| 参数项 | 描述                                                                                                             |
| -- |----------------------------------------------------------------------------------------------------------------|
| const char* name | 配置项名称。名称可填[DISABLE](capi-hiappevent-cfg-h.md#disable)和[MAX_STORAGE](capi-hiappevent-cfg-h.md#max_storage)。     |
| const char* value | 配置项值。如果配置项名称是[DISABLE](capi-hiappevent-cfg-h.md#disable)，值可以填“true”或者“false”；<br> 如果配置项名称是[MAX_STORAGE](capi-hiappevent-cfg-h.md#max_storage)，配额值字符串只由数字字符和大小单位字符（单位字符支持[b |k|kb|m|mb|g|gb|t|tb]，不区分大小写）构成。<br> 配额值字符串必须以数字开头，后面可以选择不传单位字符（默认使用byte作为单位），或者以单位字符结尾。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| bool | 配置结果。如果配置成功，则返回true；如果配置失败则返回false。 |

### OH_HiAppEvent_CreateWatcher()

```
HiAppEvent_Watcher* OH_HiAppEvent_CreateWatcher(const char* name)
```

**描述**

创建一个用于监听app事件的监听器。注意：创建的监听器不再使用后必须通过调用OH_HiAppEvent_DestroyWatcher接口进行销毁。

**起始版本：** 12


**参数：**

| 参数项 | 描述 |
| -- | -- |
| const char* name | 监听器名称。 |

**返回：**

| 类型                      | 说明 |
|-------------------------| -- |
| [HiAppEvent_Watcher](capi-hiappevent-hiappevent-watcher.md)* | 接口调用成功时返回指向的新建监听器的指针，name参数异常时返回nullptr。 |

### OH_HiAppEvent_DestroyWatcher()

```
void OH_HiAppEvent_DestroyWatcher(HiAppEvent_Watcher* watcher)
```

**描述**

销毁已创建的监听器。注意：已创建的监听器不再使用后，需要将其销毁，释放内存，防止内存泄漏，销毁后需将对应指针置空。

**起始版本：** 12


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [HiAppEvent_Watcher](capi-hiappevent-hiappevent-watcher.md)* watcher | 指向监听器的指针（即OH_HiAppEvent_CreateWatcher接口返回的指针）。 |

### OH_HiAppEvent_SetTriggerCondition()

```
int OH_HiAppEvent_SetTriggerCondition(HiAppEvent_Watcher* watcher, int row, int size, int timeOut)
```

**描述**

用于设置监听器OH_HiAppEvent_OnTrigger回调的触发条件。<br> 分别可以从监视器新接收事件数量、新接收事件大小、onTrigger触发超时时间，设置触发条件。调用方应至少保证从一个方面设置触发条件。

**起始版本：** 12


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [HiAppEvent_Watcher](capi-hiappevent-hiappevent-watcher.md)* watcher | 指向监听器的指针（即OH_HiAppEvent_CreateWatcher接口返回的指针）。 |
| int row | 当输入值大于0，且新接收事件的数量大于等于该值时，将调用设置的onTrigger回调函数；<br> 当输入值小于等于0时，不再以接收数量多少为维度来触发onTrigger回调。 |
| int size | 当输入值大于0，且新接收事件的大小(单个事件大小计算方式为，将事件转换为json字符串后，字符串的长度)大于等于该值时，将调用设置的onTrigger回调函数；<br> 当输入值小于等于0时，不再以新接收事件大小为维度触发onTrigger回调。 |
| int timeOut | 单位秒，当输入值大于0，每经过timeout秒，将检查监视器是否存在新接收到的事件，如果存在将触发onTrigger回调。<br> 触发onTrigger后，经过timeOut秒后将再次检查是否存在新接收到的事件。<br> 当输入值小于等于0，不以超时时间为维度触发onTrigger回调。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int | 0：接口调用成功；-5：watcher入参空指针。 |

### OH_HiAppEvent_SetAppEventFilter()

```
int OH_HiAppEvent_SetAppEventFilter(HiAppEvent_Watcher* watcher, const char* domain, uint8_t eventTypes,const char* const *names, int namesLen)
```

**描述**

用于设置监听器需要监听的事件的类型。该函数可以重复调用，可添加多个过滤规则，而非替换，监听器将收到满足任一过滤规则的事件的通知。

**起始版本：** 12


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [HiAppEvent_Watcher](capi-hiappevent-hiappevent-watcher.md)* watcher | 指向监听器的指针（即OH_HiAppEvent_CreateWatcher接口返回的指针）。 |
| const char* domain | 需要监听事件的领域。 |
| uint8_t eventTypes | 需要监听事件的事件类型。使用按位与方式进行匹配，可支持监听多种类型的事件。第一位为1（数值为1）表示支持监听故障类型的事件；<br> 第二位为1（数值为2）表示支持监听统计类型的事件；<br> 第三位为1（数值为4）表示支持监听安全类型的事件；<br> 第四位为1（数值为8）表示支持监听行为类型的事件。<br> 都为1（数值为15）或者都为0（数值为0）表示支持所有类型事件。 |
| const char* const *names | 需要监听的事件名称数组。 |
| int namesLen | 监听的事件名称的数组长度。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int | 0：接口调用成功；-1：names参数异常；-4：domain参数异常；-5：watcher入参空指针。 |

### OH_HiAppEvent_SetWatcherOnTrigger()

```
int OH_HiAppEvent_SetWatcherOnTrigger(HiAppEvent_Watcher* watcher, OH_HiAppEvent_OnTrigger onTrigger)
```

**描述**

用于设置监听器onTrigger回调的接口。<br> 如果未设置OnReceive回调或已将其设置为nullptr，则将保存观察者接收到的应用事件。当保存的应用事件满足onTrigger回调的触发条件时，将调用onTrigger回调。

**起始版本：** 12


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [HiAppEvent_Watcher](capi-hiappevent-hiappevent-watcher.md)* watcher | 指向监听器的指针（即OH_HiAppEvent_CreateWatcher接口返回的指针）。 |
| [OH_HiAppEvent_OnTrigger](capi-hiappevent-h.md#oh_hiappevent_ontrigger) onTrigger | 需要设置的回调。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int | 0：接口调用成功；-5：watcher入参空指针。 |

### OH_HiAppEvent_SetWatcherOnReceive()

```
int OH_HiAppEvent_SetWatcherOnReceive(HiAppEvent_Watcher* watcher, OH_HiAppEvent_OnReceive onReceive)
```

**描述**

用于设置监听器onReceive回调函数的接口。当监听器监听到相应事件后，onReceive回调函数将被调用。

**起始版本：** 12


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [HiAppEvent_Watcher](capi-hiappevent-hiappevent-watcher.md)* watcher | 指向监听器的指针（即OH_HiAppEvent_CreateWatcher接口返回的指针）。 |
| [OH_HiAppEvent_OnReceive](capi-hiappevent-h.md#oh_hiappevent_onreceive) onReceive | 回调函数的函数指针。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int | 0：接口调用成功；-5：watcher入参空指针。 |

### OH_HiAppEvent_TakeWatcherData()

```
int OH_HiAppEvent_TakeWatcherData(HiAppEvent_Watcher* watcher, uint32_t eventNum, OH_HiAppEvent_OnTake onTake)
```

**描述**

用于获取监听器收到后保存的事件。

**起始版本：** 12


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [HiAppEvent_Watcher](capi-hiappevent-hiappevent-watcher.md)* watcher | 指向监听器的指针（即OH_HiAppEvent_CreateWatcher接口返回的指针）。 |
| uint32_t eventNum | 当输入值小于等于0时，取全部已保存事件；当输入值大于0时，按照事件发生时间倒序排列，取指定数量的已保存事件。 |
| [OH_HiAppEvent_OnTake](capi-hiappevent-h.md#oh_hiappevent_ontake) onTake | 回调函数指针，事件通过调用该函数返回事件信息。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int | 0：接口调用成功；-5：watcher入参空指针；-6：还未调用OH_HiAppEvent_AddWatcher，操作顺序有误。 |

### OH_HiAppEvent_AddWatcher()

```
int OH_HiAppEvent_AddWatcher(HiAppEvent_Watcher* watcher)
```

**描述**

添加监听器的接口，监听器开始监听系统消息。

**起始版本：** 12


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [HiAppEvent_Watcher](capi-hiappevent-hiappevent-watcher.md)* watcher | 指向监听器的指针（即OH_HiAppEvent_CreateWatcher接口返回的指针）。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int | 0：接口调用成功；-5：watcher入参空指针。 |

### OH_HiAppEvent_RemoveWatcher()

```
int OH_HiAppEvent_RemoveWatcher(HiAppEvent_Watcher* watcher)
```

**描述**

移除监听器的接口，监听器停止监听系统消息。注意：该接口仅仅使监听器停止监听系统消息，并未销毁该监听器，该监听器依然常驻内存，直至调用OH_HiAppEvent_DestroyWatcher接口，内存才会释放。

**起始版本：** 12


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [HiAppEvent_Watcher](capi-hiappevent-hiappevent-watcher.md)* watcher | 指向监听器的指针（即OH_HiAppEvent_CreateWatcher接口返回的指针）。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int | 0：接口调用成功；-5：watcher入参空指针；-6：还未调用OH_HiAppEvent_AddWatcher，操作顺序有误。 |

### OH_HiAppEvent_ClearData()

```
void OH_HiAppEvent_ClearData()
```

**描述**

清除所有监视器保存的所有事件。

**起始版本：** 12

### OH_HiAppEvent_CreateProcessor()

```
HiAppEvent_Processor* OH_HiAppEvent_CreateProcessor(const char* name)
```

**描述**

创建一个用于处理app事件上报的处理者。注意：创建的处理者不再使用后必须通过调用OH_HiAppEvent_DestroyProcessor接口进行销毁。

**起始版本：** 18


**参数：**

| 参数项 | 描述 |
| -- | -- |
| const char* name | 处理者名称。只能包含大小写字母、数字、下划线和$，不能以数字开头，长度非空且不超过256个字符。 |

**返回：**

| 类型                        | 说明 |
|---------------------------| -- |
| [HiAppEvent_Processor](capi-hiappevent-hiappevent-processor.md)* | 接口调用成功时返回指向的新建处理者的指针，name参数异常时返回nullptr。 |

### OH_HiAppEvent_SetReportRoute()

```
int OH_HiAppEvent_SetReportRoute(HiAppEvent_Processor* processor, const char* appId, const char* routeInfo)
```

**描述**

设置处理者事件上报路由的接口。

**起始版本：** 18


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [HiAppEvent_Processor](capi-hiappevent-hiappevent-processor.md)* processor | 指向处理者的指针（即OH_HiAppEvent_CreateProcessor接口返回的指针）。 |
| const char* appId | 处理者的应用ID。 |
| const char* routeInfo | 服务器位置信息，默认为空字符串。传入字符串长度不能超8KB，超过时会被置为默认值。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int | [HIAPPEVENT_SUCCESS](capi-hiappevent-h.md#hiappevent_errorcode)：接口调用成功；<br>         [HIAPPEVENT_PROCESSOR_IS_NULL](capi-hiappevent-h.md#hiappevent_errorcode)：processor入参为空；<br>         [HIAPPEVENT_INVALID_PARAM_VALUE](capi-hiappevent-h.md#hiappevent_errorcode)：参数值无效；<br>         [HIAPPEVENT_INVALID_UID](capi-hiappevent-h.md#hiappevent_errorcode)：用户标识无效；<br>         [HIAPPEVENT_INVALID_PARAM_VALUE_LENGTH](capi-hiappevent-h.md#hiappevent_errorcode)：参数值长度无效。<br>         具体可参考[HiAppEvent_ErrorCode](capi-hiappevent-h.md#hiappevent_errorcode)。 |

### OH_HiAppEvent_SetReportPolicy()

```
int OH_HiAppEvent_SetReportPolicy(HiAppEvent_Processor* processor, int periodReport, int batchReport,bool onStartReport, bool onBackgroundReport)
```

**描述**

设置处理者事件上报策略的接口。

**起始版本：** 18


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [HiAppEvent_Processor](capi-hiappevent-hiappevent-processor.md)* processor | 指向处理者的指针（即OH_HiAppEvent_CreateProcessor接口返回的指针）。 |
| int periodReport | 事件定时上报周期，单位为秒。 |
| int batchReport | 事件上报阈值，当事件条数达到阈值时上报事件。 |
| bool onStartReport | 数据处理者在启动时是否上报事件，默认值为false。 |
| bool onBackgroundReport | 应用程序进入后台时，是否上报事件，默认值为false。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int | [HIAPPEVENT_SUCCESS](capi-hiappevent-h.md#hiappevent_errorcode)：接口调用成功；<br>         [HIAPPEVENT_PROCESSOR_IS_NULL](capi-hiappevent-h.md#hiappevent_errorcode)：processor入参为空；<br>         [HIAPPEVENT_INVALID_PARAM_VALUE](capi-hiappevent-h.md#hiappevent_errorcode)：参数值无效；<br>         [HIAPPEVENT_INVALID_UID](capi-hiappevent-h.md#hiappevent_errorcode)：用户标识无效。<br>         具体可参考[HiAppEvent_ErrorCode](capi-hiappevent-h.md#hiappevent_errorcode)。 |

### OH_HiAppEvent_SetReportEvent()

```
int OH_HiAppEvent_SetReportEvent(HiAppEvent_Processor* processor, const char* domain, const char* name,bool isRealTime)
```

**描述**

设置处理者上报事件的接口。

**起始版本：** 18


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [HiAppEvent_Processor](capi-hiappevent-hiappevent-processor.md)* processor | 指向处理者的指针（即OH_HiAppEvent_CreateProcessor接口返回的指针）。 |
| const char* domain | 上报事件的领域。 |
| const char* name | 上报事件的名称。 |
| bool isRealTime | 是否实时上报。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int | [HIAPPEVENT_SUCCESS](capi-hiappevent-h.md#hiappevent_errorcode)：接口调用成功；<br>         [HIAPPEVENT_PROCESSOR_IS_NULL](capi-hiappevent-h.md#hiappevent_errorcode)：processor入参为空；<br>         [HIAPPEVENT_INVALID_PARAM_VALUE](capi-hiappevent-h.md#hiappevent_errorcode)：参数值无效；<br>         [HIAPPEVENT_INVALID_UID](capi-hiappevent-h.md#hiappevent_errorcode)：用户标识无效。<br>         具体可参考[HiAppEvent_ErrorCode](capi-hiappevent-h.md#hiappevent_errorcode)。 |

### OH_HiAppEvent_SetCustomConfig()

```
int OH_HiAppEvent_SetCustomConfig(HiAppEvent_Processor* processor, const char* key, const char* value)
```

**描述**

设置处理者自定义扩展参数的接口。

**起始版本：** 18


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [HiAppEvent_Processor](capi-hiappevent-hiappevent-processor.md)* processor | 指向处理者的指针（即OH_HiAppEvent_CreateProcessor接口返回的指针）。 |
| const char* key | 参数名，长度不超过32个字符。 |
| const char* value | 参数值，长度不超过1024个字符。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int | [HIAPPEVENT_SUCCESS](capi-hiappevent-h.md#hiappevent_errorcode)：接口调用成功；<br>         [HIAPPEVENT_PROCESSOR_IS_NULL](capi-hiappevent-h.md#hiappevent_errorcode)：processor入参为空；<br>         [HIAPPEVENT_INVALID_PARAM_VALUE](capi-hiappevent-h.md#hiappevent_errorcode)：参数值无效；<br>         [HIAPPEVENT_INVALID_UID](capi-hiappevent-h.md#hiappevent_errorcode)：用户标识无效；<br>         [HIAPPEVENT_INVALID_PARAM_VALUE_LENGTH](capi-hiappevent-h.md#hiappevent_errorcode)：参数值长度无效。<br>         具体可参考[HiAppEvent_ErrorCode](capi-hiappevent-h.md#hiappevent_errorcode)。 |

### OH_HiAppEvent_SetConfigId()

```
int OH_HiAppEvent_SetConfigId(HiAppEvent_Processor* processor, int configId)
```

**描述**

设置处理者配置id的接口。

**起始版本：** 18


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [HiAppEvent_Processor](capi-hiappevent-hiappevent-processor.md)* processor | 指向处理者的指针（即OH_HiAppEvent_CreateProcessor接口返回的指针）。 |
| int configId | 数据处理者配置id，自然数。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int | [HIAPPEVENT_SUCCESS](capi-hiappevent-h.md#hiappevent_errorcode)：接口调用成功；<br>         [HIAPPEVENT_PROCESSOR_IS_NULL](capi-hiappevent-h.md#hiappevent_errorcode)：processor入参为空；<br>         [HIAPPEVENT_INVALID_PARAM_VALUE](capi-hiappevent-h.md#hiappevent_errorcode)：参数值无效；<br>         [HIAPPEVENT_INVALID_UID](capi-hiappevent-h.md#hiappevent_errorcode)：用户标识无效。<br>         具体可参考[HiAppEvent_ErrorCode](capi-hiappevent-h.md#hiappevent_errorcode)。 |

### OH_HiAppEvent_SetConfigName()

```
int OH_HiAppEvent_SetConfigName(HiAppEvent_Processor* processor, const char* configName)
```

**描述**

设置处理者的配置名称的接口。

**起始版本：** 20


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [HiAppEvent_Processor](capi-hiappevent-hiappevent-processor.md)* processor | 指向处理者的指针（即OH_HiAppEvent_CreateProcessor接口返回的指针）。 |
| const char* configName |  数据处理者的配置名称。只能包含大小写字母、数字、下划线和$，不能以数字开头，长度非空且不超过256个字符。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int | [HIAPPEVENT_SUCCESS](capi-hiappevent-h.md#hiappevent_errorcode)：接口调用成功；<br>         [HIAPPEVENT_PROCESSOR_IS_NULL](capi-hiappevent-h.md#hiappevent_errorcode)：processor入参为空；<br>         [HIAPPEVENT_INVALID_PARAM_VALUE](capi-hiappevent-h.md#hiappevent_errorcode)：参数值无效；<br>         [HIAPPEVENT_INVALID_UID](capi-hiappevent-h.md#hiappevent_errorcode)：用户标识无效。<br>         [HIAPPEVENT_INVALID_PARAM_VALUE_LENGTH](capi-hiappevent-h.md#hiappevent_errorcode)：参数值长度无效。<br>         具体可参考[HiAppEvent_ErrorCode](capi-hiappevent-h.md#hiappevent_errorcode)。 |

### OH_HiAppEvent_SetReportUserId()

```
int OH_HiAppEvent_SetReportUserId(HiAppEvent_Processor* processor, const char* const * userIdNames, int size)
```

**描述**

设置处理者用户ID的接口。

**起始版本：** 18


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [HiAppEvent_Processor](capi-hiappevent-hiappevent-processor.md)* processor | 指向处理者的指针（即OH_HiAppEvent_CreateProcessor接口返回的指针）。 |
| const char* const * userIdNames | 处理者可以上报的用户ID的name数组。 |
| int size | 用户ID的name数组长度。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int | [HIAPPEVENT_SUCCESS](capi-hiappevent-h.md#hiappevent_errorcode)：接口调用成功；<br>         [HIAPPEVENT_PROCESSOR_IS_NULL](capi-hiappevent-h.md#hiappevent_errorcode)：processor入参为空；<br>         [HIAPPEVENT_INVALID_PARAM_VALUE](capi-hiappevent-h.md#hiappevent_errorcode)：参数值无效；<br>         [HIAPPEVENT_INVALID_UID](capi-hiappevent-h.md#hiappevent_errorcode)：用户标识无效；<br>         [HIAPPEVENT_INVALID_PARAM_VALUE_LENGTH](capi-hiappevent-h.md#hiappevent_errorcode)：参数值长度无效。<br>         具体可参考[HiAppEvent_ErrorCode](capi-hiappevent-h.md#hiappevent_errorcode)。 |

### OH_HiAppEvent_SetReportUserProperty()

```
int OH_HiAppEvent_SetReportUserProperty(HiAppEvent_Processor* processor, const char* const * userPropertyNames,int size)
```

**描述**

设置处理者用户属性的接口。

**起始版本：** 18


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [HiAppEvent_Processor](capi-hiappevent-hiappevent-processor.md)* processor | 指向处理者的指针（即OH_HiAppEvent_CreateProcessor接口返回的指针）。 |
| const char* const * userPropertyNames | 处理者可以上报的用户属性数组。 |
| int size | 用户属性数组的长度。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int | [HIAPPEVENT_SUCCESS](capi-hiappevent-h.md#hiappevent_errorcode)：接口调用成功；<br>         [HIAPPEVENT_PROCESSOR_IS_NULL](capi-hiappevent-h.md#hiappevent_errorcode)：processor入参为空；<br>         [HIAPPEVENT_INVALID_PARAM_VALUE](capi-hiappevent-h.md#hiappevent_errorcode)：参数值无效；<br>         [HIAPPEVENT_INVALID_UID](capi-hiappevent-h.md#hiappevent_errorcode)：用户标识无效；<br>         [HIAPPEVENT_INVALID_PARAM_VALUE_LENGTH](capi-hiappevent-h.md#hiappevent_errorcode)：参数值长度无效。<br>         具体可参考[HiAppEvent_ErrorCode](capi-hiappevent-h.md#hiappevent_errorcode)。 |

### OH_HiAppEvent_AddProcessor()

```
int64_t OH_HiAppEvent_AddProcessor(HiAppEvent_Processor* processor)
```

**描述**

添加数据处理者的接口。开发者可添加数据处理者，用于提供事件上云功能。数据处理者的实现可预置在设备中，开发者可根据数据处理者的约束设置属性。注意：Processor的配置信息需要由数据处理者提供，目前设备内暂未预置可供交互的数据处理者，因此当前事件上云功能不可用。

**起始版本：** 18


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [HiAppEvent_Processor](capi-hiappevent-hiappevent-processor.md)* processor | 指向处理者的指针（即OH_HiAppEvent_CreateProcessor接口返回的指针）。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int64_t | 调用成功时返回处理者唯一ID，大于0；<br>         [HIAPPEVENT_PROCESSOR_IS_NULL](capi-hiappevent-h.md#hiappevent_errorcode)：processor入参为空；<br>         [HIAPPEVENT_INVALID_PARAM_VALUE](capi-hiappevent-h.md#hiappevent_errorcode)：参数值无效；<br>         [HIAPPEVENT_OPERATE_FAILED](capi-hiappevent-h.md#hiappevent_errorcode)：数据处理者名称未找到或注册失败；<br>         [HIAPPEVENT_INVALID_UID](capi-hiappevent-h.md#hiappevent_errorcode)：用户标识无效。<br>         具体可参考[HiAppEvent_ErrorCode](capi-hiappevent-h.md#hiappevent_errorcode)。 |

### OH_HiAppEvent_DestroyProcessor()

```
void OH_HiAppEvent_DestroyProcessor(HiAppEvent_Processor* processor)
```

**描述**

销毁已创建的数据处理者。注意：已创建的处理者不再使用后，需要将其销毁，释放内存，防止内存泄漏，销毁后需将对应指针置空。

**起始版本：** 18


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [HiAppEvent_Processor](capi-hiappevent-hiappevent-processor.md)* processor | 指向处理者的指针（即OH_HiAppEvent_CreateProcessor接口返回的指针）。 |

### OH_HiAppEvent_RemoveProcessor()

```
int OH_HiAppEvent_RemoveProcessor(int64_t processorId)
```

**描述**

移除数据处理者的接口，处理者停止上报事件。注意：该接口仅仅使处理者停止上报事件，并未销毁该处理者，该处理者依然常驻内存，直至调用OH_HiAppEvent_DestroyProcessor接口，内存才会释放。

**起始版本：** 18


**参数：**

| 参数项 | 描述 |
| -- | -- |
| int64_t processorId | 处理者唯一ID。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int | [HIAPPEVENT_SUCCESS](capi-hiappevent-h.md#hiappevent_errorcode)：接口调用成功；<br>         [HIAPPEVENT_PROCESSOR_NOT_FOUND](capi-hiappevent-h.md#hiappevent_errorcode)：事件处理者不存在；<br>         [HIAPPEVENT_OPERATE_FAILED](capi-hiappevent-h.md#hiappevent_errorcode)：操作失败；<br>         [HIAPPEVENT_INVALID_UID](capi-hiappevent-h.md#hiappevent_errorcode)：用户标识无效。<br>         具体可参考[HiAppEvent_ErrorCode](capi-hiappevent-h.md#hiappevent_errorcode)。 |

### OH_HiAppEvent_CreateConfig()

```
HiAppEvent_Config* OH_HiAppEvent_CreateConfig(void)
```

**描述**

创建一个指向设置系统事件触发条件的配置对象的指针。

**起始版本：** 15

**返回：**

| 类型                     | 说明 |
|------------------------| -- |
| [HiAppEvent_Config](capi-hiappevent-hiappevent-config.md)* | 指向设置系统事件触发条件的配置对象的指针。 |

### OH_HiAppEvent_DestroyConfig()

```
void OH_HiAppEvent_DestroyConfig(HiAppEvent_Config* config)
```

**描述**

销毁已创建的配置对象。注意：已创建的配置对象不再使用后，需要将其销毁，释放内存，防止内存泄漏，销毁后需要将对应指针置空。

**起始版本：** 15


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [HiAppEvent_Config](capi-hiappevent-hiappevent-config.md)* config | 指向配置对象的指针（即OH_HiAppEvent_CreateConfig接口返回的指针）。 |

### OH_HiAppEvent_SetConfigItem()

```
int OH_HiAppEvent_SetConfigItem(HiAppEvent_Config* config, const char* itemName, const char* itemValue)
```

**描述**

设置配置对象中的配置项。

**起始版本：** 15


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [HiAppEvent_Config](capi-hiappevent-hiappevent-config.md)* config | 指向配置对象的指针（即OH_HiAppEvent_CreateConfig接口返回的指针）。 |
| const char* itemName | 待设定配置项的名称。 |
| const char* itemValue | 待设定配置项的值。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int | [HIAPPEVENT_SUCCESS](capi-hiappevent-h.md#hiappevent_errorcode)：接口调用成功；<br>         [HIAPPEVENT_EVENT_CONFIG_IS_NULL](capi-hiappevent-h.md#hiappevent_errorcode)：传入的指向配置对象的指针为空；<br>         [HIAPPEVENT_INVALID_PARAM_VALUE](capi-hiappevent-h.md#hiappevent_errorcode)：设定的配置项无效。<br>         具体可参考[HiAppEvent_ErrorCode](capi-hiappevent-h.md#hiappevent_errorcode)。 |

### OH_HiAppEvent_SetEventConfig()

```
int OH_HiAppEvent_SetEventConfig(const char* name, HiAppEvent_Config* config)
```

**描述**

设定系统事件订阅触发条件。

**起始版本：** 15


**参数：**

| 参数项 | 描述 |
| -- | -- |
| const char* name | 系统事件的名称。 |
| [HiAppEvent_Config](capi-hiappevent-hiappevent-config.md)* config | 指向配置对象的指针（即OH_HiAppEvent_CreateConfig接口返回的指针）。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int | [HIAPPEVENT_SUCCESS](capi-hiappevent-h.md#hiappevent_errorcode)：接口调用成功；<br>         [HIAPPEVENT_INVALID_PARAM_VALUE](capi-hiappevent-h.md#hiappevent_errorcode)：设置的参数无效。<br>         具体可参考[HiAppEvent_ErrorCode](capi-hiappevent-h.md#hiappevent_errorcode)。 |


