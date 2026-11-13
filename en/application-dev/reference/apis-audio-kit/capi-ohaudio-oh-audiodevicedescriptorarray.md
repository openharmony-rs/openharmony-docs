# OH_AudioDeviceDescriptorArray
<!--Kit: Audio Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @songshenke-->
<!--Designer: @zhanganxiang1-->
<!--Tester: @Filger-->
<!--Adviser: @w_Machine_cc-->
<!-- md-trans-meta sourceCommit=b6df2b7e0ebfe1d3ad7614c1acb5050cb14b218b translatedAt=2026-11-03T04:19:52.937Z pushedAt=2026-11-04T03:11:46.990Z nl=1 -->

```c
typedef struct OH_AudioDeviceDescriptorArray {...} OH_AudioDeviceDescriptorArray
```

## Overview

Declares a struct for an audio device descriptor array.

**Since**: 12

**Related module**: [OHAudio](capi-ohaudio.md)

**Header file**: [native_audio_device_base.h](capi-native-audio-device-base-h.md)

## Summary

### Member Variables

| Name| Description|
| -- | -- |
| uint32_t size | Number of elements in the audio device descriptor array. |
| [OH_AudioDeviceDescriptor](capi-ohaudio-oh-audiodevicedescriptor.md)** descriptors | Double pointer to the audio device descriptors in the array.|


