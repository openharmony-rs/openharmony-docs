# native_audio_accessory_manager.h

## Overview

Declare audio accessory manager related interfaces.

**Library**: libohaudio.so

**System capability**: SystemCapability.Multimedia.Audio.Core

**Since**: 10

**Related module**: [OHAudio](capi-ohaudio.md)

## Summary

### Function

| Name | typedef keyword | Description |
| -- | -- | -- |
| [typedef bool (\*OH_AudioAccessory_SetNoiseReductionCallback)(OH_AudioAccessory *accessory, OH_AudioNoiseReductionMode mode)](#oh_audioaccessory_setnoisereductioncallback) | OH_AudioAccessory_SetNoiseReductionCallback | Callback for noise reduction mode change on an accessory.<br> <b>When Called:</b> When the system requests a change to the noise reduction mode on the accessory. This callback may be called at any time after the accessory is connected. |
| [OH_AudioCommon_Result OH_AudioManager_GetAccessoryManager(OH_AudioAccessoryManager **outManager)](#oh_audiomanager_getaccessorymanager) | - | Obtains the audio accessory manager instance. |
| [OH_AudioCommon_Result OH_AudioAccessoryManager_CreateInput(OH_AudioAccessoryManager *manager, const OH_AudioAccessoryInfo *info, const OH_AudioAccessoryCapabilities *capabilities, OH_AudioAccessory_OpenInputStreamCallback openInputStream, OH_AudioAccessory **outOwnedAccessory)](#oh_audioaccessorymanager_createinput) | - | Creates an input audio accessory instance and registers its capabilities.<br> This function creates only the audio accessory instance. It does not create any input stream immediately.<br> The framework performs a deep copy of the accessoryName, manufacturer, modelNumber, and macAddress fields. The caller may free these buffers after this function returns. The framework also performs a deep copy of the streamProperties array in capabilities. The caller may free this array after this function returns.<br> On success, the framework allocates an [OH_AudioAccessory](capi-ohaudio-oh-audioaccessory.md) handle and returns it through accessory pointer.<br> Input streams are created lazily by the framework when an application actually starts recording from this accessory. At that time, the framework creates a new [OH_AudioAccessoryInputStream](capi-ohaudio-oh-audioaccessoryinputstream.md) handle and invokes open stream. The callback receives the newly created stream handle and the requested stream information, and is where the caller must register the required stream callbacks.<br> The stream handle is managed by the framework and must not be released by the caller. A stream remains valid until the framework invokes [OH_AudioAccessoryInputStream_ReleaseCallback](capi-native-audio-accessory-input-stream-manager-h.md#oh_audioaccessoryinputstream_releasecallback) for that stream. After the release callback returns, the stream handle becomes invalid and must not be used again. During the lifetime of one accessory handle, input streams may be created and released multiple times. |
| [OH_AudioCommon_Result OH_AudioAccessoryManager_SetAssociatedMacAddresses(OH_AudioAccessoryManager *manager, OH_AudioAccessory *accessory, const char **macAddresses, uint32_t count)](#oh_audioaccessorymanager_setassociatedmacaddresses) | - | Sets the list of associated MAC addresses for the audio accessory.<br> This interface replaces the existing list of associated MAC addresses linked to the accessory instance. It is designed for multi-transmitter scenarios (e.g., 1-to-2, 1-to-4 systems) where the group of connected transmitters may change dynamically.Call this after the accessory is created to report all currently active transmitters associated with the primary MAC. If a transmitter is replaced or disconnected, call this again with the updated list to overwrite the previous state. Safe to call during an active recording session. |
| [OH_AudioCommon_Result OH_AudioAccessoryManager_RegisterNoiseReductionCapability(OH_AudioAccessoryManager *manager, OH_AudioAccessory *accessory, const OH_AudioAccessoryNoiseReductionCapability *capability, OH_AudioAccessory_SetNoiseReductionCallback onNoiseReduction)](#oh_audioaccessorymanager_registernoisereductioncapability) | - | Registers the noise reduction capability of an audio accessory.<br> The framework performs a deep copy of the supportedModes array and other fields in the capability structure. The caller may free the capability structure and the supportedModes array after this function returns. |
| [OH_AudioCommon_Result OH_AudioAccessoryManager_SetNoiseReductionMode(OH_AudioAccessoryManager *manager, OH_AudioAccessory *accessory, OH_AudioNoiseReductionMode mode)](#oh_audioaccessorymanager_setnoisereductionmode) | - | Sets the noise reduction mode of an audio accessory.<br> This function allows the accessory service to actively synchronize the current noise reduction mode to the framework. It is typically used when the mode is changed through other means (e.g., hardware buttons or a companion app), ensuring the framework stays updated with the accessory's actual state. |
| [OH_AudioCommon_Result OH_AudioAccessoryManager_Connected(OH_AudioAccessoryManager *manager, OH_AudioAccessory *accessory)](#oh_audioaccessorymanager_connected) | - | Connects the audio accessory to the audio framework.<br> All required capabilities must be registered before calling this function.<br> <b>Recommendation:</b> It is recommended that third-party audio accessories prioritize integration with the Smart Life app. This ensures a consistent user experience for device discovery and connection, allowing the accessory service to avoid direct permission management. |
| [OH_AudioCommon_Result OH_AudioAccessoryManager_Disconnected(OH_AudioAccessoryManager *manager, OH_AudioAccessory *accessory)](#oh_audioaccessorymanager_disconnected) | - | Disconnects the audio accessory from the audio framework. |
| [OH_AudioCommon_Result OH_AudioAccessoryManager_Destroy(OH_AudioAccessoryManager *manager, OH_AudioAccessory *accessory)](#oh_audioaccessorymanager_destroy) | - | Destroys the audio accessory instance.<br> The accessory must be disconnected before destroying. |

### Variable

| Name | Description |
| -- | -- |
| bool (*OH_AudioAccessory_SetNoiseReductionCallback)( OH_AudioAccessory *accessory, OH_AudioNoiseReductionMode mode) | Callback for noise reduction mode change on an accessory.<br> <b>When Called:</b> When the system requests a change to the noise reduction mode on the accessory. This callback may be called at any time after the accessory is connected.<br>**Since**: 26.0.0 |

## Function description

### OH_AudioAccessory_SetNoiseReductionCallback()

```c
typedef bool (*OH_AudioAccessory_SetNoiseReductionCallback)(OH_AudioAccessory *accessory, OH_AudioNoiseReductionMode mode)
```

**Description**

Callback for noise reduction mode change on an accessory.<br> <b>When Called:</b> When the system requests a change to the noise reduction mode on the accessory. This callback may be called at any time after the accessory is connected.

**System capability**: SystemCapability.Multimedia.Audio.Core

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AudioAccessory \*accessory | [in] The audio accessory. |
| OH_AudioNoiseReductionMode mode | [in] The noise reduction mode to set on the accessory. |

**Returns**:

| Type | Description |
| -- | -- |
| bool | <ul>          <li>`true` if the requested mode is handled successfully.</li>          <li>`false` otherwise.</li>          </ul> |

### OH_AudioManager_GetAccessoryManager()

```c
OH_AudioCommon_Result OH_AudioManager_GetAccessoryManager(OH_AudioAccessoryManager **outManager)
```

**Description**

Obtains the audio accessory manager instance.

**System capability**: SystemCapability.Multimedia.Audio.Core

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AudioAccessoryManager **outManager | [out] Returns a pointer to the manager handle. Note that the handle is managed by the system and must not be released by the caller, otherwise an exception may occur. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AudioCommon_Result | <ul>          <li>[AUDIOCOMMON_RESULT_SUCCESS](capi-native-audio-common-h.md#oh_audiocommon_result) if execution succeeds.</li>          <li>[AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM](capi-native-audio-common-h.md#oh_audiocommon_result) if manager is null.</li>          </ul> |

### OH_AudioAccessoryManager_CreateInput()

```c
OH_AudioCommon_Result OH_AudioAccessoryManager_CreateInput(OH_AudioAccessoryManager *manager, const OH_AudioAccessoryInfo *info, const OH_AudioAccessoryCapabilities *capabilities, OH_AudioAccessory_OpenInputStreamCallback openInputStream, OH_AudioAccessory **outOwnedAccessory)
```

**Description**

Creates an input audio accessory instance and registers its capabilities.<br> This function creates only the audio accessory instance. It does not create any input stream immediately.<br> The framework performs a deep copy of the accessoryName, manufacturer, modelNumber, and macAddress fields. The caller may free these buffers after this function returns. The framework also performs a deep copy of the streamProperties array in capabilities. The caller may free this array after this function returns.<br> On success, the framework allocates an [OH_AudioAccessory](capi-ohaudio-oh-audioaccessory.md) handle and returns it through accessory pointer.<br> Input streams are created lazily by the framework when an application actually starts recording from this accessory. At that time, the framework creates a new [OH_AudioAccessoryInputStream](capi-ohaudio-oh-audioaccessoryinputstream.md) handle and invokes open stream. The callback receives the newly created stream handle and the requested stream information, and is where the caller must register the required stream callbacks.<br> The stream handle is managed by the framework and must not be released by the caller. A stream remains valid until the framework invokes [OH_AudioAccessoryInputStream_ReleaseCallback](capi-native-audio-accessory-input-stream-manager-h.md#oh_audioaccessoryinputstream_releasecallback) for that stream. After the release callback returns, the stream handle becomes invalid and must not be used again. During the lifetime of one accessory handle, input streams may be created and released multiple times.

**System capability**: SystemCapability.Multimedia.Audio.Core

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AudioAccessoryManager *manager | [in] Pointer to the audio accessory manager. |
| const OH_AudioAccessoryInfo *info | [in] Pointer to the accessory basic information. Must not be null. |
| const OH_AudioAccessoryCapabilities *capabilities | [in] Pointer to the accessory capabilities. Must not be null. |
| OH_AudioAccessory_OpenInputStreamCallback openInputStream | [in] Callback invoked when the framework opens an input stream. Must not be null. The callback is invoked only when the framework creates a stream for this accessory, not when this function is called. |
| OH_AudioAccessory **outOwnedAccessory | [out] Returns the created accessory handle. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AudioCommon_Result | <ul>          <li>[AUDIOCOMMON_RESULT_SUCCESS](capi-native-audio-common-h.md#oh_audiocommon_result) if execution succeeds.</li>          <li>[AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM](capi-native-audio-common-h.md#oh_audiocommon_result) if any parameter is null.</li>          <li>[AUDIOCOMMON_RESULT_ERROR_ILLEGAL_STATE](capi-native-audio-common-h.md#oh_audiocommon_result) if the manager is not initialized.</li>          </ul> |

### OH_AudioAccessoryManager_SetAssociatedMacAddresses()

```c
OH_AudioCommon_Result OH_AudioAccessoryManager_SetAssociatedMacAddresses(OH_AudioAccessoryManager *manager, OH_AudioAccessory *accessory, const char **macAddresses, uint32_t count)
```

**Description**

Sets the list of associated MAC addresses for the audio accessory.<br> This interface replaces the existing list of associated MAC addresses linked to the accessory instance. It is designed for multi-transmitter scenarios (e.g., 1-to-2, 1-to-4 systems) where the group of connected transmitters may change dynamically.Call this after the accessory is created to report all currently active transmitters associated with the primary MAC. If a transmitter is replaced or disconnected, call this again with the updated list to overwrite the previous state. Safe to call during an active recording session.

**System capability**: SystemCapability.Multimedia.Audio.Core

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AudioAccessoryManager *manager | [in] Pointer to the audio accessory manager. |
| OH_AudioAccessory *accessory | [in] Pointer to the accessory handle. |
| const char **macAddresses | [in] Array of MAC addresses to associate. <b>Can be null if count is 0</b>, indicating that all associated MAC addresses should be cleared (e.g., when all secondary transmitters disconnect). If not null, the framework performs a deep copy of these strings. Each element must conform to the following rules: - Must be a NUL-terminated ASCII string in colon-separated hexadecimal notation, e.g. "00:11:22:33:44:55". Both upper-case and lower-case hex digits (A-F / a-f) are accepted. - Must be a non-null, non-empty string. - Duplicate addresses within the same array are ignored; only the first occurrence of each unique address takes effect. |
| uint32_t count | [in] Number of MAC addresses in the array. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AudioCommon_Result | <ul>          <li>[AUDIOCOMMON_RESULT_SUCCESS](capi-native-audio-common-h.md#oh_audiocommon_result) if execution succeeds.</li>          <li>[AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM](capi-native-audio-common-h.md#oh_audiocommon_result) if parameters are invalid.</li>          <li>[AUDIOCOMMON_RESULT_ERROR_ILLEGAL_STATE](capi-native-audio-common-h.md#oh_audiocommon_result) if the accessory is not created.</li>          </ul> |

### OH_AudioAccessoryManager_RegisterNoiseReductionCapability()

```c
OH_AudioCommon_Result OH_AudioAccessoryManager_RegisterNoiseReductionCapability(OH_AudioAccessoryManager *manager, OH_AudioAccessory *accessory, const OH_AudioAccessoryNoiseReductionCapability *capability, OH_AudioAccessory_SetNoiseReductionCallback onNoiseReduction)
```

**Description**

Registers the noise reduction capability of an audio accessory.<br> The framework performs a deep copy of the supportedModes array and other fields in the capability structure. The caller may free the capability structure and the supportedModes array after this function returns.

**System capability**: SystemCapability.Multimedia.Audio.Core

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AudioAccessoryManager *manager | [in] Pointer to the audio accessory manager. |
| OH_AudioAccessory *accessory | [in] Pointer to the accessory handle created by CreateInput. |
| const OH_AudioAccessoryNoiseReductionCapability *capability | [in] Pointer to the noise reduction capability. Must not be null. |
| [OH_AudioAccessory_SetNoiseReductionCallback](capi-native-audio-accessory-manager-h.md#oh_audioaccessory_setnoisereductioncallback) onNoiseReduction | [in] Callback invoked when the framework requests a noise reduction mode change. May be null if the accessory does not support dynamic mode switching. If provided, the callback must return `true` on success and `false` on failure. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AudioCommon_Result | <ul>          <li>[AUDIOCOMMON_RESULT_SUCCESS](capi-native-audio-common-h.md#oh_audiocommon_result) if execution succeeds.</li>          <li>[AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM](capi-native-audio-common-h.md#oh_audiocommon_result) if parameters are invalid.</li>          <li>[AUDIOCOMMON_RESULT_ERROR_ILLEGAL_STATE](capi-native-audio-common-h.md#oh_audiocommon_result) if the accessory is not created.</li>          </ul> |

### OH_AudioAccessoryManager_SetNoiseReductionMode()

```c
OH_AudioCommon_Result OH_AudioAccessoryManager_SetNoiseReductionMode(OH_AudioAccessoryManager *manager, OH_AudioAccessory *accessory, OH_AudioNoiseReductionMode mode)
```

**Description**

Sets the noise reduction mode of an audio accessory.<br> This function allows the accessory service to actively synchronize the current noise reduction mode to the framework. It is typically used when the mode is changed through other means (e.g., hardware buttons or a companion app), ensuring the framework stays updated with the accessory's actual state.

**System capability**: SystemCapability.Multimedia.Audio.Core

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AudioAccessoryManager *manager | [in] Pointer to the audio accessory manager. |
| OH_AudioAccessory *accessory | [in] Pointer to the accessory handle. |
| OH_AudioNoiseReductionMode mode | [in] The noise reduction mode to set. Must be one of the modes registered via RegisterNoiseReductionCapability. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AudioCommon_Result | <ul>          <li>[AUDIOCOMMON_RESULT_SUCCESS](capi-native-audio-common-h.md#oh_audiocommon_result) if execution succeeds.</li>          <li>[AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM](capi-native-audio-common-h.md#oh_audiocommon_result) if parameters are invalid.</li>          <li>[AUDIOCOMMON_RESULT_ERROR_ILLEGAL_STATE](capi-native-audio-common-h.md#oh_audiocommon_result) if the accessory is not connected.</li>          <li>[AUDIOCOMMON_RESULT_ERROR_UNSUPPORTED](capi-native-audio-common-h.md#oh_audiocommon_result) if the mode is not supported.</li>          </ul> |

### OH_AudioAccessoryManager_Connected()

```c
OH_AudioCommon_Result OH_AudioAccessoryManager_Connected(OH_AudioAccessoryManager *manager, OH_AudioAccessory *accessory)
```

**Description**

Connects the audio accessory to the audio framework.<br> All required capabilities must be registered before calling this function.<br> <b>Recommendation:</b> It is recommended that third-party audio accessories prioritize integration with the Smart Life app. This ensures a consistent user experience for device discovery and connection, allowing the accessory service to avoid direct permission management.

**System capability**: SystemCapability.Multimedia.Audio.Core

**Required permission**: ohos.permission.MANAGE_AUDIO_ACCESSORY

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AudioAccessoryManager *manager | [in] Pointer to the audio accessory manager. |
| OH_AudioAccessory *accessory | [in] Pointer to the accessory handle to connect. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AudioCommon_Result | <ul>          <li>[AUDIOCOMMON_RESULT_SUCCESS](capi-native-audio-common-h.md#oh_audiocommon_result) if execution succeeds.</li>          <li>[AUDIOCOMMON_RESULT_ERROR_PERMISSION_DENIED](capi-native-audio-common-h.md#oh_audiocommon_result) if the caller does not have the                   required permission.</li>          <li>[AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM](capi-native-audio-common-h.md#oh_audiocommon_result) if accessory is null.</li>          <li>[AUDIOCOMMON_RESULT_ERROR_ILLEGAL_STATE](capi-native-audio-common-h.md#oh_audiocommon_result) if capabilities are not registered or                   the accessory is already connected.</li>          <li>[AUDIOCOMMON_RESULT_ERROR_SYSTEM](capi-native-audio-common-h.md#oh_audiocommon_result) if audio server process die.</li>          </ul> |

### OH_AudioAccessoryManager_Disconnected()

```c
OH_AudioCommon_Result OH_AudioAccessoryManager_Disconnected(OH_AudioAccessoryManager *manager, OH_AudioAccessory *accessory)
```

**Description**

Disconnects the audio accessory from the audio framework.

**System capability**: SystemCapability.Multimedia.Audio.Core

**Required permission**: ohos.permission.MANAGE_AUDIO_ACCESSORY

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AudioAccessoryManager *manager | [in] Pointer to the audio accessory manager. |
| OH_AudioAccessory *accessory | [in] Pointer to the accessory handle to disconnect. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AudioCommon_Result | <ul>          <li>[AUDIOCOMMON_RESULT_SUCCESS](capi-native-audio-common-h.md#oh_audiocommon_result) if execution succeeds.</li>          <li>[AUDIOCOMMON_RESULT_ERROR_PERMISSION_DENIED](capi-native-audio-common-h.md#oh_audiocommon_result) if the caller does not have the                   required permission.</li>          <li>[AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM](capi-native-audio-common-h.md#oh_audiocommon_result) if accessory is null.</li>          <li>[AUDIOCOMMON_RESULT_ERROR_ILLEGAL_STATE](capi-native-audio-common-h.md#oh_audiocommon_result) if the accessory is not connected.</li>          <li>[AUDIOCOMMON_RESULT_ERROR_SYSTEM](capi-native-audio-common-h.md#oh_audiocommon_result) if audio server process die.</li>          </ul> |

### OH_AudioAccessoryManager_Destroy()

```c
OH_AudioCommon_Result OH_AudioAccessoryManager_Destroy(OH_AudioAccessoryManager *manager, OH_AudioAccessory *accessory)
```

**Description**

Destroys the audio accessory instance.<br> The accessory must be disconnected before destroying.

**System capability**: SystemCapability.Multimedia.Audio.Core

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AudioAccessoryManager *manager | [in] Pointer to the audio accessory manager. |
| OH_AudioAccessory *accessory | [in] Pointer to the accessory handle to destroy. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AudioCommon_Result | <ul>          <li>[AUDIOCOMMON_RESULT_SUCCESS](capi-native-audio-common-h.md#oh_audiocommon_result) if execution succeeds.</li>          <li>[AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM](capi-native-audio-common-h.md#oh_audiocommon_result) if accessory is null.</li>          <li>[AUDIOCOMMON_RESULT_ERROR_ILLEGAL_STATE](capi-native-audio-common-h.md#oh_audiocommon_result) if the accessory is still connected.</li>          </ul> |


