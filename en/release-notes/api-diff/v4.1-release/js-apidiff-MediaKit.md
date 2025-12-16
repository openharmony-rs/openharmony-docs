| Change Type | Old Version | New Version | d.ts File |
| ---- | ------ | ------ | -------- |
|New API |NA|Class name: global;<br>API declaration: declare namespace media<br>Differences: declare namespace media|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: media;<br>API declaration: function createAVPlayer(callback: AsyncCallback\<AVPlayer>): void;<br>Differences: function createAVPlayer(callback: AsyncCallback\<AVPlayer>): void;|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: media;<br>API declaration: function createAVPlayer(): Promise\<AVPlayer>;<br>Differences: function createAVPlayer(): Promise\<AVPlayer>;|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: media;<br>API declaration: function createAVRecorder(callback: AsyncCallback\<AVRecorder>): void;<br>Differences: function createAVRecorder(callback: AsyncCallback\<AVRecorder>): void;|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: media;<br>API declaration: function createAVRecorder(): Promise\<AVRecorder>;<br>Differences: function createAVRecorder(): Promise\<AVRecorder>;|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: media;<br>API declaration: function createAudioPlayer(): AudioPlayer;<br>Differences: function createAudioPlayer(): AudioPlayer;|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: media;<br>API declaration: function createAudioRecorder(): AudioRecorder;<br>Differences: function createAudioRecorder(): AudioRecorder;|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: media;<br>API declaration: function createVideoPlayer(callback: AsyncCallback\<VideoPlayer>): void;<br>Differences: function createVideoPlayer(callback: AsyncCallback\<VideoPlayer>): void;|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: media;<br>API declaration: function createVideoPlayer(): Promise\<VideoPlayer>;<br>Differences: function createVideoPlayer(): Promise\<VideoPlayer>;|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: media;<br>API declaration: function createSoundPool(maxStreams: number, audioRenderInfo: audio.AudioRendererInfo, callback: AsyncCallback\<SoundPool>): void;<br>Differences: function createSoundPool(maxStreams: number, audioRenderInfo: audio.AudioRendererInfo, callback: AsyncCallback\<SoundPool>): void;|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: media;<br>API declaration: function createSoundPool(maxStreams: number, audioRenderInfo: audio.AudioRendererInfo): Promise\<SoundPool>;<br>Differences: function createSoundPool(maxStreams: number, audioRenderInfo: audio.AudioRendererInfo): Promise\<SoundPool>;|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: media;<br>API declaration: type SoundPool = _SoundPool;<br>Differences: type SoundPool = _SoundPool;|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: media;<br>API declaration: type PlayParameters = _PlayParameters;<br>Differences: type PlayParameters = _PlayParameters;|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: media;<br>API declaration: enum StateChangeReason<br>Differences: enum StateChangeReason|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: StateChangeReason;<br>API declaration: USER = 1<br>Differences: USER = 1|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: StateChangeReason;<br>API declaration: BACKGROUND = 2<br>Differences: BACKGROUND = 2|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: media;<br>API declaration: function createAVMetadataExtractor(): Promise\<AVMetadataExtractor>;<br>Differences: function createAVMetadataExtractor(): Promise\<AVMetadataExtractor>;|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: media;<br>API declaration: function createAVMetadataExtractor(callback: AsyncCallback\<AVMetadataExtractor>): void;<br>Differences: function createAVMetadataExtractor(callback: AsyncCallback\<AVMetadataExtractor>): void;|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: media;<br>API declaration: interface AVMetadataExtractor<br>Differences: interface AVMetadataExtractor|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: AVMetadataExtractor;<br>API declaration: fdSrc?: AVFileDescriptor;<br>Differences: fdSrc?: AVFileDescriptor;|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: AVMetadataExtractor;<br>API declaration: dataSrc?: AVDataSrcDescriptor;<br>Differences: dataSrc?: AVDataSrcDescriptor;|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: AVMetadataExtractor;<br>API declaration: fetchMetadata(callback: AsyncCallback\<AVMetadata>): void;<br>Differences: fetchMetadata(callback: AsyncCallback\<AVMetadata>): void;|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: AVMetadataExtractor;<br>API declaration: fetchMetadata(): Promise\<AVMetadata>;<br>Differences: fetchMetadata(): Promise\<AVMetadata>;|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: AVMetadataExtractor;<br>API declaration: fetchAlbumCover(callback: AsyncCallback\<image.PixelMap>): void;<br>Differences: fetchAlbumCover(callback: AsyncCallback\<image.PixelMap>): void;|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: AVMetadataExtractor;<br>API declaration: fetchAlbumCover(): Promise\<image.PixelMap>;<br>Differences: fetchAlbumCover(): Promise\<image.PixelMap>;|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: AVMetadataExtractor;<br>API declaration: release(callback: AsyncCallback\<void>): void;<br>Differences: release(callback: AsyncCallback\<void>): void;|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: AVMetadataExtractor;<br>API declaration: release(): Promise\<void>;<br>Differences: release(): Promise\<void>;|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: media;<br>API declaration: interface AVMetadata<br>Differences: interface AVMetadata|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: AVMetadata;<br>API declaration: album?: string;<br>Differences: album?: string;|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: AVMetadata;<br>API declaration: albumArtist?: string;<br>Differences: albumArtist?: string;|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: AVMetadata;<br>API declaration: artist?: string;<br>Differences: artist?: string;|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: AVMetadata;<br>API declaration: author?: string;<br>Differences: author?: string;|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: AVMetadata;<br>API declaration: dateTime?: string;<br>Differences: dateTime?: string;|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: AVMetadata;<br>API declaration: dateTimeFormat?: string;<br>Differences: dateTimeFormat?: string;|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: AVMetadata;<br>API declaration: composer?: string;<br>Differences: composer?: string;|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: AVMetadata;<br>API declaration: duration?: string;<br>Differences: duration?: string;|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: AVMetadata;<br>API declaration: genre?: string;<br>Differences: genre?: string;|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: AVMetadata;<br>API declaration: hasAudio?: string;<br>Differences: hasAudio?: string;|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: AVMetadata;<br>API declaration: hasVideo?: string;<br>Differences: hasVideo?: string;|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: AVMetadata;<br>API declaration: mimeType?: string;<br>Differences: mimeType?: string;|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: AVMetadata;<br>API declaration: trackCount?: string;<br>Differences: trackCount?: string;|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: AVMetadata;<br>API declaration: sampleRate?: string;<br>Differences: sampleRate?: string;|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: AVMetadata;<br>API declaration: title?: string;<br>Differences: title?: string;|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: AVMetadata;<br>API declaration: videoHeight?: string;<br>Differences: videoHeight?: string;|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: AVMetadata;<br>API declaration: videoWidth?: string;<br>Differences: videoWidth?: string;|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: AVMetadata;<br>API declaration: videoOrientation?: string;<br>Differences: videoOrientation?: string;|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: media;<br>API declaration: enum AVErrorCode<br>Differences: enum AVErrorCode|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: AVErrorCode;<br>API declaration: AVERR_OK = 0<br>Differences: AVERR_OK = 0|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: AVErrorCode;<br>API declaration: AVERR_NO_PERMISSION = 201<br>Differences: AVERR_NO_PERMISSION = 201|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: AVErrorCode;<br>API declaration: AVERR_INVALID_PARAMETER = 401<br>Differences: AVERR_INVALID_PARAMETER = 401|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: AVErrorCode;<br>API declaration: AVERR_UNSUPPORT_CAPABILITY = 801<br>Differences: AVERR_UNSUPPORT_CAPABILITY = 801|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: AVErrorCode;<br>API declaration: AVERR_NO_MEMORY = 5400101<br>Differences: AVERR_NO_MEMORY = 5400101|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: AVErrorCode;<br>API declaration: AVERR_OPERATE_NOT_PERMIT = 5400102<br>Differences: AVERR_OPERATE_NOT_PERMIT = 5400102|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: AVErrorCode;<br>API declaration: AVERR_IO = 5400103<br>Differences: AVERR_IO = 5400103|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: AVErrorCode;<br>API declaration: AVERR_TIMEOUT = 5400104<br>Differences: AVERR_TIMEOUT = 5400104|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: AVErrorCode;<br>API declaration: AVERR_SERVICE_DIED = 5400105<br>Differences: AVERR_SERVICE_DIED = 5400105|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: AVErrorCode;<br>API declaration: AVERR_UNSUPPORT_FORMAT = 5400106<br>Differences: AVERR_UNSUPPORT_FORMAT = 5400106|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: AVErrorCode;<br>API declaration: AVERR_AUDIO_INTERRUPTED = 5400107<br>Differences: AVERR_AUDIO_INTERRUPTED = 5400107|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: media;<br>API declaration: type AVPlayerState = 'idle' \| 'initialized' \| 'prepared' \| 'playing' \| 'paused' \| 'completed' \| 'stopped' \| 'released' \| 'error';<br>Differences: type AVPlayerState = 'idle' \| 'initialized' \| 'prepared' \| 'playing' \| 'paused' \| 'completed' \| 'stopped' \| 'released' \| 'error';|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: media;<br>API declaration: interface AVPlayer<br>Differences: interface AVPlayer|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: AVPlayer;<br>API declaration: prepare(callback: AsyncCallback\<void>): void;<br>Differences: prepare(callback: AsyncCallback\<void>): void;|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: AVPlayer;<br>API declaration: prepare(): Promise\<void>;<br>Differences: prepare(): Promise\<void>;|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: AVPlayer;<br>API declaration: play(callback: AsyncCallback\<void>): void;<br>Differences: play(callback: AsyncCallback\<void>): void;|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: AVPlayer;<br>API declaration: play(): Promise\<void>;<br>Differences: play(): Promise\<void>;|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: AVPlayer;<br>API declaration: pause(callback: AsyncCallback\<void>): void;<br>Differences: pause(callback: AsyncCallback\<void>): void;|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: AVPlayer;<br>API declaration: pause(): Promise\<void>;<br>Differences: pause(): Promise\<void>;|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: AVPlayer;<br>API declaration: stop(callback: AsyncCallback\<void>): void;<br>Differences: stop(callback: AsyncCallback\<void>): void;|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: AVPlayer;<br>API declaration: stop(): Promise\<void>;<br>Differences: stop(): Promise\<void>;|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: AVPlayer;<br>API declaration: reset(callback: AsyncCallback\<void>): void;<br>Differences: reset(callback: AsyncCallback\<void>): void;|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: AVPlayer;<br>API declaration: reset(): Promise\<void>;<br>Differences: reset(): Promise\<void>;|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: AVPlayer;<br>API declaration: release(callback: AsyncCallback\<void>): void;<br>Differences: release(callback: AsyncCallback\<void>): void;|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: AVPlayer;<br>API declaration: release(): Promise\<void>;<br>Differences: release(): Promise\<void>;|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: AVPlayer;<br>API declaration: seek(timeMs: number, mode?: SeekMode): void;<br>Differences: seek(timeMs: number, mode?: SeekMode): void;|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: AVPlayer;<br>API declaration: setVolume(volume: number): void;<br>Differences: setVolume(volume: number): void;|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: AVPlayer;<br>API declaration: getTrackDescription(callback: AsyncCallback\<Array\<MediaDescription>>): void;<br>Differences: getTrackDescription(callback: AsyncCallback\<Array\<MediaDescription>>): void;|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: AVPlayer;<br>API declaration: getTrackDescription(): Promise\<Array\<MediaDescription>>;<br>Differences: getTrackDescription(): Promise\<Array\<MediaDescription>>;|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: AVPlayer;<br>API declaration: url?: string;<br>Differences: url?: string;|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: AVPlayer;<br>API declaration: fdSrc?: AVFileDescriptor;<br>Differences: fdSrc?: AVFileDescriptor;|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: AVPlayer;<br>API declaration: dataSrc?: AVDataSrcDescriptor;<br>Differences: dataSrc?: AVDataSrcDescriptor;|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: AVPlayer;<br>API declaration: loop: boolean;<br>Differences: loop: boolean;|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: AVPlayer;<br>API declaration: audioInterruptMode?: audio.InterruptMode;<br>Differences: audioInterruptMode?: audio.InterruptMode;|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: AVPlayer;<br>API declaration: audioRendererInfo?: audio.AudioRendererInfo;<br>Differences: audioRendererInfo?: audio.AudioRendererInfo;|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: AVPlayer;<br>API declaration: audioEffectMode?: audio.AudioEffectMode;<br>Differences: audioEffectMode?: audio.AudioEffectMode;|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: AVPlayer;<br>API declaration: readonly currentTime: number;<br>Differences: readonly currentTime: number;|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: AVPlayer;<br>API declaration: readonly duration: number;<br>Differences: readonly duration: number;|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: AVPlayer;<br>API declaration: readonly state: AVPlayerState;<br>Differences: readonly state: AVPlayerState;|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: AVPlayer;<br>API declaration: surfaceId?: string;<br>Differences: surfaceId?: string;|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: AVPlayer;<br>API declaration: readonly width: number;<br>Differences: readonly width: number;|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: AVPlayer;<br>API declaration: readonly height: number;<br>Differences: readonly height: number;|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: AVPlayer;<br>API declaration: videoScaleType?: VideoScaleType;<br>Differences: videoScaleType?: VideoScaleType;|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: AVPlayer;<br>API declaration: setSpeed(speed: PlaybackSpeed): void;<br>Differences: setSpeed(speed: PlaybackSpeed): void;|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: AVPlayer;<br>API declaration: setBitrate(bitrate: number): void;<br>Differences: setBitrate(bitrate: number): void;|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: AVPlayer;<br>API declaration: setDecryptionConfig(mediaKeySession: drm.MediaKeySession, secureVideoPath: boolean): void;<br>Differences: setDecryptionConfig(mediaKeySession: drm.MediaKeySession, secureVideoPath: boolean): void;|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: AVPlayer;<br>API declaration: getMediaKeySystemInfos(): Array\<drm.MediaKeySystemInfo>;<br>Differences: getMediaKeySystemInfos(): Array\<drm.MediaKeySystemInfo>;|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: AVPlayer;<br>API declaration: on(type: 'mediaKeySystemInfoUpdate', callback: (mediaKeySystemInfo: Array\<drm.MediaKeySystemInfo>) => void): void;<br>Differences: on(type: 'mediaKeySystemInfoUpdate', callback: (mediaKeySystemInfo: Array\<drm.MediaKeySystemInfo>) => void): void;|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: AVPlayer;<br>API declaration: off(type: 'mediaKeySystemInfoUpdate', callback?: (mediaKeySystemInfo: Array\<drm.MediaKeySystemInfo>) => void): void;<br>Differences: off(type: 'mediaKeySystemInfoUpdate', callback?: (mediaKeySystemInfo: Array\<drm.MediaKeySystemInfo>) => void): void;|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: AVPlayer;<br>API declaration: on(type: 'stateChange', callback: (state: AVPlayerState, reason: StateChangeReason) => void): void;<br>Differences: on(type: 'stateChange', callback: (state: AVPlayerState, reason: StateChangeReason) => void): void;|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: AVPlayer;<br>API declaration: off(type: 'stateChange'): void;<br>Differences: off(type: 'stateChange'): void;|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: AVPlayer;<br>API declaration: on(type: 'volumeChange', callback: Callback\<number>): void;<br>Differences: on(type: 'volumeChange', callback: Callback\<number>): void;|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: AVPlayer;<br>API declaration: off(type: 'volumeChange'): void;<br>Differences: off(type: 'volumeChange'): void;|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: AVPlayer;<br>API declaration: on(type: 'endOfStream', callback: Callback\<void>): void;<br>Differences: on(type: 'endOfStream', callback: Callback\<void>): void;|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: AVPlayer;<br>API declaration: off(type: 'endOfStream'): void;<br>Differences: off(type: 'endOfStream'): void;|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: AVPlayer;<br>API declaration: on(type: 'seekDone', callback: Callback\<number>): void;<br>Differences: on(type: 'seekDone', callback: Callback\<number>): void;|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: AVPlayer;<br>API declaration: off(type: 'seekDone'): void;<br>Differences: off(type: 'seekDone'): void;|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: AVPlayer;<br>API declaration: on(type: 'speedDone', callback: Callback\<number>): void;<br>Differences: on(type: 'speedDone', callback: Callback\<number>): void;|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: AVPlayer;<br>API declaration: off(type: 'speedDone'): void;<br>Differences: off(type: 'speedDone'): void;|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: AVPlayer;<br>API declaration: on(type: 'bitrateDone', callback: Callback\<number>): void;<br>Differences: on(type: 'bitrateDone', callback: Callback\<number>): void;|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: AVPlayer;<br>API declaration: off(type: 'bitrateDone'): void;<br>Differences: off(type: 'bitrateDone'): void;|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: AVPlayer;<br>API declaration: on(type: 'timeUpdate', callback: Callback\<number>): void;<br>Differences: on(type: 'timeUpdate', callback: Callback\<number>): void;|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: AVPlayer;<br>API declaration: off(type: 'timeUpdate'): void;<br>Differences: off(type: 'timeUpdate'): void;|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: AVPlayer;<br>API declaration: on(type: 'durationUpdate', callback: Callback\<number>): void;<br>Differences: on(type: 'durationUpdate', callback: Callback\<number>): void;|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: AVPlayer;<br>API declaration: off(type: 'durationUpdate'): void;<br>Differences: off(type: 'durationUpdate'): void;|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: AVPlayer;<br>API declaration: on(type: 'bufferingUpdate', callback: (infoType: BufferingInfoType, value: number) => void): void;<br>Differences: on(type: 'bufferingUpdate', callback: (infoType: BufferingInfoType, value: number) => void): void;|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: AVPlayer;<br>API declaration: off(type: 'bufferingUpdate'): void;<br>Differences: off(type: 'bufferingUpdate'): void;|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: AVPlayer;<br>API declaration: on(type: 'startRenderFrame', callback: Callback\<void>): void;<br>Differences: on(type: 'startRenderFrame', callback: Callback\<void>): void;|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: AVPlayer;<br>API declaration: off(type: 'startRenderFrame'): void;<br>Differences: off(type: 'startRenderFrame'): void;|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: AVPlayer;<br>API declaration: on(type: 'videoSizeChange', callback: (width: number, height: number) => void): void;<br>Differences: on(type: 'videoSizeChange', callback: (width: number, height: number) => void): void;|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: AVPlayer;<br>API declaration: off(type: 'videoSizeChange'): void;<br>Differences: off(type: 'videoSizeChange'): void;|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: AVPlayer;<br>API declaration: on(type: 'audioInterrupt', callback: (info: audio.InterruptEvent) => void): void;<br>Differences: on(type: 'audioInterrupt', callback: (info: audio.InterruptEvent) => void): void;|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: AVPlayer;<br>API declaration: off(type: 'audioInterrupt'): void;<br>Differences: off(type: 'audioInterrupt'): void;|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: AVPlayer;<br>API declaration: on(type: 'availableBitrates', callback: (bitrates: Array\<number>) => void): void;<br>Differences: on(type: 'availableBitrates', callback: (bitrates: Array\<number>) => void): void;|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: AVPlayer;<br>API declaration: off(type: 'availableBitrates'): void;<br>Differences: off(type: 'availableBitrates'): void;|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: AVPlayer;<br>API declaration: on(type: 'error', callback: ErrorCallback): void;<br>Differences: on(type: 'error', callback: ErrorCallback): void;|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: AVPlayer;<br>API declaration: off(type: 'error'): void;<br>Differences: off(type: 'error'): void;|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: AVPlayer;<br>API declaration: on(type: 'audioOutputDeviceChangeWithInfo', callback: Callback\<audio.AudioStreamDeviceChangeInfo>): void;<br>Differences: on(type: 'audioOutputDeviceChangeWithInfo', callback: Callback\<audio.AudioStreamDeviceChangeInfo>): void;|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: AVPlayer;<br>API declaration: off(type: 'audioOutputDeviceChangeWithInfo', callback?: Callback\<audio.AudioStreamDeviceChangeInfo>): void;<br>Differences: off(type: 'audioOutputDeviceChangeWithInfo', callback?: Callback\<audio.AudioStreamDeviceChangeInfo>): void;|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: media;<br>API declaration: enum MediaErrorCode<br>Differences: enum MediaErrorCode|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: MediaErrorCode;<br>API declaration: MSERR_OK = 0<br>Differences: MSERR_OK = 0|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: MediaErrorCode;<br>API declaration: MSERR_NO_MEMORY = 1<br>Differences: MSERR_NO_MEMORY = 1|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: MediaErrorCode;<br>API declaration: MSERR_OPERATION_NOT_PERMIT = 2<br>Differences: MSERR_OPERATION_NOT_PERMIT = 2|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: MediaErrorCode;<br>API declaration: MSERR_INVALID_VAL = 3<br>Differences: MSERR_INVALID_VAL = 3|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: MediaErrorCode;<br>API declaration: MSERR_IO = 4<br>Differences: MSERR_IO = 4|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: MediaErrorCode;<br>API declaration: MSERR_TIMEOUT = 5<br>Differences: MSERR_TIMEOUT = 5|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: MediaErrorCode;<br>API declaration: MSERR_UNKNOWN = 6<br>Differences: MSERR_UNKNOWN = 6|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: MediaErrorCode;<br>API declaration: MSERR_SERVICE_DIED = 7<br>Differences: MSERR_SERVICE_DIED = 7|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: MediaErrorCode;<br>API declaration: MSERR_INVALID_STATE = 8<br>Differences: MSERR_INVALID_STATE = 8|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: MediaErrorCode;<br>API declaration: MSERR_UNSUPPORTED = 9<br>Differences: MSERR_UNSUPPORTED = 9|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: media;<br>API declaration: enum BufferingInfoType<br>Differences: enum BufferingInfoType|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: BufferingInfoType;<br>API declaration: BUFFERING_START = 1<br>Differences: BUFFERING_START = 1|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: BufferingInfoType;<br>API declaration: BUFFERING_END = 2<br>Differences: BUFFERING_END = 2|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: BufferingInfoType;<br>API declaration: BUFFERING_PERCENT = 3<br>Differences: BUFFERING_PERCENT = 3|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: BufferingInfoType;<br>API declaration: CACHED_DURATION = 4<br>Differences: CACHED_DURATION = 4|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: media;<br>API declaration: interface AVFileDescriptor<br>Differences: interface AVFileDescriptor|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: AVFileDescriptor;<br>API declaration: fd: number;<br>Differences: fd: number;|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: AVFileDescriptor;<br>API declaration: offset?: number;<br>Differences: offset?: number;|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: AVFileDescriptor;<br>API declaration: length?: number;<br>Differences: length?: number;|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: media;<br>API declaration: interface AVDataSrcDescriptor<br>Differences: interface AVDataSrcDescriptor|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: AVDataSrcDescriptor;<br>API declaration: fileSize: number;<br>Differences: fileSize: number;|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: AVDataSrcDescriptor;<br>API declaration: callback: (buffer: ArrayBuffer, length: number, pos?: number) => number;<br>Differences: callback: (buffer: ArrayBuffer, length: number, pos?: number) => number;|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: media;<br>API declaration: type AudioState = 'idle' \| 'playing' \| 'paused' \| 'stopped' \| 'error';<br>Differences: type AudioState = 'idle' \| 'playing' \| 'paused' \| 'stopped' \| 'error';|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: media;<br>API declaration: interface AudioPlayer<br>Differences: interface AudioPlayer|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: AudioPlayer;<br>API declaration: play(): void;<br>Differences: play(): void;|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: AudioPlayer;<br>API declaration: pause(): void;<br>Differences: pause(): void;|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: AudioPlayer;<br>API declaration: stop(): void;<br>Differences: stop(): void;|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: AudioPlayer;<br>API declaration: reset(): void;<br>Differences: reset(): void;|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: AudioPlayer;<br>API declaration: seek(timeMs: number): void;<br>Differences: seek(timeMs: number): void;|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: AudioPlayer;<br>API declaration: setVolume(vol: number): void;<br>Differences: setVolume(vol: number): void;|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: AudioPlayer;<br>API declaration: release(): void;<br>Differences: release(): void;|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: AudioPlayer;<br>API declaration: getTrackDescription(callback: AsyncCallback\<Array\<MediaDescription>>): void;<br>Differences: getTrackDescription(callback: AsyncCallback\<Array\<MediaDescription>>): void;|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: AudioPlayer;<br>API declaration: getTrackDescription(): Promise\<Array\<MediaDescription>>;<br>Differences: getTrackDescription(): Promise\<Array\<MediaDescription>>;|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: AudioPlayer;<br>API declaration: on(type: 'bufferingUpdate', callback: (infoType: BufferingInfoType, value: number) => void): void;<br>Differences: on(type: 'bufferingUpdate', callback: (infoType: BufferingInfoType, value: number) => void): void;|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: AudioPlayer;<br>API declaration: src: string;<br>Differences: src: string;|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: AudioPlayer;<br>API declaration: fdSrc: AVFileDescriptor;<br>Differences: fdSrc: AVFileDescriptor;|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: AudioPlayer;<br>API declaration: loop: boolean;<br>Differences: loop: boolean;|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: AudioPlayer;<br>API declaration: audioInterruptMode?: audio.InterruptMode;<br>Differences: audioInterruptMode?: audio.InterruptMode;|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: AudioPlayer;<br>API declaration: readonly currentTime: number;<br>Differences: readonly currentTime: number;|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: AudioPlayer;<br>API declaration: readonly duration: number;<br>Differences: readonly duration: number;|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: AudioPlayer;<br>API declaration: readonly state: AudioState;<br>Differences: readonly state: AudioState;|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: AudioPlayer;<br>API declaration: on(type: 'play' \| 'pause' \| 'stop' \| 'reset' \| 'dataLoad' \| 'finish' \| 'volumeChange', callback: () => void): void;<br>Differences: on(type: 'play' \| 'pause' \| 'stop' \| 'reset' \| 'dataLoad' \| 'finish' \| 'volumeChange', callback: () => void): void;|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: AudioPlayer;<br>API declaration: on(type: 'play' \| 'pause' \| 'stop' \| 'reset' \| 'dataLoad' \| 'finish' \| 'volumeChange', callback: () => void): void;<br>Differences: on(type: 'play' \| 'pause' \| 'stop' \| 'reset' \| 'dataLoad' \| 'finish' \| 'volumeChange', callback: () => void): void;|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: AudioPlayer;<br>API declaration: on(type: 'play' \| 'pause' \| 'stop' \| 'reset' \| 'dataLoad' \| 'finish' \| 'volumeChange', callback: () => void): void;<br>Differences: on(type: 'play' \| 'pause' \| 'stop' \| 'reset' \| 'dataLoad' \| 'finish' \| 'volumeChange', callback: () => void): void;|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: AudioPlayer;<br>API declaration: on(type: 'play' \| 'pause' \| 'stop' \| 'reset' \| 'dataLoad' \| 'finish' \| 'volumeChange', callback: () => void): void;<br>Differences: on(type: 'play' \| 'pause' \| 'stop' \| 'reset' \| 'dataLoad' \| 'finish' \| 'volumeChange', callback: () => void): void;|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: AudioPlayer;<br>API declaration: on(type: 'play' \| 'pause' \| 'stop' \| 'reset' \| 'dataLoad' \| 'finish' \| 'volumeChange', callback: () => void): void;<br>Differences: on(type: 'play' \| 'pause' \| 'stop' \| 'reset' \| 'dataLoad' \| 'finish' \| 'volumeChange', callback: () => void): void;|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: AudioPlayer;<br>API declaration: on(type: 'play' \| 'pause' \| 'stop' \| 'reset' \| 'dataLoad' \| 'finish' \| 'volumeChange', callback: () => void): void;<br>Differences: on(type: 'play' \| 'pause' \| 'stop' \| 'reset' \| 'dataLoad' \| 'finish' \| 'volumeChange', callback: () => void): void;|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: AudioPlayer;<br>API declaration: on(type: 'play' \| 'pause' \| 'stop' \| 'reset' \| 'dataLoad' \| 'finish' \| 'volumeChange', callback: () => void): void;<br>Differences: on(type: 'play' \| 'pause' \| 'stop' \| 'reset' \| 'dataLoad' \| 'finish' \| 'volumeChange', callback: () => void): void;|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: AudioPlayer;<br>API declaration: on(type: 'timeUpdate', callback: Callback\<number>): void;<br>Differences: on(type: 'timeUpdate', callback: Callback\<number>): void;|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: AudioPlayer;<br>API declaration: on(type: 'audioInterrupt', callback: (info: audio.InterruptEvent) => void): void;<br>Differences: on(type: 'audioInterrupt', callback: (info: audio.InterruptEvent) => void): void;|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: AudioPlayer;<br>API declaration: on(type: 'error', callback: ErrorCallback): void;<br>Differences: on(type: 'error', callback: ErrorCallback): void;|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: media;<br>API declaration: type AVRecorderState = 'idle' \| 'prepared' \| 'started' \| 'paused' \| 'stopped' \| 'released' \| 'error';<br>Differences: type AVRecorderState = 'idle' \| 'prepared' \| 'started' \| 'paused' \| 'stopped' \| 'released' \| 'error';|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: media;<br>API declaration: interface AVRecorder<br>Differences: interface AVRecorder|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: AVRecorder;<br>API declaration: prepare(config: AVRecorderConfig, callback: AsyncCallback\<void>): void;<br>Differences: prepare(config: AVRecorderConfig, callback: AsyncCallback\<void>): void;|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: AVRecorder;<br>API declaration: prepare(config: AVRecorderConfig): Promise\<void>;<br>Differences: prepare(config: AVRecorderConfig): Promise\<void>;|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: AVRecorder;<br>API declaration: getAVRecorderConfig(callback: AsyncCallback\<AVRecorderConfig>): void;<br>Differences: getAVRecorderConfig(callback: AsyncCallback\<AVRecorderConfig>): void;|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: AVRecorder;<br>API declaration: getAVRecorderConfig(): Promise\<AVRecorderConfig>;<br>Differences: getAVRecorderConfig(): Promise\<AVRecorderConfig>;|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: AVRecorder;<br>API declaration: getInputSurface(callback: AsyncCallback\<string>): void;<br>Differences: getInputSurface(callback: AsyncCallback\<string>): void;|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: AVRecorder;<br>API declaration: getInputSurface(): Promise\<string>;<br>Differences: getInputSurface(): Promise\<string>;|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: AVRecorder;<br>API declaration: start(callback: AsyncCallback\<void>): void;<br>Differences: start(callback: AsyncCallback\<void>): void;|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: AVRecorder;<br>API declaration: start(): Promise\<void>;<br>Differences: start(): Promise\<void>;|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: AVRecorder;<br>API declaration: pause(callback: AsyncCallback\<void>): void;<br>Differences: pause(callback: AsyncCallback\<void>): void;|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: AVRecorder;<br>API declaration: pause(): Promise\<void>;<br>Differences: pause(): Promise\<void>;|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: AVRecorder;<br>API declaration: resume(callback: AsyncCallback\<void>): void;<br>Differences: resume(callback: AsyncCallback\<void>): void;|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: AVRecorder;<br>API declaration: resume(): Promise\<void>;<br>Differences: resume(): Promise\<void>;|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: AVRecorder;<br>API declaration: stop(callback: AsyncCallback\<void>): void;<br>Differences: stop(callback: AsyncCallback\<void>): void;|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: AVRecorder;<br>API declaration: stop(): Promise\<void>;<br>Differences: stop(): Promise\<void>;|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: AVRecorder;<br>API declaration: reset(callback: AsyncCallback\<void>): void;<br>Differences: reset(callback: AsyncCallback\<void>): void;|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: AVRecorder;<br>API declaration: reset(): Promise\<void>;<br>Differences: reset(): Promise\<void>;|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: AVRecorder;<br>API declaration: release(callback: AsyncCallback\<void>): void;<br>Differences: release(callback: AsyncCallback\<void>): void;|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: AVRecorder;<br>API declaration: release(): Promise\<void>;<br>Differences: release(): Promise\<void>;|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: AVRecorder;<br>API declaration: getCurrentAudioCapturerInfo(callback: AsyncCallback\<audio.AudioCapturerChangeInfo>): void;<br>Differences: getCurrentAudioCapturerInfo(callback: AsyncCallback\<audio.AudioCapturerChangeInfo>): void;|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: AVRecorder;<br>API declaration: getCurrentAudioCapturerInfo(): Promise\<audio.AudioCapturerChangeInfo>;<br>Differences: getCurrentAudioCapturerInfo(): Promise\<audio.AudioCapturerChangeInfo>;|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: AVRecorder;<br>API declaration: getAudioCapturerMaxAmplitude(callback: AsyncCallback\<number>): void;<br>Differences: getAudioCapturerMaxAmplitude(callback: AsyncCallback\<number>): void;|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: AVRecorder;<br>API declaration: getAudioCapturerMaxAmplitude(): Promise\<number>;<br>Differences: getAudioCapturerMaxAmplitude(): Promise\<number>;|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: AVRecorder;<br>API declaration: getAvailableEncoder(callback: AsyncCallback\<Array\<EncoderInfo>>): void;<br>Differences: getAvailableEncoder(callback: AsyncCallback\<Array\<EncoderInfo>>): void;|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: AVRecorder;<br>API declaration: getAvailableEncoder(): Promise\<Array\<EncoderInfo>>;<br>Differences: getAvailableEncoder(): Promise\<Array\<EncoderInfo>>;|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: AVRecorder;<br>API declaration: readonly state: AVRecorderState;<br>Differences: readonly state: AVRecorderState;|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: AVRecorder;<br>API declaration: on(type: 'audioCapturerChange', callback: Callback\<audio.AudioCapturerChangeInfo>): void;<br>Differences: on(type: 'audioCapturerChange', callback: Callback\<audio.AudioCapturerChangeInfo>): void;|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: AVRecorder;<br>API declaration: on(type: 'stateChange', callback: (state: AVRecorderState, reason: StateChangeReason) => void): void;<br>Differences: on(type: 'stateChange', callback: (state: AVRecorderState, reason: StateChangeReason) => void): void;|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: AVRecorder;<br>API declaration: on(type: 'error', callback: ErrorCallback): void;<br>Differences: on(type: 'error', callback: ErrorCallback): void;|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: AVRecorder;<br>API declaration: off(type: 'stateChange'): void;<br>Differences: off(type: 'stateChange'): void;|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: AVRecorder;<br>API declaration: off(type: 'error'): void;<br>Differences: off(type: 'error'): void;|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: AVRecorder;<br>API declaration: off(type: 'audioCapturerChange'): void;<br>Differences: off(type: 'audioCapturerChange'): void;|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: media;<br>API declaration: enum AudioEncoder<br>Differences: enum AudioEncoder|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: AudioEncoder;<br>API declaration: DEFAULT = 0<br>Differences: DEFAULT = 0|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: AudioEncoder;<br>API declaration: AMR_NB = 1<br>Differences: AMR_NB = 1|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: AudioEncoder;<br>API declaration: AMR_WB = 2<br>Differences: AMR_WB = 2|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: AudioEncoder;<br>API declaration: AAC_LC = 3<br>Differences: AAC_LC = 3|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: AudioEncoder;<br>API declaration: HE_AAC = 4<br>Differences: HE_AAC = 4|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: media;<br>API declaration: enum AudioOutputFormat<br>Differences: enum AudioOutputFormat|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: AudioOutputFormat;<br>API declaration: DEFAULT = 0<br>Differences: DEFAULT = 0|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: AudioOutputFormat;<br>API declaration: MPEG_4 = 2<br>Differences: MPEG_4 = 2|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: AudioOutputFormat;<br>API declaration: AMR_NB = 3<br>Differences: AMR_NB = 3|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: AudioOutputFormat;<br>API declaration: AMR_WB = 4<br>Differences: AMR_WB = 4|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: AudioOutputFormat;<br>API declaration: AAC_ADTS = 6<br>Differences: AAC_ADTS = 6|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: media;<br>API declaration: interface Location<br>Differences: interface Location|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: Location;<br>API declaration: latitude: number;<br>Differences: latitude: number;|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: Location;<br>API declaration: longitude: number;<br>Differences: longitude: number;|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: media;<br>API declaration: interface AudioRecorderConfig<br>Differences: interface AudioRecorderConfig|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: AudioRecorderConfig;<br>API declaration: audioEncoder?: AudioEncoder;<br>Differences: audioEncoder?: AudioEncoder;|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: AudioRecorderConfig;<br>API declaration: audioEncodeBitRate?: number;<br>Differences: audioEncodeBitRate?: number;|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: AudioRecorderConfig;<br>API declaration: audioSampleRate?: number;<br>Differences: audioSampleRate?: number;|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: AudioRecorderConfig;<br>API declaration: numberOfChannels?: number;<br>Differences: numberOfChannels?: number;|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: AudioRecorderConfig;<br>API declaration: format?: AudioOutputFormat;<br>Differences: format?: AudioOutputFormat;|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: AudioRecorderConfig;<br>API declaration: uri: string;<br>Differences: uri: string;|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: AudioRecorderConfig;<br>API declaration: location?: Location;<br>Differences: location?: Location;|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: AudioRecorderConfig;<br>API declaration: audioEncoderMime?: CodecMimeType;<br>Differences: audioEncoderMime?: CodecMimeType;|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: AudioRecorderConfig;<br>API declaration: fileFormat?: ContainerFormatType;<br>Differences: fileFormat?: ContainerFormatType;|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: media;<br>API declaration: interface AudioRecorder<br>Differences: interface AudioRecorder|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: AudioRecorder;<br>API declaration: prepare(config: AudioRecorderConfig): void;<br>Differences: prepare(config: AudioRecorderConfig): void;|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: AudioRecorder;<br>API declaration: start(): void;<br>Differences: start(): void;|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: AudioRecorder;<br>API declaration: pause(): void;<br>Differences: pause(): void;|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: AudioRecorder;<br>API declaration: resume(): void;<br>Differences: resume(): void;|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: AudioRecorder;<br>API declaration: stop(): void;<br>Differences: stop(): void;|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: AudioRecorder;<br>API declaration: release(): void;<br>Differences: release(): void;|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: AudioRecorder;<br>API declaration: reset(): void;<br>Differences: reset(): void;|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: AudioRecorder;<br>API declaration: on(type: 'prepare' \| 'start' \| 'pause' \| 'resume' \| 'stop' \| 'release' \| 'reset', callback: () => void): void;<br>Differences: on(type: 'prepare' \| 'start' \| 'pause' \| 'resume' \| 'stop' \| 'release' \| 'reset', callback: () => void): void;|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: AudioRecorder;<br>API declaration: on(type: 'prepare' \| 'start' \| 'pause' \| 'resume' \| 'stop' \| 'release' \| 'reset', callback: () => void): void;<br>Differences: on(type: 'prepare' \| 'start' \| 'pause' \| 'resume' \| 'stop' \| 'release' \| 'reset', callback: () => void): void;|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: AudioRecorder;<br>API declaration: on(type: 'prepare' \| 'start' \| 'pause' \| 'resume' \| 'stop' \| 'release' \| 'reset', callback: () => void): void;<br>Differences: on(type: 'prepare' \| 'start' \| 'pause' \| 'resume' \| 'stop' \| 'release' \| 'reset', callback: () => void): void;|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: AudioRecorder;<br>API declaration: on(type: 'prepare' \| 'start' \| 'pause' \| 'resume' \| 'stop' \| 'release' \| 'reset', callback: () => void): void;<br>Differences: on(type: 'prepare' \| 'start' \| 'pause' \| 'resume' \| 'stop' \| 'release' \| 'reset', callback: () => void): void;|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: AudioRecorder;<br>API declaration: on(type: 'prepare' \| 'start' \| 'pause' \| 'resume' \| 'stop' \| 'release' \| 'reset', callback: () => void): void;<br>Differences: on(type: 'prepare' \| 'start' \| 'pause' \| 'resume' \| 'stop' \| 'release' \| 'reset', callback: () => void): void;|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: AudioRecorder;<br>API declaration: on(type: 'prepare' \| 'start' \| 'pause' \| 'resume' \| 'stop' \| 'release' \| 'reset', callback: () => void): void;<br>Differences: on(type: 'prepare' \| 'start' \| 'pause' \| 'resume' \| 'stop' \| 'release' \| 'reset', callback: () => void): void;|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: AudioRecorder;<br>API declaration: on(type: 'prepare' \| 'start' \| 'pause' \| 'resume' \| 'stop' \| 'release' \| 'reset', callback: () => void): void;<br>Differences: on(type: 'prepare' \| 'start' \| 'pause' \| 'resume' \| 'stop' \| 'release' \| 'reset', callback: () => void): void;|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: AudioRecorder;<br>API declaration: on(type: 'error', callback: ErrorCallback): void;<br>Differences: on(type: 'error', callback: ErrorCallback): void;|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: media;<br>API declaration: type VideoPlayState = 'idle' \| 'prepared' \| 'playing' \| 'paused' \| 'stopped' \| 'error';<br>Differences: type VideoPlayState = 'idle' \| 'prepared' \| 'playing' \| 'paused' \| 'stopped' \| 'error';|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: media;<br>API declaration: enum PlaybackSpeed<br>Differences: enum PlaybackSpeed|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: PlaybackSpeed;<br>API declaration: SPEED_FORWARD_0_75_X = 0<br>Differences: SPEED_FORWARD_0_75_X = 0|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: PlaybackSpeed;<br>API declaration: SPEED_FORWARD_1_00_X = 1<br>Differences: SPEED_FORWARD_1_00_X = 1|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: PlaybackSpeed;<br>API declaration: SPEED_FORWARD_1_25_X = 2<br>Differences: SPEED_FORWARD_1_25_X = 2|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: PlaybackSpeed;<br>API declaration: SPEED_FORWARD_1_75_X = 3<br>Differences: SPEED_FORWARD_1_75_X = 3|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: PlaybackSpeed;<br>API declaration: SPEED_FORWARD_2_00_X = 4<br>Differences: SPEED_FORWARD_2_00_X = 4|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: media;<br>API declaration: interface VideoPlayer<br>Differences: interface VideoPlayer|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: VideoPlayer;<br>API declaration: setDisplaySurface(surfaceId: string, callback: AsyncCallback\<void>): void;<br>Differences: setDisplaySurface(surfaceId: string, callback: AsyncCallback\<void>): void;|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: VideoPlayer;<br>API declaration: setDisplaySurface(surfaceId: string): Promise\<void>;<br>Differences: setDisplaySurface(surfaceId: string): Promise\<void>;|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: VideoPlayer;<br>API declaration: prepare(callback: AsyncCallback\<void>): void;<br>Differences: prepare(callback: AsyncCallback\<void>): void;|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: VideoPlayer;<br>API declaration: prepare(): Promise\<void>;<br>Differences: prepare(): Promise\<void>;|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: VideoPlayer;<br>API declaration: play(callback: AsyncCallback\<void>): void;<br>Differences: play(callback: AsyncCallback\<void>): void;|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: VideoPlayer;<br>API declaration: play(): Promise\<void>;<br>Differences: play(): Promise\<void>;|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: VideoPlayer;<br>API declaration: pause(callback: AsyncCallback\<void>): void;<br>Differences: pause(callback: AsyncCallback\<void>): void;|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: VideoPlayer;<br>API declaration: pause(): Promise\<void>;<br>Differences: pause(): Promise\<void>;|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: VideoPlayer;<br>API declaration: stop(callback: AsyncCallback\<void>): void;<br>Differences: stop(callback: AsyncCallback\<void>): void;|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: VideoPlayer;<br>API declaration: stop(): Promise\<void>;<br>Differences: stop(): Promise\<void>;|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: VideoPlayer;<br>API declaration: reset(callback: AsyncCallback\<void>): void;<br>Differences: reset(callback: AsyncCallback\<void>): void;|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: VideoPlayer;<br>API declaration: reset(): Promise\<void>;<br>Differences: reset(): Promise\<void>;|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: VideoPlayer;<br>API declaration: seek(timeMs: number, callback: AsyncCallback\<number>): void;<br>Differences: seek(timeMs: number, callback: AsyncCallback\<number>): void;|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: VideoPlayer;<br>API declaration: seek(timeMs: number, mode: SeekMode, callback: AsyncCallback\<number>): void;<br>Differences: seek(timeMs: number, mode: SeekMode, callback: AsyncCallback\<number>): void;|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: VideoPlayer;<br>API declaration: seek(timeMs: number, mode?: SeekMode): Promise\<number>;<br>Differences: seek(timeMs: number, mode?: SeekMode): Promise\<number>;|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: VideoPlayer;<br>API declaration: setVolume(vol: number, callback: AsyncCallback\<void>): void;<br>Differences: setVolume(vol: number, callback: AsyncCallback\<void>): void;|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: VideoPlayer;<br>API declaration: setVolume(vol: number): Promise\<void>;<br>Differences: setVolume(vol: number): Promise\<void>;|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: VideoPlayer;<br>API declaration: release(callback: AsyncCallback\<void>): void;<br>Differences: release(callback: AsyncCallback\<void>): void;|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: VideoPlayer;<br>API declaration: release(): Promise\<void>;<br>Differences: release(): Promise\<void>;|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: VideoPlayer;<br>API declaration: getTrackDescription(callback: AsyncCallback\<Array\<MediaDescription>>): void;<br>Differences: getTrackDescription(callback: AsyncCallback\<Array\<MediaDescription>>): void;|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: VideoPlayer;<br>API declaration: getTrackDescription(): Promise\<Array\<MediaDescription>>;<br>Differences: getTrackDescription(): Promise\<Array\<MediaDescription>>;|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: VideoPlayer;<br>API declaration: url: string;<br>Differences: url: string;|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: VideoPlayer;<br>API declaration: fdSrc: AVFileDescriptor;<br>Differences: fdSrc: AVFileDescriptor;|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: VideoPlayer;<br>API declaration: loop: boolean;<br>Differences: loop: boolean;|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: VideoPlayer;<br>API declaration: readonly currentTime: number;<br>Differences: readonly currentTime: number;|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: VideoPlayer;<br>API declaration: readonly duration: number;<br>Differences: readonly duration: number;|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: VideoPlayer;<br>API declaration: readonly state: VideoPlayState;<br>Differences: readonly state: VideoPlayState;|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: VideoPlayer;<br>API declaration: readonly width: number;<br>Differences: readonly width: number;|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: VideoPlayer;<br>API declaration: readonly height: number;<br>Differences: readonly height: number;|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: VideoPlayer;<br>API declaration: audioInterruptMode?: audio.InterruptMode;<br>Differences: audioInterruptMode?: audio.InterruptMode;|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: VideoPlayer;<br>API declaration: videoScaleType?: VideoScaleType;<br>Differences: videoScaleType?: VideoScaleType;|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: VideoPlayer;<br>API declaration: setSpeed(speed: number, callback: AsyncCallback\<number>): void;<br>Differences: setSpeed(speed: number, callback: AsyncCallback\<number>): void;|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: VideoPlayer;<br>API declaration: setSpeed(speed: number): Promise\<number>;<br>Differences: setSpeed(speed: number): Promise\<number>;|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: VideoPlayer;<br>API declaration: on(type: 'playbackCompleted', callback: Callback\<void>): void;<br>Differences: on(type: 'playbackCompleted', callback: Callback\<void>): void;|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: VideoPlayer;<br>API declaration: on(type: 'bufferingUpdate', callback: (infoType: BufferingInfoType, value: number) => void): void;<br>Differences: on(type: 'bufferingUpdate', callback: (infoType: BufferingInfoType, value: number) => void): void;|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: VideoPlayer;<br>API declaration: on(type: 'startRenderFrame', callback: Callback\<void>): void;<br>Differences: on(type: 'startRenderFrame', callback: Callback\<void>): void;|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: VideoPlayer;<br>API declaration: on(type: 'videoSizeChanged', callback: (width: number, height: number) => void): void;<br>Differences: on(type: 'videoSizeChanged', callback: (width: number, height: number) => void): void;|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: VideoPlayer;<br>API declaration: on(type: 'audioInterrupt', callback: (info: audio.InterruptEvent) => void): void;<br>Differences: on(type: 'audioInterrupt', callback: (info: audio.InterruptEvent) => void): void;|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: VideoPlayer;<br>API declaration: on(type: 'error', callback: ErrorCallback): void;<br>Differences: on(type: 'error', callback: ErrorCallback): void;|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: media;<br>API declaration: enum VideoScaleType<br>Differences: enum VideoScaleType|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: VideoScaleType;<br>API declaration: VIDEO_SCALE_TYPE_FIT = 0<br>Differences: VIDEO_SCALE_TYPE_FIT = 0|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: VideoScaleType;<br>API declaration: VIDEO_SCALE_TYPE_FIT_CROP = 1<br>Differences: VIDEO_SCALE_TYPE_FIT_CROP = 1|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: media;<br>API declaration: enum ContainerFormatType<br>Differences: enum ContainerFormatType|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: ContainerFormatType;<br>API declaration: CFT_MPEG_4 = 'mp4'<br>Differences: CFT_MPEG_4 = 'mp4'|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: ContainerFormatType;<br>API declaration: CFT_MPEG_4A = 'm4a'<br>Differences: CFT_MPEG_4A = 'm4a'|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: media;<br>API declaration: enum MediaType<br>Differences: enum MediaType|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: MediaType;<br>API declaration: MEDIA_TYPE_AUD = 0<br>Differences: MEDIA_TYPE_AUD = 0|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: MediaType;<br>API declaration: MEDIA_TYPE_VID = 1<br>Differences: MEDIA_TYPE_VID = 1|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: media;<br>API declaration: enum MediaDescriptionKey<br>Differences: enum MediaDescriptionKey|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: MediaDescriptionKey;<br>API declaration: MD_KEY_TRACK_INDEX = 'track_index'<br>Differences: MD_KEY_TRACK_INDEX = 'track_index'|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: MediaDescriptionKey;<br>API declaration: MD_KEY_TRACK_TYPE = 'track_type'<br>Differences: MD_KEY_TRACK_TYPE = 'track_type'|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: MediaDescriptionKey;<br>API declaration: MD_KEY_CODEC_MIME = 'codec_mime'<br>Differences: MD_KEY_CODEC_MIME = 'codec_mime'|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: MediaDescriptionKey;<br>API declaration: MD_KEY_DURATION = 'duration'<br>Differences: MD_KEY_DURATION = 'duration'|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: MediaDescriptionKey;<br>API declaration: MD_KEY_BITRATE = 'bitrate'<br>Differences: MD_KEY_BITRATE = 'bitrate'|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: MediaDescriptionKey;<br>API declaration: MD_KEY_WIDTH = 'width'<br>Differences: MD_KEY_WIDTH = 'width'|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: MediaDescriptionKey;<br>API declaration: MD_KEY_HEIGHT = 'height'<br>Differences: MD_KEY_HEIGHT = 'height'|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: MediaDescriptionKey;<br>API declaration: MD_KEY_FRAME_RATE = 'frame_rate'<br>Differences: MD_KEY_FRAME_RATE = 'frame_rate'|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: MediaDescriptionKey;<br>API declaration: MD_KEY_AUD_CHANNEL_COUNT = 'channel_count'<br>Differences: MD_KEY_AUD_CHANNEL_COUNT = 'channel_count'|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: MediaDescriptionKey;<br>API declaration: MD_KEY_AUD_SAMPLE_RATE = 'sample_rate'<br>Differences: MD_KEY_AUD_SAMPLE_RATE = 'sample_rate'|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: media;<br>API declaration: enum AudioSourceType<br>Differences: enum AudioSourceType|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: AudioSourceType;<br>API declaration: AUDIO_SOURCE_TYPE_DEFAULT = 0<br>Differences: AUDIO_SOURCE_TYPE_DEFAULT = 0|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: AudioSourceType;<br>API declaration: AUDIO_SOURCE_TYPE_MIC = 1<br>Differences: AUDIO_SOURCE_TYPE_MIC = 1|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: media;<br>API declaration: enum VideoSourceType<br>Differences: enum VideoSourceType|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: VideoSourceType;<br>API declaration: VIDEO_SOURCE_TYPE_SURFACE_YUV = 0<br>Differences: VIDEO_SOURCE_TYPE_SURFACE_YUV = 0|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: VideoSourceType;<br>API declaration: VIDEO_SOURCE_TYPE_SURFACE_ES = 1<br>Differences: VIDEO_SOURCE_TYPE_SURFACE_ES = 1|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: media;<br>API declaration: interface EncoderInfo<br>Differences: interface EncoderInfo|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: EncoderInfo;<br>API declaration: mimeType: CodecMimeType;<br>Differences: mimeType: CodecMimeType;|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: EncoderInfo;<br>API declaration: type: string;<br>Differences: type: string;|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: EncoderInfo;<br>API declaration: bitRate?: Range;<br>Differences: bitRate?: Range;|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: EncoderInfo;<br>API declaration: frameRate?: Range;<br>Differences: frameRate?: Range;|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: EncoderInfo;<br>API declaration: width?: Range;<br>Differences: width?: Range;|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: EncoderInfo;<br>API declaration: height?: Range;<br>Differences: height?: Range;|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: EncoderInfo;<br>API declaration: channels?: Range;<br>Differences: channels?: Range;|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: EncoderInfo;<br>API declaration: sampleRate?: Array\<number>;<br>Differences: sampleRate?: Array\<number>;|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: media;<br>API declaration: interface Range<br>Differences: interface Range|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: Range;<br>API declaration: min: number;<br>Differences: min: number;|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: Range;<br>API declaration: max: number;<br>Differences: max: number;|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: media;<br>API declaration: interface AVRecorderProfile<br>Differences: interface AVRecorderProfile|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: AVRecorderProfile;<br>API declaration: audioBitrate?: number;<br>Differences: audioBitrate?: number;|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: AVRecorderProfile;<br>API declaration: audioChannels?: number;<br>Differences: audioChannels?: number;|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: AVRecorderProfile;<br>API declaration: audioCodec?: CodecMimeType;<br>Differences: audioCodec?: CodecMimeType;|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: AVRecorderProfile;<br>API declaration: audioSampleRate?: number;<br>Differences: audioSampleRate?: number;|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: AVRecorderProfile;<br>API declaration: fileFormat: ContainerFormatType;<br>Differences: fileFormat: ContainerFormatType;|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: AVRecorderProfile;<br>API declaration: videoBitrate?: number;<br>Differences: videoBitrate?: number;|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: AVRecorderProfile;<br>API declaration: videoCodec?: CodecMimeType;<br>Differences: videoCodec?: CodecMimeType;|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: AVRecorderProfile;<br>API declaration: videoFrameWidth?: number;<br>Differences: videoFrameWidth?: number;|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: AVRecorderProfile;<br>API declaration: videoFrameHeight?: number;<br>Differences: videoFrameHeight?: number;|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: AVRecorderProfile;<br>API declaration: videoFrameRate?: number;<br>Differences: videoFrameRate?: number;|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: AVRecorderProfile;<br>API declaration: isHdr?: boolean;<br>Differences: isHdr?: boolean;|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: media;<br>API declaration: interface AVRecorderConfig<br>Differences: interface AVRecorderConfig|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: AVRecorderConfig;<br>API declaration: audioSourceType?: AudioSourceType;<br>Differences: audioSourceType?: AudioSourceType;|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: AVRecorderConfig;<br>API declaration: videoSourceType?: VideoSourceType;<br>Differences: videoSourceType?: VideoSourceType;|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: AVRecorderConfig;<br>API declaration: profile: AVRecorderProfile;<br>Differences: profile: AVRecorderProfile;|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: AVRecorderConfig;<br>API declaration: url: string;<br>Differences: url: string;|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: AVRecorderConfig;<br>API declaration: rotation?: number;<br>Differences: rotation?: number;|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: AVRecorderConfig;<br>API declaration: location?: Location;<br>Differences: location?: Location;|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: media;<br>API declaration: interface MediaDescription<br>Differences: interface MediaDescription|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: MediaDescription;<br>API declaration: [key: string]: Object;<br>Differences: [key: string]: Object;|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: media;<br>API declaration: enum SeekMode<br>Differences: enum SeekMode|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: SeekMode;<br>API declaration: SEEK_NEXT_SYNC = 0<br>Differences: SEEK_NEXT_SYNC = 0|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: SeekMode;<br>API declaration: SEEK_PREV_SYNC = 1<br>Differences: SEEK_PREV_SYNC = 1|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: media;<br>API declaration: enum CodecMimeType<br>Differences: enum CodecMimeType|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: CodecMimeType;<br>API declaration: VIDEO_H263 = 'video/h263'<br>Differences: VIDEO_H263 = 'video/h263'|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: CodecMimeType;<br>API declaration: VIDEO_AVC = 'video/avc'<br>Differences: VIDEO_AVC = 'video/avc'|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: CodecMimeType;<br>API declaration: VIDEO_MPEG2 = 'video/mpeg2'<br>Differences: VIDEO_MPEG2 = 'video/mpeg2'|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: CodecMimeType;<br>API declaration: VIDEO_MPEG4 = 'video/mp4v-es'<br>Differences: VIDEO_MPEG4 = 'video/mp4v-es'|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: CodecMimeType;<br>API declaration: VIDEO_VP8 = 'video/x-vnd.on2.vp8'<br>Differences: VIDEO_VP8 = 'video/x-vnd.on2.vp8'|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: CodecMimeType;<br>API declaration: AUDIO_AAC = 'audio/mp4a-latm'<br>Differences: AUDIO_AAC = 'audio/mp4a-latm'|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: CodecMimeType;<br>API declaration: AUDIO_VORBIS = 'audio/vorbis'<br>Differences: AUDIO_VORBIS = 'audio/vorbis'|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: CodecMimeType;<br>API declaration: AUDIO_FLAC = 'audio/flac'<br>Differences: AUDIO_FLAC = 'audio/flac'|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: CodecMimeType;<br>API declaration: VIDEO_HEVC = 'video/hevc'<br>Differences: VIDEO_HEVC = 'video/hevc'|api/@ohos.multimedia.media.d.ts|
|New Kit|Class name: global;<br>API declaration: <br>Differences: NA|Class name: global;<br>API declaration: api\@ohos.multimedia.media.d.ts<br>Differences: MediaKit|api/@ohos.multimedia.media.d.ts|
|New Kit|Class name: global;<br>API declaration: <br>Differences: NA|Class name: global;<br>API declaration: kits\@kit.MediaKit.d.ts<br>Differences: MediaKit|kits/@kit.MediaKit.d.ts|
