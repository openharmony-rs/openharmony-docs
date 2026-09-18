# @ohos.multimedia.avsession

**Since:** 9

**System capability:** SystemCapability.Multimedia.AVSession.Core

## Modules to Import

```TypeScript
import { avSession } from '@kit.AVSessionKit';
```

## Summary

### Functions

| Name | Description |
| --- | --- |
| [createAVSession](arkts-avsession-avsession-createavsession-f.md) | Create an AVSession instance. An ability can only create one AVSession |
| [createAVSession](arkts-avsession-avsession-createavsession-f.md) | Create an AVSession instance. An ability can only create one AVSession |
| [createController](arkts-avsession-avsession-createcontroller-f.md) | Create an avsession controller |
| [getAllSessionDescriptors](arkts-avsession-avsession-getallsessiondescriptors-f.md) | Get all avsession descriptors which can be shown on system entrance. |
| [getAVSession](arkts-avsession-avsession-getavsession-f.md) | Get an AVSession instance if already created. |
| [isDesktopLyricSupported](arkts-avsession-avsession-isdesktoplyricsupported-f.md) | Whether desktop lyric feature is supported. |
| [offSessionCreate](arkts-avsession-avsession-offsessioncreate-f.md) | Unregister session create callback |
| [offSessionCreateForAudioZone](arkts-avsession-avsession-offsessioncreateforaudiozone-f.md) | Unregister session create callback for a specific audio zone. |
| [offSessionDestroy](arkts-avsession-avsession-offsessiondestroy-f.md) | Unregister session destroy callback |
| [offSessionDestroyForAudioZone](arkts-avsession-avsession-offsessiondestroyforaudiozone-f.md) | Unregister session destroy callback for a specific audio zone. |
| [offTopSessionChange](arkts-avsession-avsession-offtopsessionchange-f.md) | Unregister top session changed callback |
| [offTopSessionChangeForAudioZone](arkts-avsession-avsession-offtopsessionchangeforaudiozone-f.md) | Unregister top session changed callback for a specific audio zone. |
| [onSessionCreate](arkts-avsession-avsession-onsessioncreate-f.md) | Register session create callback |
| [onSessionCreateForAudioZone](arkts-avsession-avsession-onsessioncreateforaudiozone-f.md) | Register session create callback for a specific audio zone. |
| [onSessionDestroy](arkts-avsession-avsession-onsessiondestroy-f.md) | Register session destroy callback |
| [onSessionDestroyForAudioZone](arkts-avsession-avsession-onsessiondestroyforaudiozone-f.md) | Register session destroy callback for a specific audio zone. |
| [onTopSessionChange](arkts-avsession-avsession-ontopsessionchange-f.md) | Register top session changed callback |
| [onTopSessionChangeForAudioZone](arkts-avsession-avsession-ontopsessionchangeforaudiozone-f.md) | Register top session changed callback for a specific audio zone. |

<!--Del-->
### Functions(System API)

| Name | Description |
| --- | --- |
| [castAudio](arkts-avsession-avsession-castaudio-f-sys.md) | Cast Audio to the remote devices or cast back local device |
| [castAudio](arkts-avsession-avsession-castaudio-f-sys.md) | Cast Audio to the remote devices or cast back local device |
| [createController](arkts-avsession-avsession-createcontroller-f-sys.md) | Create an avsession controller |
| [getAllSessionDescriptors](arkts-avsession-avsession-getallsessiondescriptors-f-sys.md) | Get all avsession descriptors of the system |
| [getAVCastController](arkts-avsession-avsession-getavcastcontroller-f-sys.md) | Register a callback to retrieve an avsession cast controller. This function can be used at both side to get the same controller to do the playback control. |
| [getAVCastController](arkts-avsession-avsession-getavcastcontroller-f-sys.md) | Get the current session's remote controller client. If the avsession is not under casting state, the controller will return null. |
| [getDistributedSessionController](arkts-avsession-avsession-getdistributedsessioncontroller-f-sys.md) | Get distributed avsession controller |
| [getHistoricalAVQueueInfos](arkts-avsession-avsession-gethistoricalavqueueinfos-f-sys.md) | Get history play list information records. |
| [getHistoricalAVQueueInfos](arkts-avsession-avsession-gethistoricalavqueueinfos-f-sys.md) | Get history play list information records. |
| [getHistoricalSessionDescriptors](arkts-avsession-avsession-gethistoricalsessiondescriptors-f-sys.md) | Get history avsession records. These sessions have been destroyed. |
| [getHistoricalSessionDescriptors](arkts-avsession-avsession-gethistoricalsessiondescriptors-f-sys.md) | Get history avsession records. These sessions have been destroyed. |
| [getSessionDescriptors](arkts-avsession-avsession-getsessiondescriptors-f-sys.md) | Get session descriptors of the system based on different session category. |
| [getSessionDescriptorsForAudioZone](arkts-avsession-avsession-getsessiondescriptorsforaudiozone-f-sys.md) | Get session descriptors for a unique audio zone across different session category. |
| [off](arkts-avsession-avsession-off-f-sys.md#offsessioncreate) | Unregister session create callback |
| [off](arkts-avsession-avsession-off-f-sys.md#offsessiondestroy) | Unregister session destroy callback |
| [off](arkts-avsession-avsession-off-f-sys.md#offtopsessionchange) | Unregister top session changed callback |
| [off](arkts-avsession-avsession-off-f-sys.md#offsessionservicedie) | Unregister Session service death callback, notifying the application to clean up resources. |
| [off](arkts-avsession-avsession-off-f-sys.md#offdistributedsessionchange) | Unregister distributed session changed callback |
| [off](arkts-avsession-avsession-off-f-sys.md#offdeviceavailable) | Unregister device discovery callback |
| [off](arkts-avsession-avsession-off-f-sys.md#offdeviceoffline) | Unregister device offline callback |
| [off](arkts-avsession-avsession-off-f-sys.md#offdevicelogevent) | UnRegister log event callback. |
| [off](arkts-avsession-avsession-off-f-sys.md#offdevicestatechanged) | Unregisters a system callback for the device connection phase. |
| [offActiveSessionChanged](arkts-avsession-avsession-offactivesessionchanged-f-sys.md) | Unregister active session changed callback. |
| [offSystemCommonEvent](arkts-avsession-avsession-offsystemcommonevent-f-sys.md) | Unregister system common event callback |
| [on](arkts-avsession-avsession-on-f-sys.md#onsessioncreate) | Register session create callback |
| [on](arkts-avsession-avsession-on-f-sys.md#onsessiondestroy) | Register session destroy callback |
| [on](arkts-avsession-avsession-on-f-sys.md#ontopsessionchange) | Register top session changed callback |
| [on](arkts-avsession-avsession-on-f-sys.md#onsessionservicedie) | Register Session service death callback, notifying the application to clean up resources. |
| [on](arkts-avsession-avsession-on-f-sys.md#ondistributedsessionchange) | Register distributed session changed callback |
| [on](arkts-avsession-avsession-on-f-sys.md#ondeviceavailable) | Register device discovery callback |
| [on](arkts-avsession-avsession-on-f-sys.md#ondeviceoffline) | Register device offline callback |
| [on](arkts-avsession-avsession-on-f-sys.md#ondevicelogevent) | Register log event callback. |
| [on](arkts-avsession-avsession-on-f-sys.md#ondevicestatechanged) | Registers a system callback for the device connection phase. The callback includes information such as error codes, connection status, radar errors, and user behavior codes. |
| [onActiveSessionChanged](arkts-avsession-avsession-onactivesessionchanged-f-sys.md) | Register active session changed callback. |
| [onSystemCommonEvent](arkts-avsession-avsession-onsystemcommonevent-f-sys.md) | Register system common event callback |
| [sendSystemAVKeyEvent](arkts-avsession-avsession-sendsystemavkeyevent-f-sys.md) | Send system media key event.The system automatically selects the recipient. |
| [sendSystemAVKeyEvent](arkts-avsession-avsession-sendsystemavkeyevent-f-sys.md) | Send system media key event.The system automatically selects the recipient. |
| [sendSystemCommonCommand](arkts-avsession-avsession-sendsystemcommoncommand-f-sys.md) | Send system control command. The system automatically selects the recipient. |
| [sendSystemControlCommand](arkts-avsession-avsession-sendsystemcontrolcommand-f-sys.md) | Send system control command.The system automatically selects the recipient. |
| [sendSystemControlCommand](arkts-avsession-avsession-sendsystemcontrolcommand-f-sys.md) | Send system control command.The system automatically selects the recipient. |
| [setDiscoverable](arkts-avsession-avsession-setdiscoverable-f-sys.md) | Enable or disable device to be discoverable, used at sink side. |
| [setDiscoverable](arkts-avsession-avsession-setdiscoverable-f-sys.md) | Enable or disable device to be discoverable, used at sink side. |
| [startAVPlayback](arkts-avsession-avsession-startavplayback-f-sys.md) | Start an application for media playback. |
| [startAVPlayback](arkts-avsession-avsession-startavplayback-f-sys.md) | Start an application for media playback with command info. |
| [startAVPlaybackForAudioZone](arkts-avsession-avsession-startavplaybackforaudiozone-f-sys.md) | Start an application for media playback with command info for an specific audio zone. |
| [startCastDeviceDiscovery](arkts-avsession-avsession-startcastdevicediscovery-f-sys.md) | Start device discovery. |
| [startCastDeviceDiscovery](arkts-avsession-avsession-startcastdevicediscovery-f-sys.md) | Start device discovery. |
| [startCastDeviceDiscovery](arkts-avsession-avsession-startcastdevicediscovery-f-sys.md) | Start device discovery. |
| [startCasting](arkts-avsession-avsession-startcasting-f-sys.md) | Cast resource to remote device. |
| [startCasting](arkts-avsession-avsession-startcasting-f-sys.md) | Cast resource to remote device. |
| [startDeviceLogging](arkts-avsession-avsession-startdevicelogging-f-sys.md) | Begin to write device logs into a file descriptor for the purpose of problem locating. If the logs exceed max file size, no logs will be written and DEVICE_LOG_FULL event will be omitted. |
| [stopCastDeviceDiscovery](arkts-avsession-avsession-stopcastdevicediscovery-f-sys.md) | Stop device discovery. |
| [stopCastDeviceDiscovery](arkts-avsession-avsession-stopcastdevicediscovery-f-sys.md) | Stop device discovery. |
| [stopCasting](arkts-avsession-avsession-stopcasting-f-sys.md) | Stop current cast and disconnect device connection. |
| [stopCasting](arkts-avsession-avsession-stopcasting-f-sys.md) | Stop current cast and disconnect device connection. |
| [stopDeviceLogging](arkts-avsession-avsession-stopdevicelogging-f-sys.md) | Stop the current device written even the discovery is ongoing. |
<!--DelEnd-->

### Classes

| Name | Description |
| --- | --- |
| [AVCastPickerHelper](arkts-avsession-avsession-avcastpickerhelper-c.md) | A helper to enable a picker to select output devices |

### Interfaces

| Name | Description |
| --- | --- |
| [AudioCapabilities](arkts-avsession-avsession-audiocapabilities-i.md) | Audio capabilities. |
| [AVCallState](arkts-avsession-avsession-avcallstate-i.md) | Used to indicate the call state of the current call. |
| [AVCastControlCommand](arkts-avsession-avsession-avcastcontrolcommand-i.md) | The definition of cast command to be sent to the session |
| [AVCastController](arkts-avsession-avsession-avcastcontroller-i.md) | AVCastController definition used to implement a remote control when a cast is connected |
| [AVCastPickerOptions](arkts-avsession-avsession-avcastpickeroptions-i.md) | An option to make different picker usage |
| [AVControlCommand](arkts-avsession-avsession-avcontrolcommand-i.md) | The definition of command to be sent to the session |
| [AVMediaDescription](arkts-avsession-avsession-avmediadescription-i.md) | The description of the media for an item in the playlist of the session |
| [AVMetadata](arkts-avsession-avsession-avmetadata-i.md) | The metadata of the current media.Used to set the properties of the current media file |
| [AVPlaybackState](arkts-avsession-avsession-avplaybackstate-i.md) | Used to indicate the playback state of the current media. If the playback state of the media changes, it needs to be updated synchronously |
| [AVQueueItem](arkts-avsession-avsession-avqueueitem-i.md) | The item in the playlist of the session |
| [AVSession](arkts-avsession-avsession-avsession-i.md) | AVSession object. |
| [AVSessionController](arkts-avsession-avsession-avsessioncontroller-i.md) | Session controller,used to control media playback and get media information |
| [AVSessionDescriptor](arkts-avsession-avsession-avsessiondescriptor-i.md) | The description of the session |
| [CallMetadata](arkts-avsession-avsession-callmetadata-i.md) | The metadata of the current call. |
| [CastDisplayInfo](arkts-avsession-avsession-castdisplayinfo-i.md) | Define the information for extended display screen. |
| [CommandInfo](arkts-avsession-avsession-commandinfo-i.md) | The definition of command information to be sent to the session |
| [DesktopLyricState](arkts-avsession-avsession-desktoplyricstate-i.md) | Desktop lyric state definition. |
| [DeviceInfo](arkts-avsession-avsession-deviceinfo-i.md) | Device Information Definition |
| [MenuPosition](arkts-avsession-avsession-menuposition-i.md) | Position definition of one component on which the menu will bind and popup. |
| [OutputDeviceInfo](arkts-avsession-avsession-outputdeviceinfo-i.md) | Target Device Information Definition |
| [PlaybackPosition](arkts-avsession-avsession-playbackposition-i.md) | Playback position definition |

<!--Del-->
### Interfaces(System API)

| Name | Description |
| --- | --- |
| [AVCastController](arkts-avsession-avsession-avcastcontroller-i-sys.md) | AVCastController definition used to implement a remote control when a cast is connected |
| [AVQueueInfo](arkts-avsession-avsession-avqueueinfo-i-sys.md) | The play list information definition. |
| [AVSessionController](arkts-avsession-avsession-avsessioncontroller-i-sys.md) | Session controller,used to control media playback and get media information |
| [AVSessionDescriptor](arkts-avsession-avsession-avsessiondescriptor-i-sys.md) | The description of the session |
| [DeviceInfo](arkts-avsession-avsession-deviceinfo-i-sys.md) | Device Information Definition |
| [DeviceState](arkts-avsession-avsession-devicestate-i-sys.md) | Device state used to describe states including discovery, authentication and other scenes. |
| [HiPlayDeviceInfo](arkts-avsession-avsession-hiplaydeviceinfo-i-sys.md) | HiPlay Device Information Definition |
| [SessionToken](arkts-avsession-avsession-sessiontoken-i-sys.md) | Session token. Used to judge the legitimacy of the session. |
<!--DelEnd-->

### Enums

| Name | Description |
| --- | --- |
| [AVCastCategory](arkts-avsession-avsession-avcastcategory-e.md) | cast category indicating different playback scenes |
| [AVSessionErrorCode](arkts-avsession-avsession-avsessionerrorcode-e.md) | Enumerates ErrorCode types, returns in BusinessError.code. |
| [BackgroundPlayMode](arkts-avsession-avsession-backgroundplaymode-e.md) | Supported background play mode definitions. |
| [CallerType](arkts-avsession-avsession-callertype-e.md) | Enumerates CallerType including caller source type. |
| [CallState](arkts-avsession-avsession-callstate-e.md) | Enumeration of current call state |
| [CastDisplayState](arkts-avsession-avsession-castdisplaystate-e.md) | Enumerates the cast display states. |
| [ConnectionState](arkts-avsession-avsession-connectionstate-e.md) | Define the device connection state. |
| [DecoderType](arkts-avsession-avsession-decodertype-e.md) | The defination of decoder type. |
| [DeviceType](arkts-avsession-avsession-devicetype-e.md) | Device type definition |
| [DisplayTag](arkts-avsession-avsession-displaytag-e.md) | The pre-defined display tag by system. |
| [ExtraKey](arkts-avsession-avsession-extrakey-e.md) | Define some common extra keys used in different scenarios. |
| [LoopMode](arkts-avsession-avsession-loopmode-e.md) | Loop Play Mode Definition |
| [PlaybackState](arkts-avsession-avsession-playbackstate-e.md) | Definition of current playback state |
| [ProtocolType](arkts-avsession-avsession-protocoltype-e.md) | Define different protocol capability |
| [ResolutionLevel](arkts-avsession-avsession-resolutionlevel-e.md) | The defination of suggested resolution. |
| [SkipIntervals](arkts-avsession-avsession-skipintervals-e.md) | Supported skip intervals definition |

<!--Del-->
### Enums(System API)

| Name | Description |
| --- | --- |
| [ConnectionState](arkts-avsession-avsession-connectionstate-e-sys.md) | Define the device connection state. |
| [DeviceLogEventCode](arkts-avsession-avsession-devicelogeventcode-e-sys.md) | Enumerates device log event code. |
| [DistributedSessionType](arkts-avsession-avsession-distributedsessiontype-e-sys.md) | Define different distributed session type |
| [ExtraKey](arkts-avsession-avsession-extrakey-e-sys.md) | Define some common extra keys used in different scenarios. |
| [ProtocolType](arkts-avsession-avsession-protocoltype-e-sys.md) | Define different protocol capability |
| [SessionCategory](arkts-avsession-avsession-sessioncategory-e-sys.md) | Session category for different scenes. |
<!--DelEnd-->

### Types

| Name | Description |
| --- | --- |
| [AVCastControlCommandType](arkts-avsession-avsession-avcastcontrolcommandtype-t.md) | The type of control command |
| [AVControlCommandType](arkts-avsession-avsession-avcontrolcommandtype-t.md) | The type of control command. |
| [AVMediaCenterControlType](arkts-avsession-avsession-avmediacentercontroltype-t.md) | The type of media center control command, which can be used to determine the button displayed on the media center. |
| [AVSessionType](arkts-avsession-avsession-avsessiontype-t.md) | Session type supports audio & video, voice_call, video_call, photo |
| [EventProcess](arkts-avsession-avsession-eventprocess-t.md) | The general process funcation with an event and arguments. |
| [ExtraInfo](arkts-avsession-avsession-extrainfo-t.md) | The extra info object. |
| [KeyRequestCallback](arkts-avsession-avsession-keyrequestcallback-t.md) | The callback of key request. |
| [NoParamCallback](arkts-avsession-avsession-noparamcallback-t.md) | Defines the basic callback. |
| [TwoParamCallback](arkts-avsession-avsession-twoparamcallback-t.md) | Defines the callback type including two parameters. |
