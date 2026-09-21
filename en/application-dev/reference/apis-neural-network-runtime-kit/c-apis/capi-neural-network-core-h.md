# neural_network_core.h

## Overview

Defines the Neural Network Core APIs. The AI inference framework uses the Native APIs provided by Neural Network Core to compile models and perform inference and computing on acceleration hardware.<br> Note: Currently, the APIs of Neural Network Core do not support multi-thread calling. <br> include "neural_network_runtime/neural_network_core.h"

**Library**: libneural_network_core.so

**System capability**: SystemCapability.AI.NeuralNetworkRuntime

**Since**: 9

**Related module**: [NeuralNetworkRuntime](capi-neuralnetworkruntime.md)

## Summary

### Function

| Name | Description |
| -- | -- |
| [OH_NNCompilation *OH_NNCompilation_Construct(const OH_NNModel *model)](#oh_nncompilation_construct) | Creates a compilation instance of the [OH_NNCompilation](capi-neuralnetworkruntime-oh-nncompilation.md) type.<br> After the OH_NNModel module completes model construction, APIs provided by the OH_NNCompilation module pass the model to underlying device for compilation. This method creates a [OH_NNCompilation](capi-neuralnetworkruntime-oh-nncompilation.md) instance based on the passed [OH_NNModel](capi-neuralnetworkruntime-oh-nnmodel.md) instance. The [OH_NNCompilation_SetDevice](capi-neural-network-core-h.md#oh_nncompilation_setdevice) method is called to set the device to compile on, and [OH_NNCompilation_Build](capi-neural-network-core-h.md#oh_nncompilation_build) is then called to complete compilation.<br> In addition to computing device selection, the OH_NNCompilation module supports features such as model caching, performance preference, priority setting, and float16 computing, which can be implemented by the following methods: [OH_NNCompilation_SetCache](capi-neural-network-core-h.md#oh_nncompilation_setcache) [OH_NNCompilation_SetPerformanceMode](capi-neural-network-core-h.md#oh_nncompilation_setperformancemode) [OH_NNCompilation_SetPriority](capi-neural-network-core-h.md#oh_nncompilation_setpriority) [OH_NNCompilation_EnableFloat16](capi-neural-network-core-h.md#oh_nncompilation_enablefloat16)<br> After [OH_NNCompilation_Build](capi-neural-network-core-h.md#oh_nncompilation_build) is called, the [OH_NNModel](capi-neuralnetworkruntime-oh-nnmodel.md) instance can be released. |
| [OH_NNCompilation *OH_NNCompilation_ConstructWithOfflineModelFile(const char *modelPath)](#oh_nncompilation_constructwithofflinemodelfile) | Creates a compilation instance based on an offline model file.<br> This method conflicts with the way of passing an online built model or an offline model file buffer, and you have to choose only one of the three construction methods. <br> Offline model is a type of model that is offline compiled by the model converter provided by a device vendor. So that the offline model can only be used on the specified device, but the compilation time of offline model is usually much less than [OH_NNModel](capi-neuralnetworkruntime-oh-nnmodel.md). <br> You should perform the offline compilation during your development and deploy the offline model in your app package. |
| [OH_NNCompilation *OH_NNCompilation_ConstructWithOfflineModelBuffer(const void *modelBuffer, size_t modelSize)](#oh_nncompilation_constructwithofflinemodelbuffer) | Creates a compilation instance based on an offline model file buffer.<br> This method conflicts with the way of passing an online built model or an offline model file path, and you have to choose only one of the three construction methods. <br> Note that the returned [OH_NNCompilation](capi-neuralnetworkruntime-oh-nncompilation.md) instance only saves the <b>modelBuffer</b> pointer inside, instead of copying its data. You should not release <b>modelBuffer</b> before the [OH_NNCompilation](capi-neuralnetworkruntime-oh-nncompilation.md) instance is destroied. |
| [OH_NNCompilation *OH_NNCompilation_ConstructForCache()](#oh_nncompilation_constructforcache) | Creates a empty compilation instance for restoration from cache later.<br> See [OH_NNCompilation_SetCache](capi-neural-network-core-h.md#oh_nncompilation_setcache) for the description of cache.<br> The restoration time from the cache is less than compilation with [OH_NNModel](capi-neuralnetworkruntime-oh-nnmodel.md).<br> You should call [OH_NNCompilation_SetCache](capi-neural-network-core-h.md#oh_nncompilation_setcache) or [OH_NNCompilation_ImportCacheFromBuffer](capi-neural-network-core-h.md#oh_nncompilation_importcachefrombuffer) first, and then call [OH_NNCompilation_Build](capi-neural-network-core-h.md#oh_nncompilation_build) to complete the restoration. |
| [OH_NN_ReturnCode OH_NNCompilation_ExportCacheToBuffer(OH_NNCompilation *compilation, const void *buffer, size_t length, size_t *modelSize)](#oh_nncompilation_exportcachetobuffer) | Exports the cache to a given buffer.<br> See [OH_NNCompilation_SetCache](capi-neural-network-core-h.md#oh_nncompilation_setcache) for the description of cache.<br> Note that the cache is the result of compilation building [OH_NNCompilation_Build](capi-neural-network-core-h.md#oh_nncompilation_build), so that this method must be called after [OH_NNCompilation_Build](capi-neural-network-core-h.md#oh_nncompilation_build). |
| [OH_NN_ReturnCode OH_NNCompilation_ImportCacheFromBuffer(OH_NNCompilation *compilation, const void *buffer, size_t modelSize)](#oh_nncompilation_importcachefrombuffer) | Imports the cache from a given buffer.<br> See [OH_NNCompilation_SetCache](capi-neural-network-core-h.md#oh_nncompilation_setcache) for the description of cache.<br> [OH_NNCompilation_Build](capi-neural-network-core-h.md#oh_nncompilation_build) should be called to complete the restoration after [OH_NNCompilation_ImportCacheFromBuffer](capi-neural-network-core-h.md#oh_nncompilation_importcachefrombuffer) is called.<br> Note that <b>compilation</b> only saves the <b>buffer</b> pointer inside, instead of copying its data. You should not release <b>buffer</b> before <b>compilation</b> is destroied. |
| [OH_NN_ReturnCode OH_NNCompilation_AddExtensionConfig(OH_NNCompilation *compilation, const char *configName, const void *configValue, const size_t configValueSize)](#oh_nncompilation_addextensionconfig) | Adds an extension config for a custom hardware attribute.<br> Some devices have their own specific attributes which have not been opened in NNRt. This method provides an additional way for you to set these custom hardware attributes of the device. You should query their names and values from the device vendor's documents, and add them into compilation instance one by one. These attributes will be passed directly to device driver, and this method will return error code if the driver cannot parse them. <br> After [OH_NNCompilation_Build](capi-neural-network-core-h.md#oh_nncompilation_build) is called, the <b>configName</b> and <b>configValue</b> can be released. |
| [OH_NN_ReturnCode OH_NNCompilation_SetDevice(OH_NNCompilation *compilation, size_t deviceID)](#oh_nncompilation_setdevice) | Specifies the device for model compilation and computing.<br> In the compilation phase, you need to specify the device for model compilation and computing. Call [OH_NNDevice_GetAllDevicesID](capi-neural-network-core-h.md#oh_nndevice_getalldevicesid) to obtain available device IDs. Call [OH_NNDevice_GetType](capi-neural-network-core-h.md#oh_nndevice_gettype) and [OH_NNDevice_GetName](capi-neural-network-core-h.md#oh_nndevice_getname) to obtain device information and pass target device ID to this method for setting. <br> * |
| [OH_NN_ReturnCode OH_NNCompilation_SetCache(OH_NNCompilation *compilation, const char *cachePath, uint32_t version)](#oh_nncompilation_setcache) | Set the cache directory and version of the compiled model.<br> On the device that supports caching, a model can be saved as a cache file after being compiled on the device driver. The model can be directly read from the cache file in the next compilation, saving recompilation time. This method performs different operations based on the passed cache directory and version: <br> - No file exists in the cache directory: Caches the compiled model to the directory and sets the cache version to <b>version</b>. <br> - A complete cache file exists in the cache directory, and its version is <b>version</b>: Reads the cache file in the path and passes the data to the underlying device for conversion into executable model instances. <br> - A complete cache file exists in the cache directory, and its version is earlier than <b>version</b>: When model compilation is complete on the underlying device, overwrites the cache file and changes the version number to <b>version</b>. <br> - A complete cache file exists in the cache directory, and its version is later than <b>version</b>: Returns the [OH_NN_INVALID_PARAMETER](capi-neural-network-runtime-type-h.md#oh_nn_returncode) error code without reading the cache file. <br> - The cache file in the cache directory is incomplete or you do not have the permission to access the cache file. Returns the [OH_NN_INVALID_FILE](capi-neural-network-runtime-type-h.md#oh_nn_returncode) error code. <br> - The cache directory does not exist or you do not have the access permission. Returns the [OH_NN_INVALID_PATH](capi-neural-network-runtime-type-h.md#oh_nn_returncode) error code. |
| [OH_NN_ReturnCode OH_NNCompilation_SetPerformanceMode(OH_NNCompilation *compilation, OH_NN_PerformanceMode performanceMode)](#oh_nncompilation_setperformancemode) | Sets the performance mode for model computing.<br> Allows you to set the performance mode for model computing to meet the requirements of low power consumption and ultimate performance. If this method is not called to set the performance mode in the compilation phase, the compilation instance assigns the [OH_NN_PERFORMANCE_NONE](capi-neural-network-runtime-type-h.md#oh_nn_performancemode) mode for the model by default. In this case, the device performs computing in the default performance mode. <br> If this method is called on the device that does not support the setting of the performance mode, the [OH_NN_UNAVALIDABLE_DEVICE](capi-neural-network-runtime-type-h.md#oh_nn_returncode) error code is returned. |
| [OH_NN_ReturnCode OH_NNCompilation_SetPriority(OH_NNCompilation *compilation, OH_NN_Priority priority)](#oh_nncompilation_setpriority) | Sets the model computing priority.<br> Allows you to set computing priorities for models. The priorities apply only to models created by the process with the same UID. The settings will not affect models created by processes with different UIDs on different devices. <br> If this method is called on the device that does not support the priority setting, the [OH_NN_UNAVALIDABLE_DEVICE](capi-neural-network-runtime-type-h.md#oh_nn_returncode) error code is returned. |
| [OH_NN_ReturnCode OH_NNCompilation_EnableFloat16(OH_NNCompilation *compilation, bool enableFloat16)](#oh_nncompilation_enablefloat16) | Enables float16 for computing.<br> Float32 is used by default for the model of float type. If this method is called on a device that supports float16, float16 will be used for computing the float32 model to reduce memory usage and execution time. <br> This option is useless for the model of int type, e.g. int8 type. <br> If this method is called on the device that does not support float16, the [OH_NN_UNAVALIDABLE_DEVICE](capi-neural-network-runtime-type-h.md#oh_nn_returncode) error code is returned. |
| [OH_NN_ReturnCode OH_NNCompilation_Build(OH_NNCompilation *compilation)](#oh_nncompilation_build) | Compiles a model.<br> After the compilation configuration is complete, call this method to return the compilation result. The compilation instance pushes the model and compilation options to the device for compilation. After this method is called, additional compilation operations cannot be performed. <br> If the [OH_NNCompilation_SetDevice](capi-neural-network-core-h.md#oh_nncompilation_setdevice), [OH_NNCompilation_SetCache](capi-neural-network-core-h.md#oh_nncompilation_setcache), [OH_NNCompilation_SetPerformanceMode](capi-neural-network-core-h.md#oh_nncompilation_setperformancemode), [OH_NNCompilation_SetPriority](capi-neural-network-core-h.md#oh_nncompilation_setpriority), and [OH_NNCompilation_EnableFloat16](capi-neural-network-core-h.md#oh_nncompilation_enablefloat16) methods are called, [OH_NN_OPERATION_FORBIDDEN](capi-neural-network-runtime-type-h.md#oh_nn_returncode) is returned. |
| [void OH_NNCompilation_Destroy(OH_NNCompilation **compilation)](#oh_nncompilation_destroy) | Releases the <b>Compilation</b> object.<br> This method needs to be called to release the compilation instance created by [OH_NNCompilation_Construct](capi-neural-network-core-h.md#oh_nncompilation_construct), [OH_NNCompilation_ConstructWithOfflineModelFile](capi-neural-network-core-h.md#oh_nncompilation_constructwithofflinemodelfile), [OH_NNCompilation_ConstructWithOfflineModelBuffer](capi-neural-network-core-h.md#oh_nncompilation_constructwithofflinemodelbuffer) and [OH_NNCompilation_ConstructForCache](capi-neural-network-core-h.md#oh_nncompilation_constructforcache). Otherwise, the memory leak will occur. <br> If <b>compilation</b> or <b>*compilation</b> is a null pointer, this method only prints warning logs and does not execute the release. |
| [NN_TensorDesc *OH_NNTensorDesc_Create()](#oh_nntensordesc_create) | Creates an [NN_TensorDesc](capi-neuralnetworkruntime-nn-tensordesc.md) instance.<br> The [NN_TensorDesc](capi-neuralnetworkruntime-nn-tensordesc.md) describes various tensor attributes, such as name/data type/shape/format, etc.<br> The following methods can be called to create a [NN_Tensor](capi-neuralnetworkruntime-nn-tensor.md) instance based on the passed [NN_TensorDesc](capi-neuralnetworkruntime-nn-tensordesc.md) instance: [OH_NNTensor_Create](capi-neural-network-core-h.md#oh_nntensor_create) [OH_NNTensor_CreateWithSize](capi-neural-network-core-h.md#oh_nntensor_createwithsize) [OH_NNTensor_CreateWithFd](capi-neural-network-core-h.md#oh_nntensor_createwithfd)<br> Note that these methods will copy the [NN_TensorDesc](capi-neuralnetworkruntime-nn-tensordesc.md) instance into [NN_Tensor](capi-neuralnetworkruntime-nn-tensor.md). Therefore you can create multiple [NN_Tensor](capi-neuralnetworkruntime-nn-tensor.md) instances with the same [NN_TensorDesc](capi-neuralnetworkruntime-nn-tensordesc.md) instance. And you should destroy the [NN_TensorDesc](capi-neuralnetworkruntime-nn-tensordesc.md) instance by [OH_NNTensorDesc_Destroy](capi-neural-network-core-h.md#oh_nntensordesc_destroy) when it is no longer used. |
| [OH_NN_ReturnCode OH_NNTensorDesc_Destroy(NN_TensorDesc **tensorDesc)](#oh_nntensordesc_destroy) | Releases an [NN_TensorDesc](capi-neuralnetworkruntime-nn-tensordesc.md) instance.<br> When the [NN_TensorDesc](capi-neuralnetworkruntime-nn-tensordesc.md) instance is no longer used, this method needs to be called to release it. Otherwise, the memory leak will occur. <br> If <b>tensorDesc</b> or <b>*tensorDesc</b> is a null pointer, this method will return error code and does not execute the release. |
| [OH_NN_ReturnCode OH_NNTensorDesc_SetName(NN_TensorDesc *tensorDesc, const char *name)](#oh_nntensordesc_setname) | Sets the name of a [NN_TensorDesc](capi-neuralnetworkruntime-nn-tensordesc.md).<br> After the [NN_TensorDesc](capi-neuralnetworkruntime-nn-tensordesc.md) instance is created, call this method to set the tensor name. The value of <b>*name</b> is a C-style string ended with <b>'\0'</b>.<br> if <b>tensorDesc</b> or <b>name</b> is a null pointer, this method will return error code. |
| [OH_NN_ReturnCode OH_NNTensorDesc_GetName(const NN_TensorDesc *tensorDesc, const char **name)](#oh_nntensordesc_getname) | Gets the name of a [NN_TensorDesc](capi-neuralnetworkruntime-nn-tensordesc.md).<br> Call this method to obtain the name of the specified [NN_TensorDesc](capi-neuralnetworkruntime-nn-tensordesc.md) instance. The value of <b>*name</b> is a C-style string ended with <b>'\0'</b>.<br> if <b>tensorDesc</b> or <b>name</b> is a null pointer, this method will return error code. As an output parameter, <b>*name</b> must be a null pointer, otherwise the method will return an error code. Fou example, you should define char* tensorName = NULL, and pass &tensorName as the argument of <b>name</b>.<br> You do not need to release the memory of <b>name</b>. It will be released when <b>tensorDesc</b> is destroied. |
| [OH_NN_ReturnCode OH_NNTensorDesc_SetDataType(NN_TensorDesc *tensorDesc, OH_NN_DataType dataType)](#oh_nntensordesc_setdatatype) | Sets the data type of a [NN_TensorDesc](capi-neuralnetworkruntime-nn-tensordesc.md).<br> After the [NN_TensorDesc](capi-neuralnetworkruntime-nn-tensordesc.md) instance is created, call this method to set the tensor data type. <br> if <b>tensorDesc</b> is a null pointer, this method will return error code. |
| [OH_NN_ReturnCode OH_NNTensorDesc_GetDataType(const NN_TensorDesc *tensorDesc, OH_NN_DataType *dataType)](#oh_nntensordesc_getdatatype) | Gets the data type of a [NN_TensorDesc](capi-neuralnetworkruntime-nn-tensordesc.md).<br> Call this method to obtain the data type of the specified [NN_TensorDesc](capi-neuralnetworkruntime-nn-tensordesc.md) instance. <br> if <b>tensorDesc</b> or <b>dataType</b> is a null pointer, this method will return error code. |
| [OH_NN_ReturnCode OH_NNTensorDesc_SetShape(NN_TensorDesc *tensorDesc, const int32_t *shape, size_t shapeLength)](#oh_nntensordesc_setshape) | Sets the shape of a [NN_TensorDesc](capi-neuralnetworkruntime-nn-tensordesc.md).<br> After the [NN_TensorDesc](capi-neuralnetworkruntime-nn-tensordesc.md) instance is created, call this method to set the tensor shape. <br> if <b>tensorDesc</b> or <b>shape</b> is a null pointer, or <b>shapeLength</b> is 0, this method will return error code. |
| [OH_NN_ReturnCode OH_NNTensorDesc_GetShape(const NN_TensorDesc *tensorDesc, int32_t **shape, size_t *shapeLength)](#oh_nntensordesc_getshape) | Gets the shape of a [NN_TensorDesc](capi-neuralnetworkruntime-nn-tensordesc.md).<br> Call this method to obtain the shape of the specified [NN_TensorDesc](capi-neuralnetworkruntime-nn-tensordesc.md) instance. <br> if <b>tensorDesc</b>, <b>shape</b> or <b>shapeLength</b> is a null pointer, this method will return error code. As an output parameter, <b>*shape</b> must be a null pointer, otherwise the method will return an error code. Fou example, you should define int32_t* tensorShape = NULL, and pass &tensorShape as the argument of <b>shape</b>. <br> You do not need to release the memory of <b>shape</b>. It will be released when <b>tensorDesc</b> is destroied. |
| [OH_NN_ReturnCode OH_NNTensorDesc_SetFormat(NN_TensorDesc *tensorDesc, OH_NN_Format format)](#oh_nntensordesc_setformat) | Sets the format of a [NN_TensorDesc](capi-neuralnetworkruntime-nn-tensordesc.md).<br> After the [NN_TensorDesc](capi-neuralnetworkruntime-nn-tensordesc.md) instance is created, call this method to set the tensor format. <br> if <b>tensorDesc</b> is a null pointer, this method will return error code. |
| [OH_NN_ReturnCode OH_NNTensorDesc_GetFormat(const NN_TensorDesc *tensorDesc, OH_NN_Format *format)](#oh_nntensordesc_getformat) | Gets the format of a [NN_TensorDesc](capi-neuralnetworkruntime-nn-tensordesc.md).<br> Call this method to obtain the format of the specified [NN_TensorDesc](capi-neuralnetworkruntime-nn-tensordesc.md) instance. <br> if <b>tensorDesc</b> or <b>format</b> is a null pointer, this method will return error code. |
| [OH_NN_ReturnCode OH_NNTensorDesc_GetElementCount(const NN_TensorDesc *tensorDesc, size_t *elementCount)](#oh_nntensordesc_getelementcount) | Gets the element count of a [NN_TensorDesc](capi-neuralnetworkruntime-nn-tensordesc.md).<br> Call this method to obtain the element count of the specified [NN_TensorDesc](capi-neuralnetworkruntime-nn-tensordesc.md) instance. If you need to obtain byte size of the tensor data, call [OH_NNTensorDesc_GetByteSize](capi-neural-network-core-h.md#oh_nntensordesc_getbytesize). <br> If the tensor shape is dynamic, this method will return error code, and <b>elementCount</b> will be 0. <br> if <b>tensorDesc</b> or <b>elementCount</b> is a null pointer, this method will return error code. |
| [OH_NN_ReturnCode OH_NNTensorDesc_GetByteSize(const NN_TensorDesc *tensorDesc, size_t *byteSize)](#oh_nntensordesc_getbytesize) | Gets the byte size of a [NN_TensorDesc](capi-neuralnetworkruntime-nn-tensordesc.md).<br> Call this method to obtain the byte size of the specified [NN_TensorDesc](capi-neuralnetworkruntime-nn-tensordesc.md) instance. <br> If the tensor shape is dynamic, this method will return error code, and <b>byteSize</b> will be 0. <br> If you need to obtain element count of the tensor data, call [OH_NNTensorDesc_GetElementCount](capi-neural-network-core-h.md#oh_nntensordesc_getelementcount). <br> if <b>tensorDesc</b> or <b>byteSize</b> is a null pointer, this method will return error code. |
| [NN_Tensor *OH_NNTensor_Create(size_t deviceID, NN_TensorDesc *tensorDesc)](#oh_nntensor_create) | Creates a [NN_Tensor](capi-neuralnetworkruntime-nn-tensor.md) instance from [NN_TensorDesc](capi-neuralnetworkruntime-nn-tensordesc.md).<br> This method use [OH_NNTensorDesc_GetByteSize](capi-neural-network-core-h.md#oh_nntensordesc_getbytesize) to calculate the byte size of tensor data and allocate shared memory on device for it. The device dirver will get the tensor data directly by the "zero-copy" way.<br> Note that this method will copy the <b>tensorDesc</b> into [NN_Tensor](capi-neuralnetworkruntime-nn-tensor.md). Therefore you should destroy <b>tensorDesc</b> by [OH_NNTensorDesc_Destroy](capi-neural-network-core-h.md#oh_nntensordesc_destroy) if it is no longer used.<br> If the tensor shape is dynamic, this method will return error code.<br> <b>deviceID</b> indicates the selected device. If it is 0, the first device in the current device list will be used by default.<br> <b>tensorDesc</b> must be provided, and this method will return an error code if it is a null pointer.<br> Call [OH_NNTensor_Destroy](capi-neural-network-core-h.md#oh_nntensor_destroy) to release the [NN_Tensor](capi-neuralnetworkruntime-nn-tensor.md) instance if it is no longer used. |
| [NN_Tensor *OH_NNTensor_CreateWithSize(size_t deviceID, NN_TensorDesc *tensorDesc, size_t size)](#oh_nntensor_createwithsize) | Creates a [NN_Tensor](capi-neuralnetworkruntime-nn-tensor.md) instance with specified size and [NN_TensorDesc](capi-neuralnetworkruntime-nn-tensordesc.md).<br> This method use <b>size</b> as the byte size of tensor data and allocate shared memory on device for it. The device dirver will get the tensor data directly by the "zero-copy" way.<br> Note that this method will copy the <b>tensorDesc</b> into [NN_Tensor](capi-neuralnetworkruntime-nn-tensor.md). Therefore you should destroy <b>tensorDesc</b> by [OH_NNTensorDesc_Destroy](capi-neural-network-core-h.md#oh_nntensordesc_destroy) if it is no longer used.<br> <b>deviceID</b> indicates the selected device. If it is 0, the first device in the current device list will be used by default.<br> <b>tensorDesc</b> must be provided, if it is a null pointer, the method returns an error code. <b>size</b> must be no less than the byte size of tensorDesc. Otherwise, this method will return an error code. If the tensor shape is dynamic, the <b>size</b> will not be checked.<br> Call [OH_NNTensor_Destroy](capi-neural-network-core-h.md#oh_nntensor_destroy) to release the [NN_Tensor](capi-neuralnetworkruntime-nn-tensor.md) instance if it is no longer used. |
| [NN_Tensor *OH_NNTensor_CreateWithFd(size_t deviceID, NN_TensorDesc *tensorDesc, int fd, size_t size, size_t offset)](#oh_nntensor_createwithfd) | Creates a [NN_Tensor](capi-neuralnetworkruntime-nn-tensor.md) instance with specified file descriptor and [NN_TensorDesc](capi-neuralnetworkruntime-nn-tensordesc.md).<br> This method reuses the shared memory corresponding to the file descriptor <b>fd</b> passed. It may comes from another [NN_Tensor](capi-neuralnetworkruntime-nn-tensor.md) instance. When you call the [OH_NNTensor_Destroy](capi-neural-network-core-h.md#oh_nntensor_destroy) method to release the tensor created by this method, the tensor data memory will not be released.<br> Note that this method will copy the <b>tensorDesc</b> into [NN_Tensor](capi-neuralnetworkruntime-nn-tensor.md). Therefore you should destroy <b>tensorDesc</b> by [OH_NNTensorDesc_Destroy](capi-neural-network-core-h.md#oh_nntensordesc_destroy) if it is no longer used.<br> <b>deviceID</b> indicates the selected device. If it is 0, the first device in the current device list will be used by default.<br> <b>tensorDesc</b> must be provided, if it is a null pointer, the method returns an error code.<br> Call [OH_NNTensor_Destroy](capi-neural-network-core-h.md#oh_nntensor_destroy) to release the [NN_Tensor](capi-neuralnetworkruntime-nn-tensor.md) instance if it is no longer used. |
| [OH_NN_ReturnCode OH_NNTensor_Destroy(NN_Tensor **tensor)](#oh_nntensor_destroy) | Releases a [NN_Tensor](capi-neuralnetworkruntime-nn-tensor.md) instance.<br> When the [NN_Tensor](capi-neuralnetworkruntime-nn-tensor.md) instance is no longer used, this method needs to be called to release the instance. Otherwise, the memory leak will occur.<br> If <b>tensor</b> or <b>*tensor</b> is a null pointer, this method will return error code and does not execute the release. |
| [NN_TensorDesc *OH_NNTensor_GetTensorDesc(const NN_Tensor *tensor)](#oh_nntensor_gettensordesc) | Gets the [NN_TensorDesc](capi-neuralnetworkruntime-nn-tensordesc.md) instance of a [NN_Tensor](capi-neuralnetworkruntime-nn-tensor.md).<br> Call this method to obtain the inner [NN_TensorDesc](capi-neuralnetworkruntime-nn-tensordesc.md) instance pointer of the specified [NN_Tensor](capi-neuralnetworkruntime-nn-tensor.md) instance. You can get various types of the tensor attributes such as name/format/data type/shape from the returned [NN_TensorDesc](capi-neuralnetworkruntime-nn-tensordesc.md) instance.<br> You should not destory the returned [NN_TensorDesc](capi-neuralnetworkruntime-nn-tensordesc.md) instance because it points to the inner instance of [NN_Tensor](capi-neuralnetworkruntime-nn-tensor.md). Otherwise, a menory corruption of double free will occur when [OH_NNTensor_Destroy](capi-neural-network-core-h.md#oh_nntensor_destroy) is called.<br> if <b>tensor</b> is a null pointer, this method will return null pointer. |
| [void *OH_NNTensor_GetDataBuffer(const NN_Tensor *tensor)](#oh_nntensor_getdatabuffer) | Gets the data buffer of a [NN_Tensor](capi-neuralnetworkruntime-nn-tensor.md).<br> You can read/write data from/to the tensor data buffer. The buffer is mapped from a shared memory on device, so the device dirver will get the tensor data directly by this "zero-copy" way.<br> Note that the real tensor data only uses the segment [offset, size) of the shared memory. The offset can be got by [OH_NNTensor_GetOffset](capi-neural-network-core-h.md#oh_nntensor_getoffset) and the size can be got by [OH_NNTensor_GetSize](capi-neural-network-core-h.md#oh_nntensor_getsize).<br> if <b>tensor</b> is a null pointer, this method will return null pointer. |
| [OH_NN_ReturnCode OH_NNTensor_GetFd(const NN_Tensor *tensor, int *fd)](#oh_nntensor_getfd) | Gets the file descriptor of the shared memory of a [NN_Tensor](capi-neuralnetworkruntime-nn-tensor.md).<br> The file descriptor <b>fd</b> corresponds to the shared memory of the tensor data, and can be resued by another [NN_Tensor](capi-neuralnetworkruntime-nn-tensor.md) through [OH_NNTensor_CreateWithFd](capi-neural-network-core-h.md#oh_nntensor_createwithfd).<br> if <b>tensor</b> or <b>fd</b> is a null pointer, this method will return error code. |
| [OH_NN_ReturnCode OH_NNTensor_GetSize(const NN_Tensor *tensor, size_t *size)](#oh_nntensor_getsize) | Gets the size of the shared memory of a [NN_Tensor](capi-neuralnetworkruntime-nn-tensor.md).<br> The <b>size</b> corresponds to the shared memory of the tensor data, and can be resued by another [NN_Tensor](capi-neuralnetworkruntime-nn-tensor.md) through [OH_NNTensor_CreateWithFd](capi-neural-network-core-h.md#oh_nntensor_createwithfd).<br> The <b>size</b> is as same as the argument <b>size</b> of [OH_NNTensor_CreateWithSize](capi-neural-network-core-h.md#oh_nntensor_createwithsize) and [OH_NNTensor_CreateWithFd](capi-neural-network-core-h.md#oh_nntensor_createwithfd). But for a tensor created by [OH_NNTensor_Create](capi-neural-network-core-h.md#oh_nntensor_create), it equals to the tensor byte size.<br> Note that the real tensor data only uses the segment [offset, size) of the shared memory. The offset can be got by [OH_NNTensor_GetOffset](capi-neural-network-core-h.md#oh_nntensor_getoffset) and the size can be got by [OH_NNTensor_GetSize](capi-neural-network-core-h.md#oh_nntensor_getsize).<br> if <b>tensor</b> or <b>size</b> is a null pointer, this method will return error code. |
| [OH_NN_ReturnCode OH_NNTensor_GetOffset(const NN_Tensor *tensor, size_t *offset)](#oh_nntensor_getoffset) | Get the data offset of a tensor.<br> The <b>offset</b> corresponds to the shared memory of the tensor data, and can be resued by another [NN_Tensor](capi-neuralnetworkruntime-nn-tensor.md) through [OH_NNTensor_CreateWithFd](capi-neural-network-core-h.md#oh_nntensor_createwithfd).<br> Note that the real tensor data only uses the segment [offset, size) of the shared memory. The offset can be got by [OH_NNTensor_GetOffset](capi-neural-network-core-h.md#oh_nntensor_getoffset) and the size can be got by [OH_NNTensor_GetSize](capi-neural-network-core-h.md#oh_nntensor_getsize).<br> if <b>tensor</b> or <b>offset</b> is a null pointer, this method will return error code. |
| [OH_NNExecutor *OH_NNExecutor_Construct(OH_NNCompilation *compilation)](#oh_nnexecutor_construct) | Creates an executor instance of the [OH_NNExecutor](capi-neuralnetworkruntime-oh-nnexecutor.md) type.<br> This method constructs a model inference executor associated with the device based on the passed compilation. <br> After the [OH_NNExecutor](capi-neuralnetworkruntime-oh-nnexecutor.md) instance is created, you can release the [OH_NNCompilation](capi-neuralnetworkruntime-oh-nncompilation.md) instance if you do not need to create any other executors. |
| [OH_NN_ReturnCode OH_NNExecutor_GetOutputShape(OH_NNExecutor *executor, uint32_t outputIndex, int32_t **shape, uint32_t *shapeLength)](#oh_nnexecutor_getoutputshape) | Obtains the dimension information about the output tensor.<br> After [OH_NNExecutor_Run](capi-neural-network-runtime-h.md#oh_nnexecutor_run) is called to complete a single inference, call this method to obtain the specified output dimension information and number of dimensions. It is commonly used in dynamic shape input and output scenarios.<br> If the <b>outputIndex</b> is greater than or equal to the output tensor number, this method will return error code. The output tensor number can be got by [OH_NNExecutor_GetOutputCount](capi-neural-network-core-h.md#oh_nnexecutor_getoutputcount).<br> As an output parameter, <b>*shape</b> must be a null pointer, otherwise the method will return an error code. Fou example, you should define int32_t* tensorShape = NULL, and pass &tensorShape as the argument of <b>shape</b>.<br> You do not need to release the memory of <b>shape</b>. It will be released when <b>executor</b> is destroied. |
| [void OH_NNExecutor_Destroy(OH_NNExecutor **executor)](#oh_nnexecutor_destroy) | Destroys an executor instance to release the memory occupied by the executor.<br> This method needs to be called to release the executor instance created by calling [OH_NNExecutor_Construct](capi-neural-network-core-h.md#oh_nnexecutor_construct). Otherwise, the memory leak will occur. <br> If <b>executor</b> or <b>*executor</b> is a null pointer, this method only prints warning logs and does not execute the release. |
| [OH_NN_ReturnCode OH_NNExecutor_GetInputCount(const OH_NNExecutor *executor, size_t *inputCount)](#oh_nnexecutor_getinputcount) | Gets the input tensor count.<br> You can get the input tensor count from the executor, and then create an input tensor descriptor with its index by [OH_NNExecutor_CreateInputTensorDesc](capi-neural-network-core-h.md#oh_nnexecutor_createinputtensordesc). |
| [OH_NN_ReturnCode OH_NNExecutor_GetOutputCount(const OH_NNExecutor *executor, size_t *outputCount)](#oh_nnexecutor_getoutputcount) | Gets the output tensor count.<br> You can get the output tensor count from the executor, and then create an output tensor descriptor with its index by [OH_NNExecutor_CreateOutputTensorDesc](capi-neural-network-core-h.md#oh_nnexecutor_createoutputtensordesc). |
| [NN_TensorDesc *OH_NNExecutor_CreateInputTensorDesc(const OH_NNExecutor *executor, size_t index)](#oh_nnexecutor_createinputtensordesc) | Creates an input tensor descriptor with its index.<br> The input tensor descriptor contains all attributes of the input tensor. If the <b>index</b> is greater than or equal to the input tensor number, this method will return error code. The input tensor number can be got by [OH_NNExecutor_GetInputCount](capi-neural-network-core-h.md#oh_nnexecutor_getinputcount). |
| [NN_TensorDesc *OH_NNExecutor_CreateOutputTensorDesc(const OH_NNExecutor *executor, size_t index)](#oh_nnexecutor_createoutputtensordesc) | Creates an output tensor descriptor with its index.<br> The output tensor descriptor contains all attributes of the output tensor. If the <b>index</b> is greater than or equal to the output tensor number, this method will return error code. The output tensor number can be got by [OH_NNExecutor_GetOutputCount](capi-neural-network-core-h.md#oh_nnexecutor_getoutputcount). |
| [OH_NN_ReturnCode OH_NNExecutor_GetInputDimRange(const OH_NNExecutor *executor, size_t index, size_t **minInputDims, size_t **maxInputDims, size_t *shapeLength)](#oh_nnexecutor_getinputdimrange) | Gets the dimension ranges of an input tensor.<br> The supported dimension ranges of an input tensor with dynamic shape may be different among various devices. You can call this method to get the dimension ranges of the input tensor supported by the device. <b>*minInputDims</b> contains the minimum demensions of the input tensor, and <b>*maxInputDims</b> contains the maximum, e.g. if an input tensor has dynamic shape [-1, -1, -1, 3], its <b>*minInputDims</b> may be [1, 10, 10, 3] and <b>*maxInputDims</b> may be [100, 1024, 1024, 3] on the device.<br> If the <b>index</b> is greater than or equal to the input tensor number, this method will return error code. The input tensor number can be got by [OH_NNExecutor_GetInputCount](capi-neural-network-core-h.md#oh_nnexecutor_getinputcount).<br> As an output parameter, <b>*minInputDims</b> or <b>*maxInputDims</b> must be a null pointer, otherwise the method will return an error code. For example, you should define int32_t* minInDims = NULL, and pass &minInDims as the argument of <b>minInputDims</b>.<br> You do not need to release the memory of <b>*minInputDims</b> or <b>*maxInputDims</b>. It will be released when <b>executor</b> is destroied. |
| [OH_NN_ReturnCode OH_NNExecutor_SetOnRunDone(OH_NNExecutor *executor, NN_OnRunDone onRunDone)](#oh_nnexecutor_setonrundone) | Sets the callback function handle for the post-process when the asynchronous execution has been done.<br> The definition fo the callback function: [NN_OnRunDone](capi-neural-network-runtime-type-h.md#nn_onrundone). |
| [OH_NN_ReturnCode OH_NNExecutor_SetOnServiceDied(OH_NNExecutor *executor, NN_OnServiceDied onServiceDied)](#oh_nnexecutor_setonservicedied) | Sets the callback function handle for the post-process when the device driver service is dead during asynchronous execution.<br> The definition fo the callback function: [NN_OnServiceDied](capi-neural-network-runtime-type-h.md#nn_onservicedied). |
| [OH_NN_ReturnCode OH_NNExecutor_RunSync(OH_NNExecutor *executor, NN_Tensor *inputTensor[], size_t inputCount, NN_Tensor *outputTensor[], size_t outputCount)](#oh_nnexecutor_runsync) | Synchronous execution of the model inference.<br> Input and output tensors should be created first by [OH_NNTensor_Create](capi-neural-network-core-h.md#oh_nntensor_create), [OH_NNTensor_CreateWithSize](capi-neural-network-core-h.md#oh_nntensor_createwithsize) or [OH_NNTensor_CreateWithFd](capi-neural-network-core-h.md#oh_nntensor_createwithfd). And then the input tensors data which is got by [OH_NNTensor_GetDataBuffer](capi-neural-network-core-h.md#oh_nntensor_getdatabuffer) must be filled. The executor will then yield out the results by inference execution and fill them into output tensors data for you to read. <br> In the case of dynamic shape, you can get the real output shape directly by [OH_NNExecutor_GetOutputShape](capi-neural-network-core-h.md#oh_nnexecutor_getoutputshape), or you can create a tensor descriptor from an output tensor by [OH_NNTensor_GetTensorDesc](capi-neural-network-core-h.md#oh_nntensor_gettensordesc), and then read its real shape by [OH_NNTensorDesc_GetShape](capi-neural-network-core-h.md#oh_nntensordesc_getshape). |
| [OH_NN_ReturnCode OH_NNExecutor_RunAsync(OH_NNExecutor *executor, NN_Tensor *inputTensor[], size_t inputCount, NN_Tensor *outputTensor[], size_t outputCount, int32_t timeout, void *userData)](#oh_nnexecutor_runasync) | Asynchronous execution of the model inference.<br> Input and output tensors should be created first by [OH_NNTensor_Create](capi-neural-network-core-h.md#oh_nntensor_create), [OH_NNTensor_CreateWithSize](capi-neural-network-core-h.md#oh_nntensor_createwithsize) or [OH_NNTensor_CreateWithFd](capi-neural-network-core-h.md#oh_nntensor_createwithfd). And then the input tensors data which is got by [OH_NNTensor_GetDataBuffer](capi-neural-network-core-h.md#oh_nntensor_getdatabuffer) must be filled. The executor will yield out the results by inference execution and fill them into output tensors data for you to read.<br> In the case of dynamic shape, you can get the real output shape directly by [OH_NNExecutor_GetOutputShape](capi-neural-network-core-h.md#oh_nnexecutor_getoutputshape), or you can create a tensor descriptor from an output tensor by [OH_NNTensor_GetTensorDesc](capi-neural-network-core-h.md#oh_nntensor_gettensordesc), and then read its real shape by [OH_NNTensorDesc_GetShape](capi-neural-network-core-h.md#oh_nntensordesc_getshape).<br> The method is non-blocked and will return immediately.<br> The callback function handles are set by [OH_NNExecutor_SetOnRunDone](capi-neural-network-core-h.md#oh_nnexecutor_setonrundone) and [OH_NNExecutor_SetOnServiceDied](capi-neural-network-core-h.md#oh_nnexecutor_setonservicedied). The inference results and error code can be got by [NN_OnRunDone](capi-neural-network-runtime-type-h.md#nn_onrundone). And you can deal with the abnormal termination of device driver service during asynchronous execution by [NN_OnServiceDied](capi-neural-network-runtime-type-h.md#nn_onservicedied).<br> If the execution time reaches the <b>timeout</b>, the execution will be terminated with no outputs, and the <b>errCode<b> returned in callback function [NN_OnRunDone](capi-neural-network-runtime-type-h.md#nn_onrundone) will be [OH_NN_TIMEOUT](capi-neural-network-runtime-type-h.md#oh_nn_returncode).<br> The <b>userData</b> is asynchronous execution identifier and will be returned as the first parameter of the callback function. You can input any value you want as long as it can identify different asynchronous executions. |
| [OH_NN_ReturnCode OH_NNDevice_GetAllDevicesID(const size_t **allDevicesID, uint32_t *deviceCount)](#oh_nndevice_getalldevicesid) | Obtains the IDs of all devices connected.<br> Each device has an unique and fixed ID. This method returns device IDs on the current device through the uint32_t array.<br> Device IDs are returned through the size_t array. Each element of the array is the ID of a single device.<br> The array memory is managed inside, so you do not need to care about it. The data pointer is valid before this method is called next time. |
| [OH_NN_ReturnCode OH_NNDevice_GetName(size_t deviceID, const char **name)](#oh_nndevice_getname) | Obtains the name of the specified device.<br> <b>deviceID</b> specifies the device whose name will be obtained. The device ID needs to be obtained by calling [OH_NNDevice_GetAllDevicesID](capi-neural-network-core-h.md#oh_nndevice_getalldevicesid). If it is 0, the first device in the current device list will be used by default.<br> The value of <b>*name</b> is a C-style string ended with <b>'\0'</b>. <b>*name</b> must be a null pointer. Otherwise, [OH_NN_INVALID_PARAMETER](capi-neural-network-runtime-type-h.md#oh_nn_returncode) is returned. Fou example, you should define char* deviceName = NULL, and pass &deviceName as the argument of <b>name</b>. |
| [OH_NN_ReturnCode OH_NNDevice_GetType(size_t deviceID, OH_NN_DeviceType *deviceType)](#oh_nndevice_gettype) | Obtains the type information of the specified device.<br> <b>deviceID</b> specifies the device whose type will be obtained. If it is 0, the first device in the current device list will be used. Currently the following device types are supported: - <b>OH_NN_CPU</b>: CPU device. - <b>OH_NN_GPU</b>: GPU device. - <b>OH_NN_ACCELERATOR</b>: machine learning dedicated accelerator. - <b>OH_NN_OTHERS</b>: other hardware types. |

## Function description

### OH_NNCompilation_Construct()

```c
OH_NNCompilation *OH_NNCompilation_Construct(const OH_NNModel *model)
```

**Description**

Creates a compilation instance of the [OH_NNCompilation](capi-neuralnetworkruntime-oh-nncompilation.md) type.<br> After the OH_NNModel module completes model construction, APIs provided by the OH_NNCompilation module pass the model to underlying device for compilation. This method creates a [OH_NNCompilation](capi-neuralnetworkruntime-oh-nncompilation.md) instance based on the passed [OH_NNModel](capi-neuralnetworkruntime-oh-nnmodel.md) instance. The [OH_NNCompilation_SetDevice](capi-neural-network-core-h.md#oh_nncompilation_setdevice) method is called to set the device to compile on, and [OH_NNCompilation_Build](capi-neural-network-core-h.md#oh_nncompilation_build) is then called to complete compilation.<br> In addition to computing device selection, the OH_NNCompilation module supports features such as model caching, performance preference, priority setting, and float16 computing, which can be implemented by the following methods: [OH_NNCompilation_SetCache](capi-neural-network-core-h.md#oh_nncompilation_setcache) [OH_NNCompilation_SetPerformanceMode](capi-neural-network-core-h.md#oh_nncompilation_setperformancemode) [OH_NNCompilation_SetPriority](capi-neural-network-core-h.md#oh_nncompilation_setpriority) [OH_NNCompilation_EnableFloat16](capi-neural-network-core-h.md#oh_nncompilation_enablefloat16)<br> After [OH_NNCompilation_Build](capi-neural-network-core-h.md#oh_nncompilation_build) is called, the [OH_NNModel](capi-neuralnetworkruntime-oh-nnmodel.md) instance can be released.

**System capability**: SystemCapability.AI.NeuralNetworkRuntime

**Since**: 9

**Parameters**:

| Parameter | Description |
| -- | -- |
| const OH_NNModel *model | Pointer to the [OH_NNModel](capi-neuralnetworkruntime-oh-nnmodel.md) instance. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_NNCompilation * | Pointer to a [OH_NNCompilation](capi-neuralnetworkruntime-oh-nncompilation.md) instance, or NULL if it fails to create. |

### OH_NNCompilation_ConstructWithOfflineModelFile()

```c
OH_NNCompilation *OH_NNCompilation_ConstructWithOfflineModelFile(const char *modelPath)
```

**Description**

Creates a compilation instance based on an offline model file.<br> This method conflicts with the way of passing an online built model or an offline model file buffer, and you have to choose only one of the three construction methods. <br> Offline model is a type of model that is offline compiled by the model converter provided by a device vendor. So that the offline model can only be used on the specified device, but the compilation time of offline model is usually much less than [OH_NNModel](capi-neuralnetworkruntime-oh-nnmodel.md). <br> You should perform the offline compilation during your development and deploy the offline model in your app package.

**System capability**: SystemCapability.AI.NeuralNetworkRuntime

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| const char *modelPath | Offline model file path. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_NNCompilation * | Pointer to an [OH_NNCompilation](capi-neuralnetworkruntime-oh-nncompilation.md) instance, or NULL if it fails to create. |

### OH_NNCompilation_ConstructWithOfflineModelBuffer()

```c
OH_NNCompilation *OH_NNCompilation_ConstructWithOfflineModelBuffer(const void *modelBuffer, size_t modelSize)
```

**Description**

Creates a compilation instance based on an offline model file buffer.<br> This method conflicts with the way of passing an online built model or an offline model file path, and you have to choose only one of the three construction methods. <br> Note that the returned [OH_NNCompilation](capi-neuralnetworkruntime-oh-nncompilation.md) instance only saves the <b>modelBuffer</b> pointer inside, instead of copying its data. You should not release <b>modelBuffer</b> before the [OH_NNCompilation](capi-neuralnetworkruntime-oh-nncompilation.md) instance is destroied.

**System capability**: SystemCapability.AI.NeuralNetworkRuntime

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| const void *modelBuffer | Offline model file buffer. |
| size_t modelSize | Offfline model buffer size. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_NNCompilation * | Pointer to an [OH_NNCompilation](capi-neuralnetworkruntime-oh-nncompilation.md) instance, or NULL if it fails to create. |

### OH_NNCompilation_ConstructForCache()

```c
OH_NNCompilation *OH_NNCompilation_ConstructForCache()
```

**Description**

Creates a empty compilation instance for restoration from cache later.<br> See [OH_NNCompilation_SetCache](capi-neural-network-core-h.md#oh_nncompilation_setcache) for the description of cache.<br> The restoration time from the cache is less than compilation with [OH_NNModel](capi-neuralnetworkruntime-oh-nnmodel.md).<br> You should call [OH_NNCompilation_SetCache](capi-neural-network-core-h.md#oh_nncompilation_setcache) or [OH_NNCompilation_ImportCacheFromBuffer](capi-neural-network-core-h.md#oh_nncompilation_importcachefrombuffer) first, and then call [OH_NNCompilation_Build](capi-neural-network-core-h.md#oh_nncompilation_build) to complete the restoration.

**System capability**: SystemCapability.AI.NeuralNetworkRuntime

**Since**: 11

**Returns**:

| Type | Description |
| -- | -- |
| OH_NNCompilation * | Pointer to an [OH_NNCompilation](capi-neuralnetworkruntime-oh-nncompilation.md) instance, or NULL if it fails to create. |

### OH_NNCompilation_ExportCacheToBuffer()

```c
OH_NN_ReturnCode OH_NNCompilation_ExportCacheToBuffer(OH_NNCompilation *compilation, const void *buffer, size_t length, size_t *modelSize)
```

**Description**

Exports the cache to a given buffer.<br> See [OH_NNCompilation_SetCache](capi-neural-network-core-h.md#oh_nncompilation_setcache) for the description of cache.<br> Note that the cache is the result of compilation building [OH_NNCompilation_Build](capi-neural-network-core-h.md#oh_nncompilation_build), so that this method must be called after [OH_NNCompilation_Build](capi-neural-network-core-h.md#oh_nncompilation_build).

**System capability**: SystemCapability.AI.NeuralNetworkRuntime

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_NNCompilation *compilation | Pointer to the [OH_NNCompilation](capi-neuralnetworkruntime-oh-nncompilation.md) instance. |
| const void *buffer | Pointer to the given buffer. |
| size_t length | Buffer length. |
| size_t *modelSize | Byte size of the model cache. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_NN_ReturnCode | Execution result of the function. If the operation is successful, <b>OH_NN_SUCCESS</b> is returned.          If the operation fails, an error code is returned. For details about the error codes,          see [OH_NN_ReturnCode](capi-neural-network-runtime-type-h.md#oh_nn_returncode). |

### OH_NNCompilation_ImportCacheFromBuffer()

```c
OH_NN_ReturnCode OH_NNCompilation_ImportCacheFromBuffer(OH_NNCompilation *compilation, const void *buffer, size_t modelSize)
```

**Description**

Imports the cache from a given buffer.<br> See [OH_NNCompilation_SetCache](capi-neural-network-core-h.md#oh_nncompilation_setcache) for the description of cache.<br> [OH_NNCompilation_Build](capi-neural-network-core-h.md#oh_nncompilation_build) should be called to complete the restoration after [OH_NNCompilation_ImportCacheFromBuffer](capi-neural-network-core-h.md#oh_nncompilation_importcachefrombuffer) is called.<br> Note that <b>compilation</b> only saves the <b>buffer</b> pointer inside, instead of copying its data. You should not release <b>buffer</b> before <b>compilation</b> is destroied.

**System capability**: SystemCapability.AI.NeuralNetworkRuntime

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_NNCompilation *compilation | Pointer to the [OH_NNCompilation](capi-neuralnetworkruntime-oh-nncompilation.md) instance. |
| const void *buffer | Pointer to the given buffer. |
| size_t modelSize | Byte size of the model cache. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_NN_ReturnCode | Execution result of the function. If the operation is successful, <b>OH_NN_SUCCESS</b> is returned.          If the operation fails, an error code is returned. For details about the error codes,          see [OH_NN_ReturnCode](capi-neural-network-runtime-type-h.md#oh_nn_returncode). |

### OH_NNCompilation_AddExtensionConfig()

```c
OH_NN_ReturnCode OH_NNCompilation_AddExtensionConfig(OH_NNCompilation *compilation, const char *configName, const void *configValue, const size_t configValueSize)
```

**Description**

Adds an extension config for a custom hardware attribute.<br> Some devices have their own specific attributes which have not been opened in NNRt. This method provides an additional way for you to set these custom hardware attributes of the device. You should query their names and values from the device vendor's documents, and add them into compilation instance one by one. These attributes will be passed directly to device driver, and this method will return error code if the driver cannot parse them. <br> After [OH_NNCompilation_Build](capi-neural-network-core-h.md#oh_nncompilation_build) is called, the <b>configName</b> and <b>configValue</b> can be released.

**System capability**: SystemCapability.AI.NeuralNetworkRuntime

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_NNCompilation *compilation | Pointer to the [OH_NNCompilation](capi-neuralnetworkruntime-oh-nncompilation.md) instance. |
| const char *configName | Config name. |
| const void *configValue | A byte buffer saving the config value. |
| const size_t configValueSize | Byte size of the config value. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_NN_ReturnCode | Execution result of the function. If the operation is successful, <b>OH_NN_SUCCESS</b> is returned.          If the operation fails, an error code is returned.          For details about the error codes, see [OH_NN_ReturnCode](capi-neural-network-runtime-type-h.md#oh_nn_returncode). |

### OH_NNCompilation_SetDevice()

```c
OH_NN_ReturnCode OH_NNCompilation_SetDevice(OH_NNCompilation *compilation, size_t deviceID)
```

**Description**

Specifies the device for model compilation and computing.<br> In the compilation phase, you need to specify the device for model compilation and computing. Call [OH_NNDevice_GetAllDevicesID](capi-neural-network-core-h.md#oh_nndevice_getalldevicesid) to obtain available device IDs. Call [OH_NNDevice_GetType](capi-neural-network-core-h.md#oh_nndevice_gettype) and [OH_NNDevice_GetName](capi-neural-network-core-h.md#oh_nndevice_getname) to obtain device information and pass target device ID to this method for setting. <br> *

**System capability**: SystemCapability.AI.NeuralNetworkRuntime

**Since**: 9

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_NNCompilation *compilation | Pointer to the [OH_NNCompilation](capi-neuralnetworkruntime-oh-nncompilation.md) instance. |
| size_t deviceID | Device id. If it is 0, the first device in the current device list will be used by default. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_NN_ReturnCode | Execution result of the function. If the operation is successful, <b>OH_NN_SUCCESS</b> is returned.          If the operation fails, an error code is returned.          For details about the error codes, see [OH_NN_ReturnCode](capi-neural-network-runtime-type-h.md#oh_nn_returncode). |

### OH_NNCompilation_SetCache()

```c
OH_NN_ReturnCode OH_NNCompilation_SetCache(OH_NNCompilation *compilation, const char *cachePath, uint32_t version)
```

**Description**

Set the cache directory and version of the compiled model.<br> On the device that supports caching, a model can be saved as a cache file after being compiled on the device driver. The model can be directly read from the cache file in the next compilation, saving recompilation time. This method performs different operations based on the passed cache directory and version: <br> - No file exists in the cache directory: Caches the compiled model to the directory and sets the cache version to <b>version</b>. <br> - A complete cache file exists in the cache directory, and its version is <b>version</b>: Reads the cache file in the path and passes the data to the underlying device for conversion into executable model instances. <br> - A complete cache file exists in the cache directory, and its version is earlier than <b>version</b>: When model compilation is complete on the underlying device, overwrites the cache file and changes the version number to <b>version</b>. <br> - A complete cache file exists in the cache directory, and its version is later than <b>version</b>: Returns the [OH_NN_INVALID_PARAMETER](capi-neural-network-runtime-type-h.md#oh_nn_returncode) error code without reading the cache file. <br> - The cache file in the cache directory is incomplete or you do not have the permission to access the cache file. Returns the [OH_NN_INVALID_FILE](capi-neural-network-runtime-type-h.md#oh_nn_returncode) error code. <br> - The cache directory does not exist or you do not have the access permission. Returns the [OH_NN_INVALID_PATH](capi-neural-network-runtime-type-h.md#oh_nn_returncode) error code.

**System capability**: SystemCapability.AI.NeuralNetworkRuntime

**Since**: 9

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_NNCompilation *compilation | Pointer to the [OH_NNCompilation](capi-neuralnetworkruntime-oh-nncompilation.md) instance. |
| const char *cachePath | Directory for storing model cache files. This method creates directories for different devices in the <b>cachePath</b> directory. You are advised to use a separate cache directory for each model. |
| uint32_t version | Cache version. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_NN_ReturnCode | Execution result of the function. If the operation is successful, <b>OH_NN_SUCCESS</b> is returned.          If the operation fails, an error code is returned.          For details about the error codes, see [OH_NN_ReturnCode](capi-neural-network-runtime-type-h.md#oh_nn_returncode). |

### OH_NNCompilation_SetPerformanceMode()

```c
OH_NN_ReturnCode OH_NNCompilation_SetPerformanceMode(OH_NNCompilation *compilation, OH_NN_PerformanceMode performanceMode)
```

**Description**

Sets the performance mode for model computing.<br> Allows you to set the performance mode for model computing to meet the requirements of low power consumption and ultimate performance. If this method is not called to set the performance mode in the compilation phase, the compilation instance assigns the [OH_NN_PERFORMANCE_NONE](capi-neural-network-runtime-type-h.md#oh_nn_performancemode) mode for the model by default. In this case, the device performs computing in the default performance mode. <br> If this method is called on the device that does not support the setting of the performance mode, the [OH_NN_UNAVALIDABLE_DEVICE](capi-neural-network-runtime-type-h.md#oh_nn_returncode) error code is returned.

**System capability**: SystemCapability.AI.NeuralNetworkRuntime

**Since**: 9

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_NNCompilation *compilation | Pointer to the [OH_NNCompilation](capi-neuralnetworkruntime-oh-nncompilation.md) instance. |
| OH_NN_PerformanceMode performanceMode | Performance mode. For details about the available performance modes, see [OH_NN_PerformanceMode](capi-neural-network-runtime-type-h.md#oh_nn_performancemode). |

**Returns**:

| Type | Description |
| -- | -- |
| OH_NN_ReturnCode | Execution result of the function. If the operation is successful, <b>OH_NN_SUCCESS</b> is returned.          If the operation fails, an error code is returned.          For details about the error codes, see [OH_NN_ReturnCode](capi-neural-network-runtime-type-h.md#oh_nn_returncode). |

### OH_NNCompilation_SetPriority()

```c
OH_NN_ReturnCode OH_NNCompilation_SetPriority(OH_NNCompilation *compilation, OH_NN_Priority priority)
```

**Description**

Sets the model computing priority.<br> Allows you to set computing priorities for models. The priorities apply only to models created by the process with the same UID. The settings will not affect models created by processes with different UIDs on different devices. <br> If this method is called on the device that does not support the priority setting, the [OH_NN_UNAVALIDABLE_DEVICE](capi-neural-network-runtime-type-h.md#oh_nn_returncode) error code is returned.

**System capability**: SystemCapability.AI.NeuralNetworkRuntime

**Since**: 9

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_NNCompilation *compilation | Pointer to the [OH_NNCompilation](capi-neuralnetworkruntime-oh-nncompilation.md) instance. |
| OH_NN_Priority priority | Priority. For details about the optional priorities, see [OH_NN_Priority](capi-neural-network-runtime-type-h.md#oh_nn_priority). |

**Returns**:

| Type | Description |
| -- | -- |
| OH_NN_ReturnCode | Execution result of the function. If the operation is successful, <b>OH_NN_SUCCESS</b> is returned.          If the operation fails, an error code is returned.          For details about the error codes, see [OH_NN_ReturnCode](capi-neural-network-runtime-type-h.md#oh_nn_returncode). |

### OH_NNCompilation_EnableFloat16()

```c
OH_NN_ReturnCode OH_NNCompilation_EnableFloat16(OH_NNCompilation *compilation, bool enableFloat16)
```

**Description**

Enables float16 for computing.<br> Float32 is used by default for the model of float type. If this method is called on a device that supports float16, float16 will be used for computing the float32 model to reduce memory usage and execution time. <br> This option is useless for the model of int type, e.g. int8 type. <br> If this method is called on the device that does not support float16, the [OH_NN_UNAVALIDABLE_DEVICE](capi-neural-network-runtime-type-h.md#oh_nn_returncode) error code is returned.

**System capability**: SystemCapability.AI.NeuralNetworkRuntime

**Since**: 9

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_NNCompilation *compilation | Pointer to the [OH_NNCompilation](capi-neuralnetworkruntime-oh-nncompilation.md) instance. |
| bool enableFloat16 | Indicates whether to enable float16. If this parameter is set to <b>true</b>, float16 inference is performed. If this parameter is set to <b>false</b>, float32 inference is performed. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_NN_ReturnCode | Execution result of the function. If the operation is successful, <b>OH_NN_SUCCESS</b> is returned.          If the operation fails, an error code is returned.          For details about the error codes, see [OH_NN_ReturnCode](capi-neural-network-runtime-type-h.md#oh_nn_returncode). |

### OH_NNCompilation_Build()

```c
OH_NN_ReturnCode OH_NNCompilation_Build(OH_NNCompilation *compilation)
```

**Description**

Compiles a model.<br> After the compilation configuration is complete, call this method to return the compilation result. The compilation instance pushes the model and compilation options to the device for compilation. After this method is called, additional compilation operations cannot be performed. <br> If the [OH_NNCompilation_SetDevice](capi-neural-network-core-h.md#oh_nncompilation_setdevice), [OH_NNCompilation_SetCache](capi-neural-network-core-h.md#oh_nncompilation_setcache), [OH_NNCompilation_SetPerformanceMode](capi-neural-network-core-h.md#oh_nncompilation_setperformancemode), [OH_NNCompilation_SetPriority](capi-neural-network-core-h.md#oh_nncompilation_setpriority), and [OH_NNCompilation_EnableFloat16](capi-neural-network-core-h.md#oh_nncompilation_enablefloat16) methods are called, [OH_NN_OPERATION_FORBIDDEN](capi-neural-network-runtime-type-h.md#oh_nn_returncode) is returned.

**System capability**: SystemCapability.AI.NeuralNetworkRuntime

**Since**: 9

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_NNCompilation *compilation | Pointer to the [OH_NNCompilation](capi-neuralnetworkruntime-oh-nncompilation.md) instance. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_NN_ReturnCode | Execution result of the function. If the operation is successful, <b>OH_NN_SUCCESS</b> is returned. If the          operation fails, an error code is returned. For details about the error codes, see [OH_NN_ReturnCode](capi-neural-network-runtime-type-h.md#oh_nn_returncode). |

### OH_NNCompilation_Destroy()

```c
void OH_NNCompilation_Destroy(OH_NNCompilation **compilation)
```

**Description**

Releases the <b>Compilation</b> object.<br> This method needs to be called to release the compilation instance created by [OH_NNCompilation_Construct](capi-neural-network-core-h.md#oh_nncompilation_construct), [OH_NNCompilation_ConstructWithOfflineModelFile](capi-neural-network-core-h.md#oh_nncompilation_constructwithofflinemodelfile), [OH_NNCompilation_ConstructWithOfflineModelBuffer](capi-neural-network-core-h.md#oh_nncompilation_constructwithofflinemodelbuffer) and [OH_NNCompilation_ConstructForCache](capi-neural-network-core-h.md#oh_nncompilation_constructforcache). Otherwise, the memory leak will occur. <br> If <b>compilation</b> or <b>*compilation</b> is a null pointer, this method only prints warning logs and does not execute the release.

**System capability**: SystemCapability.AI.NeuralNetworkRuntime

**Since**: 9

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_NNCompilation **compilation | Double pointer to the [OH_NNCompilation](capi-neuralnetworkruntime-oh-nncompilation.md) instance. After a compilation instance is destroyed,this method sets <b>*compilation</b> to a null pointer. |

### OH_NNTensorDesc_Create()

```c
NN_TensorDesc *OH_NNTensorDesc_Create()
```

**Description**

Creates an [NN_TensorDesc](capi-neuralnetworkruntime-nn-tensordesc.md) instance.<br> The [NN_TensorDesc](capi-neuralnetworkruntime-nn-tensordesc.md) describes various tensor attributes, such as name/data type/shape/format, etc.<br> The following methods can be called to create a [NN_Tensor](capi-neuralnetworkruntime-nn-tensor.md) instance based on the passed [NN_TensorDesc](capi-neuralnetworkruntime-nn-tensordesc.md) instance: [OH_NNTensor_Create](capi-neural-network-core-h.md#oh_nntensor_create) [OH_NNTensor_CreateWithSize](capi-neural-network-core-h.md#oh_nntensor_createwithsize) [OH_NNTensor_CreateWithFd](capi-neural-network-core-h.md#oh_nntensor_createwithfd)<br> Note that these methods will copy the [NN_TensorDesc](capi-neuralnetworkruntime-nn-tensordesc.md) instance into [NN_Tensor](capi-neuralnetworkruntime-nn-tensor.md). Therefore you can create multiple [NN_Tensor](capi-neuralnetworkruntime-nn-tensor.md) instances with the same [NN_TensorDesc](capi-neuralnetworkruntime-nn-tensordesc.md) instance. And you should destroy the [NN_TensorDesc](capi-neuralnetworkruntime-nn-tensordesc.md) instance by [OH_NNTensorDesc_Destroy](capi-neural-network-core-h.md#oh_nntensordesc_destroy) when it is no longer used.

**System capability**: SystemCapability.AI.NeuralNetworkRuntime

**Since**: 11

**Returns**:

| Type | Description |
| -- | -- |
| NN_TensorDesc * | Pointer to a [NN_TensorDesc](capi-neuralnetworkruntime-nn-tensordesc.md) instance, or NULL if it fails to create. |

### OH_NNTensorDesc_Destroy()

```c
OH_NN_ReturnCode OH_NNTensorDesc_Destroy(NN_TensorDesc **tensorDesc)
```

**Description**

Releases an [NN_TensorDesc](capi-neuralnetworkruntime-nn-tensordesc.md) instance.<br> When the [NN_TensorDesc](capi-neuralnetworkruntime-nn-tensordesc.md) instance is no longer used, this method needs to be called to release it. Otherwise, the memory leak will occur. <br> If <b>tensorDesc</b> or <b>*tensorDesc</b> is a null pointer, this method will return error code and does not execute the release.

**System capability**: SystemCapability.AI.NeuralNetworkRuntime

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| NN_TensorDesc **tensorDesc | Double pointer to the [NN_TensorDesc](capi-neuralnetworkruntime-nn-tensordesc.md) instance. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_NN_ReturnCode | Execution result of the function. If the operation is successful, <b>OH_NN_SUCCESS</b> is returned.          If the operation fails, an error code is returned.          For details about the error codes, see [OH_NN_ReturnCode](capi-neural-network-runtime-type-h.md#oh_nn_returncode). |

### OH_NNTensorDesc_SetName()

```c
OH_NN_ReturnCode OH_NNTensorDesc_SetName(NN_TensorDesc *tensorDesc, const char *name)
```

**Description**

Sets the name of a [NN_TensorDesc](capi-neuralnetworkruntime-nn-tensordesc.md).<br> After the [NN_TensorDesc](capi-neuralnetworkruntime-nn-tensordesc.md) instance is created, call this method to set the tensor name. The value of <b>*name</b> is a C-style string ended with <b>'\0'</b>.<br> if <b>tensorDesc</b> or <b>name</b> is a null pointer, this method will return error code.

**System capability**: SystemCapability.AI.NeuralNetworkRuntime

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| NN_TensorDesc *tensorDesc | Pointer to the [NN_TensorDesc](capi-neuralnetworkruntime-nn-tensordesc.md) instance. |
| const char *name | The name of the tensor that needs to be set. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_NN_ReturnCode | Execution result of the function. If the operation is successful, <b>OH_NN_SUCCESS</b> is returned.          If the operation fails, an error code is returned. For details about the error codes,          see [OH_NN_ReturnCode](capi-neural-network-runtime-type-h.md#oh_nn_returncode). |

### OH_NNTensorDesc_GetName()

```c
OH_NN_ReturnCode OH_NNTensorDesc_GetName(const NN_TensorDesc *tensorDesc, const char **name)
```

**Description**

Gets the name of a [NN_TensorDesc](capi-neuralnetworkruntime-nn-tensordesc.md).<br> Call this method to obtain the name of the specified [NN_TensorDesc](capi-neuralnetworkruntime-nn-tensordesc.md) instance. The value of <b>*name</b> is a C-style string ended with <b>'\0'</b>.<br> if <b>tensorDesc</b> or <b>name</b> is a null pointer, this method will return error code. As an output parameter, <b>*name</b> must be a null pointer, otherwise the method will return an error code. Fou example, you should define char* tensorName = NULL, and pass &tensorName as the argument of <b>name</b>.<br> You do not need to release the memory of <b>name</b>. It will be released when <b>tensorDesc</b> is destroied.

**System capability**: SystemCapability.AI.NeuralNetworkRuntime

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| const NN_TensorDesc *tensorDesc | Pointer to the [NN_TensorDesc](capi-neuralnetworkruntime-nn-tensordesc.md) instance. |
| const char **name | The retured name of the tensor. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_NN_ReturnCode | Execution result of the function. If the operation is successful, <b>OH_NN_SUCCESS</b> is returned.          If the operation fails, an error code is returned. For details about the error codes,          see [OH_NN_ReturnCode](capi-neural-network-runtime-type-h.md#oh_nn_returncode). |

### OH_NNTensorDesc_SetDataType()

```c
OH_NN_ReturnCode OH_NNTensorDesc_SetDataType(NN_TensorDesc *tensorDesc, OH_NN_DataType dataType)
```

**Description**

Sets the data type of a [NN_TensorDesc](capi-neuralnetworkruntime-nn-tensordesc.md).<br> After the [NN_TensorDesc](capi-neuralnetworkruntime-nn-tensordesc.md) instance is created, call this method to set the tensor data type. <br> if <b>tensorDesc</b> is a null pointer, this method will return error code.

**System capability**: SystemCapability.AI.NeuralNetworkRuntime

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| NN_TensorDesc *tensorDesc | Pointer to the [NN_TensorDesc](capi-neuralnetworkruntime-nn-tensordesc.md) instance. |
| OH_NN_DataType dataType | The data type of the tensor that needs to be set. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_NN_ReturnCode | Execution result of the function. If the operation is successful, <b>OH_NN_SUCCESS</b> is returned.          If the operation fails, an error code is returned.          For details about the error codes, see [OH_NN_ReturnCode](capi-neural-network-runtime-type-h.md#oh_nn_returncode). |

### OH_NNTensorDesc_GetDataType()

```c
OH_NN_ReturnCode OH_NNTensorDesc_GetDataType(const NN_TensorDesc *tensorDesc, OH_NN_DataType *dataType)
```

**Description**

Gets the data type of a [NN_TensorDesc](capi-neuralnetworkruntime-nn-tensordesc.md).<br> Call this method to obtain the data type of the specified [NN_TensorDesc](capi-neuralnetworkruntime-nn-tensordesc.md) instance. <br> if <b>tensorDesc</b> or <b>dataType</b> is a null pointer, this method will return error code.

**System capability**: SystemCapability.AI.NeuralNetworkRuntime

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| const NN_TensorDesc *tensorDesc | Pointer to the [NN_TensorDesc](capi-neuralnetworkruntime-nn-tensordesc.md) instance. |
| OH_NN_DataType *dataType | The returned data type of the tensor. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_NN_ReturnCode | Execution result of the function. If the operation is successful, <b>OH_NN_SUCCESS</b> is returned. If the          operation fails, an error code is returned. For details about the error codes, see [OH_NN_ReturnCode](capi-neural-network-runtime-type-h.md#oh_nn_returncode). |

### OH_NNTensorDesc_SetShape()

```c
OH_NN_ReturnCode OH_NNTensorDesc_SetShape(NN_TensorDesc *tensorDesc, const int32_t *shape, size_t shapeLength)
```

**Description**

Sets the shape of a [NN_TensorDesc](capi-neuralnetworkruntime-nn-tensordesc.md).<br> After the [NN_TensorDesc](capi-neuralnetworkruntime-nn-tensordesc.md) instance is created, call this method to set the tensor shape. <br> if <b>tensorDesc</b> or <b>shape</b> is a null pointer, or <b>shapeLength</b> is 0, this method will return error code.

**System capability**: SystemCapability.AI.NeuralNetworkRuntime

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| NN_TensorDesc *tensorDesc | Pointer to the [NN_TensorDesc](capi-neuralnetworkruntime-nn-tensordesc.md) instance. |
| const int32_t *shape | The shape list of the tensor that needs to be set. |
| size_t shapeLength | The length of the shape list that needs to be set. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_NN_ReturnCode | Execution result of the function. If the operation is successful, <b>OH_NN_SUCCESS</b> is returned. If the          operation fails, an error code is returned. For details about the error codes, see [OH_NN_ReturnCode](capi-neural-network-runtime-type-h.md#oh_nn_returncode). |

### OH_NNTensorDesc_GetShape()

```c
OH_NN_ReturnCode OH_NNTensorDesc_GetShape(const NN_TensorDesc *tensorDesc, int32_t **shape, size_t *shapeLength)
```

**Description**

Gets the shape of a [NN_TensorDesc](capi-neuralnetworkruntime-nn-tensordesc.md).<br> Call this method to obtain the shape of the specified [NN_TensorDesc](capi-neuralnetworkruntime-nn-tensordesc.md) instance. <br> if <b>tensorDesc</b>, <b>shape</b> or <b>shapeLength</b> is a null pointer, this method will return error code. As an output parameter, <b>*shape</b> must be a null pointer, otherwise the method will return an error code. Fou example, you should define int32_t* tensorShape = NULL, and pass &tensorShape as the argument of <b>shape</b>. <br> You do not need to release the memory of <b>shape</b>. It will be released when <b>tensorDesc</b> is destroied.

**System capability**: SystemCapability.AI.NeuralNetworkRuntime

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| const NN_TensorDesc *tensorDesc | Pointer to the [NN_TensorDesc](capi-neuralnetworkruntime-nn-tensordesc.md) instance. |
| int32_t **shape | Return the shape list of the tensor. |
| size_t *shapeLength | The returned length of the shape list. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_NN_ReturnCode | Execution result of the function. If the operation is successful, <b>OH_NN_SUCCESS</b> is returned. If the          operation fails, an error code is returned. For details about the error codes, see [OH_NN_ReturnCode](capi-neural-network-runtime-type-h.md#oh_nn_returncode). |

### OH_NNTensorDesc_SetFormat()

```c
OH_NN_ReturnCode OH_NNTensorDesc_SetFormat(NN_TensorDesc *tensorDesc, OH_NN_Format format)
```

**Description**

Sets the format of a [NN_TensorDesc](capi-neuralnetworkruntime-nn-tensordesc.md).<br> After the [NN_TensorDesc](capi-neuralnetworkruntime-nn-tensordesc.md) instance is created, call this method to set the tensor format. <br> if <b>tensorDesc</b> is a null pointer, this method will return error code.

**System capability**: SystemCapability.AI.NeuralNetworkRuntime

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| NN_TensorDesc *tensorDesc | Pointer to the [NN_TensorDesc](capi-neuralnetworkruntime-nn-tensordesc.md) instance. |
| OH_NN_Format format | The format of the tensor that needs to be set. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_NN_ReturnCode | Execution result of the function. If the operation is successful, <b>OH_NN_SUCCESS</b> is returned. If the          operation fails, an error code is returned. For details about the error codes, see [OH_NN_ReturnCode](capi-neural-network-runtime-type-h.md#oh_nn_returncode). |

### OH_NNTensorDesc_GetFormat()

```c
OH_NN_ReturnCode OH_NNTensorDesc_GetFormat(const NN_TensorDesc *tensorDesc, OH_NN_Format *format)
```

**Description**

Gets the format of a [NN_TensorDesc](capi-neuralnetworkruntime-nn-tensordesc.md).<br> Call this method to obtain the format of the specified [NN_TensorDesc](capi-neuralnetworkruntime-nn-tensordesc.md) instance. <br> if <b>tensorDesc</b> or <b>format</b> is a null pointer, this method will return error code.

**System capability**: SystemCapability.AI.NeuralNetworkRuntime

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| const NN_TensorDesc *tensorDesc | Pointer to the [NN_TensorDesc](capi-neuralnetworkruntime-nn-tensordesc.md) instance. |
| OH_NN_Format *format | The returned format of the tensor. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_NN_ReturnCode | Execution result of the function. If the operation is successful, <b>OH_NN_SUCCESS</b> is returned. If the          operation fails, an error code is returned. For details about the error codes, see [OH_NN_ReturnCode](capi-neural-network-runtime-type-h.md#oh_nn_returncode). |

### OH_NNTensorDesc_GetElementCount()

```c
OH_NN_ReturnCode OH_NNTensorDesc_GetElementCount(const NN_TensorDesc *tensorDesc, size_t *elementCount)
```

**Description**

Gets the element count of a [NN_TensorDesc](capi-neuralnetworkruntime-nn-tensordesc.md).<br> Call this method to obtain the element count of the specified [NN_TensorDesc](capi-neuralnetworkruntime-nn-tensordesc.md) instance. If you need to obtain byte size of the tensor data, call [OH_NNTensorDesc_GetByteSize](capi-neural-network-core-h.md#oh_nntensordesc_getbytesize). <br> If the tensor shape is dynamic, this method will return error code, and <b>elementCount</b> will be 0. <br> if <b>tensorDesc</b> or <b>elementCount</b> is a null pointer, this method will return error code.

**System capability**: SystemCapability.AI.NeuralNetworkRuntime

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| const NN_TensorDesc *tensorDesc | Pointer to the [NN_TensorDesc](capi-neuralnetworkruntime-nn-tensordesc.md) instance. |
| size_t *elementCount | The returned element count of the tensor. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_NN_ReturnCode | Execution result of the function. If the operation is successful, <b>OH_NN_SUCCESS</b> is returned. If the          operation fails, an error code is returned. For details about the error codes, see [OH_NN_ReturnCode](capi-neural-network-runtime-type-h.md#oh_nn_returncode). |

### OH_NNTensorDesc_GetByteSize()

```c
OH_NN_ReturnCode OH_NNTensorDesc_GetByteSize(const NN_TensorDesc *tensorDesc, size_t *byteSize)
```

**Description**

Gets the byte size of a [NN_TensorDesc](capi-neuralnetworkruntime-nn-tensordesc.md).<br> Call this method to obtain the byte size of the specified [NN_TensorDesc](capi-neuralnetworkruntime-nn-tensordesc.md) instance. <br> If the tensor shape is dynamic, this method will return error code, and <b>byteSize</b> will be 0. <br> If you need to obtain element count of the tensor data, call [OH_NNTensorDesc_GetElementCount](capi-neural-network-core-h.md#oh_nntensordesc_getelementcount). <br> if <b>tensorDesc</b> or <b>byteSize</b> is a null pointer, this method will return error code.

**System capability**: SystemCapability.AI.NeuralNetworkRuntime

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| const NN_TensorDesc *tensorDesc | Pointer to the [NN_TensorDesc](capi-neuralnetworkruntime-nn-tensordesc.md) instance. |
| size_t *byteSize | The returned byte size of the tensor. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_NN_ReturnCode | Execution result of the function. If the operation is successful, <b>OH_NN_SUCCESS</b> is returned. If the          operation fails, an error code is returned. For details about the error codes, see [OH_NN_ReturnCode](capi-neural-network-runtime-type-h.md#oh_nn_returncode). |

### OH_NNTensor_Create()

```c
NN_Tensor *OH_NNTensor_Create(size_t deviceID, NN_TensorDesc *tensorDesc)
```

**Description**

Creates a [NN_Tensor](capi-neuralnetworkruntime-nn-tensor.md) instance from [NN_TensorDesc](capi-neuralnetworkruntime-nn-tensordesc.md).<br> This method use [OH_NNTensorDesc_GetByteSize](capi-neural-network-core-h.md#oh_nntensordesc_getbytesize) to calculate the byte size of tensor data and allocate shared memory on device for it. The device dirver will get the tensor data directly by the "zero-copy" way.<br> Note that this method will copy the <b>tensorDesc</b> into [NN_Tensor](capi-neuralnetworkruntime-nn-tensor.md). Therefore you should destroy <b>tensorDesc</b> by [OH_NNTensorDesc_Destroy](capi-neural-network-core-h.md#oh_nntensordesc_destroy) if it is no longer used.<br> If the tensor shape is dynamic, this method will return error code.<br> <b>deviceID</b> indicates the selected device. If it is 0, the first device in the current device list will be used by default.<br> <b>tensorDesc</b> must be provided, and this method will return an error code if it is a null pointer.<br> Call [OH_NNTensor_Destroy](capi-neural-network-core-h.md#oh_nntensor_destroy) to release the [NN_Tensor](capi-neuralnetworkruntime-nn-tensor.md) instance if it is no longer used.

**System capability**: SystemCapability.AI.NeuralNetworkRuntime

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| size_t deviceID | Device id. If it is 0, the first device in the current device list will be used by default. |
| NN_TensorDesc *tensorDesc | Pointer to the [NN_TensorDesc](capi-neuralnetworkruntime-nn-tensordesc.md) instance. |

**Returns**:

| Type | Description |
| -- | -- |
| NN_Tensor * | Pointer to a [NN_Tensor](capi-neuralnetworkruntime-nn-tensor.md) instance, or NULL if it fails to create. |

### OH_NNTensor_CreateWithSize()

```c
NN_Tensor *OH_NNTensor_CreateWithSize(size_t deviceID, NN_TensorDesc *tensorDesc, size_t size)
```

**Description**

Creates a [NN_Tensor](capi-neuralnetworkruntime-nn-tensor.md) instance with specified size and [NN_TensorDesc](capi-neuralnetworkruntime-nn-tensordesc.md).<br> This method use <b>size</b> as the byte size of tensor data and allocate shared memory on device for it. The device dirver will get the tensor data directly by the "zero-copy" way.<br> Note that this method will copy the <b>tensorDesc</b> into [NN_Tensor](capi-neuralnetworkruntime-nn-tensor.md). Therefore you should destroy <b>tensorDesc</b> by [OH_NNTensorDesc_Destroy](capi-neural-network-core-h.md#oh_nntensordesc_destroy) if it is no longer used.<br> <b>deviceID</b> indicates the selected device. If it is 0, the first device in the current device list will be used by default.<br> <b>tensorDesc</b> must be provided, if it is a null pointer, the method returns an error code. <b>size</b> must be no less than the byte size of tensorDesc. Otherwise, this method will return an error code. If the tensor shape is dynamic, the <b>size</b> will not be checked.<br> Call [OH_NNTensor_Destroy](capi-neural-network-core-h.md#oh_nntensor_destroy) to release the [NN_Tensor](capi-neuralnetworkruntime-nn-tensor.md) instance if it is no longer used.

**System capability**: SystemCapability.AI.NeuralNetworkRuntime

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| size_t deviceID | Device id. If it is 0, the first device in the current device list will be used by default. |
| NN_TensorDesc *tensorDesc | Pointer to the [NN_TensorDesc](capi-neuralnetworkruntime-nn-tensordesc.md) instance. |
| size_t size | Size of tensor data that need to be allocated. |

**Returns**:

| Type | Description |
| -- | -- |
| NN_Tensor * | Pointer to a [NN_Tensor](capi-neuralnetworkruntime-nn-tensor.md) instance, or NULL if it fails to create. |

### OH_NNTensor_CreateWithFd()

```c
NN_Tensor *OH_NNTensor_CreateWithFd(size_t deviceID, NN_TensorDesc *tensorDesc, int fd, size_t size, size_t offset)
```

**Description**

Creates a [NN_Tensor](capi-neuralnetworkruntime-nn-tensor.md) instance with specified file descriptor and [NN_TensorDesc](capi-neuralnetworkruntime-nn-tensordesc.md).<br> This method reuses the shared memory corresponding to the file descriptor <b>fd</b> passed. It may comes from another [NN_Tensor](capi-neuralnetworkruntime-nn-tensor.md) instance. When you call the [OH_NNTensor_Destroy](capi-neural-network-core-h.md#oh_nntensor_destroy) method to release the tensor created by this method, the tensor data memory will not be released.<br> Note that this method will copy the <b>tensorDesc</b> into [NN_Tensor](capi-neuralnetworkruntime-nn-tensor.md). Therefore you should destroy <b>tensorDesc</b> by [OH_NNTensorDesc_Destroy](capi-neural-network-core-h.md#oh_nntensordesc_destroy) if it is no longer used.<br> <b>deviceID</b> indicates the selected device. If it is 0, the first device in the current device list will be used by default.<br> <b>tensorDesc</b> must be provided, if it is a null pointer, the method returns an error code.<br> Call [OH_NNTensor_Destroy](capi-neural-network-core-h.md#oh_nntensor_destroy) to release the [NN_Tensor](capi-neuralnetworkruntime-nn-tensor.md) instance if it is no longer used.

**System capability**: SystemCapability.AI.NeuralNetworkRuntime

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| size_t deviceID | Device id. If it is 0, the first device in the current device list will be used by default. |
| NN_TensorDesc *tensorDesc | Pointer to the [NN_TensorDesc](capi-neuralnetworkruntime-nn-tensordesc.md) instance. |
| int fd | file descriptor of the shared memory to be resued. |
| size_t size | Size of the shared memory to be resued. |
| size_t offset | Offset of the shared memory to be resued. |

**Returns**:

| Type | Description |
| -- | -- |
| NN_Tensor * | Pinter to a [NN_Tensor](capi-neuralnetworkruntime-nn-tensor.md) instance, or NULL if it fails to create. |

### OH_NNTensor_Destroy()

```c
OH_NN_ReturnCode OH_NNTensor_Destroy(NN_Tensor **tensor)
```

**Description**

Releases a [NN_Tensor](capi-neuralnetworkruntime-nn-tensor.md) instance.<br> When the [NN_Tensor](capi-neuralnetworkruntime-nn-tensor.md) instance is no longer used, this method needs to be called to release the instance. Otherwise, the memory leak will occur.<br> If <b>tensor</b> or <b>*tensor</b> is a null pointer, this method will return error code and does not execute the release.

**System capability**: SystemCapability.AI.NeuralNetworkRuntime

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| NN_Tensor **tensor | Double pointer to the [NN_Tensor](capi-neuralnetworkruntime-nn-tensor.md) instance. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_NN_ReturnCode | Execution result of the function. If the operation is successful, <b>OH_NN_SUCCESS</b> is returned.          If the operation fails, an error code is returned. For details about the error codes,          see [OH_NN_ReturnCode](capi-neural-network-runtime-type-h.md#oh_nn_returncode). |

### OH_NNTensor_GetTensorDesc()

```c
NN_TensorDesc *OH_NNTensor_GetTensorDesc(const NN_Tensor *tensor)
```

**Description**

Gets the [NN_TensorDesc](capi-neuralnetworkruntime-nn-tensordesc.md) instance of a [NN_Tensor](capi-neuralnetworkruntime-nn-tensor.md).<br> Call this method to obtain the inner [NN_TensorDesc](capi-neuralnetworkruntime-nn-tensordesc.md) instance pointer of the specified [NN_Tensor](capi-neuralnetworkruntime-nn-tensor.md) instance. You can get various types of the tensor attributes such as name/format/data type/shape from the returned [NN_TensorDesc](capi-neuralnetworkruntime-nn-tensordesc.md) instance.<br> You should not destory the returned [NN_TensorDesc](capi-neuralnetworkruntime-nn-tensordesc.md) instance because it points to the inner instance of [NN_Tensor](capi-neuralnetworkruntime-nn-tensor.md). Otherwise, a menory corruption of double free will occur when [OH_NNTensor_Destroy](capi-neural-network-core-h.md#oh_nntensor_destroy) is called.<br> if <b>tensor</b> is a null pointer, this method will return null pointer.

**System capability**: SystemCapability.AI.NeuralNetworkRuntime

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| const NN_Tensor *tensor | Pointer to the [NN_Tensor](capi-neuralnetworkruntime-nn-tensor.md) instance. |

**Returns**:

| Type | Description |
| -- | -- |
| NN_TensorDesc * | Pointer to the [NN_TensorDesc](capi-neuralnetworkruntime-nn-tensordesc.md) instance, or NULL if it fails to create. |

### OH_NNTensor_GetDataBuffer()

```c
void *OH_NNTensor_GetDataBuffer(const NN_Tensor *tensor)
```

**Description**

Gets the data buffer of a [NN_Tensor](capi-neuralnetworkruntime-nn-tensor.md).<br> You can read/write data from/to the tensor data buffer. The buffer is mapped from a shared memory on device, so the device dirver will get the tensor data directly by this "zero-copy" way.<br> Note that the real tensor data only uses the segment [offset, size) of the shared memory. The offset can be got by [OH_NNTensor_GetOffset](capi-neural-network-core-h.md#oh_nntensor_getoffset) and the size can be got by [OH_NNTensor_GetSize](capi-neural-network-core-h.md#oh_nntensor_getsize).<br> if <b>tensor</b> is a null pointer, this method will return null pointer.

**System capability**: SystemCapability.AI.NeuralNetworkRuntime

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| const NN_Tensor *tensor | Pointer to the [NN_Tensor](capi-neuralnetworkruntime-nn-tensor.md) instance. |

**Returns**:

| Type | Description |
| -- | -- |
| void * | Pointer to data buffer of the tensor, or NULL if it fails to create. |

### OH_NNTensor_GetFd()

```c
OH_NN_ReturnCode OH_NNTensor_GetFd(const NN_Tensor *tensor, int *fd)
```

**Description**

Gets the file descriptor of the shared memory of a [NN_Tensor](capi-neuralnetworkruntime-nn-tensor.md).<br> The file descriptor <b>fd</b> corresponds to the shared memory of the tensor data, and can be resued by another [NN_Tensor](capi-neuralnetworkruntime-nn-tensor.md) through [OH_NNTensor_CreateWithFd](capi-neural-network-core-h.md#oh_nntensor_createwithfd).<br> if <b>tensor</b> or <b>fd</b> is a null pointer, this method will return error code.

**System capability**: SystemCapability.AI.NeuralNetworkRuntime

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| const NN_Tensor *tensor | Pointer to the [NN_Tensor](capi-neuralnetworkruntime-nn-tensor.md) instance. |
| int *fd | The returned file descriptor of the shared memory. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_NN_ReturnCode | Execution result of the function. If the operation is successful, <b>OH_NN_SUCCESS</b> is returned.          If the operation fails, an error code is returned. For details about the error codes,          see [OH_NN_ReturnCode](capi-neural-network-runtime-type-h.md#oh_nn_returncode). |

### OH_NNTensor_GetSize()

```c
OH_NN_ReturnCode OH_NNTensor_GetSize(const NN_Tensor *tensor, size_t *size)
```

**Description**

Gets the size of the shared memory of a [NN_Tensor](capi-neuralnetworkruntime-nn-tensor.md).<br> The <b>size</b> corresponds to the shared memory of the tensor data, and can be resued by another [NN_Tensor](capi-neuralnetworkruntime-nn-tensor.md) through [OH_NNTensor_CreateWithFd](capi-neural-network-core-h.md#oh_nntensor_createwithfd).<br> The <b>size</b> is as same as the argument <b>size</b> of [OH_NNTensor_CreateWithSize](capi-neural-network-core-h.md#oh_nntensor_createwithsize) and [OH_NNTensor_CreateWithFd](capi-neural-network-core-h.md#oh_nntensor_createwithfd). But for a tensor created by [OH_NNTensor_Create](capi-neural-network-core-h.md#oh_nntensor_create), it equals to the tensor byte size.<br> Note that the real tensor data only uses the segment [offset, size) of the shared memory. The offset can be got by [OH_NNTensor_GetOffset](capi-neural-network-core-h.md#oh_nntensor_getoffset) and the size can be got by [OH_NNTensor_GetSize](capi-neural-network-core-h.md#oh_nntensor_getsize).<br> if <b>tensor</b> or <b>size</b> is a null pointer, this method will return error code.

**System capability**: SystemCapability.AI.NeuralNetworkRuntime

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| const NN_Tensor *tensor | Pointer to the [NN_Tensor](capi-neuralnetworkruntime-nn-tensor.md) instance. |
| size_t *size | The returned size of tensor data. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_NN_ReturnCode | Execution result of the function. If the operation is successful, <b>OH_NN_SUCCESS</b> is returned.          If the operation fails, an error code is returned. For details about the error codes,          see [OH_NN_ReturnCode](capi-neural-network-runtime-type-h.md#oh_nn_returncode). |

### OH_NNTensor_GetOffset()

```c
OH_NN_ReturnCode OH_NNTensor_GetOffset(const NN_Tensor *tensor, size_t *offset)
```

**Description**

Get the data offset of a tensor.<br> The <b>offset</b> corresponds to the shared memory of the tensor data, and can be resued by another [NN_Tensor](capi-neuralnetworkruntime-nn-tensor.md) through [OH_NNTensor_CreateWithFd](capi-neural-network-core-h.md#oh_nntensor_createwithfd).<br> Note that the real tensor data only uses the segment [offset, size) of the shared memory. The offset can be got by [OH_NNTensor_GetOffset](capi-neural-network-core-h.md#oh_nntensor_getoffset) and the size can be got by [OH_NNTensor_GetSize](capi-neural-network-core-h.md#oh_nntensor_getsize).<br> if <b>tensor</b> or <b>offset</b> is a null pointer, this method will return error code.

**System capability**: SystemCapability.AI.NeuralNetworkRuntime

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| const NN_Tensor *tensor | Pointer to the [NN_Tensor](capi-neuralnetworkruntime-nn-tensor.md) instance. |
| size_t *offset | The returned offset of tensor data. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_NN_ReturnCode | Execution result of the function. If the operation is successful, <b>OH_NN_SUCCESS</b> is returned.          If the operation fails, an error code is returned. For details about the error codes,          see [OH_NN_ReturnCode](capi-neural-network-runtime-type-h.md#oh_nn_returncode). |

### OH_NNExecutor_Construct()

```c
OH_NNExecutor *OH_NNExecutor_Construct(OH_NNCompilation *compilation)
```

**Description**

Creates an executor instance of the [OH_NNExecutor](capi-neuralnetworkruntime-oh-nnexecutor.md) type.<br> This method constructs a model inference executor associated with the device based on the passed compilation. <br> After the [OH_NNExecutor](capi-neuralnetworkruntime-oh-nnexecutor.md) instance is created, you can release the [OH_NNCompilation](capi-neuralnetworkruntime-oh-nncompilation.md) instance if you do not need to create any other executors.

**System capability**: SystemCapability.AI.NeuralNetworkRuntime

**Since**: 9

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_NNCompilation *compilation | Pointer to the [OH_NNCompilation](capi-neuralnetworkruntime-oh-nncompilation.md) instance. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_NNExecutor * | Pointer to a [OH_NNExecutor](capi-neuralnetworkruntime-oh-nnexecutor.md) instance, or NULL if it fails to create. |

### OH_NNExecutor_GetOutputShape()

```c
OH_NN_ReturnCode OH_NNExecutor_GetOutputShape(OH_NNExecutor *executor, uint32_t outputIndex, int32_t **shape, uint32_t *shapeLength)
```

**Description**

Obtains the dimension information about the output tensor.<br> After [OH_NNExecutor_Run](capi-neural-network-runtime-h.md#oh_nnexecutor_run) is called to complete a single inference, call this method to obtain the specified output dimension information and number of dimensions. It is commonly used in dynamic shape input and output scenarios.<br> If the <b>outputIndex</b> is greater than or equal to the output tensor number, this method will return error code. The output tensor number can be got by [OH_NNExecutor_GetOutputCount](capi-neural-network-core-h.md#oh_nnexecutor_getoutputcount).<br> As an output parameter, <b>*shape</b> must be a null pointer, otherwise the method will return an error code. Fou example, you should define int32_t* tensorShape = NULL, and pass &tensorShape as the argument of <b>shape</b>.<br> You do not need to release the memory of <b>shape</b>. It will be released when <b>executor</b> is destroied.

**System capability**: SystemCapability.AI.NeuralNetworkRuntime

**Since**: 9

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_NNExecutor *executor | Pointer to the [OH_NNExecutor](capi-neuralnetworkruntime-oh-nnexecutor.md) instance. |
| uint32_t outputIndex | Output Index value, which is in the same sequence of the data output when [OH_NNModel_SpecifyInputsAndOutputs](capi-neural-network-runtime-h.md#oh_nnmodel_specifyinputsandoutputs) is called.<br>                   Assume that <b>outputIndices</b> is <b>{4, 6, 8}</b> when<br>                   [OH_NNModel_SpecifyInputsAndOutputs](capi-neural-network-runtime-h.md#oh_nnmodel_specifyinputsandoutputs) is called.<br>                   When [OH_NNExecutor_GetOutputShape](capi-neural-network-core-h.md#oh_nnexecutor_getoutputshape) is called to obtain dimension information about the output tensor, <b>outputIndices</b> is <b>{0, 1, 2}</b>. |
| int32_t **shape | Pointer to the int32_t array. The value of each element in the array is the length of the output tensor in each dimension. |
| uint32_t *shapeLength | Pointer to the uint32_t type. The number of output dimensions is returned. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_NN_ReturnCode | Execution result of the function. If the operation is successful, <b>OH_NN_SUCCESS</b> is returned.          If the operation fails, an error code is returned. For details about the error codes,          see [OH_NN_ReturnCode](capi-neural-network-runtime-type-h.md#oh_nn_returncode). |

### OH_NNExecutor_Destroy()

```c
void OH_NNExecutor_Destroy(OH_NNExecutor **executor)
```

**Description**

Destroys an executor instance to release the memory occupied by the executor.<br> This method needs to be called to release the executor instance created by calling [OH_NNExecutor_Construct](capi-neural-network-core-h.md#oh_nnexecutor_construct). Otherwise, the memory leak will occur. <br> If <b>executor</b> or <b>*executor</b> is a null pointer, this method only prints warning logs and does not execute the release.

**System capability**: SystemCapability.AI.NeuralNetworkRuntime

**Since**: 9

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_NNExecutor **executor | Double pointer to the [OH_NNExecutor](capi-neuralnetworkruntime-oh-nnexecutor.md) instance. |

### OH_NNExecutor_GetInputCount()

```c
OH_NN_ReturnCode OH_NNExecutor_GetInputCount(const OH_NNExecutor *executor, size_t *inputCount)
```

**Description**

Gets the input tensor count.<br> You can get the input tensor count from the executor, and then create an input tensor descriptor with its index by [OH_NNExecutor_CreateInputTensorDesc](capi-neural-network-core-h.md#oh_nnexecutor_createinputtensordesc).

**System capability**: SystemCapability.AI.NeuralNetworkRuntime

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| const OH_NNExecutor *executor | Pointer to the [OH_NNExecutor](capi-neuralnetworkruntime-oh-nnexecutor.md) instance. |
| size_t *inputCount | Input tensor count returned. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_NN_ReturnCode | Execution result of the function. If the operation is successful, <b>OH_NN_SUCCESS</b> is returned.          If the operation fails, an error code is returned.          For details about the error codes, see [OH_NN_ReturnCode](capi-neural-network-runtime-type-h.md#oh_nn_returncode). |

### OH_NNExecutor_GetOutputCount()

```c
OH_NN_ReturnCode OH_NNExecutor_GetOutputCount(const OH_NNExecutor *executor, size_t *outputCount)
```

**Description**

Gets the output tensor count.<br> You can get the output tensor count from the executor, and then create an output tensor descriptor with its index by [OH_NNExecutor_CreateOutputTensorDesc](capi-neural-network-core-h.md#oh_nnexecutor_createoutputtensordesc).

**System capability**: SystemCapability.AI.NeuralNetworkRuntime

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| const OH_NNExecutor *executor | Pointer to the [OH_NNExecutor](capi-neuralnetworkruntime-oh-nnexecutor.md) instance. |
| OutputCount | Output tensor count returned. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_NN_ReturnCode | Execution result of the function. If the operation is successful, <b>OH_NN_SUCCESS</b> is returned.          If the operation fails, an error code is returned.          For details about the error codes, see [OH_NN_ReturnCode](capi-neural-network-runtime-type-h.md#oh_nn_returncode). |

### OH_NNExecutor_CreateInputTensorDesc()

```c
NN_TensorDesc *OH_NNExecutor_CreateInputTensorDesc(const OH_NNExecutor *executor, size_t index)
```

**Description**

Creates an input tensor descriptor with its index.<br> The input tensor descriptor contains all attributes of the input tensor. If the <b>index</b> is greater than or equal to the input tensor number, this method will return error code. The input tensor number can be got by [OH_NNExecutor_GetInputCount](capi-neural-network-core-h.md#oh_nnexecutor_getinputcount).

**System capability**: SystemCapability.AI.NeuralNetworkRuntime

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| const OH_NNExecutor *executor | Pointer to the [OH_NNExecutor](capi-neuralnetworkruntime-oh-nnexecutor.md) instance. |
| size_t index | Input tensor index. |

**Returns**:

| Type | Description |
| -- | -- |
| NN_TensorDesc * | Pointer to [NN_TensorDesc](capi-neuralnetworkruntime-nn-tensordesc.md) instance, or NULL if it fails to create. |

### OH_NNExecutor_CreateOutputTensorDesc()

```c
NN_TensorDesc *OH_NNExecutor_CreateOutputTensorDesc(const OH_NNExecutor *executor, size_t index)
```

**Description**

Creates an output tensor descriptor with its index.<br> The output tensor descriptor contains all attributes of the output tensor. If the <b>index</b> is greater than or equal to the output tensor number, this method will return error code. The output tensor number can be got by [OH_NNExecutor_GetOutputCount](capi-neural-network-core-h.md#oh_nnexecutor_getoutputcount).

**System capability**: SystemCapability.AI.NeuralNetworkRuntime

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| const OH_NNExecutor *executor | Pointer to the [OH_NNExecutor](capi-neuralnetworkruntime-oh-nnexecutor.md) instance. |
| size_t index | Output tensor index. |

**Returns**:

| Type | Description |
| -- | -- |
| NN_TensorDesc * | Pointer to [NN_TensorDesc](capi-neuralnetworkruntime-nn-tensordesc.md) instance, or NULL if it fails to create. |

### OH_NNExecutor_GetInputDimRange()

```c
OH_NN_ReturnCode OH_NNExecutor_GetInputDimRange(const OH_NNExecutor *executor, size_t index, size_t **minInputDims, size_t **maxInputDims, size_t *shapeLength)
```

**Description**

Gets the dimension ranges of an input tensor.<br> The supported dimension ranges of an input tensor with dynamic shape may be different among various devices. You can call this method to get the dimension ranges of the input tensor supported by the device. <b>*minInputDims</b> contains the minimum demensions of the input tensor, and <b>*maxInputDims</b> contains the maximum, e.g. if an input tensor has dynamic shape [-1, -1, -1, 3], its <b>*minInputDims</b> may be [1, 10, 10, 3] and <b>*maxInputDims</b> may be [100, 1024, 1024, 3] on the device.<br> If the <b>index</b> is greater than or equal to the input tensor number, this method will return error code. The input tensor number can be got by [OH_NNExecutor_GetInputCount](capi-neural-network-core-h.md#oh_nnexecutor_getinputcount).<br> As an output parameter, <b>*minInputDims</b> or <b>*maxInputDims</b> must be a null pointer, otherwise the method will return an error code. For example, you should define int32_t* minInDims = NULL, and pass &minInDims as the argument of <b>minInputDims</b>.<br> You do not need to release the memory of <b>*minInputDims</b> or <b>*maxInputDims</b>. It will be released when <b>executor</b> is destroied.

**System capability**: SystemCapability.AI.NeuralNetworkRuntime

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| const OH_NNExecutor *executor | Pointer to the [OH_NNExecutor](capi-neuralnetworkruntime-oh-nnexecutor.md) instance. |
| size_t index | Input tensor index. |
| size_t **minInputDims | Returned pointer to an array contains the minimum dimensions of the input tensor. |
| size_t **maxInputDims | Returned pointer to an array contains the maximum dimensions of the input tensor. |
| size_t *shapeLength | Returned length of the shape of input tensor. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_NN_ReturnCode | Execution result of the function. If the operation is successful, <b>OH_NN_SUCCESS</b> is returned.          If the operation fails, an error code is returned. For details about the error codes,          see [OH_NN_ReturnCode](capi-neural-network-runtime-type-h.md#oh_nn_returncode). |

### OH_NNExecutor_SetOnRunDone()

```c
OH_NN_ReturnCode OH_NNExecutor_SetOnRunDone(OH_NNExecutor *executor, NN_OnRunDone onRunDone)
```

**Description**

Sets the callback function handle for the post-process when the asynchronous execution has been done.<br> The definition fo the callback function: [NN_OnRunDone](capi-neural-network-runtime-type-h.md#nn_onrundone).

**System capability**: SystemCapability.AI.NeuralNetworkRuntime

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_NNExecutor *executor | Pointer to the [OH_NNExecutor](capi-neuralnetworkruntime-oh-nnexecutor.md) instance. |
| NN_OnRunDone onRunDone | Callback function handle [NN_OnRunDone](capi-neural-network-runtime-type-h.md#nn_onrundone). |

**Returns**:

| Type | Description |
| -- | -- |
| OH_NN_ReturnCode | Execution result of the function. If the operation is successful, <b>OH_NN_SUCCESS</b> is returned.          If the operation fails, an error code is returned.          For details about the error codes, see [OH_NN_ReturnCode](capi-neural-network-runtime-type-h.md#oh_nn_returncode). |

### OH_NNExecutor_SetOnServiceDied()

```c
OH_NN_ReturnCode OH_NNExecutor_SetOnServiceDied(OH_NNExecutor *executor, NN_OnServiceDied onServiceDied)
```

**Description**

Sets the callback function handle for the post-process when the device driver service is dead during asynchronous execution.<br> The definition fo the callback function: [NN_OnServiceDied](capi-neural-network-runtime-type-h.md#nn_onservicedied).

**System capability**: SystemCapability.AI.NeuralNetworkRuntime

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_NNExecutor *executor | Pointer to the [OH_NNExecutor](capi-neuralnetworkruntime-oh-nnexecutor.md) instance. |
| NN_OnServiceDied onServiceDied | Callback function handle [NN_OnServiceDied](capi-neural-network-runtime-type-h.md#nn_onservicedied). |

**Returns**:

| Type | Description |
| -- | -- |
| OH_NN_ReturnCode | Execution result of the function. If the operation is successful, <b>OH_NN_SUCCESS</b> is returned.          If the operation fails, an error code is returned.          For details about the error codes, see [OH_NN_ReturnCode](capi-neural-network-runtime-type-h.md#oh_nn_returncode). |

### OH_NNExecutor_RunSync()

```c
OH_NN_ReturnCode OH_NNExecutor_RunSync(OH_NNExecutor *executor, NN_Tensor *inputTensor[], size_t inputCount, NN_Tensor *outputTensor[], size_t outputCount)
```

**Description**

Synchronous execution of the model inference.<br> Input and output tensors should be created first by [OH_NNTensor_Create](capi-neural-network-core-h.md#oh_nntensor_create), [OH_NNTensor_CreateWithSize](capi-neural-network-core-h.md#oh_nntensor_createwithsize) or [OH_NNTensor_CreateWithFd](capi-neural-network-core-h.md#oh_nntensor_createwithfd). And then the input tensors data which is got by [OH_NNTensor_GetDataBuffer](capi-neural-network-core-h.md#oh_nntensor_getdatabuffer) must be filled. The executor will then yield out the results by inference execution and fill them into output tensors data for you to read. <br> In the case of dynamic shape, you can get the real output shape directly by [OH_NNExecutor_GetOutputShape](capi-neural-network-core-h.md#oh_nnexecutor_getoutputshape), or you can create a tensor descriptor from an output tensor by [OH_NNTensor_GetTensorDesc](capi-neural-network-core-h.md#oh_nntensor_gettensordesc), and then read its real shape by [OH_NNTensorDesc_GetShape](capi-neural-network-core-h.md#oh_nntensordesc_getshape).

**System capability**: SystemCapability.AI.NeuralNetworkRuntime

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_NNExecutor *executor | Pointer to the [OH_NNExecutor](capi-neuralnetworkruntime-oh-nnexecutor.md) instance. |
| NN_Tensor *inputTensor[] | An array of input tensors [NN_Tensor](capi-neuralnetworkruntime-nn-tensor.md). |
| size_t inputCount | Number of input tensors. |
| NN_Tensor *outputTensor[] | An array of output tensors [NN_Tensor](capi-neuralnetworkruntime-nn-tensor.md). |
| size_t outputCount | Number of output tensors. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_NN_ReturnCode | Execution result of the function. If the operation is successful, <b>OH_NN_SUCCESS</b> is returned.          If the operation fails, an error code is returned.          For details about the error codes, see [OH_NN_ReturnCode](capi-neural-network-runtime-type-h.md#oh_nn_returncode). |

### OH_NNExecutor_RunAsync()

```c
OH_NN_ReturnCode OH_NNExecutor_RunAsync(OH_NNExecutor *executor, NN_Tensor *inputTensor[], size_t inputCount, NN_Tensor *outputTensor[], size_t outputCount, int32_t timeout, void *userData)
```

**Description**

Asynchronous execution of the model inference.<br> Input and output tensors should be created first by [OH_NNTensor_Create](capi-neural-network-core-h.md#oh_nntensor_create), [OH_NNTensor_CreateWithSize](capi-neural-network-core-h.md#oh_nntensor_createwithsize) or [OH_NNTensor_CreateWithFd](capi-neural-network-core-h.md#oh_nntensor_createwithfd). And then the input tensors data which is got by [OH_NNTensor_GetDataBuffer](capi-neural-network-core-h.md#oh_nntensor_getdatabuffer) must be filled. The executor will yield out the results by inference execution and fill them into output tensors data for you to read.<br> In the case of dynamic shape, you can get the real output shape directly by [OH_NNExecutor_GetOutputShape](capi-neural-network-core-h.md#oh_nnexecutor_getoutputshape), or you can create a tensor descriptor from an output tensor by [OH_NNTensor_GetTensorDesc](capi-neural-network-core-h.md#oh_nntensor_gettensordesc), and then read its real shape by [OH_NNTensorDesc_GetShape](capi-neural-network-core-h.md#oh_nntensordesc_getshape).<br> The method is non-blocked and will return immediately.<br> The callback function handles are set by [OH_NNExecutor_SetOnRunDone](capi-neural-network-core-h.md#oh_nnexecutor_setonrundone) and [OH_NNExecutor_SetOnServiceDied](capi-neural-network-core-h.md#oh_nnexecutor_setonservicedied). The inference results and error code can be got by [NN_OnRunDone](capi-neural-network-runtime-type-h.md#nn_onrundone). And you can deal with the abnormal termination of device driver service during asynchronous execution by [NN_OnServiceDied](capi-neural-network-runtime-type-h.md#nn_onservicedied).<br> If the execution time reaches the <b>timeout</b>, the execution will be terminated with no outputs, and the <b>errCode<b> returned in callback function [NN_OnRunDone](capi-neural-network-runtime-type-h.md#nn_onrundone) will be [OH_NN_TIMEOUT](capi-neural-network-runtime-type-h.md#oh_nn_returncode).<br> The <b>userData</b> is asynchronous execution identifier and will be returned as the first parameter of the callback function. You can input any value you want as long as it can identify different asynchronous executions.

**System capability**: SystemCapability.AI.NeuralNetworkRuntime

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_NNExecutor *executor | Pointer to the [OH_NNExecutor](capi-neuralnetworkruntime-oh-nnexecutor.md) instance. |
| NN_Tensor *inputTensor[] | An array of input tensors [NN_Tensor](capi-neuralnetworkruntime-nn-tensor.md). |
| size_t inputCount | Number of input tensors. |
| NN_Tensor *outputTensor[] | An array of output tensors [NN_Tensor](capi-neuralnetworkruntime-nn-tensor.md). |
| size_t outputCount | Number of output tensors. |
| int32_t timeout | Time limit (millisecond) of the asynchronous execution, e.g. 1000. |
| void *userData | Asynchronous execution identifier. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_NN_ReturnCode | Execution result of the function. If the operation is successful, <b>OH_NN_SUCCESS</b> is returned.          If the operation fails, an error code is returned. For details about the error codes,          see [OH_NN_ReturnCode](capi-neural-network-runtime-type-h.md#oh_nn_returncode). |

### OH_NNDevice_GetAllDevicesID()

```c
OH_NN_ReturnCode OH_NNDevice_GetAllDevicesID(const size_t **allDevicesID, uint32_t *deviceCount)
```

**Description**

Obtains the IDs of all devices connected.<br> Each device has an unique and fixed ID. This method returns device IDs on the current device through the uint32_t array.<br> Device IDs are returned through the size_t array. Each element of the array is the ID of a single device.<br> The array memory is managed inside, so you do not need to care about it. The data pointer is valid before this method is called next time.

**System capability**: SystemCapability.AI.NeuralNetworkRuntime

**Since**: 9

**Parameters**:

| Parameter | Description |
| -- | -- |
| const size_t **allDevicesID | Pointer to the size_t array. The input <b>*allDevicesID</b> must be a null pointer. Otherwise, [OH_NN_INVALID_PARAMETER](capi-neural-network-runtime-type-h.md#oh_nn_returncode) is returned. |
| uint32_t *deviceCount | Pointer of the uint32_t type, which is used to return the length of <b>*allDevicesID</b>. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_NN_ReturnCode | Execution result of the function. If the operation is successful, <b>OH_NN_SUCCESS</b> is returned.          If the operation fails, an error code is returned. For details about the error codes,          see [OH_NN_ReturnCode](capi-neural-network-runtime-type-h.md#oh_nn_returncode). |

### OH_NNDevice_GetName()

```c
OH_NN_ReturnCode OH_NNDevice_GetName(size_t deviceID, const char **name)
```

**Description**

Obtains the name of the specified device.<br> <b>deviceID</b> specifies the device whose name will be obtained. The device ID needs to be obtained by calling [OH_NNDevice_GetAllDevicesID](capi-neural-network-core-h.md#oh_nndevice_getalldevicesid). If it is 0, the first device in the current device list will be used by default.<br> The value of <b>*name</b> is a C-style string ended with <b>'\0'</b>. <b>*name</b> must be a null pointer. Otherwise, [OH_NN_INVALID_PARAMETER](capi-neural-network-runtime-type-h.md#oh_nn_returncode) is returned. Fou example, you should define char* deviceName = NULL, and pass &deviceName as the argument of <b>name</b>.

**System capability**: SystemCapability.AI.NeuralNetworkRuntime

**Since**: 9

**Parameters**:

| Parameter | Description |
| -- | -- |
| size_t deviceID | Device ID. If it is 0, the first device in the current device list will be used by default. |
| const char **name | The device name returned. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_NN_ReturnCode | Execution result of the function. If the operation is successful, <b>OH_NN_SUCCESS</b> is returned.          If the operation fails, an error code is returned. For details about the error codes,          see [OH_NN_ReturnCode](capi-neural-network-runtime-type-h.md#oh_nn_returncode). |

### OH_NNDevice_GetType()

```c
OH_NN_ReturnCode OH_NNDevice_GetType(size_t deviceID, OH_NN_DeviceType *deviceType)
```

**Description**

Obtains the type information of the specified device.<br> <b>deviceID</b> specifies the device whose type will be obtained. If it is 0, the first device in the current device list will be used. Currently the following device types are supported: - <b>OH_NN_CPU</b>: CPU device. - <b>OH_NN_GPU</b>: GPU device. - <b>OH_NN_ACCELERATOR</b>: machine learning dedicated accelerator. - <b>OH_NN_OTHERS</b>: other hardware types.

**System capability**: SystemCapability.AI.NeuralNetworkRuntime

**Since**: 9

**Parameters**:

| Parameter | Description |
| -- | -- |
| size_t deviceID | Device ID. If it is 0, the first device in the current device list will be used by default. |
| OH_NN_DeviceType *deviceType | The device type [OH_NN_DeviceType](capi-neural-network-runtime-type-h.md#oh_nn_devicetype) returned. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_NN_ReturnCode | Execution result of the function. If the operation is successful, <b>OH_NN_SUCCESS</b> is returned.          If the operation fails, an error code is returned.          For details about the error codes, see [OH_NN_ReturnCode](capi-neural-network-runtime-type-h.md#oh_nn_returncode). |


