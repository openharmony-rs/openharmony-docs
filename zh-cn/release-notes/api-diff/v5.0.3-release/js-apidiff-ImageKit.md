| 操作 | 旧版本 | 新版本 | d.ts文件 |
| ---- | ------ | ------ | -------- |
|API跨平台权限变更|类名：sendableImage；<br>API声明：type ISendable = lang.ISendable;<br>差异内容：NA|类名：sendableImage；<br>API声明：type ISendable = lang.ISendable;<br>差异内容：crossplatform|api/@ohos.multimedia.sendableImage.d.ets|
|syscap变更|类名：sendableImage；<br>API声明：type ISendable = lang.ISendable;<br>差异内容：NA|类名：sendableImage；<br>API声明：type ISendable = lang.ISendable;<br>差异内容：SystemCapability.Multimedia.Image.Core|api/@ohos.multimedia.sendableImage.d.ets|
|删除错误码|类名：AuxiliaryPicture；<br>API声明：writePixelsFromBuffer(data: ArrayBuffer): Promise\<void>;<br>差异内容：7600301,7600302|类名：AuxiliaryPicture；<br>API声明：writePixelsFromBuffer(data: ArrayBuffer): Promise\<void>;<br>差异内容：NA|api/@ohos.multimedia.image.d.ts|
|删除错误码|类名：AuxiliaryPicture；<br>API声明：readPixelsToBuffer(): Promise\<ArrayBuffer>;<br>差异内容：7600301,7600302|类名：AuxiliaryPicture；<br>API声明：readPixelsToBuffer(): Promise\<ArrayBuffer>;<br>差异内容：NA|api/@ohos.multimedia.image.d.ts|
|删除错误码|类名：Metadata；<br>API声明：clone(): Promise\<Metadata>;<br>差异内容：7600301,7600302|类名：Metadata；<br>API声明：clone(): Promise\<Metadata>;<br>差异内容：NA|api/@ohos.multimedia.image.d.ts|
|删除错误码|类名：ImageSource；<br>API声明：createPixelMapList(options?: DecodingOptions): Promise\<Array\<PixelMap>>;<br>差异内容：62980110,62980112,62980113,62980122|类名：ImageSource；<br>API声明：createPixelMapList(options?: DecodingOptions): Promise\<Array\<PixelMap>>;<br>差异内容：NA|api/@ohos.multimedia.image.d.ts|
|删除错误码|类名：ImageSource；<br>API声明：createPixelMapList(callback: AsyncCallback\<Array\<PixelMap>>): void;<br>差异内容：62980110,62980112,62980113,62980122|类名：ImageSource；<br>API声明：createPixelMapList(callback: AsyncCallback\<Array\<PixelMap>>): void;<br>差异内容：NA|api/@ohos.multimedia.image.d.ts|
|删除错误码|类名：ImageSource；<br>API声明：createPixelMapList(options: DecodingOptions, callback: AsyncCallback\<Array\<PixelMap>>): void;<br>差异内容：62980110,62980112,62980113,62980122|类名：ImageSource；<br>API声明：createPixelMapList(options: DecodingOptions, callback: AsyncCallback\<Array\<PixelMap>>): void;<br>差异内容：NA|api/@ohos.multimedia.image.d.ts|
|删除错误码|类名：ImageSource；<br>API声明：getDelayTimeList(): Promise\<Array\<number>>;<br>差异内容：62980112,62980113,62980137|类名：ImageSource；<br>API声明：getDelayTimeList(): Promise\<Array\<number>>;<br>差异内容：NA|api/@ohos.multimedia.image.d.ts|
|删除错误码|类名：ImageSource；<br>API声明：getDelayTimeList(callback: AsyncCallback\<Array\<number>>): void;<br>差异内容：62980112,62980113,62980137|类名：ImageSource；<br>API声明：getDelayTimeList(callback: AsyncCallback\<Array\<number>>): void;<br>差异内容：NA|api/@ohos.multimedia.image.d.ts|
|删除错误码|类名：ImageSource；<br>API声明：getFrameCount(): Promise\<number>;<br>差异内容：62980110|类名：ImageSource；<br>API声明：getFrameCount(): Promise\<number>;<br>差异内容：NA|api/@ohos.multimedia.image.d.ts|
|删除错误码|类名：ImageSource；<br>API声明：getFrameCount(callback: AsyncCallback\<number>): void;<br>差异内容：62980110|类名：ImageSource；<br>API声明：getFrameCount(callback: AsyncCallback\<number>): void;<br>差异内容：NA|api/@ohos.multimedia.image.d.ts|
|删除错误码|类名：ImageSource；<br>API声明：getImageProperty(key: PropertyKey, options?: ImagePropertyOptions): Promise\<string>;<br>差异内容：62980116|类名：ImageSource；<br>API声明：getImageProperty(key: PropertyKey, options?: ImagePropertyOptions): Promise\<string>;<br>差异内容：NA|api/@ohos.multimedia.image.d.ts|
|删除错误码|类名：ImageSource；<br>API声明：modifyImageProperties(records: Record\<PropertyKey, string \| null>): Promise\<void>;<br>差异内容：62980133|类名：ImageSource；<br>API声明：modifyImageProperties(records: Record\<PropertyKey, string \| null>): Promise\<void>;<br>差异内容：NA|api/@ohos.multimedia.image.d.ts|
|函数变更|类名：ImageCreator；<br>API声明：queueImage(interface: Image, callback: AsyncCallback\<void>): void;<br>差异内容：interface: Image, callback: AsyncCallback\<void>|类名：ImageCreator；<br>API声明：queueImage(image: Image, callback: AsyncCallback\<void>): void;<br>差异内容：image: Image, callback: AsyncCallback\<void>|api/@ohos.multimedia.image.d.ts|
|函数变更|类名：ImageCreator；<br>API声明：queueImage(interface: Image): Promise\<void>;<br>差异内容：interface: Image|类名：ImageCreator；<br>API声明：queueImage(image: Image): Promise\<void>;<br>差异内容：image: Image|api/@ohos.multimedia.image.d.ts|
|新增API|NA|类名：global；<br>API声明：declare namespace videoProcessingEngine<br>差异内容：declare namespace videoProcessingEngine|api/@ohos.multimedia.videoProcessingEngine.d.ts|
|新增API|NA|类名：videoProcessingEngine；<br>API声明：enum QualityLevel<br>差异内容：enum QualityLevel|api/@ohos.multimedia.videoProcessingEngine.d.ts|
|新增API|NA|类名：QualityLevel；<br>API声明：NONE = 0<br>差异内容：NONE = 0|api/@ohos.multimedia.videoProcessingEngine.d.ts|
|新增API|NA|类名：QualityLevel；<br>API声明：LOW = 1<br>差异内容：LOW = 1|api/@ohos.multimedia.videoProcessingEngine.d.ts|
|新增API|NA|类名：QualityLevel；<br>API声明：MEDIUM = 2<br>差异内容：MEDIUM = 2|api/@ohos.multimedia.videoProcessingEngine.d.ts|
|新增API|NA|类名：QualityLevel；<br>API声明：HIGH = 3<br>差异内容：HIGH = 3|api/@ohos.multimedia.videoProcessingEngine.d.ts|
|新增API|NA|类名：videoProcessingEngine；<br>API声明：interface ImageProcessor<br>差异内容：interface ImageProcessor|api/@ohos.multimedia.videoProcessingEngine.d.ts|
|新增API|NA|类名：ImageProcessor；<br>API声明：enhanceDetail(sourceImage: image.PixelMap, width: number, height: number, level?: QualityLevel): Promise\<image.PixelMap>;<br>差异内容：enhanceDetail(sourceImage: image.PixelMap, width: number, height: number, level?: QualityLevel): Promise\<image.PixelMap>;|api/@ohos.multimedia.videoProcessingEngine.d.ts|
|新增API|NA|类名：ImageProcessor；<br>API声明：enhanceDetail(sourceImage: image.PixelMap, scale: number, level?: QualityLevel): Promise\<image.PixelMap>;<br>差异内容：enhanceDetail(sourceImage: image.PixelMap, scale: number, level?: QualityLevel): Promise\<image.PixelMap>;|api/@ohos.multimedia.videoProcessingEngine.d.ts|
|新增API|NA|类名：ImageProcessor；<br>API声明：enhanceDetailSync(sourceImage: image.PixelMap, width: number, height: number, level?: QualityLevel): image.PixelMap;<br>差异内容：enhanceDetailSync(sourceImage: image.PixelMap, width: number, height: number, level?: QualityLevel): image.PixelMap;|api/@ohos.multimedia.videoProcessingEngine.d.ts|
|新增API|NA|类名：ImageProcessor；<br>API声明：enhanceDetailSync(sourceImage: image.PixelMap, scale: number, level?: QualityLevel): image.PixelMap;<br>差异内容：enhanceDetailSync(sourceImage: image.PixelMap, scale: number, level?: QualityLevel): image.PixelMap;|api/@ohos.multimedia.videoProcessingEngine.d.ts|
|新增API|NA|类名：videoProcessingEngine；<br>API声明：function initializeEnvironment(): Promise\<void>;<br>差异内容：function initializeEnvironment(): Promise\<void>;|api/@ohos.multimedia.videoProcessingEngine.d.ts|
|新增API|NA|类名：videoProcessingEngine；<br>API声明：function deinitializeEnvironment(): Promise\<void>;<br>差异内容：function deinitializeEnvironment(): Promise\<void>;|api/@ohos.multimedia.videoProcessingEngine.d.ts|
|新增API|NA|类名：videoProcessingEngine；<br>API声明：function create(): ImageProcessor;<br>差异内容：function create(): ImageProcessor;|api/@ohos.multimedia.videoProcessingEngine.d.ts|
|新增API|NA|类名：image；<br>API声明：function createPixelMapFromSurface(surfaceId: string): Promise\<PixelMap>;<br>差异内容：function createPixelMapFromSurface(surfaceId: string): Promise\<PixelMap>;|api/@ohos.multimedia.image.d.ts|
|新增API|NA|类名：image；<br>API声明：function createPixelMapFromSurfaceSync(surfaceId: string): PixelMap;<br>差异内容：function createPixelMapFromSurfaceSync(surfaceId: string): PixelMap;|api/@ohos.multimedia.image.d.ts|
|新增API|NA|类名：PixelMapFormat；<br>API声明：ARGB_8888 = 1<br>差异内容：ARGB_8888 = 1|api/@ohos.multimedia.image.d.ts|
|新增API|NA|类名：PixelMapFormat；<br>API声明：ASTC_4x4 = 102<br>差异内容：ASTC_4x4 = 102|api/@ohos.multimedia.image.d.ts|
|新增API|NA|类名：image；<br>API声明：enum AllocatorType<br>差异内容：enum AllocatorType|api/@ohos.multimedia.image.d.ts|
|新增API|NA|类名：AllocatorType；<br>API声明：AUTO = 0<br>差异内容：AUTO = 0|api/@ohos.multimedia.image.d.ts|
|新增API|NA|类名：AllocatorType；<br>API声明：DMA = 1<br>差异内容：DMA = 1|api/@ohos.multimedia.image.d.ts|
|新增API|NA|类名：AllocatorType；<br>API声明：SHARE_MEMORY = 2<br>差异内容：SHARE_MEMORY = 2|api/@ohos.multimedia.image.d.ts|
|新增API|NA|类名：image；<br>API声明：enum CropAndScaleStrategy<br>差异内容：enum CropAndScaleStrategy|api/@ohos.multimedia.image.d.ts|
|新增API|NA|类名：CropAndScaleStrategy；<br>API声明：SCALE_FIRST = 1<br>差异内容：SCALE_FIRST = 1|api/@ohos.multimedia.image.d.ts|
|新增API|NA|类名：CropAndScaleStrategy；<br>API声明：CROP_FIRST = 2<br>差异内容：CROP_FIRST = 2|api/@ohos.multimedia.image.d.ts|
|新增API|NA|类名：image；<br>API声明：interface PackingOptionsForSequence<br>差异内容：interface PackingOptionsForSequence|api/@ohos.multimedia.image.d.ts|
|新增API|NA|类名：PackingOptionsForSequence；<br>API声明：frameCount: number;<br>差异内容：frameCount: number;|api/@ohos.multimedia.image.d.ts|
|新增API|NA|类名：PackingOptionsForSequence；<br>API声明：delayTimeList: Array\<number>;<br>差异内容：delayTimeList: Array\<number>;|api/@ohos.multimedia.image.d.ts|
|新增API|NA|类名：PackingOptionsForSequence；<br>API声明：disposalTypes?: Array\<number>;<br>差异内容：disposalTypes?: Array\<number>;|api/@ohos.multimedia.image.d.ts|
|新增API|NA|类名：PackingOptionsForSequence；<br>API声明：loopCount?: number;<br>差异内容：loopCount?: number;|api/@ohos.multimedia.image.d.ts|
|新增API|NA|类名：DecodingOptions；<br>API声明：cropAndScaleStrategy?: CropAndScaleStrategy;<br>差异内容：cropAndScaleStrategy?: CropAndScaleStrategy;|api/@ohos.multimedia.image.d.ts|
|新增API|NA|类名：image；<br>API声明：function createPixelMapUsingAllocator(colors: ArrayBuffer, param: InitializationOptions, allocatorType?: AllocatorType): Promise\<PixelMap>;<br>差异内容：function createPixelMapUsingAllocator(colors: ArrayBuffer, param: InitializationOptions, allocatorType?: AllocatorType): Promise\<PixelMap>;|api/@ohos.multimedia.image.d.ts|
|新增API|NA|类名：image；<br>API声明：function createPixelMapUsingAllocatorSync(colors: ArrayBuffer, param: InitializationOptions, allocatorType?: AllocatorType): PixelMap;<br>差异内容：function createPixelMapUsingAllocatorSync(colors: ArrayBuffer, param: InitializationOptions, allocatorType?: AllocatorType): PixelMap;|api/@ohos.multimedia.image.d.ts|
|新增API|NA|类名：image；<br>API声明：function createPixelMapUsingAllocatorSync(param: InitializationOptions, allocatorType?: AllocatorType): PixelMap;<br>差异内容：function createPixelMapUsingAllocatorSync(param: InitializationOptions, allocatorType?: AllocatorType): PixelMap;|api/@ohos.multimedia.image.d.ts|
|新增API|NA|类名：PixelMap；<br>API声明：createScaledPixelMap(x: number, y: number, level?: AntiAliasingLevel): Promise\<PixelMap>;<br>差异内容：createScaledPixelMap(x: number, y: number, level?: AntiAliasingLevel): Promise\<PixelMap>;|api/@ohos.multimedia.image.d.ts|
|新增API|NA|类名：PixelMap；<br>API声明：createScaledPixelMapSync(x: number, y: number, level?: AntiAliasingLevel): PixelMap;<br>差异内容：createScaledPixelMapSync(x: number, y: number, level?: AntiAliasingLevel): PixelMap;|api/@ohos.multimedia.image.d.ts|
|新增API|NA|类名：PixelMap；<br>API声明：cloneSync(): PixelMap;<br>差异内容：cloneSync(): PixelMap;|api/@ohos.multimedia.image.d.ts|
|新增API|NA|类名：PixelMap；<br>API声明：clone(): Promise\<PixelMap>;<br>差异内容：clone(): Promise\<PixelMap>;|api/@ohos.multimedia.image.d.ts|
|新增API|NA|类名：MetadataType；<br>API声明：GIF_METADATA = 5<br>差异内容：GIF_METADATA = 5|api/@ohos.multimedia.image.d.ts|
|新增API|NA|类名：image；<br>API声明：enum GifPropertyKey<br>差异内容：enum GifPropertyKey|api/@ohos.multimedia.image.d.ts|
|新增API|NA|类名：GifPropertyKey；<br>API声明：GIF_DELAY_TIME = 'GifDelayTime'<br>差异内容：GIF_DELAY_TIME = 'GifDelayTime'|api/@ohos.multimedia.image.d.ts|
|新增API|NA|类名：GifPropertyKey；<br>API声明：GIF_DISPOSAL_TYPE = 'GifDisposalType'<br>差异内容：GIF_DISPOSAL_TYPE = 'GifDisposalType'|api/@ohos.multimedia.image.d.ts|
|新增API|NA|类名：ImageSource；<br>API声明：createPixelMapUsingAllocator(options?: DecodingOptions, allocatorType?: AllocatorType): Promise\<PixelMap>;<br>差异内容：createPixelMapUsingAllocator(options?: DecodingOptions, allocatorType?: AllocatorType): Promise\<PixelMap>;|api/@ohos.multimedia.image.d.ts|
|新增API|NA|类名：ImageSource；<br>API声明：createPixelMapUsingAllocatorSync(options?: DecodingOptions, allocatorType?: AllocatorType): PixelMap;<br>差异内容：createPixelMapUsingAllocatorSync(options?: DecodingOptions, allocatorType?: AllocatorType): PixelMap;|api/@ohos.multimedia.image.d.ts|
|新增API|NA|类名：ImageSource；<br>API声明：getImagePropertySync(key: PropertyKey): string;<br>差异内容：getImagePropertySync(key: PropertyKey): string;|api/@ohos.multimedia.image.d.ts|
|新增API|NA|类名：ImageSource；<br>API声明：createPictureAtIndex(index: number): Promise\<Picture>;<br>差异内容：createPictureAtIndex(index: number): Promise\<Picture>;|api/@ohos.multimedia.image.d.ts|
|新增API|NA|类名：ImagePacker；<br>API声明：packToDataFromPixelmapSequence(pixelmapSequence: Array\<PixelMap>, options: PackingOptionsForSequence): Promise\<ArrayBuffer>;<br>差异内容：packToDataFromPixelmapSequence(pixelmapSequence: Array\<PixelMap>, options: PackingOptionsForSequence): Promise\<ArrayBuffer>;|api/@ohos.multimedia.image.d.ts|
|新增API|NA|类名：ImagePacker；<br>API声明：packToFileFromPixelmapSequence(pixelmapSequence: Array\<PixelMap>, fd: number, options: PackingOptionsForSequence): Promise\<void>;<br>差异内容：packToFileFromPixelmapSequence(pixelmapSequence: Array\<PixelMap>, fd: number, options: PackingOptionsForSequence): Promise\<void>;|api/@ohos.multimedia.image.d.ts|
|新增API|NA|类名：image；<br>API声明：function getImageSourceSupportedFormats(): string[];<br>差异内容：function getImageSourceSupportedFormats(): string[];|api/@ohos.multimedia.image.d.ts|
|新增API|NA|类名：image；<br>API声明：function getImagePackerSupportedFormats(): string[];<br>差异内容：function getImagePackerSupportedFormats(): string[];|api/@ohos.multimedia.image.d.ts|
|起始版本有变化|类名：sendableImage；<br>API声明：type ISendable = lang.ISendable;<br>差异内容：NA|类名：sendableImage；<br>API声明：type ISendable = lang.ISendable;<br>差异内容：12|api/@ohos.multimedia.sendableImage.d.ets|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\@ohos.multimedia.videoProcessingEngine.d.ts<br>差异内容：ImageKit|api/@ohos.multimedia.videoProcessingEngine.d.ts|
