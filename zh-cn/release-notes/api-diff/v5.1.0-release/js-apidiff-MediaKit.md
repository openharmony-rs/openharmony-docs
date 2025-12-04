| 操作 | 旧版本 | 新版本 | d.ts文件 |
| ---- | ------ | ------ | -------- |
|syscap变更|类名：media；<br>API声明：type OnAVRecorderStateChangeHandler = (state: AVRecorderState, reason: StateChangeReason) => void;<br>差异内容：SystemCapability.Multimedia.Media.AVRecorder|类名：media；<br>API声明：type OnAVRecorderStateChangeHandler = (state: AVRecorderState, reason: StateChangeReason) => void;<br>差异内容：SystemCapability.Multimedia.Media.AVPlayer|api/@ohos.multimedia.media.d.ts|
|删除错误码|类名：AVPlayer；<br>API声明：on(type: 'error', callback: ErrorCallback): void;<br>差异内容：5410002|类名：AVPlayer；<br>API声明：on(type: 'error', callback: ErrorCallback): void;<br>差异内容：NA|api/@ohos.multimedia.media.d.ts|
|删除错误码|类名：AVTranscoder；<br>API声明：prepare(config: AVTranscoderConfig): Promise\<void>;<br>差异内容：5400103|类名：AVTranscoder；<br>API声明：prepare(config: AVTranscoderConfig): Promise\<void>;<br>差异内容：NA|api/@ohos.multimedia.media.d.ts|
|删除API|类名：global；<br>API声明：export enum ErrorType<br>差异内容：export enum ErrorType|NA|api/multimedia/soundPool.d.ts|
|删除API|类名：ErrorType；<br>API声明：LOAD_ERROR = 1<br>差异内容：LOAD_ERROR = 1|NA|api/multimedia/soundPool.d.ts|
|删除API|类名：ErrorType；<br>API声明：PLAY_ERROR = 2<br>差异内容：PLAY_ERROR = 2|NA|api/multimedia/soundPool.d.ts|
|删除API|类名：global；<br>API声明：export interface ErrorInfo<br>差异内容：export interface ErrorInfo|NA|api/multimedia/soundPool.d.ts|
|删除API|类名：ErrorInfo；<br>API声明：errorCode: T;<br>差异内容：errorCode: T;|NA|api/multimedia/soundPool.d.ts|
|删除API|类名：ErrorInfo；<br>API声明：errorType?: ErrorType;<br>差异内容：errorType?: ErrorType;|NA|api/multimedia/soundPool.d.ts|
|删除API|类名：ErrorInfo；<br>API声明：soundId?: number;<br>差异内容：soundId?: number;|NA|api/multimedia/soundPool.d.ts|
|删除API|类名：ErrorInfo；<br>API声明：streamId?: number;<br>差异内容：streamId?: number;|NA|api/multimedia/soundPool.d.ts|
|删除API|类名：SoundPool；<br>API声明：on(type: 'playFinishedWithStreamId', callback: Callback\<number>): void;<br>差异内容：on(type: 'playFinishedWithStreamId', callback: Callback\<number>): void;|NA|api/multimedia/soundPool.d.ts|
|删除API|类名：SoundPool；<br>API声明：off(type: 'playFinishedWithStreamId'): void;<br>差异内容：off(type: 'playFinishedWithStreamId'): void;|NA|api/multimedia/soundPool.d.ts|
|删除API|类名：SoundPool；<br>API声明：on(type: 'errorOccurred', callback: Callback\<ErrorInfo>): void;<br>差异内容：on(type: 'errorOccurred', callback: Callback\<ErrorInfo>): void;|NA|api/multimedia/soundPool.d.ts|
|删除API|类名：SoundPool；<br>API声明：off(type: 'errorOccurred', callback?: Callback\<ErrorInfo>): void;<br>差异内容：off(type: 'errorOccurred', callback?: Callback\<ErrorInfo>): void;|NA|api/multimedia/soundPool.d.ts|
|删除API|类名：media；<br>API声明：function createMediaSourceWithStreamData(streams: Array\<MediaStream>): MediaSource;<br>差异内容：function createMediaSourceWithStreamData(streams: Array\<MediaStream>): MediaSource;|NA|api/@ohos.multimedia.media.d.ts|
|删除API|类名：AVMetadataExtractor；<br>API声明：setUrlSource(url: string, headers?: Record\<string, string>): void;<br>差异内容：setUrlSource(url: string, headers?: Record\<string, string>): void;|NA|api/@ohos.multimedia.media.d.ts|
|删除API|类名：AVMetadataExtractor；<br>API声明：fetchFrameByTime(timeUs: number, options: AVImageQueryOptions, param: PixelMapParams): Promise\<image.PixelMap>;<br>差异内容：fetchFrameByTime(timeUs: number, options: AVImageQueryOptions, param: PixelMapParams): Promise\<image.PixelMap>;|NA|api/@ohos.multimedia.media.d.ts|
|删除API|类名：AVMetadata；<br>API声明：tracks?: Array\<MediaDescription>;<br>差异内容：tracks?: Array\<MediaDescription>;|NA|api/@ohos.multimedia.media.d.ts|
|删除API|类名：media；<br>API声明：declare interface OutputSize<br>差异内容：declare interface OutputSize|NA|api/@ohos.multimedia.media.d.ts|
|删除API|类名：OutputSize；<br>API声明：width?: number;<br>差异内容：width?: number;|NA|api/@ohos.multimedia.media.d.ts|
|删除API|类名：OutputSize；<br>API声明：height?: number;<br>差异内容：height?: number;|NA|api/@ohos.multimedia.media.d.ts|
|删除API|类名：AVImageGenerator；<br>API声明：fetchScaledFrameByTime(timeUs: number, queryMode: AVImageQueryOptions, outputSize?: OutputSize): Promise\<image.PixelMap>;<br>差异内容：fetchScaledFrameByTime(timeUs: number, queryMode: AVImageQueryOptions, outputSize?: OutputSize): Promise\<image.PixelMap>;|NA|api/@ohos.multimedia.media.d.ts|
|删除API|类名：AVErrorCode；<br>API声明：AVERR_SEEK_CONTINUOUS_UNSUPPORTED = 5410002<br>差异内容：AVERR_SEEK_CONTINUOUS_UNSUPPORTED = 5410002|NA|api/@ohos.multimedia.media.d.ts|
|删除API|类名：AVErrorCode；<br>API声明：AVERR_SUPER_RESOLUTION_UNSUPPORTED = 5410003<br>差异内容：AVERR_SUPER_RESOLUTION_UNSUPPORTED = 5410003|NA|api/@ohos.multimedia.media.d.ts|
|删除API|类名：AVErrorCode；<br>API声明：AVERR_SUPER_RESOLUTION_NOT_ENABLED = 5410004<br>差异内容：AVERR_SUPER_RESOLUTION_NOT_ENABLED = 5410004|NA|api/@ohos.multimedia.media.d.ts|
|删除API|类名：AVErrorCode；<br>API声明：AVERR_PARAMETER_OUT_OF_RANGE = 5400108<br>差异内容：AVERR_PARAMETER_OUT_OF_RANGE = 5400108|NA|api/@ohos.multimedia.media.d.ts|
|删除API|类名：media；<br>API声明：type OnSuperResolutionChanged = (enabled: boolean) => void;<br>差异内容：type OnSuperResolutionChanged = (enabled: boolean) => void;|NA|api/@ohos.multimedia.media.d.ts|
|删除API|类名：media；<br>API声明：interface SeiMessage<br>差异内容：interface SeiMessage|NA|api/@ohos.multimedia.media.d.ts|
|删除API|类名：SeiMessage；<br>API声明：payloadType: number;<br>差异内容：payloadType: number;|NA|api/@ohos.multimedia.media.d.ts|
|删除API|类名：SeiMessage；<br>API声明：payload: ArrayBuffer;<br>差异内容：payload: ArrayBuffer;|NA|api/@ohos.multimedia.media.d.ts|
|删除API|类名：media；<br>API声明：type OnSeiMessageHandle = (messages: Array\<SeiMessage>, playbackPosition?: number) => void;<br>差异内容：type OnSeiMessageHandle = (messages: Array\<SeiMessage>, playbackPosition?: number) => void;|NA|api/@ohos.multimedia.media.d.ts|
|删除API|类名：media；<br>API声明：type OnPlaybackRateDone = (rate: number) => void;<br>差异内容：type OnPlaybackRateDone = (rate: number) => void;|NA|api/@ohos.multimedia.media.d.ts|
|删除API|类名：AVPlayer；<br>API声明：setPlaybackRange(startTimeMs: number, endTimeMs: number, mode?: SeekMode): Promise\<void>;<br>差异内容：setPlaybackRange(startTimeMs: number, endTimeMs: number, mode?: SeekMode): Promise\<void>;|NA|api/@ohos.multimedia.media.d.ts|
|删除API|类名：AVPlayer；<br>API声明：isSeekContinuousSupported(): boolean;<br>差异内容：isSeekContinuousSupported(): boolean;|NA|api/@ohos.multimedia.media.d.ts|
|删除API|类名：AVPlayer；<br>API声明：getPlaybackPosition(): number;<br>差异内容：getPlaybackPosition(): number;|NA|api/@ohos.multimedia.media.d.ts|
|删除API|类名：AVPlayer；<br>API声明：setSuperResolution(enabled: boolean): Promise\<void>;<br>差异内容：setSuperResolution(enabled: boolean): Promise\<void>;|NA|api/@ohos.multimedia.media.d.ts|
|删除API|类名：AVPlayer；<br>API声明：setVideoWindowSize(width: number, height: number): Promise\<void>;<br>差异内容：setVideoWindowSize(width: number, height: number): Promise\<void>;|NA|api/@ohos.multimedia.media.d.ts|
|删除API|类名：AVPlayer；<br>API声明：setPlaybackRate(rate: number): void;<br>差异内容：setPlaybackRate(rate: number): void;|NA|api/@ohos.multimedia.media.d.ts|
|删除API|类名：AVPlayer；<br>API声明：on(type: 'playbackRateDone', callback: OnPlaybackRateDone): void;<br>差异内容：on(type: 'playbackRateDone', callback: OnPlaybackRateDone): void;|NA|api/@ohos.multimedia.media.d.ts|
|删除API|类名：AVPlayer；<br>API声明：off(type: 'playbackRateDone', callback?: OnPlaybackRateDone): void;<br>差异内容：off(type: 'playbackRateDone', callback?: OnPlaybackRateDone): void;|NA|api/@ohos.multimedia.media.d.ts|
|删除API|类名：AVPlayer；<br>API声明：on(type: 'seiMessageReceived', payloadTypes: Array\<number>, callback: OnSeiMessageHandle): void;<br>差异内容：on(type: 'seiMessageReceived', payloadTypes: Array\<number>, callback: OnSeiMessageHandle): void;|NA|api/@ohos.multimedia.media.d.ts|
|删除API|类名：AVPlayer；<br>API声明：off(type: 'seiMessageReceived', payloadTypes?: Array\<number>, callback?: OnSeiMessageHandle): void;<br>差异内容：off(type: 'seiMessageReceived', payloadTypes?: Array\<number>, callback?: OnSeiMessageHandle): void;|NA|api/@ohos.multimedia.media.d.ts|
|删除API|类名：AVPlayer；<br>API声明：on(type: 'superResolutionChanged', callback: OnSuperResolutionChanged): void;<br>差异内容：on(type: 'superResolutionChanged', callback: OnSuperResolutionChanged): void;|NA|api/@ohos.multimedia.media.d.ts|
|删除API|类名：AVPlayer；<br>API声明：off(type: 'superResolutionChanged', callback?: OnSuperResolutionChanged): void;<br>差异内容：off(type: 'superResolutionChanged', callback?: OnSuperResolutionChanged): void;|NA|api/@ohos.multimedia.media.d.ts|
|删除API|类名：media；<br>API声明：type SourceOpenCallback = (request: MediaSourceLoadingRequest) => number;<br>差异内容：type SourceOpenCallback = (request: MediaSourceLoadingRequest) => number;|NA|api/@ohos.multimedia.media.d.ts|
|删除API|类名：media；<br>API声明：type SourceReadCallback = (uuid: number, requestedOffset: number, requestedLength: number) => void;<br>差异内容：type SourceReadCallback = (uuid: number, requestedOffset: number, requestedLength: number) => void;|NA|api/@ohos.multimedia.media.d.ts|
|删除API|类名：media；<br>API声明：type SourceCloseCallback = (uuid: number) => void;<br>差异内容：type SourceCloseCallback = (uuid: number) => void;|NA|api/@ohos.multimedia.media.d.ts|
|删除API|类名：media；<br>API声明：interface MediaSourceLoader<br>差异内容：interface MediaSourceLoader|NA|api/@ohos.multimedia.media.d.ts|
|删除API|类名：MediaSourceLoader；<br>API声明：open: SourceOpenCallback;<br>差异内容：open: SourceOpenCallback;|NA|api/@ohos.multimedia.media.d.ts|
|删除API|类名：MediaSourceLoader；<br>API声明：read: SourceReadCallback;<br>差异内容：read: SourceReadCallback;|NA|api/@ohos.multimedia.media.d.ts|
|删除API|类名：MediaSourceLoader；<br>API声明：close: SourceCloseCallback;<br>差异内容：close: SourceCloseCallback;|NA|api/@ohos.multimedia.media.d.ts|
|删除API|类名：media；<br>API声明：enum LoadingRequestError<br>差异内容：enum LoadingRequestError|NA|api/@ohos.multimedia.media.d.ts|
|删除API|类名：LoadingRequestError；<br>API声明：LOADING_ERROR_SUCCESS = 0<br>差异内容：LOADING_ERROR_SUCCESS = 0|NA|api/@ohos.multimedia.media.d.ts|
|删除API|类名：LoadingRequestError；<br>API声明：LOADING_ERROR_NOT_READY = 1<br>差异内容：LOADING_ERROR_NOT_READY = 1|NA|api/@ohos.multimedia.media.d.ts|
|删除API|类名：LoadingRequestError；<br>API声明：LOADING_ERROR_NO_RESOURCE = 2<br>差异内容：LOADING_ERROR_NO_RESOURCE = 2|NA|api/@ohos.multimedia.media.d.ts|
|删除API|类名：LoadingRequestError；<br>API声明：LOADING_ERROR_INVAID_HANDLE = 3<br>差异内容：LOADING_ERROR_INVAID_HANDLE = 3|NA|api/@ohos.multimedia.media.d.ts|
|删除API|类名：LoadingRequestError；<br>API声明：LOADING_ERROR_ACCESS_DENIED = 4<br>差异内容：LOADING_ERROR_ACCESS_DENIED = 4|NA|api/@ohos.multimedia.media.d.ts|
|删除API|类名：LoadingRequestError；<br>API声明：LOADING_ERROR_ACCESS_TIMEOUT = 5<br>差异内容：LOADING_ERROR_ACCESS_TIMEOUT = 5|NA|api/@ohos.multimedia.media.d.ts|
|删除API|类名：LoadingRequestError；<br>API声明：LOADING_ERROR_AUTHORIZE_FAILED = 6<br>差异内容：LOADING_ERROR_AUTHORIZE_FAILED = 6|NA|api/@ohos.multimedia.media.d.ts|
|删除API|类名：media；<br>API声明：interface MediaSourceLoadingRequest<br>差异内容：interface MediaSourceLoadingRequest|NA|api/@ohos.multimedia.media.d.ts|
|删除API|类名：MediaSourceLoadingRequest；<br>API声明：url: string;<br>差异内容：url: string;|NA|api/@ohos.multimedia.media.d.ts|
|删除API|类名：MediaSourceLoadingRequest；<br>API声明：header?: Record\<string, string>;<br>差异内容：header?: Record\<string, string>;|NA|api/@ohos.multimedia.media.d.ts|
|删除API|类名：MediaSourceLoadingRequest；<br>API声明：respondData(uuid: number, offset: number, buffer: ArrayBuffer): number;<br>差异内容：respondData(uuid: number, offset: number, buffer: ArrayBuffer): number;|NA|api/@ohos.multimedia.media.d.ts|
|删除API|类名：MediaSourceLoadingRequest；<br>API声明：respondHeader(uuid: number, header?: Record\<string, string>, redirectUrl?: string): void;<br>差异内容：respondHeader(uuid: number, header?: Record\<string, string>, redirectUrl?: string): void;|NA|api/@ohos.multimedia.media.d.ts|
|删除API|类名：MediaSourceLoadingRequest；<br>API声明：finishLoading(uuid: number, state: LoadingRequestError): void;<br>差异内容：finishLoading(uuid: number, state: LoadingRequestError): void;|NA|api/@ohos.multimedia.media.d.ts|
|删除API|类名：media；<br>API声明：interface MediaStream<br>差异内容：interface MediaStream|NA|api/@ohos.multimedia.media.d.ts|
|删除API|类名：MediaStream；<br>API声明：url: string;<br>差异内容：url: string;|NA|api/@ohos.multimedia.media.d.ts|
|删除API|类名：MediaStream；<br>API声明：width: number;<br>差异内容：width: number;|NA|api/@ohos.multimedia.media.d.ts|
|删除API|类名：MediaStream；<br>API声明：height: number;<br>差异内容：height: number;|NA|api/@ohos.multimedia.media.d.ts|
|删除API|类名：MediaStream；<br>API声明：bitrate: number;<br>差异内容：bitrate: number;|NA|api/@ohos.multimedia.media.d.ts|
|删除API|类名：MediaSource；<br>API声明：setMediaResourceLoaderDelegate(resourceLoader: MediaSourceLoader): void;<br>差异内容：setMediaResourceLoaderDelegate(resourceLoader: MediaSourceLoader): void;|NA|api/@ohos.multimedia.media.d.ts|
|删除API|类名：PlaybackStrategy；<br>API声明：showFirstFrameOnPrepare?: boolean;<br>差异内容：showFirstFrameOnPrepare?: boolean;|NA|api/@ohos.multimedia.media.d.ts|
|删除API|类名：PlaybackStrategy；<br>API声明：preferredBufferDurationForPlaying?: number;<br>差异内容：preferredBufferDurationForPlaying?: number;|NA|api/@ohos.multimedia.media.d.ts|
|删除API|类名：PlaybackStrategy；<br>API声明：enableSuperResolution?: boolean;<br>差异内容：enableSuperResolution?: boolean;|NA|api/@ohos.multimedia.media.d.ts|
|删除API|类名：PlaybackStrategy；<br>API声明：thresholdForAutoQuickPlay?: number;<br>差异内容：thresholdForAutoQuickPlay?: number;|NA|api/@ohos.multimedia.media.d.ts|
|删除API|类名：PlaybackStrategy；<br>API声明：keepDecodingOnMute?: boolean;<br>差异内容：keepDecodingOnMute?: boolean;|NA|api/@ohos.multimedia.media.d.ts|
|删除API|类名：AVRecorder；<br>API声明：setWillMuteWhenInterrupted(muteWhenInterrupted: boolean): Promise\<void>;<br>差异内容：setWillMuteWhenInterrupted(muteWhenInterrupted: boolean): Promise\<void>;|NA|api/@ohos.multimedia.media.d.ts|
|删除API|类名：VideoScaleType；<br>API声明：VIDEO_SCALE_TYPE_SCALED_ASPECT = 2<br>差异内容：VIDEO_SCALE_TYPE_SCALED_ASPECT = 2|NA|api/@ohos.multimedia.media.d.ts|
|删除API|类名：ContainerFormatType；<br>API声明：CFT_AMR = 'amr'<br>差异内容：CFT_AMR = 'amr'|NA|api/@ohos.multimedia.media.d.ts|
|删除API|类名：ContainerFormatType；<br>API声明：CFT_AAC = 'aac'<br>差异内容：CFT_AAC = 'aac'|NA|api/@ohos.multimedia.media.d.ts|
|删除API|类名：MediaType；<br>API声明：MEDIA_TYPE_UNSUPPORTED = -1<br>差异内容：MEDIA_TYPE_UNSUPPORTED = -1|NA|api/@ohos.multimedia.media.d.ts|
|删除API|类名：MediaType；<br>API声明：MEDIA_TYPE_ATTACHMENT = 3<br>差异内容：MEDIA_TYPE_ATTACHMENT = 3|NA|api/@ohos.multimedia.media.d.ts|
|删除API|类名：MediaType；<br>API声明：MEDIA_TYPE_DATA = 4<br>差异内容：MEDIA_TYPE_DATA = 4|NA|api/@ohos.multimedia.media.d.ts|
|删除API|类名：MediaType；<br>API声明：MEDIA_TYPE_TIMED_METADATA = 5<br>差异内容：MEDIA_TYPE_TIMED_METADATA = 5|NA|api/@ohos.multimedia.media.d.ts|
|删除API|类名：MediaType；<br>API声明：MEDIA_TYPE_AUXILIARY = 6<br>差异内容：MEDIA_TYPE_AUXILIARY = 6|NA|api/@ohos.multimedia.media.d.ts|
|删除API|类名：AVRecorderProfile；<br>API声明：enableBFrame?: boolean;<br>差异内容：enableBFrame?: boolean;|NA|api/@ohos.multimedia.media.d.ts|
|删除API|类名：AVRecorderConfig；<br>API声明：maxDuration?: number;<br>差异内容：maxDuration?: number;|NA|api/@ohos.multimedia.media.d.ts|
|删除API|类名：SeekMode；<br>API声明：SEEK_CONTINUOUS = 3<br>差异内容：SEEK_CONTINUOUS = 3|NA|api/@ohos.multimedia.media.d.ts|
|删除API|类名：CodecMimeType；<br>API声明：AUDIO_AMR_NB = 'audio/3gpp'<br>差异内容：AUDIO_AMR_NB = 'audio/3gpp'|NA|api/@ohos.multimedia.media.d.ts|
|删除API|类名：CodecMimeType；<br>API声明：AUDIO_AMR_WB = 'audio/amr-wb'<br>差异内容：AUDIO_AMR_WB = 'audio/amr-wb'|NA|api/@ohos.multimedia.media.d.ts|
|删除API|类名：media；<br>API声明：enum AVScreenCaptureFillMode<br>差异内容：enum AVScreenCaptureFillMode|NA|api/@ohos.multimedia.media.d.ts|
|删除API|类名：AVScreenCaptureFillMode；<br>API声明：PRESERVE_ASPECT_RATIO = 0<br>差异内容：PRESERVE_ASPECT_RATIO = 0|NA|api/@ohos.multimedia.media.d.ts|
|删除API|类名：AVScreenCaptureFillMode；<br>API声明：SCALE_TO_FILL = 1<br>差异内容：SCALE_TO_FILL = 1|NA|api/@ohos.multimedia.media.d.ts|
|删除API|类名：media；<br>API声明：interface AVScreenCaptureStrategy<br>差异内容：interface AVScreenCaptureStrategy|NA|api/@ohos.multimedia.media.d.ts|
|删除API|类名：AVScreenCaptureStrategy；<br>API声明：keepCaptureDuringCall?: boolean;<br>差异内容：keepCaptureDuringCall?: boolean;|NA|api/@ohos.multimedia.media.d.ts|
|删除API|类名：AVScreenCaptureStrategy；<br>API声明：enableBFrame?: boolean;<br>差异内容：enableBFrame?: boolean;|NA|api/@ohos.multimedia.media.d.ts|
|删除API|类名：AVScreenCaptureRecordConfig；<br>API声明：fillMode?: AVScreenCaptureFillMode;<br>差异内容：fillMode?: AVScreenCaptureFillMode;|NA|api/@ohos.multimedia.media.d.ts|
|删除API|类名：AVScreenCaptureRecordConfig；<br>API声明：strategy?: AVScreenCaptureStrategy;<br>差异内容：strategy?: AVScreenCaptureStrategy;|NA|api/@ohos.multimedia.media.d.ts|
|删除API|类名：AVTranscoderConfig；<br>API声明：enableBFrame?: boolean;<br>差异内容：enableBFrame?: boolean;|NA|api/@ohos.multimedia.media.d.ts|
|API从支持元服务到不支持元服务|类名：AVPlayer；<br>API声明：off(type: 'volumeChange', callback?: Callback\<number>): void;<br>差异内容：atomicservice|类名：AVPlayer；<br>API声明：off(type: 'volumeChange', callback?: Callback\<number>): void;<br>差异内容：NA|api/@ohos.multimedia.media.d.ts|
|API从支持元服务到不支持元服务|类名：AVPlayer；<br>API声明：off(type: 'endOfStream', callback?: Callback\<void>): void;<br>差异内容：atomicservice|类名：AVPlayer；<br>API声明：off(type: 'endOfStream', callback?: Callback\<void>): void;<br>差异内容：NA|api/@ohos.multimedia.media.d.ts|
|API从支持元服务到不支持元服务|类名：AVPlayer；<br>API声明：off(type: 'speedDone', callback?: Callback\<number>): void;<br>差异内容：atomicservice|类名：AVPlayer；<br>API声明：off(type: 'speedDone', callback?: Callback\<number>): void;<br>差异内容：NA|api/@ohos.multimedia.media.d.ts|
|API从支持元服务到不支持元服务|类名：AVPlayer；<br>API声明：off(type: 'bitrateDone', callback?: Callback\<number>): void;<br>差异内容：atomicservice|类名：AVPlayer；<br>API声明：off(type: 'bitrateDone', callback?: Callback\<number>): void;<br>差异内容：NA|api/@ohos.multimedia.media.d.ts|
|API从支持元服务到不支持元服务|类名：AVPlayer；<br>API声明：off(type: 'durationUpdate', callback?: Callback\<number>): void;<br>差异内容：atomicservice|类名：AVPlayer；<br>API声明：off(type: 'durationUpdate', callback?: Callback\<number>): void;<br>差异内容：NA|api/@ohos.multimedia.media.d.ts|
|API从支持元服务到不支持元服务|类名：AVPlayer；<br>API声明：off(type: 'startRenderFrame', callback?: Callback\<void>): void;<br>差异内容：atomicservice|类名：AVPlayer；<br>API声明：off(type: 'startRenderFrame', callback?: Callback\<void>): void;<br>差异内容：NA|api/@ohos.multimedia.media.d.ts|
|删除导出符号|类名：global；<br>API声明：export enum ErrorType<br>差异内容：export enum ErrorType|类名：global；<br>API声明：<br>差异内容：NA|api/multimedia/soundPool.d.ts|
|删除导出符号|类名：global；<br>API声明：export interface ErrorInfo<br>差异内容：export interface ErrorInfo|类名：global；<br>API声明：<br>差异内容：NA|api/multimedia/soundPool.d.ts|
