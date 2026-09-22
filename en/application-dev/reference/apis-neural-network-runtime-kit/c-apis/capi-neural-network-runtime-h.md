# neural_network_runtime.h

## Overview

Defines the Neural Network Runtime APIs. The AI inference framework uses the Native APIs provided by Neural Network Runtime to construct models.  Note: Currently, the APIs of Neural Network Runtime do not support multi-thread calling. <br> include "neural_network_runtime/neural_network_runtime.h"

**Library**: libneural_network_runtime.so

**System capability**: SystemCapability.AI.NeuralNetworkRuntime

**Since**: 9

**Related module**: [NeuralNetworkRuntime](capi-neuralnetworkruntime.md)

## Summary

### Function

| Name | Description |
| -- | -- |
| [NN_QuantParam *OH_NNQuantParam_Create()](#oh_nnquantparam_create) | Creates a [NN_QuantParam](capi-neuralnetworkruntime-nn-quantparam.md) instance.<br> After the [NN_QuantParam](capi-neuralnetworkruntime-nn-quantparam.md) instance is created, call [OH_NNQuantParam_SetScales](capi-neural-network-runtime-h.md#oh_nnquantparam_setscales), [OH_NNQuantParam_SetZeroPoints](capi-neural-network-runtime-h.md#oh_nnquantparam_setzeropoints), [OH_NNQuantParam_SetNumBits](capi-neural-network-runtime-h.md#oh_nnquantparam_setnumbits) to set its attributes, and then call [OH_NNModel_SetTensorQuantParams](capi-neural-network-runtime-h.md#oh_nnmodel_settensorquantparams) to set it to a tensor. After that you should destroy it by calling [OH_NNQuantParam_Destroy](capi-neural-network-runtime-h.md#oh_nnquantparam_destroy) to avoid memory leak. |
| [OH_NN_ReturnCode OH_NNQuantParam_SetScales(NN_QuantParam *quantParams, const double *scales, size_t quantCount)](#oh_nnquantparam_setscales) | Sets the scales of the [NN_QuantParam](capi-neuralnetworkruntime-nn-quantparam.md) instance.<br> The parameter <b>quantCount</b> is the number of quantization parameters of a tensor, e.g. the quantCount is the channel count if the tensor is per-channel quantized. |
| [OH_NN_ReturnCode OH_NNQuantParam_SetZeroPoints(NN_QuantParam *quantParams, const int32_t *zeroPoints, size_t quantCount)](#oh_nnquantparam_setzeropoints) | Sets the zero points of the [NN_QuantParam](capi-neuralnetworkruntime-nn-quantparam.md) instance.<br> The parameter <b>quantCount</b> is the number of quantization parameters of a tensor, e.g. the quantCount is the channel count if the tensor is per-channel quantized. |
| [OH_NN_ReturnCode OH_NNQuantParam_SetNumBits(NN_QuantParam *quantParams, const uint32_t *numBits, size_t quantCount)](#oh_nnquantparam_setnumbits) | Sets the number bits of the [NN_QuantParam](capi-neuralnetworkruntime-nn-quantparam.md) instance.<br> The parameter <b>quantCount</b> is the number of quantization parameters of a tensor, e.g. the quantCount is the channel count if the tensor is per-channel quantized. |
| [OH_NN_ReturnCode OH_NNQuantParam_Destroy(NN_QuantParam **quantParams)](#oh_nnquantparam_destroy) | Releases a [NN_QuantParam](capi-neuralnetworkruntime-nn-quantparam.md) instance.<br> The [NN_QuantParam](capi-neuralnetworkruntime-nn-quantparam.md) instance needs to be released to avoid memory leak after it is set to a [NN_TensorDesc](capi-neuralnetworkruntime-nn-tensordesc.md). <br> If <b>quantParams</b> or <b>*quantParams</b> is a null pointer, this method only prints warning logs and does not execute the release. |
| [OH_NNModel *OH_NNModel_Construct(void)](#oh_nnmodel_construct) | Creates a model instance of the [OH_NNModel](capi-neuralnetworkruntime-oh-nnmodel.md) type and uses other APIs provided by OH_NNModel to construct the model instance.<br> Before composition, call [OH_NNModel_Construct](capi-neural-network-runtime-h.md#oh_nnmodel_construct) to create a model instance. Based on the model topology, call the [OH_NNModel_AddTensorToModel](capi-neural-network-runtime-h.md#oh_nnmodel_addtensortomodel), [OH_NNModel_AddOperation](capi-neural-network-runtime-h.md#oh_nnmodel_addoperation), and [OH_NNModel_SetTensorData](capi-neural-network-runtime-h.md#oh_nnmodel_settensordata) methods to fill in the data and operator nodes of the model, and then call [OH_NNModel_SpecifyInputsAndOutputs](capi-neural-network-runtime-h.md#oh_nnmodel_specifyinputsandoutputs) to specify the inputs and outputs of the model. After the model topology is constructed, call [OH_NNModel_Finish](capi-neural-network-runtime-h.md#oh_nnmodel_finish) to build the model. <br> After a model instance is no longer used, you need to destroy it by calling [OH_NNModel_Destroy](capi-neural-network-runtime-h.md#oh_nnmodel_destroy) to avoid memory leak. |
| [OH_NN_ReturnCode OH_NNModel_AddTensorToModel(OH_NNModel *model, const NN_TensorDesc *tensorDesc)](#oh_nnmodel_addtensortomodel) | Adds a tensor to the model instance.<br> The data node and operator parameters in the Neural Network Runtime model are composed of tensors of the model. This method is used to add tensors to a model instance based on the <b>tensorDesc</b> parameter with type of [NN_TensorDesc](capi-neuralnetworkruntime-nn-tensordesc.md). [NN_TensorDesc](capi-neuralnetworkruntime-nn-tensordesc.md) contains some attributes such as shape, format, data type and provides corresponding APIs to access them. The order of adding tensors is specified by the indices recorded in the model. The [OH_NNModel_SetTensorData](capi-neural-network-runtime-h.md#oh_nnmodel_settensordata), [OH_NNModel_AddOperation](capi-neural-network-runtime-h.md#oh_nnmodel_addoperation), and [OH_NNModel_SpecifyInputsAndOutputs](capi-neural-network-runtime-h.md#oh_nnmodel_specifyinputsandoutputs) methods specify tensors based on the indices. <br> Neural Network Runtime supports inputs and outputs of the dynamic shape. When adding a data node with a dynamic shape, you need to set the dimensions that support dynamic changes to <b>-1</b>. For example, if the shape of a four-dimensional tensor is set to <b>[1, -1, 2, 2]</b>, the second dimension supports dynamic changes. |
| [OH_NN_ReturnCode OH_NNModel_SetTensorData(OH_NNModel *model, uint32_t index, const void *dataBuffer, size_t length)](#oh_nnmodel_settensordata) | Sets the tensor value.<br> For tensors with constant values (such as model weights), you need to use this method to set their data. The index of a tensor is determined by the order in which the tensor is added to the model. For details about how to add a tensor, see [OH_NNModel_AddTensorToModel](capi-neural-network-runtime-h.md#oh_nnmodel_addtensortomodel). |
| [OH_NN_ReturnCode OH_NNModel_SetTensorQuantParams(OH_NNModel *model, uint32_t index, NN_QuantParam *quantParam)](#oh_nnmodel_settensorquantparams) | Sets the quantization parameter of a tensor. |
| [OH_NN_ReturnCode OH_NNModel_SetTensorType(OH_NNModel *model, uint32_t index, OH_NN_TensorType tensorType)](#oh_nnmodel_settensortype) | Sets the tensor type. See [OH_NN_TensorType](capi-neural-network-runtime-type-h.md#oh_nn_tensortype) for details. |
| [OH_NN_ReturnCode OH_NNModel_AddOperation(OH_NNModel *model, OH_NN_OperationType op, const OH_NN_UInt32Array *paramIndices, const OH_NN_UInt32Array *inputIndices, const OH_NN_UInt32Array *outputIndices)](#oh_nnmodel_addoperation) | Adds an operator to a model instance.<br> This method is used to add an operator to a model instance. The operator type is specified by <b>op</b>, and the operator parameters, inputs, and outputs are specified by <b>paramIndices</b>, <b>inputIndices</b>, and <b>outputIndices</b> respectively. This method verifies the attributes of operator parameters and the number of input and output parameters. These attributes must be correctly set when [OH_NNModel_AddTensorToModel](capi-neural-network-runtime-h.md#oh_nnmodel_addtensortomodel) is called to add tensors. For details about the expected parameters, input attributes, and output attributes of each operator, see [OH_NN_OperationType](capi-neural-network-runtime-type-h.md#oh_nn_operationtype). <br> <b>paramIndices</b>, <b>inputIndices</b>, and <b>outputIndices</b> store the indices of tensors. The indices are determined by the order in which tensors are added to the model. For details about how to add a tensor, see [OH_NNModel_AddTensorToModel](capi-neural-network-runtime-h.md#oh_nnmodel_addtensortomodel). <br> If unnecessary parameters are added when adding an operator, this method returns [OH_NN_INVALID_PARAMETER](capi-neural-network-runtime-type-h.md#oh_nn_returncode). If no operator parameter is set, the operator uses the default parameter value. For details about the default values, see [OH_NN_OperationType](capi-neural-network-runtime-type-h.md#oh_nn_operationtype). |
| [OH_NN_ReturnCode OH_NNModel_SpecifyInputsAndOutputs(OH_NNModel *model, const OH_NN_UInt32Array *inputIndices, const OH_NN_UInt32Array *outputIndices)](#oh_nnmodel_specifyinputsandoutputs) | Specifies the inputs and outputs of a model.<br> A tensor must be specified as the end-to-end inputs and outputs of a model instance. This type of tensor cannot be set using [OH_NNModel_SetTensorData](capi-neural-network-runtime-h.md#oh_nnmodel_settensordata). <br> The index of a tensor is determined by the order in which the tensor is added to the model. For details about how to add a tensor, see [OH_NNModel_AddTensorToModel](capi-neural-network-runtime-h.md#oh_nnmodel_addtensortomodel). <br> Currently, the model inputs and outputs cannot be set asynchronously. |
| [OH_NN_ReturnCode OH_NNModel_Finish(OH_NNModel *model)](#oh_nnmodel_finish) | Completes model composition.<br> After the model topology is set up, call this method to indicate that the composition is complete. After this method is called, additional composition operations cannot be performed. If [OH_NNModel_AddTensorToModel](capi-neural-network-runtime-h.md#oh_nnmodel_addtensortomodel), [OH_NNModel_AddOperation](capi-neural-network-runtime-h.md#oh_nnmodel_addoperation), [OH_NNModel_SetTensorData](capi-neural-network-runtime-h.md#oh_nnmodel_settensordata), and [OH_NNModel_SpecifyInputsAndOutputs](capi-neural-network-runtime-h.md#oh_nnmodel_specifyinputsandoutputs) are called, [OH_NN_OPERATION_FORBIDDEN](capi-neural-network-runtime-type-h.md#oh_nn_returncode) is returned. <br> Before calling [OH_NNModel_GetAvailableOperations](capi-neural-network-runtime-h.md#oh_nnmodel_getavailableoperations) and [OH_NNCompilation_Construct](capi-neural-network-core-h.md#oh_nncompilation_construct), you must call this method to complete composition. |
| [void OH_NNModel_Destroy(OH_NNModel **model)](#oh_nnmodel_destroy) | Releases a model instance.<br> This method needs to be called to release the model instance created by calling [OH_NNModel_Construct](capi-neural-network-runtime-h.md#oh_nnmodel_construct). Otherwise, memory leak will occur. <br> If <b>model</b> or <b>*model</b> is a null pointer, this method only prints warning logs and does not execute the release. |
| [OH_NN_ReturnCode OH_NNModel_GetAvailableOperations(OH_NNModel *model, size_t deviceID, const bool **isSupported, uint32_t *opCount)](#oh_nnmodel_getavailableoperations) | Queries whether the device supports operators in the model. The support status is indicated by the Boolean value.<br> Queries whether underlying device supports operators in a model instance. The device is specified by <b>deviceID</b>, and the result is represented by the array pointed by <b>isSupported</b>. If the <i>i</i>th operator is supported, the value of <b>(*isSupported)</b>[<i>i</i>] is <b>true</b>. Otherwise, the value is <b>false</b>. <br> After this method is successfully executed, <b>(*isSupported)</b> points to the bool array that records the operator support status. The operator quantity for the array length is the same as that for the model instance. The memory corresponding to this array is managed by Neural Network Runtime and is automatically destroyed after the model instance is destroyed or this method is called again. |
| [OH_NN_ReturnCode OH_NNModel_AddTensor(OH_NNModel *model, const OH_NN_Tensor *tensor)](#oh_nnmodel_addtensor) | Adds a tensor to a model instance.<br> The data node and operator parameters in the Neural Network Runtime model are composed of tensors of the model. This method is used to add tensors to a model instance based on the <b>tensor</b> parameter. The sequence of adding tensors is specified by the index value recorded in the model. The [OH_NNModel_SetTensorData](capi-neural-network-runtime-h.md#oh_nnmodel_settensordata), [OH_NNModel_AddOperation](capi-neural-network-runtime-h.md#oh_nnmodel_addoperation), and [OH_NNModel_SpecifyInputsAndOutputs](capi-neural-network-runtime-h.md#oh_nnmodel_specifyinputsandoutputs) methods specifies tensors based on the index value.<br> Neural Network Runtime supports inputs and outputs of the dynamic shape. When adding a data node with a dynamic shape, you need to set the dimensions that support dynamic changes in <b>tensor.dimensions</b> to <b>-1</b>. For example, if <b>tensor.dimensions</b> of a four-dimensional tensor is set to <b>[1, -1, 2, 2]</b>, the second dimension supports dynamic changes.(Deprecated in API11) |
| [OH_NN_ReturnCode OH_NNExecutor_SetInput(OH_NNExecutor *executor, uint32_t inputIndex, const OH_NN_Tensor *tensor, const void *dataBuffer, size_t length)](#oh_nnexecutor_setinput) | Sets the single input data for a model.<br> This method copies the data whose length is specified by <b>length</b> (in bytes) in <b>dataBuffer</b> to the shared memory of the underlying device. <b>inputIndex</b> specifies the input to be set and <b>tensor</b> sets information such as the input shape, type, and quantization parameters.<br> Neural Network Runtime supports models with dynamical shape input. For fixed shape input and dynamic shape input scenarios, this method uses different processing policies.<br> - Fixed shape input: The attributes of <b>tensor</b> must be the same as those of the tensor added by calling [OH_NNModel_AddTensor](capi-neural-network-runtime-h.md#oh_nnmodel_addtensor) in the composition phase. - Dynamic shape input: In the composition phase, because the shape is not fixed, each value in <b>tensor.dimensions</b> must be greater than <b>0</b> in the method calls to determine the shape input in the calculation phase. When setting the shape, you can modify only the dimension whose value is <b>-1</b>. Assume that <b>[-1, 224, 224, 3]</b> is input as the the dimension of A in the composition phase. When this method is called, only the size of the first dimension can be modified, e.g. to <b>[3, 224, 224, 3]</b>. If other dimensions are adjusted, [OH_NN_INVALID_PARAMETER](capi-neural-network-runtime-type-h.md#oh_nn_returncode) is returned.(Deprecated in API11) |
| [OH_NN_ReturnCode OH_NNExecutor_SetOutput(OH_NNExecutor *executor, uint32_t outputIndex, void *dataBuffer, size_t length)](#oh_nnexecutor_setoutput) | Sets the buffer for a single output of a model.<br> This method binds the buffer to which <b>dataBuffer</b> points to the output specified by <b>outputIndex</b>. The length of the buffer is specified by <b>length</b>.<br> After [OH_NNExecutor_Run](capi-neural-network-runtime-h.md#oh_nnexecutor_run) is called to complete a single model inference, Neural Network Runtime compares the length of the buffer to which <b>dataBuffer</b> points with the length of the output data and returns different results based on the actual situation.<br> - If the buffer length is greater than or equal to the data length, the inference result is copied to the buffer and [OH_NN_SUCCESS](capi-neural-network-runtime-type-h.md#oh_nn_returncode) is returned. You can read the inference result from <b>dataBuffer</b>. - If the buffer length is smaller than the data length, [OH_NNExecutor_Run](capi-neural-network-runtime-h.md#oh_nnexecutor_run) returns [OH_NN_INVALID_PARAMETER](capi-neural-network-runtime-type-h.md#oh_nn_returncode) and generates a log indicating that the buffer is too small.(Deprecated in API11) |
| [OH_NN_ReturnCode OH_NNExecutor_Run(OH_NNExecutor *executor)](#oh_nnexecutor_run) | Performs inference.<br> Performs end-to-end inference and computing of the model on the device associated with the executor.(Deprecated in API11) |
| [OH_NN_Memory *OH_NNExecutor_AllocateInputMemory(OH_NNExecutor *executor, uint32_t inputIndex, size_t length)](#oh_nnexecutor_allocateinputmemory) | Allocates shared memory to a single input on a device.<br> Neural Network Runtime provides a method for proactively allocating shared memory on a device. By specifying the executor and input index value, this method allocates shared memory whose size is specified by <b>length</b> on the device associated with a single input and returns the operation result through the [OH_NN_Memory](capi-neuralnetworkruntime-oh-nn-memory.md) instance.(Deprecated in API11) |
| [OH_NN_Memory *OH_NNExecutor_AllocateOutputMemory(OH_NNExecutor *executor, uint32_t outputIndex, size_t length)](#oh_nnexecutor_allocateoutputmemory) | Allocates shared memory to a single output on a device.<br> Neural Network Runtime provides a method for proactively allocating shared memory on a device. By specifying the executor and output index value, this method allocates shared memory whose size is specified by <b>length</b> on the device associated with a single output and returns the operation result through the [OH_NN_Memory](capi-neuralnetworkruntime-oh-nn-memory.md) instance.(Deprecated in API11) |
| [void OH_NNExecutor_DestroyInputMemory(OH_NNExecutor *executor, uint32_t inputIndex, OH_NN_Memory **memory)](#oh_nnexecutor_destroyinputmemory) | Releases the input memory to which the [OH_NN_Memory](capi-neuralnetworkruntime-oh-nn-memory.md) instance points.<br> This method needs to be called to release the memory instance created by calling [OH_NNExecutor_AllocateInputMemory](capi-neural-network-runtime-h.md#oh_nnexecutor_allocateinputmemory). Otherwise, memory leak will occur. The mapping between <b>inputIndex</b> and <b>memory</b> must be the same as that in memory instance creation.<br> If <b>memory</b> or <b>*memory</b> is a null pointer, this method only prints warning logs and does not execute the release logic.(Deprecated in API11) |
| [void OH_NNExecutor_DestroyOutputMemory(OH_NNExecutor *executor, uint32_t outputIndex, OH_NN_Memory **memory)](#oh_nnexecutor_destroyoutputmemory) | Releases the output memory to which the [OH_NN_Memory](capi-neuralnetworkruntime-oh-nn-memory.md) instance points.<br> This method needs to be called to release the memory instance created by calling [OH_NNExecutor_AllocateOutputMemory](capi-neural-network-runtime-h.md#oh_nnexecutor_allocateoutputmemory). Otherwise, memory leak will occur. The mapping between <b>outputIndex</b> and <b>memory</b> must be the same as that in memory instance creation.<br> If <b>memory</b> or <b>*memory</b> is a null pointer, this method only prints warning logs and does not execute the release logic.(Deprecated in API11) |
| [OH_NN_ReturnCode OH_NNExecutor_SetInputWithMemory(OH_NNExecutor *executor, uint32_t inputIndex, const OH_NN_Tensor *tensor, const OH_NN_Memory *memory)](#oh_nnexecutor_setinputwithmemory) | Specifies the hardware shared memory pointed to by the [OH_NN_Memory](capi-neuralnetworkruntime-oh-nn-memory.md) instance as the shared memory used by a single input.<br> In scenarios where memory needs to be managed by yourself, this method binds the execution input to the [OH_NN_Memory](capi-neuralnetworkruntime-oh-nn-memory.md) memory instance. During computing, the underlying device reads the input data from the shared memory pointed to by the memory instance. By using this method, concurrent execution of input setting, computing, and read can be implemented to improve inference efficiency of a data flow.(Deprecated in API11) |
| [OH_NN_ReturnCode OH_NNExecutor_SetOutputWithMemory(OH_NNExecutor *executor, uint32_t outputIndex, const OH_NN_Memory *memory)](#oh_nnexecutor_setoutputwithmemory) | Specifies the hardware shared memory pointed to by the [OH_NN_Memory](capi-neuralnetworkruntime-oh-nn-memory.md) instance as the shared memory used by a single output.<br> In scenarios where memory needs to be managed by yourself, this method binds the execution output to the [OH_NN_Memory](capi-neuralnetworkruntime-oh-nn-memory.md) memory instance. When computing is performed, the underlying hardware directly writes the computing result to the shared memory to which the memory instance points. By using this method, concurrent execution of input setting, computing, and read can be implemented to improve inference efficiency of a data flow.(Deprecated in API11) |

## Function description

### OH_NNQuantParam_Create()

```c
NN_QuantParam *OH_NNQuantParam_Create()
```

**Description**

Creates a [NN_QuantParam](capi-neuralnetworkruntime-nn-quantparam.md) instance.<br> After the [NN_QuantParam](capi-neuralnetworkruntime-nn-quantparam.md) instance is created, call [OH_NNQuantParam_SetScales](capi-neural-network-runtime-h.md#oh_nnquantparam_setscales), [OH_NNQuantParam_SetZeroPoints](capi-neural-network-runtime-h.md#oh_nnquantparam_setzeropoints), [OH_NNQuantParam_SetNumBits](capi-neural-network-runtime-h.md#oh_nnquantparam_setnumbits) to set its attributes, and then call [OH_NNModel_SetTensorQuantParams](capi-neural-network-runtime-h.md#oh_nnmodel_settensorquantparams) to set it to a tensor. After that you should destroy it by calling [OH_NNQuantParam_Destroy](capi-neural-network-runtime-h.md#oh_nnquantparam_destroy) to avoid memory leak.

**System capability**: SystemCapability.AI.NeuralNetworkRuntime

**Since**: 11

**Returns**:

| Type | Description |
| -- | -- |
| NN_QuantParam * | Pointer to a [NN_QuantParam](capi-neuralnetworkruntime-nn-quantparam.md) instance, or NULL if it fails to create. |

### OH_NNQuantParam_SetScales()

```c
OH_NN_ReturnCode OH_NNQuantParam_SetScales(NN_QuantParam *quantParams, const double *scales, size_t quantCount)
```

**Description**

Sets the scales of the [NN_QuantParam](capi-neuralnetworkruntime-nn-quantparam.md) instance.<br> The parameter <b>quantCount</b> is the number of quantization parameters of a tensor, e.g. the quantCount is the channel count if the tensor is per-channel quantized.

**System capability**: SystemCapability.AI.NeuralNetworkRuntime

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| NN_QuantParam *quantParams | Pointer to the [NN_QuantParam](capi-neuralnetworkruntime-nn-quantparam.md) instance. |
| const double *scales | An array of scales for all quantization parameters of the tensor. |
| size_t quantCount | Number of quantization parameters of the tensor. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_NN_ReturnCode | Execution result of the function. If the operation is successful, <b>OH_NN_SUCCESS</b> is returned.          If the operation fails, an error code is returned. For details about the error codes,          see [OH_NN_ReturnCode](capi-neural-network-runtime-type-h.md#oh_nn_returncode). |

### OH_NNQuantParam_SetZeroPoints()

```c
OH_NN_ReturnCode OH_NNQuantParam_SetZeroPoints(NN_QuantParam *quantParams, const int32_t *zeroPoints, size_t quantCount)
```

**Description**

Sets the zero points of the [NN_QuantParam](capi-neuralnetworkruntime-nn-quantparam.md) instance.<br> The parameter <b>quantCount</b> is the number of quantization parameters of a tensor, e.g. the quantCount is the channel count if the tensor is per-channel quantized.

**System capability**: SystemCapability.AI.NeuralNetworkRuntime

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| NN_QuantParam *quantParams | Pointer to the [NN_QuantParam](capi-neuralnetworkruntime-nn-quantparam.md) instance. |
| const int32_t *zeroPoints | An array of zero points for all quantization parameters of the tensor. |
| size_t quantCount | Number of quantization parameters of the tensor. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_NN_ReturnCode | Execution result of the function. If the operation is successful, <b>OH_NN_SUCCESS</b> is returned.          If the operation fails, an error code is returned. For details about the error codes,          see [OH_NN_ReturnCode](capi-neural-network-runtime-type-h.md#oh_nn_returncode). |

### OH_NNQuantParam_SetNumBits()

```c
OH_NN_ReturnCode OH_NNQuantParam_SetNumBits(NN_QuantParam *quantParams, const uint32_t *numBits, size_t quantCount)
```

**Description**

Sets the number bits of the [NN_QuantParam](capi-neuralnetworkruntime-nn-quantparam.md) instance.<br> The parameter <b>quantCount</b> is the number of quantization parameters of a tensor, e.g. the quantCount is the channel count if the tensor is per-channel quantized.

**System capability**: SystemCapability.AI.NeuralNetworkRuntime

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| NN_QuantParam *quantParams | Pointer to the [NN_QuantParam](capi-neuralnetworkruntime-nn-quantparam.md) instance. |
| const uint32_t *numBits | An array of number bits for all quantization parameters of the tensor. |
| size_t quantCount | Number of quantization parameters of the tensor. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_NN_ReturnCode | Execution result of the function. If the operation is successful, <b>OH_NN_SUCCESS</b> is returned.          If the operation fails, an error code is returned. For details about the error codes,          see [OH_NN_ReturnCode](capi-neural-network-runtime-type-h.md#oh_nn_returncode). |

### OH_NNQuantParam_Destroy()

```c
OH_NN_ReturnCode OH_NNQuantParam_Destroy(NN_QuantParam **quantParams)
```

**Description**

Releases a [NN_QuantParam](capi-neuralnetworkruntime-nn-quantparam.md) instance.<br> The [NN_QuantParam](capi-neuralnetworkruntime-nn-quantparam.md) instance needs to be released to avoid memory leak after it is set to a [NN_TensorDesc](capi-neuralnetworkruntime-nn-tensordesc.md). <br> If <b>quantParams</b> or <b>*quantParams</b> is a null pointer, this method only prints warning logs and does not execute the release.

**System capability**: SystemCapability.AI.NeuralNetworkRuntime

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| NN_QuantParam **quantParams | Double pointer to the [NN_QuantParam](capi-neuralnetworkruntime-nn-quantparam.md) instance. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_NN_ReturnCode | Execution result of the function. If the operation is successful, <b>OH_NN_SUCCESS</b> is returned. If the           operation fails, an error code is returned. For details about the error codes, see [OH_NN_ReturnCode](capi-neural-network-runtime-type-h.md#oh_nn_returncode). |

### OH_NNModel_Construct()

```c
OH_NNModel *OH_NNModel_Construct(void)
```

**Description**

Creates a model instance of the [OH_NNModel](capi-neuralnetworkruntime-oh-nnmodel.md) type and uses other APIs provided by OH_NNModel to construct the model instance.<br> Before composition, call [OH_NNModel_Construct](capi-neural-network-runtime-h.md#oh_nnmodel_construct) to create a model instance. Based on the model topology, call the [OH_NNModel_AddTensorToModel](capi-neural-network-runtime-h.md#oh_nnmodel_addtensortomodel), [OH_NNModel_AddOperation](capi-neural-network-runtime-h.md#oh_nnmodel_addoperation), and [OH_NNModel_SetTensorData](capi-neural-network-runtime-h.md#oh_nnmodel_settensordata) methods to fill in the data and operator nodes of the model, and then call [OH_NNModel_SpecifyInputsAndOutputs](capi-neural-network-runtime-h.md#oh_nnmodel_specifyinputsandoutputs) to specify the inputs and outputs of the model. After the model topology is constructed, call [OH_NNModel_Finish](capi-neural-network-runtime-h.md#oh_nnmodel_finish) to build the model. <br> After a model instance is no longer used, you need to destroy it by calling [OH_NNModel_Destroy](capi-neural-network-runtime-h.md#oh_nnmodel_destroy) to avoid memory leak.

**System capability**: SystemCapability.AI.NeuralNetworkRuntime

**Since**: 9

**Returns**:

| Type | Description |
| -- | -- |
| OH_NNModel * | Pointer to a [OH_NNModel](capi-neuralnetworkruntime-oh-nnmodel.md) instance, or NULL if it fails to create. |

### OH_NNModel_AddTensorToModel()

```c
OH_NN_ReturnCode OH_NNModel_AddTensorToModel(OH_NNModel *model, const NN_TensorDesc *tensorDesc)
```

**Description**

Adds a tensor to the model instance.<br> The data node and operator parameters in the Neural Network Runtime model are composed of tensors of the model. This method is used to add tensors to a model instance based on the <b>tensorDesc</b> parameter with type of [NN_TensorDesc](capi-neuralnetworkruntime-nn-tensordesc.md). [NN_TensorDesc](capi-neuralnetworkruntime-nn-tensordesc.md) contains some attributes such as shape, format, data type and provides corresponding APIs to access them. The order of adding tensors is specified by the indices recorded in the model. The [OH_NNModel_SetTensorData](capi-neural-network-runtime-h.md#oh_nnmodel_settensordata), [OH_NNModel_AddOperation](capi-neural-network-runtime-h.md#oh_nnmodel_addoperation), and [OH_NNModel_SpecifyInputsAndOutputs](capi-neural-network-runtime-h.md#oh_nnmodel_specifyinputsandoutputs) methods specify tensors based on the indices. <br> Neural Network Runtime supports inputs and outputs of the dynamic shape. When adding a data node with a dynamic shape, you need to set the dimensions that support dynamic changes to <b>-1</b>. For example, if the shape of a four-dimensional tensor is set to <b>[1, -1, 2, 2]</b>, the second dimension supports dynamic changes.

**System capability**: SystemCapability.AI.NeuralNetworkRuntime

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_NNModel *model | Pointer to the [OH_NNModel](capi-neuralnetworkruntime-oh-nnmodel.md) instance. |
| const NN_TensorDesc *tensorDesc | Pointer to the [NN_TensorDesc](capi-neuralnetworkruntime-nn-tensordesc.md) instance. The tensor descriptor specifies the attributes of the tensor added to the model instance. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_NN_ReturnCode | Execution result of the function. If the operation is successful, <b>OH_NN_SUCCESS</b> is returned. If the          operation fails, an error code is returned. For details about the error codes, see [OH_NN_ReturnCode](capi-neural-network-runtime-type-h.md#oh_nn_returncode). |

### OH_NNModel_SetTensorData()

```c
OH_NN_ReturnCode OH_NNModel_SetTensorData(OH_NNModel *model, uint32_t index, const void *dataBuffer, size_t length)
```

**Description**

Sets the tensor value.<br> For tensors with constant values (such as model weights), you need to use this method to set their data. The index of a tensor is determined by the order in which the tensor is added to the model. For details about how to add a tensor, see [OH_NNModel_AddTensorToModel](capi-neural-network-runtime-h.md#oh_nnmodel_addtensortomodel).

**System capability**: SystemCapability.AI.NeuralNetworkRuntime

**Since**: 9

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_NNModel *model | Pointer to the [OH_NNModel](capi-neuralnetworkruntime-oh-nnmodel.md) instance. |
| uint32_t index | Index of a tensor. |
| const void *dataBuffer | Pointer to real data. |
| size_t length | Length of the data buffer. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_NN_ReturnCode | Execution result of the function. If the operation is successful, <b>OH_NN_SUCCESS</b> is returned. If the          operation fails, an error code is returned. For details about the error codes, see [OH_NN_ReturnCode](capi-neural-network-runtime-type-h.md#oh_nn_returncode). |

### OH_NNModel_SetTensorQuantParams()

```c
OH_NN_ReturnCode OH_NNModel_SetTensorQuantParams(OH_NNModel *model, uint32_t index, NN_QuantParam *quantParam)
```

**Description**

Sets the quantization parameter of a tensor.

**System capability**: SystemCapability.AI.NeuralNetworkRuntime

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_NNModel *model | Pointer to the [OH_NNModel](capi-neuralnetworkruntime-oh-nnmodel.md) instance. |
| uint32_t index | Index of a tensor. |
| NN_QuantParam *quantParam | Pointer to the quantization parameter instance. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_NN_ReturnCode | Execution result of the function. If the operation is successful, <b>OH_NN_SUCCESS</b> is returned. If the          operation fails, an error code is returned. For details about the error codes, see [OH_NN_ReturnCode](capi-neural-network-runtime-type-h.md#oh_nn_returncode). |

### OH_NNModel_SetTensorType()

```c
OH_NN_ReturnCode OH_NNModel_SetTensorType(OH_NNModel *model, uint32_t index, OH_NN_TensorType tensorType)
```

**Description**

Sets the tensor type. See [OH_NN_TensorType](capi-neural-network-runtime-type-h.md#oh_nn_tensortype) for details.

**System capability**: SystemCapability.AI.NeuralNetworkRuntime

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_NNModel *model | Pointer to the [OH_NNModel](capi-neuralnetworkruntime-oh-nnmodel.md) instance. |
| uint32_t index | Index of a tensor. |
| OH_NN_TensorType tensorType | Tensor type of [OH_NN_TensorType](capi-neural-network-runtime-type-h.md#oh_nn_tensortype). |

**Returns**:

| Type | Description |
| -- | -- |
| OH_NN_ReturnCode | Execution result of the function. If the operation is successful, <b>OH_NN_SUCCESS</b> is returned. If the          operation fails, an error code is returned. For details about the error codes, see [OH_NN_ReturnCode](capi-neural-network-runtime-type-h.md#oh_nn_returncode). |

### OH_NNModel_AddOperation()

```c
OH_NN_ReturnCode OH_NNModel_AddOperation(OH_NNModel *model, OH_NN_OperationType op, const OH_NN_UInt32Array *paramIndices, const OH_NN_UInt32Array *inputIndices, const OH_NN_UInt32Array *outputIndices)
```

**Description**

Adds an operator to a model instance.<br> This method is used to add an operator to a model instance. The operator type is specified by <b>op</b>, and the operator parameters, inputs, and outputs are specified by <b>paramIndices</b>, <b>inputIndices</b>, and <b>outputIndices</b> respectively. This method verifies the attributes of operator parameters and the number of input and output parameters. These attributes must be correctly set when [OH_NNModel_AddTensorToModel](capi-neural-network-runtime-h.md#oh_nnmodel_addtensortomodel) is called to add tensors. For details about the expected parameters, input attributes, and output attributes of each operator, see [OH_NN_OperationType](capi-neural-network-runtime-type-h.md#oh_nn_operationtype). <br> <b>paramIndices</b>, <b>inputIndices</b>, and <b>outputIndices</b> store the indices of tensors. The indices are determined by the order in which tensors are added to the model. For details about how to add a tensor, see [OH_NNModel_AddTensorToModel](capi-neural-network-runtime-h.md#oh_nnmodel_addtensortomodel). <br> If unnecessary parameters are added when adding an operator, this method returns [OH_NN_INVALID_PARAMETER](capi-neural-network-runtime-type-h.md#oh_nn_returncode). If no operator parameter is set, the operator uses the default parameter value. For details about the default values, see [OH_NN_OperationType](capi-neural-network-runtime-type-h.md#oh_nn_operationtype).

**System capability**: SystemCapability.AI.NeuralNetworkRuntime

**Since**: 9

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_NNModel *model | Pointer to the [OH_NNModel](capi-neuralnetworkruntime-oh-nnmodel.md) instance. |
| OH_NN_OperationType op | Specifies the type of an operator to be added. For details, see the enumerated values of [OH_NN_OperationType](capi-neural-network-runtime-type-h.md#oh_nn_operationtype). |
| const OH_NN_UInt32Array *paramIndices | Pointer to the <b>OH_NN_UInt32Array</b> instance, which is used to set operator parameters. |
| const OH_NN_UInt32Array *inputIndices | Pointer to the <b>OH_NN_UInt32Array</b> instance, which is used to set the operator input. |
| const OH_NN_UInt32Array *outputIndices | Pointer to the <b>OH_NN_UInt32Array</b> instance, which is used to set the operator output. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_NN_ReturnCode | Execution result of the function. If the operation is successful, <b>OH_NN_SUCCESS</b> is returned. If the          operation fails, an error code is returned. For details about the error codes, see [OH_NN_ReturnCode](capi-neural-network-runtime-type-h.md#oh_nn_returncode). |

### OH_NNModel_SpecifyInputsAndOutputs()

```c
OH_NN_ReturnCode OH_NNModel_SpecifyInputsAndOutputs(OH_NNModel *model, const OH_NN_UInt32Array *inputIndices, const OH_NN_UInt32Array *outputIndices)
```

**Description**

Specifies the inputs and outputs of a model.<br> A tensor must be specified as the end-to-end inputs and outputs of a model instance. This type of tensor cannot be set using [OH_NNModel_SetTensorData](capi-neural-network-runtime-h.md#oh_nnmodel_settensordata). <br> The index of a tensor is determined by the order in which the tensor is added to the model. For details about how to add a tensor, see [OH_NNModel_AddTensorToModel](capi-neural-network-runtime-h.md#oh_nnmodel_addtensortomodel). <br> Currently, the model inputs and outputs cannot be set asynchronously.

**System capability**: SystemCapability.AI.NeuralNetworkRuntime

**Since**: 9

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_NNModel *model | Pointer to the [OH_NNModel](capi-neuralnetworkruntime-oh-nnmodel.md) instance. |
| const OH_NN_UInt32Array *inputIndices | Pointer to the <b>OH_NN_UInt32Array</b> instance, which is used to set the operator input. |
| const OH_NN_UInt32Array *outputIndices | Pointer to the <b>OH_NN_UInt32Array</b> instance, which is used to set the operator output. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_NN_ReturnCode | Execution result of the function. If the operation is successful, <b>OH_NN_SUCCESS</b> is returned. If the          operation fails, an error code is returned. For details about the error codes, see [OH_NN_ReturnCode](capi-neural-network-runtime-type-h.md#oh_nn_returncode). |

### OH_NNModel_Finish()

```c
OH_NN_ReturnCode OH_NNModel_Finish(OH_NNModel *model)
```

**Description**

Completes model composition.<br> After the model topology is set up, call this method to indicate that the composition is complete. After this method is called, additional composition operations cannot be performed. If [OH_NNModel_AddTensorToModel](capi-neural-network-runtime-h.md#oh_nnmodel_addtensortomodel), [OH_NNModel_AddOperation](capi-neural-network-runtime-h.md#oh_nnmodel_addoperation), [OH_NNModel_SetTensorData](capi-neural-network-runtime-h.md#oh_nnmodel_settensordata), and [OH_NNModel_SpecifyInputsAndOutputs](capi-neural-network-runtime-h.md#oh_nnmodel_specifyinputsandoutputs) are called, [OH_NN_OPERATION_FORBIDDEN](capi-neural-network-runtime-type-h.md#oh_nn_returncode) is returned. <br> Before calling [OH_NNModel_GetAvailableOperations](capi-neural-network-runtime-h.md#oh_nnmodel_getavailableoperations) and [OH_NNCompilation_Construct](capi-neural-network-core-h.md#oh_nncompilation_construct), you must call this method to complete composition.

**System capability**: SystemCapability.AI.NeuralNetworkRuntime

**Since**: 9

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_NNModel *model | Pointer to the [OH_NNModel](capi-neuralnetworkruntime-oh-nnmodel.md) instance. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_NN_ReturnCode | Execution result of the function. If the operation is successful, <b>OH_NN_SUCCESS</b> is returned. If the          operation fails, an error code is returned. For details about the error codes, see [OH_NN_ReturnCode](capi-neural-network-runtime-type-h.md#oh_nn_returncode). |

### OH_NNModel_Destroy()

```c
void OH_NNModel_Destroy(OH_NNModel **model)
```

**Description**

Releases a model instance.<br> This method needs to be called to release the model instance created by calling [OH_NNModel_Construct](capi-neural-network-runtime-h.md#oh_nnmodel_construct). Otherwise, memory leak will occur. <br> If <b>model</b> or <b>*model</b> is a null pointer, this method only prints warning logs and does not execute the release.

**System capability**: SystemCapability.AI.NeuralNetworkRuntime

**Since**: 9

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_NNModel **model | Double pointer to the [OH_NNModel](capi-neuralnetworkruntime-oh-nnmodel.md) instance. After a model instance is destroyed, this method sets <b>*model</b> to a null pointer. |

### OH_NNModel_GetAvailableOperations()

```c
OH_NN_ReturnCode OH_NNModel_GetAvailableOperations(OH_NNModel *model, size_t deviceID, const bool **isSupported, uint32_t *opCount)
```

**Description**

Queries whether the device supports operators in the model. The support status is indicated by the Boolean value.<br> Queries whether underlying device supports operators in a model instance. The device is specified by <b>deviceID</b>, and the result is represented by the array pointed by <b>isSupported</b>. If the <i>i</i>th operator is supported, the value of <b>(*isSupported)</b>[<i>i</i>] is <b>true</b>. Otherwise, the value is <b>false</b>. <br> After this method is successfully executed, <b>(*isSupported)</b> points to the bool array that records the operator support status. The operator quantity for the array length is the same as that for the model instance. The memory corresponding to this array is managed by Neural Network Runtime and is automatically destroyed after the model instance is destroyed or this method is called again.

**System capability**: SystemCapability.AI.NeuralNetworkRuntime

**Since**: 9

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_NNModel *model | Pointer to the [OH_NNModel](capi-neuralnetworkruntime-oh-nnmodel.md) instance. |
| size_t deviceID | Device ID to be queried, which can be obtained by using [OH_NNDevice_GetAllDevicesID](capi-neural-network-core-h.md#oh_nndevice_getalldevicesid). |
| const bool **isSupported | Pointer to the bool array. When this method is called, <b>(*isSupported)</b> must be a null pointer. Otherwise, [OH_NN_INVALID_PARAMETER](capi-neural-network-runtime-type-h.md#oh_nn_returncode) is returned. |
| uint32_t *opCount | Number of operators in a model instance, corresponding to the length of the <b>(*isSupported)</b> array. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_NN_ReturnCode | Execution result of the function. If the operation is successful, <b>OH_NN_SUCCESS</b> is returned. If the          operation fails, an error code is returned. For details about the error codes, see [OH_NN_ReturnCode](capi-neural-network-runtime-type-h.md#oh_nn_returncode). |

### OH_NNModel_AddTensor()

```c
OH_NN_ReturnCode OH_NNModel_AddTensor(OH_NNModel *model, const OH_NN_Tensor *tensor)
```

**Description**

Adds a tensor to a model instance.<br> The data node and operator parameters in the Neural Network Runtime model are composed of tensors of the model. This method is used to add tensors to a model instance based on the <b>tensor</b> parameter. The sequence of adding tensors is specified by the index value recorded in the model. The [OH_NNModel_SetTensorData](capi-neural-network-runtime-h.md#oh_nnmodel_settensordata), [OH_NNModel_AddOperation](capi-neural-network-runtime-h.md#oh_nnmodel_addoperation), and [OH_NNModel_SpecifyInputsAndOutputs](capi-neural-network-runtime-h.md#oh_nnmodel_specifyinputsandoutputs) methods specifies tensors based on the index value.<br> Neural Network Runtime supports inputs and outputs of the dynamic shape. When adding a data node with a dynamic shape, you need to set the dimensions that support dynamic changes in <b>tensor.dimensions</b> to <b>-1</b>. For example, if <b>tensor.dimensions</b> of a four-dimensional tensor is set to <b>[1, -1, 2, 2]</b>, the second dimension supports dynamic changes.

**System capability**: SystemCapability.AI.NeuralNetworkRuntime

**Since**: 9

**Deprecated**: 11

**Replaced by**: [OH_NNModel_AddTensorToModel](capi-neural-network-runtime-h.md#oh_nnmodel_addtensortomodel)

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_NNModel *model | Pointer to the [OH_NNModel](capi-neuralnetworkruntime-oh-nnmodel.md) instance. |
| const OH_NN_Tensor *tensor | Pointer to the [OH_NN_Tensor](capi-neuralnetworkruntime-oh-nn-tensor.md) tensor. The tensor specifies the attributes of the tensor added to the model instance. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_NN_ReturnCode | Execution result of the function. If the operation is successful, <b>OH_NN_SUCCESS</b> is returned.          If the operation fails, an error code is returned. For details about the error codes,          see [OH_NN_ReturnCode](capi-neural-network-runtime-type-h.md#oh_nn_returncode). |

### OH_NNExecutor_SetInput()

```c
OH_NN_ReturnCode OH_NNExecutor_SetInput(OH_NNExecutor *executor, uint32_t inputIndex, const OH_NN_Tensor *tensor, const void *dataBuffer, size_t length)
```

**Description**

Sets the single input data for a model.<br> This method copies the data whose length is specified by <b>length</b> (in bytes) in <b>dataBuffer</b> to the shared memory of the underlying device. <b>inputIndex</b> specifies the input to be set and <b>tensor</b> sets information such as the input shape, type, and quantization parameters.<br> Neural Network Runtime supports models with dynamical shape input. For fixed shape input and dynamic shape input scenarios, this method uses different processing policies.<br> - Fixed shape input: The attributes of <b>tensor</b> must be the same as those of the tensor added by calling [OH_NNModel_AddTensor](capi-neural-network-runtime-h.md#oh_nnmodel_addtensor) in the composition phase. - Dynamic shape input: In the composition phase, because the shape is not fixed, each value in <b>tensor.dimensions</b> must be greater than <b>0</b> in the method calls to determine the shape input in the calculation phase. When setting the shape, you can modify only the dimension whose value is <b>-1</b>. Assume that <b>[-1, 224, 224, 3]</b> is input as the the dimension of A in the composition phase. When this method is called, only the size of the first dimension can be modified, e.g. to <b>[3, 224, 224, 3]</b>. If other dimensions are adjusted, [OH_NN_INVALID_PARAMETER](capi-neural-network-runtime-type-h.md#oh_nn_returncode) is returned.

**System capability**: SystemCapability.AI.NeuralNetworkRuntime

**Since**: 9

**Deprecated**: 11

**Replaced by**: [OH_NNExecutor_RunSync](capi-neural-network-core-h.md#oh_nnexecutor_runsync)

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_NNExecutor *executor | Pointer to the [OH_NNExecutor](capi-neuralnetworkruntime-oh-nnexecutor.md) instance. |
| uint32_t inputIndex | Input index value, which is in the same sequence of the data input when [OH_NNModel_SpecifyInputsAndOutputs](capi-neural-network-runtime-h.md#oh_nnmodel_specifyinputsandoutputs) is called.<br>                  Assume that the value of <b>inputIndices</b> is <b>{1, 5, 9}</b> when<br>                  [OH_NNModel_SpecifyInputsAndOutputs](capi-neural-network-runtime-h.md#oh_nnmodel_specifyinputsandoutputs) is called. In input settings, the index value for the three inputs is <b>{0, 1, 2}</b>. |
| const OH_NN_Tensor *tensor | Sets the tensor corresponding to the input data. |
| const void *dataBuffer | Pointer to the input data. |
| size_t length | Length of the data buffer, in bytes. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_NN_ReturnCode | Execution result of the function. If the operation is successful, <b>OH_NN_SUCCESS</b> is returned.          If the operation fails, an error code is returned. For details about the error codes,          see [OH_NN_ReturnCode](capi-neural-network-runtime-type-h.md#oh_nn_returncode). |

### OH_NNExecutor_SetOutput()

```c
OH_NN_ReturnCode OH_NNExecutor_SetOutput(OH_NNExecutor *executor, uint32_t outputIndex, void *dataBuffer, size_t length)
```

**Description**

Sets the buffer for a single output of a model.<br> This method binds the buffer to which <b>dataBuffer</b> points to the output specified by <b>outputIndex</b>. The length of the buffer is specified by <b>length</b>.<br> After [OH_NNExecutor_Run](capi-neural-network-runtime-h.md#oh_nnexecutor_run) is called to complete a single model inference, Neural Network Runtime compares the length of the buffer to which <b>dataBuffer</b> points with the length of the output data and returns different results based on the actual situation.<br> - If the buffer length is greater than or equal to the data length, the inference result is copied to the buffer and [OH_NN_SUCCESS](capi-neural-network-runtime-type-h.md#oh_nn_returncode) is returned. You can read the inference result from <b>dataBuffer</b>. - If the buffer length is smaller than the data length, [OH_NNExecutor_Run](capi-neural-network-runtime-h.md#oh_nnexecutor_run) returns [OH_NN_INVALID_PARAMETER](capi-neural-network-runtime-type-h.md#oh_nn_returncode) and generates a log indicating that the buffer is too small.

**System capability**: SystemCapability.AI.NeuralNetworkRuntime

**Since**: 9

**Deprecated**: 11

**Replaced by**: [OH_NNExecutor_RunSync](capi-neural-network-core-h.md#oh_nnexecutor_runsync)

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_NNExecutor *executor | Pointer to the [OH_NNExecutor](capi-neuralnetworkruntime-oh-nnexecutor.md) instance. |
| uint32_t outputIndex | Output Index value, which is in the same sequence of the data output when [OH_NNModel_SpecifyInputsAndOutputs](capi-neural-network-runtime-h.md#oh_nnmodel_specifyinputsandoutputs) is called.<br>                   Assume that the value of <b>outputIndices</b> is <b>{4, 6, 8}</b> when<br>                   [OH_NNModel_SpecifyInputsAndOutputs](capi-neural-network-runtime-h.md#oh_nnmodel_specifyinputsandoutputs) is called. In output buffer settings, the index value for the three outputs is <b>{0, 1, 2}</b>. |
| void *dataBuffer | Pointer to the output data. |
| size_t length | Length of the data buffer, in bytes. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_NN_ReturnCode | Execution result of the function. If the operation is successful, <b>OH_NN_SUCCESS</b> is returned.          If the operation fails, an error code is returned. For details about the error codes,          see [OH_NN_ReturnCode](capi-neural-network-runtime-type-h.md#oh_nn_returncode). |

### OH_NNExecutor_Run()

```c
OH_NN_ReturnCode OH_NNExecutor_Run(OH_NNExecutor *executor)
```

**Description**

Performs inference.<br> Performs end-to-end inference and computing of the model on the device associated with the executor.

**System capability**: SystemCapability.AI.NeuralNetworkRuntime

**Since**: 9

**Deprecated**: 11

**Replaced by**: [OH_NNExecutor_RunSync](capi-neural-network-core-h.md#oh_nnexecutor_runsync)

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_NNExecutor *executor | Pointer to the [OH_NNExecutor](capi-neuralnetworkruntime-oh-nnexecutor.md) instance. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_NN_ReturnCode | Execution result of the function. If the operation is successful, <b>OH_NN_SUCCESS</b> is returned.          If the operation fails, an error code is returned. For details about the error codes,          see [OH_NN_ReturnCode](capi-neural-network-runtime-type-h.md#oh_nn_returncode). |

### OH_NNExecutor_AllocateInputMemory()

```c
OH_NN_Memory *OH_NNExecutor_AllocateInputMemory(OH_NNExecutor *executor, uint32_t inputIndex, size_t length)
```

**Description**

Allocates shared memory to a single input on a device.<br> Neural Network Runtime provides a method for proactively allocating shared memory on a device. By specifying the executor and input index value, this method allocates shared memory whose size is specified by <b>length</b> on the device associated with a single input and returns the operation result through the [OH_NN_Memory](capi-neuralnetworkruntime-oh-nn-memory.md) instance.

**System capability**: SystemCapability.AI.NeuralNetworkRuntime

**Since**: 9

**Deprecated**: 11

**Replaced by**: [OH_NNTensor_CreateWithSize](capi-neural-network-core-h.md#oh_nntensor_createwithsize)

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_NNExecutor *executor | Pointer to the [OH_NNExecutor](capi-neuralnetworkruntime-oh-nnexecutor.md) instance. |
| uint32_t inputIndex | Input index value, which is in the same sequence of the data input when [OH_NNModel_SpecifyInputsAndOutputs](capi-neural-network-runtime-h.md#oh_nnmodel_specifyinputsandoutputs) is called.<br>                  Assume that the value of <b>inputIndices</b> is <b>{1, 5, 9}</b> when<br>                  [OH_NNModel_SpecifyInputsAndOutputs](capi-neural-network-runtime-h.md#oh_nnmodel_specifyinputsandoutputs) is called. In the memory input application, the index value for the three inputs is <b>{0, 1, 2}</b>. |
| size_t length | Memory size to be applied for, in bytes. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_NN_Memory * | Pointer to a [OH_NN_Memory](capi-neuralnetworkruntime-oh-nn-memory.md) instance, or NULL if it fails to create. |

### OH_NNExecutor_AllocateOutputMemory()

```c
OH_NN_Memory *OH_NNExecutor_AllocateOutputMemory(OH_NNExecutor *executor, uint32_t outputIndex, size_t length)
```

**Description**

Allocates shared memory to a single output on a device.<br> Neural Network Runtime provides a method for proactively allocating shared memory on a device. By specifying the executor and output index value, this method allocates shared memory whose size is specified by <b>length</b> on the device associated with a single output and returns the operation result through the [OH_NN_Memory](capi-neuralnetworkruntime-oh-nn-memory.md) instance.

**System capability**: SystemCapability.AI.NeuralNetworkRuntime

**Since**: 9

**Deprecated**: 11

**Replaced by**: [OH_NNTensor_CreateWithSize](capi-neural-network-core-h.md#oh_nntensor_createwithsize)

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_NNExecutor *executor | Pointer to the [OH_NNExecutor](capi-neuralnetworkruntime-oh-nnexecutor.md) instance. |
| uint32_t outputIndex | Output Index value, which is in the same sequence of the data output when [OH_NNModel_SpecifyInputsAndOutputs](capi-neural-network-runtime-h.md#oh_nnmodel_specifyinputsandoutputs) is called.<br>                   Assume that the value of <b>outputIndices</b> is <b>{4, 6, 8}</b> when<br>                   [OH_NNModel_SpecifyInputsAndOutputs](capi-neural-network-runtime-h.md#oh_nnmodel_specifyinputsandoutputs) is called. In output memory application, the index value for the three outputs is <b>{0, 1, 2}</b>. |
| size_t length | Memory size to be applied for, in bytes. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_NN_Memory * | Pointer to a [OH_NN_Memory](capi-neuralnetworkruntime-oh-nn-memory.md) instance, or NULL if it fails to create. |

### OH_NNExecutor_DestroyInputMemory()

```c
void OH_NNExecutor_DestroyInputMemory(OH_NNExecutor *executor, uint32_t inputIndex, OH_NN_Memory **memory)
```

**Description**

Releases the input memory to which the [OH_NN_Memory](capi-neuralnetworkruntime-oh-nn-memory.md) instance points.<br> This method needs to be called to release the memory instance created by calling [OH_NNExecutor_AllocateInputMemory](capi-neural-network-runtime-h.md#oh_nnexecutor_allocateinputmemory). Otherwise, memory leak will occur. The mapping between <b>inputIndex</b> and <b>memory</b> must be the same as that in memory instance creation.<br> If <b>memory</b> or <b>*memory</b> is a null pointer, this method only prints warning logs and does not execute the release logic.

**System capability**: SystemCapability.AI.NeuralNetworkRuntime

**Since**: 9

**Deprecated**: 11

**Replaced by**: [OH_NNTensor_Destroy](capi-neural-network-core-h.md#oh_nntensor_destroy)

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_NNExecutor *executor | Pointer to the [OH_NNExecutor](capi-neuralnetworkruntime-oh-nnexecutor.md) instance. |
| uint32_t inputIndex | Input index value, which is in the same sequence of the data input when [OH_NNModel_SpecifyInputsAndOutputs](capi-neural-network-runtime-h.md#oh_nnmodel_specifyinputsandoutputs) is called.<br>                  Assume that the value of <b>inputIndices</b> is <b>{1, 5, 9}</b> when<br>                  [OH_NNModel_SpecifyInputsAndOutputs](capi-neural-network-runtime-h.md#oh_nnmodel_specifyinputsandoutputs) is called. In memory input release, the index value for the three inputs is <b>{0, 1, 2}</b>. |
| OH_NN_Memory **memory | Double pointer to the [OH_NN_Memory](capi-neuralnetworkruntime-oh-nn-memory.md) instance. After shared memory is destroyed, this method sets <b>*memory</b> to a null pointer. |

### OH_NNExecutor_DestroyOutputMemory()

```c
void OH_NNExecutor_DestroyOutputMemory(OH_NNExecutor *executor, uint32_t outputIndex, OH_NN_Memory **memory)
```

**Description**

Releases the output memory to which the [OH_NN_Memory](capi-neuralnetworkruntime-oh-nn-memory.md) instance points.<br> This method needs to be called to release the memory instance created by calling [OH_NNExecutor_AllocateOutputMemory](capi-neural-network-runtime-h.md#oh_nnexecutor_allocateoutputmemory). Otherwise, memory leak will occur. The mapping between <b>outputIndex</b> and <b>memory</b> must be the same as that in memory instance creation.<br> If <b>memory</b> or <b>*memory</b> is a null pointer, this method only prints warning logs and does not execute the release logic.

**System capability**: SystemCapability.AI.NeuralNetworkRuntime

**Since**: 9

**Deprecated**: 11

**Replaced by**: [OH_NNTensor_Destroy](capi-neural-network-core-h.md#oh_nntensor_destroy)

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_NNExecutor *executor | Pointer to the [OH_NNExecutor](capi-neuralnetworkruntime-oh-nnexecutor.md) instance. |
| uint32_t outputIndex | Output Index value, which is in the same sequence of the data output when [OH_NNModel_SpecifyInputsAndOutputs](capi-neural-network-runtime-h.md#oh_nnmodel_specifyinputsandoutputs) is called.<br>                   Assume that the value of <b>outputIndices</b> is <b>{4, 6, 8}</b> when<br>                   [OH_NNModel_SpecifyInputsAndOutputs](capi-neural-network-runtime-h.md#oh_nnmodel_specifyinputsandoutputs) is called. In output memory release, the index value for the three outputs is <b>{0, 1, 2}</b>. |
| OH_NN_Memory **memory | Double pointer to the [OH_NN_Memory](capi-neuralnetworkruntime-oh-nn-memory.md) instance. After shared memory is destroyed, this method sets <b>*memory</b> to a null pointer. |

### OH_NNExecutor_SetInputWithMemory()

```c
OH_NN_ReturnCode OH_NNExecutor_SetInputWithMemory(OH_NNExecutor *executor, uint32_t inputIndex, const OH_NN_Tensor *tensor, const OH_NN_Memory *memory)
```

**Description**

Specifies the hardware shared memory pointed to by the [OH_NN_Memory](capi-neuralnetworkruntime-oh-nn-memory.md) instance as the shared memory used by a single input.<br> In scenarios where memory needs to be managed by yourself, this method binds the execution input to the [OH_NN_Memory](capi-neuralnetworkruntime-oh-nn-memory.md) memory instance. During computing, the underlying device reads the input data from the shared memory pointed to by the memory instance. By using this method, concurrent execution of input setting, computing, and read can be implemented to improve inference efficiency of a data flow.

**System capability**: SystemCapability.AI.NeuralNetworkRuntime

**Since**: 9

**Deprecated**: 11

**Replaced by**: [OH_NNExecutor_RunSync](capi-neural-network-core-h.md#oh_nnexecutor_runsync)

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_NNExecutor *executor | Pointer to the [OH_NNExecutor](capi-neuralnetworkruntime-oh-nnexecutor.md) instance. |
| uint32_t inputIndex | Input index value, which is in the same sequence of the data input when [OH_NNModel_SpecifyInputsAndOutputs](capi-neural-network-runtime-h.md#oh_nnmodel_specifyinputsandoutputs) is called.<br>                  Assume that the value of <b>inputIndices</b> is <b>{1, 5, 9}</b> when<br>                  [OH_NNModel_SpecifyInputsAndOutputs](capi-neural-network-runtime-h.md#oh_nnmodel_specifyinputsandoutputs) is called. When the input shared memory is specified, the index value for the three inputs is <b>{0, 1, 2}</b>. |
| const OH_NN_Tensor *tensor | Pointer to [OH_NN_Tensor](capi-neuralnetworkruntime-oh-nn-tensor.md), used to set the tensor corresponding to a single input. |
| const OH_NN_Memory *memory | Pointer to [OH_NN_Memory](capi-neuralnetworkruntime-oh-nn-memory.md). |

**Returns**:

| Type | Description |
| -- | -- |
| OH_NN_ReturnCode | Execution result of the function. If the operation is successful, <b>OH_NN_SUCCESS</b> is returned.          If the operation fails, an error code is returned. For details about the error codes,          see [OH_NN_ReturnCode](capi-neural-network-runtime-type-h.md#oh_nn_returncode). |

### OH_NNExecutor_SetOutputWithMemory()

```c
OH_NN_ReturnCode OH_NNExecutor_SetOutputWithMemory(OH_NNExecutor *executor, uint32_t outputIndex, const OH_NN_Memory *memory)
```

**Description**

Specifies the hardware shared memory pointed to by the [OH_NN_Memory](capi-neuralnetworkruntime-oh-nn-memory.md) instance as the shared memory used by a single output.<br> In scenarios where memory needs to be managed by yourself, this method binds the execution output to the [OH_NN_Memory](capi-neuralnetworkruntime-oh-nn-memory.md) memory instance. When computing is performed, the underlying hardware directly writes the computing result to the shared memory to which the memory instance points. By using this method, concurrent execution of input setting, computing, and read can be implemented to improve inference efficiency of a data flow.

**System capability**: SystemCapability.AI.NeuralNetworkRuntime

**Since**: 9

**Deprecated**: 11

**Replaced by**: [OH_NNExecutor_RunSync](capi-neural-network-core-h.md#oh_nnexecutor_runsync)

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_NNExecutor *executor | Executor. |
| uint32_t outputIndex | Output Index value, which is in the same sequence of the data output when [OH_NNModel_SpecifyInputsAndOutputs](capi-neural-network-runtime-h.md#oh_nnmodel_specifyinputsandoutputs) is called.<br>                   Assume that the value of <b>outputIndices</b> is <b>{4, 6, 8}</b> when<br>                   [OH_NNModel_SpecifyInputsAndOutputs](capi-neural-network-runtime-h.md#oh_nnmodel_specifyinputsandoutputs) is called. When the output shared memory is specified, the index value for the three outputs is <b>{0, 1, 2}</b>. |
| const OH_NN_Memory *memory | Pointer to [OH_NN_Memory](capi-neuralnetworkruntime-oh-nn-memory.md). |

**Returns**:

| Type | Description |
| -- | -- |
| OH_NN_ReturnCode | Execution result of the function. If the operation is successful, <b>OH_NN_SUCCESS</b> is returned.          If the operation fails, an error code is returned. For details about the error codes,          see [OH_NN_ReturnCode](capi-neural-network-runtime-type-h.md#oh_nn_returncode). |


