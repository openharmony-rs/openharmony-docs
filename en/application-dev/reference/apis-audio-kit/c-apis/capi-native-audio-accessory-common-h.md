# native_audio_accessory_common.h

## Overview

Declare common types for external audio accessory device interfaces.

**Library**: libohaudio.so

**System capability**: SystemCapability.Multimedia.Audio.Core

**Since**: 10

**Related module**: [OHAudio](capi-ohaudio.md)

## Summary

### Struct

| Name | typedef keyword | Description |
| -- | -- | -- |
| [OH_AudioAccessoryInfo](capi-ohaudio-oh-audioaccessoryinfo.md) | OH_AudioAccessoryInfo | Defines the basic information of an audio accessory.<br> <b>Version Control:</b> Callers MUST set structSize to sizeof(OH_AudioAccessoryInfo) before passing this structure to the framework. |
| [OH_AudioAccessoryNoiseReductionCapability](capi-ohaudio-oh-audioaccessorynoisereductioncapability.md) | OH_AudioAccessoryNoiseReductionCapability | Defines the noise reduction capability of an audio accessory. |
| [OH_AudioAccessoryCapabilities](capi-ohaudio-oh-audioaccessorycapabilities.md) | OH_AudioAccessoryCapabilities | Defines the capabilities of an audio accessory.<br> <b>Version Control:</b> Callers MUST set structSize to sizeof(OH_AudioAccessoryCapabilities). |
| [OH_AudioAccessoryManager](capi-ohaudio-oh-audioaccessorymanager.md) | OH_AudioAccessoryManager | Declare the audio accessory manager. |
| [OH_AudioAccessory](capi-ohaudio-oh-audioaccessory.md) | OH_AudioAccessory | Declare the audio accessory. |
| [OH_AudioAccessoryInputStream](capi-ohaudio-oh-audioaccessoryinputstream.md) | OH_AudioAccessoryInputStream | Declare the audio accessory input stream. |

### Enum

| Name | typedef keyword | Description |
| -- | -- | -- |
| [OH_AudioAccessoryType](#oh_audioaccessorytype) | OH_AudioAccessoryType | Enumerates audio accessory connection types. |

## Enum type description

### OH_AudioAccessoryType

```c
enum OH_AudioAccessoryType
```

**Description**

Enumerates audio accessory connection types.

**System capability**: SystemCapability.Multimedia.Audio.Core

**Since**: 26.0.0

| Enum item | Description |
| -- | -- |
| AUDIO_ACCESSORY_TYPE_BT_SPP = 1 | Bluetooth SPP (Signal Processing Plugin) connection.<br>**Since**: 26.0.0 |


