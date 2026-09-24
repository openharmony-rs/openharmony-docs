# Using MindSpore Lite for Model Conversion

<!--Kit: MindSpore Lite Kit-->
<!--Subsystem: AI-->
<!--Owner: @zhuguodong8-->
<!--Designer: @zhuguodong8; @jjfeing-->
<!--Tester: @principal87-->
<!--Adviser: @ge-yafang-->
<!-- md-trans-meta sourceCommit=dca31322189f91fc40f262b55618120da7c83182 translatedAt=2026-09-17T08:10:07.949Z pushedAt=2026-09-21T11:20:02.476Z -->

## When to Use

The deployment process is as follows:
1. The developer first uses the MindSpore Lite model conversion tool to convert the original model (for example, ONNX or CAFFE) into a model file with the .ms extension. For the ONNX [operators](mindspore-lite-term.md#operator) supported by MindSpore Lite Kit, see the [MindSpore Lite Kit Operator Support List](mindspore-lite-supported-operators.md) to ensure successful model conversion.
2. Call APIs of the MindSpore Lite inference engine to perform [model inference](mindspore-lite-guidelines.md).

## Obtaining the Model Conversion Tool

You can obtain the MindSpore Lite model conversion tool in either of the following ways:

### Download

| Component                                                   | Hardware Platform| OS    | URL                                                        | SHA-256                                                      |
| ------------------------------------------------------- | -------- | ------------ | ------------------------------------------------------------ | ------------------------------------------------------------ |
| On-device inference and training benchmark tool, converter tool, and cropper tool| CPU      | Linux-x86_64 | [mindspore-lite-2.7.0-linux-x64.tar.gz](https://ms-release.obs.cn-north-4.myhuaweicloud.com/2.7.0/MindSporeLite/lite/release/linux/x86_64/mindspore-lite-2.7.0-linux-x64.tar.gz) | 8bb1097100c9fec12675670ba2d4264a2cd6da3a9be093eb56631d00fc0c455b |

### Source Code Building

> **NOTE**
>
> - Because the compilation option for supporting PyTorch model conversion is disabled by default, the downloaded installation package does not support PyTorch model conversion. It can be obtained only through source code building.
>
> - If the model contains transpose and convolution [operator fusion](mindspore-lite-term.md#operator-fusion), it must be obtained through source code building. Otherwise, a warning similar to the following may occur: node infer shape failed, node is Default/Conv2DFusion-xxx.
>
> - When the [NPU](mindspore-lite-term.md#npu) backend is specified for inference, you need to customize [disabling clip operator fusion](#disabling-the-fusion-of-specified-operators), and the model conversion tool must be obtained through source code building. Otherwise, an error similar to the following may occur: BuildKirinNPUModel# Create full model kernel failed.

1. The environment requirements are as follows:

   - System environment: Linux x86_64 (Ubuntu 18.04.02LTS recommended)
   - C++ build dependencies:
     -  GCC >= 7.3.0
     -  CMake >= 3.18.3
     -  Git >= 2.28.0

2. Obtain the [MindSpore Lite source code](https://gitcode.com/openharmony/third_party_mindspore). The complete source code of MindSpore Lite is available at `mindspore-src/source/`.

3. Start building.

   To obtain the conversion tool that supports PyTorch model conversion, run **export MSLITE_ENABLE_CONVERT_PYTORCH_MODEL=on && export LIB_TORCH_PATH="/home/user/libtorch"** before you begin model building. Add the libtorch environment variable by running **export LD_LIBRARY_PATH="/home/user/libtorch/lib:${LD_LIBRARY_PATH}"** before conversion. You can download the libtorch package of the CPU version and decompress it to `/home/user/libtorch`.

   ```bash
   cd mindspore-src/source/
   bash build.sh -I x86_64 -j 8
   ```

   After the building is complete, you can obtain the MindSpore Lite release package from `output/` in the root directory of the source code. The conversion tool is available at `tools/converter/converter/` after decompression.

## Configure environment variables.

After obtaining the model conversion tool, you need to add the dynamic link library (DLL) required by the conversion tool to the environment variable `LD_LIBRARY_PATH`.

```bash
export LD_LIBRARY_PATH=${PACKAGE_PATH}/tools/converter/lib:${LD_LIBRARY_PATH}
```

**${PACKAGE_PATH}** indicates the path where the MindSpore Lite release package is decompressed.


## Parameter Description

The MindSpore Lite model conversion tool provides multiple parameter settings. You can use them as required. In addition, you can run `./converter_lite --help` to obtain the help information in real time.

The following describes the parameters in detail.

|        Name       | Mandatory           | Description                                                    | Value Range                                        |
| :----------------: | ------------------- | ------------------------------------------------------------ | ------------------------------------------------ |
|       --help       | No                 | Displays all help information.                                          | -                                                |
|       --fmk        | Yes                 | Original format of the input model. MSLITE is supported only when an [MS model](mindspore-lite-term.md#ms-model) is converted to Micro code. | MINDIR, CAFFE, TFLITE, TF, ONNX, PYTORCH, MSLITE |
|    --modelFile     | Yes                 | Path of the input model.                                            | -                                                |
|    --outputFile    | Yes                 | Path of the output model. You do not need to add an extension because the extension `.ms` is automatically generated.           | -                                                |
|    --weightFile    | Yes for CAFFE model conversion| Path of the model weight file.                                    | -                                                |
|    --configFile    | No                  | 1) Can be used as the path of the [post-training quantization](mindspore-lite-term.md#post-training-quantization) configuration file; 2) can be used as the path of the extension feature configuration file. | -                                                |
|       --fp16       | No                  | Sets whether to store weights in float32 data format as float16 data format during model serialization.<br>The default value is off. | on, off                                          |
|    --inputShape    | No                  | Sets the dimensions of the model input. The order of the input dimensions is the same as that in the original model. For certain models, the model structure can be further optimized, but the converted model may lose the dynamic shape feature. The input name and shape are separated by `:`, multiple inputs are separated by `;`, and the whole value is enclosed in double quotation marks `""`. For example, configure it as "inTensorName_1: 1,32,32,4;inTensorName_2:1,64,64,4;". | -                                                |
| --inputDataFormat  | No                  | Sets the input format of the exported model. It is valid only for four-dimensional inputs.<br>The default value is NHWC. | NHWC, NCHW                                       |
|  --inputDataType   | No                  | Sets the data type of the input tensor of the quantized model. It is valid only when the quantization parameters (scale and zero point) of the model input tensor are configured. By default, it is the same as the data type of the input tensor of the original model.<br>The default value is DEFAULT. | FLOAT32, INT8, UINT8, DEFAULT                    |
|  --outputDataType  | No                  | Sets the data type of the output tensor of the quantized model. It is valid only when the quantization parameters (scale and zero point) of the model output tensor are configured. By default, it is the same as the data type of the output tensor of the original model.<br>The default value is DEFAULT. | FLOAT32, INT8, UINT8, DEFAULT                    |
| --outputDataFormat | No                  | Sets the output format of the exported model. It is valid only for four-dimensional outputs.<br>The default value is NHWC. | NHWC, NCHW                                       |

> **NOTE**
> - The parameter name and value are separated by an equal sign (=) and no space is allowed between them.
> - Generally, a CAFFE model has two files: the model structure `*.prototxt`, which corresponds to the `--modelFile` parameter, and the model weight `*.caffemodel`, which corresponds to the `--weightFile` parameter.

## Example

The following conversion command uses the CAFFE model LeNet as an example.

```bash
./converter_lite --fmk=CAFFE --modelFile=lenet.prototxt --weightFile=lenet.caffemodel --outputFile=lenet
```
In this example, the CAFFE model is used. Therefore, you need to specify two input files: model structure and model weight. In addition, add other mandatory parameters, that is, fmk type and output path.

The command output is as follows:

```bash
CONVERT RESULT SUCCESS:0
```
This indicates that the CAFFE model has been successfully converted into a MindSpore Lite model, and a new file `lenet.ms` is obtained.

## (Optional) Offline Model Conversion

When the deployment scenario has strict requirements on loading latency, developers may want to further reduce the loading latency. In this case, another deployment solution can be used, that is, inference based on the [offline model](mindspore-lite-term.md#offline-model). An offline model is a model converted using the offline model conversion tool provided by the hardware vendor, and it is parsed and inferred by the hardware vendor.

During inference, MindSpore Lite directly sends the offline model to the AI hardware connected to NNRt. This way, the model can be loaded without the need for online image composition, greatly reducing the model loading delay. In addition, MindSpore Lite can provide additional hardware-specific information to assist the AI hardware in model inference.

### Constraints

- Offline model inference can only be implemented at the NNRt backend. The AI hardware needs to connect to NNRt and support offline model inference.
- The offline model conversion tool can be obtained only through source code building.
- During offline model conversion, `fmk` must be set to `THIRDPARTY`.
- The offline model comes as a black box and cannot be directly parsed by the conversion tool to obtain its input and output tensor information. Therefore, you need to manually configure the tensor information in the extended configuration file of the conversion tool.

### Description of the Extended Configuration File

An example of the extended configuration is as follows:
- `[third_party_model]` in the first line is a fixed keyword that indicates the section of offline model configuration.
- The following lines exhibit the name, data type, shape, and memory format of the input and output tensors of the model respectively. Each field occupies a line and is expressed in the key-value pair format. The sequence of fields is not limited.
- Among the fields, data type and shape are mandatory, and other parameters are optional.
- Extended parameters are also provided. They are used to encapsulate custom configuration of the offline model into an .ms file in the key-value pair format. The .ms file is passed to the AI hardware by NNRt during inference.

```text
[third_party_model]
input_names=in_0;in_1
input_dtypes=float32;float32
input_shapes=8,256,256;8,256,256,3
input_formats=NCHW;NCHW
output_names=out_0
output_dtypes=float32
output_shapes=8,64
output_formats=NCHW
extended_parameters=key_foo:value_foo;key_bar:value_bar
```

Field description:

- `input_names` (optional): model input name, which is in the string format. If multiple names are specified, use a semicolon (;) to separate them.
- `input_dtypes` (mandatory): model input data type, which is in the type format. If multiple data types are specified, use a semicolon (;) to separate them.
- `input_shapes` (mandatory): model input shape, which is in the integer array format. If multiple input shapes are specified, use a semicolon (;) to separate them.
- `input_formats` (optional): model input memory format, which is in the string format. If multiple formats are specified, use a semicolon (;) to separate them. The default value is NHWC.
- `output_names` (optional): model output name, which is in the string format. If multiple outputs are specified, use a semicolon (`;`) to separate them.
- `output_dtypes` (mandatory): model output data type, which is in the type format. If multiple data types are specified, use a semicolon (;) to separate them.
- `output_shapes` (mandatory): model output shape, which is in the integer array format. If multiple output shapes are specified, use a semicolon (;) to separate them.
- `output_formats` (optional): model output memory layout, which is in the string format. If multiple outputs are specified, use a semicolon (`;`) to separate them. The default value is NHWC.
- `extended_parameters` (optional): custom configuration of the inference hardware, which is in the key-value pair format. It is passed to the AI hardware through the NNRt backend during inference.

## Appendix

### Disabling the Fusion of Specified Operators

If you need to disable the fusion of specified operators, create a configuration file, for example, **converter.cfg**, and configure and file content as follows:

```ini
[registry]
# If **disable_fusion** is set to **off**, you can configure **fusion_blacklists** to disable the fusion of specified operators. If **disable_fusion** is set to **on**, the fusion of operators is disabled, and **fusion_blacklists** does not take effect. The default value of **disable_fusion** is **off**.
disable_fusion=off
# To disable the fusion of multiple operators, separate the operators with commas (,).
fusion_blacklists=ConvActivationFusion,MatMulActivationFusion,clip_convert_activation_pass
```

When running the converter, set **configFile** to **converter.cfg**.

The following lists the operators for which fusion can be disabled:

- AddConcatActivationFusion
- SqueezeFusion
- TransposeFusion
- ReshapeReshapeFusion 
- ConvBiasaddFusion 
- ConvBatchNormFusion 
- ConvScaleFusion 
- GroupNormFusion 
- TfNormFusion 
- OnnxLayerNormFusion 
- OnnxLayerNormFusion2 
- BatchMatMulFusion 
- BatchNormToScaleFusion 
- SigmoidMulFusion 
- ActivationFusion 
- ConvActivationFusion 
- ConvTupleGetItemFusion 
- ConvTupleActivationFusion  
- TfliteLstmCellFusion 
- TfLstmCellFusion 
- TfBidirectionGruFusion 
- TfGeLUFusion 
- OnnxGeLUFusion 
- TfliteRelPosMultiHeadAttentionFusion  
- GLUFusion 
- ConstFoldPass 
- AffineFusion 
- AffineActivationFusion 
- ConvConvFusion 
- ConvPadFusion 
- MatMulAddFusion 
- MatMulMulFusion 
- TransposeMatMulFusion 
- MulAddFusion 
- ScaleActivationFusion 
- ScaleScaleFusion 
- FullConnectedFusion 
- FullconnectedAddFusion 
- TensorDotFusion 
- MatMulActivationFusion 
- clip_convert_activation_pass  