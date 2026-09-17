# types.h

## Overview

Provides the model file types and device types supported by MindSpore Lite.

**Library**: libmindspore_lite_ndk.so

**Since**: 9

**Related module**: [MindSpore](capi-mindspore.md)

## Summary

### Struct

| Name | typedef keyword | Description |
| -- | -- | -- |
| [NNRTDeviceDesc](capi-mindspore-nnrtdevicedesc.md) | NNRTDeviceDesc | Defines the device descriptor of NNRT. |

### Enum

| Name | typedef keyword | Description |
| -- | -- | -- |
| [OH_AI_ModelType](#oh_ai_modeltype) | OH_AI_ModelType | model file type. |
| [OH_AI_DeviceType](#oh_ai_devicetype) | OH_AI_DeviceType | device type information. |
| [OH_AI_NNRTDeviceType](#oh_ai_nnrtdevicetype) | OH_AI_NNRTDeviceType | the hard deivce type managed by NNRT. |
| [OH_AI_PerformanceMode](#oh_ai_performancemode) | OH_AI_PerformanceMode | performance mode of the NNRT hard deivce. |
| [OH_AI_Priority](#oh_ai_priority) | OH_AI_Priority | NNRT reasoning task priority. |
| [OH_AI_OptimizationLevel](#oh_ai_optimizationlevel) | OH_AI_OptimizationLevel | optimization level for train model. |
| [OH_AI_QuantizationType](#oh_ai_quantizationtype) | OH_AI_QuantizationType | quantization type |

### Macro

| Name | Description |
| -- | -- |
| MINDSPORE_INCLUDE_C_API_TYPES_C_H | Provides the model file types and device types supported by MindSpore Lite.<br>**Since**: 9 |

## Enum type description

### OH_AI_ModelType

```c
enum OH_AI_ModelType
```

**Description**

model file type.

**Since**: 9

| Enum item | Description |
| -- | -- |
| OH_AI_MODELTYPE_MINDIR = 0 | the model type is MindIR, and the corresponding model file extension is .ms. |
| OH_AI_MODELTYPE_INVALID = 0xFFFFFFFF | invaild model type |

### OH_AI_DeviceType

```c
enum OH_AI_DeviceType
```

**Description**

device type information.

**Since**: 9

| Enum item | Description |
| -- | -- |
| OH_AI_DEVICETYPE_CPU = 0 | cpu |
| OH_AI_DEVICETYPE_GPU | gpu |
| OH_AI_DEVICETYPE_KIRIN_NPU | kirin npu |
| OH_AI_DEVICETYPE_NNRT = 60 | nnrt device, ohos-only device range: [60, 80) |
| OH_AI_DEVICETYPE_INVALID = 100 | invalid device type |

### OH_AI_NNRTDeviceType

```c
enum OH_AI_NNRTDeviceType
```

**Description**

the hard deivce type managed by NNRT.

**Since**: 10

| Enum item | Description |
| -- | -- |
| OH_AI_NNRTDEVICE_OTHERS = 0 | Devices that are not CPU, GPU, or dedicated accelerator |
| OH_AI_NNRTDEVICE_CPU = 1 | CPU device |
| OH_AI_NNRTDEVICE_GPU = 2 | GPU device |
| OH_AI_NNRTDEVICE_ACCELERATOR = 3 | Dedicated hardware accelerator |

### OH_AI_PerformanceMode

```c
enum OH_AI_PerformanceMode
```

**Description**

performance mode of the NNRT hard deivce.

**Since**: 10

| Enum item | Description |
| -- | -- |
| OH_AI_PERFORMANCE_NONE = 0 | No performance mode preference |
| OH_AI_PERFORMANCE_LOW = 1 | Low power consumption mode |
| OH_AI_PERFORMANCE_MEDIUM = 2 | Medium performance mode |
| OH_AI_PERFORMANCE_HIGH = 3 | High performance mode |
| OH_AI_PERFORMANCE_EXTREME = 4 | Ultimate performance mode |

### OH_AI_Priority

```c
enum OH_AI_Priority
```

**Description**

NNRT reasoning task priority.

**Since**: 10

| Enum item | Description |
| -- | -- |
| OH_AI_PRIORITY_NONE = 0 | No priority preference |
| OH_AI_PRIORITY_LOW = 1 | Low priority |
| OH_AI_PRIORITY_MEDIUM = 2 | Medium priority |
| OH_AI_PRIORITY_HIGH = 3 | High priority |

### OH_AI_OptimizationLevel

```c
enum OH_AI_OptimizationLevel
```

**Description**

optimization level for train model.

**Since**: 11

| Enum item | Description |
| -- | -- |
| OH_AI_KO0 = 0 | Do not change |
| OH_AI_KO2 = 2 | Cast network to float16, keep batchnorm and loss in float32 |
| OH_AI_KO3 = 3 | Cast network to float16, including bacthnorm |
| OH_AI_KAUTO = 4 | Choose optimization based on device |
| OH_AI_KOPTIMIZATIONTYPE = 0xFFFFFFFF | Invalid optimizatin level |

### OH_AI_QuantizationType

```c
enum OH_AI_QuantizationType
```

**Description**

quantization type

**Since**: 11

| Enum item | Description |
| -- | -- |
| OH_AI_NO_QUANT = 0 | Do not change |
| OH_AI_WEIGHT_QUANT = 1 | weight quantization |
| OH_AI_FULL_QUANT = 2 | full quantization |
| OH_AI_UNKNOWN_QUANT_TYPE = 0xFFFFFFFF | invalid quantization type |


