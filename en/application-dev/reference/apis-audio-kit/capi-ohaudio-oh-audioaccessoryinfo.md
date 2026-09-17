# OH_AudioAccessoryInfo

<!--Kit: Audio Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @songshenke-->
<!--Designer: @hao-liangfei; @zhanganxiang-->
<!--Tester: @Filger-->
<!--Adviser: @w_Machine_cc-->
<!-- md-trans-meta sourceCommit=fea09459a0476f095195448c2ce1ed787d76ab6a translatedAt=2026-08-31T02:32:20.925Z pushedAt=2026-08-31T08:40:57.362Z -->

```c
typedef struct OH_AudioAccessoryInfo {...} OH_AudioAccessoryInfo
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