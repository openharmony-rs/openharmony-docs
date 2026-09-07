# native_audio_accessory_common.h

<!--Kit: Audio Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @songshenke-->
<!--Designer: @hao-liangfei; @zhanganxiang-->
<!--Tester: @Filger-->
<!--Adviser: @w_Machine_cc-->
<!-- md-trans-meta sourceCommit=fea09459a0476f095195448c2ce1ed787d76ab6a translatedAt=2026-08-31T02:31:45.829Z pushedAt=2026-08-31T08:07:46.799Z -->

## Overview

Declares the public data structures of the external audio accessory device interfaces.

Defines the public types of the audio accessory interfaces.

**File to include:** <ohaudio/native_audio_accessory_common.h>

**Library:** libohaudio.so

**System capability:** SystemCapability.Multimedia.Audio.Core

**Since:** 26.0.0

**Related module:** [OHAudio](capi-ohaudio.md)

## Summary

### Structs

| Name | typedef Keyword | Description |
| -- | -- | -- |
| [OH_AudioAccessoryManager](capi-ohaudio-oh-audioaccessorymanager.md) | OH_AudioAccessoryManager | Declares an audio accessory manager. |
| [OH_AudioAccessory](capi-ohaudio-oh-audioaccessory.md) | OH_AudioAccessory | Declares an audio accessory. |
| [OH_AudioAccessoryInputStream](capi-ohaudio-oh-audioaccessoryinputstream.md) | OH_AudioAccessoryInputStream | Declares an audio accessory input stream. |
| [OH_AudioAccessoryInfo](capi-ohaudio-oh-audioaccessoryinfo.md) | OH_AudioAccessoryInfo | Defines the basic information about an audio accessory. |
| [OH_AudioAccessoryNoiseReductionCapability](capi-ohaudio-oh-audioaccessorynoisereductioncapability.md) | OH_AudioAccessoryNoiseReductionCapability | Defines the noise reduction capability of an audio accessory. |
| [OH_AudioAccessoryCapabilities](capi-ohaudio-oh-audioaccessorycapabilities.md) | OH_AudioAccessoryCapabilities | Defines the capabilities of an audio accessory. |

### Enum

| Name | typedef Keyword | Description |
| -- | -- | -- |
| [OH_AudioAccessoryType](#oh_audioaccessorytype) | OH_AudioAccessoryType | Enumerates the audio accessory connection types. |

## Enum Description

### OH_AudioAccessoryType

```c
enum OH_AudioAccessoryType
```

**Description**

Enumerates the connection types of an audio accessory.

**Since:** 26.0.0

| enum item | Description |
| -- | -- |
| AUDIO_ACCESSORY_TYPE_BT_SPP = 1 | Bluetooth Serial Port Profile (SPP) connection. |