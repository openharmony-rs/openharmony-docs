# AudioSessionManager

This interface implements audio session management.

Before calling any API in AudioSessionManager, you must use [getSessionManager](arkts-audio-audio-audiomanager-i.md#getsessionmanager) to obtain an AudioSessionManager instance.

> **NOTE:** 
> 
> - The initial APIs of this interface are supported since API version 12.

@typedef AudioSessionManager [since 12 - 24]

**Since:** 12

**System capability:** SystemCapability.Multimedia.Audio.Core

## Modules to Import

```TypeScript
import { audio } from '@kit.AudioKit';
```

## activateAudioSession

```TypeScript
activateAudioSession(strategy: AudioSessionStrategy): Promise<void>
```

Activates an audio session. This API uses a promise to return the result.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.Multimedia.Audio.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| strategy | [AudioSessionStrategy](arkts-audio-audio-audiosessionstrategy-i.md) | Yes | Audio session strategy. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.Mandatory parameters unspecified. 2.Incorrect parameter types. |
| [6800101](../errorcode-audio.md#6800101-invalid-parameter) | Parameter verification failed. |
| [6800301](../errorcode-audio.md#6800301-system-error) | System error. Possible causes: 1.Focus preemption failure. 2.Audio server process died. |

## clearSelectedMediaInputDevice

```TypeScript
clearSelectedMediaInputDevice(): Promise<void>
```

Clears the media input device set by calling [selectMediaInputDevice](#selectmediainputdevice). This API uses a promise to return the result.

**Since:** 21

**System capability:** SystemCapability.Multimedia.Audio.Device

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [6800301](../errorcode-audio.md#6800301-system-error) | Audio client call audio service error, System error. |

## deactivateAudioSession

```TypeScript
deactivateAudioSession(): Promise<void>
```

Deactivates this audio session. This API uses a promise to return the result.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.Multimedia.Audio.Core

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [6800301](../errorcode-audio.md#6800301-system-error) | System error. Possible causes: 1.The audio session is not existed or has been released. 2.Audio server process died. |

## enableMuteSuggestionWhenMixWithOthers

```TypeScript
enableMuteSuggestionWhenMixWithOthers(enable: boolean): void
```

Enables mute suggestion notifications for mixed playback.

Typically, when the audio mixing mode is used, if two applications plays audio at the same time, their audio streams are mixed. In certain scenarios (such as games or broadcasts), applications can mute their own audio to provide a better user experience.

If this feature is enabled, mute and unmute suggestions will be sent through the [AudioSessionStateChangedEvent](arkts-audio-audio-audiosessionstatechangedevent-i.md) callback after the audio session state change event is subscribed to. Receiving the muted suggestion indicates that another application starts to play audio, and the played audio and the audio of this application cannot be mixed.

This feature can be used only by audio sessions for which [AudioSessionScene](arkts-audio-audio-audiosessionscene-e.md) has been set and the **CONCURRENCY_MIX_WITH_OTHERS** mode has been activated. This feature takes effect only once when the audio session is activated. You need to enable it again before each activation of the audio session.

For details, see [Enabling Mute Suggestion Notifications for Mixed Playback](../../../media/audio/audio-session-management.md#enabling-mute-suggestion-notifications-for-mixed-playback).

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Audio.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| enable | boolean | Yes | Whether to enable mute suggestion notifications for mixed playback. **true** to enable, **false** otherwise. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [6800103](../errorcode-audio.md#6800103-unsupported-state) | Function is called without setting [AudioSessionScene](arkts-audio-audio-audiosessionscene-e.md) or called after audio session activation. |
| [6800301](../errorcode-audio.md#6800301-system-error) | Audio client call audio service error, system internal error. |

## getAvailableDevices

```TypeScript
getAvailableDevices(deviceUsage: DeviceUsage): AudioDeviceDescriptors
```

Obtains the available audio devices.

**Since:** 21

**System capability:** SystemCapability.Multimedia.Audio.Device

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| deviceUsage | [DeviceUsage](arkts-audio-audio-deviceusage-e.md) | Yes | Audio device type (classified by usage). |

**Return value:**

| Type | Description |
| --- | --- |
| [AudioDeviceDescriptors](arkts-audio-audio-audiodevicedescriptors-t.md) | Device list. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [6800101](../errorcode-audio.md#6800101-invalid-parameter) | Parameter verification failed. |
| [6800301](../errorcode-audio.md#6800301-system-error) | Audio client call audio service error, System error. |

## getBluetoothAndNearlinkPreferredRecordCategory

```TypeScript
getBluetoothAndNearlinkPreferredRecordCategory(): BluetoothAndNearlinkPreferredRecordCategory
```

Obtains the preferred device category for recording with Bluetooth or NearLink, which is set by calling [setBluetoothAndNearlinkPreferredRecordCategory](#setbluetoothandnearlinkpreferredrecordcategory).

**Since:** 21

**System capability:** SystemCapability.Multimedia.Audio.Device

**Return value:**

| Type | Description |
| --- | --- |
| [BluetoothAndNearlinkPreferredRecordCategory](arkts-audio-audio-bluetoothandnearlinkpreferredrecordcategory-e.md) | Preferred device category for recording with Bluetooth or NearLink. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [6800301](../errorcode-audio.md#6800301-system-error) | Audio client call audio service error, System error. |

## getDefaultOutputDevice

```TypeScript
getDefaultOutputDevice(): DeviceType
```

Obtains the default audio output device set by calling [setDefaultOutputDevice](#setdefaultoutputdevice).

**Since:** 20

**System capability:** SystemCapability.Multimedia.Audio.Device

**Return value:**

| Type | Description |
| --- | --- |
| [DeviceType](arkts-audio-audio-devicetype-e.md) | Device type.<br>The options are **EARPIECE**, **SPEAKER**, and **DEFAULT**. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [6800101](../errorcode-audio.md#6800101-invalid-parameter) | Parameter verification failed. |
| [6800103](../errorcode-audio.md#6800103-unsupported-state) | Operation not permit at current state. Return by promise. |

## getSelectedMediaInputDevice

```TypeScript
getSelectedMediaInputDevice(): AudioDeviceDescriptor
```

Obtains the media input device set by calling [selectMediaInputDevice](#selectmediainputdevice). If no device has been specified, the device with **deviceType** set to **INVALID** is returned.

**Since:** 21

**System capability:** SystemCapability.Multimedia.Audio.Device

**Return value:**

| Type | Description |
| --- | --- |
| [AudioDeviceDescriptor](arkts-audio-audio-audiodevicedescriptor-i.md) | Media input device. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [6800301](../errorcode-audio.md#6800301-system-error) | Audio client call audio service error, System error. |

## isAudioSessionActivated

```TypeScript
isAudioSessionActivated(): boolean
```

Checks whether this audio session is activated.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.Multimedia.Audio.Core

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Check result for whether the audio session is activated. **true** if activated, **false** otherwise. |

## isOtherMediaPlaying

```TypeScript
isOtherMediaPlaying(): boolean
```

Check whether any other application is currently playing audio of the four media types: **MUSIC**, **MOVIE**, **AUDIOBOOK**, and **GAME**. Audio sessions that have activated these media types will also be checked.

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Audio.Core

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Whether another application is playing audio of certain media types. **true** means yes; **false** otherwise. |

## off('audioSessionDeactivated')

```TypeScript
off(type: 'audioSessionDeactivated', callback?: Callback<AudioSessionDeactivatedEvent>): void
```

Unsubscribes from the audio session deactivation event. This API uses an asynchronous callback to return the result.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.Multimedia.Audio.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'audioSessionDeactivated' | Yes | Event type. The event **'audioSessionDeactivated'** is triggered when the audio session is deactivated. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[AudioSessionDeactivatedEvent](arkts-audio-audio-audiosessiondeactivatedevent-i.md)&gt; | No | Callback used to return the reason why the audio session is deactivated. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| [6800101](../errorcode-audio.md#6800101-invalid-parameter) | Parameter verification failed. |

## off('audioSessionStateChanged')

```TypeScript
off(type: 'audioSessionStateChanged', callback?: Callback<AudioSessionStateChangedEvent>): void
```

Unsubscribes from the audio session state change event. This API uses an asynchronous callback to return the result.

**Since:** 20

**System capability:** SystemCapability.Multimedia.Audio.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'audioSessionStateChanged' | Yes | Event type. The event **'audioSessionStateChanged'** is triggered when the audio session state is changed. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[AudioSessionStateChangedEvent](arkts-audio-audio-audiosessionstatechangedevent-i.md)&gt; | No | Callback used to return the audio session change information. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [6800101](../errorcode-audio.md#6800101-invalid-parameter) | Parameter verification failed. |
| [6800301](../errorcode-audio.md#6800301-system-error) | Audio client call audio service error, System error. |

## off('currentOutputDeviceChanged')

```TypeScript
off(type: 'currentOutputDeviceChanged', callback?: Callback<CurrentOutputDeviceChangedEvent>): void
```

Unsubscribes from the current output device change event. This API uses an asynchronous callback to return the result.

**Since:** 20

**System capability:** SystemCapability.Multimedia.Audio.Device

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'currentOutputDeviceChanged' | Yes | Event type. The event **'currentOutputDeviceChanged'** is triggered when the current output device is changed. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[CurrentOutputDeviceChangedEvent](arkts-audio-audio-currentoutputdevicechangedevent-i.md)&gt; | No | Callback used to return the information about the current output device. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [6800101](../errorcode-audio.md#6800101-invalid-parameter) | Parameter verification failed. |
| [6800301](../errorcode-audio.md#6800301-system-error) | Audio client call audio service error, System error. |

## off('availableDeviceChange')

```TypeScript
off(type: 'availableDeviceChange', callback?: Callback<DeviceChangeAction>): void
```

Unsubscribes from the event indicating that the connection status of an available audio device is changed.

**Since:** 21

**System capability:** SystemCapability.Multimedia.Audio.Device

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'availableDeviceChange' | Yes | Event type. The event **'availableDeviceChange'** is triggered when the connection status of available audio devices is changed. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[DeviceChangeAction](arkts-audio-audio-devicechangeaction-i.md)&gt; | No | Callback used to return the available device change details. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [6800301](../errorcode-audio.md#6800301-system-error) | Audio client call audio service error, System error. |

## off('currentInputDeviceChanged')

```TypeScript
off(type: 'currentInputDeviceChanged', callback?: Callback<CurrentInputDeviceChangedEvent>): void
```

Unsubscribes from the current input device change event.

**Since:** 21

**System capability:** SystemCapability.Multimedia.Audio.Device

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'currentInputDeviceChanged' | Yes | Event type. The event **'currentInputDeviceChanged'** is triggered when the current input device is changed. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[CurrentInputDeviceChangedEvent](arkts-audio-audio-currentinputdevicechangedevent-i.md)&gt; | No | Callback used to return the information about the current input device. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [6800301](../errorcode-audio.md#6800301-system-error) | Audio client call audio service error, System error. |

## on('audioSessionDeactivated')

```TypeScript
on(type: 'audioSessionDeactivated', callback: Callback<AudioSessionDeactivatedEvent>): void
```

Subscribes to the audio session deactivation event, which is triggered when an audio session is deactivated. This API uses an asynchronous callback to return the result.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.Multimedia.Audio.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'audioSessionDeactivated' | Yes | Event type. The event **'audioSessionDeactivated'** is triggered when the audio session is deactivated. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[AudioSessionDeactivatedEvent](arkts-audio-audio-audiosessiondeactivatedevent-i.md)&gt; | Yes | Callback used to return the reason why the audio session is deactivated. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.Mandatory parameters unspecified. 2.Incorrect parameter types. |
| [6800101](../errorcode-audio.md#6800101-invalid-parameter) | Parameter verification failed. |

## on('audioSessionStateChanged')

```TypeScript
on(type: 'audioSessionStateChanged', callback: Callback<AudioSessionStateChangedEvent>): void
```

Subscribes to the audio session state change event, which is triggered when the audio session focus is changed. This API uses an asynchronous callback to return the result.

**Since:** 20

**System capability:** SystemCapability.Multimedia.Audio.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'audioSessionStateChanged' | Yes | Event type. The event **'audioSessionStateChanged'** is triggered when the audio session state is changed. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[AudioSessionStateChangedEvent](arkts-audio-audio-audiosessionstatechangedevent-i.md)&gt; | Yes | Callback used to return the audio session change information. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [6800101](../errorcode-audio.md#6800101-invalid-parameter) | Parameter verification failed. |
| [6800102](../errorcode-audio.md#6800102-memory-allocation-failure) | Allocate memory failed. |
| [6800301](../errorcode-audio.md#6800301-system-error) | Audio client call audio service error, System error. |

## on('currentOutputDeviceChanged')

```TypeScript
on(type: 'currentOutputDeviceChanged', callback: Callback<CurrentOutputDeviceChangedEvent>): void
```

Subscribes to the current output device change event, which is triggered when the current output device is changed. This API uses an asynchronous callback to return the result.

**Since:** 20

**System capability:** SystemCapability.Multimedia.Audio.Device

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'currentOutputDeviceChanged' | Yes | Event type. The event **'currentOutputDeviceChanged'** is triggered when the current output device is changed. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[CurrentOutputDeviceChangedEvent](arkts-audio-audio-currentoutputdevicechangedevent-i.md)&gt; | Yes | Callback used to return the information about the current output device. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [6800101](../errorcode-audio.md#6800101-invalid-parameter) | Parameter verification failed. |
| [6800102](../errorcode-audio.md#6800102-memory-allocation-failure) | Allocate memory failed. |
| [6800301](../errorcode-audio.md#6800301-system-error) | Audio client call audio service error, System error. |

## on('availableDeviceChange')

```TypeScript
on(type: 'availableDeviceChange', deviceUsage: DeviceUsage, callback: Callback<DeviceChangeAction>): void
```

Subscribes to the event indicating that the connection status of an available audio device is changed.

**Since:** 21

**System capability:** SystemCapability.Multimedia.Audio.Device

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'availableDeviceChange' | Yes | Event type. The event **'availableDeviceChange'** is triggered when the connection status of available audio devices is changed. |
| deviceUsage | [DeviceUsage](arkts-audio-audio-deviceusage-e.md) | Yes | Audio device type (classified by usage). |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[DeviceChangeAction](arkts-audio-audio-devicechangeaction-i.md)&gt; | Yes | Callback used to return the available device change details. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [6800101](../errorcode-audio.md#6800101-invalid-parameter) | Parameter verification failed. |
| [6800301](../errorcode-audio.md#6800301-system-error) | Audio client call audio service error, System error. |

## on('currentInputDeviceChanged')

```TypeScript
on(type: 'currentInputDeviceChanged', callback: Callback<CurrentInputDeviceChangedEvent>): void
```

Subscribes to the current input device change event, which is triggered when the current input device is changed.

**Since:** 21

**System capability:** SystemCapability.Multimedia.Audio.Device

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'currentInputDeviceChanged' | Yes | Event type. The event **'currentInputDeviceChanged'** is triggered when the current input device is changed. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[CurrentInputDeviceChangedEvent](arkts-audio-audio-currentinputdevicechangedevent-i.md)&gt; | Yes | Callback used to return the information about the current input device. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [6800101](../errorcode-audio.md#6800101-invalid-parameter) | Parameter verification failed. |
| [6800301](../errorcode-audio.md#6800301-system-error) | Audio client call audio service error, System error. |

## selectMediaInputDevice

```TypeScript
selectMediaInputDevice(inputAudioDevice: AudioDeviceDescriptor): Promise<void>
```

Selects a media input device. This API uses a promise to return the result.

> **NOTE:** 
> 
> - This API is not suitable for VoIP call recording; that is, it does not apply to scenarios where [SourceType](arkts-audio-audio-sourcetype-e.md) is **SOURCE_TYPE_VOICE_COMMUNICATION**.
> 
> - Before calling this API, call [getAvailableDevices](#getavailabledevices) to query the list of available input devices and select an input device from the list.
> 
> - If there are recording streams of other applications with higher priorities in the system, the actual input device used will follow the input device selected by these applications.
> 
> - Applications can listen for the [currentInputDeviceChanged](#oncurrentinputdevicechanged)event to find out the actual input device being used.

**Since:** 21

**System capability:** SystemCapability.Multimedia.Audio.Device

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| inputAudioDevice | [AudioDeviceDescriptor](arkts-audio-audio-audiodevicedescriptor-i.md) | Yes | Media input device. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [6800101](../errorcode-audio.md#6800101-invalid-parameter) | Parameter verification failed, for example, the selected device does not exist. |
| [6800301](../errorcode-audio.md#6800301-system-error) | Audio client call audio service error, System error. |

## setAudioSessionBehavior

```TypeScript
setAudioSessionBehavior(behavior: number): void
```

Sets audio session behavior parameters. (Multiple flags can be combined.)

> **NOTE:** 
> 
> If this API is called while an audio session is active, you must call the
> [activateAudioSession](#activateaudiosession) API again
> for the settings to take effect.

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Audio.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| behavior | number | Yes | Specifies the audio session behavior.<br>This can be a single flag or a bitwise OR combination of multiple flags.<br>For details about the supported audio session behaviors, see [AudioSessionBehaviorFlags](arkts-audio-audio-audiosessionbehaviorflags-e.md). |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [6800101](../errorcode-audio.md#6800101-invalid-parameter) | Parameter verification failed. |
| [6800103](../errorcode-audio.md#6800103-unsupported-state) | Operation not permitted in the current state. |

## setAudioSessionScene

```TypeScript
setAudioSessionScene(scene: AudioSessionScene): void
```

Sets an audio session scene.

**Since:** 20

**System capability:** SystemCapability.Multimedia.Audio.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| scene | [AudioSessionScene](arkts-audio-audio-audiosessionscene-e.md) | Yes | Audio session scene. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [6800101](../errorcode-audio.md#6800101-invalid-parameter) | Parameter verification failed. |
| [6800103](../errorcode-audio.md#6800103-unsupported-state) | Operation not permit at current state. |
| [6800301](../errorcode-audio.md#6800301-system-error) | Audio client call audio service error, System error. |

## setBluetoothAndNearlinkPreferredRecordCategory

```TypeScript
setBluetoothAndNearlinkPreferredRecordCategory(category: BluetoothAndNearlinkPreferredRecordCategory): Promise<void>
```

Sets the preferred device category for recording with Bluetooth or NearLink. This API uses a promise to return the result.

> **NOTE:** 
> 
> - Applications can set this category before connecting to Bluetooth or NearLink devices, and the system prioritizes using the device for recording when the device is connected.
> 
> - If there are recording streams of other applications with higher priorities in the system, the actual input device used will follow the input device selected by these applications.
> 
> - Applications can listen for the [currentInputDeviceChanged](#oncurrentinputdevicechanged)event to find out the actual input device being used.

**Since:** 21

**System capability:** SystemCapability.Multimedia.Audio.Device

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| category | [BluetoothAndNearlinkPreferredRecordCategory](arkts-audio-audio-bluetoothandnearlinkpreferredrecordcategory-e.md) | Yes | Preferred device category for recording with Bluetooth or NearLink. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [6800101](../errorcode-audio.md#6800101-invalid-parameter) | Parameter verification failed. |
| [6800301](../errorcode-audio.md#6800301-system-error) | Audio client call audio service error, System error. |

## setCapturerMuteHint

```TypeScript
setCapturerMuteHint(mute: boolean): Promise<void>
```

Set mute hint for all capturer streams in the current audio session. It dose not mute the recording stream, only affects internal processing strategy.

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Audio.Capturer

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| mute | boolean | Yes | Use true if application recording stream muted by application if self. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise used to return the result. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [6800103](../errorcode-audio.md#6800103-unsupported-state) | Operation not permit at current state, there is no audio capturer running. |

## setDefaultOutputDevice

```TypeScript
setDefaultOutputDevice(deviceType: DeviceType): Promise<void>
```

Sets the default audio output device. This API uses a promise to return the result.

> **NOTE:** 
> 
> - This API applies to the following scenario: When [AudioSessionScene](arkts-audio-audio-audiosessionscene-e.md) is set to **VoIP**, the setting takes effect immediately after the AudioSession is activated. For non-VoIP scenarios, the setting does not take effect upon AudioSession activation. Instead, the setting applies when [StreamUsage](arkts-audio-audio-streamusage-e.md) for playback is voice message, VoIP voice call,or VoIP video call. Supported devices include the earpiece, speaker, and system default device.
> 
> - This API can be called at any time after an AudioSessionManager instance is created. The system records the device set by the application. However, the setting takes effect only after the AudioSession is activated. When the application starts playing, if an external device like Bluetooth headsets or wired headsets is connected,the system prioritizes audio output through the external device. Otherwise, the system uses the device set by the application.

**Since:** 20

**System capability:** SystemCapability.Multimedia.Audio.Device

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| deviceType | [DeviceType](arkts-audio-audio-devicetype-e.md) | Yes | Device type.<br>The options are **EARPIECE**, **SPEAKER**, and **DEFAULT**. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [6800101](../errorcode-audio.md#6800101-invalid-parameter) | Parameter verification failed. Return by promise. |
| [6800102](../errorcode-audio.md#6800102-memory-allocation-failure) | Allocate memory failed. Return by promise. |
| [6800301](../errorcode-audio.md#6800301-system-error) | Audio client call audio service error, System error. |

## setMediaOutputDevice

```TypeScript
setMediaOutputDevice(deviceType: DeviceType): Promise<void>
```

Set the audio output device to the built-in speaker, when other audio peripherals are connected, such as bluetooth headphones or wired headsets. It should be noted that this interface only applies to media streams. In scenarios where there are concurrent playback streams with higher priority or user selects the output device through system UI, the actual output device used by the application may differ from the selected one. The application can obtain currently active output device by subscribing to the currentOutputDeviceChanged event.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Audio.Device

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| deviceType | [DeviceType](arkts-audio-audio-devicetype-e.md) | Yes | the available deviceTypes are SPEAKER: Built-in speaker DEFAULT: Restore to system default output device |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise used to return the result. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [6800101](../errorcode-audio.md#6800101-invalid-parameter) | Parameter verification failed, for example, the selected device type is not supported. |
| [6800301](../errorcode-audio.md#6800301-system-error) | System error. Possible causes: 1.Internal variable memory allocation failed. 2.Audio server process died. 3.Speaker device is not available. |
