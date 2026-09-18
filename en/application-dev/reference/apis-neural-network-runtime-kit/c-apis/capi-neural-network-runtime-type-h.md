# neural_network_runtime_type.h

## Overview

Defines the structure and enumeration.<br> include "neural_network_runtime/neural_network_runtime_type.h"

**Library**: libneural_network_runtime.so

**System capability**: SystemCapability.AI.NeuralNetworkRuntime

**Since**: 9

**Related module**: [NeuralNetworkRuntime](capi-neuralnetworkruntime.md)

## Summary

### Struct

| Name | typedef keyword | Description |
| -- | -- | -- |
| [OH_NN_UInt32Array](capi-neuralnetworkruntime-oh-nn-uint32array.md) | OH_NN_UInt32Array | This structure is used to store a 32-bit unsigned integer array. |
| [OH_NN_QuantParam](capi-neuralnetworkruntime-oh-nn-quantparam.md) | OH_NN_QuantParam | Quantization information.<br> In quantization scenarios, the 32-bit floating-point data type is quantized into the fixed-point data type according to the following formula: \f[<br> q = clamp(round(\frac{r}{s}+z), q_{min}, q_{max})<br> \f]<br>s and z are quantization parameters, which are stored by <b>scale</b> and <b>zeroPoint</b><br>in [OH_NN_QuantParam](capi-neuralnetworkruntime-oh-nn-quantparam.md).<br>r is a floating point number, q is the quantization result, q_min is the lower bound of the quantization result, and<br>q_max is an upper bound of a quantization result. The calculation method is as follows:<br> \f[<br> \text{clamp}(x,min,max) =<br> \begin{cases}<br> q_{min} = -(1 << (numBits - 1)) \ q_{max} = (1 << (numBits - 1)) \ \end{cases}<br> \f]<br>The clamp function is defined as follows:<br> \f[<br> \text{clamp}(x,min,max) =<br> \begin{cases}<br> \text{max} & \text{ if } x > \text{ max } \ \text{min} & \text{ if } x < \text{ min } \ x & \text{ otherwise } \ \end{cases}<br> \f] |
| [OH_NN_Tensor](capi-neuralnetworkruntime-oh-nn-tensor.md) | OH_NN_Tensor | Defines the tensor structure.<br> It is usually used to construct data nodes and operator parameters in a model graph. When constructing a tensor, you need to specify the data type, number of dimensions, dimension information, and quantization information. |
| [OH_NN_Memory](capi-neuralnetworkruntime-oh-nn-memory.md) | OH_NN_Memory | Defines the memory structure. |
| [OH_NNModel](capi-neuralnetworkruntime-oh-nnmodel.md) | OH_NNModel | Defines the handles of models. |
| [OH_NNCompilation](capi-neuralnetworkruntime-oh-nncompilation.md) | OH_NNCompilation | Defines the compilation handle. |
| [OH_NNExecutor](capi-neuralnetworkruntime-oh-nnexecutor.md) | OH_NNExecutor | Defines the executor handle. |
| [NN_QuantParam](capi-neuralnetworkruntime-nn-quantparam.md) | NN_QuantParam | Defines the quantization parameter handle. |
| [NN_TensorDesc](capi-neuralnetworkruntime-nn-tensordesc.md) | NN_TensorDesc | Defines the tensor descriptor handle. |
| [NN_Tensor](capi-neuralnetworkruntime-nn-tensor.md) | NN_Tensor | Defines the tensor handle. |

### Enum

| Name | typedef keyword | Description |
| -- | -- | -- |
| [OH_NN_PerformanceMode](#oh_nn_performancemode) | OH_NN_PerformanceMode | Defines the hardware performance mode. |
| [OH_NN_Priority](#oh_nn_priority) | OH_NN_Priority | Defines the model inference task priority. |
| [OH_NN_ReturnCode](#oh_nn_returncode) | OH_NN_ReturnCode | Defines error codes. |
| [OH_NN_FuseType](#oh_nn_fusetype) | OH_NN_FuseType | Defines activation function types in the fusion operator. |
| [OH_NN_Format](#oh_nn_format) | OH_NN_Format | Defines the layout type of tensor data. |
| [OH_NN_DeviceType](#oh_nn_devicetype) | OH_NN_DeviceType | Defines device types. |
| [OH_NN_DataType](#oh_nn_datatype) | OH_NN_DataType | Defines tensor data types. |
| [OH_NN_OperationType](#oh_nn_operationtype) | OH_NN_OperationType | Defines operator types. |
| [OH_NN_TensorType](#oh_nn_tensortype) | OH_NN_TensorType | Enumerates the tensor data types.<br> Tensors are usually used to set the input, output, and operator parameters of a model. When a tensor is used as the input or output of a model (or operator), set the tensor type to [OH_NN_TENSOR](capi-neural-network-runtime-type-h.md#oh_nn_tensortype).<br>When the tensor is used as an operator parameter, select an enumerated value other than [OH_NN_TENSOR](capi-neural-network-runtime-type-h.md#oh_nn_tensortype)<br>as the tensor type. Assume that the <b>pad</b> parameter of the [OH_NN_OPS_CONV2D](capi-neural-network-runtime-type-h.md#oh_nn_operationtype) operator is being set.<br>You need to set the <b>type</b> attribute of the [OH_NN_Tensor](capi-neuralnetworkruntime-oh-nn-tensor.md) instance to [OH_NN_CONV2D_PAD](capi-neural-network-runtime-type-h.md#oh_nn_tensortype). The settings of other operator parameters are similar. The enumerated values are named in the format OH_NN_{<i>Operator name</i>}_{<i>Attribute name</i>}. |

### Function

| Name | typedef keyword | Description |
| -- | -- | -- |
| [typedef void (\*NN_OnRunDone)(void *userData, OH_NN_ReturnCode errCode, void *outputTensor[], int32_t outputCount)](#nn_onrundone) | NN_OnRunDone | Defines the callback function handle for the post-process when the asynchronous execution has been done.<br> Use <b>userData</b> to identify the asynchronous execution you want to get. It is the argument <b>userData</b> passed to {@link OH_NNExecutor_RunAsync}.<br>Use <b>errCode</b> of type [OH_NN_ReturnCode](capi-neural-network-runtime-type-h.md#oh_nn_returncode) to get the error code returned by the asynchronous execution.<br>The <b>outputTensor</b> and <b>outputCount</b> are the inference results, which is the same as ones passed to<br>{@link OH_NNExecutor_RunAsync}. |
| [typedef void (\*NN_OnServiceDied)(void *userData)](#nn_onservicedied) | NN_OnServiceDied | Defines the callback function handle for the post-process when the device driver service is dead during asynchronous execution.<br> You should recompile the model if this callback function is called.<br> Use <b>userData</b> to identify the asynchronous execution you want to get. It is the argument <b>userData</b> passed to {@link OH_NNExecutor_RunAsync}. |

### Variable

| Name | Description |
| -- | -- |
| void (*NN_OnRunDone)(void *userData, OH_NN_ReturnCode errCode, void *outputTensor[], int32_t outputCount) | Defines the callback function handle for the post-process when the asynchronous execution has been done.<br> Use <b>userData</b> to identify the asynchronous execution you want to get. It is the argument <b>userData</b> passed to {@link OH_NNExecutor_RunAsync}.<br>Use <b>errCode</b> of type [OH_NN_ReturnCode](capi-neural-network-runtime-type-h.md#oh_nn_returncode) to get the error code returned by the asynchronous execution.<br>The <b>outputTensor</b> and <b>outputCount</b> are the inference results, which is the same as ones passed to<br>{@link OH_NNExecutor_RunAsync}.<br>**Since**: 11 |
| void (*NN_OnServiceDied)(void *userData) | Defines the callback function handle for the post-process when the device driver service is dead during asynchronous execution.<br> You should recompile the model if this callback function is called.<br> Use <b>userData</b> to identify the asynchronous execution you want to get. It is the argument <b>userData</b> passed to {@link OH_NNExecutor_RunAsync}.<br>**Since**: 11 |

## Enum type description

### OH_NN_PerformanceMode

```c
enum OH_NN_PerformanceMode
```

**Description**

Defines the hardware performance mode.

**Since**: 9

| Enum item | Description |
| -- | -- |
| OH_NN_PERFORMANCE_NONE = 0 | No performance mode preference |
| OH_NN_PERFORMANCE_LOW = 1 | Low power consumption mode |
| OH_NN_PERFORMANCE_MEDIUM = 2 | Medium performance mode |
| OH_NN_PERFORMANCE_HIGH = 3 | High performance mode |
| OH_NN_PERFORMANCE_EXTREME = 4 | Ultimate performance mode |

### OH_NN_Priority

```c
enum OH_NN_Priority
```

**Description**

Defines the model inference task priority.

**Since**: 9

| Enum item | Description |
| -- | -- |
| OH_NN_PRIORITY_NONE = 0 | No priority preference |
| OH_NN_PRIORITY_LOW = 1 | Low priority |
| OH_NN_PRIORITY_MEDIUM = 2 | Medium priority |
| OH_NN_PRIORITY_HIGH = 3 | High priority |

### OH_NN_ReturnCode

```c
enum OH_NN_ReturnCode
```

**Description**

Defines error codes.

**Since**: 9

| Enum item | Description |
| -- | -- |
| OH_NN_SUCCESS = 0 | The operation is successful. |
| OH_NN_FAILED = 1 | The operation failed. |
| OH_NN_INVALID_PARAMETER = 2 | Invalid parameter. |
| OH_NN_MEMORY_ERROR = 3 |  |
| OH_NN_OPERATION_FORBIDDEN = 4 | Invalid operation. |
| OH_NN_NULL_PTR = 5 | Null pointer exception |
| OH_NN_INVALID_FILE = 6 | Invalid file. |
| OH_NN_UNAVALIDABLE_DEVICE = 7 |  |
| OH_NN_INVALID_PATH = 8 | Invalid path. |
| OH_NN_TIMEOUT = 9 |  |
| OH_NN_UNSUPPORTED = 10 |  |
| OH_NN_CONNECTION_EXCEPTION = 11 |  |
| OH_NN_SAVE_CACHE_EXCEPTION = 12 |  |
| OH_NN_DYNAMIC_SHAPE = 13 |  |
| OH_NN_UNAVAILABLE_DEVICE = 14 |  |

### OH_NN_FuseType

```c
enum OH_NN_FuseType
```

**Description**

Defines activation function types in the fusion operator.

**Since**: 9

| Enum item | Description |
| -- | -- |
| OH_NN_FUSED_NONE = 0 | The fusion activation function is not specified. |
| OH_NN_FUSED_RELU = 1 | Fusion relu activation function |
| OH_NN_FUSED_RELU6 = 2 | Fusion relu6 activation function |

### OH_NN_Format

```c
enum OH_NN_Format
```

**Description**

Defines the layout type of tensor data.

**Since**: 9

| Enum item | Description |
| -- | -- |
| OH_NN_FORMAT_NONE = 0 | The tensor does not have a specific layout type (such as scalar or vector). |
| OH_NN_FORMAT_NCHW = 1 | The tensor arranges data in NCHW format. |
| OH_NN_FORMAT_NHWC = 2 | The tensor arranges data in NHWC format. |
| OH_NN_FORMAT_ND = 3 |  |

### OH_NN_DeviceType

```c
enum OH_NN_DeviceType
```

**Description**

Defines device types.

**Since**: 9

| Enum item | Description |
| -- | -- |
| OH_NN_OTHERS = 0 | Devices that are not CPU, GPU, or dedicated accelerator |
| OH_NN_CPU = 1 | CPU device |
| OH_NN_GPU = 2 | GPU device |
| OH_NN_ACCELERATOR = 3 | Dedicated hardware accelerator |

### OH_NN_DataType

```c
enum OH_NN_DataType
```

**Description**

Defines tensor data types.

**Since**: 9

| Enum item | Description |
| -- | -- |
| OH_NN_UNKNOWN = 0 | Unknown type |
| OH_NN_BOOL = 1 | bool |
| OH_NN_INT8 = 2 | int8 |
| OH_NN_INT16 = 3 | int16 |
| OH_NN_INT32 = 4 | int32 |
| OH_NN_INT64 = 5 | int64 |
| OH_NN_UINT8 = 6 | uint8 |
| OH_NN_UINT16 = 7 | uint16 |
| OH_NN_UINT32 = 8 | uint32 |
| OH_NN_UINT64 = 9 | uint64 |
| OH_NN_FLOAT16 = 10 | float16 |
| OH_NN_FLOAT32 = 11 | float32 |
| OH_NN_FLOAT64 = 12 | float64 |

### OH_NN_OperationType

```c
enum OH_NN_OperationType
```

**Description**

Defines operator types.

**Since**: 9

| Enum item | Description |
| -- | -- |
| OH_NN_OPS_ADD = 1 |  |
| OH_NN_OPS_AVG_POOL = 2 |  |
| OH_NN_OPS_BATCH_NORM = 3 |  |
| OH_NN_OPS_BATCH_TO_SPACE_ND = 4 |  |
| OH_NN_OPS_BIAS_ADD = 5 |  |
| OH_NN_OPS_CAST = 6 |  |
| OH_NN_OPS_CONCAT = 7 |  |
| OH_NN_OPS_CONV2D = 8 |  |
| OH_NN_OPS_CONV2D_TRANSPOSE = 9 |  |
| OH_NN_OPS_DEPTHWISE_CONV2D_NATIVE = 10 |  |
| OH_NN_OPS_DIV = 11 |  |
| OH_NN_OPS_ELTWISE = 12 |  |
| OH_NN_OPS_EXPAND_DIMS = 13 |  |
| OH_NN_OPS_FILL = 14 |  |
| OH_NN_OPS_FULL_CONNECTION = 15 |  |
| OH_NN_OPS_GATHER = 16 |  |
| OH_NN_OPS_HSWISH = 17 |  |
| OH_NN_OPS_LESS_EQUAL = 18 |  |
| OH_NN_OPS_MATMUL = 19 |  |
| OH_NN_OPS_MAXIMUM = 20 |  |
| OH_NN_OPS_MAX_POOL = 21 |  |
| OH_NN_OPS_MUL = 22 |  |
| OH_NN_OPS_ONE_HOT = 23 |  |
| OH_NN_OPS_PAD = 24 |  |
| OH_NN_OPS_POW = 25 |  |
| OH_NN_OPS_SCALE = 26 |  |
| OH_NN_OPS_SHAPE = 27 |  |
| OH_NN_OPS_SIGMOID = 28 |  |
| OH_NN_OPS_SLICE = 29 |  |
| OH_NN_OPS_SOFTMAX = 30 |  |
| OH_NN_OPS_SPACE_TO_BATCH_ND = 31 |  |
| OH_NN_OPS_SPLIT = 32 |  |
| OH_NN_OPS_SQRT = 33 |  |
| OH_NN_OPS_SQUARED_DIFFERENCE = 34 |  |
| OH_NN_OPS_SQUEEZE = 35 |  |
| OH_NN_OPS_STACK = 36 |  |
| OH_NN_OPS_STRIDED_SLICE = 37 |  |
| OH_NN_OPS_SUB = 38 |  |
| OH_NN_OPS_TANH = 39 |  |
| OH_NN_OPS_TILE = 40 |  |
| OH_NN_OPS_TRANSPOSE = 41 |  |
| OH_NN_OPS_REDUCE_MEAN = 42 |  |
| OH_NN_OPS_RESIZE_BILINEAR = 43 |  |
| OH_NN_OPS_RSQRT = 44 |  |
| OH_NN_OPS_RESHAPE = 45 |  |
| OH_NN_OPS_PRELU = 46 |  |
| OH_NN_OPS_RELU = 47 |  |
| OH_NN_OPS_RELU6 = 48 |  |
| OH_NN_OPS_LAYER_NORM = 49 |  |
| OH_NN_OPS_REDUCE_PROD = 50 |  |
| OH_NN_OPS_REDUCE_ALL = 51 |  |
| OH_NN_OPS_QUANT_DTYPE_CAST = 52 |  |
| OH_NN_OPS_TOP_K = 53 |  |
| OH_NN_OPS_ARG_MAX = 54 |  |
| OH_NN_OPS_UNSQUEEZE = 55 |  |
| OH_NN_OPS_GELU = 56 |  |
| OH_NN_OPS_UNSTACK = 57 |  |
| OH_NN_OPS_ABS = 58 |  |
| OH_NN_OPS_ERF = 59 |  |
| OH_NN_OPS_EXP = 60 |  |
| OH_NN_OPS_LESS = 61 |  |
| OH_NN_OPS_SELECT = 62 |  |
| OH_NN_OPS_SQUARE = 63 |  |
| OH_NN_OPS_FLATTEN = 64 |  |
| OH_NN_OPS_DEPTH_TO_SPACE = 65 |  |
| OH_NN_OPS_RANGE = 66 |  |
| OH_NN_OPS_INSTANCE_NORM = 67 |  |
| OH_NN_OPS_CONSTANT_OF_SHAPE = 68 |  |
| OH_NN_OPS_BROADCAST_TO = 69 |  |
| OH_NN_OPS_EQUAL = 70 |  |
| OH_NN_OPS_GREATER = 71 |  |
| OH_NN_OPS_NOT_EQUAL = 72 |  |
| OH_NN_OPS_GREATER_EQUAL = 73 |  |
| OH_NN_OPS_LEAKY_RELU = 74 |  |
| OH_NN_OPS_LSTM = 75 |  |
| OH_NN_OPS_CLIP = 76 |  |
| OH_NN_OPS_ALL = 77 |  |
| OH_NN_OPS_ASSERT = 78 |  |
| OH_NN_OPS_COS = 79 |  |
| OH_NN_OPS_LOG = 80 |  |
| OH_NN_OPS_LOGICAL_AND = 81 |  |
| OH_NN_OPS_LOGICAL_NOT = 82 |  |
| OH_NN_OPS_MOD = 83 |  |
| OH_NN_OPS_NEG = 84 |  |
| OH_NN_OPS_RECIPROCAL = 85 |  |
| OH_NN_OPS_SIN = 86 |  |
| OH_NN_OPS_WHERE = 87 |  |
| OH_NN_OPS_SPARSE_TO_DENSE = 88 |  |
| OH_NN_OPS_LOGICAL_OR = 89 |  |
| OH_NN_OPS_CEIL = 90 |  |
| OH_NN_OPS_CROP = 91 |  |
| OH_NN_OPS_DETECTION_POST_PROCESS = 92 |  |
| OH_NN_OPS_FLOOR = 93 |  |
| OH_NN_OPS_L2_NORMALIZE = 94 |  |
| OH_NN_OPS_LOG_SOFTMAX = 95 |  |
| OH_NN_OPS_LRN = 96 |  |
| OH_NN_OPS_MINIMUM = 97 |  |
| OH_NN_OPS_RANK = 98 |  |
| OH_NN_OPS_REDUCE_MAX = 99 |  |
| OH_NN_OPS_REDUCE_MIN = 100 |  |
| OH_NN_OPS_REDUCE_SUM = 101 |  |
| OH_NN_OPS_ROUND = 102 |  |
| OH_NN_OPS_SCATTER_ND = 103 |  |
| OH_NN_OPS_SPACE_TO_DEPTH = 104 |  |
| OH_NN_OPS_SWISH = 105 |  |
| OH_NN_OPS_REDUCE_L2 = 106 |  |
| OH_NN_OPS_HARD_SIGMOID = 107 |  |
| OH_NN_OPS_GATHER_ND = 108 |  |

### OH_NN_TensorType

```c
enum OH_NN_TensorType
```

**Description**

Enumerates the tensor data types.<br> Tensors are usually used to set the input, output, and operator parameters of a model. When a tensor is used as the input or output of a model (or operator), set the tensor type to [OH_NN_TENSOR](capi-neural-network-runtime-type-h.md#oh_nn_tensortype).<br>When the tensor is used as an operator parameter, select an enumerated value other than [OH_NN_TENSOR](capi-neural-network-runtime-type-h.md#oh_nn_tensortype)<br>as the tensor type. Assume that the <b>pad</b> parameter of the [OH_NN_OPS_CONV2D](capi-neural-network-runtime-type-h.md#oh_nn_operationtype) operator is being set.<br>You need to set the <b>type</b> attribute of the [OH_NN_Tensor](capi-neuralnetworkruntime-oh-nn-tensor.md) instance to [OH_NN_CONV2D_PAD](capi-neural-network-runtime-type-h.md#oh_nn_tensortype). The settings of other operator parameters are similar. The enumerated values are named in the format OH_NN_{<i>Operator name</i>}_{<i>Attribute name</i>}.

**Since**: 9

| Enum item | Description |
| -- | -- |
| OH_NN_TENSOR = 0 | This enumerated value is used when the tensor is used as the input or output of a model (or operator). |
| OH_NN_ADD_ACTIVATIONTYPE = 1 | This enumerated value is used when the tensor is used as the <b>activationType</b> parameter |
| OH_NN_AVG_POOL_KERNEL_SIZE = 2 | This enumerated value is used when the tensor is used as the <b>kernelSize</b> parameter |
| OH_NN_AVG_POOL_STRIDE = 3 | This enumerated value is used when the tensor is used as the <b>stride</b> parameter |
| OH_NN_AVG_POOL_PAD_MODE = 4 | This enumerated value is used when the tensor is used as the <b>padMode</b> parameter |
| OH_NN_AVG_POOL_PAD = 5 | This enumerated value is used when the tensor is used as the <b>pad</b> parameter of the AvgPool operator. |
| OH_NN_AVG_POOL_ACTIVATION_TYPE = 6 | This enumerated value is used when the tensor is used as the <b>activationType</b> parameter |
| OH_NN_BATCH_NORM_EPSILON = 7 | This enumerated value is used when the tensor is used as the <b>eosilon</b> parameter |
| OH_NN_BATCH_TO_SPACE_ND_BLOCKSIZE = 8 | This enumerated value is used when the tensor is used as the <b>blockSize</b> parameter |
| OH_NN_BATCH_TO_SPACE_ND_CROPS = 9 | This enumerated value is used when the tensor is used as the <b>crops</b> parameter |
| OH_NN_CONCAT_AXIS = 10 | This enumerated value is used when the tensor is used as the <b>axis</b> parameter of the Concat operator. |
| OH_NN_CONV2D_STRIDES = 11 | This enumerated value is used when the tensor is used as the <b>strides</b> parameter |
| OH_NN_CONV2D_PAD = 12 | This enumerated value is used when the tensor is used as the <b>pad</b> parameter of the Conv2D operator. |
| OH_NN_CONV2D_DILATION = 13 | This enumerated value is used when the tensor is used as the <b>dilation</b> parameter |
| OH_NN_CONV2D_PAD_MODE = 14 | This enumerated value is used when the tensor is used as the <b>padMode</b> parameter |
| OH_NN_CONV2D_ACTIVATION_TYPE = 15 | This enumerated value is used when the tensor is used as the <b>activationType</b> parameter |
| OH_NN_CONV2D_GROUP = 16 | This enumerated value is used when the tensor is used as the <b>group</b> parameter of the Conv2D operator. |
| OH_NN_CONV2D_TRANSPOSE_STRIDES = 17 | This enumerated value is used when the tensor is used as the <b>strides</b> parameter |
| OH_NN_CONV2D_TRANSPOSE_PAD = 18 | This enumerated value is used when the tensor is used as the <b>pad</b> parameter |
| OH_NN_CONV2D_TRANSPOSE_DILATION = 19 | This enumerated value is used when the tensor is used as the <b>dilation</b> parameter |
| OH_NN_CONV2D_TRANSPOSE_OUTPUT_PADDINGS = 20 | This enumerated value is used when the tensor is used as the <b>outputPaddings</b> parameter |
| OH_NN_CONV2D_TRANSPOSE_PAD_MODE = 21 | This enumerated value is used when the tensor is used as the <b>padMode</b> parameter |
| OH_NN_CONV2D_TRANSPOSE_ACTIVATION_TYPE = 22 | This enumerated value is used when the tensor is used as the <b>activationType</b> parameter |
| OH_NN_CONV2D_TRANSPOSE_GROUP = 23 | This enumerated value is used when the tensor is used as the <b>group</b> parameter |
| OH_NN_DEPTHWISE_CONV2D_NATIVE_STRIDES = 24 | This enumerated value is used when the tensor is used as the <b>strides</b> parameter |
| OH_NN_DEPTHWISE_CONV2D_NATIVE_PAD = 25 | This enumerated value is used when the tensor is used as the <b>pad</b> parameter |
| OH_NN_DEPTHWISE_CONV2D_NATIVE_DILATION = 26 | This enumerated value is used when the tensor is used as the <b>dilation</b> parameter |
| OH_NN_DEPTHWISE_CONV2D_NATIVE_PAD_MODE = 27 | This enumerated value is used when the tensor is used as the <b>padMode</b> parameter |
| OH_NN_DEPTHWISE_CONV2D_NATIVE_ACTIVATION_TYPE = 28 | This enumerated value is used when the tensor is used as the <b>activationType</b> parameter |
| OH_NN_DIV_ACTIVATIONTYPE = 29 | This enumerated value is used when the tensor is used as the <b>activationType</b> parameter |
| OH_NN_ELTWISE_MODE = 30 | This enumerated value is used when the tensor is used as the <b>mode</b> parameter of the Eltwise operator. |
| OH_NN_FULL_CONNECTION_AXIS = 31 | This enumerated value is used when the tensor is used as the <b>axis</b> parameter |
| OH_NN_FULL_CONNECTION_ACTIVATIONTYPE = 32 | This enumerated value is used when the tensor is used as the <b>activationType</b> parameter |
| OH_NN_MATMUL_TRANSPOSE_A = 33 | This enumerated value is used when the tensor is used as the <b>transposeA</b> parameter |
| OH_NN_MATMUL_TRANSPOSE_B = 34 | This enumerated value is used when the tensor is used as the <b>transposeB</b> parameter |
| OH_NN_MATMUL_ACTIVATION_TYPE = 35 | This enumerated value is used when the tensor is used as the <b>activationType</b> parameter |
| OH_NN_MAX_POOL_KERNEL_SIZE = 36 | This enumerated value is used when the tensor is used as the <b>kernelSize</b> parameter |
| OH_NN_MAX_POOL_STRIDE = 37 | This enumerated value is used when the tensor is used as the <b>stride</b> parameter |
| OH_NN_MAX_POOL_PAD_MODE = 38 | This enumerated value is used when the tensor is used as the <b>padMode</b> parameter |
| OH_NN_MAX_POOL_PAD = 39 | This enumerated value is used when the tensor is used as the <b>pad</b> parameter of the MaxPool operator. |
| OH_NN_MAX_POOL_ACTIVATION_TYPE = 40 | This enumerated value is used when the tensor is used as the <b>activationType</b> parameter |
| OH_NN_MUL_ACTIVATION_TYPE = 41 | This enumerated value is used when the tensor is used as the <b>activationType</b> parameter |
| OH_NN_ONE_HOT_AXIS = 42 | This enumerated value is used when the tensor is used as the <b>axis</b> parameter of the OneHot operator. |
| OH_NN_PAD_CONSTANT_VALUE = 43 | This enumerated value is used when the tensor is used as the <b>constantValue</b> parameter |
| OH_NN_SCALE_ACTIVATIONTYPE = 44 | This enumerated value is used when the tensor is used as the <b>activationType</b> parameter |
| OH_NN_SCALE_AXIS = 45 | This enumerated value is used when the tensor is used as the <b>axis</b> parameter of the Scale operator. |
| OH_NN_SOFTMAX_AXIS = 46 | This enumerated value is used when the tensor is used as the <b>axis</b> parameter of the Softmax operator. |
| OH_NN_SPACE_TO_BATCH_ND_BLOCK_SHAPE = 47 | This enumerated value is used when the tensor is used as the <b>BlockShape</b> parameter |
| OH_NN_SPACE_TO_BATCH_ND_PADDINGS = 48 | This enumerated value is used when the tensor is used as the <b>Paddings</b> parameter |
| OH_NN_SPLIT_AXIS = 49 | This enumerated value is used when the tensor is used as the <b>Axis</b> parameter of the Split operator. |
| OH_NN_SPLIT_OUTPUT_NUM = 50 | This enumerated value is used when the tensor is used as the <b>OutputNum</b> parameter |
| OH_NN_SPLIT_SIZE_SPLITS = 51 | This enumerated value is used when the tensor is used as the <b>SizeSplits</b> parameter |
| OH_NN_SQUEEZE_AXIS = 52 | This enumerated value is used when the tensor is used as the <b>Axis</b> parameter of the Squeeze operator. |
| OH_NN_STACK_AXIS = 53 | This enumerated value is used when the tensor is used as the <b>Axis</b> parameter of the Stack operator. |
| OH_NN_STRIDED_SLICE_BEGIN_MASK = 54 | This enumerated value is used when the tensor is used as the <b>BeginMask</b> parameter |
| OH_NN_STRIDED_SLICE_END_MASK = 55 | This enumerated value is used when the tensor is used as the <b>EndMask</b> parameter |
| OH_NN_STRIDED_SLICE_ELLIPSIS_MASK = 56 | This enumerated value is used when the tensor is used as the <b>EllipsisMask</b> parameter |
| OH_NN_STRIDED_SLICE_NEW_AXIS_MASK = 57 | This enumerated value is used when the tensor is used as the <b>NewAxisMask</b> parameter |
| OH_NN_STRIDED_SLICE_SHRINK_AXIS_MASK = 58 | This enumerated value is used when the tensor is used as the <b>ShrinkAxisMask</b> parameter |
| OH_NN_SUB_ACTIVATIONTYPE = 59 | This enumerated value is used when the tensor is used as the <b>ActivationType</b> parameter |
| OH_NN_REDUCE_MEAN_KEEP_DIMS = 60 | This enumerated value is used when the tensor is used as the <b>keepDims</b> parameter |
| OH_NN_RESIZE_BILINEAR_NEW_HEIGHT = 61 | This enumerated value is used when the tensor is used as the <b>newHeight</b> parameter |
| OH_NN_RESIZE_BILINEAR_NEW_WIDTH = 62 | This enumerated value is used when the tensor is used as the <b>newWidth</b> parameter |
| OH_NN_RESIZE_BILINEAR_PRESERVE_ASPECT_RATIO = 63 | This enumerated value is used when the tensor is used as the <b>preserveAspectRatio</b> parameter |
| OH_NN_RESIZE_BILINEAR_COORDINATE_TRANSFORM_MODE = 64 | This enumerated value is used when the tensor is used as the <b>coordinateTransformMode</b> parameter |
| OH_NN_RESIZE_BILINEAR_EXCLUDE_OUTSIDE = 65 | This enumerated value is used when the tensor is used as the <b>excludeOutside</b> parameter |
| OH_NN_LAYER_NORM_BEGIN_NORM_AXIS = 66 | This enumerated value is used when the tensor is used as the <b>beginNormAxis</b> parameter |
| OH_NN_LAYER_NORM_EPSILON = 67 | This enumerated value is used when the tensor is used as the <b>epsilon</b> parameter |
| OH_NN_LAYER_NORM_BEGIN_PARAM_AXIS = 68 | This enumerated value is used when the tensor is used as the <b>beginParamsAxis</b> parameter |
| OH_NN_LAYER_NORM_ELEMENTWISE_AFFINE = 69 | This enumerated value is used when the tensor is used as the <b>elementwiseAffine</b> parameter |
| OH_NN_REDUCE_PROD_KEEP_DIMS = 70 | This enumerated value is used when the tensor is used as the <b>keepDims</b> parameter |
| OH_NN_REDUCE_ALL_KEEP_DIMS = 71 | This enumerated value is used when the tensor is used as the <b>keepDims</b> parameter |
| OH_NN_QUANT_DTYPE_CAST_SRC_T = 72 | This enumerated value is used when the tensor is used as the <b>src_t</b> parameter |
| OH_NN_QUANT_DTYPE_CAST_DST_T = 73 | This enumerated value is used when the tensor is used as the <b>dst_t</b> parameter |
| OH_NN_TOP_K_SORTED = 74 | This enumerated value is used when the tensor is used as the <b>Sorted</b> parameter |
| OH_NN_ARG_MAX_AXIS = 75 | This enumerated value is used when the tensor is used as the <b>axis</b> parameter |
| OH_NN_ARG_MAX_KEEPDIMS = 76 | This enumerated value is used when the tensor is used as the <b>keepDims</b> parameter |
| OH_NN_UNSQUEEZE_AXIS = 77 | This enumerated value is used when the tensor is used as the <b>axis</b> parameter |
| OH_NN_UNSTACK_AXIS = 78 | This enumerated value is used when the tensor is used as the <b>axis</b> parameter of the Unstack operator. @since 12 |
| OH_NN_FLATTEN_AXIS = 79 | This enumerated value is used when the tensor is used as the <b>axis</b> parameter of the Flatten operator. @since 12 |
| OH_NN_DEPTH_TO_SPACE_BLOCK_SIZE = 80 | This enumerated value is used when the tensor is used as the <b>blockSize</b> parameter of the DepthToSpace operator. @since 12 |
| OH_NN_DEPTH_TO_SPACE_MODE = 81 | This enumerated value is used when the tensor is used as the <b>mode</b> parameter of the DepthToSpace operator. @since 12 |
| OH_NN_RANGE_START = 82 | This enumerated value is used when the tensor is used as the <b>start</b> parameter of the Range operator. @since 12 |
| OH_NN_RANGE_LIMIT = 83 | This enumerated value is used when the tensor is used as the <b>limit</b> parameter of the Range operator. @since 12 |
| OH_NN_RANGE_DELTA = 84 | This enumerated value is used when the tensor is used as the <b>delta</b> parameter of the Range operator. @since 12 |
| OH_NN_CONSTANT_OF_SHAPE_DATA_TYPE = 85 | This enumerated value is used when the tensor is used as the <b>dataType</b> parameter of the ConstantOfShape operator. @since 12 |
| OH_NN_CONSTANT_OF_SHAPE_VALUE = 86 | This enumerated value is used when the tensor is used as the <b>value</b> parameter of the ConstantOfShape operator. @since 12 |
| OH_NN_BROADCAST_TO_SHAPE = 87 | This enumerated value is used when the tensor is used as the <b>shape</b> parameter of the BroadcastTo operator. @since 12 |
| OH_NN_INSTANCE_NORM_EPSILON = 88 | This enumerated value is used when the tensor is used as the <b>epsilon</b> parameter of the InstanceNorm operator. @since 12 |
| OH_NN_EXP_BASE = 89 | This enumerated value is used when the tensor is used as the <b>base</b> parameter of the Exp operator. @since 12 |
| OH_NN_EXP_SCALE = 90 | This enumerated value is used when the tensor is used as the <b>scale</b> parameter of the Exp operator. @since 12 |
| OH_NN_EXP_SHIFT = 91 | This enumerated value is used when the tensor is used as the <b>shift</b> parameter of the Exp operator. @since 12 |
| OH_NN_LEAKY_RELU_NEGATIVE_SLOPE = 92 | This enumerated value is used when the tensor is used as the <b>negativeSlope</b> parameter of the LeakyRelu operator. @since 12 |
| OH_NN_LSTM_BIDIRECTIONAL = 93 | This enumerated value is used when the tensor is used as the <b>bidirectional</b> parameter of the LSTM operator. @since 12 |
| OH_NN_LSTM_HAS_BIAS = 94 | This enumerated value is used when the tensor is used as the <b>hasBias</b> parameter of the LSTM operator. @since 12 |
| OH_NN_LSTM_INPUT_SIZE = 95 | This enumerated value is used when the tensor is used as the <b>inputSize</b> parameter of the LSTM operator. @since 12 |
| OH_NN_LSTM_HIDDEN_SIZE = 96 | This enumerated value is used when the tensor is used as the <b>hiddenSize</b> parameter of the LSTM operator. @since 12 |
| OH_NN_LSTM_NUM_LAYERS = 97 | This enumerated value is used when the tensor is used as the <b>numLayers</b> parameter of the LSTM operator. @since 12 |
| OH_NN_LSTM_NUM_DIRECTIONS = 98 | This enumerated value is used when the tensor is used as the <b>numDirections</b> parameter of the LSTM operator. @since 12 |
| OH_NN_LSTM_DROPOUT = 99 | This enumerated value is used when the tensor is used as the <b>dropout</b> parameter of the LSTM operator. @since 12 |
| OH_NN_LSTM_ZONEOUT_CELL = 100 | This enumerated value is used when the tensor is used as the <b>zoneoutCell</b> parameter of the LSTM operator. @since 12 |
| OH_NN_LSTM_ZONEOUT_HIDDEN = 101 | This enumerated value is used when the tensor is used as the <b>zoneoutHidden</b> parameter of the LSTM operator. @since 12 |
| OH_NN_LSTM_PROJ_SIZE = 102 | This enumerated value is used when the tensor is used as the <b>projSize</b> parameter of the LSTM operator. @since 12 |
| OH_NN_CLIP_MAX = 103 | This enumerated value is used when the tensor is used as the <b>max</b> parameter of the Clip operator. @since 12 |
| OH_NN_CLIP_MIN = 104 | This enumerated value is used when the tensor is used as the <b>min</b> parameter of the Clip operator. @since 12 |
| OH_NN_ALL_KEEP_DIMS = 105 | This enumerated value is used when the tensor is used as the <b>keepDims</b> parameter of the All operator. @since 12 |
| OH_NN_ASSERT_SUMMARIZE = 106 | This enumerated value is used when the tensor is used as the <b>summarize</b> parameter of the Assert operator. @since 12 |
| OH_NN_POW_SCALE = 107 | This enumerated value is used when the tensor is used as the <b>scale</b> parameter of the pow operator. @since 12 |
| OH_NN_POW_SHIFT = 108 | This enumerated value is used when the tensor is used as the <b>shift</b> parameter of the pow operator. @since 12 |
| OH_NN_AVG_POOL_ROUND_MODE = 109 | This enumerated value is used when the tensor is used as the <b>roundMode</b> parameter of the AvgPool operator. @since 12 |
| OH_NN_AVG_POOL_GLOBAL = 110 | This enumerated value is used when the tensor is used as the <b>global</b> parameter of the AvgPool operator. @since 12 |
| OH_NN_FULL_CONNECTION_HAS_BIAS = 111 | This enumerated value is used when the tensor is used as the <b>hasBias</b> parameter of the FullConnection operator. @since 12 |
| OH_NN_FULL_CONNECTION_USE_AXIS = 112 | This enumerated value is used when the tensor is used as the <b>useAxis</b> parameter of the FullConnection operator. @since 12 |
| OH_NN_GELU_APPROXIMATE = 113 | This enumerated value is used when the tensor is used as the <b>approximate</b> parameter of the GeLU operator. @since 12 |
| OH_NN_MAX_POOL_ROUND_MODE = 114 | This enumerated value is used when the tensor is used as the <b>roundMode</b> parameter of the MaxPool operator. @since 12 |
| OH_NN_MAX_POOL_GLOBAL = 115 | This enumerated value is used when the tensor is used as the <b>global</b> parameter of the MaxPool operator. @since 12 |
| OH_NN_PAD_PADDING_MODE = 116 | This enumerated value is used when the tensor is used as the <b>paddingMode</b> parameter of the Pad operator. @since 12 |
| OH_NN_REDUCE_MEAN_REDUCE_TO_END = 117 | This enumerated value is used when the tensor is used as the <b>reduceToEnd</b> parameter of the ReduceMean operator. @since 12 |
| OH_NN_REDUCE_MEAN_COEFF = 118 | This enumerated value is used when the tensor is used as the <b>coeff</b> parameter of the ReduceMean operator. @since 12 |
| OH_NN_REDUCE_PROD_REDUCE_TO_END = 119 | This enumerated value is used when the tensor is used as the <b>reduceToEnd</b> parameter of the ReduceProd operator. @since 12 |
| OH_NN_REDUCE_PROD_COEFF = 120 | This enumerated value is used when the tensor is used as the <b>coeff</b> parameter of the ReduceProd operator. @since 12 |
| OH_NN_REDUCE_ALL_REDUCE_TO_END = 121 | This enumerated value is used when the tensor is used as the <b>reduceToEnd</b> parameter of the ReduceAll operator. @since 12 |
| OH_NN_REDUCE_ALL_COEFF = 122 | This enumerated value is used when the tensor is used as the <b>coeff</b> parameter of the ReduceAll operator. @since 12 |
| OH_NN_TOP_K_AXIS = 123 | This enumerated value is used when the tensor is used as the <b>axis</b> parameter of the Topk operator. @since 12 |
| OH_NN_ARG_MAX_TOP_K = 124 | This enumerated value is used when the tensor is used as the <b>topK</b> parameter of the ArgMax operator. @since 12 |
| OH_NN_ARG_MAX_OUT_MAX_VALUE = 125 | This enumerated value is used when the tensor is used as the <b>outMaxValue</b> parameter of the ArgMax operator. @since 12 |
| OH_NN_QUANT_DTYPE_CAST_AXIS = 126 | This enumerated value is used when the tensor is used as the <b>axis</b> parameter of the QuantDTypeCast operator. @since 12 |
| OH_NN_SLICE_AXES = 127 | This enumerated value is used when the tensor is used as the <b>axes</b> parameter of the Slice operator. @since 12 |
| OH_NN_TILE_DIMS = 128 | This enumerated value is used when the tensor is used as the <b>dims</b> parameter of the Tile operator. @since 12 |
| OH_NN_CROP_AXIS = 129 | This enumerated value is used when the tensor is used as the <b>axis</b> parameter of the crop operator. @since 12 |
| OH_NN_CROP_OFFSET = 130 | This enumerated value is used when the tensor is used as the <b>offset</b> parameter of the crop operator. @since 12 |
| OH_NN_DETECTION_POST_PROCESS_INPUT_SIZE = 131 | This enumerated value is used when the tensor is used as the <b>inputSize</b> parameter of the detectionPostProcess operator. @since 12 |
| OH_NN_DETECTION_POST_PROCESS_SCALE = 132 | This enumerated value is used when the tensor is used as the <b>scale</b> parameter of the detectionPostProcess operator. @since 12 |
| OH_NN_DETECTION_POST_PROCESS_NMS_IOU_THRESHOLD = 133 | This enumerated value is used when the tensor is used as the <b>nmsIoUThreshold</b> parameter of the detectionPostProcess operator. @since 12 |
| OH_NN_DETECTION_POST_PROCESS_NMS_SCORE_THRESHOLD = 134 | This enumerated value is used when the tensor is used as the <b>nmsScoreThreshold</b> parameter of the detectionPostProcess operator. @since 12 |
| OH_NN_DETECTION_POST_PROCESS_MAX_DETECTIONS = 135 | This enumerated value is used when the tensor is used as the <b>maxDetections</b> parameter of the detectionPostProcess operator. @since 12 |
| OH_NN_DETECTION_POST_PROCESS_DETECTIONS_PER_CLASS = 136 | This enumerated value is used when the tensor is used as the <b>detectionsPerClass</b> parameter of the detectionPostProcess operator. @since 12 |
| OH_NN_DETECTION_POST_PROCESS_MAX_CLASSES_PER_DETECTION = 137 | This enumerated value is used when the tensor is used as the <b>maxClassesPerDetection</b> parameter of the detectionPostProcess operator. @since 12 |
| OH_NN_DETECTION_POST_PROCESS_NUM_CLASSES = 138 | This enumerated value is used when the tensor is used as the <b>numClasses</b> parameter of the detectionPostProcess operator. @since 12 |
| OH_NN_DETECTION_POST_PROCESS_USE_REGULAR_NMS = 139 | This enumerated value is used when the tensor is used as the <b>useRegularNms</b> parameter of the detectionPostProcess operator. @since 12 |
| OH_NN_DETECTION_POST_PROCESS_OUT_QUANTIZED = 140 | This enumerated value is used when the tensor is used as the <b>outQuantized</b> parameter of the detectionPostProcess operator. @since 12 |
| OH_NN_L2_NORMALIZE_AXIS = 141 | This enumerated value is used when the tensor is used as the <b>axis</b> parameter of the L2Normalize operator. @since 12 |
| OH_NN_L2_NORMALIZE_EPSILON = 142 | This enumerated value is used when the tensor is used as the <b>epsilon</b> parameter of the L2Normalize operator. @since 12 |
| OH_NN_L2_NORMALIZE_ACTIVATION_TYPE = 143 | This enumerated value is used when the tensor is used as the <b>activationType</b> parameter of the L2Normalize operator. @since 12 |
| OH_NN_LOG_SOFTMAX_AXIS = 144 | This enumerated value is used when the tensor is used as the <b>axis</b> parameter of the softmax operator. @since 12 |
| OH_NN_LRN_DEPTH_RADIUS = 145 | This enumerated value is used when the tensor is used as the <b>depthRedius</b> parameter of the LRN operator. @since 12 |
| OH_NN_LRN_BIAS = 146 | This enumerated value is used when the tensor is used as the <b>bias</b> parameter of the LRN operator. @since 12 |
| OH_NN_LRN_ALPHA = 147 | This enumerated value is used when the tensor is used as the <b>alpha</b> parameter of the LRN operator. @since 12 |
| OH_NN_LRN_BETA = 148 | This enumerated value is used when the tensor is used as the <b>beta</b> parameter of the LRN operator. @since 12 |
| OH_NN_LRN_NORM_REGION = 149 | This enumerated value is used when the tensor is used as the <b>normRegion</b> parameter of the LRN operator. @since 12 |
| OH_NN_SPACE_TO_DEPTH_BLOCK_SIZE = 150 | This enumerated value is used when the tensor is used as the <b>blockSize</b> parameter of the spaceToDepth operator. @since 12 |
| OH_NN_REDUCE_MAX_KEEP_DIMS = 151 | This enumerated value is used when the tensor is used as the <b>keepDims</b> parameter of the ReduceMax operator. @since 12 |
| OH_NN_REDUCE_MAX_REDUCE_TO_END = 152 | This enumerated value is used when the tensor is used as the <b>reduceToEnd</b> parameter of the ReduceMax operator. @since 12 |
| OH_NN_REDUCE_MAX_COEFF = 153 | This enumerated value is used when the tensor is used as the <b>coeff</b> parameter of the ReduceMax operator. @since 12 |
| OH_NN_REDUCE_MIN_KEEP_DIMS = 154 | This enumerated value is used when the tensor is used as the <b>keepDims</b> parameter of the ReduceMin operator. @since 12 |
| OH_NN_REDUCE_MIN_REDUCE_TO_END = 155 | This enumerated value is used when the tensor is used as the <b>reduceToEnd</b> parameter of the ReduceMin operator. @since 12 |
| OH_NN_REDUCE_MIN_COEFF = 156 | This enumerated value is used when the tensor is used as the <b>coeff</b> parameter of the ReduceMin operator. @since 12 |
| OH_NN_REDUCE_SUM_KEEP_DIMS = 157 | This enumerated value is used when the tensor is used as the <b>keepDims</b> parameter of the ReduceSum operator. @since 12 |
| OH_NN_REDUCE_SUM_REDUCE_TO_END = 158 | This enumerated value is used when the tensor is used as the <b>reduceToEnd</b> parameter of the ReduceSum operator. @since 12 |
| OH_NN_REDUCE_SUM_COEFF = 159 | This enumerated value is used when the tensor is used as the <b>coeff</b> parameter of the ReduceSum operator. @since 12 |
| OH_NN_REDUCE_L2_KEEP_DIMS = 160 | This enumerated value is used when the tensor is used as the <b>keepDims</b> parameter of the ReduceL2 operator. @since 12 |
| OH_NN_REDUCE_L2_REDUCE_TO_END = 161 | This enumerated value is used when the tensor is used as the <b>reduceToEnd</b> parameter of the ReduceL2 operator. @since 12 |
| OH_NN_REDUCE_L2_COEFF = 162 | This enumerated value is used when the tensor is used as the <b>coeff</b> parameter of the ReduceL2 operator. @since 12 |


## Function description

### NN_OnRunDone()

```c
typedef void (*NN_OnRunDone)(void *userData, OH_NN_ReturnCode errCode, void *outputTensor[], int32_t outputCount)
```

**Description**

Defines the callback function handle for the post-process when the asynchronous execution has been done.<br> Use <b>userData</b> to identify the asynchronous execution you want to get. It is the argument <b>userData</b> passed to {@link OH_NNExecutor_RunAsync}.<br>Use <b>errCode</b> of type [OH_NN_ReturnCode](capi-neural-network-runtime-type-h.md#oh_nn_returncode) to get the error code returned by the asynchronous execution.<br>The <b>outputTensor</b> and <b>outputCount</b> are the inference results, which is the same as ones passed to<br>{@link OH_NNExecutor_RunAsync}.

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| void \*userData | Asynchronous execution identifier, which is the argument <b>userData</b> passed to {@link OH_NNExecutor_RunAsync}. |
| [OH_NN_ReturnCode](capi-neural-network-runtime-type-h.md#oh_nn_returncode) errCode | Error code [OH_NN_ReturnCode](capi-neural-network-runtime-type-h.md#oh_nn_returncode) returned by the asynchronous execution. |
| void \*outputTensor[] | An array of output tensors [NN_Tensor](capi-neuralnetworkruntime-nn-tensor.md) of the model, which is the same as the argument <b>outputTensor</b> passed to {@link OH_NNExecutor_RunAsync}. |
| int32_t outputCount | Output tensor count, which is the same as the argument <b>outputCount</b> passed to {@link OH_NNExecutor_RunAsync}. |

### NN_OnServiceDied()

```c
typedef void (*NN_OnServiceDied)(void *userData)
```

**Description**

Defines the callback function handle for the post-process when the device driver service is dead during asynchronous execution.<br> You should recompile the model if this callback function is called.<br> Use <b>userData</b> to identify the asynchronous execution you want to get. It is the argument <b>userData</b> passed to {@link OH_NNExecutor_RunAsync}.

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| void \*userData | Asynchronous execution identifier, which is the argument <b>userData</b> passed to {@link OH_NNExecutor_RunAsync}. |


