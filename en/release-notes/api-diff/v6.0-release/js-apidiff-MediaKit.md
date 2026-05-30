| Change Type | Old Version | New Version | d.ts File |
| ---- | ------ | ------ | -------- |
|New API |NA|Class name: AVErrorCode;<br>API declaration: AVERR_SEEK_CONTINUOUS_UNSUPPORTED = 5410002<br>DIfferences: AVERR_SEEK_CONTINUOUS_UNSUPPORTED = 5410002|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: AVErrorCode;<br>API declaration: AVERR_SUPER_RESOLUTION_UNSUPPORTED = 5410003<br>DIfferences: AVERR_SUPER_RESOLUTION_UNSUPPORTED = 5410003|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: AVErrorCode;<br>API declaration: AVERR_SUPER_RESOLUTION_NOT_ENABLED = 5410004<br>DIfferences: AVERR_SUPER_RESOLUTION_NOT_ENABLED = 5410004|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: media;<br>API declaration: type OnSuperResolutionChanged = (enabled: boolean) => void;<br>DIfferences: type OnSuperResolutionChanged = (enabled: boolean) => void;|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: media;<br>API declaration: interface SeiMessage<br>DIfferences: interface SeiMessage|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: SeiMessage;<br>API declaration: payloadType: number;<br>DIfferences: payloadType: number;|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: SeiMessage;<br>API declaration: payload: ArrayBuffer;<br>DIfferences: payload: ArrayBuffer;|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: media;<br>API declaration: type OnSeiMessageHandle = (messages: Array\<SeiMessage>, playbackPosition?: number) => void;<br>DIfferences: type OnSeiMessageHandle = (messages: Array\<SeiMessage>, playbackPosition?: number) => void;|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: AVPlayer;<br>API declaration: setPlaybackRange(startTimeMs: number, endTimeMs: number, mode?: SeekMode): Promise\<void>;<br>DIfferences: setPlaybackRange(startTimeMs: number, endTimeMs: number, mode?: SeekMode): Promise\<void>;|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: AVPlayer;<br>API declaration: isSeekContinuousSupported(): boolean;<br>DIfferences: isSeekContinuousSupported(): boolean;|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: AVPlayer;<br>API declaration: getPlaybackPosition(): number;<br>DIfferences: getPlaybackPosition(): number;|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: AVPlayer;<br>API declaration: setSuperResolution(enabled: boolean): Promise\<void>;<br>DIfferences: setSuperResolution(enabled: boolean): Promise\<void>;|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: AVPlayer;<br>API declaration: setVideoWindowSize(width: number, height: number): Promise\<void>;<br>DIfferences: setVideoWindowSize(width: number, height: number): Promise\<void>;|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: AVPlayer;<br>API declaration: on(type: 'seiMessageReceived', payloadTypes: Array\<number>, callback: OnSeiMessageHandle): void;<br>DIfferences: on(type: 'seiMessageReceived', payloadTypes: Array\<number>, callback: OnSeiMessageHandle): void;|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: AVPlayer;<br>API declaration: off(type: 'seiMessageReceived', payloadTypes?: Array\<number>, callback?: OnSeiMessageHandle): void;<br>DIfferences: off(type: 'seiMessageReceived', payloadTypes?: Array\<number>, callback?: OnSeiMessageHandle): void;|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: AVPlayer;<br>API declaration: on(type: 'superResolutionChanged', callback: OnSuperResolutionChanged): void;<br>DIfferences: on(type: 'superResolutionChanged', callback: OnSuperResolutionChanged): void;|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: AVPlayer;<br>API declaration: off(type: 'superResolutionChanged', callback?: OnSuperResolutionChanged): void;<br>DIfferences: off(type: 'superResolutionChanged', callback?: OnSuperResolutionChanged): void;|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: media;<br>API declaration: type SourceOpenCallback = (request: MediaSourceLoadingRequest) => number;<br>DIfferences: type SourceOpenCallback = (request: MediaSourceLoadingRequest) => number;|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: media;<br>API declaration: type SourceReadCallback = (uuid: number, requestedOffset: number, requestedLength: number) => void;<br>DIfferences: type SourceReadCallback = (uuid: number, requestedOffset: number, requestedLength: number) => void;|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: media;<br>API declaration: type SourceCloseCallback = (uuid: number) => void;<br>DIfferences: type SourceCloseCallback = (uuid: number) => void;|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: media;<br>API declaration: interface MediaSourceLoader<br>DIfferences: interface MediaSourceLoader|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: MediaSourceLoader;<br>API declaration: open: SourceOpenCallback;<br>DIfferences: open: SourceOpenCallback;|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: MediaSourceLoader;<br>API declaration: read: SourceReadCallback;<br>DIfferences: read: SourceReadCallback;|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: MediaSourceLoader;<br>API declaration: close: SourceCloseCallback;<br>DIfferences: close: SourceCloseCallback;|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: media;<br>API declaration: enum LoadingRequestError<br>DIfferences: enum LoadingRequestError|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: LoadingRequestError;<br>API declaration: LOADING_ERROR_SUCCESS = 0<br>DIfferences: LOADING_ERROR_SUCCESS = 0|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: LoadingRequestError;<br>API declaration: LOADING_ERROR_NOT_READY = 1<br>DIfferences: LOADING_ERROR_NOT_READY = 1|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: LoadingRequestError;<br>API declaration: LOADING_ERROR_NO_RESOURCE = 2<br>DIfferences: LOADING_ERROR_NO_RESOURCE = 2|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: LoadingRequestError;<br>API declaration: LOADING_ERROR_INVAID_HANDLE = 3<br>DIfferences: LOADING_ERROR_INVAID_HANDLE = 3|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: LoadingRequestError;<br>API declaration: LOADING_ERROR_ACCESS_DENIED = 4<br>DIfferences: LOADING_ERROR_ACCESS_DENIED = 4|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: LoadingRequestError;<br>API declaration: LOADING_ERROR_ACCESS_TIMEOUT = 5<br>DIfferences: LOADING_ERROR_ACCESS_TIMEOUT = 5|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: LoadingRequestError;<br>API declaration: LOADING_ERROR_AUTHORIZE_FAILED = 6<br>DIfferences: LOADING_ERROR_AUTHORIZE_FAILED = 6|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: media;<br>API declaration: interface MediaSourceLoadingRequest<br>DIfferences: interface MediaSourceLoadingRequest|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: MediaSourceLoadingRequest;<br>API declaration: url: string;<br>DIfferences: url: string;|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: MediaSourceLoadingRequest;<br>API declaration: header?: Record\<string, string>;<br>DIfferences: header?: Record\<string, string>;|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: MediaSourceLoadingRequest;<br>API declaration: respondData(uuid: number, offset: number, buffer: ArrayBuffer): number;<br>DIfferences: respondData(uuid: number, offset: number, buffer: ArrayBuffer): number;|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: MediaSourceLoadingRequest;<br>API declaration: respondHeader(uuid: number, header?: Record\<string, string>, redirectUrl?: string): void;<br>DIfferences: respondHeader(uuid: number, header?: Record\<string, string>, redirectUrl?: string): void;|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: MediaSourceLoadingRequest;<br>API declaration: finishLoading(uuid: number, state: LoadingRequestError): void;<br>DIfferences: finishLoading(uuid: number, state: LoadingRequestError): void;|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: MediaSource;<br>API declaration: setMediaResourceLoaderDelegate(resourceLoader: MediaSourceLoader): void;<br>DIfferences: setMediaResourceLoaderDelegate(resourceLoader: MediaSourceLoader): void;|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: PlaybackStrategy;<br>API declaration: showFirstFrameOnPrepare?: boolean;<br>DIfferences: showFirstFrameOnPrepare?: boolean;|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: PlaybackStrategy;<br>API declaration: preferredBufferDurationForPlaying?: number;<br>DIfferences: preferredBufferDurationForPlaying?: number;|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: PlaybackStrategy;<br>API declaration: enableSuperResolution?: boolean;<br>DIfferences: enableSuperResolution?: boolean;|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: PlaybackStrategy;<br>API declaration: thresholdForAutoQuickPlay?: number;<br>DIfferences: thresholdForAutoQuickPlay?: number;|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: ContainerFormatType;<br>API declaration: CFT_AMR = 'amr'<br>DIfferences: CFT_AMR = 'amr'|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: AVRecorderConfig;<br>API declaration: maxDuration?: number;<br>DIfferences: maxDuration?: number;|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: SeekMode;<br>API declaration: SEEK_CONTINUOUS = 3<br>DIfferences: SEEK_CONTINUOUS = 3|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: CodecMimeType;<br>API declaration: AUDIO_AMR_NB = 'audio/3gpp'<br>DIfferences: AUDIO_AMR_NB = 'audio/3gpp'|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: CodecMimeType;<br>API declaration: AUDIO_AMR_WB = 'audio/amr-wb'<br>DIfferences: AUDIO_AMR_WB = 'audio/amr-wb'|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: media;<br>API declaration: enum AVScreenCaptureFillMode<br>DIfferences: enum AVScreenCaptureFillMode|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: AVScreenCaptureFillMode;<br>API declaration: PRESERVE_ASPECT_RATIO = 0<br>DIfferences: PRESERVE_ASPECT_RATIO = 0|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: AVScreenCaptureFillMode;<br>API declaration: SCALE_TO_FILL = 1<br>DIfferences: SCALE_TO_FILL = 1|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: AVScreenCaptureRecordConfig;<br>API declaration: fillMode?: AVScreenCaptureFillMode;<br>DIfferences: fillMode?: AVScreenCaptureFillMode;|api/@ohos.multimedia.media.d.ts|
|New API |NA|Class name: SoundPool;<br>API declaration: on(type: 'playFinishedWithStreamId', callback: Callback\<number>): void;<br>DIfferences: on(type: 'playFinishedWithStreamId', callback: Callback\<number>): void;|api/multimedia/soundPool.d.ts|
|New API |NA|Class name: SoundPool;<br>API declaration: off(type: 'playFinishedWithStreamId'): void;<br>DIfferences: off(type: 'playFinishedWithStreamId'): void;|api/multimedia/soundPool.d.ts|
