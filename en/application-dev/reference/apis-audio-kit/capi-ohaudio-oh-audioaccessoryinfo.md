# OH_AudioAccessoryInfo
<!--Kit: Audio Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @songshenke-->
<!--Designer: @zhanganxiang1-->
<!--Tester: @Filger-->
<!--Adviser: @w_Machine_cc-->
<!-- md-trans-meta sourceCommit=03e07731f28ea3c4338c42628096ca0f42c1efd0 translatedAt=2026-11-03T04:16:49.296Z pushedAt=2026-11-04T03:11:46.977Z nl=1 -->

```c
typedef struct {...} OH_AudioAccessoryInfo
```

## Overview

Defines the basic information about an audio accessory.

Before passing this struct to the system, the caller must set structSize to sizeof(OH_AudioAccessoryInfo).

**Since:** 26.0.0

**Related module:** [OHAudio](capi-ohaudio.md)

**File to include:** [native_audio_accessory_common.h](capi-native-audio-accessory-common-h.md)

## Summary

### Member Variables

| Name | Description |
| -- | -- |
| uint32_t structSize | Size of the struct, in bytes.<br>The caller must initialize this field.<br>The system uses this field to verify the struct size. |
| const char *accessoryName | Name of the accessory (the name of the external audio device), used for UX display.<br>The system performs a deep copy of this field. |
| const char *manufacturer | Name of the manufacturer.<br>The system performs a deep copy of this field. |
| const char *modelNumber | Model number.<br>The system performs a deep copy of this field. |
| const char *macAddress | MAC address of the accessory.<br>The system performs a deep copy of this field. |
| [OH_AudioAccessoryType](capi-native-audio-accessory-common-h.md#oh_audioaccessorytype) type | Connection type of the accessory. |
| bool isUnidirectional | Whether the accessory is a unidirectional audio device. The value true indicates a unidirectional device, and false indicates a bidirectional device. |
