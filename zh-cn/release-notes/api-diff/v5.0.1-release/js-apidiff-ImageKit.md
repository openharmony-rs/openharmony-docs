| 操作 | 旧版本 | 新版本 | d.ts文件 |
| ---- | ------ | ------ | -------- |
|API废弃版本变更|类名：ImagePacker；<br>API声明：packing(source: ImageSource, option: PackingOption, callback: AsyncCallback\<ArrayBuffer>): void;<br>差异内容：NA|类名：ImagePacker；<br>API声明：packing(source: ImageSource, option: PackingOption, callback: AsyncCallback\<ArrayBuffer>): void;<br>差异内容：13|api/@ohos.multimedia.image.d.ts|
|API废弃版本变更|类名：ImagePacker；<br>API声明：packing(source: ImageSource, option: PackingOption): Promise\<ArrayBuffer>;<br>差异内容：NA|类名：ImagePacker；<br>API声明：packing(source: ImageSource, option: PackingOption): Promise\<ArrayBuffer>;<br>差异内容：13|api/@ohos.multimedia.image.d.ts|
|API废弃版本变更|类名：ImagePacker；<br>API声明：packing(source: PixelMap, option: PackingOption, callback: AsyncCallback\<ArrayBuffer>): void;<br>差异内容：NA|类名：ImagePacker；<br>API声明：packing(source: PixelMap, option: PackingOption, callback: AsyncCallback\<ArrayBuffer>): void;<br>差异内容：13|api/@ohos.multimedia.image.d.ts|
|API废弃版本变更|类名：ImagePacker；<br>API声明：packing(source: PixelMap, option: PackingOption): Promise\<ArrayBuffer>;<br>差异内容：NA|类名：ImagePacker；<br>API声明：packing(source: PixelMap, option: PackingOption): Promise\<ArrayBuffer>;<br>差异内容：13|api/@ohos.multimedia.image.d.ts|
|新增错误码|类名：ImagePacker；<br>API声明：packToFile(source: ImageSource, fd: number, options: PackingOption, callback: AsyncCallback\<void>): void;<br>差异内容：NA|类名：ImagePacker；<br>API声明：packToFile(source: ImageSource, fd: number, options: PackingOption, callback: AsyncCallback\<void>): void;<br>差异内容：62980096,62980101,62980106,62980113,62980115,62980119,62980120,62980172,62980252|api/@ohos.multimedia.image.d.ts|
|新增错误码|类名：ImagePacker；<br>API声明：packToFile(source: ImageSource, fd: number, options: PackingOption): Promise\<void>;<br>差异内容：NA|类名：ImagePacker；<br>API声明：packToFile(source: ImageSource, fd: number, options: PackingOption): Promise\<void>;<br>差异内容：62980096,62980101,62980106,62980113,62980115,62980119,62980120,62980172,62980252|api/@ohos.multimedia.image.d.ts|
|新增错误码|类名：ImagePacker；<br>API声明：packToFile(source: PixelMap, fd: number, options: PackingOption, callback: AsyncCallback\<void>): void;<br>差异内容：NA|类名：ImagePacker；<br>API声明：packToFile(source: PixelMap, fd: number, options: PackingOption, callback: AsyncCallback\<void>): void;<br>差异内容：62980096,62980101,62980106,62980113,62980115,62980119,62980120,62980172,62980252|api/@ohos.multimedia.image.d.ts|
|新增错误码|类名：ImagePacker；<br>API声明：packToFile(source: PixelMap, fd: number, options: PackingOption): Promise\<void>;<br>差异内容：NA|类名：ImagePacker；<br>API声明：packToFile(source: PixelMap, fd: number, options: PackingOption): Promise\<void>;<br>差异内容：62980096,62980101,62980106,62980113,62980115,62980119,62980120,62980172,62980252|api/@ohos.multimedia.image.d.ts|
|新增API|NA|类名：PixelMap；<br>API声明：setMemoryNameSync(name: string): void;<br>差异内容：setMemoryNameSync(name: string): void;|api/@ohos.multimedia.image.d.ts|
|新增API|NA|类名：image；<br>API声明：interface Picture<br>差异内容：interface Picture|api/@ohos.multimedia.image.d.ts|
|新增API|NA|类名：Picture；<br>API声明：getMainPixelmap(): PixelMap;<br>差异内容：getMainPixelmap(): PixelMap;|api/@ohos.multimedia.image.d.ts|
|新增API|NA|类名：Picture；<br>API声明：getHdrComposedPixelmap(): Promise\<PixelMap>;<br>差异内容：getHdrComposedPixelmap(): Promise\<PixelMap>;|api/@ohos.multimedia.image.d.ts|
|新增API|NA|类名：Picture；<br>API声明：getGainmapPixelmap(): PixelMap \| null;<br>差异内容：getGainmapPixelmap(): PixelMap \| null;|api/@ohos.multimedia.image.d.ts|
|新增API|NA|类名：Picture；<br>API声明：setAuxiliaryPicture(type: AuxiliaryPictureType, auxiliaryPicture: AuxiliaryPicture): void;<br>差异内容：setAuxiliaryPicture(type: AuxiliaryPictureType, auxiliaryPicture: AuxiliaryPicture): void;|api/@ohos.multimedia.image.d.ts|
|新增API|NA|类名：Picture；<br>API声明：getAuxiliaryPicture(type: AuxiliaryPictureType): AuxiliaryPicture \| null;<br>差异内容：getAuxiliaryPicture(type: AuxiliaryPictureType): AuxiliaryPicture \| null;|api/@ohos.multimedia.image.d.ts|
|新增API|NA|类名：Picture；<br>API声明：setMetadata(metadataType: MetadataType, metadata: Metadata): Promise\<void>;<br>差异内容：setMetadata(metadataType: MetadataType, metadata: Metadata): Promise\<void>;|api/@ohos.multimedia.image.d.ts|
|新增API|NA|类名：Picture；<br>API声明：getMetadata(metadataType: MetadataType): Promise\<Metadata>;<br>差异内容：getMetadata(metadataType: MetadataType): Promise\<Metadata>;|api/@ohos.multimedia.image.d.ts|
|新增API|NA|类名：Picture；<br>API声明：marshalling(sequence: rpc.MessageSequence): void;<br>差异内容：marshalling(sequence: rpc.MessageSequence): void;|api/@ohos.multimedia.image.d.ts|
|新增API|NA|类名：Picture；<br>API声明：release(): void;<br>差异内容：release(): void;|api/@ohos.multimedia.image.d.ts|
|新增API|NA|类名：image；<br>API声明：function createPicture(mainPixelmap: PixelMap): Picture;<br>差异内容：function createPicture(mainPixelmap: PixelMap): Picture;|api/@ohos.multimedia.image.d.ts|
|新增API|NA|类名：image；<br>API声明：function createPictureFromParcel(sequence: rpc.MessageSequence): Picture;<br>差异内容：function createPictureFromParcel(sequence: rpc.MessageSequence): Picture;|api/@ohos.multimedia.image.d.ts|
|新增API|NA|类名：image；<br>API声明：function createAuxiliaryPicture(buffer: ArrayBuffer, size: Size, type: AuxiliaryPictureType): AuxiliaryPicture;<br>差异内容：function createAuxiliaryPicture(buffer: ArrayBuffer, size: Size, type: AuxiliaryPictureType): AuxiliaryPicture;|api/@ohos.multimedia.image.d.ts|
|新增API|NA|类名：image；<br>API声明：interface AuxiliaryPicture<br>差异内容：interface AuxiliaryPicture|api/@ohos.multimedia.image.d.ts|
|新增API|NA|类名：AuxiliaryPicture；<br>API声明：writePixelsFromBuffer(data: ArrayBuffer): Promise\<void>;<br>差异内容：writePixelsFromBuffer(data: ArrayBuffer): Promise\<void>;|api/@ohos.multimedia.image.d.ts|
|新增API|NA|类名：AuxiliaryPicture；<br>API声明：readPixelsToBuffer(): Promise\<ArrayBuffer>;<br>差异内容：readPixelsToBuffer(): Promise\<ArrayBuffer>;|api/@ohos.multimedia.image.d.ts|
|新增API|NA|类名：AuxiliaryPicture；<br>API声明：getType(): AuxiliaryPictureType;<br>差异内容：getType(): AuxiliaryPictureType;|api/@ohos.multimedia.image.d.ts|
|新增API|NA|类名：AuxiliaryPicture；<br>API声明：setMetadata(metadataType: MetadataType, metadata: Metadata): Promise\<void>;<br>差异内容：setMetadata(metadataType: MetadataType, metadata: Metadata): Promise\<void>;|api/@ohos.multimedia.image.d.ts|
|新增API|NA|类名：AuxiliaryPicture；<br>API声明：getMetadata(metadataType: MetadataType): Promise\<Metadata>;<br>差异内容：getMetadata(metadataType: MetadataType): Promise\<Metadata>;|api/@ohos.multimedia.image.d.ts|
|新增API|NA|类名：AuxiliaryPicture；<br>API声明：getAuxiliaryPictureInfo(): AuxiliaryPictureInfo;<br>差异内容：getAuxiliaryPictureInfo(): AuxiliaryPictureInfo;|api/@ohos.multimedia.image.d.ts|
|新增API|NA|类名：AuxiliaryPicture；<br>API声明：setAuxiliaryPictureInfo(info: AuxiliaryPictureInfo): void;<br>差异内容：setAuxiliaryPictureInfo(info: AuxiliaryPictureInfo): void;|api/@ohos.multimedia.image.d.ts|
|新增API|NA|类名：AuxiliaryPicture；<br>API声明：release(): void;<br>差异内容：release(): void;|api/@ohos.multimedia.image.d.ts|
|新增API|NA|类名：image；<br>API声明：enum AuxiliaryPictureType<br>差异内容：enum AuxiliaryPictureType|api/@ohos.multimedia.image.d.ts|
|新增API|NA|类名：AuxiliaryPictureType；<br>API声明：GAINMAP = 1<br>差异内容：GAINMAP = 1|api/@ohos.multimedia.image.d.ts|
|新增API|NA|类名：AuxiliaryPictureType；<br>API声明：DEPTH_MAP = 2<br>差异内容：DEPTH_MAP = 2|api/@ohos.multimedia.image.d.ts|
|新增API|NA|类名：AuxiliaryPictureType；<br>API声明：UNREFOCUS_MAP = 3<br>差异内容：UNREFOCUS_MAP = 3|api/@ohos.multimedia.image.d.ts|
|新增API|NA|类名：AuxiliaryPictureType；<br>API声明：LINEAR_MAP = 4<br>差异内容：LINEAR_MAP = 4|api/@ohos.multimedia.image.d.ts|
|新增API|NA|类名：AuxiliaryPictureType；<br>API声明：FRAGMENT_MAP = 5<br>差异内容：FRAGMENT_MAP = 5|api/@ohos.multimedia.image.d.ts|
|新增API|NA|类名：image；<br>API声明：enum MetadataType<br>差异内容：enum MetadataType|api/@ohos.multimedia.image.d.ts|
|新增API|NA|类名：MetadataType；<br>API声明：EXIF_METADATA = 1<br>差异内容：EXIF_METADATA = 1|api/@ohos.multimedia.image.d.ts|
|新增API|NA|类名：MetadataType；<br>API声明：FRAGMENT_METADATA = 2<br>差异内容：FRAGMENT_METADATA = 2|api/@ohos.multimedia.image.d.ts|
|新增API|NA|类名：image；<br>API声明：interface Metadata<br>差异内容：interface Metadata|api/@ohos.multimedia.image.d.ts|
|新增API|NA|类名：Metadata；<br>API声明：getProperties(key: Array\<string>): Promise\<Record\<string, string \| null>>;<br>差异内容：getProperties(key: Array\<string>): Promise\<Record\<string, string \| null>>;|api/@ohos.multimedia.image.d.ts|
|新增API|NA|类名：Metadata；<br>API声明：setProperties(records: Record\<string, string \| null>): Promise\<void>;<br>差异内容：setProperties(records: Record\<string, string \| null>): Promise\<void>;|api/@ohos.multimedia.image.d.ts|
|新增API|NA|类名：Metadata；<br>API声明：getAllProperties(): Promise\<Record\<string, string \| null>>;<br>差异内容：getAllProperties(): Promise\<Record\<string, string \| null>>;|api/@ohos.multimedia.image.d.ts|
|新增API|NA|类名：Metadata；<br>API声明：clone(): Promise\<Metadata>;<br>差异内容：clone(): Promise\<Metadata>;|api/@ohos.multimedia.image.d.ts|
|新增API|NA|类名：image；<br>API声明：enum FragmentMapPropertyKey<br>差异内容：enum FragmentMapPropertyKey|api/@ohos.multimedia.image.d.ts|
|新增API|NA|类名：FragmentMapPropertyKey；<br>API声明：X_IN_ORIGINAL = 'XInOriginal'<br>差异内容：X_IN_ORIGINAL = 'XInOriginal'|api/@ohos.multimedia.image.d.ts|
|新增API|NA|类名：FragmentMapPropertyKey；<br>API声明：Y_IN_ORIGINAL = 'YInOriginal'<br>差异内容：Y_IN_ORIGINAL = 'YInOriginal'|api/@ohos.multimedia.image.d.ts|
|新增API|NA|类名：FragmentMapPropertyKey；<br>API声明：WIDTH = 'FragmentImageWidth'<br>差异内容：WIDTH = 'FragmentImageWidth'|api/@ohos.multimedia.image.d.ts|
|新增API|NA|类名：FragmentMapPropertyKey；<br>API声明：HEIGHT = 'FragmentImageHeight'<br>差异内容：HEIGHT = 'FragmentImageHeight'|api/@ohos.multimedia.image.d.ts|
|新增API|NA|类名：image；<br>API声明：interface DecodingOptionsForPicture<br>差异内容：interface DecodingOptionsForPicture|api/@ohos.multimedia.image.d.ts|
|新增API|NA|类名：DecodingOptionsForPicture；<br>API声明：desiredAuxiliaryPictures: Array\<AuxiliaryPictureType>;<br>差异内容：desiredAuxiliaryPictures: Array\<AuxiliaryPictureType>;|api/@ohos.multimedia.image.d.ts|
|新增API|NA|类名：image；<br>API声明：interface AuxiliaryPictureInfo<br>差异内容：interface AuxiliaryPictureInfo|api/@ohos.multimedia.image.d.ts|
|新增API|NA|类名：AuxiliaryPictureInfo；<br>API声明：auxiliaryPictureType: AuxiliaryPictureType;<br>差异内容：auxiliaryPictureType: AuxiliaryPictureType;|api/@ohos.multimedia.image.d.ts|
|新增API|NA|类名：AuxiliaryPictureInfo；<br>API声明：size: Size;<br>差异内容：size: Size;|api/@ohos.multimedia.image.d.ts|
|新增API|NA|类名：AuxiliaryPictureInfo；<br>API声明：rowStride: number;<br>差异内容：rowStride: number;|api/@ohos.multimedia.image.d.ts|
|新增API|NA|类名：AuxiliaryPictureInfo；<br>API声明：pixelFormat: PixelMapFormat;<br>差异内容：pixelFormat: PixelMapFormat;|api/@ohos.multimedia.image.d.ts|
|新增API|NA|类名：AuxiliaryPictureInfo；<br>API声明：colorSpace: colorSpaceManager.ColorSpaceManager;<br>差异内容：colorSpace: colorSpaceManager.ColorSpaceManager;|api/@ohos.multimedia.image.d.ts|
|新增API|NA|类名：ImageSource；<br>API声明：createPicture(options?: DecodingOptionsForPicture): Promise\<Picture>;<br>差异内容：createPicture(options?: DecodingOptionsForPicture): Promise\<Picture>;|api/@ohos.multimedia.image.d.ts|
|新增API|NA|类名：ImagePacker；<br>API声明：packToData(source: ImageSource, options: PackingOption): Promise\<ArrayBuffer>;<br>差异内容：packToData(source: ImageSource, options: PackingOption): Promise\<ArrayBuffer>;|api/@ohos.multimedia.image.d.ts|
|新增API|NA|类名：ImagePacker；<br>API声明：packToData(source: PixelMap, options: PackingOption): Promise\<ArrayBuffer>;<br>差异内容：packToData(source: PixelMap, options: PackingOption): Promise\<ArrayBuffer>;|api/@ohos.multimedia.image.d.ts|
|新增API|NA|类名：ImageReceiver；<br>API声明：off(type: 'imageArrival', callback?: AsyncCallback\<void>): void;<br>差异内容：off(type: 'imageArrival', callback?: AsyncCallback\<void>): void;|api/@ohos.multimedia.image.d.ts|
|新增API|NA|类名：ImageCreator；<br>API声明：off(type: 'imageRelease', callback?: AsyncCallback\<void>): void;<br>差异内容：off(type: 'imageRelease', callback?: AsyncCallback\<void>): void;|api/@ohos.multimedia.image.d.ts|
