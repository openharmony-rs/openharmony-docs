# model.h

## Overview

Provides model-related APIs for model creation and inference.

**Library**: libmindspore_lite_ndk.so

**Since**: 9

**Related module**: [MindSpore](capi-mindspore.md)

## Summary

### Struct

| Name | Description |
| -- | -- |
| [OH_AI_TensorHandleArray](capi-mindspore-oh-ai-tensorhandlearray.md) | Defines a pointer to a training configuration object. |
| [OH_AI_ShapeInfo](capi-mindspore-oh-ai-shapeinfo.md) |  |
| [OH_AI_CallBackParam](capi-mindspore-oh-ai-callbackparam.md) |  |

### Macro

| Name | Description |
| -- | -- |
| MINDSPORE_INCLUDE_C_API_MODEL_C_H | Provides model-related APIs for model creation and inference.<br>**Since**: 9 |

### Function

| Name | Description |
| -- | -- |
| [OH_AI_API OH_AI_ModelHandle OH_AI_ModelCreate(void)](#oh_ai_modelcreate) | Create a model object. |
| [OH_AI_API void OH_AI_ModelDestroy(OH_AI_ModelHandle *model)](#oh_ai_modeldestroy) | Destroy the model object. |
| [OH_AI_API OH_AI_Status OH_AI_ModelBuild(OH_AI_ModelHandle model, const void *model_data, size_t data_size, OH_AI_ModelType model_type, const OH_AI_ContextHandle model_context)](#oh_ai_modelbuild) | Build the model from model file buffer so that it can run on a device. |
| [OH_AI_API OH_AI_Status OH_AI_ModelBuildFromFile(OH_AI_ModelHandle model, const char *model_path, OH_AI_ModelType model_type, const OH_AI_ContextHandle model_context)](#oh_ai_modelbuildfromfile) | Load and build the model from model path so that it can run on a device. |
| [OH_AI_API OH_AI_Status OH_AI_ModelResize(OH_AI_ModelHandle model, const OH_AI_TensorHandleArray inputs, OH_AI_ShapeInfo *shape_infos, size_t shape_info_num)](#oh_ai_modelresize) | Resizes the shapes of inputs. |
| [OH_AI_API OH_AI_Status OH_AI_ModelPredict(OH_AI_ModelHandle model, const OH_AI_TensorHandleArray inputs, OH_AI_TensorHandleArray *outputs, const OH_AI_KernelCallBack before, const OH_AI_KernelCallBack after)](#oh_ai_modelpredict) | Inference model. |
| [OH_AI_API OH_AI_TensorHandleArray OH_AI_ModelGetInputs(const OH_AI_ModelHandle model)](#oh_ai_modelgetinputs) | Obtains all input tensor handles of the model. |
| [OH_AI_API OH_AI_TensorHandleArray OH_AI_ModelGetOutputs(const OH_AI_ModelHandle model)](#oh_ai_modelgetoutputs) | Obtains all output tensor handles of the model. |
| [OH_AI_API OH_AI_TensorHandle OH_AI_ModelGetInputByTensorName(const OH_AI_ModelHandle model, const char *tensor_name)](#oh_ai_modelgetinputbytensorname) | Obtains the input tensor handle of the model by name. |
| [OH_AI_API OH_AI_TensorHandle OH_AI_ModelGetOutputByTensorName(const OH_AI_ModelHandle model, const char *tensor_name)](#oh_ai_modelgetoutputbytensorname) | Obtains the output tensor handle of the model by name. |
| [OH_AI_API OH_AI_TrainCfgHandle OH_AI_TrainCfgCreate()](#oh_ai_traincfgcreate) | Create a TrainCfg object. Only valid for Lite Train. |
| [OH_AI_API void OH_AI_TrainCfgDestroy(OH_AI_TrainCfgHandle *train_cfg)](#oh_ai_traincfgdestroy) | Destroy the train_cfg object. Only valid for Lite Train. |
| [OH_AI_API char **OH_AI_TrainCfgGetLossName(OH_AI_TrainCfgHandle train_cfg, size_t *num)](#oh_ai_traincfggetlossname) | Obtains part of the name that identify a loss kernel. Only valid for Lite Train. |
| [OH_AI_API void OH_AI_TrainCfgSetLossName(OH_AI_TrainCfgHandle train_cfg, const char **loss_name, size_t num)](#oh_ai_traincfgsetlossname) | Set part of the name that identify a loss kernel. Only valid for Lite Train. |
| [OH_AI_API OH_AI_OptimizationLevel OH_AI_TrainCfgGetOptimizationLevel(OH_AI_TrainCfgHandle train_cfg)](#oh_ai_traincfggetoptimizationlevel) | Obtains optimization level of the train_cfg. Only valid for Lite Train. |
| [OH_AI_API void OH_AI_TrainCfgSetOptimizationLevel(OH_AI_TrainCfgHandle train_cfg, OH_AI_OptimizationLevel level)](#oh_ai_traincfgsetoptimizationlevel) | Set optimization level of the train_cfg. Only valid for Lite Train. |
| [OH_AI_API OH_AI_Status OH_AI_TrainModelBuild(OH_AI_ModelHandle model, const void *model_data, size_t data_size, OH_AI_ModelType model_type, const OH_AI_ContextHandle model_context, const OH_AI_TrainCfgHandle train_cfg)](#oh_ai_trainmodelbuild) | Build the train model from model buffer so that it can run on a device. Only valid for Lite Train. |
| [OH_AI_API OH_AI_Status OH_AI_TrainModelBuildFromFile(OH_AI_ModelHandle model, const char *model_path, OH_AI_ModelType model_type, const OH_AI_ContextHandle model_context, const OH_AI_TrainCfgHandle train_cfg)](#oh_ai_trainmodelbuildfromfile) | Build the train model from model file buffer so that it can run on a device. Only valid for Lite Train. |
| [OH_AI_API OH_AI_Status OH_AI_RunStep(OH_AI_ModelHandle model, const OH_AI_KernelCallBack before, const OH_AI_KernelCallBack after)](#oh_ai_runstep) | Train model by step. Only valid for Lite Train. |
| [OH_AI_API OH_AI_Status OH_AI_ModelSetLearningRate(OH_AI_ModelHandle model, float learning_rate)](#oh_ai_modelsetlearningrate) | Sets the Learning Rate of the training. Only valid for Lite Train. |
| [OH_AI_API float OH_AI_ModelGetLearningRate(OH_AI_ModelHandle model)](#oh_ai_modelgetlearningrate) | Obtains the Learning Rate of the optimizer. Only valid for Lite Train. |
| [OH_AI_API OH_AI_TensorHandleArray OH_AI_ModelGetWeights(OH_AI_ModelHandle model)](#oh_ai_modelgetweights) | Obtains all weights tensors of the model. Only valid for Lite Train. |
| [OH_AI_API OH_AI_Status OH_AI_ModelUpdateWeights(OH_AI_ModelHandle model, const OH_AI_TensorHandleArray new_weights)](#oh_ai_modelupdateweights) | update weights tensors of the model. Only valid for Lite Train. |
| [OH_AI_API bool OH_AI_ModelGetTrainMode(OH_AI_ModelHandle model)](#oh_ai_modelgettrainmode) | Get the model running mode. |
| [OH_AI_API OH_AI_Status OH_AI_ModelSetTrainMode(OH_AI_ModelHandle model, bool train)](#oh_ai_modelsettrainmode) | Set the model running mode. Only valid for Lite Train. |
| [OH_AI_API OH_AI_Status OH_AI_ModelSetupVirtualBatch(OH_AI_ModelHandle model, int virtual_batch_multiplier, float lr, float momentum)](#oh_ai_modelsetupvirtualbatch) | Setup training with virtual batches. Only valid for Lite Train. |
| [OH_AI_API OH_AI_Status OH_AI_ExportModel(OH_AI_ModelHandle model, OH_AI_ModelType model_type, const char *model_file, OH_AI_QuantizationType quantization_type, bool export_inference_only, char **output_tensor_name, size_t num)](#oh_ai_exportmodel) | Export training model from file. Only valid for Lite Train. |
| [OH_AI_API OH_AI_Status OH_AI_ExportModelBuffer(OH_AI_ModelHandle model, OH_AI_ModelType model_type, void *model_data, size_t *data_size, OH_AI_QuantizationType quantization_type, bool export_inference_only, char **output_tensor_name, size_t num)](#oh_ai_exportmodelbuffer) | Export training model from buffer. Only valid for Lite Train. |
| [OH_AI_API OH_AI_Status OH_AI_ExportWeightsCollaborateWithMicro(OH_AI_ModelHandle model, OH_AI_ModelType model_type, const char *weight_file, bool is_inference, bool enable_fp16, char **changeable_weights_name, size_t num)](#oh_ai_exportweightscollaboratewithmicro) | Export model's weights, which can be used in micro only. Only valid for Lite Train. |
| [OH_AI_API OH_AI_Status OH_AI_ModelLoadConfig(OH_AI_ModelHandle model, const char *config_path)](#oh_ai_modelloadconfig) | Load the config file of the model. |
| [OH_AI_API OH_AI_Status OH_AI_ModelPredictWithConfig(OH_AI_ModelHandle model, const OH_AI_TensorHandleArray inputs, OH_AI_TensorHandleArray *outputs, const char *config, const OH_AI_KernelCallBack before, const OH_AI_KernelCallBack after)](#oh_ai_modelpredictwithconfig) | Run model inference with configuration. |

### Variable

| Name | Description |
| -- | -- |
| void *OH_AI_TrainCfgHandle | Defines a pointer to a training configuration object.<br>**Since**: 11 |

## Function description

### OH_AI_ModelCreate()

```c
OH_AI_API OH_AI_ModelHandle OH_AI_ModelCreate(void)
```

**Description**

Create a model object.

**Since**: 9

**Returns**:

| Type | Description |
| -- | -- |
| OH_AI_API OH_AI_ModelHandle | Model object handle. |

### OH_AI_ModelDestroy()

```c
OH_AI_API void OH_AI_ModelDestroy(OH_AI_ModelHandle *model)
```

**Description**

Destroy the model object.

**Since**: 9

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AI_ModelHandle *model | Model object handle address. |

### OH_AI_ModelBuild()

```c
OH_AI_API OH_AI_Status OH_AI_ModelBuild(OH_AI_ModelHandle model, const void *model_data, size_t data_size, OH_AI_ModelType model_type, const OH_AI_ContextHandle model_context)
```

**Description**

Build the model from model file buffer so that it can run on a device.

**Since**: 9

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AI_ModelHandle model | Model object handle. |
| const void *model_data | Define the buffer read from a model file. |
| size_t data_size | Define bytes number of model file buffer. |
| OH_AI_ModelType model_type | Define The type of model file. |
| const OH_AI_ContextHandle model_context | Define the context used to store options during execution. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AI_API OH_AI_Status | OH_AI_Status. |

### OH_AI_ModelBuildFromFile()

```c
OH_AI_API OH_AI_Status OH_AI_ModelBuildFromFile(OH_AI_ModelHandle model, const char *model_path, OH_AI_ModelType model_type, const OH_AI_ContextHandle model_context)
```

**Description**

Load and build the model from model path so that it can run on a device.

**Since**: 9

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AI_ModelHandle model | Model object handle. |
| const char *model_path | Define the model file path. |
| OH_AI_ModelType model_type | Define The type of model file. |
| const OH_AI_ContextHandle model_context | Define the context used to store options during execution. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AI_API OH_AI_Status | OH_AI_Status. |

### OH_AI_ModelResize()

```c
OH_AI_API OH_AI_Status OH_AI_ModelResize(OH_AI_ModelHandle model, const OH_AI_TensorHandleArray inputs, OH_AI_ShapeInfo *shape_infos, size_t shape_info_num)
```

**Description**

Resizes the shapes of inputs.

**Since**: 9

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AI_ModelHandle model | Model object handle. |
| [const OH_AI_TensorHandleArray](capi-mindspore-oh-ai-tensorhandlearray.md) inputs | The array that includes all input tensor handles. |
| [OH_AI_ShapeInfo](capi-mindspore-oh-ai-shapeinfo.md) *shape_infos | Defines the new shapes of inputs, should be consistent with inputs. |
| size_t shape_info_num | The num of shape_infos. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AI_API OH_AI_Status | OH_AI_Status. |

### OH_AI_ModelPredict()

```c
OH_AI_API OH_AI_Status OH_AI_ModelPredict(OH_AI_ModelHandle model, const OH_AI_TensorHandleArray inputs, OH_AI_TensorHandleArray *outputs, const OH_AI_KernelCallBack before, const OH_AI_KernelCallBack after)
```

**Description**

Inference model.

**Since**: 9

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AI_ModelHandle model | Model object handle. |
| [const OH_AI_TensorHandleArray](capi-mindspore-oh-ai-tensorhandlearray.md) inputs | The array that includes all input tensor handles. |
| [OH_AI_TensorHandleArray](capi-mindspore-oh-ai-tensorhandlearray.md) *outputs | The array that includes all output tensor handles. |
| const OH_AI_KernelCallBack before | CallBack before predict. |
| const OH_AI_KernelCallBack after | CallBack after predict. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AI_API OH_AI_Status | OH_AI_Status. |

### OH_AI_ModelGetInputs()

```c
OH_AI_API OH_AI_TensorHandleArray OH_AI_ModelGetInputs(const OH_AI_ModelHandle model)
```

**Description**

Obtains all input tensor handles of the model.

**Since**: 9

**Parameters**:

| Parameter | Description |
| -- | -- |
| const OH_AI_ModelHandle model | Model object handle. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AI_API OH_AI_TensorHandleArray | The array that includes all input tensor handles. |

### OH_AI_ModelGetOutputs()

```c
OH_AI_API OH_AI_TensorHandleArray OH_AI_ModelGetOutputs(const OH_AI_ModelHandle model)
```

**Description**

Obtains all output tensor handles of the model.

**Since**: 9

**Parameters**:

| Parameter | Description |
| -- | -- |
| const OH_AI_ModelHandle model | Model object handle. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AI_API OH_AI_TensorHandleArray | The array that includes all output tensor handles. |

### OH_AI_ModelGetInputByTensorName()

```c
OH_AI_API OH_AI_TensorHandle OH_AI_ModelGetInputByTensorName(const OH_AI_ModelHandle model, const char *tensor_name)
```

**Description**

Obtains the input tensor handle of the model by name.

**Since**: 9

**Parameters**:

| Parameter | Description |
| -- | -- |
| const OH_AI_ModelHandle model | Model object handle. |
| const char *tensor_name | The name of tensor. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AI_API OH_AI_TensorHandle | The input tensor handle with the given name, if the name is not found, an NULL is returned. |

### OH_AI_ModelGetOutputByTensorName()

```c
OH_AI_API OH_AI_TensorHandle OH_AI_ModelGetOutputByTensorName(const OH_AI_ModelHandle model, const char *tensor_name)
```

**Description**

Obtains the output tensor handle of the model by name.

**Since**: 9

**Parameters**:

| Parameter | Description |
| -- | -- |
| const OH_AI_ModelHandle model | Model object handle. |
| const char *tensor_name | The name of tensor. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AI_API OH_AI_TensorHandle | The output tensor handle with the given name, if the name is not found, an NULL is returned. |

### OH_AI_TrainCfgCreate()

```c
OH_AI_API OH_AI_TrainCfgHandle OH_AI_TrainCfgCreate()
```

**Description**

Create a TrainCfg object. Only valid for Lite Train.

**Since**: 11

**Returns**:

| Type | Description |
| -- | -- |
| OH_AI_API OH_AI_TrainCfgHandle | TrainCfg object handle. |

### OH_AI_TrainCfgDestroy()

```c
OH_AI_API void OH_AI_TrainCfgDestroy(OH_AI_TrainCfgHandle *train_cfg)
```

**Description**

Destroy the train_cfg object. Only valid for Lite Train.

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AI_TrainCfgHandle *train_cfg | TrainCfg object handle. |

### OH_AI_TrainCfgGetLossName()

```c
OH_AI_API char **OH_AI_TrainCfgGetLossName(OH_AI_TrainCfgHandle train_cfg, size_t *num)
```

**Description**

Obtains part of the name that identify a loss kernel. Only valid for Lite Train.

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AI_TrainCfgHandle train_cfg | TrainCfg object handle. |
| size_t *num | The num of loss_name. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AI_API char ** | loss_name. |

### OH_AI_TrainCfgSetLossName()

```c
OH_AI_API void OH_AI_TrainCfgSetLossName(OH_AI_TrainCfgHandle train_cfg, const char **loss_name, size_t num)
```

**Description**

Set part of the name that identify a loss kernel. Only valid for Lite Train.

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AI_TrainCfgHandle train_cfg | TrainCfg object handle. |
| const char **loss_name | Define part of the name that identify a loss kernel. |
| size_t num | The num of loss_name. |

### OH_AI_TrainCfgGetOptimizationLevel()

```c
OH_AI_API OH_AI_OptimizationLevel OH_AI_TrainCfgGetOptimizationLevel(OH_AI_TrainCfgHandle train_cfg)
```

**Description**

Obtains optimization level of the train_cfg. Only valid for Lite Train.

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AI_TrainCfgHandle train_cfg | TrainCfg object handle. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AI_API OH_AI_OptimizationLevel | OH_AI_OptimizationLevel. |

### OH_AI_TrainCfgSetOptimizationLevel()

```c
OH_AI_API void OH_AI_TrainCfgSetOptimizationLevel(OH_AI_TrainCfgHandle train_cfg, OH_AI_OptimizationLevel level)
```

**Description**

Set optimization level of the train_cfg. Only valid for Lite Train.

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AI_TrainCfgHandle train_cfg | TrainCfg object handle. |
| OH_AI_OptimizationLevel level | The optimization level of train_cfg. |

### OH_AI_TrainModelBuild()

```c
OH_AI_API OH_AI_Status OH_AI_TrainModelBuild(OH_AI_ModelHandle model, const void *model_data, size_t data_size, OH_AI_ModelType model_type, const OH_AI_ContextHandle model_context, const OH_AI_TrainCfgHandle train_cfg)
```

**Description**

Build the train model from model buffer so that it can run on a device. Only valid for Lite Train.

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AI_ModelHandle model | Model object handle. |
| const void *model_data | Define the buffer read from a model file. |
| size_t data_size | Define bytes number of model file buffer. |
| OH_AI_ModelType model_type | Define The type of model file. |
| const OH_AI_ContextHandle model_context | Define the context used to store options during execution. |
| const OH_AI_TrainCfgHandle train_cfg | Define the config used by training. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AI_API OH_AI_Status | OH_AI_Status. |

### OH_AI_TrainModelBuildFromFile()

```c
OH_AI_API OH_AI_Status OH_AI_TrainModelBuildFromFile(OH_AI_ModelHandle model, const char *model_path, OH_AI_ModelType model_type, const OH_AI_ContextHandle model_context, const OH_AI_TrainCfgHandle train_cfg)
```

**Description**

Build the train model from model file buffer so that it can run on a device. Only valid for Lite Train.

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AI_ModelHandle model | Model object handle. |
| const char *model_path | Define the model path. |
| OH_AI_ModelType model_type | Define The type of model file. |
| const OH_AI_ContextHandle model_context | Define the context used to store options during execution. |
| const OH_AI_TrainCfgHandle train_cfg | Define the config used by training. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AI_API OH_AI_Status | OH_AI_Status. |

### OH_AI_RunStep()

```c
OH_AI_API OH_AI_Status OH_AI_RunStep(OH_AI_ModelHandle model, const OH_AI_KernelCallBack before, const OH_AI_KernelCallBack after)
```

**Description**

Train model by step. Only valid for Lite Train.

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AI_ModelHandle model | Model object handle. |
| const OH_AI_KernelCallBack before | CallBack before predict. |
| const OH_AI_KernelCallBack after | CallBack after predict. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AI_API OH_AI_Status | OH_AI_Status. |

### OH_AI_ModelSetLearningRate()

```c
OH_AI_API OH_AI_Status OH_AI_ModelSetLearningRate(OH_AI_ModelHandle model, float learning_rate)
```

**Description**

Sets the Learning Rate of the training. Only valid for Lite Train.

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| float learning_rate | to set. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AI_API OH_AI_Status | OH_AI_Status of operation. |

### OH_AI_ModelGetLearningRate()

```c
OH_AI_API float OH_AI_ModelGetLearningRate(OH_AI_ModelHandle model)
```

**Description**

Obtains the Learning Rate of the optimizer. Only valid for Lite Train.

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AI_ModelHandle model | Model object handle. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AI_API float | Learning rate. 0.0 if no optimizer was found. |

### OH_AI_ModelGetWeights()

```c
OH_AI_API OH_AI_TensorHandleArray OH_AI_ModelGetWeights(OH_AI_ModelHandle model)
```

**Description**

Obtains all weights tensors of the model. Only valid for Lite Train.

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AI_ModelHandle model | Model object handle. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AI_API OH_AI_TensorHandleArray | The vector that includes all gradient tensors. |

### OH_AI_ModelUpdateWeights()

```c
OH_AI_API OH_AI_Status OH_AI_ModelUpdateWeights(OH_AI_ModelHandle model, const OH_AI_TensorHandleArray new_weights)
```

**Description**

update weights tensors of the model. Only valid for Lite Train.

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| [const OH_AI_TensorHandleArray](capi-mindspore-oh-ai-tensorhandlearray.md) new_weights | A vector new weights. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AI_API OH_AI_Status | OH_AI_Status |

### OH_AI_ModelGetTrainMode()

```c
OH_AI_API bool OH_AI_ModelGetTrainMode(OH_AI_ModelHandle model)
```

**Description**

Get the model running mode.

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AI_ModelHandle model | Model object handle. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AI_API bool | Is Train Mode or not. |

### OH_AI_ModelSetTrainMode()

```c
OH_AI_API OH_AI_Status OH_AI_ModelSetTrainMode(OH_AI_ModelHandle model, bool train)
```

**Description**

Set the model running mode. Only valid for Lite Train.

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AI_ModelHandle model | Model object handle. |
| bool train | True means model runs in Train Mode, otherwise Eval Mode. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AI_API OH_AI_Status | OH_AI_Status. |

### OH_AI_ModelSetupVirtualBatch()

```c
OH_AI_API OH_AI_Status OH_AI_ModelSetupVirtualBatch(OH_AI_ModelHandle model, int virtual_batch_multiplier, float lr, float momentum)
```

**Description**

Setup training with virtual batches. Only valid for Lite Train.

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AI_ModelHandle model | Model object handle. |
| int virtual_batch_multiplier | Virtual batch multiplier, use any number < 1 to disable. |
| float lr | Learning rate to use for virtual batch, -1 for internal configuration. |
| float momentum | Batch norm momentum to use for virtual batch, -1 for internal configuration. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AI_API OH_AI_Status | OH_AI_Status. |

### OH_AI_ExportModel()

```c
OH_AI_API OH_AI_Status OH_AI_ExportModel(OH_AI_ModelHandle model, OH_AI_ModelType model_type, const char *model_file, OH_AI_QuantizationType quantization_type, bool export_inference_only, char **output_tensor_name, size_t num)
```

**Description**

Export training model from file. Only valid for Lite Train.

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AI_ModelHandle model | The model data. |
| OH_AI_ModelType model_type | The model file type. |
| const char *model_file | The exported model file. |
| OH_AI_QuantizationType quantization_type | The quantification type. |
| bool export_inference_only | Whether to export a reasoning only model. |
| char **output_tensor_name | The set the name of the output tensor of the exported reasoning model, default as empty, and export the complete reasoning model. |
| size_t num | The number of output_tensor_name. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AI_API OH_AI_Status | OH_AI_Status. |

### OH_AI_ExportModelBuffer()

```c
OH_AI_API OH_AI_Status OH_AI_ExportModelBuffer(OH_AI_ModelHandle model, OH_AI_ModelType model_type, void *model_data, size_t *data_size, OH_AI_QuantizationType quantization_type, bool export_inference_only, char **output_tensor_name, size_t num)
```

**Description**

Export training model from buffer. Only valid for Lite Train.

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AI_ModelHandle model | The model data. |
| OH_AI_ModelType model_type | The model file type. |
| void *model_data | The exported model buffer. |
| size_t *data_size | The exported model buffer size. |
| OH_AI_QuantizationType quantization_type | The quantification type. |
| bool export_inference_only | Whether to export a reasoning only model. |
| char **output_tensor_name | The set the name of the output tensor of the exported reasoning model, default as empty, and export the complete reasoning model. |
| size_t num | The number of output_tensor_name. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AI_API OH_AI_Status | OH_AI_Status. |

### OH_AI_ExportWeightsCollaborateWithMicro()

```c
OH_AI_API OH_AI_Status OH_AI_ExportWeightsCollaborateWithMicro(OH_AI_ModelHandle model, OH_AI_ModelType model_type, const char *weight_file, bool is_inference, bool enable_fp16, char **changeable_weights_name, size_t num)
```

**Description**

Export model's weights, which can be used in micro only. Only valid for Lite Train.

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AI_ModelHandle model | The model data. |
| OH_AI_ModelType model_type | The model file type. |
| const char *weight_file | The path of exported weight file. |
| bool is_inference | Whether to export weights from a reasoning model. Currently, only support this is `true`. |
| bool enable_fp16 | Float-weight is whether to be saved in float16 format. |
| char **changeable_weights_name | The set the name of these weight tensors, whose shape is changeable. |
| size_t num | The number of changeable_weights_name. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AI_API OH_AI_Status | OH_AI_Status. |

### OH_AI_ModelLoadConfig()

```c
OH_AI_API OH_AI_Status OH_AI_ModelLoadConfig(OH_AI_ModelHandle model, const char *config_path)
```

**Description**

Load the config file of the model.

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AI_ModelHandle model | Model object handle. |
| const char *config_path | The config file path. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AI_API OH_AI_Status | OH_AI_Status. |

### OH_AI_ModelPredictWithConfig()

```c
OH_AI_API OH_AI_Status OH_AI_ModelPredictWithConfig(OH_AI_ModelHandle model, const OH_AI_TensorHandleArray inputs, OH_AI_TensorHandleArray *outputs, const char *config, const OH_AI_KernelCallBack before, const OH_AI_KernelCallBack after)
```

**Description**

Run model inference with configuration.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AI_ModelHandle model | Model object handle. |
| [const OH_AI_TensorHandleArray](capi-mindspore-oh-ai-tensorhandlearray.md) inputs | The array that includes all input tensor handles. |
| [OH_AI_TensorHandleArray](capi-mindspore-oh-ai-tensorhandlearray.md) *outputs | The array that includes all output tensor handles. |
| const char *config | The config buffer of predition, as format of key-values. |
| const OH_AI_KernelCallBack before | CallBack before predict. |
| const OH_AI_KernelCallBack after | CallBack after predict. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AI_API OH_AI_Status | OH_AI_Status. |


