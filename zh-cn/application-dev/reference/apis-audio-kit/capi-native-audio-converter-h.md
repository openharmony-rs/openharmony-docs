# native_audio_converter.h
<!--Kit: Audio Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @xxngwang-->
<!--Designer: @jay-liusong-->
<!--Tester: @Filger-->
<!--Adviser: @w_Machine_cc-->

## 概述

声明输入音频格式、输出音频格式底层数据结构和格式转换接口。

**引用文件：** <ohaudiosuite/native_audio_converter.h>

**库：** libohaudiosuite.so

**系统能力：** SystemCapability.Multimedia.Audio.SuiteEngine

**起始版本：** 26.0.0

**相关模块：** [OHAudioSuite](capi-ohaudiosuite.md)

## 汇总

### 结构体

| 名称 | typedef关键字 | 描述 |
| -- | -- | -- |
| [OH_AudioConverter_Format](capi-audioconverter-oh-audioconverter-format.md) | OH_AudioConverter_Format | 定义音频格式转换器的数据结构，用于描述音频格式。|
| [OH_AudioConverterStruct](capi-audioconverter-oh-audioconverterstruct.md) | OH_AudioConverter | 声明音频格式转换器。<br> 音频格式转换器的句柄用于执行与其相关的功能。 |
|<!--DelRow--> [OH_AudioSuite_ConverterFormatEx](capi-ohaudiosuite-oh-audiosuite-converterformatex-sys.md) | OH_AudioSuite_ConverterFormatEx | 定义扩展音频转换器格式信息结构体。<br>**系统接口：** 此接口为系统接口。 |
|<!--DelRow--> [OH_AudioSuite_ConverterInputInfo](capi-ohaudiosuite-oh-audiosuite-converterinputinfo-sys.md) | OH_AudioSuite_ConverterInputInfo | 定义音频转换器输入数据结构体。<br>**系统接口：** 此接口为系统接口。 |
|<!--DelRow--> [OH_AudioSuite_ConverterOutputInfo](capi-ohaudiosuite-oh-audiosuite-converteroutputinfo-sys.md) | OH_AudioSuite_ConverterOutputInfo | 定义音频转换器输出数据结构体。<br>**系统接口：** 此接口为系统接口。 |

### 枚举

| 名称 | typedef关键字 | 描述 |
| -- | -- | -- |
| [OH_AudioConverter_Result](#oh_audioconverter_result) | OH_AudioConverter_Result | 定义函数执行的返回结果。 |
| [OH_AudioConverter_InputStatus](#oh_audioconverter_inputstatus) | OH_AudioConverter_InputStatus | 定义回调函数[OH_AudioConverter_RequestDataCallback](capi-native-audio-converter-h.md#oh_audioconverter_requestdatacallback)提供的输入音频数据的状态。转换器使用此状态来确定如何处理后续的转换逻辑。例如，继续提取数据，暂停或清除缓存数据。<br> 注意：即使回调返回AUDIOCONVERTER_INPUT_DATA_FINISHED，也必须重复调用OH_AudioConverter_Process，直到[OH_AudioConverter_Process](capi-native-audio-converter-h.md#oh_audioconverter_process)返回AUDIOCONVERTER_SUCCESS，并且outputSize=0（表示所有缓存数据均已处理完成）。 |

### 函数

| 名称 | typedef关键字 | 描述 |
| -- | -- | -- |
| [OH_AudioConverter_Result OH_AudioConverter_Create(const OH_AudioConverter_Format* inputFormat, const OH_AudioConverter_Format* outputFormat, OH_AudioConverter** converter)](#oh_audioconverter_create) | - | 创建音频格式转换器。 |
| [void OH_AudioConverter_Destroy(OH_AudioConverter* converter)](#oh_audioconverter_destroy) | - | 销毁音频格式转换器。 |
| [typedef int32_t (\*OH_AudioConverter_RequestDataCallback)(void* userData, const void** outInputData, OH_AudioConverter_InputStatus* outStatus)](#oh_audioconverter_requestdatacallback) | OH_AudioConverter_RequestDataCallback | 请求数据的回调函数。转换器在[OH_AudioConverter_Process](capi-native-audio-converter-h.md#oh_audioconverter_process)期间调用此回调函数以主动请求输入音频数据。<br> 调用者必须填充输出参数（outInputData，outStatus），并返回通过回调函数读取的数据大小。<br> 单个回调返回的最大数据大小为400KB。<br> outInputData指向的内存必须保持有效，直到OH_AudioConverter_Process返回处理完成为止。 |
| [OH_AudioConverter_Result OH_AudioConverter_SetInputCallback(OH_AudioConverter* converter, OH_AudioConverter_RequestDataCallback callback, void* userData)](#oh_audioconverter_setinputcallback) | - | 设置转换器请求数据回调函数。此函数绑定音频格式转换器的输入数据回调函数。回调函数由[OH_AudioConverter_Process](capi-native-audio-converter-h.md#oh_audioconverter_process)调用，获取输入音频数据并进行处理。 |
| [OH_AudioConverter_Result OH_AudioConverter_Process(OH_AudioConverter* converter, void* outputData, int32_t outputCapacity, int32_t* outputSize)](#oh_audioconverter_process) | - | 执行音频格式转换处理函数。该函数执行音频转换过程，将输入音频转换为目标格式，需要注意：该函数必须在[OH_AudioConverter_SetInputCallback](capi-native-audio-converter-h.md#oh_audioconverter_setinputcallback)之后调用，并且最终转换结果写入的输出缓冲区必须由调用方分配和管理。即使回调返回AUDIOCONVERTER_INPUT_DATA_FINISHED，也必须重复调用此函数，直到返回AUDIOCONVERTER_SUCCESS且outputSize=0（表示所有缓存数据均已处理完成）。 |
|<!--DelRow--> [OH_AudioConverter_Result OH_AudioSuite_ConverterCreateEx(const OH_AudioSuite_ConverterFormatEx *inputFormat, const OH_AudioSuite_ConverterFormatEx *outputFormat, OH_AudioConverter **outOwnedConverter)](#oh_audiosuite_convertercreateex) | - | 创建支持扩展格式的音频转换器。<br>**系统接口：** 此接口为系统接口。 |
|<!--DelRow--> [OH_AudioConverter_Result OH_AudioSuite_ConverterGetMinInOutSizes(OH_AudioConverter *converter, uint32_t *inputMinSize, uint32_t *outputMinSize)](#oh_audiosuite_convertergetmininoutsizes) | - | 计算保证输出为整数采样点数的最小输入字节数及对应输出字节数。<br> 最小字节数由创建转换器时设置的输入和输出格式共同决定，与采样率、通道数、位深均相关。<br>**系统接口：** 此接口为系统接口。 |
|<!--DelRow--> [OH_AudioConverter_Result OH_AudioSuite_ConverterDirectProcess(OH_AudioConverter *converter, const OH_AudioSuite_ConverterInputInfo *inData, OH_AudioSuite_ConverterOutputInfo *outData)](#oh_audiosuite_converterdirectprocess) | - | 执行音频格式转换，由调用方直接传入输入数据。<br> 该接口处理调用者直接传入的输入数据，每次调用最多支持输入1000毫秒长度的音频数据。同一转换器实例不可同时通过[OH_AudioConverter_SetInputCallback](capi-native-audio-converter-h.md#oh_audioconverter_setinputcallback)设置回调或由本接口传入数据，二者只能选择一种。当输入和输出采样率不同时，首次调用及每次调用[OH_AudioSuite_ConverterFlush](#oh_audiosuite_converterflush)后的首次调用， 会在输出数据前面填充一定长度的静音数据。采样率相同时不会填充。填充静音数据的字节数可通过[OH_AudioSuite_ConverterGetDelaySize](#oh_audiosuite_convertergetdelaysize)获取。<br>**系统接口：** 此接口为系统接口。 |
|<!--DelRow--> [OH_AudioConverter_Result OH_AudioSuite_ConverterGetDelaySize(OH_AudioConverter *converter, uint32_t *delaySize)](#oh_audiosuite_convertergetdelaysize) | - | 获取采样率转换时首次输出数据前面填充的静音数据字节数。<br> 需在[OH_AudioSuite_ConverterDirectProcess](#oh_audiosuite_converterdirectprocess)产生静音填充后调用。 调用[OH_AudioSuite_ConverterFlush](#oh_audiosuite_converterflush)后静音填充会重新产生。采样率相同时返回0。<br>**系统接口：** 此接口为系统接口。 |
|<!--DelRow--> [OH_AudioConverter_Result OH_AudioSuite_ConverterFlush(OH_AudioConverter *converter)](#oh_audiosuite_converterflush) | - | 清空音频转换器内部缓存和处理状态。<br> 当音频数据不连续时（例如快进、快退场景），或在一个音频流处理结束前需要重新开始新的音频流时，需要调用此接口清空转换器内部缓存和处理状态，使转换器恢复到初始状态。调用后转换器可继续接收新的音频数据进行转换，无需销毁重建。<br>**系统接口：** 此接口为系统接口。 |

## 枚举类型说明

### OH_AudioConverter_Result

```c
enum OH_AudioConverter_Result
```

**描述**

定义函数执行的返回结果。

**起始版本：** 26.0.0

| 枚举项 | 描述 |
| -- | -- |
| AUDIOCONVERTER_SUCCESS = 0 |  函数调用成功。<br>**起始版本：** 26.0.0 |
| AUDIOCONVERTER_ERROR_INVALID_PARAM = 1 |  函数输入参数无效。例如传入的音频格式转换器指针为nullptr。<br>**起始版本：** 26.0.0 |
| AUDIOCONVERTER_ERROR_UNSUPPORTED_FORMAT = 2 |  不支持的音频格式。例如不支持的编码类型、采样格式等。<br>**起始版本：** 26.0.0 |
| AUDIOCONVERTER_ERROR_SYSTEM = 3 |  系统错误。例如使用已销毁的音频格式转换器执行格式转换。<br>**起始版本：** 26.0.0 |
| AUDIOCONVERTER_ERROR_MEMORY_ALLOC_FAILED = 4 |  内存分配失败。例如内部输出数据缓冲区内存分配失败。<br>**起始版本：** 26.0.0 |
| AUDIOCONVERTER_ERROR_BUFFER_TOO_SMALL = 5 |  输出缓存容量不足。例如设置的存储输出数据的容量不足以存储一帧输出数据量。<br>**起始版本：** 26.0.0 |
| AUDIOCONVERTER_ERROR_NOT_INITIALIZED = 6 |  音频格式转换器实例未初始化。例如未创建音频格式转换器直接执行格式转换处理函数。<br>**起始版本：** 26.0.0 |
| AUDIOCONVERTER_ERROR_CALLBACK_INVALID = 7 |  输入回调函数无效。例如输入回调函数返回数据量小于0或大于最大值400KB。<br>**起始版本：** 26.0.0 |
| AUDIOCONVERTER_ERROR_CALLBACK_NOT_SET = 8 |  未设置回调函数。例如输入回调函数指针为nullptr。<br>**起始版本：** 26.0.0 |
| AUDIOCONVERTER_ERROR_NOT_SYSTEM_APP = 202 |  权限校验失败，非系统应用调用了系统API。<br>**起始版本：** 26.1.0 |
| AUDIOCONVERTER_ERROR_UNSUPPORTED_OPERATION = 6800104 |  操作不支持。例如在已设置输入回调的情况下再以直接传入数据的方式处理音频。<br>**起始版本：** 26.1.0 |

### OH_AudioConverter_InputStatus

```c
enum OH_AudioConverter_InputStatus
```

**描述**

定义回调函数[OH_AudioConverter_RequestDataCallback](capi-native-audio-converter-h.md#oh_audioconverter_requestdatacallback)提供的输入音频数据的状态。转换器使用此状态来确定如何处理后续的转换逻辑。例如，继续提取数据，暂停或清除缓存数据。<br> 注意：即使回调返回AUDIOCONVERTER_INPUT_DATA_FINISHED，也必须重复调用OH_AudioConverter_Process，直到[OH_AudioConverter_Process](capi-native-audio-converter-h.md#oh_audioconverter_process)返回AUDIOCONVERTER_SUCCESS，并且outputSize=0（表示所有缓存数据均已处理完成）。

**起始版本：** 26.0.0

| 枚举项 | 描述 |
| -- | -- |
| AUDIOCONVERTER_INPUT_HAVE_DATA = 1 | 提供的输入数据有效。 |
| AUDIOCONVERTER_INPUT_NO_AVAILABLE_DATA = 2 | 暂时没有可用的输入数据。 |
| AUDIOCONVERTER_INPUT_DATA_FINISHED = 3 | 输入数据流已完成。 |


## 函数说明

### OH_AudioConverter_Create()

```c
OH_AudioConverter_Result OH_AudioConverter_Create(const OH_AudioConverter_Format* inputFormat, const OH_AudioConverter_Format* outputFormat, OH_AudioConverter** converter)
```

**描述**

创建音频格式转换器。

> **说明：** 
>
> - 此函数创建的转换器实例必须通过[OH_AudioConverter_Destroy](capi-native-audio-converter-h.md#oh_audioconverter_destroy)的显式方式销毁。
> - 支持的音频格式规范（适用于输入/输出）：
> 该转换器仅支持PCM（脉冲编码调制）音频格式。
> - 支持采样率：8000 Hz、11025 Hz、12000 Hz、16000 Hz、22050 Hz、24000 Hz、32000 Hz、44100 Hz、48000 Hz、
> 64000 Hz、88200 Hz、96000 Hz、176400 Hz和192000 Hz。
> - 支持声道布局：CH_LAYOUT_MONO、CH_LAYOUT_STEREO、CH_LAYOUT_STEREO_DOWNMIX、
> CH_LAYOUT_2POINT1、CH_LAYOUT_3POINT0、CH_LAYOUT_SURROUND、CH_LAYOUT_3POINT1、CH_LAYOUT_4POINT0、CH_LAYOUT_QUAD_SIDE、
> CH_LAYOUT_QUAD、CH_LAYOUT_2POINT0POINT2、CH_LAYOUT_4POINT1、CH_LAYOUT_5POINT0、CH_LAYOUT_5POINT0_BACK、
> CH_LAYOUT_2POINT1POINT2、CH_LAYOUT_3POINT0POINT2、CH_LAYOUT_5POINT1、CH_LAYOUT_5POINT1_BACK、CH_LAYOUT_6POINT0、
> CH_LAYOUT_3POINT1POINT2、CH_LAYOUT_6POINT0_FRONT、CH_LAYOUT_HEXAGONAL、CH_LAYOUT_6POINT1、CH_LAYOUT_6POINT1_BACK、
> CH_LAYOUT_6POINT1_FRONT、CH_LAYOUT_7POINT0、CH_LAYOUT_7POINT0_FRONT、CH_LAYOUT_7POINT1、CH_LAYOUT_OCTAGONAL、
> CH_LAYOUT_5POINT1POINT2、CH_LAYOUT_7POINT1_WIDE和CH_LAYOUT_7POINT1_WIDE_BACK。
> - 支持采样格式（位深）：SAMPLE_U8 (8-bit unsigned PCM)、
> SAMPLE_S16LE (16-bit signed little-endian PCM)、SAMPLE_S24LE (24-bit signed little-endian PCM)、
> SAMPLE_S32LE (32-bit signed little-endian PCM)和SAMPLE_F32LE (32-bit float little-endian PCM)。

**起始版本：** 26.0.0

**参数：**

| 参数项 | 描述 |
| --- | --- |
| const [OH_AudioConverter_Format](capi-audioconverter-oh-audioconverter-format.md)* inputFormat | 指向输入音频格式的指针。 |
| const [OH_AudioConverter_Format](capi-audioconverter-oh-audioconverter-format.md)* outputFormat | 指向输出音频格式的指针。 |
| [OH_AudioConverter](capi-audioconverter-oh-audioconverterstruct.md)** converter | 指向可用的音频格式转换器的指针。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [OH_AudioConverter_Result](capi-native-audio-converter-h.md#oh_audioconverter_result) | AUDIOCONVERTER_SUCCESS：创建音频格式转换器成功，可以正常执行后续流程。<br>         AUDIOCONVERTER_ERROR_INVALID_PARAM：函数输入参数无效，需要检查传入的音频格式转换器指针是否非nullptr。<br>         AUDIOCONVERTER_ERROR_UNSUPPORTED_FORMAT：音频输入/输出格式组合不支持，输入或输出格式超出允许范围，需要检查配置的音频格式。<br>          AUDIOCONVERTER_ERROR_MEMORY_ALLOC_FAILED：创建音频格式转换器内存分配失败。<br>          AUDIOCONVERTER_ERROR_SYSTEM：系统错误，需要检查是否使用已销毁的音频格式转换器执行格式转换。 |

### OH_AudioConverter_Destroy()

```c
void OH_AudioConverter_Destroy(OH_AudioConverter* converter)
```

**描述**

销毁音频格式转换器。

**起始版本：** 26.0.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AudioConverter](capi-audioconverter-oh-audioconverterstruct.md)* converter | 由[OH_AudioConverter_Create](capi-native-audio-converter-h.md#oh_audioconverter_create)函数创建的转换器。 |

### OH_AudioConverter_RequestDataCallback()

```c
typedef int32_t (*OH_AudioConverter_RequestDataCallback)(void* userData, const void** outInputData, OH_AudioConverter_InputStatus* outStatus
)
```

**描述**

请求数据的回调函数。转换器在[OH_AudioConverter_Process](capi-native-audio-converter-h.md#oh_audioconverter_process)期间调用此回调函数以主动请求输入音频数据。<br> 调用者必须填充输出参数（outInputData，outStatus），并返回通过回调函数读取的数据大小。<br> 单个回调返回的最大数据大小为400KB。<br> outInputData指向的内存必须保持有效，直到OH_AudioConverter_Process返回处理完成为止。

**起始版本：** 26.0.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| void\* userData | 传递给回调函数的用户自定义数据。 |
| const void\*\* outInputData | 指向回调函数设置的指向输入音频数据缓冲区的指针。 |
| [OH_AudioConverter_InputStatus](capi-native-audio-converter-h.md#oh_audioconverter_inputstatus)\* outStatus | 通过回调函数设置，用于通知转换器输入数据的状态。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 通过outInputData指针指向有效的输入数据的大小。 |

### OH_AudioConverter_SetInputCallback()

```c
OH_AudioConverter_Result OH_AudioConverter_SetInputCallback(OH_AudioConverter* converter, OH_AudioConverter_RequestDataCallback callback, void* userData
)
```

**描述**

设置转换器请求数据回调函数。此函数绑定音频格式转换器的输入数据回调函数。回调函数由[OH_AudioConverter_Process](capi-native-audio-converter-h.md#oh_audioconverter_process)调用，获取输入音频数据并进行处理。

**起始版本：** 26.0.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AudioConverter](capi-audioconverter-oh-audioconverterstruct.md)* converter | 由[OH_AudioConverter_Create](capi-native-audio-converter-h.md#oh_audioconverter_create)函数创建转换器。 |
| [OH_AudioConverter_RequestDataCallback](capi-native-audio-converter-h.md#oh_audioconverter_requestdatacallback) callback | 回调函数用于写入音频数据。 |
| void* userData | 指向将传递给回调函数的应用程序数据结构的指针。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [OH_AudioConverter_Result](capi-native-audio-converter-h.md#oh_audioconverter_result) | AUDIOCONVERTER_SUCCESS：设置输入回调函数成功，可以正常执行后续流程。<br>         AUDIOCONVERTER_ERROR_INVALID_PARAM：函数输入参数无效，需要检查传入的音频格式转换器指针是否非nullptr。<br>         AUDIOCONVERTER_ERROR_NOT_INITIALIZED：音频格式转换器未初始化，需要检查当前音频格式转换器是否有效。<br>         AUDIOCONVERTER_ERROR_CALLBACK_INVALID：回调函数无效，需要检查输入回调函数返回数据量是否在允许范围内。<br>         AUDIOCONVERTER_ERROR_CALLBACK_NOT_SET：回调函数未设置，需要检查回调函数指针是否非空。<br>         AUDIOCONVERTER_ERROR_SYSTEM：系统错误，需要检查是否使用已销毁的音频格式转换器执行格式转换。<br>         AUDIOCONVERTER_ERROR_UNSUPPORTED_OPERATION：当前处理流程不支持设置回调。**适用版本：** 26.1.0。 |

### OH_AudioConverter_Process()

```c
OH_AudioConverter_Result OH_AudioConverter_Process(OH_AudioConverter* converter, void* outputData, int32_t outputCapacity, int32_t* outputSize
)
```

**描述**

执行音频格式转换处理函数。该函数执行音频转换过程，将输入音频转换为目标格式，需要注意：该函数必须在[OH_AudioConverter_SetInputCallback](capi-native-audio-converter-h.md#oh_audioconverter_setinputcallback)之后调用，并且最终转换结果写入的输出缓冲区必须由调用方分配和管理。即使回调返回AUDIOCONVERTER_INPUT_DATA_FINISHED，也必须重复调用此函数，直到返回AUDIOCONVERTER_SUCCESS且outputSize=0（表示所有缓存数据均已处理完成）。

**起始版本：** 26.0.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AudioConverter](capi-audioconverter-oh-audioconverterstruct.md)* converter | 由[OH_AudioConverter_Create](capi-native-audio-converter-h.md#oh_audioconverter_create)函数创建转换器。 |
| void* outputData | 指向调用者分配的输出缓冲区的指针。 |
| int32_t outputCapacity | 调用者指定的输出缓冲区大小。 |
| int32_t* outputSize | 系统实际写入输出缓冲区数据的大小。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [OH_AudioConverter_Result](capi-native-audio-converter-h.md#oh_audioconverter_result) | AUDIOCONVERTER_SUCCESS：PCM音频数据格式转换成功，可以正常执行后续流程。<br>         AUDIOCONVERTER_ERROR_INVALID_PARAM：函数输入参数无效，需要检查传入的音频格式转换器指针是否非nullptr。<br>         AUDIOCONVERTER_ERROR_NOT_INITIALIZED：音频格式转换器未初始化，需要检查当前音频格式转换器是否有效。<br>         AUDIOCONVERTER_ERROR_CALLBACK_INVALID：输入回调函数无效，需要检查输入回调函数返回数据量是否在允许范围内。<br>         AUDIOCONVERTER_ERROR_CALLBACK_NOT_SET：回调函数未设置，需要检查回调函数是否已成功设置并且函数指针是否非空。<br>         AUDIOCONVERTER_ERROR_BUFFER_TOO_SMALL：输出缓冲区容量不足，需要检查设置的存储输出数据的缓冲区容量是否足够存放一帧输出数据。<br>          AUDIOCONVERTER_ERROR_SYSTEM：系统错误，需要检查是否使用已销毁的音频格式转换器执行格式转换。 |

<!--Del-->
### OH_AudioSuite_ConverterCreateEx()

```c
OH_AudioConverter_Result OH_AudioSuite_ConverterCreateEx(const OH_AudioSuite_ConverterFormatEx *inputFormat, const OH_AudioSuite_ConverterFormatEx *outputFormat, OH_AudioConverter **outOwnedConverter)
```

**描述**

创建支持扩展格式的音频转换器。支持不设置数据读取回调函数，通过直接传入数据的方式进行处理。

**起始版本：** 26.1.0

**资源释放：** [OH_AudioConverter_Destroy](capi-native-audio-converter-h.md#oh_audioconverter_destroy)

**系统接口：** 此接口为系统接口。

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [const OH_AudioSuite_ConverterFormatEx](capi-ohaudiosuite-oh-audiosuite-converterformatex-sys.md) *inputFormat | [入参] 指向输入音频格式的指针。不可为NULL，且调用者须保证其在本次调用返回前始终有效。 |
| [const OH_AudioSuite_ConverterFormatEx](capi-ohaudiosuite-oh-audiosuite-converterformatex-sys.md) *outputFormat | [入参] 输出音频格式配置指针。不能为NULL，调用期间必须保持有效。 |
| [OH_AudioConverter](capi-audioconverter-oh-audioconverterstruct.md) **outOwnedConverter | [出参] 用于接收所创建的音频转换器实例的指针。该实例的所有权归调用方，须调用 [OH_AudioConverter_Destroy](capi-native-audio-converter-h.md#oh_audioconverter_destroy)将其释放。该指针参数不可为NULL，且无需预先初始化。调用失败时，不会向该参数写入任何内容。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [OH_AudioConverter_Result](capi-native-audio-converter-h.md#oh_audioconverter_result) | <ul> <li>[AUDIOCONVERTER_SUCCESS](capi-native-audio-converter-h.md#oh_audioconverter_result) 执行成功。</li> <li>[AUDIOCONVERTER_ERROR_NOT_SYSTEM_APP](capi-native-audio-converter-h.md#oh_audioconverter_result) 权限校验失败，非系统应用使用了系统API。</li> <li>[AUDIOCONVERTER_ERROR_INVALID_PARAM](capi-native-audio-converter-h.md#oh_audioconverter_result) 参数无效，可能原因如下：<br>inputFormat为NULL。<br>outputFormat为NULL。<br>outOwnedConverter为NULL。</li> <li>[AUDIOCONVERTER_ERROR_UNSUPPORTED_FORMAT](capi-native-audio-converter-h.md#oh_audioconverter_result) inputFormat/outputFormat中的音频格式不支持。</li> <li>[AUDIOCONVERTER_ERROR_MEMORY_ALLOC_FAILED](capi-native-audio-converter-h.md#oh_audioconverter_result) 内存分配失败。</li> </ul> |

### OH_AudioSuite_ConverterGetMinInOutSizes()

```c
OH_AudioConverter_Result OH_AudioSuite_ConverterGetMinInOutSizes(OH_AudioConverter *converter, uint32_t *inputMinSize, uint32_t *outputMinSize)
```

**描述**

计算所需的最小输入字节数以及与之对应的输出字节数，以确保输出为整数个采样点。最小输入字节数由创建转换器时设置的输入、输出格式共同决定，取决于两者的采样率之比、通道数与采样位宽。

**起始版本：** 26.1.0

**系统接口：** 此接口为系统接口。

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AudioConverter](capi-audioconverter-oh-audioconverterstruct.md) *converter | [入参] 由[OH_AudioSuite_ConverterCreateEx](capi-native-audio-converter-h.md#oh_audiosuite_convertercreateex)或[OH_AudioConverter_Create](capi-native-audio-converter-h.md#oh_audioconverter_create)创建的转换器实例。不能为NULL，调用期间必须保持有效。 |
| uint32_t *inputMinSize | [出参] 返回最小输入字节数，单位为字节（byte）。`inputMinSize`不能为NULL，`inputMinSize`指向的变量无需初始化；调用失败时不会写入内容。 |
| uint32_t *outputMinSize | [出参] 返回对应最小输出字节数，单位为字节（byte）。`outputMinSize`不能为NULL，`outputMinSize`指向的变量无需初始化；调用失败时不会写入内容。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [OH_AudioConverter_Result](capi-native-audio-converter-h.md#oh_audioconverter_result) | <ul> <li>[AUDIOCONVERTER_SUCCESS](capi-native-audio-converter-h.md#oh_audioconverter_result) 执行成功。</li> <li>[AUDIOCONVERTER_ERROR_NOT_SYSTEM_APP](capi-native-audio-converter-h.md#oh_audioconverter_result) 权限校验失败，非系统应用使用了系统API。</li> <li>[AUDIOCONVERTER_ERROR_INVALID_PARAM](capi-native-audio-converter-h.md#oh_audioconverter_result) 参数无效，可能原因如下：<br>converter为NULL。<br>inputMinSize为NULL。<br>outputMinSize为NULL。</li> </ul> |

### OH_AudioSuite_ConverterDirectProcess()

```c
OH_AudioConverter_Result OH_AudioSuite_ConverterDirectProcess(OH_AudioConverter *converter, const OH_AudioSuite_ConverterInputInfo *inData, OH_AudioSuite_ConverterOutputInfo *outData)
```

**描述**

执行音频格式转换，输入数据由调用方直接传入。<br>该接口处理由调用方直接传入的输入数据，每次调用最多可输入1000毫秒的音频数据。同一转换器实例同一时刻只能选用一种数据传入方式：通过[OH_AudioConverter_SetInputCallback](capi-native-audio-converter-h.md#oh_audioconverter_setinputcallback)设置输入回调，或通过本接口传入数据。输入与输出采样率不同时，首次调用，以及每次调用[OH_AudioSuite_ConverterFlush](#oh_audiosuite_converterflush)之后的首次调用，输出数据前都会填充一段静音数据；采样率相同时不填充。所填充静音数据的字节数可通过[OH_AudioSuite_ConverterGetDelaySize](#oh_audiosuite_convertergetdelaysize)获取。

**起始版本：** 26.1.0

**系统接口：** 此接口为系统接口。

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AudioConverter](capi-audioconverter-oh-audioconverterstruct.md) *converter | [入参] 由[OH_AudioSuite_ConverterCreateEx](capi-native-audio-converter-h.md#oh_audiosuite_convertercreateex)或[OH_AudioConverter_Create](capi-native-audio-converter-h.md#oh_audioconverter_create)创建的转换器实例。不能为NULL，调用期间必须保持有效。 |
| [const OH_AudioSuite_ConverterInputInfo](capi-ohaudiosuite-oh-audiosuite-converterinputinfo-sys.md) *inData | [入参] 输入音频数据描述符指针。不能为NULL，调用期间必须保持有效。`inData->size`为输入字节数，必须是[OH_AudioSuite_ConverterGetMinInOutSizes](#oh_audiosuite_convertergetmininoutsizes)返回的最小输入字节数的整数倍。 |
| [OH_AudioSuite_ConverterOutputInfo](capi-ohaudiosuite-oh-audiosuite-converteroutputinfo-sys.md) *outData | [入参，出参] 输出音频数据描述符的指针。该参数不可为NULL，且在本次调用期间必须保持有效。调用方须分配输出缓冲区，并设置`outData->data`与`outData->size`。若`inData->size`为最小输入字节数的k倍，则`outData->size`不得小于最小输出字节数的k倍；最小输入字节数与最小输出字节数由[OH_AudioSuite_ConverterGetMinInOutSizes](#oh_audiosuite_convertergetmininoutsizes)获取。转换结果写入`outData->data`，实际写入的字节数通过`outData->writeSize`回传。调用失败时，不会向`outData->data`写入任何内容。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [OH_AudioConverter_Result](capi-native-audio-converter-h.md#oh_audioconverter_result) | <ul> <li>[AUDIOCONVERTER_SUCCESS](capi-native-audio-converter-h.md#oh_audioconverter_result) 执行成功。</li> <li>[AUDIOCONVERTER_ERROR_NOT_SYSTEM_APP](capi-native-audio-converter-h.md#oh_audioconverter_result) 权限校验失败，非系统应用使用了系统API。</li> <li>[AUDIOCONVERTER_ERROR_INVALID_PARAM](capi-native-audio-converter-h.md#oh_audioconverter_result) 参数无效，可能原因如下：<br>converter为NULL。<br>inData为NULL。<br>inData->data为NULL。<br>inData->size为0。<br>inData->size不是[OH_AudioSuite_ConverterGetMinInOutSizes](#oh_audiosuite_convertergetmininoutsizes)返回的最小输入字节数的整数倍。<br>inData->size对应的音频时长超过1000毫秒。<br>outData为NULL。<br>outData->data为NULL。</li> <li>[AUDIOCONVERTER_ERROR_UNSUPPORTED_OPERATION](capi-native-audio-converter-h.md#oh_audioconverter_result) 已通过[OH_AudioConverter_SetInputCallback](capi-native-audio-converter-h.md#oh_audioconverter_setinputcallback)设置回调。</li> <li>[AUDIOCONVERTER_ERROR_BUFFER_TOO_SMALL](capi-native-audio-converter-h.md#oh_audioconverter_result) 输出缓冲区不足。</li> <li>[AUDIOCONVERTER_ERROR_SYSTEM](capi-native-audio-converter-h.md#oh_audioconverter_result) 系统内部错误。</li> </ul> |

### OH_AudioSuite_ConverterGetDelaySize()

```c
OH_AudioConverter_Result OH_AudioSuite_ConverterGetDelaySize(OH_AudioConverter *converter, uint32_t *delaySize)
```

**描述**

获取采样率转换时首次输出数据前面所填充的静音数据字节数。<br> 需在[OH_AudioSuite_ConverterDirectProcess](#oh_audiosuite_converterdirectprocess)产生静音填充之后调用，否则返回0；调用[OH_AudioSuite_ConverterFlush](#oh_audiosuite_converterflush)后，静音填充会重新产生。输入与输出采样率相同时返回0。

**起始版本：** 26.1.0

**系统接口：** 此接口为系统接口。

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AudioConverter](capi-audioconverter-oh-audioconverterstruct.md) *converter | [入参] 由[OH_AudioSuite_ConverterCreateEx](capi-native-audio-converter-h.md#oh_audiosuite_convertercreateex)或[OH_AudioConverter_Create](capi-native-audio-converter-h.md#oh_audioconverter_create)创建的转换器实例。不能为NULL，调用期间必须保持有效。 |
| uint32_t *delaySize | [出参] 返回首次输出数据前面填充的静音数据字节数，单位为字节（byte）。不能为NULL，无需初始化；调用失败时不会写入内容。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [OH_AudioConverter_Result](capi-native-audio-converter-h.md#oh_audioconverter_result) | <ul> <li>[AUDIOCONVERTER_SUCCESS](capi-native-audio-converter-h.md#oh_audioconverter_result) 执行成功。</li> <li>[AUDIOCONVERTER_ERROR_NOT_SYSTEM_APP](capi-native-audio-converter-h.md#oh_audioconverter_result) 权限校验失败，非系统应用使用了系统API。</li> <li>[AUDIOCONVERTER_ERROR_INVALID_PARAM](capi-native-audio-converter-h.md#oh_audioconverter_result) 参数无效，可能原因如下：<br>converter为NULL。<br>delaySize为NULL。</li> </ul> |

### OH_AudioSuite_ConverterFlush()

```c
OH_AudioConverter_Result OH_AudioSuite_ConverterFlush(OH_AudioConverter *converter)
```

**描述**

清空音频转换器内部的缓冲区与处理状态。<br>当音频数据不连续（例如快进、快退）时，或在某个音频流尚未处理完成就重新开始新的音频流时，需调用本接口，使转换器恢复至初始状态。调用后转换器可直接接收新的音频数据进行转换，无需销毁并重建。

**起始版本：** 26.1.0

**系统接口：** 此接口为系统接口。

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AudioConverter](capi-audioconverter-oh-audioconverterstruct.md) *converter | [入参] 由[OH_AudioSuite_ConverterCreateEx](capi-native-audio-converter-h.md#oh_audiosuite_convertercreateex)或[OH_AudioConverter_Create](capi-native-audio-converter-h.md#oh_audioconverter_create)创建的转换器实例。不能为NULL，调用期间必须保持有效。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [OH_AudioConverter_Result](capi-native-audio-converter-h.md#oh_audioconverter_result) | <ul> <li>[AUDIOCONVERTER_SUCCESS](capi-native-audio-converter-h.md#oh_audioconverter_result) 执行成功。</li> <li>[AUDIOCONVERTER_ERROR_NOT_SYSTEM_APP](capi-native-audio-converter-h.md#oh_audioconverter_result) 权限校验失败，非系统应用使用了系统API。</li> <li>[AUDIOCONVERTER_ERROR_INVALID_PARAM](capi-native-audio-converter-h.md#oh_audioconverter_result) 参数无效，converter为NULL。</li> </ul> |
<!--DelEnd-->
