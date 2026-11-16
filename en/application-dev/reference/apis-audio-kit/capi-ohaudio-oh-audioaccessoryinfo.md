# OH_AudioAccessoryInfo
<!--Kit: Audio Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @songshenke-->
<!--Designer: @zhanganxiang1-->
<!--Tester: @Filger-->
<!--Adviser: @w_Machine_cc-->
<!-- md-trans-meta sourceCommit=96f4a6288457dc7323c09f4157fef4291d5dc537 translatedAt=2026-11-09T10:26:30.633Z pushedAt=2026-11-09T11:28:48.584Z nl=1 -->

```c
typedef struct {...} OH_AudioAccessoryInfo
```

## Overview

Defines the basic information of an audio accessory.

Before passing this struct to the system, the caller must set **structSize** to sizeof(OH_AudioAccessoryInfo).

**Since:** 26.0.0

**Related module:** [OHAudio](capi-ohaudio.md)

**File to include:** [native_audio_accessory_common.h](capi-native-audio-accessory-common-h.md)

## Summary

### Member Variables

| Name | Description |
| -- | -- |
| uint32_t structSize | Size of the struct, in bytes.<br>The caller must initialize this field.<br>The system verifies the struct size through this field. |
| const char *accessoryName | Name of the accessory (name of the external audio device), used for UX display.<br>The system performs a deep copy of this field. |
| const char *manufacturer | Name of the manufacturer.<br>The system performs a deep copy of this field. |
| const char *modelNumber | Model number.<br>The system performs a deep copy of this field. |
| const char *macAddress | MAC address of the accessory.<br>The system performs a deep copy of this field. |
| [OH_AudioAccessoryType](capi-native-audio-accessory-common-h.md#oh_audioaccessorytype) type | Connection type of the accessory. |
| bool isUnidirectional | Whether the accessory is a unidirectional audio device. The value true indicates a unidirectional device, and false indicates a bidirectional device. |