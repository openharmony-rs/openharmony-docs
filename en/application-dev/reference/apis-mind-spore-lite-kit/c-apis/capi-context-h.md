# context.h

## Overview

Provides **Context** APIs for configuring runtime information.

**Library**: libmindspore_lite_ndk.so

**Since**: 13

**Related module**: [MindSpore](capi-mindspore.md)

## Summary

### Macro

| Name | Description |
| -- | -- |
| MINDSPORE_INCLUDE_C_API_CONTEXT_C_H | Provides **Context** APIs for configuring runtime information.<br>**Since**: 9 |

### Function

| Name | Description |
| -- | -- |
| [OH_AI_API OH_AI_ContextHandle OH_AI_ContextCreate()](#oh_ai_contextcreate) | Create a context object. |
| [OH_AI_API void OH_AI_ContextDestroy(OH_AI_ContextHandle *context)](#oh_ai_contextdestroy) | Destroy the context object. |
| [OH_AI_API void OH_AI_ContextSetThreadNum(OH_AI_ContextHandle context, int32_t thread_num)](#oh_ai_contextsetthreadnum) | Set the number of threads at runtime. |
| [OH_AI_API int32_t OH_AI_ContextGetThreadNum(const OH_AI_ContextHandle context)](#oh_ai_contextgetthreadnum) | Obtain the current thread number setting. |
| [OH_AI_API void OH_AI_ContextSetThreadAffinityMode(OH_AI_ContextHandle context, int mode)](#oh_ai_contextsetthreadaffinitymode) | Set the thread affinity to CPU cores. |
| [OH_AI_API int OH_AI_ContextGetThreadAffinityMode(const OH_AI_ContextHandle context)](#oh_ai_contextgetthreadaffinitymode) | Obtain the thread affinity of CPU cores. |
| [OH_AI_API void OH_AI_ContextSetThreadAffinityCoreList(OH_AI_ContextHandle context, const int32_t *core_list, size_t core_num)](#oh_ai_contextsetthreadaffinitycorelist) | Set the thread lists to CPU cores.<br> If core_list and mode are set by OH_AI_ContextSetThreadAffinityMode at the same time, the core_list is effective, but the mode is not effective. |
| [OH_AI_API const int32_t *OH_AI_ContextGetThreadAffinityCoreList(const OH_AI_ContextHandle context, size_t *core_num)](#oh_ai_contextgetthreadaffinitycorelist) | Obtain the thread lists of CPU cores. |
| [OH_AI_API void OH_AI_ContextSetEnableParallel(OH_AI_ContextHandle context, bool is_parallel)](#oh_ai_contextsetenableparallel) | Set the status whether to perform model inference or training in parallel. |
| [OH_AI_API bool OH_AI_ContextGetEnableParallel(const OH_AI_ContextHandle context)](#oh_ai_contextgetenableparallel) | Obtain the status whether to perform model inference or training in parallel. |
| [OH_AI_API void OH_AI_ContextAddDeviceInfo(OH_AI_ContextHandle context, OH_AI_DeviceInfoHandle device_info)](#oh_ai_contextadddeviceinfo) | Add device info to context object. |
| [OH_AI_API OH_AI_DeviceInfoHandle OH_AI_DeviceInfoCreate(OH_AI_DeviceType device_type)](#oh_ai_deviceinfocreate) | Create a device info object. |
| [OH_AI_API void OH_AI_DeviceInfoDestroy(OH_AI_DeviceInfoHandle *device_info)](#oh_ai_deviceinfodestroy) | Destroy the device info object. |
| [OH_AI_API void OH_AI_DeviceInfoSetProvider(OH_AI_DeviceInfoHandle device_info, const char *provider)](#oh_ai_deviceinfosetprovider) | Set provider's name. |
| [OH_AI_API const char *OH_AI_DeviceInfoGetProvider(const OH_AI_DeviceInfoHandle device_info)](#oh_ai_deviceinfogetprovider) | Obtain provider's name |
| [OH_AI_API void OH_AI_DeviceInfoSetProviderDevice(OH_AI_DeviceInfoHandle device_info, const char *device)](#oh_ai_deviceinfosetproviderdevice) | Set provider's device type. |
| [OH_AI_API const char *OH_AI_DeviceInfoGetProviderDevice(const OH_AI_DeviceInfoHandle device_info)](#oh_ai_deviceinfogetproviderdevice) | Obtain provider's device type. |
| [OH_AI_API OH_AI_DeviceType OH_AI_DeviceInfoGetDeviceType(const OH_AI_DeviceInfoHandle device_info)](#oh_ai_deviceinfogetdevicetype) | Obtain the device type of the device info. |
| [OH_AI_API void OH_AI_DeviceInfoSetEnableFP16(OH_AI_DeviceInfoHandle device_info, bool is_fp16)](#oh_ai_deviceinfosetenablefp16) | Set enables to perform the float16 inference, Only valid for CPU/GPU. |
| [OH_AI_API bool OH_AI_DeviceInfoGetEnableFP16(const OH_AI_DeviceInfoHandle device_info)](#oh_ai_deviceinfogetenablefp16) | Obtain enables to perform the float16 inference, Only valid for CPU/GPU. |
| [OH_AI_API void OH_AI_DeviceInfoSetFrequency(OH_AI_DeviceInfoHandle device_info, int frequency)](#oh_ai_deviceinfosetfrequency) | Set the NPU frequency, Only valid for NPU. |
| [OH_AI_API int OH_AI_DeviceInfoGetFrequency(const OH_AI_DeviceInfoHandle device_info)](#oh_ai_deviceinfogetfrequency) | Obtain the NPU frequency, Only valid for NPU. |
| [OH_AI_API NNRTDeviceDesc *OH_AI_GetAllNNRTDeviceDescs(size_t *num)](#oh_ai_getallnnrtdevicedescs) | Obtain the all device descriptions in NNRT. |
| [OH_AI_API NNRTDeviceDesc *OH_AI_GetElementOfNNRTDeviceDescs(NNRTDeviceDesc *descs, size_t index)](#oh_ai_getelementofnnrtdevicedescs) | Obtain the specified element in NNRt device description array. |
| [OH_AI_API void OH_AI_DestroyAllNNRTDeviceDescs(NNRTDeviceDesc **desc)](#oh_ai_destroyallnnrtdevicedescs) | Destroy the NNRT device descriptions returned by OH_AI_NNRTGetAllDeviceDescs(). |
| [OH_AI_API size_t OH_AI_GetDeviceIdFromNNRTDeviceDesc(const NNRTDeviceDesc *desc)](#oh_ai_getdeviceidfromnnrtdevicedesc) | Obtain the device id in NNRT device description. |
| [OH_AI_API const char *OH_AI_GetNameFromNNRTDeviceDesc(const NNRTDeviceDesc *desc)](#oh_ai_getnamefromnnrtdevicedesc) | Obtain the device name in NNRT device description. |
| [OH_AI_API OH_AI_NNRTDeviceType OH_AI_GetTypeFromNNRTDeviceDesc(const NNRTDeviceDesc *desc)](#oh_ai_gettypefromnnrtdevicedesc) | Obtain the device type in NNRT device description. |
| [OH_AI_API OH_AI_DeviceInfoHandle OH_AI_CreateNNRTDeviceInfoByName(const char *name)](#oh_ai_creatennrtdeviceinfobyname) | Create the NNRT device info by exactly matching the specific device name. |
| [OH_AI_API OH_AI_DeviceInfoHandle OH_AI_CreateNNRTDeviceInfoByType(OH_AI_NNRTDeviceType type)](#oh_ai_creatennrtdeviceinfobytype) | Create the NNRT device info by finding the first device with the specific device type. |
| [OH_AI_API void OH_AI_DeviceInfoSetDeviceId(OH_AI_DeviceInfoHandle device_info, size_t device_id)](#oh_ai_deviceinfosetdeviceid) | Set the NNRT device id, Only valid for NNRT. |
| [OH_AI_API size_t OH_AI_DeviceInfoGetDeviceId(const OH_AI_DeviceInfoHandle device_info)](#oh_ai_deviceinfogetdeviceid) | Obtain the NNRT device id, Only valid for NNRT. |
| [OH_AI_API void OH_AI_DeviceInfoSetPerformanceMode(OH_AI_DeviceInfoHandle device_info, OH_AI_PerformanceMode mode)](#oh_ai_deviceinfosetperformancemode) | Set the NNRT performance mode, Only valid for NNRT. |
| [OH_AI_API OH_AI_PerformanceMode OH_AI_DeviceInfoGetPerformanceMode(const OH_AI_DeviceInfoHandle device_info)](#oh_ai_deviceinfogetperformancemode) | Obtain the NNRT performance mode, Only valid for NNRT. |
| [OH_AI_API void OH_AI_DeviceInfoSetPriority(OH_AI_DeviceInfoHandle device_info, OH_AI_Priority priority)](#oh_ai_deviceinfosetpriority) | Set the NNRT priority, Only valid for NNRT. |
| [OH_AI_API OH_AI_Priority OH_AI_DeviceInfoGetPriority(const OH_AI_DeviceInfoHandle device_info)](#oh_ai_deviceinfogetpriority) | Obtain the NNRT priority, Only valid for NNRT. |
| [OH_AI_API OH_AI_Status OH_AI_DeviceInfoAddExtension(OH_AI_DeviceInfoHandle device_info, const char *name, const char *value, size_t value_size)](#oh_ai_deviceinfoaddextension) | Add extension of key/value format to device info, Only valid for NNRT. |

## Function description

### OH_AI_ContextCreate()

```c
OH_AI_API OH_AI_ContextHandle OH_AI_ContextCreate()
```

**Description**

Create a context object.

**Since**: 9

**Returns**:

| Type | Description |
| -- | -- |
| OH_AI_API OH_AI_ContextHandle | Context object handle. |

### OH_AI_ContextDestroy()

```c
OH_AI_API void OH_AI_ContextDestroy(OH_AI_ContextHandle *context)
```

**Description**

Destroy the context object.

**Since**: 9

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AI_ContextHandle *context | Context object handle address. |

### OH_AI_ContextSetThreadNum()

```c
OH_AI_API void OH_AI_ContextSetThreadNum(OH_AI_ContextHandle context, int32_t thread_num)
```

**Description**

Set the number of threads at runtime.

**Since**: 9

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AI_ContextHandle context | Context object handle. |
| int32_t thread_num | the number of threads at runtime. |

### OH_AI_ContextGetThreadNum()

```c
OH_AI_API int32_t OH_AI_ContextGetThreadNum(const OH_AI_ContextHandle context)
```

**Description**

Obtain the current thread number setting.

**Since**: 9

**Parameters**:

| Parameter | Description |
| -- | -- |
| const OH_AI_ContextHandle context | Context object handle. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AI_API int32_t | The current thread number setting. |

### OH_AI_ContextSetThreadAffinityMode()

```c
OH_AI_API void OH_AI_ContextSetThreadAffinityMode(OH_AI_ContextHandle context, int mode)
```

**Description**

Set the thread affinity to CPU cores.

**Since**: 9

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AI_ContextHandle context | Context object handle. |
| mode: | 0: no affinities, 1: big cores first, 2: little cores first |

### OH_AI_ContextGetThreadAffinityMode()

```c
OH_AI_API int OH_AI_ContextGetThreadAffinityMode(const OH_AI_ContextHandle context)
```

**Description**

Obtain the thread affinity of CPU cores.

**Since**: 9

**Parameters**:

| Parameter | Description |
| -- | -- |
| const OH_AI_ContextHandle context | Context object handle. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AI_API int | Thread affinity to CPU cores. 0: no affinities, 1: big cores first, 2: little cores first |

### OH_AI_ContextSetThreadAffinityCoreList()

```c
OH_AI_API void OH_AI_ContextSetThreadAffinityCoreList(OH_AI_ContextHandle context, const int32_t *core_list, size_t core_num)
```

**Description**

Set the thread lists to CPU cores.<br> If core_list and mode are set by OH_AI_ContextSetThreadAffinityMode at the same time, the core_list is effective, but the mode is not effective.

**Since**: 9

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AI_ContextHandle context | Context object handle. |
| core_list: | a array of thread core lists. |
| size_t core_num | The number of core. |

### OH_AI_ContextGetThreadAffinityCoreList()

```c
OH_AI_API const int32_t *OH_AI_ContextGetThreadAffinityCoreList(const OH_AI_ContextHandle context, size_t *core_num)
```

**Description**

Obtain the thread lists of CPU cores.

**Since**: 9

**Parameters**:

| Parameter | Description |
| -- | -- |
| const OH_AI_ContextHandle context | Context object handle. |
| size_t *core_num | The number of core. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AI_API const int32_t * | a array of thread core lists. |

### OH_AI_ContextSetEnableParallel()

```c
OH_AI_API void OH_AI_ContextSetEnableParallel(OH_AI_ContextHandle context, bool is_parallel)
```

**Description**

Set the status whether to perform model inference or training in parallel.

**Since**: 9

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AI_ContextHandle context | Context object handle. |
| is_parallel: | true, parallel; false, not in parallel. |

### OH_AI_ContextGetEnableParallel()

```c
OH_AI_API bool OH_AI_ContextGetEnableParallel(const OH_AI_ContextHandle context)
```

**Description**

Obtain the status whether to perform model inference or training in parallel.

**Since**: 9

**Parameters**:

| Parameter | Description |
| -- | -- |
| const OH_AI_ContextHandle context | Context object handle. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AI_API bool | Bool value that indicates whether in parallel. |

### OH_AI_ContextAddDeviceInfo()

```c
OH_AI_API void OH_AI_ContextAddDeviceInfo(OH_AI_ContextHandle context, OH_AI_DeviceInfoHandle device_info)
```

**Description**

Add device info to context object.

**Since**: 9

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AI_ContextHandle context | Context object handle. |
| OH_AI_DeviceInfoHandle device_info | Device info object handle. |

### OH_AI_DeviceInfoCreate()

```c
OH_AI_API OH_AI_DeviceInfoHandle OH_AI_DeviceInfoCreate(OH_AI_DeviceType device_type)
```

**Description**

Create a device info object.

**Since**: 9

**Parameters**:

| Parameter | Description |
| -- | -- |
| device_info | Device info object handle. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AI_API OH_AI_DeviceInfoHandle | Device info object handle. |

### OH_AI_DeviceInfoDestroy()

```c
OH_AI_API void OH_AI_DeviceInfoDestroy(OH_AI_DeviceInfoHandle *device_info)
```

**Description**

Destroy the device info object.

**Since**: 9

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AI_DeviceInfoHandle *device_info | Device info object handle address. |

### OH_AI_DeviceInfoSetProvider()

```c
OH_AI_API void OH_AI_DeviceInfoSetProvider(OH_AI_DeviceInfoHandle device_info, const char *provider)
```

**Description**

Set provider's name.

**Since**: 9

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AI_DeviceInfoHandle device_info | Device info object handle. |
| const char *provider | define the provider's name. |

### OH_AI_DeviceInfoGetProvider()

```c
OH_AI_API const char *OH_AI_DeviceInfoGetProvider(const OH_AI_DeviceInfoHandle device_info)
```

**Description**

Obtain provider's name

**Since**: 9

**Parameters**:

| Parameter | Description |
| -- | -- |
| const OH_AI_DeviceInfoHandle device_info | Device info object handle. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AI_API const char * | provider's name. |

### OH_AI_DeviceInfoSetProviderDevice()

```c
OH_AI_API void OH_AI_DeviceInfoSetProviderDevice(OH_AI_DeviceInfoHandle device_info, const char *device)
```

**Description**

Set provider's device type.

**Since**: 9

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AI_DeviceInfoHandle device_info | Device info object handle. |
| const char *device | define the provider's device type. EG: CPU. |

### OH_AI_DeviceInfoGetProviderDevice()

```c
OH_AI_API const char *OH_AI_DeviceInfoGetProviderDevice(const OH_AI_DeviceInfoHandle device_info)
```

**Description**

Obtain provider's device type.

**Since**: 9

**Parameters**:

| Parameter | Description |
| -- | -- |
| const OH_AI_DeviceInfoHandle device_info | Device info object handle. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AI_API const char * | provider's device type. |

### OH_AI_DeviceInfoGetDeviceType()

```c
OH_AI_API OH_AI_DeviceType OH_AI_DeviceInfoGetDeviceType(const OH_AI_DeviceInfoHandle device_info)
```

**Description**

Obtain the device type of the device info.

**Since**: 9

**Parameters**:

| Parameter | Description |
| -- | -- |
| const OH_AI_DeviceInfoHandle device_info | Device info object handle. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AI_API OH_AI_DeviceType | Device Type of the device info. |

### OH_AI_DeviceInfoSetEnableFP16()

```c
OH_AI_API void OH_AI_DeviceInfoSetEnableFP16(OH_AI_DeviceInfoHandle device_info, bool is_fp16)
```

**Description**

Set enables to perform the float16 inference, Only valid for CPU/GPU.

**Since**: 9

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AI_DeviceInfoHandle device_info | Device info object handle. |
| bool is_fp16 | Enable float16 inference or not. |

### OH_AI_DeviceInfoGetEnableFP16()

```c
OH_AI_API bool OH_AI_DeviceInfoGetEnableFP16(const OH_AI_DeviceInfoHandle device_info)
```

**Description**

Obtain enables to perform the float16 inference, Only valid for CPU/GPU.

**Since**: 9

**Parameters**:

| Parameter | Description |
| -- | -- |
| const OH_AI_DeviceInfoHandle device_info | Device info object handle. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AI_API bool | Whether enable float16 inference. |

### OH_AI_DeviceInfoSetFrequency()

```c
OH_AI_API void OH_AI_DeviceInfoSetFrequency(OH_AI_DeviceInfoHandle device_info, int frequency)
```

**Description**

Set the NPU frequency, Only valid for NPU.

**Since**: 9

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AI_DeviceInfoHandle device_info | Device info object handle. |
| int frequency | Can be set to 0 (automatic adjustment), 1 (low power consumption), 2 (balanced), 3 (high performance), 4 (extreme performance), default as 3. |

### OH_AI_DeviceInfoGetFrequency()

```c
OH_AI_API int OH_AI_DeviceInfoGetFrequency(const OH_AI_DeviceInfoHandle device_info)
```

**Description**

Obtain the NPU frequency, Only valid for NPU.

**Since**: 9

**Parameters**:

| Parameter | Description |
| -- | -- |
| const OH_AI_DeviceInfoHandle device_info | Device info object handle. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AI_API int | NPU frequency |

### OH_AI_GetAllNNRTDeviceDescs()

```c
OH_AI_API NNRTDeviceDesc *OH_AI_GetAllNNRTDeviceDescs(size_t *num)
```

**Description**

Obtain the all device descriptions in NNRT.

**Since**: 10

**Parameters**:

| Parameter | Description |
| -- | -- |
| size_t *num | Number of NNRT device description. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AI_API NNRTDeviceDesc * | NNRT device description array. |

### OH_AI_GetElementOfNNRTDeviceDescs()

```c
OH_AI_API NNRTDeviceDesc *OH_AI_GetElementOfNNRTDeviceDescs(NNRTDeviceDesc *descs, size_t index)
```

**Description**

Obtain the specified element in NNRt device description array.

**Since**: 10

**Parameters**:

| Parameter | Description |
| -- | -- |
| NNRTDeviceDesc *descs | NNRT device description array. |
| size_t index | Element index. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AI_API NNRTDeviceDesc * | NNRT device description. |

### OH_AI_DestroyAllNNRTDeviceDescs()

```c
OH_AI_API void OH_AI_DestroyAllNNRTDeviceDescs(NNRTDeviceDesc **desc)
```

**Description**

Destroy the NNRT device descriptions returned by OH_AI_NNRTGetAllDeviceDescs().

**Since**: 10

**Parameters**:

| Parameter | Description |
| -- | -- |
| NNRTDeviceDesc **desc | NNRT device description array. |

### OH_AI_GetDeviceIdFromNNRTDeviceDesc()

```c
OH_AI_API size_t OH_AI_GetDeviceIdFromNNRTDeviceDesc(const NNRTDeviceDesc *desc)
```

**Description**

Obtain the device id in NNRT device description.

**Since**: 10

**Parameters**:

| Parameter | Description |
| -- | -- |
| const NNRTDeviceDesc *desc | pointer to the NNRT device description instance. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AI_API size_t | NNRT device id. |

### OH_AI_GetNameFromNNRTDeviceDesc()

```c
OH_AI_API const char *OH_AI_GetNameFromNNRTDeviceDesc(const NNRTDeviceDesc *desc)
```

**Description**

Obtain the device name in NNRT device description.

**Since**: 10

**Parameters**:

| Parameter | Description |
| -- | -- |
| const NNRTDeviceDesc *desc | pointer to the NNRT device description instance. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AI_API const char * | NNRT device name. |

### OH_AI_GetTypeFromNNRTDeviceDesc()

```c
OH_AI_API OH_AI_NNRTDeviceType OH_AI_GetTypeFromNNRTDeviceDesc(const NNRTDeviceDesc *desc)
```

**Description**

Obtain the device type in NNRT device description.

**Since**: 10

**Parameters**:

| Parameter | Description |
| -- | -- |
| const NNRTDeviceDesc *desc | pointer to the NNRT device description instance. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AI_API OH_AI_NNRTDeviceType | NNRT device type. |

### OH_AI_CreateNNRTDeviceInfoByName()

```c
OH_AI_API OH_AI_DeviceInfoHandle OH_AI_CreateNNRTDeviceInfoByName(const char *name)
```

**Description**

Create the NNRT device info by exactly matching the specific device name.

**Since**: 10

**Parameters**:

| Parameter | Description |
| -- | -- |
| const char *name | NNRt device name. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AI_API OH_AI_DeviceInfoHandle | Device info object handle. |

### OH_AI_CreateNNRTDeviceInfoByType()

```c
OH_AI_API OH_AI_DeviceInfoHandle OH_AI_CreateNNRTDeviceInfoByType(OH_AI_NNRTDeviceType type)
```

**Description**

Create the NNRT device info by finding the first device with the specific device type.

**Since**: 10

**Parameters**:

| Parameter | Description |
| -- | -- |
| name | NNRt device type. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AI_API OH_AI_DeviceInfoHandle | Device info object handle. |

### OH_AI_DeviceInfoSetDeviceId()

```c
OH_AI_API void OH_AI_DeviceInfoSetDeviceId(OH_AI_DeviceInfoHandle device_info, size_t device_id)
```

**Description**

Set the NNRT device id, Only valid for NNRT.

**Since**: 10

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AI_DeviceInfoHandle device_info | Device info object handle. |
| size_t device_id | NNRT device id. |

### OH_AI_DeviceInfoGetDeviceId()

```c
OH_AI_API size_t OH_AI_DeviceInfoGetDeviceId(const OH_AI_DeviceInfoHandle device_info)
```

**Description**

Obtain the NNRT device id, Only valid for NNRT.

**Since**: 10

**Parameters**:

| Parameter | Description |
| -- | -- |
| const OH_AI_DeviceInfoHandle device_info | Device info object handle. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AI_API size_t | NNRT device id. |

### OH_AI_DeviceInfoSetPerformanceMode()

```c
OH_AI_API void OH_AI_DeviceInfoSetPerformanceMode(OH_AI_DeviceInfoHandle device_info, OH_AI_PerformanceMode mode)
```

**Description**

Set the NNRT performance mode, Only valid for NNRT.

**Since**: 10

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AI_DeviceInfoHandle device_info | Device info object handle. |
| device_id | NNRT performance mode. |

### OH_AI_DeviceInfoGetPerformanceMode()

```c
OH_AI_API OH_AI_PerformanceMode OH_AI_DeviceInfoGetPerformanceMode(const OH_AI_DeviceInfoHandle device_info)
```

**Description**

Obtain the NNRT performance mode, Only valid for NNRT.

**Since**: 10

**Parameters**:

| Parameter | Description |
| -- | -- |
| const OH_AI_DeviceInfoHandle device_info | Device info object handle. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AI_API OH_AI_PerformanceMode | NNRT performance mode. |

### OH_AI_DeviceInfoSetPriority()

```c
OH_AI_API void OH_AI_DeviceInfoSetPriority(OH_AI_DeviceInfoHandle device_info, OH_AI_Priority priority)
```

**Description**

Set the NNRT priority, Only valid for NNRT.

**Since**: 10

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AI_DeviceInfoHandle device_info | Device info object handle. |
| device_id | NNRT priority. |

### OH_AI_DeviceInfoGetPriority()

```c
OH_AI_API OH_AI_Priority OH_AI_DeviceInfoGetPriority(const OH_AI_DeviceInfoHandle device_info)
```

**Description**

Obtain the NNRT priority, Only valid for NNRT.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| const OH_AI_DeviceInfoHandle device_info | Device info object handle. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AI_API OH_AI_Priority | NNRT priority. |

### OH_AI_DeviceInfoAddExtension()

```c
OH_AI_API OH_AI_Status OH_AI_DeviceInfoAddExtension(OH_AI_DeviceInfoHandle device_info, const char *name, const char *value, size_t value_size)
```

**Description**

Add extension of key/value format to device info, Only valid for NNRT.

**Since**: 10

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AI_DeviceInfoHandle device_info | Device info object handle. |
| const char *name | The content of key as a C string. |
| const char *value | The pointer to the value, which is a byte array. |
| size_t value_size | The size of the value, which is a byte array. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AI_API OH_AI_Status | OH_AI_STATUS_SUCCESS if success, or detail error code if failed. |


