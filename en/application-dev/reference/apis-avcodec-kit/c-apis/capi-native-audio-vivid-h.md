# native_audio_vivid.h

## Overview

The file declares the functions and enums related to Audio Vivid.

**Include**: <multimedia/player_framework/native_audio_vivid.h>

**Library**: libnative_media_core.so

**System capability**: SystemCapability.Multimedia.Media.Core

**Since**: 9

**Related module**: [Core](capi-core.md)

## Summary

### Struct

| Name | typedef keyword | Description |
| -- | -- | -- |
| [OH_CartesianPosition](capi-core-oh-cartesianposition.md) | OH_CartesianPosition | Represents a position in Cartesian coordinates.<br> Cartesian coordinates use x, y, and z axes to define a position in three-dimensional space. |
| [OH_PolarPosition](capi-core-oh-polarposition.md) | OH_PolarPosition | Represents a position in polar (spherical) coordinates.<br> Polar coordinates use azimuth, elevation, and distance to define a position in three-dimensional space. |
| [OH_AudioObjectPosition](capi-core-oh-audioobjectposition.md) | OH_AudioObjectPosition | Represents the position of an audio object in three-dimensional space.<br> The position can be expressed in either Cartesian or polar coordinates. |
| [OH_AudioVividMetaBuilderStruct](capi-core-oh-audiovividmetabuilderstruct.md) | OH_AudioVividMetaBuilder | Forward declaration of OH_AudioVividMetaBuilder. |

### Enum

| Name | typedef keyword | Description |
| -- | -- | -- |
| [OH_AudioVividSignalFormat](#oh_audiovividsignalformat) | OH_AudioVividSignalFormat | Enumerates the signal formats of the Audio Vivid encoder. |

### Function

| Name | Description |
| -- | -- |
| [OH_AVErrCode OH_AudioVividMetaBuilder_Create(OH_AudioVividMetaBuilder **builder, const OH_AVFormat *format)](#oh_audiovividmetabuilder_create) | Creates an Audio Vivid metadata builder. |
| [OH_AVErrCode OH_AudioVividMetaBuilder_UpdateObjectPos(OH_AudioVividMetaBuilder *builder, int32_t objectIndex, OH_AudioObjectPosition pos)](#oh_audiovividmetabuilder_updateobjectpos) | Updates the position of the audio object when the Audio Vivid signal format is [OH_AudioVividSignalFormat](capi-native-audio-vivid-h.md#oh_audiovividsignalformat).OH_AUDIO_VIVID_SIGNAL_FORMAT_MIX. In this signal format, the channel arrangement in the input encoded Pulse Code Modulation (PCM) data is as follows: bed channels come first, followed by object channels.<br> The object channels correspond to **objectIndex** in sequence, starting from 0. |
| [OH_AVErrCode OH_AudioVividMetaBuilder_UpdateObjectGain(OH_AudioVividMetaBuilder *builder, int32_t objectIndex, float gain)](#oh_audiovividmetabuilder_updateobjectgain) | Updates the linear gain of audio object rendering when the Audio Vivid signal format is [OH_AudioVividSignalFormat](capi-native-audio-vivid-h.md#oh_audiovividsignalformat).OH_AUDIO_VIVID_SIGNAL_FORMAT_MIX. |
| [OH_AVErrCode OH_AudioVividMetaBuilder_GetMetaLen(const OH_AudioVividMetaBuilder *builder, bool withStaticMeta, int32_t *len)](#oh_audiovividmetabuilder_getmetalen) | Obtains the length of metadata. |
| [OH_AVErrCode OH_AudioVividMetaBuilder_GetMeta(const OH_AudioVividMetaBuilder *builder, bool withStaticMeta, uint8_t *buffer, int32_t len)](#oh_audiovividmetabuilder_getmeta) | Obtains the metadata buffer. |
| [OH_AVErrCode OH_AudioVividMetaBuilder_Destroy(OH_AudioVividMetaBuilder *builder)](#oh_audiovividmetabuilder_destroy) | Destroys an Audio Vivid metadata builder and releases resources. |
| [OH_AVErrCode OH_AudioVividMetaBuilder_CreateEmptyBuilder(OH_AudioVividMetaBuilder **builder)](#oh_audiovividmetabuilder_createemptybuilder) | Creates an empty Audio Vivid metadata builder.<br> This function is used for merging metadata scenarios. After creating an empty builder, you can update base metadata by calling [OH_AudioVividMetaBuilder_UpdateBaseMeta](capi-native-audio-vivid-h.md#oh_audiovividmetabuilder_updatebasemeta), then add, modify, or remove objects. |
| [OH_AVErrCode OH_AudioVividMetaBuilder_UpdateBaseMeta(OH_AudioVividMetaBuilder *builder, const uint8_t *buffer, int32_t len)](#oh_audiovividmetabuilder_updatebasemeta) | Updates the base metadata of the builder.<br> The buffer contains complete Audio Vivid metadata, which may include static metadata and/or dynamic metadata. The builder will retain the soundbed and object information from the base metadata. |
| [OH_AVErrCode OH_AudioVividMetaBuilder_AddObject(OH_AudioVividMetaBuilder *builder, int32_t *objectIndex)](#oh_audiovividmetabuilder_addobject) | Adds a new audio object to the builder.<br> After adding an object, you can update its position and gain using [OH_AudioVividMetaBuilder_UpdateObjectPos](capi-native-audio-vivid-h.md#oh_audiovividmetabuilder_updateobjectpos) and [OH_AudioVividMetaBuilder_UpdateObjectGain](capi-native-audio-vivid-h.md#oh_audiovividmetabuilder_updateobjectgain). |
| [OH_AVErrCode OH_AudioVividMetaBuilder_RemoveObject(OH_AudioVividMetaBuilder *builder, int32_t objectIndex)](#oh_audiovividmetabuilder_removeobject) | Removes an audio object from the builder.<br> Only objects added by [OH_AudioVividMetaBuilder_AddObject](capi-native-audio-vivid-h.md#oh_audiovividmetabuilder_addobject) can be removed. Base objects from the base metadata cannot be removed. After removal, the indices of remaining objects remain unchanged. |

## Enum type description

### OH_AudioVividSignalFormat

```c
enum OH_AudioVividSignalFormat
```

**Description**

Enumerates the signal formats of the Audio Vivid encoder.

**System capability**: SystemCapability.Multimedia.Media.Core

**Since**: 26.0.0

| Enum item | Description |
| -- | -- |
| OH_AUDIO_VIVID_SIGNAL_FORMAT_MONO = 0 | Mono. The encoder accepts mono data and internally sets the channel layout to [OH_AudioChannelLayout](capi-native-audio-channel-layout-h.md#oh_audiochannellayout).CH_LAYOUT_MONO.<br>**Since**: 26.0.0 |
| OH_AUDIO_VIVID_SIGNAL_FORMAT_STEREO = 1 | Stereo. The encoder accepts stereo data and internally sets the channel layout to [OH_AudioChannelLayout](capi-native-audio-channel-layout-h.md#oh_audiochannellayout).CH_LAYOUT_STEREO.<br>**Since**: 26.0.0 |
| OH_AUDIO_VIVID_SIGNAL_FORMAT_MC = 2 | Multi-channel audio. The encoder supports the following channel layouts: [OH_AudioChannelLayout](capi-native-audio-channel-layout-h.md#oh_audiochannellayout).CH_LAYOUT_5POINT1, [OH_AudioChannelLayout](capi-native-audio-channel-layout-h.md#oh_audiochannellayout).CH_LAYOUT_5POINT1POINT2, [OH_AudioChannelLayout](capi-native-audio-channel-layout-h.md#oh_audiochannellayout).CH_LAYOUT_5POINT1POINT4, [OH_AudioChannelLayout](capi-native-audio-channel-layout-h.md#oh_audiochannellayout).CH_LAYOUT_7POINT1, [OH_AudioChannelLayout](capi-native-audio-channel-layout-h.md#oh_audiochannellayout).CH_LAYOUT_7POINT1POINT2 and [OH_AudioChannelLayout](capi-native-audio-channel-layout-h.md#oh_audiochannellayout).CH_LAYOUT_7POINT1POINT4.<br>**Since**: 26.0.0 |
| OH_AUDIO_VIVID_SIGNAL_FORMAT_MIX = 4 | Hybrid mode, including a bed and an object. The bed supports the following channel layouts: [OH_AudioChannelLayout](capi-native-audio-channel-layout-h.md#oh_audiochannellayout).CH_LAYOUT_STEREO, [OH_AudioChannelLayout](capi-native-audio-channel-layout-h.md#oh_audiochannellayout).CH_LAYOUT_5POINT1, [OH_AudioChannelLayout](capi-native-audio-channel-layout-h.md#oh_audiochannellayout).CH_LAYOUT_5POINT1POINT2, [OH_AudioChannelLayout](capi-native-audio-channel-layout-h.md#oh_audiochannellayout).CH_LAYOUT_5POINT1POINT4, [OH_AudioChannelLayout](capi-native-audio-channel-layout-h.md#oh_audiochannellayout).CH_LAYOUT_7POINT1, [OH_AudioChannelLayout](capi-native-audio-channel-layout-h.md#oh_audiochannellayout).CH_LAYOUT_7POINT1POINT2 and [OH_AudioChannelLayout](capi-native-audio-channel-layout-h.md#oh_audiochannellayout).CH_LAYOUT_7POINT1POINT4.<br>**Since**: 26.0.0 |


## Function description

### OH_AudioVividMetaBuilder_Create()

```c
OH_AVErrCode OH_AudioVividMetaBuilder_Create(OH_AudioVividMetaBuilder **builder, const OH_AVFormat *format)
```

**Description**

Creates an Audio Vivid metadata builder.

> **Note**:
>
> Lifecycle Management:* *     The instance created by this function must be manually released by calling [OH_AudioVividMetaBuilder_Destroy](capi-native-audio-vivid-h.md#oh_audiovividmetabuilder_destroy) when it is no longer needed to prevent memory leaks.

**System capability**: SystemCapability.Multimedia.Media.Core

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AudioVividMetaBuilder](capi-core-oh-audiovividmetabuilderstruct.md) **builder | Output parameter, which is used to obtain the double pointer to the **OH_AudioVividMetaBuilder**<br>instance. |
| const OH_AVFormat *format | Pointer to **OH_AVFormat** that contains the audio format information. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AVErrCode | [AV_ERR_OK](capi-native-averrors-h.md#oh_averrcode): The operation is successful.      <br>[AV_ERR_INVALID_VAL](capi-native-averrors-h.md#oh_averrcode): The builder or format parameter is a null pointer or invalid.      <br>[AV_ERR_UNSUPPORT](capi-native-averrors-h.md#oh_averrcode): This function is not supported on the device.      <br>[AV_ERR_UNKNOWN](capi-native-averrors-h.md#oh_averrcode): Failed to create the builder. This is an unknown error. Check the log for details. |

### OH_AudioVividMetaBuilder_UpdateObjectPos()

```c
OH_AVErrCode OH_AudioVividMetaBuilder_UpdateObjectPos(OH_AudioVividMetaBuilder *builder, int32_t objectIndex, OH_AudioObjectPosition pos)
```

**Description**

Updates the position of the audio object when the Audio Vivid signal format is [OH_AudioVividSignalFormat](capi-native-audio-vivid-h.md#oh_audiovividsignalformat).OH_AUDIO_VIVID_SIGNAL_FORMAT_MIX. In this signal format, the channel arrangement in the input encoded Pulse Code Modulation (PCM) data is as follows: bed channels come first, followed by object channels.<br> The object channels correspond to **objectIndex** in sequence, starting from 0.

**System capability**: SystemCapability.Multimedia.Media.Core

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AudioVividMetaBuilder](capi-core-oh-audiovividmetabuilderstruct.md) *builder | Pointer to **OH_AudioVividMetaBuilder**. |
| int32_t objectIndex | Index of the audio object to be updated, starting from 0. The value cannot be greater than {@link OH_MD_KEY_AUDIO_OBJECT_NUMBER} set in the **format** parameter passed to [OH_AudioVividMetaBuilder_Create](capi-native-audio-vivid-h.md#oh_audiovividmetabuilder_create) for creating the builder. |
| [OH_AudioObjectPosition](capi-core-oh-audioobjectposition.md) pos | New position of the audio object source. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AVErrCode | [AV_ERR_OK](capi-native-averrors-h.md#oh_averrcode): The operation is successful.      <br>[AV_ERR_INVALID_VAL](capi-native-averrors-h.md#oh_averrcode): The builder parameter is a null pointer or invalid, or the objectIndex      or pos parameter is invalid. |

### OH_AudioVividMetaBuilder_UpdateObjectGain()

```c
OH_AVErrCode OH_AudioVividMetaBuilder_UpdateObjectGain(OH_AudioVividMetaBuilder *builder, int32_t objectIndex, float gain)
```

**Description**

Updates the linear gain of audio object rendering when the Audio Vivid signal format is [OH_AudioVividSignalFormat](capi-native-audio-vivid-h.md#oh_audiovividsignalformat).OH_AUDIO_VIVID_SIGNAL_FORMAT_MIX.

**System capability**: SystemCapability.Multimedia.Media.Core

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AudioVividMetaBuilder](capi-core-oh-audiovividmetabuilderstruct.md) *builder | Pointer to **OH_AudioVividMetaBuilder**. |
| int32_t objectIndex | Index of the audio object to be updated, starting from 0. The value cannot be greater than {@link OH_MD_KEY_AUDIO_OBJECT_NUMBER} set in the **format** parameter passed to [OH_AudioVividMetaBuilder_Create](capi-native-audio-vivid-h.md#oh_audiovividmetabuilder_create) for creating the builder. |
| float gain | Linear gain applied during object rendering. The value range is [0.0, 6.0], where **0.0** indicates silence, and **1.0** indicates no change. This parameter is optional. If it is not set, no gain is applied. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AVErrCode | [AV_ERR_OK](capi-native-averrors-h.md#oh_averrcode): The operation is successful.      <br>[AV_ERR_INVALID_VAL](capi-native-averrors-h.md#oh_averrcode): The builder parameter is a null pointer or invalid, or the objectIndex      or gain parameter is invalid. |

### OH_AudioVividMetaBuilder_GetMetaLen()

```c
OH_AVErrCode OH_AudioVividMetaBuilder_GetMetaLen(const OH_AudioVividMetaBuilder *builder, bool withStaticMeta, int32_t *len)
```

**Description**

Obtains the length of metadata.

**System capability**: SystemCapability.Multimedia.Media.Core

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| [const OH_AudioVividMetaBuilder](capi-core-oh-audiovividmetabuilderstruct.md) *builder | Pointer to **OH_AudioVividMetaBuilder**. |
| bool withStaticMeta | Whether the output length includes static metadata. The value **true** indicates that the output length includes static metadata, and the value **false** indicates that the output length includes only dynamic metadata. |
| int32_t *len | Pointer used to receive the metadata length. The unit is bytes. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AVErrCode | [AV_ERR_OK](capi-native-averrors-h.md#oh_averrcode): The operation is successful.      <br>[AV_ERR_INVALID_VAL](capi-native-averrors-h.md#oh_averrcode): The builder parameter is a null pointer or invalid, or the len parameter      is a null pointer. |

### OH_AudioVividMetaBuilder_GetMeta()

```c
OH_AVErrCode OH_AudioVividMetaBuilder_GetMeta(const OH_AudioVividMetaBuilder *builder, bool withStaticMeta, uint8_t *buffer, int32_t len)
```

**Description**

Obtains the metadata buffer.

**System capability**: SystemCapability.Multimedia.Media.Core

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| [const OH_AudioVividMetaBuilder](capi-core-oh-audiovividmetabuilderstruct.md) *builder | Pointer to **OH_AudioVividMetaBuilder**. |
| bool withStaticMeta | Whether the output buffer includes static metadata. The value **true** indicates that the output buffer includes static metadata, and the value **false** indicates that the output buffer includes only dynamic metadata. |
| uint8_t *buffer | Pointer to the buffer for receiving the metadata. |
| int32_t len | Buffer length, in bytes. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AVErrCode | [AV_ERR_OK](capi-native-averrors-h.md#oh_averrcode): The operation is successful.      <br>[AV_ERR_INVALID_VAL](capi-native-averrors-h.md#oh_averrcode): The builder parameter is a null pointer or invalid, the buffer parameter      is a null pointer, or the len parameter value is insufficient. |

### OH_AudioVividMetaBuilder_Destroy()

```c
OH_AVErrCode OH_AudioVividMetaBuilder_Destroy(OH_AudioVividMetaBuilder *builder)
```

**Description**

Destroys an Audio Vivid metadata builder and releases resources.

**System capability**: SystemCapability.Multimedia.Media.Core

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AudioVividMetaBuilder](capi-core-oh-audiovividmetabuilderstruct.md) *builder | Pointer to **OH_AudioVividMetaBuilder** to be destroyed. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AVErrCode | [AV_ERR_OK](capi-native-averrors-h.md#oh_averrcode): The operation is successful.      <br>[AV_ERR_INVALID_VAL](capi-native-averrors-h.md#oh_averrcode): The builder parameter is a null pointer. |

### OH_AudioVividMetaBuilder_CreateEmptyBuilder()

```c
OH_AVErrCode OH_AudioVividMetaBuilder_CreateEmptyBuilder(OH_AudioVividMetaBuilder **builder)
```

**Description**

Creates an empty Audio Vivid metadata builder.<br> This function is used for merging metadata scenarios. After creating an empty builder, you can update base metadata by calling [OH_AudioVividMetaBuilder_UpdateBaseMeta](capi-native-audio-vivid-h.md#oh_audiovividmetabuilder_updatebasemeta), then add, modify, or remove objects.

> **Note**:
>
> Lifecycle Management:* *      The instance created by this function must be manually released by calling [OH_AudioVividMetaBuilder_Destroy](capi-native-audio-vivid-h.md#oh_audiovividmetabuilder_destroy) when it is no longer needed to prevent memory leaks.

**System capability**: SystemCapability.Multimedia.Media.Core

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AudioVividMetaBuilder](capi-core-oh-audiovividmetabuilderstruct.md) **builder | Output Parameter. Pointer to retrieve the OH_AudioVividMetaBuilder instance pointer. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AVErrCode | [AV_ERR_OK](capi-native-averrors-h.md#oh_averrcode): The operation is successful.      <br>[AV_ERR_INVALID_VAL](capi-native-averrors-h.md#oh_averrcode): builder is nullptr.      <br>[AV_ERR_UNSUPPORT](capi-native-averrors-h.md#oh_averrcode): current device not support this function.      <br>[AV_ERR_UNKNOWN](capi-native-averrors-h.md#oh_averrcode): create builder fail with unknown error. For details, check logs. |

### OH_AudioVividMetaBuilder_UpdateBaseMeta()

```c
OH_AVErrCode OH_AudioVividMetaBuilder_UpdateBaseMeta(OH_AudioVividMetaBuilder *builder, const uint8_t *buffer, int32_t len)
```

**Description**

Updates the base metadata of the builder.<br> The buffer contains complete Audio Vivid metadata, which may include static metadata and/or dynamic metadata. The builder will retain the soundbed and object information from the base metadata.

> **Note**:
>
> Constraint:* *      The total number of soundbed channels plus base objects plus added objects must not exceed 16.

**System capability**: SystemCapability.Multimedia.Media.Core

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AudioVividMetaBuilder](capi-core-oh-audiovividmetabuilderstruct.md) *builder | Pointer to the OH_AudioVividMetaBuilder. |
| const uint8_t *buffer | Pointer to the buffer containing the base metadata data. |
| int32_t len | Length of the buffer in bytes. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AVErrCode | [AV_ERR_OK](capi-native-averrors-h.md#oh_averrcode): The operation is successful.      <br>[AV_ERR_INVALID_VAL](capi-native-averrors-h.md#oh_averrcode), builder is nullptr or invalid, buffer is nullptr or len is invalid. |

### OH_AudioVividMetaBuilder_AddObject()

```c
OH_AVErrCode OH_AudioVividMetaBuilder_AddObject(OH_AudioVividMetaBuilder *builder, int32_t *objectIndex)
```

**Description**

Adds a new audio object to the builder.<br> After adding an object, you can update its position and gain using [OH_AudioVividMetaBuilder_UpdateObjectPos](capi-native-audio-vivid-h.md#oh_audiovividmetabuilder_updateobjectpos) and [OH_AudioVividMetaBuilder_UpdateObjectGain](capi-native-audio-vivid-h.md#oh_audiovividmetabuilder_updateobjectgain).

> **Note**:
>
> Constraint:* *      The total number of soundbed channels plus base objects plus added objects must not exceed 16.

**System capability**: SystemCapability.Multimedia.Media.Core

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AudioVividMetaBuilder](capi-core-oh-audiovividmetabuilderstruct.md) *builder | Pointer to the OH_AudioVividMetaBuilder. |
| int32_t *objectIndex | Output parameter. Pointer to receive the index of the newly added object. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AVErrCode | [AV_ERR_OK](capi-native-averrors-h.md#oh_averrcode): The operation is successful.      <br>[AV_ERR_INVALID_VAL](capi-native-averrors-h.md#oh_averrcode), builder is nullptr or invalid, objectIndex is nullptr.      <br>[AV_ERR_UNKNOWN](capi-native-averrors-h.md#oh_averrcode), add object fail with unknown error. For details, check logs. |

### OH_AudioVividMetaBuilder_RemoveObject()

```c
OH_AVErrCode OH_AudioVividMetaBuilder_RemoveObject(OH_AudioVividMetaBuilder *builder, int32_t objectIndex)
```

**Description**

Removes an audio object from the builder.<br> Only objects added by [OH_AudioVividMetaBuilder_AddObject](capi-native-audio-vivid-h.md#oh_audiovividmetabuilder_addobject) can be removed. Base objects from the base metadata cannot be removed. After removal, the indices of remaining objects remain unchanged.

**System capability**: SystemCapability.Multimedia.Media.Core

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AudioVividMetaBuilder](capi-core-oh-audiovividmetabuilderstruct.md) *builder | Pointer to the OH_AudioVividMetaBuilder. |
| int32_t objectIndex | Index of the audio object to remove. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AVErrCode | [AV_ERR_OK](capi-native-averrors-h.md#oh_averrcode): The operation is successful.      <br>[AV_ERR_INVALID_VAL](capi-native-averrors-h.md#oh_averrcode), builder is nullptr or invalid, objectIndex is invalid. |


