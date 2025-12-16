# lowpower_avsink_base.h
<!--Kit: Media Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @wang-haizhou6-->
<!--Designer: @HmQQQ-->
<!--Tester: @xchaosioda-->
<!--Adviser: @w_Machine_cc-->

## Overview

The file declares the basic dependencies for OH_LowPowerAudioSink and OH_LowPowerVideoSink.

**File to include**: <multimedia/player_framework/lowpower_avsink_base.h>

**Library**: liblowpower_avsink.so

**System capability**: SystemCapability.Multimedia.Media.LowPowerAVSink

**Since**: 20

**Related module**: [AVSinkBase](capi-avsinkbase.md)

## Summary

### Structs

| Name| typedef Keyword| Description|
| -- | -- | -- |
| [OH_AVSamplesBuffer](capi-avsinkbase-oh-avsamplesbuffer.md) | OH_AVSamplesBuffer | Describes the input data of the LowPowerAVSink. After receiving the DataNeeded callback, the application must pack data into an OH_AVSamplesBuffer instance and pass it to the corresponding lowpower_avsink.|

### Functions

| Name| Description|
| -- | -- |
| [OH_AVErrCode OH_AVSamplesBuffer_AppendOneBuffer(OH_AVSamplesBuffer *samplesBuffer, OH_AVBuffer *avBuffer)](#oh_avsamplesbuffer_appendonebuffer) | Appends data from an OH_AVBuffer instance to an OH_AVSamplesBuffer instance.|
| [int32_t OH_AVSamplesBuffer_GetRemainedCapacity(OH_AVSamplesBuffer *samplesBuffer)](#oh_avsamplesbuffer_getremainedcapacity) | Obtains the remaining capacity available in an OH_AVSamplesBuffer instance.|
| [OH_LowPowerAVSink_Capability *OH_LowPowerAVSink_GetCapability()](#oh_lowpoweravsink_getcapability) | Obtains the capability of the low-power player. It mainly helps you find out what the low-power player can do, including the media formats and features it supports.<br> When you call this function, you can learn about the device's capabilities in audio and video processing. For example, you can find out which encoding and decoding formats are supported, as well as the range of bit rates that the device can handle.|

## Function Description

### OH_AVSamplesBuffer_AppendOneBuffer()

```c
OH_AVErrCode OH_AVSamplesBuffer_AppendOneBuffer(OH_AVSamplesBuffer *samplesBuffer, OH_AVBuffer *avBuffer)
```

**Description**

Appends data from an OH_AVBuffer instance to an OH_AVSamplesBuffer instance.

**Since**: 20

**Parameters**

| Name| Description|
| -- | -- |
| [OH_AVSamplesBuffer](capi-avsinkbase-oh-avsamplesbuffer.md) *samplesBuffer | Pointer to an OH_AVSamplesBuffer instance.|
| [OH_AVBuffer](../apis-avcodec-kit/capi-core-oh-avbuffer.md) *avBuffer | Pointer to an OH_AVBuffer instance.|

**Returns**

| Type| Description|
| -- | -- |
| [OH_AVErrCode](../apis-avcodec-kit/capi-native-averrors-h.md#oh_averrcode) | **AV_ERR_OK**: The operation is successful.<br> **AV_ERR_INVALID_VAL**: An input parameter is nullptr or invalid.<br> **AV_ERR_NO_MEMORY**: The framePacketBuffer does not have sufficient remaining capacity to append an OH_AVBuffer.<br> **AV_ERR_UNKNOWN**: An unknown error occurs.|

### OH_AVSamplesBuffer_GetRemainedCapacity()

```c
int32_t OH_AVSamplesBuffer_GetRemainedCapacity(OH_AVSamplesBuffer *samplesBuffer)
```

**Description**

Obtains the remaining capacity available in an OH_AVSamplesBuffer instance.

**Since**: 20

**Parameters**

| Name| Description|
| -- | -- |
| [OH_AVSamplesBuffer](capi-avsinkbase-oh-avsamplesbuffer.md) *samplesBuffer | Pointer to an OH_AVSamplesBuffer instance.|

**Returns**

| Type| Description|
| -- | -- |
| int32_t | Remaining capacity available in the OH_AVSamplesBuffer instance, in bytes. If **sampleBuffer** or data poniter is nullptr or invalid, **-1** is returned.|

### OH_LowPowerAVSink_GetCapability()

```c
OH_LowPowerAVSink_Capability *OH_LowPowerAVSink_GetCapability()
```

**Description**

Obtains the capability of the low-power player. It mainly helps you find out what the low-power player can do, including the media formats and features it supports.<br> When you call this function, you can learn about the device's capabilities in audio and video processing. For example, you can find out which encoding and decoding formats are supported, as well as the range of bit rates that the device can handle.

**Since**: 21

**Returns**

| Type| Description|
| -- | -- |
| OH_LowPowerAVSink_Capability * | **OH_LowPowerAVSink_Capability**: The low-power player is supported.<br> **nullptr**: The low-power player is not supported or the capability fails to be obtained.|
