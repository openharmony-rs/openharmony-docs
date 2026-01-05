| Change Type | Old Version | New Version | d.ts File |
| ---- | ------ | ------ | -------- |
|New API|NA|Class name: global;<br>API declaration: declare namespace rpc<br>Differences: declare namespace rpc|api/@ohos.rpc.d.ts|
|New API|NA|Class name: rpc;<br>API declaration: enum ErrorCode<br>Differences: enum ErrorCode|api/@ohos.rpc.d.ts|
|New API|NA|Class name: ErrorCode;<br>API declaration: CHECK_PARAM_ERROR = 401<br>Differences: CHECK_PARAM_ERROR = 401|api/@ohos.rpc.d.ts|
|New API|NA|Class name: ErrorCode;<br>API declaration: OS_MMAP_ERROR = 1900001<br>Differences: OS_MMAP_ERROR = 1900001|api/@ohos.rpc.d.ts|
|New API|NA|Class name: ErrorCode;<br>API declaration: OS_IOCTL_ERROR = 1900002<br>Differences: OS_IOCTL_ERROR = 1900002|api/@ohos.rpc.d.ts|
|New API|NA|Class name: ErrorCode;<br>API declaration: WRITE_TO_ASHMEM_ERROR = 1900003<br>Differences: WRITE_TO_ASHMEM_ERROR = 1900003|api/@ohos.rpc.d.ts|
|New API|NA|Class name: ErrorCode;<br>API declaration: READ_FROM_ASHMEM_ERROR = 1900004<br>Differences: READ_FROM_ASHMEM_ERROR = 1900004|api/@ohos.rpc.d.ts|
|New API|NA|Class name: ErrorCode;<br>API declaration: ONLY_PROXY_OBJECT_PERMITTED_ERROR = 1900005<br>Differences: ONLY_PROXY_OBJECT_PERMITTED_ERROR = 1900005|api/@ohos.rpc.d.ts|
|New API|NA|Class name: ErrorCode;<br>API declaration: ONLY_REMOTE_OBJECT_PERMITTED_ERROR = 1900006<br>Differences: ONLY_REMOTE_OBJECT_PERMITTED_ERROR = 1900006|api/@ohos.rpc.d.ts|
|New API|NA|Class name: ErrorCode;<br>API declaration: COMMUNICATION_ERROR = 1900007<br>Differences: COMMUNICATION_ERROR = 1900007|api/@ohos.rpc.d.ts|
|New API|NA|Class name: ErrorCode;<br>API declaration: PROXY_OR_REMOTE_OBJECT_INVALID_ERROR = 1900008<br>Differences: PROXY_OR_REMOTE_OBJECT_INVALID_ERROR = 1900008|api/@ohos.rpc.d.ts|
|New API|NA|Class name: ErrorCode;<br>API declaration: WRITE_DATA_TO_MESSAGE_SEQUENCE_ERROR = 1900009<br>Differences: WRITE_DATA_TO_MESSAGE_SEQUENCE_ERROR = 1900009|api/@ohos.rpc.d.ts|
|New API|NA|Class name: ErrorCode;<br>API declaration: READ_DATA_FROM_MESSAGE_SEQUENCE_ERROR = 1900010<br>Differences: READ_DATA_FROM_MESSAGE_SEQUENCE_ERROR = 1900010|api/@ohos.rpc.d.ts|
|New API|NA|Class name: ErrorCode;<br>API declaration: PARCEL_MEMORY_ALLOC_ERROR = 1900011<br>Differences: PARCEL_MEMORY_ALLOC_ERROR = 1900011|api/@ohos.rpc.d.ts|
|New API|NA|Class name: ErrorCode;<br>API declaration: CALL_JS_METHOD_ERROR = 1900012<br>Differences: CALL_JS_METHOD_ERROR = 1900012|api/@ohos.rpc.d.ts|
|New API|NA|Class name: ErrorCode;<br>API declaration: OS_DUP_ERROR = 1900013<br>Differences: OS_DUP_ERROR = 1900013|api/@ohos.rpc.d.ts|
|New API|NA|Class name: rpc;<br>API declaration: class MessageParcel<br>Differences: class MessageParcel|api/@ohos.rpc.d.ts|
|New API|NA|Class name: MessageParcel;<br>API declaration: static create(): MessageParcel;<br>Differences: static create(): MessageParcel;|api/@ohos.rpc.d.ts|
|New API|NA|Class name: MessageParcel;<br>API declaration: reclaim(): void;<br>Differences: reclaim(): void;|api/@ohos.rpc.d.ts|
|New API|NA|Class name: MessageParcel;<br>API declaration: writeRemoteObject(object: IRemoteObject): boolean;<br>Differences: writeRemoteObject(object: IRemoteObject): boolean;|api/@ohos.rpc.d.ts|
|New API|NA|Class name: MessageParcel;<br>API declaration: readRemoteObject(): IRemoteObject;<br>Differences: readRemoteObject(): IRemoteObject;|api/@ohos.rpc.d.ts|
|New API|NA|Class name: MessageParcel;<br>API declaration: writeInterfaceToken(token: string): boolean;<br>Differences: writeInterfaceToken(token: string): boolean;|api/@ohos.rpc.d.ts|
|New API|NA|Class name: MessageParcel;<br>API declaration: readInterfaceToken(): string;<br>Differences: readInterfaceToken(): string;|api/@ohos.rpc.d.ts|
|New API|NA|Class name: MessageParcel;<br>API declaration: getSize(): number;<br>Differences: getSize(): number;|api/@ohos.rpc.d.ts|
|New API|NA|Class name: MessageParcel;<br>API declaration: getCapacity(): number;<br>Differences: getCapacity(): number;|api/@ohos.rpc.d.ts|
|New API|NA|Class name: MessageParcel;<br>API declaration: setSize(size: number): boolean;<br>Differences: setSize(size: number): boolean;|api/@ohos.rpc.d.ts|
|New API|NA|Class name: MessageParcel;<br>API declaration: setCapacity(size: number): boolean;<br>Differences: setCapacity(size: number): boolean;|api/@ohos.rpc.d.ts|
|New API|NA|Class name: MessageParcel;<br>API declaration: getWritableBytes(): number;<br>Differences: getWritableBytes(): number;|api/@ohos.rpc.d.ts|
|New API|NA|Class name: MessageParcel;<br>API declaration: getReadableBytes(): number;<br>Differences: getReadableBytes(): number;|api/@ohos.rpc.d.ts|
|New API|NA|Class name: MessageParcel;<br>API declaration: getReadPosition(): number;<br>Differences: getReadPosition(): number;|api/@ohos.rpc.d.ts|
|New API|NA|Class name: MessageParcel;<br>API declaration: getWritePosition(): number;<br>Differences: getWritePosition(): number;|api/@ohos.rpc.d.ts|
|New API|NA|Class name: MessageParcel;<br>API declaration: rewindRead(pos: number): boolean;<br>Differences: rewindRead(pos: number): boolean;|api/@ohos.rpc.d.ts|
|New API|NA|Class name: MessageParcel;<br>API declaration: rewindWrite(pos: number): boolean;<br>Differences: rewindWrite(pos: number): boolean;|api/@ohos.rpc.d.ts|
|New API|NA|Class name: MessageParcel;<br>API declaration: writeNoException(): void;<br>Differences: writeNoException(): void;|api/@ohos.rpc.d.ts|
|New API|NA|Class name: MessageParcel;<br>API declaration: readException(): void;<br>Differences: readException(): void;|api/@ohos.rpc.d.ts|
|New API|NA|Class name: MessageParcel;<br>API declaration: writeByte(val: number): boolean;<br>Differences: writeByte(val: number): boolean;|api/@ohos.rpc.d.ts|
|New API|NA|Class name: MessageParcel;<br>API declaration: writeShort(val: number): boolean;<br>Differences: writeShort(val: number): boolean;|api/@ohos.rpc.d.ts|
|New API|NA|Class name: MessageParcel;<br>API declaration: writeInt(val: number): boolean;<br>Differences: writeInt(val: number): boolean;|api/@ohos.rpc.d.ts|
|New API|NA|Class name: MessageParcel;<br>API declaration: writeLong(val: number): boolean;<br>Differences: writeLong(val: number): boolean;|api/@ohos.rpc.d.ts|
|New API|NA|Class name: MessageParcel;<br>API declaration: writeFloat(val: number): boolean;<br>Differences: writeFloat(val: number): boolean;|api/@ohos.rpc.d.ts|
|New API|NA|Class name: MessageParcel;<br>API declaration: writeDouble(val: number): boolean;<br>Differences: writeDouble(val: number): boolean;|api/@ohos.rpc.d.ts|
|New API|NA|Class name: MessageParcel;<br>API declaration: writeBoolean(val: boolean): boolean;<br>Differences: writeBoolean(val: boolean): boolean;|api/@ohos.rpc.d.ts|
|New API|NA|Class name: MessageParcel;<br>API declaration: writeChar(val: number): boolean;<br>Differences: writeChar(val: number): boolean;|api/@ohos.rpc.d.ts|
|New API|NA|Class name: MessageParcel;<br>API declaration: writeString(val: string): boolean;<br>Differences: writeString(val: string): boolean;|api/@ohos.rpc.d.ts|
|New API|NA|Class name: MessageParcel;<br>API declaration: writeSequenceable(val: Sequenceable): boolean;<br>Differences: writeSequenceable(val: Sequenceable): boolean;|api/@ohos.rpc.d.ts|
|New API|NA|Class name: MessageParcel;<br>API declaration: writeByteArray(byteArray: number[]): boolean;<br>Differences: writeByteArray(byteArray: number[]): boolean;|api/@ohos.rpc.d.ts|
|New API|NA|Class name: MessageParcel;<br>API declaration: writeShortArray(shortArray: number[]): boolean;<br>Differences: writeShortArray(shortArray: number[]): boolean;|api/@ohos.rpc.d.ts|
|New API|NA|Class name: MessageParcel;<br>API declaration: writeIntArray(intArray: number[]): boolean;<br>Differences: writeIntArray(intArray: number[]): boolean;|api/@ohos.rpc.d.ts|
|New API|NA|Class name: MessageParcel;<br>API declaration: writeLongArray(longArray: number[]): boolean;<br>Differences: writeLongArray(longArray: number[]): boolean;|api/@ohos.rpc.d.ts|
|New API|NA|Class name: MessageParcel;<br>API declaration: writeFloatArray(floatArray: number[]): boolean;<br>Differences: writeFloatArray(floatArray: number[]): boolean;|api/@ohos.rpc.d.ts|
|New API|NA|Class name: MessageParcel;<br>API declaration: writeDoubleArray(doubleArray: number[]): boolean;<br>Differences: writeDoubleArray(doubleArray: number[]): boolean;|api/@ohos.rpc.d.ts|
|New API|NA|Class name: MessageParcel;<br>API declaration: writeBooleanArray(booleanArray: boolean[]): boolean;<br>Differences: writeBooleanArray(booleanArray: boolean[]): boolean;|api/@ohos.rpc.d.ts|
|New API|NA|Class name: MessageParcel;<br>API declaration: writeCharArray(charArray: number[]): boolean;<br>Differences: writeCharArray(charArray: number[]): boolean;|api/@ohos.rpc.d.ts|
|New API|NA|Class name: MessageParcel;<br>API declaration: writeStringArray(stringArray: string[]): boolean;<br>Differences: writeStringArray(stringArray: string[]): boolean;|api/@ohos.rpc.d.ts|
|New API|NA|Class name: MessageParcel;<br>API declaration: writeSequenceableArray(sequenceableArray: Sequenceable[]): boolean;<br>Differences: writeSequenceableArray(sequenceableArray: Sequenceable[]): boolean;|api/@ohos.rpc.d.ts|
|New API|NA|Class name: MessageParcel;<br>API declaration: writeRemoteObjectArray(objectArray: IRemoteObject[]): boolean;<br>Differences: writeRemoteObjectArray(objectArray: IRemoteObject[]): boolean;|api/@ohos.rpc.d.ts|
|New API|NA|Class name: MessageParcel;<br>API declaration: readByte(): number;<br>Differences: readByte(): number;|api/@ohos.rpc.d.ts|
|New API|NA|Class name: MessageParcel;<br>API declaration: readShort(): number;<br>Differences: readShort(): number;|api/@ohos.rpc.d.ts|
|New API|NA|Class name: MessageParcel;<br>API declaration: readInt(): number;<br>Differences: readInt(): number;|api/@ohos.rpc.d.ts|
|New API|NA|Class name: MessageParcel;<br>API declaration: readLong(): number;<br>Differences: readLong(): number;|api/@ohos.rpc.d.ts|
|New API|NA|Class name: MessageParcel;<br>API declaration: readFloat(): number;<br>Differences: readFloat(): number;|api/@ohos.rpc.d.ts|
|New API|NA|Class name: MessageParcel;<br>API declaration: readDouble(): number;<br>Differences: readDouble(): number;|api/@ohos.rpc.d.ts|
|New API|NA|Class name: MessageParcel;<br>API declaration: readBoolean(): boolean;<br>Differences: readBoolean(): boolean;|api/@ohos.rpc.d.ts|
|New API|NA|Class name: MessageParcel;<br>API declaration: readChar(): number;<br>Differences: readChar(): number;|api/@ohos.rpc.d.ts|
|New API|NA|Class name: MessageParcel;<br>API declaration: readString(): string;<br>Differences: readString(): string;|api/@ohos.rpc.d.ts|
|New API|NA|Class name: MessageParcel;<br>API declaration: readSequenceable(dataIn: Sequenceable): boolean;<br>Differences: readSequenceable(dataIn: Sequenceable): boolean;|api/@ohos.rpc.d.ts|
|New API|NA|Class name: MessageParcel;<br>API declaration: readByteArray(dataIn: number[]): void;<br>Differences: readByteArray(dataIn: number[]): void;|api/@ohos.rpc.d.ts|
|New API|NA|Class name: MessageParcel;<br>API declaration: readByteArray(): number[];<br>Differences: readByteArray(): number[];|api/@ohos.rpc.d.ts|
|New API|NA|Class name: MessageParcel;<br>API declaration: readShortArray(dataIn: number[]): void;<br>Differences: readShortArray(dataIn: number[]): void;|api/@ohos.rpc.d.ts|
|New API|NA|Class name: MessageParcel;<br>API declaration: readShortArray(): number[];<br>Differences: readShortArray(): number[];|api/@ohos.rpc.d.ts|
|New API|NA|Class name: MessageParcel;<br>API declaration: readIntArray(dataIn: number[]): void;<br>Differences: readIntArray(dataIn: number[]): void;|api/@ohos.rpc.d.ts|
|New API|NA|Class name: MessageParcel;<br>API declaration: readIntArray(): number[];<br>Differences: readIntArray(): number[];|api/@ohos.rpc.d.ts|
|New API|NA|Class name: MessageParcel;<br>API declaration: readLongArray(dataIn: number[]): void;<br>Differences: readLongArray(dataIn: number[]): void;|api/@ohos.rpc.d.ts|
|New API|NA|Class name: MessageParcel;<br>API declaration: readLongArray(): number[];<br>Differences: readLongArray(): number[];|api/@ohos.rpc.d.ts|
|New API|NA|Class name: MessageParcel;<br>API declaration: readFloatArray(dataIn: number[]): void;<br>Differences: readFloatArray(dataIn: number[]): void;|api/@ohos.rpc.d.ts|
|New API|NA|Class name: MessageParcel;<br>API declaration: readFloatArray(): number[];<br>Differences: readFloatArray(): number[];|api/@ohos.rpc.d.ts|
|New API|NA|Class name: MessageParcel;<br>API declaration: readDoubleArray(dataIn: number[]): void;<br>Differences: readDoubleArray(dataIn: number[]): void;|api/@ohos.rpc.d.ts|
|New API|NA|Class name: MessageParcel;<br>API declaration: readDoubleArray(): number[];<br>Differences: readDoubleArray(): number[];|api/@ohos.rpc.d.ts|
|New API|NA|Class name: MessageParcel;<br>API declaration: readBooleanArray(dataIn: boolean[]): void;<br>Differences: readBooleanArray(dataIn: boolean[]): void;|api/@ohos.rpc.d.ts|
|New API|NA|Class name: MessageParcel;<br>API declaration: readBooleanArray(): boolean[];<br>Differences: readBooleanArray(): boolean[];|api/@ohos.rpc.d.ts|
|New API|NA|Class name: MessageParcel;<br>API declaration: readCharArray(dataIn: number[]): void;<br>Differences: readCharArray(dataIn: number[]): void;|api/@ohos.rpc.d.ts|
|New API|NA|Class name: MessageParcel;<br>API declaration: readCharArray(): number[];<br>Differences: readCharArray(): number[];|api/@ohos.rpc.d.ts|
|New API|NA|Class name: MessageParcel;<br>API declaration: readStringArray(dataIn: string[]): void;<br>Differences: readStringArray(dataIn: string[]): void;|api/@ohos.rpc.d.ts|
|New API|NA|Class name: MessageParcel;<br>API declaration: readStringArray(): string[];<br>Differences: readStringArray(): string[];|api/@ohos.rpc.d.ts|
|New API|NA|Class name: MessageParcel;<br>API declaration: readSequenceableArray(sequenceableArray: Sequenceable[]): void;<br>Differences: readSequenceableArray(sequenceableArray: Sequenceable[]): void;|api/@ohos.rpc.d.ts|
|New API|NA|Class name: MessageParcel;<br>API declaration: readRemoteObjectArray(objects: IRemoteObject[]): void;<br>Differences: readRemoteObjectArray(objects: IRemoteObject[]): void;|api/@ohos.rpc.d.ts|
|New API|NA|Class name: MessageParcel;<br>API declaration: readRemoteObjectArray(): IRemoteObject[];<br>Differences: readRemoteObjectArray(): IRemoteObject[];|api/@ohos.rpc.d.ts|
|New API|NA|Class name: MessageParcel;<br>API declaration: static closeFileDescriptor(fd: number): void;<br>Differences: static closeFileDescriptor(fd: number): void;|api/@ohos.rpc.d.ts|
|New API|NA|Class name: MessageParcel;<br>API declaration: static dupFileDescriptor(fd: number): number;<br>Differences: static dupFileDescriptor(fd: number): number;|api/@ohos.rpc.d.ts|
|New API|NA|Class name: MessageParcel;<br>API declaration: containFileDescriptors(): boolean;<br>Differences: containFileDescriptors(): boolean;|api/@ohos.rpc.d.ts|
|New API|NA|Class name: MessageParcel;<br>API declaration: writeFileDescriptor(fd: number): boolean;<br>Differences: writeFileDescriptor(fd: number): boolean;|api/@ohos.rpc.d.ts|
|New API|NA|Class name: MessageParcel;<br>API declaration: readFileDescriptor(): number;<br>Differences: readFileDescriptor(): number;|api/@ohos.rpc.d.ts|
|New API|NA|Class name: MessageParcel;<br>API declaration: writeAshmem(ashmem: Ashmem): boolean;<br>Differences: writeAshmem(ashmem: Ashmem): boolean;|api/@ohos.rpc.d.ts|
|New API|NA|Class name: MessageParcel;<br>API declaration: readAshmem(): Ashmem;<br>Differences: readAshmem(): Ashmem;|api/@ohos.rpc.d.ts|
|New API|NA|Class name: MessageParcel;<br>API declaration: getRawDataCapacity(): number;<br>Differences: getRawDataCapacity(): number;|api/@ohos.rpc.d.ts|
|New API|NA|Class name: MessageParcel;<br>API declaration: writeRawData(rawData: number[], size: number): boolean;<br>Differences: writeRawData(rawData: number[], size: number): boolean;|api/@ohos.rpc.d.ts|
|New API|NA|Class name: MessageParcel;<br>API declaration: readRawData(size: number): number[];<br>Differences: readRawData(size: number): number[];|api/@ohos.rpc.d.ts|
|New API|NA|Class name: rpc;<br>API declaration: class MessageSequence<br>Differences: class MessageSequence|api/@ohos.rpc.d.ts|
|New API|NA|Class name: MessageSequence;<br>API declaration: static create(): MessageSequence;<br>Differences: static create(): MessageSequence;|api/@ohos.rpc.d.ts|
|New API|NA|Class name: MessageSequence;<br>API declaration: reclaim(): void;<br>Differences: reclaim(): void;|api/@ohos.rpc.d.ts|
|New API|NA|Class name: MessageSequence;<br>API declaration: writeRemoteObject(object: IRemoteObject): void;<br>Differences: writeRemoteObject(object: IRemoteObject): void;|api/@ohos.rpc.d.ts|
|New API|NA|Class name: MessageSequence;<br>API declaration: readRemoteObject(): IRemoteObject;<br>Differences: readRemoteObject(): IRemoteObject;|api/@ohos.rpc.d.ts|
|New API|NA|Class name: MessageSequence;<br>API declaration: writeInterfaceToken(token: string): void;<br>Differences: writeInterfaceToken(token: string): void;|api/@ohos.rpc.d.ts|
|New API|NA|Class name: MessageSequence;<br>API declaration: readInterfaceToken(): string;<br>Differences: readInterfaceToken(): string;|api/@ohos.rpc.d.ts|
|New API|NA|Class name: MessageSequence;<br>API declaration: getSize(): number;<br>Differences: getSize(): number;|api/@ohos.rpc.d.ts|
|New API|NA|Class name: MessageSequence;<br>API declaration: getCapacity(): number;<br>Differences: getCapacity(): number;|api/@ohos.rpc.d.ts|
|New API|NA|Class name: MessageSequence;<br>API declaration: setSize(size: number): void;<br>Differences: setSize(size: number): void;|api/@ohos.rpc.d.ts|
|New API|NA|Class name: MessageSequence;<br>API declaration: setCapacity(size: number): void;<br>Differences: setCapacity(size: number): void;|api/@ohos.rpc.d.ts|
|New API|NA|Class name: MessageSequence;<br>API declaration: getWritableBytes(): number;<br>Differences: getWritableBytes(): number;|api/@ohos.rpc.d.ts|
|New API|NA|Class name: MessageSequence;<br>API declaration: getReadableBytes(): number;<br>Differences: getReadableBytes(): number;|api/@ohos.rpc.d.ts|
|New API|NA|Class name: MessageSequence;<br>API declaration: getReadPosition(): number;<br>Differences: getReadPosition(): number;|api/@ohos.rpc.d.ts|
|New API|NA|Class name: MessageSequence;<br>API declaration: getWritePosition(): number;<br>Differences: getWritePosition(): number;|api/@ohos.rpc.d.ts|
|New API|NA|Class name: MessageSequence;<br>API declaration: rewindRead(pos: number): void;<br>Differences: rewindRead(pos: number): void;|api/@ohos.rpc.d.ts|
|New API|NA|Class name: MessageSequence;<br>API declaration: rewindWrite(pos: number): void;<br>Differences: rewindWrite(pos: number): void;|api/@ohos.rpc.d.ts|
|New API|NA|Class name: MessageSequence;<br>API declaration: writeNoException(): void;<br>Differences: writeNoException(): void;|api/@ohos.rpc.d.ts|
|New API|NA|Class name: MessageSequence;<br>API declaration: readException(): void;<br>Differences: readException(): void;|api/@ohos.rpc.d.ts|
|New API|NA|Class name: MessageSequence;<br>API declaration: writeByte(val: number): void;<br>Differences: writeByte(val: number): void;|api/@ohos.rpc.d.ts|
|New API|NA|Class name: MessageSequence;<br>API declaration: writeShort(val: number): void;<br>Differences: writeShort(val: number): void;|api/@ohos.rpc.d.ts|
|New API|NA|Class name: MessageSequence;<br>API declaration: writeInt(val: number): void;<br>Differences: writeInt(val: number): void;|api/@ohos.rpc.d.ts|
|New API|NA|Class name: MessageSequence;<br>API declaration: writeLong(val: number): void;<br>Differences: writeLong(val: number): void;|api/@ohos.rpc.d.ts|
|New API|NA|Class name: MessageSequence;<br>API declaration: writeFloat(val: number): void;<br>Differences: writeFloat(val: number): void;|api/@ohos.rpc.d.ts|
|New API|NA|Class name: MessageSequence;<br>API declaration: writeDouble(val: number): void;<br>Differences: writeDouble(val: number): void;|api/@ohos.rpc.d.ts|
|New API|NA|Class name: MessageSequence;<br>API declaration: writeBoolean(val: boolean): void;<br>Differences: writeBoolean(val: boolean): void;|api/@ohos.rpc.d.ts|
|New API|NA|Class name: MessageSequence;<br>API declaration: writeChar(val: number): void;<br>Differences: writeChar(val: number): void;|api/@ohos.rpc.d.ts|
|New API|NA|Class name: MessageSequence;<br>API declaration: writeString(val: string): void;<br>Differences: writeString(val: string): void;|api/@ohos.rpc.d.ts|
|New API|NA|Class name: MessageSequence;<br>API declaration: writeParcelable(val: Parcelable): void;<br>Differences: writeParcelable(val: Parcelable): void;|api/@ohos.rpc.d.ts|
|New API|NA|Class name: MessageSequence;<br>API declaration: writeByteArray(byteArray: number[]): void;<br>Differences: writeByteArray(byteArray: number[]): void;|api/@ohos.rpc.d.ts|
|New API|NA|Class name: MessageSequence;<br>API declaration: writeShortArray(shortArray: number[]): void;<br>Differences: writeShortArray(shortArray: number[]): void;|api/@ohos.rpc.d.ts|
|New API|NA|Class name: MessageSequence;<br>API declaration: writeIntArray(intArray: number[]): void;<br>Differences: writeIntArray(intArray: number[]): void;|api/@ohos.rpc.d.ts|
|New API|NA|Class name: MessageSequence;<br>API declaration: writeLongArray(longArray: number[]): void;<br>Differences: writeLongArray(longArray: number[]): void;|api/@ohos.rpc.d.ts|
|New API|NA|Class name: MessageSequence;<br>API declaration: writeFloatArray(floatArray: number[]): void;<br>Differences: writeFloatArray(floatArray: number[]): void;|api/@ohos.rpc.d.ts|
|New API|NA|Class name: MessageSequence;<br>API declaration: writeDoubleArray(doubleArray: number[]): void;<br>Differences: writeDoubleArray(doubleArray: number[]): void;|api/@ohos.rpc.d.ts|
|New API|NA|Class name: MessageSequence;<br>API declaration: writeBooleanArray(booleanArray: boolean[]): void;<br>Differences: writeBooleanArray(booleanArray: boolean[]): void;|api/@ohos.rpc.d.ts|
|New API|NA|Class name: MessageSequence;<br>API declaration: writeCharArray(charArray: number[]): void;<br>Differences: writeCharArray(charArray: number[]): void;|api/@ohos.rpc.d.ts|
|New API|NA|Class name: MessageSequence;<br>API declaration: writeStringArray(stringArray: string[]): void;<br>Differences: writeStringArray(stringArray: string[]): void;|api/@ohos.rpc.d.ts|
|New API|NA|Class name: MessageSequence;<br>API declaration: writeParcelableArray(parcelableArray: Parcelable[]): void;<br>Differences: writeParcelableArray(parcelableArray: Parcelable[]): void;|api/@ohos.rpc.d.ts|
|New API|NA|Class name: MessageSequence;<br>API declaration: writeRemoteObjectArray(objectArray: IRemoteObject[]): void;<br>Differences: writeRemoteObjectArray(objectArray: IRemoteObject[]): void;|api/@ohos.rpc.d.ts|
|New API|NA|Class name: MessageSequence;<br>API declaration: readByte(): number;<br>Differences: readByte(): number;|api/@ohos.rpc.d.ts|
|New API|NA|Class name: MessageSequence;<br>API declaration: readShort(): number;<br>Differences: readShort(): number;|api/@ohos.rpc.d.ts|
|New API|NA|Class name: MessageSequence;<br>API declaration: readInt(): number;<br>Differences: readInt(): number;|api/@ohos.rpc.d.ts|
|New API|NA|Class name: MessageSequence;<br>API declaration: readLong(): number;<br>Differences: readLong(): number;|api/@ohos.rpc.d.ts|
|New API|NA|Class name: MessageSequence;<br>API declaration: readFloat(): number;<br>Differences: readFloat(): number;|api/@ohos.rpc.d.ts|
|New API|NA|Class name: MessageSequence;<br>API declaration: readDouble(): number;<br>Differences: readDouble(): number;|api/@ohos.rpc.d.ts|
|New API|NA|Class name: MessageSequence;<br>API declaration: readBoolean(): boolean;<br>Differences: readBoolean(): boolean;|api/@ohos.rpc.d.ts|
|New API|NA|Class name: MessageSequence;<br>API declaration: readChar(): number;<br>Differences: readChar(): number;|api/@ohos.rpc.d.ts|
|New API|NA|Class name: MessageSequence;<br>API declaration: readString(): string;<br>Differences: readString(): string;|api/@ohos.rpc.d.ts|
|New API|NA|Class name: MessageSequence;<br>API declaration: readParcelable(dataIn: Parcelable): void;<br>Differences: readParcelable(dataIn: Parcelable): void;|api/@ohos.rpc.d.ts|
|New API|NA|Class name: MessageSequence;<br>API declaration: readByteArray(dataIn: number[]): void;<br>Differences: readByteArray(dataIn: number[]): void;|api/@ohos.rpc.d.ts|
|New API|NA|Class name: MessageSequence;<br>API declaration: readByteArray(): number[];<br>Differences: readByteArray(): number[];|api/@ohos.rpc.d.ts|
|New API|NA|Class name: MessageSequence;<br>API declaration: readShortArray(dataIn: number[]): void;<br>Differences: readShortArray(dataIn: number[]): void;|api/@ohos.rpc.d.ts|
|New API|NA|Class name: MessageSequence;<br>API declaration: readShortArray(): number[];<br>Differences: readShortArray(): number[];|api/@ohos.rpc.d.ts|
|New API|NA|Class name: MessageSequence;<br>API declaration: readIntArray(dataIn: number[]): void;<br>Differences: readIntArray(dataIn: number[]): void;|api/@ohos.rpc.d.ts|
|New API|NA|Class name: MessageSequence;<br>API declaration: readIntArray(): number[];<br>Differences: readIntArray(): number[];|api/@ohos.rpc.d.ts|
|New API|NA|Class name: MessageSequence;<br>API declaration: readLongArray(dataIn: number[]): void;<br>Differences: readLongArray(dataIn: number[]): void;|api/@ohos.rpc.d.ts|
|New API|NA|Class name: MessageSequence;<br>API declaration: readLongArray(): number[];<br>Differences: readLongArray(): number[];|api/@ohos.rpc.d.ts|
|New API|NA|Class name: MessageSequence;<br>API declaration: readFloatArray(dataIn: number[]): void;<br>Differences: readFloatArray(dataIn: number[]): void;|api/@ohos.rpc.d.ts|
|New API|NA|Class name: MessageSequence;<br>API declaration: readFloatArray(): number[];<br>Differences: readFloatArray(): number[];|api/@ohos.rpc.d.ts|
|New API|NA|Class name: MessageSequence;<br>API declaration: readDoubleArray(dataIn: number[]): void;<br>Differences: readDoubleArray(dataIn: number[]): void;|api/@ohos.rpc.d.ts|
|New API|NA|Class name: MessageSequence;<br>API declaration: readDoubleArray(): number[];<br>Differences: readDoubleArray(): number[];|api/@ohos.rpc.d.ts|
|New API|NA|Class name: MessageSequence;<br>API declaration: readBooleanArray(dataIn: boolean[]): void;<br>Differences: readBooleanArray(dataIn: boolean[]): void;|api/@ohos.rpc.d.ts|
|New API|NA|Class name: MessageSequence;<br>API declaration: readBooleanArray(): boolean[];<br>Differences: readBooleanArray(): boolean[];|api/@ohos.rpc.d.ts|
|New API|NA|Class name: MessageSequence;<br>API declaration: readCharArray(dataIn: number[]): void;<br>Differences: readCharArray(dataIn: number[]): void;|api/@ohos.rpc.d.ts|
|New API|NA|Class name: MessageSequence;<br>API declaration: readCharArray(): number[];<br>Differences: readCharArray(): number[];|api/@ohos.rpc.d.ts|
|New API|NA|Class name: MessageSequence;<br>API declaration: readStringArray(dataIn: string[]): void;<br>Differences: readStringArray(dataIn: string[]): void;|api/@ohos.rpc.d.ts|
|New API|NA|Class name: MessageSequence;<br>API declaration: readStringArray(): string[];<br>Differences: readStringArray(): string[];|api/@ohos.rpc.d.ts|
|New API|NA|Class name: MessageSequence;<br>API declaration: readParcelableArray(parcelableArray: Parcelable[]): void;<br>Differences: readParcelableArray(parcelableArray: Parcelable[]): void;|api/@ohos.rpc.d.ts|
|New API|NA|Class name: MessageSequence;<br>API declaration: readRemoteObjectArray(objects: IRemoteObject[]): void;<br>Differences: readRemoteObjectArray(objects: IRemoteObject[]): void;|api/@ohos.rpc.d.ts|
|New API|NA|Class name: MessageSequence;<br>API declaration: readRemoteObjectArray(): IRemoteObject[];<br>Differences: readRemoteObjectArray(): IRemoteObject[];|api/@ohos.rpc.d.ts|
|New API|NA|Class name: MessageSequence;<br>API declaration: static closeFileDescriptor(fd: number): void;<br>Differences: static closeFileDescriptor(fd: number): void;|api/@ohos.rpc.d.ts|
|New API|NA|Class name: MessageSequence;<br>API declaration: static dupFileDescriptor(fd: number): number;<br>Differences: static dupFileDescriptor(fd: number): number;|api/@ohos.rpc.d.ts|
|New API|NA|Class name: MessageSequence;<br>API declaration: containFileDescriptors(): boolean;<br>Differences: containFileDescriptors(): boolean;|api/@ohos.rpc.d.ts|
|New API|NA|Class name: MessageSequence;<br>API declaration: writeFileDescriptor(fd: number): void;<br>Differences: writeFileDescriptor(fd: number): void;|api/@ohos.rpc.d.ts|
|New API|NA|Class name: MessageSequence;<br>API declaration: readFileDescriptor(): number;<br>Differences: readFileDescriptor(): number;|api/@ohos.rpc.d.ts|
|New API|NA|Class name: MessageSequence;<br>API declaration: writeAshmem(ashmem: Ashmem): void;<br>Differences: writeAshmem(ashmem: Ashmem): void;|api/@ohos.rpc.d.ts|
|New API|NA|Class name: MessageSequence;<br>API declaration: readAshmem(): Ashmem;<br>Differences: readAshmem(): Ashmem;|api/@ohos.rpc.d.ts|
|New API|NA|Class name: MessageSequence;<br>API declaration: getRawDataCapacity(): number;<br>Differences: getRawDataCapacity(): number;|api/@ohos.rpc.d.ts|
|New API|NA|Class name: MessageSequence;<br>API declaration: writeRawData(rawData: number[], size: number): void;<br>Differences: writeRawData(rawData: number[], size: number): void;|api/@ohos.rpc.d.ts|
|New API|NA|Class name: MessageSequence;<br>API declaration: writeRawDataBuffer(rawData: ArrayBuffer, size: number): void;<br>Differences: writeRawDataBuffer(rawData: ArrayBuffer, size: number): void;|api/@ohos.rpc.d.ts|
|New API|NA|Class name: MessageSequence;<br>API declaration: readRawData(size: number): number[];<br>Differences: readRawData(size: number): number[];|api/@ohos.rpc.d.ts|
|New API|NA|Class name: MessageSequence;<br>API declaration: readRawDataBuffer(size: number): ArrayBuffer;<br>Differences: readRawDataBuffer(size: number): ArrayBuffer;|api/@ohos.rpc.d.ts|
|New API|NA|Class name: rpc;<br>API declaration: interface Sequenceable<br>Differences: interface Sequenceable|api/@ohos.rpc.d.ts|
|New API|NA|Class name: Sequenceable;<br>API declaration: marshalling(dataOut: MessageParcel): boolean;<br>Differences: marshalling(dataOut: MessageParcel): boolean;|api/@ohos.rpc.d.ts|
|New API|NA|Class name: Sequenceable;<br>API declaration: unmarshalling(dataIn: MessageParcel): boolean;<br>Differences: unmarshalling(dataIn: MessageParcel): boolean;|api/@ohos.rpc.d.ts|
|New API|NA|Class name: rpc;<br>API declaration: interface Parcelable<br>Differences: interface Parcelable|api/@ohos.rpc.d.ts|
|New API|NA|Class name: Parcelable;<br>API declaration: marshalling(dataOut: MessageSequence): boolean;<br>Differences: marshalling(dataOut: MessageSequence): boolean;|api/@ohos.rpc.d.ts|
|New API|NA|Class name: Parcelable;<br>API declaration: unmarshalling(dataIn: MessageSequence): boolean;<br>Differences: unmarshalling(dataIn: MessageSequence): boolean;|api/@ohos.rpc.d.ts|
|New API|NA|Class name: rpc;<br>API declaration: interface SendRequestResult<br>Differences: interface SendRequestResult|api/@ohos.rpc.d.ts|
|New API|NA|Class name: SendRequestResult;<br>API declaration: errCode: number;<br>Differences: errCode: number;|api/@ohos.rpc.d.ts|
|New API|NA|Class name: SendRequestResult;<br>API declaration: code: number;<br>Differences: code: number;|api/@ohos.rpc.d.ts|
|New API|NA|Class name: SendRequestResult;<br>API declaration: data: MessageParcel;<br>Differences: data: MessageParcel;|api/@ohos.rpc.d.ts|
|New API|NA|Class name: SendRequestResult;<br>API declaration: reply: MessageParcel;<br>Differences: reply: MessageParcel;|api/@ohos.rpc.d.ts|
|New API|NA|Class name: rpc;<br>API declaration: interface RequestResult<br>Differences: interface RequestResult|api/@ohos.rpc.d.ts|
|New API|NA|Class name: RequestResult;<br>API declaration: errCode: number;<br>Differences: errCode: number;|api/@ohos.rpc.d.ts|
|New API|NA|Class name: RequestResult;<br>API declaration: code: number;<br>Differences: code: number;|api/@ohos.rpc.d.ts|
|New API|NA|Class name: RequestResult;<br>API declaration: data: MessageSequence;<br>Differences: data: MessageSequence;|api/@ohos.rpc.d.ts|
|New API|NA|Class name: RequestResult;<br>API declaration: reply: MessageSequence;<br>Differences: reply: MessageSequence;|api/@ohos.rpc.d.ts|
|New API|NA|Class name: rpc;<br>API declaration: abstract class IRemoteObject<br>Differences: abstract class IRemoteObject|api/@ohos.rpc.d.ts|
|New API|NA|Class name: IRemoteObject;<br>API declaration: queryLocalInterface(descriptor: string): IRemoteBroker;<br>Differences: queryLocalInterface(descriptor: string): IRemoteBroker;|api/@ohos.rpc.d.ts|
|New API|NA|Class name: IRemoteObject;<br>API declaration: getLocalInterface(descriptor: string): IRemoteBroker;<br>Differences: getLocalInterface(descriptor: string): IRemoteBroker;|api/@ohos.rpc.d.ts|
|New API|NA|Class name: IRemoteObject;<br>API declaration: sendRequest(code: number, data: MessageParcel, reply: MessageParcel, options: MessageOption): boolean;<br>Differences: sendRequest(code: number, data: MessageParcel, reply: MessageParcel, options: MessageOption): boolean;|api/@ohos.rpc.d.ts|
|New API|NA|Class name: IRemoteObject;<br>API declaration: sendRequest(code: number, data: MessageParcel, reply: MessageParcel, options: MessageOption): Promise\<SendRequestResult>;<br>Differences: sendRequest(code: number, data: MessageParcel, reply: MessageParcel, options: MessageOption): Promise\<SendRequestResult>;|api/@ohos.rpc.d.ts|
|New API|NA|Class name: IRemoteObject;<br>API declaration: sendRequest(code: number, data: MessageParcel, reply: MessageParcel, options: MessageOption, callback: AsyncCallback\<SendRequestResult>): void;<br>Differences: sendRequest(code: number, data: MessageParcel, reply: MessageParcel, options: MessageOption, callback: AsyncCallback\<SendRequestResult>): void;|api/@ohos.rpc.d.ts|
|New API|NA|Class name: IRemoteObject;<br>API declaration: sendMessageRequest(code: number, data: MessageSequence, reply: MessageSequence, options: MessageOption): Promise\<RequestResult>;<br>Differences: sendMessageRequest(code: number, data: MessageSequence, reply: MessageSequence, options: MessageOption): Promise\<RequestResult>;|api/@ohos.rpc.d.ts|
|New API|NA|Class name: IRemoteObject;<br>API declaration: sendMessageRequest(code: number, data: MessageSequence, reply: MessageSequence, options: MessageOption, callback: AsyncCallback\<RequestResult>): void;<br>Differences: sendMessageRequest(code: number, data: MessageSequence, reply: MessageSequence, options: MessageOption, callback: AsyncCallback\<RequestResult>): void;|api/@ohos.rpc.d.ts|
|New API|NA|Class name: IRemoteObject;<br>API declaration: addDeathRecipient(recipient: DeathRecipient, flags: number): boolean;<br>Differences: addDeathRecipient(recipient: DeathRecipient, flags: number): boolean;|api/@ohos.rpc.d.ts|
|New API|NA|Class name: IRemoteObject;<br>API declaration: registerDeathRecipient(recipient: DeathRecipient, flags: number): void;<br>Differences: registerDeathRecipient(recipient: DeathRecipient, flags: number): void;|api/@ohos.rpc.d.ts|
|New API|NA|Class name: IRemoteObject;<br>API declaration: removeDeathRecipient(recipient: DeathRecipient, flags: number): boolean;<br>Differences: removeDeathRecipient(recipient: DeathRecipient, flags: number): boolean;|api/@ohos.rpc.d.ts|
|New API|NA|Class name: IRemoteObject;<br>API declaration: unregisterDeathRecipient(recipient: DeathRecipient, flags: number): void;<br>Differences: unregisterDeathRecipient(recipient: DeathRecipient, flags: number): void;|api/@ohos.rpc.d.ts|
|New API|NA|Class name: IRemoteObject;<br>API declaration: getInterfaceDescriptor(): string;<br>Differences: getInterfaceDescriptor(): string;|api/@ohos.rpc.d.ts|
|New API|NA|Class name: IRemoteObject;<br>API declaration: getDescriptor(): string;<br>Differences: getDescriptor(): string;|api/@ohos.rpc.d.ts|
|New API|NA|Class name: IRemoteObject;<br>API declaration: isObjectDead(): boolean;<br>Differences: isObjectDead(): boolean;|api/@ohos.rpc.d.ts|
|New API|NA|Class name: rpc;<br>API declaration: interface IRemoteBroker<br>Differences: interface IRemoteBroker|api/@ohos.rpc.d.ts|
|New API|NA|Class name: IRemoteBroker;<br>API declaration: asObject(): IRemoteObject;<br>Differences: asObject(): IRemoteObject;|api/@ohos.rpc.d.ts|
|New API|NA|Class name: rpc;<br>API declaration: interface DeathRecipient<br>Differences: interface DeathRecipient|api/@ohos.rpc.d.ts|
|New API|NA|Class name: DeathRecipient;<br>API declaration: onRemoteDied(): void;<br>Differences: onRemoteDied(): void;|api/@ohos.rpc.d.ts|
|New API|NA|Class name: rpc;<br>API declaration: class MessageOption<br>Differences: class MessageOption|api/@ohos.rpc.d.ts|
|New API|NA|Class name: MessageOption;<br>API declaration: TF_SYNC: number;<br>Differences: TF_SYNC: number;|api/@ohos.rpc.d.ts|
|New API|NA|Class name: MessageOption;<br>API declaration: TF_ASYNC: number;<br>Differences: TF_ASYNC: number;|api/@ohos.rpc.d.ts|
|New API|NA|Class name: MessageOption;<br>API declaration: TF_ACCEPT_FDS: number;<br>Differences: TF_ACCEPT_FDS: number;|api/@ohos.rpc.d.ts|
|New API|NA|Class name: MessageOption;<br>API declaration: TF_WAIT_TIME: number;<br>Differences: TF_WAIT_TIME: number;|api/@ohos.rpc.d.ts|
|New API|NA|Class name: MessageOption;<br>API declaration: getFlags(): number;<br>Differences: getFlags(): number;|api/@ohos.rpc.d.ts|
|New API|NA|Class name: MessageOption;<br>API declaration: setFlags(flags: number): void;<br>Differences: setFlags(flags: number): void;|api/@ohos.rpc.d.ts|
|New API|NA|Class name: MessageOption;<br>API declaration: isAsync(): boolean;<br>Differences: isAsync(): boolean;|api/@ohos.rpc.d.ts|
|New API|NA|Class name: MessageOption;<br>API declaration: setAsync(async: boolean): void;<br>Differences: setAsync(async: boolean): void;|api/@ohos.rpc.d.ts|
|New API|NA|Class name: MessageOption;<br>API declaration: getWaitTime(): number;<br>Differences: getWaitTime(): number;|api/@ohos.rpc.d.ts|
|New API|NA|Class name: MessageOption;<br>API declaration: setWaitTime(waitTime: number): void;<br>Differences: setWaitTime(waitTime: number): void;|api/@ohos.rpc.d.ts|
|New API|NA|Class name: rpc;<br>API declaration: class RemoteObject<br>Differences: class RemoteObject|api/@ohos.rpc.d.ts|
|New API|NA|Class name: RemoteObject;<br>API declaration: queryLocalInterface(descriptor: string): IRemoteBroker;<br>Differences: queryLocalInterface(descriptor: string): IRemoteBroker;|api/@ohos.rpc.d.ts|
|New API|NA|Class name: RemoteObject;<br>API declaration: getLocalInterface(descriptor: string): IRemoteBroker;<br>Differences: getLocalInterface(descriptor: string): IRemoteBroker;|api/@ohos.rpc.d.ts|
|New API|NA|Class name: RemoteObject;<br>API declaration: getInterfaceDescriptor(): string;<br>Differences: getInterfaceDescriptor(): string;|api/@ohos.rpc.d.ts|
|New API|NA|Class name: RemoteObject;<br>API declaration: getDescriptor(): string;<br>Differences: getDescriptor(): string;|api/@ohos.rpc.d.ts|
|New API|NA|Class name: RemoteObject;<br>API declaration: onRemoteMessageRequest(code: number, data: MessageSequence, reply: MessageSequence, options: MessageOption): boolean \| Promise\<boolean>;<br>Differences: onRemoteMessageRequest(code: number, data: MessageSequence, reply: MessageSequence, options: MessageOption): boolean \| Promise\<boolean>;|api/@ohos.rpc.d.ts|
|New API|NA|Class name: RemoteObject;<br>API declaration: onRemoteRequest(code: number, data: MessageParcel, reply: MessageParcel, options: MessageOption): boolean;<br>Differences: onRemoteRequest(code: number, data: MessageParcel, reply: MessageParcel, options: MessageOption): boolean;|api/@ohos.rpc.d.ts|
|New API|NA|Class name: RemoteObject;<br>API declaration: sendRequest(code: number, data: MessageParcel, reply: MessageParcel, options: MessageOption): boolean;<br>Differences: sendRequest(code: number, data: MessageParcel, reply: MessageParcel, options: MessageOption): boolean;|api/@ohos.rpc.d.ts|
|New API|NA|Class name: RemoteObject;<br>API declaration: sendRequest(code: number, data: MessageParcel, reply: MessageParcel, options: MessageOption): Promise\<SendRequestResult>;<br>Differences: sendRequest(code: number, data: MessageParcel, reply: MessageParcel, options: MessageOption): Promise\<SendRequestResult>;|api/@ohos.rpc.d.ts|
|New API|NA|Class name: RemoteObject;<br>API declaration: sendRequest(code: number, data: MessageParcel, reply: MessageParcel, options: MessageOption, callback: AsyncCallback\<SendRequestResult>): void;<br>Differences: sendRequest(code: number, data: MessageParcel, reply: MessageParcel, options: MessageOption, callback: AsyncCallback\<SendRequestResult>): void;|api/@ohos.rpc.d.ts|
|New API|NA|Class name: RemoteObject;<br>API declaration: sendMessageRequest(code: number, data: MessageSequence, reply: MessageSequence, options: MessageOption): Promise\<RequestResult>;<br>Differences: sendMessageRequest(code: number, data: MessageSequence, reply: MessageSequence, options: MessageOption): Promise\<RequestResult>;|api/@ohos.rpc.d.ts|
|New API|NA|Class name: RemoteObject;<br>API declaration: sendMessageRequest(code: number, data: MessageSequence, reply: MessageSequence, options: MessageOption, callback: AsyncCallback\<RequestResult>): void;<br>Differences: sendMessageRequest(code: number, data: MessageSequence, reply: MessageSequence, options: MessageOption, callback: AsyncCallback\<RequestResult>): void;|api/@ohos.rpc.d.ts|
|New API|NA|Class name: RemoteObject;<br>API declaration: getCallingPid(): number;<br>Differences: getCallingPid(): number;|api/@ohos.rpc.d.ts|
|New API|NA|Class name: RemoteObject;<br>API declaration: getCallingUid(): number;<br>Differences: getCallingUid(): number;|api/@ohos.rpc.d.ts|
|New API|NA|Class name: RemoteObject;<br>API declaration: attachLocalInterface(localInterface: IRemoteBroker, descriptor: string): void;<br>Differences: attachLocalInterface(localInterface: IRemoteBroker, descriptor: string): void;|api/@ohos.rpc.d.ts|
|New API|NA|Class name: RemoteObject;<br>API declaration: modifyLocalInterface(localInterface: IRemoteBroker, descriptor: string): void;<br>Differences: modifyLocalInterface(localInterface: IRemoteBroker, descriptor: string): void;|api/@ohos.rpc.d.ts|
|New API|NA|Class name: rpc;<br>API declaration: class RemoteProxy<br>Differences: class RemoteProxy|api/@ohos.rpc.d.ts|
|New API|NA|Class name: RemoteProxy;<br>API declaration: PING_TRANSACTION: number;<br>Differences: PING_TRANSACTION: number;|api/@ohos.rpc.d.ts|
|New API|NA|Class name: RemoteProxy;<br>API declaration: DUMP_TRANSACTION: number;<br>Differences: DUMP_TRANSACTION: number;|api/@ohos.rpc.d.ts|
|New API|NA|Class name: RemoteProxy;<br>API declaration: INTERFACE_TRANSACTION: number;<br>Differences: INTERFACE_TRANSACTION: number;|api/@ohos.rpc.d.ts|
|New API|NA|Class name: RemoteProxy;<br>API declaration: MIN_TRANSACTION_ID: number;<br>Differences: MIN_TRANSACTION_ID: number;|api/@ohos.rpc.d.ts|
|New API|NA|Class name: RemoteProxy;<br>API declaration: MAX_TRANSACTION_ID: number;<br>Differences: MAX_TRANSACTION_ID: number;|api/@ohos.rpc.d.ts|
|New API|NA|Class name: RemoteProxy;<br>API declaration: queryLocalInterface(interface: string): IRemoteBroker;<br>Differences: queryLocalInterface(interface: string): IRemoteBroker;|api/@ohos.rpc.d.ts|
|New API|NA|Class name: RemoteProxy;<br>API declaration: getLocalInterface(interface: string): IRemoteBroker;<br>Differences: getLocalInterface(interface: string): IRemoteBroker;|api/@ohos.rpc.d.ts|
|New API|NA|Class name: RemoteProxy;<br>API declaration: addDeathRecipient(recipient: DeathRecipient, flags: number): boolean;<br>Differences: addDeathRecipient(recipient: DeathRecipient, flags: number): boolean;|api/@ohos.rpc.d.ts|
|New API|NA|Class name: RemoteProxy;<br>API declaration: registerDeathRecipient(recipient: DeathRecipient, flags: number): void;<br>Differences: registerDeathRecipient(recipient: DeathRecipient, flags: number): void;|api/@ohos.rpc.d.ts|
|New API|NA|Class name: RemoteProxy;<br>API declaration: removeDeathRecipient(recipient: DeathRecipient, flags: number): boolean;<br>Differences: removeDeathRecipient(recipient: DeathRecipient, flags: number): boolean;|api/@ohos.rpc.d.ts|
|New API|NA|Class name: RemoteProxy;<br>API declaration: unregisterDeathRecipient(recipient: DeathRecipient, flags: number): void;<br>Differences: unregisterDeathRecipient(recipient: DeathRecipient, flags: number): void;|api/@ohos.rpc.d.ts|
|New API|NA|Class name: RemoteProxy;<br>API declaration: getInterfaceDescriptor(): string;<br>Differences: getInterfaceDescriptor(): string;|api/@ohos.rpc.d.ts|
|New API|NA|Class name: RemoteProxy;<br>API declaration: getDescriptor(): string;<br>Differences: getDescriptor(): string;|api/@ohos.rpc.d.ts|
|New API|NA|Class name: RemoteProxy;<br>API declaration: sendRequest(code: number, data: MessageParcel, reply: MessageParcel, options: MessageOption): boolean;<br>Differences: sendRequest(code: number, data: MessageParcel, reply: MessageParcel, options: MessageOption): boolean;|api/@ohos.rpc.d.ts|
|New API|NA|Class name: RemoteProxy;<br>API declaration: sendRequest(code: number, data: MessageParcel, reply: MessageParcel, options: MessageOption): Promise\<SendRequestResult>;<br>Differences: sendRequest(code: number, data: MessageParcel, reply: MessageParcel, options: MessageOption): Promise\<SendRequestResult>;|api/@ohos.rpc.d.ts|
|New API|NA|Class name: RemoteProxy;<br>API declaration: sendRequest(code: number, data: MessageParcel, reply: MessageParcel, options: MessageOption, callback: AsyncCallback\<SendRequestResult>): void;<br>Differences: sendRequest(code: number, data: MessageParcel, reply: MessageParcel, options: MessageOption, callback: AsyncCallback\<SendRequestResult>): void;|api/@ohos.rpc.d.ts|
|New API|NA|Class name: RemoteProxy;<br>API declaration: sendMessageRequest(code: number, data: MessageSequence, reply: MessageSequence, options: MessageOption): Promise\<RequestResult>;<br>Differences: sendMessageRequest(code: number, data: MessageSequence, reply: MessageSequence, options: MessageOption): Promise\<RequestResult>;|api/@ohos.rpc.d.ts|
|New API|NA|Class name: RemoteProxy;<br>API declaration: sendMessageRequest(code: number, data: MessageSequence, reply: MessageSequence, options: MessageOption, callback: AsyncCallback\<RequestResult>): void;<br>Differences: sendMessageRequest(code: number, data: MessageSequence, reply: MessageSequence, options: MessageOption, callback: AsyncCallback\<RequestResult>): void;|api/@ohos.rpc.d.ts|
|New API|NA|Class name: RemoteProxy;<br>API declaration: isObjectDead(): boolean;<br>Differences: isObjectDead(): boolean;|api/@ohos.rpc.d.ts|
|New API|NA|Class name: rpc;<br>API declaration: class IPCSkeleton<br>Differences: class IPCSkeleton|api/@ohos.rpc.d.ts|
|New API|NA|Class name: IPCSkeleton;<br>API declaration: static getContextObject(): IRemoteObject;<br>Differences: static getContextObject(): IRemoteObject;|api/@ohos.rpc.d.ts|
|New API|NA|Class name: IPCSkeleton;<br>API declaration: static getCallingPid(): number;<br>Differences: static getCallingPid(): number;|api/@ohos.rpc.d.ts|
|New API|NA|Class name: IPCSkeleton;<br>API declaration: static getCallingUid(): number;<br>Differences: static getCallingUid(): number;|api/@ohos.rpc.d.ts|
|New API|NA|Class name: IPCSkeleton;<br>API declaration: static getCallingTokenId(): number;<br>Differences: static getCallingTokenId(): number;|api/@ohos.rpc.d.ts|
|New API|NA|Class name: IPCSkeleton;<br>API declaration: static getCallingDeviceID(): string;<br>Differences: static getCallingDeviceID(): string;|api/@ohos.rpc.d.ts|
|New API|NA|Class name: IPCSkeleton;<br>API declaration: static getLocalDeviceID(): string;<br>Differences: static getLocalDeviceID(): string;|api/@ohos.rpc.d.ts|
|New API|NA|Class name: IPCSkeleton;<br>API declaration: static isLocalCalling(): boolean;<br>Differences: static isLocalCalling(): boolean;|api/@ohos.rpc.d.ts|
|New API|NA|Class name: IPCSkeleton;<br>API declaration: static flushCommands(object: IRemoteObject): number;<br>Differences: static flushCommands(object: IRemoteObject): number;|api/@ohos.rpc.d.ts|
|New API|NA|Class name: IPCSkeleton;<br>API declaration: static flushCmdBuffer(object: IRemoteObject): void;<br>Differences: static flushCmdBuffer(object: IRemoteObject): void;|api/@ohos.rpc.d.ts|
|New API|NA|Class name: IPCSkeleton;<br>API declaration: static resetCallingIdentity(): string;<br>Differences: static resetCallingIdentity(): string;|api/@ohos.rpc.d.ts|
|New API|NA|Class name: IPCSkeleton;<br>API declaration: static setCallingIdentity(identity: string): boolean;<br>Differences: static setCallingIdentity(identity: string): boolean;|api/@ohos.rpc.d.ts|
|New API|NA|Class name: IPCSkeleton;<br>API declaration: static restoreCallingIdentity(identity: string): void;<br>Differences: static restoreCallingIdentity(identity: string): void;|api/@ohos.rpc.d.ts|
|New API|NA|Class name: rpc;<br>API declaration: class Ashmem<br>Differences: class Ashmem|api/@ohos.rpc.d.ts|
|New API|NA|Class name: Ashmem;<br>API declaration: PROT_EXEC: number;<br>Differences: PROT_EXEC: number;|api/@ohos.rpc.d.ts|
|New API|NA|Class name: Ashmem;<br>API declaration: PROT_NONE: number;<br>Differences: PROT_NONE: number;|api/@ohos.rpc.d.ts|
|New API|NA|Class name: Ashmem;<br>API declaration: PROT_READ: number;<br>Differences: PROT_READ: number;|api/@ohos.rpc.d.ts|
|New API|NA|Class name: Ashmem;<br>API declaration: PROT_WRITE: number;<br>Differences: PROT_WRITE: number;|api/@ohos.rpc.d.ts|
|New API|NA|Class name: Ashmem;<br>API declaration: static createAshmem(name: string, size: number): Ashmem;<br>Differences: static createAshmem(name: string, size: number): Ashmem;|api/@ohos.rpc.d.ts|
|New API|NA|Class name: Ashmem;<br>API declaration: static create(name: string, size: number): Ashmem;<br>Differences: static create(name: string, size: number): Ashmem;|api/@ohos.rpc.d.ts|
|New API|NA|Class name: Ashmem;<br>API declaration: static create(ashmem: Ashmem): Ashmem;<br>Differences: static create(ashmem: Ashmem): Ashmem;|api/@ohos.rpc.d.ts|
|New API|NA|Class name: Ashmem;<br>API declaration: static createAshmemFromExisting(ashmem: Ashmem): Ashmem;<br>Differences: static createAshmemFromExisting(ashmem: Ashmem): Ashmem;|api/@ohos.rpc.d.ts|
|New API|NA|Class name: Ashmem;<br>API declaration: closeAshmem(): void;<br>Differences: closeAshmem(): void;|api/@ohos.rpc.d.ts|
|New API|NA|Class name: Ashmem;<br>API declaration: unmapAshmem(): void;<br>Differences: unmapAshmem(): void;|api/@ohos.rpc.d.ts|
|New API|NA|Class name: Ashmem;<br>API declaration: getAshmemSize(): number;<br>Differences: getAshmemSize(): number;|api/@ohos.rpc.d.ts|
|New API|NA|Class name: Ashmem;<br>API declaration: mapAshmem(mapType: number): boolean;<br>Differences: mapAshmem(mapType: number): boolean;|api/@ohos.rpc.d.ts|
|New API|NA|Class name: Ashmem;<br>API declaration: mapTypedAshmem(mapType: number): void;<br>Differences: mapTypedAshmem(mapType: number): void;|api/@ohos.rpc.d.ts|
|New API|NA|Class name: Ashmem;<br>API declaration: mapReadAndWriteAshmem(): boolean;<br>Differences: mapReadAndWriteAshmem(): boolean;|api/@ohos.rpc.d.ts|
|New API|NA|Class name: Ashmem;<br>API declaration: mapReadWriteAshmem(): void;<br>Differences: mapReadWriteAshmem(): void;|api/@ohos.rpc.d.ts|
|New API|NA|Class name: Ashmem;<br>API declaration: mapReadOnlyAshmem(): boolean;<br>Differences: mapReadOnlyAshmem(): boolean;|api/@ohos.rpc.d.ts|
|New API|NA|Class name: Ashmem;<br>API declaration: mapReadonlyAshmem(): void;<br>Differences: mapReadonlyAshmem(): void;|api/@ohos.rpc.d.ts|
|New API|NA|Class name: Ashmem;<br>API declaration: setProtection(protectionType: number): boolean;<br>Differences: setProtection(protectionType: number): boolean;|api/@ohos.rpc.d.ts|
|New API|NA|Class name: Ashmem;<br>API declaration: setProtectionType(protectionType: number): void;<br>Differences: setProtectionType(protectionType: number): void;|api/@ohos.rpc.d.ts|
|New API|NA|Class name: Ashmem;<br>API declaration: writeToAshmem(buf: number[], size: number, offset: number): boolean;<br>Differences: writeToAshmem(buf: number[], size: number, offset: number): boolean;|api/@ohos.rpc.d.ts|
|New API|NA|Class name: Ashmem;<br>API declaration: writeAshmem(buf: number[], size: number, offset: number): void;<br>Differences: writeAshmem(buf: number[], size: number, offset: number): void;|api/@ohos.rpc.d.ts|
|New API|NA|Class name: Ashmem;<br>API declaration: writeDataToAshmem(buf: ArrayBuffer, size: number, offset: number): void;<br>Differences: writeDataToAshmem(buf: ArrayBuffer, size: number, offset: number): void;|api/@ohos.rpc.d.ts|
|New API|NA|Class name: Ashmem;<br>API declaration: readFromAshmem(size: number, offset: number): number[];<br>Differences: readFromAshmem(size: number, offset: number): number[];|api/@ohos.rpc.d.ts|
|New API|NA|Class name: Ashmem;<br>API declaration: readAshmem(size: number, offset: number): number[];<br>Differences: readAshmem(size: number, offset: number): number[];|api/@ohos.rpc.d.ts|
|New API|NA|Class name: Ashmem;<br>API declaration: readDataFromAshmem(size: number, offset: number): ArrayBuffer;<br>Differences: readDataFromAshmem(size: number, offset: number): ArrayBuffer;|api/@ohos.rpc.d.ts|
|Member moved from parent to child class|Class name: IRemoteObject;<br>API declaration: queryLocalInterface(descriptor: string): IRemoteBroker;<br>Differences: queryLocalInterface(descriptor: string): IRemoteBroker;|Class name: RemoteObject;<br>API declaration: queryLocalInterface(descriptor: string): IRemoteBroker;<br>Differences: NA|api/@ohos.rpc.d.ts|
|Member moved from parent to child class|Class name: IRemoteObject;<br>API declaration: getLocalInterface(descriptor: string): IRemoteBroker;<br>Differences: getLocalInterface(descriptor: string): IRemoteBroker;|Class name: RemoteObject;<br>API declaration: getLocalInterface(descriptor: string): IRemoteBroker;<br>Differences: NA|api/@ohos.rpc.d.ts|
|Member moved from parent to child class|Class name: IRemoteObject;<br>API declaration: sendRequest(code: number, data: MessageParcel, reply: MessageParcel, options: MessageOption): boolean;<br>Differences: sendRequest(code: number, data: MessageParcel, reply: MessageParcel, options: MessageOption): boolean;|Class name: RemoteObject;<br>API declaration: sendRequest(code: number, data: MessageParcel, reply: MessageParcel, options: MessageOption): boolean;<br>Differences: NA|api/@ohos.rpc.d.ts|
|Member moved from parent to child class|Class name: IRemoteObject;<br>API declaration: sendRequest(code: number, data: MessageParcel, reply: MessageParcel, options: MessageOption): Promise\<SendRequestResult>;<br>Differences: sendRequest(code: number, data: MessageParcel, reply: MessageParcel, options: MessageOption): Promise\<SendRequestResult>;|Class name: RemoteObject;<br>API declaration: sendRequest(code: number, data: MessageParcel, reply: MessageParcel, options: MessageOption): boolean;<br>Differences: NA|api/@ohos.rpc.d.ts|
|Member moved from parent to child class|Class name: IRemoteObject;<br>API declaration: sendRequest(code: number, data: MessageParcel, reply: MessageParcel, options: MessageOption, callback: AsyncCallback\<SendRequestResult>): void;<br>Differences: sendRequest(code: number, data: MessageParcel, reply: MessageParcel, options: MessageOption, callback: AsyncCallback\<SendRequestResult>): void;|Class name: RemoteObject;<br>API declaration: sendRequest(code: number, data: MessageParcel, reply: MessageParcel, options: MessageOption): boolean;<br>Differences: NA|api/@ohos.rpc.d.ts|
|Member moved from parent to child class|Class name: IRemoteObject;<br>API declaration: sendMessageRequest(code: number, data: MessageSequence, reply: MessageSequence, options: MessageOption): Promise\<RequestResult>;<br>Differences: sendMessageRequest(code: number, data: MessageSequence, reply: MessageSequence, options: MessageOption): Promise\<RequestResult>;|Class name: RemoteObject;<br>API declaration: sendMessageRequest(code: number, data: MessageSequence, reply: MessageSequence, options: MessageOption): Promise\<RequestResult>;<br>Differences: NA|api/@ohos.rpc.d.ts|
|Member moved from parent to child class|Class name: IRemoteObject;<br>API declaration: sendMessageRequest(code: number, data: MessageSequence, reply: MessageSequence, options: MessageOption, callback: AsyncCallback\<RequestResult>): void;<br>Differences: sendMessageRequest(code: number, data: MessageSequence, reply: MessageSequence, options: MessageOption, callback: AsyncCallback\<RequestResult>): void;|Class name: RemoteObject;<br>API declaration: sendMessageRequest(code: number, data: MessageSequence, reply: MessageSequence, options: MessageOption): Promise\<RequestResult>;<br>Differences: NA|api/@ohos.rpc.d.ts|
|Member moved from parent to child class|Class name: IRemoteObject;<br>API declaration: addDeathRecipient(recipient: DeathRecipient, flags: number): boolean;<br>Differences: addDeathRecipient(recipient: DeathRecipient, flags: number): boolean;|Class name: RemoteProxy;<br>API declaration: addDeathRecipient(recipient: DeathRecipient, flags: number): boolean;<br>Differences: NA|api/@ohos.rpc.d.ts|
|Member moved from parent to child class|Class name: IRemoteObject;<br>API declaration: registerDeathRecipient(recipient: DeathRecipient, flags: number): void;<br>Differences: registerDeathRecipient(recipient: DeathRecipient, flags: number): void;|Class name: RemoteProxy;<br>API declaration: registerDeathRecipient(recipient: DeathRecipient, flags: number): void;<br>Differences: NA|api/@ohos.rpc.d.ts|
|Member moved from parent to child class|Class name: IRemoteObject;<br>API declaration: removeDeathRecipient(recipient: DeathRecipient, flags: number): boolean;<br>Differences: removeDeathRecipient(recipient: DeathRecipient, flags: number): boolean;|Class name: RemoteProxy;<br>API declaration: removeDeathRecipient(recipient: DeathRecipient, flags: number): boolean;<br>Differences: NA|api/@ohos.rpc.d.ts|
|Member moved from parent to child class|Class name: IRemoteObject;<br>API declaration: unregisterDeathRecipient(recipient: DeathRecipient, flags: number): void;<br>Differences: unregisterDeathRecipient(recipient: DeathRecipient, flags: number): void;|Class name: RemoteProxy;<br>API declaration: unregisterDeathRecipient(recipient: DeathRecipient, flags: number): void;<br>Differences: NA|api/@ohos.rpc.d.ts|
|Member moved from parent to child class|Class name: IRemoteObject;<br>API declaration: getInterfaceDescriptor(): string;<br>Differences: getInterfaceDescriptor(): string;|Class name: RemoteObject;<br>API declaration: getInterfaceDescriptor(): string;<br>Differences: NA|api/@ohos.rpc.d.ts|
|Member moved from parent to child class|Class name: IRemoteObject;<br>API declaration: getDescriptor(): string;<br>Differences: getDescriptor(): string;|Class name: RemoteObject;<br>API declaration: getDescriptor(): string;<br>Differences: NA|api/@ohos.rpc.d.ts|
|Member moved from parent to child class|Class name: IRemoteObject;<br>API declaration: isObjectDead(): boolean;<br>Differences: isObjectDead(): boolean;|Class name: RemoteProxy;<br>API declaration: isObjectDead(): boolean;<br>Differences: NA|api/@ohos.rpc.d.ts|
|New Kit|Class name: global;<br>API declaration: <br>Differences: NA|Class name: global;<br>API declaration: api\@ohos.rpc.d.ts<br>Differences: IPCKit|api/@ohos.rpc.d.ts|
|New Kit|Class name: global;<br>API declaration: <br>Differences: NA|Class name: global;<br>API declaration: kits\@kit.IPCKit.d.ts<br>Differences: IPCKit|kits/@kit.IPCKit.d.ts|
