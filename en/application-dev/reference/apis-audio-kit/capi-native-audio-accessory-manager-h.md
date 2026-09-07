# native_audio_accessory_manager.h

<!--Kit: Audio Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @songshenke-->
<!--Designer: @hao-liangfei; @zhanganxiang-->
<!--Tester: @Filger-->
<!--Adviser: @w_Machine_cc-->
<!-- md-trans-meta sourceCommit=f6b98329623e60d030164db3f328ee8bd5405051 translatedAt=2026-08-31T02:32:24.387Z pushedAt=2026-08-31T09:33:15.829Z -->

## Overview

Declares the APIs related to the audio accessory manager.

The APIs in this file are used to manage the creation, connection, disconnection, and destruction of audio accessories.

**File to include:** <ohaudio/native_audio_accessory_manager.h>

**Library:** libohaudio.so

**System capability:** SystemCapability.Multimedia.Audio.Core

**Since:** 26.0.0

**Related module:** [OHAudio](capi-ohaudio.md)

## Summary

### Functions

| Name | typedef Keyword | Description |
| -- | -- | -- |
| [typedef bool (\*OH_AudioAccessory_SetNoiseReductionCallback)(OH_AudioAccessory *accessory, OH_AudioNoiseReductionMode mode)](#oh_audioaccessory_setnoisereductioncallback) | OH_AudioAccessory_SetNoiseReductionCallback | Defines the callback for audio accessory noise reduction mode changes. |
| [OH_AudioCommon_Result OH_AudioManager_GetAccessoryManager(OH_AudioAccessoryManager **outManager)](#oh_audiomanager_getaccessorymanager) | - | Obtains an audio accessory manager instance. |
| [OH_AudioCommon_Result OH_AudioAccessoryManager_CreateInput(OH_AudioAccessoryManager *manager, const OH_AudioAccessoryInfo *info, const OH_AudioAccessoryCapabilities *capabilities, OH_AudioAccessory_OpenInputStreamCallback openInputStream, OH_AudioAccessory **outOwnedAccessory)](#oh_audioaccessorymanager_createinput) | - | Creates an audio accessory instance and sets its supported audio stream capabilities. |
| [OH_AudioCommon_Result OH_AudioAccessoryManager_SetAssociatedMacAddresses(OH_AudioAccessoryManager *manager, OH_AudioAccessory *accessory, const char **macAddresses, uint32_t count)](#oh_audioaccessorymanager_setassociatedmacaddresses) | - | Sets the MAC address list of the secondary accessories used together with the primary audio accessory. |
| [OH_AudioCommon_Result OH_AudioAccessoryManager_RegisterNoiseReductionCapability(OH_AudioAccessoryManager *manager, OH_AudioAccessory *accessory, const OH_AudioAccessoryNoiseReductionCapability *capability, OH_AudioAccessory_SetNoiseReductionCallback onNoiseReduction)](#oh_audioaccessorymanager_registernoisereductioncapability) | - | Registers the noise reduction capability of an audio accessory. |
| [OH_AudioCommon_Result OH_AudioAccessoryManager_SetNoiseReductionMode(OH_AudioAccessoryManager *manager, OH_AudioAccessory *accessory, OH_AudioNoiseReductionMode mode)](#oh_audioaccessorymanager_setnoisereductionmode) | - | Sets the noise reduction mode of an audio accessory. |
| [OH_AudioCommon_Result OH_AudioAccessoryManager_Connected(OH_AudioAccessoryManager *manager, OH_AudioAccessory *accessory)](#oh_audioaccessorymanager_connected) | - | Connects an audio accessory to the audio system. |
| [OH_AudioCommon_Result OH_AudioAccessoryManager_Disconnected(OH_AudioAccessoryManager *manager, OH_AudioAccessory *accessory)](#oh_audioaccessorymanager_disconnected) | - | Disconnects an audio accessory. |
| [OH_AudioCommon_Result OH_AudioAccessoryManager_Destroy(OH_AudioAccessoryManager *manager, OH_AudioAccessory *accessory)](#oh_audioaccessorymanager_destroy) | - | Destroys an audio accessory instance. |

## Function Description

### OH_AudioAccessory_SetNoiseReductionCallback()

```c
typedef bool (*OH_AudioAccessory_SetNoiseReductionCallback)(OH_AudioAccessory *accessory, OH_AudioNoiseReductionMode mode)
```

**Description**

Defines the callback for audio accessory noise reduction mode changes.

Trigger timing: when the noise reduction mode of the accessory changes. This callback can be triggered at any time after the accessory is connected.

**Since:** 26.0.0

**Parameters**

| Name | Description |
| -- | -- |
| [OH_AudioAccessory](capi-ohaudio-oh-audioaccessory.md) *accessory | Audio accessory. |
| [OH_AudioNoiseReductionMode](capi-native-audio-common-h.md#oh_audionoisereductionmode) mode | Current noise reduction mode of the accessory. |

**Return**

| Type | Description |
| -- | -- |
| bool | true if the requested noise reduction mode is processed successfully; false otherwise. |

### OH_AudioManager_GetAccessoryManager()

```c
OH_AudioCommon_Result OH_AudioManager_GetAccessoryManager(OH_AudioAccessoryManager **outManager)
```

**Description**

Obtains an audio accessory manager instance.

**Since:** 26.0.0

**Parameters**

| Name | Description |
| -- | -- |
| [OH_AudioAccessoryManager](capi-ohaudio-oh-audioaccessorymanager.md) **outManager | Address of the pointer to OH_AudioAccessoryManager. The pointer address is managed by the system and must not be released by the caller; otherwise, exceptions may occur. |

**Return**

| Type | Description |
| -- | -- |
| [OH_AudioCommon_Result](capi-native-audio-common-h.md#oh_audiocommon_result) | AUDIOCOMMON_RESULT_SUCCESS: The function is executed successfully.<br>AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM: The outManager parameter is NULL. |

### OH_AudioAccessoryManager_CreateInput()

```c
OH_AudioCommon_Result OH_AudioAccessoryManager_CreateInput(OH_AudioAccessoryManager *manager, const OH_AudioAccessoryInfo *info, const OH_AudioAccessoryCapabilities *capabilities, OH_AudioAccessory_OpenInputStreamCallback openInputStream, OH_AudioAccessory **outOwnedAccessory)
```

**Description**

Creates an audio accessory instance and sets the audio stream capabilities it supports.

> **NOTE**
>
> - This function is used only to create an audio accessory instance. It does not create any input stream.
> - When the function is executed successfully, the system returns the created OH_AudioAccessory handle through the outOwnedAccessory handle.
> - The audio accessory instance must be released by calling OH_AudioAccessoryManager_Destroy when it is no longer used.
> - When an app requests to capture audio from this audio accessory, the system triggers the openInputStream callback.
> - During the lifecycle of an audio accessory, the input stream may be created and released multiple times.

**Since:** 26.0.0

**Parameters**

| Name | Description |
| -- | -- |
| [OH_AudioAccessoryManager](capi-ohaudio-oh-audioaccessorymanager.md) *manager | Pointer to the audio accessory manager instance obtained through OH_AudioManager_GetAccessoryManager. |
| const [OH_AudioAccessoryInfo](capi-ohaudio-oh-audioaccessoryinfo.md) *info | Pointer to the basic information of the accessory. It cannot be NULL. |
| const [OH_AudioAccessoryCapabilities](capi-ohaudio-oh-audioaccessorycapabilities.md) *capabilities | Pointer to the capabilities of the accessory. It cannot be NULL. |
| OH_AudioAccessory_OpenInputStreamCallback openInputStream | Callback invoked to open the input stream of the audio accessory. It cannot be NULL.<br>This callback is invoked only when the app requests to capture audio from this audio accessory, rather than when this function is called. |
| [OH_AudioAccessory](capi-ohaudio-oh-audioaccessory.md) **outOwnedAccessory | Address of the pointer to OH_AudioAccessory, used to receive the created audio accessory instance. |

**Return**

| Type | Description |
| -- | -- |
| [OH_AudioCommon_Result](capi-native-audio-common-h.md#oh_audiocommon_result) | Result code.<br>AUDIOCOMMON_RESULT_SUCCESS: Success.<br>AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM: Invalid parameter, including info being NULL, capabilities being NULL, openInputStream being NULL, outOwnedAccessory being NULL, incomplete info, incomplete capabilities, or outOwnedAccessory already created through OH_AudioAccessoryManager_CreateInput.<br>AUDIOCOMMON_RESULT_ERROR_ILLEGAL_STATE: The manager parameter is not initialized through OH_AudioManager_GetAccessoryManager. |

### OH_AudioAccessoryManager_SetAssociatedMacAddresses()

```c
OH_AudioCommon_Result OH_AudioAccessoryManager_SetAssociatedMacAddresses(OH_AudioAccessoryManager *manager, OH_AudioAccessory *accessory, const char **macAddresses, uint32_t count)
```

**Description**

Sets the MAC address list of the secondary accessories used in combination with the primary audio accessory.

> **NOTE**
>
> - This function applies to multi-accessory combination scenarios (for example, two-in-one and four-in-one), and supports dynamic management of accessory combinations.
> - Initialization: After an accessory is created, call this function to set the initial secondary accessory list.
> - Dynamic update: When a secondary accessory is replaced or disconnected, call this function to overwrite the old MAC list.
> - Thread safety: This function can be safely called during recording.
> - Limitation: This function is used only to update the MAC address list of secondary accessories, not to update the MAC address of the primary accessory. When the primary accessory is disconnected or its MAC address changes, disconnect and destroy the original accessory handle first, and then create an accessory instance again with the new primary accessory information.

**Since:** 26.0.0

**Parameters**

| Name | Description |
| -- | -- |
| [OH_AudioAccessoryManager](capi-ohaudio-oh-audioaccessorymanager.md) *manager | Pointer to the audio accessory manager instance obtained through OH_AudioManager_GetAccessoryManager. |
| [OH_AudioAccessory](capi-ohaudio-oh-audioaccessory.md) *accessory | Pointer to the primary accessory handle. |
| const char **macAddresses | Array of MAC addresses of secondary accessories.<br>When count is 0, this parameter can be null, indicating that the MAC address list of secondary accessories is cleared. This applies to the scenario where all secondary accessories are disconnected.<br>Each element must comply with the following rules:<br>- The format is a NUL-terminated ASCII string in colon-separated hexadecimal notation.<br>  Both uppercase and lowercase hexadecimal digits (A-F / a-f) are accepted.<br>- The string must be non-null and non-zero in length.<br>- Duplicate addresses in the same array are ignored, and only the first occurrence of each unique address takes effect. |
| uint32_t count | Number of elements in the MAC address array. |

**Return**

| Type | Description |
| -- | -- |
| [OH_AudioCommon_Result](capi-native-audio-common-h.md#oh_audiocommon_result) | Result code.<br>AUDIOCOMMON_RESULT_SUCCESS: The function is executed successfully.<br>AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM: Invalid parameter, including manager being null, manager not initialized through OH_AudioManager_GetAccessoryManager, accessory being null, or the number of addresses passed in macAddresses being inconsistent with count.<br>AUDIOCOMMON_RESULT_ERROR_ILLEGAL_STATE: The accessory parameter is not created through OH_AudioAccessoryManager_CreateInput. |

### OH_AudioAccessoryManager_RegisterNoiseReductionCapability()

```c
OH_AudioCommon_Result OH_AudioAccessoryManager_RegisterNoiseReductionCapability(OH_AudioAccessoryManager *manager, OH_AudioAccessory *accessory, const OH_AudioAccessoryNoiseReductionCapability *capability, OH_AudioAccessory_SetNoiseReductionCallback onNoiseReduction)
```

**Description**

Registers the noise reduction capability of an audio accessory.

**Since:** 26.0.0

**Parameters**

| Name | Description |
| -- | -- |
| [OH_AudioAccessoryManager](capi-ohaudio-oh-audioaccessorymanager.md) *manager | Pointer to the audio accessory manager instance obtained through OH_AudioManager_GetAccessoryManager. |
| [OH_AudioAccessory](capi-ohaudio-oh-audioaccessory.md) *accessory | Pointer to the audio accessory instance obtained through OH_AudioAccessoryManager_CreateInput. |
| const [OH_AudioAccessoryNoiseReductionCapability](capi-ohaudio-oh-audioaccessorynoisereductioncapability.md) *capability | Pointer to the noise reduction capability, which cannot be NULL. |
| OH_AudioAccessory_SetNoiseReductionCallback onNoiseReduction | Callback for audio accessory noise reduction mode changes.<br>This parameter can be NULL if the accessory does not support dynamic mode switching. |

**Return**

| Type | Description |
| -- | -- |
| [OH_AudioCommon_Result](capi-native-audio-common-h.md#oh_audiocommon_result) | Result code.<br>AUDIOCOMMON_RESULT_SUCCESS: Success.<br>AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM: Invalid parameter, including manager being NULL, manager not initialized through OH_AudioManager_GetAccessoryManager, accessory being NULL, capability being NULL, or supportedModes in capability being NULL or supportedModeCount being 0.<br>AUDIOCOMMON_RESULT_ERROR_ILLEGAL_STATE: The accessory parameter is not created through OH_AudioAccessoryManager_CreateInput. |

### OH_AudioAccessoryManager_SetNoiseReductionMode()

```c
OH_AudioCommon_Result OH_AudioAccessoryManager_SetNoiseReductionMode(OH_AudioAccessoryManager *manager, OH_AudioAccessory *accessory, OH_AudioNoiseReductionMode mode)
```

**Description**

Sets the noise reduction mode of an audio accessory.

> **NOTE**
>
> - This function is called by the service or app associated with the accessory to synchronize the current noise reduction mode of the accessory to the system.
> - It is typically used when the noise reduction mode is changed through other means (such as a hardware button or a companion app), to ensure that the noise reduction mode on the system side stays consistent with the actual noise reduction mode of the accessory.

**Since:** 26.0.0

**Parameters**

| Name | Description |
| -- | -- |
| [OH_AudioAccessoryManager](capi-ohaudio-oh-audioaccessorymanager.md) *manager | Pointer to the audio accessory manager instance obtained through OH_AudioManager_GetAccessoryManager. |
| [OH_AudioAccessory](capi-ohaudio-oh-audioaccessory.md) *accessory | Pointer to the audio accessory instance obtained through OH_AudioAccessoryManager_CreateInput. |
| [OH_AudioNoiseReductionMode](capi-native-audio-common-h.md#oh_audionoisereductionmode) mode | Noise reduction mode to set. It must be one of the modes registered through RegisterNoiseReductionCapability. |

**Return**

| Type | Description |
| -- | -- |
| [OH_AudioCommon_Result](capi-native-audio-common-h.md#oh_audiocommon_result) | Result code.<br>AUDIOCOMMON_RESULT_SUCCESS: The function is executed successfully.<br>AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM: The accessory parameter is NULL.<br>AUDIOCOMMON_RESULT_ERROR_ILLEGAL_STATE: The accessory parameter is not created through OH_AudioAccessoryManager_CreateInput or not connected through OH_AudioAccessoryManager_Connected.<br>AUDIOCOMMON_RESULT_ERROR_UNSUPPORTED: The noise reduction mode to set is not registered through OH_AudioAccessoryManager_RegisterNoiseReductionCapability. |

### OH_AudioAccessoryManager_Connected()

```c
OH_AudioCommon_Result OH_AudioAccessoryManager_Connected(OH_AudioAccessoryManager *manager, OH_AudioAccessory *accessory)
```

**Description**

Connects an audio accessory to the audio system.

> **NOTE**
>
> - Before calling this function, obtain the audio accessory manager instance through OH_AudioManager_GetAccessoryManager and create the accessory instance through OH_AudioAccessoryManager_CreateInput.
> - It is recommended that the audio accessory management program be integrated into the Smart Life app first to provide users with a consistent device discovery and connection experience.
> - If it is used as a standalone audio accessory management app, the ACL permission ohos.permission.MANAGE_AUDIO_ACCESSORY must be requested.

**Required permissions:** ohos.permission.MANAGE_AUDIO_ACCESSORY

**Since:** 26.0.0

**Parameters**

| Name | Description |
| -- | -- |
| [OH_AudioAccessoryManager](capi-ohaudio-oh-audioaccessorymanager.md) *manager | Pointer to the audio accessory manager instance obtained through OH_AudioManager_GetAccessoryManager. |
| [OH_AudioAccessory](capi-ohaudio-oh-audioaccessory.md) *accessory | Pointer to the audio accessory instance obtained through OH_AudioAccessoryManager_CreateInput. |

**Return**

| Type | Description |
| -- | -- |
| [OH_AudioCommon_Result](capi-native-audio-common-h.md#oh_audiocommon_result) | Result code.<br>AUDIOCOMMON_RESULT_SUCCESS: The function is executed successfully.<br>AUDIOCOMMON_RESULT_ERROR_PERMISSION_DENIED: The caller does not have the ohos.permission.MANAGE_AUDIO_ACCESSORY permission.<br>AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM: Invalid parameter, including manager being NULL, manager not initialized through OH_AudioManager_GetAccessoryManager, or accessory being NULL.<br>AUDIOCOMMON_RESULT_ERROR_ILLEGAL_STATE: The accessory parameter is not created through OH_AudioAccessoryManager_CreateInput, or the accessory is already connected through OH_AudioAccessoryManager_Connected.<br>AUDIOCOMMON_RESULT_ERROR_SYSTEM: The audio service process is dead. |

### OH_AudioAccessoryManager_Disconnected()

```c
OH_AudioCommon_Result OH_AudioAccessoryManager_Disconnected(OH_AudioAccessoryManager *manager, OH_AudioAccessory *accessory)
```

**Description**

Disconnects an audio accessory.

**Required permissions:** ohos.permission.MANAGE_AUDIO_ACCESSORY

**Since:** 26.0.0

**Parameters**

| Name | Description |
| -- | -- |
| [OH_AudioAccessoryManager](capi-ohaudio-oh-audioaccessorymanager.md) *manager | Pointer to the audio accessory manager instance obtained through OH_AudioManager_GetAccessoryManager. |
| [OH_AudioAccessory](capi-ohaudio-oh-audioaccessory.md) *accessory | Pointer to the audio accessory instance obtained through OH_AudioAccessoryManager_CreateInput. |

**Return**

| Type | Description |
| -- | -- |
| [OH_AudioCommon_Result](capi-native-audio-common-h.md#oh_audiocommon_result) | Result code.<br>AUDIOCOMMON_RESULT_SUCCESS: The function is executed successfully.<br>AUDIOCOMMON_RESULT_ERROR_PERMISSION_DENIED: The caller does not have the ohos.permission.MANAGE_AUDIO_ACCESSORY permission.<br>AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM: The accessory parameter is NULL.<br>AUDIOCOMMON_RESULT_ERROR_ILLEGAL_STATE: The accessory parameter is not connected through OH_AudioAccessoryManager_Connected.<br>AUDIOCOMMON_RESULT_ERROR_SYSTEM: The audio service process is dead. |

### OH_AudioAccessoryManager_Destroy()

```c
OH_AudioCommon_Result OH_AudioAccessoryManager_Destroy(OH_AudioAccessoryManager *manager, OH_AudioAccessory *accessory)
```

**Description**

Destroys an audio accessory instance.

> **NOTE**
>
> Disconnect the accessory before destroying it.

**Since:** 26.0.0

**Parameters**

| Name | Description |
| -- | -- |
| [OH_AudioAccessoryManager](capi-ohaudio-oh-audioaccessorymanager.md) *manager | Pointer to the audio accessory manager instance obtained through OH_AudioManager_GetAccessoryManager. |
| [OH_AudioAccessory](capi-ohaudio-oh-audioaccessory.md) *accessory | Pointer to the audio accessory instance obtained through OH_AudioAccessoryManager_CreateInput. |

**Return**

| Type | Description |
| -- | -- |
| [OH_AudioCommon_Result](capi-native-audio-common-h.md#oh_audiocommon_result) | Result code.<br>AUDIOCOMMON_RESULT_SUCCESS: The function is executed successfully.<br>AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM: The parameter is invalid, including when manager is NULL, manager is not initialized through OH_AudioManager_GetAccessoryManager, or accessory is NULL.<br>AUDIOCOMMON_RESULT_ERROR_ILLEGAL_STATE: The accessory parameter is not disconnected through OH_AudioAccessoryManager_Disconnected. |