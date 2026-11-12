# native_audio_converter.h(System API)

## Overview

Declare underlying data structure.

**Library**: libohaudiosuite.so

**System capability**: SystemCapability.Multimedia.Audio.SuiteEngine

**Since**: 26.0.0

**System API:** This is a system API.

**Related module**: [OHAudioSuite](capi-audio-kit-ohaudiosuite.md)

## Summary

### Functions

| Name | Description |
| -- | -- |
| [OH_AudioConverter_Result OH_AudioSuite_ConverterCreateEx(const OH_AudioSuite_ConverterFormatEx *inputFormat, const OH_AudioSuite_ConverterFormatEx *outputFormat, OH_AudioConverter **outOwnedConverter)(System API)](#oh_audiosuite_convertercreateex) | Create an audio converter that supports extended formats.<br>**System API:** This is a system API. |
| [OH_AudioConverter_Result OH_AudioSuite_ConverterGetMinInOutSizes(OH_AudioConverter *converter, uint32_t *inputMinSize, uint32_t *outputMinSize)(System API)](#oh_audiosuite_convertergetmininoutsizes) | Calculate the minimum number of input bytes and the corresponding number of output bytes to ensure that the output is an integer sample number.<br> The minimum number of bytes is determined by the input and output formats set when the converter was created, and is related to the sampling rate, number of channels, and bit depth.<br>**System API:** This is a system API. |
| [OH_AudioConverter_Result OH_AudioSuite_ConverterDirectProcess(OH_AudioConverter *converter, const OH_AudioSuite_ConverterInputInfo *inData, OH_AudioSuite_ConverterOutputInfo *outData)(System API)](#oh_audiosuite_converterdirectprocess) | Converts the audio format and transfers the input data to the invoking party.<br> This interface processes the input data directly transferred by the invoker. A maximum of 1000 ms audio data can be input each time the interface is invoked. The same converter instance cannot set callback through [OH_AudioConverter_SetInputCallback](capi-native-audio-converter-h.md#oh_audioconverter_setinputcallback) or transfer data through this interface at the same time. When the input and output sampling rates are different, the first call and the first call after each call [OH_AudioSuite_ConverterFlush](capi-native-audio-converter-h.md#oh_audiosuite_converterflush) are called, The output data is preceded by a certain length of silence data. No padding is performed when the sampling rate is the same. The number of bytes to fill in the silence data can be obtained from [OH_AudioSuite_ConverterGetDelaySize](capi-native-audio-converter-h.md#oh_audiosuite_convertergetdelaysize).<br>**System API:** This is a system API. |
| [OH_AudioConverter_Result OH_AudioSuite_ConverterGetDelaySize(OH_AudioConverter *converter, uint32_t *delaySize)(System API)](#oh_audiosuite_convertergetdelaysize) | Obtains the number of silent data bytes padded before the first output data during sampling rate conversion.<br> This interface is invoked after the [OH_AudioSuite_ConverterDirectProcess](capi-native-audio-converter-h.md#oh_audiosuite_converterdirectprocess) generates mute filling. The mute padding is re-created after [OH_AudioSuite_ConverterFlush](capi-native-audio-converter-h.md#oh_audiosuite_converterflush) is called. If the sampling rates are the same, 0 is returned.<br>**System API:** This is a system API. |
| [OH_AudioConverter_Result OH_AudioSuite_ConverterFlush(OH_AudioConverter *converter)(System API)](#oh_audiosuite_converterflush) | Clears the internal buffer and processing status of the audio converter.<br> when the audio data is discontinuous(e.g., fast forward, fast rewind scene), or when a new audio stream is restarted before the processing of an audio stream is completed, This interface needs to be called to clear the internal cache and processing status of the converter. Restore the converter to its original state. After the call, the converter can continue to receive new audio data for conversion without destroying and rebuilding.<br>**System API:** This is a system API. |

## Function description

### OH_AudioSuite_ConverterCreateEx()

```c
OH_AudioConverter_Result OH_AudioSuite_ConverterCreateEx(const OH_AudioSuite_ConverterFormatEx *inputFormat, const OH_AudioSuite_ConverterFormatEx *outputFormat, OH_AudioConverter **outOwnedConverter)
```

**Description**

Create an audio converter that supports extended formats.

<!--Device-OH_AudioConverter_Result OH_AudioSuite_ConverterCreateEx(const OH_AudioSuite_ConverterFormatEx *inputFormat, const OH_AudioSuite_ConverterFormatEx *outputFormat, OH_AudioConverter **outOwnedConverter)--><!--Device-OH_AudioConverter_Result OH_AudioSuite_ConverterCreateEx(const OH_AudioSuite_ConverterFormatEx *inputFormat, const OH_AudioSuite_ConverterFormatEx *outputFormat, OH_AudioConverter **outOwnedConverter)-End-->

**System capability**: SystemCapability.Multimedia.Audio.SuiteEngine

**Since**: 26.1.0

**Resource release**: [OH_AudioConverter_Destroy](#oh_audioconverter_destroy)

**System API:** This is a system API.

**Parameters**:

| Parameter | Description |
| -- | -- |
| [const OH_AudioSuite_ConverterFormatEx](capi-ohaudiosuite-oh-audiosuite-converterformatex.md) *inputFormat | [Input parameter] Pointer to the input audio format. Cannot be NULL and must remain valid for the duration of the call. |
| [const OH_AudioSuite_ConverterFormatEx](capi-ohaudiosuite-oh-audiosuite-converterformatex.md) *outputFormat | [Input parameter] Pointer to the output audio format. Cannot be NULL and must remain valid for the duration of the call. |
| [OH_AudioConverter](capi-ohaudiosuite-oh-audioconverterstruct.md) **outOwnedConverter | [Output parameter] Pointer to the created audio converter instance. The caller owns the result and must use the [OH_AudioConverter_Destroy](capi-native-audio-converter-h.md#oh_audioconverter_destroy) Release. The value cannot be NULL and does not need to be initialized. No content is written when the call fails. |

**Returns**:

| Type | Description |
| -- | -- |
| [OH_AudioConverter_Result](capi-native-audio-converter-h.md#oh_audioconverter_result) | <ul> <li>[AUDIOCONVERTER_SUCCESS](capi-native-audio-converter-h.md#oh_audioconverter_result) Execution succeeded. </li> <li>202 Permission verification failed because a non-system application uses the system API. </li> <li>[AUDIOCONVERTER_ERROR_INVALID_PARAM](capi-native-audio-converter-h.md#oh_audioconverter_result)The parameter is invalid. The possible causes are as follows: <br>1. The value of inputFormat is NULL. <br>2. The value of outputFormat is NULL. <br>3. outOwnedConverter is NULL. </li> <li>[AUDIOCONVERTER_ERROR_UNSUPPORTED_FORMAT](capi-native-audio-converter-h.md#oh_audioconverter_result)The audio format in inputFormat/outputFormat is not supported. </li> <li>[AUDIOCONVERTER_ERROR_MEMORY_ALLOC_FAILED](capi-native-audio-converter-h.md#oh_audioconverter_result) Memory allocation failed. </li> </ul> |

### OH_AudioSuite_ConverterGetMinInOutSizes()

```c
OH_AudioConverter_Result OH_AudioSuite_ConverterGetMinInOutSizes(OH_AudioConverter *converter, uint32_t *inputMinSize, uint32_t *outputMinSize)
```

**Description**

Calculate the minimum number of input bytes and the corresponding number of output bytes to ensure that the output is an integer sample number.<br> The minimum number of bytes is determined by the input and output formats set when the converter was created, and is related to the sampling rate, number of channels, and bit depth.

<!--Device-OH_AudioConverter_Result OH_AudioSuite_ConverterGetMinInOutSizes(OH_AudioConverter *converter, uint32_t *inputMinSize, uint32_t *outputMinSize)--><!--Device-OH_AudioConverter_Result OH_AudioSuite_ConverterGetMinInOutSizes(OH_AudioConverter *converter, uint32_t *inputMinSize, uint32_t *outputMinSize)-End-->

**System capability**: SystemCapability.Multimedia.Audio.SuiteEngine

**Since**: 26.1.0

**System API:** This is a system API.

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AudioConverter](capi-ohaudiosuite-oh-audioconverterstruct.md) *converter | [Input parameter] Converter instance created by the [OH_AudioSuite_ConverterCreateEx](capi-native-audio-converter-h.md#oh_audiosuite_convertercreateex) or [OH_AudioConverter_Create](capi-native-audio-converter-h.md#oh_audioconverter_create). cannot be null and must remain valid during the call. |
| uint32_t *inputMinSize | [Output parameter] Minimum number of input bytes, in bytes. The value cannot be NULL and does not need to be initialized. No content is written when the call fails. |
| uint32_t *outputMinSize | [Output parameter] Minimum number of output bytes, in bytes. The value cannot be NULL and does not need to be initialized. No content is written when the call fails. |

**Returns**:

| Type | Description |
| -- | -- |
| [OH_AudioConverter_Result](capi-native-audio-converter-h.md#oh_audioconverter_result) | <ul> <li>[AUDIOCONVERTER_SUCCESS](capi-native-audio-converter-h.md#oh_audioconverter_result) Execution succeeded. </li> <li>202 Permission verification failed because a non-system application uses the system API. </li> <li>[AUDIOCONVERTER_ERROR_INVALID_PARAM](capi-native-audio-converter-h.md#oh_audioconverter_result)The parameter is invalid. The possible causes are as follows: <br>1. The converter is NULL. <br>2. The value of inputMinSize is NULL. <br>3. The value of outputMinSize is NULL. </li> </ul> |

### OH_AudioSuite_ConverterDirectProcess()

```c
OH_AudioConverter_Result OH_AudioSuite_ConverterDirectProcess(OH_AudioConverter *converter, const OH_AudioSuite_ConverterInputInfo *inData, OH_AudioSuite_ConverterOutputInfo *outData)
```

**Description**

Converts the audio format and transfers the input data to the invoking party.<br> This interface processes the input data directly transferred by the invoker. A maximum of 1000 ms audio data can be input each time the interface is invoked. The same converter instance cannot set callback through [OH_AudioConverter_SetInputCallback](capi-native-audio-converter-h.md#oh_audioconverter_setinputcallback) or transfer data through this interface at the same time. When the input and output sampling rates are different, the first call and the first call after each call [OH_AudioSuite_ConverterFlush](capi-native-audio-converter-h.md#oh_audiosuite_converterflush) are called, The output data is preceded by a certain length of silence data. No padding is performed when the sampling rate is the same. The number of bytes to fill in the silence data can be obtained from [OH_AudioSuite_ConverterGetDelaySize](capi-native-audio-converter-h.md#oh_audiosuite_convertergetdelaysize).

<!--Device-OH_AudioConverter_Result OH_AudioSuite_ConverterDirectProcess(OH_AudioConverter *converter, const OH_AudioSuite_ConverterInputInfo *inData, OH_AudioSuite_ConverterOutputInfo *outData)--><!--Device-OH_AudioConverter_Result OH_AudioSuite_ConverterDirectProcess(OH_AudioConverter *converter, const OH_AudioSuite_ConverterInputInfo *inData, OH_AudioSuite_ConverterOutputInfo *outData)-End-->

**System capability**: SystemCapability.Multimedia.Audio.SuiteEngine

**Since**: 26.1.0

**System API:** This is a system API.

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AudioConverter](capi-ohaudiosuite-oh-audioconverterstruct.md) *converter | [Input parameter] Converter instance created by the [OH_AudioSuite_ConverterCreateEx](capi-native-audio-converter-h.md#oh_audiosuite_convertercreateex) or [OH_AudioConverter_Create](capi-native-audio-converter-h.md#oh_audioconverter_create). cannot be null and must remain valid during the call. |
| [const OH_AudioSuite_ConverterInputInfo](capi-ohaudiosuite-oh-audiosuite-converterinputinfo.md) *inData | [Input parameter] Pointer to the input audio data descriptor. Cannot be NULL and must remain valid for the duration of the call. **inData->size** indicates the number of input bytes, which must be an integer multiple of the minimum number of input bytes returned by the [OH_AudioSuite_ConverterGetMinInOutSizes](capi-native-audio-converter-h.md#oh_audiosuite_convertergetmininoutsizes). |
| [OH_AudioSuite_ConverterOutputInfo](capi-ohaudiosuite-oh-audiosuite-converteroutputinfo.md) *outData | [Input parameter, output parameter] Pointer to the output audio data descriptor. Cannot be NULL and must remain valid for the duration of the call. <br>The caller needs to allocate the output buffer and set **outData->data** and **outData->size**. If **inData->size** is k times the minimum number of input bytes, **outData->size** must be greater than k times the minimum number of output bytes, The minimum number of input bytes and the minimum number of output bytes are obtained from [OH_AudioSuite_ConverterGetMinInOutSizes](capi-native-audio-converter-h.md#oh_audiosuite_convertergetmininoutsizes). <br>The conversion result is written to **outData->data**. The actual number of written bytes is returned through **outData->writeSize**. <br>No content is written when the call fails. |

**Returns**:

| Type | Description |
| -- | -- |
| [OH_AudioConverter_Result](capi-native-audio-converter-h.md#oh_audioconverter_result) | <ul> <li>[AUDIOCONVERTER_SUCCESS](capi-native-audio-converter-h.md#oh_audioconverter_result) Execution succeeded. </li> <li>202 Permission verification failed because a non-system application uses the system API. </li> <li>[AUDIOCONVERTER_ERROR_INVALID_PARAM](capi-native-audio-converter-h.md#oh_audioconverter_result)The parameter is invalid. The possible causes are as follows: <br>1. The converter is NULL. <br>2. The value of inData is NULL. <br>3. **inData->data** is NULL. <br>4. **inData->size** is 0. <br>5. **inData->size** is not an integer multiple of the minimum number of input bytes returned by the [OH_AudioSuite_ConverterGetMinInOutSizes](capi-native-audio-converter-h.md#oh_audiosuite_convertergetmininoutsizes). <br>6. **inData->size** The audio duration exceeds 1000 ms. <br>7. The value of outData is NULL. <br>8. **outData->data** is NULL. </li> <li>[AUDIOCONVERTER_ERROR_UNSUPPORTED_OPERATION](capi-native-audio-converter-h.md#oh_audioconverter_result) The callback has been set through [OH_AudioConverter_SetInputCallback](capi-native-audio-converter-h.md#oh_audioconverter_setinputcallback). </li> <li>[AUDIOCONVERTER_ERROR_BUFFER_TOO_SMALL](capi-native-audio-converter-h.md#oh_audioconverter_result)The output buffer is insufficient. </li> <li>[AUDIOCONVERTER_ERROR_SYSTEM](capi-native-audio-converter-h.md#oh_audioconverter_result) An internal system error occurs. </li> </ul> |

### OH_AudioSuite_ConverterGetDelaySize()

```c
OH_AudioConverter_Result OH_AudioSuite_ConverterGetDelaySize(OH_AudioConverter *converter, uint32_t *delaySize)
```

**Description**

Obtains the number of silent data bytes padded before the first output data during sampling rate conversion.<br> This interface is invoked after the [OH_AudioSuite_ConverterDirectProcess](capi-native-audio-converter-h.md#oh_audiosuite_converterdirectprocess) generates mute filling. The mute padding is re-created after [OH_AudioSuite_ConverterFlush](capi-native-audio-converter-h.md#oh_audiosuite_converterflush) is called. If the sampling rates are the same, 0 is returned.

<!--Device-OH_AudioConverter_Result OH_AudioSuite_ConverterGetDelaySize(OH_AudioConverter *converter, uint32_t *delaySize)--><!--Device-OH_AudioConverter_Result OH_AudioSuite_ConverterGetDelaySize(OH_AudioConverter *converter, uint32_t *delaySize)-End-->

**System capability**: SystemCapability.Multimedia.Audio.SuiteEngine

**Since**: 26.1.0

**System API:** This is a system API.

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AudioConverter](capi-ohaudiosuite-oh-audioconverterstruct.md) *converter | [Input parameter] Converter instance created by the [OH_AudioSuite_ConverterCreateEx](capi-native-audio-converter-h.md#oh_audiosuite_convertercreateex) or [OH_AudioConverter_Create](capi-native-audio-converter-h.md#oh_audioconverter_create). cannot be null and must remain valid during the call. |
| uint32_t *delaySize | [Output parameter] Number of bytes filled before the first output data, in bytes. cannot be NULL and does not need to be initialized. No content is written when the call fails. |

**Returns**:

| Type | Description |
| -- | -- |
| [OH_AudioConverter_Result](capi-native-audio-converter-h.md#oh_audioconverter_result) | <ul> <li>[AUDIOCONVERTER_SUCCESS](capi-native-audio-converter-h.md#oh_audioconverter_result) Execution succeeded. </li> <li>202 Permission verification failed because a non-system application uses the system API. </li> <li>[AUDIOCONVERTER_ERROR_INVALID_PARAM](capi-native-audio-converter-h.md#oh_audioconverter_result)The parameter is invalid. The possible causes are as follows: <br>1. The converter is NULL. <br>2. The value of delaySize is NULL. </li> </ul> |

### OH_AudioSuite_ConverterFlush()

```c
OH_AudioConverter_Result OH_AudioSuite_ConverterFlush(OH_AudioConverter *converter)
```

**Description**

Clears the internal buffer and processing status of the audio converter.<br> when the audio data is discontinuous(e.g., fast forward, fast rewind scene), or when a new audio stream is restarted before the processing of an audio stream is completed, This interface needs to be called to clear the internal cache and processing status of the converter. Restore the converter to its original state. After the call, the converter can continue to receive new audio data for conversion without destroying and rebuilding.

<!--Device-OH_AudioConverter_Result OH_AudioSuite_ConverterFlush(OH_AudioConverter *converter)--><!--Device-OH_AudioConverter_Result OH_AudioSuite_ConverterFlush(OH_AudioConverter *converter)-End-->

**System capability**: SystemCapability.Multimedia.Audio.SuiteEngine

**Since**: 26.1.0

**System API:** This is a system API.

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AudioConverter](capi-ohaudiosuite-oh-audioconverterstruct.md) *converter | [Input parameter] Converter instance created by the [OH_AudioSuite_ConverterCreateEx](capi-native-audio-converter-h.md#oh_audiosuite_convertercreateex) or [OH_AudioConverter_Create](capi-native-audio-converter-h.md#oh_audioconverter_create). cannot be null and must remain valid during the call. |

**Returns**:

| Type | Description |
| -- | -- |
| [OH_AudioConverter_Result](capi-native-audio-converter-h.md#oh_audioconverter_result) | <ul> <li>[AUDIOCONVERTER_SUCCESS](capi-native-audio-converter-h.md#oh_audioconverter_result) Execution succeeded. </li> <li>202 Permission verification failed because a non-system application uses the system API. </li> <li>[AUDIOCONVERTER_ERROR_INVALID_PARAM](capi-native-audio-converter-h.md#oh_audioconverter_result) The parameter is invalid. The converter is NULL. </li> </ul> |


