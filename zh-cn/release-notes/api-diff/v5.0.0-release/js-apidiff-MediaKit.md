| 操作 | 旧版本 | 新版本 | d.ts文件 |
| ---- | ------ | ------ | -------- |
|API跨平台权限变更|类名：global；<br>API声明：declare namespace media<br>差异内容：NA|类名：global；<br>API声明：declare namespace media<br>差异内容：crossplatform|api/@ohos.multimedia.media.d.ts|
|API跨平台权限变更|类名：media；<br>API声明：function createAVPlayer(callback: AsyncCallback\<AVPlayer>): void;<br>差异内容：NA|类名：media；<br>API声明：function createAVPlayer(callback: AsyncCallback\<AVPlayer>): void;<br>差异内容：crossplatform|api/@ohos.multimedia.media.d.ts|
|API跨平台权限变更|类名：media；<br>API声明：function createAVPlayer(): Promise\<AVPlayer>;<br>差异内容：NA|类名：media；<br>API声明：function createAVPlayer(): Promise\<AVPlayer>;<br>差异内容：crossplatform|api/@ohos.multimedia.media.d.ts|
|API跨平台权限变更|类名：media；<br>API声明：function createAVRecorder(callback: AsyncCallback\<AVRecorder>): void;<br>差异内容：NA|类名：media；<br>API声明：function createAVRecorder(callback: AsyncCallback\<AVRecorder>): void;<br>差异内容：crossplatform|api/@ohos.multimedia.media.d.ts|
|API跨平台权限变更|类名：media；<br>API声明：function createAVRecorder(): Promise\<AVRecorder>;<br>差异内容：NA|类名：media；<br>API声明：function createAVRecorder(): Promise\<AVRecorder>;<br>差异内容：crossplatform|api/@ohos.multimedia.media.d.ts|
|API跨平台权限变更|类名：media；<br>API声明：enum StateChangeReason<br>差异内容：NA|类名：media；<br>API声明：enum StateChangeReason<br>差异内容：crossplatform|api/@ohos.multimedia.media.d.ts|
|API跨平台权限变更|类名：StateChangeReason；<br>API声明：USER = 1<br>差异内容：NA|类名：StateChangeReason；<br>API声明：USER = 1<br>差异内容：crossplatform|api/@ohos.multimedia.media.d.ts|
|API跨平台权限变更|类名：StateChangeReason；<br>API声明：BACKGROUND = 2<br>差异内容：NA|类名：StateChangeReason；<br>API声明：BACKGROUND = 2<br>差异内容：crossplatform|api/@ohos.multimedia.media.d.ts|
|API跨平台权限变更|类名：media；<br>API声明：function createAVMetadataExtractor(): Promise\<AVMetadataExtractor>;<br>差异内容：NA|类名：media；<br>API声明：function createAVMetadataExtractor(): Promise\<AVMetadataExtractor>;<br>差异内容：crossplatform|api/@ohos.multimedia.media.d.ts|
|API跨平台权限变更|类名：media；<br>API声明：function createAVMetadataExtractor(callback: AsyncCallback\<AVMetadataExtractor>): void;<br>差异内容：NA|类名：media；<br>API声明：function createAVMetadataExtractor(callback: AsyncCallback\<AVMetadataExtractor>): void;<br>差异内容：crossplatform|api/@ohos.multimedia.media.d.ts|
|API跨平台权限变更|类名：media；<br>API声明：interface AVMetadataExtractor<br>差异内容：NA|类名：media；<br>API声明：interface AVMetadataExtractor<br>差异内容：crossplatform|api/@ohos.multimedia.media.d.ts|
|API跨平台权限变更|类名：AVMetadataExtractor；<br>API声明：fdSrc?: AVFileDescriptor;<br>差异内容：NA|类名：AVMetadataExtractor；<br>API声明：fdSrc?: AVFileDescriptor;<br>差异内容：crossplatform|api/@ohos.multimedia.media.d.ts|
|API跨平台权限变更|类名：AVMetadataExtractor；<br>API声明：dataSrc?: AVDataSrcDescriptor;<br>差异内容：NA|类名：AVMetadataExtractor；<br>API声明：dataSrc?: AVDataSrcDescriptor;<br>差异内容：crossplatform|api/@ohos.multimedia.media.d.ts|
|API跨平台权限变更|类名：AVMetadataExtractor；<br>API声明：fetchMetadata(callback: AsyncCallback\<AVMetadata>): void;<br>差异内容：NA|类名：AVMetadataExtractor；<br>API声明：fetchMetadata(callback: AsyncCallback\<AVMetadata>): void;<br>差异内容：crossplatform|api/@ohos.multimedia.media.d.ts|
|API跨平台权限变更|类名：AVMetadataExtractor；<br>API声明：fetchMetadata(): Promise\<AVMetadata>;<br>差异内容：NA|类名：AVMetadataExtractor；<br>API声明：fetchMetadata(): Promise\<AVMetadata>;<br>差异内容：crossplatform|api/@ohos.multimedia.media.d.ts|
|API跨平台权限变更|类名：AVMetadataExtractor；<br>API声明：fetchAlbumCover(callback: AsyncCallback\<image.PixelMap>): void;<br>差异内容：NA|类名：AVMetadataExtractor；<br>API声明：fetchAlbumCover(callback: AsyncCallback\<image.PixelMap>): void;<br>差异内容：crossplatform|api/@ohos.multimedia.media.d.ts|
|API跨平台权限变更|类名：AVMetadataExtractor；<br>API声明：fetchAlbumCover(): Promise\<image.PixelMap>;<br>差异内容：NA|类名：AVMetadataExtractor；<br>API声明：fetchAlbumCover(): Promise\<image.PixelMap>;<br>差异内容：crossplatform|api/@ohos.multimedia.media.d.ts|
|API跨平台权限变更|类名：AVMetadataExtractor；<br>API声明：release(callback: AsyncCallback\<void>): void;<br>差异内容：NA|类名：AVMetadataExtractor；<br>API声明：release(callback: AsyncCallback\<void>): void;<br>差异内容：crossplatform|api/@ohos.multimedia.media.d.ts|
|API跨平台权限变更|类名：AVMetadataExtractor；<br>API声明：release(): Promise\<void>;<br>差异内容：NA|类名：AVMetadataExtractor；<br>API声明：release(): Promise\<void>;<br>差异内容：crossplatform|api/@ohos.multimedia.media.d.ts|
|API跨平台权限变更|类名：media；<br>API声明：interface AVMetadata<br>差异内容：NA|类名：media；<br>API声明：interface AVMetadata<br>差异内容：crossplatform|api/@ohos.multimedia.media.d.ts|
|API跨平台权限变更|类名：AVMetadata；<br>API声明：album?: string;<br>差异内容：NA|类名：AVMetadata；<br>API声明：album?: string;<br>差异内容：crossplatform|api/@ohos.multimedia.media.d.ts|
|API跨平台权限变更|类名：AVMetadata；<br>API声明：albumArtist?: string;<br>差异内容：NA|类名：AVMetadata；<br>API声明：albumArtist?: string;<br>差异内容：crossplatform|api/@ohos.multimedia.media.d.ts|
|API跨平台权限变更|类名：AVMetadata；<br>API声明：artist?: string;<br>差异内容：NA|类名：AVMetadata；<br>API声明：artist?: string;<br>差异内容：crossplatform|api/@ohos.multimedia.media.d.ts|
|API跨平台权限变更|类名：AVMetadata；<br>API声明：author?: string;<br>差异内容：NA|类名：AVMetadata；<br>API声明：author?: string;<br>差异内容：crossplatform|api/@ohos.multimedia.media.d.ts|
|API跨平台权限变更|类名：AVMetadata；<br>API声明：dateTime?: string;<br>差异内容：NA|类名：AVMetadata；<br>API声明：dateTime?: string;<br>差异内容：crossplatform|api/@ohos.multimedia.media.d.ts|
|API跨平台权限变更|类名：AVMetadata；<br>API声明：dateTimeFormat?: string;<br>差异内容：NA|类名：AVMetadata；<br>API声明：dateTimeFormat?: string;<br>差异内容：crossplatform|api/@ohos.multimedia.media.d.ts|
|API跨平台权限变更|类名：AVMetadata；<br>API声明：composer?: string;<br>差异内容：NA|类名：AVMetadata；<br>API声明：composer?: string;<br>差异内容：crossplatform|api/@ohos.multimedia.media.d.ts|
|API跨平台权限变更|类名：AVMetadata；<br>API声明：duration?: string;<br>差异内容：NA|类名：AVMetadata；<br>API声明：duration?: string;<br>差异内容：crossplatform|api/@ohos.multimedia.media.d.ts|
|API跨平台权限变更|类名：AVMetadata；<br>API声明：genre?: string;<br>差异内容：NA|类名：AVMetadata；<br>API声明：genre?: string;<br>差异内容：crossplatform|api/@ohos.multimedia.media.d.ts|
|API跨平台权限变更|类名：AVMetadata；<br>API声明：hasAudio?: string;<br>差异内容：NA|类名：AVMetadata；<br>API声明：hasAudio?: string;<br>差异内容：crossplatform|api/@ohos.multimedia.media.d.ts|
|API跨平台权限变更|类名：AVMetadata；<br>API声明：hasVideo?: string;<br>差异内容：NA|类名：AVMetadata；<br>API声明：hasVideo?: string;<br>差异内容：crossplatform|api/@ohos.multimedia.media.d.ts|
|API跨平台权限变更|类名：AVMetadata；<br>API声明：mimeType?: string;<br>差异内容：NA|类名：AVMetadata；<br>API声明：mimeType?: string;<br>差异内容：crossplatform|api/@ohos.multimedia.media.d.ts|
|API跨平台权限变更|类名：AVMetadata；<br>API声明：trackCount?: string;<br>差异内容：NA|类名：AVMetadata；<br>API声明：trackCount?: string;<br>差异内容：crossplatform|api/@ohos.multimedia.media.d.ts|
|API跨平台权限变更|类名：AVMetadata；<br>API声明：sampleRate?: string;<br>差异内容：NA|类名：AVMetadata；<br>API声明：sampleRate?: string;<br>差异内容：crossplatform|api/@ohos.multimedia.media.d.ts|
|API跨平台权限变更|类名：AVMetadata；<br>API声明：title?: string;<br>差异内容：NA|类名：AVMetadata；<br>API声明：title?: string;<br>差异内容：crossplatform|api/@ohos.multimedia.media.d.ts|
|API跨平台权限变更|类名：AVMetadata；<br>API声明：videoHeight?: string;<br>差异内容：NA|类名：AVMetadata；<br>API声明：videoHeight?: string;<br>差异内容：crossplatform|api/@ohos.multimedia.media.d.ts|
|API跨平台权限变更|类名：AVMetadata；<br>API声明：videoWidth?: string;<br>差异内容：NA|类名：AVMetadata；<br>API声明：videoWidth?: string;<br>差异内容：crossplatform|api/@ohos.multimedia.media.d.ts|
|API跨平台权限变更|类名：AVMetadata；<br>API声明：videoOrientation?: string;<br>差异内容：NA|类名：AVMetadata；<br>API声明：videoOrientation?: string;<br>差异内容：crossplatform|api/@ohos.multimedia.media.d.ts|
|API跨平台权限变更|类名：media；<br>API声明：enum AVErrorCode<br>差异内容：NA|类名：media；<br>API声明：enum AVErrorCode<br>差异内容：crossplatform|api/@ohos.multimedia.media.d.ts|
|API跨平台权限变更|类名：AVErrorCode；<br>API声明：AVERR_OK = 0<br>差异内容：NA|类名：AVErrorCode；<br>API声明：AVERR_OK = 0<br>差异内容：crossplatform|api/@ohos.multimedia.media.d.ts|
|API跨平台权限变更|类名：AVErrorCode；<br>API声明：AVERR_NO_PERMISSION = 201<br>差异内容：NA|类名：AVErrorCode；<br>API声明：AVERR_NO_PERMISSION = 201<br>差异内容：crossplatform|api/@ohos.multimedia.media.d.ts|
|API跨平台权限变更|类名：AVErrorCode；<br>API声明：AVERR_INVALID_PARAMETER = 401<br>差异内容：NA|类名：AVErrorCode；<br>API声明：AVERR_INVALID_PARAMETER = 401<br>差异内容：crossplatform|api/@ohos.multimedia.media.d.ts|
|API跨平台权限变更|类名：AVErrorCode；<br>API声明：AVERR_UNSUPPORT_CAPABILITY = 801<br>差异内容：NA|类名：AVErrorCode；<br>API声明：AVERR_UNSUPPORT_CAPABILITY = 801<br>差异内容：crossplatform|api/@ohos.multimedia.media.d.ts|
|API跨平台权限变更|类名：AVErrorCode；<br>API声明：AVERR_NO_MEMORY = 5400101<br>差异内容：NA|类名：AVErrorCode；<br>API声明：AVERR_NO_MEMORY = 5400101<br>差异内容：crossplatform|api/@ohos.multimedia.media.d.ts|
|API跨平台权限变更|类名：AVErrorCode；<br>API声明：AVERR_OPERATE_NOT_PERMIT = 5400102<br>差异内容：NA|类名：AVErrorCode；<br>API声明：AVERR_OPERATE_NOT_PERMIT = 5400102<br>差异内容：crossplatform|api/@ohos.multimedia.media.d.ts|
|API跨平台权限变更|类名：AVErrorCode；<br>API声明：AVERR_IO = 5400103<br>差异内容：NA|类名：AVErrorCode；<br>API声明：AVERR_IO = 5400103<br>差异内容：crossplatform|api/@ohos.multimedia.media.d.ts|
|API跨平台权限变更|类名：AVErrorCode；<br>API声明：AVERR_TIMEOUT = 5400104<br>差异内容：NA|类名：AVErrorCode；<br>API声明：AVERR_TIMEOUT = 5400104<br>差异内容：crossplatform|api/@ohos.multimedia.media.d.ts|
|API跨平台权限变更|类名：AVErrorCode；<br>API声明：AVERR_SERVICE_DIED = 5400105<br>差异内容：NA|类名：AVErrorCode；<br>API声明：AVERR_SERVICE_DIED = 5400105<br>差异内容：crossplatform|api/@ohos.multimedia.media.d.ts|
|API跨平台权限变更|类名：AVErrorCode；<br>API声明：AVERR_UNSUPPORT_FORMAT = 5400106<br>差异内容：NA|类名：AVErrorCode；<br>API声明：AVERR_UNSUPPORT_FORMAT = 5400106<br>差异内容：crossplatform|api/@ohos.multimedia.media.d.ts|
|API跨平台权限变更|类名：AVErrorCode；<br>API声明：AVERR_AUDIO_INTERRUPTED = 5400107<br>差异内容：NA|类名：AVErrorCode；<br>API声明：AVERR_AUDIO_INTERRUPTED = 5400107<br>差异内容：crossplatform|api/@ohos.multimedia.media.d.ts|
|API跨平台权限变更|类名：media；<br>API声明：type AVPlayerState = 'idle' \| 'initialized' \| 'prepared' \| 'playing' \| 'paused' \| 'completed' \| 'stopped' \| 'released' \| 'error';<br>差异内容：NA|类名：media；<br>API声明：type AVPlayerState = 'idle' \| 'initialized' \| 'prepared' \| 'playing' \| 'paused' \| 'completed' \| 'stopped' \| 'released' \| 'error';<br>差异内容：crossplatform|api/@ohos.multimedia.media.d.ts|
|API跨平台权限变更|类名：media；<br>API声明：interface AVPlayer<br>差异内容：NA|类名：media；<br>API声明：interface AVPlayer<br>差异内容：crossplatform|api/@ohos.multimedia.media.d.ts|
|API跨平台权限变更|类名：AVPlayer；<br>API声明：prepare(callback: AsyncCallback\<void>): void;<br>差异内容：NA|类名：AVPlayer；<br>API声明：prepare(callback: AsyncCallback\<void>): void;<br>差异内容：crossplatform|api/@ohos.multimedia.media.d.ts|
|API跨平台权限变更|类名：AVPlayer；<br>API声明：prepare(): Promise\<void>;<br>差异内容：NA|类名：AVPlayer；<br>API声明：prepare(): Promise\<void>;<br>差异内容：crossplatform|api/@ohos.multimedia.media.d.ts|
|API跨平台权限变更|类名：AVPlayer；<br>API声明：play(callback: AsyncCallback\<void>): void;<br>差异内容：NA|类名：AVPlayer；<br>API声明：play(callback: AsyncCallback\<void>): void;<br>差异内容：crossplatform|api/@ohos.multimedia.media.d.ts|
|API跨平台权限变更|类名：AVPlayer；<br>API声明：play(): Promise\<void>;<br>差异内容：NA|类名：AVPlayer；<br>API声明：play(): Promise\<void>;<br>差异内容：crossplatform|api/@ohos.multimedia.media.d.ts|
|API跨平台权限变更|类名：AVPlayer；<br>API声明：pause(callback: AsyncCallback\<void>): void;<br>差异内容：NA|类名：AVPlayer；<br>API声明：pause(callback: AsyncCallback\<void>): void;<br>差异内容：crossplatform|api/@ohos.multimedia.media.d.ts|
|API跨平台权限变更|类名：AVPlayer；<br>API声明：pause(): Promise\<void>;<br>差异内容：NA|类名：AVPlayer；<br>API声明：pause(): Promise\<void>;<br>差异内容：crossplatform|api/@ohos.multimedia.media.d.ts|
|API跨平台权限变更|类名：AVPlayer；<br>API声明：stop(callback: AsyncCallback\<void>): void;<br>差异内容：NA|类名：AVPlayer；<br>API声明：stop(callback: AsyncCallback\<void>): void;<br>差异内容：crossplatform|api/@ohos.multimedia.media.d.ts|
|API跨平台权限变更|类名：AVPlayer；<br>API声明：stop(): Promise\<void>;<br>差异内容：NA|类名：AVPlayer；<br>API声明：stop(): Promise\<void>;<br>差异内容：crossplatform|api/@ohos.multimedia.media.d.ts|
|API跨平台权限变更|类名：AVPlayer；<br>API声明：reset(callback: AsyncCallback\<void>): void;<br>差异内容：NA|类名：AVPlayer；<br>API声明：reset(callback: AsyncCallback\<void>): void;<br>差异内容：crossplatform|api/@ohos.multimedia.media.d.ts|
|API跨平台权限变更|类名：AVPlayer；<br>API声明：reset(): Promise\<void>;<br>差异内容：NA|类名：AVPlayer；<br>API声明：reset(): Promise\<void>;<br>差异内容：crossplatform|api/@ohos.multimedia.media.d.ts|
|API跨平台权限变更|类名：AVPlayer；<br>API声明：release(callback: AsyncCallback\<void>): void;<br>差异内容：NA|类名：AVPlayer；<br>API声明：release(callback: AsyncCallback\<void>): void;<br>差异内容：crossplatform|api/@ohos.multimedia.media.d.ts|
|API跨平台权限变更|类名：AVPlayer；<br>API声明：release(): Promise\<void>;<br>差异内容：NA|类名：AVPlayer；<br>API声明：release(): Promise\<void>;<br>差异内容：crossplatform|api/@ohos.multimedia.media.d.ts|
|API跨平台权限变更|类名：AVPlayer；<br>API声明：seek(timeMs: number, mode?: SeekMode): void;<br>差异内容：NA|类名：AVPlayer；<br>API声明：seek(timeMs: number, mode?: SeekMode): void;<br>差异内容：crossplatform|api/@ohos.multimedia.media.d.ts|
|API跨平台权限变更|类名：AVPlayer；<br>API声明：setVolume(volume: number): void;<br>差异内容：NA|类名：AVPlayer；<br>API声明：setVolume(volume: number): void;<br>差异内容：crossplatform|api/@ohos.multimedia.media.d.ts|
|API跨平台权限变更|类名：AVPlayer；<br>API声明：getTrackDescription(callback: AsyncCallback\<Array\<MediaDescription>>): void;<br>差异内容：NA|类名：AVPlayer；<br>API声明：getTrackDescription(callback: AsyncCallback\<Array\<MediaDescription>>): void;<br>差异内容：crossplatform|api/@ohos.multimedia.media.d.ts|
|API跨平台权限变更|类名：AVPlayer；<br>API声明：getTrackDescription(): Promise\<Array\<MediaDescription>>;<br>差异内容：NA|类名：AVPlayer；<br>API声明：getTrackDescription(): Promise\<Array\<MediaDescription>>;<br>差异内容：crossplatform|api/@ohos.multimedia.media.d.ts|
|API跨平台权限变更|类名：AVPlayer；<br>API声明：url?: string;<br>差异内容：NA|类名：AVPlayer；<br>API声明：url?: string;<br>差异内容：crossplatform|api/@ohos.multimedia.media.d.ts|
|API跨平台权限变更|类名：AVPlayer；<br>API声明：fdSrc?: AVFileDescriptor;<br>差异内容：NA|类名：AVPlayer；<br>API声明：fdSrc?: AVFileDescriptor;<br>差异内容：crossplatform|api/@ohos.multimedia.media.d.ts|
|API跨平台权限变更|类名：AVPlayer；<br>API声明：dataSrc?: AVDataSrcDescriptor;<br>差异内容：NA|类名：AVPlayer；<br>API声明：dataSrc?: AVDataSrcDescriptor;<br>差异内容：crossplatform|api/@ohos.multimedia.media.d.ts|
|API跨平台权限变更|类名：AVPlayer；<br>API声明：loop: boolean;<br>差异内容：NA|类名：AVPlayer；<br>API声明：loop: boolean;<br>差异内容：crossplatform|api/@ohos.multimedia.media.d.ts|
|API跨平台权限变更|类名：AVPlayer；<br>API声明：readonly currentTime: number;<br>差异内容：NA|类名：AVPlayer；<br>API声明：readonly currentTime: number;<br>差异内容：crossplatform|api/@ohos.multimedia.media.d.ts|
|API跨平台权限变更|类名：AVPlayer；<br>API声明：readonly duration: number;<br>差异内容：NA|类名：AVPlayer；<br>API声明：readonly duration: number;<br>差异内容：crossplatform|api/@ohos.multimedia.media.d.ts|
|API跨平台权限变更|类名：AVPlayer；<br>API声明：readonly state: AVPlayerState;<br>差异内容：NA|类名：AVPlayer；<br>API声明：readonly state: AVPlayerState;<br>差异内容：crossplatform|api/@ohos.multimedia.media.d.ts|
|API跨平台权限变更|类名：AVPlayer；<br>API声明：surfaceId?: string;<br>差异内容：NA|类名：AVPlayer；<br>API声明：surfaceId?: string;<br>差异内容：crossplatform|api/@ohos.multimedia.media.d.ts|
|API跨平台权限变更|类名：AVPlayer；<br>API声明：readonly width: number;<br>差异内容：NA|类名：AVPlayer；<br>API声明：readonly width: number;<br>差异内容：crossplatform|api/@ohos.multimedia.media.d.ts|
|API跨平台权限变更|类名：AVPlayer；<br>API声明：readonly height: number;<br>差异内容：NA|类名：AVPlayer；<br>API声明：readonly height: number;<br>差异内容：crossplatform|api/@ohos.multimedia.media.d.ts|
|API跨平台权限变更|类名：AVPlayer；<br>API声明：videoScaleType?: VideoScaleType;<br>差异内容：NA|类名：AVPlayer；<br>API声明：videoScaleType?: VideoScaleType;<br>差异内容：crossplatform|api/@ohos.multimedia.media.d.ts|
|API跨平台权限变更|类名：AVPlayer；<br>API声明：setSpeed(speed: PlaybackSpeed): void;<br>差异内容：NA|类名：AVPlayer；<br>API声明：setSpeed(speed: PlaybackSpeed): void;<br>差异内容：crossplatform|api/@ohos.multimedia.media.d.ts|
|API跨平台权限变更|类名：AVPlayer；<br>API声明：setBitrate(bitrate: number): void;<br>差异内容：NA|类名：AVPlayer；<br>API声明：setBitrate(bitrate: number): void;<br>差异内容：crossplatform|api/@ohos.multimedia.media.d.ts|
|API跨平台权限变更|类名：AVPlayer；<br>API声明：on(type: 'stateChange', callback: (state: AVPlayerState, reason: StateChangeReason) => void): void;<br>差异内容：NA|类名：AVPlayer；<br>API声明：on(type: 'stateChange', callback: OnAVPlayerStateChangeHandle): void;<br>差异内容：crossplatform|api/@ohos.multimedia.media.d.ts|
|API跨平台权限变更|类名：AVPlayer；<br>API声明：off(type: 'stateChange'): void;<br>差异内容：NA|类名：AVPlayer；<br>API声明：off(type: 'stateChange', callback?: OnAVPlayerStateChangeHandle): void;<br>差异内容：crossplatform|api/@ohos.multimedia.media.d.ts|
|API跨平台权限变更|类名：AVPlayer；<br>API声明：on(type: 'volumeChange', callback: Callback\<number>): void;<br>差异内容：NA|类名：AVPlayer；<br>API声明：on(type: 'volumeChange', callback: Callback\<number>): void;<br>差异内容：crossplatform|api/@ohos.multimedia.media.d.ts|
|API跨平台权限变更|类名：AVPlayer；<br>API声明：off(type: 'volumeChange'): void;<br>差异内容：NA|类名：AVPlayer；<br>API声明：off(type: 'volumeChange', callback?: Callback\<number>): void;<br>差异内容：crossplatform|api/@ohos.multimedia.media.d.ts|
|API跨平台权限变更|类名：AVPlayer；<br>API声明：on(type: 'endOfStream', callback: Callback\<void>): void;<br>差异内容：NA|类名：AVPlayer；<br>API声明：on(type: 'endOfStream', callback: Callback\<void>): void;<br>差异内容：crossplatform|api/@ohos.multimedia.media.d.ts|
|API跨平台权限变更|类名：AVPlayer；<br>API声明：off(type: 'endOfStream'): void;<br>差异内容：NA|类名：AVPlayer；<br>API声明：off(type: 'endOfStream', callback?: Callback\<void>): void;<br>差异内容：crossplatform|api/@ohos.multimedia.media.d.ts|
|API跨平台权限变更|类名：AVPlayer；<br>API声明：on(type: 'seekDone', callback: Callback\<number>): void;<br>差异内容：NA|类名：AVPlayer；<br>API声明：on(type: 'seekDone', callback: Callback\<number>): void;<br>差异内容：crossplatform|api/@ohos.multimedia.media.d.ts|
|API跨平台权限变更|类名：AVPlayer；<br>API声明：off(type: 'seekDone'): void;<br>差异内容：NA|类名：AVPlayer；<br>API声明：off(type: 'seekDone', callback?: Callback\<number>): void;<br>差异内容：crossplatform|api/@ohos.multimedia.media.d.ts|
|API跨平台权限变更|类名：AVPlayer；<br>API声明：on(type: 'speedDone', callback: Callback\<number>): void;<br>差异内容：NA|类名：AVPlayer；<br>API声明：on(type: 'speedDone', callback: Callback\<number>): void;<br>差异内容：crossplatform|api/@ohos.multimedia.media.d.ts|
|API跨平台权限变更|类名：AVPlayer；<br>API声明：off(type: 'speedDone'): void;<br>差异内容：NA|类名：AVPlayer；<br>API声明：off(type: 'speedDone', callback?: Callback\<number>): void;<br>差异内容：crossplatform|api/@ohos.multimedia.media.d.ts|
|API跨平台权限变更|类名：AVPlayer；<br>API声明：on(type: 'timeUpdate', callback: Callback\<number>): void;<br>差异内容：NA|类名：AVPlayer；<br>API声明：on(type: 'timeUpdate', callback: Callback\<number>): void;<br>差异内容：crossplatform|api/@ohos.multimedia.media.d.ts|
|API跨平台权限变更|类名：AVPlayer；<br>API声明：off(type: 'timeUpdate'): void;<br>差异内容：NA|类名：AVPlayer；<br>API声明：off(type: 'timeUpdate', callback?: Callback\<number>): void;<br>差异内容：crossplatform|api/@ohos.multimedia.media.d.ts|
|API跨平台权限变更|类名：AVPlayer；<br>API声明：on(type: 'durationUpdate', callback: Callback\<number>): void;<br>差异内容：NA|类名：AVPlayer；<br>API声明：on(type: 'durationUpdate', callback: Callback\<number>): void;<br>差异内容：crossplatform|api/@ohos.multimedia.media.d.ts|
|API跨平台权限变更|类名：AVPlayer；<br>API声明：off(type: 'durationUpdate'): void;<br>差异内容：NA|类名：AVPlayer；<br>API声明：off(type: 'durationUpdate', callback?: Callback\<number>): void;<br>差异内容：crossplatform|api/@ohos.multimedia.media.d.ts|
|API跨平台权限变更|类名：AVPlayer；<br>API声明：on(type: 'bufferingUpdate', callback: (infoType: BufferingInfoType, value: number) => void): void;<br>差异内容：NA|类名：AVPlayer；<br>API声明：on(type: 'bufferingUpdate', callback: OnBufferingUpdateHandler): void;<br>差异内容：crossplatform|api/@ohos.multimedia.media.d.ts|
|API跨平台权限变更|类名：AVPlayer；<br>API声明：off(type: 'bufferingUpdate'): void;<br>差异内容：NA|类名：AVPlayer；<br>API声明：off(type: 'bufferingUpdate', callback?: OnBufferingUpdateHandler): void;<br>差异内容：crossplatform|api/@ohos.multimedia.media.d.ts|
|API跨平台权限变更|类名：AVPlayer；<br>API声明：on(type: 'videoSizeChange', callback: (width: number, height: number) => void): void;<br>差异内容：NA|类名：AVPlayer；<br>API声明：on(type: 'videoSizeChange', callback: OnVideoSizeChangeHandler): void;<br>差异内容：crossplatform|api/@ohos.multimedia.media.d.ts|
|API跨平台权限变更|类名：AVPlayer；<br>API声明：off(type: 'videoSizeChange'): void;<br>差异内容：NA|类名：AVPlayer；<br>API声明：off(type: 'videoSizeChange', callback?: OnVideoSizeChangeHandler): void;<br>差异内容：crossplatform|api/@ohos.multimedia.media.d.ts|
|API跨平台权限变更|类名：AVPlayer；<br>API声明：on(type: 'audioInterrupt', callback: (info: audio.InterruptEvent) => void): void;<br>差异内容：NA|类名：AVPlayer；<br>API声明：on(type: 'audioInterrupt', callback: Callback\<audio.InterruptEvent>): void;<br>差异内容：crossplatform|api/@ohos.multimedia.media.d.ts|
|API跨平台权限变更|类名：AVPlayer；<br>API声明：off(type: 'audioInterrupt'): void;<br>差异内容：NA|类名：AVPlayer；<br>API声明：off(type: 'audioInterrupt', callback?: Callback\<audio.InterruptEvent>): void;<br>差异内容：crossplatform|api/@ohos.multimedia.media.d.ts|
|API跨平台权限变更|类名：AVPlayer；<br>API声明：on(type: 'availableBitrates', callback: (bitrates: Array\<number>) => void): void;<br>差异内容：NA|类名：AVPlayer；<br>API声明：on(type: 'availableBitrates', callback: Callback\<Array\<number>>): void;<br>差异内容：crossplatform|api/@ohos.multimedia.media.d.ts|
|API跨平台权限变更|类名：AVPlayer；<br>API声明：off(type: 'availableBitrates'): void;<br>差异内容：NA|类名：AVPlayer；<br>API声明：off(type: 'availableBitrates', callback?: Callback\<Array\<number>>): void;<br>差异内容：crossplatform|api/@ohos.multimedia.media.d.ts|
|API跨平台权限变更|类名：AVPlayer；<br>API声明：on(type: 'error', callback: ErrorCallback): void;<br>差异内容：NA|类名：AVPlayer；<br>API声明：on(type: 'error', callback: ErrorCallback): void;<br>差异内容：crossplatform|api/@ohos.multimedia.media.d.ts|
|API跨平台权限变更|类名：AVPlayer；<br>API声明：off(type: 'error'): void;<br>差异内容：NA|类名：AVPlayer；<br>API声明：off(type: 'error', callback?: ErrorCallback): void;<br>差异内容：crossplatform|api/@ohos.multimedia.media.d.ts|
|API跨平台权限变更|类名：media；<br>API声明：enum BufferingInfoType<br>差异内容：NA|类名：media；<br>API声明：enum BufferingInfoType<br>差异内容：crossplatform|api/@ohos.multimedia.media.d.ts|
|API跨平台权限变更|类名：BufferingInfoType；<br>API声明：BUFFERING_START = 1<br>差异内容：NA|类名：BufferingInfoType；<br>API声明：BUFFERING_START = 1<br>差异内容：crossplatform|api/@ohos.multimedia.media.d.ts|
|API跨平台权限变更|类名：BufferingInfoType；<br>API声明：BUFFERING_END = 2<br>差异内容：NA|类名：BufferingInfoType；<br>API声明：BUFFERING_END = 2<br>差异内容：crossplatform|api/@ohos.multimedia.media.d.ts|
|API跨平台权限变更|类名：BufferingInfoType；<br>API声明：BUFFERING_PERCENT = 3<br>差异内容：NA|类名：BufferingInfoType；<br>API声明：BUFFERING_PERCENT = 3<br>差异内容：crossplatform|api/@ohos.multimedia.media.d.ts|
|API跨平台权限变更|类名：BufferingInfoType；<br>API声明：CACHED_DURATION = 4<br>差异内容：NA|类名：BufferingInfoType；<br>API声明：CACHED_DURATION = 4<br>差异内容：crossplatform|api/@ohos.multimedia.media.d.ts|
|API跨平台权限变更|类名：media；<br>API声明：interface AVFileDescriptor<br>差异内容：NA|类名：media；<br>API声明：interface AVFileDescriptor<br>差异内容：crossplatform|api/@ohos.multimedia.media.d.ts|
|API跨平台权限变更|类名：AVFileDescriptor；<br>API声明：fd: number;<br>差异内容：NA|类名：AVFileDescriptor；<br>API声明：fd: number;<br>差异内容：crossplatform|api/@ohos.multimedia.media.d.ts|
|API跨平台权限变更|类名：AVFileDescriptor；<br>API声明：offset?: number;<br>差异内容：NA|类名：AVFileDescriptor；<br>API声明：offset?: number;<br>差异内容：crossplatform|api/@ohos.multimedia.media.d.ts|
|API跨平台权限变更|类名：AVFileDescriptor；<br>API声明：length?: number;<br>差异内容：NA|类名：AVFileDescriptor；<br>API声明：length?: number;<br>差异内容：crossplatform|api/@ohos.multimedia.media.d.ts|
|API跨平台权限变更|类名：media；<br>API声明：interface AVDataSrcDescriptor<br>差异内容：NA|类名：media；<br>API声明：interface AVDataSrcDescriptor<br>差异内容：crossplatform|api/@ohos.multimedia.media.d.ts|
|API跨平台权限变更|类名：AVDataSrcDescriptor；<br>API声明：fileSize: number;<br>差异内容：NA|类名：AVDataSrcDescriptor；<br>API声明：fileSize: number;<br>差异内容：crossplatform|api/@ohos.multimedia.media.d.ts|
|API跨平台权限变更|类名：AVDataSrcDescriptor；<br>API声明：callback: (buffer: ArrayBuffer, length: number, pos?: number) => number;<br>差异内容：NA|类名：AVDataSrcDescriptor；<br>API声明：callback: (buffer: ArrayBuffer, length: number, pos?: number) => number;<br>差异内容：crossplatform|api/@ohos.multimedia.media.d.ts|
|API跨平台权限变更|类名：media；<br>API声明：type AVRecorderState = 'idle' \| 'prepared' \| 'started' \| 'paused' \| 'stopped' \| 'released' \| 'error';<br>差异内容：NA|类名：media；<br>API声明：type AVRecorderState = 'idle' \| 'prepared' \| 'started' \| 'paused' \| 'stopped' \| 'released' \| 'error';<br>差异内容：crossplatform|api/@ohos.multimedia.media.d.ts|
|API跨平台权限变更|类名：media；<br>API声明：interface AVRecorder<br>差异内容：NA|类名：media；<br>API声明：interface AVRecorder<br>差异内容：crossplatform|api/@ohos.multimedia.media.d.ts|
|API跨平台权限变更|类名：AVRecorder；<br>API声明：prepare(config: AVRecorderConfig, callback: AsyncCallback\<void>): void;<br>差异内容：NA|类名：AVRecorder；<br>API声明：prepare(config: AVRecorderConfig, callback: AsyncCallback\<void>): void;<br>差异内容：crossplatform|api/@ohos.multimedia.media.d.ts|
|API跨平台权限变更|类名：AVRecorder；<br>API声明：prepare(config: AVRecorderConfig): Promise\<void>;<br>差异内容：NA|类名：AVRecorder；<br>API声明：prepare(config: AVRecorderConfig): Promise\<void>;<br>差异内容：crossplatform|api/@ohos.multimedia.media.d.ts|
|API跨平台权限变更|类名：AVRecorder；<br>API声明：start(callback: AsyncCallback\<void>): void;<br>差异内容：NA|类名：AVRecorder；<br>API声明：start(callback: AsyncCallback\<void>): void;<br>差异内容：crossplatform|api/@ohos.multimedia.media.d.ts|
|API跨平台权限变更|类名：AVRecorder；<br>API声明：start(): Promise\<void>;<br>差异内容：NA|类名：AVRecorder；<br>API声明：start(): Promise\<void>;<br>差异内容：crossplatform|api/@ohos.multimedia.media.d.ts|
|API跨平台权限变更|类名：AVRecorder；<br>API声明：pause(callback: AsyncCallback\<void>): void;<br>差异内容：NA|类名：AVRecorder；<br>API声明：pause(callback: AsyncCallback\<void>): void;<br>差异内容：crossplatform|api/@ohos.multimedia.media.d.ts|
|API跨平台权限变更|类名：AVRecorder；<br>API声明：pause(): Promise\<void>;<br>差异内容：NA|类名：AVRecorder；<br>API声明：pause(): Promise\<void>;<br>差异内容：crossplatform|api/@ohos.multimedia.media.d.ts|
|API跨平台权限变更|类名：AVRecorder；<br>API声明：resume(callback: AsyncCallback\<void>): void;<br>差异内容：NA|类名：AVRecorder；<br>API声明：resume(callback: AsyncCallback\<void>): void;<br>差异内容：crossplatform|api/@ohos.multimedia.media.d.ts|
|API跨平台权限变更|类名：AVRecorder；<br>API声明：resume(): Promise\<void>;<br>差异内容：NA|类名：AVRecorder；<br>API声明：resume(): Promise\<void>;<br>差异内容：crossplatform|api/@ohos.multimedia.media.d.ts|
|API跨平台权限变更|类名：AVRecorder；<br>API声明：stop(callback: AsyncCallback\<void>): void;<br>差异内容：NA|类名：AVRecorder；<br>API声明：stop(callback: AsyncCallback\<void>): void;<br>差异内容：crossplatform|api/@ohos.multimedia.media.d.ts|
|API跨平台权限变更|类名：AVRecorder；<br>API声明：stop(): Promise\<void>;<br>差异内容：NA|类名：AVRecorder；<br>API声明：stop(): Promise\<void>;<br>差异内容：crossplatform|api/@ohos.multimedia.media.d.ts|
|API跨平台权限变更|类名：AVRecorder；<br>API声明：reset(callback: AsyncCallback\<void>): void;<br>差异内容：NA|类名：AVRecorder；<br>API声明：reset(callback: AsyncCallback\<void>): void;<br>差异内容：crossplatform|api/@ohos.multimedia.media.d.ts|
|API跨平台权限变更|类名：AVRecorder；<br>API声明：reset(): Promise\<void>;<br>差异内容：NA|类名：AVRecorder；<br>API声明：reset(): Promise\<void>;<br>差异内容：crossplatform|api/@ohos.multimedia.media.d.ts|
|API跨平台权限变更|类名：AVRecorder；<br>API声明：release(callback: AsyncCallback\<void>): void;<br>差异内容：NA|类名：AVRecorder；<br>API声明：release(callback: AsyncCallback\<void>): void;<br>差异内容：crossplatform|api/@ohos.multimedia.media.d.ts|
|API跨平台权限变更|类名：AVRecorder；<br>API声明：release(): Promise\<void>;<br>差异内容：NA|类名：AVRecorder；<br>API声明：release(): Promise\<void>;<br>差异内容：crossplatform|api/@ohos.multimedia.media.d.ts|
|API跨平台权限变更|类名：AVRecorder；<br>API声明：readonly state: AVRecorderState;<br>差异内容：NA|类名：AVRecorder；<br>API声明：readonly state: AVRecorderState;<br>差异内容：crossplatform|api/@ohos.multimedia.media.d.ts|
|API跨平台权限变更|类名：AVRecorder；<br>API声明：on(type: 'stateChange', callback: (state: AVRecorderState, reason: StateChangeReason) => void): void;<br>差异内容：NA|类名：AVRecorder；<br>API声明：on(type: 'stateChange', callback: OnAVRecorderStateChangeHandler): void;<br>差异内容：crossplatform|api/@ohos.multimedia.media.d.ts|
|API跨平台权限变更|类名：AVRecorder；<br>API声明：on(type: 'error', callback: ErrorCallback): void;<br>差异内容：NA|类名：AVRecorder；<br>API声明：on(type: 'error', callback: ErrorCallback): void;<br>差异内容：crossplatform|api/@ohos.multimedia.media.d.ts|
|API跨平台权限变更|类名：AVRecorder；<br>API声明：off(type: 'stateChange'): void;<br>差异内容：NA|类名：AVRecorder；<br>API声明：off(type: 'stateChange', callback?: OnAVRecorderStateChangeHandler): void;<br>差异内容：crossplatform|api/@ohos.multimedia.media.d.ts|
|API跨平台权限变更|类名：AVRecorder；<br>API声明：off(type: 'error'): void;<br>差异内容：NA|类名：AVRecorder；<br>API声明：off(type: 'error', callback?: ErrorCallback): void;<br>差异内容：crossplatform|api/@ohos.multimedia.media.d.ts|
|API跨平台权限变更|类名：media；<br>API声明：interface Location<br>差异内容：NA|类名：media；<br>API声明：interface Location<br>差异内容：crossplatform|api/@ohos.multimedia.media.d.ts|
|API跨平台权限变更|类名：Location；<br>API声明：latitude: number;<br>差异内容：NA|类名：Location；<br>API声明：latitude: number;<br>差异内容：crossplatform|api/@ohos.multimedia.media.d.ts|
|API跨平台权限变更|类名：Location；<br>API声明：longitude: number;<br>差异内容：NA|类名：Location；<br>API声明：longitude: number;<br>差异内容：crossplatform|api/@ohos.multimedia.media.d.ts|
|API跨平台权限变更|类名：media；<br>API声明：enum PlaybackSpeed<br>差异内容：NA|类名：media；<br>API声明：enum PlaybackSpeed<br>差异内容：crossplatform|api/@ohos.multimedia.media.d.ts|
|API跨平台权限变更|类名：PlaybackSpeed；<br>API声明：SPEED_FORWARD_0_75_X = 0<br>差异内容：NA|类名：PlaybackSpeed；<br>API声明：SPEED_FORWARD_0_75_X = 0<br>差异内容：crossplatform|api/@ohos.multimedia.media.d.ts|
|API跨平台权限变更|类名：PlaybackSpeed；<br>API声明：SPEED_FORWARD_1_00_X = 1<br>差异内容：NA|类名：PlaybackSpeed；<br>API声明：SPEED_FORWARD_1_00_X = 1<br>差异内容：crossplatform|api/@ohos.multimedia.media.d.ts|
|API跨平台权限变更|类名：PlaybackSpeed；<br>API声明：SPEED_FORWARD_1_25_X = 2<br>差异内容：NA|类名：PlaybackSpeed；<br>API声明：SPEED_FORWARD_1_25_X = 2<br>差异内容：crossplatform|api/@ohos.multimedia.media.d.ts|
|API跨平台权限变更|类名：PlaybackSpeed；<br>API声明：SPEED_FORWARD_1_75_X = 3<br>差异内容：NA|类名：PlaybackSpeed；<br>API声明：SPEED_FORWARD_1_75_X = 3<br>差异内容：crossplatform|api/@ohos.multimedia.media.d.ts|
|API跨平台权限变更|类名：PlaybackSpeed；<br>API声明：SPEED_FORWARD_2_00_X = 4<br>差异内容：NA|类名：PlaybackSpeed；<br>API声明：SPEED_FORWARD_2_00_X = 4<br>差异内容：crossplatform|api/@ohos.multimedia.media.d.ts|
|API跨平台权限变更|类名：media；<br>API声明：enum VideoScaleType<br>差异内容：NA|类名：media；<br>API声明：enum VideoScaleType<br>差异内容：crossplatform|api/@ohos.multimedia.media.d.ts|
|API跨平台权限变更|类名：VideoScaleType；<br>API声明：VIDEO_SCALE_TYPE_FIT = 0<br>差异内容：NA|类名：VideoScaleType；<br>API声明：VIDEO_SCALE_TYPE_FIT = 0<br>差异内容：crossplatform|api/@ohos.multimedia.media.d.ts|
|API跨平台权限变更|类名：VideoScaleType；<br>API声明：VIDEO_SCALE_TYPE_FIT_CROP = 1<br>差异内容：NA|类名：VideoScaleType；<br>API声明：VIDEO_SCALE_TYPE_FIT_CROP = 1<br>差异内容：crossplatform|api/@ohos.multimedia.media.d.ts|
|API跨平台权限变更|类名：media；<br>API声明：enum ContainerFormatType<br>差异内容：NA|类名：media；<br>API声明：enum ContainerFormatType<br>差异内容：crossplatform|api/@ohos.multimedia.media.d.ts|
|API跨平台权限变更|类名：ContainerFormatType；<br>API声明：CFT_MPEG_4 = 'mp4'<br>差异内容：NA|类名：ContainerFormatType；<br>API声明：CFT_MPEG_4 = 'mp4'<br>差异内容：crossplatform|api/@ohos.multimedia.media.d.ts|
|API跨平台权限变更|类名：ContainerFormatType；<br>API声明：CFT_MPEG_4A = 'm4a'<br>差异内容：NA|类名：ContainerFormatType；<br>API声明：CFT_MPEG_4A = 'm4a'<br>差异内容：crossplatform|api/@ohos.multimedia.media.d.ts|
|API跨平台权限变更|类名：media；<br>API声明：enum MediaType<br>差异内容：NA|类名：media；<br>API声明：enum MediaType<br>差异内容：crossplatform|api/@ohos.multimedia.media.d.ts|
|API跨平台权限变更|类名：MediaType；<br>API声明：MEDIA_TYPE_AUD = 0<br>差异内容：NA|类名：MediaType；<br>API声明：MEDIA_TYPE_AUD = 0<br>差异内容：crossplatform|api/@ohos.multimedia.media.d.ts|
|API跨平台权限变更|类名：MediaType；<br>API声明：MEDIA_TYPE_VID = 1<br>差异内容：NA|类名：MediaType；<br>API声明：MEDIA_TYPE_VID = 1<br>差异内容：crossplatform|api/@ohos.multimedia.media.d.ts|
|API跨平台权限变更|类名：media；<br>API声明：enum MediaDescriptionKey<br>差异内容：NA|类名：media；<br>API声明：enum MediaDescriptionKey<br>差异内容：crossplatform|api/@ohos.multimedia.media.d.ts|
|API跨平台权限变更|类名：MediaDescriptionKey；<br>API声明：MD_KEY_TRACK_INDEX = 'track_index'<br>差异内容：NA|类名：MediaDescriptionKey；<br>API声明：MD_KEY_TRACK_INDEX = 'track_index'<br>差异内容：crossplatform|api/@ohos.multimedia.media.d.ts|
|API跨平台权限变更|类名：MediaDescriptionKey；<br>API声明：MD_KEY_TRACK_TYPE = 'track_type'<br>差异内容：NA|类名：MediaDescriptionKey；<br>API声明：MD_KEY_TRACK_TYPE = 'track_type'<br>差异内容：crossplatform|api/@ohos.multimedia.media.d.ts|
|API跨平台权限变更|类名：MediaDescriptionKey；<br>API声明：MD_KEY_CODEC_MIME = 'codec_mime'<br>差异内容：NA|类名：MediaDescriptionKey；<br>API声明：MD_KEY_CODEC_MIME = 'codec_mime'<br>差异内容：crossplatform|api/@ohos.multimedia.media.d.ts|
|API跨平台权限变更|类名：MediaDescriptionKey；<br>API声明：MD_KEY_DURATION = 'duration'<br>差异内容：NA|类名：MediaDescriptionKey；<br>API声明：MD_KEY_DURATION = 'duration'<br>差异内容：crossplatform|api/@ohos.multimedia.media.d.ts|
|API跨平台权限变更|类名：MediaDescriptionKey；<br>API声明：MD_KEY_BITRATE = 'bitrate'<br>差异内容：NA|类名：MediaDescriptionKey；<br>API声明：MD_KEY_BITRATE = 'bitrate'<br>差异内容：crossplatform|api/@ohos.multimedia.media.d.ts|
|API跨平台权限变更|类名：MediaDescriptionKey；<br>API声明：MD_KEY_WIDTH = 'width'<br>差异内容：NA|类名：MediaDescriptionKey；<br>API声明：MD_KEY_WIDTH = 'width'<br>差异内容：crossplatform|api/@ohos.multimedia.media.d.ts|
|API跨平台权限变更|类名：MediaDescriptionKey；<br>API声明：MD_KEY_HEIGHT = 'height'<br>差异内容：NA|类名：MediaDescriptionKey；<br>API声明：MD_KEY_HEIGHT = 'height'<br>差异内容：crossplatform|api/@ohos.multimedia.media.d.ts|
|API跨平台权限变更|类名：MediaDescriptionKey；<br>API声明：MD_KEY_FRAME_RATE = 'frame_rate'<br>差异内容：NA|类名：MediaDescriptionKey；<br>API声明：MD_KEY_FRAME_RATE = 'frame_rate'<br>差异内容：crossplatform|api/@ohos.multimedia.media.d.ts|
|API跨平台权限变更|类名：MediaDescriptionKey；<br>API声明：MD_KEY_AUD_CHANNEL_COUNT = 'channel_count'<br>差异内容：NA|类名：MediaDescriptionKey；<br>API声明：MD_KEY_AUD_CHANNEL_COUNT = 'channel_count'<br>差异内容：crossplatform|api/@ohos.multimedia.media.d.ts|
|API跨平台权限变更|类名：MediaDescriptionKey；<br>API声明：MD_KEY_AUD_SAMPLE_RATE = 'sample_rate'<br>差异内容：NA|类名：MediaDescriptionKey；<br>API声明：MD_KEY_AUD_SAMPLE_RATE = 'sample_rate'<br>差异内容：crossplatform|api/@ohos.multimedia.media.d.ts|
|API跨平台权限变更|类名：media；<br>API声明：enum AudioSourceType<br>差异内容：NA|类名：media；<br>API声明：enum AudioSourceType<br>差异内容：crossplatform|api/@ohos.multimedia.media.d.ts|
|API跨平台权限变更|类名：AudioSourceType；<br>API声明：AUDIO_SOURCE_TYPE_DEFAULT = 0<br>差异内容：NA|类名：AudioSourceType；<br>API声明：AUDIO_SOURCE_TYPE_DEFAULT = 0<br>差异内容：crossplatform|api/@ohos.multimedia.media.d.ts|
|API跨平台权限变更|类名：AudioSourceType；<br>API声明：AUDIO_SOURCE_TYPE_MIC = 1<br>差异内容：NA|类名：AudioSourceType；<br>API声明：AUDIO_SOURCE_TYPE_MIC = 1<br>差异内容：crossplatform|api/@ohos.multimedia.media.d.ts|
|API跨平台权限变更|类名：media；<br>API声明：enum VideoSourceType<br>差异内容：NA|类名：media；<br>API声明：enum VideoSourceType<br>差异内容：crossplatform|api/@ohos.multimedia.media.d.ts|
|API跨平台权限变更|类名：VideoSourceType；<br>API声明：VIDEO_SOURCE_TYPE_SURFACE_YUV = 0<br>差异内容：NA|类名：VideoSourceType；<br>API声明：VIDEO_SOURCE_TYPE_SURFACE_YUV = 0<br>差异内容：crossplatform|api/@ohos.multimedia.media.d.ts|
|API跨平台权限变更|类名：VideoSourceType；<br>API声明：VIDEO_SOURCE_TYPE_SURFACE_ES = 1<br>差异内容：NA|类名：VideoSourceType；<br>API声明：VIDEO_SOURCE_TYPE_SURFACE_ES = 1<br>差异内容：crossplatform|api/@ohos.multimedia.media.d.ts|
|API跨平台权限变更|类名：media；<br>API声明：interface AVRecorderProfile<br>差异内容：NA|类名：media；<br>API声明：interface AVRecorderProfile<br>差异内容：crossplatform|api/@ohos.multimedia.media.d.ts|
|API跨平台权限变更|类名：AVRecorderProfile；<br>API声明：audioBitrate?: number;<br>差异内容：NA|类名：AVRecorderProfile；<br>API声明：audioBitrate?: number;<br>差异内容：crossplatform|api/@ohos.multimedia.media.d.ts|
|API跨平台权限变更|类名：AVRecorderProfile；<br>API声明：audioChannels?: number;<br>差异内容：NA|类名：AVRecorderProfile；<br>API声明：audioChannels?: number;<br>差异内容：crossplatform|api/@ohos.multimedia.media.d.ts|
|API跨平台权限变更|类名：AVRecorderProfile；<br>API声明：audioCodec?: CodecMimeType;<br>差异内容：NA|类名：AVRecorderProfile；<br>API声明：audioCodec?: CodecMimeType;<br>差异内容：crossplatform|api/@ohos.multimedia.media.d.ts|
|API跨平台权限变更|类名：AVRecorderProfile；<br>API声明：audioSampleRate?: number;<br>差异内容：NA|类名：AVRecorderProfile；<br>API声明：audioSampleRate?: number;<br>差异内容：crossplatform|api/@ohos.multimedia.media.d.ts|
|API跨平台权限变更|类名：AVRecorderProfile；<br>API声明：fileFormat: ContainerFormatType;<br>差异内容：NA|类名：AVRecorderProfile；<br>API声明：fileFormat: ContainerFormatType;<br>差异内容：crossplatform|api/@ohos.multimedia.media.d.ts|
|API跨平台权限变更|类名：AVRecorderProfile；<br>API声明：videoBitrate?: number;<br>差异内容：NA|类名：AVRecorderProfile；<br>API声明：videoBitrate?: number;<br>差异内容：crossplatform|api/@ohos.multimedia.media.d.ts|
|API跨平台权限变更|类名：AVRecorderProfile；<br>API声明：videoCodec?: CodecMimeType;<br>差异内容：NA|类名：AVRecorderProfile；<br>API声明：videoCodec?: CodecMimeType;<br>差异内容：crossplatform|api/@ohos.multimedia.media.d.ts|
|API跨平台权限变更|类名：AVRecorderProfile；<br>API声明：videoFrameWidth?: number;<br>差异内容：NA|类名：AVRecorderProfile；<br>API声明：videoFrameWidth?: number;<br>差异内容：crossplatform|api/@ohos.multimedia.media.d.ts|
|API跨平台权限变更|类名：AVRecorderProfile；<br>API声明：videoFrameHeight?: number;<br>差异内容：NA|类名：AVRecorderProfile；<br>API声明：videoFrameHeight?: number;<br>差异内容：crossplatform|api/@ohos.multimedia.media.d.ts|
|API跨平台权限变更|类名：AVRecorderProfile；<br>API声明：videoFrameRate?: number;<br>差异内容：NA|类名：AVRecorderProfile；<br>API声明：videoFrameRate?: number;<br>差异内容：crossplatform|api/@ohos.multimedia.media.d.ts|
|API跨平台权限变更|类名：AVRecorderProfile；<br>API声明：isHdr?: boolean;<br>差异内容：NA|类名：AVRecorderProfile；<br>API声明：isHdr?: boolean;<br>差异内容：crossplatform|api/@ohos.multimedia.media.d.ts|
|API跨平台权限变更|类名：media；<br>API声明：interface AVRecorderConfig<br>差异内容：NA|类名：media；<br>API声明：interface AVRecorderConfig<br>差异内容：crossplatform|api/@ohos.multimedia.media.d.ts|
|API跨平台权限变更|类名：AVRecorderConfig；<br>API声明：audioSourceType?: AudioSourceType;<br>差异内容：NA|类名：AVRecorderConfig；<br>API声明：audioSourceType?: AudioSourceType;<br>差异内容：crossplatform|api/@ohos.multimedia.media.d.ts|
|API跨平台权限变更|类名：AVRecorderConfig；<br>API声明：videoSourceType?: VideoSourceType;<br>差异内容：NA|类名：AVRecorderConfig；<br>API声明：videoSourceType?: VideoSourceType;<br>差异内容：crossplatform|api/@ohos.multimedia.media.d.ts|
|API跨平台权限变更|类名：AVRecorderConfig；<br>API声明：profile: AVRecorderProfile;<br>差异内容：NA|类名：AVRecorderConfig；<br>API声明：profile: AVRecorderProfile;<br>差异内容：crossplatform|api/@ohos.multimedia.media.d.ts|
|API跨平台权限变更|类名：AVRecorderConfig；<br>API声明：url: string;<br>差异内容：NA|类名：AVRecorderConfig；<br>API声明：url: string;<br>差异内容：crossplatform|api/@ohos.multimedia.media.d.ts|
|API跨平台权限变更|类名：media；<br>API声明：interface MediaDescription<br>差异内容：NA|类名：media；<br>API声明：interface MediaDescription<br>差异内容：crossplatform|api/@ohos.multimedia.media.d.ts|
|API跨平台权限变更|类名：MediaDescription；<br>API声明：[key: string]: Object;<br>差异内容：NA|类名：MediaDescription；<br>API声明：[key: string]: Object;<br>差异内容：crossplatform|api/@ohos.multimedia.media.d.ts|
|API跨平台权限变更|类名：media；<br>API声明：enum SeekMode<br>差异内容：NA|类名：media；<br>API声明：enum SeekMode<br>差异内容：crossplatform|api/@ohos.multimedia.media.d.ts|
|API跨平台权限变更|类名：SeekMode；<br>API声明：SEEK_NEXT_SYNC = 0<br>差异内容：NA|类名：SeekMode；<br>API声明：SEEK_NEXT_SYNC = 0<br>差异内容：crossplatform|api/@ohos.multimedia.media.d.ts|
|API跨平台权限变更|类名：SeekMode；<br>API声明：SEEK_PREV_SYNC = 1<br>差异内容：NA|类名：SeekMode；<br>API声明：SEEK_PREV_SYNC = 1<br>差异内容：crossplatform|api/@ohos.multimedia.media.d.ts|
|API跨平台权限变更|类名：media；<br>API声明：enum CodecMimeType<br>差异内容：NA|类名：media；<br>API声明：enum CodecMimeType<br>差异内容：crossplatform|api/@ohos.multimedia.media.d.ts|
|API跨平台权限变更|类名：CodecMimeType；<br>API声明：VIDEO_H263 = 'video/h263'<br>差异内容：NA|类名：CodecMimeType；<br>API声明：VIDEO_H263 = 'video/h263'<br>差异内容：crossplatform|api/@ohos.multimedia.media.d.ts|
|API跨平台权限变更|类名：CodecMimeType；<br>API声明：VIDEO_AVC = 'video/avc'<br>差异内容：NA|类名：CodecMimeType；<br>API声明：VIDEO_AVC = 'video/avc'<br>差异内容：crossplatform|api/@ohos.multimedia.media.d.ts|
|API跨平台权限变更|类名：CodecMimeType；<br>API声明：VIDEO_MPEG2 = 'video/mpeg2'<br>差异内容：NA|类名：CodecMimeType；<br>API声明：VIDEO_MPEG2 = 'video/mpeg2'<br>差异内容：crossplatform|api/@ohos.multimedia.media.d.ts|
|API跨平台权限变更|类名：CodecMimeType；<br>API声明：VIDEO_MPEG4 = 'video/mp4v-es'<br>差异内容：NA|类名：CodecMimeType；<br>API声明：VIDEO_MPEG4 = 'video/mp4v-es'<br>差异内容：crossplatform|api/@ohos.multimedia.media.d.ts|
|API跨平台权限变更|类名：CodecMimeType；<br>API声明：VIDEO_VP8 = 'video/x-vnd.on2.vp8'<br>差异内容：NA|类名：CodecMimeType；<br>API声明：VIDEO_VP8 = 'video/x-vnd.on2.vp8'<br>差异内容：crossplatform|api/@ohos.multimedia.media.d.ts|
|API跨平台权限变更|类名：CodecMimeType；<br>API声明：AUDIO_AAC = 'audio/mp4a-latm'<br>差异内容：NA|类名：CodecMimeType；<br>API声明：AUDIO_AAC = 'audio/mp4a-latm'<br>差异内容：crossplatform|api/@ohos.multimedia.media.d.ts|
|API跨平台权限变更|类名：CodecMimeType；<br>API声明：AUDIO_VORBIS = 'audio/vorbis'<br>差异内容：NA|类名：CodecMimeType；<br>API声明：AUDIO_VORBIS = 'audio/vorbis'<br>差异内容：crossplatform|api/@ohos.multimedia.media.d.ts|
|API跨平台权限变更|类名：CodecMimeType；<br>API声明：AUDIO_FLAC = 'audio/flac'<br>差异内容：NA|类名：CodecMimeType；<br>API声明：AUDIO_FLAC = 'audio/flac'<br>差异内容：crossplatform|api/@ohos.multimedia.media.d.ts|
|API跨平台权限变更|类名：CodecMimeType；<br>API声明：VIDEO_HEVC = 'video/hevc'<br>差异内容：NA|类名：CodecMimeType；<br>API声明：VIDEO_HEVC = 'video/hevc'<br>差异内容：crossplatform|api/@ohos.multimedia.media.d.ts|
|syscap变更|类名：global；<br>API声明：declare namespace media<br>差异内容：NA|类名：global；<br>API声明：declare namespace media<br>差异内容：SystemCapability.Multimedia.Media.Core|api/@ohos.multimedia.media.d.ts|
|API废弃版本变更|类名：AVRecorderConfig；<br>API声明：rotation?: number;<br>差异内容：NA|类名：AVRecorderConfig；<br>API声明：rotation?: number;<br>差异内容：12|api/@ohos.multimedia.media.d.ts|
|API废弃版本变更|类名：AVRecorderConfig；<br>API声明：location?: Location;<br>差异内容：NA|类名：AVRecorderConfig；<br>API声明：location?: Location;<br>差异内容：12|api/@ohos.multimedia.media.d.ts|
|新增错误码|类名：AudioRecorder；<br>API声明：prepare(config: AudioRecorderConfig): void;<br>差异内容：NA|类名：AudioRecorder；<br>API声明：prepare(config: AudioRecorderConfig): void;<br>差异内容：201|api/@ohos.multimedia.media.d.ts|
|函数变更|类名：AVPlayer；<br>API声明：off(type: 'stateChange'): void;<br>差异内容：NA|类名：AVPlayer；<br>API声明：off(type: 'stateChange', callback?: OnAVPlayerStateChangeHandle): void;<br>差异内容：callback?: OnAVPlayerStateChangeHandle|api/@ohos.multimedia.media.d.ts|
|函数变更|类名：AVPlayer；<br>API声明：off(type: 'volumeChange'): void;<br>差异内容：NA|类名：AVPlayer；<br>API声明：off(type: 'volumeChange', callback?: Callback\<number>): void;<br>差异内容：callback?: Callback\<number>|api/@ohos.multimedia.media.d.ts|
|函数变更|类名：AVPlayer；<br>API声明：off(type: 'endOfStream'): void;<br>差异内容：NA|类名：AVPlayer；<br>API声明：off(type: 'endOfStream', callback?: Callback\<void>): void;<br>差异内容：callback?: Callback\<void>|api/@ohos.multimedia.media.d.ts|
|函数变更|类名：AVPlayer；<br>API声明：off(type: 'seekDone'): void;<br>差异内容：NA|类名：AVPlayer；<br>API声明：off(type: 'seekDone', callback?: Callback\<number>): void;<br>差异内容：callback?: Callback\<number>|api/@ohos.multimedia.media.d.ts|
|函数变更|类名：AVPlayer；<br>API声明：off(type: 'speedDone'): void;<br>差异内容：NA|类名：AVPlayer；<br>API声明：off(type: 'speedDone', callback?: Callback\<number>): void;<br>差异内容：callback?: Callback\<number>|api/@ohos.multimedia.media.d.ts|
|函数变更|类名：AVPlayer；<br>API声明：off(type: 'bitrateDone'): void;<br>差异内容：NA|类名：AVPlayer；<br>API声明：off(type: 'bitrateDone', callback?: Callback\<number>): void;<br>差异内容：callback?: Callback\<number>|api/@ohos.multimedia.media.d.ts|
|函数变更|类名：AVPlayer；<br>API声明：off(type: 'timeUpdate'): void;<br>差异内容：NA|类名：AVPlayer；<br>API声明：off(type: 'timeUpdate', callback?: Callback\<number>): void;<br>差异内容：callback?: Callback\<number>|api/@ohos.multimedia.media.d.ts|
|函数变更|类名：AVPlayer；<br>API声明：off(type: 'durationUpdate'): void;<br>差异内容：NA|类名：AVPlayer；<br>API声明：off(type: 'durationUpdate', callback?: Callback\<number>): void;<br>差异内容：callback?: Callback\<number>|api/@ohos.multimedia.media.d.ts|
|函数变更|类名：AVPlayer；<br>API声明：off(type: 'bufferingUpdate'): void;<br>差异内容：NA|类名：AVPlayer；<br>API声明：off(type: 'bufferingUpdate', callback?: OnBufferingUpdateHandler): void;<br>差异内容：callback?: OnBufferingUpdateHandler|api/@ohos.multimedia.media.d.ts|
|函数变更|类名：AVPlayer；<br>API声明：off(type: 'startRenderFrame'): void;<br>差异内容：NA|类名：AVPlayer；<br>API声明：off(type: 'startRenderFrame', callback?: Callback\<void>): void;<br>差异内容：callback?: Callback\<void>|api/@ohos.multimedia.media.d.ts|
|函数变更|类名：AVPlayer；<br>API声明：off(type: 'videoSizeChange'): void;<br>差异内容：NA|类名：AVPlayer；<br>API声明：off(type: 'videoSizeChange', callback?: OnVideoSizeChangeHandler): void;<br>差异内容：callback?: OnVideoSizeChangeHandler|api/@ohos.multimedia.media.d.ts|
|函数变更|类名：AVPlayer；<br>API声明：off(type: 'audioInterrupt'): void;<br>差异内容：NA|类名：AVPlayer；<br>API声明：off(type: 'audioInterrupt', callback?: Callback\<audio.InterruptEvent>): void;<br>差异内容：callback?: Callback\<audio.InterruptEvent>|api/@ohos.multimedia.media.d.ts|
|函数变更|类名：AVPlayer；<br>API声明：off(type: 'availableBitrates'): void;<br>差异内容：NA|类名：AVPlayer；<br>API声明：off(type: 'availableBitrates', callback?: Callback\<Array\<number>>): void;<br>差异内容：callback?: Callback\<Array\<number>>|api/@ohos.multimedia.media.d.ts|
|函数变更|类名：AVPlayer；<br>API声明：off(type: 'error'): void;<br>差异内容：NA|类名：AVPlayer；<br>API声明：off(type: 'error', callback?: ErrorCallback): void;<br>差异内容：callback?: ErrorCallback|api/@ohos.multimedia.media.d.ts|
|函数变更|类名：AVRecorder；<br>API声明：off(type: 'stateChange'): void;<br>差异内容：NA|类名：AVRecorder；<br>API声明：off(type: 'stateChange', callback?: OnAVRecorderStateChangeHandler): void;<br>差异内容：callback?: OnAVRecorderStateChangeHandler|api/@ohos.multimedia.media.d.ts|
|函数变更|类名：AVRecorder；<br>API声明：off(type: 'error'): void;<br>差异内容：NA|类名：AVRecorder；<br>API声明：off(type: 'error', callback?: ErrorCallback): void;<br>差异内容：callback?: ErrorCallback|api/@ohos.multimedia.media.d.ts|
|函数变更|类名：AVRecorder；<br>API声明：off(type: 'audioCapturerChange'): void;<br>差异内容：NA|类名：AVRecorder；<br>API声明：off(type: 'audioCapturerChange', callback?: Callback\<audio.AudioCapturerChangeInfo>): void;<br>差异内容：callback?: Callback\<audio.AudioCapturerChangeInfo>|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：media；<br>API声明：function createMediaSourceWithUrl(url: string, headers?: Record\<string, string>): MediaSource;<br>差异内容：function createMediaSourceWithUrl(url: string, headers?: Record\<string, string>): MediaSource;|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：media；<br>API声明：function createAVScreenCaptureRecorder(): Promise\<AVScreenCaptureRecorder>;<br>差异内容：function createAVScreenCaptureRecorder(): Promise\<AVScreenCaptureRecorder>;|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：media；<br>API声明：function createAVTranscoder(): Promise\<AVTranscoder>;<br>差异内容：function createAVTranscoder(): Promise\<AVTranscoder>;|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：media；<br>API声明：function createAVImageGenerator(): Promise\<AVImageGenerator>;<br>差异内容：function createAVImageGenerator(): Promise\<AVImageGenerator>;|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：media；<br>API声明：function createAVImageGenerator(callback: AsyncCallback\<AVImageGenerator>): void;<br>差异内容：function createAVImageGenerator(callback: AsyncCallback\<AVImageGenerator>): void;|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：AVMetadata；<br>API声明：hdrType?: HdrType;<br>差异内容：hdrType?: HdrType;|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：AVMetadata；<br>API声明：location?: Location;<br>差异内容：location?: Location;|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：AVMetadata；<br>API声明：customInfo?: Record\<string, string>;<br>差异内容：customInfo?: Record\<string, string>;|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：media；<br>API声明：enum HdrType<br>差异内容：enum HdrType|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：HdrType；<br>API声明：AV_HDR_TYPE_NONE = 0<br>差异内容：AV_HDR_TYPE_NONE = 0|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：HdrType；<br>API声明：AV_HDR_TYPE_VIVID = 1<br>差异内容：AV_HDR_TYPE_VIVID = 1|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：media；<br>API声明：interface AVImageGenerator<br>差异内容：interface AVImageGenerator|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：AVImageGenerator；<br>API声明：fdSrc?: AVFileDescriptor;<br>差异内容：fdSrc?: AVFileDescriptor;|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：AVImageGenerator；<br>API声明：fetchFrameByTime(timeUs: number, options: AVImageQueryOptions, param: PixelMapParams, callback: AsyncCallback\<image.PixelMap>): void;<br>差异内容：fetchFrameByTime(timeUs: number, options: AVImageQueryOptions, param: PixelMapParams, callback: AsyncCallback\<image.PixelMap>): void;|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：AVImageGenerator；<br>API声明：fetchFrameByTime(timeUs: number, options: AVImageQueryOptions, param: PixelMapParams): Promise\<image.PixelMap>;<br>差异内容：fetchFrameByTime(timeUs: number, options: AVImageQueryOptions, param: PixelMapParams): Promise\<image.PixelMap>;|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：AVImageGenerator；<br>API声明：release(callback: AsyncCallback\<void>): void;<br>差异内容：release(callback: AsyncCallback\<void>): void;|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：AVImageGenerator；<br>API声明：release(): Promise\<void>;<br>差异内容：release(): Promise\<void>;|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：media；<br>API声明：enum AVImageQueryOptions<br>差异内容：enum AVImageQueryOptions|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：AVImageQueryOptions；<br>API声明：AV_IMAGE_QUERY_NEXT_SYNC<br>差异内容：AV_IMAGE_QUERY_NEXT_SYNC|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：AVImageQueryOptions；<br>API声明：AV_IMAGE_QUERY_PREVIOUS_SYNC<br>差异内容：AV_IMAGE_QUERY_PREVIOUS_SYNC|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：AVImageQueryOptions；<br>API声明：AV_IMAGE_QUERY_CLOSEST_SYNC<br>差异内容：AV_IMAGE_QUERY_CLOSEST_SYNC|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：AVImageQueryOptions；<br>API声明：AV_IMAGE_QUERY_CLOSEST<br>差异内容：AV_IMAGE_QUERY_CLOSEST|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：media；<br>API声明：interface PixelMapParams<br>差异内容：interface PixelMapParams|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：PixelMapParams；<br>API声明：width?: number;<br>差异内容：width?: number;|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：PixelMapParams；<br>API声明：height?: number;<br>差异内容：height?: number;|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：media；<br>API声明：type OnTrackChangeHandler = (index: number, isSelected: boolean) => void;<br>差异内容：type OnTrackChangeHandler = (index: number, isSelected: boolean) => void;|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：media；<br>API声明：type OnAVPlayerStateChangeHandle = (state: AVPlayerState, reason: StateChangeReason) => void;<br>差异内容：type OnAVPlayerStateChangeHandle = (state: AVPlayerState, reason: StateChangeReason) => void;|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：media；<br>API声明：type OnBufferingUpdateHandler = (infoType: BufferingInfoType, value: number) => void;<br>差异内容：type OnBufferingUpdateHandler = (infoType: BufferingInfoType, value: number) => void;|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：media；<br>API声明：type OnVideoSizeChangeHandler = (width: number, height: number) => void;<br>差异内容：type OnVideoSizeChangeHandler = (width: number, height: number) => void;|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：AVPlayer；<br>API声明：getSelectedTracks(): Promise\<Array\<number>>;<br>差异内容：getSelectedTracks(): Promise\<Array\<number>>;|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：AVPlayer；<br>API声明：selectTrack(index: number, mode?: SwitchMode): Promise\<void>;<br>差异内容：selectTrack(index: number, mode?: SwitchMode): Promise\<void>;|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：AVPlayer；<br>API声明：deselectTrack(index: number): Promise\<void>;<br>差异内容：deselectTrack(index: number): Promise\<void>;|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：AVPlayer；<br>API声明：setMediaSource(src: MediaSource, strategy?: PlaybackStrategy): Promise\<void>;<br>差异内容：setMediaSource(src: MediaSource, strategy?: PlaybackStrategy): Promise\<void>;|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：AVPlayer；<br>API声明：addSubtitleFromFd(fd: number, offset?: number, length?: number): Promise\<void>;<br>差异内容：addSubtitleFromFd(fd: number, offset?: number, length?: number): Promise\<void>;|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：AVPlayer；<br>API声明：addSubtitleFromUrl(url: string): Promise\<void>;<br>差异内容：addSubtitleFromUrl(url: string): Promise\<void>;|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：AVPlayer；<br>API声明：getPlaybackInfo(): Promise\<PlaybackInfo>;<br>差异内容：getPlaybackInfo(): Promise\<PlaybackInfo>;|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：AVPlayer；<br>API声明：setPlaybackStrategy(strategy: PlaybackStrategy): Promise\<void>;<br>差异内容：setPlaybackStrategy(strategy: PlaybackStrategy): Promise\<void>;|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：AVPlayer；<br>API声明：setMediaMuted(mediaType: MediaType, muted: boolean): Promise\<void>;<br>差异内容：setMediaMuted(mediaType: MediaType, muted: boolean): Promise\<void>;|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：AVPlayer；<br>API声明：on(type: 'subtitleUpdate', callback: Callback\<SubtitleInfo>): void;<br>差异内容：on(type: 'subtitleUpdate', callback: Callback\<SubtitleInfo>): void;|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：AVPlayer；<br>API声明：off(type: 'subtitleUpdate', callback?: Callback\<SubtitleInfo>): void;<br>差异内容：off(type: 'subtitleUpdate', callback?: Callback\<SubtitleInfo>): void;|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：AVPlayer；<br>API声明：on(type: 'trackChange', callback: OnTrackChangeHandler): void;<br>差异内容：on(type: 'trackChange', callback: OnTrackChangeHandler): void;|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：AVPlayer；<br>API声明：off(type: 'trackChange', callback?: OnTrackChangeHandler): void;<br>差异内容：off(type: 'trackChange', callback?: OnTrackChangeHandler): void;|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：AVPlayer；<br>API声明：on(type: 'trackInfoUpdate', callback: Callback\<Array\<MediaDescription>>): void;<br>差异内容：on(type: 'trackInfoUpdate', callback: Callback\<Array\<MediaDescription>>): void;|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：AVPlayer；<br>API声明：off(type: 'trackInfoUpdate', callback?: Callback\<Array\<MediaDescription>>): void;<br>差异内容：off(type: 'trackInfoUpdate', callback?: Callback\<Array\<MediaDescription>>): void;|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：media；<br>API声明：interface PlaybackInfo<br>差异内容：interface PlaybackInfo|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：PlaybackInfo；<br>API声明：[key: string]: Object;<br>差异内容：[key: string]: Object;|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：media；<br>API声明：enum PlaybackInfoKey<br>差异内容：enum PlaybackInfoKey|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：PlaybackInfoKey；<br>API声明：SERVER_IP_ADDRESS = 'server_ip_address'<br>差异内容：SERVER_IP_ADDRESS = 'server_ip_address'|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：PlaybackInfoKey；<br>API声明：AVG_DOWNLOAD_RATE = 'average_download_rate'<br>差异内容：AVG_DOWNLOAD_RATE = 'average_download_rate'|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：PlaybackInfoKey；<br>API声明：DOWNLOAD_RATE = 'download_rate'<br>差异内容：DOWNLOAD_RATE = 'download_rate'|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：PlaybackInfoKey；<br>API声明：IS_DOWNLOADING = 'is_downloading'<br>差异内容：IS_DOWNLOADING = 'is_downloading'|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：PlaybackInfoKey；<br>API声明：BUFFER_DURATION = 'buffer_duration'<br>差异内容：BUFFER_DURATION = 'buffer_duration'|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：media；<br>API声明：interface MediaSource<br>差异内容：interface MediaSource|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：MediaSource；<br>API声明：setMimeType(mimeType: AVMimeTypes): void;<br>差异内容：setMimeType(mimeType: AVMimeTypes): void;|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：media；<br>API声明：enum AVMimeTypes<br>差异内容：enum AVMimeTypes|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：AVMimeTypes；<br>API声明：APPLICATION_M3U8 = 'application/m3u8'<br>差异内容：APPLICATION_M3U8 = 'application/m3u8'|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：media；<br>API声明：interface PlaybackStrategy<br>差异内容：interface PlaybackStrategy|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：PlaybackStrategy；<br>API声明：preferredWidth?: number;<br>差异内容：preferredWidth?: number;|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：PlaybackStrategy；<br>API声明：preferredHeight?: number;<br>差异内容：preferredHeight?: number;|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：PlaybackStrategy；<br>API声明：preferredBufferDuration?: number;<br>差异内容：preferredBufferDuration?: number;|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：PlaybackStrategy；<br>API声明：preferredHdr?: boolean;<br>差异内容：preferredHdr?: boolean;|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：PlaybackStrategy；<br>API声明：mutedMediaType?: MediaType;<br>差异内容：mutedMediaType?: MediaType;|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：media；<br>API声明：interface SubtitleInfo<br>差异内容：interface SubtitleInfo|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：SubtitleInfo；<br>API声明：duration?: number;<br>差异内容：duration?: number;|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：SubtitleInfo；<br>API声明：startTime?: number;<br>差异内容：startTime?: number;|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：SubtitleInfo；<br>API声明：text?: string;<br>差异内容：text?: string;|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：media；<br>API声明：type OnAVRecorderStateChangeHandler = (state: AVRecorderState, reason: StateChangeReason) => void;<br>差异内容：type OnAVRecorderStateChangeHandler = (state: AVRecorderState, reason: StateChangeReason) => void;|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：AVRecorder；<br>API声明：updateRotation(rotation: number): Promise\<void>;<br>差异内容：updateRotation(rotation: number): Promise\<void>;|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：AVRecorder；<br>API声明：on(type: 'photoAssetAvailable', callback: Callback\<photoAccessHelper.PhotoAsset>): void;<br>差异内容：on(type: 'photoAssetAvailable', callback: Callback\<photoAccessHelper.PhotoAsset>): void;|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：AVRecorder；<br>API声明：off(type: 'photoAssetAvailable', callback?: Callback\<photoAccessHelper.PhotoAsset>): void;<br>差异内容：off(type: 'photoAssetAvailable', callback?: Callback\<photoAccessHelper.PhotoAsset>): void;|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：PlaybackSpeed；<br>API声明：SPEED_FORWARD_0_50_X = 5<br>差异内容：SPEED_FORWARD_0_50_X = 5|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：PlaybackSpeed；<br>API声明：SPEED_FORWARD_1_50_X = 6<br>差异内容：SPEED_FORWARD_1_50_X = 6|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：PlaybackSpeed；<br>API声明：SPEED_FORWARD_0_25_X = 8<br>差异内容：SPEED_FORWARD_0_25_X = 8|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：PlaybackSpeed；<br>API声明：SPEED_FORWARD_0_125_X = 9<br>差异内容：SPEED_FORWARD_0_125_X = 9|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：ContainerFormatType；<br>API声明：CFT_MP3 = 'mp3'<br>差异内容：CFT_MP3 = 'mp3'|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：ContainerFormatType；<br>API声明：CFT_WAV = 'wav'<br>差异内容：CFT_WAV = 'wav'|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：MediaType；<br>API声明：MEDIA_TYPE_SUBTITLE = 2<br>差异内容：MEDIA_TYPE_SUBTITLE = 2|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：MediaDescriptionKey；<br>API声明：MD_KEY_AUD_SAMPLE_DEPTH = 'sample_depth'<br>差异内容：MD_KEY_AUD_SAMPLE_DEPTH = 'sample_depth'|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：MediaDescriptionKey；<br>API声明：MD_KEY_LANGUAGE = 'language'<br>差异内容：MD_KEY_LANGUAGE = 'language'|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：MediaDescriptionKey；<br>API声明：MD_KEY_TRACK_NAME = 'track_name'<br>差异内容：MD_KEY_TRACK_NAME = 'track_name'|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：MediaDescriptionKey；<br>API声明：MD_KEY_HDR_TYPE = 'hdr_type'<br>差异内容：MD_KEY_HDR_TYPE = 'hdr_type'|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：AudioSourceType；<br>API声明：AUDIO_SOURCE_TYPE_VOICE_RECOGNITION = 2<br>差异内容：AUDIO_SOURCE_TYPE_VOICE_RECOGNITION = 2|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：AudioSourceType；<br>API声明：AUDIO_SOURCE_TYPE_VOICE_COMMUNICATION = 7<br>差异内容：AUDIO_SOURCE_TYPE_VOICE_COMMUNICATION = 7|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：AudioSourceType；<br>API声明：AUDIO_SOURCE_TYPE_VOICE_MESSAGE = 10<br>差异内容：AUDIO_SOURCE_TYPE_VOICE_MESSAGE = 10|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：AudioSourceType；<br>API声明：AUDIO_SOURCE_TYPE_CAMCORDER = 13<br>差异内容：AUDIO_SOURCE_TYPE_CAMCORDER = 13|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：media；<br>API声明：enum FileGenerationMode<br>差异内容：enum FileGenerationMode|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：FileGenerationMode；<br>API声明：APP_CREATE = 0<br>差异内容：APP_CREATE = 0|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：FileGenerationMode；<br>API声明：AUTO_CREATE_CAMERA_SCENE = 1<br>差异内容：AUTO_CREATE_CAMERA_SCENE = 1|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：AVRecorderProfile；<br>API声明：enableTemporalScale?: boolean;<br>差异内容：enableTemporalScale?: boolean;|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：AVRecorderConfig；<br>API声明：fileGenerationMode?: FileGenerationMode;<br>差异内容：fileGenerationMode?: FileGenerationMode;|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：AVRecorderConfig；<br>API声明：metadata?: AVMetadata;<br>差异内容：metadata?: AVMetadata;|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：SeekMode；<br>API声明：SEEK_CLOSEST = 2<br>差异内容：SEEK_CLOSEST = 2|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：media；<br>API声明：enum SwitchMode<br>差异内容：enum SwitchMode|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：SwitchMode；<br>API声明：SMOOTH = 0<br>差异内容：SMOOTH = 0|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：SwitchMode；<br>API声明：SEGMENT = 1<br>差异内容：SEGMENT = 1|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：SwitchMode；<br>API声明：CLOSEST = 2<br>差异内容：CLOSEST = 2|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：CodecMimeType；<br>API声明：AUDIO_MP3 = 'audio/mpeg'<br>差异内容：AUDIO_MP3 = 'audio/mpeg'|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：CodecMimeType；<br>API声明：AUDIO_G711MU = 'audio/g711mu'<br>差异内容：AUDIO_G711MU = 'audio/g711mu'|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：media；<br>API声明：enum AVScreenCaptureRecordPreset<br>差异内容：enum AVScreenCaptureRecordPreset|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：AVScreenCaptureRecordPreset；<br>API声明：SCREEN_RECORD_PRESET_H264_AAC_MP4 = 0<br>差异内容：SCREEN_RECORD_PRESET_H264_AAC_MP4 = 0|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：AVScreenCaptureRecordPreset；<br>API声明：SCREEN_RECORD_PRESET_H265_AAC_MP4 = 1<br>差异内容：SCREEN_RECORD_PRESET_H265_AAC_MP4 = 1|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：media；<br>API声明：enum AVScreenCaptureStateCode<br>差异内容：enum AVScreenCaptureStateCode|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：AVScreenCaptureStateCode；<br>API声明：SCREENCAPTURE_STATE_STARTED = 0<br>差异内容：SCREENCAPTURE_STATE_STARTED = 0|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：AVScreenCaptureStateCode；<br>API声明：SCREENCAPTURE_STATE_CANCELED = 1<br>差异内容：SCREENCAPTURE_STATE_CANCELED = 1|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：AVScreenCaptureStateCode；<br>API声明：SCREENCAPTURE_STATE_STOPPED_BY_USER = 2<br>差异内容：SCREENCAPTURE_STATE_STOPPED_BY_USER = 2|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：AVScreenCaptureStateCode；<br>API声明：SCREENCAPTURE_STATE_INTERRUPTED_BY_OTHER = 3<br>差异内容：SCREENCAPTURE_STATE_INTERRUPTED_BY_OTHER = 3|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：AVScreenCaptureStateCode；<br>API声明：SCREENCAPTURE_STATE_STOPPED_BY_CALL = 4<br>差异内容：SCREENCAPTURE_STATE_STOPPED_BY_CALL = 4|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：AVScreenCaptureStateCode；<br>API声明：SCREENCAPTURE_STATE_MIC_UNAVAILABLE = 5<br>差异内容：SCREENCAPTURE_STATE_MIC_UNAVAILABLE = 5|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：AVScreenCaptureStateCode；<br>API声明：SCREENCAPTURE_STATE_MIC_MUTED_BY_USER = 6<br>差异内容：SCREENCAPTURE_STATE_MIC_MUTED_BY_USER = 6|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：AVScreenCaptureStateCode；<br>API声明：SCREENCAPTURE_STATE_MIC_UNMUTED_BY_USER = 7<br>差异内容：SCREENCAPTURE_STATE_MIC_UNMUTED_BY_USER = 7|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：AVScreenCaptureStateCode；<br>API声明：SCREENCAPTURE_STATE_ENTER_PRIVATE_SCENE = 8<br>差异内容：SCREENCAPTURE_STATE_ENTER_PRIVATE_SCENE = 8|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：AVScreenCaptureStateCode；<br>API声明：SCREENCAPTURE_STATE_EXIT_PRIVATE_SCENE = 9<br>差异内容：SCREENCAPTURE_STATE_EXIT_PRIVATE_SCENE = 9|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：AVScreenCaptureStateCode；<br>API声明：SCREENCAPTURE_STATE_STOPPED_BY_USER_SWITCHES = 10<br>差异内容：SCREENCAPTURE_STATE_STOPPED_BY_USER_SWITCHES = 10|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：media；<br>API声明：interface AVScreenCaptureRecordConfig<br>差异内容：interface AVScreenCaptureRecordConfig|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：AVScreenCaptureRecordConfig；<br>API声明：fd: number;<br>差异内容：fd: number;|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：AVScreenCaptureRecordConfig；<br>API声明：frameWidth?: number;<br>差异内容：frameWidth?: number;|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：AVScreenCaptureRecordConfig；<br>API声明：frameHeight?: number;<br>差异内容：frameHeight?: number;|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：AVScreenCaptureRecordConfig；<br>API声明：videoBitrate?: number;<br>差异内容：videoBitrate?: number;|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：AVScreenCaptureRecordConfig；<br>API声明：audioSampleRate?: number;<br>差异内容：audioSampleRate?: number;|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：AVScreenCaptureRecordConfig；<br>API声明：audioChannelCount?: number;<br>差异内容：audioChannelCount?: number;|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：AVScreenCaptureRecordConfig；<br>API声明：audioBitrate?: number;<br>差异内容：audioBitrate?: number;|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：AVScreenCaptureRecordConfig；<br>API声明：preset?: AVScreenCaptureRecordPreset;<br>差异内容：preset?: AVScreenCaptureRecordPreset;|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：media；<br>API声明：interface AVScreenCaptureRecorder<br>差异内容：interface AVScreenCaptureRecorder|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：AVScreenCaptureRecorder；<br>API声明：init(config: AVScreenCaptureRecordConfig): Promise\<void>;<br>差异内容：init(config: AVScreenCaptureRecordConfig): Promise\<void>;|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：AVScreenCaptureRecorder；<br>API声明：startRecording(): Promise\<void>;<br>差异内容：startRecording(): Promise\<void>;|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：AVScreenCaptureRecorder；<br>API声明：stopRecording(): Promise\<void>;<br>差异内容：stopRecording(): Promise\<void>;|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：AVScreenCaptureRecorder；<br>API声明：skipPrivacyMode(windowIDs: Array\<number>): Promise\<void>;<br>差异内容：skipPrivacyMode(windowIDs: Array\<number>): Promise\<void>;|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：AVScreenCaptureRecorder；<br>API声明：setMicEnabled(enable: boolean): Promise\<void>;<br>差异内容：setMicEnabled(enable: boolean): Promise\<void>;|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：AVScreenCaptureRecorder；<br>API声明：release(): Promise\<void>;<br>差异内容：release(): Promise\<void>;|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：AVScreenCaptureRecorder；<br>API声明：on(type: 'stateChange', callback: Callback\<AVScreenCaptureStateCode>): void;<br>差异内容：on(type: 'stateChange', callback: Callback\<AVScreenCaptureStateCode>): void;|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：AVScreenCaptureRecorder；<br>API声明：on(type: 'error', callback: ErrorCallback): void;<br>差异内容：on(type: 'error', callback: ErrorCallback): void;|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：AVScreenCaptureRecorder；<br>API声明：off(type: 'stateChange', callback?: Callback\<AVScreenCaptureStateCode>): void;<br>差异内容：off(type: 'stateChange', callback?: Callback\<AVScreenCaptureStateCode>): void;|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：AVScreenCaptureRecorder；<br>API声明：off(type: 'error', callback?: ErrorCallback): void;<br>差异内容：off(type: 'error', callback?: ErrorCallback): void;|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：media；<br>API声明：interface AVTranscoderConfig<br>差异内容：interface AVTranscoderConfig|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：AVTranscoderConfig；<br>API声明：audioBitrate?: number;<br>差异内容：audioBitrate?: number;|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：AVTranscoderConfig；<br>API声明：audioCodec?: CodecMimeType;<br>差异内容：audioCodec?: CodecMimeType;|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：AVTranscoderConfig；<br>API声明：fileFormat: ContainerFormatType;<br>差异内容：fileFormat: ContainerFormatType;|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：AVTranscoderConfig；<br>API声明：videoBitrate?: number;<br>差异内容：videoBitrate?: number;|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：AVTranscoderConfig；<br>API声明：videoCodec?: CodecMimeType;<br>差异内容：videoCodec?: CodecMimeType;|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：AVTranscoderConfig；<br>API声明：videoFrameWidth?: number;<br>差异内容：videoFrameWidth?: number;|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：AVTranscoderConfig；<br>API声明：videoFrameHeight?: number;<br>差异内容：videoFrameHeight?: number;|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：media；<br>API声明：interface AVTranscoder<br>差异内容：interface AVTranscoder|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：AVTranscoder；<br>API声明：fdSrc: AVFileDescriptor;<br>差异内容：fdSrc: AVFileDescriptor;|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：AVTranscoder；<br>API声明：fdDst: number;<br>差异内容：fdDst: number;|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：AVTranscoder；<br>API声明：prepare(config: AVTranscoderConfig): Promise\<void>;<br>差异内容：prepare(config: AVTranscoderConfig): Promise\<void>;|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：AVTranscoder；<br>API声明：start(): Promise\<void>;<br>差异内容：start(): Promise\<void>;|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：AVTranscoder；<br>API声明：pause(): Promise\<void>;<br>差异内容：pause(): Promise\<void>;|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：AVTranscoder；<br>API声明：resume(): Promise\<void>;<br>差异内容：resume(): Promise\<void>;|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：AVTranscoder；<br>API声明：cancel(): Promise\<void>;<br>差异内容：cancel(): Promise\<void>;|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：AVTranscoder；<br>API声明：release(): Promise\<void>;<br>差异内容：release(): Promise\<void>;|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：AVTranscoder；<br>API声明：on(type: 'complete', callback: Callback\<void>): void;<br>差异内容：on(type: 'complete', callback: Callback\<void>): void;|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：AVTranscoder；<br>API声明：on(type: 'error', callback: ErrorCallback): void;<br>差异内容：on(type: 'error', callback: ErrorCallback): void;|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：AVTranscoder；<br>API声明：on(type: 'progressUpdate', callback: Callback\<number>): void;<br>差异内容：on(type: 'progressUpdate', callback: Callback\<number>): void;|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：AVTranscoder；<br>API声明：off(type: 'complete', callback?: Callback\<void>): void;<br>差异内容：off(type: 'complete', callback?: Callback\<void>): void;|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：AVTranscoder；<br>API声明：off(type: 'error', callback?: ErrorCallback): void;<br>差异内容：off(type: 'error', callback?: ErrorCallback): void;|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：AVTranscoder；<br>API声明：off(type: 'progressUpdate', callback?: Callback\<number>): void;<br>差异内容：off(type: 'progressUpdate', callback?: Callback\<number>): void;|api/@ohos.multimedia.media.d.ts|
|新增kit|类名：global；<br>API声明：api\multimedia\soundPool.d.ts<br>差异内容：NA|类名：global；<br>API声明：api\multimedia\soundPool.d.ts<br>差异内容：MediaKit|api/multimedia/soundPool.d.ts|
|API从不支持元服务到支持元服务|类名：media；<br>API声明：function createAVRecorder(): Promise\<AVRecorder>;<br>差异内容：NA|类名：media；<br>API声明：function createAVRecorder(): Promise\<AVRecorder>;<br>差异内容：atomicservice|api/@ohos.multimedia.media.d.ts|
|API从不支持元服务到支持元服务|类名：AVPlayer；<br>API声明：setVolume(volume: number): void;<br>差异内容：NA|类名：AVPlayer；<br>API声明：setVolume(volume: number): void;<br>差异内容：atomicservice|api/@ohos.multimedia.media.d.ts|
|API从不支持元服务到支持元服务|类名：AVPlayer；<br>API声明：loop: boolean;<br>差异内容：NA|类名：AVPlayer；<br>API声明：loop: boolean;<br>差异内容：atomicservice|api/@ohos.multimedia.media.d.ts|
|API从不支持元服务到支持元服务|类名：AVPlayer；<br>API声明：audioInterruptMode?: audio.InterruptMode;<br>差异内容：NA|类名：AVPlayer；<br>API声明：audioInterruptMode?: audio.InterruptMode;<br>差异内容：atomicservice|api/@ohos.multimedia.media.d.ts|
|API从不支持元服务到支持元服务|类名：AVPlayer；<br>API声明：audioRendererInfo?: audio.AudioRendererInfo;<br>差异内容：NA|类名：AVPlayer；<br>API声明：audioRendererInfo?: audio.AudioRendererInfo;<br>差异内容：atomicservice|api/@ohos.multimedia.media.d.ts|
|API从不支持元服务到支持元服务|类名：AVPlayer；<br>API声明：audioEffectMode?: audio.AudioEffectMode;<br>差异内容：NA|类名：AVPlayer；<br>API声明：audioEffectMode?: audio.AudioEffectMode;<br>差异内容：atomicservice|api/@ohos.multimedia.media.d.ts|
|API从不支持元服务到支持元服务|类名：AVPlayer；<br>API声明：readonly currentTime: number;<br>差异内容：NA|类名：AVPlayer；<br>API声明：readonly currentTime: number;<br>差异内容：atomicservice|api/@ohos.multimedia.media.d.ts|
|API从不支持元服务到支持元服务|类名：AVPlayer；<br>API声明：readonly state: AVPlayerState;<br>差异内容：NA|类名：AVPlayer；<br>API声明：readonly state: AVPlayerState;<br>差异内容：atomicservice|api/@ohos.multimedia.media.d.ts|
|API从不支持元服务到支持元服务|类名：AVPlayer；<br>API声明：readonly width: number;<br>差异内容：NA|类名：AVPlayer；<br>API声明：readonly width: number;<br>差异内容：atomicservice|api/@ohos.multimedia.media.d.ts|
|API从不支持元服务到支持元服务|类名：AVPlayer；<br>API声明：readonly height: number;<br>差异内容：NA|类名：AVPlayer；<br>API声明：readonly height: number;<br>差异内容：atomicservice|api/@ohos.multimedia.media.d.ts|
|API从不支持元服务到支持元服务|类名：AVPlayer；<br>API声明：videoScaleType?: VideoScaleType;<br>差异内容：NA|类名：AVPlayer；<br>API声明：videoScaleType?: VideoScaleType;<br>差异内容：atomicservice|api/@ohos.multimedia.media.d.ts|
|API从不支持元服务到支持元服务|类名：AVPlayer；<br>API声明：setSpeed(speed: PlaybackSpeed): void;<br>差异内容：NA|类名：AVPlayer；<br>API声明：setSpeed(speed: PlaybackSpeed): void;<br>差异内容：atomicservice|api/@ohos.multimedia.media.d.ts|
|API从不支持元服务到支持元服务|类名：AVPlayer；<br>API声明：setBitrate(bitrate: number): void;<br>差异内容：NA|类名：AVPlayer；<br>API声明：setBitrate(bitrate: number): void;<br>差异内容：atomicservice|api/@ohos.multimedia.media.d.ts|
|API从不支持元服务到支持元服务|类名：AVPlayer；<br>API声明：setDecryptionConfig(mediaKeySession: drm.MediaKeySession, secureVideoPath: boolean): void;<br>差异内容：NA|类名：AVPlayer；<br>API声明：setDecryptionConfig(mediaKeySession: drm.MediaKeySession, secureVideoPath: boolean): void;<br>差异内容：atomicservice|api/@ohos.multimedia.media.d.ts|
|API从不支持元服务到支持元服务|类名：AVPlayer；<br>API声明：getMediaKeySystemInfos(): Array\<drm.MediaKeySystemInfo>;<br>差异内容：NA|类名：AVPlayer；<br>API声明：getMediaKeySystemInfos(): Array\<drm.MediaKeySystemInfo>;<br>差异内容：atomicservice|api/@ohos.multimedia.media.d.ts|
|API从不支持元服务到支持元服务|类名：AVPlayer；<br>API声明：on(type: 'mediaKeySystemInfoUpdate', callback: (mediaKeySystemInfo: Array\<drm.MediaKeySystemInfo>) => void): void;<br>差异内容：NA|类名：AVPlayer；<br>API声明：on(type: 'mediaKeySystemInfoUpdate', callback: Callback\<Array\<drm.MediaKeySystemInfo>>): void;<br>差异内容：atomicservice|api/@ohos.multimedia.media.d.ts|
|API从不支持元服务到支持元服务|类名：AVPlayer；<br>API声明：off(type: 'mediaKeySystemInfoUpdate', callback?: (mediaKeySystemInfo: Array\<drm.MediaKeySystemInfo>) => void): void;<br>差异内容：NA|类名：AVPlayer；<br>API声明：off(type: 'mediaKeySystemInfoUpdate', callback?: Callback\<Array\<drm.MediaKeySystemInfo>>): void;<br>差异内容：atomicservice|api/@ohos.multimedia.media.d.ts|
|API从不支持元服务到支持元服务|类名：AVPlayer；<br>API声明：on(type: 'volumeChange', callback: Callback\<number>): void;<br>差异内容：NA|类名：AVPlayer；<br>API声明：on(type: 'volumeChange', callback: Callback\<number>): void;<br>差异内容：atomicservice|api/@ohos.multimedia.media.d.ts|
|API从不支持元服务到支持元服务|类名：AVPlayer；<br>API声明：on(type: 'endOfStream', callback: Callback\<void>): void;<br>差异内容：NA|类名：AVPlayer；<br>API声明：on(type: 'endOfStream', callback: Callback\<void>): void;<br>差异内容：atomicservice|api/@ohos.multimedia.media.d.ts|
|API从不支持元服务到支持元服务|类名：AVPlayer；<br>API声明：on(type: 'speedDone', callback: Callback\<number>): void;<br>差异内容：NA|类名：AVPlayer；<br>API声明：on(type: 'speedDone', callback: Callback\<number>): void;<br>差异内容：atomicservice|api/@ohos.multimedia.media.d.ts|
|API从不支持元服务到支持元服务|类名：AVPlayer；<br>API声明：on(type: 'bitrateDone', callback: Callback\<number>): void;<br>差异内容：NA|类名：AVPlayer；<br>API声明：on(type: 'bitrateDone', callback: Callback\<number>): void;<br>差异内容：atomicservice|api/@ohos.multimedia.media.d.ts|
|API从不支持元服务到支持元服务|类名：AVPlayer；<br>API声明：on(type: 'durationUpdate', callback: Callback\<number>): void;<br>差异内容：NA|类名：AVPlayer；<br>API声明：on(type: 'durationUpdate', callback: Callback\<number>): void;<br>差异内容：atomicservice|api/@ohos.multimedia.media.d.ts|
|API从不支持元服务到支持元服务|类名：AVPlayer；<br>API声明：on(type: 'bufferingUpdate', callback: (infoType: BufferingInfoType, value: number) => void): void;<br>差异内容：NA|类名：AVPlayer；<br>API声明：on(type: 'bufferingUpdate', callback: OnBufferingUpdateHandler): void;<br>差异内容：atomicservice|api/@ohos.multimedia.media.d.ts|
|API从不支持元服务到支持元服务|类名：AVPlayer；<br>API声明：off(type: 'bufferingUpdate'): void;<br>差异内容：NA|类名：AVPlayer；<br>API声明：off(type: 'bufferingUpdate', callback?: OnBufferingUpdateHandler): void;<br>差异内容：atomicservice|api/@ohos.multimedia.media.d.ts|
|API从不支持元服务到支持元服务|类名：AVPlayer；<br>API声明：on(type: 'startRenderFrame', callback: Callback\<void>): void;<br>差异内容：NA|类名：AVPlayer；<br>API声明：on(type: 'startRenderFrame', callback: Callback\<void>): void;<br>差异内容：atomicservice|api/@ohos.multimedia.media.d.ts|
|API从不支持元服务到支持元服务|类名：AVPlayer；<br>API声明：on(type: 'videoSizeChange', callback: (width: number, height: number) => void): void;<br>差异内容：NA|类名：AVPlayer；<br>API声明：on(type: 'videoSizeChange', callback: OnVideoSizeChangeHandler): void;<br>差异内容：atomicservice|api/@ohos.multimedia.media.d.ts|
|API从不支持元服务到支持元服务|类名：AVPlayer；<br>API声明：off(type: 'videoSizeChange'): void;<br>差异内容：NA|类名：AVPlayer；<br>API声明：off(type: 'videoSizeChange', callback?: OnVideoSizeChangeHandler): void;<br>差异内容：atomicservice|api/@ohos.multimedia.media.d.ts|
|API从不支持元服务到支持元服务|类名：AVPlayer；<br>API声明：on(type: 'audioInterrupt', callback: (info: audio.InterruptEvent) => void): void;<br>差异内容：NA|类名：AVPlayer；<br>API声明：on(type: 'audioInterrupt', callback: Callback\<audio.InterruptEvent>): void;<br>差异内容：atomicservice|api/@ohos.multimedia.media.d.ts|
|API从不支持元服务到支持元服务|类名：AVPlayer；<br>API声明：off(type: 'audioInterrupt'): void;<br>差异内容：NA|类名：AVPlayer；<br>API声明：off(type: 'audioInterrupt', callback?: Callback\<audio.InterruptEvent>): void;<br>差异内容：atomicservice|api/@ohos.multimedia.media.d.ts|
|API从不支持元服务到支持元服务|类名：AVPlayer；<br>API声明：on(type: 'availableBitrates', callback: (bitrates: Array\<number>) => void): void;<br>差异内容：NA|类名：AVPlayer；<br>API声明：on(type: 'availableBitrates', callback: Callback\<Array\<number>>): void;<br>差异内容：atomicservice|api/@ohos.multimedia.media.d.ts|
|API从不支持元服务到支持元服务|类名：AVPlayer；<br>API声明：off(type: 'availableBitrates'): void;<br>差异内容：NA|类名：AVPlayer；<br>API声明：off(type: 'availableBitrates', callback?: Callback\<Array\<number>>): void;<br>差异内容：atomicservice|api/@ohos.multimedia.media.d.ts|
|API从不支持元服务到支持元服务|类名：AVPlayer；<br>API声明：on(type: 'audioOutputDeviceChangeWithInfo', callback: Callback\<audio.AudioStreamDeviceChangeInfo>): void;<br>差异内容：NA|类名：AVPlayer；<br>API声明：on(type: 'audioOutputDeviceChangeWithInfo', callback: Callback\<audio.AudioStreamDeviceChangeInfo>): void;<br>差异内容：atomicservice|api/@ohos.multimedia.media.d.ts|
|API从不支持元服务到支持元服务|类名：AVPlayer；<br>API声明：off(type: 'audioOutputDeviceChangeWithInfo', callback?: Callback\<audio.AudioStreamDeviceChangeInfo>): void;<br>差异内容：NA|类名：AVPlayer；<br>API声明：off(type: 'audioOutputDeviceChangeWithInfo', callback?: Callback\<audio.AudioStreamDeviceChangeInfo>): void;<br>差异内容：atomicservice|api/@ohos.multimedia.media.d.ts|
|API从不支持元服务到支持元服务|类名：media；<br>API声明：enum BufferingInfoType<br>差异内容：NA|类名：media；<br>API声明：enum BufferingInfoType<br>差异内容：atomicservice|api/@ohos.multimedia.media.d.ts|
|API从不支持元服务到支持元服务|类名：BufferingInfoType；<br>API声明：BUFFERING_START = 1<br>差异内容：NA|类名：BufferingInfoType；<br>API声明：BUFFERING_START = 1<br>差异内容：atomicservice|api/@ohos.multimedia.media.d.ts|
|API从不支持元服务到支持元服务|类名：BufferingInfoType；<br>API声明：BUFFERING_END = 2<br>差异内容：NA|类名：BufferingInfoType；<br>API声明：BUFFERING_END = 2<br>差异内容：atomicservice|api/@ohos.multimedia.media.d.ts|
|API从不支持元服务到支持元服务|类名：BufferingInfoType；<br>API声明：BUFFERING_PERCENT = 3<br>差异内容：NA|类名：BufferingInfoType；<br>API声明：BUFFERING_PERCENT = 3<br>差异内容：atomicservice|api/@ohos.multimedia.media.d.ts|
|API从不支持元服务到支持元服务|类名：BufferingInfoType；<br>API声明：CACHED_DURATION = 4<br>差异内容：NA|类名：BufferingInfoType；<br>API声明：CACHED_DURATION = 4<br>差异内容：atomicservice|api/@ohos.multimedia.media.d.ts|
|API从不支持元服务到支持元服务|类名：media；<br>API声明：type AVRecorderState = 'idle' \| 'prepared' \| 'started' \| 'paused' \| 'stopped' \| 'released' \| 'error';<br>差异内容：NA|类名：media；<br>API声明：type AVRecorderState = 'idle' \| 'prepared' \| 'started' \| 'paused' \| 'stopped' \| 'released' \| 'error';<br>差异内容：atomicservice|api/@ohos.multimedia.media.d.ts|
|API从不支持元服务到支持元服务|类名：media；<br>API声明：interface AVRecorder<br>差异内容：NA|类名：media；<br>API声明：interface AVRecorder<br>差异内容：atomicservice|api/@ohos.multimedia.media.d.ts|
|API从不支持元服务到支持元服务|类名：AVRecorder；<br>API声明：prepare(config: AVRecorderConfig): Promise\<void>;<br>差异内容：NA|类名：AVRecorder；<br>API声明：prepare(config: AVRecorderConfig): Promise\<void>;<br>差异内容：atomicservice|api/@ohos.multimedia.media.d.ts|
|API从不支持元服务到支持元服务|类名：AVRecorder；<br>API声明：start(): Promise\<void>;<br>差异内容：NA|类名：AVRecorder；<br>API声明：start(): Promise\<void>;<br>差异内容：atomicservice|api/@ohos.multimedia.media.d.ts|
|API从不支持元服务到支持元服务|类名：AVRecorder；<br>API声明：pause(): Promise\<void>;<br>差异内容：NA|类名：AVRecorder；<br>API声明：pause(): Promise\<void>;<br>差异内容：atomicservice|api/@ohos.multimedia.media.d.ts|
|API从不支持元服务到支持元服务|类名：AVRecorder；<br>API声明：resume(): Promise\<void>;<br>差异内容：NA|类名：AVRecorder；<br>API声明：resume(): Promise\<void>;<br>差异内容：atomicservice|api/@ohos.multimedia.media.d.ts|
|API从不支持元服务到支持元服务|类名：AVRecorder；<br>API声明：stop(): Promise\<void>;<br>差异内容：NA|类名：AVRecorder；<br>API声明：stop(): Promise\<void>;<br>差异内容：atomicservice|api/@ohos.multimedia.media.d.ts|
|API从不支持元服务到支持元服务|类名：AVRecorder；<br>API声明：release(): Promise\<void>;<br>差异内容：NA|类名：AVRecorder；<br>API声明：release(): Promise\<void>;<br>差异内容：atomicservice|api/@ohos.multimedia.media.d.ts|
|API从不支持元服务到支持元服务|类名：AVRecorder；<br>API声明：readonly state: AVRecorderState;<br>差异内容：NA|类名：AVRecorder；<br>API声明：readonly state: AVRecorderState;<br>差异内容：atomicservice|api/@ohos.multimedia.media.d.ts|
|API从不支持元服务到支持元服务|类名：AVRecorder；<br>API声明：on(type: 'stateChange', callback: (state: AVRecorderState, reason: StateChangeReason) => void): void;<br>差异内容：NA|类名：AVRecorder；<br>API声明：on(type: 'stateChange', callback: OnAVRecorderStateChangeHandler): void;<br>差异内容：atomicservice|api/@ohos.multimedia.media.d.ts|
|API从不支持元服务到支持元服务|类名：AVRecorder；<br>API声明：on(type: 'error', callback: ErrorCallback): void;<br>差异内容：NA|类名：AVRecorder；<br>API声明：on(type: 'error', callback: ErrorCallback): void;<br>差异内容：atomicservice|api/@ohos.multimedia.media.d.ts|
|API从不支持元服务到支持元服务|类名：AVRecorder；<br>API声明：off(type: 'stateChange'): void;<br>差异内容：NA|类名：AVRecorder；<br>API声明：off(type: 'stateChange', callback?: OnAVRecorderStateChangeHandler): void;<br>差异内容：atomicservice|api/@ohos.multimedia.media.d.ts|
|API从不支持元服务到支持元服务|类名：AVRecorder；<br>API声明：off(type: 'error'): void;<br>差异内容：NA|类名：AVRecorder；<br>API声明：off(type: 'error', callback?: ErrorCallback): void;<br>差异内容：atomicservice|api/@ohos.multimedia.media.d.ts|
|API从不支持元服务到支持元服务|类名：media；<br>API声明：enum PlaybackSpeed<br>差异内容：NA|类名：media；<br>API声明：enum PlaybackSpeed<br>差异内容：atomicservice|api/@ohos.multimedia.media.d.ts|
|API从不支持元服务到支持元服务|类名：PlaybackSpeed；<br>API声明：SPEED_FORWARD_0_75_X = 0<br>差异内容：NA|类名：PlaybackSpeed；<br>API声明：SPEED_FORWARD_0_75_X = 0<br>差异内容：atomicservice|api/@ohos.multimedia.media.d.ts|
|API从不支持元服务到支持元服务|类名：PlaybackSpeed；<br>API声明：SPEED_FORWARD_1_00_X = 1<br>差异内容：NA|类名：PlaybackSpeed；<br>API声明：SPEED_FORWARD_1_00_X = 1<br>差异内容：atomicservice|api/@ohos.multimedia.media.d.ts|
|API从不支持元服务到支持元服务|类名：PlaybackSpeed；<br>API声明：SPEED_FORWARD_1_25_X = 2<br>差异内容：NA|类名：PlaybackSpeed；<br>API声明：SPEED_FORWARD_1_25_X = 2<br>差异内容：atomicservice|api/@ohos.multimedia.media.d.ts|
|API从不支持元服务到支持元服务|类名：PlaybackSpeed；<br>API声明：SPEED_FORWARD_1_75_X = 3<br>差异内容：NA|类名：PlaybackSpeed；<br>API声明：SPEED_FORWARD_1_75_X = 3<br>差异内容：atomicservice|api/@ohos.multimedia.media.d.ts|
|API从不支持元服务到支持元服务|类名：PlaybackSpeed；<br>API声明：SPEED_FORWARD_2_00_X = 4<br>差异内容：NA|类名：PlaybackSpeed；<br>API声明：SPEED_FORWARD_2_00_X = 4<br>差异内容：atomicservice|api/@ohos.multimedia.media.d.ts|
|API从不支持元服务到支持元服务|类名：media；<br>API声明：enum VideoScaleType<br>差异内容：NA|类名：media；<br>API声明：enum VideoScaleType<br>差异内容：atomicservice|api/@ohos.multimedia.media.d.ts|
|API从不支持元服务到支持元服务|类名：VideoScaleType；<br>API声明：VIDEO_SCALE_TYPE_FIT = 0<br>差异内容：NA|类名：VideoScaleType；<br>API声明：VIDEO_SCALE_TYPE_FIT = 0<br>差异内容：atomicservice|api/@ohos.multimedia.media.d.ts|
|API从不支持元服务到支持元服务|类名：VideoScaleType；<br>API声明：VIDEO_SCALE_TYPE_FIT_CROP = 1<br>差异内容：NA|类名：VideoScaleType；<br>API声明：VIDEO_SCALE_TYPE_FIT_CROP = 1<br>差异内容：atomicservice|api/@ohos.multimedia.media.d.ts|
|API从不支持元服务到支持元服务|类名：media；<br>API声明：enum ContainerFormatType<br>差异内容：NA|类名：media；<br>API声明：enum ContainerFormatType<br>差异内容：atomicservice|api/@ohos.multimedia.media.d.ts|
|API从不支持元服务到支持元服务|类名：ContainerFormatType；<br>API声明：CFT_MPEG_4A = 'm4a'<br>差异内容：NA|类名：ContainerFormatType；<br>API声明：CFT_MPEG_4A = 'm4a'<br>差异内容：atomicservice|api/@ohos.multimedia.media.d.ts|
|API从不支持元服务到支持元服务|类名：media；<br>API声明：enum AudioSourceType<br>差异内容：NA|类名：media；<br>API声明：enum AudioSourceType<br>差异内容：atomicservice|api/@ohos.multimedia.media.d.ts|
|API从不支持元服务到支持元服务|类名：AudioSourceType；<br>API声明：AUDIO_SOURCE_TYPE_MIC = 1<br>差异内容：NA|类名：AudioSourceType；<br>API声明：AUDIO_SOURCE_TYPE_MIC = 1<br>差异内容：atomicservice|api/@ohos.multimedia.media.d.ts|
|API从不支持元服务到支持元服务|类名：media；<br>API声明：interface AVRecorderProfile<br>差异内容：NA|类名：media；<br>API声明：interface AVRecorderProfile<br>差异内容：atomicservice|api/@ohos.multimedia.media.d.ts|
|API从不支持元服务到支持元服务|类名：AVRecorderProfile；<br>API声明：audioBitrate?: number;<br>差异内容：NA|类名：AVRecorderProfile；<br>API声明：audioBitrate?: number;<br>差异内容：atomicservice|api/@ohos.multimedia.media.d.ts|
|API从不支持元服务到支持元服务|类名：AVRecorderProfile；<br>API声明：audioChannels?: number;<br>差异内容：NA|类名：AVRecorderProfile；<br>API声明：audioChannels?: number;<br>差异内容：atomicservice|api/@ohos.multimedia.media.d.ts|
|API从不支持元服务到支持元服务|类名：AVRecorderProfile；<br>API声明：audioCodec?: CodecMimeType;<br>差异内容：NA|类名：AVRecorderProfile；<br>API声明：audioCodec?: CodecMimeType;<br>差异内容：atomicservice|api/@ohos.multimedia.media.d.ts|
|API从不支持元服务到支持元服务|类名：AVRecorderProfile；<br>API声明：audioSampleRate?: number;<br>差异内容：NA|类名：AVRecorderProfile；<br>API声明：audioSampleRate?: number;<br>差异内容：atomicservice|api/@ohos.multimedia.media.d.ts|
|API从不支持元服务到支持元服务|类名：AVRecorderProfile；<br>API声明：fileFormat: ContainerFormatType;<br>差异内容：NA|类名：AVRecorderProfile；<br>API声明：fileFormat: ContainerFormatType;<br>差异内容：atomicservice|api/@ohos.multimedia.media.d.ts|
|API从不支持元服务到支持元服务|类名：media；<br>API声明：interface AVRecorderConfig<br>差异内容：NA|类名：media；<br>API声明：interface AVRecorderConfig<br>差异内容：atomicservice|api/@ohos.multimedia.media.d.ts|
|API从不支持元服务到支持元服务|类名：AVRecorderConfig；<br>API声明：audioSourceType?: AudioSourceType;<br>差异内容：NA|类名：AVRecorderConfig；<br>API声明：audioSourceType?: AudioSourceType;<br>差异内容：atomicservice|api/@ohos.multimedia.media.d.ts|
|API从不支持元服务到支持元服务|类名：AVRecorderConfig；<br>API声明：profile: AVRecorderProfile;<br>差异内容：NA|类名：AVRecorderConfig；<br>API声明：profile: AVRecorderProfile;<br>差异内容：atomicservice|api/@ohos.multimedia.media.d.ts|
|API从不支持元服务到支持元服务|类名：AVRecorderConfig；<br>API声明：url: string;<br>差异内容：NA|类名：AVRecorderConfig；<br>API声明：url: string;<br>差异内容：atomicservice|api/@ohos.multimedia.media.d.ts|
|API从不支持元服务到支持元服务|类名：media；<br>API声明：enum CodecMimeType<br>差异内容：NA|类名：media；<br>API声明：enum CodecMimeType<br>差异内容：atomicservice|api/@ohos.multimedia.media.d.ts|
|API从不支持元服务到支持元服务|类名：CodecMimeType；<br>API声明：AUDIO_AAC = 'audio/mp4a-latm'<br>差异内容：NA|类名：CodecMimeType；<br>API声明：AUDIO_AAC = 'audio/mp4a-latm'<br>差异内容：atomicservice|api/@ohos.multimedia.media.d.ts|
|函数变更|类名：AVPlayer；<br>API声明：on(type: 'mediaKeySystemInfoUpdate', callback: (mediaKeySystemInfo: Array\<drm.MediaKeySystemInfo>) => void): void;<br>差异内容：callback: (mediaKeySystemInfo: Array\<drm.MediaKeySystemInfo>) => void|类名：AVPlayer；<br>API声明：on(type: 'mediaKeySystemInfoUpdate', callback: Callback\<Array\<drm.MediaKeySystemInfo>>): void;<br>差异内容：callback: Callback\<Array\<drm.MediaKeySystemInfo>>|api/@ohos.multimedia.media.d.ts|
|函数变更|类名：AVPlayer；<br>API声明：off(type: 'mediaKeySystemInfoUpdate', callback?: (mediaKeySystemInfo: Array\<drm.MediaKeySystemInfo>) => void): void;<br>差异内容：callback?: (mediaKeySystemInfo: Array\<drm.MediaKeySystemInfo>) => void|类名：AVPlayer；<br>API声明：off(type: 'mediaKeySystemInfoUpdate', callback?: Callback\<Array\<drm.MediaKeySystemInfo>>): void;<br>差异内容：callback?: Callback\<Array\<drm.MediaKeySystemInfo>>|api/@ohos.multimedia.media.d.ts|
|函数变更|类名：AVPlayer；<br>API声明：on(type: 'stateChange', callback: (state: AVPlayerState, reason: StateChangeReason) => void): void;<br>差异内容：callback: (state: AVPlayerState, reason: StateChangeReason) => void|类名：AVPlayer；<br>API声明：on(type: 'stateChange', callback: OnAVPlayerStateChangeHandle): void;<br>差异内容：callback: OnAVPlayerStateChangeHandle|api/@ohos.multimedia.media.d.ts|
|函数变更|类名：AVPlayer；<br>API声明：on(type: 'bufferingUpdate', callback: (infoType: BufferingInfoType, value: number) => void): void;<br>差异内容：callback: (infoType: BufferingInfoType, value: number) => void|类名：AVPlayer；<br>API声明：on(type: 'bufferingUpdate', callback: OnBufferingUpdateHandler): void;<br>差异内容：callback: OnBufferingUpdateHandler|api/@ohos.multimedia.media.d.ts|
|函数变更|类名：AVPlayer；<br>API声明：on(type: 'videoSizeChange', callback: (width: number, height: number) => void): void;<br>差异内容：callback: (width: number, height: number) => void|类名：AVPlayer；<br>API声明：on(type: 'videoSizeChange', callback: OnVideoSizeChangeHandler): void;<br>差异内容：callback: OnVideoSizeChangeHandler|api/@ohos.multimedia.media.d.ts|
|函数变更|类名：AVPlayer；<br>API声明：on(type: 'audioInterrupt', callback: (info: audio.InterruptEvent) => void): void;<br>差异内容：callback: (info: audio.InterruptEvent) => void|类名：AVPlayer；<br>API声明：on(type: 'audioInterrupt', callback: Callback\<audio.InterruptEvent>): void;<br>差异内容：callback: Callback\<audio.InterruptEvent>|api/@ohos.multimedia.media.d.ts|
|函数变更|类名：AVRecorder；<br>API声明：on(type: 'stateChange', callback: (state: AVRecorderState, reason: StateChangeReason) => void): void;<br>差异内容：callback: (state: AVRecorderState, reason: StateChangeReason) => void|类名：AVRecorder；<br>API声明：on(type: 'stateChange', callback: OnAVRecorderStateChangeHandler): void;<br>差异内容：callback: OnAVRecorderStateChangeHandler|api/@ohos.multimedia.media.d.ts|
|函数变更|类名：AVPlayer；<br>API声明：on(type: 'availableBitrates', callback: (bitrates: Array\<number>) => void): void;<br>差异内容：callback: (bitrates: Array\<number>) => void|类名：AVPlayer；<br>API声明：on(type: 'availableBitrates', callback: Callback\<Array\<number>>): void;<br>差异内容：callback: Callback\<Array\<number>>|api/@ohos.multimedia.media.d.ts|
