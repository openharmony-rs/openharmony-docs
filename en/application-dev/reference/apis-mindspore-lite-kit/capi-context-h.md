# context.h

<!--Kit: MindSpore Lite Kit-->
<!--Subsystem: AI-->
<!--Owner: @zhuguodong8-->
<!--Designer: @zhuguodong8; @jjfeing-->
<!--Tester: @principal87-->
<!--Adviser: @ge-yafang-->
<!-- md-trans-meta sourceCommit=942dacb937645c1a58f8c4b064aa07a764386785 translatedAt=2026-11-10T08:44:30.805Z pushedAt=2026-11-10T10:50:44.772Z nl=1 -->

## Overview

Provides context-related APIs for configuring runtime information. This API is not thread-safe.

**File to include:** <mindspore/context.h>

**Library:** libmindspore_lite_ndk.so

**System capability:** SystemCapability.Ai.MindSpore

**Since**: 9

**Related module:** [MindSpore](capi-mindspore.md)

## Summary

### Structs

| Name                                                           | typedef Keyword | Description                                |
|--------------------------------------------------------------|------------|-----------------------------------|
| [OH_AI_ContextHandle](capi-mindspore-oh-ai-contexthandle.md) | void*      | Pointer to the MindSpore Lite context information, which points to Context. |
| [OH_AI_DeviceInfoHandle](capi-mindspore-oh-ai-DeviceInfoHandle.md)   | void*          | Pointer to the MindSpore Lite running device information.                                  |

### Functions

| Name | Description |
| -- | -- |
| [OH_AI_API OH_AI_ContextHandle OH_AI_ContextCreate()](#oh_ai_contextcreate) | Creates a context object. Note: This API must be used together with OH_AI_ContextDestroy. |
| [OH_AI_API void OH_AI_ContextDestroy(OH_AI_ContextHandle *context)](#oh_ai_contextdestroy) | Destroys a context object. |
| [OH_AI_API void OH_AI_ContextSetThreadNum(OH_AI_ContextHandle context, int32_t thread_num)](#oh_ai_contextsetthreadnum) | Sets the number of runtime threads. |
| [OH_AI_API int32_t OH_AI_ContextGetThreadNum(const OH_AI_ContextHandle context)](#oh_ai_contextgetthreadnum) | Obtains the number of threads. |
| [OH_AI_API void OH_AI_ContextSetThreadAffinityMode(OH_AI_ContextHandle context, int mode)](#oh_ai_contextsetthreadaffinitymode) | Sets the policy for binding runtime threads to CPU cores. CPU physical cores are classified into big, medium, and small cores by frequency. Only big cores or medium cores need to be bound, and small cores do not need to be bound. |
| [OH_AI_API int OH_AI_ContextGetThreadAffinityMode(const OH_AI_ContextHandle context)](#oh_ai_contextgetthreadaffinitymode) | Obtains the policy for binding runtime threads to CPU cores. |
| [OH_AI_API void OH_AI_ContextSetThreadAffinityCoreList(OH_AI_ContextHandle context, const int32_t *core_list,size_t core_num)](#oh_ai_contextsetthreadaffinitycorelist) | Sets the list of CPU cores to which runtime threads are bound.<br> For example, when core_list=[2,6,8], the threads run on CPU cores 2, 6, and 8.<br> If both [OH_AI_ContextSetThreadAffinityMode](capi-context-h.md#oh_ai_contextsetthreadaffinitymode) and [OH_AI_ContextSetThreadAffinityCoreList](capi-context-h.md#oh_ai_contextsetthreadaffinitycorelist) are called for the same context object,<br> only the core_list parameter of [OH_AI_ContextSetThreadAffinityCoreList](capi-context-h.md#oh_ai_contextsetthreadaffinitycorelist) takes effect, while the mode parameter of [OH_AI_ContextSetThreadAffinityMode](capi-context-h.md#oh_ai_contextsetthreadaffinitymode) does not take effect. |
| [OH_AI_API const int32_t *OH_AI_ContextGetThreadAffinityCoreList(const OH_AI_ContextHandle context, size_t *core_num)](#oh_ai_contextgetthreadaffinitycorelist) | Obtains the CPU core binding list. |
| [OH_AI_API void OH_AI_ContextSetEnableParallel(OH_AI_ContextHandle context, bool is_parallel)](#oh_ai_contextsetenableparallel) | Sets whether to support parallelism at runtime. This feature is not enabled yet, and the setting does not take effect. |
| [OH_AI_API bool OH_AI_ContextGetEnableParallel(const OH_AI_ContextHandle context)](#oh_ai_contextgetenableparallel) | Obtains whether parallelism between operators is supported. |
| [OH_AI_API void OH_AI_ContextAddDeviceInfo(OH_AI_ContextHandle context, OH_AI_DeviceInfoHandle device_info)](#oh_ai_contextadddeviceinfo) | Attaches user-defined running device information to the inference context. |
| [OH_AI_API OH_AI_DeviceInfoHandle OH_AI_DeviceInfoCreate(OH_AI_DeviceType device_type)](#oh_ai_deviceinfocreate) | Creates a device information object. |
| [OH_AI_API void OH_AI_DeviceInfoDestroy(OH_AI_DeviceInfoHandle *device_info)](#oh_ai_deviceinfodestroy) | Destroys a device information instance. Note: After a device information instance is added to the context, the caller does not need to destroy it manually. |
| [OH_AI_API void OH_AI_DeviceInfoSetProvider(OH_AI_DeviceInfoHandle device_info, const char *provider)](#oh_ai_deviceinfosetprovider) | Sets the name of the provider. |
| [OH_AI_API const char *OH_AI_DeviceInfoGetProvider(const OH_AI_DeviceInfoHandle device_info)](#oh_ai_deviceinfogetprovider) | Obtains the name of the provider. |
| [OH_AI_API void OH_AI_DeviceInfoSetProviderDevice(OH_AI_DeviceInfoHandle device_info, const char *device)](#oh_ai_deviceinfosetproviderdevice) | Sets the name of the provider device. |
| [OH_AI_API const char *OH_AI_DeviceInfoGetProviderDevice(const OH_AI_DeviceInfoHandle device_info)](#oh_ai_deviceinfogetproviderdevice) | Obtains the name of the provider device. |
| [OH_AI_API OH_AI_DeviceType OH_AI_DeviceInfoGetDeviceType(const OH_AI_DeviceInfoHandle device_info)](#oh_ai_deviceinfogetdevicetype) | Obtains the type of the device. |
| [OH_AI_API void OH_AI_DeviceInfoSetEnableFP16(OH_AI_DeviceInfoHandle device_info, bool is_fp16)](#oh_ai_deviceinfosetenablefp16) | Sets whether to enable the float16 inference mode. This API is available only for CPU/GPU devices. |
| [OH_AI_API bool OH_AI_DeviceInfoGetEnableFP16(const OH_AI_DeviceInfoHandle device_info)](#oh_ai_deviceinfogetenablefp16) | Obtains whether the float16 inference mode is enabled. This API is available only for CPU/GPU devices. |
| [OH_AI_API void OH_AI_DeviceInfoSetFrequency(OH_AI_DeviceInfoHandle device_info, int frequency)](#oh_ai_deviceinfosetfrequency) | Sets the NPU frequency. This API is available only for NPU devices. |
| [OH_AI_API int OH_AI_DeviceInfoGetFrequency(const OH_AI_DeviceInfoHandle device_info)](#oh_ai_deviceinfogetfrequency) | Obtains the NPU frequency type. This API is available only for NPU devices. |
| [OH_AI_API NNRTDeviceDesc *OH_AI_GetAllNNRTDeviceDescs(size_t *num)](#oh_ai_getallnnrtdevicedescs) | Obtains the description information of all NNRt hardware devices in the system. |
| [OH_AI_API NNRTDeviceDesc *OH_AI_GetElementOfNNRTDeviceDescs(NNRTDeviceDesc *descs, size_t index)](#oh_ai_getelementofnnrtdevicedescs) | Obtains the pointer to an element in the NNRt device description information array. |
| [OH_AI_API void OH_AI_DestroyAllNNRTDeviceDescs(NNRTDeviceDesc **desc)](#oh_ai_destroyallnnrtdevicedescs) | Destroys the NNRt description information instance array obtained from [OH_AI_GetAllNNRTDeviceDescs](capi-context-h.md#oh_ai_getallnnrtdevicedescs). |
| [OH_AI_API size_t OH_AI_GetDeviceIdFromNNRTDeviceDesc(const NNRTDeviceDesc *desc)](#oh_ai_getdeviceidfromnnrtdevicedesc) | Obtains the NNRt device ID from a specific NNRt device description information instance. Note: This ID is valid only for NNRt. |
| [OH_AI_API const char *OH_AI_GetNameFromNNRTDeviceDesc(const NNRTDeviceDesc *desc)](#oh_ai_getnamefromnnrtdevicedesc) | Obtains the NNRt device name from a specific NNRt device description information instance. |
| [OH_AI_API OH_AI_NNRTDeviceType OH_AI_GetTypeFromNNRTDeviceDesc(const NNRTDeviceDesc *desc)](#oh_ai_gettypefromnnrtdevicedesc) | Obtains the NNRt device type from a specific NNRt device description information instance. |
| [OH_AI_API OH_AI_DeviceInfoHandle OH_AI_CreateNNRTDeviceInfoByName(const char *name)](#oh_ai_creatennrtdeviceinfobyname) | Finds the NNRt device with the specified name and creates NNRt device information based on the first device found. |
| [OH_AI_API OH_AI_DeviceInfoHandle OH_AI_CreateNNRTDeviceInfoByType(OH_AI_NNRTDeviceType type)](#oh_ai_creatennrtdeviceinfobytype) | Finds the NNRt device of the specified type and creates NNRt device information based on the first device found. |
| [OH_AI_API void OH_AI_DeviceInfoSetDeviceId(OH_AI_DeviceInfoHandle device_info, size_t device_id)](#oh_ai_deviceinfosetdeviceid) | Sets the NNRt device ID. This API is available only for NNRt devices. |
| [OH_AI_API size_t OH_AI_DeviceInfoGetDeviceId(const OH_AI_DeviceInfoHandle device_info)](#oh_ai_deviceinfogetdeviceid) | Obtains the NNRt device ID. This API is available only for NNRt devices. |
| [OH_AI_API void OH_AI_DeviceInfoSetPerformanceMode(OH_AI_DeviceInfoHandle device_info, OH_AI_PerformanceMode mode)](#oh_ai_deviceinfosetperformancemode) | Sets the NNRt performance mode. This API is available only for NNRt devices. |
| [OH_AI_API OH_AI_PerformanceMode OH_AI_DeviceInfoGetPerformanceMode(const OH_AI_DeviceInfoHandle device_info)](#oh_ai_deviceinfogetperformancemode) | Obtains the NNRt performance mode. This API is available only for NNRt devices. |
| [OH_AI_API void OH_AI_DeviceInfoSetPriority(OH_AI_DeviceInfoHandle device_info, OH_AI_Priority priority)](#oh_ai_deviceinfosetpriority) | Sets the NNRt task priority. This API is available only for NNRt devices. |
| [OH_AI_API OH_AI_Priority OH_AI_DeviceInfoGetPriority(const OH_AI_DeviceInfoHandle device_info)](#oh_ai_deviceinfogetpriority) | Obtains the NNRt task priority. This API is available only for NNRt devices. |
| [OH_AI_API OH_AI_Status OH_AI_DeviceInfoAddExtension(OH_AI_DeviceInfoHandle device_info, const char *name,const char *value, size_t value_size)](#oh_ai_deviceinfoaddextension) | Adds an extension configuration in key/value pair form to the device information. This API is valid only for NNRt device information.<br>Currently, only the following 11 keys are supported: {"CachePath": "YourCachePath"}, {"CacheVersion": "YourCacheVersion"},<br> {"QuantBuffer": "YourQuantBuffer"}, {"ModelName": "YourModelName"},<br> {"isProfiling": "YourProfilingSwitch"}, {"opLayout": "YourOpLayout"},<br> {"InputDims": "YourInputDims"}, {"DynamicDims": "YourDynamicDims"},<br> {"QuantConfigData": "YourQuantConfigData"}, {"BandMode": "YourBandMode"},<br> {"NPU_FM_SHARED": "YourNPU_FM_SHARED"}. You can configure the value of each key based on your usage. |

## Function Description

### OH_AI_ContextCreate()

```c
OH_AI_API OH_AI_ContextHandle OH_AI_ContextCreate()
```

**Description**

Creates a context object. Note: This interface must be used together with OH_AI_ContextDestroy.

**Since**: 9

**Return**

| Type | Description |
| -- | -- |
| OH_AI_API [OH_AI_ContextHandle](capi-mindspore-oh-ai-contexthandle.md) | Pointer to the [OH_AI_ContextHandle](capi-mindspore-oh-ai-contexthandle.md) of the context information. |

### OH_AI_ContextDestroy()

```c
OH_AI_API void OH_AI_ContextDestroy(OH_AI_ContextHandle *context)
```

**Description**

Destroys the context object.

**Since**: 9


**Parameters**

| Name | Description |
| -- | -- |
| [OH_AI_ContextHandle](capi-mindspore-oh-ai-contexthandle.md) *context | Double pointer to [OH_AI_ContextHandle](capi-mindspore-oh-ai-contexthandle.md). After the context is destroyed, context is set to a null pointer. |

### OH_AI_ContextSetThreadNum()

```c
OH_AI_API void OH_AI_ContextSetThreadNum(OH_AI_ContextHandle context, int32_t thread_num)
```

**Description**

Sets the number of threads at runtime.

**Since**: 9


**Parameters**

| Name | Description |
| -- | -- |
| [OH_AI_ContextHandle](capi-mindspore-oh-ai-contexthandle.md) context | Pointer to the [OH_AI_ContextHandle](capi-mindspore-oh-ai-contexthandle.md) of the context information instance. |
| int32_t thread_num | Number of threads at runtime. The length is subject to the system limitation. |

### OH_AI_ContextGetThreadNum()

```c
OH_AI_API int32_t OH_AI_ContextGetThreadNum(const OH_AI_ContextHandle context)
```

**Description**

Gets the number of threads.

**Since**: 9


**Parameters**

| Name | Description |
| -- | -- |
| const [OH_AI_ContextHandle](capi-mindspore-oh-ai-contexthandle.md) context | Pointer to the [OH_AI_ContextHandle](capi-mindspore-oh-ai-contexthandle.md) of the context information instance. |

**Return**

| Type | Description |
| -- | -- |
| OH_AI_API int32_t | Current number of threads. |

### OH_AI_ContextSetThreadAffinityMode()

```c
OH_AI_API void OH_AI_ContextSetThreadAffinityMode(OH_AI_ContextHandle context, int mode)
```

**Description**

Sets the policy for binding runtime threads to CPU cores. CPU physical cores are classified into big, medium, and small cores by frequency. Only big cores or medium cores need to be bound, and small cores do not need to be bound.

**Since**: 9


**Parameters**

| Name | Description |
| -- | -- |
| [OH_AI_ContextHandle](capi-mindspore-oh-ai-contexthandle.md) context | Pointer to the [OH_AI_ContextHandle](capi-mindspore-oh-ai-contexthandle.md) of the context information instance. |
| int mode | Core binding policy. There are three policies: 0 means no core binding, 1 means big cores first, and 2 means medium cores first. |

### OH_AI_ContextGetThreadAffinityMode()

```c
OH_AI_API int OH_AI_ContextGetThreadAffinityMode(const OH_AI_ContextHandle context)
```

**Description**

Obtains the policy for binding runtime threads to CPU cores.

**Since**: 9


**Parameters**

| Name | Description |
| -- | -- |
| const [OH_AI_ContextHandle](capi-mindspore-oh-ai-contexthandle.md) context | Pointer to the [OH_AI_ContextHandle](capi-mindspore-oh-ai-contexthandle.md) of the context information instance. |

**Return**

| Type | Description |
| -- | -- |
| OH_AI_API int | Core binding policy. There are three policies: 0 indicates no core binding, 1 indicates big cores first, and 2 indicates medium cores first. |

### OH_AI_ContextSetThreadAffinityCoreList()

```c
OH_AI_API void OH_AI_ContextSetThreadAffinityCoreList(OH_AI_ContextHandle context, const int32_t *core_list,size_t core_num)
```

**Description**

Sets the list of CPU cores to which runtime threads are bound.<br> For example, when core_list=[2,6,8], the threads run on CPU cores 2, 6, and 8.<br> If both [OH_AI_ContextSetThreadAffinityMode](capi-context-h.md#oh_ai_contextsetthreadaffinitymode) and [OH_AI_ContextSetThreadAffinityCoreList](capi-context-h.md#oh_ai_contextsetthreadaffinitycorelist) are called for the same context object, only the core_list parameter of [OH_AI_ContextSetThreadAffinityCoreList](capi-context-h.md#oh_ai_contextsetthreadaffinitycorelist) takes effect, while the mode parameter of [OH_AI_ContextSetThreadAffinityMode](capi-context-h.md#oh_ai_contextsetthreadaffinitymode) does not.

**Since**: 9


**Parameters**

| Name | Description |
| -- | -- |
| [OH_AI_ContextHandle](capi-mindspore-oh-ai-contexthandle.md) context | Pointer to the [OH_AI_ContextHandle](capi-mindspore-oh-ai-contexthandle.md) context information instance. |
| const int32_t *core_list | List of CPU cores to which threads are bound. |
| size_t core_num | Number of cores, which represents the length of core_list. |

### OH_AI_ContextGetThreadAffinityCoreList()

```c
OH_AI_API const int32_t *OH_AI_ContextGetThreadAffinityCoreList(const OH_AI_ContextHandle context, size_t *core_num)
```

**Description**

Gets the CPU core binding list.

**Since**: 9


**Parameters**

| Name | Description |
| -- | -- |
| const [OH_AI_ContextHandle](capi-mindspore-oh-ai-contexthandle.md) context | Pointer to the [OH_AI_ContextHandle](capi-mindspore-oh-ai-contexthandle.md) of the context information instance. |
| size_t *core_num | Output parameter, which indicates the number of cores. |

**Return**

| Type | Description |
| -- | -- |
| OH_AI_API const int32_t * | CPU core binding list. This list object is managed by [OH_AI_ContextHandle](capi-mindspore-oh-ai-contexthandle.md), and the caller does not need to release it manually. |

### OH_AI_ContextSetEnableParallel()

```c
OH_AI_API void OH_AI_ContextSetEnableParallel(OH_AI_ContextHandle context, bool is_parallel)
```

**Description**

Sets whether to enable parallel execution at runtime. This feature is not enabled yet, so the setting does not take effect.

**Since**: 9


**Parameters**

| Name | Description |
| -- | -- |
| [OH_AI_ContextHandle](capi-mindspore-oh-ai-contexthandle.md) context | Pointer to the context information instance [OH_AI_ContextHandle](capi-mindspore-oh-ai-contexthandle.md). |
| bool is_parallel | Whether to enable parallel execution. The value true means parallel execution is supported, and false means the opposite. |

### OH_AI_ContextGetEnableParallel()

```c
OH_AI_API bool OH_AI_ContextGetEnableParallel(const OH_AI_ContextHandle context)
```

**Description**

Obtains whether parallel execution between operators is supported.

**Since**: 9


**Parameters**

| Name | Description |
| -- | -- |
| const [OH_AI_ContextHandle](capi-mindspore-oh-ai-contexthandle.md) context | Pointer to the [OH_AI_ContextHandle](capi-mindspore-oh-ai-contexthandle.md) of the context information instance. |

**Return**

| Type | Description |
| -- | -- |
| OH_AI_API bool | Whether parallel execution is supported. The value **true** indicates that parallel execution is supported, and **false** indicates the opposite. |

### OH_AI_ContextAddDeviceInfo()

```c
OH_AI_API void OH_AI_ContextAddDeviceInfo(OH_AI_ContextHandle context, OH_AI_DeviceInfoHandle device_info)
```

**Description**

Attaches a user-defined running device information to the inference context.

**Since**: 9


**Parameters**

| Name | Description |
| -- | -- |
| [OH_AI_ContextHandle](capi-mindspore-oh-ai-contexthandle.md) context | Pointer to the [OH_AI_ContextHandle](capi-mindspore-oh-ai-contexthandle.md) of the context information instance. |
| [OH_AI_DeviceInfoHandle](capi-mindspore-oh-ai-DeviceInfoHandle.md) device_info | Pointer to the [OH_AI_DeviceInfoHandle](capi-mindspore-oh-ai-DeviceInfoHandle.md) of the device information instance. |

### OH_AI_DeviceInfoCreate()

```c
OH_AI_API OH_AI_DeviceInfoHandle OH_AI_DeviceInfoCreate(OH_AI_DeviceType device_type)
```

**Description**

Creates a device information object.

**Since**: 9


**Parameters**

| Name | Description |
| -- | -- |
| [OH_AI_DeviceType](capi-types-h.md#oh_ai_devicetype) device_type | Device type. For details, see [OH_AI_DeviceType](capi-types-h.md#oh_ai_devicetype). |

**Return**

| Type | Description |
| -- | -- |
| OH_AI_API [OH_AI_DeviceInfoHandle](capi-mindspore-oh-ai-DeviceInfoHandle.md) | Pointer to the [OH_AI_DeviceInfoHandle](capi-mindspore-oh-ai-DeviceInfoHandle.md) of the device information instance. |

### OH_AI_DeviceInfoDestroy()

```c
OH_AI_API void OH_AI_DeviceInfoDestroy(OH_AI_DeviceInfoHandle *device_info)
```

**Description**

Releases a device information instance. **Note:** After a device information instance is added to the context, the caller does not need to release it manually.

**Since**: 9


**Parameters**

| Name | Description |
| -- | -- |
| [OH_AI_DeviceInfoHandle](capi-mindspore-oh-ai-DeviceInfoHandle.md) *device_info | Pointer to the [OH_AI_DeviceInfoHandle](capi-mindspore-oh-ai-DeviceInfoHandle.md) of the device information instance. |

### OH_AI_DeviceInfoSetProvider()

```c
OH_AI_API void OH_AI_DeviceInfoSetProvider(OH_AI_DeviceInfoHandle device_info, const char *provider)
```

**Description**

Sets the manufacturer name.

**Since**: 9


**Parameters**

| Name | Description |
| -- | -- |
| [OH_AI_DeviceInfoHandle](capi-mindspore-oh-ai-DeviceInfoHandle.md) device_info | Pointer to the [OH_AI_DeviceInfoHandle](capi-mindspore-oh-ai-DeviceInfoHandle.md) of the device information instance. |
| const char *provider | Manufacturer name. The string length is subject to system limitations. |

### OH_AI_DeviceInfoGetProvider()

```c
OH_AI_API const char *OH_AI_DeviceInfoGetProvider(const OH_AI_DeviceInfoHandle device_info)
```

**Description**

Gets the name of the manufacturer.

**Since**: 9


**Parameters**

| Name | Description |
| -- | -- |
| const [OH_AI_DeviceInfoHandle](capi-mindspore-oh-ai-DeviceInfoHandle.md) device_info | Pointer to the [OH_AI_DeviceInfoHandle](capi-mindspore-oh-ai-DeviceInfoHandle.md) of the device information instance. |

**Return**

| Type | Description |
| -- | -- |
| OH_AI_API const char * | Name of the manufacturer. |

### OH_AI_DeviceInfoSetProviderDevice()

```c
OH_AI_API void OH_AI_DeviceInfoSetProviderDevice(OH_AI_DeviceInfoHandle device_info, const char *device)
```

**Description**

Sets the name of the manufacturer device.

**Since**: 9


**Parameters**

| Name | Description |
| -- | -- |
| [OH_AI_DeviceInfoHandle](capi-mindspore-oh-ai-DeviceInfoHandle.md) device_info | Pointer to the [OH_AI_DeviceInfoHandle](capi-mindspore-oh-ai-DeviceInfoHandle.md) of the device information instance. |
| const char *device | Name of the manufacturer device, for example, CPU. The string length is subject to the system limitation. |

### OH_AI_DeviceInfoGetProviderDevice()

```c
OH_AI_API const char *OH_AI_DeviceInfoGetProviderDevice(const OH_AI_DeviceInfoHandle device_info)
```

**Description**

Gets the name of the manufacturer device.

**Since**: 9


**Parameters**

| Name | Description |
| -- | -- |
| const [OH_AI_DeviceInfoHandle](capi-mindspore-oh-ai-DeviceInfoHandle.md) device_info | Pointer to the [OH_AI_DeviceInfoHandle](capi-mindspore-oh-ai-DeviceInfoHandle.md) that points to the device information instance. |

**Return**

| Type | Description |
| -- | -- |
| OH_AI_API const char * | Name of the manufacturer device. |

### OH_AI_DeviceInfoGetDeviceType()

```c
OH_AI_API OH_AI_DeviceType OH_AI_DeviceInfoGetDeviceType(const OH_AI_DeviceInfoHandle device_info)
```

**Description**

Obtains the device type.

**Since**: 9


**Parameters**

| Name | Description |
| -- | -- |
| const [OH_AI_DeviceInfoHandle](capi-mindspore-oh-ai-DeviceInfoHandle.md) device_info | Pointer to the [OH_AI_DeviceInfoHandle](capi-mindspore-oh-ai-DeviceInfoHandle.md) of the device information instance. |

**Return**

| Type                                                             | Description |
|----------------------------------------------------------------| -- |
| OH_AI_API [OH_AI_DeviceType](capi-types-h.md#oh_ai_devicetype) | Manufacturer device type. |

### OH_AI_DeviceInfoSetEnableFP16()

```c
OH_AI_API void OH_AI_DeviceInfoSetEnableFP16(OH_AI_DeviceInfoHandle device_info, bool is_fp16)
```

**Description**

Sets whether to enable the float16 inference mode. This interface is available only for CPU and GPU devices.

**Since**: 9


**Parameters**

| Name | Description |
| -- | -- |
| [OH_AI_DeviceInfoHandle](capi-mindspore-oh-ai-DeviceInfoHandle.md) device_info | Pointer to the [OH_AI_DeviceInfoHandle](capi-mindspore-oh-ai-DeviceInfoHandle.md) instance of the device information. |
| bool is_fp16 | Whether to enable the float16 inference mode. The value **true** means to enable the float16 inference mode, and **false** means not to enable it. |

### OH_AI_DeviceInfoGetEnableFP16()

```c
OH_AI_API bool OH_AI_DeviceInfoGetEnableFP16(const OH_AI_DeviceInfoHandle device_info)
```

**Description**

Gets whether to enable the float16 inference mode. This mode is available only on CPU/GPU devices.

**Since**: 9


**Parameters**

| Name | Description |
| -- | -- |
| const [OH_AI_DeviceInfoHandle](capi-mindspore-oh-ai-DeviceInfoHandle.md) device_info | Pointer to the [OH_AI_DeviceInfoHandle](capi-mindspore-oh-ai-DeviceInfoHandle.md) of the device information instance. |

**Return**

| Type | Description |
| -- | -- |
| OH_AI_API bool | Whether to enable the float16 inference mode. The value **true** means to enable the float16 inference mode, and **false** means not to enable it. |

### OH_AI_DeviceInfoSetFrequency()

```c
OH_AI_API void OH_AI_DeviceInfoSetFrequency(OH_AI_DeviceInfoHandle device_info, int frequency)
```

**Description**

Sets the frequency of the NPU. This interface is available only for NPU devices.

**Since**: 9


**Parameters**

| Name | Description |
| -- | -- |
| [OH_AI_DeviceInfoHandle](capi-mindspore-oh-ai-DeviceInfoHandle.md) device_info | Pointer to the [OH_AI_DeviceInfoHandle](capi-mindspore-oh-ai-DeviceInfoHandle.md) of the device information instance. |
| int frequency | Frequency type. The value ranges from 0 to 4, and the default value is 3. 0 means not set, and the frequency is adjusted by the system; 1 means low power consumption; 2 means balanced; 3 means high performance; 4 means ultra-high performance. |

### OH_AI_DeviceInfoGetFrequency()

```c
OH_AI_API int OH_AI_DeviceInfoGetFrequency(const OH_AI_DeviceInfoHandle device_info)
```

**Description**

Obtains the frequency type of the NPU. This interface is available only for NPU devices.

**Since**: 9


**Parameters**

| Name | Description |
| -- | -- |
| const [OH_AI_DeviceInfoHandle](capi-mindspore-oh-ai-DeviceInfoHandle.md) device_info | Pointer to the [OH_AI_DeviceInfoHandle](capi-mindspore-oh-ai-DeviceInfoHandle.md) of the device information instance. |

**Return**

| Type | Description |
| -- | -- |
| OH_AI_API int | Frequency type of the NPU. The value ranges from 0 to 4, where 0 indicates no setting and the frequency is adjusted by the system, 1 indicates low power consumption, 2 indicates balanced, 3 indicates high performance, and 4 indicates ultra-high performance. |

### OH_AI_GetAllNNRTDeviceDescs()

```c
OH_AI_API NNRTDeviceDesc *OH_AI_GetAllNNRTDeviceDescs(size_t *num)
```

**Description**

Obtains the description information of all NNRt hardware devices in the system.

**Since**: 10


**Parameters**

| Name | Description |
| -- | -- |
| size_t *num | Output parameter, which is a pointer to the quantity of devices. |

**Return**

| Type                             | Description |
|--------------------------------| -- |
| OH_AI_API [NNRTDeviceDesc](capi-mindspore-nnrtdevicedesc.md) * | Pointer to the array of NNRt device description information instances. NULL is returned if the acquisition fails. |

### OH_AI_GetElementOfNNRTDeviceDescs()

```c
OH_AI_API NNRTDeviceDesc *OH_AI_GetElementOfNNRTDeviceDescs(NNRTDeviceDesc *descs, size_t index)
```

**Description**

Obtains the element pointer in the NNRt device description information array.

**Since**: 10


**Parameters**

| Name | Description |
| -- | -- |
| [NNRTDeviceDesc](capi-mindspore-nnrtdevicedesc.md) *descs | Pointer to the NNRt device description information array. |
| size_t index | Index of the element in the array. |

**Return**

| Type | Description |
| -- | -- |
| OH_AI_API [NNRTDeviceDesc](capi-mindspore-nnrtdevicedesc.md) * | Pointer to the NNRt device description information type. |

### OH_AI_DestroyAllNNRTDeviceDescs()

```c
OH_AI_API void OH_AI_DestroyAllNNRTDeviceDescs(NNRTDeviceDesc **desc)
```

**Description**

Destroys the array of NNRt description information instances obtained from [OH_AI_GetAllNNRTDeviceDescs](capi-context-h.md#oh_ai_getallnnrtdevicedescs).

**Since**: 10


**Parameters**

| Name | Description |
| -- | -- |
| [NNRTDeviceDesc](capi-mindspore-nnrtdevicedesc.md) **desc | Double pointer to the array of NNRt device description information instances. After the destruction is complete, the content pointed to by desc is set to NULL. |

### OH_AI_GetDeviceIdFromNNRTDeviceDesc()

```c
OH_AI_API size_t OH_AI_GetDeviceIdFromNNRTDeviceDesc(const NNRTDeviceDesc *desc)
```

**Description**

Gets the NNRt device ID from a specific NNRt device description information instance. Note that this ID is valid only for NNRt.

**Since**: 10


**Parameters**

| Name | Description |
| -- | -- |
| const [NNRTDeviceDesc](capi-mindspore-nnrtdevicedesc.md) *desc | Pointer to the NNRt device description information instance. |

**Return**

| Type | Description |
| -- | -- |
| OH_AI_API size_t | NNRt device ID. |

### OH_AI_GetNameFromNNRTDeviceDesc()

```c
OH_AI_API const char *OH_AI_GetNameFromNNRTDeviceDesc(const NNRTDeviceDesc *desc)
```

**Description**

Obtains the NNRt device name from a specific NNRt device description information instance.

**Since**: 10


**Parameters**

| Name | Description |
| -- | -- |
| const [NNRTDeviceDesc](capi-mindspore-nnrtdevicedesc.md) *desc | Pointer to the NNRt device description information instance. |

**Return**

| Type | Description |
| -- | -- |
| OH_AI_API const char * | NNRt device name, a pointer to a constant string held by desc. The caller does not need to release this pointer separately. |

### OH_AI_GetTypeFromNNRTDeviceDesc()

```c
OH_AI_API OH_AI_NNRTDeviceType OH_AI_GetTypeFromNNRTDeviceDesc(const NNRTDeviceDesc *desc)
```

**Description**

Obtains the NNRt device type from a specific NNRt device description information instance.

**Since**: 10


**Parameters**

| Name | Description |
| -- | -- |
| const [NNRTDeviceDesc](capi-mindspore-nnrtdevicedesc.md) *desc | Pointer to the NNRt device description information instance. |

**Return**

| Type                                                                     | Description |
|------------------------------------------------------------------------| -- |
| OH_AI_API [OH_AI_NNRTDeviceType](capi-types-h.md#oh_ai_nnrtdevicetype) | [OH_AI_NNRTDeviceType](capi-types-h.md#oh_ai_nnrtdevicetype) NNRt device type. |

### OH_AI_CreateNNRTDeviceInfoByName()

```c
OH_AI_API OH_AI_DeviceInfoHandle OH_AI_CreateNNRTDeviceInfoByName(const char *name)
```

**Description**

Searches for the NNRt device with the specified name and creates NNRt device information based on the first device information found.

**Since**: 10


**Parameters**

| Name | Description |
| -- | -- |
| const char *name | Name of the target NNRt device. The string length is subject to the system limitation. |

**Return**

| Type | Description |
| -- | -- |
| OH_AI_API [OH_AI_DeviceInfoHandle](capi-mindspore-oh-ai-DeviceInfoHandle.md) | Pointer to the [OH_AI_DeviceInfoHandle](capi-mindspore-oh-ai-DeviceInfoHandle.md) of the device information instance. |

### OH_AI_CreateNNRTDeviceInfoByType()

```c
OH_AI_API OH_AI_DeviceInfoHandle OH_AI_CreateNNRTDeviceInfoByType(OH_AI_NNRTDeviceType type)
```

**Description**

Searches for an NNRt device of the specified type and creates NNRt device information based on the first device found.

**Since**: 10


**Parameters**

| Name | Description |
| -- | -- |
| [OH_AI_NNRTDeviceType](capi-types-h.md#oh_ai_nnrtdevicetype) type | Target NNRt device type of [OH_AI_NNRTDeviceType](capi-types-h.md#oh_ai_nnrtdevicetype). |

**Return**

| Type | Description |
| -- | -- |
| OH_AI_API [OH_AI_DeviceInfoHandle](capi-mindspore-oh-ai-DeviceInfoHandle.md) | [OH_AI_DeviceInfoHandle](capi-mindspore-oh-ai-DeviceInfoHandle.md) pointing to the device information instance. |

### OH_AI_DeviceInfoSetDeviceId()

```c
OH_AI_API void OH_AI_DeviceInfoSetDeviceId(OH_AI_DeviceInfoHandle device_info, size_t device_id)
```

**Description**

Sets the NNRt device ID. This interface is available only for NNRt devices.

**Since**: 10


**Parameters**

| Name | Description |
| -- | -- |
| [OH_AI_DeviceInfoHandle](capi-mindspore-oh-ai-DeviceInfoHandle.md) device_info | Pointer to the [OH_AI_DeviceInfoHandle](capi-mindspore-oh-ai-DeviceInfoHandle.md) of the device information instance. |
| size_t device_id | NNRt device ID. |

### OH_AI_DeviceInfoGetDeviceId()

```c
OH_AI_API size_t OH_AI_DeviceInfoGetDeviceId(const OH_AI_DeviceInfoHandle device_info)
```

**Description**

Gets the NNRt device ID, available only for NNRt devices.

**Since**: 10


**Parameters**

| Name | Description |
| -- | -- |
| const [OH_AI_DeviceInfoHandle](capi-mindspore-oh-ai-DeviceInfoHandle.md) device_info | Pointer to the [OH_AI_DeviceInfoHandle](capi-mindspore-oh-ai-DeviceInfoHandle.md) of the device information instance. |

**Return**

| Type | Description |
| -- | -- |
| OH_AI_API size_t | NNRt device ID. |

### OH_AI_DeviceInfoSetPerformanceMode()

```c
OH_AI_API void OH_AI_DeviceInfoSetPerformanceMode(OH_AI_DeviceInfoHandle device_info, OH_AI_PerformanceMode mode)
```

**Description**

Sets the NNRt performance mode, which is available only for NNRt devices.

**Since**: 10


**Parameters**

| Name | Description |
| -- | -- |
| [OH_AI_DeviceInfoHandle](capi-mindspore-oh-ai-DeviceInfoHandle.md) device_info | Pointer to the [OH_AI_DeviceInfoHandle](capi-mindspore-oh-ai-DeviceInfoHandle.md) of the device information instance. |
| [OH_AI_PerformanceMode](capi-types-h.md#oh_ai_performancemode) mode | [OH_AI_PerformanceMode](capi-types-h.md#oh_ai_performancemode) NNRt performance mode. |

### OH_AI_DeviceInfoGetPerformanceMode()

```c
OH_AI_API OH_AI_PerformanceMode OH_AI_DeviceInfoGetPerformanceMode(const OH_AI_DeviceInfoHandle device_info)
```

**Description**

Obtains the NNRt performance mode. This interface is available only for NNRt devices.

**Since**: 10


**Parameters**

| Name | Description |
| -- | -- |
| const [OH_AI_DeviceInfoHandle](capi-mindspore-oh-ai-DeviceInfoHandle.md) device_info | Pointer to the [OH_AI_DeviceInfoHandle](capi-mindspore-oh-ai-DeviceInfoHandle.md) of the device information instance. |

**Return**

| Type                                                                       | Description |
|--------------------------------------------------------------------------| -- |
| OH_AI_API [OH_AI_PerformanceMode](capi-types-h.md#oh_ai_performancemode) | [OH_AI_PerformanceMode](capi-types-h.md#oh_ai_performancemode) NNRt performance mode. |

### OH_AI_DeviceInfoSetPriority()

```c
OH_AI_API void OH_AI_DeviceInfoSetPriority(OH_AI_DeviceInfoHandle device_info, OH_AI_Priority priority)
```

**Description**

Sets the NNRt task priority. This interface is available only for NNRt devices.

**Since**: 10


**Parameters**

| Name | Description |
| -- | -- |
| [OH_AI_DeviceInfoHandle](capi-mindspore-oh-ai-DeviceInfoHandle.md) device_info | Pointer to the [OH_AI_DeviceInfoHandle](capi-mindspore-oh-ai-DeviceInfoHandle.md) of the device information instance. |
| [OH_AI_Priority](capi-types-h.md#oh_ai_priority) priority | [OH_AI_Priority](capi-types-h.md#oh_ai_priority) NNRt task priority. |

### OH_AI_DeviceInfoGetPriority()

```c
OH_AI_API OH_AI_Priority OH_AI_DeviceInfoGetPriority(const OH_AI_DeviceInfoHandle device_info)
```

**Description**

Gets the NNRt task priority. This interface is available only for NNRt devices.

**Since**: 23


**Parameters**

| Name | Description |
| -- | -- |
| const [OH_AI_DeviceInfoHandle](capi-mindspore-oh-ai-DeviceInfoHandle.md) device_info | Pointer to the [OH_AI_DeviceInfoHandle](capi-mindspore-oh-ai-DeviceInfoHandle.md) of the device information instance. |

**Return**

| Type | Description |
| -- | -- |
| OH_AI_API [OH_AI_Priority](capi-types-h.md#oh_ai_priority) | [OH_AI_Priority](capi-types-h.md#oh_ai_priority) NNRt task priority. |

### OH_AI_DeviceInfoAddExtension()

```c
OH_AI_API OH_AI_Status OH_AI_DeviceInfoAddExtension(OH_AI_DeviceInfoHandle device_info, const char *name,const char *value, size_t value_size)
```

**Description**

Adds an extension configuration in the form of key/value pairs to the device information. This interface is valid only for NNRt device information.<br>Currently, only the following 11 keys are supported: {"CachePath": "YourCachePath"}, {"CacheVersion": "YourCacheVersion"},<br> {"QuantBuffer": "YourQuantBuffer"}, {"ModelName": "YourModelName"},<br> {"isProfiling": "YourProfilingSwitch"}, {"opLayout": "YourOpLayout"},<br> {"InputDims": "YourInputDims"}, {"DynamicDims": "YourDynamicDims"},<br> {"QuantConfigData": "YourQuantConfigData"}, {"BandMode": "YourBandMode"},<br> {"NPU_FM_SHARED": "YourNPU_FM_SHARED"}. You can configure the value of each key based on your usage.

**Since**: 10


**Parameters**

| Name | Description |
| -- | -- |
| [OH_AI_DeviceInfoHandle](capi-mindspore-oh-ai-DeviceInfoHandle.md) device_info | Pointer to the [OH_AI_DeviceInfoHandle](capi-mindspore-oh-ai-DeviceInfoHandle.md) of the device information instance. |
| const char *name | Key of a single extension item, in the C string format. The string length is limited to 128. |
| const char *value | Start address of the value content of a single extension item. The string length is subject to the system limitation. |
| size_t value_size | Length of the value content of a single extension item. |

**Return**

| Type                                                      | Description |
|---------------------------------------------------------| -- |
| OH_AI_API [OH_AI_Status](capi-status-h.md#oh_ai_status) | [OH_AI_Status](capi-status-h.md#oh_ai_status) result code. Returns OH_AI_STATUS_SUCCESS if the operation is successful; returns a specific error code otherwise. |


