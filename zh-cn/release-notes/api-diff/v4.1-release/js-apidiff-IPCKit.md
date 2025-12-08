| 操作 | 旧版本 | 新版本 | d.ts文件 |
| ---- | ------ | ------ | -------- |
|新增API|NA|类名：global；<br>API声明：declare namespace rpc<br>差异内容：declare namespace rpc|api/@ohos.rpc.d.ts|
|新增API|NA|类名：rpc；<br>API声明：enum ErrorCode<br>差异内容：enum ErrorCode|api/@ohos.rpc.d.ts|
|新增API|NA|类名：ErrorCode；<br>API声明：CHECK_PARAM_ERROR = 401<br>差异内容：CHECK_PARAM_ERROR = 401|api/@ohos.rpc.d.ts|
|新增API|NA|类名：ErrorCode；<br>API声明：OS_MMAP_ERROR = 1900001<br>差异内容：OS_MMAP_ERROR = 1900001|api/@ohos.rpc.d.ts|
|新增API|NA|类名：ErrorCode；<br>API声明：OS_IOCTL_ERROR = 1900002<br>差异内容：OS_IOCTL_ERROR = 1900002|api/@ohos.rpc.d.ts|
|新增API|NA|类名：ErrorCode；<br>API声明：WRITE_TO_ASHMEM_ERROR = 1900003<br>差异内容：WRITE_TO_ASHMEM_ERROR = 1900003|api/@ohos.rpc.d.ts|
|新增API|NA|类名：ErrorCode；<br>API声明：READ_FROM_ASHMEM_ERROR = 1900004<br>差异内容：READ_FROM_ASHMEM_ERROR = 1900004|api/@ohos.rpc.d.ts|
|新增API|NA|类名：ErrorCode；<br>API声明：ONLY_PROXY_OBJECT_PERMITTED_ERROR = 1900005<br>差异内容：ONLY_PROXY_OBJECT_PERMITTED_ERROR = 1900005|api/@ohos.rpc.d.ts|
|新增API|NA|类名：ErrorCode；<br>API声明：ONLY_REMOTE_OBJECT_PERMITTED_ERROR = 1900006<br>差异内容：ONLY_REMOTE_OBJECT_PERMITTED_ERROR = 1900006|api/@ohos.rpc.d.ts|
|新增API|NA|类名：ErrorCode；<br>API声明：COMMUNICATION_ERROR = 1900007<br>差异内容：COMMUNICATION_ERROR = 1900007|api/@ohos.rpc.d.ts|
|新增API|NA|类名：ErrorCode；<br>API声明：PROXY_OR_REMOTE_OBJECT_INVALID_ERROR = 1900008<br>差异内容：PROXY_OR_REMOTE_OBJECT_INVALID_ERROR = 1900008|api/@ohos.rpc.d.ts|
|新增API|NA|类名：ErrorCode；<br>API声明：WRITE_DATA_TO_MESSAGE_SEQUENCE_ERROR = 1900009<br>差异内容：WRITE_DATA_TO_MESSAGE_SEQUENCE_ERROR = 1900009|api/@ohos.rpc.d.ts|
|新增API|NA|类名：ErrorCode；<br>API声明：READ_DATA_FROM_MESSAGE_SEQUENCE_ERROR = 1900010<br>差异内容：READ_DATA_FROM_MESSAGE_SEQUENCE_ERROR = 1900010|api/@ohos.rpc.d.ts|
|新增API|NA|类名：ErrorCode；<br>API声明：PARCEL_MEMORY_ALLOC_ERROR = 1900011<br>差异内容：PARCEL_MEMORY_ALLOC_ERROR = 1900011|api/@ohos.rpc.d.ts|
|新增API|NA|类名：ErrorCode；<br>API声明：CALL_JS_METHOD_ERROR = 1900012<br>差异内容：CALL_JS_METHOD_ERROR = 1900012|api/@ohos.rpc.d.ts|
|新增API|NA|类名：ErrorCode；<br>API声明：OS_DUP_ERROR = 1900013<br>差异内容：OS_DUP_ERROR = 1900013|api/@ohos.rpc.d.ts|
|新增API|NA|类名：rpc；<br>API声明：class MessageParcel<br>差异内容：class MessageParcel|api/@ohos.rpc.d.ts|
|新增API|NA|类名：MessageParcel；<br>API声明：static create(): MessageParcel;<br>差异内容：static create(): MessageParcel;|api/@ohos.rpc.d.ts|
|新增API|NA|类名：MessageParcel；<br>API声明：reclaim(): void;<br>差异内容：reclaim(): void;|api/@ohos.rpc.d.ts|
|新增API|NA|类名：MessageParcel；<br>API声明：writeRemoteObject(object: IRemoteObject): boolean;<br>差异内容：writeRemoteObject(object: IRemoteObject): boolean;|api/@ohos.rpc.d.ts|
|新增API|NA|类名：MessageParcel；<br>API声明：readRemoteObject(): IRemoteObject;<br>差异内容：readRemoteObject(): IRemoteObject;|api/@ohos.rpc.d.ts|
|新增API|NA|类名：MessageParcel；<br>API声明：writeInterfaceToken(token: string): boolean;<br>差异内容：writeInterfaceToken(token: string): boolean;|api/@ohos.rpc.d.ts|
|新增API|NA|类名：MessageParcel；<br>API声明：readInterfaceToken(): string;<br>差异内容：readInterfaceToken(): string;|api/@ohos.rpc.d.ts|
|新增API|NA|类名：MessageParcel；<br>API声明：getSize(): number;<br>差异内容：getSize(): number;|api/@ohos.rpc.d.ts|
|新增API|NA|类名：MessageParcel；<br>API声明：getCapacity(): number;<br>差异内容：getCapacity(): number;|api/@ohos.rpc.d.ts|
|新增API|NA|类名：MessageParcel；<br>API声明：setSize(size: number): boolean;<br>差异内容：setSize(size: number): boolean;|api/@ohos.rpc.d.ts|
|新增API|NA|类名：MessageParcel；<br>API声明：setCapacity(size: number): boolean;<br>差异内容：setCapacity(size: number): boolean;|api/@ohos.rpc.d.ts|
|新增API|NA|类名：MessageParcel；<br>API声明：getWritableBytes(): number;<br>差异内容：getWritableBytes(): number;|api/@ohos.rpc.d.ts|
|新增API|NA|类名：MessageParcel；<br>API声明：getReadableBytes(): number;<br>差异内容：getReadableBytes(): number;|api/@ohos.rpc.d.ts|
|新增API|NA|类名：MessageParcel；<br>API声明：getReadPosition(): number;<br>差异内容：getReadPosition(): number;|api/@ohos.rpc.d.ts|
|新增API|NA|类名：MessageParcel；<br>API声明：getWritePosition(): number;<br>差异内容：getWritePosition(): number;|api/@ohos.rpc.d.ts|
|新增API|NA|类名：MessageParcel；<br>API声明：rewindRead(pos: number): boolean;<br>差异内容：rewindRead(pos: number): boolean;|api/@ohos.rpc.d.ts|
|新增API|NA|类名：MessageParcel；<br>API声明：rewindWrite(pos: number): boolean;<br>差异内容：rewindWrite(pos: number): boolean;|api/@ohos.rpc.d.ts|
|新增API|NA|类名：MessageParcel；<br>API声明：writeNoException(): void;<br>差异内容：writeNoException(): void;|api/@ohos.rpc.d.ts|
|新增API|NA|类名：MessageParcel；<br>API声明：readException(): void;<br>差异内容：readException(): void;|api/@ohos.rpc.d.ts|
|新增API|NA|类名：MessageParcel；<br>API声明：writeByte(val: number): boolean;<br>差异内容：writeByte(val: number): boolean;|api/@ohos.rpc.d.ts|
|新增API|NA|类名：MessageParcel；<br>API声明：writeShort(val: number): boolean;<br>差异内容：writeShort(val: number): boolean;|api/@ohos.rpc.d.ts|
|新增API|NA|类名：MessageParcel；<br>API声明：writeInt(val: number): boolean;<br>差异内容：writeInt(val: number): boolean;|api/@ohos.rpc.d.ts|
|新增API|NA|类名：MessageParcel；<br>API声明：writeLong(val: number): boolean;<br>差异内容：writeLong(val: number): boolean;|api/@ohos.rpc.d.ts|
|新增API|NA|类名：MessageParcel；<br>API声明：writeFloat(val: number): boolean;<br>差异内容：writeFloat(val: number): boolean;|api/@ohos.rpc.d.ts|
|新增API|NA|类名：MessageParcel；<br>API声明：writeDouble(val: number): boolean;<br>差异内容：writeDouble(val: number): boolean;|api/@ohos.rpc.d.ts|
|新增API|NA|类名：MessageParcel；<br>API声明：writeBoolean(val: boolean): boolean;<br>差异内容：writeBoolean(val: boolean): boolean;|api/@ohos.rpc.d.ts|
|新增API|NA|类名：MessageParcel；<br>API声明：writeChar(val: number): boolean;<br>差异内容：writeChar(val: number): boolean;|api/@ohos.rpc.d.ts|
|新增API|NA|类名：MessageParcel；<br>API声明：writeString(val: string): boolean;<br>差异内容：writeString(val: string): boolean;|api/@ohos.rpc.d.ts|
|新增API|NA|类名：MessageParcel；<br>API声明：writeSequenceable(val: Sequenceable): boolean;<br>差异内容：writeSequenceable(val: Sequenceable): boolean;|api/@ohos.rpc.d.ts|
|新增API|NA|类名：MessageParcel；<br>API声明：writeByteArray(byteArray: number[]): boolean;<br>差异内容：writeByteArray(byteArray: number[]): boolean;|api/@ohos.rpc.d.ts|
|新增API|NA|类名：MessageParcel；<br>API声明：writeShortArray(shortArray: number[]): boolean;<br>差异内容：writeShortArray(shortArray: number[]): boolean;|api/@ohos.rpc.d.ts|
|新增API|NA|类名：MessageParcel；<br>API声明：writeIntArray(intArray: number[]): boolean;<br>差异内容：writeIntArray(intArray: number[]): boolean;|api/@ohos.rpc.d.ts|
|新增API|NA|类名：MessageParcel；<br>API声明：writeLongArray(longArray: number[]): boolean;<br>差异内容：writeLongArray(longArray: number[]): boolean;|api/@ohos.rpc.d.ts|
|新增API|NA|类名：MessageParcel；<br>API声明：writeFloatArray(floatArray: number[]): boolean;<br>差异内容：writeFloatArray(floatArray: number[]): boolean;|api/@ohos.rpc.d.ts|
|新增API|NA|类名：MessageParcel；<br>API声明：writeDoubleArray(doubleArray: number[]): boolean;<br>差异内容：writeDoubleArray(doubleArray: number[]): boolean;|api/@ohos.rpc.d.ts|
|新增API|NA|类名：MessageParcel；<br>API声明：writeBooleanArray(booleanArray: boolean[]): boolean;<br>差异内容：writeBooleanArray(booleanArray: boolean[]): boolean;|api/@ohos.rpc.d.ts|
|新增API|NA|类名：MessageParcel；<br>API声明：writeCharArray(charArray: number[]): boolean;<br>差异内容：writeCharArray(charArray: number[]): boolean;|api/@ohos.rpc.d.ts|
|新增API|NA|类名：MessageParcel；<br>API声明：writeStringArray(stringArray: string[]): boolean;<br>差异内容：writeStringArray(stringArray: string[]): boolean;|api/@ohos.rpc.d.ts|
|新增API|NA|类名：MessageParcel；<br>API声明：writeSequenceableArray(sequenceableArray: Sequenceable[]): boolean;<br>差异内容：writeSequenceableArray(sequenceableArray: Sequenceable[]): boolean;|api/@ohos.rpc.d.ts|
|新增API|NA|类名：MessageParcel；<br>API声明：writeRemoteObjectArray(objectArray: IRemoteObject[]): boolean;<br>差异内容：writeRemoteObjectArray(objectArray: IRemoteObject[]): boolean;|api/@ohos.rpc.d.ts|
|新增API|NA|类名：MessageParcel；<br>API声明：readByte(): number;<br>差异内容：readByte(): number;|api/@ohos.rpc.d.ts|
|新增API|NA|类名：MessageParcel；<br>API声明：readShort(): number;<br>差异内容：readShort(): number;|api/@ohos.rpc.d.ts|
|新增API|NA|类名：MessageParcel；<br>API声明：readInt(): number;<br>差异内容：readInt(): number;|api/@ohos.rpc.d.ts|
|新增API|NA|类名：MessageParcel；<br>API声明：readLong(): number;<br>差异内容：readLong(): number;|api/@ohos.rpc.d.ts|
|新增API|NA|类名：MessageParcel；<br>API声明：readFloat(): number;<br>差异内容：readFloat(): number;|api/@ohos.rpc.d.ts|
|新增API|NA|类名：MessageParcel；<br>API声明：readDouble(): number;<br>差异内容：readDouble(): number;|api/@ohos.rpc.d.ts|
|新增API|NA|类名：MessageParcel；<br>API声明：readBoolean(): boolean;<br>差异内容：readBoolean(): boolean;|api/@ohos.rpc.d.ts|
|新增API|NA|类名：MessageParcel；<br>API声明：readChar(): number;<br>差异内容：readChar(): number;|api/@ohos.rpc.d.ts|
|新增API|NA|类名：MessageParcel；<br>API声明：readString(): string;<br>差异内容：readString(): string;|api/@ohos.rpc.d.ts|
|新增API|NA|类名：MessageParcel；<br>API声明：readSequenceable(dataIn: Sequenceable): boolean;<br>差异内容：readSequenceable(dataIn: Sequenceable): boolean;|api/@ohos.rpc.d.ts|
|新增API|NA|类名：MessageParcel；<br>API声明：readByteArray(dataIn: number[]): void;<br>差异内容：readByteArray(dataIn: number[]): void;|api/@ohos.rpc.d.ts|
|新增API|NA|类名：MessageParcel；<br>API声明：readByteArray(): number[];<br>差异内容：readByteArray(): number[];|api/@ohos.rpc.d.ts|
|新增API|NA|类名：MessageParcel；<br>API声明：readShortArray(dataIn: number[]): void;<br>差异内容：readShortArray(dataIn: number[]): void;|api/@ohos.rpc.d.ts|
|新增API|NA|类名：MessageParcel；<br>API声明：readShortArray(): number[];<br>差异内容：readShortArray(): number[];|api/@ohos.rpc.d.ts|
|新增API|NA|类名：MessageParcel；<br>API声明：readIntArray(dataIn: number[]): void;<br>差异内容：readIntArray(dataIn: number[]): void;|api/@ohos.rpc.d.ts|
|新增API|NA|类名：MessageParcel；<br>API声明：readIntArray(): number[];<br>差异内容：readIntArray(): number[];|api/@ohos.rpc.d.ts|
|新增API|NA|类名：MessageParcel；<br>API声明：readLongArray(dataIn: number[]): void;<br>差异内容：readLongArray(dataIn: number[]): void;|api/@ohos.rpc.d.ts|
|新增API|NA|类名：MessageParcel；<br>API声明：readLongArray(): number[];<br>差异内容：readLongArray(): number[];|api/@ohos.rpc.d.ts|
|新增API|NA|类名：MessageParcel；<br>API声明：readFloatArray(dataIn: number[]): void;<br>差异内容：readFloatArray(dataIn: number[]): void;|api/@ohos.rpc.d.ts|
|新增API|NA|类名：MessageParcel；<br>API声明：readFloatArray(): number[];<br>差异内容：readFloatArray(): number[];|api/@ohos.rpc.d.ts|
|新增API|NA|类名：MessageParcel；<br>API声明：readDoubleArray(dataIn: number[]): void;<br>差异内容：readDoubleArray(dataIn: number[]): void;|api/@ohos.rpc.d.ts|
|新增API|NA|类名：MessageParcel；<br>API声明：readDoubleArray(): number[];<br>差异内容：readDoubleArray(): number[];|api/@ohos.rpc.d.ts|
|新增API|NA|类名：MessageParcel；<br>API声明：readBooleanArray(dataIn: boolean[]): void;<br>差异内容：readBooleanArray(dataIn: boolean[]): void;|api/@ohos.rpc.d.ts|
|新增API|NA|类名：MessageParcel；<br>API声明：readBooleanArray(): boolean[];<br>差异内容：readBooleanArray(): boolean[];|api/@ohos.rpc.d.ts|
|新增API|NA|类名：MessageParcel；<br>API声明：readCharArray(dataIn: number[]): void;<br>差异内容：readCharArray(dataIn: number[]): void;|api/@ohos.rpc.d.ts|
|新增API|NA|类名：MessageParcel；<br>API声明：readCharArray(): number[];<br>差异内容：readCharArray(): number[];|api/@ohos.rpc.d.ts|
|新增API|NA|类名：MessageParcel；<br>API声明：readStringArray(dataIn: string[]): void;<br>差异内容：readStringArray(dataIn: string[]): void;|api/@ohos.rpc.d.ts|
|新增API|NA|类名：MessageParcel；<br>API声明：readStringArray(): string[];<br>差异内容：readStringArray(): string[];|api/@ohos.rpc.d.ts|
|新增API|NA|类名：MessageParcel；<br>API声明：readSequenceableArray(sequenceableArray: Sequenceable[]): void;<br>差异内容：readSequenceableArray(sequenceableArray: Sequenceable[]): void;|api/@ohos.rpc.d.ts|
|新增API|NA|类名：MessageParcel；<br>API声明：readRemoteObjectArray(objects: IRemoteObject[]): void;<br>差异内容：readRemoteObjectArray(objects: IRemoteObject[]): void;|api/@ohos.rpc.d.ts|
|新增API|NA|类名：MessageParcel；<br>API声明：readRemoteObjectArray(): IRemoteObject[];<br>差异内容：readRemoteObjectArray(): IRemoteObject[];|api/@ohos.rpc.d.ts|
|新增API|NA|类名：MessageParcel；<br>API声明：static closeFileDescriptor(fd: number): void;<br>差异内容：static closeFileDescriptor(fd: number): void;|api/@ohos.rpc.d.ts|
|新增API|NA|类名：MessageParcel；<br>API声明：static dupFileDescriptor(fd: number): number;<br>差异内容：static dupFileDescriptor(fd: number): number;|api/@ohos.rpc.d.ts|
|新增API|NA|类名：MessageParcel；<br>API声明：containFileDescriptors(): boolean;<br>差异内容：containFileDescriptors(): boolean;|api/@ohos.rpc.d.ts|
|新增API|NA|类名：MessageParcel；<br>API声明：writeFileDescriptor(fd: number): boolean;<br>差异内容：writeFileDescriptor(fd: number): boolean;|api/@ohos.rpc.d.ts|
|新增API|NA|类名：MessageParcel；<br>API声明：readFileDescriptor(): number;<br>差异内容：readFileDescriptor(): number;|api/@ohos.rpc.d.ts|
|新增API|NA|类名：MessageParcel；<br>API声明：writeAshmem(ashmem: Ashmem): boolean;<br>差异内容：writeAshmem(ashmem: Ashmem): boolean;|api/@ohos.rpc.d.ts|
|新增API|NA|类名：MessageParcel；<br>API声明：readAshmem(): Ashmem;<br>差异内容：readAshmem(): Ashmem;|api/@ohos.rpc.d.ts|
|新增API|NA|类名：MessageParcel；<br>API声明：getRawDataCapacity(): number;<br>差异内容：getRawDataCapacity(): number;|api/@ohos.rpc.d.ts|
|新增API|NA|类名：MessageParcel；<br>API声明：writeRawData(rawData: number[], size: number): boolean;<br>差异内容：writeRawData(rawData: number[], size: number): boolean;|api/@ohos.rpc.d.ts|
|新增API|NA|类名：MessageParcel；<br>API声明：readRawData(size: number): number[];<br>差异内容：readRawData(size: number): number[];|api/@ohos.rpc.d.ts|
|新增API|NA|类名：rpc；<br>API声明：class MessageSequence<br>差异内容：class MessageSequence|api/@ohos.rpc.d.ts|
|新增API|NA|类名：MessageSequence；<br>API声明：static create(): MessageSequence;<br>差异内容：static create(): MessageSequence;|api/@ohos.rpc.d.ts|
|新增API|NA|类名：MessageSequence；<br>API声明：reclaim(): void;<br>差异内容：reclaim(): void;|api/@ohos.rpc.d.ts|
|新增API|NA|类名：MessageSequence；<br>API声明：writeRemoteObject(object: IRemoteObject): void;<br>差异内容：writeRemoteObject(object: IRemoteObject): void;|api/@ohos.rpc.d.ts|
|新增API|NA|类名：MessageSequence；<br>API声明：readRemoteObject(): IRemoteObject;<br>差异内容：readRemoteObject(): IRemoteObject;|api/@ohos.rpc.d.ts|
|新增API|NA|类名：MessageSequence；<br>API声明：writeInterfaceToken(token: string): void;<br>差异内容：writeInterfaceToken(token: string): void;|api/@ohos.rpc.d.ts|
|新增API|NA|类名：MessageSequence；<br>API声明：readInterfaceToken(): string;<br>差异内容：readInterfaceToken(): string;|api/@ohos.rpc.d.ts|
|新增API|NA|类名：MessageSequence；<br>API声明：getSize(): number;<br>差异内容：getSize(): number;|api/@ohos.rpc.d.ts|
|新增API|NA|类名：MessageSequence；<br>API声明：getCapacity(): number;<br>差异内容：getCapacity(): number;|api/@ohos.rpc.d.ts|
|新增API|NA|类名：MessageSequence；<br>API声明：setSize(size: number): void;<br>差异内容：setSize(size: number): void;|api/@ohos.rpc.d.ts|
|新增API|NA|类名：MessageSequence；<br>API声明：setCapacity(size: number): void;<br>差异内容：setCapacity(size: number): void;|api/@ohos.rpc.d.ts|
|新增API|NA|类名：MessageSequence；<br>API声明：getWritableBytes(): number;<br>差异内容：getWritableBytes(): number;|api/@ohos.rpc.d.ts|
|新增API|NA|类名：MessageSequence；<br>API声明：getReadableBytes(): number;<br>差异内容：getReadableBytes(): number;|api/@ohos.rpc.d.ts|
|新增API|NA|类名：MessageSequence；<br>API声明：getReadPosition(): number;<br>差异内容：getReadPosition(): number;|api/@ohos.rpc.d.ts|
|新增API|NA|类名：MessageSequence；<br>API声明：getWritePosition(): number;<br>差异内容：getWritePosition(): number;|api/@ohos.rpc.d.ts|
|新增API|NA|类名：MessageSequence；<br>API声明：rewindRead(pos: number): void;<br>差异内容：rewindRead(pos: number): void;|api/@ohos.rpc.d.ts|
|新增API|NA|类名：MessageSequence；<br>API声明：rewindWrite(pos: number): void;<br>差异内容：rewindWrite(pos: number): void;|api/@ohos.rpc.d.ts|
|新增API|NA|类名：MessageSequence；<br>API声明：writeNoException(): void;<br>差异内容：writeNoException(): void;|api/@ohos.rpc.d.ts|
|新增API|NA|类名：MessageSequence；<br>API声明：readException(): void;<br>差异内容：readException(): void;|api/@ohos.rpc.d.ts|
|新增API|NA|类名：MessageSequence；<br>API声明：writeByte(val: number): void;<br>差异内容：writeByte(val: number): void;|api/@ohos.rpc.d.ts|
|新增API|NA|类名：MessageSequence；<br>API声明：writeShort(val: number): void;<br>差异内容：writeShort(val: number): void;|api/@ohos.rpc.d.ts|
|新增API|NA|类名：MessageSequence；<br>API声明：writeInt(val: number): void;<br>差异内容：writeInt(val: number): void;|api/@ohos.rpc.d.ts|
|新增API|NA|类名：MessageSequence；<br>API声明：writeLong(val: number): void;<br>差异内容：writeLong(val: number): void;|api/@ohos.rpc.d.ts|
|新增API|NA|类名：MessageSequence；<br>API声明：writeFloat(val: number): void;<br>差异内容：writeFloat(val: number): void;|api/@ohos.rpc.d.ts|
|新增API|NA|类名：MessageSequence；<br>API声明：writeDouble(val: number): void;<br>差异内容：writeDouble(val: number): void;|api/@ohos.rpc.d.ts|
|新增API|NA|类名：MessageSequence；<br>API声明：writeBoolean(val: boolean): void;<br>差异内容：writeBoolean(val: boolean): void;|api/@ohos.rpc.d.ts|
|新增API|NA|类名：MessageSequence；<br>API声明：writeChar(val: number): void;<br>差异内容：writeChar(val: number): void;|api/@ohos.rpc.d.ts|
|新增API|NA|类名：MessageSequence；<br>API声明：writeString(val: string): void;<br>差异内容：writeString(val: string): void;|api/@ohos.rpc.d.ts|
|新增API|NA|类名：MessageSequence；<br>API声明：writeParcelable(val: Parcelable): void;<br>差异内容：writeParcelable(val: Parcelable): void;|api/@ohos.rpc.d.ts|
|新增API|NA|类名：MessageSequence；<br>API声明：writeByteArray(byteArray: number[]): void;<br>差异内容：writeByteArray(byteArray: number[]): void;|api/@ohos.rpc.d.ts|
|新增API|NA|类名：MessageSequence；<br>API声明：writeShortArray(shortArray: number[]): void;<br>差异内容：writeShortArray(shortArray: number[]): void;|api/@ohos.rpc.d.ts|
|新增API|NA|类名：MessageSequence；<br>API声明：writeIntArray(intArray: number[]): void;<br>差异内容：writeIntArray(intArray: number[]): void;|api/@ohos.rpc.d.ts|
|新增API|NA|类名：MessageSequence；<br>API声明：writeLongArray(longArray: number[]): void;<br>差异内容：writeLongArray(longArray: number[]): void;|api/@ohos.rpc.d.ts|
|新增API|NA|类名：MessageSequence；<br>API声明：writeFloatArray(floatArray: number[]): void;<br>差异内容：writeFloatArray(floatArray: number[]): void;|api/@ohos.rpc.d.ts|
|新增API|NA|类名：MessageSequence；<br>API声明：writeDoubleArray(doubleArray: number[]): void;<br>差异内容：writeDoubleArray(doubleArray: number[]): void;|api/@ohos.rpc.d.ts|
|新增API|NA|类名：MessageSequence；<br>API声明：writeBooleanArray(booleanArray: boolean[]): void;<br>差异内容：writeBooleanArray(booleanArray: boolean[]): void;|api/@ohos.rpc.d.ts|
|新增API|NA|类名：MessageSequence；<br>API声明：writeCharArray(charArray: number[]): void;<br>差异内容：writeCharArray(charArray: number[]): void;|api/@ohos.rpc.d.ts|
|新增API|NA|类名：MessageSequence；<br>API声明：writeStringArray(stringArray: string[]): void;<br>差异内容：writeStringArray(stringArray: string[]): void;|api/@ohos.rpc.d.ts|
|新增API|NA|类名：MessageSequence；<br>API声明：writeParcelableArray(parcelableArray: Parcelable[]): void;<br>差异内容：writeParcelableArray(parcelableArray: Parcelable[]): void;|api/@ohos.rpc.d.ts|
|新增API|NA|类名：MessageSequence；<br>API声明：writeRemoteObjectArray(objectArray: IRemoteObject[]): void;<br>差异内容：writeRemoteObjectArray(objectArray: IRemoteObject[]): void;|api/@ohos.rpc.d.ts|
|新增API|NA|类名：MessageSequence；<br>API声明：readByte(): number;<br>差异内容：readByte(): number;|api/@ohos.rpc.d.ts|
|新增API|NA|类名：MessageSequence；<br>API声明：readShort(): number;<br>差异内容：readShort(): number;|api/@ohos.rpc.d.ts|
|新增API|NA|类名：MessageSequence；<br>API声明：readInt(): number;<br>差异内容：readInt(): number;|api/@ohos.rpc.d.ts|
|新增API|NA|类名：MessageSequence；<br>API声明：readLong(): number;<br>差异内容：readLong(): number;|api/@ohos.rpc.d.ts|
|新增API|NA|类名：MessageSequence；<br>API声明：readFloat(): number;<br>差异内容：readFloat(): number;|api/@ohos.rpc.d.ts|
|新增API|NA|类名：MessageSequence；<br>API声明：readDouble(): number;<br>差异内容：readDouble(): number;|api/@ohos.rpc.d.ts|
|新增API|NA|类名：MessageSequence；<br>API声明：readBoolean(): boolean;<br>差异内容：readBoolean(): boolean;|api/@ohos.rpc.d.ts|
|新增API|NA|类名：MessageSequence；<br>API声明：readChar(): number;<br>差异内容：readChar(): number;|api/@ohos.rpc.d.ts|
|新增API|NA|类名：MessageSequence；<br>API声明：readString(): string;<br>差异内容：readString(): string;|api/@ohos.rpc.d.ts|
|新增API|NA|类名：MessageSequence；<br>API声明：readParcelable(dataIn: Parcelable): void;<br>差异内容：readParcelable(dataIn: Parcelable): void;|api/@ohos.rpc.d.ts|
|新增API|NA|类名：MessageSequence；<br>API声明：readByteArray(dataIn: number[]): void;<br>差异内容：readByteArray(dataIn: number[]): void;|api/@ohos.rpc.d.ts|
|新增API|NA|类名：MessageSequence；<br>API声明：readByteArray(): number[];<br>差异内容：readByteArray(): number[];|api/@ohos.rpc.d.ts|
|新增API|NA|类名：MessageSequence；<br>API声明：readShortArray(dataIn: number[]): void;<br>差异内容：readShortArray(dataIn: number[]): void;|api/@ohos.rpc.d.ts|
|新增API|NA|类名：MessageSequence；<br>API声明：readShortArray(): number[];<br>差异内容：readShortArray(): number[];|api/@ohos.rpc.d.ts|
|新增API|NA|类名：MessageSequence；<br>API声明：readIntArray(dataIn: number[]): void;<br>差异内容：readIntArray(dataIn: number[]): void;|api/@ohos.rpc.d.ts|
|新增API|NA|类名：MessageSequence；<br>API声明：readIntArray(): number[];<br>差异内容：readIntArray(): number[];|api/@ohos.rpc.d.ts|
|新增API|NA|类名：MessageSequence；<br>API声明：readLongArray(dataIn: number[]): void;<br>差异内容：readLongArray(dataIn: number[]): void;|api/@ohos.rpc.d.ts|
|新增API|NA|类名：MessageSequence；<br>API声明：readLongArray(): number[];<br>差异内容：readLongArray(): number[];|api/@ohos.rpc.d.ts|
|新增API|NA|类名：MessageSequence；<br>API声明：readFloatArray(dataIn: number[]): void;<br>差异内容：readFloatArray(dataIn: number[]): void;|api/@ohos.rpc.d.ts|
|新增API|NA|类名：MessageSequence；<br>API声明：readFloatArray(): number[];<br>差异内容：readFloatArray(): number[];|api/@ohos.rpc.d.ts|
|新增API|NA|类名：MessageSequence；<br>API声明：readDoubleArray(dataIn: number[]): void;<br>差异内容：readDoubleArray(dataIn: number[]): void;|api/@ohos.rpc.d.ts|
|新增API|NA|类名：MessageSequence；<br>API声明：readDoubleArray(): number[];<br>差异内容：readDoubleArray(): number[];|api/@ohos.rpc.d.ts|
|新增API|NA|类名：MessageSequence；<br>API声明：readBooleanArray(dataIn: boolean[]): void;<br>差异内容：readBooleanArray(dataIn: boolean[]): void;|api/@ohos.rpc.d.ts|
|新增API|NA|类名：MessageSequence；<br>API声明：readBooleanArray(): boolean[];<br>差异内容：readBooleanArray(): boolean[];|api/@ohos.rpc.d.ts|
|新增API|NA|类名：MessageSequence；<br>API声明：readCharArray(dataIn: number[]): void;<br>差异内容：readCharArray(dataIn: number[]): void;|api/@ohos.rpc.d.ts|
|新增API|NA|类名：MessageSequence；<br>API声明：readCharArray(): number[];<br>差异内容：readCharArray(): number[];|api/@ohos.rpc.d.ts|
|新增API|NA|类名：MessageSequence；<br>API声明：readStringArray(dataIn: string[]): void;<br>差异内容：readStringArray(dataIn: string[]): void;|api/@ohos.rpc.d.ts|
|新增API|NA|类名：MessageSequence；<br>API声明：readStringArray(): string[];<br>差异内容：readStringArray(): string[];|api/@ohos.rpc.d.ts|
|新增API|NA|类名：MessageSequence；<br>API声明：readParcelableArray(parcelableArray: Parcelable[]): void;<br>差异内容：readParcelableArray(parcelableArray: Parcelable[]): void;|api/@ohos.rpc.d.ts|
|新增API|NA|类名：MessageSequence；<br>API声明：readRemoteObjectArray(objects: IRemoteObject[]): void;<br>差异内容：readRemoteObjectArray(objects: IRemoteObject[]): void;|api/@ohos.rpc.d.ts|
|新增API|NA|类名：MessageSequence；<br>API声明：readRemoteObjectArray(): IRemoteObject[];<br>差异内容：readRemoteObjectArray(): IRemoteObject[];|api/@ohos.rpc.d.ts|
|新增API|NA|类名：MessageSequence；<br>API声明：static closeFileDescriptor(fd: number): void;<br>差异内容：static closeFileDescriptor(fd: number): void;|api/@ohos.rpc.d.ts|
|新增API|NA|类名：MessageSequence；<br>API声明：static dupFileDescriptor(fd: number): number;<br>差异内容：static dupFileDescriptor(fd: number): number;|api/@ohos.rpc.d.ts|
|新增API|NA|类名：MessageSequence；<br>API声明：containFileDescriptors(): boolean;<br>差异内容：containFileDescriptors(): boolean;|api/@ohos.rpc.d.ts|
|新增API|NA|类名：MessageSequence；<br>API声明：writeFileDescriptor(fd: number): void;<br>差异内容：writeFileDescriptor(fd: number): void;|api/@ohos.rpc.d.ts|
|新增API|NA|类名：MessageSequence；<br>API声明：readFileDescriptor(): number;<br>差异内容：readFileDescriptor(): number;|api/@ohos.rpc.d.ts|
|新增API|NA|类名：MessageSequence；<br>API声明：writeAshmem(ashmem: Ashmem): void;<br>差异内容：writeAshmem(ashmem: Ashmem): void;|api/@ohos.rpc.d.ts|
|新增API|NA|类名：MessageSequence；<br>API声明：readAshmem(): Ashmem;<br>差异内容：readAshmem(): Ashmem;|api/@ohos.rpc.d.ts|
|新增API|NA|类名：MessageSequence；<br>API声明：getRawDataCapacity(): number;<br>差异内容：getRawDataCapacity(): number;|api/@ohos.rpc.d.ts|
|新增API|NA|类名：MessageSequence；<br>API声明：writeRawData(rawData: number[], size: number): void;<br>差异内容：writeRawData(rawData: number[], size: number): void;|api/@ohos.rpc.d.ts|
|新增API|NA|类名：MessageSequence；<br>API声明：writeRawDataBuffer(rawData: ArrayBuffer, size: number): void;<br>差异内容：writeRawDataBuffer(rawData: ArrayBuffer, size: number): void;|api/@ohos.rpc.d.ts|
|新增API|NA|类名：MessageSequence；<br>API声明：readRawData(size: number): number[];<br>差异内容：readRawData(size: number): number[];|api/@ohos.rpc.d.ts|
|新增API|NA|类名：MessageSequence；<br>API声明：readRawDataBuffer(size: number): ArrayBuffer;<br>差异内容：readRawDataBuffer(size: number): ArrayBuffer;|api/@ohos.rpc.d.ts|
|新增API|NA|类名：rpc；<br>API声明：interface Sequenceable<br>差异内容：interface Sequenceable|api/@ohos.rpc.d.ts|
|新增API|NA|类名：Sequenceable；<br>API声明：marshalling(dataOut: MessageParcel): boolean;<br>差异内容：marshalling(dataOut: MessageParcel): boolean;|api/@ohos.rpc.d.ts|
|新增API|NA|类名：Sequenceable；<br>API声明：unmarshalling(dataIn: MessageParcel): boolean;<br>差异内容：unmarshalling(dataIn: MessageParcel): boolean;|api/@ohos.rpc.d.ts|
|新增API|NA|类名：rpc；<br>API声明：interface Parcelable<br>差异内容：interface Parcelable|api/@ohos.rpc.d.ts|
|新增API|NA|类名：Parcelable；<br>API声明：marshalling(dataOut: MessageSequence): boolean;<br>差异内容：marshalling(dataOut: MessageSequence): boolean;|api/@ohos.rpc.d.ts|
|新增API|NA|类名：Parcelable；<br>API声明：unmarshalling(dataIn: MessageSequence): boolean;<br>差异内容：unmarshalling(dataIn: MessageSequence): boolean;|api/@ohos.rpc.d.ts|
|新增API|NA|类名：rpc；<br>API声明：interface SendRequestResult<br>差异内容：interface SendRequestResult|api/@ohos.rpc.d.ts|
|新增API|NA|类名：SendRequestResult；<br>API声明：errCode: number;<br>差异内容：errCode: number;|api/@ohos.rpc.d.ts|
|新增API|NA|类名：SendRequestResult；<br>API声明：code: number;<br>差异内容：code: number;|api/@ohos.rpc.d.ts|
|新增API|NA|类名：SendRequestResult；<br>API声明：data: MessageParcel;<br>差异内容：data: MessageParcel;|api/@ohos.rpc.d.ts|
|新增API|NA|类名：SendRequestResult；<br>API声明：reply: MessageParcel;<br>差异内容：reply: MessageParcel;|api/@ohos.rpc.d.ts|
|新增API|NA|类名：rpc；<br>API声明：interface RequestResult<br>差异内容：interface RequestResult|api/@ohos.rpc.d.ts|
|新增API|NA|类名：RequestResult；<br>API声明：errCode: number;<br>差异内容：errCode: number;|api/@ohos.rpc.d.ts|
|新增API|NA|类名：RequestResult；<br>API声明：code: number;<br>差异内容：code: number;|api/@ohos.rpc.d.ts|
|新增API|NA|类名：RequestResult；<br>API声明：data: MessageSequence;<br>差异内容：data: MessageSequence;|api/@ohos.rpc.d.ts|
|新增API|NA|类名：RequestResult；<br>API声明：reply: MessageSequence;<br>差异内容：reply: MessageSequence;|api/@ohos.rpc.d.ts|
|新增API|NA|类名：rpc；<br>API声明：abstract class IRemoteObject<br>差异内容：abstract class IRemoteObject|api/@ohos.rpc.d.ts|
|新增API|NA|类名：IRemoteObject；<br>API声明：queryLocalInterface(descriptor: string): IRemoteBroker;<br>差异内容：queryLocalInterface(descriptor: string): IRemoteBroker;|api/@ohos.rpc.d.ts|
|新增API|NA|类名：IRemoteObject；<br>API声明：getLocalInterface(descriptor: string): IRemoteBroker;<br>差异内容：getLocalInterface(descriptor: string): IRemoteBroker;|api/@ohos.rpc.d.ts|
|新增API|NA|类名：IRemoteObject；<br>API声明：sendRequest(code: number, data: MessageParcel, reply: MessageParcel, options: MessageOption): boolean;<br>差异内容：sendRequest(code: number, data: MessageParcel, reply: MessageParcel, options: MessageOption): boolean;|api/@ohos.rpc.d.ts|
|新增API|NA|类名：IRemoteObject；<br>API声明：sendRequest(code: number, data: MessageParcel, reply: MessageParcel, options: MessageOption): Promise\<SendRequestResult>;<br>差异内容：sendRequest(code: number, data: MessageParcel, reply: MessageParcel, options: MessageOption): Promise\<SendRequestResult>;|api/@ohos.rpc.d.ts|
|新增API|NA|类名：IRemoteObject；<br>API声明：sendRequest(code: number, data: MessageParcel, reply: MessageParcel, options: MessageOption, callback: AsyncCallback\<SendRequestResult>): void;<br>差异内容：sendRequest(code: number, data: MessageParcel, reply: MessageParcel, options: MessageOption, callback: AsyncCallback\<SendRequestResult>): void;|api/@ohos.rpc.d.ts|
|新增API|NA|类名：IRemoteObject；<br>API声明：sendMessageRequest(code: number, data: MessageSequence, reply: MessageSequence, options: MessageOption): Promise\<RequestResult>;<br>差异内容：sendMessageRequest(code: number, data: MessageSequence, reply: MessageSequence, options: MessageOption): Promise\<RequestResult>;|api/@ohos.rpc.d.ts|
|新增API|NA|类名：IRemoteObject；<br>API声明：sendMessageRequest(code: number, data: MessageSequence, reply: MessageSequence, options: MessageOption, callback: AsyncCallback\<RequestResult>): void;<br>差异内容：sendMessageRequest(code: number, data: MessageSequence, reply: MessageSequence, options: MessageOption, callback: AsyncCallback\<RequestResult>): void;|api/@ohos.rpc.d.ts|
|新增API|NA|类名：IRemoteObject；<br>API声明：addDeathRecipient(recipient: DeathRecipient, flags: number): boolean;<br>差异内容：addDeathRecipient(recipient: DeathRecipient, flags: number): boolean;|api/@ohos.rpc.d.ts|
|新增API|NA|类名：IRemoteObject；<br>API声明：registerDeathRecipient(recipient: DeathRecipient, flags: number): void;<br>差异内容：registerDeathRecipient(recipient: DeathRecipient, flags: number): void;|api/@ohos.rpc.d.ts|
|新增API|NA|类名：IRemoteObject；<br>API声明：removeDeathRecipient(recipient: DeathRecipient, flags: number): boolean;<br>差异内容：removeDeathRecipient(recipient: DeathRecipient, flags: number): boolean;|api/@ohos.rpc.d.ts|
|新增API|NA|类名：IRemoteObject；<br>API声明：unregisterDeathRecipient(recipient: DeathRecipient, flags: number): void;<br>差异内容：unregisterDeathRecipient(recipient: DeathRecipient, flags: number): void;|api/@ohos.rpc.d.ts|
|新增API|NA|类名：IRemoteObject；<br>API声明：getInterfaceDescriptor(): string;<br>差异内容：getInterfaceDescriptor(): string;|api/@ohos.rpc.d.ts|
|新增API|NA|类名：IRemoteObject；<br>API声明：getDescriptor(): string;<br>差异内容：getDescriptor(): string;|api/@ohos.rpc.d.ts|
|新增API|NA|类名：IRemoteObject；<br>API声明：isObjectDead(): boolean;<br>差异内容：isObjectDead(): boolean;|api/@ohos.rpc.d.ts|
|新增API|NA|类名：rpc；<br>API声明：interface IRemoteBroker<br>差异内容：interface IRemoteBroker|api/@ohos.rpc.d.ts|
|新增API|NA|类名：IRemoteBroker；<br>API声明：asObject(): IRemoteObject;<br>差异内容：asObject(): IRemoteObject;|api/@ohos.rpc.d.ts|
|新增API|NA|类名：rpc；<br>API声明：interface DeathRecipient<br>差异内容：interface DeathRecipient|api/@ohos.rpc.d.ts|
|新增API|NA|类名：DeathRecipient；<br>API声明：onRemoteDied(): void;<br>差异内容：onRemoteDied(): void;|api/@ohos.rpc.d.ts|
|新增API|NA|类名：rpc；<br>API声明：class MessageOption<br>差异内容：class MessageOption|api/@ohos.rpc.d.ts|
|新增API|NA|类名：MessageOption；<br>API声明：TF_SYNC: number;<br>差异内容：TF_SYNC: number;|api/@ohos.rpc.d.ts|
|新增API|NA|类名：MessageOption；<br>API声明：TF_ASYNC: number;<br>差异内容：TF_ASYNC: number;|api/@ohos.rpc.d.ts|
|新增API|NA|类名：MessageOption；<br>API声明：TF_ACCEPT_FDS: number;<br>差异内容：TF_ACCEPT_FDS: number;|api/@ohos.rpc.d.ts|
|新增API|NA|类名：MessageOption；<br>API声明：TF_WAIT_TIME: number;<br>差异内容：TF_WAIT_TIME: number;|api/@ohos.rpc.d.ts|
|新增API|NA|类名：MessageOption；<br>API声明：getFlags(): number;<br>差异内容：getFlags(): number;|api/@ohos.rpc.d.ts|
|新增API|NA|类名：MessageOption；<br>API声明：setFlags(flags: number): void;<br>差异内容：setFlags(flags: number): void;|api/@ohos.rpc.d.ts|
|新增API|NA|类名：MessageOption；<br>API声明：isAsync(): boolean;<br>差异内容：isAsync(): boolean;|api/@ohos.rpc.d.ts|
|新增API|NA|类名：MessageOption；<br>API声明：setAsync(async: boolean): void;<br>差异内容：setAsync(async: boolean): void;|api/@ohos.rpc.d.ts|
|新增API|NA|类名：MessageOption；<br>API声明：getWaitTime(): number;<br>差异内容：getWaitTime(): number;|api/@ohos.rpc.d.ts|
|新增API|NA|类名：MessageOption；<br>API声明：setWaitTime(waitTime: number): void;<br>差异内容：setWaitTime(waitTime: number): void;|api/@ohos.rpc.d.ts|
|新增API|NA|类名：rpc；<br>API声明：class RemoteObject<br>差异内容：class RemoteObject|api/@ohos.rpc.d.ts|
|新增API|NA|类名：RemoteObject；<br>API声明：queryLocalInterface(descriptor: string): IRemoteBroker;<br>差异内容：queryLocalInterface(descriptor: string): IRemoteBroker;|api/@ohos.rpc.d.ts|
|新增API|NA|类名：RemoteObject；<br>API声明：getLocalInterface(descriptor: string): IRemoteBroker;<br>差异内容：getLocalInterface(descriptor: string): IRemoteBroker;|api/@ohos.rpc.d.ts|
|新增API|NA|类名：RemoteObject；<br>API声明：getInterfaceDescriptor(): string;<br>差异内容：getInterfaceDescriptor(): string;|api/@ohos.rpc.d.ts|
|新增API|NA|类名：RemoteObject；<br>API声明：getDescriptor(): string;<br>差异内容：getDescriptor(): string;|api/@ohos.rpc.d.ts|
|新增API|NA|类名：RemoteObject；<br>API声明：onRemoteMessageRequest(code: number, data: MessageSequence, reply: MessageSequence, options: MessageOption): boolean \| Promise\<boolean>;<br>差异内容：onRemoteMessageRequest(code: number, data: MessageSequence, reply: MessageSequence, options: MessageOption): boolean \| Promise\<boolean>;|api/@ohos.rpc.d.ts|
|新增API|NA|类名：RemoteObject；<br>API声明：onRemoteRequest(code: number, data: MessageParcel, reply: MessageParcel, options: MessageOption): boolean;<br>差异内容：onRemoteRequest(code: number, data: MessageParcel, reply: MessageParcel, options: MessageOption): boolean;|api/@ohos.rpc.d.ts|
|新增API|NA|类名：RemoteObject；<br>API声明：sendRequest(code: number, data: MessageParcel, reply: MessageParcel, options: MessageOption): boolean;<br>差异内容：sendRequest(code: number, data: MessageParcel, reply: MessageParcel, options: MessageOption): boolean;|api/@ohos.rpc.d.ts|
|新增API|NA|类名：RemoteObject；<br>API声明：sendRequest(code: number, data: MessageParcel, reply: MessageParcel, options: MessageOption): Promise\<SendRequestResult>;<br>差异内容：sendRequest(code: number, data: MessageParcel, reply: MessageParcel, options: MessageOption): Promise\<SendRequestResult>;|api/@ohos.rpc.d.ts|
|新增API|NA|类名：RemoteObject；<br>API声明：sendRequest(code: number, data: MessageParcel, reply: MessageParcel, options: MessageOption, callback: AsyncCallback\<SendRequestResult>): void;<br>差异内容：sendRequest(code: number, data: MessageParcel, reply: MessageParcel, options: MessageOption, callback: AsyncCallback\<SendRequestResult>): void;|api/@ohos.rpc.d.ts|
|新增API|NA|类名：RemoteObject；<br>API声明：sendMessageRequest(code: number, data: MessageSequence, reply: MessageSequence, options: MessageOption): Promise\<RequestResult>;<br>差异内容：sendMessageRequest(code: number, data: MessageSequence, reply: MessageSequence, options: MessageOption): Promise\<RequestResult>;|api/@ohos.rpc.d.ts|
|新增API|NA|类名：RemoteObject；<br>API声明：sendMessageRequest(code: number, data: MessageSequence, reply: MessageSequence, options: MessageOption, callback: AsyncCallback\<RequestResult>): void;<br>差异内容：sendMessageRequest(code: number, data: MessageSequence, reply: MessageSequence, options: MessageOption, callback: AsyncCallback\<RequestResult>): void;|api/@ohos.rpc.d.ts|
|新增API|NA|类名：RemoteObject；<br>API声明：getCallingPid(): number;<br>差异内容：getCallingPid(): number;|api/@ohos.rpc.d.ts|
|新增API|NA|类名：RemoteObject；<br>API声明：getCallingUid(): number;<br>差异内容：getCallingUid(): number;|api/@ohos.rpc.d.ts|
|新增API|NA|类名：RemoteObject；<br>API声明：attachLocalInterface(localInterface: IRemoteBroker, descriptor: string): void;<br>差异内容：attachLocalInterface(localInterface: IRemoteBroker, descriptor: string): void;|api/@ohos.rpc.d.ts|
|新增API|NA|类名：RemoteObject；<br>API声明：modifyLocalInterface(localInterface: IRemoteBroker, descriptor: string): void;<br>差异内容：modifyLocalInterface(localInterface: IRemoteBroker, descriptor: string): void;|api/@ohos.rpc.d.ts|
|新增API|NA|类名：rpc；<br>API声明：class RemoteProxy<br>差异内容：class RemoteProxy|api/@ohos.rpc.d.ts|
|新增API|NA|类名：RemoteProxy；<br>API声明：PING_TRANSACTION: number;<br>差异内容：PING_TRANSACTION: number;|api/@ohos.rpc.d.ts|
|新增API|NA|类名：RemoteProxy；<br>API声明：DUMP_TRANSACTION: number;<br>差异内容：DUMP_TRANSACTION: number;|api/@ohos.rpc.d.ts|
|新增API|NA|类名：RemoteProxy；<br>API声明：INTERFACE_TRANSACTION: number;<br>差异内容：INTERFACE_TRANSACTION: number;|api/@ohos.rpc.d.ts|
|新增API|NA|类名：RemoteProxy；<br>API声明：MIN_TRANSACTION_ID: number;<br>差异内容：MIN_TRANSACTION_ID: number;|api/@ohos.rpc.d.ts|
|新增API|NA|类名：RemoteProxy；<br>API声明：MAX_TRANSACTION_ID: number;<br>差异内容：MAX_TRANSACTION_ID: number;|api/@ohos.rpc.d.ts|
|新增API|NA|类名：RemoteProxy；<br>API声明：queryLocalInterface(interface: string): IRemoteBroker;<br>差异内容：queryLocalInterface(interface: string): IRemoteBroker;|api/@ohos.rpc.d.ts|
|新增API|NA|类名：RemoteProxy；<br>API声明：getLocalInterface(interface: string): IRemoteBroker;<br>差异内容：getLocalInterface(interface: string): IRemoteBroker;|api/@ohos.rpc.d.ts|
|新增API|NA|类名：RemoteProxy；<br>API声明：addDeathRecipient(recipient: DeathRecipient, flags: number): boolean;<br>差异内容：addDeathRecipient(recipient: DeathRecipient, flags: number): boolean;|api/@ohos.rpc.d.ts|
|新增API|NA|类名：RemoteProxy；<br>API声明：registerDeathRecipient(recipient: DeathRecipient, flags: number): void;<br>差异内容：registerDeathRecipient(recipient: DeathRecipient, flags: number): void;|api/@ohos.rpc.d.ts|
|新增API|NA|类名：RemoteProxy；<br>API声明：removeDeathRecipient(recipient: DeathRecipient, flags: number): boolean;<br>差异内容：removeDeathRecipient(recipient: DeathRecipient, flags: number): boolean;|api/@ohos.rpc.d.ts|
|新增API|NA|类名：RemoteProxy；<br>API声明：unregisterDeathRecipient(recipient: DeathRecipient, flags: number): void;<br>差异内容：unregisterDeathRecipient(recipient: DeathRecipient, flags: number): void;|api/@ohos.rpc.d.ts|
|新增API|NA|类名：RemoteProxy；<br>API声明：getInterfaceDescriptor(): string;<br>差异内容：getInterfaceDescriptor(): string;|api/@ohos.rpc.d.ts|
|新增API|NA|类名：RemoteProxy；<br>API声明：getDescriptor(): string;<br>差异内容：getDescriptor(): string;|api/@ohos.rpc.d.ts|
|新增API|NA|类名：RemoteProxy；<br>API声明：sendRequest(code: number, data: MessageParcel, reply: MessageParcel, options: MessageOption): boolean;<br>差异内容：sendRequest(code: number, data: MessageParcel, reply: MessageParcel, options: MessageOption): boolean;|api/@ohos.rpc.d.ts|
|新增API|NA|类名：RemoteProxy；<br>API声明：sendRequest(code: number, data: MessageParcel, reply: MessageParcel, options: MessageOption): Promise\<SendRequestResult>;<br>差异内容：sendRequest(code: number, data: MessageParcel, reply: MessageParcel, options: MessageOption): Promise\<SendRequestResult>;|api/@ohos.rpc.d.ts|
|新增API|NA|类名：RemoteProxy；<br>API声明：sendRequest(code: number, data: MessageParcel, reply: MessageParcel, options: MessageOption, callback: AsyncCallback\<SendRequestResult>): void;<br>差异内容：sendRequest(code: number, data: MessageParcel, reply: MessageParcel, options: MessageOption, callback: AsyncCallback\<SendRequestResult>): void;|api/@ohos.rpc.d.ts|
|新增API|NA|类名：RemoteProxy；<br>API声明：sendMessageRequest(code: number, data: MessageSequence, reply: MessageSequence, options: MessageOption): Promise\<RequestResult>;<br>差异内容：sendMessageRequest(code: number, data: MessageSequence, reply: MessageSequence, options: MessageOption): Promise\<RequestResult>;|api/@ohos.rpc.d.ts|
|新增API|NA|类名：RemoteProxy；<br>API声明：sendMessageRequest(code: number, data: MessageSequence, reply: MessageSequence, options: MessageOption, callback: AsyncCallback\<RequestResult>): void;<br>差异内容：sendMessageRequest(code: number, data: MessageSequence, reply: MessageSequence, options: MessageOption, callback: AsyncCallback\<RequestResult>): void;|api/@ohos.rpc.d.ts|
|新增API|NA|类名：RemoteProxy；<br>API声明：isObjectDead(): boolean;<br>差异内容：isObjectDead(): boolean;|api/@ohos.rpc.d.ts|
|新增API|NA|类名：rpc；<br>API声明：class IPCSkeleton<br>差异内容：class IPCSkeleton|api/@ohos.rpc.d.ts|
|新增API|NA|类名：IPCSkeleton；<br>API声明：static getContextObject(): IRemoteObject;<br>差异内容：static getContextObject(): IRemoteObject;|api/@ohos.rpc.d.ts|
|新增API|NA|类名：IPCSkeleton；<br>API声明：static getCallingPid(): number;<br>差异内容：static getCallingPid(): number;|api/@ohos.rpc.d.ts|
|新增API|NA|类名：IPCSkeleton；<br>API声明：static getCallingUid(): number;<br>差异内容：static getCallingUid(): number;|api/@ohos.rpc.d.ts|
|新增API|NA|类名：IPCSkeleton；<br>API声明：static getCallingTokenId(): number;<br>差异内容：static getCallingTokenId(): number;|api/@ohos.rpc.d.ts|
|新增API|NA|类名：IPCSkeleton；<br>API声明：static getCallingDeviceID(): string;<br>差异内容：static getCallingDeviceID(): string;|api/@ohos.rpc.d.ts|
|新增API|NA|类名：IPCSkeleton；<br>API声明：static getLocalDeviceID(): string;<br>差异内容：static getLocalDeviceID(): string;|api/@ohos.rpc.d.ts|
|新增API|NA|类名：IPCSkeleton；<br>API声明：static isLocalCalling(): boolean;<br>差异内容：static isLocalCalling(): boolean;|api/@ohos.rpc.d.ts|
|新增API|NA|类名：IPCSkeleton；<br>API声明：static flushCommands(object: IRemoteObject): number;<br>差异内容：static flushCommands(object: IRemoteObject): number;|api/@ohos.rpc.d.ts|
|新增API|NA|类名：IPCSkeleton；<br>API声明：static flushCmdBuffer(object: IRemoteObject): void;<br>差异内容：static flushCmdBuffer(object: IRemoteObject): void;|api/@ohos.rpc.d.ts|
|新增API|NA|类名：IPCSkeleton；<br>API声明：static resetCallingIdentity(): string;<br>差异内容：static resetCallingIdentity(): string;|api/@ohos.rpc.d.ts|
|新增API|NA|类名：IPCSkeleton；<br>API声明：static setCallingIdentity(identity: string): boolean;<br>差异内容：static setCallingIdentity(identity: string): boolean;|api/@ohos.rpc.d.ts|
|新增API|NA|类名：IPCSkeleton；<br>API声明：static restoreCallingIdentity(identity: string): void;<br>差异内容：static restoreCallingIdentity(identity: string): void;|api/@ohos.rpc.d.ts|
|新增API|NA|类名：rpc；<br>API声明：class Ashmem<br>差异内容：class Ashmem|api/@ohos.rpc.d.ts|
|新增API|NA|类名：Ashmem；<br>API声明：PROT_EXEC: number;<br>差异内容：PROT_EXEC: number;|api/@ohos.rpc.d.ts|
|新增API|NA|类名：Ashmem；<br>API声明：PROT_NONE: number;<br>差异内容：PROT_NONE: number;|api/@ohos.rpc.d.ts|
|新增API|NA|类名：Ashmem；<br>API声明：PROT_READ: number;<br>差异内容：PROT_READ: number;|api/@ohos.rpc.d.ts|
|新增API|NA|类名：Ashmem；<br>API声明：PROT_WRITE: number;<br>差异内容：PROT_WRITE: number;|api/@ohos.rpc.d.ts|
|新增API|NA|类名：Ashmem；<br>API声明：static createAshmem(name: string, size: number): Ashmem;<br>差异内容：static createAshmem(name: string, size: number): Ashmem;|api/@ohos.rpc.d.ts|
|新增API|NA|类名：Ashmem；<br>API声明：static create(name: string, size: number): Ashmem;<br>差异内容：static create(name: string, size: number): Ashmem;|api/@ohos.rpc.d.ts|
|新增API|NA|类名：Ashmem；<br>API声明：static create(ashmem: Ashmem): Ashmem;<br>差异内容：static create(ashmem: Ashmem): Ashmem;|api/@ohos.rpc.d.ts|
|新增API|NA|类名：Ashmem；<br>API声明：static createAshmemFromExisting(ashmem: Ashmem): Ashmem;<br>差异内容：static createAshmemFromExisting(ashmem: Ashmem): Ashmem;|api/@ohos.rpc.d.ts|
|新增API|NA|类名：Ashmem；<br>API声明：closeAshmem(): void;<br>差异内容：closeAshmem(): void;|api/@ohos.rpc.d.ts|
|新增API|NA|类名：Ashmem；<br>API声明：unmapAshmem(): void;<br>差异内容：unmapAshmem(): void;|api/@ohos.rpc.d.ts|
|新增API|NA|类名：Ashmem；<br>API声明：getAshmemSize(): number;<br>差异内容：getAshmemSize(): number;|api/@ohos.rpc.d.ts|
|新增API|NA|类名：Ashmem；<br>API声明：mapAshmem(mapType: number): boolean;<br>差异内容：mapAshmem(mapType: number): boolean;|api/@ohos.rpc.d.ts|
|新增API|NA|类名：Ashmem；<br>API声明：mapTypedAshmem(mapType: number): void;<br>差异内容：mapTypedAshmem(mapType: number): void;|api/@ohos.rpc.d.ts|
|新增API|NA|类名：Ashmem；<br>API声明：mapReadAndWriteAshmem(): boolean;<br>差异内容：mapReadAndWriteAshmem(): boolean;|api/@ohos.rpc.d.ts|
|新增API|NA|类名：Ashmem；<br>API声明：mapReadWriteAshmem(): void;<br>差异内容：mapReadWriteAshmem(): void;|api/@ohos.rpc.d.ts|
|新增API|NA|类名：Ashmem；<br>API声明：mapReadOnlyAshmem(): boolean;<br>差异内容：mapReadOnlyAshmem(): boolean;|api/@ohos.rpc.d.ts|
|新增API|NA|类名：Ashmem；<br>API声明：mapReadonlyAshmem(): void;<br>差异内容：mapReadonlyAshmem(): void;|api/@ohos.rpc.d.ts|
|新增API|NA|类名：Ashmem；<br>API声明：setProtection(protectionType: number): boolean;<br>差异内容：setProtection(protectionType: number): boolean;|api/@ohos.rpc.d.ts|
|新增API|NA|类名：Ashmem；<br>API声明：setProtectionType(protectionType: number): void;<br>差异内容：setProtectionType(protectionType: number): void;|api/@ohos.rpc.d.ts|
|新增API|NA|类名：Ashmem；<br>API声明：writeToAshmem(buf: number[], size: number, offset: number): boolean;<br>差异内容：writeToAshmem(buf: number[], size: number, offset: number): boolean;|api/@ohos.rpc.d.ts|
|新增API|NA|类名：Ashmem；<br>API声明：writeAshmem(buf: number[], size: number, offset: number): void;<br>差异内容：writeAshmem(buf: number[], size: number, offset: number): void;|api/@ohos.rpc.d.ts|
|新增API|NA|类名：Ashmem；<br>API声明：writeDataToAshmem(buf: ArrayBuffer, size: number, offset: number): void;<br>差异内容：writeDataToAshmem(buf: ArrayBuffer, size: number, offset: number): void;|api/@ohos.rpc.d.ts|
|新增API|NA|类名：Ashmem；<br>API声明：readFromAshmem(size: number, offset: number): number[];<br>差异内容：readFromAshmem(size: number, offset: number): number[];|api/@ohos.rpc.d.ts|
|新增API|NA|类名：Ashmem；<br>API声明：readAshmem(size: number, offset: number): number[];<br>差异内容：readAshmem(size: number, offset: number): number[];|api/@ohos.rpc.d.ts|
|新增API|NA|类名：Ashmem；<br>API声明：readDataFromAshmem(size: number, offset: number): ArrayBuffer;<br>差异内容：readDataFromAshmem(size: number, offset: number): ArrayBuffer;|api/@ohos.rpc.d.ts|
|成员由父类迁移至子类|类名：IRemoteObject；<br>API声明：queryLocalInterface(descriptor: string): IRemoteBroker;<br>差异内容：queryLocalInterface(descriptor: string): IRemoteBroker;|类名：RemoteObject；<br>API声明：queryLocalInterface(descriptor: string): IRemoteBroker;<br>差异内容：NA|api/@ohos.rpc.d.ts|
|成员由父类迁移至子类|类名：IRemoteObject；<br>API声明：getLocalInterface(descriptor: string): IRemoteBroker;<br>差异内容：getLocalInterface(descriptor: string): IRemoteBroker;|类名：RemoteObject；<br>API声明：getLocalInterface(descriptor: string): IRemoteBroker;<br>差异内容：NA|api/@ohos.rpc.d.ts|
|成员由父类迁移至子类|类名：IRemoteObject；<br>API声明：sendRequest(code: number, data: MessageParcel, reply: MessageParcel, options: MessageOption): boolean;<br>差异内容：sendRequest(code: number, data: MessageParcel, reply: MessageParcel, options: MessageOption): boolean;|类名：RemoteObject；<br>API声明：sendRequest(code: number, data: MessageParcel, reply: MessageParcel, options: MessageOption): boolean;<br>差异内容：NA|api/@ohos.rpc.d.ts|
|成员由父类迁移至子类|类名：IRemoteObject；<br>API声明：sendRequest(code: number, data: MessageParcel, reply: MessageParcel, options: MessageOption): Promise\<SendRequestResult>;<br>差异内容：sendRequest(code: number, data: MessageParcel, reply: MessageParcel, options: MessageOption): Promise\<SendRequestResult>;|类名：RemoteObject；<br>API声明：sendRequest(code: number, data: MessageParcel, reply: MessageParcel, options: MessageOption): boolean;<br>差异内容：NA|api/@ohos.rpc.d.ts|
|成员由父类迁移至子类|类名：IRemoteObject；<br>API声明：sendRequest(code: number, data: MessageParcel, reply: MessageParcel, options: MessageOption, callback: AsyncCallback\<SendRequestResult>): void;<br>差异内容：sendRequest(code: number, data: MessageParcel, reply: MessageParcel, options: MessageOption, callback: AsyncCallback\<SendRequestResult>): void;|类名：RemoteObject；<br>API声明：sendRequest(code: number, data: MessageParcel, reply: MessageParcel, options: MessageOption): boolean;<br>差异内容：NA|api/@ohos.rpc.d.ts|
|成员由父类迁移至子类|类名：IRemoteObject；<br>API声明：sendMessageRequest(code: number, data: MessageSequence, reply: MessageSequence, options: MessageOption): Promise\<RequestResult>;<br>差异内容：sendMessageRequest(code: number, data: MessageSequence, reply: MessageSequence, options: MessageOption): Promise\<RequestResult>;|类名：RemoteObject；<br>API声明：sendMessageRequest(code: number, data: MessageSequence, reply: MessageSequence, options: MessageOption): Promise\<RequestResult>;<br>差异内容：NA|api/@ohos.rpc.d.ts|
|成员由父类迁移至子类|类名：IRemoteObject；<br>API声明：sendMessageRequest(code: number, data: MessageSequence, reply: MessageSequence, options: MessageOption, callback: AsyncCallback\<RequestResult>): void;<br>差异内容：sendMessageRequest(code: number, data: MessageSequence, reply: MessageSequence, options: MessageOption, callback: AsyncCallback\<RequestResult>): void;|类名：RemoteObject；<br>API声明：sendMessageRequest(code: number, data: MessageSequence, reply: MessageSequence, options: MessageOption): Promise\<RequestResult>;<br>差异内容：NA|api/@ohos.rpc.d.ts|
|成员由父类迁移至子类|类名：IRemoteObject；<br>API声明：addDeathRecipient(recipient: DeathRecipient, flags: number): boolean;<br>差异内容：addDeathRecipient(recipient: DeathRecipient, flags: number): boolean;|类名：RemoteProxy；<br>API声明：addDeathRecipient(recipient: DeathRecipient, flags: number): boolean;<br>差异内容：NA|api/@ohos.rpc.d.ts|
|成员由父类迁移至子类|类名：IRemoteObject；<br>API声明：registerDeathRecipient(recipient: DeathRecipient, flags: number): void;<br>差异内容：registerDeathRecipient(recipient: DeathRecipient, flags: number): void;|类名：RemoteProxy；<br>API声明：registerDeathRecipient(recipient: DeathRecipient, flags: number): void;<br>差异内容：NA|api/@ohos.rpc.d.ts|
|成员由父类迁移至子类|类名：IRemoteObject；<br>API声明：removeDeathRecipient(recipient: DeathRecipient, flags: number): boolean;<br>差异内容：removeDeathRecipient(recipient: DeathRecipient, flags: number): boolean;|类名：RemoteProxy；<br>API声明：removeDeathRecipient(recipient: DeathRecipient, flags: number): boolean;<br>差异内容：NA|api/@ohos.rpc.d.ts|
|成员由父类迁移至子类|类名：IRemoteObject；<br>API声明：unregisterDeathRecipient(recipient: DeathRecipient, flags: number): void;<br>差异内容：unregisterDeathRecipient(recipient: DeathRecipient, flags: number): void;|类名：RemoteProxy；<br>API声明：unregisterDeathRecipient(recipient: DeathRecipient, flags: number): void;<br>差异内容：NA|api/@ohos.rpc.d.ts|
|成员由父类迁移至子类|类名：IRemoteObject；<br>API声明：getInterfaceDescriptor(): string;<br>差异内容：getInterfaceDescriptor(): string;|类名：RemoteObject；<br>API声明：getInterfaceDescriptor(): string;<br>差异内容：NA|api/@ohos.rpc.d.ts|
|成员由父类迁移至子类|类名：IRemoteObject；<br>API声明：getDescriptor(): string;<br>差异内容：getDescriptor(): string;|类名：RemoteObject；<br>API声明：getDescriptor(): string;<br>差异内容：NA|api/@ohos.rpc.d.ts|
|成员由父类迁移至子类|类名：IRemoteObject；<br>API声明：isObjectDead(): boolean;<br>差异内容：isObjectDead(): boolean;|类名：RemoteProxy；<br>API声明：isObjectDead(): boolean;<br>差异内容：NA|api/@ohos.rpc.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\@ohos.rpc.d.ts<br>差异内容：IPCKit|api/@ohos.rpc.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：kits\@kit.IPCKit.d.ts<br>差异内容：IPCKit|kits/@kit.IPCKit.d.ts|
