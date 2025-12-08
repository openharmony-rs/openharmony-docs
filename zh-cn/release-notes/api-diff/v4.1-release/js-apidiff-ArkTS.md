| 操作 | 旧版本 | 新版本 | d.ts文件 |
| ---- | ------ | ------ | -------- |
|新增API|NA|类名：global；<br>API声明：declare namespace buffer<br>差异内容：declare namespace buffer|api/@ohos.buffer.d.ts|
|新增API|NA|类名：buffer；<br>API声明：type BufferEncoding = 'ascii' \| 'utf8' \| 'utf-8' \| 'utf16le' \| 'ucs2' \| 'ucs-2' \| 'base64' \| 'base64url' \| 'latin1' \| 'binary' \| 'hex';<br>差异内容：type BufferEncoding = 'ascii' \| 'utf8' \| 'utf-8' \| 'utf16le' \| 'ucs2' \| 'ucs-2' \| 'base64' \| 'base64url' \| 'latin1' \| 'binary' \| 'hex';|api/@ohos.buffer.d.ts|
|新增API|NA|类名：buffer；<br>API声明：interface TypedArray<br>差异内容：interface TypedArray|api/@ohos.buffer.d.ts|
|新增API|NA|类名：buffer；<br>API声明：function alloc(size: number, fill?: string \| Buffer \| number, encoding?: BufferEncoding): Buffer;<br>差异内容：function alloc(size: number, fill?: string \| Buffer \| number, encoding?: BufferEncoding): Buffer;|api/@ohos.buffer.d.ts|
|新增API|NA|类名：buffer；<br>API声明：function allocUninitializedFromPool(size: number): Buffer;<br>差异内容：function allocUninitializedFromPool(size: number): Buffer;|api/@ohos.buffer.d.ts|
|新增API|NA|类名：buffer；<br>API声明：function allocUninitialized(size: number): Buffer;<br>差异内容：function allocUninitialized(size: number): Buffer;|api/@ohos.buffer.d.ts|
|新增API|NA|类名：buffer；<br>API声明：function byteLength(string: string \| Buffer \| TypedArray \| DataView \| ArrayBuffer \| SharedArrayBuffer, encoding?: BufferEncoding): number;<br>差异内容：function byteLength(string: string \| Buffer \| TypedArray \| DataView \| ArrayBuffer \| SharedArrayBuffer, encoding?: BufferEncoding): number;|api/@ohos.buffer.d.ts|
|新增API|NA|类名：buffer；<br>API声明：function concat(list: Buffer[] \| Uint8Array[], totalLength?: number): Buffer;<br>差异内容：function concat(list: Buffer[] \| Uint8Array[], totalLength?: number): Buffer;|api/@ohos.buffer.d.ts|
|新增API|NA|类名：buffer；<br>API声明：function from(array: number[]): Buffer;<br>差异内容：function from(array: number[]): Buffer;|api/@ohos.buffer.d.ts|
|新增API|NA|类名：buffer；<br>API声明：function from(arrayBuffer: ArrayBuffer \| SharedArrayBuffer, byteOffset?: number, length?: number): Buffer;<br>差异内容：function from(arrayBuffer: ArrayBuffer \| SharedArrayBuffer, byteOffset?: number, length?: number): Buffer;|api/@ohos.buffer.d.ts|
|新增API|NA|类名：buffer；<br>API声明：function from(buffer: Buffer \| Uint8Array): Buffer;<br>差异内容：function from(buffer: Buffer \| Uint8Array): Buffer;|api/@ohos.buffer.d.ts|
|新增API|NA|类名：buffer；<br>API声明：function from(object: Object, offsetOrEncoding: number \| string, length: number): Buffer;<br>差异内容：function from(object: Object, offsetOrEncoding: number \| string, length: number): Buffer;|api/@ohos.buffer.d.ts|
|新增API|NA|类名：buffer；<br>API声明：function from(string: String, encoding?: BufferEncoding): Buffer;<br>差异内容：function from(string: String, encoding?: BufferEncoding): Buffer;|api/@ohos.buffer.d.ts|
|新增API|NA|类名：buffer；<br>API声明：function isBuffer(obj: Object): boolean;<br>差异内容：function isBuffer(obj: Object): boolean;|api/@ohos.buffer.d.ts|
|新增API|NA|类名：buffer；<br>API声明：function isEncoding(encoding: string): boolean;<br>差异内容：function isEncoding(encoding: string): boolean;|api/@ohos.buffer.d.ts|
|新增API|NA|类名：buffer；<br>API声明：function compare(buf1: Buffer \| Uint8Array, buf2: Buffer \| Uint8Array): -1 \| 0 \| 1;<br>差异内容：function compare(buf1: Buffer \| Uint8Array, buf2: Buffer \| Uint8Array): -1 \| 0 \| 1;|api/@ohos.buffer.d.ts|
|新增API|NA|类名：buffer；<br>API声明：function transcode(source: Buffer \| Uint8Array, fromEnc: string, toEnc: string): Buffer;<br>差异内容：function transcode(source: Buffer \| Uint8Array, fromEnc: string, toEnc: string): Buffer;|api/@ohos.buffer.d.ts|
|新增API|NA|类名：buffer；<br>API声明：class Buffer<br>差异内容：class Buffer|api/@ohos.buffer.d.ts|
|新增API|NA|类名：Buffer；<br>API声明：length: number;<br>差异内容：length: number;|api/@ohos.buffer.d.ts|
|新增API|NA|类名：Buffer；<br>API声明：buffer: ArrayBuffer;<br>差异内容：buffer: ArrayBuffer;|api/@ohos.buffer.d.ts|
|新增API|NA|类名：Buffer；<br>API声明：byteOffset: number;<br>差异内容：byteOffset: number;|api/@ohos.buffer.d.ts|
|新增API|NA|类名：Buffer；<br>API声明：fill(value: string \| Buffer \| Uint8Array \| number, offset?: number, end?: number, encoding?: BufferEncoding): Buffer;<br>差异内容：fill(value: string \| Buffer \| Uint8Array \| number, offset?: number, end?: number, encoding?: BufferEncoding): Buffer;|api/@ohos.buffer.d.ts|
|新增API|NA|类名：Buffer；<br>API声明：compare(target: Buffer \| Uint8Array, targetStart?: number, targetEnd?: number, sourceStart?: number, sourceEnd?: number): -1 \| 0 \| 1;<br>差异内容：compare(target: Buffer \| Uint8Array, targetStart?: number, targetEnd?: number, sourceStart?: number, sourceEnd?: number): -1 \| 0 \| 1;|api/@ohos.buffer.d.ts|
|新增API|NA|类名：Buffer；<br>API声明：copy(target: Buffer \| Uint8Array, targetStart?: number, sourceStart?: number, sourceEnd?: number): number;<br>差异内容：copy(target: Buffer \| Uint8Array, targetStart?: number, sourceStart?: number, sourceEnd?: number): number;|api/@ohos.buffer.d.ts|
|新增API|NA|类名：Buffer；<br>API声明：equals(otherBuffer: Uint8Array \| Buffer): boolean;<br>差异内容：equals(otherBuffer: Uint8Array \| Buffer): boolean;|api/@ohos.buffer.d.ts|
|新增API|NA|类名：Buffer；<br>API声明：includes(value: string \| number \| Buffer \| Uint8Array, byteOffset?: number, encoding?: BufferEncoding): boolean;<br>差异内容：includes(value: string \| number \| Buffer \| Uint8Array, byteOffset?: number, encoding?: BufferEncoding): boolean;|api/@ohos.buffer.d.ts|
|新增API|NA|类名：Buffer；<br>API声明：indexOf(value: string \| number \| Buffer \| Uint8Array, byteOffset?: number, encoding?: BufferEncoding): number;<br>差异内容：indexOf(value: string \| number \| Buffer \| Uint8Array, byteOffset?: number, encoding?: BufferEncoding): number;|api/@ohos.buffer.d.ts|
|新增API|NA|类名：Buffer；<br>API声明：keys(): IterableIterator\<number>;<br>差异内容：keys(): IterableIterator\<number>;|api/@ohos.buffer.d.ts|
|新增API|NA|类名：Buffer；<br>API声明：values(): IterableIterator\<number>;<br>差异内容：values(): IterableIterator\<number>;|api/@ohos.buffer.d.ts|
|新增API|NA|类名：Buffer；<br>API声明：entries(): IterableIterator\<[<br>            number,<br>            number<br>        ]>;<br>差异内容：entries(): IterableIterator\<[<br>            number,<br>            number<br>        ]>;|api/@ohos.buffer.d.ts|
|新增API|NA|类名：Buffer；<br>API声明：lastIndexOf(value: string \| number \| Buffer \| Uint8Array, byteOffset?: number, encoding?: BufferEncoding): number;<br>差异内容：lastIndexOf(value: string \| number \| Buffer \| Uint8Array, byteOffset?: number, encoding?: BufferEncoding): number;|api/@ohos.buffer.d.ts|
|新增API|NA|类名：Buffer；<br>API声明：readBigInt64BE(offset?: number): bigint;<br>差异内容：readBigInt64BE(offset?: number): bigint;|api/@ohos.buffer.d.ts|
|新增API|NA|类名：Buffer；<br>API声明：readBigInt64LE(offset?: number): bigint;<br>差异内容：readBigInt64LE(offset?: number): bigint;|api/@ohos.buffer.d.ts|
|新增API|NA|类名：Buffer；<br>API声明：readBigUInt64BE(offset?: number): bigint;<br>差异内容：readBigUInt64BE(offset?: number): bigint;|api/@ohos.buffer.d.ts|
|新增API|NA|类名：Buffer；<br>API声明：readBigUInt64LE(offset?: number): bigint;<br>差异内容：readBigUInt64LE(offset?: number): bigint;|api/@ohos.buffer.d.ts|
|新增API|NA|类名：Buffer；<br>API声明：readDoubleBE(offset?: number): number;<br>差异内容：readDoubleBE(offset?: number): number;|api/@ohos.buffer.d.ts|
|新增API|NA|类名：Buffer；<br>API声明：readDoubleLE(offset?: number): number;<br>差异内容：readDoubleLE(offset?: number): number;|api/@ohos.buffer.d.ts|
|新增API|NA|类名：Buffer；<br>API声明：readFloatBE(offset?: number): number;<br>差异内容：readFloatBE(offset?: number): number;|api/@ohos.buffer.d.ts|
|新增API|NA|类名：Buffer；<br>API声明：readFloatLE(offset?: number): number;<br>差异内容：readFloatLE(offset?: number): number;|api/@ohos.buffer.d.ts|
|新增API|NA|类名：Buffer；<br>API声明：readInt8(offset?: number): number;<br>差异内容：readInt8(offset?: number): number;|api/@ohos.buffer.d.ts|
|新增API|NA|类名：Buffer；<br>API声明：readInt16BE(offset?: number): number;<br>差异内容：readInt16BE(offset?: number): number;|api/@ohos.buffer.d.ts|
|新增API|NA|类名：Buffer；<br>API声明：readInt16LE(offset?: number): number;<br>差异内容：readInt16LE(offset?: number): number;|api/@ohos.buffer.d.ts|
|新增API|NA|类名：Buffer；<br>API声明：readInt32BE(offset?: number): number;<br>差异内容：readInt32BE(offset?: number): number;|api/@ohos.buffer.d.ts|
|新增API|NA|类名：Buffer；<br>API声明：readInt32LE(offset?: number): number;<br>差异内容：readInt32LE(offset?: number): number;|api/@ohos.buffer.d.ts|
|新增API|NA|类名：Buffer；<br>API声明：readIntBE(offset: number, byteLength: number): number;<br>差异内容：readIntBE(offset: number, byteLength: number): number;|api/@ohos.buffer.d.ts|
|新增API|NA|类名：Buffer；<br>API声明：readIntLE(offset: number, byteLength: number): number;<br>差异内容：readIntLE(offset: number, byteLength: number): number;|api/@ohos.buffer.d.ts|
|新增API|NA|类名：Buffer；<br>API声明：readUInt8(offset?: number): number;<br>差异内容：readUInt8(offset?: number): number;|api/@ohos.buffer.d.ts|
|新增API|NA|类名：Buffer；<br>API声明：readUInt16BE(offset?: number): number;<br>差异内容：readUInt16BE(offset?: number): number;|api/@ohos.buffer.d.ts|
|新增API|NA|类名：Buffer；<br>API声明：readUInt16LE(offset?: number): number;<br>差异内容：readUInt16LE(offset?: number): number;|api/@ohos.buffer.d.ts|
|新增API|NA|类名：Buffer；<br>API声明：readUInt32BE(offset?: number): number;<br>差异内容：readUInt32BE(offset?: number): number;|api/@ohos.buffer.d.ts|
|新增API|NA|类名：Buffer；<br>API声明：readUInt32LE(offset?: number): number;<br>差异内容：readUInt32LE(offset?: number): number;|api/@ohos.buffer.d.ts|
|新增API|NA|类名：Buffer；<br>API声明：readUIntBE(offset: number, byteLength: number): number;<br>差异内容：readUIntBE(offset: number, byteLength: number): number;|api/@ohos.buffer.d.ts|
|新增API|NA|类名：Buffer；<br>API声明：readUIntLE(offset: number, byteLength: number): number;<br>差异内容：readUIntLE(offset: number, byteLength: number): number;|api/@ohos.buffer.d.ts|
|新增API|NA|类名：Buffer；<br>API声明：subarray(start?: number, end?: number): Buffer;<br>差异内容：subarray(start?: number, end?: number): Buffer;|api/@ohos.buffer.d.ts|
|新增API|NA|类名：Buffer；<br>API声明：swap16(): Buffer;<br>差异内容：swap16(): Buffer;|api/@ohos.buffer.d.ts|
|新增API|NA|类名：Buffer；<br>API声明：swap32(): Buffer;<br>差异内容：swap32(): Buffer;|api/@ohos.buffer.d.ts|
|新增API|NA|类名：Buffer；<br>API声明：swap64(): Buffer;<br>差异内容：swap64(): Buffer;|api/@ohos.buffer.d.ts|
|新增API|NA|类名：Buffer；<br>API声明：toJSON(): Object;<br>差异内容：toJSON(): Object;|api/@ohos.buffer.d.ts|
|新增API|NA|类名：Buffer；<br>API声明：toString(encoding?: string, start?: number, end?: number): string;<br>差异内容：toString(encoding?: string, start?: number, end?: number): string;|api/@ohos.buffer.d.ts|
|新增API|NA|类名：Buffer；<br>API声明：write(str: string, offset?: number, length?: number, encoding?: string): number;<br>差异内容：write(str: string, offset?: number, length?: number, encoding?: string): number;|api/@ohos.buffer.d.ts|
|新增API|NA|类名：Buffer；<br>API声明：writeBigInt64BE(value: bigint, offset?: number): number;<br>差异内容：writeBigInt64BE(value: bigint, offset?: number): number;|api/@ohos.buffer.d.ts|
|新增API|NA|类名：Buffer；<br>API声明：writeBigInt64LE(value: bigint, offset?: number): number;<br>差异内容：writeBigInt64LE(value: bigint, offset?: number): number;|api/@ohos.buffer.d.ts|
|新增API|NA|类名：Buffer；<br>API声明：writeBigUInt64BE(value: bigint, offset?: number): number;<br>差异内容：writeBigUInt64BE(value: bigint, offset?: number): number;|api/@ohos.buffer.d.ts|
|新增API|NA|类名：Buffer；<br>API声明：writeBigUInt64LE(value: bigint, offset?: number): number;<br>差异内容：writeBigUInt64LE(value: bigint, offset?: number): number;|api/@ohos.buffer.d.ts|
|新增API|NA|类名：Buffer；<br>API声明：writeDoubleBE(value: number, offset?: number): number;<br>差异内容：writeDoubleBE(value: number, offset?: number): number;|api/@ohos.buffer.d.ts|
|新增API|NA|类名：Buffer；<br>API声明：writeDoubleLE(value: number, offset?: number): number;<br>差异内容：writeDoubleLE(value: number, offset?: number): number;|api/@ohos.buffer.d.ts|
|新增API|NA|类名：Buffer；<br>API声明：writeFloatBE(value: number, offset?: number): number;<br>差异内容：writeFloatBE(value: number, offset?: number): number;|api/@ohos.buffer.d.ts|
|新增API|NA|类名：Buffer；<br>API声明：writeFloatLE(value: number, offset?: number): number;<br>差异内容：writeFloatLE(value: number, offset?: number): number;|api/@ohos.buffer.d.ts|
|新增API|NA|类名：Buffer；<br>API声明：writeInt8(value: number, offset?: number): number;<br>差异内容：writeInt8(value: number, offset?: number): number;|api/@ohos.buffer.d.ts|
|新增API|NA|类名：Buffer；<br>API声明：writeInt16BE(value: number, offset?: number): number;<br>差异内容：writeInt16BE(value: number, offset?: number): number;|api/@ohos.buffer.d.ts|
|新增API|NA|类名：Buffer；<br>API声明：writeInt16LE(value: number, offset?: number): number;<br>差异内容：writeInt16LE(value: number, offset?: number): number;|api/@ohos.buffer.d.ts|
|新增API|NA|类名：Buffer；<br>API声明：writeInt32BE(value: number, offset?: number): number;<br>差异内容：writeInt32BE(value: number, offset?: number): number;|api/@ohos.buffer.d.ts|
|新增API|NA|类名：Buffer；<br>API声明：writeInt32LE(value: number, offset?: number): number;<br>差异内容：writeInt32LE(value: number, offset?: number): number;|api/@ohos.buffer.d.ts|
|新增API|NA|类名：Buffer；<br>API声明：writeIntBE(value: number, offset: number, byteLength: number): number;<br>差异内容：writeIntBE(value: number, offset: number, byteLength: number): number;|api/@ohos.buffer.d.ts|
|新增API|NA|类名：Buffer；<br>API声明：writeIntLE(value: number, offset: number, byteLength: number): number;<br>差异内容：writeIntLE(value: number, offset: number, byteLength: number): number;|api/@ohos.buffer.d.ts|
|新增API|NA|类名：Buffer；<br>API声明：writeUInt8(value: number, offset?: number): number;<br>差异内容：writeUInt8(value: number, offset?: number): number;|api/@ohos.buffer.d.ts|
|新增API|NA|类名：Buffer；<br>API声明：writeUInt16BE(value: number, offset?: number): number;<br>差异内容：writeUInt16BE(value: number, offset?: number): number;|api/@ohos.buffer.d.ts|
|新增API|NA|类名：Buffer；<br>API声明：writeUInt16LE(value: number, offset?: number): number;<br>差异内容：writeUInt16LE(value: number, offset?: number): number;|api/@ohos.buffer.d.ts|
|新增API|NA|类名：Buffer；<br>API声明：writeUInt32BE(value: number, offset?: number): number;<br>差异内容：writeUInt32BE(value: number, offset?: number): number;|api/@ohos.buffer.d.ts|
|新增API|NA|类名：Buffer；<br>API声明：writeUInt32LE(value: number, offset?: number): number;<br>差异内容：writeUInt32LE(value: number, offset?: number): number;|api/@ohos.buffer.d.ts|
|新增API|NA|类名：Buffer；<br>API声明：writeUIntBE(value: number, offset: number, byteLength: number): number;<br>差异内容：writeUIntBE(value: number, offset: number, byteLength: number): number;|api/@ohos.buffer.d.ts|
|新增API|NA|类名：Buffer；<br>API声明：writeUIntLE(value: number, offset: number, byteLength: number): number;<br>差异内容：writeUIntLE(value: number, offset: number, byteLength: number): number;|api/@ohos.buffer.d.ts|
|新增API|NA|类名：buffer；<br>API声明：class Blob<br>差异内容：class Blob|api/@ohos.buffer.d.ts|
|新增API|NA|类名：Blob；<br>API声明：size: number;<br>差异内容：size: number;|api/@ohos.buffer.d.ts|
|新增API|NA|类名：Blob；<br>API声明：type: string;<br>差异内容：type: string;|api/@ohos.buffer.d.ts|
|新增API|NA|类名：Blob；<br>API声明：arrayBuffer(): Promise\<ArrayBuffer>;<br>差异内容：arrayBuffer(): Promise\<ArrayBuffer>;|api/@ohos.buffer.d.ts|
|新增API|NA|类名：Blob；<br>API声明：slice(start?: number, end?: number, type?: string): Blob;<br>差异内容：slice(start?: number, end?: number, type?: string): Blob;|api/@ohos.buffer.d.ts|
|新增API|NA|类名：Blob；<br>API声明：text(): Promise\<string>;<br>差异内容：text(): Promise\<string>;|api/@ohos.buffer.d.ts|
|新增API|NA|类名：global；<br>API声明：declare namespace xml<br>差异内容：declare namespace xml|api/@ohos.convertxml.d.ts|
|新增API|NA|类名：xml；<br>API声明：interface ConvertOptions<br>差异内容：interface ConvertOptions|api/@ohos.convertxml.d.ts|
|新增API|NA|类名：ConvertOptions；<br>API声明：trim: boolean;<br>差异内容：trim: boolean;|api/@ohos.convertxml.d.ts|
|新增API|NA|类名：ConvertOptions；<br>API声明：ignoreDeclaration?: boolean;<br>差异内容：ignoreDeclaration?: boolean;|api/@ohos.convertxml.d.ts|
|新增API|NA|类名：ConvertOptions；<br>API声明：ignoreInstruction?: boolean;<br>差异内容：ignoreInstruction?: boolean;|api/@ohos.convertxml.d.ts|
|新增API|NA|类名：ConvertOptions；<br>API声明：ignoreAttributes?: boolean;<br>差异内容：ignoreAttributes?: boolean;|api/@ohos.convertxml.d.ts|
|新增API|NA|类名：ConvertOptions；<br>API声明：ignoreComment?: boolean;<br>差异内容：ignoreComment?: boolean;|api/@ohos.convertxml.d.ts|
|新增API|NA|类名：ConvertOptions；<br>API声明：ignoreCDATA?: boolean;<br>差异内容：ignoreCDATA?: boolean;|api/@ohos.convertxml.d.ts|
|新增API|NA|类名：ConvertOptions；<br>API声明：ignoreDoctype?: boolean;<br>差异内容：ignoreDoctype?: boolean;|api/@ohos.convertxml.d.ts|
|新增API|NA|类名：ConvertOptions；<br>API声明：ignoreText?: boolean;<br>差异内容：ignoreText?: boolean;|api/@ohos.convertxml.d.ts|
|新增API|NA|类名：ConvertOptions；<br>API声明：declarationKey: string;<br>差异内容：declarationKey: string;|api/@ohos.convertxml.d.ts|
|新增API|NA|类名：ConvertOptions；<br>API声明：instructionKey: string;<br>差异内容：instructionKey: string;|api/@ohos.convertxml.d.ts|
|新增API|NA|类名：ConvertOptions；<br>API声明：attributesKey: string;<br>差异内容：attributesKey: string;|api/@ohos.convertxml.d.ts|
|新增API|NA|类名：ConvertOptions；<br>API声明：textKey: string;<br>差异内容：textKey: string;|api/@ohos.convertxml.d.ts|
|新增API|NA|类名：ConvertOptions；<br>API声明：cdataKey: string;<br>差异内容：cdataKey: string;|api/@ohos.convertxml.d.ts|
|新增API|NA|类名：ConvertOptions；<br>API声明：doctypeKey: string;<br>差异内容：doctypeKey: string;|api/@ohos.convertxml.d.ts|
|新增API|NA|类名：ConvertOptions；<br>API声明：commentKey: string;<br>差异内容：commentKey: string;|api/@ohos.convertxml.d.ts|
|新增API|NA|类名：ConvertOptions；<br>API声明：parentKey: string;<br>差异内容：parentKey: string;|api/@ohos.convertxml.d.ts|
|新增API|NA|类名：ConvertOptions；<br>API声明：typeKey: string;<br>差异内容：typeKey: string;|api/@ohos.convertxml.d.ts|
|新增API|NA|类名：ConvertOptions；<br>API声明：nameKey: string;<br>差异内容：nameKey: string;|api/@ohos.convertxml.d.ts|
|新增API|NA|类名：ConvertOptions；<br>API声明：elementsKey: string;<br>差异内容：elementsKey: string;|api/@ohos.convertxml.d.ts|
|新增API|NA|类名：xml；<br>API声明：class ConvertXML<br>差异内容：class ConvertXML|api/@ohos.convertxml.d.ts|
|新增API|NA|类名：ConvertXML；<br>API声明：convert(xml: string, options?: ConvertOptions): Object;<br>差异内容：convert(xml: string, options?: ConvertOptions): Object;|api/@ohos.convertxml.d.ts|
|新增API|NA|类名：ConvertXML；<br>API声明：convertToJSObject(xml: string, options?: ConvertOptions): Object;<br>差异内容：convertToJSObject(xml: string, options?: ConvertOptions): Object;|api/@ohos.convertxml.d.ts|
|新增API|NA|类名：global；<br>API声明：declare namespace process<br>差异内容：declare namespace process|api/@ohos.process.d.ts|
|新增API|NA|类名：process；<br>API声明：export class ProcessManager<br>差异内容：export class ProcessManager|api/@ohos.process.d.ts|
|新增API|NA|类名：ProcessManager；<br>API声明：isAppUid(v: number): boolean;<br>差异内容：isAppUid(v: number): boolean;|api/@ohos.process.d.ts|
|新增API|NA|类名：ProcessManager；<br>API声明：getUidForName(v: string): number;<br>差异内容：getUidForName(v: string): number;|api/@ohos.process.d.ts|
|新增API|NA|类名：ProcessManager；<br>API声明：getThreadPriority(v: number): number;<br>差异内容：getThreadPriority(v: number): number;|api/@ohos.process.d.ts|
|新增API|NA|类名：ProcessManager；<br>API声明：getSystemConfig(name: number): number;<br>差异内容：getSystemConfig(name: number): number;|api/@ohos.process.d.ts|
|新增API|NA|类名：ProcessManager；<br>API声明：getEnvironmentVar(name: string): string;<br>差异内容：getEnvironmentVar(name: string): string;|api/@ohos.process.d.ts|
|新增API|NA|类名：ProcessManager；<br>API声明：exit(code: number): void;<br>差异内容：exit(code: number): void;|api/@ohos.process.d.ts|
|新增API|NA|类名：ProcessManager；<br>API声明：kill(signal: number, pid: number): boolean;<br>差异内容：kill(signal: number, pid: number): boolean;|api/@ohos.process.d.ts|
|新增API|NA|类名：process；<br>API声明：const uid: number;<br>差异内容：const uid: number;|api/@ohos.process.d.ts|
|新增API|NA|类名：process；<br>API声明：const pid: number;<br>差异内容：const pid: number;|api/@ohos.process.d.ts|
|新增API|NA|类名：process；<br>API声明：const tid: number;<br>差异内容：const tid: number;|api/@ohos.process.d.ts|
|新增API|NA|类名：process；<br>API声明：function isIsolatedProcess(): boolean;<br>差异内容：function isIsolatedProcess(): boolean;|api/@ohos.process.d.ts|
|新增API|NA|类名：process；<br>API声明：function isAppUid(v: number): boolean;<br>差异内容：function isAppUid(v: number): boolean;|api/@ohos.process.d.ts|
|新增API|NA|类名：process；<br>API声明：function is64Bit(): boolean;<br>差异内容：function is64Bit(): boolean;|api/@ohos.process.d.ts|
|新增API|NA|类名：process；<br>API声明：function getUidForName(v: string): number;<br>差异内容：function getUidForName(v: string): number;|api/@ohos.process.d.ts|
|新增API|NA|类名：process；<br>API声明：function getThreadPriority(v: number): number;<br>差异内容：function getThreadPriority(v: number): number;|api/@ohos.process.d.ts|
|新增API|NA|类名：process；<br>API声明：function getStartRealtime(): number;<br>差异内容：function getStartRealtime(): number;|api/@ohos.process.d.ts|
|新增API|NA|类名：process；<br>API声明：function getPastCpuTime(): number;<br>差异内容：function getPastCpuTime(): number;|api/@ohos.process.d.ts|
|新增API|NA|类名：process；<br>API声明：function getSystemConfig(name: number): number;<br>差异内容：function getSystemConfig(name: number): number;|api/@ohos.process.d.ts|
|新增API|NA|类名：process；<br>API声明：function getEnvironmentVar(name: string): string;<br>差异内容：function getEnvironmentVar(name: string): string;|api/@ohos.process.d.ts|
|新增API|NA|类名：process；<br>API声明：type EventListener = (evt: Object) => void;<br>差异内容：type EventListener = (evt: Object) => void;|api/@ohos.process.d.ts|
|新增API|NA|类名：process；<br>API声明：function abort(): void;<br>差异内容：function abort(): void;|api/@ohos.process.d.ts|
|新增API|NA|类名：process；<br>API声明：function exit(code: number): void;<br>差异内容：function exit(code: number): void;|api/@ohos.process.d.ts|
|新增API|NA|类名：process；<br>API声明：function uptime(): number;<br>差异内容：function uptime(): number;|api/@ohos.process.d.ts|
|新增API|NA|类名：process；<br>API声明：function kill(signal: number, pid: number): boolean;<br>差异内容：function kill(signal: number, pid: number): boolean;|api/@ohos.process.d.ts|
|新增API|NA|类名：global；<br>API声明：declare namespace taskpool<br>差异内容：declare namespace taskpool|api/@ohos.taskpool.d.ts|
|新增API|NA|类名：taskpool；<br>API声明：enum Priority<br>差异内容：enum Priority|api/@ohos.taskpool.d.ts|
|新增API|NA|类名：Priority；<br>API声明：HIGH = 0<br>差异内容：HIGH = 0|api/@ohos.taskpool.d.ts|
|新增API|NA|类名：Priority；<br>API声明：MEDIUM = 1<br>差异内容：MEDIUM = 1|api/@ohos.taskpool.d.ts|
|新增API|NA|类名：Priority；<br>API声明：LOW = 2<br>差异内容：LOW = 2|api/@ohos.taskpool.d.ts|
|新增API|NA|类名：taskpool；<br>API声明：class Task<br>差异内容：class Task|api/@ohos.taskpool.d.ts|
|新增API|NA|类名：Task；<br>API声明：static isCanceled(): boolean;<br>差异内容：static isCanceled(): boolean;|api/@ohos.taskpool.d.ts|
|新增API|NA|类名：Task；<br>API声明：static sendData(...args: Object[]): void;<br>差异内容：static sendData(...args: Object[]): void;|api/@ohos.taskpool.d.ts|
|新增API|NA|类名：Task；<br>API声明：setTransferList(transfer?: ArrayBuffer[]): void;<br>差异内容：setTransferList(transfer?: ArrayBuffer[]): void;|api/@ohos.taskpool.d.ts|
|新增API|NA|类名：Task；<br>API声明：setCloneList(cloneList: Object[] \| ArrayBuffer[]): void;<br>差异内容：setCloneList(cloneList: Object[] \| ArrayBuffer[]): void;|api/@ohos.taskpool.d.ts|
|新增API|NA|类名：Task；<br>API声明：onReceiveData(callback?: Function): void;<br>差异内容：onReceiveData(callback?: Function): void;|api/@ohos.taskpool.d.ts|
|新增API|NA|类名：Task；<br>API声明：addDependency(...tasks: Task[]): void;<br>差异内容：addDependency(...tasks: Task[]): void;|api/@ohos.taskpool.d.ts|
|新增API|NA|类名：Task；<br>API声明：removeDependency(...tasks: Task[]): void;<br>差异内容：removeDependency(...tasks: Task[]): void;|api/@ohos.taskpool.d.ts|
|新增API|NA|类名：Task；<br>API声明：function: Function;<br>差异内容：function: Function;|api/@ohos.taskpool.d.ts|
|新增API|NA|类名：Task；<br>API声明：arguments?: Object[];<br>差异内容：arguments?: Object[];|api/@ohos.taskpool.d.ts|
|新增API|NA|类名：Task；<br>API声明：name: string;<br>差异内容：name: string;|api/@ohos.taskpool.d.ts|
|新增API|NA|类名：Task；<br>API声明：totalDuration: number;<br>差异内容：totalDuration: number;|api/@ohos.taskpool.d.ts|
|新增API|NA|类名：Task；<br>API声明：ioDuration: number;<br>差异内容：ioDuration: number;|api/@ohos.taskpool.d.ts|
|新增API|NA|类名：Task；<br>API声明：cpuDuration: number;<br>差异内容：cpuDuration: number;|api/@ohos.taskpool.d.ts|
|新增API|NA|类名：taskpool；<br>API声明：class TaskGroup<br>差异内容：class TaskGroup|api/@ohos.taskpool.d.ts|
|新增API|NA|类名：TaskGroup；<br>API声明：addTask(func: Function, ...args: Object[]): void;<br>差异内容：addTask(func: Function, ...args: Object[]): void;|api/@ohos.taskpool.d.ts|
|新增API|NA|类名：TaskGroup；<br>API声明：addTask(task: Task): void;<br>差异内容：addTask(task: Task): void;|api/@ohos.taskpool.d.ts|
|新增API|NA|类名：TaskGroup；<br>API声明：name: string;<br>差异内容：name: string;|api/@ohos.taskpool.d.ts|
|新增API|NA|类名：taskpool；<br>API声明：class SequenceRunner<br>差异内容：class SequenceRunner|api/@ohos.taskpool.d.ts|
|新增API|NA|类名：SequenceRunner；<br>API声明：execute(task: Task): Promise\<Object>;<br>差异内容：execute(task: Task): Promise\<Object>;|api/@ohos.taskpool.d.ts|
|新增API|NA|类名：taskpool；<br>API声明：enum State<br>差异内容：enum State|api/@ohos.taskpool.d.ts|
|新增API|NA|类名：State；<br>API声明：WAITING = 1<br>差异内容：WAITING = 1|api/@ohos.taskpool.d.ts|
|新增API|NA|类名：State；<br>API声明：RUNNING = 2<br>差异内容：RUNNING = 2|api/@ohos.taskpool.d.ts|
|新增API|NA|类名：State；<br>API声明：CANCELED = 3<br>差异内容：CANCELED = 3|api/@ohos.taskpool.d.ts|
|新增API|NA|类名：taskpool；<br>API声明：class TaskInfo<br>差异内容：class TaskInfo|api/@ohos.taskpool.d.ts|
|新增API|NA|类名：TaskInfo；<br>API声明：taskId: number;<br>差异内容：taskId: number;|api/@ohos.taskpool.d.ts|
|新增API|NA|类名：TaskInfo；<br>API声明：state: State;<br>差异内容：state: State;|api/@ohos.taskpool.d.ts|
|新增API|NA|类名：TaskInfo；<br>API声明：duration?: number;<br>差异内容：duration?: number;|api/@ohos.taskpool.d.ts|
|新增API|NA|类名：taskpool；<br>API声明：class ThreadInfo<br>差异内容：class ThreadInfo|api/@ohos.taskpool.d.ts|
|新增API|NA|类名：ThreadInfo；<br>API声明：tid: number;<br>差异内容：tid: number;|api/@ohos.taskpool.d.ts|
|新增API|NA|类名：ThreadInfo；<br>API声明：taskIds?: number[];<br>差异内容：taskIds?: number[];|api/@ohos.taskpool.d.ts|
|新增API|NA|类名：ThreadInfo；<br>API声明：priority?: Priority;<br>差异内容：priority?: Priority;|api/@ohos.taskpool.d.ts|
|新增API|NA|类名：taskpool；<br>API声明：class TaskPoolInfo<br>差异内容：class TaskPoolInfo|api/@ohos.taskpool.d.ts|
|新增API|NA|类名：TaskPoolInfo；<br>API声明：threadInfos: ThreadInfo[];<br>差异内容：threadInfos: ThreadInfo[];|api/@ohos.taskpool.d.ts|
|新增API|NA|类名：TaskPoolInfo；<br>API声明：taskInfos: TaskInfo[];<br>差异内容：taskInfos: TaskInfo[];|api/@ohos.taskpool.d.ts|
|新增API|NA|类名：taskpool；<br>API声明：function execute(func: Function, ...args: Object[]): Promise\<Object>;<br>差异内容：function execute(func: Function, ...args: Object[]): Promise\<Object>;|api/@ohos.taskpool.d.ts|
|新增API|NA|类名：taskpool；<br>API声明：function execute(task: Task, priority?: Priority): Promise\<Object>;<br>差异内容：function execute(task: Task, priority?: Priority): Promise\<Object>;|api/@ohos.taskpool.d.ts|
|新增API|NA|类名：taskpool；<br>API声明：function execute(group: TaskGroup, priority?: Priority): Promise\<Object[]>;<br>差异内容：function execute(group: TaskGroup, priority?: Priority): Promise\<Object[]>;|api/@ohos.taskpool.d.ts|
|新增API|NA|类名：taskpool；<br>API声明：function executeDelayed(delayTime: number, task: Task, priority?: Priority): Promise\<Object>;<br>差异内容：function executeDelayed(delayTime: number, task: Task, priority?: Priority): Promise\<Object>;|api/@ohos.taskpool.d.ts|
|新增API|NA|类名：taskpool；<br>API声明：function cancel(task: Task): void;<br>差异内容：function cancel(task: Task): void;|api/@ohos.taskpool.d.ts|
|新增API|NA|类名：taskpool；<br>API声明：function cancel(group: TaskGroup): void;<br>差异内容：function cancel(group: TaskGroup): void;|api/@ohos.taskpool.d.ts|
|新增API|NA|类名：taskpool；<br>API声明：function getTaskPoolInfo(): TaskPoolInfo;<br>差异内容：function getTaskPoolInfo(): TaskPoolInfo;|api/@ohos.taskpool.d.ts|
|新增API|NA|类名：global；<br>API声明：declare namespace uri<br>差异内容：declare namespace uri|api/@ohos.uri.d.ts|
|新增API|NA|类名：uri；<br>API声明：class URI<br>差异内容：class URI|api/@ohos.uri.d.ts|
|新增API|NA|类名：URI；<br>API声明：toString(): string;<br>差异内容：toString(): string;|api/@ohos.uri.d.ts|
|新增API|NA|类名：URI；<br>API声明：equals(other: URI): boolean;<br>差异内容：equals(other: URI): boolean;|api/@ohos.uri.d.ts|
|新增API|NA|类名：URI；<br>API声明：equalsTo(other: URI): boolean;<br>差异内容：equalsTo(other: URI): boolean;|api/@ohos.uri.d.ts|
|新增API|NA|类名：URI；<br>API声明：checkIsAbsolute(): boolean;<br>差异内容：checkIsAbsolute(): boolean;|api/@ohos.uri.d.ts|
|新增API|NA|类名：URI；<br>API声明：normalize(): URI;<br>差异内容：normalize(): URI;|api/@ohos.uri.d.ts|
|新增API|NA|类名：URI；<br>API声明：scheme: string;<br>差异内容：scheme: string;|api/@ohos.uri.d.ts|
|新增API|NA|类名：URI；<br>API声明：userInfo: string;<br>差异内容：userInfo: string;|api/@ohos.uri.d.ts|
|新增API|NA|类名：URI；<br>API声明：host: string;<br>差异内容：host: string;|api/@ohos.uri.d.ts|
|新增API|NA|类名：URI；<br>API声明：port: string;<br>差异内容：port: string;|api/@ohos.uri.d.ts|
|新增API|NA|类名：URI；<br>API声明：path: string;<br>差异内容：path: string;|api/@ohos.uri.d.ts|
|新增API|NA|类名：URI；<br>API声明：query: string;<br>差异内容：query: string;|api/@ohos.uri.d.ts|
|新增API|NA|类名：URI；<br>API声明：fragment: string;<br>差异内容：fragment: string;|api/@ohos.uri.d.ts|
|新增API|NA|类名：URI；<br>API声明：authority: string;<br>差异内容：authority: string;|api/@ohos.uri.d.ts|
|新增API|NA|类名：URI；<br>API声明：ssp: string;<br>差异内容：ssp: string;|api/@ohos.uri.d.ts|
|新增API|NA|类名：global；<br>API声明：declare namespace url<br>差异内容：declare namespace url|api/@ohos.url.d.ts|
|新增API|NA|类名：url；<br>API声明：class URLSearchParams<br>差异内容：class URLSearchParams|api/@ohos.url.d.ts|
|新增API|NA|类名：URLSearchParams；<br>API声明：append(name: string, value: string): void;<br>差异内容：append(name: string, value: string): void;|api/@ohos.url.d.ts|
|新增API|NA|类名：URLSearchParams；<br>API声明：delete(name: string): void;<br>差异内容：delete(name: string): void;|api/@ohos.url.d.ts|
|新增API|NA|类名：URLSearchParams；<br>API声明：getAll(name: string): string[];<br>差异内容：getAll(name: string): string[];|api/@ohos.url.d.ts|
|新增API|NA|类名：URLSearchParams；<br>API声明：entries(): IterableIterator\<[<br>            string,<br>            string<br>        ]>;<br>差异内容：entries(): IterableIterator\<[<br>            string,<br>            string<br>        ]>;|api/@ohos.url.d.ts|
|新增API|NA|类名：URLSearchParams；<br>API声明：forEach(callbackFn: (value: string, key: string, searchParams: URLSearchParams) => void, thisArg?: Object): void;<br>差异内容：forEach(callbackFn: (value: string, key: string, searchParams: URLSearchParams) => void, thisArg?: Object): void;|api/@ohos.url.d.ts|
|新增API|NA|类名：URLSearchParams；<br>API声明：get(name: string): string \| null;<br>差异内容：get(name: string): string \| null;|api/@ohos.url.d.ts|
|新增API|NA|类名：URLSearchParams；<br>API声明：has(name: string): boolean;<br>差异内容：has(name: string): boolean;|api/@ohos.url.d.ts|
|新增API|NA|类名：URLSearchParams；<br>API声明：set(name: string, value: string): void;<br>差异内容：set(name: string, value: string): void;|api/@ohos.url.d.ts|
|新增API|NA|类名：URLSearchParams；<br>API声明：sort(): void;<br>差异内容：sort(): void;|api/@ohos.url.d.ts|
|新增API|NA|类名：URLSearchParams；<br>API声明：keys(): IterableIterator\<string>;<br>差异内容：keys(): IterableIterator\<string>;|api/@ohos.url.d.ts|
|新增API|NA|类名：URLSearchParams；<br>API声明：values(): IterableIterator\<string>;<br>差异内容：values(): IterableIterator\<string>;|api/@ohos.url.d.ts|
|新增API|NA|类名：URLSearchParams；<br>API声明：[Symbol.iterator](): IterableIterator\<[<br>            string,<br>            string<br>        ]>;<br>差异内容：[Symbol.iterator](): IterableIterator\<[<br>            string,<br>            string<br>        ]>;|api/@ohos.url.d.ts|
|新增API|NA|类名：URLSearchParams；<br>API声明：toString(): string;<br>差异内容：toString(): string;|api/@ohos.url.d.ts|
|新增API|NA|类名：url；<br>API声明：class URLParams<br>差异内容：class URLParams|api/@ohos.url.d.ts|
|新增API|NA|类名：URLParams；<br>API声明：append(name: string, value: string): void;<br>差异内容：append(name: string, value: string): void;|api/@ohos.url.d.ts|
|新增API|NA|类名：URLParams；<br>API声明：delete(name: string): void;<br>差异内容：delete(name: string): void;|api/@ohos.url.d.ts|
|新增API|NA|类名：URLParams；<br>API声明：getAll(name: string): string[];<br>差异内容：getAll(name: string): string[];|api/@ohos.url.d.ts|
|新增API|NA|类名：URLParams；<br>API声明：entries(): IterableIterator\<[<br>            string,<br>            string<br>        ]>;<br>差异内容：entries(): IterableIterator\<[<br>            string,<br>            string<br>        ]>;|api/@ohos.url.d.ts|
|新增API|NA|类名：URLParams；<br>API声明：forEach(callbackFn: (value: string, key: string, searchParams: URLParams) => void, thisArg?: Object): void;<br>差异内容：forEach(callbackFn: (value: string, key: string, searchParams: URLParams) => void, thisArg?: Object): void;|api/@ohos.url.d.ts|
|新增API|NA|类名：URLParams；<br>API声明：get(name: string): string \| null;<br>差异内容：get(name: string): string \| null;|api/@ohos.url.d.ts|
|新增API|NA|类名：URLParams；<br>API声明：has(name: string): boolean;<br>差异内容：has(name: string): boolean;|api/@ohos.url.d.ts|
|新增API|NA|类名：URLParams；<br>API声明：set(name: string, value: string): void;<br>差异内容：set(name: string, value: string): void;|api/@ohos.url.d.ts|
|新增API|NA|类名：URLParams；<br>API声明：sort(): void;<br>差异内容：sort(): void;|api/@ohos.url.d.ts|
|新增API|NA|类名：URLParams；<br>API声明：keys(): IterableIterator\<string>;<br>差异内容：keys(): IterableIterator\<string>;|api/@ohos.url.d.ts|
|新增API|NA|类名：URLParams；<br>API声明：values(): IterableIterator\<string>;<br>差异内容：values(): IterableIterator\<string>;|api/@ohos.url.d.ts|
|新增API|NA|类名：URLParams；<br>API声明：[Symbol.iterator](): IterableIterator\<[<br>            string,<br>            string<br>        ]>;<br>差异内容：[Symbol.iterator](): IterableIterator\<[<br>            string,<br>            string<br>        ]>;|api/@ohos.url.d.ts|
|新增API|NA|类名：URLParams；<br>API声明：toString(): string;<br>差异内容：toString(): string;|api/@ohos.url.d.ts|
|新增API|NA|类名：url；<br>API声明：class URL<br>差异内容：class URL|api/@ohos.url.d.ts|
|新增API|NA|类名：URL；<br>API声明：static parseURL(url: string, base?: string \| URL): URL;<br>差异内容：static parseURL(url: string, base?: string \| URL): URL;|api/@ohos.url.d.ts|
|新增API|NA|类名：URL；<br>API声明：toString(): string;<br>差异内容：toString(): string;|api/@ohos.url.d.ts|
|新增API|NA|类名：URL；<br>API声明：toJSON(): string;<br>差异内容：toJSON(): string;|api/@ohos.url.d.ts|
|新增API|NA|类名：URL；<br>API声明：hash: string;<br>差异内容：hash: string;|api/@ohos.url.d.ts|
|新增API|NA|类名：URL；<br>API声明：host: string;<br>差异内容：host: string;|api/@ohos.url.d.ts|
|新增API|NA|类名：URL；<br>API声明：hostname: string;<br>差异内容：hostname: string;|api/@ohos.url.d.ts|
|新增API|NA|类名：URL；<br>API声明：href: string;<br>差异内容：href: string;|api/@ohos.url.d.ts|
|新增API|NA|类名：URL；<br>API声明：readonly origin: string;<br>差异内容：readonly origin: string;|api/@ohos.url.d.ts|
|新增API|NA|类名：URL；<br>API声明：password: string;<br>差异内容：password: string;|api/@ohos.url.d.ts|
|新增API|NA|类名：URL；<br>API声明：pathname: string;<br>差异内容：pathname: string;|api/@ohos.url.d.ts|
|新增API|NA|类名：URL；<br>API声明：port: string;<br>差异内容：port: string;|api/@ohos.url.d.ts|
|新增API|NA|类名：URL；<br>API声明：protocol: string;<br>差异内容：protocol: string;|api/@ohos.url.d.ts|
|新增API|NA|类名：URL；<br>API声明：search: string;<br>差异内容：search: string;|api/@ohos.url.d.ts|
|新增API|NA|类名：URL；<br>API声明：readonly searchParams: URLSearchParams;<br>差异内容：readonly searchParams: URLSearchParams;|api/@ohos.url.d.ts|
|新增API|NA|类名：URL；<br>API声明：readonly params: URLParams;<br>差异内容：readonly params: URLParams;|api/@ohos.url.d.ts|
|新增API|NA|类名：URL；<br>API声明：username: string;<br>差异内容：username: string;|api/@ohos.url.d.ts|
|新增API|NA|类名：global；<br>API声明：declare class ArrayList<br>差异内容：declare class ArrayList|api/@ohos.util.ArrayList.d.ts|
|新增API|NA|类名：ArrayList；<br>API声明：length: number;<br>差异内容：length: number;|api/@ohos.util.ArrayList.d.ts|
|新增API|NA|类名：ArrayList；<br>API声明：add(element: T): boolean;<br>差异内容：add(element: T): boolean;|api/@ohos.util.ArrayList.d.ts|
|新增API|NA|类名：ArrayList；<br>API声明：insert(element: T, index: number): void;<br>差异内容：insert(element: T, index: number): void;|api/@ohos.util.ArrayList.d.ts|
|新增API|NA|类名：ArrayList；<br>API声明：has(element: T): boolean;<br>差异内容：has(element: T): boolean;|api/@ohos.util.ArrayList.d.ts|
|新增API|NA|类名：ArrayList；<br>API声明：getIndexOf(element: T): number;<br>差异内容：getIndexOf(element: T): number;|api/@ohos.util.ArrayList.d.ts|
|新增API|NA|类名：ArrayList；<br>API声明：removeByIndex(index: number): T;<br>差异内容：removeByIndex(index: number): T;|api/@ohos.util.ArrayList.d.ts|
|新增API|NA|类名：ArrayList；<br>API声明：remove(element: T): boolean;<br>差异内容：remove(element: T): boolean;|api/@ohos.util.ArrayList.d.ts|
|新增API|NA|类名：ArrayList；<br>API声明：getLastIndexOf(element: T): number;<br>差异内容：getLastIndexOf(element: T): number;|api/@ohos.util.ArrayList.d.ts|
|新增API|NA|类名：ArrayList；<br>API声明：removeByRange(fromIndex: number, toIndex: number): void;<br>差异内容：removeByRange(fromIndex: number, toIndex: number): void;|api/@ohos.util.ArrayList.d.ts|
|新增API|NA|类名：ArrayList；<br>API声明：replaceAllElements(callbackFn: (value: T, index?: number, arrlist?: ArrayList\<T>) => T, thisArg?: Object): void;<br>差异内容：replaceAllElements(callbackFn: (value: T, index?: number, arrlist?: ArrayList\<T>) => T, thisArg?: Object): void;|api/@ohos.util.ArrayList.d.ts|
|新增API|NA|类名：ArrayList；<br>API声明：forEach(callbackFn: (value: T, index?: number, arrlist?: ArrayList\<T>) => void, thisArg?: Object): void;<br>差异内容：forEach(callbackFn: (value: T, index?: number, arrlist?: ArrayList\<T>) => void, thisArg?: Object): void;|api/@ohos.util.ArrayList.d.ts|
|新增API|NA|类名：ArrayList；<br>API声明：sort(comparator?: (firstValue: T, secondValue: T) => number): void;<br>差异内容：sort(comparator?: (firstValue: T, secondValue: T) => number): void;|api/@ohos.util.ArrayList.d.ts|
|新增API|NA|类名：ArrayList；<br>API声明：subArrayList(fromIndex: number, toIndex: number): ArrayList\<T>;<br>差异内容：subArrayList(fromIndex: number, toIndex: number): ArrayList\<T>;|api/@ohos.util.ArrayList.d.ts|
|新增API|NA|类名：ArrayList；<br>API声明：clear(): void;<br>差异内容：clear(): void;|api/@ohos.util.ArrayList.d.ts|
|新增API|NA|类名：ArrayList；<br>API声明：clone(): ArrayList\<T>;<br>差异内容：clone(): ArrayList\<T>;|api/@ohos.util.ArrayList.d.ts|
|新增API|NA|类名：ArrayList；<br>API声明：getCapacity(): number;<br>差异内容：getCapacity(): number;|api/@ohos.util.ArrayList.d.ts|
|新增API|NA|类名：ArrayList；<br>API声明：convertToArray(): Array\<T>;<br>差异内容：convertToArray(): Array\<T>;|api/@ohos.util.ArrayList.d.ts|
|新增API|NA|类名：ArrayList；<br>API声明：isEmpty(): boolean;<br>差异内容：isEmpty(): boolean;|api/@ohos.util.ArrayList.d.ts|
|新增API|NA|类名：ArrayList；<br>API声明：increaseCapacityTo(newCapacity: number): void;<br>差异内容：increaseCapacityTo(newCapacity: number): void;|api/@ohos.util.ArrayList.d.ts|
|新增API|NA|类名：ArrayList；<br>API声明：trimToCurrentLength(): void;<br>差异内容：trimToCurrentLength(): void;|api/@ohos.util.ArrayList.d.ts|
|新增API|NA|类名：ArrayList；<br>API声明：[Symbol.iterator](): IterableIterator\<T>;<br>差异内容：[Symbol.iterator](): IterableIterator\<T>;|api/@ohos.util.ArrayList.d.ts|
|新增API|NA|类名：global；<br>API声明：declare namespace util<br>差异内容：declare namespace util|api/@ohos.util.d.ts|
|新增API|NA|类名：util；<br>API声明：function printf(format: string, ...args: Object[]): string;<br>差异内容：function printf(format: string, ...args: Object[]): string;|api/@ohos.util.d.ts|
|新增API|NA|类名：util；<br>API声明：function format(format: string, ...args: Object[]): string;<br>差异内容：function format(format: string, ...args: Object[]): string;|api/@ohos.util.d.ts|
|新增API|NA|类名：util；<br>API声明：function getErrorString(errno: number): string;<br>差异内容：function getErrorString(errno: number): string;|api/@ohos.util.d.ts|
|新增API|NA|类名：util；<br>API声明：function errnoToString(errno: number): string;<br>差异内容：function errnoToString(errno: number): string;|api/@ohos.util.d.ts|
|新增API|NA|类名：util；<br>API声明：function callbackWrapper(original: Function): (err: Object, value: Object) => void;<br>差异内容：function callbackWrapper(original: Function): (err: Object, value: Object) => void;|api/@ohos.util.d.ts|
|新增API|NA|类名：util；<br>API声明：function promisify(original: (err: Object, value: Object) => void): Function;<br>差异内容：function promisify(original: (err: Object, value: Object) => void): Function;|api/@ohos.util.d.ts|
|新增API|NA|类名：util；<br>API声明：function promiseWrapper(original: (err: Object, value: Object) => void): Object;<br>差异内容：function promiseWrapper(original: (err: Object, value: Object) => void): Object;|api/@ohos.util.d.ts|
|新增API|NA|类名：util；<br>API声明：function generateRandomUUID(entropyCache?: boolean): string;<br>差异内容：function generateRandomUUID(entropyCache?: boolean): string;|api/@ohos.util.d.ts|
|新增API|NA|类名：util；<br>API声明：function generateRandomBinaryUUID(entropyCache?: boolean): Uint8Array;<br>差异内容：function generateRandomBinaryUUID(entropyCache?: boolean): Uint8Array;|api/@ohos.util.d.ts|
|新增API|NA|类名：util；<br>API声明：function parseUUID(uuid: string): Uint8Array;<br>差异内容：function parseUUID(uuid: string): Uint8Array;|api/@ohos.util.d.ts|
|新增API|NA|类名：util；<br>API声明：interface TextDecoderOptions<br>差异内容：interface TextDecoderOptions|api/@ohos.util.d.ts|
|新增API|NA|类名：TextDecoderOptions；<br>API声明：fatal?: boolean;<br>差异内容：fatal?: boolean;|api/@ohos.util.d.ts|
|新增API|NA|类名：TextDecoderOptions；<br>API声明：ignoreBOM?: boolean;<br>差异内容：ignoreBOM?: boolean;|api/@ohos.util.d.ts|
|新增API|NA|类名：util；<br>API声明：interface DecodeWithStreamOptions<br>差异内容：interface DecodeWithStreamOptions|api/@ohos.util.d.ts|
|新增API|NA|类名：DecodeWithStreamOptions；<br>API声明：stream?: boolean;<br>差异内容：stream?: boolean;|api/@ohos.util.d.ts|
|新增API|NA|类名：util；<br>API声明：class TextDecoder<br>差异内容：class TextDecoder|api/@ohos.util.d.ts|
|新增API|NA|类名：TextDecoder；<br>API声明：readonly encoding: string;<br>差异内容：readonly encoding: string;|api/@ohos.util.d.ts|
|新增API|NA|类名：TextDecoder；<br>API声明：readonly fatal: boolean;<br>差异内容：readonly fatal: boolean;|api/@ohos.util.d.ts|
|新增API|NA|类名：TextDecoder；<br>API声明：readonly ignoreBOM = false;<br>差异内容：readonly ignoreBOM = false;|api/@ohos.util.d.ts|
|新增API|NA|类名：TextDecoder；<br>API声明：static create(encoding?: string, options?: TextDecoderOptions): TextDecoder;<br>差异内容：static create(encoding?: string, options?: TextDecoderOptions): TextDecoder;|api/@ohos.util.d.ts|
|新增API|NA|类名：TextDecoder；<br>API声明：decode(input: Uint8Array, options?: {<br>            stream?: false;<br>        }): string;<br>差异内容：decode(input: Uint8Array, options?: {<br>            stream?: false;<br>        }): string;|api/@ohos.util.d.ts|
|新增API|NA|类名：TextDecoder；<br>API声明：decodeWithStream(input: Uint8Array, options?: DecodeWithStreamOptions): string;<br>差异内容：decodeWithStream(input: Uint8Array, options?: DecodeWithStreamOptions): string;|api/@ohos.util.d.ts|
|新增API|NA|类名：util；<br>API声明：interface EncodeIntoUint8ArrayInfo<br>差异内容：interface EncodeIntoUint8ArrayInfo|api/@ohos.util.d.ts|
|新增API|NA|类名：EncodeIntoUint8ArrayInfo；<br>API声明：read: number;<br>差异内容：read: number;|api/@ohos.util.d.ts|
|新增API|NA|类名：EncodeIntoUint8ArrayInfo；<br>API声明：written: number;<br>差异内容：written: number;|api/@ohos.util.d.ts|
|新增API|NA|类名：util；<br>API声明：class TextEncoder<br>差异内容：class TextEncoder|api/@ohos.util.d.ts|
|新增API|NA|类名：TextEncoder；<br>API声明：readonly encoding = 'utf-8';<br>差异内容：readonly encoding = 'utf-8';|api/@ohos.util.d.ts|
|新增API|NA|类名：TextEncoder；<br>API声明：encode(input?: string): Uint8Array;<br>差异内容：encode(input?: string): Uint8Array;|api/@ohos.util.d.ts|
|新增API|NA|类名：TextEncoder；<br>API声明：encodeInto(input?: string): Uint8Array;<br>差异内容：encodeInto(input?: string): Uint8Array;|api/@ohos.util.d.ts|
|新增API|NA|类名：TextEncoder；<br>API声明：encodeInto(input: string, dest: Uint8Array): {<br>            read: number;<br>            written: number;<br>        };<br>差异内容：encodeInto(input: string, dest: Uint8Array): {<br>            read: number;<br>            written: number;<br>        };|api/@ohos.util.d.ts|
|新增API|NA|类名：TextEncoder；<br>API声明：encodeIntoUint8Array(input: string, dest: Uint8Array): EncodeIntoUint8ArrayInfo;<br>差异内容：encodeIntoUint8Array(input: string, dest: Uint8Array): EncodeIntoUint8ArrayInfo;|api/@ohos.util.d.ts|
|新增API|NA|类名：util；<br>API声明：class RationalNumber<br>差异内容：class RationalNumber|api/@ohos.util.d.ts|
|新增API|NA|类名：RationalNumber；<br>API声明：static parseRationalNumber(numerator: number, denominator: number): RationalNumber;<br>差异内容：static parseRationalNumber(numerator: number, denominator: number): RationalNumber;|api/@ohos.util.d.ts|
|新增API|NA|类名：RationalNumber；<br>API声明：static createRationalFromString(rationalString: string): RationalNumber;<br>差异内容：static createRationalFromString(rationalString: string): RationalNumber;|api/@ohos.util.d.ts|
|新增API|NA|类名：RationalNumber；<br>API声明：compareTo(another: RationalNumber): number;<br>差异内容：compareTo(another: RationalNumber): number;|api/@ohos.util.d.ts|
|新增API|NA|类名：RationalNumber；<br>API声明：compare(another: RationalNumber): number;<br>差异内容：compare(another: RationalNumber): number;|api/@ohos.util.d.ts|
|新增API|NA|类名：RationalNumber；<br>API声明：equals(obj: Object): boolean;<br>差异内容：equals(obj: Object): boolean;|api/@ohos.util.d.ts|
|新增API|NA|类名：RationalNumber；<br>API声明：valueOf(): number;<br>差异内容：valueOf(): number;|api/@ohos.util.d.ts|
|新增API|NA|类名：RationalNumber；<br>API声明：static getCommonDivisor(number1: number, number2: number): number;<br>差异内容：static getCommonDivisor(number1: number, number2: number): number;|api/@ohos.util.d.ts|
|新增API|NA|类名：RationalNumber；<br>API声明：static getCommonFactor(number1: number, number2: number): number;<br>差异内容：static getCommonFactor(number1: number, number2: number): number;|api/@ohos.util.d.ts|
|新增API|NA|类名：RationalNumber；<br>API声明：getDenominator(): number;<br>差异内容：getDenominator(): number;|api/@ohos.util.d.ts|
|新增API|NA|类名：RationalNumber；<br>API声明：getNumerator(): number;<br>差异内容：getNumerator(): number;|api/@ohos.util.d.ts|
|新增API|NA|类名：RationalNumber；<br>API声明：isFinite(): boolean;<br>差异内容：isFinite(): boolean;|api/@ohos.util.d.ts|
|新增API|NA|类名：RationalNumber；<br>API声明：isNaN(): boolean;<br>差异内容：isNaN(): boolean;|api/@ohos.util.d.ts|
|新增API|NA|类名：RationalNumber；<br>API声明：isZero(): boolean;<br>差异内容：isZero(): boolean;|api/@ohos.util.d.ts|
|新增API|NA|类名：RationalNumber；<br>API声明：toString(): string;<br>差异内容：toString(): string;|api/@ohos.util.d.ts|
|新增API|NA|类名：util；<br>API声明：class LruBuffer<br>差异内容：class LruBuffer|api/@ohos.util.d.ts|
|新增API|NA|类名：LruBuffer；<br>API声明：updateCapacity(newCapacity: number): void;<br>差异内容：updateCapacity(newCapacity: number): void;|api/@ohos.util.d.ts|
|新增API|NA|类名：LruBuffer；<br>API声明：toString(): string;<br>差异内容：toString(): string;|api/@ohos.util.d.ts|
|新增API|NA|类名：LruBuffer；<br>API声明：length: number;<br>差异内容：length: number;|api/@ohos.util.d.ts|
|新增API|NA|类名：LruBuffer；<br>API声明：getCapacity(): number;<br>差异内容：getCapacity(): number;|api/@ohos.util.d.ts|
|新增API|NA|类名：LruBuffer；<br>API声明：clear(): void;<br>差异内容：clear(): void;|api/@ohos.util.d.ts|
|新增API|NA|类名：LruBuffer；<br>API声明：getCreateCount(): number;<br>差异内容：getCreateCount(): number;|api/@ohos.util.d.ts|
|新增API|NA|类名：LruBuffer；<br>API声明：getMissCount(): number;<br>差异内容：getMissCount(): number;|api/@ohos.util.d.ts|
|新增API|NA|类名：LruBuffer；<br>API声明：getRemovalCount(): number;<br>差异内容：getRemovalCount(): number;|api/@ohos.util.d.ts|
|新增API|NA|类名：LruBuffer；<br>API声明：getMatchCount(): number;<br>差异内容：getMatchCount(): number;|api/@ohos.util.d.ts|
|新增API|NA|类名：LruBuffer；<br>API声明：getPutCount(): number;<br>差异内容：getPutCount(): number;|api/@ohos.util.d.ts|
|新增API|NA|类名：LruBuffer；<br>API声明：isEmpty(): boolean;<br>差异内容：isEmpty(): boolean;|api/@ohos.util.d.ts|
|新增API|NA|类名：LruBuffer；<br>API声明：get(key: K): V \| undefined;<br>差异内容：get(key: K): V \| undefined;|api/@ohos.util.d.ts|
|新增API|NA|类名：LruBuffer；<br>API声明：put(key: K, value: V): V;<br>差异内容：put(key: K, value: V): V;|api/@ohos.util.d.ts|
|新增API|NA|类名：LruBuffer；<br>API声明：values(): V[];<br>差异内容：values(): V[];|api/@ohos.util.d.ts|
|新增API|NA|类名：LruBuffer；<br>API声明：keys(): K[];<br>差异内容：keys(): K[];|api/@ohos.util.d.ts|
|新增API|NA|类名：LruBuffer；<br>API声明：remove(key: K): V \| undefined;<br>差异内容：remove(key: K): V \| undefined;|api/@ohos.util.d.ts|
|新增API|NA|类名：LruBuffer；<br>API声明：afterRemoval(isEvict: boolean, key: K, value: V, newValue: V): void;<br>差异内容：afterRemoval(isEvict: boolean, key: K, value: V, newValue: V): void;|api/@ohos.util.d.ts|
|新增API|NA|类名：LruBuffer；<br>API声明：contains(key: K): boolean;<br>差异内容：contains(key: K): boolean;|api/@ohos.util.d.ts|
|新增API|NA|类名：LruBuffer；<br>API声明：createDefault(key: K): V;<br>差异内容：createDefault(key: K): V;|api/@ohos.util.d.ts|
|新增API|NA|类名：LruBuffer；<br>API声明：entries(): IterableIterator\<[<br>            K,<br>            V<br>        ]>;<br>差异内容：entries(): IterableIterator\<[<br>            K,<br>            V<br>        ]>;|api/@ohos.util.d.ts|
|新增API|NA|类名：LruBuffer；<br>API声明：[Symbol.iterator](): IterableIterator\<[<br>            K,<br>            V<br>        ]>;<br>差异内容：[Symbol.iterator](): IterableIterator\<[<br>            K,<br>            V<br>        ]>;|api/@ohos.util.d.ts|
|新增API|NA|类名：util；<br>API声明：class LRUCache<br>差异内容：class LRUCache|api/@ohos.util.d.ts|
|新增API|NA|类名：LRUCache；<br>API声明：updateCapacity(newCapacity: number): void;<br>差异内容：updateCapacity(newCapacity: number): void;|api/@ohos.util.d.ts|
|新增API|NA|类名：LRUCache；<br>API声明：toString(): string;<br>差异内容：toString(): string;|api/@ohos.util.d.ts|
|新增API|NA|类名：LRUCache；<br>API声明：length: number;<br>差异内容：length: number;|api/@ohos.util.d.ts|
|新增API|NA|类名：LRUCache；<br>API声明：getCapacity(): number;<br>差异内容：getCapacity(): number;|api/@ohos.util.d.ts|
|新增API|NA|类名：LRUCache；<br>API声明：clear(): void;<br>差异内容：clear(): void;|api/@ohos.util.d.ts|
|新增API|NA|类名：LRUCache；<br>API声明：getCreateCount(): number;<br>差异内容：getCreateCount(): number;|api/@ohos.util.d.ts|
|新增API|NA|类名：LRUCache；<br>API声明：getMissCount(): number;<br>差异内容：getMissCount(): number;|api/@ohos.util.d.ts|
|新增API|NA|类名：LRUCache；<br>API声明：getRemovalCount(): number;<br>差异内容：getRemovalCount(): number;|api/@ohos.util.d.ts|
|新增API|NA|类名：LRUCache；<br>API声明：getMatchCount(): number;<br>差异内容：getMatchCount(): number;|api/@ohos.util.d.ts|
|新增API|NA|类名：LRUCache；<br>API声明：getPutCount(): number;<br>差异内容：getPutCount(): number;|api/@ohos.util.d.ts|
|新增API|NA|类名：LRUCache；<br>API声明：isEmpty(): boolean;<br>差异内容：isEmpty(): boolean;|api/@ohos.util.d.ts|
|新增API|NA|类名：LRUCache；<br>API声明：get(key: K): V \| undefined;<br>差异内容：get(key: K): V \| undefined;|api/@ohos.util.d.ts|
|新增API|NA|类名：LRUCache；<br>API声明：put(key: K, value: V): V;<br>差异内容：put(key: K, value: V): V;|api/@ohos.util.d.ts|
|新增API|NA|类名：LRUCache；<br>API声明：values(): V[];<br>差异内容：values(): V[];|api/@ohos.util.d.ts|
|新增API|NA|类名：LRUCache；<br>API声明：keys(): K[];<br>差异内容：keys(): K[];|api/@ohos.util.d.ts|
|新增API|NA|类名：LRUCache；<br>API声明：remove(key: K): V \| undefined;<br>差异内容：remove(key: K): V \| undefined;|api/@ohos.util.d.ts|
|新增API|NA|类名：LRUCache；<br>API声明：afterRemoval(isEvict: boolean, key: K, value: V, newValue: V): void;<br>差异内容：afterRemoval(isEvict: boolean, key: K, value: V, newValue: V): void;|api/@ohos.util.d.ts|
|新增API|NA|类名：LRUCache；<br>API声明：contains(key: K): boolean;<br>差异内容：contains(key: K): boolean;|api/@ohos.util.d.ts|
|新增API|NA|类名：LRUCache；<br>API声明：createDefault(key: K): V;<br>差异内容：createDefault(key: K): V;|api/@ohos.util.d.ts|
|新增API|NA|类名：LRUCache；<br>API声明：entries(): IterableIterator\<[<br>            K,<br>            V<br>        ]>;<br>差异内容：entries(): IterableIterator\<[<br>            K,<br>            V<br>        ]>;|api/@ohos.util.d.ts|
|新增API|NA|类名：LRUCache；<br>API声明：[Symbol.iterator](): IterableIterator\<[<br>            K,<br>            V<br>        ]>;<br>差异内容：[Symbol.iterator](): IterableIterator\<[<br>            K,<br>            V<br>        ]>;|api/@ohos.util.d.ts|
|新增API|NA|类名：util；<br>API声明：interface ScopeComparable<br>差异内容：interface ScopeComparable|api/@ohos.util.d.ts|
|新增API|NA|类名：ScopeComparable；<br>API声明：compareTo(other: ScopeComparable): boolean;<br>差异内容：compareTo(other: ScopeComparable): boolean;|api/@ohos.util.d.ts|
|新增API|NA|类名：util；<br>API声明：type ScopeType = ScopeComparable \| number;<br>差异内容：type ScopeType = ScopeComparable \| number;|api/@ohos.util.d.ts|
|新增API|NA|类名：util；<br>API声明：class Scope<br>差异内容：class Scope|api/@ohos.util.d.ts|
|新增API|NA|类名：Scope；<br>API声明：toString(): string;<br>差异内容：toString(): string;|api/@ohos.util.d.ts|
|新增API|NA|类名：Scope；<br>API声明：intersect(range: Scope): Scope;<br>差异内容：intersect(range: Scope): Scope;|api/@ohos.util.d.ts|
|新增API|NA|类名：Scope；<br>API声明：intersect(lowerObj: ScopeType, upperObj: ScopeType): Scope;<br>差异内容：intersect(lowerObj: ScopeType, upperObj: ScopeType): Scope;|api/@ohos.util.d.ts|
|新增API|NA|类名：Scope；<br>API声明：getUpper(): ScopeType;<br>差异内容：getUpper(): ScopeType;|api/@ohos.util.d.ts|
|新增API|NA|类名：Scope；<br>API声明：getLower(): ScopeType;<br>差异内容：getLower(): ScopeType;|api/@ohos.util.d.ts|
|新增API|NA|类名：Scope；<br>API声明：expand(lowerObj: ScopeType, upperObj: ScopeType): Scope;<br>差异内容：expand(lowerObj: ScopeType, upperObj: ScopeType): Scope;|api/@ohos.util.d.ts|
|新增API|NA|类名：Scope；<br>API声明：expand(range: Scope): Scope;<br>差异内容：expand(range: Scope): Scope;|api/@ohos.util.d.ts|
|新增API|NA|类名：Scope；<br>API声明：expand(value: ScopeType): Scope;<br>差异内容：expand(value: ScopeType): Scope;|api/@ohos.util.d.ts|
|新增API|NA|类名：Scope；<br>API声明：contains(value: ScopeType): boolean;<br>差异内容：contains(value: ScopeType): boolean;|api/@ohos.util.d.ts|
|新增API|NA|类名：Scope；<br>API声明：contains(range: Scope): boolean;<br>差异内容：contains(range: Scope): boolean;|api/@ohos.util.d.ts|
|新增API|NA|类名：Scope；<br>API声明：clamp(value: ScopeType): ScopeType;<br>差异内容：clamp(value: ScopeType): ScopeType;|api/@ohos.util.d.ts|
|新增API|NA|类名：util；<br>API声明：class ScopeHelper<br>差异内容：class ScopeHelper|api/@ohos.util.d.ts|
|新增API|NA|类名：ScopeHelper；<br>API声明：toString(): string;<br>差异内容：toString(): string;|api/@ohos.util.d.ts|
|新增API|NA|类名：ScopeHelper；<br>API声明：intersect(range: ScopeHelper): ScopeHelper;<br>差异内容：intersect(range: ScopeHelper): ScopeHelper;|api/@ohos.util.d.ts|
|新增API|NA|类名：ScopeHelper；<br>API声明：intersect(lowerObj: ScopeType, upperObj: ScopeType): ScopeHelper;<br>差异内容：intersect(lowerObj: ScopeType, upperObj: ScopeType): ScopeHelper;|api/@ohos.util.d.ts|
|新增API|NA|类名：ScopeHelper；<br>API声明：getUpper(): ScopeType;<br>差异内容：getUpper(): ScopeType;|api/@ohos.util.d.ts|
|新增API|NA|类名：ScopeHelper；<br>API声明：getLower(): ScopeType;<br>差异内容：getLower(): ScopeType;|api/@ohos.util.d.ts|
|新增API|NA|类名：ScopeHelper；<br>API声明：expand(lowerObj: ScopeType, upperObj: ScopeType): ScopeHelper;<br>差异内容：expand(lowerObj: ScopeType, upperObj: ScopeType): ScopeHelper;|api/@ohos.util.d.ts|
|新增API|NA|类名：ScopeHelper；<br>API声明：expand(range: ScopeHelper): ScopeHelper;<br>差异内容：expand(range: ScopeHelper): ScopeHelper;|api/@ohos.util.d.ts|
|新增API|NA|类名：ScopeHelper；<br>API声明：expand(value: ScopeType): ScopeHelper;<br>差异内容：expand(value: ScopeType): ScopeHelper;|api/@ohos.util.d.ts|
|新增API|NA|类名：ScopeHelper；<br>API声明：contains(value: ScopeType): boolean;<br>差异内容：contains(value: ScopeType): boolean;|api/@ohos.util.d.ts|
|新增API|NA|类名：ScopeHelper；<br>API声明：contains(range: ScopeHelper): boolean;<br>差异内容：contains(range: ScopeHelper): boolean;|api/@ohos.util.d.ts|
|新增API|NA|类名：ScopeHelper；<br>API声明：clamp(value: ScopeType): ScopeType;<br>差异内容：clamp(value: ScopeType): ScopeType;|api/@ohos.util.d.ts|
|新增API|NA|类名：util；<br>API声明：class Base64<br>差异内容：class Base64|api/@ohos.util.d.ts|
|新增API|NA|类名：Base64；<br>API声明：encodeSync(src: Uint8Array): Uint8Array;<br>差异内容：encodeSync(src: Uint8Array): Uint8Array;|api/@ohos.util.d.ts|
|新增API|NA|类名：Base64；<br>API声明：encodeToStringSync(src: Uint8Array): string;<br>差异内容：encodeToStringSync(src: Uint8Array): string;|api/@ohos.util.d.ts|
|新增API|NA|类名：Base64；<br>API声明：decodeSync(src: Uint8Array \| string): Uint8Array;<br>差异内容：decodeSync(src: Uint8Array \| string): Uint8Array;|api/@ohos.util.d.ts|
|新增API|NA|类名：Base64；<br>API声明：encode(src: Uint8Array): Promise\<Uint8Array>;<br>差异内容：encode(src: Uint8Array): Promise\<Uint8Array>;|api/@ohos.util.d.ts|
|新增API|NA|类名：Base64；<br>API声明：encodeToString(src: Uint8Array): Promise\<string>;<br>差异内容：encodeToString(src: Uint8Array): Promise\<string>;|api/@ohos.util.d.ts|
|新增API|NA|类名：Base64；<br>API声明：decode(src: Uint8Array \| string): Promise\<Uint8Array>;<br>差异内容：decode(src: Uint8Array \| string): Promise\<Uint8Array>;|api/@ohos.util.d.ts|
|新增API|NA|类名：util；<br>API声明：enum Type<br>差异内容：enum Type|api/@ohos.util.d.ts|
|新增API|NA|类名：Type；<br>API声明：BASIC<br>差异内容：BASIC|api/@ohos.util.d.ts|
|新增API|NA|类名：Type；<br>API声明：MIME<br>差异内容：MIME|api/@ohos.util.d.ts|
|新增API|NA|类名：util；<br>API声明：class Base64Helper<br>差异内容：class Base64Helper|api/@ohos.util.d.ts|
|新增API|NA|类名：Base64Helper；<br>API声明：encodeSync(src: Uint8Array): Uint8Array;<br>差异内容：encodeSync(src: Uint8Array): Uint8Array;|api/@ohos.util.d.ts|
|新增API|NA|类名：Base64Helper；<br>API声明：encodeToStringSync(src: Uint8Array, options?: Type): string;<br>差异内容：encodeToStringSync(src: Uint8Array, options?: Type): string;|api/@ohos.util.d.ts|
|新增API|NA|类名：Base64Helper；<br>API声明：decodeSync(src: Uint8Array \| string, options?: Type): Uint8Array;<br>差异内容：decodeSync(src: Uint8Array \| string, options?: Type): Uint8Array;|api/@ohos.util.d.ts|
|新增API|NA|类名：Base64Helper；<br>API声明：encode(src: Uint8Array): Promise\<Uint8Array>;<br>差异内容：encode(src: Uint8Array): Promise\<Uint8Array>;|api/@ohos.util.d.ts|
|新增API|NA|类名：Base64Helper；<br>API声明：encodeToString(src: Uint8Array, options?: Type): Promise\<string>;<br>差异内容：encodeToString(src: Uint8Array, options?: Type): Promise\<string>;|api/@ohos.util.d.ts|
|新增API|NA|类名：Base64Helper；<br>API声明：decode(src: Uint8Array \| string, options?: Type): Promise\<Uint8Array>;<br>差异内容：decode(src: Uint8Array \| string, options?: Type): Promise\<Uint8Array>;|api/@ohos.util.d.ts|
|新增API|NA|类名：util；<br>API声明：class types<br>差异内容：class types|api/@ohos.util.d.ts|
|新增API|NA|类名：types；<br>API声明：isAnyArrayBuffer(value: Object): boolean;<br>差异内容：isAnyArrayBuffer(value: Object): boolean;|api/@ohos.util.d.ts|
|新增API|NA|类名：types；<br>API声明：isArrayBufferView(value: Object): boolean;<br>差异内容：isArrayBufferView(value: Object): boolean;|api/@ohos.util.d.ts|
|新增API|NA|类名：types；<br>API声明：isArgumentsObject(value: Object): boolean;<br>差异内容：isArgumentsObject(value: Object): boolean;|api/@ohos.util.d.ts|
|新增API|NA|类名：types；<br>API声明：isArrayBuffer(value: Object): boolean;<br>差异内容：isArrayBuffer(value: Object): boolean;|api/@ohos.util.d.ts|
|新增API|NA|类名：types；<br>API声明：isAsyncFunction(value: Object): boolean;<br>差异内容：isAsyncFunction(value: Object): boolean;|api/@ohos.util.d.ts|
|新增API|NA|类名：types；<br>API声明：isBigInt64Array(value: Object): boolean;<br>差异内容：isBigInt64Array(value: Object): boolean;|api/@ohos.util.d.ts|
|新增API|NA|类名：types；<br>API声明：isBigUint64Array(value: Object): boolean;<br>差异内容：isBigUint64Array(value: Object): boolean;|api/@ohos.util.d.ts|
|新增API|NA|类名：types；<br>API声明：isBooleanObject(value: Object): boolean;<br>差异内容：isBooleanObject(value: Object): boolean;|api/@ohos.util.d.ts|
|新增API|NA|类名：types；<br>API声明：isBoxedPrimitive(value: Object): boolean;<br>差异内容：isBoxedPrimitive(value: Object): boolean;|api/@ohos.util.d.ts|
|新增API|NA|类名：types；<br>API声明：isDataView(value: Object): boolean;<br>差异内容：isDataView(value: Object): boolean;|api/@ohos.util.d.ts|
|新增API|NA|类名：types；<br>API声明：isDate(value: Object): boolean;<br>差异内容：isDate(value: Object): boolean;|api/@ohos.util.d.ts|
|新增API|NA|类名：types；<br>API声明：isExternal(value: Object): boolean;<br>差异内容：isExternal(value: Object): boolean;|api/@ohos.util.d.ts|
|新增API|NA|类名：types；<br>API声明：isFloat32Array(value: Object): boolean;<br>差异内容：isFloat32Array(value: Object): boolean;|api/@ohos.util.d.ts|
|新增API|NA|类名：types；<br>API声明：isFloat64Array(value: Object): boolean;<br>差异内容：isFloat64Array(value: Object): boolean;|api/@ohos.util.d.ts|
|新增API|NA|类名：types；<br>API声明：isGeneratorFunction(value: Object): boolean;<br>差异内容：isGeneratorFunction(value: Object): boolean;|api/@ohos.util.d.ts|
|新增API|NA|类名：types；<br>API声明：isGeneratorObject(value: Object): boolean;<br>差异内容：isGeneratorObject(value: Object): boolean;|api/@ohos.util.d.ts|
|新增API|NA|类名：types；<br>API声明：isInt8Array(value: Object): boolean;<br>差异内容：isInt8Array(value: Object): boolean;|api/@ohos.util.d.ts|
|新增API|NA|类名：types；<br>API声明：isInt16Array(value: Object): boolean;<br>差异内容：isInt16Array(value: Object): boolean;|api/@ohos.util.d.ts|
|新增API|NA|类名：types；<br>API声明：isInt32Array(value: Object): boolean;<br>差异内容：isInt32Array(value: Object): boolean;|api/@ohos.util.d.ts|
|新增API|NA|类名：types；<br>API声明：isMap(value: Object): boolean;<br>差异内容：isMap(value: Object): boolean;|api/@ohos.util.d.ts|
|新增API|NA|类名：types；<br>API声明：isMapIterator(value: Object): boolean;<br>差异内容：isMapIterator(value: Object): boolean;|api/@ohos.util.d.ts|
|新增API|NA|类名：types；<br>API声明：isModuleNamespaceObject(value: Object): boolean;<br>差异内容：isModuleNamespaceObject(value: Object): boolean;|api/@ohos.util.d.ts|
|新增API|NA|类名：types；<br>API声明：isNativeError(value: Object): boolean;<br>差异内容：isNativeError(value: Object): boolean;|api/@ohos.util.d.ts|
|新增API|NA|类名：types；<br>API声明：isNumberObject(value: Object): boolean;<br>差异内容：isNumberObject(value: Object): boolean;|api/@ohos.util.d.ts|
|新增API|NA|类名：types；<br>API声明：isPromise(value: Object): boolean;<br>差异内容：isPromise(value: Object): boolean;|api/@ohos.util.d.ts|
|新增API|NA|类名：types；<br>API声明：isProxy(value: Object): boolean;<br>差异内容：isProxy(value: Object): boolean;|api/@ohos.util.d.ts|
|新增API|NA|类名：types；<br>API声明：isRegExp(value: Object): boolean;<br>差异内容：isRegExp(value: Object): boolean;|api/@ohos.util.d.ts|
|新增API|NA|类名：types；<br>API声明：isSet(value: Object): boolean;<br>差异内容：isSet(value: Object): boolean;|api/@ohos.util.d.ts|
|新增API|NA|类名：types；<br>API声明：isSetIterator(value: Object): boolean;<br>差异内容：isSetIterator(value: Object): boolean;|api/@ohos.util.d.ts|
|新增API|NA|类名：types；<br>API声明：isSharedArrayBuffer(value: Object): boolean;<br>差异内容：isSharedArrayBuffer(value: Object): boolean;|api/@ohos.util.d.ts|
|新增API|NA|类名：types；<br>API声明：isStringObject(value: Object): boolean;<br>差异内容：isStringObject(value: Object): boolean;|api/@ohos.util.d.ts|
|新增API|NA|类名：types；<br>API声明：isSymbolObject(value: Object): boolean;<br>差异内容：isSymbolObject(value: Object): boolean;|api/@ohos.util.d.ts|
|新增API|NA|类名：types；<br>API声明：isTypedArray(value: Object): boolean;<br>差异内容：isTypedArray(value: Object): boolean;|api/@ohos.util.d.ts|
|新增API|NA|类名：types；<br>API声明：isUint8Array(value: Object): boolean;<br>差异内容：isUint8Array(value: Object): boolean;|api/@ohos.util.d.ts|
|新增API|NA|类名：types；<br>API声明：isUint8ClampedArray(value: Object): boolean;<br>差异内容：isUint8ClampedArray(value: Object): boolean;|api/@ohos.util.d.ts|
|新增API|NA|类名：types；<br>API声明：isUint16Array(value: Object): boolean;<br>差异内容：isUint16Array(value: Object): boolean;|api/@ohos.util.d.ts|
|新增API|NA|类名：types；<br>API声明：isUint32Array(value: Object): boolean;<br>差异内容：isUint32Array(value: Object): boolean;|api/@ohos.util.d.ts|
|新增API|NA|类名：types；<br>API声明：isWeakMap(value: Object): boolean;<br>差异内容：isWeakMap(value: Object): boolean;|api/@ohos.util.d.ts|
|新增API|NA|类名：types；<br>API声明：isWeakSet(value: Object): boolean;<br>差异内容：isWeakSet(value: Object): boolean;|api/@ohos.util.d.ts|
|新增API|NA|类名：util；<br>API声明：class Aspect<br>差异内容：class Aspect|api/@ohos.util.d.ts|
|新增API|NA|类名：Aspect；<br>API声明：static addBefore(targetClass: Object, methodName: string, isStatic: boolean, before: Function): void;<br>差异内容：static addBefore(targetClass: Object, methodName: string, isStatic: boolean, before: Function): void;|api/@ohos.util.d.ts|
|新增API|NA|类名：Aspect；<br>API声明：static addAfter(targetClass: Object, methodName: string, isStatic: boolean, after: Function): void;<br>差异内容：static addAfter(targetClass: Object, methodName: string, isStatic: boolean, after: Function): void;|api/@ohos.util.d.ts|
|新增API|NA|类名：Aspect；<br>API声明：static replace(targetClass: Object, methodName: string, isStatic: boolean, instead: Function): void;<br>差异内容：static replace(targetClass: Object, methodName: string, isStatic: boolean, instead: Function): void;|api/@ohos.util.d.ts|
|新增API|NA|类名：global；<br>API声明：declare class Deque<br>差异内容：declare class Deque|api/@ohos.util.Deque.d.ts|
|新增API|NA|类名：Deque；<br>API声明：length: number;<br>差异内容：length: number;|api/@ohos.util.Deque.d.ts|
|新增API|NA|类名：Deque；<br>API声明：insertFront(element: T): void;<br>差异内容：insertFront(element: T): void;|api/@ohos.util.Deque.d.ts|
|新增API|NA|类名：Deque；<br>API声明：insertEnd(element: T): void;<br>差异内容：insertEnd(element: T): void;|api/@ohos.util.Deque.d.ts|
|新增API|NA|类名：Deque；<br>API声明：has(element: T): boolean;<br>差异内容：has(element: T): boolean;|api/@ohos.util.Deque.d.ts|
|新增API|NA|类名：Deque；<br>API声明：getFirst(): T;<br>差异内容：getFirst(): T;|api/@ohos.util.Deque.d.ts|
|新增API|NA|类名：Deque；<br>API声明：getLast(): T;<br>差异内容：getLast(): T;|api/@ohos.util.Deque.d.ts|
|新增API|NA|类名：Deque；<br>API声明：popFirst(): T;<br>差异内容：popFirst(): T;|api/@ohos.util.Deque.d.ts|
|新增API|NA|类名：Deque；<br>API声明：popLast(): T;<br>差异内容：popLast(): T;|api/@ohos.util.Deque.d.ts|
|新增API|NA|类名：Deque；<br>API声明：forEach(callbackFn: (value: T, index?: number, deque?: Deque\<T>) => void, thisArg?: Object): void;<br>差异内容：forEach(callbackFn: (value: T, index?: number, deque?: Deque\<T>) => void, thisArg?: Object): void;|api/@ohos.util.Deque.d.ts|
|新增API|NA|类名：Deque；<br>API声明：[Symbol.iterator](): IterableIterator\<T>;<br>差异内容：[Symbol.iterator](): IterableIterator\<T>;|api/@ohos.util.Deque.d.ts|
|新增API|NA|类名：global；<br>API声明：declare class HashMap<br>差异内容：declare class HashMap|api/@ohos.util.HashMap.d.ts|
|新增API|NA|类名：HashMap；<br>API声明：length: number;<br>差异内容：length: number;|api/@ohos.util.HashMap.d.ts|
|新增API|NA|类名：HashMap；<br>API声明：isEmpty(): boolean;<br>差异内容：isEmpty(): boolean;|api/@ohos.util.HashMap.d.ts|
|新增API|NA|类名：HashMap；<br>API声明：hasKey(key: K): boolean;<br>差异内容：hasKey(key: K): boolean;|api/@ohos.util.HashMap.d.ts|
|新增API|NA|类名：HashMap；<br>API声明：hasValue(value: V): boolean;<br>差异内容：hasValue(value: V): boolean;|api/@ohos.util.HashMap.d.ts|
|新增API|NA|类名：HashMap；<br>API声明：get(key: K): V;<br>差异内容：get(key: K): V;|api/@ohos.util.HashMap.d.ts|
|新增API|NA|类名：HashMap；<br>API声明：setAll(map: HashMap\<K, V>): void;<br>差异内容：setAll(map: HashMap\<K, V>): void;|api/@ohos.util.HashMap.d.ts|
|新增API|NA|类名：HashMap；<br>API声明：set(key: K, value: V): Object;<br>差异内容：set(key: K, value: V): Object;|api/@ohos.util.HashMap.d.ts|
|新增API|NA|类名：HashMap；<br>API声明：remove(key: K): V;<br>差异内容：remove(key: K): V;|api/@ohos.util.HashMap.d.ts|
|新增API|NA|类名：HashMap；<br>API声明：clear(): void;<br>差异内容：clear(): void;|api/@ohos.util.HashMap.d.ts|
|新增API|NA|类名：HashMap；<br>API声明：keys(): IterableIterator\<K>;<br>差异内容：keys(): IterableIterator\<K>;|api/@ohos.util.HashMap.d.ts|
|新增API|NA|类名：HashMap；<br>API声明：values(): IterableIterator\<V>;<br>差异内容：values(): IterableIterator\<V>;|api/@ohos.util.HashMap.d.ts|
|新增API|NA|类名：HashMap；<br>API声明：replace(key: K, newValue: V): boolean;<br>差异内容：replace(key: K, newValue: V): boolean;|api/@ohos.util.HashMap.d.ts|
|新增API|NA|类名：HashMap；<br>API声明：forEach(callbackFn: (value?: V, key?: K, map?: HashMap\<K, V>) => void, thisArg?: Object): void;<br>差异内容：forEach(callbackFn: (value?: V, key?: K, map?: HashMap\<K, V>) => void, thisArg?: Object): void;|api/@ohos.util.HashMap.d.ts|
|新增API|NA|类名：HashMap；<br>API声明：entries(): IterableIterator\<[<br>        K,<br>        V<br>    ]>;<br>差异内容：entries(): IterableIterator\<[<br>        K,<br>        V<br>    ]>;|api/@ohos.util.HashMap.d.ts|
|新增API|NA|类名：HashMap；<br>API声明：[Symbol.iterator](): IterableIterator\<[<br>        K,<br>        V<br>    ]>;<br>差异内容：[Symbol.iterator](): IterableIterator\<[<br>        K,<br>        V<br>    ]>;|api/@ohos.util.HashMap.d.ts|
|新增API|NA|类名：global；<br>API声明：declare class HashSet<br>差异内容：declare class HashSet|api/@ohos.util.HashSet.d.ts|
|新增API|NA|类名：HashSet；<br>API声明：length: number;<br>差异内容：length: number;|api/@ohos.util.HashSet.d.ts|
|新增API|NA|类名：HashSet；<br>API声明：isEmpty(): boolean;<br>差异内容：isEmpty(): boolean;|api/@ohos.util.HashSet.d.ts|
|新增API|NA|类名：HashSet；<br>API声明：has(value: T): boolean;<br>差异内容：has(value: T): boolean;|api/@ohos.util.HashSet.d.ts|
|新增API|NA|类名：HashSet；<br>API声明：add(value: T): boolean;<br>差异内容：add(value: T): boolean;|api/@ohos.util.HashSet.d.ts|
|新增API|NA|类名：HashSet；<br>API声明：remove(value: T): boolean;<br>差异内容：remove(value: T): boolean;|api/@ohos.util.HashSet.d.ts|
|新增API|NA|类名：HashSet；<br>API声明：clear(): void;<br>差异内容：clear(): void;|api/@ohos.util.HashSet.d.ts|
|新增API|NA|类名：HashSet；<br>API声明：forEach(callbackFn: (value?: T, key?: T, set?: HashSet\<T>) => void, thisArg?: Object): void;<br>差异内容：forEach(callbackFn: (value?: T, key?: T, set?: HashSet\<T>) => void, thisArg?: Object): void;|api/@ohos.util.HashSet.d.ts|
|新增API|NA|类名：HashSet；<br>API声明：values(): IterableIterator\<T>;<br>差异内容：values(): IterableIterator\<T>;|api/@ohos.util.HashSet.d.ts|
|新增API|NA|类名：HashSet；<br>API声明：entries(): IterableIterator\<[<br>        T,<br>        T<br>    ]>;<br>差异内容：entries(): IterableIterator\<[<br>        T,<br>        T<br>    ]>;|api/@ohos.util.HashSet.d.ts|
|新增API|NA|类名：HashSet；<br>API声明：[Symbol.iterator](): IterableIterator\<T>;<br>差异内容：[Symbol.iterator](): IterableIterator\<T>;|api/@ohos.util.HashSet.d.ts|
|新增API|NA|类名：global；<br>API声明：declare class LightWeightMap<br>差异内容：declare class LightWeightMap|api/@ohos.util.LightWeightMap.d.ts|
|新增API|NA|类名：LightWeightMap；<br>API声明：length: number;<br>差异内容：length: number;|api/@ohos.util.LightWeightMap.d.ts|
|新增API|NA|类名：LightWeightMap；<br>API声明：hasAll(map: LightWeightMap\<K, V>): boolean;<br>差异内容：hasAll(map: LightWeightMap\<K, V>): boolean;|api/@ohos.util.LightWeightMap.d.ts|
|新增API|NA|类名：LightWeightMap；<br>API声明：hasKey(key: K): boolean;<br>差异内容：hasKey(key: K): boolean;|api/@ohos.util.LightWeightMap.d.ts|
|新增API|NA|类名：LightWeightMap；<br>API声明：hasValue(value: V): boolean;<br>差异内容：hasValue(value: V): boolean;|api/@ohos.util.LightWeightMap.d.ts|
|新增API|NA|类名：LightWeightMap；<br>API声明：increaseCapacityTo(minimumCapacity: number): void;<br>差异内容：increaseCapacityTo(minimumCapacity: number): void;|api/@ohos.util.LightWeightMap.d.ts|
|新增API|NA|类名：LightWeightMap；<br>API声明：entries(): IterableIterator\<[<br>        K,<br>        V<br>    ]>;<br>差异内容：entries(): IterableIterator\<[<br>        K,<br>        V<br>    ]>;|api/@ohos.util.LightWeightMap.d.ts|
|新增API|NA|类名：LightWeightMap；<br>API声明：get(key: K): V;<br>差异内容：get(key: K): V;|api/@ohos.util.LightWeightMap.d.ts|
|新增API|NA|类名：LightWeightMap；<br>API声明：getIndexOfKey(key: K): number;<br>差异内容：getIndexOfKey(key: K): number;|api/@ohos.util.LightWeightMap.d.ts|
|新增API|NA|类名：LightWeightMap；<br>API声明：getIndexOfValue(value: V): number;<br>差异内容：getIndexOfValue(value: V): number;|api/@ohos.util.LightWeightMap.d.ts|
|新增API|NA|类名：LightWeightMap；<br>API声明：isEmpty(): boolean;<br>差异内容：isEmpty(): boolean;|api/@ohos.util.LightWeightMap.d.ts|
|新增API|NA|类名：LightWeightMap；<br>API声明：getKeyAt(index: number): K;<br>差异内容：getKeyAt(index: number): K;|api/@ohos.util.LightWeightMap.d.ts|
|新增API|NA|类名：LightWeightMap；<br>API声明：keys(): IterableIterator\<K>;<br>差异内容：keys(): IterableIterator\<K>;|api/@ohos.util.LightWeightMap.d.ts|
|新增API|NA|类名：LightWeightMap；<br>API声明：setAll(map: LightWeightMap\<K, V>): void;<br>差异内容：setAll(map: LightWeightMap\<K, V>): void;|api/@ohos.util.LightWeightMap.d.ts|
|新增API|NA|类名：LightWeightMap；<br>API声明：set(key: K, value: V): Object;<br>差异内容：set(key: K, value: V): Object;|api/@ohos.util.LightWeightMap.d.ts|
|新增API|NA|类名：LightWeightMap；<br>API声明：remove(key: K): V;<br>差异内容：remove(key: K): V;|api/@ohos.util.LightWeightMap.d.ts|
|新增API|NA|类名：LightWeightMap；<br>API声明：removeAt(index: number): boolean;<br>差异内容：removeAt(index: number): boolean;|api/@ohos.util.LightWeightMap.d.ts|
|新增API|NA|类名：LightWeightMap；<br>API声明：clear(): void;<br>差异内容：clear(): void;|api/@ohos.util.LightWeightMap.d.ts|
|新增API|NA|类名：LightWeightMap；<br>API声明：setValueAt(index: number, newValue: V): boolean;<br>差异内容：setValueAt(index: number, newValue: V): boolean;|api/@ohos.util.LightWeightMap.d.ts|
|新增API|NA|类名：LightWeightMap；<br>API声明：forEach(callbackFn: (value?: V, key?: K, map?: LightWeightMap\<K, V>) => void, thisArg?: Object): void;<br>差异内容：forEach(callbackFn: (value?: V, key?: K, map?: LightWeightMap\<K, V>) => void, thisArg?: Object): void;|api/@ohos.util.LightWeightMap.d.ts|
|新增API|NA|类名：LightWeightMap；<br>API声明：[Symbol.iterator](): IterableIterator\<[<br>        K,<br>        V<br>    ]>;<br>差异内容：[Symbol.iterator](): IterableIterator\<[<br>        K,<br>        V<br>    ]>;|api/@ohos.util.LightWeightMap.d.ts|
|新增API|NA|类名：LightWeightMap；<br>API声明：toString(): String;<br>差异内容：toString(): String;|api/@ohos.util.LightWeightMap.d.ts|
|新增API|NA|类名：LightWeightMap；<br>API声明：getValueAt(index: number): V;<br>差异内容：getValueAt(index: number): V;|api/@ohos.util.LightWeightMap.d.ts|
|新增API|NA|类名：LightWeightMap；<br>API声明：values(): IterableIterator\<V>;<br>差异内容：values(): IterableIterator\<V>;|api/@ohos.util.LightWeightMap.d.ts|
|新增API|NA|类名：global；<br>API声明：declare class LightWeightSet<br>差异内容：declare class LightWeightSet|api/@ohos.util.LightWeightSet.d.ts|
|新增API|NA|类名：LightWeightSet；<br>API声明：length: number;<br>差异内容：length: number;|api/@ohos.util.LightWeightSet.d.ts|
|新增API|NA|类名：LightWeightSet；<br>API声明：add(obj: T): boolean;<br>差异内容：add(obj: T): boolean;|api/@ohos.util.LightWeightSet.d.ts|
|新增API|NA|类名：LightWeightSet；<br>API声明：addAll(set: LightWeightSet\<T>): boolean;<br>差异内容：addAll(set: LightWeightSet\<T>): boolean;|api/@ohos.util.LightWeightSet.d.ts|
|新增API|NA|类名：LightWeightSet；<br>API声明：hasAll(set: LightWeightSet\<T>): boolean;<br>差异内容：hasAll(set: LightWeightSet\<T>): boolean;|api/@ohos.util.LightWeightSet.d.ts|
|新增API|NA|类名：LightWeightSet；<br>API声明：has(key: T): boolean;<br>差异内容：has(key: T): boolean;|api/@ohos.util.LightWeightSet.d.ts|
|新增API|NA|类名：LightWeightSet；<br>API声明：equal(obj: Object): boolean;<br>差异内容：equal(obj: Object): boolean;|api/@ohos.util.LightWeightSet.d.ts|
|新增API|NA|类名：LightWeightSet；<br>API声明：increaseCapacityTo(minimumCapacity: number): void;<br>差异内容：increaseCapacityTo(minimumCapacity: number): void;|api/@ohos.util.LightWeightSet.d.ts|
|新增API|NA|类名：LightWeightSet；<br>API声明：getIndexOf(key: T): number;<br>差异内容：getIndexOf(key: T): number;|api/@ohos.util.LightWeightSet.d.ts|
|新增API|NA|类名：LightWeightSet；<br>API声明：remove(key: T): T;<br>差异内容：remove(key: T): T;|api/@ohos.util.LightWeightSet.d.ts|
|新增API|NA|类名：LightWeightSet；<br>API声明：removeAt(index: number): boolean;<br>差异内容：removeAt(index: number): boolean;|api/@ohos.util.LightWeightSet.d.ts|
|新增API|NA|类名：LightWeightSet；<br>API声明：clear(): void;<br>差异内容：clear(): void;|api/@ohos.util.LightWeightSet.d.ts|
|新增API|NA|类名：LightWeightSet；<br>API声明：forEach(callbackFn: (value?: T, key?: T, set?: LightWeightSet\<T>) => void, thisArg?: Object): void;<br>差异内容：forEach(callbackFn: (value?: T, key?: T, set?: LightWeightSet\<T>) => void, thisArg?: Object): void;|api/@ohos.util.LightWeightSet.d.ts|
|新增API|NA|类名：LightWeightSet；<br>API声明：[Symbol.iterator](): IterableIterator\<T>;<br>差异内容：[Symbol.iterator](): IterableIterator\<T>;|api/@ohos.util.LightWeightSet.d.ts|
|新增API|NA|类名：LightWeightSet；<br>API声明：toString(): String;<br>差异内容：toString(): String;|api/@ohos.util.LightWeightSet.d.ts|
|新增API|NA|类名：LightWeightSet；<br>API声明：toArray(): Array\<T>;<br>差异内容：toArray(): Array\<T>;|api/@ohos.util.LightWeightSet.d.ts|
|新增API|NA|类名：LightWeightSet；<br>API声明：getValueAt(index: number): T;<br>差异内容：getValueAt(index: number): T;|api/@ohos.util.LightWeightSet.d.ts|
|新增API|NA|类名：LightWeightSet；<br>API声明：values(): IterableIterator\<T>;<br>差异内容：values(): IterableIterator\<T>;|api/@ohos.util.LightWeightSet.d.ts|
|新增API|NA|类名：LightWeightSet；<br>API声明：entries(): IterableIterator\<[<br>        T,<br>        T<br>    ]>;<br>差异内容：entries(): IterableIterator\<[<br>        T,<br>        T<br>    ]>;|api/@ohos.util.LightWeightSet.d.ts|
|新增API|NA|类名：LightWeightSet；<br>API声明：isEmpty(): boolean;<br>差异内容：isEmpty(): boolean;|api/@ohos.util.LightWeightSet.d.ts|
|新增API|NA|类名：global；<br>API声明：declare class LinkedList<br>差异内容：declare class LinkedList|api/@ohos.util.LinkedList.d.ts|
|新增API|NA|类名：LinkedList；<br>API声明：length: number;<br>差异内容：length: number;|api/@ohos.util.LinkedList.d.ts|
|新增API|NA|类名：LinkedList；<br>API声明：add(element: T): boolean;<br>差异内容：add(element: T): boolean;|api/@ohos.util.LinkedList.d.ts|
|新增API|NA|类名：LinkedList；<br>API声明：insert(index: number, element: T): void;<br>差异内容：insert(index: number, element: T): void;|api/@ohos.util.LinkedList.d.ts|
|新增API|NA|类名：LinkedList；<br>API声明：get(index: number): T;<br>差异内容：get(index: number): T;|api/@ohos.util.LinkedList.d.ts|
|新增API|NA|类名：LinkedList；<br>API声明：addFirst(element: T): void;<br>差异内容：addFirst(element: T): void;|api/@ohos.util.LinkedList.d.ts|
|新增API|NA|类名：LinkedList；<br>API声明：removeFirst(): T;<br>差异内容：removeFirst(): T;|api/@ohos.util.LinkedList.d.ts|
|新增API|NA|类名：LinkedList；<br>API声明：removeLast(): T;<br>差异内容：removeLast(): T;|api/@ohos.util.LinkedList.d.ts|
|新增API|NA|类名：LinkedList；<br>API声明：has(element: T): boolean;<br>差异内容：has(element: T): boolean;|api/@ohos.util.LinkedList.d.ts|
|新增API|NA|类名：LinkedList；<br>API声明：getIndexOf(element: T): number;<br>差异内容：getIndexOf(element: T): number;|api/@ohos.util.LinkedList.d.ts|
|新增API|NA|类名：LinkedList；<br>API声明：removeByIndex(index: number): T;<br>差异内容：removeByIndex(index: number): T;|api/@ohos.util.LinkedList.d.ts|
|新增API|NA|类名：LinkedList；<br>API声明：remove(element: T): boolean;<br>差异内容：remove(element: T): boolean;|api/@ohos.util.LinkedList.d.ts|
|新增API|NA|类名：LinkedList；<br>API声明：removeFirstFound(element: T): boolean;<br>差异内容：removeFirstFound(element: T): boolean;|api/@ohos.util.LinkedList.d.ts|
|新增API|NA|类名：LinkedList；<br>API声明：removeLastFound(element: T): boolean;<br>差异内容：removeLastFound(element: T): boolean;|api/@ohos.util.LinkedList.d.ts|
|新增API|NA|类名：LinkedList；<br>API声明：getLastIndexOf(element: T): number;<br>差异内容：getLastIndexOf(element: T): number;|api/@ohos.util.LinkedList.d.ts|
|新增API|NA|类名：LinkedList；<br>API声明：getFirst(): T;<br>差异内容：getFirst(): T;|api/@ohos.util.LinkedList.d.ts|
|新增API|NA|类名：LinkedList；<br>API声明：getLast(): T;<br>差异内容：getLast(): T;|api/@ohos.util.LinkedList.d.ts|
|新增API|NA|类名：LinkedList；<br>API声明：set(index: number, element: T): T;<br>差异内容：set(index: number, element: T): T;|api/@ohos.util.LinkedList.d.ts|
|新增API|NA|类名：LinkedList；<br>API声明：forEach(callbackFn: (value: T, index?: number, LinkedList?: LinkedList\<T>) => void, thisArg?: Object): void;<br>差异内容：forEach(callbackFn: (value: T, index?: number, LinkedList?: LinkedList\<T>) => void, thisArg?: Object): void;|api/@ohos.util.LinkedList.d.ts|
|新增API|NA|类名：LinkedList；<br>API声明：clear(): void;<br>差异内容：clear(): void;|api/@ohos.util.LinkedList.d.ts|
|新增API|NA|类名：LinkedList；<br>API声明：clone(): LinkedList\<T>;<br>差异内容：clone(): LinkedList\<T>;|api/@ohos.util.LinkedList.d.ts|
|新增API|NA|类名：LinkedList；<br>API声明：convertToArray(): Array\<T>;<br>差异内容：convertToArray(): Array\<T>;|api/@ohos.util.LinkedList.d.ts|
|新增API|NA|类名：LinkedList；<br>API声明：[Symbol.iterator](): IterableIterator\<T>;<br>差异内容：[Symbol.iterator](): IterableIterator\<T>;|api/@ohos.util.LinkedList.d.ts|
|新增API|NA|类名：global；<br>API声明：declare class List<br>差异内容：declare class List|api/@ohos.util.List.d.ts|
|新增API|NA|类名：List；<br>API声明：length: number;<br>差异内容：length: number;|api/@ohos.util.List.d.ts|
|新增API|NA|类名：List；<br>API声明：add(element: T): boolean;<br>差异内容：add(element: T): boolean;|api/@ohos.util.List.d.ts|
|新增API|NA|类名：List；<br>API声明：insert(element: T, index: number): void;<br>差异内容：insert(element: T, index: number): void;|api/@ohos.util.List.d.ts|
|新增API|NA|类名：List；<br>API声明：get(index: number): T;<br>差异内容：get(index: number): T;|api/@ohos.util.List.d.ts|
|新增API|NA|类名：List；<br>API声明：has(element: T): boolean;<br>差异内容：has(element: T): boolean;|api/@ohos.util.List.d.ts|
|新增API|NA|类名：List；<br>API声明：getIndexOf(element: T): number;<br>差异内容：getIndexOf(element: T): number;|api/@ohos.util.List.d.ts|
|新增API|NA|类名：List；<br>API声明：removeByIndex(index: number): T;<br>差异内容：removeByIndex(index: number): T;|api/@ohos.util.List.d.ts|
|新增API|NA|类名：List；<br>API声明：remove(element: T): boolean;<br>差异内容：remove(element: T): boolean;|api/@ohos.util.List.d.ts|
|新增API|NA|类名：List；<br>API声明：getLastIndexOf(element: T): number;<br>差异内容：getLastIndexOf(element: T): number;|api/@ohos.util.List.d.ts|
|新增API|NA|类名：List；<br>API声明：getFirst(): T;<br>差异内容：getFirst(): T;|api/@ohos.util.List.d.ts|
|新增API|NA|类名：List；<br>API声明：getLast(): T;<br>差异内容：getLast(): T;|api/@ohos.util.List.d.ts|
|新增API|NA|类名：List；<br>API声明：set(index: number, element: T): T;<br>差异内容：set(index: number, element: T): T;|api/@ohos.util.List.d.ts|
|新增API|NA|类名：List；<br>API声明：equal(obj: Object): boolean;<br>差异内容：equal(obj: Object): boolean;|api/@ohos.util.List.d.ts|
|新增API|NA|类名：List；<br>API声明：forEach(callbackFn: (value: T, index?: number, List?: List\<T>) => void, thisArg?: Object): void;<br>差异内容：forEach(callbackFn: (value: T, index?: number, List?: List\<T>) => void, thisArg?: Object): void;|api/@ohos.util.List.d.ts|
|新增API|NA|类名：List；<br>API声明：sort(comparator: (firstValue: T, secondValue: T) => number): void;<br>差异内容：sort(comparator: (firstValue: T, secondValue: T) => number): void;|api/@ohos.util.List.d.ts|
|新增API|NA|类名：List；<br>API声明：clear(): void;<br>差异内容：clear(): void;|api/@ohos.util.List.d.ts|
|新增API|NA|类名：List；<br>API声明：getSubList(fromIndex: number, toIndex: number): List\<T>;<br>差异内容：getSubList(fromIndex: number, toIndex: number): List\<T>;|api/@ohos.util.List.d.ts|
|新增API|NA|类名：List；<br>API声明：replaceAllElements(callbackFn: (value: T, index?: number, list?: List\<T>) => T, thisArg?: Object): void;<br>差异内容：replaceAllElements(callbackFn: (value: T, index?: number, list?: List\<T>) => T, thisArg?: Object): void;|api/@ohos.util.List.d.ts|
|新增API|NA|类名：List；<br>API声明：convertToArray(): Array\<T>;<br>差异内容：convertToArray(): Array\<T>;|api/@ohos.util.List.d.ts|
|新增API|NA|类名：List；<br>API声明：isEmpty(): boolean;<br>差异内容：isEmpty(): boolean;|api/@ohos.util.List.d.ts|
|新增API|NA|类名：List；<br>API声明：[Symbol.iterator](): IterableIterator\<T>;<br>差异内容：[Symbol.iterator](): IterableIterator\<T>;|api/@ohos.util.List.d.ts|
|新增API|NA|类名：global；<br>API声明：declare class PlainArray<br>差异内容：declare class PlainArray|api/@ohos.util.PlainArray.d.ts|
|新增API|NA|类名：PlainArray；<br>API声明：length: number;<br>差异内容：length: number;|api/@ohos.util.PlainArray.d.ts|
|新增API|NA|类名：PlainArray；<br>API声明：add(key: number, value: T): void;<br>差异内容：add(key: number, value: T): void;|api/@ohos.util.PlainArray.d.ts|
|新增API|NA|类名：PlainArray；<br>API声明：clear(): void;<br>差异内容：clear(): void;|api/@ohos.util.PlainArray.d.ts|
|新增API|NA|类名：PlainArray；<br>API声明：clone(): PlainArray\<T>;<br>差异内容：clone(): PlainArray\<T>;|api/@ohos.util.PlainArray.d.ts|
|新增API|NA|类名：PlainArray；<br>API声明：has(key: number): boolean;<br>差异内容：has(key: number): boolean;|api/@ohos.util.PlainArray.d.ts|
|新增API|NA|类名：PlainArray；<br>API声明：get(key: number): T;<br>差异内容：get(key: number): T;|api/@ohos.util.PlainArray.d.ts|
|新增API|NA|类名：PlainArray；<br>API声明：getIndexOfKey(key: number): number;<br>差异内容：getIndexOfKey(key: number): number;|api/@ohos.util.PlainArray.d.ts|
|新增API|NA|类名：PlainArray；<br>API声明：getIndexOfValue(value: T): number;<br>差异内容：getIndexOfValue(value: T): number;|api/@ohos.util.PlainArray.d.ts|
|新增API|NA|类名：PlainArray；<br>API声明：isEmpty(): boolean;<br>差异内容：isEmpty(): boolean;|api/@ohos.util.PlainArray.d.ts|
|新增API|NA|类名：PlainArray；<br>API声明：getKeyAt(index: number): number;<br>差异内容：getKeyAt(index: number): number;|api/@ohos.util.PlainArray.d.ts|
|新增API|NA|类名：PlainArray；<br>API声明：remove(key: number): T;<br>差异内容：remove(key: number): T;|api/@ohos.util.PlainArray.d.ts|
|新增API|NA|类名：PlainArray；<br>API声明：removeAt(index: number): T;<br>差异内容：removeAt(index: number): T;|api/@ohos.util.PlainArray.d.ts|
|新增API|NA|类名：PlainArray；<br>API声明：removeRangeFrom(index: number, size: number): number;<br>差异内容：removeRangeFrom(index: number, size: number): number;|api/@ohos.util.PlainArray.d.ts|
|新增API|NA|类名：PlainArray；<br>API声明：setValueAt(index: number, value: T): void;<br>差异内容：setValueAt(index: number, value: T): void;|api/@ohos.util.PlainArray.d.ts|
|新增API|NA|类名：PlainArray；<br>API声明：toString(): String;<br>差异内容：toString(): String;|api/@ohos.util.PlainArray.d.ts|
|新增API|NA|类名：PlainArray；<br>API声明：getValueAt(index: number): T;<br>差异内容：getValueAt(index: number): T;|api/@ohos.util.PlainArray.d.ts|
|新增API|NA|类名：PlainArray；<br>API声明：forEach(callbackFn: (value: T, index?: number, PlainArray?: PlainArray\<T>) => void, thisArg?: Object): void;<br>差异内容：forEach(callbackFn: (value: T, index?: number, PlainArray?: PlainArray\<T>) => void, thisArg?: Object): void;|api/@ohos.util.PlainArray.d.ts|
|新增API|NA|类名：PlainArray；<br>API声明：[Symbol.iterator](): IterableIterator\<[<br>        number,<br>        T<br>    ]>;<br>差异内容：[Symbol.iterator](): IterableIterator\<[<br>        number,<br>        T<br>    ]>;|api/@ohos.util.PlainArray.d.ts|
|新增API|NA|类名：global；<br>API声明：declare class Queue<br>差异内容：declare class Queue|api/@ohos.util.Queue.d.ts|
|新增API|NA|类名：Queue；<br>API声明：length: number;<br>差异内容：length: number;|api/@ohos.util.Queue.d.ts|
|新增API|NA|类名：Queue；<br>API声明：add(element: T): boolean;<br>差异内容：add(element: T): boolean;|api/@ohos.util.Queue.d.ts|
|新增API|NA|类名：Queue；<br>API声明：getFirst(): T;<br>差异内容：getFirst(): T;|api/@ohos.util.Queue.d.ts|
|新增API|NA|类名：Queue；<br>API声明：pop(): T;<br>差异内容：pop(): T;|api/@ohos.util.Queue.d.ts|
|新增API|NA|类名：Queue；<br>API声明：forEach(callbackFn: (value: T, index?: number, Queue?: Queue\<T>) => void, thisArg?: Object): void;<br>差异内容：forEach(callbackFn: (value: T, index?: number, Queue?: Queue\<T>) => void, thisArg?: Object): void;|api/@ohos.util.Queue.d.ts|
|新增API|NA|类名：Queue；<br>API声明：[Symbol.iterator](): IterableIterator\<T>;<br>差异内容：[Symbol.iterator](): IterableIterator\<T>;|api/@ohos.util.Queue.d.ts|
|新增API|NA|类名：global；<br>API声明：declare class Stack<br>差异内容：declare class Stack|api/@ohos.util.Stack.d.ts|
|新增API|NA|类名：Stack；<br>API声明：length: number;<br>差异内容：length: number;|api/@ohos.util.Stack.d.ts|
|新增API|NA|类名：Stack；<br>API声明：isEmpty(): boolean;<br>差异内容：isEmpty(): boolean;|api/@ohos.util.Stack.d.ts|
|新增API|NA|类名：Stack；<br>API声明：peek(): T;<br>差异内容：peek(): T;|api/@ohos.util.Stack.d.ts|
|新增API|NA|类名：Stack；<br>API声明：pop(): T;<br>差异内容：pop(): T;|api/@ohos.util.Stack.d.ts|
|新增API|NA|类名：Stack；<br>API声明：push(item: T): T;<br>差异内容：push(item: T): T;|api/@ohos.util.Stack.d.ts|
|新增API|NA|类名：Stack；<br>API声明：locate(element: T): number;<br>差异内容：locate(element: T): number;|api/@ohos.util.Stack.d.ts|
|新增API|NA|类名：Stack；<br>API声明：forEach(callbackFn: (value: T, index?: number, stack?: Stack\<T>) => void, thisArg?: Object): void;<br>差异内容：forEach(callbackFn: (value: T, index?: number, stack?: Stack\<T>) => void, thisArg?: Object): void;|api/@ohos.util.Stack.d.ts|
|新增API|NA|类名：Stack；<br>API声明：[Symbol.iterator](): IterableIterator\<T>;<br>差异内容：[Symbol.iterator](): IterableIterator\<T>;|api/@ohos.util.Stack.d.ts|
|新增API|NA|类名：global；<br>API声明：declare class TreeMap<br>差异内容：declare class TreeMap|api/@ohos.util.TreeMap.d.ts|
|新增API|NA|类名：TreeMap；<br>API声明：length: number;<br>差异内容：length: number;|api/@ohos.util.TreeMap.d.ts|
|新增API|NA|类名：TreeMap；<br>API声明：isEmpty(): boolean;<br>差异内容：isEmpty(): boolean;|api/@ohos.util.TreeMap.d.ts|
|新增API|NA|类名：TreeMap；<br>API声明：hasKey(key: K): boolean;<br>差异内容：hasKey(key: K): boolean;|api/@ohos.util.TreeMap.d.ts|
|新增API|NA|类名：TreeMap；<br>API声明：hasValue(value: V): boolean;<br>差异内容：hasValue(value: V): boolean;|api/@ohos.util.TreeMap.d.ts|
|新增API|NA|类名：TreeMap；<br>API声明：get(key: K): V;<br>差异内容：get(key: K): V;|api/@ohos.util.TreeMap.d.ts|
|新增API|NA|类名：TreeMap；<br>API声明：getFirstKey(): K;<br>差异内容：getFirstKey(): K;|api/@ohos.util.TreeMap.d.ts|
|新增API|NA|类名：TreeMap；<br>API声明：getLastKey(): K;<br>差异内容：getLastKey(): K;|api/@ohos.util.TreeMap.d.ts|
|新增API|NA|类名：TreeMap；<br>API声明：setAll(map: TreeMap\<K, V>): void;<br>差异内容：setAll(map: TreeMap\<K, V>): void;|api/@ohos.util.TreeMap.d.ts|
|新增API|NA|类名：TreeMap；<br>API声明：set(key: K, value: V): Object;<br>差异内容：set(key: K, value: V): Object;|api/@ohos.util.TreeMap.d.ts|
|新增API|NA|类名：TreeMap；<br>API声明：remove(key: K): V;<br>差异内容：remove(key: K): V;|api/@ohos.util.TreeMap.d.ts|
|新增API|NA|类名：TreeMap；<br>API声明：clear(): void;<br>差异内容：clear(): void;|api/@ohos.util.TreeMap.d.ts|
|新增API|NA|类名：TreeMap；<br>API声明：getLowerKey(key: K): K;<br>差异内容：getLowerKey(key: K): K;|api/@ohos.util.TreeMap.d.ts|
|新增API|NA|类名：TreeMap；<br>API声明：getHigherKey(key: K): K;<br>差异内容：getHigherKey(key: K): K;|api/@ohos.util.TreeMap.d.ts|
|新增API|NA|类名：TreeMap；<br>API声明：keys(): IterableIterator\<K>;<br>差异内容：keys(): IterableIterator\<K>;|api/@ohos.util.TreeMap.d.ts|
|新增API|NA|类名：TreeMap；<br>API声明：values(): IterableIterator\<V>;<br>差异内容：values(): IterableIterator\<V>;|api/@ohos.util.TreeMap.d.ts|
|新增API|NA|类名：TreeMap；<br>API声明：replace(key: K, newValue: V): boolean;<br>差异内容：replace(key: K, newValue: V): boolean;|api/@ohos.util.TreeMap.d.ts|
|新增API|NA|类名：TreeMap；<br>API声明：forEach(callbackFn: (value?: V, key?: K, map?: TreeMap\<K, V>) => void, thisArg?: Object): void;<br>差异内容：forEach(callbackFn: (value?: V, key?: K, map?: TreeMap\<K, V>) => void, thisArg?: Object): void;|api/@ohos.util.TreeMap.d.ts|
|新增API|NA|类名：TreeMap；<br>API声明：entries(): IterableIterator\<[<br>        K,<br>        V<br>    ]>;<br>差异内容：entries(): IterableIterator\<[<br>        K,<br>        V<br>    ]>;|api/@ohos.util.TreeMap.d.ts|
|新增API|NA|类名：TreeMap；<br>API声明：[Symbol.iterator](): IterableIterator\<[<br>        K,<br>        V<br>    ]>;<br>差异内容：[Symbol.iterator](): IterableIterator\<[<br>        K,<br>        V<br>    ]>;|api/@ohos.util.TreeMap.d.ts|
|新增API|NA|类名：global；<br>API声明：declare class TreeSet<br>差异内容：declare class TreeSet|api/@ohos.util.TreeSet.d.ts|
|新增API|NA|类名：TreeSet；<br>API声明：length: number;<br>差异内容：length: number;|api/@ohos.util.TreeSet.d.ts|
|新增API|NA|类名：TreeSet；<br>API声明：isEmpty(): boolean;<br>差异内容：isEmpty(): boolean;|api/@ohos.util.TreeSet.d.ts|
|新增API|NA|类名：TreeSet；<br>API声明：has(value: T): boolean;<br>差异内容：has(value: T): boolean;|api/@ohos.util.TreeSet.d.ts|
|新增API|NA|类名：TreeSet；<br>API声明：add(value: T): boolean;<br>差异内容：add(value: T): boolean;|api/@ohos.util.TreeSet.d.ts|
|新增API|NA|类名：TreeSet；<br>API声明：remove(value: T): boolean;<br>差异内容：remove(value: T): boolean;|api/@ohos.util.TreeSet.d.ts|
|新增API|NA|类名：TreeSet；<br>API声明：clear(): void;<br>差异内容：clear(): void;|api/@ohos.util.TreeSet.d.ts|
|新增API|NA|类名：TreeSet；<br>API声明：getFirstValue(): T;<br>差异内容：getFirstValue(): T;|api/@ohos.util.TreeSet.d.ts|
|新增API|NA|类名：TreeSet；<br>API声明：getLastValue(): T;<br>差异内容：getLastValue(): T;|api/@ohos.util.TreeSet.d.ts|
|新增API|NA|类名：TreeSet；<br>API声明：getLowerValue(key: T): T;<br>差异内容：getLowerValue(key: T): T;|api/@ohos.util.TreeSet.d.ts|
|新增API|NA|类名：TreeSet；<br>API声明：getHigherValue(key: T): T;<br>差异内容：getHigherValue(key: T): T;|api/@ohos.util.TreeSet.d.ts|
|新增API|NA|类名：TreeSet；<br>API声明：popFirst(): T;<br>差异内容：popFirst(): T;|api/@ohos.util.TreeSet.d.ts|
|新增API|NA|类名：TreeSet；<br>API声明：popLast(): T;<br>差异内容：popLast(): T;|api/@ohos.util.TreeSet.d.ts|
|新增API|NA|类名：TreeSet；<br>API声明：forEach(callbackFn: (value?: T, key?: T, set?: TreeSet\<T>) => void, thisArg?: Object): void;<br>差异内容：forEach(callbackFn: (value?: T, key?: T, set?: TreeSet\<T>) => void, thisArg?: Object): void;|api/@ohos.util.TreeSet.d.ts|
|新增API|NA|类名：TreeSet；<br>API声明：values(): IterableIterator\<T>;<br>差异内容：values(): IterableIterator\<T>;|api/@ohos.util.TreeSet.d.ts|
|新增API|NA|类名：TreeSet；<br>API声明：entries(): IterableIterator\<[<br>        T,<br>        T<br>    ]>;<br>差异内容：entries(): IterableIterator\<[<br>        T,<br>        T<br>    ]>;|api/@ohos.util.TreeSet.d.ts|
|新增API|NA|类名：TreeSet；<br>API声明：[Symbol.iterator](): IterableIterator\<T>;<br>差异内容：[Symbol.iterator](): IterableIterator\<T>;|api/@ohos.util.TreeSet.d.ts|
|新增API|NA|类名：global；<br>API声明：declare class Vector<br>差异内容：declare class Vector|api/@ohos.util.Vector.d.ts|
|新增API|NA|类名：Vector；<br>API声明：length: number;<br>差异内容：length: number;|api/@ohos.util.Vector.d.ts|
|新增API|NA|类名：Vector；<br>API声明：add(element: T): boolean;<br>差异内容：add(element: T): boolean;|api/@ohos.util.Vector.d.ts|
|新增API|NA|类名：Vector；<br>API声明：insert(element: T, index: number): void;<br>差异内容：insert(element: T, index: number): void;|api/@ohos.util.Vector.d.ts|
|新增API|NA|类名：Vector；<br>API声明：has(element: T): boolean;<br>差异内容：has(element: T): boolean;|api/@ohos.util.Vector.d.ts|
|新增API|NA|类名：Vector；<br>API声明：get(index: number): T;<br>差异内容：get(index: number): T;|api/@ohos.util.Vector.d.ts|
|新增API|NA|类名：Vector；<br>API声明：getIndexOf(element: T): number;<br>差异内容：getIndexOf(element: T): number;|api/@ohos.util.Vector.d.ts|
|新增API|NA|类名：Vector；<br>API声明：getFirstElement(): T;<br>差异内容：getFirstElement(): T;|api/@ohos.util.Vector.d.ts|
|新增API|NA|类名：Vector；<br>API声明：getLastElement(): T;<br>差异内容：getLastElement(): T;|api/@ohos.util.Vector.d.ts|
|新增API|NA|类名：Vector；<br>API声明：removeByIndex(index: number): T;<br>差异内容：removeByIndex(index: number): T;|api/@ohos.util.Vector.d.ts|
|新增API|NA|类名：Vector；<br>API声明：remove(element: T): boolean;<br>差异内容：remove(element: T): boolean;|api/@ohos.util.Vector.d.ts|
|新增API|NA|类名：Vector；<br>API声明：set(index: number, element: T): T;<br>差异内容：set(index: number, element: T): T;|api/@ohos.util.Vector.d.ts|
|新增API|NA|类名：Vector；<br>API声明：getLastIndexOf(element: T): number;<br>差异内容：getLastIndexOf(element: T): number;|api/@ohos.util.Vector.d.ts|
|新增API|NA|类名：Vector；<br>API声明：getLastIndexFrom(element: T, index: number): number;<br>差异内容：getLastIndexFrom(element: T, index: number): number;|api/@ohos.util.Vector.d.ts|
|新增API|NA|类名：Vector；<br>API声明：getIndexFrom(element: T, index: number): number;<br>差异内容：getIndexFrom(element: T, index: number): number;|api/@ohos.util.Vector.d.ts|
|新增API|NA|类名：Vector；<br>API声明：removeByRange(fromIndex: number, toIndex: number): void;<br>差异内容：removeByRange(fromIndex: number, toIndex: number): void;|api/@ohos.util.Vector.d.ts|
|新增API|NA|类名：Vector；<br>API声明：replaceAllElements(callbackFn: (value: T, index?: number, vector?: Vector\<T>) => T, thisArg?: Object): void;<br>差异内容：replaceAllElements(callbackFn: (value: T, index?: number, vector?: Vector\<T>) => T, thisArg?: Object): void;|api/@ohos.util.Vector.d.ts|
|新增API|NA|类名：Vector；<br>API声明：forEach(callbackFn: (value: T, index?: number, vector?: Vector\<T>) => void, thisArg?: Object): void;<br>差异内容：forEach(callbackFn: (value: T, index?: number, vector?: Vector\<T>) => void, thisArg?: Object): void;|api/@ohos.util.Vector.d.ts|
|新增API|NA|类名：Vector；<br>API声明：sort(comparator?: (firstValue: T, secondValue: T) => number): void;<br>差异内容：sort(comparator?: (firstValue: T, secondValue: T) => number): void;|api/@ohos.util.Vector.d.ts|
|新增API|NA|类名：Vector；<br>API声明：subVector(fromIndex: number, toIndex: number): Vector\<T>;<br>差异内容：subVector(fromIndex: number, toIndex: number): Vector\<T>;|api/@ohos.util.Vector.d.ts|
|新增API|NA|类名：Vector；<br>API声明：clear(): void;<br>差异内容：clear(): void;|api/@ohos.util.Vector.d.ts|
|新增API|NA|类名：Vector；<br>API声明：clone(): Vector\<T>;<br>差异内容：clone(): Vector\<T>;|api/@ohos.util.Vector.d.ts|
|新增API|NA|类名：Vector；<br>API声明：setLength(newSize: number): void;<br>差异内容：setLength(newSize: number): void;|api/@ohos.util.Vector.d.ts|
|新增API|NA|类名：Vector；<br>API声明：getCapacity(): number;<br>差异内容：getCapacity(): number;|api/@ohos.util.Vector.d.ts|
|新增API|NA|类名：Vector；<br>API声明：convertToArray(): Array\<T>;<br>差异内容：convertToArray(): Array\<T>;|api/@ohos.util.Vector.d.ts|
|新增API|NA|类名：Vector；<br>API声明：isEmpty(): boolean;<br>差异内容：isEmpty(): boolean;|api/@ohos.util.Vector.d.ts|
|新增API|NA|类名：Vector；<br>API声明：increaseCapacityTo(newCapacity: number): void;<br>差异内容：increaseCapacityTo(newCapacity: number): void;|api/@ohos.util.Vector.d.ts|
|新增API|NA|类名：Vector；<br>API声明：toString(): string;<br>差异内容：toString(): string;|api/@ohos.util.Vector.d.ts|
|新增API|NA|类名：Vector；<br>API声明：trimToCurrentLength(): void;<br>差异内容：trimToCurrentLength(): void;|api/@ohos.util.Vector.d.ts|
|新增API|NA|类名：Vector；<br>API声明：copyToArray(array: Array\<T>): void;<br>差异内容：copyToArray(array: Array\<T>): void;|api/@ohos.util.Vector.d.ts|
|新增API|NA|类名：Vector；<br>API声明：[Symbol.iterator](): IterableIterator\<T>;<br>差异内容：[Symbol.iterator](): IterableIterator\<T>;|api/@ohos.util.Vector.d.ts|
|新增API|NA|类名：global；<br>API声明：export interface WorkerOptions<br>差异内容：export interface WorkerOptions|api/@ohos.worker.d.ts|
|新增API|NA|类名：WorkerOptions；<br>API声明：type?: 'classic' \| 'module';<br>差异内容：type?: 'classic' \| 'module';|api/@ohos.worker.d.ts|
|新增API|NA|类名：WorkerOptions；<br>API声明：name?: string;<br>差异内容：name?: string;|api/@ohos.worker.d.ts|
|新增API|NA|类名：WorkerOptions；<br>API声明：shared?: boolean;<br>差异内容：shared?: boolean;|api/@ohos.worker.d.ts|
|新增API|NA|类名：global；<br>API声明：export interface Event<br>差异内容：export interface Event|api/@ohos.worker.d.ts|
|新增API|NA|类名：Event；<br>API声明：readonly type: string;<br>差异内容：readonly type: string;|api/@ohos.worker.d.ts|
|新增API|NA|类名：Event；<br>API声明：readonly timeStamp: number;<br>差异内容：readonly timeStamp: number;|api/@ohos.worker.d.ts|
|新增API|NA|类名：global；<br>API声明：export interface ErrorEvent<br>差异内容：export interface ErrorEvent|api/@ohos.worker.d.ts|
|新增API|NA|类名：ErrorEvent；<br>API声明：readonly message: string;<br>差异内容：readonly message: string;|api/@ohos.worker.d.ts|
|新增API|NA|类名：ErrorEvent；<br>API声明：readonly filename: string;<br>差异内容：readonly filename: string;|api/@ohos.worker.d.ts|
|新增API|NA|类名：ErrorEvent；<br>API声明：readonly lineno: number;<br>差异内容：readonly lineno: number;|api/@ohos.worker.d.ts|
|新增API|NA|类名：ErrorEvent；<br>API声明：readonly colno: number;<br>差异内容：readonly colno: number;|api/@ohos.worker.d.ts|
|新增API|NA|类名：ErrorEvent；<br>API声明：readonly error: Object;<br>差异内容：readonly error: Object;|api/@ohos.worker.d.ts|
|新增API|NA|类名：global；<br>API声明：export interface MessageEvent<br>差异内容：export interface MessageEvent|api/@ohos.worker.d.ts|
|新增API|NA|类名：MessageEvent；<br>API声明：readonly data: T;<br>差异内容：readonly data: T;|api/@ohos.worker.d.ts|
|新增API|NA|类名：global；<br>API声明：export interface MessageEvents<br>差异内容：export interface MessageEvents|api/@ohos.worker.d.ts|
|新增API|NA|类名：MessageEvents；<br>API声明：readonly data;<br>差异内容：readonly data;|api/@ohos.worker.d.ts|
|新增API|NA|类名：global；<br>API声明：export interface PostMessageOptions<br>差异内容：export interface PostMessageOptions|api/@ohos.worker.d.ts|
|新增API|NA|类名：PostMessageOptions；<br>API声明：transfer?: Object[];<br>差异内容：transfer?: Object[];|api/@ohos.worker.d.ts|
|新增API|NA|类名：global；<br>API声明：export interface EventListener<br>差异内容：export interface EventListener|api/@ohos.worker.d.ts|
|新增API|NA|类名：global；<br>API声明：export interface WorkerEventListener<br>差异内容：export interface WorkerEventListener|api/@ohos.worker.d.ts|
|新增API|NA|类名：global；<br>API声明：type MessageType = 'message' \| 'messageerror';<br>差异内容：type MessageType = 'message' \| 'messageerror';|api/@ohos.worker.d.ts|
|新增API|NA|类名：global；<br>API声明：export interface EventTarget<br>差异内容：export interface EventTarget|api/@ohos.worker.d.ts|
|新增API|NA|类名：EventTarget；<br>API声明：addEventListener(type: string, listener: EventListener): void;<br>差异内容：addEventListener(type: string, listener: EventListener): void;|api/@ohos.worker.d.ts|
|新增API|NA|类名：EventTarget；<br>API声明：dispatchEvent(event: Event): boolean;<br>差异内容：dispatchEvent(event: Event): boolean;|api/@ohos.worker.d.ts|
|新增API|NA|类名：EventTarget；<br>API声明：removeEventListener(type: string, callback?: EventListener): void;<br>差异内容：removeEventListener(type: string, callback?: EventListener): void;|api/@ohos.worker.d.ts|
|新增API|NA|类名：EventTarget；<br>API声明：removeAllListener(): void;<br>差异内容：removeAllListener(): void;|api/@ohos.worker.d.ts|
|新增API|NA|类名：global；<br>API声明：export interface WorkerEventTarget<br>差异内容：export interface WorkerEventTarget|api/@ohos.worker.d.ts|
|新增API|NA|类名：WorkerEventTarget；<br>API声明：addEventListener(type: string, listener: WorkerEventListener): void;<br>差异内容：addEventListener(type: string, listener: WorkerEventListener): void;|api/@ohos.worker.d.ts|
|新增API|NA|类名：WorkerEventTarget；<br>API声明：dispatchEvent(event: Event): boolean;<br>差异内容：dispatchEvent(event: Event): boolean;|api/@ohos.worker.d.ts|
|新增API|NA|类名：WorkerEventTarget；<br>API声明：removeEventListener(type: string, callback?: WorkerEventListener): void;<br>差异内容：removeEventListener(type: string, callback?: WorkerEventListener): void;|api/@ohos.worker.d.ts|
|新增API|NA|类名：WorkerEventTarget；<br>API声明：removeAllListener(): void;<br>差异内容：removeAllListener(): void;|api/@ohos.worker.d.ts|
|新增API|NA|类名：global；<br>API声明：declare interface WorkerGlobalScope<br>差异内容：declare interface WorkerGlobalScope|api/@ohos.worker.d.ts|
|新增API|NA|类名：WorkerGlobalScope；<br>API声明：readonly name: string;<br>差异内容：readonly name: string;|api/@ohos.worker.d.ts|
|新增API|NA|类名：WorkerGlobalScope；<br>API声明：onerror?: (ev: ErrorEvent) => void;<br>差异内容：onerror?: (ev: ErrorEvent) => void;|api/@ohos.worker.d.ts|
|新增API|NA|类名：WorkerGlobalScope；<br>API声明：readonly self: WorkerGlobalScope & typeof globalThis;<br>差异内容：readonly self: WorkerGlobalScope & typeof globalThis;|api/@ohos.worker.d.ts|
|新增API|NA|类名：global；<br>API声明：declare interface GlobalScope<br>差异内容：declare interface GlobalScope|api/@ohos.worker.d.ts|
|新增API|NA|类名：GlobalScope；<br>API声明：readonly name: string;<br>差异内容：readonly name: string;|api/@ohos.worker.d.ts|
|新增API|NA|类名：GlobalScope；<br>API声明：onerror?: (ev: ErrorEvent) => void;<br>差异内容：onerror?: (ev: ErrorEvent) => void;|api/@ohos.worker.d.ts|
|新增API|NA|类名：GlobalScope；<br>API声明：readonly self: GlobalScope & typeof globalThis;<br>差异内容：readonly self: GlobalScope & typeof globalThis;|api/@ohos.worker.d.ts|
|新增API|NA|类名：global；<br>API声明：export interface DedicatedWorkerGlobalScope<br>差异内容：export interface DedicatedWorkerGlobalScope|api/@ohos.worker.d.ts|
|新增API|NA|类名：DedicatedWorkerGlobalScope；<br>API声明：onmessage?: (this: DedicatedWorkerGlobalScope, ev: MessageEvent) => void;<br>差异内容：onmessage?: (this: DedicatedWorkerGlobalScope, ev: MessageEvent) => void;|api/@ohos.worker.d.ts|
|新增API|NA|类名：DedicatedWorkerGlobalScope；<br>API声明：onmessageerror?: (this: DedicatedWorkerGlobalScope, ev: MessageEvent) => void;<br>差异内容：onmessageerror?: (this: DedicatedWorkerGlobalScope, ev: MessageEvent) => void;|api/@ohos.worker.d.ts|
|新增API|NA|类名：DedicatedWorkerGlobalScope；<br>API声明：close(): void;<br>差异内容：close(): void;|api/@ohos.worker.d.ts|
|新增API|NA|类名：DedicatedWorkerGlobalScope；<br>API声明：postMessage(messageObject: Object, transfer: Transferable[]): void;<br>差异内容：postMessage(messageObject: Object, transfer: Transferable[]): void;|api/@ohos.worker.d.ts|
|新增API|NA|类名：DedicatedWorkerGlobalScope；<br>API声明：postMessage(messageObject: Object, options?: PostMessageOptions): void;<br>差异内容：postMessage(messageObject: Object, options?: PostMessageOptions): void;|api/@ohos.worker.d.ts|
|新增API|NA|类名：DedicatedWorkerGlobalScope；<br>API声明：postMessage(messageObject: Object, transfer: ArrayBuffer[]): void;<br>差异内容：postMessage(messageObject: Object, transfer: ArrayBuffer[]): void;|api/@ohos.worker.d.ts|
|新增API|NA|类名：global；<br>API声明：export interface ThreadWorkerGlobalScope<br>差异内容：export interface ThreadWorkerGlobalScope|api/@ohos.worker.d.ts|
|新增API|NA|类名：ThreadWorkerGlobalScope；<br>API声明：onmessage?: (this: ThreadWorkerGlobalScope, ev: MessageEvents) => void;<br>差异内容：onmessage?: (this: ThreadWorkerGlobalScope, ev: MessageEvents) => void;|api/@ohos.worker.d.ts|
|新增API|NA|类名：ThreadWorkerGlobalScope；<br>API声明：onmessageerror?: (this: ThreadWorkerGlobalScope, ev: MessageEvents) => void;<br>差异内容：onmessageerror?: (this: ThreadWorkerGlobalScope, ev: MessageEvents) => void;|api/@ohos.worker.d.ts|
|新增API|NA|类名：ThreadWorkerGlobalScope；<br>API声明：close(): void;<br>差异内容：close(): void;|api/@ohos.worker.d.ts|
|新增API|NA|类名：ThreadWorkerGlobalScope；<br>API声明：postMessage(messageObject: Object, transfer: ArrayBuffer[]): void;<br>差异内容：postMessage(messageObject: Object, transfer: ArrayBuffer[]): void;|api/@ohos.worker.d.ts|
|新增API|NA|类名：ThreadWorkerGlobalScope；<br>API声明：postMessage(messageObject: Object, options?: PostMessageOptions): void;<br>差异内容：postMessage(messageObject: Object, options?: PostMessageOptions): void;|api/@ohos.worker.d.ts|
|新增API|NA|类名：ThreadWorkerGlobalScope；<br>API声明：callGlobalCallObjectMethod(instanceName: string, methodName: string, timeout: number, ...args: Object[]): Object;<br>差异内容：callGlobalCallObjectMethod(instanceName: string, methodName: string, timeout: number, ...args: Object[]): Object;|api/@ohos.worker.d.ts|
|新增API|NA|类名：global；<br>API声明：declare namespace worker<br>差异内容：declare namespace worker|api/@ohos.worker.d.ts|
|新增API|NA|类名：worker；<br>API声明：class ThreadWorker<br>差异内容：class ThreadWorker|api/@ohos.worker.d.ts|
|新增API|NA|类名：ThreadWorker；<br>API声明：onexit?: (code: number) => void;<br>差异内容：onexit?: (code: number) => void;|api/@ohos.worker.d.ts|
|新增API|NA|类名：ThreadWorker；<br>API声明：onerror?: (err: ErrorEvent) => void;<br>差异内容：onerror?: (err: ErrorEvent) => void;|api/@ohos.worker.d.ts|
|新增API|NA|类名：ThreadWorker；<br>API声明：onmessage?: (event: MessageEvents) => void;<br>差异内容：onmessage?: (event: MessageEvents) => void;|api/@ohos.worker.d.ts|
|新增API|NA|类名：ThreadWorker；<br>API声明：onmessageerror?: (event: MessageEvents) => void;<br>差异内容：onmessageerror?: (event: MessageEvents) => void;|api/@ohos.worker.d.ts|
|新增API|NA|类名：ThreadWorker；<br>API声明：postMessage(message: Object, transfer: ArrayBuffer[]): void;<br>差异内容：postMessage(message: Object, transfer: ArrayBuffer[]): void;|api/@ohos.worker.d.ts|
|新增API|NA|类名：ThreadWorker；<br>API声明：postMessage(message: Object, options?: PostMessageOptions): void;<br>差异内容：postMessage(message: Object, options?: PostMessageOptions): void;|api/@ohos.worker.d.ts|
|新增API|NA|类名：ThreadWorker；<br>API声明：on(type: string, listener: WorkerEventListener): void;<br>差异内容：on(type: string, listener: WorkerEventListener): void;|api/@ohos.worker.d.ts|
|新增API|NA|类名：ThreadWorker；<br>API声明：once(type: string, listener: WorkerEventListener): void;<br>差异内容：once(type: string, listener: WorkerEventListener): void;|api/@ohos.worker.d.ts|
|新增API|NA|类名：ThreadWorker；<br>API声明：off(type: string, listener?: WorkerEventListener): void;<br>差异内容：off(type: string, listener?: WorkerEventListener): void;|api/@ohos.worker.d.ts|
|新增API|NA|类名：ThreadWorker；<br>API声明：terminate(): void;<br>差异内容：terminate(): void;|api/@ohos.worker.d.ts|
|新增API|NA|类名：ThreadWorker；<br>API声明：addEventListener(type: string, listener: WorkerEventListener): void;<br>差异内容：addEventListener(type: string, listener: WorkerEventListener): void;|api/@ohos.worker.d.ts|
|新增API|NA|类名：ThreadWorker；<br>API声明：dispatchEvent(event: Event): boolean;<br>差异内容：dispatchEvent(event: Event): boolean;|api/@ohos.worker.d.ts|
|新增API|NA|类名：ThreadWorker；<br>API声明：removeEventListener(type: string, callback?: WorkerEventListener): void;<br>差异内容：removeEventListener(type: string, callback?: WorkerEventListener): void;|api/@ohos.worker.d.ts|
|新增API|NA|类名：ThreadWorker；<br>API声明：removeAllListener(): void;<br>差异内容：removeAllListener(): void;|api/@ohos.worker.d.ts|
|新增API|NA|类名：ThreadWorker；<br>API声明：registerGlobalCallObject(instanceName: string, globalCallObject: Object): void;<br>差异内容：registerGlobalCallObject(instanceName: string, globalCallObject: Object): void;|api/@ohos.worker.d.ts|
|新增API|NA|类名：ThreadWorker；<br>API声明：unregisterGlobalCallObject(instanceName?: string): void;<br>差异内容：unregisterGlobalCallObject(instanceName?: string): void;|api/@ohos.worker.d.ts|
|新增API|NA|类名：worker；<br>API声明：class RestrictedWorker<br>差异内容：class RestrictedWorker|api/@ohos.worker.d.ts|
|新增API|NA|类名：worker；<br>API声明：class Worker<br>差异内容：class Worker|api/@ohos.worker.d.ts|
|新增API|NA|类名：Worker；<br>API声明：onexit?: (code: number) => void;<br>差异内容：onexit?: (code: number) => void;|api/@ohos.worker.d.ts|
|新增API|NA|类名：Worker；<br>API声明：onerror?: (err: ErrorEvent) => void;<br>差异内容：onerror?: (err: ErrorEvent) => void;|api/@ohos.worker.d.ts|
|新增API|NA|类名：Worker；<br>API声明：onmessage?: (event: MessageEvent) => void;<br>差异内容：onmessage?: (event: MessageEvent) => void;|api/@ohos.worker.d.ts|
|新增API|NA|类名：Worker；<br>API声明：onmessageerror?: (event: MessageEvent) => void;<br>差异内容：onmessageerror?: (event: MessageEvent) => void;|api/@ohos.worker.d.ts|
|新增API|NA|类名：Worker；<br>API声明：postMessage(message: Object, transfer: ArrayBuffer[]): void;<br>差异内容：postMessage(message: Object, transfer: ArrayBuffer[]): void;|api/@ohos.worker.d.ts|
|新增API|NA|类名：Worker；<br>API声明：postMessage(message: Object, options?: PostMessageOptions): void;<br>差异内容：postMessage(message: Object, options?: PostMessageOptions): void;|api/@ohos.worker.d.ts|
|新增API|NA|类名：Worker；<br>API声明：on(type: string, listener: EventListener): void;<br>差异内容：on(type: string, listener: EventListener): void;|api/@ohos.worker.d.ts|
|新增API|NA|类名：Worker；<br>API声明：once(type: string, listener: EventListener): void;<br>差异内容：once(type: string, listener: EventListener): void;|api/@ohos.worker.d.ts|
|新增API|NA|类名：Worker；<br>API声明：off(type: string, listener?: EventListener): void;<br>差异内容：off(type: string, listener?: EventListener): void;|api/@ohos.worker.d.ts|
|新增API|NA|类名：Worker；<br>API声明：terminate(): void;<br>差异内容：terminate(): void;|api/@ohos.worker.d.ts|
|新增API|NA|类名：worker；<br>API声明：const parentPort: DedicatedWorkerGlobalScope;<br>差异内容：const parentPort: DedicatedWorkerGlobalScope;|api/@ohos.worker.d.ts|
|新增API|NA|类名：worker；<br>API声明：const workerPort: ThreadWorkerGlobalScope;<br>差异内容：const workerPort: ThreadWorkerGlobalScope;|api/@ohos.worker.d.ts|
|新增API|NA|类名：global；<br>API声明：declare namespace xml<br>差异内容：declare namespace xml|api/@ohos.xml.d.ts|
|新增API|NA|类名：xml；<br>API声明：class XmlSerializer<br>差异内容：class XmlSerializer|api/@ohos.xml.d.ts|
|新增API|NA|类名：XmlSerializer；<br>API声明：setAttributes(name: string, value: string): void;<br>差异内容：setAttributes(name: string, value: string): void;|api/@ohos.xml.d.ts|
|新增API|NA|类名：XmlSerializer；<br>API声明：addEmptyElement(name: string): void;<br>差异内容：addEmptyElement(name: string): void;|api/@ohos.xml.d.ts|
|新增API|NA|类名：XmlSerializer；<br>API声明：setDeclaration(): void;<br>差异内容：setDeclaration(): void;|api/@ohos.xml.d.ts|
|新增API|NA|类名：XmlSerializer；<br>API声明：startElement(name: string): void;<br>差异内容：startElement(name: string): void;|api/@ohos.xml.d.ts|
|新增API|NA|类名：XmlSerializer；<br>API声明：endElement(): void;<br>差异内容：endElement(): void;|api/@ohos.xml.d.ts|
|新增API|NA|类名：XmlSerializer；<br>API声明：setNamespace(prefix: string, namespace: string): void;<br>差异内容：setNamespace(prefix: string, namespace: string): void;|api/@ohos.xml.d.ts|
|新增API|NA|类名：XmlSerializer；<br>API声明：setComment(text: string): void;<br>差异内容：setComment(text: string): void;|api/@ohos.xml.d.ts|
|新增API|NA|类名：XmlSerializer；<br>API声明：setCDATA(text: string): void;<br>差异内容：setCDATA(text: string): void;|api/@ohos.xml.d.ts|
|新增API|NA|类名：XmlSerializer；<br>API声明：setText(text: string): void;<br>差异内容：setText(text: string): void;|api/@ohos.xml.d.ts|
|新增API|NA|类名：XmlSerializer；<br>API声明：setDocType(text: string): void;<br>差异内容：setDocType(text: string): void;|api/@ohos.xml.d.ts|
|新增API|NA|类名：xml；<br>API声明：enum EventType<br>差异内容：enum EventType|api/@ohos.xml.d.ts|
|新增API|NA|类名：EventType；<br>API声明：START_DOCUMENT<br>差异内容：START_DOCUMENT|api/@ohos.xml.d.ts|
|新增API|NA|类名：EventType；<br>API声明：END_DOCUMENT<br>差异内容：END_DOCUMENT|api/@ohos.xml.d.ts|
|新增API|NA|类名：EventType；<br>API声明：START_TAG<br>差异内容：START_TAG|api/@ohos.xml.d.ts|
|新增API|NA|类名：EventType；<br>API声明：END_TAG<br>差异内容：END_TAG|api/@ohos.xml.d.ts|
|新增API|NA|类名：EventType；<br>API声明：TEXT<br>差异内容：TEXT|api/@ohos.xml.d.ts|
|新增API|NA|类名：EventType；<br>API声明：CDSECT<br>差异内容：CDSECT|api/@ohos.xml.d.ts|
|新增API|NA|类名：EventType；<br>API声明：COMMENT<br>差异内容：COMMENT|api/@ohos.xml.d.ts|
|新增API|NA|类名：EventType；<br>API声明：DOCDECL<br>差异内容：DOCDECL|api/@ohos.xml.d.ts|
|新增API|NA|类名：EventType；<br>API声明：INSTRUCTION<br>差异内容：INSTRUCTION|api/@ohos.xml.d.ts|
|新增API|NA|类名：EventType；<br>API声明：ENTITY_REFERENCE<br>差异内容：ENTITY_REFERENCE|api/@ohos.xml.d.ts|
|新增API|NA|类名：EventType；<br>API声明：WHITESPACE<br>差异内容：WHITESPACE|api/@ohos.xml.d.ts|
|新增API|NA|类名：xml；<br>API声明：interface ParseInfo<br>差异内容：interface ParseInfo|api/@ohos.xml.d.ts|
|新增API|NA|类名：ParseInfo；<br>API声明：getColumnNumber(): number;<br>差异内容：getColumnNumber(): number;|api/@ohos.xml.d.ts|
|新增API|NA|类名：ParseInfo；<br>API声明：getDepth(): number;<br>差异内容：getDepth(): number;|api/@ohos.xml.d.ts|
|新增API|NA|类名：ParseInfo；<br>API声明：getLineNumber(): number;<br>差异内容：getLineNumber(): number;|api/@ohos.xml.d.ts|
|新增API|NA|类名：ParseInfo；<br>API声明：getName(): string;<br>差异内容：getName(): string;|api/@ohos.xml.d.ts|
|新增API|NA|类名：ParseInfo；<br>API声明：getNamespace(): string;<br>差异内容：getNamespace(): string;|api/@ohos.xml.d.ts|
|新增API|NA|类名：ParseInfo；<br>API声明：getPrefix(): string;<br>差异内容：getPrefix(): string;|api/@ohos.xml.d.ts|
|新增API|NA|类名：ParseInfo；<br>API声明：getText(): string;<br>差异内容：getText(): string;|api/@ohos.xml.d.ts|
|新增API|NA|类名：ParseInfo；<br>API声明：isEmptyElementTag(): boolean;<br>差异内容：isEmptyElementTag(): boolean;|api/@ohos.xml.d.ts|
|新增API|NA|类名：ParseInfo；<br>API声明：isWhitespace(): boolean;<br>差异内容：isWhitespace(): boolean;|api/@ohos.xml.d.ts|
|新增API|NA|类名：ParseInfo；<br>API声明：getAttributeCount(): number;<br>差异内容：getAttributeCount(): number;|api/@ohos.xml.d.ts|
|新增API|NA|类名：xml；<br>API声明：interface ParseOptions<br>差异内容：interface ParseOptions|api/@ohos.xml.d.ts|
|新增API|NA|类名：ParseOptions；<br>API声明：supportDoctype?: boolean;<br>差异内容：supportDoctype?: boolean;|api/@ohos.xml.d.ts|
|新增API|NA|类名：ParseOptions；<br>API声明：ignoreNameSpace?: boolean;<br>差异内容：ignoreNameSpace?: boolean;|api/@ohos.xml.d.ts|
|新增API|NA|类名：ParseOptions；<br>API声明：tagValueCallbackFunction?: (name: string, value: string) => boolean;<br>差异内容：tagValueCallbackFunction?: (name: string, value: string) => boolean;|api/@ohos.xml.d.ts|
|新增API|NA|类名：ParseOptions；<br>API声明：attributeValueCallbackFunction?: (name: string, value: string) => boolean;<br>差异内容：attributeValueCallbackFunction?: (name: string, value: string) => boolean;|api/@ohos.xml.d.ts|
|新增API|NA|类名：ParseOptions；<br>API声明：tokenValueCallbackFunction?: (eventType: EventType, value: ParseInfo) => boolean;<br>差异内容：tokenValueCallbackFunction?: (eventType: EventType, value: ParseInfo) => boolean;|api/@ohos.xml.d.ts|
|新增API|NA|类名：xml；<br>API声明：class XmlPullParser<br>差异内容：class XmlPullParser|api/@ohos.xml.d.ts|
|新增API|NA|类名：XmlPullParser；<br>API声明：parse(option: ParseOptions): void;<br>差异内容：parse(option: ParseOptions): void;|api/@ohos.xml.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\@ohos.buffer.d.ts<br>差异内容：ArkTS|api/@ohos.buffer.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\@ohos.convertxml.d.ts<br>差异内容：ArkTS|api/@ohos.convertxml.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\@ohos.process.d.ts<br>差异内容：ArkTS|api/@ohos.process.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\@ohos.taskpool.d.ts<br>差异内容：ArkTS|api/@ohos.taskpool.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\@ohos.uri.d.ts<br>差异内容：ArkTS|api/@ohos.uri.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\@ohos.url.d.ts<br>差异内容：ArkTS|api/@ohos.url.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\@ohos.util.ArrayList.d.ts<br>差异内容：ArkTS|api/@ohos.util.ArrayList.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\@ohos.util.d.ts<br>差异内容：ArkTS|api/@ohos.util.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\@ohos.util.Deque.d.ts<br>差异内容：ArkTS|api/@ohos.util.Deque.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\@ohos.util.HashMap.d.ts<br>差异内容：ArkTS|api/@ohos.util.HashMap.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\@ohos.util.HashSet.d.ts<br>差异内容：ArkTS|api/@ohos.util.HashSet.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\@ohos.util.LightWeightMap.d.ts<br>差异内容：ArkTS|api/@ohos.util.LightWeightMap.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\@ohos.util.LightWeightSet.d.ts<br>差异内容：ArkTS|api/@ohos.util.LightWeightSet.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\@ohos.util.LinkedList.d.ts<br>差异内容：ArkTS|api/@ohos.util.LinkedList.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\@ohos.util.List.d.ts<br>差异内容：ArkTS|api/@ohos.util.List.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\@ohos.util.PlainArray.d.ts<br>差异内容：ArkTS|api/@ohos.util.PlainArray.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\@ohos.util.Queue.d.ts<br>差异内容：ArkTS|api/@ohos.util.Queue.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\@ohos.util.Stack.d.ts<br>差异内容：ArkTS|api/@ohos.util.Stack.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\@ohos.util.TreeMap.d.ts<br>差异内容：ArkTS|api/@ohos.util.TreeMap.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\@ohos.util.TreeSet.d.ts<br>差异内容：ArkTS|api/@ohos.util.TreeSet.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\@ohos.util.Vector.d.ts<br>差异内容：ArkTS|api/@ohos.util.Vector.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\@ohos.worker.d.ts<br>差异内容：ArkTS|api/@ohos.worker.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\@ohos.xml.d.ts<br>差异内容：ArkTS|api/@ohos.xml.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：kits\@kit.ArkTS.d.ts<br>差异内容：ArkTS|kits/@kit.ArkTS.d.ts|
