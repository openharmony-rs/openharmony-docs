| 操作 | 旧版本 | 新版本 | d.ts文件 |
| ---- | ------ | ------ | -------- |
|新增错误码|类名：AuxiliaryPicture；<br>API声明：writePixelsFromBuffer(data: ArrayBuffer): Promise\<void>;<br>差异内容：NA|类名：AuxiliaryPicture；<br>API声明：writePixelsFromBuffer(data: ArrayBuffer): Promise\<void>;<br>差异内容：7600301,7600302|api/@ohos.multimedia.image.d.ts|
|新增错误码|类名：AuxiliaryPicture；<br>API声明：readPixelsToBuffer(): Promise\<ArrayBuffer>;<br>差异内容：NA|类名：AuxiliaryPicture；<br>API声明：readPixelsToBuffer(): Promise\<ArrayBuffer>;<br>差异内容：7600301,7600302|api/@ohos.multimedia.image.d.ts|
|新增错误码|类名：Metadata；<br>API声明：clone(): Promise\<Metadata>;<br>差异内容：NA|类名：Metadata；<br>API声明：clone(): Promise\<Metadata>;<br>差异内容：7600301,7600302|api/@ohos.multimedia.image.d.ts|
|新增错误码|类名：ImageSource；<br>API声明：createPixelMapList(options?: DecodingOptions): Promise\<Array\<PixelMap>>;<br>差异内容：NA|类名：ImageSource；<br>API声明：createPixelMapList(options?: DecodingOptions): Promise\<Array\<PixelMap>>;<br>差异内容：62980110,62980112,62980113,62980122|api/@ohos.multimedia.image.d.ts|
|新增错误码|类名：ImageSource；<br>API声明：createPixelMapList(callback: AsyncCallback\<Array\<PixelMap>>): void;<br>差异内容：NA|类名：ImageSource；<br>API声明：createPixelMapList(callback: AsyncCallback\<Array\<PixelMap>>): void;<br>差异内容：62980110,62980112,62980113,62980122|api/@ohos.multimedia.image.d.ts|
|新增错误码|类名：ImageSource；<br>API声明：createPixelMapList(options: DecodingOptions, callback: AsyncCallback\<Array\<PixelMap>>): void;<br>差异内容：NA|类名：ImageSource；<br>API声明：createPixelMapList(options: DecodingOptions, callback: AsyncCallback\<Array\<PixelMap>>): void;<br>差异内容：62980110,62980112,62980113,62980122|api/@ohos.multimedia.image.d.ts|
|新增错误码|类名：ImageSource；<br>API声明：getDelayTimeList(): Promise\<Array\<number>>;<br>差异内容：NA|类名：ImageSource；<br>API声明：getDelayTimeList(): Promise\<Array\<number>>;<br>差异内容：62980112,62980113,62980137|api/@ohos.multimedia.image.d.ts|
|新增错误码|类名：ImageSource；<br>API声明：getDelayTimeList(callback: AsyncCallback\<Array\<number>>): void;<br>差异内容：NA|类名：ImageSource；<br>API声明：getDelayTimeList(callback: AsyncCallback\<Array\<number>>): void;<br>差异内容：62980112,62980113,62980137|api/@ohos.multimedia.image.d.ts|
|新增错误码|类名：ImageSource；<br>API声明：getFrameCount(): Promise\<number>;<br>差异内容：NA|类名：ImageSource；<br>API声明：getFrameCount(): Promise\<number>;<br>差异内容：62980110|api/@ohos.multimedia.image.d.ts|
|新增错误码|类名：ImageSource；<br>API声明：getFrameCount(callback: AsyncCallback\<number>): void;<br>差异内容：NA|类名：ImageSource；<br>API声明：getFrameCount(callback: AsyncCallback\<number>): void;<br>差异内容：62980110|api/@ohos.multimedia.image.d.ts|
|新增错误码|类名：ImageSource；<br>API声明：getImageProperty(key: PropertyKey, options?: ImagePropertyOptions): Promise\<string>;<br>差异内容：NA|类名：ImageSource；<br>API声明：getImageProperty(key: PropertyKey, options?: ImagePropertyOptions): Promise\<string>;<br>差异内容：62980116|api/@ohos.multimedia.image.d.ts|
|新增错误码|类名：ImageSource；<br>API声明：modifyImageProperties(records: Record\<PropertyKey, string \| null>): Promise\<void>;<br>差异内容：NA|类名：ImageSource；<br>API声明：modifyImageProperties(records: Record\<PropertyKey, string \| null>): Promise\<void>;<br>差异内容：62980133|api/@ohos.multimedia.image.d.ts|
|函数变更|类名：ImageCreator；<br>API声明：queueImage(image: Image, callback: AsyncCallback\<void>): void;<br>差异内容：image: Image, callback: AsyncCallback\<void>|类名：ImageCreator；<br>API声明：queueImage(interface: Image, callback: AsyncCallback\<void>): void;<br>差异内容：interface: Image, callback: AsyncCallback\<void>|api/@ohos.multimedia.image.d.ts|
|函数变更|类名：ImageCreator；<br>API声明：queueImage(image: Image): Promise\<void>;<br>差异内容：image: Image|类名：ImageCreator；<br>API声明：queueImage(interface: Image): Promise\<void>;<br>差异内容：interface: Image|api/@ohos.multimedia.image.d.ts|
|删除API|类名：global；<br>API声明：declare namespace videoProcessingEngine<br>差异内容：declare namespace videoProcessingEngine|NA|api/@ohos.multimedia.videoProcessingEngine.d.ts|
|删除API|类名：videoProcessingEngine；<br>API声明：enum QualityLevel<br>差异内容：enum QualityLevel|NA|api/@ohos.multimedia.videoProcessingEngine.d.ts|
|删除API|类名：QualityLevel；<br>API声明：NONE = 0<br>差异内容：NONE = 0|NA|api/@ohos.multimedia.videoProcessingEngine.d.ts|
|删除API|类名：QualityLevel；<br>API声明：LOW = 1<br>差异内容：LOW = 1|NA|api/@ohos.multimedia.videoProcessingEngine.d.ts|
|删除API|类名：QualityLevel；<br>API声明：MEDIUM = 2<br>差异内容：MEDIUM = 2|NA|api/@ohos.multimedia.videoProcessingEngine.d.ts|
|删除API|类名：QualityLevel；<br>API声明：HIGH = 3<br>差异内容：HIGH = 3|NA|api/@ohos.multimedia.videoProcessingEngine.d.ts|
|删除API|类名：videoProcessingEngine；<br>API声明：interface ImageProcessor<br>差异内容：interface ImageProcessor|NA|api/@ohos.multimedia.videoProcessingEngine.d.ts|
|删除API|类名：ImageProcessor；<br>API声明：enhanceDetail(sourceImage: image.PixelMap, width: number, height: number, level?: QualityLevel): Promise\<image.PixelMap>;<br>差异内容：enhanceDetail(sourceImage: image.PixelMap, width: number, height: number, level?: QualityLevel): Promise\<image.PixelMap>;|NA|api/@ohos.multimedia.videoProcessingEngine.d.ts|
|删除API|类名：ImageProcessor；<br>API声明：enhanceDetail(sourceImage: image.PixelMap, scale: number, level?: QualityLevel): Promise\<image.PixelMap>;<br>差异内容：enhanceDetail(sourceImage: image.PixelMap, scale: number, level?: QualityLevel): Promise\<image.PixelMap>;|NA|api/@ohos.multimedia.videoProcessingEngine.d.ts|
|删除API|类名：ImageProcessor；<br>API声明：enhanceDetailSync(sourceImage: image.PixelMap, width: number, height: number, level?: QualityLevel): image.PixelMap;<br>差异内容：enhanceDetailSync(sourceImage: image.PixelMap, width: number, height: number, level?: QualityLevel): image.PixelMap;|NA|api/@ohos.multimedia.videoProcessingEngine.d.ts|
|删除API|类名：ImageProcessor；<br>API声明：enhanceDetailSync(sourceImage: image.PixelMap, scale: number, level?: QualityLevel): image.PixelMap;<br>差异内容：enhanceDetailSync(sourceImage: image.PixelMap, scale: number, level?: QualityLevel): image.PixelMap;|NA|api/@ohos.multimedia.videoProcessingEngine.d.ts|
|删除API|类名：videoProcessingEngine；<br>API声明：function initializeEnvironment(): Promise\<void>;<br>差异内容：function initializeEnvironment(): Promise\<void>;|NA|api/@ohos.multimedia.videoProcessingEngine.d.ts|
|删除API|类名：videoProcessingEngine；<br>API声明：function deinitializeEnvironment(): Promise\<void>;<br>差异内容：function deinitializeEnvironment(): Promise\<void>;|NA|api/@ohos.multimedia.videoProcessingEngine.d.ts|
|删除API|类名：videoProcessingEngine；<br>API声明：function create(): ImageProcessor;<br>差异内容：function create(): ImageProcessor;|NA|api/@ohos.multimedia.videoProcessingEngine.d.ts|
|删除API|类名：PixelMapFormat；<br>API声明：ARGB_8888 = 1<br>差异内容：ARGB_8888 = 1|NA|api/@ohos.multimedia.image.d.ts|
|删除API|类名：PixelMapFormat；<br>API声明：ASTC_4x4 = 102<br>差异内容：ASTC_4x4 = 102|NA|api/@ohos.multimedia.image.d.ts|
|删除API|类名：image；<br>API声明：enum CropAndScaleStrategy<br>差异内容：enum CropAndScaleStrategy|NA|api/@ohos.multimedia.image.d.ts|
|删除API|类名：CropAndScaleStrategy；<br>API声明：SCALE_FIRST = 1<br>差异内容：SCALE_FIRST = 1|NA|api/@ohos.multimedia.image.d.ts|
|删除API|类名：CropAndScaleStrategy；<br>API声明：CROP_FIRST = 2<br>差异内容：CROP_FIRST = 2|NA|api/@ohos.multimedia.image.d.ts|
|删除API|类名：image；<br>API声明：interface PackingOptionsForSequence<br>差异内容：interface PackingOptionsForSequence|NA|api/@ohos.multimedia.image.d.ts|
|删除API|类名：PackingOptionsForSequence；<br>API声明：frameCount: number;<br>差异内容：frameCount: number;|NA|api/@ohos.multimedia.image.d.ts|
|删除API|类名：PackingOptionsForSequence；<br>API声明：delayTimeList: Array\<number>;<br>差异内容：delayTimeList: Array\<number>;|NA|api/@ohos.multimedia.image.d.ts|
|删除API|类名：PackingOptionsForSequence；<br>API声明：disposalTypes?: Array\<number>;<br>差异内容：disposalTypes?: Array\<number>;|NA|api/@ohos.multimedia.image.d.ts|
|删除API|类名：PackingOptionsForSequence；<br>API声明：loopCount?: number;<br>差异内容：loopCount?: number;|NA|api/@ohos.multimedia.image.d.ts|
|删除API|类名：DecodingOptions；<br>API声明：cropAndScaleStrategy?: CropAndScaleStrategy;<br>差异内容：cropAndScaleStrategy?: CropAndScaleStrategy;|NA|api/@ohos.multimedia.image.d.ts|
|删除API|类名：image；<br>API声明：function createPixelMapUsingAllocator(colors: ArrayBuffer, param: InitializationOptions, allocatorType?: AllocatorType): Promise\<PixelMap>;<br>差异内容：function createPixelMapUsingAllocator(colors: ArrayBuffer, param: InitializationOptions, allocatorType?: AllocatorType): Promise\<PixelMap>;|NA|api/@ohos.multimedia.image.d.ts|
|删除API|类名：image；<br>API声明：function createPixelMapUsingAllocatorSync(colors: ArrayBuffer, param: InitializationOptions, allocatorType?: AllocatorType): PixelMap;<br>差异内容：function createPixelMapUsingAllocatorSync(colors: ArrayBuffer, param: InitializationOptions, allocatorType?: AllocatorType): PixelMap;|NA|api/@ohos.multimedia.image.d.ts|
|删除API|类名：image；<br>API声明：function createPixelMapUsingAllocatorSync(param: InitializationOptions, allocatorType?: AllocatorType): PixelMap;<br>差异内容：function createPixelMapUsingAllocatorSync(param: InitializationOptions, allocatorType?: AllocatorType): PixelMap;|NA|api/@ohos.multimedia.image.d.ts|
|删除API|类名：PixelMap；<br>API声明：createScaledPixelMap(x: number, y: number, level?: AntiAliasingLevel): Promise\<PixelMap>;<br>差异内容：createScaledPixelMap(x: number, y: number, level?: AntiAliasingLevel): Promise\<PixelMap>;|NA|api/@ohos.multimedia.image.d.ts|
|删除API|类名：PixelMap；<br>API声明：createScaledPixelMapSync(x: number, y: number, level?: AntiAliasingLevel): PixelMap;<br>差异内容：createScaledPixelMapSync(x: number, y: number, level?: AntiAliasingLevel): PixelMap;|NA|api/@ohos.multimedia.image.d.ts|
|删除API|类名：PixelMap；<br>API声明：cloneSync(): PixelMap;<br>差异内容：cloneSync(): PixelMap;|NA|api/@ohos.multimedia.image.d.ts|
|删除API|类名：PixelMap；<br>API声明：clone(): Promise\<PixelMap>;<br>差异内容：clone(): Promise\<PixelMap>;|NA|api/@ohos.multimedia.image.d.ts|
|删除API|类名：MetadataType；<br>API声明：GIF_METADATA = 5<br>差异内容：GIF_METADATA = 5|NA|api/@ohos.multimedia.image.d.ts|
|删除API|类名：image；<br>API声明：enum GifPropertyKey<br>差异内容：enum GifPropertyKey|NA|api/@ohos.multimedia.image.d.ts|
|删除API|类名：GifPropertyKey；<br>API声明：GIF_DELAY_TIME = 'GifDelayTime'<br>差异内容：GIF_DELAY_TIME = 'GifDelayTime'|NA|api/@ohos.multimedia.image.d.ts|
|删除API|类名：GifPropertyKey；<br>API声明：GIF_DISPOSAL_TYPE = 'GifDisposalType'<br>差异内容：GIF_DISPOSAL_TYPE = 'GifDisposalType'|NA|api/@ohos.multimedia.image.d.ts|
|删除API|类名：ImageSource；<br>API声明：getImagePropertySync(key: PropertyKey): string;<br>差异内容：getImagePropertySync(key: PropertyKey): string;|NA|api/@ohos.multimedia.image.d.ts|
|删除API|类名：ImageSource；<br>API声明：createPictureAtIndex(index: number): Promise\<Picture>;<br>差异内容：createPictureAtIndex(index: number): Promise\<Picture>;|NA|api/@ohos.multimedia.image.d.ts|
|删除API|类名：ImagePacker；<br>API声明：packToDataFromPixelmapSequence(pixelmapSequence: Array\<PixelMap>, options: PackingOptionsForSequence): Promise\<ArrayBuffer>;<br>差异内容：packToDataFromPixelmapSequence(pixelmapSequence: Array\<PixelMap>, options: PackingOptionsForSequence): Promise\<ArrayBuffer>;|NA|api/@ohos.multimedia.image.d.ts|
|删除API|类名：ImagePacker；<br>API声明：packToFileFromPixelmapSequence(pixelmapSequence: Array\<PixelMap>, fd: number, options: PackingOptionsForSequence): Promise\<void>;<br>差异内容：packToFileFromPixelmapSequence(pixelmapSequence: Array\<PixelMap>, fd: number, options: PackingOptionsForSequence): Promise\<void>;|NA|api/@ohos.multimedia.image.d.ts|
|删除API|类名：image；<br>API声明：function getImageSourceSupportedFormats(): string[];<br>差异内容：function getImageSourceSupportedFormats(): string[];|NA|api/@ohos.multimedia.image.d.ts|
|删除API|类名：image；<br>API声明：function getImagePackerSupportedFormats(): string[];<br>差异内容：function getImagePackerSupportedFormats(): string[];|NA|api/@ohos.multimedia.image.d.ts|
|删除kit|类名：global；<br>API声明：api\@ohos.multimedia.videoProcessingEngine.d.ts<br>差异内容：ImageKit|类名：global；<br>API声明：<br>差异内容：NA|api/@ohos.multimedia.videoProcessingEngine.d.ts|
