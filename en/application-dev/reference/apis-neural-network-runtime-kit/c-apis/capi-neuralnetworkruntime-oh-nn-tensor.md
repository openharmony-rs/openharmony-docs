# OH_NN_Tensor

```c
typedef struct OH_NN_Tensor {...} OH_NN_Tensor
```

## Overview

Defines the tensor structure.<br> It is usually used to construct data nodes and operator parameters in a model graph. When constructing a tensor, you need to specify the data type, number of dimensions, dimension information, and quantization information.

**System capability**: SystemCapability.AI.NeuralNetworkRuntime

**Since**: 9

**Deprecated**: 11

**Replaced by**: {@link NN_TensorDesc}

**Related module**: [NeuralNetworkRuntime](capi-neuralnetworkruntime.md)

**Header file**: [neural_network_runtime_type.h](capi-neural-network-runtime-type-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| [OH_NN_DataType](capi-neural-network-runtime-type-h.md#oh_nn_datatype) dataType | Data type of the specified tensor. The value must be an enumerated value of {@link OH_NN_DataType}. |
| uint32_t dimensionCount | Number of dimensions of the specified tensor |
| const int32_t *dimensions | Dimension information (shape) of the specified tensor |
| const [OH_NN_QuantParam](capi-neuralnetworkruntime-oh-nn-quantparam.md) *quantParam | Quantization information of the specified tensor. The data type must be {@link OH_NN_QuantParam}. |
| [OH_NN_TensorType](capi-neural-network-runtime-type-h.md#oh_nn_tensortype) type |  |


