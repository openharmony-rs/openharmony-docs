# @ohos.multimedia.avsession

**起始版本：** 23

<!--Device-unnamed-declare namespace avSession--><!--Device-unnamed-declare namespace avSession-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.Core

## 导入模块

```TypeScript
import { avSession } from '@kit.AVSessionKit';
```

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [createAVSession](arkts-avsession-avsession-createavsession-f.md) | 创建会话对象，一个应用程序仅允许存在一个会话，重复创建会失败，结果通过callback异步回调方式返回。 |
| [createAVSession](arkts-avsession-avsession-createavsession-f.md) | 创建会话对象，一个应用进程仅允许存在一个会话，重复创建会失败，结果通过Promise异步回调方式返回。 |
| [getAVSession](arkts-avsession-avsession-getavsession-f.md) | 获取会话对象。使用Promise异步回调。 该接口可将当前进程已创建过的会话对象返回，如果没有创建过会话对象，该接口调用会失败并抛出异常。 |
| [isDesktopLyricSupported](arkts-avsession-avsession-isdesktoplyricsupported-f.md) | 设备是否支持桌面歌词功能。使用Promise异步回调。 |
| [offSessionCreate](arkts-avsession-avsession-offsessioncreate-f.md) | Unregister session create callback |
| [offSessionDestroy](arkts-avsession-avsession-offsessiondestroy-f.md) | Unregister session destroy callback |
| [offTopSessionChange](arkts-avsession-avsession-offtopsessionchange-f.md) | Unregister top session changed callback |
| [onSessionCreate](arkts-avsession-avsession-onsessioncreate-f.md) | Register session create callback |
| [onSessionDestroy](arkts-avsession-avsession-onsessiondestroy-f.md) | Register session destroy callback |
| [onTopSessionChange](arkts-avsession-avsession-ontopsessionchange-f.md) | Register top session changed callback |

<!--Del-->
### 函数（系统接口）

| 名称 | 说明 |
| --- | --- |
| [castAudio](arkts-avsession-avsession-castaudio-f-sys.md) | 投播会话到指定设备列表。结果通过callback异步回调方式返回。 需要导入`ohos.multimedia.audio`模块获取AudioDeviceDescriptor的相关描述。 |
| [castAudio](arkts-avsession-avsession-castaudio-f-sys.md) | 投播会话到指定设备列表。结果通过Promise异步回调方式返回。 调用此接口之前，需要导入`ohos.multimedia.audio`模块获取AudioDeviceDescriptor的相关描述。 |
| [castAudioSession](arkts-avsession-avsession-castaudiosession-f-sys.md) | Cast Audio to the remote devices or cast back local device |
| [castAudioSession](arkts-avsession-avsession-castaudiosession-f-sys.md) | Cast Audio to the remote devices or cast back local device |
| [castAudioSessionAll](arkts-avsession-avsession-castaudiosessionall-f-sys.md) | Cast all the media audio to the remote devices or cast back local device |
| [createController](arkts-avsession-avsession-createcontroller-f-sys.md) | 根据会话ID创建会话控制器。使用callback异步回调。 |
| [createController](arkts-avsession-avsession-createcontroller-f-sys.md) | 根据会话ID创建会话控制器。使用Promise异步回调。 |
| [getAVCastController](arkts-avsession-avsession-getavcastcontroller-f-sys.md) | 设备建立连接后，获取投播控制器。结果通过callback异步回调方式返回。 此功能在本端和远端都可以使用，通过该接口可以获取一个相同的控制器，进行投播音频的播放控制。 |
| [getAVCastController](arkts-avsession-avsession-getavcastcontroller-f-sys.md) | Register a callback to retrieve an avsession cast controller. This function can be used at both side to get the same controller to do the playback control. |
| [getAVCastController](arkts-avsession-avsession-getavcastcontroller-f-sys.md) | 设备建立连接后，获取投播控制器。结果通过Promise方式返回。 此功能在本端和远端都可以使用，通过该接口可以获取一个相同的控制器，进行投播音频的播放控制。 |
| [getAVCastController](arkts-avsession-avsession-getavcastcontroller-f-sys.md) | Get the current session's remote controller client. If the avsession is not under casting state, the controller will return undefined. |
| [getAllSessionDescriptors](arkts-avsession-avsession-getallsessiondescriptors-f-sys.md) | 获取所有设置过媒体信息且注册过控制回调的会话的描述符信息。使用callback异步回调。 |
| [getAllSessionDescriptors](arkts-avsession-avsession-getallsessiondescriptors-f-sys.md) | 获取所有设置过媒体信息且注册过控制回调的会话的描述符信息。结果通过Promise异步回调方式返回。 |
| [getDistributedSessionController](arkts-avsession-avsession-getdistributedsessioncontroller-f-sys.md) | 根据远端会话类型，获取远端分布式会话控制器。结果通过Promise异步回调方式返回。 |
| [getHistoricalAVQueueInfos](arkts-avsession-avsession-gethistoricalavqueueinfos-f-sys.md) | 获取全部的历史播放歌单。结果通过callback异步回调方式返回。 |
| [getHistoricalAVQueueInfos](arkts-avsession-avsession-gethistoricalavqueueinfos-f-sys.md) | 获取全部的历史播放歌单。结果通过Promise异步回调方式返回。 |
| [getHistoricalSessionDescriptors](arkts-avsession-avsession-gethistoricalsessiondescriptors-f-sys.md) | 获取所有已被销毁的会话相关描述。结果通过callback异步回调方式返回。 |
| [getHistoricalSessionDescriptors](arkts-avsession-avsession-gethistoricalsessiondescriptors-f-sys.md) | 获取所有已被销毁的会话相关描述。结果通过Promise异步回调方式返回。 |
| [getSessionDescriptors](arkts-avsession-avsession-getsessiondescriptors-f-sys.md) | 根据不同的会话类别获取对应的会话描述。使用Promise异步回调。 |
| [getSessionDescriptorsForAudioZone](arkts-avsession-avsession-getsessiondescriptorsforaudiozone-f-sys.md) | 获取根据userid查询对应音区的会话 |
| [offActiveSessionChanged](arkts-avsession-avsession-offactivesessionchanged-f-sys.md) | 取消允许在系统控制入口显示的会话变更事件监听，取消后将不再对该事件进行监听。使用callback异步回调。 |
| [offAudioZoneSessionChange](arkts-avsession-avsession-offaudiozonesessionchange-f-sys.md) | 取消注册音区对应的会话变化监听 |
| [offDeviceAvailable](arkts-avsession-avsession-offdeviceavailable-f-sys.md) | Unregister device discovery callback |
| [offDeviceLogEvent](arkts-avsession-avsession-offdevicelogevent-f-sys.md) | UnRegister log event callback. |
| [offDeviceOffline](arkts-avsession-avsession-offdeviceoffline-f-sys.md) | Unregister device offline callback |
| [offDeviceStateChanged](arkts-avsession-avsession-offdevicestatechanged-f-sys.md) | Unregisters a system callback for the device connection phase. |
| [offDistributedSessionChange](arkts-avsession-avsession-offdistributedsessionchange-f-sys.md) | Unregister distributed session changed callback |
| [offSessionServiceDie](arkts-avsession-avsession-offsessionservicedie-f-sys.md) | Unregister Session service death callback, notifying the application to clean up resources. |
| [offSystemCommonEvent](arkts-avsession-avsession-offsystemcommonevent-f-sys.md) | 取消注册通用事件回调监听 |
| [off_deviceAvailable](arkts-avsession-avsession-offdeviceavailable-f-sys.md) | 取消设备发现回调的监听。 |
| [off_deviceLogEvent](arkts-avsession-avsession-offdevicelogevent-f-sys.md) | 取消监听日志事件的回调。 |
| [off_deviceOffline](arkts-avsession-avsession-offdeviceoffline-f-sys.md) | 取消设备下线回调的监听。 |
| [off_deviceStateChanged](arkts-avsession-avsession-offdevicestatechanged-f-sys.md) | 取消投播设备连接状态的监听。 |
| [off_distributedSessionChange](arkts-avsession-avsession-offdistributedsessionchange-f-sys.md) | 取消最新分布式远端会话变更的监听事件，取消后，不再进行该事件的监听。 |
| [off_sessionCreate](arkts-avsession-avsession-offsessioncreate-f-sys.md#offsessioncreate) | 注销会话创建事件监听。注销后，不再接收该事件。 |
| [off_sessionDestroy](arkts-avsession-avsession-offsessiondestroy-f-sys.md#offsessiondestroy) | 注销会话销毁事件监听。注销后，不再监听该事件。 |
| [off_sessionServiceDie](arkts-avsession-avsession-offsessionservicedie-f-sys.md) | 取消会话服务死亡监听，取消后，不再进行服务死亡监听。 |
| [off_topSessionChange](arkts-avsession-avsession-offtopsessionchange-f-sys.md#offtopsessionchange) | 注销最新播放会话变更事件监听。注销后，不再进行该事件的监听。 |
| [onActiveSessionChanged](arkts-avsession-avsession-onactivesessionchanged-f-sys.md) | 允许在系统控制入口显示的会话变更的监听事件。使用callback异步回调。 |
| [onAudioZoneSessionChange](arkts-avsession-avsession-onaudiozonesessionchange-f-sys.md) | 注册音区会话变化回调 |
| [onDeviceAvailable](arkts-avsession-avsession-ondeviceavailable-f-sys.md) | Register device discovery callback |
| [onDeviceLogEvent](arkts-avsession-avsession-ondevicelogevent-f-sys.md) | Register log event callback. |
| [onDeviceOffline](arkts-avsession-avsession-ondeviceoffline-f-sys.md) | Register device offline callback |
| [onDeviceStateChanged](arkts-avsession-avsession-ondevicestatechanged-f-sys.md) | Registers a system callback for the device connection phase. The callback includes information such as error codes, connection status, radar errors, and user behavior codes. |
| [onDistributedSessionChange](arkts-avsession-avsession-ondistributedsessionchange-f-sys.md) | Register distributed session changed callback |
| [onSessionServiceDie](arkts-avsession-avsession-onsessionservicedie-f-sys.md) | Register Session service death callback, notifying the application to clean up resources. |
| [onSystemCommonEvent](arkts-avsession-avsession-onsystemcommonevent-f-sys.md) | 监听系统通用事件命令回调 |
| [on_deviceAvailable](arkts-avsession-avsession-ondeviceavailable-f-sys.md) | 设备发现回调监听。 |
| [on_deviceLogEvent](arkts-avsession-avsession-ondevicelogevent-f-sys.md) | 监听日志事件的回调。 |
| [on_deviceOffline](arkts-avsession-avsession-ondeviceoffline-f-sys.md) | 设备下线回调监听。 |
| [on_deviceStateChanged](arkts-avsession-avsession-ondevicestatechanged-f-sys.md) | 投播设备连接状态的回调函数。 |
| [on_distributedSessionChange](arkts-avsession-avsession-ondistributedsessionchange-f-sys.md) | 最新分布式远端会话变更的监听事件。 |
| [on_sessionCreate](arkts-avsession-avsession-onsessioncreate-f-sys.md#onsessioncreate) | 会话的创建事件监听。 使用callback异步回调。 |
| [on_sessionDestroy](arkts-avsession-avsession-onsessiondestroy-f-sys.md#onsessiondestroy) | 会话的销毁事件监听。使用callback异步回调。 |
| [on_sessionServiceDie](arkts-avsession-avsession-onsessionservicedie-f-sys.md) | 监听会话的服务死亡事件。通知应用清理资源。 |
| [on_topSessionChange](arkts-avsession-avsession-ontopsessionchange-f-sys.md#ontopsessionchange) | 最新播放会话变更的事件监听。使用callback异步回调。 |
| [sendSystemAVKeyEvent](arkts-avsession-avsession-sendsystemavkeyevent-f-sys.md) | 发送按键事件给置顶会话。结果通过callback异步回调方式返回。 |
| [sendSystemAVKeyEvent](arkts-avsession-avsession-sendsystemavkeyevent-f-sys.md) | 发送按键事件给置顶会话。结果通过Promise异步回调方式返回。 |
| [sendSystemCommonCommand](arkts-avsession-avsession-sendsystemcommoncommand-f-sys.md) | 发送通用事件命令 |
| [sendSystemControlCommand](arkts-avsession-avsession-sendsystemcontrolcommand-f-sys.md) | 发送控制命令给置顶会话。结果通过callback异步回调方式返回。 |
| [sendSystemControlCommand](arkts-avsession-avsession-sendsystemcontrolcommand-f-sys.md) | 发送控制命令给置顶会话。结果通过Promise异步回调方式返回。 |
| [setDiscoverable](arkts-avsession-avsession-setdiscoverable-f-sys.md) | 设置设备是否可被发现，用于投播接收端。结果通过callback异步回调方式返回。 |
| [setDiscoverable](arkts-avsession-avsession-setdiscoverable-f-sys.md) | 设置设备是否可被发现，用于投播接收端。结果通过Promise异步回调方式返回。 |
| [startAVPlayback](arkts-avsession-avsession-startavplayback-f-sys.md) | 启动媒体播放应用程序。结果通过Promise异步回调方式返回。 |
| [startAVPlayback](arkts-avsession-avsession-startavplayback-f-sys.md) | 携带启动参数的冷启动应用播放接口 |
| [startCastDeviceDiscovery](arkts-avsession-avsession-startcastdevicediscovery-f-sys.md) | 开始设备搜索发现。结果通过callback异步回调方式返回。 |
| [startCastDeviceDiscovery](arkts-avsession-avsession-startcastdevicediscovery-f-sys.md) | 指定过滤条件，开始设备搜索发现。结果通过callback异步回调方式返回。 |
| [startCastDeviceDiscovery](arkts-avsession-avsession-startcastdevicediscovery-f-sys.md) | 开始设备搜索发现。结果通过Promise异步回调方式返回。 |
| [startCasting](arkts-avsession-avsession-startcasting-f-sys.md) | 启动投播。结果通过callback异步回调方式返回。 |
| [startCasting](arkts-avsession-avsession-startcasting-f-sys.md) | 启动投播。结果通过Promise异步回调方式返回。 |
| [startDeviceLogging](arkts-avsession-avsession-startdevicelogging-f-sys.md) | 开始将设备日志写入文件。结果通过Promise异步回调方式返回。 |
| [stopCastDeviceDiscovery](arkts-avsession-avsession-stopcastdevicediscovery-f-sys.md) | 结束设备搜索发现。结果通过callback异步回调方式返回。 |
| [stopCastDeviceDiscovery](arkts-avsession-avsession-stopcastdevicediscovery-f-sys.md) | 结束设备搜索发现。结果通过Promise异步回调方式返回。 |
| [stopCasting](arkts-avsession-avsession-stopcasting-f-sys.md) | 结束投播。结果通过callback异步回调方式返回。 |
| [stopCasting](arkts-avsession-avsession-stopcasting-f-sys.md) | 结束投播。结果通过Promise异步回调方式返回。 |
| [stopDeviceLogging](arkts-avsession-avsession-stopdevicelogging-f-sys.md) | 停止当前设备日志写入。结果通过Promise异步回调方式返回。 |
<!--DelEnd-->

### 类

| 名称 | 说明 |
| --- | --- |
| [AVCastPickerHelper](arkts-avsession-avsession-avcastpickerhelper-c.md) | 投播半模态对象，可拉起半模态窗口，选择投播设备。在使用前，需要创建AVCastPickerHelper实例。 |

### 接口

| 名称 | 说明 |
| --- | --- |
| [AVCallState](arkts-avsession-avsession-avcallstate-i.md) | 通话状态相关属性。 |
| [AVCastControlCommand](arkts-avsession-avsession-avcastcontrolcommand-i.md) | 投播控制器接受的命令的对象描述。 |
| [AVCastController](arkts-avsession-avsession-avcastcontroller-i.md) | 在投播建立后，调用[avSession.getAVCastController](arkts-avsession-avsession-getavcastcontroller-f-sys.md)后，返回会话控制器实例。控制器可查看会话ID，并可完成对会话发送命令及事件， 获取会话元数据，播放状态信息等操作。 |
| [AVCastPickerOptions](arkts-avsession-avsession-avcastpickeroptions-i.md) | 拉起的投播组件包含的配置属性。 |
| [AVControlCommand](arkts-avsession-avsession-avcontrolcommand-i.md) | 会话接受的命令的对象描述。 |
| [AVMediaDescription](arkts-avsession-avsession-avmediadescription-i.md) | 播放列表媒体元数据的相关属性。 |
| [AVMetadata](arkts-avsession-avsession-avmetadata-i.md) | 媒体元数据的相关属性。 |
| [AVPlaybackState](arkts-avsession-avsession-avplaybackstate-i.md) | 媒体播放状态的相关属性。 |
| [AVQueueItem](arkts-avsession-avsession-avqueueitem-i.md) | 播放列表中单项的相关属性。 |
| [AVSession](arkts-avsession-avsession-avsession-i.md) | 调用[avSession.createAVSession](arkts-avsession-avsession-createavsession-f.md)后，返回会话的实例，可以获得会话ID，完成设置元数据，播放状态信息等操作。 |
| [AVSessionController](arkts-avsession-avsession-avsessioncontroller-i.md) | AVSessionController控制器可查看会话ID，并可完成对会话发送命令及事件，获取会话元数据，播放状态信息等操作。 |
| [AudioCapabilities](arkts-avsession-avsession-audiocapabilities-i.md) | 表示投播设备支持的音频能力。 |
| [CallMetadata](arkts-avsession-avsession-callmetadata-i.md) | 通话会话元数据相关属性。 |
| [CastDisplayInfo](arkts-avsession-avsession-castdisplayinfo-i.md) | 扩展屏投播显示设备相关属性。 |
| [CommandInfo](arkts-avsession-avsession-commandinfo-i.md) | 定义要发送到会话的命令信息。 |
| [DesktopLyricState](arkts-avsession-avsession-desktoplyricstate-i.md) | 桌面歌词状态。 |
| [DeviceInfo](arkts-avsession-avsession-deviceinfo-i.md) | 播放设备的相关信息。 |
| [MenuPosition](arkts-avsession-avsession-menuposition-i.md) | 定义可弹出菜单的组件的位置。 |
| [OutputDeviceInfo](arkts-avsession-avsession-outputdeviceinfo-i.md) | 播放设备的相关信息。 |
| [PlaybackPosition](arkts-avsession-avsession-playbackposition-i.md) | 媒体播放位置的相关属性。 |

<!--Del-->
### 接口（系统接口）

| 名称 | 说明 |
| --- | --- |
| [AVCastController](arkts-avsession-avsession-avcastcontroller-i-sys.md) | 在投播建立后，调用[avSession.getAVCastController](arkts-avsession-avsession-getavcastcontroller-f-sys.md)后，返回会话控制器实例。控制器可查看会话ID，并可完成对会话发送命令及事件， 获取会话元数据，播放状态信息等操作。 |
| [AVQueueInfo](arkts-avsession-avsession-avqueueinfo-i-sys.md) | 歌单（歌曲列表）的相关属性。 |
| [AVSessionDescriptor](arkts-avsession-avsession-avsessiondescriptor-i-sys.md) | 会话的相关描述信息。 |
| [DeviceInfo](arkts-avsession-avsession-deviceinfo-i-sys.md) | 播放设备的相关信息。 |
| [DeviceState](arkts-avsession-avsession-devicestate-i-sys.md) | 投播设备的连接状态。 |
| [HiPlayDeviceInfo](arkts-avsession-avsession-hiplaydeviceinfo-i-sys.md) | HiPlay 设备类型定义 |
| [SessionToken](arkts-avsession-avsession-sessiontoken-i-sys.md) | 会话令牌的信息。 |
<!--DelEnd-->

### 枚举

| 名称 | 说明 |
| --- | --- |
| [AVCastCategory](arkts-avsession-avsession-avcastcategory-e.md) | 投播的类别枚举。 |
| [AVSessionErrorCode](arkts-avsession-avsession-avsessionerrorcode-e.md) | 会话发生错误时的错误码。 |
| [BackgroundPlayMode](arkts-avsession-avsession-backgroundplaymode-e.md) | 表示session支持的后台播放模式的枚举。 \| 名称 \| 值 \| 说明 \| \| ------------------------- \| - \| ----------------------- \| \| ENABLE_BACKGROUND_PLAY \| 0 \| 支持后台播放。 \| \| DISABLE_BACKGROUND_PLAY \| 1 \| 不支持后台播放。 \| |
| [CallState](arkts-avsession-avsession-callstate-e.md) | 表示通话状态的枚举。 |
| [CallerType](arkts-avsession-avsession-callertype-e.md) | 表示调用方来源类型的枚举。 |
| [CastDisplayState](arkts-avsession-avsession-castdisplaystate-e.md) | 投播显示设备状态的枚举。 |
| [ConnectionState](arkts-avsession-avsession-connectionstate-e.md) | 连接状态枚举。 |
| [DecoderType](arkts-avsession-avsession-decodertype-e.md) | 枚举，设备所支持的解码格式。 |
| [DeviceType](arkts-avsession-avsession-devicetype-e.md) | 播放设备的类型枚举。 |
| [DisplayTag](arkts-avsession-avsession-displaytag-e.md) | 枚举，表示当前媒体资源的金标，即应用媒体音源的特殊类型标识。 |
| [ExtraKey](arkts-avsession-avsession-extrakey-e.md) | 表示定义在不同场景中使用的额外键的枚举。 |
| [LoopMode](arkts-avsession-avsession-loopmode-e.md) | 表示媒体播放循环模式的枚举。 |
| [PlaybackState](arkts-avsession-avsession-playbackstate-e.md) | 表示媒体播放状态的枚举。 |
| [ProtocolType](arkts-avsession-avsession-protocoltype-e.md) | 远端设备支持的协议类型的枚举。 |
| [ResolutionLevel](arkts-avsession-avsession-resolutionlevel-e.md) | 枚举，设备所支持的分辨率。 |
| [SkipIntervals](arkts-avsession-avsession-skipintervals-e.md) | 表示session支持的快进快退时间间隔的枚举。 \| 名称 \| 值 \| 说明 \| \| ---------------------- \| -- \| ----------------------- \| \| SECONDS_10 \| 10 \| 时间为10秒。 \| \| SECONDS_15 \| 15 \| 时间为15秒。 \| \| SECONDS_30 \| 30 \| 时间为30秒。 \| |

<!--Del-->
### 枚举（系统接口）

| 名称 | 说明 |
| --- | --- |
| [ConnectionState](arkts-avsession-avsession-connectionstate-e-sys.md) | 连接状态枚举。 |
| [DeviceLogEventCode](arkts-avsession-avsession-devicelogeventcode-e-sys.md) | 设备日志事件返回值的枚举。 |
| [DistributedSessionType](arkts-avsession-avsession-distributedsessiontype-e-sys.md) | 表示远端分布式设备支持的会话类型枚举。 |
| [ExtraKey](arkts-avsession-avsession-extrakey-e-sys.md) | 表示定义在不同场景中使用的额外键的枚举。 |
| [ProtocolType](arkts-avsession-avsession-protocoltype-e-sys.md) | 远端设备支持的协议类型的枚举。 |
| [SessionCategory](arkts-avsession-avsession-sessioncategory-e-sys.md) | 表示不同场景会话类别的枚举。 |
<!--DelEnd-->

### 类型

| 名称 | 说明 |
| --- | --- |
| [AVCastControlCommandType](arkts-avsession-avsession-avcastcontrolcommandtype-t.md) |  |
| [AVControlCommandType](arkts-avsession-avsession-avcontrolcommandtype-t.md) | The type of control command |
| [AVMediaCenterControlType](arkts-avsession-avsession-avmediacentercontroltype-t.md) | 应用可选择设置优先级的播控组件类型 |
| [AVSessionType](arkts-avsession-avsession-avsessiontype-t.md) | 当前会话支持的会话类型。 该类型可取的值为下表字符串。 |
| [ConnectionEvent](arkts-avsession-avsession-connectionevent-t.md) | The connection event supplied by system to indicate device state and information. |
| [EventProcess](arkts-avsession-avsession-eventprocess-t.md) | The general process funcation with an event and arguments. |
| [ExtraInfo](arkts-avsession-avsession-extrainfo-t.md) | The extra info object. |
| [KeyRequestCallback](arkts-avsession-avsession-keyrequestcallback-t.md) | 许可证请求事件的回调函数。 |
| [NoParamCallback](arkts-avsession-avsession-noparamcallback-t.md) | 定义无参数的回调函数类型。 |
| [TwoParamCallback](arkts-avsession-avsession-twoparamcallback-t.md) | 定义包含两个参数的回调类型。 |
| [VideoSizeEvent](arkts-avsession-avsession-videosizeevent-t.md) | The video size event. |

