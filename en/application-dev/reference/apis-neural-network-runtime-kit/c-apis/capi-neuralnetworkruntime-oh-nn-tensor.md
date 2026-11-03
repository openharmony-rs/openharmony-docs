# OH_NN_Tensor

```c
struct OH_NN_Tensor {...}
```

## Overview

Defines the tensor structure.<br> It is usually used to construct data nodes and operator parameters in a model graph. When constructing a tensor, you need to specify the data type, number of dimensions, dimension information, and quantization information.

**System capability**: SystemCapability.AI.NeuralNetworkRuntime

**Since**: 9

**Deprecated**: 11

**Replaced by**: [NN_TensorDesc](capi-neuralnetworkruntime-nn-tensordesc.md)

**Related module**: [NeuralNetworkRuntime](capi-others-neuralnetworkruntime.md)

**Header file**: [neural_network_runtime_type.h](capi-neural-network-runtime-type-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| [OH_NN_DataType](capi-neural-network-runtime-type-h.md#oh_nn_datatype) dataType | Data type of the specified tensor. The value must be an enumerated value of [OH_NN_DataType](capi-neural-network-runtime-type-h.md#oh_nn_datatype). |
| uint32_t dimensionCount | Number of dimensions of the specified tensor |
| const int32_t *dimensions | Dimension information (shape) of the specified tensor |
| const OH_NN_QuantParam *quantParam | Quantization information of the specified tensor. The data type must be [OH_NN_QuantParam](capi-neuralnetworkruntime-oh-nn-quantparam.md). |
| [OH_NN_TensorType](capi-neural-network-runtime-type-h.md#oh_nn_tensortype) type | Specifies the tensor type. The value of <b>type</b> is related to the tensor usage. When the tensor is used as the input or output of the model, set <b>type</b> to [OH_NN_TENSOR](capi-neural-network-runtime-type-h.md#oh_nn_tensortype). When a tensor is used as an operator parameter, select any enumerated value except [OH_NN_TENSOR](capi-neural-network-runtime-type-h.md#oh_nn_tensortype) from [OH_NN_TensorType](capi-neural-network-runtime-type-h.md#oh_nn_tensortype).<br>**Since**: 9 |


