# OH_AudioDeviceDescriptorArray
<!--Kit: Audio Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @songshenke-->
<!--Designer: @zhanganxiang1-->
<!--Tester: @Filger-->
<!--Adviser: @w_Machine_cc-->
<!-- md-trans-meta sourceCommit=138f7dcec9e99067f11a5ba1afa58271363a7ef2 translatedAt=2026-10-08T12:41:32.266Z pushedAt=2026-10-13T06:27:50.935Z -->

```c
typedef struct OH_AudioDeviceDescriptorArray {...} OH_AudioDeviceDescriptorArray
```

## Overview

Declares the audio device descriptor array struct.

**Since**: 12

**Related module**: [OHAudio](capi-ohaudio.md)

**Header file**: [native_audio_device_base.h](capi-native-audio-device-base-h.md)

## Summary

### Member Variables

| Name| Description|
| -- | -- |
| uint32_t size | Number of elements in the audio device descriptor array. |
| [OH_AudioDeviceDescriptor](capi-ohaudio-oh-audiodevicedescriptor.md)** descriptors | Double pointer to the audio device descriptors in the array.|


