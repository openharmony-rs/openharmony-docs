# types.h

## Overview

Provides the model file types and device types supported by MindSpore Lite.

**Library**: libmindspore_lite_ndk.so

**Since**: 9

**Related module**: [MindSpore](capi-mind-spore-lite-kit-mindspore.md)

## Summary

### Structs

| Name | typedef keyword | Description |
| -- | -- | -- |
| [NNRTDeviceDesc](capi-mindspore-nnrtdevicedesc.md) | NNRTDeviceDesc | Defines the device descriptor of NNRT. |

### Enums

| Name | typedef keyword | Description |
| -- | -- | -- |
| [OH_AI_ModelType](#oh_ai_modeltype) | OH_AI_ModelType | model file type. |
| [OH_AI_DeviceType](#oh_ai_devicetype) | OH_AI_DeviceType | device type information. |
| [OH_AI_NNRTDeviceType](#oh_ai_nnrtdevicetype) | OH_AI_NNRTDeviceType | the hard device type managed by NNRT. |
| [OH_AI_PerformanceMode](#oh_ai_performancemode) | OH_AI_PerformanceMode | performance mode of the NNRT hard device. |
| [OH_AI_Priority](#oh_ai_priority) | OH_AI_Priority | NNRT inference task priority. |
| [OH_AI_OptimizationLevel](#oh_ai_optimizationlevel) | OH_AI_OptimizationLevel | optimization level for train model. |
| [OH_AI_QuantizationType](#oh_ai_quantizationtype) | OH_AI_QuantizationType | quantization type |

### Macros

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

<!--Device-enum OH_AI_ModelType--><!--Device-enum OH_AI_ModelType-End-->

**Since**: 9

| Enum item | Description |
| -- | -- |
| OH_AI_MODELTYPE_MINDIR = 0 | the model type is MindIR, and the corresponding model file extension is .ms.<br><!--Device-OH_AI_MODELTYPE_MINDIR = 0--><!--Device-OH_AI_MODELTYPE_MINDIR = 0-End--> |
| OH_AI_MODELTYPE_INVALID = 0xFFFFFFFF | invalid model type<br><!--Device-OH_AI_MODELTYPE_INVALID = 0xFFFFFFFF--><!--Device-OH_AI_MODELTYPE_INVALID = 0xFFFFFFFF-End--> |

### OH_AI_DeviceType

```c
enum OH_AI_DeviceType
```

**Description**

device type information.

<!--Device-enum OH_AI_DeviceType--><!--Device-enum OH_AI_DeviceType-End-->

**Since**: 9

| Enum item | Description |
| -- | -- |
| OH_AI_DEVICETYPE_CPU = 0 | cpu<br><!--Device-OH_AI_DEVICETYPE_CPU = 0--><!--Device-OH_AI_DEVICETYPE_CPU = 0-End--> |
| OH_AI_DEVICETYPE_GPU | gpu<br><!--Device-OH_AI_DEVICETYPE_GPU--><!--Device-OH_AI_DEVICETYPE_GPU-End--> |
| OH_AI_DEVICETYPE_KIRIN_NPU | kirin npu<br><!--Device-OH_AI_DEVICETYPE_KIRIN_NPU--><!--Device-OH_AI_DEVICETYPE_KIRIN_NPU-End--> |
| OH_AI_DEVICETYPE_NNRT = 60 | nnrt device, ohos-only device range: [60, 80)<br><!--Device-OH_AI_DEVICETYPE_NNRT = 60--><!--Device-OH_AI_DEVICETYPE_NNRT = 60-End--> |
| OH_AI_DEVICETYPE_INVALID = 100 | invalid device type<br><!--Device-OH_AI_DEVICETYPE_INVALID = 100--><!--Device-OH_AI_DEVICETYPE_INVALID = 100-End--> |

### OH_AI_NNRTDeviceType

```c
enum OH_AI_NNRTDeviceType
```

**Description**

the hard device type managed by NNRT.

<!--Device-enum OH_AI_NNRTDeviceType--><!--Device-enum OH_AI_NNRTDeviceType-End-->

**Since**: 10

| Enum item | Description |
| -- | -- |
| OH_AI_NNRTDEVICE_OTHERS = 0 | Devices that are not CPU, GPU, or dedicated accelerator<br><!--Device-OH_AI_NNRTDEVICE_OTHERS = 0--><!--Device-OH_AI_NNRTDEVICE_OTHERS = 0-End--> |
| OH_AI_NNRTDEVICE_CPU = 1 | CPU device<br><!--Device-OH_AI_NNRTDEVICE_CPU = 1--><!--Device-OH_AI_NNRTDEVICE_CPU = 1-End--> |
| OH_AI_NNRTDEVICE_GPU = 2 | GPU device<br><!--Device-OH_AI_NNRTDEVICE_GPU = 2--><!--Device-OH_AI_NNRTDEVICE_GPU = 2-End--> |
| OH_AI_NNRTDEVICE_ACCELERATOR = 3 | Dedicated hardware accelerator<br><!--Device-OH_AI_NNRTDEVICE_ACCELERATOR = 3--><!--Device-OH_AI_NNRTDEVICE_ACCELERATOR = 3-End--> |

### OH_AI_PerformanceMode

```c
enum OH_AI_PerformanceMode
```

**Description**

performance mode of the NNRT hard device.

<!--Device-enum OH_AI_PerformanceMode--><!--Device-enum OH_AI_PerformanceMode-End-->

**Since**: 10

| Enum item | Description |
| -- | -- |
| OH_AI_PERFORMANCE_NONE = 0 | No performance mode preference<br><!--Device-OH_AI_PERFORMANCE_NONE = 0--><!--Device-OH_AI_PERFORMANCE_NONE = 0-End--> |
| OH_AI_PERFORMANCE_LOW = 1 | Low power consumption mode<br><!--Device-OH_AI_PERFORMANCE_LOW = 1--><!--Device-OH_AI_PERFORMANCE_LOW = 1-End--> |
| OH_AI_PERFORMANCE_MEDIUM = 2 | Medium performance mode<br><!--Device-OH_AI_PERFORMANCE_MEDIUM = 2--><!--Device-OH_AI_PERFORMANCE_MEDIUM = 2-End--> |
| OH_AI_PERFORMANCE_HIGH = 3 | High performance mode<br><!--Device-OH_AI_PERFORMANCE_HIGH = 3--><!--Device-OH_AI_PERFORMANCE_HIGH = 3-End--> |
| OH_AI_PERFORMANCE_EXTREME = 4 | Ultimate performance mode<br><!--Device-OH_AI_PERFORMANCE_EXTREME = 4--><!--Device-OH_AI_PERFORMANCE_EXTREME = 4-End--> |

### OH_AI_Priority

```c
enum OH_AI_Priority
```

**Description**

NNRT inference task priority.

<!--Device-enum OH_AI_Priority--><!--Device-enum OH_AI_Priority-End-->

**Since**: 10

| Enum item | Description |
| -- | -- |
| OH_AI_PRIORITY_NONE = 0 | No priority preference<br><!--Device-OH_AI_PRIORITY_NONE = 0--><!--Device-OH_AI_PRIORITY_NONE = 0-End--> |
| OH_AI_PRIORITY_LOW = 1 | Low priority<br><!--Device-OH_AI_PRIORITY_LOW = 1--><!--Device-OH_AI_PRIORITY_LOW = 1-End--> |
| OH_AI_PRIORITY_MEDIUM = 2 | Medium priority<br><!--Device-OH_AI_PRIORITY_MEDIUM = 2--><!--Device-OH_AI_PRIORITY_MEDIUM = 2-End--> |
| OH_AI_PRIORITY_HIGH = 3 | High priority<br><!--Device-OH_AI_PRIORITY_HIGH = 3--><!--Device-OH_AI_PRIORITY_HIGH = 3-End--> |

### OH_AI_OptimizationLevel

```c
enum OH_AI_OptimizationLevel
```

**Description**

optimization level for train model.

<!--Device-enum OH_AI_OptimizationLevel--><!--Device-enum OH_AI_OptimizationLevel-End-->

**Since**: 11

| Enum item | Description |
| -- | -- |
| OH_AI_KO0 = 0 | Do not change<br><!--Device-OH_AI_KO0 = 0--><!--Device-OH_AI_KO0 = 0-End--> |
| OH_AI_KO2 = 2 | Cast network to float16, keep batchnorm and loss in float32<br><!--Device-OH_AI_KO2 = 2--><!--Device-OH_AI_KO2 = 2-End--> |
| OH_AI_KO3 = 3 | Cast network to float16, including batchnorm<br><!--Device-OH_AI_KO3 = 3--><!--Device-OH_AI_KO3 = 3-End--> |
| OH_AI_KAUTO = 4 | Choose optimization based on device<br><!--Device-OH_AI_KAUTO = 4--><!--Device-OH_AI_KAUTO = 4-End--> |
| OH_AI_KOPTIMIZATIONTYPE = 0xFFFFFFFF | Invalid optimization level<br><!--Device-OH_AI_KOPTIMIZATIONTYPE = 0xFFFFFFFF--><!--Device-OH_AI_KOPTIMIZATIONTYPE = 0xFFFFFFFF-End--> |

### OH_AI_QuantizationType

```c
enum OH_AI_QuantizationType
```

**Description**

quantization type

<!--Device-enum OH_AI_QuantizationType--><!--Device-enum OH_AI_QuantizationType-End-->

**Since**: 11

| Enum item | Description |
| -- | -- |
| OH_AI_NO_QUANT = 0 | Do not change<br><!--Device-OH_AI_NO_QUANT = 0--><!--Device-OH_AI_NO_QUANT = 0-End--> |
| OH_AI_WEIGHT_QUANT = 1 | weight quantization<br><!--Device-OH_AI_WEIGHT_QUANT = 1--><!--Device-OH_AI_WEIGHT_QUANT = 1-End--> |
| OH_AI_FULL_QUANT = 2 | full quantization<br><!--Device-OH_AI_FULL_QUANT = 2--><!--Device-OH_AI_FULL_QUANT = 2-End--> |
| OH_AI_UNKNOWN_QUANT_TYPE = 0xFFFFFFFF | invalid quantization type<br><!--Device-OH_AI_UNKNOWN_QUANT_TYPE = 0xFFFFFFFF--><!--Device-OH_AI_UNKNOWN_QUANT_TYPE = 0xFFFFFFFF-End--> |


