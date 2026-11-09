# native_audio_converter.h（系统接口）

## 概述

声明输入音频格式、输出音频格式底层数据结构和格式转换接口。

**库：** libohaudiosuite.so

**系统能力：** SystemCapability.Multimedia.Audio.SuiteEngine

**起始版本：** 26.0.0

**系统接口：** 此接口为系统接口。

**相关模块：** [OHAudioSuite](capi-audio-kit-ohaudiosuite.md)

## 汇总

### 函数

| 名称 | 描述 |
| -- | -- |
| [OH_AudioConverter_Result OH_AudioSuite_ConverterCreateEx(const OH_AudioSuite_ConverterFormatEx *inputFormat, const OH_AudioSuite_ConverterFormatEx *outputFormat, OH_AudioConverter **outOwnedConverter)（系统接口）](#oh_audiosuite_convertercreateex) | 创建支持扩展格式的音频转换器。<br>**系统接口：** 此接口为系统接口。 |
| [OH_AudioConverter_Result OH_AudioSuite_ConverterGetMinInOutSizes(OH_AudioConverter *converter, uint32_t *inputMinSize, uint32_t *outputMinSize)（系统接口）](#oh_audiosuite_convertergetmininoutsizes) | 计算保证输出为整数采样数的最小输入字节数及对应输出字节数。<br> 最小字节数由创建转换器时设置的输入和输出格式共同决定，与采样率、通道数、位深均相关。<br>**系统接口：** 此接口为系统接口。 |
| [OH_AudioConverter_Result OH_AudioSuite_ConverterDirectProcess(OH_AudioConverter *converter, const OH_AudioSuite_ConverterInputInfo *inData, OH_AudioSuite_ConverterOutputInfo *outData)（系统接口）](#oh_audiosuite_converterdirectprocess) | 执行音频格式转换，由调用方直接传入输入数据。<br> 该接口处理调用者直接传入的输入数据，每次调用最多支持输入1000ms长度的音频数据。 同一转换器实例不可同时通过[OH_AudioConverter_SetInputCallback](capi-native-audio-converter-h.md#oh_audioconverter_setinputcallback)设置回调或由本接口传入数据，二者只能选择一种。 当输入和输出采样率不同时，首次调用及每次调用[OH_AudioSuite_ConverterFlush](capi-native-audio-converter-h.md#oh_audiosuite_converterflush)后的首次调用， 会在输出数据前面填充一定长度的静音数据。采样率相同时不会填充。 填充静音数据的字节数可通过[OH_AudioSuite_ConverterGetDelaySize](capi-native-audio-converter-h.md#oh_audiosuite_convertergetdelaysize)获取。<br>**系统接口：** 此接口为系统接口。 |
| [OH_AudioConverter_Result OH_AudioSuite_ConverterGetDelaySize(OH_AudioConverter *converter, uint32_t *delaySize)（系统接口）](#oh_audiosuite_convertergetdelaysize) | 获取采样率转换时首次输出数据前面填充的静音数据字节数。<br> 需在[OH_AudioSuite_ConverterDirectProcess](capi-native-audio-converter-h.md#oh_audiosuite_converterdirectprocess)产生静音填充后调用。 调用[OH_AudioSuite_ConverterFlush](capi-native-audio-converter-h.md#oh_audiosuite_converterflush)后静音填充会重新产生。 采样率相同时返回0。<br>**系统接口：** 此接口为系统接口。 |
| [OH_AudioConverter_Result OH_AudioSuite_ConverterFlush(OH_AudioConverter *converter)（系统接口）](#oh_audiosuite_converterflush) | 清空音频转换器内部缓存和处理状态。<br> 当音频数据不连续时（例如快进、快退场景），或者在一个音频流处理结束前、重新开始一个新的音频流时， 需要调用此接口清空转换器内部缓存和处理状态。使转换器恢复到初始状态。 调用后转换器可继续接收新的音频数据进行转换，无需销毁重建。<br>**系统接口：** 此接口为系统接口。 |

## 函数说明

### OH_AudioSuite_ConverterCreateEx()

```c
OH_AudioConverter_Result OH_AudioSuite_ConverterCreateEx(const OH_AudioSuite_ConverterFormatEx *inputFormat, const OH_AudioSuite_ConverterFormatEx *outputFormat, OH_AudioConverter **outOwnedConverter)
```

**描述：**

创建支持扩展格式的音频转换器。

<!--Device-OH_AudioConverter_Result OH_AudioSuite_ConverterCreateEx(const OH_AudioSuite_ConverterFormatEx *inputFormat, const OH_AudioSuite_ConverterFormatEx *outputFormat, OH_AudioConverter **outOwnedConverter)--><!--Device-OH_AudioConverter_Result OH_AudioSuite_ConverterCreateEx(const OH_AudioSuite_ConverterFormatEx *inputFormat, const OH_AudioSuite_ConverterFormatEx *outputFormat, OH_AudioConverter **outOwnedConverter)-End-->

**系统能力：** SystemCapability.Multimedia.Audio.SuiteEngine

**起始版本：** 26.1.0

**资源释放：** [OH_AudioConverter_Destroy](#oh_audioconverter_destroy)

**系统接口：** 此接口为系统接口。

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [const OH_AudioSuite_ConverterFormatEx](capi-ohaudiosuite-oh-audiosuite-converterformatex.md) *inputFormat | [入参] 输入音频格式配置指针。不能为NULL，调用期间必须保持有效。 |
| [const OH_AudioSuite_ConverterFormatEx](capi-ohaudiosuite-oh-audiosuite-converterformatex.md) *outputFormat | [入参] 输出音频格式配置指针。不能为NULL，调用期间必须保持有效。 |
| [OH_AudioConverter](capi-ohaudiosuite-oh-audioconverterstruct.md) **outOwnedConverter | [出参] 用于接收创建的音频转换器实例的指针。调用方拥有该结果并必须使用 [OH_AudioConverter_Destroy](capi-native-audio-converter-h.md#oh_audioconverter_destroy)释放。不能为NULL，无需初始化。调用失败时不会写入内容。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| [OH_AudioConverter_Result](capi-native-audio-converter-h.md#oh_audioconverter_result) | <ul> <li>[AUDIOCONVERTER_SUCCESS](capi-native-audio-converter-h.md#oh_audioconverter_result) 执行成功。</li> <li>202 权限校验失败，非系统应用使用了系统API。</li> <li>[AUDIOCONVERTER_ERROR_INVALID_PARAM](capi-native-audio-converter-h.md#oh_audioconverter_result) 参数无效，可能原因如下：<br>1. inputFormat为NULL。<br>2. outputFormat为NULL。<br>3. outOwnedConverter为NULL。</li> <li>[AUDIOCONVERTER_ERROR_UNSUPPORTED_FORMAT](capi-native-audio-converter-h.md#oh_audioconverter_result) inputFormat/outputFormat中的音频格式不支持。</li> <li>[AUDIOCONVERTER_ERROR_MEMORY_ALLOC_FAILED](capi-native-audio-converter-h.md#oh_audioconverter_result) 内存分配失败。</li> </ul> |

### OH_AudioSuite_ConverterGetMinInOutSizes()

```c
OH_AudioConverter_Result OH_AudioSuite_ConverterGetMinInOutSizes(OH_AudioConverter *converter, uint32_t *inputMinSize, uint32_t *outputMinSize)
```

**描述：**

计算保证输出为整数采样数的最小输入字节数及对应输出字节数。<br> 最小字节数由创建转换器时设置的输入和输出格式共同决定，与采样率、通道数、位深均相关。

<!--Device-OH_AudioConverter_Result OH_AudioSuite_ConverterGetMinInOutSizes(OH_AudioConverter *converter, uint32_t *inputMinSize, uint32_t *outputMinSize)--><!--Device-OH_AudioConverter_Result OH_AudioSuite_ConverterGetMinInOutSizes(OH_AudioConverter *converter, uint32_t *inputMinSize, uint32_t *outputMinSize)-End-->

**系统能力：** SystemCapability.Multimedia.Audio.SuiteEngine

**起始版本：** 26.1.0

**系统接口：** 此接口为系统接口。

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AudioConverter](capi-ohaudiosuite-oh-audioconverterstruct.md) *converter | [入参] 由[OH_AudioSuite_ConverterCreateEx](capi-native-audio-converter-h.md#oh_audiosuite_convertercreateex)或[OH_AudioConverter_Create](capi-native-audio-converter-h.md#oh_audioconverter_create)创建的转换器实例。 不能为NULL，调用期间必须保持有效。 |
| uint32_t *inputMinSize | [出参] 返回最小输入字节数，单位为字节。不能为NULL，无需初始化；调用失败时不会写入内容。 |
| uint32_t *outputMinSize | [出参] 返回对应最小输出字节数，单位为字节。不能为NULL，无需初始化；调用失败时不会写入内容。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| [OH_AudioConverter_Result](capi-native-audio-converter-h.md#oh_audioconverter_result) | <ul> <li>[AUDIOCONVERTER_SUCCESS](capi-native-audio-converter-h.md#oh_audioconverter_result) 执行成功。</li> <li>202 权限校验失败，非系统应用使用了系统API。</li> <li>[AUDIOCONVERTER_ERROR_INVALID_PARAM](capi-native-audio-converter-h.md#oh_audioconverter_result) 参数无效，可能原因如下：<br>1. converter为NULL。<br>2. inputMinSize为NULL。<br>3. outputMinSize为NULL。</li> </ul> |

### OH_AudioSuite_ConverterDirectProcess()

```c
OH_AudioConverter_Result OH_AudioSuite_ConverterDirectProcess(OH_AudioConverter *converter, const OH_AudioSuite_ConverterInputInfo *inData, OH_AudioSuite_ConverterOutputInfo *outData)
```

**描述：**

执行音频格式转换，由调用方直接传入输入数据。<br> 该接口处理调用者直接传入的输入数据，每次调用最多支持输入1000ms长度的音频数据。 同一转换器实例不可同时通过[OH_AudioConverter_SetInputCallback](capi-native-audio-converter-h.md#oh_audioconverter_setinputcallback)设置回调或由本接口传入数据，二者只能选择一种。 当输入和输出采样率不同时，首次调用及每次调用[OH_AudioSuite_ConverterFlush](capi-native-audio-converter-h.md#oh_audiosuite_converterflush)后的首次调用， 会在输出数据前面填充一定长度的静音数据。采样率相同时不会填充。 填充静音数据的字节数可通过[OH_AudioSuite_ConverterGetDelaySize](capi-native-audio-converter-h.md#oh_audiosuite_convertergetdelaysize)获取。

<!--Device-OH_AudioConverter_Result OH_AudioSuite_ConverterDirectProcess(OH_AudioConverter *converter, const OH_AudioSuite_ConverterInputInfo *inData, OH_AudioSuite_ConverterOutputInfo *outData)--><!--Device-OH_AudioConverter_Result OH_AudioSuite_ConverterDirectProcess(OH_AudioConverter *converter, const OH_AudioSuite_ConverterInputInfo *inData, OH_AudioSuite_ConverterOutputInfo *outData)-End-->

**系统能力：** SystemCapability.Multimedia.Audio.SuiteEngine

**起始版本：** 26.1.0

**系统接口：** 此接口为系统接口。

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AudioConverter](capi-ohaudiosuite-oh-audioconverterstruct.md) *converter | [入参] 由[OH_AudioSuite_ConverterCreateEx](capi-native-audio-converter-h.md#oh_audiosuite_convertercreateex)或[OH_AudioConverter_Create](capi-native-audio-converter-h.md#oh_audioconverter_create)创建的转换器实例。 不能为NULL，调用期间必须保持有效。 |
| [const OH_AudioSuite_ConverterInputInfo](capi-ohaudiosuite-oh-audiosuite-converterinputinfo.md) *inData | [入参] 输入音频数据描述符指针。不能为NULL，调用期间必须保持有效。 **inData->size**为输入字节数，必须是[OH_AudioSuite_ConverterGetMinInOutSizes](capi-native-audio-converter-h.md#oh_audiosuite_convertergetmininoutsizes)返回的最小输入字节数的整数倍。 |
| [OH_AudioSuite_ConverterOutputInfo](capi-ohaudiosuite-oh-audiosuite-converteroutputinfo.md) *outData | [入参，出参] 输出音频数据描述符指针。不能为NULL，调用期间必须保持有效。 <br>调用者需分配输出缓冲区并设置**outData->data**和**outData->size**。 若**inData->size**是最小输入字节数的k倍，则**outData->size**必须大于最小输出字节数的k倍， 其中最小输入字节数和最小输出字节数由[OH_AudioSuite_ConverterGetMinInOutSizes](capi-native-audio-converter-h.md#oh_audiosuite_convertergetmininoutsizes)获取。 <br>转换结果写入**outData->data**，实际写入字节数通过**outData->writeSize**返回。 <br>调用失败时不会写入内容。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| [OH_AudioConverter_Result](capi-native-audio-converter-h.md#oh_audioconverter_result) | <ul> <li>[AUDIOCONVERTER_SUCCESS](capi-native-audio-converter-h.md#oh_audioconverter_result) 执行成功。</li> <li>202 权限校验失败，非系统应用使用了系统API。</li> <li>[AUDIOCONVERTER_ERROR_INVALID_PARAM](capi-native-audio-converter-h.md#oh_audioconverter_result) 参数无效，可能原因如下：<br>1. converter为NULL。<br>2. inData为NULL。<br>3. **inData->data**为NULL。<br>4. **inData->size**为0。<br>5. **inData->size**不是[OH_AudioSuite_ConverterGetMinInOutSizes](capi-native-audio-converter-h.md#oh_audiosuite_convertergetmininoutsizes)返回的最小输入字节数的整数倍。<br>6. **inData->size**对应的音频时长超过1000毫秒。<br>7. outData为NULL。<br>8. **outData->data**为NULL。</li> <li>[AUDIOCONVERTER_ERROR_UNSUPPORTED_OPERATION](capi-native-audio-converter-h.md#oh_audioconverter_result) 已通过[OH_AudioConverter_SetInputCallback](capi-native-audio-converter-h.md#oh_audioconverter_setinputcallback)设置回调。</li> <li>[AUDIOCONVERTER_ERROR_BUFFER_TOO_SMALL](capi-native-audio-converter-h.md#oh_audioconverter_result) 输出缓冲区不足。</li> <li>[AUDIOCONVERTER_ERROR_SYSTEM](capi-native-audio-converter-h.md#oh_audioconverter_result) 系统内部错误。</li> </ul> |

### OH_AudioSuite_ConverterGetDelaySize()

```c
OH_AudioConverter_Result OH_AudioSuite_ConverterGetDelaySize(OH_AudioConverter *converter, uint32_t *delaySize)
```

**描述：**

获取采样率转换时首次输出数据前面填充的静音数据字节数。<br> 需在[OH_AudioSuite_ConverterDirectProcess](capi-native-audio-converter-h.md#oh_audiosuite_converterdirectprocess)产生静音填充后调用。 调用[OH_AudioSuite_ConverterFlush](capi-native-audio-converter-h.md#oh_audiosuite_converterflush)后静音填充会重新产生。 采样率相同时返回0。

<!--Device-OH_AudioConverter_Result OH_AudioSuite_ConverterGetDelaySize(OH_AudioConverter *converter, uint32_t *delaySize)--><!--Device-OH_AudioConverter_Result OH_AudioSuite_ConverterGetDelaySize(OH_AudioConverter *converter, uint32_t *delaySize)-End-->

**系统能力：** SystemCapability.Multimedia.Audio.SuiteEngine

**起始版本：** 26.1.0

**系统接口：** 此接口为系统接口。

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AudioConverter](capi-ohaudiosuite-oh-audioconverterstruct.md) *converter | [入参] 由[OH_AudioSuite_ConverterCreateEx](capi-native-audio-converter-h.md#oh_audiosuite_convertercreateex)或[OH_AudioConverter_Create](capi-native-audio-converter-h.md#oh_audioconverter_create)创建的转换器实例。 不能为NULL，调用期间必须保持有效。 |
| uint32_t *delaySize | [出参] 返回首次输出数据前面填充的静音数据字节数，单位为字节。 不能为NULL，无需初始化；调用失败时不会写入内容。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| [OH_AudioConverter_Result](capi-native-audio-converter-h.md#oh_audioconverter_result) | <ul> <li>[AUDIOCONVERTER_SUCCESS](capi-native-audio-converter-h.md#oh_audioconverter_result) 执行成功。</li> <li>202 权限校验失败，非系统应用使用了系统API。</li> <li>[AUDIOCONVERTER_ERROR_INVALID_PARAM](capi-native-audio-converter-h.md#oh_audioconverter_result) 参数无效，可能原因如下：<br>1. converter为NULL。<br>2. delaySize为NULL。</li> </ul> |

### OH_AudioSuite_ConverterFlush()

```c
OH_AudioConverter_Result OH_AudioSuite_ConverterFlush(OH_AudioConverter *converter)
```

**描述：**

清空音频转换器内部缓存和处理状态。<br> 当音频数据不连续时（例如快进、快退场景），或者在一个音频流处理结束前、重新开始一个新的音频流时， 需要调用此接口清空转换器内部缓存和处理状态。使转换器恢复到初始状态。 调用后转换器可继续接收新的音频数据进行转换，无需销毁重建。

<!--Device-OH_AudioConverter_Result OH_AudioSuite_ConverterFlush(OH_AudioConverter *converter)--><!--Device-OH_AudioConverter_Result OH_AudioSuite_ConverterFlush(OH_AudioConverter *converter)-End-->

**系统能力：** SystemCapability.Multimedia.Audio.SuiteEngine

**起始版本：** 26.1.0

**系统接口：** 此接口为系统接口。

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AudioConverter](capi-ohaudiosuite-oh-audioconverterstruct.md) *converter | [入参] 由[OH_AudioSuite_ConverterCreateEx](capi-native-audio-converter-h.md#oh_audiosuite_convertercreateex)或[OH_AudioConverter_Create](capi-native-audio-converter-h.md#oh_audioconverter_create)创建的转换器实例。 不能为NULL，调用期间必须保持有效。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| [OH_AudioConverter_Result](capi-native-audio-converter-h.md#oh_audioconverter_result) | <ul> <li>[AUDIOCONVERTER_SUCCESS](capi-native-audio-converter-h.md#oh_audioconverter_result) 执行成功。</li> <li>202 权限校验失败，非系统应用使用了系统API。</li> <li>[AUDIOCONVERTER_ERROR_INVALID_PARAM](capi-native-audio-converter-h.md#oh_audioconverter_result) 参数无效，converter为NULL。</li> </ul> |


