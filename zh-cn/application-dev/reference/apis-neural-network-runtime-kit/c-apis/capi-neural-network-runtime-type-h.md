# neural_network_runtime_type.h

## 概述

Neural Network Runtime定义的结构体和枚举值。<br> include "neural_network_runtime/neural_network_runtime_type.h"

**库：** libneural_network_runtime.so

**系统能力：** SystemCapability.AI.NeuralNetworkRuntime

**起始版本：** 9

**相关模块：** [NeuralNetworkRuntime](capi-neuralnetworkruntime.md)

## 汇总

### 结构体

| 名称 | typedef关键字 | 描述 |
| -- | -- | -- |
| [OH_NNModel](capi-neuralnetworkruntime-oh-nnmodel.md) | OH_NNModel | 模型句柄。 |
| [OH_NNCompilation](capi-neuralnetworkruntime-oh-nncompilation.md) | OH_NNCompilation | 编译器句柄。 |
| [OH_NNExecutor](capi-neuralnetworkruntime-oh-nnexecutor.md) | OH_NNExecutor | 执行器句柄。 |
| [NN_QuantParam](capi-neuralnetworkruntime-nn-quantparam.md) | NN_QuantParam | 量化参数的句柄。 |
| [NN_TensorDesc](capi-neuralnetworkruntime-nn-tensordesc.md) | NN_TensorDesc | Tensor描述的句柄。 |
| [NN_Tensor](capi-neuralnetworkruntime-nn-tensor.md) | NN_Tensor | Tensor句柄。 |

### 枚举

| 名称 | typedef关键字 | 描述 |
| -- | -- | -- |
| [OH_NN_PerformanceMode](#oh_nn_performancemode) | OH_NN_PerformanceMode | 硬件的性能模式。 |
| [OH_NN_Priority](#oh_nn_priority) | OH_NN_Priority | 模型推理任务优先级 |
| [OH_NN_ReturnCode](#oh_nn_returncode) | OH_NN_ReturnCode | Neural Network Runtime 定义的错误码类型。 |
| [OH_NN_FuseType](#oh_nn_fusetype) | OH_NN_FuseType | Neural Network Runtime 融合算子中激活函数的类型。 |
| [OH_NN_Format](#oh_nn_format) | OH_NN_Format | ；张量数据的排布类型。 |
| [OH_NN_DeviceType](#oh_nn_devicetype) | OH_NN_DeviceType | Neural Network Runtime 支持的设备类型 |
| [OH_NN_DataType](#oh_nn_datatype) | OH_NN_DataType | Neural Network Runtime 支持的数据类型。 |
| [OH_NN_OperationType](#oh_nn_operationtype) | OH_NN_OperationType | Neural Network Runtime 支持算子的类型。 |
| [OH_NN_TensorType](#oh_nn_tensortype) | OH_NN_TensorType | 张量的类型。 <br> 张量通常用于设置模型的输入、输出和算子参数。作为模型（或算子）的输入和输出时，需要将张量类型设置为[OH_NN_TENSOR](capi-neural-network-runtime-type-h.md#oh_nn_tensortype)；<br>当张量作为算子参数时，需要选择除[OH_NN_TENSOR](capi-neural-network-runtime-type-h.md#oh_nn_tensortype)以外合适的枚举值，作为张量的类型。<br>假设正在设置[OH_NN_OPS_CONV2D](capi-neural-network-runtime-type-h.md#oh_nn_operationtype)算子的pad参数，则需要将{@link OH_NN_Tensor}实例的type属性设置为<br>[OH_NN_PAD](capi-neural-network-runtime-type-h.md#oh_nn_tensortype)。其他算子参数的设置以此类推，枚举值的命名遵守 OH_NN_{算子名词}_{属性名} 的格式。 |

### 函数

| 名称 | typedef关键字 | 描述 |
| -- | -- | -- |
| [typedef void (\*NN_OnRunDone)(void *userData, OH_NN_ReturnCode errCode, void *outputTensor[], int32_t outputCount)](#nn_onrundone) | NN_OnRunDone | 异步推理结束后的回调处理函数句柄。 使用参数userData来查询希望获取的那次异步推理执行。 userData与调用异步推理{@link OH_NNExecutor_RunAsync}接口时传入的参数userData是一致的。 <br> 使用参数errCode（[OH_NN_ReturnCode](capi-neural-network-runtime-type-h.md#oh_nn_returncode)类型）来获取该次异步推理的返回状态。 |
| [typedef void (\*NN_OnServiceDied)(void *userData)](#nn_onservicedied) | NN_OnServiceDied | 异步推理执行期间设备驱动服务异常终止时的回调处理函数句柄。<br> 如果该回调函数被调用，您需要重新编译模型。 <br> 使用参数userData来查询希望获取的那次异步推理执行。 userData与调用异步推理{@link OH_NNExecutor_RunAsync}接口时传入的参数userData是一致的。 |

### 变量

| 名称 | 描述 |
| -- | -- |
| void (*NN_OnRunDone)(void *userData, OH_NN_ReturnCode errCode, void *outputTensor[], int32_t outputCount) | 异步推理结束后的回调处理函数句柄。 使用参数userData来查询希望获取的那次异步推理执行。 userData与调用异步推理{@link OH_NNExecutor_RunAsync}接口时传入的参数userData是一致的。 <br> 使用参数errCode（[OH_NN_ReturnCode](capi-neural-network-runtime-type-h.md#oh_nn_returncode)类型）来获取该次异步推理的返回状态。<br>**起始版本：** 11 |
| void (*NN_OnServiceDied)(void *userData) | 异步推理执行期间设备驱动服务异常终止时的回调处理函数句柄。<br> 如果该回调函数被调用，您需要重新编译模型。 <br> 使用参数userData来查询希望获取的那次异步推理执行。 userData与调用异步推理{@link OH_NNExecutor_RunAsync}接口时传入的参数userData是一致的。<br>**起始版本：** 11 |

## 枚举类型说明

### OH_NN_PerformanceMode

```c
enum OH_NN_PerformanceMode
```

**描述：**

硬件的性能模式。

**系统能力：** SystemCapability.AI.NeuralNetworkRuntime

**起始版本：** 9

| 枚举项 | 描述 |
| -- | -- |
| OH_NN_PERFORMANCE_NONE = 0 | 无性能模式偏好。 |
| OH_NN_PERFORMANCE_LOW = 1 | 低能耗模式。 |
| OH_NN_PERFORMANCE_MEDIUM = 2 | 中性能模式。 |
| OH_NN_PERFORMANCE_HIGH = 3 | 高性能模式。 |
| OH_NN_PERFORMANCE_EXTREME = 4 | 极致性能模式。 |

### OH_NN_Priority

```c
enum OH_NN_Priority
```

**描述：**

模型推理任务优先级

**系统能力：** SystemCapability.AI.NeuralNetworkRuntime

**起始版本：** 9

| 枚举项 | 描述 |
| -- | -- |
| OH_NN_PRIORITY_NONE = 0 | 无优先级偏好。 |
| OH_NN_PRIORITY_LOW = 1 | 低优先级。 |
| OH_NN_PRIORITY_MEDIUM = 2 | 中优先级。 |
| OH_NN_PRIORITY_HIGH = 3 | 高优先级。 |

### OH_NN_ReturnCode

```c
enum OH_NN_ReturnCode
```

**描述：**

Neural Network Runtime 定义的错误码类型。

**系统能力：** SystemCapability.AI.NeuralNetworkRuntime

**起始版本：** 9

| 枚举项 | 描述 |
| -- | -- |
| OH_NN_SUCCESS = 0 | 操作成功。 |
| OH_NN_FAILED = 1 | 操作失败。 |
| OH_NN_INVALID_PARAMETER = 2 | 非法参数。 |
| OH_NN_MEMORY_ERROR = 3 | 内存相关的错误，包括：内存不足、内存数据拷贝失败、内存申请失败等。 |
| OH_NN_OPERATION_FORBIDDEN = 4 | 非法操作。 |
| OH_NN_NULL_PTR = 5 | 空指针异常。 |
| OH_NN_INVALID_FILE = 6 | 无效文件。 |
| OH_NN_UNAVALIDABLE_DEVICE = 7 |  |
| OH_NN_INVALID_PATH = 8 | 非法路径。 |
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

**描述：**

Neural Network Runtime 融合算子中激活函数的类型。

**系统能力：** SystemCapability.AI.NeuralNetworkRuntime

**起始版本：** 9

| 枚举项 | 描述 |
| -- | -- |
| OH_NN_FUSED_NONE = 0 | 未指定融合激活函数。 |
| OH_NN_FUSED_RELU = 1 | 融合relu激活函数。 |
| OH_NN_FUSED_RELU6 = 2 | 融合relu6激活函数。 |

### OH_NN_Format

```c
enum OH_NN_Format
```

**描述：**

；张量数据的排布类型。

**系统能力：** SystemCapability.AI.NeuralNetworkRuntime

**起始版本：** 9

| 枚举项 | 描述 |
| -- | -- |
| OH_NN_FORMAT_NONE = 0 | 当张量没有特定的排布类型时（如标量或矢量），使用本枚举值。 |
| OH_NN_FORMAT_NCHW = 1 | 当张量按照NCHW的格式排布数据时，使用本枚举值。 |
| OH_NN_FORMAT_NHWC = 2 | 当张量按照NHWC的格式排布数据时，使用本枚举值。 |
| OH_NN_FORMAT_ND = 3 |  |

### OH_NN_DeviceType

```c
enum OH_NN_DeviceType
```

**描述：**

Neural Network Runtime 支持的设备类型

**系统能力：** SystemCapability.AI.NeuralNetworkRuntime

**起始版本：** 9

| 枚举项 | 描述 |
| -- | -- |
| OH_NN_OTHERS = 0 | 不属于CPU、GPU、专用加速器的设备。 |
| OH_NN_CPU = 1 | CPU设备。 |
| OH_NN_GPU = 2 | GPU设备。 |
| OH_NN_ACCELERATOR = 3， | 专用硬件加速器。 |

### OH_NN_DataType

```c
enum OH_NN_DataType
```

**描述：**

Neural Network Runtime 支持的数据类型。

**系统能力：** SystemCapability.AI.NeuralNetworkRuntime

**起始版本：** 9

| 枚举项 | 描述 |
| -- | -- |
| OH_NN_UNKNOWN = 0 | 张量数据类型未知。 |
| OH_NN_BOOL = 1 | 张量数据类型为bool。 |
| OH_NN_INT8 = 2 | 张量数据类型为int8。 |
| OH_NN_INT16 = 3 | 张量数据类型为int16。 |
| OH_NN_INT32 = 4 | 张量数据类型为int32。 |
| OH_NN_INT64 = 5 | 张量数据类型为int64。 |
| OH_NN_UINT8 = 6 | 张量数据类型为uint8。 |
| OH_NN_UINT16 = 7 | 张量数据类型为uint16。 |
| OH_NN_UINT32 = 8 | 张量数据类型为uint32。 |
| OH_NN_UINT64 = 9 | 张量数据类型为uint64。 |
| OH_NN_FLOAT16 = 10 | 张量数据类型为float16。 |
| OH_NN_FLOAT32 = 11 | 张量数据类型为float32。 |
| OH_NN_FLOAT64 = 12 | 张量数据类型为float64。 |

### OH_NN_OperationType

```c
enum OH_NN_OperationType
```

**描述：**

Neural Network Runtime 支持算子的类型。

**系统能力：** SystemCapability.AI.NeuralNetworkRuntime

**起始版本：** 9

| 枚举项 | 描述 |
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

**描述：**

张量的类型。 <br> 张量通常用于设置模型的输入、输出和算子参数。作为模型（或算子）的输入和输出时，需要将张量类型设置为[OH_NN_TENSOR](capi-neural-network-runtime-type-h.md#oh_nn_tensortype)；<br>当张量作为算子参数时，需要选择除[OH_NN_TENSOR](capi-neural-network-runtime-type-h.md#oh_nn_tensortype)以外合适的枚举值，作为张量的类型。<br>假设正在设置[OH_NN_OPS_CONV2D](capi-neural-network-runtime-type-h.md#oh_nn_operationtype)算子的pad参数，则需要将{@link OH_NN_Tensor}实例的type属性设置为<br>[OH_NN_PAD](capi-neural-network-runtime-type-h.md#oh_nn_tensortype)。其他算子参数的设置以此类推，枚举值的命名遵守 OH_NN_{算子名词}_{属性名} 的格式。

**系统能力：** SystemCapability.AI.NeuralNetworkRuntime

**起始版本：** 9

| 枚举项 | 描述 |
| -- | -- |
| OH_NN_TENSOR = 0 | 当张量作为模型（或算子）的输入或输出时，使用本枚举值。 |
| OH_NN_ADD_ACTIVATIONTYPE = 1 | 当张量作为Add算子的activationType参数时，使用本枚举值。 |
| OH_NN_AVG_POOL_KERNEL_SIZE = 2 | 当张量作为AvgPool算子的kernelSize参数时，使用本枚举值。 |
| OH_NN_AVG_POOL_STRIDE = 3 | 当张量作为AvgPool算子的stride参数时，使用本枚举值。 |
| OH_NN_AVG_POOL_PAD_MODE = 4 | 当张量作为AvgPool算子的padMode参数时，使用本枚举值。 |
| OH_NN_AVG_POOL_PAD = 5 | 当张量作为AvgPool算子的pad参数时，使用本枚举值。 |
| OH_NN_AVG_POOL_ACTIVATION_TYPE = 6 | 当张量作为AvgPool算子的activationType参数时，使用本枚举值。 |
| OH_NN_BATCH_NORM_EPSILON = 7 | 当张量作为BatchNorm算子的epsilon参数时，使用本枚举值。 |
| OH_NN_BATCH_TO_SPACE_ND_BLOCKSIZE = 8 | 当张量作为BatchToSpaceND算子的blockSize参数时，使用本枚举值。 |
| OH_NN_BATCH_TO_SPACE_ND_CROPS = 9 | 当张量作为BatchToSpaceND算子的crops参数时，使用本枚举值。 |
| OH_NN_CONCAT_AXIS = 10 | 当张量作为Concat算子的axis参数时，使用本枚举值。 |
| OH_NN_CONV2D_STRIDES = 11 | 当张量作为Conv2D算子的strides参数时，使用本枚举值。 |
| OH_NN_CONV2D_PAD = 12 | 当张量作为Conv2D算子的pad参数时，使用本枚举值。 |
| OH_NN_CONV2D_DILATION = 13 | 当张量作为Conv2D算子的dilation参数时，使用本枚举值。 |
| OH_NN_CONV2D_PAD_MODE = 14 | 当张量作为Conv2D算子的padMode参数时，使用本枚举值。 |
| OH_NN_CONV2D_ACTIVATION_TYPE = 15 | 当张量作为Conv2D算子的activationType参数时，使用本枚举值。 |
| OH_NN_CONV2D_GROUP = 16 | 当张量作为Conv2D算子的group参数时，使用本枚举值。 |
| OH_NN_CONV2D_TRANSPOSE_STRIDES = 17 | 当张量作为Conv2DTranspose算子的strides参数时，使用本枚举值。 |
| OH_NN_CONV2D_TRANSPOSE_PAD = 18 | 当张量作为Conv2DTranspose算子的pad参数时，使用本枚举值。 |
| OH_NN_CONV2D_TRANSPOSE_DILATION = 19 | 当张量作为Conv2DTranspose算子的dilation参数时，使用本枚举值。 |
| OH_NN_CONV2D_TRANSPOSE_OUTPUT_PADDINGS = 20 | 当张量作为Conv2DTranspose算子的outputPaddings参数时，使用本枚举值。 |
| OH_NN_CONV2D_TRANSPOSE_PAD_MODE = 21 | 当张量作为Conv2DTranspose算子的padMode参数时，使用本枚举值。 |
| OH_NN_CONV2D_TRANSPOSE_ACTIVATION_TYPE = 22 | 当张量作为Conv2DTranspose算子的activationType参数时，使用本枚举值。 |
| OH_NN_CONV2D_TRANSPOSE_GROUP = 23 | 当张量作为Conv2DTranspose算子的group参数时，使用本枚举值。 |
| OH_NN_DEPTHWISE_CONV2D_NATIVE_STRIDES = 24 | 当张量作为DepthwiseConv2dNative算子的strides参数时，使用本枚举值。 |
| OH_NN_DEPTHWISE_CONV2D_NATIVE_PAD = 25 | 当张量作为DepthwiseConv2dNative算子的pad参数时，使用本枚举值。 |
| OH_NN_DEPTHWISE_CONV2D_NATIVE_DILATION = 26 | 当张量作为DepthwiseConv2dNative算子的dilation参数时，使用本枚举值。 |
| OH_NN_DEPTHWISE_CONV2D_NATIVE_PAD_MODE = 27 | 当张量作为DepthwiseConv2dNative算子的padMode参数时，使用本枚举值。 |
| OH_NN_DEPTHWISE_CONV2D_NATIVE_ACTIVATION_TYPE = 28 | 当张量作为DepthwiseConv2dNative算子的activationType参数时，使用本枚举值。 |
| OH_NN_DIV_ACTIVATIONTYPE = 29 | 当张量作为Div算子的activationType参数时，使用本枚举值。 |
| OH_NN_ELTWISE_MODE = 30 | 当张量作为Eltwise算子的mode参数时，使用本枚举值。 |
| OH_NN_FULL_CONNECTION_AXIS = 31 | 当张量作为FullConnection算子的axis参数时，使用本枚举值。 |
| OH_NN_FULL_CONNECTION_ACTIVATIONTYPE = 32 | 当张量作为FullConnection算子的activationType参数时，使用本枚举值。 |
| OH_NN_MATMUL_TRANSPOSE_A = 33 | 当张量作为Matmul算子的transposeA参数时，使用本枚举值。 |
| OH_NN_MATMUL_TRANSPOSE_B = 34 | 当张量作为Matmul算子的transposeB参数时，使用本枚举值。 |
| OH_NN_MATMUL_ACTIVATION_TYPE = 35 | 当张量作为Matmul算子的activationType参数时，使用本枚举值。 |
| OH_NN_MAX_POOL_KERNEL_SIZE = 36 | 当张量作为MaxPool算子的kernelSize参数时，使用本枚举值。 |
| OH_NN_MAX_POOL_STRIDE = 37 | 当张量作为MaxPool算子的stride参数时，使用本枚举值。 |
| OH_NN_MAX_POOL_PAD_MODE = 38 | 当张量作为MaxPool算子的padMode参数时，使用本枚举值。 |
| OH_NN_MAX_POOL_PAD = 39 | 当张量作为MaxPool算子的pad参数时，使用本枚举值。 |
| OH_NN_MAX_POOL_ACTIVATION_TYPE = 40 | 当张量作为MaxPool算子的activationType参数时，使用本枚举值。 |
| OH_NN_MUL_ACTIVATION_TYPE = 41 | 当张量作为Mul算子的activationType参数时，使用本枚举值。 |
| OH_NN_ONE_HOT_AXIS = 42 | 当张量作为OneHot算子的axis参数时，使用本枚举值。 |
| OH_NN_PAD_CONSTANT_VALUE = 43 | 当张量作为Pad算子的constantValue参数时，使用本枚举值。 |
| OH_NN_SCALE_ACTIVATIONTYPE = 44 | 当张量作为Scale算子的activationType参数时，使用本枚举值。 |
| OH_NN_SCALE_AXIS = 45 | 当张量作为Scale算子的axis参数时，使用本枚举值。 |
| OH_NN_SOFTMAX_AXIS = 46 | 当张量作为Softmax算子的axis参数时，使用本枚举值。 |
| OH_NN_SPACE_TO_BATCH_ND_BLOCK_SHAPE = 47 | 当张量作为SpaceToBatchND算子的BlockShape参数时，使用本枚举值。 |
| OH_NN_SPACE_TO_BATCH_ND_PADDINGS = 48 | 当张量作为SpaceToBatchND算子的Paddings参数时，使用本枚举值。 |
| OH_NN_SPLIT_AXIS = 49 | 当张量作为Split算子的Axis参数时，使用本枚举值。 |
| OH_NN_SPLIT_OUTPUT_NUM = 50 | 当张量作为Split算子的OutputNum参数时，使用本枚举值。 |
| OH_NN_SPLIT_SIZE_SPLITS = 51 | 当张量作为Split算子的SizeSplits参数时，使用本枚举值。 |
| OH_NN_SQUEEZE_AXIS = 52 | 当张量作为Squeeze算子的Axis参数时，使用本枚举值。 |
| OH_NN_STACK_AXIS = 53 | 当张量作为Stack算子的Axis参数时，使用本枚举值。 |
| OH_NN_STRIDED_SLICE_BEGIN_MASK = 54 | 当张量作为StridedSlice算子的BeginMask参数时，使用本枚举值。 |
| OH_NN_STRIDED_SLICE_END_MASK = 55 | 当张量作为StridedSlice算子的EndMask参数时，使用本枚举值。 |
| OH_NN_STRIDED_SLICE_ELLIPSIS_MASK = 56 | 当张量作为StridedSlice算子的EllipsisMask参数时，使用本枚举值。 |
| OH_NN_STRIDED_SLICE_NEW_AXIS_MASK = 57 | 当张量作为StridedSlice算子的NewAxisMask参数时，使用本枚举值。 |
| OH_NN_STRIDED_SLICE_SHRINK_AXIS_MASK = 58 | 当张量作为StridedSlice算子的ShrinkAxisMask参数时，使用本枚举值。 |
| OH_NN_SUB_ACTIVATIONTYPE = 59 | 当张量作为Sub算子的ActivationType参数时，使用本枚举值。 |
| OH_NN_REDUCE_MEAN_KEEP_DIMS = 60 | 当张量作为ReduceMean算子的keepDims参数时，使用本枚举值。 |
| OH_NN_RESIZE_BILINEAR_NEW_HEIGHT = 61 | 当张量作为ResizeBilinear算子的newHeight参数时，使用本枚举值。 |
| OH_NN_RESIZE_BILINEAR_NEW_WIDTH = 62 | 当张量作为ResizeBilinear算子的newWidth参数时，使用本枚举值。 |
| OH_NN_RESIZE_BILINEAR_PRESERVE_ASPECT_RATIO = 63 | 当张量作为ResizeBilinear算子的preserveAspectRatio参数时，使用本枚举值。 |
| OH_NN_RESIZE_BILINEAR_COORDINATE_TRANSFORM_MODE = 64 | 当张量作为ResizeBilinear算子的coordinateTransformMode参数时，使用本枚举值。 |
| OH_NN_RESIZE_BILINEAR_EXCLUDE_OUTSIDE = 65 | 当张量作为ResizeBilinear算子的excludeOutside参数时，使用本枚举值。 |
| OH_NN_LAYER_NORM_BEGIN_NORM_AXIS = 66 | 当张量作为LayerNorm算子的beginNormAxis参数时，使用本枚举值。 |
| OH_NN_LAYER_NORM_EPSILON = 67 | 当张量作为LayerNorm算子的epsilon参数时，使用本枚举值。 |
| OH_NN_LAYER_NORM_BEGIN_PARAM_AXIS = 68 | 当张量作为LayerNorm算子的beginParamsAxis参数时，使用本枚举值。 |
| OH_NN_LAYER_NORM_ELEMENTWISE_AFFINE = 69 | 当张量作为LayerNorm算子的elementwiseAffine参数时，使用本枚举值。 |
| OH_NN_REDUCE_PROD_KEEP_DIMS = 70 | 当张量作为ReduceProd算子的keepDims参数时，使用本枚举值。 |
| OH_NN_REDUCE_ALL_KEEP_DIMS = 71 | 当张量作为ReduceAll算子的keepDims参数时，使用本枚举值。 |
| OH_NN_QUANT_DTYPE_CAST_SRC_T = 72 | 当张量作为QuantDTypeCast算子的srcT参数时，使用本枚举值。 |
| OH_NN_QUANT_DTYPE_CAST_DST_T = 73 | 当张量作为QuantDTypeCast算子的dstT参数时，使用本枚举值。 |
| OH_NN_TOP_K_SORTED = 74 | 当张量作为Topk算子的Sorted参数时，使用本枚举值。 |
| OH_NN_ARG_MAX_AXIS = 75 | 当张量作为ArgMax算子的axis参数时，使用本枚举值。 |
| OH_NN_ARG_MAX_KEEPDIMS = 76 | 当张量作为ArgMax算子的keepDims参数时，使用本枚举值。 |
| OH_NN_UNSQUEEZE_AXIS = 77 | 当张量作为Unsqueeze算子的Axis参数时，使用本枚举值。 |
| OH_NN_UNSTACK_AXIS = 78 | 当张量作为Unstack算子的axis参数时，使用本枚举值。 @since 12 |
| OH_NN_FLATTEN_AXIS = 79 | 当张量作为Flatten算子的axis参数时，使用本枚举值。 @since 12 |
| OH_NN_DEPTH_TO_SPACE_BLOCK_SIZE = 80 | 当张量作为DepthToSpace算子的blockSize参数时，使用本枚举值。 @since 12 |
| OH_NN_DEPTH_TO_SPACE_MODE = 81 | 当张量作为DepthToSpace算子的mode参数时，使用本枚举值。 @since 12 |
| OH_NN_RANGE_START = 82 | 当张量作为Range算子的start参数时，使用本枚举值。 @since 12 |
| OH_NN_RANGE_LIMIT = 83 | 当张量作为Range算子的limit参数时，使用本枚举值。 @since 12 |
| OH_NN_RANGE_DELTA = 84 | 当张量作为Range算子的delta参数时，使用本枚举值。 @since 12 |
| OH_NN_CONSTANT_OF_SHAPE_DATA_TYPE = 85 | 当张量作为ConstantOfShape算子的dataType参数时，使用本枚举值。 @since 12 |
| OH_NN_CONSTANT_OF_SHAPE_VALUE = 86 | 当张量作为ConstantOfShape算子的value参数时，使用本枚举值。 @since 12 |
| OH_NN_BROADCAST_TO_SHAPE = 87 | 当张量作为BroadcastTo算子的shape参数时，使用本枚举值。 @since 12 |
| OH_NN_INSTANCE_NORM_EPSILON = 88 | 当张量作为InstanceNorm算子的epsilon参数时，使用本枚举值。 @since 12 |
| OH_NN_EXP_BASE = 89 | 当张量作为Exp算子的base参数时，使用本枚举值。 @since 12 |
| OH_NN_EXP_SCALE = 90 | 当张量作为Exp算子的scale参数时，使用本枚举值。 @since 12 |
| OH_NN_EXP_SHIFT = 91 | 当张量作为Exp算子的shift参数时，使用本枚举值。 @since 12 |
| OH_NN_LEAKY_RELU_NEGATIVE_SLOPE = 92 | 当张量作为LeakyRelu算子的negativeSlope参数时，使用本枚举值。 @since 12 |
| OH_NN_LSTM_BIDIRECTIONAL = 93 | 当张量作为LSTM算子的bidirectional参数时，使用本枚举值。 @since 12 |
| OH_NN_LSTM_HAS_BIAS = 94 | 当张量作为LSTM算子的hasBias参数时，使用本枚举值。 @since 12 |
| OH_NN_LSTM_INPUT_SIZE = 95 | 当张量作为LSTM算子的inputSize参数时，使用本枚举值。 @since 12 |
| OH_NN_LSTM_HIDDEN_SIZE = 96 | 当张量作为LSTM算子的hiddenSize参数时，使用本枚举值。 @since 12 |
| OH_NN_LSTM_NUM_LAYERS = 97 | 当张量作为LSTM算子的numLayers参数时，使用本枚举值。 @since 12 |
| OH_NN_LSTM_NUM_DIRECTIONS = 98 | 当张量作为LSTM算子的numDirections参数时，使用本枚举值。 @since 12 |
| OH_NN_LSTM_DROPOUT = 99 | 当张量作为LSTM算子的dropout参数时，使用本枚举值。 @since 12 |
| OH_NN_LSTM_ZONEOUT_CELL = 100 | 当张量作为LSTM算子的zoneoutCell参数时，使用本枚举值。 @since 12 |
| OH_NN_LSTM_ZONEOUT_HIDDEN = 101 | 当张量作为LSTM算子的zoneoutHidden参数时，使用本枚举值。 @since 12 |
| OH_NN_LSTM_PROJ_SIZE = 102 | 当张量作为LSTM算子的projSize参数时，使用本枚举值。 @since 12 |
| OH_NN_CLIP_MAX = 103 | 当张量作为Clip算子的max参数时，使用本枚举值。 @since 12 |
| OH_NN_CLIP_MIN = 104 | 当张量作为Clip算子的min参数时，使用本枚举值。 @since 12 |
| OH_NN_ALL_KEEP_DIMS = 105 | 当张量作为All算子的keepDims参数时，使用本枚举值。 @since 12 |
| OH_NN_ASSERT_SUMMARIZE = 106 | 当张量作为Assert算子的summarize参数时，使用本枚举值。 @since 12 |
| OH_NN_POW_SCALE = 107 | 当张量作为Pow算子的scale参数时，使用本枚举值。 @since 12 |
| OH_NN_POW_SHIFT = 108 | 当张量作为Pow算子的shift参数时，使用本枚举值。 @since 12 |
| OH_NN_AVG_POOL_ROUND_MODE = 109 | 当张量作为AvgPool算子的RoundMode参数时，使用本枚举值。 @since 12 |
| OH_NN_AVG_POOL_GLOBAL = 110 | 当张量作为AvgPool算子的global参数时，使用本枚举值。 @since 12 |
| OH_NN_FULL_CONNECTION_HAS_BIAS = 111 | 当张量作为FullConnection算子的hasBias参数时，使用本枚举值。 @since 12 |
| OH_NN_FULL_CONNECTION_USE_AXIS = 112 | 当张量作为FullConnection算子的useAxis参数时，使用本枚举值。 @since 12 |
| OH_NN_GELU_APPROXIMATE = 113 | 当张量作为GeLU算子的approximate参数时，使用本枚举值。 @since 12 |
| OH_NN_MAX_POOL_ROUND_MODE = 114 | 当张量作为MaxPool算子的RoundMode参数时，使用本枚举值。 @since 12 |
| OH_NN_MAX_POOL_GLOBAL = 115 | 当张量作为MaxPool算子的global参数时，使用本枚举值。 @since 12 |
| OH_NN_PAD_PADDING_MODE = 116 | 当张量作为Pad算子的paddingMode参数时，使用本枚举值。 @since 12 |
| OH_NN_REDUCE_MEAN_REDUCE_TO_END = 117 | 当张量作为ReduceMean算子的reduceToEnd参数时，使用本枚举值。 @since 12 |
| OH_NN_REDUCE_MEAN_COEFF = 118 | 当张量作为ReduceMean算子的coeff参数时，使用本枚举值。 @since 12 |
| OH_NN_REDUCE_PROD_REDUCE_TO_END = 119 | 当张量作为ReduceProd算子的reduceToEnd参数时，使用本枚举值。 @since 12 |
| OH_NN_REDUCE_PROD_COEFF = 120 | 当张量作为ReduceProd算子的coeff参数时，使用本枚举值。 @since 12 |
| OH_NN_REDUCE_ALL_REDUCE_TO_END = 121 | 当张量作为ReduceAll算子的reduceToEnd参数时，使用本枚举值。 @since 12 |
| OH_NN_REDUCE_ALL_COEFF = 122 | 当张量作为ReduceAll算子的coeff参数时，使用本枚举值。 @since 12 |
| OH_NN_TOP_K_AXIS = 123 | 当张量作为TopK算子的axis参数时，使用本枚举值。 @since 12 |
| OH_NN_ARG_MAX_TOP_K = 124 | 当张量作为ArgMax算子的topK参数时，使用本枚举值。 @since 12 |
| OH_NN_ARG_MAX_OUT_MAX_VALUE = 125 | 当张量作为ArgMax算子的outMaxValue参数时，使用本枚举值。 @since 12 |
| OH_NN_QUANT_DTYPE_CAST_AXIS = 126 | 当张量作为QuantDTypeCast算子的axis参数时，使用本枚举值。 @since 12 |
| OH_NN_SLICE_AXES = 127 | 当张量作为Slice算子的axes参数时，使用本枚举值。 @since 12 |
| OH_NN_TILE_DIMS = 128 | 当张量作为Tile算子的dims参数时，使用本枚举值。 @since 12 |
| OH_NN_CROP_AXIS = 129 | 当张量作为Crop算子的axis参数时，使用本枚举值。 @since 12 |
| OH_NN_CROP_OFFSET = 130 | 当张量作为Crop算子的offset参数时，使用本枚举值。 @since 12 |
| OH_NN_DETECTION_POST_PROCESS_INPUT_SIZE = 131 | 当张量作为DetectionPostProcess算子的inputSize参数时，使用本枚举值。 @since 12 |
| OH_NN_DETECTION_POST_PROCESS_SCALE = 132 | 当张量作为DetectionPostProcess算子的scale参数时，使用本枚举值。 @since 12 |
| OH_NN_DETECTION_POST_PROCESS_NMS_IOU_THRESHOLD = 133 | 当张量作为DetectionPostProcess算子的nmsIouThreshold参数时，使用本枚举值。 @since 12 |
| OH_NN_DETECTION_POST_PROCESS_NMS_SCORE_THRESHOLD = 134 | 当张量作为DetectionPostProcess算子的nmsScoreThreshold参数时，使用本枚举值。 @since 12 |
| OH_NN_DETECTION_POST_PROCESS_MAX_DETECTIONS = 135 | 当张量作为DetectionPostProcess算子的maxDetections参数时，使用本枚举值。 @since 12 |
| OH_NN_DETECTION_POST_PROCESS_DETECTIONS_PER_CLASS = 136 | 当张量作为DetectionPostProcess算子的perClass参数时，使用本枚举值。 @since 12 |
| OH_NN_DETECTION_POST_PROCESS_MAX_CLASSES_PER_DETECTION = 137 | 当张量作为DetectionPostProcess算子的maxClassPerDetection参数时，使用本枚举值。 @since 12 |
| OH_NN_DETECTION_POST_PROCESS_NUM_CLASSES = 138 | 当张量作为DetectionPostProcess算子的numClasses参数时，使用本枚举值。 @since 12 |
| OH_NN_DETECTION_POST_PROCESS_USE_REGULAR_NMS = 139 | 当张量作为DetectionPostProcess算子的useRegularNms参数时，使用本枚举值。 @since 12 |
| OH_NN_DETECTION_POST_PROCESS_OUT_QUANTIZED = 140 | 当张量作为DetectionPostProcess算子的outQuantized参数时，使用本枚举值。 @since 12 |
| OH_NN_L2_NORMALIZE_AXIS = 141 | 当张量作为L2Normalize算子的axis参数时，使用本枚举值。 @since 12 |
| OH_NN_L2_NORMALIZE_EPSILON = 142 | 当张量作为L2Normalize算子的epsilon参数时，使用本枚举值。 @since 12 |
| OH_NN_L2_NORMALIZE_ACTIVATION_TYPE = 143 | 当张量作为L2Normalize算子的activationType参数时，使用本枚举值。 @since 12 |
| OH_NN_LOG_SOFTMAX_AXIS = 144 | 当张量作为LogSoftmax算子的axis参数时，使用本枚举值。 @since 12 |
| OH_NN_LRN_DEPTH_RADIUS = 145 | 当张量作为LRN算子的depthRadius参数时，使用本枚举值。 @since 12 |
| OH_NN_LRN_BIAS = 146 | 当张量作为LRN算子的bias参数时，使用本枚举值。 @since 12 |
| OH_NN_LRN_ALPHA = 147 | 当张量作为LRN算子的alpha参数时，使用本枚举值。 @since 12 |
| OH_NN_LRN_BETA = 148 | 当张量作为LRN算子的beta参数时，使用本枚举值。 @since 12 |
| OH_NN_LRN_NORM_REGION = 149 | 当张量作为LRN算子的normRegion参数时，使用本枚举值。 @since 12 |
| OH_NN_SPACE_TO_DEPTH_BLOCK_SIZE = 150 | 当张量作为SpaceToDepth算子的blockSize参数时，使用本枚举值。 @since 12 |
| OH_NN_REDUCE_MAX_KEEP_DIMS = 151 | 当张量作为ReduceMax算子的keepDims参数时，使用本枚举值。 @since 12 |
| OH_NN_REDUCE_MAX_REDUCE_TO_END = 152 | 当张量作为ReduceMax算子的reduceToEnd参数时，使用本枚举值。 @since 12 |
| OH_NN_REDUCE_MAX_COEFF = 153 | 当张量作为ReduceMax算子的coeff参数时，使用本枚举值。 @since 12 |
| OH_NN_REDUCE_MIN_KEEP_DIMS = 154 | 当张量作为ReduceMin算子的keepDims参数时，使用本枚举值。 @since 12 |
| OH_NN_REDUCE_MIN_REDUCE_TO_END = 155 | 当张量作为ReduceMin算子的reduceToEnd参数时，使用本枚举值。 @since 12 |
| OH_NN_REDUCE_MIN_COEFF = 156 | 当张量作为ReduceMin算子的coeff参数时，使用本枚举值。 @since 12 |
| OH_NN_REDUCE_SUM_KEEP_DIMS = 157 | 当张量作为ReduceSum算子的keepDims参数时，使用本枚举值。 @since 12 |
| OH_NN_REDUCE_SUM_REDUCE_TO_END = 158 | 当张量作为ReduceSum算子的reduceToEnd参数时，使用本枚举值。 @since 12 |
| OH_NN_REDUCE_SUM_COEFF = 159 | 当张量作为ReduceSum算子的coeff参数时，使用本枚举值。 @since 12 |
| OH_NN_REDUCE_L2_KEEP_DIMS = 160 | 当张量作为ReduceL2算子的keepDims参数时，使用本枚举值。 @since 12 |
| OH_NN_REDUCE_L2_REDUCE_TO_END = 161 | 当张量作为ReduceL2算子的reduceToEnd参数时，使用本枚举值。 @since 12 |
| OH_NN_REDUCE_L2_COEFF = 162 | 当张量作为ReduceL2算子的coeff参数时，使用本枚举值。 @since 12 |


## 函数说明

### NN_OnRunDone()

```c
typedef void (*NN_OnRunDone)(void *userData, OH_NN_ReturnCode errCode, void *outputTensor[], int32_t outputCount)
```

**描述：**

异步推理结束后的回调处理函数句柄。 使用参数userData来查询希望获取的那次异步推理执行。 userData与调用异步推理{@link OH_NNExecutor_RunAsync}接口时传入的参数userData是一致的。 <br> 使用参数errCode（[OH_NN_ReturnCode](capi-neural-network-runtime-type-h.md#oh_nn_returncode)类型）来获取该次异步推理的返回状态。

**系统能力：** SystemCapability.AI.NeuralNetworkRuntime

**起始版本：** 11

**参数：**

| 参数项 | 描述 |
| -- | -- |
| void \*userData | 异步推理执行的标识符，与调用异步推理{@link OH_NNExecutor_RunAsync}接口时传入的参数userData一致。 |
| [OH_NN_ReturnCode](capi-neural-network-runtime-type-h.md#oh_nn_returncode) errCode | 该次异步推理的返回状态（[OH_NN_ReturnCode](capi-neural-network-runtime-type-h.md#oh_nn_returncode)类型）。 |
| void \*outputTensor[] | 异步推理的输出张量，与调用异步推理{@link OH_NNExecutor_RunAsync}接口时传入的参数outputTensor一致。 |
| int32_t outputCount | 异步推理输出张量的数量，与调用异步推理{@link OH_NNExecutor_RunAsync}接口时传入的参数outputCount一致。 |

### NN_OnServiceDied()

```c
typedef void (*NN_OnServiceDied)(void *userData)
```

**描述：**

异步推理执行期间设备驱动服务异常终止时的回调处理函数句柄。<br> 如果该回调函数被调用，您需要重新编译模型。 <br> 使用参数userData来查询希望获取的那次异步推理执行。 userData与调用异步推理{@link OH_NNExecutor_RunAsync}接口时传入的参数userData是一致的。

**系统能力：** SystemCapability.AI.NeuralNetworkRuntime

**起始版本：** 11

**参数：**

| 参数项 | 描述 |
| -- | -- |
| void \*userData | 异步推理执行的标识符，与调用异步推理{@link OH_NNExecutor_RunAsync}接口时传入的参数 userData 一致。 |


