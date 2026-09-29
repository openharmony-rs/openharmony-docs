# native_audio_suite_base.h(System API)

## Overview

Declare underlying data structure.

**Library**: libohaudiosuite.so

**Since**: 22

**System API:** This is a system API.

**Related module**: [OHAudioSuite](capi-ohaudiosuite.md)

## Summary

### Struct

| Name | Description |
| -- | -- |
| [OH_AudioSuite_SystemNodeFormat(System API)](capi-ohaudiosuite-oh-audiosuite-systemnodeformat-sys.md) | Define the audio format info structure, used to describe basic audio format for system node.<br>**System API:** This is a system API. |
| [OH_AudioSuite_MetaFrame(System API)](capi-ohaudiosuite-oh-audiosuite-metaframe-sys.md) | Define the audio meta data frame structure. This structure is used to pass audio data and meta data together.<br>**System API:** This is a system API. |

### Enum

| Name | typedef keyword | Description |
| -- | -- | -- |
| [OH_AudioSuite_SystemNodeType(System API)](#oh_audiosuite_systemnodetype) | OH_AudioSuite_SystemNodeType | Define audio node system type.<br>**System API:** This is a system API. |

## Enum type description

### OH_AudioSuite_SystemNodeType

```c
enum OH_AudioSuite_SystemNodeType
```

**Description**

Define audio node system type.

**Since**: 26.0.0

**System API:** This is a system API.

| Enum item | Description |
| -- | -- |
| OH_AUDIOSUITE_EFFECT_NODE_SYSTEM_TYPE_DIALOGUE_ENHANCE = 301 |  |
| OH_AUDIOSUITE_EFFECT_NODE_SYSTEM_TYPE_VOICE_BEAUTIFIER = 302 |  |


