# native_audio_converter.h

## Overview

Declare underlying data structure.

**Library**: libohaudiosuite.so

**System capability**: SystemCapability.Multimedia.Audio.SuiteEngine

**Since**: 22

**Related module**: [OHAudioSuite](capi-ohaudiosuite.md)

## Summary

### Struct

| Name | typedef keyword | Description |
| -- | -- | -- |
| [OH_AudioConverter_Format](capi-ohaudiosuite-oh-audioconverter-format.md) | OH_AudioConverter_Format | Define the audio converter format info structure, used to describe basic audio format. |
| [OH_AudioConverterStruct](capi-ohaudiosuite-oh-audioconverterstruct.md) | OH_AudioConverter | Declare the audio converter. The handle of audio converter is used for audio converter related functions. |

### Enum

| Name | typedef keyword | Description |
| -- | -- | -- |
| [OH_AudioConverter_Result](#oh_audioconverter_result) | OH_AudioConverter_Result | Define the result of the function execution. |
| [OH_AudioConverter_InputStatus](#oh_audioconverter_inputstatus) | OH_AudioConverter_InputStatus | Define the status of input audio data provided by the callback [OH_AudioConverter_RequestDataCallback](capi-native-audio-converter-h.md#oh_audioconverter_requestdatacallback). The converter uses this status to determine how to handle subsequent conversion logic (e.g., continue pulling data, pause, or flush cached data). Note for callers: Even if the callback returns [AUDIOCONVERTER_INPUT_DATA_FINISHED](capi-native-audio-converter-h.md#oh_audioconverter_inputstatus), [OH_AudioConverter_Process](capi-native-audio-converter-h.md#oh_audioconverter_process) must be called repeatedly until it returns [AUDIOCONVERTER_SUCCESS](capi-native-audio-converter-h.md#oh_audioconverter_result) with outputSize being 0 (indicating all cached data has been flushed). |

### Function

| Name | typedef keyword | Description |
| -- | -- | -- |
| [OH_AudioConverter_Result OH_AudioConverter_Create(const OH_AudioConverter_Format* inputFormat, const OH_AudioConverter_Format* outputFormat, OH_AudioConverter** converter)](#oh_audioconverter_create) | - | Request to create the audio converter.<br> The converter instance created by this function must be explicitly destroyed via [OH_AudioConverter_Destroy](capi-native-audio-converter-h.md#oh_audioconverter_destroy). Supported audio format specifications (valid for Input/Output) The converter only supports PCM (Pulse Code Modulation) audio formats. Sample rate supports 8000 Hz, 11025 Hz, 12000 Hz, 16000 Hz, 22050 Hz, 24000 Hz, 32000 Hz, 44100 Hz, 48000 Hz, 64000 Hz, 88200 Hz, 96000 Hz, 176400 Hz and 192000 Hz. Channel layout supports {@link CH_LAYOUT_MONO}, {@link CH_LAYOUT_STEREO}, {@link CH_LAYOUT_STEREO_DOWNMIX},<br>{@link CH_LAYOUT_2POINT1}, {@link CH_LAYOUT_3POINT0}, {@link CH_LAYOUT_SURROUND}, {@link CH_LAYOUT_3POINT1},<br>{@link CH_LAYOUT_4POINT0}, {@link CH_LAYOUT_QUAD_SIDE}, {@link CH_LAYOUT_QUAD}, {@link CH_LAYOUT_2POINT0POINT2},<br>{@link CH_LAYOUT_4POINT1}, {@link CH_LAYOUT_5POINT0}, {@link CH_LAYOUT_5POINT0_BACK},<br>{@link CH_LAYOUT_2POINT1POINT2}, {@link CH_LAYOUT_3POINT0POINT2}, {@link CH_LAYOUT_5POINT1},<br>{@link CH_LAYOUT_5POINT1_BACK}, {@link CH_LAYOUT_6POINT0}, {@link CH_LAYOUT_3POINT1POINT2},<br>{@link CH_LAYOUT_6POINT0_FRONT}, {@link CH_LAYOUT_HEXAGONAL}, {@link CH_LAYOUT_6POINT1},<br>{@link CH_LAYOUT_6POINT1_BACK}, {@link CH_LAYOUT_6POINT1_FRONT}, {@link CH_LAYOUT_7POINT0},<br>{@link CH_LAYOUT_7POINT0_FRONT}, {@link CH_LAYOUT_7POINT1}, {@link CH_LAYOUT_OCTAGONAL},<br>{@link CH_LAYOUT_5POINT1POINT2}, {@link CH_LAYOUT_7POINT1_WIDE} and {@link CH_LAYOUT_7POINT1_WIDE_BACK}. Sample format (bit depth) supports SAMPLE_U8 (8-bit unsigned PCM), SAMPLE_S16LE (16-bit short little-endian PCM), SAMPLE_S24LE (24-bit short little-endian PCM), SAMPLE_S32LE (32-bit short little-endian PCM), and SAMPLE_F32LE (32-bit float little-endian PCM). |
| [void OH_AudioConverter_Destroy(OH_AudioConverter* converter)](#oh_audioconverter_destroy) | - | Request to release the converter. |
| [typedef int32_t (\*OH_AudioConverter_RequestDataCallback)(void* userData, const void** outInputData, OH_AudioConverter_InputStatus* outStatus)](#oh_audioconverter_requestdatacallback) | OH_AudioConverter_RequestDataCallback | Callback function of request data.<br> The converter invokes this callback to actively request input audio data during [OH_AudioConverter_Process](capi-native-audio-converter-h.md#oh_audioconverter_process). The caller must populate the output parameters (outInputData, outStatus) and return the valid size of input data. The maximum data size returned by a single callback is 400KB. The memory pointed to by outInputData must remain valid until [OH_AudioConverter_Process](capi-native-audio-converter-h.md#oh_audioconverter_process) returns. |
| [OH_AudioConverter_Result OH_AudioConverter_SetInputCallback(OH_AudioConverter* converter, OH_AudioConverter_RequestDataCallback callback, void* userData)](#oh_audioconverter_setinputcallback) | - | Set converter request data callback.<br> This function binds the input data callback function for the audio converter. The callback is used by [OH_AudioConverter_Process](capi-native-audio-converter-h.md#oh_audioconverter_process) to pull input audio data dynamically. |
| [OH_AudioConverter_Result OH_AudioConverter_Process(OH_AudioConverter* converter, void* outputData, int32_t outputCapacity, int32_t* outputSize)](#oh_audioconverter_process) | - | Executing the audio format conversion.<br> This function executes audio conversion to convert to the target format, and writes the result to the user-provided output buffer. This function must be called after [OH_AudioConverter_SetInputCallback](capi-native-audio-converter-h.md#oh_audioconverter_setinputcallback). The output buffer must be allocated and managed by the caller. |

### Variable

| Name | Description |
| -- | -- |
| int32_t (*OH_AudioConverter_RequestDataCallback)( void* userData, const void** outInputData, OH_AudioConverter_InputStatus* outStatus ) | Callback function of request data.<br> The converter invokes this callback to actively request input audio data during [OH_AudioConverter_Process](capi-native-audio-converter-h.md#oh_audioconverter_process). The caller must populate the output parameters (outInputData, outStatus) and return the valid size of input data. The maximum data size returned by a single callback is 400KB. The memory pointed to by outInputData must remain valid until [OH_AudioConverter_Process](capi-native-audio-converter-h.md#oh_audioconverter_process) returns.<br>**Since**: 26.0.0 |

## Enum type description

### OH_AudioConverter_Result

```c
enum OH_AudioConverter_Result
```

**Description**

Define the result of the function execution.

**Since**: 26.0.0

| Enum item | Description |
| -- | -- |
| AUDIOCONVERTER_SUCCESS = 0 |  The call was successful.<br>**Since**: 26.0.0 |
| AUDIOCONVERTER_ERROR_INVALID_PARAM = 1 |  This means that the function was executed with an invalid input parameter.<br>**Since**: 26.0.0 |
| AUDIOCONVERTER_ERROR_UNSUPPORTED_FORMAT = 2 |  Unsupported audio format, such as unsupported encoding type, sample format etc.<br>**Since**: 26.0.0 |
| AUDIOCONVERTER_ERROR_SYSTEM = 3 |  A system error has occurred.<br>**Since**: 26.0.0 |
| AUDIOCONVERTER_ERROR_MEMORY_ALLOC_FAILED = 4 |  Memory allocation failed.<br>**Since**: 26.0.0 |
| AUDIOCONVERTER_ERROR_BUFFER_TOO_SMALL = 5 |  Buffer capacity is insufficient.<br>**Since**: 26.0.0 |
| AUDIOCONVERTER_ERROR_NOT_INITIALIZED = 6 |  Audio converter instance is not initialized.<br>**Since**: 26.0.0 |
| AUDIOCONVERTER_ERROR_CALLBACK_INVALID = 7 |  Callback is invalid.<br>**Since**: 26.0.0 |
| AUDIOCONVERTER_ERROR_CALLBACK_NOT_SET = 8 |  Callback is not set.<br>**Since**: 26.0.0 |

### OH_AudioConverter_InputStatus

```c
enum OH_AudioConverter_InputStatus
```

**Description**

Define the status of input audio data provided by the callback [OH_AudioConverter_RequestDataCallback](capi-native-audio-converter-h.md#oh_audioconverter_requestdatacallback). The converter uses this status to determine how to handle subsequent conversion logic (e.g., continue pulling data, pause, or flush cached data). Note for callers: Even if the callback returns [AUDIOCONVERTER_INPUT_DATA_FINISHED](capi-native-audio-converter-h.md#oh_audioconverter_inputstatus), [OH_AudioConverter_Process](capi-native-audio-converter-h.md#oh_audioconverter_process) must be called repeatedly until it returns [AUDIOCONVERTER_SUCCESS](capi-native-audio-converter-h.md#oh_audioconverter_result) with outputSize being 0 (indicating all cached data has been flushed).

**Since**: 26.0.0

| Enum item | Description |
| -- | -- |
| AUDIOCONVERTER_INPUT_HAVE_DATA = 1 |  |
| AUDIOCONVERTER_INPUT_NO_AVAILABLE_DATA = 2 |  |
| AUDIOCONVERTER_INPUT_DATA_FINISHED = 3 |  |


## Function description

### OH_AudioConverter_Create()

```c
OH_AudioConverter_Result OH_AudioConverter_Create(const OH_AudioConverter_Format* inputFormat, const OH_AudioConverter_Format* outputFormat, OH_AudioConverter** converter)
```

**Description**

Request to create the audio converter.<br> The converter instance created by this function must be explicitly destroyed via [OH_AudioConverter_Destroy](capi-native-audio-converter-h.md#oh_audioconverter_destroy). Supported audio format specifications (valid for Input/Output) The converter only supports PCM (Pulse Code Modulation) audio formats. Sample rate supports 8000 Hz, 11025 Hz, 12000 Hz, 16000 Hz, 22050 Hz, 24000 Hz, 32000 Hz, 44100 Hz, 48000 Hz, 64000 Hz, 88200 Hz, 96000 Hz, 176400 Hz and 192000 Hz. Channel layout supports {@link CH_LAYOUT_MONO}, {@link CH_LAYOUT_STEREO}, {@link CH_LAYOUT_STEREO_DOWNMIX},<br>{@link CH_LAYOUT_2POINT1}, {@link CH_LAYOUT_3POINT0}, {@link CH_LAYOUT_SURROUND}, {@link CH_LAYOUT_3POINT1},<br>{@link CH_LAYOUT_4POINT0}, {@link CH_LAYOUT_QUAD_SIDE}, {@link CH_LAYOUT_QUAD}, {@link CH_LAYOUT_2POINT0POINT2},<br>{@link CH_LAYOUT_4POINT1}, {@link CH_LAYOUT_5POINT0}, {@link CH_LAYOUT_5POINT0_BACK},<br>{@link CH_LAYOUT_2POINT1POINT2}, {@link CH_LAYOUT_3POINT0POINT2}, {@link CH_LAYOUT_5POINT1},<br>{@link CH_LAYOUT_5POINT1_BACK}, {@link CH_LAYOUT_6POINT0}, {@link CH_LAYOUT_3POINT1POINT2},<br>{@link CH_LAYOUT_6POINT0_FRONT}, {@link CH_LAYOUT_HEXAGONAL}, {@link CH_LAYOUT_6POINT1},<br>{@link CH_LAYOUT_6POINT1_BACK}, {@link CH_LAYOUT_6POINT1_FRONT}, {@link CH_LAYOUT_7POINT0},<br>{@link CH_LAYOUT_7POINT0_FRONT}, {@link CH_LAYOUT_7POINT1}, {@link CH_LAYOUT_OCTAGONAL},<br>{@link CH_LAYOUT_5POINT1POINT2}, {@link CH_LAYOUT_7POINT1_WIDE} and {@link CH_LAYOUT_7POINT1_WIDE_BACK}. Sample format (bit depth) supports SAMPLE_U8 (8-bit unsigned PCM), SAMPLE_S16LE (16-bit short little-endian PCM), SAMPLE_S24LE (24-bit short little-endian PCM), SAMPLE_S32LE (32-bit short little-endian PCM), and SAMPLE_F32LE (32-bit float little-endian PCM).

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| [const OH_AudioConverter_Format](capi-ohaudiosuite-oh-audioconverter-format.md)* inputFormat | Pointer to the input audio format configuration. |
| [const OH_AudioConverter_Format](capi-ohaudiosuite-oh-audioconverter-format.md)* outputFormat | Pointer to the output audio format configuration. |
| [OH_AudioConverter](capi-ohaudiosuite-oh-audioconverterstruct.md)** converter | Pointer to a variable that receives the created audio converter instance. |

**Returns**:

| Type | Description |
| -- | -- |
| [OH_AudioConverter_Result](capi-native-audio-converter-h.md#oh_audioconverter_result) | <ul>          <li>[AUDIOCONVERTER_SUCCESS](capi-native-audio-converter-h.md#oh_audioconverter_result) if execution succeeds.</li>          <li>[AUDIOCONVERTER_ERROR_INVALID_PARAM](capi-native-audio-converter-h.md#oh_audioconverter_result) if the input parameters are invalid</li>          <li>[AUDIOCONVERTER_ERROR_UNSUPPORTED_FORMAT](capi-native-audio-converter-h.md#oh_audioconverter_result)              if the specified input/output format combination is unsupported</li>          <li>[AUDIOCONVERTER_ERROR_MEMORY_ALLOC_FAILED](capi-native-audio-converter-h.md#oh_audioconverter_result) if memory allocation failed</li>          <li>[AUDIOCONVERTER_ERROR_SYSTEM](capi-native-audio-converter-h.md#oh_audioconverter_result) if the system has other abnormalities</li>          </ul> |

### OH_AudioConverter_Destroy()

```c
void OH_AudioConverter_Destroy(OH_AudioConverter* converter)
```

**Description**

Request to release the converter.

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AudioConverter](capi-ohaudiosuite-oh-audioconverterstruct.md)* converter | Reference created by OH_AudioConverter_Create. |

### OH_AudioConverter_RequestDataCallback()

```c
typedef int32_t (*OH_AudioConverter_RequestDataCallback)(void* userData, const void** outInputData, OH_AudioConverter_InputStatus* outStatus)
```

**Description**

Callback function of request data.<br> The converter invokes this callback to actively request input audio data during [OH_AudioConverter_Process](capi-native-audio-converter-h.md#oh_audioconverter_process). The caller must populate the output parameters (outInputData, outStatus) and return the valid size of input data. The maximum data size returned by a single callback is 400KB. The memory pointed to by outInputData must remain valid until [OH_AudioConverter_Process](capi-native-audio-converter-h.md#oh_audioconverter_process) returns.

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| void\* userData | User-defined data passed to the callback. |
| const void\*\* outInputData | Pointer to a pointer that the callback sets to point to the input audio data buffer. |
| [OH_AudioConverter_InputStatus](capi-native-audio-converter-h.md#oh_audioconverter_inputstatus)\* outStatus | Set by the callback to inform the converter about the current state of input data availability. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Size of valid input data pointed to by outInputData. |

### OH_AudioConverter_SetInputCallback()

```c
OH_AudioConverter_Result OH_AudioConverter_SetInputCallback(OH_AudioConverter* converter, OH_AudioConverter_RequestDataCallback callback, void* userData)
```

**Description**

Set converter request data callback.<br> This function binds the input data callback function for the audio converter. The callback is used by [OH_AudioConverter_Process](capi-native-audio-converter-h.md#oh_audioconverter_process) to pull input audio data dynamically.

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AudioConverter](capi-ohaudiosuite-oh-audioconverterstruct.md)* converter | Reference created by OH_AudioConverter_Create. |
| [OH_AudioConverter_RequestDataCallback](capi-native-audio-converter-h.md#oh_audioconverter_requestdatacallback) callback | Callback function that will be invoked during [OH_AudioConverter_Process](capi-native-audio-converter-h.md#oh_audioconverter_process) to actively request input audio data. |
| void* userData | Pointer to an application data structure that will be passed to the callback functions. |

**Returns**:

| Type | Description |
| -- | -- |
| [OH_AudioConverter_Result](capi-native-audio-converter-h.md#oh_audioconverter_result) | <ul>          <li>[AUDIOCONVERTER_SUCCESS](capi-native-audio-converter-h.md#oh_audioconverter_result) if execution succeeds.</li>          <li>[AUDIOCONVERTER_ERROR_INVALID_PARAM](capi-native-audio-converter-h.md#oh_audioconverter_result) if parameter is invalid,              e.g. converter is nullptr, e.t.c.</li>          <li>[AUDIOCONVERTER_ERROR_NOT_INITIALIZED](capi-native-audio-converter-h.md#oh_audioconverter_result) if the converter instance is not initialized</li>          <li>[AUDIOCONVERTER_ERROR_CALLBACK_INVALID](capi-native-audio-converter-h.md#oh_audioconverter_result) if callback is invalid,              e.g. invalid callback return, e.t.c.</li>          <li>[AUDIOCONVERTER_ERROR_SYSTEM](capi-native-audio-converter-h.md#oh_audioconverter_result) if the system has other abnormalities</li>          </ul> |

### OH_AudioConverter_Process()

```c
OH_AudioConverter_Result OH_AudioConverter_Process(OH_AudioConverter* converter, void* outputData, int32_t outputCapacity, int32_t* outputSize)
```

**Description**

Executing the audio format conversion.<br> This function executes audio conversion to convert to the target format, and writes the result to the user-provided output buffer. This function must be called after [OH_AudioConverter_SetInputCallback](capi-native-audio-converter-h.md#oh_audioconverter_setinputcallback). The output buffer must be allocated and managed by the caller.

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AudioConverter](capi-ohaudiosuite-oh-audioconverterstruct.md)* converter | Reference created by [OH_AudioConverter_Create](capi-native-audio-converter-h.md#oh_audioconverter_create). |
| void* outputData | Pointer to the output buffer allocated by the caller to receive converted audio data. |
| int32_t outputCapacity | Size of the output buffer in bytes specified by the user. |
| int32_t* outputSize | Size of output buffer the system really writes. Returns the number of bytes actually written on success. When [AUDIOCONVERTER_SUCCESS](capi-native-audio-converter-h.md#oh_audioconverter_result) is returned but outputSize is 0, it indicates that all buffered data has been fully flushed. |

**Returns**:

| Type | Description |
| -- | -- |
| [OH_AudioConverter_Result](capi-native-audio-converter-h.md#oh_audioconverter_result) | <ul>          <li>[AUDIOCONVERTER_SUCCESS](capi-native-audio-converter-h.md#oh_audioconverter_result) if execution succeeds.</li>          <li>[AUDIOCONVERTER_ERROR_INVALID_PARAM](capi-native-audio-converter-h.md#oh_audioconverter_result) if parameter is invalid,              e.g. converter is nullptr, e.t.c.</li>          <li>[AUDIOCONVERTER_ERROR_NOT_INITIALIZED](capi-native-audio-converter-h.md#oh_audioconverter_result) if the converter instance is not initialized</li>          <li>[AUDIOCONVERTER_ERROR_CALLBACK_INVALID](capi-native-audio-converter-h.md#oh_audioconverter_result) if callback is invalid,              e.g. callback returned an invalid value, e.t.c.</li>          <li>[AUDIOCONVERTER_ERROR_CALLBACK_NOT_SET](capi-native-audio-converter-h.md#oh_audioconverter_result) if no input callback is bound to the converter</li>          <li>[AUDIOCONVERTER_ERROR_BUFFER_TOO_SMALL](capi-native-audio-converter-h.md#oh_audioconverter_result) if output buffer capacity is insufficient</li>          <li>[AUDIOCONVERTER_ERROR_SYSTEM](capi-native-audio-converter-h.md#oh_audioconverter_result) if the system has other abnormalities</li>          </ul> |


