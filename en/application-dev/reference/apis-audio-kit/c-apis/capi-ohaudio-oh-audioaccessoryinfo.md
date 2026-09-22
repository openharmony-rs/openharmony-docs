# OH_AudioAccessoryInfo

```c
typedef struct OH_AudioAccessoryInfo {...} OH_AudioAccessoryInfo
```

## Overview

Defines the basic information of an audio accessory.<br> <b>Version Control:</b> Callers MUST set structSize to sizeof(OH_AudioAccessoryInfo) before passing this structure to the framework.

**System capability**: SystemCapability.Multimedia.Audio.Core

**Since**: 26.0.0

**Related module**: [OHAudio](capi-ohaudio.md)

**Header file**: [native_audio_accessory_common.h](capi-native-audio-accessory-common-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| uint32_t structSize | Size of this structure in bytes. Must be initialized by the caller (e.g., info.structSize = sizeof(OH_AudioAccessoryInfo)). The framework uses this to determine which version of the structure is being used.<br>**Since**: 26.0.0 |
| const char *accessoryName | Accessory name for UX display, such as "DJI Mic 2". The framework performs a deep copy of this field.<br>**Since**: 26.0.0 |
| const char *manufacturer | Manufacturer name, such as "DJI". The framework performs a deep copy of this field.<br>**Since**: 26.0.0 |
| const char *modelNumber | Model number, such as "CP236". The framework performs a deep copy of this field.<br>**Since**: 26.0.0 |
| const char *macAddress | MAC address of the accessory, such as "00:11:22:33:44:55". The framework performs a deep copy of this field.<br>**Since**: 26.0.0 |
| [OH_AudioAccessoryType](capi-native-audio-accessory-common-h.md#oh_audioaccessorytype) type | Accessory connection type.<br>**Since**: 26.0.0 |
| bool isUnidirectional | Indicates whether the accessory is a unidirectional audio device. true: unidirectional device; false: bidirectional device.<br>**Since**: 26.0.0 |


