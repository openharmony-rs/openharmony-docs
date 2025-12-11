| 操作 | 旧版本 | 新版本 | d.ts文件 |
| ---- | ------ | ------ | -------- |
|新增API|NA|类名：global；<br>API声明：declare struct AVCastPicker<br>差异内容：declare struct AVCastPicker|api/@ohos.multimedia.avCastPicker.d.ets|
|新增API|NA|类名：AVCastPicker；<br>API声明：@Prop<br>    normalColor?: Color \| number \| string;<br>差异内容：@Prop<br>    normalColor?: Color \| number \| string;|api/@ohos.multimedia.avCastPicker.d.ets|
|新增API|NA|类名：AVCastPicker；<br>API声明：@Prop<br>    activeColor?: Color \| number \| string;<br>差异内容：@Prop<br>    activeColor?: Color \| number \| string;|api/@ohos.multimedia.avCastPicker.d.ets|
|新增API|NA|类名：AVCastPicker；<br>API声明：onStateChange?: (state: AVCastPickerState) => void;<br>差异内容：onStateChange?: (state: AVCastPickerState) => void;|api/@ohos.multimedia.avCastPicker.d.ets|
|新增API|NA|类名：global；<br>API声明：export declare enum AVCastPickerState<br>差异内容：export declare enum AVCastPickerState|api/@ohos.multimedia.avCastPickerParam.d.ts|
|新增API|NA|类名：AVCastPickerState；<br>API声明：STATE_APPEARING<br>差异内容：STATE_APPEARING|api/@ohos.multimedia.avCastPickerParam.d.ts|
|新增API|NA|类名：AVCastPickerState；<br>API声明：STATE_DISAPPEARING<br>差异内容：STATE_DISAPPEARING|api/@ohos.multimedia.avCastPickerParam.d.ts|
|新增API|NA|类名：global；<br>API声明：declare namespace avSession<br>差异内容：declare namespace avSession|api/@ohos.multimedia.avsession.d.ts|
|新增API|NA|类名：avSession；<br>API声明：function createAVSession(context: Context, tag: string, type: AVSessionType, callback: AsyncCallback\<AVSession>): void;<br>差异内容：function createAVSession(context: Context, tag: string, type: AVSessionType, callback: AsyncCallback\<AVSession>): void;|api/@ohos.multimedia.avsession.d.ts|
|新增API|NA|类名：avSession；<br>API声明：function createAVSession(context: Context, tag: string, type: AVSessionType): Promise\<AVSession>;<br>差异内容：function createAVSession(context: Context, tag: string, type: AVSessionType): Promise\<AVSession>;|api/@ohos.multimedia.avsession.d.ts|
|新增API|NA|类名：avSession；<br>API声明：enum ProtocolType<br>差异内容：enum ProtocolType|api/@ohos.multimedia.avsession.d.ts|
|新增API|NA|类名：ProtocolType；<br>API声明：TYPE_LOCAL = 0<br>差异内容：TYPE_LOCAL = 0|api/@ohos.multimedia.avsession.d.ts|
|新增API|NA|类名：ProtocolType；<br>API声明：TYPE_CAST_PLUS_STREAM = 2<br>差异内容：TYPE_CAST_PLUS_STREAM = 2|api/@ohos.multimedia.avsession.d.ts|
|新增API|NA|类名：avSession；<br>API声明：type AVSessionType = 'audio' \| 'video' \| 'voice_call';<br>差异内容：type AVSessionType = 'audio' \| 'video' \| 'voice_call';|api/@ohos.multimedia.avsession.d.ts|
|新增API|NA|类名：avSession；<br>API声明：interface AVSession<br>差异内容：interface AVSession|api/@ohos.multimedia.avsession.d.ts|
|新增API|NA|类名：AVSession；<br>API声明：readonly sessionId: string;<br>差异内容：readonly sessionId: string;|api/@ohos.multimedia.avsession.d.ts|
|新增API|NA|类名：AVSession；<br>API声明：readonly sessionType: AVSessionType;<br>差异内容：readonly sessionType: AVSessionType;|api/@ohos.multimedia.avsession.d.ts|
|新增API|NA|类名：AVSession；<br>API声明：setAVMetadata(data: AVMetadata, callback: AsyncCallback\<void>): void;<br>差异内容：setAVMetadata(data: AVMetadata, callback: AsyncCallback\<void>): void;|api/@ohos.multimedia.avsession.d.ts|
|新增API|NA|类名：AVSession；<br>API声明：setAVMetadata(data: AVMetadata): Promise\<void>;<br>差异内容：setAVMetadata(data: AVMetadata): Promise\<void>;|api/@ohos.multimedia.avsession.d.ts|
|新增API|NA|类名：AVSession；<br>API声明：setCallMetadata(data: CallMetadata, callback: AsyncCallback\<void>): void;<br>差异内容：setCallMetadata(data: CallMetadata, callback: AsyncCallback\<void>): void;|api/@ohos.multimedia.avsession.d.ts|
|新增API|NA|类名：AVSession；<br>API声明：setCallMetadata(data: CallMetadata): Promise\<void>;<br>差异内容：setCallMetadata(data: CallMetadata): Promise\<void>;|api/@ohos.multimedia.avsession.d.ts|
|新增API|NA|类名：AVSession；<br>API声明：setAVPlaybackState(state: AVPlaybackState, callback: AsyncCallback\<void>): void;<br>差异内容：setAVPlaybackState(state: AVPlaybackState, callback: AsyncCallback\<void>): void;|api/@ohos.multimedia.avsession.d.ts|
|新增API|NA|类名：AVSession；<br>API声明：setAVPlaybackState(state: AVPlaybackState): Promise\<void>;<br>差异内容：setAVPlaybackState(state: AVPlaybackState): Promise\<void>;|api/@ohos.multimedia.avsession.d.ts|
|新增API|NA|类名：AVSession；<br>API声明：setAVCallState(state: AVCallState, callback: AsyncCallback\<void>): void;<br>差异内容：setAVCallState(state: AVCallState, callback: AsyncCallback\<void>): void;|api/@ohos.multimedia.avsession.d.ts|
|新增API|NA|类名：AVSession；<br>API声明：setAVCallState(state: AVCallState): Promise\<void>;<br>差异内容：setAVCallState(state: AVCallState): Promise\<void>;|api/@ohos.multimedia.avsession.d.ts|
|新增API|NA|类名：AVSession；<br>API声明：setLaunchAbility(ability: WantAgent, callback: AsyncCallback\<void>): void;<br>差异内容：setLaunchAbility(ability: WantAgent, callback: AsyncCallback\<void>): void;|api/@ohos.multimedia.avsession.d.ts|
|新增API|NA|类名：AVSession；<br>API声明：setLaunchAbility(ability: WantAgent): Promise\<void>;<br>差异内容：setLaunchAbility(ability: WantAgent): Promise\<void>;|api/@ohos.multimedia.avsession.d.ts|
|新增API|NA|类名：AVSession；<br>API声明：dispatchSessionEvent(event: string, args: {<br>            [key: string]: Object;<br>        }, callback: AsyncCallback\<void>): void;<br>差异内容：dispatchSessionEvent(event: string, args: {<br>            [key: string]: Object;<br>        }, callback: AsyncCallback\<void>): void;|api/@ohos.multimedia.avsession.d.ts|
|新增API|NA|类名：AVSession；<br>API声明：dispatchSessionEvent(event: string, args: {<br>            [key: string]: Object;<br>        }): Promise\<void>;<br>差异内容：dispatchSessionEvent(event: string, args: {<br>            [key: string]: Object;<br>        }): Promise\<void>;|api/@ohos.multimedia.avsession.d.ts|
|新增API|NA|类名：AVSession；<br>API声明：setAVQueueItems(items: Array\<AVQueueItem>, callback: AsyncCallback\<void>): void;<br>差异内容：setAVQueueItems(items: Array\<AVQueueItem>, callback: AsyncCallback\<void>): void;|api/@ohos.multimedia.avsession.d.ts|
|新增API|NA|类名：AVSession；<br>API声明：setAVQueueItems(items: Array\<AVQueueItem>): Promise\<void>;<br>差异内容：setAVQueueItems(items: Array\<AVQueueItem>): Promise\<void>;|api/@ohos.multimedia.avsession.d.ts|
|新增API|NA|类名：AVSession；<br>API声明：setAVQueueTitle(title: string, callback: AsyncCallback\<void>): void;<br>差异内容：setAVQueueTitle(title: string, callback: AsyncCallback\<void>): void;|api/@ohos.multimedia.avsession.d.ts|
|新增API|NA|类名：AVSession；<br>API声明：setAVQueueTitle(title: string): Promise\<void>;<br>差异内容：setAVQueueTitle(title: string): Promise\<void>;|api/@ohos.multimedia.avsession.d.ts|
|新增API|NA|类名：AVSession；<br>API声明：setExtras(extras: {<br>            [key: string]: Object;<br>        }, callback: AsyncCallback\<void>): void;<br>差异内容：setExtras(extras: {<br>            [key: string]: Object;<br>        }, callback: AsyncCallback\<void>): void;|api/@ohos.multimedia.avsession.d.ts|
|新增API|NA|类名：AVSession；<br>API声明：setExtras(extras: {<br>            [key: string]: Object;<br>        }): Promise\<void>;<br>差异内容：setExtras(extras: {<br>            [key: string]: Object;<br>        }): Promise\<void>;|api/@ohos.multimedia.avsession.d.ts|
|新增API|NA|类名：AVSession；<br>API声明：getController(callback: AsyncCallback\<AVSessionController>): void;<br>差异内容：getController(callback: AsyncCallback\<AVSessionController>): void;|api/@ohos.multimedia.avsession.d.ts|
|新增API|NA|类名：AVSession；<br>API声明：getController(): Promise\<AVSessionController>;<br>差异内容：getController(): Promise\<AVSessionController>;|api/@ohos.multimedia.avsession.d.ts|
|新增API|NA|类名：AVSession；<br>API声明：getAVCastController(callback: AsyncCallback\<AVCastController>): void;<br>差异内容：getAVCastController(callback: AsyncCallback\<AVCastController>): void;|api/@ohos.multimedia.avsession.d.ts|
|新增API|NA|类名：AVSession；<br>API声明：getAVCastController(): Promise\<AVCastController>;<br>差异内容：getAVCastController(): Promise\<AVCastController>;|api/@ohos.multimedia.avsession.d.ts|
|新增API|NA|类名：AVSession；<br>API声明：getOutputDevice(callback: AsyncCallback\<OutputDeviceInfo>): void;<br>差异内容：getOutputDevice(callback: AsyncCallback\<OutputDeviceInfo>): void;|api/@ohos.multimedia.avsession.d.ts|
|新增API|NA|类名：AVSession；<br>API声明：getOutputDevice(): Promise\<OutputDeviceInfo>;<br>差异内容：getOutputDevice(): Promise\<OutputDeviceInfo>;|api/@ohos.multimedia.avsession.d.ts|
|新增API|NA|类名：AVSession；<br>API声明：getOutputDeviceSync(): OutputDeviceInfo;<br>差异内容：getOutputDeviceSync(): OutputDeviceInfo;|api/@ohos.multimedia.avsession.d.ts|
|新增API|NA|类名：AVSession；<br>API声明：on(type: 'play', callback: () => void): void;<br>差异内容：on(type: 'play', callback: () => void): void;|api/@ohos.multimedia.avsession.d.ts|
|新增API|NA|类名：AVSession；<br>API声明：on(type: 'pause', callback: () => void): void;<br>差异内容：on(type: 'pause', callback: () => void): void;|api/@ohos.multimedia.avsession.d.ts|
|新增API|NA|类名：AVSession；<br>API声明：on(type: 'stop', callback: () => void): void;<br>差异内容：on(type: 'stop', callback: () => void): void;|api/@ohos.multimedia.avsession.d.ts|
|新增API|NA|类名：AVSession；<br>API声明：on(type: 'playNext', callback: () => void): void;<br>差异内容：on(type: 'playNext', callback: () => void): void;|api/@ohos.multimedia.avsession.d.ts|
|新增API|NA|类名：AVSession；<br>API声明：on(type: 'playPrevious', callback: () => void): void;<br>差异内容：on(type: 'playPrevious', callback: () => void): void;|api/@ohos.multimedia.avsession.d.ts|
|新增API|NA|类名：AVSession；<br>API声明：on(type: 'fastForward', callback: (time?: number) => void): void;<br>差异内容：on(type: 'fastForward', callback: (time?: number) => void): void;|api/@ohos.multimedia.avsession.d.ts|
|新增API|NA|类名：AVSession；<br>API声明：on(type: 'rewind', callback: (time?: number) => void): void;<br>差异内容：on(type: 'rewind', callback: (time?: number) => void): void;|api/@ohos.multimedia.avsession.d.ts|
|新增API|NA|类名：AVSession；<br>API声明：off(type: 'play', callback?: () => void): void;<br>差异内容：off(type: 'play', callback?: () => void): void;|api/@ohos.multimedia.avsession.d.ts|
|新增API|NA|类名：AVSession；<br>API声明：off(type: 'pause', callback?: () => void): void;<br>差异内容：off(type: 'pause', callback?: () => void): void;|api/@ohos.multimedia.avsession.d.ts|
|新增API|NA|类名：AVSession；<br>API声明：off(type: 'stop', callback?: () => void): void;<br>差异内容：off(type: 'stop', callback?: () => void): void;|api/@ohos.multimedia.avsession.d.ts|
|新增API|NA|类名：AVSession；<br>API声明：off(type: 'playNext', callback?: () => void): void;<br>差异内容：off(type: 'playNext', callback?: () => void): void;|api/@ohos.multimedia.avsession.d.ts|
|新增API|NA|类名：AVSession；<br>API声明：off(type: 'playPrevious', callback?: () => void): void;<br>差异内容：off(type: 'playPrevious', callback?: () => void): void;|api/@ohos.multimedia.avsession.d.ts|
|新增API|NA|类名：AVSession；<br>API声明：off(type: 'fastForward', callback?: () => void): void;<br>差异内容：off(type: 'fastForward', callback?: () => void): void;|api/@ohos.multimedia.avsession.d.ts|
|新增API|NA|类名：AVSession；<br>API声明：off(type: 'rewind', callback?: () => void): void;<br>差异内容：off(type: 'rewind', callback?: () => void): void;|api/@ohos.multimedia.avsession.d.ts|
|新增API|NA|类名：AVSession；<br>API声明：on(type: 'playFromAssetId', callback: (assetId: number) => void): void;<br>差异内容：on(type: 'playFromAssetId', callback: (assetId: number) => void): void;|api/@ohos.multimedia.avsession.d.ts|
|新增API|NA|类名：AVSession；<br>API声明：off(type: 'playFromAssetId', callback?: (assetId: number) => void): void;<br>差异内容：off(type: 'playFromAssetId', callback?: (assetId: number) => void): void;|api/@ohos.multimedia.avsession.d.ts|
|新增API|NA|类名：AVSession；<br>API声明：on(type: 'seek', callback: (time: number) => void): void;<br>差异内容：on(type: 'seek', callback: (time: number) => void): void;|api/@ohos.multimedia.avsession.d.ts|
|新增API|NA|类名：AVSession；<br>API声明：off(type: 'seek', callback?: (time: number) => void): void;<br>差异内容：off(type: 'seek', callback?: (time: number) => void): void;|api/@ohos.multimedia.avsession.d.ts|
|新增API|NA|类名：AVSession；<br>API声明：on(type: 'setSpeed', callback: (speed: number) => void): void;<br>差异内容：on(type: 'setSpeed', callback: (speed: number) => void): void;|api/@ohos.multimedia.avsession.d.ts|
|新增API|NA|类名：AVSession；<br>API声明：off(type: 'setSpeed', callback?: (speed: number) => void): void;<br>差异内容：off(type: 'setSpeed', callback?: (speed: number) => void): void;|api/@ohos.multimedia.avsession.d.ts|
|新增API|NA|类名：AVSession；<br>API声明：on(type: 'setLoopMode', callback: (mode: LoopMode) => void): void;<br>差异内容：on(type: 'setLoopMode', callback: (mode: LoopMode) => void): void;|api/@ohos.multimedia.avsession.d.ts|
|新增API|NA|类名：AVSession；<br>API声明：off(type: 'setLoopMode', callback?: (mode: LoopMode) => void): void;<br>差异内容：off(type: 'setLoopMode', callback?: (mode: LoopMode) => void): void;|api/@ohos.multimedia.avsession.d.ts|
|新增API|NA|类名：AVSession；<br>API声明：on(type: 'toggleFavorite', callback: (assetId: string) => void): void;<br>差异内容：on(type: 'toggleFavorite', callback: (assetId: string) => void): void;|api/@ohos.multimedia.avsession.d.ts|
|新增API|NA|类名：AVSession；<br>API声明：off(type: 'toggleFavorite', callback?: (assetId: string) => void): void;<br>差异内容：off(type: 'toggleFavorite', callback?: (assetId: string) => void): void;|api/@ohos.multimedia.avsession.d.ts|
|新增API|NA|类名：AVSession；<br>API声明：on(type: 'handleKeyEvent', callback: (event: KeyEvent) => void): void;<br>差异内容：on(type: 'handleKeyEvent', callback: (event: KeyEvent) => void): void;|api/@ohos.multimedia.avsession.d.ts|
|新增API|NA|类名：AVSession；<br>API声明：off(type: 'handleKeyEvent', callback?: (event: KeyEvent) => void): void;<br>差异内容：off(type: 'handleKeyEvent', callback?: (event: KeyEvent) => void): void;|api/@ohos.multimedia.avsession.d.ts|
|新增API|NA|类名：AVSession；<br>API声明：on(type: 'outputDeviceChange', callback: (state: ConnectionState, device: OutputDeviceInfo) => void): void;<br>差异内容：on(type: 'outputDeviceChange', callback: (state: ConnectionState, device: OutputDeviceInfo) => void): void;|api/@ohos.multimedia.avsession.d.ts|
|新增API|NA|类名：AVSession；<br>API声明：off(type: 'outputDeviceChange', callback?: (state: ConnectionState, device: OutputDeviceInfo) => void): void;<br>差异内容：off(type: 'outputDeviceChange', callback?: (state: ConnectionState, device: OutputDeviceInfo) => void): void;|api/@ohos.multimedia.avsession.d.ts|
|新增API|NA|类名：AVSession；<br>API声明：on(type: 'commonCommand', callback: (command: string, args: {<br>            [key: string]: Object;<br>        }) => void): void;<br>差异内容：on(type: 'commonCommand', callback: (command: string, args: {<br>            [key: string]: Object;<br>        }) => void): void;|api/@ohos.multimedia.avsession.d.ts|
|新增API|NA|类名：AVSession；<br>API声明：off(type: 'commonCommand', callback?: (command: string, args: {<br>            [key: string]: Object;<br>        }) => void): void;<br>差异内容：off(type: 'commonCommand', callback?: (command: string, args: {<br>            [key: string]: Object;<br>        }) => void): void;|api/@ohos.multimedia.avsession.d.ts|
|新增API|NA|类名：AVSession；<br>API声明：on(type: 'skipToQueueItem', callback: (itemId: number) => void): void;<br>差异内容：on(type: 'skipToQueueItem', callback: (itemId: number) => void): void;|api/@ohos.multimedia.avsession.d.ts|
|新增API|NA|类名：AVSession；<br>API声明：off(type: 'skipToQueueItem', callback?: (itemId: number) => void): void;<br>差异内容：off(type: 'skipToQueueItem', callback?: (itemId: number) => void): void;|api/@ohos.multimedia.avsession.d.ts|
|新增API|NA|类名：AVSession；<br>API声明：on(type: 'answer', callback: Callback\<void>): void;<br>差异内容：on(type: 'answer', callback: Callback\<void>): void;|api/@ohos.multimedia.avsession.d.ts|
|新增API|NA|类名：AVSession；<br>API声明：off(type: 'answer', callback?: Callback\<void>): void;<br>差异内容：off(type: 'answer', callback?: Callback\<void>): void;|api/@ohos.multimedia.avsession.d.ts|
|新增API|NA|类名：AVSession；<br>API声明：on(type: 'hangUp', callback: Callback\<void>): void;<br>差异内容：on(type: 'hangUp', callback: Callback\<void>): void;|api/@ohos.multimedia.avsession.d.ts|
|新增API|NA|类名：AVSession；<br>API声明：off(type: 'hangUp', callback?: Callback\<void>): void;<br>差异内容：off(type: 'hangUp', callback?: Callback\<void>): void;|api/@ohos.multimedia.avsession.d.ts|
|新增API|NA|类名：AVSession；<br>API声明：on(type: 'toggleCallMute', callback: Callback\<void>): void;<br>差异内容：on(type: 'toggleCallMute', callback: Callback\<void>): void;|api/@ohos.multimedia.avsession.d.ts|
|新增API|NA|类名：AVSession；<br>API声明：off(type: 'toggleCallMute', callback?: Callback\<void>): void;<br>差异内容：off(type: 'toggleCallMute', callback?: Callback\<void>): void;|api/@ohos.multimedia.avsession.d.ts|
|新增API|NA|类名：AVSession；<br>API声明：stopCasting(callback: AsyncCallback\<void>): void;<br>差异内容：stopCasting(callback: AsyncCallback\<void>): void;|api/@ohos.multimedia.avsession.d.ts|
|新增API|NA|类名：AVSession；<br>API声明：stopCasting(): Promise\<void>;<br>差异内容：stopCasting(): Promise\<void>;|api/@ohos.multimedia.avsession.d.ts|
|新增API|NA|类名：AVSession；<br>API声明：activate(callback: AsyncCallback\<void>): void;<br>差异内容：activate(callback: AsyncCallback\<void>): void;|api/@ohos.multimedia.avsession.d.ts|
|新增API|NA|类名：AVSession；<br>API声明：activate(): Promise\<void>;<br>差异内容：activate(): Promise\<void>;|api/@ohos.multimedia.avsession.d.ts|
|新增API|NA|类名：AVSession；<br>API声明：deactivate(callback: AsyncCallback\<void>): void;<br>差异内容：deactivate(callback: AsyncCallback\<void>): void;|api/@ohos.multimedia.avsession.d.ts|
|新增API|NA|类名：AVSession；<br>API声明：deactivate(): Promise\<void>;<br>差异内容：deactivate(): Promise\<void>;|api/@ohos.multimedia.avsession.d.ts|
|新增API|NA|类名：AVSession；<br>API声明：destroy(callback: AsyncCallback\<void>): void;<br>差异内容：destroy(callback: AsyncCallback\<void>): void;|api/@ohos.multimedia.avsession.d.ts|
|新增API|NA|类名：AVSession；<br>API声明：destroy(): Promise\<void>;<br>差异内容：destroy(): Promise\<void>;|api/@ohos.multimedia.avsession.d.ts|
|新增API|NA|类名：avSession；<br>API声明：type AVCastControlCommandType = 'play' \| 'pause' \| 'stop' \| 'playNext' \| 'playPrevious' \| 'fastForward' \| 'rewind' \| 'seek' \| 'setVolume' \| 'setSpeed' \| 'setLoopMode' \| 'toggleFavorite' \| 'toggleMute';<br>差异内容：type AVCastControlCommandType = 'play' \| 'pause' \| 'stop' \| 'playNext' \| 'playPrevious' \| 'fastForward' \| 'rewind' \| 'seek' \| 'setVolume' \| 'setSpeed' \| 'setLoopMode' \| 'toggleFavorite' \| 'toggleMute';|api/@ohos.multimedia.avsession.d.ts|
|新增API|NA|类名：avSession；<br>API声明：interface AVCastControlCommand<br>差异内容：interface AVCastControlCommand|api/@ohos.multimedia.avsession.d.ts|
|新增API|NA|类名：AVCastControlCommand；<br>API声明：command: AVCastControlCommandType;<br>差异内容：command: AVCastControlCommandType;|api/@ohos.multimedia.avsession.d.ts|
|新增API|NA|类名：AVCastControlCommand；<br>API声明：parameter?: media.PlaybackSpeed \| number \| string \| LoopMode;<br>差异内容：parameter?: media.PlaybackSpeed \| number \| string \| LoopMode;|api/@ohos.multimedia.avsession.d.ts|
|新增API|NA|类名：avSession；<br>API声明：interface AVCastController<br>差异内容：interface AVCastController|api/@ohos.multimedia.avsession.d.ts|
|新增API|NA|类名：AVCastController；<br>API声明：getAVPlaybackState(callback: AsyncCallback\<AVPlaybackState>): void;<br>差异内容：getAVPlaybackState(callback: AsyncCallback\<AVPlaybackState>): void;|api/@ohos.multimedia.avsession.d.ts|
|新增API|NA|类名：AVCastController；<br>API声明：getAVPlaybackState(): Promise\<AVPlaybackState>;<br>差异内容：getAVPlaybackState(): Promise\<AVPlaybackState>;|api/@ohos.multimedia.avsession.d.ts|
|新增API|NA|类名：AVCastController；<br>API声明：sendControlCommand(command: AVCastControlCommand, callback: AsyncCallback\<void>): void;<br>差异内容：sendControlCommand(command: AVCastControlCommand, callback: AsyncCallback\<void>): void;|api/@ohos.multimedia.avsession.d.ts|
|新增API|NA|类名：AVCastController；<br>API声明：sendControlCommand(command: AVCastControlCommand): Promise\<void>;<br>差异内容：sendControlCommand(command: AVCastControlCommand): Promise\<void>;|api/@ohos.multimedia.avsession.d.ts|
|新增API|NA|类名：AVCastController；<br>API声明：start(item: AVQueueItem, callback: AsyncCallback\<void>): void;<br>差异内容：start(item: AVQueueItem, callback: AsyncCallback\<void>): void;|api/@ohos.multimedia.avsession.d.ts|
|新增API|NA|类名：AVCastController；<br>API声明：start(item: AVQueueItem): Promise\<void>;<br>差异内容：start(item: AVQueueItem): Promise\<void>;|api/@ohos.multimedia.avsession.d.ts|
|新增API|NA|类名：AVCastController；<br>API声明：prepare(item: AVQueueItem, callback: AsyncCallback\<void>): void;<br>差异内容：prepare(item: AVQueueItem, callback: AsyncCallback\<void>): void;|api/@ohos.multimedia.avsession.d.ts|
|新增API|NA|类名：AVCastController；<br>API声明：prepare(item: AVQueueItem): Promise\<void>;<br>差异内容：prepare(item: AVQueueItem): Promise\<void>;|api/@ohos.multimedia.avsession.d.ts|
|新增API|NA|类名：AVCastController；<br>API声明：getCurrentItem(callback: AsyncCallback\<AVQueueItem>): void;<br>差异内容：getCurrentItem(callback: AsyncCallback\<AVQueueItem>): void;|api/@ohos.multimedia.avsession.d.ts|
|新增API|NA|类名：AVCastController；<br>API声明：getCurrentItem(): Promise\<AVQueueItem>;<br>差异内容：getCurrentItem(): Promise\<AVQueueItem>;|api/@ohos.multimedia.avsession.d.ts|
|新增API|NA|类名：AVCastController；<br>API声明：getValidCommands(callback: AsyncCallback\<Array\<AVCastControlCommandType>>): void;<br>差异内容：getValidCommands(callback: AsyncCallback\<Array\<AVCastControlCommandType>>): void;|api/@ohos.multimedia.avsession.d.ts|
|新增API|NA|类名：AVCastController；<br>API声明：getValidCommands(): Promise\<Array\<AVCastControlCommandType>>;<br>差异内容：getValidCommands(): Promise\<Array\<AVCastControlCommandType>>;|api/@ohos.multimedia.avsession.d.ts|
|新增API|NA|类名：AVCastController；<br>API声明：release(callback: AsyncCallback\<void>): void;<br>差异内容：release(callback: AsyncCallback\<void>): void;|api/@ohos.multimedia.avsession.d.ts|
|新增API|NA|类名：AVCastController；<br>API声明：release(): Promise\<void>;<br>差异内容：release(): Promise\<void>;|api/@ohos.multimedia.avsession.d.ts|
|新增API|NA|类名：AVCastController；<br>API声明：on(type: 'playbackStateChange', filter: Array\<keyof AVPlaybackState> \| 'all', callback: (state: AVPlaybackState) => void): void;<br>差异内容：on(type: 'playbackStateChange', filter: Array\<keyof AVPlaybackState> \| 'all', callback: (state: AVPlaybackState) => void): void;|api/@ohos.multimedia.avsession.d.ts|
|新增API|NA|类名：AVCastController；<br>API声明：off(type: 'playbackStateChange', callback?: (state: AVPlaybackState) => void): void;<br>差异内容：off(type: 'playbackStateChange', callback?: (state: AVPlaybackState) => void): void;|api/@ohos.multimedia.avsession.d.ts|
|新增API|NA|类名：AVCastController；<br>API声明：on(type: 'mediaItemChange', callback: Callback\<AVQueueItem>): void;<br>差异内容：on(type: 'mediaItemChange', callback: Callback\<AVQueueItem>): void;|api/@ohos.multimedia.avsession.d.ts|
|新增API|NA|类名：AVCastController；<br>API声明：off(type: 'mediaItemChange'): void;<br>差异内容：off(type: 'mediaItemChange'): void;|api/@ohos.multimedia.avsession.d.ts|
|新增API|NA|类名：AVCastController；<br>API声明：on(type: 'playNext', callback: Callback\<void>): void;<br>差异内容：on(type: 'playNext', callback: Callback\<void>): void;|api/@ohos.multimedia.avsession.d.ts|
|新增API|NA|类名：AVCastController；<br>API声明：off(type: 'playNext'): void;<br>差异内容：off(type: 'playNext'): void;|api/@ohos.multimedia.avsession.d.ts|
|新增API|NA|类名：AVCastController；<br>API声明：on(type: 'playPrevious', callback: Callback\<void>): void;<br>差异内容：on(type: 'playPrevious', callback: Callback\<void>): void;|api/@ohos.multimedia.avsession.d.ts|
|新增API|NA|类名：AVCastController；<br>API声明：off(type: 'playPrevious'): void;<br>差异内容：off(type: 'playPrevious'): void;|api/@ohos.multimedia.avsession.d.ts|
|新增API|NA|类名：AVCastController；<br>API声明：on(type: 'requestPlay', callback: Callback\<AVQueueItem>): void;<br>差异内容：on(type: 'requestPlay', callback: Callback\<AVQueueItem>): void;|api/@ohos.multimedia.avsession.d.ts|
|新增API|NA|类名：AVCastController；<br>API声明：off(type: 'requestPlay', callback?: Callback\<AVQueueItem>): void;<br>差异内容：off(type: 'requestPlay', callback?: Callback\<AVQueueItem>): void;|api/@ohos.multimedia.avsession.d.ts|
|新增API|NA|类名：AVCastController；<br>API声明：on(type: 'endOfStream', callback: Callback\<void>): void;<br>差异内容：on(type: 'endOfStream', callback: Callback\<void>): void;|api/@ohos.multimedia.avsession.d.ts|
|新增API|NA|类名：AVCastController；<br>API声明：off(type: 'endOfStream', callback?: Callback\<void>): void;<br>差异内容：off(type: 'endOfStream', callback?: Callback\<void>): void;|api/@ohos.multimedia.avsession.d.ts|
|新增API|NA|类名：AVCastController；<br>API声明：on(type: 'seekDone', callback: Callback\<number>): void;<br>差异内容：on(type: 'seekDone', callback: Callback\<number>): void;|api/@ohos.multimedia.avsession.d.ts|
|新增API|NA|类名：AVCastController；<br>API声明：off(type: 'seekDone'): void;<br>差异内容：off(type: 'seekDone'): void;|api/@ohos.multimedia.avsession.d.ts|
|新增API|NA|类名：AVCastController；<br>API声明：on(type: 'validCommandChange', callback: Callback\<Array\<AVCastControlCommandType>>);<br>差异内容：on(type: 'validCommandChange', callback: Callback\<Array\<AVCastControlCommandType>>);|api/@ohos.multimedia.avsession.d.ts|
|新增API|NA|类名：AVCastController；<br>API声明：off(type: 'validCommandChange', callback?: Callback\<Array\<AVCastControlCommandType>>);<br>差异内容：off(type: 'validCommandChange', callback?: Callback\<Array\<AVCastControlCommandType>>);|api/@ohos.multimedia.avsession.d.ts|
|新增API|NA|类名：AVCastController；<br>API声明：on(type: 'error', callback: ErrorCallback): void;<br>差异内容：on(type: 'error', callback: ErrorCallback): void;|api/@ohos.multimedia.avsession.d.ts|
|新增API|NA|类名：AVCastController；<br>API声明：off(type: 'error'): void;<br>差异内容：off(type: 'error'): void;|api/@ohos.multimedia.avsession.d.ts|
|新增API|NA|类名：avSession；<br>API声明：enum ConnectionState<br>差异内容：enum ConnectionState|api/@ohos.multimedia.avsession.d.ts|
|新增API|NA|类名：ConnectionState；<br>API声明：STATE_CONNECTING = 0<br>差异内容：STATE_CONNECTING = 0|api/@ohos.multimedia.avsession.d.ts|
|新增API|NA|类名：ConnectionState；<br>API声明：STATE_CONNECTED = 1<br>差异内容：STATE_CONNECTED = 1|api/@ohos.multimedia.avsession.d.ts|
|新增API|NA|类名：ConnectionState；<br>API声明：STATE_DISCONNECTED = 6<br>差异内容：STATE_DISCONNECTED = 6|api/@ohos.multimedia.avsession.d.ts|
|新增API|NA|类名：avSession；<br>API声明：enum DisplayTag<br>差异内容：enum DisplayTag|api/@ohos.multimedia.avsession.d.ts|
|新增API|NA|类名：DisplayTag；<br>API声明：TAG_AUDIO_VIVID = 1<br>差异内容：TAG_AUDIO_VIVID = 1|api/@ohos.multimedia.avsession.d.ts|
|新增API|NA|类名：avSession；<br>API声明：interface AVMetadata<br>差异内容：interface AVMetadata|api/@ohos.multimedia.avsession.d.ts|
|新增API|NA|类名：AVMetadata；<br>API声明：assetId: string;<br>差异内容：assetId: string;|api/@ohos.multimedia.avsession.d.ts|
|新增API|NA|类名：AVMetadata；<br>API声明：title?: string;<br>差异内容：title?: string;|api/@ohos.multimedia.avsession.d.ts|
|新增API|NA|类名：AVMetadata；<br>API声明：artist?: string;<br>差异内容：artist?: string;|api/@ohos.multimedia.avsession.d.ts|
|新增API|NA|类名：AVMetadata；<br>API声明：author?: string;<br>差异内容：author?: string;|api/@ohos.multimedia.avsession.d.ts|
|新增API|NA|类名：AVMetadata；<br>API声明：avQueueId?: string;<br>差异内容：avQueueId?: string;|api/@ohos.multimedia.avsession.d.ts|
|新增API|NA|类名：AVMetadata；<br>API声明：avQueueImage?: image.PixelMap \| string;<br>差异内容：avQueueImage?: image.PixelMap \| string;|api/@ohos.multimedia.avsession.d.ts|
|新增API|NA|类名：AVMetadata；<br>API声明：album?: string;<br>差异内容：album?: string;|api/@ohos.multimedia.avsession.d.ts|
|新增API|NA|类名：AVMetadata；<br>API声明：writer?: string;<br>差异内容：writer?: string;|api/@ohos.multimedia.avsession.d.ts|
|新增API|NA|类名：AVMetadata；<br>API声明：composer?: string;<br>差异内容：composer?: string;|api/@ohos.multimedia.avsession.d.ts|
|新增API|NA|类名：AVMetadata；<br>API声明：duration?: number;<br>差异内容：duration?: number;|api/@ohos.multimedia.avsession.d.ts|
|新增API|NA|类名：AVMetadata；<br>API声明：mediaImage?: image.PixelMap \| string;<br>差异内容：mediaImage?: image.PixelMap \| string;|api/@ohos.multimedia.avsession.d.ts|
|新增API|NA|类名：AVMetadata；<br>API声明：publishDate?: Date;<br>差异内容：publishDate?: Date;|api/@ohos.multimedia.avsession.d.ts|
|新增API|NA|类名：AVMetadata；<br>API声明：subtitle?: string;<br>差异内容：subtitle?: string;|api/@ohos.multimedia.avsession.d.ts|
|新增API|NA|类名：AVMetadata；<br>API声明：description?: string;<br>差异内容：description?: string;|api/@ohos.multimedia.avsession.d.ts|
|新增API|NA|类名：AVMetadata；<br>API声明：lyric?: string;<br>差异内容：lyric?: string;|api/@ohos.multimedia.avsession.d.ts|
|新增API|NA|类名：AVMetadata；<br>API声明：previousAssetId?: string;<br>差异内容：previousAssetId?: string;|api/@ohos.multimedia.avsession.d.ts|
|新增API|NA|类名：AVMetadata；<br>API声明：nextAssetId?: string;<br>差异内容：nextAssetId?: string;|api/@ohos.multimedia.avsession.d.ts|
|新增API|NA|类名：AVMetadata；<br>API声明：filter?: number;<br>差异内容：filter?: number;|api/@ohos.multimedia.avsession.d.ts|
|新增API|NA|类名：AVMetadata；<br>API声明：skipIntervals?: SkipIntervals;<br>差异内容：skipIntervals?: SkipIntervals;|api/@ohos.multimedia.avsession.d.ts|
|新增API|NA|类名：AVMetadata；<br>API声明：displayTags?: number;<br>差异内容：displayTags?: number;|api/@ohos.multimedia.avsession.d.ts|
|新增API|NA|类名：avSession；<br>API声明：interface AVMediaDescription<br>差异内容：interface AVMediaDescription|api/@ohos.multimedia.avsession.d.ts|
|新增API|NA|类名：AVMediaDescription；<br>API声明：assetId: string;<br>差异内容：assetId: string;|api/@ohos.multimedia.avsession.d.ts|
|新增API|NA|类名：AVMediaDescription；<br>API声明：title?: string;<br>差异内容：title?: string;|api/@ohos.multimedia.avsession.d.ts|
|新增API|NA|类名：AVMediaDescription；<br>API声明：subtitle?: string;<br>差异内容：subtitle?: string;|api/@ohos.multimedia.avsession.d.ts|
|新增API|NA|类名：AVMediaDescription；<br>API声明：description?: string;<br>差异内容：description?: string;|api/@ohos.multimedia.avsession.d.ts|
|新增API|NA|类名：AVMediaDescription；<br>API声明：mediaImage?: image.PixelMap \| string;<br>差异内容：mediaImage?: image.PixelMap \| string;|api/@ohos.multimedia.avsession.d.ts|
|新增API|NA|类名：AVMediaDescription；<br>API声明：extras?: {<br>            [key: string]: Object;<br>        };<br>差异内容：extras?: {<br>            [key: string]: Object;<br>        };|api/@ohos.multimedia.avsession.d.ts|
|新增API|NA|类名：AVMediaDescription；<br>API声明：mediaType?: string;<br>差异内容：mediaType?: string;|api/@ohos.multimedia.avsession.d.ts|
|新增API|NA|类名：AVMediaDescription；<br>API声明：mediaSize?: number;<br>差异内容：mediaSize?: number;|api/@ohos.multimedia.avsession.d.ts|
|新增API|NA|类名：AVMediaDescription；<br>API声明：albumTitle?: string;<br>差异内容：albumTitle?: string;|api/@ohos.multimedia.avsession.d.ts|
|新增API|NA|类名：AVMediaDescription；<br>API声明：albumCoverUri?: string;<br>差异内容：albumCoverUri?: string;|api/@ohos.multimedia.avsession.d.ts|
|新增API|NA|类名：AVMediaDescription；<br>API声明：lyricContent?: string;<br>差异内容：lyricContent?: string;|api/@ohos.multimedia.avsession.d.ts|
|新增API|NA|类名：AVMediaDescription；<br>API声明：lyricUri?: string;<br>差异内容：lyricUri?: string;|api/@ohos.multimedia.avsession.d.ts|
|新增API|NA|类名：AVMediaDescription；<br>API声明：artist?: string;<br>差异内容：artist?: string;|api/@ohos.multimedia.avsession.d.ts|
|新增API|NA|类名：AVMediaDescription；<br>API声明：mediaUri?: string;<br>差异内容：mediaUri?: string;|api/@ohos.multimedia.avsession.d.ts|
|新增API|NA|类名：AVMediaDescription；<br>API声明：fdSrc?: media.AVFileDescriptor;<br>差异内容：fdSrc?: media.AVFileDescriptor;|api/@ohos.multimedia.avsession.d.ts|
|新增API|NA|类名：AVMediaDescription；<br>API声明：duration?: number;<br>差异内容：duration?: number;|api/@ohos.multimedia.avsession.d.ts|
|新增API|NA|类名：AVMediaDescription；<br>API声明：startPosition?: number;<br>差异内容：startPosition?: number;|api/@ohos.multimedia.avsession.d.ts|
|新增API|NA|类名：AVMediaDescription；<br>API声明：creditsPosition?: number;<br>差异内容：creditsPosition?: number;|api/@ohos.multimedia.avsession.d.ts|
|新增API|NA|类名：AVMediaDescription；<br>API声明：appName?: string;<br>差异内容：appName?: string;|api/@ohos.multimedia.avsession.d.ts|
|新增API|NA|类名：AVMediaDescription；<br>API声明：displayTags?: number;<br>差异内容：displayTags?: number;|api/@ohos.multimedia.avsession.d.ts|
|新增API|NA|类名：avSession；<br>API声明：interface AVQueueItem<br>差异内容：interface AVQueueItem|api/@ohos.multimedia.avsession.d.ts|
|新增API|NA|类名：AVQueueItem；<br>API声明：itemId: number;<br>差异内容：itemId: number;|api/@ohos.multimedia.avsession.d.ts|
|新增API|NA|类名：AVQueueItem；<br>API声明：description?: AVMediaDescription;<br>差异内容：description?: AVMediaDescription;|api/@ohos.multimedia.avsession.d.ts|
|新增API|NA|类名：avSession；<br>API声明：interface AVPlaybackState<br>差异内容：interface AVPlaybackState|api/@ohos.multimedia.avsession.d.ts|
|新增API|NA|类名：AVPlaybackState；<br>API声明：state?: PlaybackState;<br>差异内容：state?: PlaybackState;|api/@ohos.multimedia.avsession.d.ts|
|新增API|NA|类名：AVPlaybackState；<br>API声明：speed?: number;<br>差异内容：speed?: number;|api/@ohos.multimedia.avsession.d.ts|
|新增API|NA|类名：AVPlaybackState；<br>API声明：position?: PlaybackPosition;<br>差异内容：position?: PlaybackPosition;|api/@ohos.multimedia.avsession.d.ts|
|新增API|NA|类名：AVPlaybackState；<br>API声明：bufferedTime?: number;<br>差异内容：bufferedTime?: number;|api/@ohos.multimedia.avsession.d.ts|
|新增API|NA|类名：AVPlaybackState；<br>API声明：loopMode?: LoopMode;<br>差异内容：loopMode?: LoopMode;|api/@ohos.multimedia.avsession.d.ts|
|新增API|NA|类名：AVPlaybackState；<br>API声明：isFavorite?: boolean;<br>差异内容：isFavorite?: boolean;|api/@ohos.multimedia.avsession.d.ts|
|新增API|NA|类名：AVPlaybackState；<br>API声明：activeItemId?: number;<br>差异内容：activeItemId?: number;|api/@ohos.multimedia.avsession.d.ts|
|新增API|NA|类名：AVPlaybackState；<br>API声明：volume?: number;<br>差异内容：volume?: number;|api/@ohos.multimedia.avsession.d.ts|
|新增API|NA|类名：AVPlaybackState；<br>API声明：maxVolume?: number;<br>差异内容：maxVolume?: number;|api/@ohos.multimedia.avsession.d.ts|
|新增API|NA|类名：AVPlaybackState；<br>API声明：muted?: boolean;<br>差异内容：muted?: boolean;|api/@ohos.multimedia.avsession.d.ts|
|新增API|NA|类名：AVPlaybackState；<br>API声明：duration?: number;<br>差异内容：duration?: number;|api/@ohos.multimedia.avsession.d.ts|
|新增API|NA|类名：AVPlaybackState；<br>API声明：videoWidth?: number;<br>差异内容：videoWidth?: number;|api/@ohos.multimedia.avsession.d.ts|
|新增API|NA|类名：AVPlaybackState；<br>API声明：videoHeight?: number;<br>差异内容：videoHeight?: number;|api/@ohos.multimedia.avsession.d.ts|
|新增API|NA|类名：AVPlaybackState；<br>API声明：extras?: {<br>            [key: string]: Object;<br>        };<br>差异内容：extras?: {<br>            [key: string]: Object;<br>        };|api/@ohos.multimedia.avsession.d.ts|
|新增API|NA|类名：avSession；<br>API声明：interface PlaybackPosition<br>差异内容：interface PlaybackPosition|api/@ohos.multimedia.avsession.d.ts|
|新增API|NA|类名：PlaybackPosition；<br>API声明：elapsedTime: number;<br>差异内容：elapsedTime: number;|api/@ohos.multimedia.avsession.d.ts|
|新增API|NA|类名：PlaybackPosition；<br>API声明：updateTime: number;<br>差异内容：updateTime: number;|api/@ohos.multimedia.avsession.d.ts|
|新增API|NA|类名：avSession；<br>API声明：interface CallMetadata<br>差异内容：interface CallMetadata|api/@ohos.multimedia.avsession.d.ts|
|新增API|NA|类名：CallMetadata；<br>API声明：name?: string;<br>差异内容：name?: string;|api/@ohos.multimedia.avsession.d.ts|
|新增API|NA|类名：CallMetadata；<br>API声明：phoneNumber?: string;<br>差异内容：phoneNumber?: string;|api/@ohos.multimedia.avsession.d.ts|
|新增API|NA|类名：CallMetadata；<br>API声明：avatar?: image.PixelMap;<br>差异内容：avatar?: image.PixelMap;|api/@ohos.multimedia.avsession.d.ts|
|新增API|NA|类名：avSession；<br>API声明：interface AVCallState<br>差异内容：interface AVCallState|api/@ohos.multimedia.avsession.d.ts|
|新增API|NA|类名：AVCallState；<br>API声明：state: CallState;<br>差异内容：state: CallState;|api/@ohos.multimedia.avsession.d.ts|
|新增API|NA|类名：AVCallState；<br>API声明：muted: boolean;<br>差异内容：muted: boolean;|api/@ohos.multimedia.avsession.d.ts|
|新增API|NA|类名：avSession；<br>API声明：enum CallState<br>差异内容：enum CallState|api/@ohos.multimedia.avsession.d.ts|
|新增API|NA|类名：CallState；<br>API声明：CALL_STATE_IDLE = 0<br>差异内容：CALL_STATE_IDLE = 0|api/@ohos.multimedia.avsession.d.ts|
|新增API|NA|类名：CallState；<br>API声明：CALL_STATE_INCOMING = 1<br>差异内容：CALL_STATE_INCOMING = 1|api/@ohos.multimedia.avsession.d.ts|
|新增API|NA|类名：CallState；<br>API声明：CALL_STATE_ACTIVE = 2<br>差异内容：CALL_STATE_ACTIVE = 2|api/@ohos.multimedia.avsession.d.ts|
|新增API|NA|类名：CallState；<br>API声明：CALL_STATE_DIALING = 3<br>差异内容：CALL_STATE_DIALING = 3|api/@ohos.multimedia.avsession.d.ts|
|新增API|NA|类名：CallState；<br>API声明：CALL_STATE_WAITING = 4<br>差异内容：CALL_STATE_WAITING = 4|api/@ohos.multimedia.avsession.d.ts|
|新增API|NA|类名：CallState；<br>API声明：CALL_STATE_HOLDING = 5<br>差异内容：CALL_STATE_HOLDING = 5|api/@ohos.multimedia.avsession.d.ts|
|新增API|NA|类名：CallState；<br>API声明：CALL_STATE_DISCONNECTING = 6<br>差异内容：CALL_STATE_DISCONNECTING = 6|api/@ohos.multimedia.avsession.d.ts|
|新增API|NA|类名：avSession；<br>API声明：enum AVCastCategory<br>差异内容：enum AVCastCategory|api/@ohos.multimedia.avsession.d.ts|
|新增API|NA|类名：AVCastCategory；<br>API声明：CATEGORY_LOCAL = 0<br>差异内容：CATEGORY_LOCAL = 0|api/@ohos.multimedia.avsession.d.ts|
|新增API|NA|类名：AVCastCategory；<br>API声明：CATEGORY_REMOTE = 1<br>差异内容：CATEGORY_REMOTE = 1|api/@ohos.multimedia.avsession.d.ts|
|新增API|NA|类名：avSession；<br>API声明：enum DeviceType<br>差异内容：enum DeviceType|api/@ohos.multimedia.avsession.d.ts|
|新增API|NA|类名：DeviceType；<br>API声明：DEVICE_TYPE_LOCAL = 0<br>差异内容：DEVICE_TYPE_LOCAL = 0|api/@ohos.multimedia.avsession.d.ts|
|新增API|NA|类名：DeviceType；<br>API声明：DEVICE_TYPE_TV = 2<br>差异内容：DEVICE_TYPE_TV = 2|api/@ohos.multimedia.avsession.d.ts|
|新增API|NA|类名：DeviceType；<br>API声明：DEVICE_TYPE_SMART_SPEAKER = 3<br>差异内容：DEVICE_TYPE_SMART_SPEAKER = 3|api/@ohos.multimedia.avsession.d.ts|
|新增API|NA|类名：DeviceType；<br>API声明：DEVICE_TYPE_BLUETOOTH = 10<br>差异内容：DEVICE_TYPE_BLUETOOTH = 10|api/@ohos.multimedia.avsession.d.ts|
|新增API|NA|类名：avSession；<br>API声明：interface DeviceInfo<br>差异内容：interface DeviceInfo|api/@ohos.multimedia.avsession.d.ts|
|新增API|NA|类名：DeviceInfo；<br>API声明：castCategory: AVCastCategory;<br>差异内容：castCategory: AVCastCategory;|api/@ohos.multimedia.avsession.d.ts|
|新增API|NA|类名：DeviceInfo；<br>API声明：deviceId: string;<br>差异内容：deviceId: string;|api/@ohos.multimedia.avsession.d.ts|
|新增API|NA|类名：DeviceInfo；<br>API声明：deviceName: string;<br>差异内容：deviceName: string;|api/@ohos.multimedia.avsession.d.ts|
|新增API|NA|类名：DeviceInfo；<br>API声明：deviceType: DeviceType;<br>差异内容：deviceType: DeviceType;|api/@ohos.multimedia.avsession.d.ts|
|新增API|NA|类名：DeviceInfo；<br>API声明：supportedProtocols?: number;<br>差异内容：supportedProtocols?: number;|api/@ohos.multimedia.avsession.d.ts|
|新增API|NA|类名：avSession；<br>API声明：interface OutputDeviceInfo<br>差异内容：interface OutputDeviceInfo|api/@ohos.multimedia.avsession.d.ts|
|新增API|NA|类名：OutputDeviceInfo；<br>API声明：devices: Array\<DeviceInfo>;<br>差异内容：devices: Array\<DeviceInfo>;|api/@ohos.multimedia.avsession.d.ts|
|新增API|NA|类名：avSession；<br>API声明：enum LoopMode<br>差异内容：enum LoopMode|api/@ohos.multimedia.avsession.d.ts|
|新增API|NA|类名：LoopMode；<br>API声明：LOOP_MODE_SEQUENCE = 0<br>差异内容：LOOP_MODE_SEQUENCE = 0|api/@ohos.multimedia.avsession.d.ts|
|新增API|NA|类名：LoopMode；<br>API声明：LOOP_MODE_SINGLE = 1<br>差异内容：LOOP_MODE_SINGLE = 1|api/@ohos.multimedia.avsession.d.ts|
|新增API|NA|类名：LoopMode；<br>API声明：LOOP_MODE_LIST = 2<br>差异内容：LOOP_MODE_LIST = 2|api/@ohos.multimedia.avsession.d.ts|
|新增API|NA|类名：LoopMode；<br>API声明：LOOP_MODE_SHUFFLE = 3<br>差异内容：LOOP_MODE_SHUFFLE = 3|api/@ohos.multimedia.avsession.d.ts|
|新增API|NA|类名：LoopMode；<br>API声明：LOOP_MODE_CUSTOM = 4<br>差异内容：LOOP_MODE_CUSTOM = 4|api/@ohos.multimedia.avsession.d.ts|
|新增API|NA|类名：avSession；<br>API声明：enum SkipIntervals<br>差异内容：enum SkipIntervals|api/@ohos.multimedia.avsession.d.ts|
|新增API|NA|类名：SkipIntervals；<br>API声明：SECONDS_10 = 10<br>差异内容：SECONDS_10 = 10|api/@ohos.multimedia.avsession.d.ts|
|新增API|NA|类名：SkipIntervals；<br>API声明：SECONDS_15 = 15<br>差异内容：SECONDS_15 = 15|api/@ohos.multimedia.avsession.d.ts|
|新增API|NA|类名：SkipIntervals；<br>API声明：SECONDS_30 = 30<br>差异内容：SECONDS_30 = 30|api/@ohos.multimedia.avsession.d.ts|
|新增API|NA|类名：avSession；<br>API声明：enum PlaybackState<br>差异内容：enum PlaybackState|api/@ohos.multimedia.avsession.d.ts|
|新增API|NA|类名：PlaybackState；<br>API声明：PLAYBACK_STATE_INITIAL = 0<br>差异内容：PLAYBACK_STATE_INITIAL = 0|api/@ohos.multimedia.avsession.d.ts|
|新增API|NA|类名：PlaybackState；<br>API声明：PLAYBACK_STATE_PREPARE = 1<br>差异内容：PLAYBACK_STATE_PREPARE = 1|api/@ohos.multimedia.avsession.d.ts|
|新增API|NA|类名：PlaybackState；<br>API声明：PLAYBACK_STATE_PLAY = 2<br>差异内容：PLAYBACK_STATE_PLAY = 2|api/@ohos.multimedia.avsession.d.ts|
|新增API|NA|类名：PlaybackState；<br>API声明：PLAYBACK_STATE_PAUSE = 3<br>差异内容：PLAYBACK_STATE_PAUSE = 3|api/@ohos.multimedia.avsession.d.ts|
|新增API|NA|类名：PlaybackState；<br>API声明：PLAYBACK_STATE_FAST_FORWARD = 4<br>差异内容：PLAYBACK_STATE_FAST_FORWARD = 4|api/@ohos.multimedia.avsession.d.ts|
|新增API|NA|类名：PlaybackState；<br>API声明：PLAYBACK_STATE_REWIND = 5<br>差异内容：PLAYBACK_STATE_REWIND = 5|api/@ohos.multimedia.avsession.d.ts|
|新增API|NA|类名：PlaybackState；<br>API声明：PLAYBACK_STATE_STOP = 6<br>差异内容：PLAYBACK_STATE_STOP = 6|api/@ohos.multimedia.avsession.d.ts|
|新增API|NA|类名：PlaybackState；<br>API声明：PLAYBACK_STATE_COMPLETED = 7<br>差异内容：PLAYBACK_STATE_COMPLETED = 7|api/@ohos.multimedia.avsession.d.ts|
|新增API|NA|类名：PlaybackState；<br>API声明：PLAYBACK_STATE_RELEASED = 8<br>差异内容：PLAYBACK_STATE_RELEASED = 8|api/@ohos.multimedia.avsession.d.ts|
|新增API|NA|类名：PlaybackState；<br>API声明：PLAYBACK_STATE_ERROR = 9<br>差异内容：PLAYBACK_STATE_ERROR = 9|api/@ohos.multimedia.avsession.d.ts|
|新增API|NA|类名：PlaybackState；<br>API声明：PLAYBACK_STATE_IDLE = 10<br>差异内容：PLAYBACK_STATE_IDLE = 10|api/@ohos.multimedia.avsession.d.ts|
|新增API|NA|类名：PlaybackState；<br>API声明：PLAYBACK_STATE_BUFFERING = 11<br>差异内容：PLAYBACK_STATE_BUFFERING = 11|api/@ohos.multimedia.avsession.d.ts|
|新增API|NA|类名：avSession；<br>API声明：interface AVSessionController<br>差异内容：interface AVSessionController|api/@ohos.multimedia.avsession.d.ts|
|新增API|NA|类名：AVSessionController；<br>API声明：readonly sessionId: string;<br>差异内容：readonly sessionId: string;|api/@ohos.multimedia.avsession.d.ts|
|新增API|NA|类名：AVSessionController；<br>API声明：getAVPlaybackState(callback: AsyncCallback\<AVPlaybackState>): void;<br>差异内容：getAVPlaybackState(callback: AsyncCallback\<AVPlaybackState>): void;|api/@ohos.multimedia.avsession.d.ts|
|新增API|NA|类名：AVSessionController；<br>API声明：getAVPlaybackState(): Promise\<AVPlaybackState>;<br>差异内容：getAVPlaybackState(): Promise\<AVPlaybackState>;|api/@ohos.multimedia.avsession.d.ts|
|新增API|NA|类名：AVSessionController；<br>API声明：getAVPlaybackStateSync(): AVPlaybackState;<br>差异内容：getAVPlaybackStateSync(): AVPlaybackState;|api/@ohos.multimedia.avsession.d.ts|
|新增API|NA|类名：AVSessionController；<br>API声明：getAVMetadata(callback: AsyncCallback\<AVMetadata>): void;<br>差异内容：getAVMetadata(callback: AsyncCallback\<AVMetadata>): void;|api/@ohos.multimedia.avsession.d.ts|
|新增API|NA|类名：AVSessionController；<br>API声明：getAVMetadata(): Promise\<AVMetadata>;<br>差异内容：getAVMetadata(): Promise\<AVMetadata>;|api/@ohos.multimedia.avsession.d.ts|
|新增API|NA|类名：AVSessionController；<br>API声明：getAVMetadataSync(): AVMetadata;<br>差异内容：getAVMetadataSync(): AVMetadata;|api/@ohos.multimedia.avsession.d.ts|
|新增API|NA|类名：AVSessionController；<br>API声明：getAVCallState(callback: AsyncCallback\<AVCallState>): void;<br>差异内容：getAVCallState(callback: AsyncCallback\<AVCallState>): void;|api/@ohos.multimedia.avsession.d.ts|
|新增API|NA|类名：AVSessionController；<br>API声明：getAVCallState(): Promise\<AVCallState>;<br>差异内容：getAVCallState(): Promise\<AVCallState>;|api/@ohos.multimedia.avsession.d.ts|
|新增API|NA|类名：AVSessionController；<br>API声明：getCallMetadata(callback: AsyncCallback\<CallMetadata>): void;<br>差异内容：getCallMetadata(callback: AsyncCallback\<CallMetadata>): void;|api/@ohos.multimedia.avsession.d.ts|
|新增API|NA|类名：AVSessionController；<br>API声明：getCallMetadata(): Promise\<CallMetadata>;<br>差异内容：getCallMetadata(): Promise\<CallMetadata>;|api/@ohos.multimedia.avsession.d.ts|
|新增API|NA|类名：AVSessionController；<br>API声明：getAVQueueTitle(callback: AsyncCallback\<string>): void;<br>差异内容：getAVQueueTitle(callback: AsyncCallback\<string>): void;|api/@ohos.multimedia.avsession.d.ts|
|新增API|NA|类名：AVSessionController；<br>API声明：getAVQueueTitle(): Promise\<string>;<br>差异内容：getAVQueueTitle(): Promise\<string>;|api/@ohos.multimedia.avsession.d.ts|
|新增API|NA|类名：AVSessionController；<br>API声明：getAVQueueTitleSync(): string;<br>差异内容：getAVQueueTitleSync(): string;|api/@ohos.multimedia.avsession.d.ts|
|新增API|NA|类名：AVSessionController；<br>API声明：getAVQueueItems(callback: AsyncCallback\<Array\<AVQueueItem>>): void;<br>差异内容：getAVQueueItems(callback: AsyncCallback\<Array\<AVQueueItem>>): void;|api/@ohos.multimedia.avsession.d.ts|
|新增API|NA|类名：AVSessionController；<br>API声明：getAVQueueItems(): Promise\<Array\<AVQueueItem>>;<br>差异内容：getAVQueueItems(): Promise\<Array\<AVQueueItem>>;|api/@ohos.multimedia.avsession.d.ts|
|新增API|NA|类名：AVSessionController；<br>API声明：getAVQueueItemsSync(): Array\<AVQueueItem>;<br>差异内容：getAVQueueItemsSync(): Array\<AVQueueItem>;|api/@ohos.multimedia.avsession.d.ts|
|新增API|NA|类名：AVSessionController；<br>API声明：skipToQueueItem(itemId: number, callback: AsyncCallback\<void>): void;<br>差异内容：skipToQueueItem(itemId: number, callback: AsyncCallback\<void>): void;|api/@ohos.multimedia.avsession.d.ts|
|新增API|NA|类名：AVSessionController；<br>API声明：skipToQueueItem(itemId: number): Promise\<void>;<br>差异内容：skipToQueueItem(itemId: number): Promise\<void>;|api/@ohos.multimedia.avsession.d.ts|
|新增API|NA|类名：AVSessionController；<br>API声明：getOutputDevice(callback: AsyncCallback\<OutputDeviceInfo>): void;<br>差异内容：getOutputDevice(callback: AsyncCallback\<OutputDeviceInfo>): void;|api/@ohos.multimedia.avsession.d.ts|
|新增API|NA|类名：AVSessionController；<br>API声明：getOutputDevice(): Promise\<OutputDeviceInfo>;<br>差异内容：getOutputDevice(): Promise\<OutputDeviceInfo>;|api/@ohos.multimedia.avsession.d.ts|
|新增API|NA|类名：AVSessionController；<br>API声明：getOutputDeviceSync(): OutputDeviceInfo;<br>差异内容：getOutputDeviceSync(): OutputDeviceInfo;|api/@ohos.multimedia.avsession.d.ts|
|新增API|NA|类名：AVSessionController；<br>API声明：sendAVKeyEvent(event: KeyEvent, callback: AsyncCallback\<void>): void;<br>差异内容：sendAVKeyEvent(event: KeyEvent, callback: AsyncCallback\<void>): void;|api/@ohos.multimedia.avsession.d.ts|
|新增API|NA|类名：AVSessionController；<br>API声明：sendAVKeyEvent(event: KeyEvent): Promise\<void>;<br>差异内容：sendAVKeyEvent(event: KeyEvent): Promise\<void>;|api/@ohos.multimedia.avsession.d.ts|
|新增API|NA|类名：AVSessionController；<br>API声明：getLaunchAbility(callback: AsyncCallback\<WantAgent>): void;<br>差异内容：getLaunchAbility(callback: AsyncCallback\<WantAgent>): void;|api/@ohos.multimedia.avsession.d.ts|
|新增API|NA|类名：AVSessionController；<br>API声明：getLaunchAbility(): Promise\<WantAgent>;<br>差异内容：getLaunchAbility(): Promise\<WantAgent>;|api/@ohos.multimedia.avsession.d.ts|
|新增API|NA|类名：AVSessionController；<br>API声明：getRealPlaybackPositionSync(): number;<br>差异内容：getRealPlaybackPositionSync(): number;|api/@ohos.multimedia.avsession.d.ts|
|新增API|NA|类名：AVSessionController；<br>API声明：isActive(callback: AsyncCallback\<boolean>): void;<br>差异内容：isActive(callback: AsyncCallback\<boolean>): void;|api/@ohos.multimedia.avsession.d.ts|
|新增API|NA|类名：AVSessionController；<br>API声明：isActive(): Promise\<boolean>;<br>差异内容：isActive(): Promise\<boolean>;|api/@ohos.multimedia.avsession.d.ts|
|新增API|NA|类名：AVSessionController；<br>API声明：isActiveSync(): boolean;<br>差异内容：isActiveSync(): boolean;|api/@ohos.multimedia.avsession.d.ts|
|新增API|NA|类名：AVSessionController；<br>API声明：destroy(callback: AsyncCallback\<void>): void;<br>差异内容：destroy(callback: AsyncCallback\<void>): void;|api/@ohos.multimedia.avsession.d.ts|
|新增API|NA|类名：AVSessionController；<br>API声明：destroy(): Promise\<void>;<br>差异内容：destroy(): Promise\<void>;|api/@ohos.multimedia.avsession.d.ts|
|新增API|NA|类名：AVSessionController；<br>API声明：getValidCommands(callback: AsyncCallback\<Array\<AVControlCommandType>>): void;<br>差异内容：getValidCommands(callback: AsyncCallback\<Array\<AVControlCommandType>>): void;|api/@ohos.multimedia.avsession.d.ts|
|新增API|NA|类名：AVSessionController；<br>API声明：getValidCommands(): Promise\<Array\<AVControlCommandType>>;<br>差异内容：getValidCommands(): Promise\<Array\<AVControlCommandType>>;|api/@ohos.multimedia.avsession.d.ts|
|新增API|NA|类名：AVSessionController；<br>API声明：getValidCommandsSync(): Array\<AVControlCommandType>;<br>差异内容：getValidCommandsSync(): Array\<AVControlCommandType>;|api/@ohos.multimedia.avsession.d.ts|
|新增API|NA|类名：AVSessionController；<br>API声明：sendControlCommand(command: AVControlCommand, callback: AsyncCallback\<void>): void;<br>差异内容：sendControlCommand(command: AVControlCommand, callback: AsyncCallback\<void>): void;|api/@ohos.multimedia.avsession.d.ts|
|新增API|NA|类名：AVSessionController；<br>API声明：sendControlCommand(command: AVControlCommand): Promise\<void>;<br>差异内容：sendControlCommand(command: AVControlCommand): Promise\<void>;|api/@ohos.multimedia.avsession.d.ts|
|新增API|NA|类名：AVSessionController；<br>API声明：sendCommonCommand(command: string, args: {<br>            [key: string]: Object;<br>        }, callback: AsyncCallback\<void>): void;<br>差异内容：sendCommonCommand(command: string, args: {<br>            [key: string]: Object;<br>        }, callback: AsyncCallback\<void>): void;|api/@ohos.multimedia.avsession.d.ts|
|新增API|NA|类名：AVSessionController；<br>API声明：sendCommonCommand(command: string, args: {<br>            [key: string]: Object;<br>        }): Promise\<void>;<br>差异内容：sendCommonCommand(command: string, args: {<br>            [key: string]: Object;<br>        }): Promise\<void>;|api/@ohos.multimedia.avsession.d.ts|
|新增API|NA|类名：AVSessionController；<br>API声明：getExtras(callback: AsyncCallback\<{<br>            [key: string]: Object;<br>        }>): void;<br>差异内容：getExtras(callback: AsyncCallback\<{<br>            [key: string]: Object;<br>        }>): void;|api/@ohos.multimedia.avsession.d.ts|
|新增API|NA|类名：AVSessionController；<br>API声明：getExtras(): Promise\<{<br>            [key: string]: Object;<br>        }>;<br>差异内容：getExtras(): Promise\<{<br>            [key: string]: Object;<br>        }>;|api/@ohos.multimedia.avsession.d.ts|
|新增API|NA|类名：AVSessionController；<br>API声明：on(type: 'metadataChange', filter: Array\<keyof AVMetadata> \| 'all', callback: (data: AVMetadata) => void);<br>差异内容：on(type: 'metadataChange', filter: Array\<keyof AVMetadata> \| 'all', callback: (data: AVMetadata) => void);|api/@ohos.multimedia.avsession.d.ts|
|新增API|NA|类名：AVSessionController；<br>API声明：off(type: 'metadataChange', callback?: (data: AVMetadata) => void);<br>差异内容：off(type: 'metadataChange', callback?: (data: AVMetadata) => void);|api/@ohos.multimedia.avsession.d.ts|
|新增API|NA|类名：AVSessionController；<br>API声明：on(type: 'playbackStateChange', filter: Array\<keyof AVPlaybackState> \| 'all', callback: (state: AVPlaybackState) => void);<br>差异内容：on(type: 'playbackStateChange', filter: Array\<keyof AVPlaybackState> \| 'all', callback: (state: AVPlaybackState) => void);|api/@ohos.multimedia.avsession.d.ts|
|新增API|NA|类名：AVSessionController；<br>API声明：off(type: 'playbackStateChange', callback?: (state: AVPlaybackState) => void);<br>差异内容：off(type: 'playbackStateChange', callback?: (state: AVPlaybackState) => void);|api/@ohos.multimedia.avsession.d.ts|
|新增API|NA|类名：AVSessionController；<br>API声明：on(type: 'callMetadataChange', filter: Array\<keyof CallMetadata> \| 'all', callback: Callback\<CallMetadata>): void;<br>差异内容：on(type: 'callMetadataChange', filter: Array\<keyof CallMetadata> \| 'all', callback: Callback\<CallMetadata>): void;|api/@ohos.multimedia.avsession.d.ts|
|新增API|NA|类名：AVSessionController；<br>API声明：off(type: 'callMetadataChange', callback?: Callback\<CallMetadata>): void;<br>差异内容：off(type: 'callMetadataChange', callback?: Callback\<CallMetadata>): void;|api/@ohos.multimedia.avsession.d.ts|
|新增API|NA|类名：AVSessionController；<br>API声明：on(type: 'callStateChange', filter: Array\<keyof AVCallState> \| 'all', callback: Callback\<AVCallState>): void;<br>差异内容：on(type: 'callStateChange', filter: Array\<keyof AVCallState> \| 'all', callback: Callback\<AVCallState>): void;|api/@ohos.multimedia.avsession.d.ts|
|新增API|NA|类名：AVSessionController；<br>API声明：off(type: 'callStateChange', callback?: Callback\<AVCallState>): void;<br>差异内容：off(type: 'callStateChange', callback?: Callback\<AVCallState>): void;|api/@ohos.multimedia.avsession.d.ts|
|新增API|NA|类名：AVSessionController；<br>API声明：on(type: 'sessionDestroy', callback: () => void);<br>差异内容：on(type: 'sessionDestroy', callback: () => void);|api/@ohos.multimedia.avsession.d.ts|
|新增API|NA|类名：AVSessionController；<br>API声明：off(type: 'sessionDestroy', callback?: () => void);<br>差异内容：off(type: 'sessionDestroy', callback?: () => void);|api/@ohos.multimedia.avsession.d.ts|
|新增API|NA|类名：AVSessionController；<br>API声明：on(type: 'activeStateChange', callback: (isActive: boolean) => void);<br>差异内容：on(type: 'activeStateChange', callback: (isActive: boolean) => void);|api/@ohos.multimedia.avsession.d.ts|
|新增API|NA|类名：AVSessionController；<br>API声明：off(type: 'activeStateChange', callback?: (isActive: boolean) => void);<br>差异内容：off(type: 'activeStateChange', callback?: (isActive: boolean) => void);|api/@ohos.multimedia.avsession.d.ts|
|新增API|NA|类名：AVSessionController；<br>API声明：on(type: 'validCommandChange', callback: (commands: Array\<AVControlCommandType>) => void);<br>差异内容：on(type: 'validCommandChange', callback: (commands: Array\<AVControlCommandType>) => void);|api/@ohos.multimedia.avsession.d.ts|
|新增API|NA|类名：AVSessionController；<br>API声明：off(type: 'validCommandChange', callback?: (commands: Array\<AVControlCommandType>) => void);<br>差异内容：off(type: 'validCommandChange', callback?: (commands: Array\<AVControlCommandType>) => void);|api/@ohos.multimedia.avsession.d.ts|
|新增API|NA|类名：AVSessionController；<br>API声明：on(type: 'outputDeviceChange', callback: (state: ConnectionState, device: OutputDeviceInfo) => void): void;<br>差异内容：on(type: 'outputDeviceChange', callback: (state: ConnectionState, device: OutputDeviceInfo) => void): void;|api/@ohos.multimedia.avsession.d.ts|
|新增API|NA|类名：AVSessionController；<br>API声明：off(type: 'outputDeviceChange', callback?: (state: ConnectionState, device: OutputDeviceInfo) => void): void;<br>差异内容：off(type: 'outputDeviceChange', callback?: (state: ConnectionState, device: OutputDeviceInfo) => void): void;|api/@ohos.multimedia.avsession.d.ts|
|新增API|NA|类名：AVSessionController；<br>API声明：on(type: 'sessionEvent', callback: (sessionEvent: string, args: {<br>            [key: string]: Object;<br>        }) => void): void;<br>差异内容：on(type: 'sessionEvent', callback: (sessionEvent: string, args: {<br>            [key: string]: Object;<br>        }) => void): void;|api/@ohos.multimedia.avsession.d.ts|
|新增API|NA|类名：AVSessionController；<br>API声明：off(type: 'sessionEvent', callback?: (sessionEvent: string, args: {<br>            [key: string]: Object;<br>        }) => void): void;<br>差异内容：off(type: 'sessionEvent', callback?: (sessionEvent: string, args: {<br>            [key: string]: Object;<br>        }) => void): void;|api/@ohos.multimedia.avsession.d.ts|
|新增API|NA|类名：AVSessionController；<br>API声明：on(type: 'queueItemsChange', callback: (items: Array\<AVQueueItem>) => void): void;<br>差异内容：on(type: 'queueItemsChange', callback: (items: Array\<AVQueueItem>) => void): void;|api/@ohos.multimedia.avsession.d.ts|
|新增API|NA|类名：AVSessionController；<br>API声明：off(type: 'queueItemsChange', callback?: (items: Array\<AVQueueItem>) => void): void;<br>差异内容：off(type: 'queueItemsChange', callback?: (items: Array\<AVQueueItem>) => void): void;|api/@ohos.multimedia.avsession.d.ts|
|新增API|NA|类名：AVSessionController；<br>API声明：on(type: 'queueTitleChange', callback: (title: string) => void): void;<br>差异内容：on(type: 'queueTitleChange', callback: (title: string) => void): void;|api/@ohos.multimedia.avsession.d.ts|
|新增API|NA|类名：AVSessionController；<br>API声明：off(type: 'queueTitleChange', callback?: (title: string) => void): void;<br>差异内容：off(type: 'queueTitleChange', callback?: (title: string) => void): void;|api/@ohos.multimedia.avsession.d.ts|
|新增API|NA|类名：AVSessionController；<br>API声明：on(type: 'extrasChange', callback: (extras: {<br>            [key: string]: Object;<br>        }) => void): void;<br>差异内容：on(type: 'extrasChange', callback: (extras: {<br>            [key: string]: Object;<br>        }) => void): void;|api/@ohos.multimedia.avsession.d.ts|
|新增API|NA|类名：AVSessionController；<br>API声明：off(type: 'extrasChange', callback?: (extras: {<br>            [key: string]: Object;<br>        }) => void): void;<br>差异内容：off(type: 'extrasChange', callback?: (extras: {<br>            [key: string]: Object;<br>        }) => void): void;|api/@ohos.multimedia.avsession.d.ts|
|新增API|NA|类名：avSession；<br>API声明：type AVControlCommandType = 'play' \| 'pause' \| 'stop' \| 'playNext' \| 'playPrevious' \| 'fastForward' \| 'rewind' \| 'seek' \| 'setSpeed' \| 'setLoopMode' \| 'toggleFavorite' \| 'playFromAssetId' \| 'answer' \| 'hangUp' \| 'toggleCallMute';<br>差异内容：type AVControlCommandType = 'play' \| 'pause' \| 'stop' \| 'playNext' \| 'playPrevious' \| 'fastForward' \| 'rewind' \| 'seek' \| 'setSpeed' \| 'setLoopMode' \| 'toggleFavorite' \| 'playFromAssetId' \| 'answer' \| 'hangUp' \| 'toggleCallMute';|api/@ohos.multimedia.avsession.d.ts|
|新增API|NA|类名：avSession；<br>API声明：interface AVControlCommand<br>差异内容：interface AVControlCommand|api/@ohos.multimedia.avsession.d.ts|
|新增API|NA|类名：AVControlCommand；<br>API声明：command: AVControlCommandType;<br>差异内容：command: AVControlCommandType;|api/@ohos.multimedia.avsession.d.ts|
|新增API|NA|类名：AVControlCommand；<br>API声明：parameter?: LoopMode \| string \| number;<br>差异内容：parameter?: LoopMode \| string \| number;|api/@ohos.multimedia.avsession.d.ts|
|新增API|NA|类名：avSession；<br>API声明：enum AVSessionErrorCode<br>差异内容：enum AVSessionErrorCode|api/@ohos.multimedia.avsession.d.ts|
|新增API|NA|类名：AVSessionErrorCode；<br>API声明：ERR_CODE_SERVICE_EXCEPTION = 6600101<br>差异内容：ERR_CODE_SERVICE_EXCEPTION = 6600101|api/@ohos.multimedia.avsession.d.ts|
|新增API|NA|类名：AVSessionErrorCode；<br>API声明：ERR_CODE_SESSION_NOT_EXIST = 6600102<br>差异内容：ERR_CODE_SESSION_NOT_EXIST = 6600102|api/@ohos.multimedia.avsession.d.ts|
|新增API|NA|类名：AVSessionErrorCode；<br>API声明：ERR_CODE_CONTROLLER_NOT_EXIST = 6600103<br>差异内容：ERR_CODE_CONTROLLER_NOT_EXIST = 6600103|api/@ohos.multimedia.avsession.d.ts|
|新增API|NA|类名：AVSessionErrorCode；<br>API声明：ERR_CODE_REMOTE_CONNECTION_ERR = 6600104<br>差异内容：ERR_CODE_REMOTE_CONNECTION_ERR = 6600104|api/@ohos.multimedia.avsession.d.ts|
|新增API|NA|类名：AVSessionErrorCode；<br>API声明：ERR_CODE_COMMAND_INVALID = 6600105<br>差异内容：ERR_CODE_COMMAND_INVALID = 6600105|api/@ohos.multimedia.avsession.d.ts|
|新增API|NA|类名：AVSessionErrorCode；<br>API声明：ERR_CODE_SESSION_INACTIVE = 6600106<br>差异内容：ERR_CODE_SESSION_INACTIVE = 6600106|api/@ohos.multimedia.avsession.d.ts|
|新增API|NA|类名：AVSessionErrorCode；<br>API声明：ERR_CODE_MESSAGE_OVERLOAD = 6600107<br>差异内容：ERR_CODE_MESSAGE_OVERLOAD = 6600107|api/@ohos.multimedia.avsession.d.ts|
|新增API|NA|类名：AVSessionErrorCode；<br>API声明：ERR_CODE_DEVICE_CONNECTION_FAILED = 6600108<br>差异内容：ERR_CODE_DEVICE_CONNECTION_FAILED = 6600108|api/@ohos.multimedia.avsession.d.ts|
|新增API|NA|类名：AVSessionErrorCode；<br>API声明：ERR_CODE_REMOTE_CONNECTION_NOT_EXIST = 6600109<br>差异内容：ERR_CODE_REMOTE_CONNECTION_NOT_EXIST = 6600109|api/@ohos.multimedia.avsession.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\@ohos.multimedia.avCastPicker.d.ets<br>差异内容：AVSessionKit|api/@ohos.multimedia.avCastPicker.d.ets|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\@ohos.multimedia.avCastPickerParam.d.ts<br>差异内容：AVSessionKit|api/@ohos.multimedia.avCastPickerParam.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\@ohos.multimedia.avsession.d.ts<br>差异内容：AVSessionKit|api/@ohos.multimedia.avsession.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：kits\@kit.AVSessionKit.d.ts<br>差异内容：AVSessionKit|kits/@kit.AVSessionKit.d.ts|
