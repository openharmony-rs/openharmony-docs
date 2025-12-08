| 操作 | 旧版本 | 新版本 | d.ts文件 |
| ---- | ------ | ------ | -------- |
|新增API|NA|类名：global；<br>API声明：declare namespace media<br>差异内容：declare namespace media|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：media；<br>API声明：function createAVPlayer(callback: AsyncCallback\<AVPlayer>): void;<br>差异内容：function createAVPlayer(callback: AsyncCallback\<AVPlayer>): void;|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：media；<br>API声明：function createAVPlayer(): Promise\<AVPlayer>;<br>差异内容：function createAVPlayer(): Promise\<AVPlayer>;|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：media；<br>API声明：function createAVRecorder(callback: AsyncCallback\<AVRecorder>): void;<br>差异内容：function createAVRecorder(callback: AsyncCallback\<AVRecorder>): void;|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：media；<br>API声明：function createAVRecorder(): Promise\<AVRecorder>;<br>差异内容：function createAVRecorder(): Promise\<AVRecorder>;|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：media；<br>API声明：function createAudioPlayer(): AudioPlayer;<br>差异内容：function createAudioPlayer(): AudioPlayer;|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：media；<br>API声明：function createAudioRecorder(): AudioRecorder;<br>差异内容：function createAudioRecorder(): AudioRecorder;|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：media；<br>API声明：function createVideoPlayer(callback: AsyncCallback\<VideoPlayer>): void;<br>差异内容：function createVideoPlayer(callback: AsyncCallback\<VideoPlayer>): void;|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：media；<br>API声明：function createVideoPlayer(): Promise\<VideoPlayer>;<br>差异内容：function createVideoPlayer(): Promise\<VideoPlayer>;|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：media；<br>API声明：function createSoundPool(maxStreams: number, audioRenderInfo: audio.AudioRendererInfo, callback: AsyncCallback\<SoundPool>): void;<br>差异内容：function createSoundPool(maxStreams: number, audioRenderInfo: audio.AudioRendererInfo, callback: AsyncCallback\<SoundPool>): void;|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：media；<br>API声明：function createSoundPool(maxStreams: number, audioRenderInfo: audio.AudioRendererInfo): Promise\<SoundPool>;<br>差异内容：function createSoundPool(maxStreams: number, audioRenderInfo: audio.AudioRendererInfo): Promise\<SoundPool>;|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：media；<br>API声明：type SoundPool = _SoundPool;<br>差异内容：type SoundPool = _SoundPool;|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：media；<br>API声明：type PlayParameters = _PlayParameters;<br>差异内容：type PlayParameters = _PlayParameters;|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：media；<br>API声明：enum StateChangeReason<br>差异内容：enum StateChangeReason|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：StateChangeReason；<br>API声明：USER = 1<br>差异内容：USER = 1|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：StateChangeReason；<br>API声明：BACKGROUND = 2<br>差异内容：BACKGROUND = 2|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：media；<br>API声明：function createAVMetadataExtractor(): Promise\<AVMetadataExtractor>;<br>差异内容：function createAVMetadataExtractor(): Promise\<AVMetadataExtractor>;|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：media；<br>API声明：function createAVMetadataExtractor(callback: AsyncCallback\<AVMetadataExtractor>): void;<br>差异内容：function createAVMetadataExtractor(callback: AsyncCallback\<AVMetadataExtractor>): void;|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：media；<br>API声明：interface AVMetadataExtractor<br>差异内容：interface AVMetadataExtractor|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：AVMetadataExtractor；<br>API声明：fdSrc?: AVFileDescriptor;<br>差异内容：fdSrc?: AVFileDescriptor;|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：AVMetadataExtractor；<br>API声明：dataSrc?: AVDataSrcDescriptor;<br>差异内容：dataSrc?: AVDataSrcDescriptor;|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：AVMetadataExtractor；<br>API声明：fetchMetadata(callback: AsyncCallback\<AVMetadata>): void;<br>差异内容：fetchMetadata(callback: AsyncCallback\<AVMetadata>): void;|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：AVMetadataExtractor；<br>API声明：fetchMetadata(): Promise\<AVMetadata>;<br>差异内容：fetchMetadata(): Promise\<AVMetadata>;|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：AVMetadataExtractor；<br>API声明：fetchAlbumCover(callback: AsyncCallback\<image.PixelMap>): void;<br>差异内容：fetchAlbumCover(callback: AsyncCallback\<image.PixelMap>): void;|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：AVMetadataExtractor；<br>API声明：fetchAlbumCover(): Promise\<image.PixelMap>;<br>差异内容：fetchAlbumCover(): Promise\<image.PixelMap>;|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：AVMetadataExtractor；<br>API声明：release(callback: AsyncCallback\<void>): void;<br>差异内容：release(callback: AsyncCallback\<void>): void;|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：AVMetadataExtractor；<br>API声明：release(): Promise\<void>;<br>差异内容：release(): Promise\<void>;|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：media；<br>API声明：interface AVMetadata<br>差异内容：interface AVMetadata|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：AVMetadata；<br>API声明：album?: string;<br>差异内容：album?: string;|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：AVMetadata；<br>API声明：albumArtist?: string;<br>差异内容：albumArtist?: string;|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：AVMetadata；<br>API声明：artist?: string;<br>差异内容：artist?: string;|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：AVMetadata；<br>API声明：author?: string;<br>差异内容：author?: string;|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：AVMetadata；<br>API声明：dateTime?: string;<br>差异内容：dateTime?: string;|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：AVMetadata；<br>API声明：dateTimeFormat?: string;<br>差异内容：dateTimeFormat?: string;|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：AVMetadata；<br>API声明：composer?: string;<br>差异内容：composer?: string;|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：AVMetadata；<br>API声明：duration?: string;<br>差异内容：duration?: string;|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：AVMetadata；<br>API声明：genre?: string;<br>差异内容：genre?: string;|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：AVMetadata；<br>API声明：hasAudio?: string;<br>差异内容：hasAudio?: string;|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：AVMetadata；<br>API声明：hasVideo?: string;<br>差异内容：hasVideo?: string;|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：AVMetadata；<br>API声明：mimeType?: string;<br>差异内容：mimeType?: string;|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：AVMetadata；<br>API声明：trackCount?: string;<br>差异内容：trackCount?: string;|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：AVMetadata；<br>API声明：sampleRate?: string;<br>差异内容：sampleRate?: string;|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：AVMetadata；<br>API声明：title?: string;<br>差异内容：title?: string;|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：AVMetadata；<br>API声明：videoHeight?: string;<br>差异内容：videoHeight?: string;|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：AVMetadata；<br>API声明：videoWidth?: string;<br>差异内容：videoWidth?: string;|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：AVMetadata；<br>API声明：videoOrientation?: string;<br>差异内容：videoOrientation?: string;|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：media；<br>API声明：enum AVErrorCode<br>差异内容：enum AVErrorCode|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：AVErrorCode；<br>API声明：AVERR_OK = 0<br>差异内容：AVERR_OK = 0|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：AVErrorCode；<br>API声明：AVERR_NO_PERMISSION = 201<br>差异内容：AVERR_NO_PERMISSION = 201|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：AVErrorCode；<br>API声明：AVERR_INVALID_PARAMETER = 401<br>差异内容：AVERR_INVALID_PARAMETER = 401|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：AVErrorCode；<br>API声明：AVERR_UNSUPPORT_CAPABILITY = 801<br>差异内容：AVERR_UNSUPPORT_CAPABILITY = 801|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：AVErrorCode；<br>API声明：AVERR_NO_MEMORY = 5400101<br>差异内容：AVERR_NO_MEMORY = 5400101|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：AVErrorCode；<br>API声明：AVERR_OPERATE_NOT_PERMIT = 5400102<br>差异内容：AVERR_OPERATE_NOT_PERMIT = 5400102|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：AVErrorCode；<br>API声明：AVERR_IO = 5400103<br>差异内容：AVERR_IO = 5400103|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：AVErrorCode；<br>API声明：AVERR_TIMEOUT = 5400104<br>差异内容：AVERR_TIMEOUT = 5400104|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：AVErrorCode；<br>API声明：AVERR_SERVICE_DIED = 5400105<br>差异内容：AVERR_SERVICE_DIED = 5400105|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：AVErrorCode；<br>API声明：AVERR_UNSUPPORT_FORMAT = 5400106<br>差异内容：AVERR_UNSUPPORT_FORMAT = 5400106|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：AVErrorCode；<br>API声明：AVERR_AUDIO_INTERRUPTED = 5400107<br>差异内容：AVERR_AUDIO_INTERRUPTED = 5400107|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：media；<br>API声明：type AVPlayerState = 'idle' \| 'initialized' \| 'prepared' \| 'playing' \| 'paused' \| 'completed' \| 'stopped' \| 'released' \| 'error';<br>差异内容：type AVPlayerState = 'idle' \| 'initialized' \| 'prepared' \| 'playing' \| 'paused' \| 'completed' \| 'stopped' \| 'released' \| 'error';|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：media；<br>API声明：interface AVPlayer<br>差异内容：interface AVPlayer|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：AVPlayer；<br>API声明：prepare(callback: AsyncCallback\<void>): void;<br>差异内容：prepare(callback: AsyncCallback\<void>): void;|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：AVPlayer；<br>API声明：prepare(): Promise\<void>;<br>差异内容：prepare(): Promise\<void>;|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：AVPlayer；<br>API声明：play(callback: AsyncCallback\<void>): void;<br>差异内容：play(callback: AsyncCallback\<void>): void;|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：AVPlayer；<br>API声明：play(): Promise\<void>;<br>差异内容：play(): Promise\<void>;|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：AVPlayer；<br>API声明：pause(callback: AsyncCallback\<void>): void;<br>差异内容：pause(callback: AsyncCallback\<void>): void;|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：AVPlayer；<br>API声明：pause(): Promise\<void>;<br>差异内容：pause(): Promise\<void>;|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：AVPlayer；<br>API声明：stop(callback: AsyncCallback\<void>): void;<br>差异内容：stop(callback: AsyncCallback\<void>): void;|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：AVPlayer；<br>API声明：stop(): Promise\<void>;<br>差异内容：stop(): Promise\<void>;|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：AVPlayer；<br>API声明：reset(callback: AsyncCallback\<void>): void;<br>差异内容：reset(callback: AsyncCallback\<void>): void;|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：AVPlayer；<br>API声明：reset(): Promise\<void>;<br>差异内容：reset(): Promise\<void>;|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：AVPlayer；<br>API声明：release(callback: AsyncCallback\<void>): void;<br>差异内容：release(callback: AsyncCallback\<void>): void;|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：AVPlayer；<br>API声明：release(): Promise\<void>;<br>差异内容：release(): Promise\<void>;|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：AVPlayer；<br>API声明：seek(timeMs: number, mode?: SeekMode): void;<br>差异内容：seek(timeMs: number, mode?: SeekMode): void;|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：AVPlayer；<br>API声明：setVolume(volume: number): void;<br>差异内容：setVolume(volume: number): void;|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：AVPlayer；<br>API声明：getTrackDescription(callback: AsyncCallback\<Array\<MediaDescription>>): void;<br>差异内容：getTrackDescription(callback: AsyncCallback\<Array\<MediaDescription>>): void;|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：AVPlayer；<br>API声明：getTrackDescription(): Promise\<Array\<MediaDescription>>;<br>差异内容：getTrackDescription(): Promise\<Array\<MediaDescription>>;|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：AVPlayer；<br>API声明：url?: string;<br>差异内容：url?: string;|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：AVPlayer；<br>API声明：fdSrc?: AVFileDescriptor;<br>差异内容：fdSrc?: AVFileDescriptor;|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：AVPlayer；<br>API声明：dataSrc?: AVDataSrcDescriptor;<br>差异内容：dataSrc?: AVDataSrcDescriptor;|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：AVPlayer；<br>API声明：loop: boolean;<br>差异内容：loop: boolean;|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：AVPlayer；<br>API声明：audioInterruptMode?: audio.InterruptMode;<br>差异内容：audioInterruptMode?: audio.InterruptMode;|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：AVPlayer；<br>API声明：audioRendererInfo?: audio.AudioRendererInfo;<br>差异内容：audioRendererInfo?: audio.AudioRendererInfo;|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：AVPlayer；<br>API声明：audioEffectMode?: audio.AudioEffectMode;<br>差异内容：audioEffectMode?: audio.AudioEffectMode;|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：AVPlayer；<br>API声明：readonly currentTime: number;<br>差异内容：readonly currentTime: number;|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：AVPlayer；<br>API声明：readonly duration: number;<br>差异内容：readonly duration: number;|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：AVPlayer；<br>API声明：readonly state: AVPlayerState;<br>差异内容：readonly state: AVPlayerState;|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：AVPlayer；<br>API声明：surfaceId?: string;<br>差异内容：surfaceId?: string;|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：AVPlayer；<br>API声明：readonly width: number;<br>差异内容：readonly width: number;|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：AVPlayer；<br>API声明：readonly height: number;<br>差异内容：readonly height: number;|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：AVPlayer；<br>API声明：videoScaleType?: VideoScaleType;<br>差异内容：videoScaleType?: VideoScaleType;|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：AVPlayer；<br>API声明：setSpeed(speed: PlaybackSpeed): void;<br>差异内容：setSpeed(speed: PlaybackSpeed): void;|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：AVPlayer；<br>API声明：setBitrate(bitrate: number): void;<br>差异内容：setBitrate(bitrate: number): void;|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：AVPlayer；<br>API声明：setDecryptionConfig(mediaKeySession: drm.MediaKeySession, secureVideoPath: boolean): void;<br>差异内容：setDecryptionConfig(mediaKeySession: drm.MediaKeySession, secureVideoPath: boolean): void;|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：AVPlayer；<br>API声明：getMediaKeySystemInfos(): Array\<drm.MediaKeySystemInfo>;<br>差异内容：getMediaKeySystemInfos(): Array\<drm.MediaKeySystemInfo>;|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：AVPlayer；<br>API声明：on(type: 'mediaKeySystemInfoUpdate', callback: (mediaKeySystemInfo: Array\<drm.MediaKeySystemInfo>) => void): void;<br>差异内容：on(type: 'mediaKeySystemInfoUpdate', callback: (mediaKeySystemInfo: Array\<drm.MediaKeySystemInfo>) => void): void;|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：AVPlayer；<br>API声明：off(type: 'mediaKeySystemInfoUpdate', callback?: (mediaKeySystemInfo: Array\<drm.MediaKeySystemInfo>) => void): void;<br>差异内容：off(type: 'mediaKeySystemInfoUpdate', callback?: (mediaKeySystemInfo: Array\<drm.MediaKeySystemInfo>) => void): void;|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：AVPlayer；<br>API声明：on(type: 'stateChange', callback: (state: AVPlayerState, reason: StateChangeReason) => void): void;<br>差异内容：on(type: 'stateChange', callback: (state: AVPlayerState, reason: StateChangeReason) => void): void;|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：AVPlayer；<br>API声明：off(type: 'stateChange'): void;<br>差异内容：off(type: 'stateChange'): void;|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：AVPlayer；<br>API声明：on(type: 'volumeChange', callback: Callback\<number>): void;<br>差异内容：on(type: 'volumeChange', callback: Callback\<number>): void;|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：AVPlayer；<br>API声明：off(type: 'volumeChange'): void;<br>差异内容：off(type: 'volumeChange'): void;|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：AVPlayer；<br>API声明：on(type: 'endOfStream', callback: Callback\<void>): void;<br>差异内容：on(type: 'endOfStream', callback: Callback\<void>): void;|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：AVPlayer；<br>API声明：off(type: 'endOfStream'): void;<br>差异内容：off(type: 'endOfStream'): void;|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：AVPlayer；<br>API声明：on(type: 'seekDone', callback: Callback\<number>): void;<br>差异内容：on(type: 'seekDone', callback: Callback\<number>): void;|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：AVPlayer；<br>API声明：off(type: 'seekDone'): void;<br>差异内容：off(type: 'seekDone'): void;|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：AVPlayer；<br>API声明：on(type: 'speedDone', callback: Callback\<number>): void;<br>差异内容：on(type: 'speedDone', callback: Callback\<number>): void;|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：AVPlayer；<br>API声明：off(type: 'speedDone'): void;<br>差异内容：off(type: 'speedDone'): void;|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：AVPlayer；<br>API声明：on(type: 'bitrateDone', callback: Callback\<number>): void;<br>差异内容：on(type: 'bitrateDone', callback: Callback\<number>): void;|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：AVPlayer；<br>API声明：off(type: 'bitrateDone'): void;<br>差异内容：off(type: 'bitrateDone'): void;|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：AVPlayer；<br>API声明：on(type: 'timeUpdate', callback: Callback\<number>): void;<br>差异内容：on(type: 'timeUpdate', callback: Callback\<number>): void;|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：AVPlayer；<br>API声明：off(type: 'timeUpdate'): void;<br>差异内容：off(type: 'timeUpdate'): void;|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：AVPlayer；<br>API声明：on(type: 'durationUpdate', callback: Callback\<number>): void;<br>差异内容：on(type: 'durationUpdate', callback: Callback\<number>): void;|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：AVPlayer；<br>API声明：off(type: 'durationUpdate'): void;<br>差异内容：off(type: 'durationUpdate'): void;|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：AVPlayer；<br>API声明：on(type: 'bufferingUpdate', callback: (infoType: BufferingInfoType, value: number) => void): void;<br>差异内容：on(type: 'bufferingUpdate', callback: (infoType: BufferingInfoType, value: number) => void): void;|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：AVPlayer；<br>API声明：off(type: 'bufferingUpdate'): void;<br>差异内容：off(type: 'bufferingUpdate'): void;|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：AVPlayer；<br>API声明：on(type: 'startRenderFrame', callback: Callback\<void>): void;<br>差异内容：on(type: 'startRenderFrame', callback: Callback\<void>): void;|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：AVPlayer；<br>API声明：off(type: 'startRenderFrame'): void;<br>差异内容：off(type: 'startRenderFrame'): void;|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：AVPlayer；<br>API声明：on(type: 'videoSizeChange', callback: (width: number, height: number) => void): void;<br>差异内容：on(type: 'videoSizeChange', callback: (width: number, height: number) => void): void;|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：AVPlayer；<br>API声明：off(type: 'videoSizeChange'): void;<br>差异内容：off(type: 'videoSizeChange'): void;|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：AVPlayer；<br>API声明：on(type: 'audioInterrupt', callback: (info: audio.InterruptEvent) => void): void;<br>差异内容：on(type: 'audioInterrupt', callback: (info: audio.InterruptEvent) => void): void;|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：AVPlayer；<br>API声明：off(type: 'audioInterrupt'): void;<br>差异内容：off(type: 'audioInterrupt'): void;|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：AVPlayer；<br>API声明：on(type: 'availableBitrates', callback: (bitrates: Array\<number>) => void): void;<br>差异内容：on(type: 'availableBitrates', callback: (bitrates: Array\<number>) => void): void;|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：AVPlayer；<br>API声明：off(type: 'availableBitrates'): void;<br>差异内容：off(type: 'availableBitrates'): void;|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：AVPlayer；<br>API声明：on(type: 'error', callback: ErrorCallback): void;<br>差异内容：on(type: 'error', callback: ErrorCallback): void;|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：AVPlayer；<br>API声明：off(type: 'error'): void;<br>差异内容：off(type: 'error'): void;|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：AVPlayer；<br>API声明：on(type: 'audioOutputDeviceChangeWithInfo', callback: Callback\<audio.AudioStreamDeviceChangeInfo>): void;<br>差异内容：on(type: 'audioOutputDeviceChangeWithInfo', callback: Callback\<audio.AudioStreamDeviceChangeInfo>): void;|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：AVPlayer；<br>API声明：off(type: 'audioOutputDeviceChangeWithInfo', callback?: Callback\<audio.AudioStreamDeviceChangeInfo>): void;<br>差异内容：off(type: 'audioOutputDeviceChangeWithInfo', callback?: Callback\<audio.AudioStreamDeviceChangeInfo>): void;|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：media；<br>API声明：enum MediaErrorCode<br>差异内容：enum MediaErrorCode|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：MediaErrorCode；<br>API声明：MSERR_OK = 0<br>差异内容：MSERR_OK = 0|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：MediaErrorCode；<br>API声明：MSERR_NO_MEMORY = 1<br>差异内容：MSERR_NO_MEMORY = 1|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：MediaErrorCode；<br>API声明：MSERR_OPERATION_NOT_PERMIT = 2<br>差异内容：MSERR_OPERATION_NOT_PERMIT = 2|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：MediaErrorCode；<br>API声明：MSERR_INVALID_VAL = 3<br>差异内容：MSERR_INVALID_VAL = 3|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：MediaErrorCode；<br>API声明：MSERR_IO = 4<br>差异内容：MSERR_IO = 4|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：MediaErrorCode；<br>API声明：MSERR_TIMEOUT = 5<br>差异内容：MSERR_TIMEOUT = 5|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：MediaErrorCode；<br>API声明：MSERR_UNKNOWN = 6<br>差异内容：MSERR_UNKNOWN = 6|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：MediaErrorCode；<br>API声明：MSERR_SERVICE_DIED = 7<br>差异内容：MSERR_SERVICE_DIED = 7|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：MediaErrorCode；<br>API声明：MSERR_INVALID_STATE = 8<br>差异内容：MSERR_INVALID_STATE = 8|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：MediaErrorCode；<br>API声明：MSERR_UNSUPPORTED = 9<br>差异内容：MSERR_UNSUPPORTED = 9|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：media；<br>API声明：enum BufferingInfoType<br>差异内容：enum BufferingInfoType|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：BufferingInfoType；<br>API声明：BUFFERING_START = 1<br>差异内容：BUFFERING_START = 1|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：BufferingInfoType；<br>API声明：BUFFERING_END = 2<br>差异内容：BUFFERING_END = 2|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：BufferingInfoType；<br>API声明：BUFFERING_PERCENT = 3<br>差异内容：BUFFERING_PERCENT = 3|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：BufferingInfoType；<br>API声明：CACHED_DURATION = 4<br>差异内容：CACHED_DURATION = 4|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：media；<br>API声明：interface AVFileDescriptor<br>差异内容：interface AVFileDescriptor|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：AVFileDescriptor；<br>API声明：fd: number;<br>差异内容：fd: number;|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：AVFileDescriptor；<br>API声明：offset?: number;<br>差异内容：offset?: number;|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：AVFileDescriptor；<br>API声明：length?: number;<br>差异内容：length?: number;|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：media；<br>API声明：interface AVDataSrcDescriptor<br>差异内容：interface AVDataSrcDescriptor|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：AVDataSrcDescriptor；<br>API声明：fileSize: number;<br>差异内容：fileSize: number;|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：AVDataSrcDescriptor；<br>API声明：callback: (buffer: ArrayBuffer, length: number, pos?: number) => number;<br>差异内容：callback: (buffer: ArrayBuffer, length: number, pos?: number) => number;|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：media；<br>API声明：type AudioState = 'idle' \| 'playing' \| 'paused' \| 'stopped' \| 'error';<br>差异内容：type AudioState = 'idle' \| 'playing' \| 'paused' \| 'stopped' \| 'error';|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：media；<br>API声明：interface AudioPlayer<br>差异内容：interface AudioPlayer|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：AudioPlayer；<br>API声明：play(): void;<br>差异内容：play(): void;|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：AudioPlayer；<br>API声明：pause(): void;<br>差异内容：pause(): void;|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：AudioPlayer；<br>API声明：stop(): void;<br>差异内容：stop(): void;|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：AudioPlayer；<br>API声明：reset(): void;<br>差异内容：reset(): void;|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：AudioPlayer；<br>API声明：seek(timeMs: number): void;<br>差异内容：seek(timeMs: number): void;|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：AudioPlayer；<br>API声明：setVolume(vol: number): void;<br>差异内容：setVolume(vol: number): void;|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：AudioPlayer；<br>API声明：release(): void;<br>差异内容：release(): void;|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：AudioPlayer；<br>API声明：getTrackDescription(callback: AsyncCallback\<Array\<MediaDescription>>): void;<br>差异内容：getTrackDescription(callback: AsyncCallback\<Array\<MediaDescription>>): void;|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：AudioPlayer；<br>API声明：getTrackDescription(): Promise\<Array\<MediaDescription>>;<br>差异内容：getTrackDescription(): Promise\<Array\<MediaDescription>>;|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：AudioPlayer；<br>API声明：on(type: 'bufferingUpdate', callback: (infoType: BufferingInfoType, value: number) => void): void;<br>差异内容：on(type: 'bufferingUpdate', callback: (infoType: BufferingInfoType, value: number) => void): void;|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：AudioPlayer；<br>API声明：src: string;<br>差异内容：src: string;|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：AudioPlayer；<br>API声明：fdSrc: AVFileDescriptor;<br>差异内容：fdSrc: AVFileDescriptor;|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：AudioPlayer；<br>API声明：loop: boolean;<br>差异内容：loop: boolean;|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：AudioPlayer；<br>API声明：audioInterruptMode?: audio.InterruptMode;<br>差异内容：audioInterruptMode?: audio.InterruptMode;|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：AudioPlayer；<br>API声明：readonly currentTime: number;<br>差异内容：readonly currentTime: number;|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：AudioPlayer；<br>API声明：readonly duration: number;<br>差异内容：readonly duration: number;|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：AudioPlayer；<br>API声明：readonly state: AudioState;<br>差异内容：readonly state: AudioState;|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：AudioPlayer；<br>API声明：on(type: 'play' \| 'pause' \| 'stop' \| 'reset' \| 'dataLoad' \| 'finish' \| 'volumeChange', callback: () => void): void;<br>差异内容：on(type: 'play' \| 'pause' \| 'stop' \| 'reset' \| 'dataLoad' \| 'finish' \| 'volumeChange', callback: () => void): void;|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：AudioPlayer；<br>API声明：on(type: 'play' \| 'pause' \| 'stop' \| 'reset' \| 'dataLoad' \| 'finish' \| 'volumeChange', callback: () => void): void;<br>差异内容：on(type: 'play' \| 'pause' \| 'stop' \| 'reset' \| 'dataLoad' \| 'finish' \| 'volumeChange', callback: () => void): void;|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：AudioPlayer；<br>API声明：on(type: 'play' \| 'pause' \| 'stop' \| 'reset' \| 'dataLoad' \| 'finish' \| 'volumeChange', callback: () => void): void;<br>差异内容：on(type: 'play' \| 'pause' \| 'stop' \| 'reset' \| 'dataLoad' \| 'finish' \| 'volumeChange', callback: () => void): void;|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：AudioPlayer；<br>API声明：on(type: 'play' \| 'pause' \| 'stop' \| 'reset' \| 'dataLoad' \| 'finish' \| 'volumeChange', callback: () => void): void;<br>差异内容：on(type: 'play' \| 'pause' \| 'stop' \| 'reset' \| 'dataLoad' \| 'finish' \| 'volumeChange', callback: () => void): void;|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：AudioPlayer；<br>API声明：on(type: 'play' \| 'pause' \| 'stop' \| 'reset' \| 'dataLoad' \| 'finish' \| 'volumeChange', callback: () => void): void;<br>差异内容：on(type: 'play' \| 'pause' \| 'stop' \| 'reset' \| 'dataLoad' \| 'finish' \| 'volumeChange', callback: () => void): void;|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：AudioPlayer；<br>API声明：on(type: 'play' \| 'pause' \| 'stop' \| 'reset' \| 'dataLoad' \| 'finish' \| 'volumeChange', callback: () => void): void;<br>差异内容：on(type: 'play' \| 'pause' \| 'stop' \| 'reset' \| 'dataLoad' \| 'finish' \| 'volumeChange', callback: () => void): void;|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：AudioPlayer；<br>API声明：on(type: 'play' \| 'pause' \| 'stop' \| 'reset' \| 'dataLoad' \| 'finish' \| 'volumeChange', callback: () => void): void;<br>差异内容：on(type: 'play' \| 'pause' \| 'stop' \| 'reset' \| 'dataLoad' \| 'finish' \| 'volumeChange', callback: () => void): void;|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：AudioPlayer；<br>API声明：on(type: 'timeUpdate', callback: Callback\<number>): void;<br>差异内容：on(type: 'timeUpdate', callback: Callback\<number>): void;|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：AudioPlayer；<br>API声明：on(type: 'audioInterrupt', callback: (info: audio.InterruptEvent) => void): void;<br>差异内容：on(type: 'audioInterrupt', callback: (info: audio.InterruptEvent) => void): void;|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：AudioPlayer；<br>API声明：on(type: 'error', callback: ErrorCallback): void;<br>差异内容：on(type: 'error', callback: ErrorCallback): void;|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：media；<br>API声明：type AVRecorderState = 'idle' \| 'prepared' \| 'started' \| 'paused' \| 'stopped' \| 'released' \| 'error';<br>差异内容：type AVRecorderState = 'idle' \| 'prepared' \| 'started' \| 'paused' \| 'stopped' \| 'released' \| 'error';|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：media；<br>API声明：interface AVRecorder<br>差异内容：interface AVRecorder|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：AVRecorder；<br>API声明：prepare(config: AVRecorderConfig, callback: AsyncCallback\<void>): void;<br>差异内容：prepare(config: AVRecorderConfig, callback: AsyncCallback\<void>): void;|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：AVRecorder；<br>API声明：prepare(config: AVRecorderConfig): Promise\<void>;<br>差异内容：prepare(config: AVRecorderConfig): Promise\<void>;|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：AVRecorder；<br>API声明：getAVRecorderConfig(callback: AsyncCallback\<AVRecorderConfig>): void;<br>差异内容：getAVRecorderConfig(callback: AsyncCallback\<AVRecorderConfig>): void;|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：AVRecorder；<br>API声明：getAVRecorderConfig(): Promise\<AVRecorderConfig>;<br>差异内容：getAVRecorderConfig(): Promise\<AVRecorderConfig>;|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：AVRecorder；<br>API声明：getInputSurface(callback: AsyncCallback\<string>): void;<br>差异内容：getInputSurface(callback: AsyncCallback\<string>): void;|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：AVRecorder；<br>API声明：getInputSurface(): Promise\<string>;<br>差异内容：getInputSurface(): Promise\<string>;|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：AVRecorder；<br>API声明：start(callback: AsyncCallback\<void>): void;<br>差异内容：start(callback: AsyncCallback\<void>): void;|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：AVRecorder；<br>API声明：start(): Promise\<void>;<br>差异内容：start(): Promise\<void>;|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：AVRecorder；<br>API声明：pause(callback: AsyncCallback\<void>): void;<br>差异内容：pause(callback: AsyncCallback\<void>): void;|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：AVRecorder；<br>API声明：pause(): Promise\<void>;<br>差异内容：pause(): Promise\<void>;|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：AVRecorder；<br>API声明：resume(callback: AsyncCallback\<void>): void;<br>差异内容：resume(callback: AsyncCallback\<void>): void;|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：AVRecorder；<br>API声明：resume(): Promise\<void>;<br>差异内容：resume(): Promise\<void>;|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：AVRecorder；<br>API声明：stop(callback: AsyncCallback\<void>): void;<br>差异内容：stop(callback: AsyncCallback\<void>): void;|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：AVRecorder；<br>API声明：stop(): Promise\<void>;<br>差异内容：stop(): Promise\<void>;|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：AVRecorder；<br>API声明：reset(callback: AsyncCallback\<void>): void;<br>差异内容：reset(callback: AsyncCallback\<void>): void;|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：AVRecorder；<br>API声明：reset(): Promise\<void>;<br>差异内容：reset(): Promise\<void>;|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：AVRecorder；<br>API声明：release(callback: AsyncCallback\<void>): void;<br>差异内容：release(callback: AsyncCallback\<void>): void;|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：AVRecorder；<br>API声明：release(): Promise\<void>;<br>差异内容：release(): Promise\<void>;|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：AVRecorder；<br>API声明：getCurrentAudioCapturerInfo(callback: AsyncCallback\<audio.AudioCapturerChangeInfo>): void;<br>差异内容：getCurrentAudioCapturerInfo(callback: AsyncCallback\<audio.AudioCapturerChangeInfo>): void;|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：AVRecorder；<br>API声明：getCurrentAudioCapturerInfo(): Promise\<audio.AudioCapturerChangeInfo>;<br>差异内容：getCurrentAudioCapturerInfo(): Promise\<audio.AudioCapturerChangeInfo>;|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：AVRecorder；<br>API声明：getAudioCapturerMaxAmplitude(callback: AsyncCallback\<number>): void;<br>差异内容：getAudioCapturerMaxAmplitude(callback: AsyncCallback\<number>): void;|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：AVRecorder；<br>API声明：getAudioCapturerMaxAmplitude(): Promise\<number>;<br>差异内容：getAudioCapturerMaxAmplitude(): Promise\<number>;|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：AVRecorder；<br>API声明：getAvailableEncoder(callback: AsyncCallback\<Array\<EncoderInfo>>): void;<br>差异内容：getAvailableEncoder(callback: AsyncCallback\<Array\<EncoderInfo>>): void;|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：AVRecorder；<br>API声明：getAvailableEncoder(): Promise\<Array\<EncoderInfo>>;<br>差异内容：getAvailableEncoder(): Promise\<Array\<EncoderInfo>>;|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：AVRecorder；<br>API声明：readonly state: AVRecorderState;<br>差异内容：readonly state: AVRecorderState;|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：AVRecorder；<br>API声明：on(type: 'audioCapturerChange', callback: Callback\<audio.AudioCapturerChangeInfo>): void;<br>差异内容：on(type: 'audioCapturerChange', callback: Callback\<audio.AudioCapturerChangeInfo>): void;|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：AVRecorder；<br>API声明：on(type: 'stateChange', callback: (state: AVRecorderState, reason: StateChangeReason) => void): void;<br>差异内容：on(type: 'stateChange', callback: (state: AVRecorderState, reason: StateChangeReason) => void): void;|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：AVRecorder；<br>API声明：on(type: 'error', callback: ErrorCallback): void;<br>差异内容：on(type: 'error', callback: ErrorCallback): void;|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：AVRecorder；<br>API声明：off(type: 'stateChange'): void;<br>差异内容：off(type: 'stateChange'): void;|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：AVRecorder；<br>API声明：off(type: 'error'): void;<br>差异内容：off(type: 'error'): void;|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：AVRecorder；<br>API声明：off(type: 'audioCapturerChange'): void;<br>差异内容：off(type: 'audioCapturerChange'): void;|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：media；<br>API声明：enum AudioEncoder<br>差异内容：enum AudioEncoder|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：AudioEncoder；<br>API声明：DEFAULT = 0<br>差异内容：DEFAULT = 0|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：AudioEncoder；<br>API声明：AMR_NB = 1<br>差异内容：AMR_NB = 1|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：AudioEncoder；<br>API声明：AMR_WB = 2<br>差异内容：AMR_WB = 2|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：AudioEncoder；<br>API声明：AAC_LC = 3<br>差异内容：AAC_LC = 3|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：AudioEncoder；<br>API声明：HE_AAC = 4<br>差异内容：HE_AAC = 4|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：media；<br>API声明：enum AudioOutputFormat<br>差异内容：enum AudioOutputFormat|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：AudioOutputFormat；<br>API声明：DEFAULT = 0<br>差异内容：DEFAULT = 0|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：AudioOutputFormat；<br>API声明：MPEG_4 = 2<br>差异内容：MPEG_4 = 2|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：AudioOutputFormat；<br>API声明：AMR_NB = 3<br>差异内容：AMR_NB = 3|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：AudioOutputFormat；<br>API声明：AMR_WB = 4<br>差异内容：AMR_WB = 4|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：AudioOutputFormat；<br>API声明：AAC_ADTS = 6<br>差异内容：AAC_ADTS = 6|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：media；<br>API声明：interface Location<br>差异内容：interface Location|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：Location；<br>API声明：latitude: number;<br>差异内容：latitude: number;|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：Location；<br>API声明：longitude: number;<br>差异内容：longitude: number;|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：media；<br>API声明：interface AudioRecorderConfig<br>差异内容：interface AudioRecorderConfig|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：AudioRecorderConfig；<br>API声明：audioEncoder?: AudioEncoder;<br>差异内容：audioEncoder?: AudioEncoder;|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：AudioRecorderConfig；<br>API声明：audioEncodeBitRate?: number;<br>差异内容：audioEncodeBitRate?: number;|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：AudioRecorderConfig；<br>API声明：audioSampleRate?: number;<br>差异内容：audioSampleRate?: number;|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：AudioRecorderConfig；<br>API声明：numberOfChannels?: number;<br>差异内容：numberOfChannels?: number;|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：AudioRecorderConfig；<br>API声明：format?: AudioOutputFormat;<br>差异内容：format?: AudioOutputFormat;|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：AudioRecorderConfig；<br>API声明：uri: string;<br>差异内容：uri: string;|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：AudioRecorderConfig；<br>API声明：location?: Location;<br>差异内容：location?: Location;|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：AudioRecorderConfig；<br>API声明：audioEncoderMime?: CodecMimeType;<br>差异内容：audioEncoderMime?: CodecMimeType;|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：AudioRecorderConfig；<br>API声明：fileFormat?: ContainerFormatType;<br>差异内容：fileFormat?: ContainerFormatType;|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：media；<br>API声明：interface AudioRecorder<br>差异内容：interface AudioRecorder|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：AudioRecorder；<br>API声明：prepare(config: AudioRecorderConfig): void;<br>差异内容：prepare(config: AudioRecorderConfig): void;|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：AudioRecorder；<br>API声明：start(): void;<br>差异内容：start(): void;|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：AudioRecorder；<br>API声明：pause(): void;<br>差异内容：pause(): void;|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：AudioRecorder；<br>API声明：resume(): void;<br>差异内容：resume(): void;|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：AudioRecorder；<br>API声明：stop(): void;<br>差异内容：stop(): void;|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：AudioRecorder；<br>API声明：release(): void;<br>差异内容：release(): void;|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：AudioRecorder；<br>API声明：reset(): void;<br>差异内容：reset(): void;|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：AudioRecorder；<br>API声明：on(type: 'prepare' \| 'start' \| 'pause' \| 'resume' \| 'stop' \| 'release' \| 'reset', callback: () => void): void;<br>差异内容：on(type: 'prepare' \| 'start' \| 'pause' \| 'resume' \| 'stop' \| 'release' \| 'reset', callback: () => void): void;|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：AudioRecorder；<br>API声明：on(type: 'prepare' \| 'start' \| 'pause' \| 'resume' \| 'stop' \| 'release' \| 'reset', callback: () => void): void;<br>差异内容：on(type: 'prepare' \| 'start' \| 'pause' \| 'resume' \| 'stop' \| 'release' \| 'reset', callback: () => void): void;|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：AudioRecorder；<br>API声明：on(type: 'prepare' \| 'start' \| 'pause' \| 'resume' \| 'stop' \| 'release' \| 'reset', callback: () => void): void;<br>差异内容：on(type: 'prepare' \| 'start' \| 'pause' \| 'resume' \| 'stop' \| 'release' \| 'reset', callback: () => void): void;|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：AudioRecorder；<br>API声明：on(type: 'prepare' \| 'start' \| 'pause' \| 'resume' \| 'stop' \| 'release' \| 'reset', callback: () => void): void;<br>差异内容：on(type: 'prepare' \| 'start' \| 'pause' \| 'resume' \| 'stop' \| 'release' \| 'reset', callback: () => void): void;|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：AudioRecorder；<br>API声明：on(type: 'prepare' \| 'start' \| 'pause' \| 'resume' \| 'stop' \| 'release' \| 'reset', callback: () => void): void;<br>差异内容：on(type: 'prepare' \| 'start' \| 'pause' \| 'resume' \| 'stop' \| 'release' \| 'reset', callback: () => void): void;|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：AudioRecorder；<br>API声明：on(type: 'prepare' \| 'start' \| 'pause' \| 'resume' \| 'stop' \| 'release' \| 'reset', callback: () => void): void;<br>差异内容：on(type: 'prepare' \| 'start' \| 'pause' \| 'resume' \| 'stop' \| 'release' \| 'reset', callback: () => void): void;|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：AudioRecorder；<br>API声明：on(type: 'prepare' \| 'start' \| 'pause' \| 'resume' \| 'stop' \| 'release' \| 'reset', callback: () => void): void;<br>差异内容：on(type: 'prepare' \| 'start' \| 'pause' \| 'resume' \| 'stop' \| 'release' \| 'reset', callback: () => void): void;|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：AudioRecorder；<br>API声明：on(type: 'error', callback: ErrorCallback): void;<br>差异内容：on(type: 'error', callback: ErrorCallback): void;|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：media；<br>API声明：type VideoPlayState = 'idle' \| 'prepared' \| 'playing' \| 'paused' \| 'stopped' \| 'error';<br>差异内容：type VideoPlayState = 'idle' \| 'prepared' \| 'playing' \| 'paused' \| 'stopped' \| 'error';|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：media；<br>API声明：enum PlaybackSpeed<br>差异内容：enum PlaybackSpeed|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：PlaybackSpeed；<br>API声明：SPEED_FORWARD_0_75_X = 0<br>差异内容：SPEED_FORWARD_0_75_X = 0|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：PlaybackSpeed；<br>API声明：SPEED_FORWARD_1_00_X = 1<br>差异内容：SPEED_FORWARD_1_00_X = 1|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：PlaybackSpeed；<br>API声明：SPEED_FORWARD_1_25_X = 2<br>差异内容：SPEED_FORWARD_1_25_X = 2|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：PlaybackSpeed；<br>API声明：SPEED_FORWARD_1_75_X = 3<br>差异内容：SPEED_FORWARD_1_75_X = 3|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：PlaybackSpeed；<br>API声明：SPEED_FORWARD_2_00_X = 4<br>差异内容：SPEED_FORWARD_2_00_X = 4|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：media；<br>API声明：interface VideoPlayer<br>差异内容：interface VideoPlayer|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：VideoPlayer；<br>API声明：setDisplaySurface(surfaceId: string, callback: AsyncCallback\<void>): void;<br>差异内容：setDisplaySurface(surfaceId: string, callback: AsyncCallback\<void>): void;|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：VideoPlayer；<br>API声明：setDisplaySurface(surfaceId: string): Promise\<void>;<br>差异内容：setDisplaySurface(surfaceId: string): Promise\<void>;|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：VideoPlayer；<br>API声明：prepare(callback: AsyncCallback\<void>): void;<br>差异内容：prepare(callback: AsyncCallback\<void>): void;|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：VideoPlayer；<br>API声明：prepare(): Promise\<void>;<br>差异内容：prepare(): Promise\<void>;|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：VideoPlayer；<br>API声明：play(callback: AsyncCallback\<void>): void;<br>差异内容：play(callback: AsyncCallback\<void>): void;|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：VideoPlayer；<br>API声明：play(): Promise\<void>;<br>差异内容：play(): Promise\<void>;|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：VideoPlayer；<br>API声明：pause(callback: AsyncCallback\<void>): void;<br>差异内容：pause(callback: AsyncCallback\<void>): void;|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：VideoPlayer；<br>API声明：pause(): Promise\<void>;<br>差异内容：pause(): Promise\<void>;|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：VideoPlayer；<br>API声明：stop(callback: AsyncCallback\<void>): void;<br>差异内容：stop(callback: AsyncCallback\<void>): void;|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：VideoPlayer；<br>API声明：stop(): Promise\<void>;<br>差异内容：stop(): Promise\<void>;|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：VideoPlayer；<br>API声明：reset(callback: AsyncCallback\<void>): void;<br>差异内容：reset(callback: AsyncCallback\<void>): void;|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：VideoPlayer；<br>API声明：reset(): Promise\<void>;<br>差异内容：reset(): Promise\<void>;|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：VideoPlayer；<br>API声明：seek(timeMs: number, callback: AsyncCallback\<number>): void;<br>差异内容：seek(timeMs: number, callback: AsyncCallback\<number>): void;|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：VideoPlayer；<br>API声明：seek(timeMs: number, mode: SeekMode, callback: AsyncCallback\<number>): void;<br>差异内容：seek(timeMs: number, mode: SeekMode, callback: AsyncCallback\<number>): void;|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：VideoPlayer；<br>API声明：seek(timeMs: number, mode?: SeekMode): Promise\<number>;<br>差异内容：seek(timeMs: number, mode?: SeekMode): Promise\<number>;|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：VideoPlayer；<br>API声明：setVolume(vol: number, callback: AsyncCallback\<void>): void;<br>差异内容：setVolume(vol: number, callback: AsyncCallback\<void>): void;|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：VideoPlayer；<br>API声明：setVolume(vol: number): Promise\<void>;<br>差异内容：setVolume(vol: number): Promise\<void>;|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：VideoPlayer；<br>API声明：release(callback: AsyncCallback\<void>): void;<br>差异内容：release(callback: AsyncCallback\<void>): void;|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：VideoPlayer；<br>API声明：release(): Promise\<void>;<br>差异内容：release(): Promise\<void>;|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：VideoPlayer；<br>API声明：getTrackDescription(callback: AsyncCallback\<Array\<MediaDescription>>): void;<br>差异内容：getTrackDescription(callback: AsyncCallback\<Array\<MediaDescription>>): void;|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：VideoPlayer；<br>API声明：getTrackDescription(): Promise\<Array\<MediaDescription>>;<br>差异内容：getTrackDescription(): Promise\<Array\<MediaDescription>>;|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：VideoPlayer；<br>API声明：url: string;<br>差异内容：url: string;|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：VideoPlayer；<br>API声明：fdSrc: AVFileDescriptor;<br>差异内容：fdSrc: AVFileDescriptor;|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：VideoPlayer；<br>API声明：loop: boolean;<br>差异内容：loop: boolean;|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：VideoPlayer；<br>API声明：readonly currentTime: number;<br>差异内容：readonly currentTime: number;|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：VideoPlayer；<br>API声明：readonly duration: number;<br>差异内容：readonly duration: number;|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：VideoPlayer；<br>API声明：readonly state: VideoPlayState;<br>差异内容：readonly state: VideoPlayState;|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：VideoPlayer；<br>API声明：readonly width: number;<br>差异内容：readonly width: number;|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：VideoPlayer；<br>API声明：readonly height: number;<br>差异内容：readonly height: number;|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：VideoPlayer；<br>API声明：audioInterruptMode?: audio.InterruptMode;<br>差异内容：audioInterruptMode?: audio.InterruptMode;|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：VideoPlayer；<br>API声明：videoScaleType?: VideoScaleType;<br>差异内容：videoScaleType?: VideoScaleType;|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：VideoPlayer；<br>API声明：setSpeed(speed: number, callback: AsyncCallback\<number>): void;<br>差异内容：setSpeed(speed: number, callback: AsyncCallback\<number>): void;|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：VideoPlayer；<br>API声明：setSpeed(speed: number): Promise\<number>;<br>差异内容：setSpeed(speed: number): Promise\<number>;|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：VideoPlayer；<br>API声明：on(type: 'playbackCompleted', callback: Callback\<void>): void;<br>差异内容：on(type: 'playbackCompleted', callback: Callback\<void>): void;|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：VideoPlayer；<br>API声明：on(type: 'bufferingUpdate', callback: (infoType: BufferingInfoType, value: number) => void): void;<br>差异内容：on(type: 'bufferingUpdate', callback: (infoType: BufferingInfoType, value: number) => void): void;|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：VideoPlayer；<br>API声明：on(type: 'startRenderFrame', callback: Callback\<void>): void;<br>差异内容：on(type: 'startRenderFrame', callback: Callback\<void>): void;|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：VideoPlayer；<br>API声明：on(type: 'videoSizeChanged', callback: (width: number, height: number) => void): void;<br>差异内容：on(type: 'videoSizeChanged', callback: (width: number, height: number) => void): void;|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：VideoPlayer；<br>API声明：on(type: 'audioInterrupt', callback: (info: audio.InterruptEvent) => void): void;<br>差异内容：on(type: 'audioInterrupt', callback: (info: audio.InterruptEvent) => void): void;|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：VideoPlayer；<br>API声明：on(type: 'error', callback: ErrorCallback): void;<br>差异内容：on(type: 'error', callback: ErrorCallback): void;|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：media；<br>API声明：enum VideoScaleType<br>差异内容：enum VideoScaleType|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：VideoScaleType；<br>API声明：VIDEO_SCALE_TYPE_FIT = 0<br>差异内容：VIDEO_SCALE_TYPE_FIT = 0|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：VideoScaleType；<br>API声明：VIDEO_SCALE_TYPE_FIT_CROP = 1<br>差异内容：VIDEO_SCALE_TYPE_FIT_CROP = 1|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：media；<br>API声明：enum ContainerFormatType<br>差异内容：enum ContainerFormatType|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：ContainerFormatType；<br>API声明：CFT_MPEG_4 = 'mp4'<br>差异内容：CFT_MPEG_4 = 'mp4'|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：ContainerFormatType；<br>API声明：CFT_MPEG_4A = 'm4a'<br>差异内容：CFT_MPEG_4A = 'm4a'|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：media；<br>API声明：enum MediaType<br>差异内容：enum MediaType|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：MediaType；<br>API声明：MEDIA_TYPE_AUD = 0<br>差异内容：MEDIA_TYPE_AUD = 0|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：MediaType；<br>API声明：MEDIA_TYPE_VID = 1<br>差异内容：MEDIA_TYPE_VID = 1|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：media；<br>API声明：enum MediaDescriptionKey<br>差异内容：enum MediaDescriptionKey|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：MediaDescriptionKey；<br>API声明：MD_KEY_TRACK_INDEX = 'track_index'<br>差异内容：MD_KEY_TRACK_INDEX = 'track_index'|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：MediaDescriptionKey；<br>API声明：MD_KEY_TRACK_TYPE = 'track_type'<br>差异内容：MD_KEY_TRACK_TYPE = 'track_type'|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：MediaDescriptionKey；<br>API声明：MD_KEY_CODEC_MIME = 'codec_mime'<br>差异内容：MD_KEY_CODEC_MIME = 'codec_mime'|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：MediaDescriptionKey；<br>API声明：MD_KEY_DURATION = 'duration'<br>差异内容：MD_KEY_DURATION = 'duration'|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：MediaDescriptionKey；<br>API声明：MD_KEY_BITRATE = 'bitrate'<br>差异内容：MD_KEY_BITRATE = 'bitrate'|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：MediaDescriptionKey；<br>API声明：MD_KEY_WIDTH = 'width'<br>差异内容：MD_KEY_WIDTH = 'width'|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：MediaDescriptionKey；<br>API声明：MD_KEY_HEIGHT = 'height'<br>差异内容：MD_KEY_HEIGHT = 'height'|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：MediaDescriptionKey；<br>API声明：MD_KEY_FRAME_RATE = 'frame_rate'<br>差异内容：MD_KEY_FRAME_RATE = 'frame_rate'|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：MediaDescriptionKey；<br>API声明：MD_KEY_AUD_CHANNEL_COUNT = 'channel_count'<br>差异内容：MD_KEY_AUD_CHANNEL_COUNT = 'channel_count'|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：MediaDescriptionKey；<br>API声明：MD_KEY_AUD_SAMPLE_RATE = 'sample_rate'<br>差异内容：MD_KEY_AUD_SAMPLE_RATE = 'sample_rate'|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：media；<br>API声明：enum AudioSourceType<br>差异内容：enum AudioSourceType|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：AudioSourceType；<br>API声明：AUDIO_SOURCE_TYPE_DEFAULT = 0<br>差异内容：AUDIO_SOURCE_TYPE_DEFAULT = 0|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：AudioSourceType；<br>API声明：AUDIO_SOURCE_TYPE_MIC = 1<br>差异内容：AUDIO_SOURCE_TYPE_MIC = 1|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：media；<br>API声明：enum VideoSourceType<br>差异内容：enum VideoSourceType|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：VideoSourceType；<br>API声明：VIDEO_SOURCE_TYPE_SURFACE_YUV = 0<br>差异内容：VIDEO_SOURCE_TYPE_SURFACE_YUV = 0|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：VideoSourceType；<br>API声明：VIDEO_SOURCE_TYPE_SURFACE_ES = 1<br>差异内容：VIDEO_SOURCE_TYPE_SURFACE_ES = 1|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：media；<br>API声明：interface EncoderInfo<br>差异内容：interface EncoderInfo|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：EncoderInfo；<br>API声明：mimeType: CodecMimeType;<br>差异内容：mimeType: CodecMimeType;|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：EncoderInfo；<br>API声明：type: string;<br>差异内容：type: string;|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：EncoderInfo；<br>API声明：bitRate?: Range;<br>差异内容：bitRate?: Range;|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：EncoderInfo；<br>API声明：frameRate?: Range;<br>差异内容：frameRate?: Range;|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：EncoderInfo；<br>API声明：width?: Range;<br>差异内容：width?: Range;|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：EncoderInfo；<br>API声明：height?: Range;<br>差异内容：height?: Range;|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：EncoderInfo；<br>API声明：channels?: Range;<br>差异内容：channels?: Range;|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：EncoderInfo；<br>API声明：sampleRate?: Array\<number>;<br>差异内容：sampleRate?: Array\<number>;|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：media；<br>API声明：interface Range<br>差异内容：interface Range|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：Range；<br>API声明：min: number;<br>差异内容：min: number;|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：Range；<br>API声明：max: number;<br>差异内容：max: number;|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：media；<br>API声明：interface AVRecorderProfile<br>差异内容：interface AVRecorderProfile|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：AVRecorderProfile；<br>API声明：audioBitrate?: number;<br>差异内容：audioBitrate?: number;|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：AVRecorderProfile；<br>API声明：audioChannels?: number;<br>差异内容：audioChannels?: number;|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：AVRecorderProfile；<br>API声明：audioCodec?: CodecMimeType;<br>差异内容：audioCodec?: CodecMimeType;|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：AVRecorderProfile；<br>API声明：audioSampleRate?: number;<br>差异内容：audioSampleRate?: number;|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：AVRecorderProfile；<br>API声明：fileFormat: ContainerFormatType;<br>差异内容：fileFormat: ContainerFormatType;|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：AVRecorderProfile；<br>API声明：videoBitrate?: number;<br>差异内容：videoBitrate?: number;|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：AVRecorderProfile；<br>API声明：videoCodec?: CodecMimeType;<br>差异内容：videoCodec?: CodecMimeType;|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：AVRecorderProfile；<br>API声明：videoFrameWidth?: number;<br>差异内容：videoFrameWidth?: number;|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：AVRecorderProfile；<br>API声明：videoFrameHeight?: number;<br>差异内容：videoFrameHeight?: number;|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：AVRecorderProfile；<br>API声明：videoFrameRate?: number;<br>差异内容：videoFrameRate?: number;|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：AVRecorderProfile；<br>API声明：isHdr?: boolean;<br>差异内容：isHdr?: boolean;|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：media；<br>API声明：interface AVRecorderConfig<br>差异内容：interface AVRecorderConfig|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：AVRecorderConfig；<br>API声明：audioSourceType?: AudioSourceType;<br>差异内容：audioSourceType?: AudioSourceType;|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：AVRecorderConfig；<br>API声明：videoSourceType?: VideoSourceType;<br>差异内容：videoSourceType?: VideoSourceType;|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：AVRecorderConfig；<br>API声明：profile: AVRecorderProfile;<br>差异内容：profile: AVRecorderProfile;|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：AVRecorderConfig；<br>API声明：url: string;<br>差异内容：url: string;|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：AVRecorderConfig；<br>API声明：rotation?: number;<br>差异内容：rotation?: number;|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：AVRecorderConfig；<br>API声明：location?: Location;<br>差异内容：location?: Location;|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：media；<br>API声明：interface MediaDescription<br>差异内容：interface MediaDescription|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：MediaDescription；<br>API声明：[key: string]: Object;<br>差异内容：[key: string]: Object;|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：media；<br>API声明：enum SeekMode<br>差异内容：enum SeekMode|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：SeekMode；<br>API声明：SEEK_NEXT_SYNC = 0<br>差异内容：SEEK_NEXT_SYNC = 0|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：SeekMode；<br>API声明：SEEK_PREV_SYNC = 1<br>差异内容：SEEK_PREV_SYNC = 1|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：media；<br>API声明：enum CodecMimeType<br>差异内容：enum CodecMimeType|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：CodecMimeType；<br>API声明：VIDEO_H263 = 'video/h263'<br>差异内容：VIDEO_H263 = 'video/h263'|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：CodecMimeType；<br>API声明：VIDEO_AVC = 'video/avc'<br>差异内容：VIDEO_AVC = 'video/avc'|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：CodecMimeType；<br>API声明：VIDEO_MPEG2 = 'video/mpeg2'<br>差异内容：VIDEO_MPEG2 = 'video/mpeg2'|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：CodecMimeType；<br>API声明：VIDEO_MPEG4 = 'video/mp4v-es'<br>差异内容：VIDEO_MPEG4 = 'video/mp4v-es'|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：CodecMimeType；<br>API声明：VIDEO_VP8 = 'video/x-vnd.on2.vp8'<br>差异内容：VIDEO_VP8 = 'video/x-vnd.on2.vp8'|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：CodecMimeType；<br>API声明：AUDIO_AAC = 'audio/mp4a-latm'<br>差异内容：AUDIO_AAC = 'audio/mp4a-latm'|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：CodecMimeType；<br>API声明：AUDIO_VORBIS = 'audio/vorbis'<br>差异内容：AUDIO_VORBIS = 'audio/vorbis'|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：CodecMimeType；<br>API声明：AUDIO_FLAC = 'audio/flac'<br>差异内容：AUDIO_FLAC = 'audio/flac'|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：CodecMimeType；<br>API声明：VIDEO_HEVC = 'video/hevc'<br>差异内容：VIDEO_HEVC = 'video/hevc'|api/@ohos.multimedia.media.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\@ohos.multimedia.media.d.ts<br>差异内容：MediaKit|api/@ohos.multimedia.media.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：kits\@kit.MediaKit.d.ts<br>差异内容：MediaKit|kits/@kit.MediaKit.d.ts|
