# OH_NN_Tensor
<!--Kit: Neural Network Runtime Kit-->
<!--Subsystem: AI-->
<!--Owner: @GbuzhidaoR-->
<!--SE: @GbuzhidaoR-->
<!--TSE @GbuzhidaoR-->

## 概述

张量结构体。

通常用于构造模型图中的数据节点和算子参数，在构造张量时需要明确数据类型、维数、维度信息和量化信息。

**起始版本：** 9

**废弃版本：** 11

**替代接口：** [NN_TensorDesc](capi-neuralnetworkruntime-nn-tensordesc.md)

**相关模块：** [NeuralNetworkRuntime](capi-neuralnetworkruntime.md)

**所在头文件：** [neural_network_runtime_type.h](capi-neural-network-runtime-type-h.md)

## 汇总

### 成员变量

| 名称                                                                                  | 描述 |
|-------------------------------------------------------------------------------------| -- |
| [OH_NN_DataType](capi-neural-network-runtime-type-h.md#oh_nn_datatype) dataType     | 指定张量的数据类型，要求从[OH_NN_DataType](capi-neural-network-runtime-type-h.md#oh_nn_datatype)枚举类型中取值。 |
| uint32_t dimensionCount                                                             | 指定张量的维数。 |
| const int32_t *dimensions                                                           | 指定张量的维度信息（形状）。 |
| const [OH_NN_QuantParam](capi-neuralnetworkruntime-oh-nn-quantparam.md) *quantParam | 指定张量的量化信息，数据类型要求为[OH_NN_QuantParam](capi-neuralnetworkruntime-oh-nn-quantparam.md)。 |
| [OH_NN_TensorType](capi-neural-network-runtime-type-h.md#oh_nn_tensortype) type     | 指定张量的类型。type的取值和张量的用途相关，当张量用作模型的输入或输出，则要求将type设置为[OH_NN_TENSOR](capi-neural-network-runtime-type-h.md#oh_nn_tensortype)；当张量用作算子参数，则要求从[OH_NN_TensorType](capi-neural-network-runtime-type-h.md#oh_nn_tensortype)中选择除[OH_NN_TENSOR](capi-neural-network-runtime-type-h.md#oh_nn_tensortype)以外的枚举值。 |


