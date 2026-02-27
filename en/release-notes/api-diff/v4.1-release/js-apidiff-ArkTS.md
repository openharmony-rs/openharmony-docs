| Change Type | Old Version | New Version | d.ts File |
| ---- | ------ | ------ | -------- |
|New API|NA|Class name: global;<br>API declaration: declare namespace buffer<br>Differences: declare namespace buffer|api/@ohos.buffer.d.ts|
|New API|NA|Class name: buffer;<br>API declaration: type BufferEncoding = 'ascii' \| 'utf8' \| 'utf-8' \| 'utf16le' \| 'ucs2' \| 'ucs-2' \| 'base64' \| 'base64url' \| 'latin1' \| 'binary' \| 'hex';<br>Differences: type BufferEncoding = 'ascii' \| 'utf8' \| 'utf-8' \| 'utf16le' \| 'ucs2' \| 'ucs-2' \| 'base64' \| 'base64url' \| 'latin1' \| 'binary' \| 'hex';|api/@ohos.buffer.d.ts|
|New API|NA|Class name: buffer;<br>API declaration: interface TypedArray<br>Differences: interface TypedArray|api/@ohos.buffer.d.ts|
|New API|NA|Class name: buffer;<br>API declaration: function alloc(size: number, fill?: string \| Buffer \| number, encoding?: BufferEncoding): Buffer;<br>Differences: function alloc(size: number, fill?: string \| Buffer \| number, encoding?: BufferEncoding): Buffer;|api/@ohos.buffer.d.ts|
|New API|NA|Class name: buffer;<br>API declaration: function allocUninitializedFromPool(size: number): Buffer;<br>Differences: function allocUninitializedFromPool(size: number): Buffer;|api/@ohos.buffer.d.ts|
|New API|NA|Class name: buffer;<br>API declaration: function allocUninitialized(size: number): Buffer;<br>Differences: function allocUninitialized(size: number): Buffer;|api/@ohos.buffer.d.ts|
|New API|NA|Class name: buffer;<br>API declaration: function byteLength(string: string \| Buffer \| TypedArray \| DataView \| ArrayBuffer \| SharedArrayBuffer, encoding?: BufferEncoding): number;<br>Differences: function byteLength(string: string \| Buffer \| TypedArray \| DataView \| ArrayBuffer \| SharedArrayBuffer, encoding?: BufferEncoding): number;|api/@ohos.buffer.d.ts|
|New API|NA|Class name: buffer;<br>API declaration: function concat(list: Buffer[] \| Uint8Array[], totalLength?: number): Buffer;<br>Differences: function concat(list: Buffer[] \| Uint8Array[], totalLength?: number): Buffer;|api/@ohos.buffer.d.ts|
|New API|NA|Class name: buffer;<br>API declaration: function from(array: number[]): Buffer;<br>Differences: function from(array: number[]): Buffer;|api/@ohos.buffer.d.ts|
|New API|NA|Class name: buffer;<br>API declaration: function from(arrayBuffer: ArrayBuffer \| SharedArrayBuffer, byteOffset?: number, length?: number): Buffer;<br>Differences: function from(arrayBuffer: ArrayBuffer \| SharedArrayBuffer, byteOffset?: number, length?: number): Buffer;|api/@ohos.buffer.d.ts|
|New API|NA|Class name: buffer;<br>API declaration: function from(buffer: Buffer \| Uint8Array): Buffer;<br>Differences: function from(buffer: Buffer \| Uint8Array): Buffer;|api/@ohos.buffer.d.ts|
|New API|NA|Class name: buffer;<br>API declaration: function from(object: Object, offsetOrEncoding: number \| string, length: number): Buffer;<br>Differences: function from(object: Object, offsetOrEncoding: number \| string, length: number): Buffer;|api/@ohos.buffer.d.ts|
|New API|NA|Class name: buffer;<br>API declaration: function from(string: String, encoding?: BufferEncoding): Buffer;<br>Differences: function from(string: String, encoding?: BufferEncoding): Buffer;|api/@ohos.buffer.d.ts|
|New API|NA|Class name: buffer;<br>API declaration: function isBuffer(obj: Object): boolean;<br>Differences: function isBuffer(obj: Object): boolean;|api/@ohos.buffer.d.ts|
|New API|NA|Class name: buffer;<br>API declaration: function isEncoding(encoding: string): boolean;<br>Differences: function isEncoding(encoding: string): boolean;|api/@ohos.buffer.d.ts|
|New API|NA|Class name: buffer;<br>API declaration: function compare(buf1: Buffer \| Uint8Array, buf2: Buffer \| Uint8Array): -1 \| 0 \| 1;<br>Differences: function compare(buf1: Buffer \| Uint8Array, buf2: Buffer \| Uint8Array): -1 \| 0 \| 1;|api/@ohos.buffer.d.ts|
|New API|NA|Class name: buffer;<br>API declaration: function transcode(source: Buffer \| Uint8Array, fromEnc: string, toEnc: string): Buffer;<br>Differences: function transcode(source: Buffer \| Uint8Array, fromEnc: string, toEnc: string): Buffer;|api/@ohos.buffer.d.ts|
|New API|NA|Class name: buffer;<br>API declaration: class Buffer<br>Differences: class Buffer|api/@ohos.buffer.d.ts|
|New API|NA|Class name: Buffer;<br>API declaration: length: number;<br>Differences: length: number;|api/@ohos.buffer.d.ts|
|New API|NA|Class name: Buffer;<br>API declaration: buffer: ArrayBuffer;<br>Differences: buffer: ArrayBuffer;|api/@ohos.buffer.d.ts|
|New API|NA|Class name: Buffer;<br>API declaration: byteOffset: number;<br>Differences: byteOffset: number;|api/@ohos.buffer.d.ts|
|New API|NA|Class name: Buffer;<br>API declaration: fill(value: string \| Buffer \| Uint8Array \| number, offset?: number, end?: number, encoding?: BufferEncoding): Buffer;<br>Differences: fill(value: string \| Buffer \| Uint8Array \| number, offset?: number, end?: number, encoding?: BufferEncoding): Buffer;|api/@ohos.buffer.d.ts|
|New API|NA|Class name: Buffer;<br>API declaration: compare(target: Buffer \| Uint8Array, targetStart?: number, targetEnd?: number, sourceStart?: number, sourceEnd?: number): -1 \| 0 \| 1;<br>Differences: compare(target: Buffer \| Uint8Array, targetStart?: number, targetEnd?: number, sourceStart?: number, sourceEnd?: number): -1 \| 0 \| 1;|api/@ohos.buffer.d.ts|
|New API|NA|Class name: Buffer;<br>API declaration: copy(target: Buffer \| Uint8Array, targetStart?: number, sourceStart?: number, sourceEnd?: number): number;<br>Differences: copy(target: Buffer \| Uint8Array, targetStart?: number, sourceStart?: number, sourceEnd?: number): number;|api/@ohos.buffer.d.ts|
|New API|NA|Class name: Buffer;<br>API declaration: equals(otherBuffer: Uint8Array \| Buffer): boolean;<br>Differences: equals(otherBuffer: Uint8Array \| Buffer): boolean;|api/@ohos.buffer.d.ts|
|New API|NA|Class name: Buffer;<br>API declaration: includes(value: string \| number \| Buffer \| Uint8Array, byteOffset?: number, encoding?: BufferEncoding): boolean;<br>Differences: includes(value: string \| number \| Buffer \| Uint8Array, byteOffset?: number, encoding?: BufferEncoding): boolean;|api/@ohos.buffer.d.ts|
|New API|NA|Class name: Buffer;<br>API declaration: indexOf(value: string \| number \| Buffer \| Uint8Array, byteOffset?: number, encoding?: BufferEncoding): number;<br>Differences: indexOf(value: string \| number \| Buffer \| Uint8Array, byteOffset?: number, encoding?: BufferEncoding): number;|api/@ohos.buffer.d.ts|
|New API|NA|Class name: Buffer;<br>API declaration: keys(): IterableIterator\<number>;<br>Differences: keys(): IterableIterator\<number>;|api/@ohos.buffer.d.ts|
|New API|NA|Class name: Buffer;<br>API declaration: values(): IterableIterator\<number>;<br>Differences: values(): IterableIterator\<number>;|api/@ohos.buffer.d.ts|
|New API|NA|Class name: Buffer;<br>API declaration: entries(): IterableIterator\<[<br>            number,<br>            number<br>        ]>;<br>Differences: entries(): IterableIterator\<[<br>            number,<br>            number<br>        ]>;|api/@ohos.buffer.d.ts|
|New API|NA|Class name: Buffer;<br>API declaration: lastIndexOf(value: string \| number \| Buffer \| Uint8Array, byteOffset?: number, encoding?: BufferEncoding): number;<br>Differences: lastIndexOf(value: string \| number \| Buffer \| Uint8Array, byteOffset?: number, encoding?: BufferEncoding): number;|api/@ohos.buffer.d.ts|
|New API|NA|Class name: Buffer;<br>API declaration: readBigInt64BE(offset?: number): bigint;<br>Differences: readBigInt64BE(offset?: number): bigint;|api/@ohos.buffer.d.ts|
|New API|NA|Class name: Buffer;<br>API declaration: readBigInt64LE(offset?: number): bigint;<br>Differences: readBigInt64LE(offset?: number): bigint;|api/@ohos.buffer.d.ts|
|New API|NA|Class name: Buffer;<br>API declaration: readBigUInt64BE(offset?: number): bigint;<br>Differences: readBigUInt64BE(offset?: number): bigint;|api/@ohos.buffer.d.ts|
|New API|NA|Class name: Buffer;<br>API declaration: readBigUInt64LE(offset?: number): bigint;<br>Differences: readBigUInt64LE(offset?: number): bigint;|api/@ohos.buffer.d.ts|
|New API|NA|Class name: Buffer;<br>API declaration: readDoubleBE(offset?: number): number;<br>Differences: readDoubleBE(offset?: number): number;|api/@ohos.buffer.d.ts|
|New API|NA|Class name: Buffer;<br>API declaration: readDoubleLE(offset?: number): number;<br>Differences: readDoubleLE(offset?: number): number;|api/@ohos.buffer.d.ts|
|New API|NA|Class name: Buffer;<br>API declaration: readFloatBE(offset?: number): number;<br>Differences: readFloatBE(offset?: number): number;|api/@ohos.buffer.d.ts|
|New API|NA|Class name: Buffer;<br>API declaration: readFloatLE(offset?: number): number;<br>Differences: readFloatLE(offset?: number): number;|api/@ohos.buffer.d.ts|
|New API|NA|Class name: Buffer;<br>API declaration: readInt8(offset?: number): number;<br>Differences: readInt8(offset?: number): number;|api/@ohos.buffer.d.ts|
|New API|NA|Class name: Buffer;<br>API declaration: readInt16BE(offset?: number): number;<br>Differences: readInt16BE(offset?: number): number;|api/@ohos.buffer.d.ts|
|New API|NA|Class name: Buffer;<br>API declaration: readInt16LE(offset?: number): number;<br>Differences: readInt16LE(offset?: number): number;|api/@ohos.buffer.d.ts|
|New API|NA|Class name: Buffer;<br>API declaration: readInt32BE(offset?: number): number;<br>Differences: readInt32BE(offset?: number): number;|api/@ohos.buffer.d.ts|
|New API|NA|Class name: Buffer;<br>API declaration: readInt32LE(offset?: number): number;<br>Differences: readInt32LE(offset?: number): number;|api/@ohos.buffer.d.ts|
|New API|NA|Class name: Buffer;<br>API declaration: readIntBE(offset: number, byteLength: number): number;<br>Differences: readIntBE(offset: number, byteLength: number): number;|api/@ohos.buffer.d.ts|
|New API|NA|Class name: Buffer;<br>API declaration: readIntLE(offset: number, byteLength: number): number;<br>Differences: readIntLE(offset: number, byteLength: number): number;|api/@ohos.buffer.d.ts|
|New API|NA|Class name: Buffer;<br>API declaration: readUInt8(offset?: number): number;<br>Differences: readUInt8(offset?: number): number;|api/@ohos.buffer.d.ts|
|New API|NA|Class name: Buffer;<br>API declaration: readUInt16BE(offset?: number): number;<br>Differences: readUInt16BE(offset?: number): number;|api/@ohos.buffer.d.ts|
|New API|NA|Class name: Buffer;<br>API declaration: readUInt16LE(offset?: number): number;<br>Differences: readUInt16LE(offset?: number): number;|api/@ohos.buffer.d.ts|
|New API|NA|Class name: Buffer;<br>API declaration: readUInt32BE(offset?: number): number;<br>Differences: readUInt32BE(offset?: number): number;|api/@ohos.buffer.d.ts|
|New API|NA|Class name: Buffer;<br>API declaration: readUInt32LE(offset?: number): number;<br>Differences: readUInt32LE(offset?: number): number;|api/@ohos.buffer.d.ts|
|New API|NA|Class name: Buffer;<br>API declaration: readUIntBE(offset: number, byteLength: number): number;<br>Differences: readUIntBE(offset: number, byteLength: number): number;|api/@ohos.buffer.d.ts|
|New API|NA|Class name: Buffer;<br>API declaration: readUIntLE(offset: number, byteLength: number): number;<br>Differences: readUIntLE(offset: number, byteLength: number): number;|api/@ohos.buffer.d.ts|
|New API|NA|Class name: Buffer;<br>API declaration: subarray(start?: number, end?: number): Buffer;<br>Differences: subarray(start?: number, end?: number): Buffer;|api/@ohos.buffer.d.ts|
|New API|NA|Class name: Buffer;<br>API declaration: swap16(): Buffer;<br>Differences: swap16(): Buffer;|api/@ohos.buffer.d.ts|
|New API|NA|Class name: Buffer;<br>API declaration: swap32(): Buffer;<br>Differences: swap32(): Buffer;|api/@ohos.buffer.d.ts|
|New API|NA|Class name: Buffer;<br>API declaration: swap64(): Buffer;<br>Differences: swap64(): Buffer;|api/@ohos.buffer.d.ts|
|New API|NA|Class name: Buffer;<br>API declaration: toJSON(): Object;<br>Differences: toJSON(): Object;|api/@ohos.buffer.d.ts|
|New API|NA|Class name: Buffer;<br>API declaration: toString(encoding?: string, start?: number, end?: number): string;<br>Differences: toString(encoding?: string, start?: number, end?: number): string;|api/@ohos.buffer.d.ts|
|New API|NA|Class name: Buffer;<br>API declaration: write(str: string, offset?: number, length?: number, encoding?: string): number;<br>Differences: write(str: string, offset?: number, length?: number, encoding?: string): number;|api/@ohos.buffer.d.ts|
|New API|NA|Class name: Buffer;<br>API declaration: writeBigInt64BE(value: bigint, offset?: number): number;<br>Differences: writeBigInt64BE(value: bigint, offset?: number): number;|api/@ohos.buffer.d.ts|
|New API|NA|Class name: Buffer;<br>API declaration: writeBigInt64LE(value: bigint, offset?: number): number;<br>Differences: writeBigInt64LE(value: bigint, offset?: number): number;|api/@ohos.buffer.d.ts|
|New API|NA|Class name: Buffer;<br>API declaration: writeBigUInt64BE(value: bigint, offset?: number): number;<br>Differences: writeBigUInt64BE(value: bigint, offset?: number): number;|api/@ohos.buffer.d.ts|
|New API|NA|Class name: Buffer;<br>API declaration: writeBigUInt64LE(value: bigint, offset?: number): number;<br>Differences: writeBigUInt64LE(value: bigint, offset?: number): number;|api/@ohos.buffer.d.ts|
|New API|NA|Class name: Buffer;<br>API declaration: writeDoubleBE(value: number, offset?: number): number;<br>Differences: writeDoubleBE(value: number, offset?: number): number;|api/@ohos.buffer.d.ts|
|New API|NA|Class name: Buffer;<br>API declaration: writeDoubleLE(value: number, offset?: number): number;<br>Differences: writeDoubleLE(value: number, offset?: number): number;|api/@ohos.buffer.d.ts|
|New API|NA|Class name: Buffer;<br>API declaration: writeFloatBE(value: number, offset?: number): number;<br>Differences: writeFloatBE(value: number, offset?: number): number;|api/@ohos.buffer.d.ts|
|New API|NA|Class name: Buffer;<br>API declaration: writeFloatLE(value: number, offset?: number): number;<br>Differences: writeFloatLE(value: number, offset?: number): number;|api/@ohos.buffer.d.ts|
|New API|NA|Class name: Buffer;<br>API declaration: writeInt8(value: number, offset?: number): number;<br>Differences: writeInt8(value: number, offset?: number): number;|api/@ohos.buffer.d.ts|
|New API|NA|Class name: Buffer;<br>API declaration: writeInt16BE(value: number, offset?: number): number;<br>Differences: writeInt16BE(value: number, offset?: number): number;|api/@ohos.buffer.d.ts|
|New API|NA|Class name: Buffer;<br>API declaration: writeInt16LE(value: number, offset?: number): number;<br>Differences: writeInt16LE(value: number, offset?: number): number;|api/@ohos.buffer.d.ts|
|New API|NA|Class name: Buffer;<br>API declaration: writeInt32BE(value: number, offset?: number): number;<br>Differences: writeInt32BE(value: number, offset?: number): number;|api/@ohos.buffer.d.ts|
|New API|NA|Class name: Buffer;<br>API declaration: writeInt32LE(value: number, offset?: number): number;<br>Differences: writeInt32LE(value: number, offset?: number): number;|api/@ohos.buffer.d.ts|
|New API|NA|Class name: Buffer;<br>API declaration: writeIntBE(value: number, offset: number, byteLength: number): number;<br>Differences: writeIntBE(value: number, offset: number, byteLength: number): number;|api/@ohos.buffer.d.ts|
|New API|NA|Class name: Buffer;<br>API declaration: writeIntLE(value: number, offset: number, byteLength: number): number;<br>Differences: writeIntLE(value: number, offset: number, byteLength: number): number;|api/@ohos.buffer.d.ts|
|New API|NA|Class name: Buffer;<br>API declaration: writeUInt8(value: number, offset?: number): number;<br>Differences: writeUInt8(value: number, offset?: number): number;|api/@ohos.buffer.d.ts|
|New API|NA|Class name: Buffer;<br>API declaration: writeUInt16BE(value: number, offset?: number): number;<br>Differences: writeUInt16BE(value: number, offset?: number): number;|api/@ohos.buffer.d.ts|
|New API|NA|Class name: Buffer;<br>API declaration: writeUInt16LE(value: number, offset?: number): number;<br>Differences: writeUInt16LE(value: number, offset?: number): number;|api/@ohos.buffer.d.ts|
|New API|NA|Class name: Buffer;<br>API declaration: writeUInt32BE(value: number, offset?: number): number;<br>Differences: writeUInt32BE(value: number, offset?: number): number;|api/@ohos.buffer.d.ts|
|New API|NA|Class name: Buffer;<br>API declaration: writeUInt32LE(value: number, offset?: number): number;<br>Differences: writeUInt32LE(value: number, offset?: number): number;|api/@ohos.buffer.d.ts|
|New API|NA|Class name: Buffer;<br>API declaration: writeUIntBE(value: number, offset: number, byteLength: number): number;<br>Differences: writeUIntBE(value: number, offset: number, byteLength: number): number;|api/@ohos.buffer.d.ts|
|New API|NA|Class name: Buffer;<br>API declaration: writeUIntLE(value: number, offset: number, byteLength: number): number;<br>Differences: writeUIntLE(value: number, offset: number, byteLength: number): number;|api/@ohos.buffer.d.ts|
|New API|NA|Class name: buffer;<br>API declaration: class Blob<br>Differences: class Blob|api/@ohos.buffer.d.ts|
|New API|NA|Class name: Blob;<br>API declaration: size: number;<br>Differences: size: number;|api/@ohos.buffer.d.ts|
|New API|NA|Class name: Blob;<br>API declaration: type: string;<br>Differences: type: string;|api/@ohos.buffer.d.ts|
|New API|NA|Class name: Blob;<br>API declaration: arrayBuffer(): Promise\<ArrayBuffer>;<br>Differences: arrayBuffer(): Promise\<ArrayBuffer>;|api/@ohos.buffer.d.ts|
|New API|NA|Class name: Blob;<br>API declaration: slice(start?: number, end?: number, type?: string): Blob;<br>Differences: slice(start?: number, end?: number, type?: string): Blob;|api/@ohos.buffer.d.ts|
|New API|NA|Class name: Blob;<br>API declaration: text(): Promise\<string>;<br>Differences: text(): Promise\<string>;|api/@ohos.buffer.d.ts|
|New API|NA|Class name: global;<br>API declaration: declare namespace xml<br>Differences: declare namespace xml|api/@ohos.convertxml.d.ts|
|New API|NA|Class name: xml;<br>API declaration: interface ConvertOptions<br>Differences: interface ConvertOptions|api/@ohos.convertxml.d.ts|
|New API|NA|Class name: ConvertOptions;<br>API declaration: trim: boolean;<br>Differences: trim: boolean;|api/@ohos.convertxml.d.ts|
|New API|NA|Class name: ConvertOptions;<br>API declaration: ignoreDeclaration?: boolean;<br>Differences: ignoreDeclaration?: boolean;|api/@ohos.convertxml.d.ts|
|New API|NA|Class name: ConvertOptions;<br>API declaration: ignoreInstruction?: boolean;<br>Differences: ignoreInstruction?: boolean;|api/@ohos.convertxml.d.ts|
|New API|NA|Class name: ConvertOptions;<br>API declaration: ignoreAttributes?: boolean;<br>Differences: ignoreAttributes?: boolean;|api/@ohos.convertxml.d.ts|
|New API|NA|Class name: ConvertOptions;<br>API declaration: ignoreComment?: boolean;<br>Differences: ignoreComment?: boolean;|api/@ohos.convertxml.d.ts|
|New API|NA|Class name: ConvertOptions;<br>API declaration: ignoreCDATA?: boolean;<br>Differences: ignoreCDATA?: boolean;|api/@ohos.convertxml.d.ts|
|New API|NA|Class name: ConvertOptions;<br>API declaration: ignoreDoctype?: boolean;<br>Differences: ignoreDoctype?: boolean;|api/@ohos.convertxml.d.ts|
|New API|NA|Class name: ConvertOptions;<br>API declaration: ignoreText?: boolean;<br>Differences: ignoreText?: boolean;|api/@ohos.convertxml.d.ts|
|New API|NA|Class name: ConvertOptions;<br>API declaration: declarationKey: string;<br>Differences: declarationKey: string;|api/@ohos.convertxml.d.ts|
|New API|NA|Class name: ConvertOptions;<br>API declaration: instructionKey: string;<br>Differences: instructionKey: string;|api/@ohos.convertxml.d.ts|
|New API|NA|Class name: ConvertOptions;<br>API declaration: attributesKey: string;<br>Differences: attributesKey: string;|api/@ohos.convertxml.d.ts|
|New API|NA|Class name: ConvertOptions;<br>API declaration: textKey: string;<br>Differences: textKey: string;|api/@ohos.convertxml.d.ts|
|New API|NA|Class name: ConvertOptions;<br>API declaration: cdataKey: string;<br>Differences: cdataKey: string;|api/@ohos.convertxml.d.ts|
|New API|NA|Class name: ConvertOptions;<br>API declaration: doctypeKey: string;<br>Differences: doctypeKey: string;|api/@ohos.convertxml.d.ts|
|New API|NA|Class name: ConvertOptions;<br>API declaration: commentKey: string;<br>Differences: commentKey: string;|api/@ohos.convertxml.d.ts|
|New API|NA|Class name: ConvertOptions;<br>API declaration: parentKey: string;<br>Differences: parentKey: string;|api/@ohos.convertxml.d.ts|
|New API|NA|Class name: ConvertOptions;<br>API declaration: typeKey: string;<br>Differences: typeKey: string;|api/@ohos.convertxml.d.ts|
|New API|NA|Class name: ConvertOptions;<br>API declaration: nameKey: string;<br>Differences: nameKey: string;|api/@ohos.convertxml.d.ts|
|New API|NA|Class name: ConvertOptions;<br>API declaration: elementsKey: string;<br>Differences: elementsKey: string;|api/@ohos.convertxml.d.ts|
|New API|NA|Class name: xml;<br>API declaration: class ConvertXML<br>Differences: class ConvertXML|api/@ohos.convertxml.d.ts|
|New API|NA|Class name: ConvertXML;<br>API declaration: convert(xml: string, options?: ConvertOptions): Object;<br>Differences: convert(xml: string, options?: ConvertOptions): Object;|api/@ohos.convertxml.d.ts|
|New API|NA|Class name: ConvertXML;<br>API declaration: convertToJSObject(xml: string, options?: ConvertOptions): Object;<br>Differences: convertToJSObject(xml: string, options?: ConvertOptions): Object;|api/@ohos.convertxml.d.ts|
|New API|NA|Class name: global;<br>API declaration: declare namespace process<br>Differences: declare namespace process|api/@ohos.process.d.ts|
|New API|NA|Class name: process;<br>API declaration: export class ProcessManager<br>Differences: export class ProcessManager|api/@ohos.process.d.ts|
|New API|NA|Class name: ProcessManager;<br>API declaration: isAppUid(v: number): boolean;<br>Differences: isAppUid(v: number): boolean;|api/@ohos.process.d.ts|
|New API|NA|Class name: ProcessManager;<br>API declaration: getUidForName(v: string): number;<br>Differences: getUidForName(v: string): number;|api/@ohos.process.d.ts|
|New API|NA|Class name: ProcessManager;<br>API declaration: getThreadPriority(v: number): number;<br>Differences: getThreadPriority(v: number): number;|api/@ohos.process.d.ts|
|New API|NA|Class name: ProcessManager;<br>API declaration: getSystemConfig(name: number): number;<br>Differences: getSystemConfig(name: number): number;|api/@ohos.process.d.ts|
|New API|NA|Class name: ProcessManager;<br>API declaration: getEnvironmentVar(name: string): string;<br>Differences: getEnvironmentVar(name: string): string;|api/@ohos.process.d.ts|
|New API|NA|Class name: ProcessManager;<br>API declaration: exit(code: number): void;<br>Differences: exit(code: number): void;|api/@ohos.process.d.ts|
|New API|NA|Class name: ProcessManager;<br>API declaration: kill(signal: number, pid: number): boolean;<br>Differences: kill(signal: number, pid: number): boolean;|api/@ohos.process.d.ts|
|New API|NA|Class name: process;<br>API declaration: const uid: number;<br>Differences: const uid: number;|api/@ohos.process.d.ts|
|New API|NA|Class name: process;<br>API declaration: const pid: number;<br>Differences: const pid: number;|api/@ohos.process.d.ts|
|New API|NA|Class name: process;<br>API declaration: const tid: number;<br>Differences: const tid: number;|api/@ohos.process.d.ts|
|New API|NA|Class name: process;<br>API declaration: function isIsolatedProcess(): boolean;<br>Differences: function isIsolatedProcess(): boolean;|api/@ohos.process.d.ts|
|New API|NA|Class name: process;<br>API declaration: function isAppUid(v: number): boolean;<br>Differences: function isAppUid(v: number): boolean;|api/@ohos.process.d.ts|
|New API|NA|Class name: process;<br>API declaration: function is64Bit(): boolean;<br>Differences: function is64Bit(): boolean;|api/@ohos.process.d.ts|
|New API|NA|Class name: process;<br>API declaration: function getUidForName(v: string): number;<br>Differences: function getUidForName(v: string): number;|api/@ohos.process.d.ts|
|New API|NA|Class name: process;<br>API declaration: function getThreadPriority(v: number): number;<br>Differences: function getThreadPriority(v: number): number;|api/@ohos.process.d.ts|
|New API|NA|Class name: process;<br>API declaration: function getStartRealtime(): number;<br>Differences: function getStartRealtime(): number;|api/@ohos.process.d.ts|
|New API|NA|Class name: process;<br>API declaration: function getPastCpuTime(): number;<br>Differences: function getPastCpuTime(): number;|api/@ohos.process.d.ts|
|New API|NA|Class name: process;<br>API declaration: function getSystemConfig(name: number): number;<br>Differences: function getSystemConfig(name: number): number;|api/@ohos.process.d.ts|
|New API|NA|Class name: process;<br>API declaration: function getEnvironmentVar(name: string): string;<br>Differences: function getEnvironmentVar(name: string): string;|api/@ohos.process.d.ts|
|New API|NA|Class name: process;<br>API declaration: type EventListener = (evt: Object) => void;<br>Differences: type EventListener = (evt: Object) => void;|api/@ohos.process.d.ts|
|New API|NA|Class name: process;<br>API declaration: function abort(): void;<br>Differences: function abort(): void;|api/@ohos.process.d.ts|
|New API|NA|Class name: process;<br>API declaration: function exit(code: number): void;<br>Differences: function exit(code: number): void;|api/@ohos.process.d.ts|
|New API|NA|Class name: process;<br>API declaration: function uptime(): number;<br>Differences: function uptime(): number;|api/@ohos.process.d.ts|
|New API|NA|Class name: process;<br>API declaration: function kill(signal: number, pid: number): boolean;<br>Differences: function kill(signal: number, pid: number): boolean;|api/@ohos.process.d.ts|
|New API|NA|Class name: global;<br>API declaration: declare namespace taskpool<br>Differences: declare namespace taskpool|api/@ohos.taskpool.d.ts|
|New API|NA|Class name: taskpool;<br>API declaration: enum Priority<br>Differences: enum Priority|api/@ohos.taskpool.d.ts|
|New API|NA|Class name: Priority;<br>API declaration: HIGH = 0<br>Differences: HIGH = 0|api/@ohos.taskpool.d.ts|
|New API|NA|Class name: Priority;<br>API declaration: MEDIUM = 1<br>Differences: MEDIUM = 1|api/@ohos.taskpool.d.ts|
|New API|NA|Class name: Priority;<br>API declaration: LOW = 2<br>Differences: LOW = 2|api/@ohos.taskpool.d.ts|
|New API|NA|Class name: taskpool;<br>API declaration: class Task<br>Differences: class Task|api/@ohos.taskpool.d.ts|
|New API|NA|Class name: Task;<br>API declaration: static isCanceled(): boolean;<br>Differences: static isCanceled(): boolean;|api/@ohos.taskpool.d.ts|
|New API|NA|Class name: Task;<br>API declaration: static sendData(...args: Object[]): void;<br>Differences: static sendData(...args: Object[]): void;|api/@ohos.taskpool.d.ts|
|New API|NA|Class name: Task;<br>API declaration: setTransferList(transfer?: ArrayBuffer[]): void;<br>Differences: setTransferList(transfer?: ArrayBuffer[]): void;|api/@ohos.taskpool.d.ts|
|New API|NA|Class name: Task;<br>API declaration: setCloneList(cloneList: Object[] \| ArrayBuffer[]): void;<br>Differences: setCloneList(cloneList: Object[] \| ArrayBuffer[]): void;|api/@ohos.taskpool.d.ts|
|New API|NA|Class name: Task;<br>API declaration: onReceiveData(callback?: Function): void;<br>Differences: onReceiveData(callback?: Function): void;|api/@ohos.taskpool.d.ts|
|New API|NA|Class name: Task;<br>API declaration: addDependency(...tasks: Task[]): void;<br>Differences: addDependency(...tasks: Task[]): void;|api/@ohos.taskpool.d.ts|
|New API|NA|Class name: Task;<br>API declaration: removeDependency(...tasks: Task[]): void;<br>Differences: removeDependency(...tasks: Task[]): void;|api/@ohos.taskpool.d.ts|
|New API|NA|Class name: Task;<br>API declaration: function: Function;<br>Differences: function: Function;|api/@ohos.taskpool.d.ts|
|New API|NA|Class name: Task;<br>API declaration: arguments?: Object[];<br>Differences: arguments?: Object[];|api/@ohos.taskpool.d.ts|
|New API|NA|Class name: Task;<br>API declaration: name: string;<br>Differences: name: string;|api/@ohos.taskpool.d.ts|
|New API|NA|Class name: Task;<br>API declaration: totalDuration: number;<br>Differences: totalDuration: number;|api/@ohos.taskpool.d.ts|
|New API|NA|Class name: Task;<br>API declaration: ioDuration: number;<br>Differences: ioDuration: number;|api/@ohos.taskpool.d.ts|
|New API|NA|Class name: Task;<br>API declaration: cpuDuration: number;<br>Differences: cpuDuration: number;|api/@ohos.taskpool.d.ts|
|New API|NA|Class name: taskpool;<br>API declaration: class TaskGroup<br>Differences: class TaskGroup|api/@ohos.taskpool.d.ts|
|New API|NA|Class name: TaskGroup;<br>API declaration: addTask(func: Function, ...args: Object[]): void;<br>Differences: addTask(func: Function, ...args: Object[]): void;|api/@ohos.taskpool.d.ts|
|New API|NA|Class name: TaskGroup;<br>API declaration: addTask(task: Task): void;<br>Differences: addTask(task: Task): void;|api/@ohos.taskpool.d.ts|
|New API|NA|Class name: TaskGroup;<br>API declaration: name: string;<br>Differences: name: string;|api/@ohos.taskpool.d.ts|
|New API|NA|Class name: taskpool;<br>API declaration: class SequenceRunner<br>Differences: class SequenceRunner|api/@ohos.taskpool.d.ts|
|New API|NA|Class name: SequenceRunner;<br>API declaration: execute(task: Task): Promise\<Object>;<br>Differences: execute(task: Task): Promise\<Object>;|api/@ohos.taskpool.d.ts|
|New API|NA|Class name: taskpool;<br>API declaration: enum State<br>Differences: enum State|api/@ohos.taskpool.d.ts|
|New API|NA|Class name: State;<br>API declaration: WAITING = 1<br>Differences: WAITING = 1|api/@ohos.taskpool.d.ts|
|New API|NA|Class name: State;<br>API declaration: RUNNING = 2<br>Differences: RUNNING = 2|api/@ohos.taskpool.d.ts|
|New API|NA|Class name: State;<br>API declaration: CANCELED = 3<br>Differences: CANCELED = 3|api/@ohos.taskpool.d.ts|
|New API|NA|Class name: taskpool;<br>API declaration: class TaskInfo<br>Differences: class TaskInfo|api/@ohos.taskpool.d.ts|
|New API|NA|Class name: TaskInfo;<br>API declaration: taskId: number;<br>Differences: taskId: number;|api/@ohos.taskpool.d.ts|
|New API|NA|Class name: TaskInfo;<br>API declaration: state: State;<br>Differences: state: State;|api/@ohos.taskpool.d.ts|
|New API|NA|Class name: TaskInfo;<br>API declaration: duration?: number;<br>Differences: duration?: number;|api/@ohos.taskpool.d.ts|
|New API|NA|Class name: taskpool;<br>API declaration: class ThreadInfo<br>Differences: class ThreadInfo|api/@ohos.taskpool.d.ts|
|New API|NA|Class name: ThreadInfo;<br>API declaration: tid: number;<br>Differences: tid: number;|api/@ohos.taskpool.d.ts|
|New API|NA|Class name: ThreadInfo;<br>API declaration: taskIds?: number[];<br>Differences: taskIds?: number[];|api/@ohos.taskpool.d.ts|
|New API|NA|Class name: ThreadInfo;<br>API declaration: priority?: Priority;<br>Differences: priority?: Priority;|api/@ohos.taskpool.d.ts|
|New API|NA|Class name: taskpool;<br>API declaration: class TaskPoolInfo<br>Differences: class TaskPoolInfo|api/@ohos.taskpool.d.ts|
|New API|NA|Class name: TaskPoolInfo;<br>API declaration: threadInfos: ThreadInfo[];<br>Differences: threadInfos: ThreadInfo[];|api/@ohos.taskpool.d.ts|
|New API|NA|Class name: TaskPoolInfo;<br>API declaration: taskInfos: TaskInfo[];<br>Differences: taskInfos: TaskInfo[];|api/@ohos.taskpool.d.ts|
|New API|NA|Class name: taskpool;<br>API declaration: function execute(func: Function, ...args: Object[]): Promise\<Object>;<br>Differences: function execute(func: Function, ...args: Object[]): Promise\<Object>;|api/@ohos.taskpool.d.ts|
|New API|NA|Class name: taskpool;<br>API declaration: function execute(task: Task, priority?: Priority): Promise\<Object>;<br>Differences: function execute(task: Task, priority?: Priority): Promise\<Object>;|api/@ohos.taskpool.d.ts|
|New API|NA|Class name: taskpool;<br>API declaration: function execute(group: TaskGroup, priority?: Priority): Promise\<Object[]>;<br>Differences: function execute(group: TaskGroup, priority?: Priority): Promise\<Object[]>;|api/@ohos.taskpool.d.ts|
|New API|NA|Class name: taskpool;<br>API declaration: function executeDelayed(delayTime: number, task: Task, priority?: Priority): Promise\<Object>;<br>Differences: function executeDelayed(delayTime: number, task: Task, priority?: Priority): Promise\<Object>;|api/@ohos.taskpool.d.ts|
|New API|NA|Class name: taskpool;<br>API declaration: function cancel(task: Task): void;<br>Differences: function cancel(task: Task): void;|api/@ohos.taskpool.d.ts|
|New API|NA|Class name: taskpool;<br>API declaration: function cancel(group: TaskGroup): void;<br>Differences: function cancel(group: TaskGroup): void;|api/@ohos.taskpool.d.ts|
|New API|NA|Class name: taskpool;<br>API declaration: function getTaskPoolInfo(): TaskPoolInfo;<br>Differences: function getTaskPoolInfo(): TaskPoolInfo;|api/@ohos.taskpool.d.ts|
|New API|NA|Class name: global;<br>API declaration: declare namespace uri<br>Differences: declare namespace uri|api/@ohos.uri.d.ts|
|New API|NA|Class name: uri;<br>API declaration: class URI<br>Differences: class URI|api/@ohos.uri.d.ts|
|New API|NA|Class name: URI;<br>API declaration: toString(): string;<br>Differences: toString(): string;|api/@ohos.uri.d.ts|
|New API|NA|Class name: URI;<br>API declaration: equals(other: URI): boolean;<br>Differences: equals(other: URI): boolean;|api/@ohos.uri.d.ts|
|New API|NA|Class name: URI;<br>API declaration: equalsTo(other: URI): boolean;<br>Differences: equalsTo(other: URI): boolean;|api/@ohos.uri.d.ts|
|New API|NA|Class name: URI;<br>API declaration: checkIsAbsolute(): boolean;<br>Differences: checkIsAbsolute(): boolean;|api/@ohos.uri.d.ts|
|New API|NA|Class name: URI;<br>API declaration: normalize(): URI;<br>Differences: normalize(): URI;|api/@ohos.uri.d.ts|
|New API|NA|Class name: URI;<br>API declaration: scheme: string;<br>Differences: scheme: string;|api/@ohos.uri.d.ts|
|New API|NA|Class name: URI;<br>API declaration: userInfo: string;<br>Differences: userInfo: string;|api/@ohos.uri.d.ts|
|New API|NA|Class name: URI;<br>API declaration: host: string;<br>Differences: host: string;|api/@ohos.uri.d.ts|
|New API|NA|Class name: URI;<br>API declaration: port: string;<br>Differences: port: string;|api/@ohos.uri.d.ts|
|New API|NA|Class name: URI;<br>API declaration: path: string;<br>Differences: path: string;|api/@ohos.uri.d.ts|
|New API|NA|Class name: URI;<br>API declaration: query: string;<br>Differences: query: string;|api/@ohos.uri.d.ts|
|New API|NA|Class name: URI;<br>API declaration: fragment: string;<br>Differences: fragment: string;|api/@ohos.uri.d.ts|
|New API|NA|Class name: URI;<br>API declaration: authority: string;<br>Differences: authority: string;|api/@ohos.uri.d.ts|
|New API|NA|Class name: URI;<br>API declaration: ssp: string;<br>Differences: ssp: string;|api/@ohos.uri.d.ts|
|New API|NA|Class name: global;<br>API declaration: declare namespace url<br>Differences: declare namespace url|api/@ohos.url.d.ts|
|New API|NA|Class name: url;<br>API declaration: class URLSearchParams<br>Differences: class URLSearchParams|api/@ohos.url.d.ts|
|New API|NA|Class name: URLSearchParams;<br>API declaration: append(name: string, value: string): void;<br>Differences: append(name: string, value: string): void;|api/@ohos.url.d.ts|
|New API|NA|Class name: URLSearchParams;<br>API declaration: delete(name: string): void;<br>Differences: delete(name: string): void;|api/@ohos.url.d.ts|
|New API|NA|Class name: URLSearchParams;<br>API declaration: getAll(name: string): string[];<br>Differences: getAll(name: string): string[];|api/@ohos.url.d.ts|
|New API|NA|Class name: URLSearchParams;<br>API declaration: entries(): IterableIterator\<[<br>            string,<br>            string<br>        ]>;<br>Differences: entries(): IterableIterator\<[<br>            string,<br>            string<br>        ]>;|api/@ohos.url.d.ts|
|New API|NA|Class name: URLSearchParams;<br>API declaration: forEach(callbackFn: (value: string, key: string, searchParams: URLSearchParams) => void, thisArg?: Object): void;<br>Differences: forEach(callbackFn: (value: string, key: string, searchParams: URLSearchParams) => void, thisArg?: Object): void;|api/@ohos.url.d.ts|
|New API|NA|Class name: URLSearchParams;<br>API declaration: get(name: string): string \| null;<br>Differences: get(name: string): string \| null;|api/@ohos.url.d.ts|
|New API|NA|Class name: URLSearchParams;<br>API declaration: has(name: string): boolean;<br>Differences: has(name: string): boolean;|api/@ohos.url.d.ts|
|New API|NA|Class name: URLSearchParams;<br>API declaration: set(name: string, value: string): void;<br>Differences: set(name: string, value: string): void;|api/@ohos.url.d.ts|
|New API|NA|Class name: URLSearchParams;<br>API declaration: sort(): void;<br>Differences: sort(): void;|api/@ohos.url.d.ts|
|New API|NA|Class name: URLSearchParams;<br>API declaration: keys(): IterableIterator\<string>;<br>Differences: keys(): IterableIterator\<string>;|api/@ohos.url.d.ts|
|New API|NA|Class name: URLSearchParams;<br>API declaration: values(): IterableIterator\<string>;<br>Differences: values(): IterableIterator\<string>;|api/@ohos.url.d.ts|
|New API|NA|Class name: URLSearchParams;<br>API declaration: [Symbol.iterator](): IterableIterator\<[<br>            string,<br>            string<br>        ]>;<br>Differences: [Symbol.iterator](): IterableIterator\<[<br>            string,<br>            string<br>        ]>;|api/@ohos.url.d.ts|
|New API|NA|Class name: URLSearchParams;<br>API declaration: toString(): string;<br>Differences: toString(): string;|api/@ohos.url.d.ts|
|New API|NA|Class name: url;<br>API declaration: class URLParams<br>Differences: class URLParams|api/@ohos.url.d.ts|
|New API|NA|Class name: URLParams;<br>API declaration: append(name: string, value: string): void;<br>Differences: append(name: string, value: string): void;|api/@ohos.url.d.ts|
|New API|NA|Class name: URLParams;<br>API declaration: delete(name: string): void;<br>Differences: delete(name: string): void;|api/@ohos.url.d.ts|
|New API|NA|Class name: URLParams;<br>API declaration: getAll(name: string): string[];<br>Differences: getAll(name: string): string[];|api/@ohos.url.d.ts|
|New API|NA|Class name: URLParams;<br>API declaration: entries(): IterableIterator\<[<br>            string,<br>            string<br>        ]>;<br>Differences: entries(): IterableIterator\<[<br>            string,<br>            string<br>        ]>;|api/@ohos.url.d.ts|
|New API|NA|Class name: URLParams;<br>API declaration: forEach(callbackFn: (value: string, key: string, searchParams: URLParams) => void, thisArg?: Object): void;<br>Differences: forEach(callbackFn: (value: string, key: string, searchParams: URLParams) => void, thisArg?: Object): void;|api/@ohos.url.d.ts|
|New API|NA|Class name: URLParams;<br>API declaration: get(name: string): string \| null;<br>Differences: get(name: string): string \| null;|api/@ohos.url.d.ts|
|New API|NA|Class name: URLParams;<br>API declaration: has(name: string): boolean;<br>Differences: has(name: string): boolean;|api/@ohos.url.d.ts|
|New API|NA|Class name: URLParams;<br>API declaration: set(name: string, value: string): void;<br>Differences: set(name: string, value: string): void;|api/@ohos.url.d.ts|
|New API|NA|Class name: URLParams;<br>API declaration: sort(): void;<br>Differences: sort(): void;|api/@ohos.url.d.ts|
|New API|NA|Class name: URLParams;<br>API declaration: keys(): IterableIterator\<string>;<br>Differences: keys(): IterableIterator\<string>;|api/@ohos.url.d.ts|
|New API|NA|Class name: URLParams;<br>API declaration: values(): IterableIterator\<string>;<br>Differences: values(): IterableIterator\<string>;|api/@ohos.url.d.ts|
|New API|NA|Class name: URLParams;<br>API declaration: [Symbol.iterator](): IterableIterator\<[<br>            string,<br>            string<br>        ]>;<br>Differences: [Symbol.iterator](): IterableIterator\<[<br>            string,<br>            string<br>        ]>;|api/@ohos.url.d.ts|
|New API|NA|Class name: URLParams;<br>API declaration: toString(): string;<br>Differences: toString(): string;|api/@ohos.url.d.ts|
|New API|NA|Class name: url;<br>API declaration: class URL<br>Differences: class URL|api/@ohos.url.d.ts|
|New API|NA|Class name: URL;<br>API declaration: static parseURL(url: string, base?: string \| URL): URL;<br>Differences: static parseURL(url: string, base?: string \| URL): URL;|api/@ohos.url.d.ts|
|New API|NA|Class name: URL;<br>API declaration: toString(): string;<br>Differences: toString(): string;|api/@ohos.url.d.ts|
|New API|NA|Class name: URL;<br>API declaration: toJSON(): string;<br>Differences: toJSON(): string;|api/@ohos.url.d.ts|
|New API|NA|Class name: URL;<br>API declaration: hash: string;<br>Differences: hash: string;|api/@ohos.url.d.ts|
|New API|NA|Class name: URL;<br>API declaration: host: string;<br>Differences: host: string;|api/@ohos.url.d.ts|
|New API|NA|Class name: URL;<br>API declaration: hostname: string;<br>Differences: hostname: string;|api/@ohos.url.d.ts|
|New API|NA|Class name: URL;<br>API declaration: href: string;<br>Differences: href: string;|api/@ohos.url.d.ts|
|New API|NA|Class name: URL;<br>API declaration: readonly origin: string;<br>Differences: readonly origin: string;|api/@ohos.url.d.ts|
|New API|NA|Class name: URL;<br>API declaration: password: string;<br>Differences: password: string;|api/@ohos.url.d.ts|
|New API|NA|Class name: URL;<br>API declaration: pathname: string;<br>Differences: pathname: string;|api/@ohos.url.d.ts|
|New API|NA|Class name: URL;<br>API declaration: port: string;<br>Differences: port: string;|api/@ohos.url.d.ts|
|New API|NA|Class name: URL;<br>API declaration: protocol: string;<br>Differences: protocol: string;|api/@ohos.url.d.ts|
|New API|NA|Class name: URL;<br>API declaration: search: string;<br>Differences: search: string;|api/@ohos.url.d.ts|
|New API|NA|Class name: URL;<br>API declaration: readonly searchParams: URLSearchParams;<br>Differences: readonly searchParams: URLSearchParams;|api/@ohos.url.d.ts|
|New API|NA|Class name: URL;<br>API declaration: readonly params: URLParams;<br>Differences: readonly params: URLParams;|api/@ohos.url.d.ts|
|New API|NA|Class name: URL;<br>API declaration: username: string;<br>Differences: username: string;|api/@ohos.url.d.ts|
|New API|NA|Class name: global;<br>API declaration: declare class ArrayList<br>Differences: declare class ArrayList|api/@ohos.util.ArrayList.d.ts|
|New API|NA|Class name: ArrayList;<br>API declaration: length: number;<br>Differences: length: number;|api/@ohos.util.ArrayList.d.ts|
|New API|NA|Class name: ArrayList;<br>API declaration: add(element: T): boolean;<br>Differences: add(element: T): boolean;|api/@ohos.util.ArrayList.d.ts|
|New API|NA|Class name: ArrayList;<br>API declaration: insert(element: T, index: number): void;<br>Differences: insert(element: T, index: number): void;|api/@ohos.util.ArrayList.d.ts|
|New API|NA|Class name: ArrayList;<br>API declaration: has(element: T): boolean;<br>Differences: has(element: T): boolean;|api/@ohos.util.ArrayList.d.ts|
|New API|NA|Class name: ArrayList;<br>API declaration: getIndexOf(element: T): number;<br>Differences: getIndexOf(element: T): number;|api/@ohos.util.ArrayList.d.ts|
|New API|NA|Class name: ArrayList;<br>API declaration: removeByIndex(index: number): T;<br>Differences: removeByIndex(index: number): T;|api/@ohos.util.ArrayList.d.ts|
|New API|NA|Class name: ArrayList;<br>API declaration: remove(element: T): boolean;<br>Differences: remove(element: T): boolean;|api/@ohos.util.ArrayList.d.ts|
|New API|NA|Class name: ArrayList;<br>API declaration: getLastIndexOf(element: T): number;<br>Differences: getLastIndexOf(element: T): number;|api/@ohos.util.ArrayList.d.ts|
|New API|NA|Class name: ArrayList;<br>API declaration: removeByRange(fromIndex: number, toIndex: number): void;<br>Differences: removeByRange(fromIndex: number, toIndex: number): void;|api/@ohos.util.ArrayList.d.ts|
|New API|NA|Class name: ArrayList;<br>API declaration: replaceAllElements(callbackFn: (value: T, index?: number, arrlist?: ArrayList\<T>) => T, thisArg?: Object): void;<br>Differences: replaceAllElements(callbackFn: (value: T, index?: number, arrlist?: ArrayList\<T>) => T, thisArg?: Object): void;|api/@ohos.util.ArrayList.d.ts|
|New API|NA|Class name: ArrayList;<br>API declaration: forEach(callbackFn: (value: T, index?: number, arrlist?: ArrayList\<T>) => void, thisArg?: Object): void;<br>Differences: forEach(callbackFn: (value: T, index?: number, arrlist?: ArrayList\<T>) => void, thisArg?: Object): void;|api/@ohos.util.ArrayList.d.ts|
|New API|NA|Class name: ArrayList;<br>API declaration: sort(comparator?: (firstValue: T, secondValue: T) => number): void;<br>Differences: sort(comparator?: (firstValue: T, secondValue: T) => number): void;|api/@ohos.util.ArrayList.d.ts|
|New API|NA|Class name: ArrayList;<br>API declaration: subArrayList(fromIndex: number, toIndex: number): ArrayList\<T>;<br>Differences: subArrayList(fromIndex: number, toIndex: number): ArrayList\<T>;|api/@ohos.util.ArrayList.d.ts|
|New API|NA|Class name: ArrayList;<br>API declaration: clear(): void;<br>Differences: clear(): void;|api/@ohos.util.ArrayList.d.ts|
|New API|NA|Class name: ArrayList;<br>API declaration: clone(): ArrayList\<T>;<br>Differences: clone(): ArrayList\<T>;|api/@ohos.util.ArrayList.d.ts|
|New API|NA|Class name: ArrayList;<br>API declaration: getCapacity(): number;<br>Differences: getCapacity(): number;|api/@ohos.util.ArrayList.d.ts|
|New API|NA|Class name: ArrayList;<br>API declaration: convertToArray(): Array\<T>;<br>Differences: convertToArray(): Array\<T>;|api/@ohos.util.ArrayList.d.ts|
|New API|NA|Class name: ArrayList;<br>API declaration: isEmpty(): boolean;<br>Differences: isEmpty(): boolean;|api/@ohos.util.ArrayList.d.ts|
|New API|NA|Class name: ArrayList;<br>API declaration: increaseCapacityTo(newCapacity: number): void;<br>Differences: increaseCapacityTo(newCapacity: number): void;|api/@ohos.util.ArrayList.d.ts|
|New API|NA|Class name: ArrayList;<br>API declaration: trimToCurrentLength(): void;<br>Differences: trimToCurrentLength(): void;|api/@ohos.util.ArrayList.d.ts|
|New API|NA|Class name: ArrayList;<br>API declaration: [Symbol.iterator](): IterableIterator\<T>;<br>Differences: [Symbol.iterator](): IterableIterator\<T>;|api/@ohos.util.ArrayList.d.ts|
|New API|NA|Class name: global;<br>API declaration: declare namespace util<br>Differences: declare namespace util|api/@ohos.util.d.ts|
|New API|NA|Class name: util;<br>API declaration: function printf(format: string, ...args: Object[]): string;<br>Differences: function printf(format: string, ...args: Object[]): string;|api/@ohos.util.d.ts|
|New API|NA|Class name: util;<br>API declaration: function format(format: string, ...args: Object[]): string;<br>Differences: function format(format: string, ...args: Object[]): string;|api/@ohos.util.d.ts|
|New API|NA|Class name: util;<br>API declaration: function getErrorString(errno: number): string;<br>Differences: function getErrorString(errno: number): string;|api/@ohos.util.d.ts|
|New API|NA|Class name: util;<br>API declaration: function errnoToString(errno: number): string;<br>Differences: function errnoToString(errno: number): string;|api/@ohos.util.d.ts|
|New API|NA|Class name: util;<br>API declaration: function callbackWrapper(original: Function): (err: Object, value: Object) => void;<br>Differences: function callbackWrapper(original: Function): (err: Object, value: Object) => void;|api/@ohos.util.d.ts|
|New API|NA|Class name: util;<br>API declaration: function promisify(original: (err: Object, value: Object) => void): Function;<br>Differences: function promisify(original: (err: Object, value: Object) => void): Function;|api/@ohos.util.d.ts|
|New API|NA|Class name: util;<br>API declaration: function promiseWrapper(original: (err: Object, value: Object) => void): Object;<br>Differences: function promiseWrapper(original: (err: Object, value: Object) => void): Object;|api/@ohos.util.d.ts|
|New API|NA|Class name: util;<br>API declaration: function generateRandomUUID(entropyCache?: boolean): string;<br>Differences: function generateRandomUUID(entropyCache?: boolean): string;|api/@ohos.util.d.ts|
|New API|NA|Class name: util;<br>API declaration: function generateRandomBinaryUUID(entropyCache?: boolean): Uint8Array;<br>Differences: function generateRandomBinaryUUID(entropyCache?: boolean): Uint8Array;|api/@ohos.util.d.ts|
|New API|NA|Class name: util;<br>API declaration: function parseUUID(uuid: string): Uint8Array;<br>Differences: function parseUUID(uuid: string): Uint8Array;|api/@ohos.util.d.ts|
|New API|NA|Class name: util;<br>API declaration: interface TextDecoderOptions<br>Differences: interface TextDecoderOptions|api/@ohos.util.d.ts|
|New API|NA|Class name: TextDecoderOptions;<br>API declaration: fatal?: boolean;<br>Differences: fatal?: boolean;|api/@ohos.util.d.ts|
|New API|NA|Class name: TextDecoderOptions;<br>API declaration: ignoreBOM?: boolean;<br>Differences: ignoreBOM?: boolean;|api/@ohos.util.d.ts|
|New API|NA|Class name: util;<br>API declaration: interface DecodeWithStreamOptions<br>Differences: interface DecodeWithStreamOptions|api/@ohos.util.d.ts|
|New API|NA|Class name: DecodeWithStreamOptions;<br>API declaration: stream?: boolean;<br>Differences: stream?: boolean;|api/@ohos.util.d.ts|
|New API|NA|Class name: util;<br>API declaration: class TextDecoder<br>Differences: class TextDecoder|api/@ohos.util.d.ts|
|New API|NA|Class name: TextDecoder;<br>API declaration: readonly encoding: string;<br>Differences: readonly encoding: string;|api/@ohos.util.d.ts|
|New API|NA|Class name: TextDecoder;<br>API declaration: readonly fatal: boolean;<br>Differences: readonly fatal: boolean;|api/@ohos.util.d.ts|
|New API|NA|Class name: TextDecoder;<br>API declaration: readonly ignoreBOM = false;<br>Differences: readonly ignoreBOM = false;|api/@ohos.util.d.ts|
|New API|NA|Class name: TextDecoder;<br>API declaration: static create(encoding?: string, options?: TextDecoderOptions): TextDecoder;<br>Differences: static create(encoding?: string, options?: TextDecoderOptions): TextDecoder;|api/@ohos.util.d.ts|
|New API|NA|Class name: TextDecoder;<br>API declaration: decode(input: Uint8Array, options?: {<br>            stream?: false;<br>        }): string;<br>Differences: decode(input: Uint8Array, options?: {<br>            stream?: false;<br>        }): string;|api/@ohos.util.d.ts|
|New API|NA|Class name: TextDecoder;<br>API declaration: decodeWithStream(input: Uint8Array, options?: DecodeWithStreamOptions): string;<br>Differences: decodeWithStream(input: Uint8Array, options?: DecodeWithStreamOptions): string;|api/@ohos.util.d.ts|
|New API|NA|Class name: util;<br>API declaration: interface EncodeIntoUint8ArrayInfo<br>Differences: interface EncodeIntoUint8ArrayInfo|api/@ohos.util.d.ts|
|New API|NA|Class name: EncodeIntoUint8ArrayInfo;<br>API declaration: read: number;<br>Differences: read: number;|api/@ohos.util.d.ts|
|New API|NA|Class name: EncodeIntoUint8ArrayInfo;<br>API declaration: written: number;<br>Differences: written: number;|api/@ohos.util.d.ts|
|New API|NA|Class name: util;<br>API declaration: class TextEncoder<br>Differences: class TextEncoder|api/@ohos.util.d.ts|
|New API|NA|Class name: TextEncoder;<br>API declaration: readonly encoding = 'utf-8';<br>Differences: readonly encoding = 'utf-8';|api/@ohos.util.d.ts|
|New API|NA|Class name: TextEncoder;<br>API declaration: encode(input?: string): Uint8Array;<br>Differences: encode(input?: string): Uint8Array;|api/@ohos.util.d.ts|
|New API|NA|Class name: TextEncoder;<br>API declaration: encodeInto(input?: string): Uint8Array;<br>Differences: encodeInto(input?: string): Uint8Array;|api/@ohos.util.d.ts|
|New API|NA|Class name: TextEncoder;<br>API declaration: encodeInto(input: string, dest: Uint8Array): {<br>            read: number;<br>            written: number;<br>        };<br>Differences: encodeInto(input: string, dest: Uint8Array): {<br>            read: number;<br>            written: number;<br>        };|api/@ohos.util.d.ts|
|New API|NA|Class name: TextEncoder;<br>API declaration: encodeIntoUint8Array(input: string, dest: Uint8Array): EncodeIntoUint8ArrayInfo;<br>Differences: encodeIntoUint8Array(input: string, dest: Uint8Array): EncodeIntoUint8ArrayInfo;|api/@ohos.util.d.ts|
|New API|NA|Class name: util;<br>API declaration: class RationalNumber<br>Differences: class RationalNumber|api/@ohos.util.d.ts|
|New API|NA|Class name: RationalNumber;<br>API declaration: static parseRationalNumber(numerator: number, denominator: number): RationalNumber;<br>Differences: static parseRationalNumber(numerator: number, denominator: number): RationalNumber;|api/@ohos.util.d.ts|
|New API|NA|Class name: RationalNumber;<br>API declaration: static createRationalFromString(rationalString: string): RationalNumber;<br>Differences: static createRationalFromString(rationalString: string): RationalNumber;|api/@ohos.util.d.ts|
|New API|NA|Class name: RationalNumber;<br>API declaration: compareTo(another: RationalNumber): number;<br>Differences: compareTo(another: RationalNumber): number;|api/@ohos.util.d.ts|
|New API|NA|Class name: RationalNumber;<br>API declaration: compare(another: RationalNumber): number;<br>Differences: compare(another: RationalNumber): number;|api/@ohos.util.d.ts|
|New API|NA|Class name: RationalNumber;<br>API declaration: equals(obj: Object): boolean;<br>Differences: equals(obj: Object): boolean;|api/@ohos.util.d.ts|
|New API|NA|Class name: RationalNumber;<br>API declaration: valueOf(): number;<br>Differences: valueOf(): number;|api/@ohos.util.d.ts|
|New API|NA|Class name: RationalNumber;<br>API declaration: static getCommonDivisor(number1: number, number2: number): number;<br>Differences: static getCommonDivisor(number1: number, number2: number): number;|api/@ohos.util.d.ts|
|New API|NA|Class name: RationalNumber;<br>API declaration: static getCommonFactor(number1: number, number2: number): number;<br>Differences: static getCommonFactor(number1: number, number2: number): number;|api/@ohos.util.d.ts|
|New API|NA|Class name: RationalNumber;<br>API declaration: getDenominator(): number;<br>Differences: getDenominator(): number;|api/@ohos.util.d.ts|
|New API|NA|Class name: RationalNumber;<br>API declaration: getNumerator(): number;<br>Differences: getNumerator(): number;|api/@ohos.util.d.ts|
|New API|NA|Class name: RationalNumber;<br>API declaration: isFinite(): boolean;<br>Differences: isFinite(): boolean;|api/@ohos.util.d.ts|
|New API|NA|Class name: RationalNumber;<br>API declaration: isNaN(): boolean;<br>Differences: isNaN(): boolean;|api/@ohos.util.d.ts|
|New API|NA|Class name: RationalNumber;<br>API declaration: isZero(): boolean;<br>Differences: isZero(): boolean;|api/@ohos.util.d.ts|
|New API|NA|Class name: RationalNumber;<br>API declaration: toString(): string;<br>Differences: toString(): string;|api/@ohos.util.d.ts|
|New API|NA|Class name: util;<br>API declaration: class LruBuffer<br>Differences: class LruBuffer|api/@ohos.util.d.ts|
|New API|NA|Class name: LruBuffer;<br>API declaration: updateCapacity(newCapacity: number): void;<br>Differences: updateCapacity(newCapacity: number): void;|api/@ohos.util.d.ts|
|New API|NA|Class name: LruBuffer;<br>API declaration: toString(): string;<br>Differences: toString(): string;|api/@ohos.util.d.ts|
|New API|NA|Class name: LruBuffer;<br>API declaration: length: number;<br>Differences: length: number;|api/@ohos.util.d.ts|
|New API|NA|Class name: LruBuffer;<br>API declaration: getCapacity(): number;<br>Differences: getCapacity(): number;|api/@ohos.util.d.ts|
|New API|NA|Class name: LruBuffer;<br>API declaration: clear(): void;<br>Differences: clear(): void;|api/@ohos.util.d.ts|
|New API|NA|Class name: LruBuffer;<br>API declaration: getCreateCount(): number;<br>Differences: getCreateCount(): number;|api/@ohos.util.d.ts|
|New API|NA|Class name: LruBuffer;<br>API declaration: getMissCount(): number;<br>Differences: getMissCount(): number;|api/@ohos.util.d.ts|
|New API|NA|Class name: LruBuffer;<br>API declaration: getRemovalCount(): number;<br>Differences: getRemovalCount(): number;|api/@ohos.util.d.ts|
|New API|NA|Class name: LruBuffer;<br>API declaration: getMatchCount(): number;<br>Differences: getMatchCount(): number;|api/@ohos.util.d.ts|
|New API|NA|Class name: LruBuffer;<br>API declaration: getPutCount(): number;<br>Differences: getPutCount(): number;|api/@ohos.util.d.ts|
|New API|NA|Class name: LruBuffer;<br>API declaration: isEmpty(): boolean;<br>Differences: isEmpty(): boolean;|api/@ohos.util.d.ts|
|New API|NA|Class name: LruBuffer;<br>API declaration: get(key: K): V \| undefined;<br>Differences: get(key: K): V \| undefined;|api/@ohos.util.d.ts|
|New API|NA|Class name: LruBuffer;<br>API declaration: put(key: K, value: V): V;<br>Differences: put(key: K, value: V): V;|api/@ohos.util.d.ts|
|New API|NA|Class name: LruBuffer;<br>API declaration: values(): V[];<br>Differences: values(): V[];|api/@ohos.util.d.ts|
|New API|NA|Class name: LruBuffer;<br>API declaration: keys(): K[];<br>Differences: keys(): K[];|api/@ohos.util.d.ts|
|New API|NA|Class name: LruBuffer;<br>API declaration: remove(key: K): V \| undefined;<br>Differences: remove(key: K): V \| undefined;|api/@ohos.util.d.ts|
|New API|NA|Class name: LruBuffer;<br>API declaration: afterRemoval(isEvict: boolean, key: K, value: V, newValue: V): void;<br>Differences: afterRemoval(isEvict: boolean, key: K, value: V, newValue: V): void;|api/@ohos.util.d.ts|
|New API|NA|Class name: LruBuffer;<br>API declaration: contains(key: K): boolean;<br>Differences: contains(key: K): boolean;|api/@ohos.util.d.ts|
|New API|NA|Class name: LruBuffer;<br>API declaration: createDefault(key: K): V;<br>Differences: createDefault(key: K): V;|api/@ohos.util.d.ts|
|New API|NA|Class name: LruBuffer;<br>API declaration: entries(): IterableIterator\<[<br>            K,<br>            V<br>        ]>;<br>Differences: entries(): IterableIterator\<[<br>            K,<br>            V<br>        ]>;|api/@ohos.util.d.ts|
|New API|NA|Class name: LruBuffer;<br>API declaration: [Symbol.iterator](): IterableIterator\<[<br>            K,<br>            V<br>        ]>;<br>Differences: [Symbol.iterator](): IterableIterator\<[<br>            K,<br>            V<br>        ]>;|api/@ohos.util.d.ts|
|New API|NA|Class name: util;<br>API declaration: class LRUCache<br>Differences: class LRUCache|api/@ohos.util.d.ts|
|New API|NA|Class name: LRUCache;<br>API declaration: updateCapacity(newCapacity: number): void;<br>Differences: updateCapacity(newCapacity: number): void;|api/@ohos.util.d.ts|
|New API|NA|Class name: LRUCache;<br>API declaration: toString(): string;<br>Differences: toString(): string;|api/@ohos.util.d.ts|
|New API|NA|Class name: LRUCache;<br>API declaration: length: number;<br>Differences: length: number;|api/@ohos.util.d.ts|
|New API|NA|Class name: LRUCache;<br>API declaration: getCapacity(): number;<br>Differences: getCapacity(): number;|api/@ohos.util.d.ts|
|New API|NA|Class name: LRUCache;<br>API declaration: clear(): void;<br>Differences: clear(): void;|api/@ohos.util.d.ts|
|New API|NA|Class name: LRUCache;<br>API declaration: getCreateCount(): number;<br>Differences: getCreateCount(): number;|api/@ohos.util.d.ts|
|New API|NA|Class name: LRUCache;<br>API declaration: getMissCount(): number;<br>Differences: getMissCount(): number;|api/@ohos.util.d.ts|
|New API|NA|Class name: LRUCache;<br>API declaration: getRemovalCount(): number;<br>Differences: getRemovalCount(): number;|api/@ohos.util.d.ts|
|New API|NA|Class name: LRUCache;<br>API declaration: getMatchCount(): number;<br>Differences: getMatchCount(): number;|api/@ohos.util.d.ts|
|New API|NA|Class name: LRUCache;<br>API declaration: getPutCount(): number;<br>Differences: getPutCount(): number;|api/@ohos.util.d.ts|
|New API|NA|Class name: LRUCache;<br>API declaration: isEmpty(): boolean;<br>Differences: isEmpty(): boolean;|api/@ohos.util.d.ts|
|New API|NA|Class name: LRUCache;<br>API declaration: get(key: K): V \| undefined;<br>Differences: get(key: K): V \| undefined;|api/@ohos.util.d.ts|
|New API|NA|Class name: LRUCache;<br>API declaration: put(key: K, value: V): V;<br>Differences: put(key: K, value: V): V;|api/@ohos.util.d.ts|
|New API|NA|Class name: LRUCache;<br>API declaration: values(): V[];<br>Differences: values(): V[];|api/@ohos.util.d.ts|
|New API|NA|Class name: LRUCache;<br>API declaration: keys(): K[];<br>Differences: keys(): K[];|api/@ohos.util.d.ts|
|New API|NA|Class name: LRUCache;<br>API declaration: remove(key: K): V \| undefined;<br>Differences: remove(key: K): V \| undefined;|api/@ohos.util.d.ts|
|New API|NA|Class name: LRUCache;<br>API declaration: afterRemoval(isEvict: boolean, key: K, value: V, newValue: V): void;<br>Differences: afterRemoval(isEvict: boolean, key: K, value: V, newValue: V): void;|api/@ohos.util.d.ts|
|New API|NA|Class name: LRUCache;<br>API declaration: contains(key: K): boolean;<br>Differences: contains(key: K): boolean;|api/@ohos.util.d.ts|
|New API|NA|Class name: LRUCache;<br>API declaration: createDefault(key: K): V;<br>Differences: createDefault(key: K): V;|api/@ohos.util.d.ts|
|New API|NA|Class name: LRUCache;<br>API declaration: entries(): IterableIterator\<[<br>            K,<br>            V<br>        ]>;<br>Differences: entries(): IterableIterator\<[<br>            K,<br>            V<br>        ]>;|api/@ohos.util.d.ts|
|New API|NA|Class name: LRUCache;<br>API declaration: [Symbol.iterator](): IterableIterator\<[<br>            K,<br>            V<br>        ]>;<br>Differences: [Symbol.iterator](): IterableIterator\<[<br>            K,<br>            V<br>        ]>;|api/@ohos.util.d.ts|
|New API|NA|Class name: util;<br>API declaration: interface ScopeComparable<br>Differences: interface ScopeComparable|api/@ohos.util.d.ts|
|New API|NA|Class name: ScopeComparable;<br>API declaration: compareTo(other: ScopeComparable): boolean;<br>Differences: compareTo(other: ScopeComparable): boolean;|api/@ohos.util.d.ts|
|New API|NA|Class name: util;<br>API declaration: type ScopeType = ScopeComparable \| number;<br>Differences: type ScopeType = ScopeComparable \| number;|api/@ohos.util.d.ts|
|New API|NA|Class name: util;<br>API declaration: class Scope<br>Differences: class Scope|api/@ohos.util.d.ts|
|New API|NA|Class name: Scope;<br>API declaration: toString(): string;<br>Differences: toString(): string;|api/@ohos.util.d.ts|
|New API|NA|Class name: Scope;<br>API declaration: intersect(range: Scope): Scope;<br>Differences: intersect(range: Scope): Scope;|api/@ohos.util.d.ts|
|New API|NA|Class name: Scope;<br>API declaration: intersect(lowerObj: ScopeType, upperObj: ScopeType): Scope;<br>Differences: intersect(lowerObj: ScopeType, upperObj: ScopeType): Scope;|api/@ohos.util.d.ts|
|New API|NA|Class name: Scope;<br>API declaration: getUpper(): ScopeType;<br>Differences: getUpper(): ScopeType;|api/@ohos.util.d.ts|
|New API|NA|Class name: Scope;<br>API declaration: getLower(): ScopeType;<br>Differences: getLower(): ScopeType;|api/@ohos.util.d.ts|
|New API|NA|Class name: Scope;<br>API declaration: expand(lowerObj: ScopeType, upperObj: ScopeType): Scope;<br>Differences: expand(lowerObj: ScopeType, upperObj: ScopeType): Scope;|api/@ohos.util.d.ts|
|New API|NA|Class name: Scope;<br>API declaration: expand(range: Scope): Scope;<br>Differences: expand(range: Scope): Scope;|api/@ohos.util.d.ts|
|New API|NA|Class name: Scope;<br>API declaration: expand(value: ScopeType): Scope;<br>Differences: expand(value: ScopeType): Scope;|api/@ohos.util.d.ts|
|New API|NA|Class name: Scope;<br>API declaration: contains(value: ScopeType): boolean;<br>Differences: contains(value: ScopeType): boolean;|api/@ohos.util.d.ts|
|New API|NA|Class name: Scope;<br>API declaration: contains(range: Scope): boolean;<br>Differences: contains(range: Scope): boolean;|api/@ohos.util.d.ts|
|New API|NA|Class name: Scope;<br>API declaration: clamp(value: ScopeType): ScopeType;<br>Differences: clamp(value: ScopeType): ScopeType;|api/@ohos.util.d.ts|
|New API|NA|Class name: util;<br>API declaration: class ScopeHelper<br>Differences: class ScopeHelper|api/@ohos.util.d.ts|
|New API|NA|Class name: ScopeHelper;<br>API declaration: toString(): string;<br>Differences: toString(): string;|api/@ohos.util.d.ts|
|New API|NA|Class name: ScopeHelper;<br>API declaration: intersect(range: ScopeHelper): ScopeHelper;<br>Differences: intersect(range: ScopeHelper): ScopeHelper;|api/@ohos.util.d.ts|
|New API|NA|Class name: ScopeHelper;<br>API declaration: intersect(lowerObj: ScopeType, upperObj: ScopeType): ScopeHelper;<br>Differences: intersect(lowerObj: ScopeType, upperObj: ScopeType): ScopeHelper;|api/@ohos.util.d.ts|
|New API|NA|Class name: ScopeHelper;<br>API declaration: getUpper(): ScopeType;<br>Differences: getUpper(): ScopeType;|api/@ohos.util.d.ts|
|New API|NA|Class name: ScopeHelper;<br>API declaration: getLower(): ScopeType;<br>Differences: getLower(): ScopeType;|api/@ohos.util.d.ts|
|New API|NA|Class name: ScopeHelper;<br>API declaration: expand(lowerObj: ScopeType, upperObj: ScopeType): ScopeHelper;<br>Differences: expand(lowerObj: ScopeType, upperObj: ScopeType): ScopeHelper;|api/@ohos.util.d.ts|
|New API|NA|Class name: ScopeHelper;<br>API declaration: expand(range: ScopeHelper): ScopeHelper;<br>Differences: expand(range: ScopeHelper): ScopeHelper;|api/@ohos.util.d.ts|
|New API|NA|Class name: ScopeHelper;<br>API declaration: expand(value: ScopeType): ScopeHelper;<br>Differences: expand(value: ScopeType): ScopeHelper;|api/@ohos.util.d.ts|
|New API|NA|Class name: ScopeHelper;<br>API declaration: contains(value: ScopeType): boolean;<br>Differences: contains(value: ScopeType): boolean;|api/@ohos.util.d.ts|
|New API|NA|Class name: ScopeHelper;<br>API declaration: contains(range: ScopeHelper): boolean;<br>Differences: contains(range: ScopeHelper): boolean;|api/@ohos.util.d.ts|
|New API|NA|Class name: ScopeHelper;<br>API declaration: clamp(value: ScopeType): ScopeType;<br>Differences: clamp(value: ScopeType): ScopeType;|api/@ohos.util.d.ts|
|New API|NA|Class name: util;<br>API declaration: class Base64<br>Differences: class Base64|api/@ohos.util.d.ts|
|New API|NA|Class name: Base64;<br>API declaration: encodeSync(src: Uint8Array): Uint8Array;<br>Differences: encodeSync(src: Uint8Array): Uint8Array;|api/@ohos.util.d.ts|
|New API|NA|Class name: Base64;<br>API declaration: encodeToStringSync(src: Uint8Array): string;<br>Differences: encodeToStringSync(src: Uint8Array): string;|api/@ohos.util.d.ts|
|New API|NA|Class name: Base64;<br>API declaration: decodeSync(src: Uint8Array \| string): Uint8Array;<br>Differences: decodeSync(src: Uint8Array \| string): Uint8Array;|api/@ohos.util.d.ts|
|New API|NA|Class name: Base64;<br>API declaration: encode(src: Uint8Array): Promise\<Uint8Array>;<br>Differences: encode(src: Uint8Array): Promise\<Uint8Array>;|api/@ohos.util.d.ts|
|New API|NA|Class name: Base64;<br>API declaration: encodeToString(src: Uint8Array): Promise\<string>;<br>Differences: encodeToString(src: Uint8Array): Promise\<string>;|api/@ohos.util.d.ts|
|New API|NA|Class name: Base64;<br>API declaration: decode(src: Uint8Array \| string): Promise\<Uint8Array>;<br>Differences: decode(src: Uint8Array \| string): Promise\<Uint8Array>;|api/@ohos.util.d.ts|
|New API|NA|Class name: util;<br>API declaration: enum Type<br>Differences: enum Type|api/@ohos.util.d.ts|
|New API|NA|Class name: Type;<br>API declaration: BASIC<br>Differences: BASIC|api/@ohos.util.d.ts|
|New API|NA|Class name: Type;<br>API declaration: MIME<br>Differences: MIME|api/@ohos.util.d.ts|
|New API|NA|Class name: util;<br>API declaration: class Base64Helper<br>Differences: class Base64Helper|api/@ohos.util.d.ts|
|New API|NA|Class name: Base64Helper;<br>API declaration: encodeSync(src: Uint8Array): Uint8Array;<br>Differences: encodeSync(src: Uint8Array): Uint8Array;|api/@ohos.util.d.ts|
|New API|NA|Class name: Base64Helper;<br>API declaration: encodeToStringSync(src: Uint8Array, options?: Type): string;<br>Differences: encodeToStringSync(src: Uint8Array, options?: Type): string;|api/@ohos.util.d.ts|
|New API|NA|Class name: Base64Helper;<br>API declaration: decodeSync(src: Uint8Array \| string, options?: Type): Uint8Array;<br>Differences: decodeSync(src: Uint8Array \| string, options?: Type): Uint8Array;|api/@ohos.util.d.ts|
|New API|NA|Class name: Base64Helper;<br>API declaration: encode(src: Uint8Array): Promise\<Uint8Array>;<br>Differences: encode(src: Uint8Array): Promise\<Uint8Array>;|api/@ohos.util.d.ts|
|New API|NA|Class name: Base64Helper;<br>API declaration: encodeToString(src: Uint8Array, options?: Type): Promise\<string>;<br>Differences: encodeToString(src: Uint8Array, options?: Type): Promise\<string>;|api/@ohos.util.d.ts|
|New API|NA|Class name: Base64Helper;<br>API declaration: decode(src: Uint8Array \| string, options?: Type): Promise\<Uint8Array>;<br>Differences: decode(src: Uint8Array \| string, options?: Type): Promise\<Uint8Array>;|api/@ohos.util.d.ts|
|New API|NA|Class name: util;<br>API declaration: class types<br>Differences: class types|api/@ohos.util.d.ts|
|New API|NA|Class name: types;<br>API declaration: isAnyArrayBuffer(value: Object): boolean;<br>Differences: isAnyArrayBuffer(value: Object): boolean;|api/@ohos.util.d.ts|
|New API|NA|Class name: types;<br>API declaration: isArrayBufferView(value: Object): boolean;<br>Differences: isArrayBufferView(value: Object): boolean;|api/@ohos.util.d.ts|
|New API|NA|Class name: types;<br>API declaration: isArgumentsObject(value: Object): boolean;<br>Differences: isArgumentsObject(value: Object): boolean;|api/@ohos.util.d.ts|
|New API|NA|Class name: types;<br>API declaration: isArrayBuffer(value: Object): boolean;<br>Differences: isArrayBuffer(value: Object): boolean;|api/@ohos.util.d.ts|
|New API|NA|Class name: types;<br>API declaration: isAsyncFunction(value: Object): boolean;<br>Differences: isAsyncFunction(value: Object): boolean;|api/@ohos.util.d.ts|
|New API|NA|Class name: types;<br>API declaration: isBigInt64Array(value: Object): boolean;<br>Differences: isBigInt64Array(value: Object): boolean;|api/@ohos.util.d.ts|
|New API|NA|Class name: types;<br>API declaration: isBigUint64Array(value: Object): boolean;<br>Differences: isBigUint64Array(value: Object): boolean;|api/@ohos.util.d.ts|
|New API|NA|Class name: types;<br>API declaration: isBooleanObject(value: Object): boolean;<br>Differences: isBooleanObject(value: Object): boolean;|api/@ohos.util.d.ts|
|New API|NA|Class name: types;<br>API declaration: isBoxedPrimitive(value: Object): boolean;<br>Differences: isBoxedPrimitive(value: Object): boolean;|api/@ohos.util.d.ts|
|New API|NA|Class name: types;<br>API declaration: isDataView(value: Object): boolean;<br>Differences: isDataView(value: Object): boolean;|api/@ohos.util.d.ts|
|New API|NA|Class name: types;<br>API declaration: isDate(value: Object): boolean;<br>Differences: isDate(value: Object): boolean;|api/@ohos.util.d.ts|
|New API|NA|Class name: types;<br>API declaration: isExternal(value: Object): boolean;<br>Differences: isExternal(value: Object): boolean;|api/@ohos.util.d.ts|
|New API|NA|Class name: types;<br>API declaration: isFloat32Array(value: Object): boolean;<br>Differences: isFloat32Array(value: Object): boolean;|api/@ohos.util.d.ts|
|New API|NA|Class name: types;<br>API declaration: isFloat64Array(value: Object): boolean;<br>Differences: isFloat64Array(value: Object): boolean;|api/@ohos.util.d.ts|
|New API|NA|Class name: types;<br>API declaration: isGeneratorFunction(value: Object): boolean;<br>Differences: isGeneratorFunction(value: Object): boolean;|api/@ohos.util.d.ts|
|New API|NA|Class name: types;<br>API declaration: isGeneratorObject(value: Object): boolean;<br>Differences: isGeneratorObject(value: Object): boolean;|api/@ohos.util.d.ts|
|New API|NA|Class name: types;<br>API declaration: isInt8Array(value: Object): boolean;<br>Differences: isInt8Array(value: Object): boolean;|api/@ohos.util.d.ts|
|New API|NA|Class name: types;<br>API declaration: isInt16Array(value: Object): boolean;<br>Differences: isInt16Array(value: Object): boolean;|api/@ohos.util.d.ts|
|New API|NA|Class name: types;<br>API declaration: isInt32Array(value: Object): boolean;<br>Differences: isInt32Array(value: Object): boolean;|api/@ohos.util.d.ts|
|New API|NA|Class name: types;<br>API declaration: isMap(value: Object): boolean;<br>Differences: isMap(value: Object): boolean;|api/@ohos.util.d.ts|
|New API|NA|Class name: types;<br>API declaration: isMapIterator(value: Object): boolean;<br>Differences: isMapIterator(value: Object): boolean;|api/@ohos.util.d.ts|
|New API|NA|Class name: types;<br>API declaration: isModuleNamespaceObject(value: Object): boolean;<br>Differences: isModuleNamespaceObject(value: Object): boolean;|api/@ohos.util.d.ts|
|New API|NA|Class name: types;<br>API declaration: isNativeError(value: Object): boolean;<br>Differences: isNativeError(value: Object): boolean;|api/@ohos.util.d.ts|
|New API|NA|Class name: types;<br>API declaration: isNumberObject(value: Object): boolean;<br>Differences: isNumberObject(value: Object): boolean;|api/@ohos.util.d.ts|
|New API|NA|Class name: types;<br>API declaration: isPromise(value: Object): boolean;<br>Differences: isPromise(value: Object): boolean;|api/@ohos.util.d.ts|
|New API|NA|Class name: types;<br>API declaration: isProxy(value: Object): boolean;<br>Differences: isProxy(value: Object): boolean;|api/@ohos.util.d.ts|
|New API|NA|Class name: types;<br>API declaration: isRegExp(value: Object): boolean;<br>Differences: isRegExp(value: Object): boolean;|api/@ohos.util.d.ts|
|New API|NA|Class name: types;<br>API declaration: isSet(value: Object): boolean;<br>Differences: isSet(value: Object): boolean;|api/@ohos.util.d.ts|
|New API|NA|Class name: types;<br>API declaration: isSetIterator(value: Object): boolean;<br>Differences: isSetIterator(value: Object): boolean;|api/@ohos.util.d.ts|
|New API|NA|Class name: types;<br>API declaration: isSharedArrayBuffer(value: Object): boolean;<br>Differences: isSharedArrayBuffer(value: Object): boolean;|api/@ohos.util.d.ts|
|New API|NA|Class name: types;<br>API declaration: isStringObject(value: Object): boolean;<br>Differences: isStringObject(value: Object): boolean;|api/@ohos.util.d.ts|
|New API|NA|Class name: types;<br>API declaration: isSymbolObject(value: Object): boolean;<br>Differences: isSymbolObject(value: Object): boolean;|api/@ohos.util.d.ts|
|New API|NA|Class name: types;<br>API declaration: isTypedArray(value: Object): boolean;<br>Differences: isTypedArray(value: Object): boolean;|api/@ohos.util.d.ts|
|New API|NA|Class name: types;<br>API declaration: isUint8Array(value: Object): boolean;<br>Differences: isUint8Array(value: Object): boolean;|api/@ohos.util.d.ts|
|New API|NA|Class name: types;<br>API declaration: isUint8ClampedArray(value: Object): boolean;<br>Differences: isUint8ClampedArray(value: Object): boolean;|api/@ohos.util.d.ts|
|New API|NA|Class name: types;<br>API declaration: isUint16Array(value: Object): boolean;<br>Differences: isUint16Array(value: Object): boolean;|api/@ohos.util.d.ts|
|New API|NA|Class name: types;<br>API declaration: isUint32Array(value: Object): boolean;<br>Differences: isUint32Array(value: Object): boolean;|api/@ohos.util.d.ts|
|New API|NA|Class name: types;<br>API declaration: isWeakMap(value: Object): boolean;<br>Differences: isWeakMap(value: Object): boolean;|api/@ohos.util.d.ts|
|New API|NA|Class name: types;<br>API declaration: isWeakSet(value: Object): boolean;<br>Differences: isWeakSet(value: Object): boolean;|api/@ohos.util.d.ts|
|New API|NA|Class name: util;<br>API declaration: class Aspect<br>Differences: class Aspect|api/@ohos.util.d.ts|
|New API|NA|Class name: Aspect;<br>API declaration: static addBefore(targetClass: Object, methodName: string, isStatic: boolean, before: Function): void;<br>Differences: static addBefore(targetClass: Object, methodName: string, isStatic: boolean, before: Function): void;|api/@ohos.util.d.ts|
|New API|NA|Class name: Aspect;<br>API declaration: static addAfter(targetClass: Object, methodName: string, isStatic: boolean, after: Function): void;<br>Differences: static addAfter(targetClass: Object, methodName: string, isStatic: boolean, after: Function): void;|api/@ohos.util.d.ts|
|New API|NA|Class name: Aspect;<br>API declaration: static replace(targetClass: Object, methodName: string, isStatic: boolean, instead: Function): void;<br>Differences: static replace(targetClass: Object, methodName: string, isStatic: boolean, instead: Function): void;|api/@ohos.util.d.ts|
|New API|NA|Class name: global;<br>API declaration: declare class Deque<br>Differences: declare class Deque|api/@ohos.util.Deque.d.ts|
|New API|NA|Class name: Deque;<br>API declaration: length: number;<br>Differences: length: number;|api/@ohos.util.Deque.d.ts|
|New API|NA|Class name: Deque;<br>API declaration: insertFront(element: T): void;<br>Differences: insertFront(element: T): void;|api/@ohos.util.Deque.d.ts|
|New API|NA|Class name: Deque;<br>API declaration: insertEnd(element: T): void;<br>Differences: insertEnd(element: T): void;|api/@ohos.util.Deque.d.ts|
|New API|NA|Class name: Deque;<br>API declaration: has(element: T): boolean;<br>Differences: has(element: T): boolean;|api/@ohos.util.Deque.d.ts|
|New API|NA|Class name: Deque;<br>API declaration: getFirst(): T;<br>Differences: getFirst(): T;|api/@ohos.util.Deque.d.ts|
|New API|NA|Class name: Deque;<br>API declaration: getLast(): T;<br>Differences: getLast(): T;|api/@ohos.util.Deque.d.ts|
|New API|NA|Class name: Deque;<br>API declaration: popFirst(): T;<br>Differences: popFirst(): T;|api/@ohos.util.Deque.d.ts|
|New API|NA|Class name: Deque;<br>API declaration: popLast(): T;<br>Differences: popLast(): T;|api/@ohos.util.Deque.d.ts|
|New API|NA|Class name: Deque;<br>API declaration: forEach(callbackFn: (value: T, index?: number, deque?: Deque\<T>) => void, thisArg?: Object): void;<br>Differences: forEach(callbackFn: (value: T, index?: number, deque?: Deque\<T>) => void, thisArg?: Object): void;|api/@ohos.util.Deque.d.ts|
|New API|NA|Class name: Deque;<br>API declaration: [Symbol.iterator](): IterableIterator\<T>;<br>Differences: [Symbol.iterator](): IterableIterator\<T>;|api/@ohos.util.Deque.d.ts|
|New API|NA|Class name: global;<br>API declaration: declare class HashMap<br>Differences: declare class HashMap|api/@ohos.util.HashMap.d.ts|
|New API|NA|Class name: HashMap;<br>API declaration: length: number;<br>Differences: length: number;|api/@ohos.util.HashMap.d.ts|
|New API|NA|Class name: HashMap;<br>API declaration: isEmpty(): boolean;<br>Differences: isEmpty(): boolean;|api/@ohos.util.HashMap.d.ts|
|New API|NA|Class name: HashMap;<br>API declaration: hasKey(key: K): boolean;<br>Differences: hasKey(key: K): boolean;|api/@ohos.util.HashMap.d.ts|
|New API|NA|Class name: HashMap;<br>API declaration: hasValue(value: V): boolean;<br>Differences: hasValue(value: V): boolean;|api/@ohos.util.HashMap.d.ts|
|New API|NA|Class name: HashMap;<br>API declaration: get(key: K): V;<br>Differences: get(key: K): V;|api/@ohos.util.HashMap.d.ts|
|New API|NA|Class name: HashMap;<br>API declaration: setAll(map: HashMap\<K, V>): void;<br>Differences: setAll(map: HashMap\<K, V>): void;|api/@ohos.util.HashMap.d.ts|
|New API|NA|Class name: HashMap;<br>API declaration: set(key: K, value: V): Object;<br>Differences: set(key: K, value: V): Object;|api/@ohos.util.HashMap.d.ts|
|New API|NA|Class name: HashMap;<br>API declaration: remove(key: K): V;<br>Differences: remove(key: K): V;|api/@ohos.util.HashMap.d.ts|
|New API|NA|Class name: HashMap;<br>API declaration: clear(): void;<br>Differences: clear(): void;|api/@ohos.util.HashMap.d.ts|
|New API|NA|Class name: HashMap;<br>API declaration: keys(): IterableIterator\<K>;<br>Differences: keys(): IterableIterator\<K>;|api/@ohos.util.HashMap.d.ts|
|New API|NA|Class name: HashMap;<br>API declaration: values(): IterableIterator\<V>;<br>Differences: values(): IterableIterator\<V>;|api/@ohos.util.HashMap.d.ts|
|New API|NA|Class name: HashMap;<br>API declaration: replace(key: K, newValue: V): boolean;<br>Differences: replace(key: K, newValue: V): boolean;|api/@ohos.util.HashMap.d.ts|
|New API|NA|Class name: HashMap;<br>API declaration: forEach(callbackFn: (value?: V, key?: K, map?: HashMap\<K, V>) => void, thisArg?: Object): void;<br>Differences: forEach(callbackFn: (value?: V, key?: K, map?: HashMap\<K, V>) => void, thisArg?: Object): void;|api/@ohos.util.HashMap.d.ts|
|New API|NA|Class name: HashMap;<br>API declaration: entries(): IterableIterator\<[<br>        K,<br>        V<br>    ]>;<br>Differences: entries(): IterableIterator\<[<br>        K,<br>        V<br>    ]>;|api/@ohos.util.HashMap.d.ts|
|New API|NA|Class name: HashMap;<br>API declaration: [Symbol.iterator](): IterableIterator\<[<br>        K,<br>        V<br>    ]>;<br>Differences: [Symbol.iterator](): IterableIterator\<[<br>        K,<br>        V<br>    ]>;|api/@ohos.util.HashMap.d.ts|
|New API|NA|Class name: global;<br>API declaration: declare class HashSet<br>Differences: declare class HashSet|api/@ohos.util.HashSet.d.ts|
|New API|NA|Class name: HashSet;<br>API declaration: length: number;<br>Differences: length: number;|api/@ohos.util.HashSet.d.ts|
|New API|NA|Class name: HashSet;<br>API declaration: isEmpty(): boolean;<br>Differences: isEmpty(): boolean;|api/@ohos.util.HashSet.d.ts|
|New API|NA|Class name: HashSet;<br>API declaration: has(value: T): boolean;<br>Differences: has(value: T): boolean;|api/@ohos.util.HashSet.d.ts|
|New API|NA|Class name: HashSet;<br>API declaration: add(value: T): boolean;<br>Differences: add(value: T): boolean;|api/@ohos.util.HashSet.d.ts|
|New API|NA|Class name: HashSet;<br>API declaration: remove(value: T): boolean;<br>Differences: remove(value: T): boolean;|api/@ohos.util.HashSet.d.ts|
|New API|NA|Class name: HashSet;<br>API declaration: clear(): void;<br>Differences: clear(): void;|api/@ohos.util.HashSet.d.ts|
|New API|NA|Class name: HashSet;<br>API declaration: forEach(callbackFn: (value?: T, key?: T, set?: HashSet\<T>) => void, thisArg?: Object): void;<br>Differences: forEach(callbackFn: (value?: T, key?: T, set?: HashSet\<T>) => void, thisArg?: Object): void;|api/@ohos.util.HashSet.d.ts|
|New API|NA|Class name: HashSet;<br>API declaration: values(): IterableIterator\<T>;<br>Differences: values(): IterableIterator\<T>;|api/@ohos.util.HashSet.d.ts|
|New API|NA|Class name: HashSet;<br>API declaration: entries(): IterableIterator\<[<br>        T,<br>        T<br>    ]>;<br>Differences: entries(): IterableIterator\<[<br>        T,<br>        T<br>    ]>;|api/@ohos.util.HashSet.d.ts|
|New API|NA|Class name: HashSet;<br>API declaration: [Symbol.iterator](): IterableIterator\<T>;<br>Differences: [Symbol.iterator](): IterableIterator\<T>;|api/@ohos.util.HashSet.d.ts|
|New API|NA|Class name: global;<br>API declaration: declare class LightWeightMap<br>Differences: declare class LightWeightMap|api/@ohos.util.LightWeightMap.d.ts|
|New API|NA|Class name: LightWeightMap;<br>API declaration: length: number;<br>Differences: length: number;|api/@ohos.util.LightWeightMap.d.ts|
|New API|NA|Class name: LightWeightMap;<br>API declaration: hasAll(map: LightWeightMap\<K, V>): boolean;<br>Differences: hasAll(map: LightWeightMap\<K, V>): boolean;|api/@ohos.util.LightWeightMap.d.ts|
|New API|NA|Class name: LightWeightMap;<br>API declaration: hasKey(key: K): boolean;<br>Differences: hasKey(key: K): boolean;|api/@ohos.util.LightWeightMap.d.ts|
|New API|NA|Class name: LightWeightMap;<br>API declaration: hasValue(value: V): boolean;<br>Differences: hasValue(value: V): boolean;|api/@ohos.util.LightWeightMap.d.ts|
|New API|NA|Class name: LightWeightMap;<br>API declaration: increaseCapacityTo(minimumCapacity: number): void;<br>Differences: increaseCapacityTo(minimumCapacity: number): void;|api/@ohos.util.LightWeightMap.d.ts|
|New API|NA|Class name: LightWeightMap;<br>API declaration: entries(): IterableIterator\<[<br>        K,<br>        V<br>    ]>;<br>Differences: entries(): IterableIterator\<[<br>        K,<br>        V<br>    ]>;|api/@ohos.util.LightWeightMap.d.ts|
|New API|NA|Class name: LightWeightMap;<br>API declaration: get(key: K): V;<br>Differences: get(key: K): V;|api/@ohos.util.LightWeightMap.d.ts|
|New API|NA|Class name: LightWeightMap;<br>API declaration: getIndexOfKey(key: K): number;<br>Differences: getIndexOfKey(key: K): number;|api/@ohos.util.LightWeightMap.d.ts|
|New API|NA|Class name: LightWeightMap;<br>API declaration: getIndexOfValue(value: V): number;<br>Differences: getIndexOfValue(value: V): number;|api/@ohos.util.LightWeightMap.d.ts|
|New API|NA|Class name: LightWeightMap;<br>API declaration: isEmpty(): boolean;<br>Differences: isEmpty(): boolean;|api/@ohos.util.LightWeightMap.d.ts|
|New API|NA|Class name: LightWeightMap;<br>API declaration: getKeyAt(index: number): K;<br>Differences: getKeyAt(index: number): K;|api/@ohos.util.LightWeightMap.d.ts|
|New API|NA|Class name: LightWeightMap;<br>API declaration: keys(): IterableIterator\<K>;<br>Differences: keys(): IterableIterator\<K>;|api/@ohos.util.LightWeightMap.d.ts|
|New API|NA|Class name: LightWeightMap;<br>API declaration: setAll(map: LightWeightMap\<K, V>): void;<br>Differences: setAll(map: LightWeightMap\<K, V>): void;|api/@ohos.util.LightWeightMap.d.ts|
|New API|NA|Class name: LightWeightMap;<br>API declaration: set(key: K, value: V): Object;<br>Differences: set(key: K, value: V): Object;|api/@ohos.util.LightWeightMap.d.ts|
|New API|NA|Class name: LightWeightMap;<br>API declaration: remove(key: K): V;<br>Differences: remove(key: K): V;|api/@ohos.util.LightWeightMap.d.ts|
|New API|NA|Class name: LightWeightMap;<br>API declaration: removeAt(index: number): boolean;<br>Differences: removeAt(index: number): boolean;|api/@ohos.util.LightWeightMap.d.ts|
|New API|NA|Class name: LightWeightMap;<br>API declaration: clear(): void;<br>Differences: clear(): void;|api/@ohos.util.LightWeightMap.d.ts|
|New API|NA|Class name: LightWeightMap;<br>API declaration: setValueAt(index: number, newValue: V): boolean;<br>Differences: setValueAt(index: number, newValue: V): boolean;|api/@ohos.util.LightWeightMap.d.ts|
|New API|NA|Class name: LightWeightMap;<br>API declaration: forEach(callbackFn: (value?: V, key?: K, map?: LightWeightMap\<K, V>) => void, thisArg?: Object): void;<br>Differences: forEach(callbackFn: (value?: V, key?: K, map?: LightWeightMap\<K, V>) => void, thisArg?: Object): void;|api/@ohos.util.LightWeightMap.d.ts|
|New API|NA|Class name: LightWeightMap;<br>API declaration: [Symbol.iterator](): IterableIterator\<[<br>        K,<br>        V<br>    ]>;<br>Differences: [Symbol.iterator](): IterableIterator\<[<br>        K,<br>        V<br>    ]>;|api/@ohos.util.LightWeightMap.d.ts|
|New API|NA|Class name: LightWeightMap;<br>API declaration: toString(): String;<br>Differences: toString(): String;|api/@ohos.util.LightWeightMap.d.ts|
|New API|NA|Class name: LightWeightMap;<br>API declaration: getValueAt(index: number): V;<br>Differences: getValueAt(index: number): V;|api/@ohos.util.LightWeightMap.d.ts|
|New API|NA|Class name: LightWeightMap;<br>API declaration: values(): IterableIterator\<V>;<br>Differences: values(): IterableIterator\<V>;|api/@ohos.util.LightWeightMap.d.ts|
|New API|NA|Class name: global;<br>API declaration: declare class LightWeightSet<br>Differences: declare class LightWeightSet|api/@ohos.util.LightWeightSet.d.ts|
|New API|NA|Class name: LightWeightSet;<br>API declaration: length: number;<br>Differences: length: number;|api/@ohos.util.LightWeightSet.d.ts|
|New API|NA|Class name: LightWeightSet;<br>API declaration: add(obj: T): boolean;<br>Differences: add(obj: T): boolean;|api/@ohos.util.LightWeightSet.d.ts|
|New API|NA|Class name: LightWeightSet;<br>API declaration: addAll(set: LightWeightSet\<T>): boolean;<br>Differences: addAll(set: LightWeightSet\<T>): boolean;|api/@ohos.util.LightWeightSet.d.ts|
|New API|NA|Class name: LightWeightSet;<br>API declaration: hasAll(set: LightWeightSet\<T>): boolean;<br>Differences: hasAll(set: LightWeightSet\<T>): boolean;|api/@ohos.util.LightWeightSet.d.ts|
|New API|NA|Class name: LightWeightSet;<br>API declaration: has(key: T): boolean;<br>Differences: has(key: T): boolean;|api/@ohos.util.LightWeightSet.d.ts|
|New API|NA|Class name: LightWeightSet;<br>API declaration: equal(obj: Object): boolean;<br>Differences: equal(obj: Object): boolean;|api/@ohos.util.LightWeightSet.d.ts|
|New API|NA|Class name: LightWeightSet;<br>API declaration: increaseCapacityTo(minimumCapacity: number): void;<br>Differences: increaseCapacityTo(minimumCapacity: number): void;|api/@ohos.util.LightWeightSet.d.ts|
|New API|NA|Class name: LightWeightSet;<br>API declaration: getIndexOf(key: T): number;<br>Differences: getIndexOf(key: T): number;|api/@ohos.util.LightWeightSet.d.ts|
|New API|NA|Class name: LightWeightSet;<br>API declaration: remove(key: T): T;<br>Differences: remove(key: T): T;|api/@ohos.util.LightWeightSet.d.ts|
|New API|NA|Class name: LightWeightSet;<br>API declaration: removeAt(index: number): boolean;<br>Differences: removeAt(index: number): boolean;|api/@ohos.util.LightWeightSet.d.ts|
|New API|NA|Class name: LightWeightSet;<br>API declaration: clear(): void;<br>Differences: clear(): void;|api/@ohos.util.LightWeightSet.d.ts|
|New API|NA|Class name: LightWeightSet;<br>API declaration: forEach(callbackFn: (value?: T, key?: T, set?: LightWeightSet\<T>) => void, thisArg?: Object): void;<br>Differences: forEach(callbackFn: (value?: T, key?: T, set?: LightWeightSet\<T>) => void, thisArg?: Object): void;|api/@ohos.util.LightWeightSet.d.ts|
|New API|NA|Class name: LightWeightSet;<br>API declaration: [Symbol.iterator](): IterableIterator\<T>;<br>Differences: [Symbol.iterator](): IterableIterator\<T>;|api/@ohos.util.LightWeightSet.d.ts|
|New API|NA|Class name: LightWeightSet;<br>API declaration: toString(): String;<br>Differences: toString(): String;|api/@ohos.util.LightWeightSet.d.ts|
|New API|NA|Class name: LightWeightSet;<br>API declaration: toArray(): Array\<T>;<br>Differences: toArray(): Array\<T>;|api/@ohos.util.LightWeightSet.d.ts|
|New API|NA|Class name: LightWeightSet;<br>API declaration: getValueAt(index: number): T;<br>Differences: getValueAt(index: number): T;|api/@ohos.util.LightWeightSet.d.ts|
|New API|NA|Class name: LightWeightSet;<br>API declaration: values(): IterableIterator\<T>;<br>Differences: values(): IterableIterator\<T>;|api/@ohos.util.LightWeightSet.d.ts|
|New API|NA|Class name: LightWeightSet;<br>API declaration: entries(): IterableIterator\<[<br>        T,<br>        T<br>    ]>;<br>Differences: entries(): IterableIterator\<[<br>        T,<br>        T<br>    ]>;|api/@ohos.util.LightWeightSet.d.ts|
|New API|NA|Class name: LightWeightSet;<br>API declaration: isEmpty(): boolean;<br>Differences: isEmpty(): boolean;|api/@ohos.util.LightWeightSet.d.ts|
|New API|NA|Class name: global;<br>API declaration: declare class LinkedList<br>Differences: declare class LinkedList|api/@ohos.util.LinkedList.d.ts|
|New API|NA|Class name: LinkedList;<br>API declaration: length: number;<br>Differences: length: number;|api/@ohos.util.LinkedList.d.ts|
|New API|NA|Class name: LinkedList;<br>API declaration: add(element: T): boolean;<br>Differences: add(element: T): boolean;|api/@ohos.util.LinkedList.d.ts|
|New API|NA|Class name: LinkedList;<br>API declaration: insert(index: number, element: T): void;<br>Differences: insert(index: number, element: T): void;|api/@ohos.util.LinkedList.d.ts|
|New API|NA|Class name: LinkedList;<br>API declaration: get(index: number): T;<br>Differences: get(index: number): T;|api/@ohos.util.LinkedList.d.ts|
|New API|NA|Class name: LinkedList;<br>API declaration: addFirst(element: T): void;<br>Differences: addFirst(element: T): void;|api/@ohos.util.LinkedList.d.ts|
|New API|NA|Class name: LinkedList;<br>API declaration: removeFirst(): T;<br>Differences: removeFirst(): T;|api/@ohos.util.LinkedList.d.ts|
|New API|NA|Class name: LinkedList;<br>API declaration: removeLast(): T;<br>Differences: removeLast(): T;|api/@ohos.util.LinkedList.d.ts|
|New API|NA|Class name: LinkedList;<br>API declaration: has(element: T): boolean;<br>Differences: has(element: T): boolean;|api/@ohos.util.LinkedList.d.ts|
|New API|NA|Class name: LinkedList;<br>API declaration: getIndexOf(element: T): number;<br>Differences: getIndexOf(element: T): number;|api/@ohos.util.LinkedList.d.ts|
|New API|NA|Class name: LinkedList;<br>API declaration: removeByIndex(index: number): T;<br>Differences: removeByIndex(index: number): T;|api/@ohos.util.LinkedList.d.ts|
|New API|NA|Class name: LinkedList;<br>API declaration: remove(element: T): boolean;<br>Differences: remove(element: T): boolean;|api/@ohos.util.LinkedList.d.ts|
|New API|NA|Class name: LinkedList;<br>API declaration: removeFirstFound(element: T): boolean;<br>Differences: removeFirstFound(element: T): boolean;|api/@ohos.util.LinkedList.d.ts|
|New API|NA|Class name: LinkedList;<br>API declaration: removeLastFound(element: T): boolean;<br>Differences: removeLastFound(element: T): boolean;|api/@ohos.util.LinkedList.d.ts|
|New API|NA|Class name: LinkedList;<br>API declaration: getLastIndexOf(element: T): number;<br>Differences: getLastIndexOf(element: T): number;|api/@ohos.util.LinkedList.d.ts|
|New API|NA|Class name: LinkedList;<br>API declaration: getFirst(): T;<br>Differences: getFirst(): T;|api/@ohos.util.LinkedList.d.ts|
|New API|NA|Class name: LinkedList;<br>API declaration: getLast(): T;<br>Differences: getLast(): T;|api/@ohos.util.LinkedList.d.ts|
|New API|NA|Class name: LinkedList;<br>API declaration: set(index: number, element: T): T;<br>Differences: set(index: number, element: T): T;|api/@ohos.util.LinkedList.d.ts|
|New API|NA|Class name: LinkedList;<br>API declaration: forEach(callbackFn: (value: T, index?: number, LinkedList?: LinkedList\<T>) => void, thisArg?: Object): void;<br>Differences: forEach(callbackFn: (value: T, index?: number, LinkedList?: LinkedList\<T>) => void, thisArg?: Object): void;|api/@ohos.util.LinkedList.d.ts|
|New API|NA|Class name: LinkedList;<br>API declaration: clear(): void;<br>Differences: clear(): void;|api/@ohos.util.LinkedList.d.ts|
|New API|NA|Class name: LinkedList;<br>API declaration: clone(): LinkedList\<T>;<br>Differences: clone(): LinkedList\<T>;|api/@ohos.util.LinkedList.d.ts|
|New API|NA|Class name: LinkedList;<br>API declaration: convertToArray(): Array\<T>;<br>Differences: convertToArray(): Array\<T>;|api/@ohos.util.LinkedList.d.ts|
|New API|NA|Class name: LinkedList;<br>API declaration: [Symbol.iterator](): IterableIterator\<T>;<br>Differences: [Symbol.iterator](): IterableIterator\<T>;|api/@ohos.util.LinkedList.d.ts|
|New API|NA|Class name: global;<br>API declaration: declare class List<br>Differences: declare class List|api/@ohos.util.List.d.ts|
|New API|NA|Class name: List;<br>API declaration: length: number;<br>Differences: length: number;|api/@ohos.util.List.d.ts|
|New API|NA|Class name: List;<br>API declaration: add(element: T): boolean;<br>Differences: add(element: T): boolean;|api/@ohos.util.List.d.ts|
|New API|NA|Class name: List;<br>API declaration: insert(element: T, index: number): void;<br>Differences: insert(element: T, index: number): void;|api/@ohos.util.List.d.ts|
|New API|NA|Class name: List;<br>API declaration: get(index: number): T;<br>Differences: get(index: number): T;|api/@ohos.util.List.d.ts|
|New API|NA|Class name: List;<br>API declaration: has(element: T): boolean;<br>Differences: has(element: T): boolean;|api/@ohos.util.List.d.ts|
|New API|NA|Class name: List;<br>API declaration: getIndexOf(element: T): number;<br>Differences: getIndexOf(element: T): number;|api/@ohos.util.List.d.ts|
|New API|NA|Class name: List;<br>API declaration: removeByIndex(index: number): T;<br>Differences: removeByIndex(index: number): T;|api/@ohos.util.List.d.ts|
|New API|NA|Class name: List;<br>API declaration: remove(element: T): boolean;<br>Differences: remove(element: T): boolean;|api/@ohos.util.List.d.ts|
|New API|NA|Class name: List;<br>API declaration: getLastIndexOf(element: T): number;<br>Differences: getLastIndexOf(element: T): number;|api/@ohos.util.List.d.ts|
|New API|NA|Class name: List;<br>API declaration: getFirst(): T;<br>Differences: getFirst(): T;|api/@ohos.util.List.d.ts|
|New API|NA|Class name: List;<br>API declaration: getLast(): T;<br>Differences: getLast(): T;|api/@ohos.util.List.d.ts|
|New API|NA|Class name: List;<br>API declaration: set(index: number, element: T): T;<br>Differences: set(index: number, element: T): T;|api/@ohos.util.List.d.ts|
|New API|NA|Class name: List;<br>API declaration: equal(obj: Object): boolean;<br>Differences: equal(obj: Object): boolean;|api/@ohos.util.List.d.ts|
|New API|NA|Class name: List;<br>API declaration: forEach(callbackFn: (value: T, index?: number, List?: List\<T>) => void, thisArg?: Object): void;<br>Differences: forEach(callbackFn: (value: T, index?: number, List?: List\<T>) => void, thisArg?: Object): void;|api/@ohos.util.List.d.ts|
|New API|NA|Class name: List;<br>API declaration: sort(comparator: (firstValue: T, secondValue: T) => number): void;<br>Differences: sort(comparator: (firstValue: T, secondValue: T) => number): void;|api/@ohos.util.List.d.ts|
|New API|NA|Class name: List;<br>API declaration: clear(): void;<br>Differences: clear(): void;|api/@ohos.util.List.d.ts|
|New API|NA|Class name: List;<br>API declaration: getSubList(fromIndex: number, toIndex: number): List\<T>;<br>Differences: getSubList(fromIndex: number, toIndex: number): List\<T>;|api/@ohos.util.List.d.ts|
|New API|NA|Class name: List;<br>API declaration: replaceAllElements(callbackFn: (value: T, index?: number, list?: List\<T>) => T, thisArg?: Object): void;<br>Differences: replaceAllElements(callbackFn: (value: T, index?: number, list?: List\<T>) => T, thisArg?: Object): void;|api/@ohos.util.List.d.ts|
|New API|NA|Class name: List;<br>API declaration: convertToArray(): Array\<T>;<br>Differences: convertToArray(): Array\<T>;|api/@ohos.util.List.d.ts|
|New API|NA|Class name: List;<br>API declaration: isEmpty(): boolean;<br>Differences: isEmpty(): boolean;|api/@ohos.util.List.d.ts|
|New API|NA|Class name: List;<br>API declaration: [Symbol.iterator](): IterableIterator\<T>;<br>Differences: [Symbol.iterator](): IterableIterator\<T>;|api/@ohos.util.List.d.ts|
|New API|NA|Class name: global;<br>API declaration: declare class PlainArray<br>Differences: declare class PlainArray|api/@ohos.util.PlainArray.d.ts|
|New API|NA|Class name: PlainArray;<br>API declaration: length: number;<br>Differences: length: number;|api/@ohos.util.PlainArray.d.ts|
|New API|NA|Class name: PlainArray;<br>API declaration: add(key: number, value: T): void;<br>Differences: add(key: number, value: T): void;|api/@ohos.util.PlainArray.d.ts|
|New API|NA|Class name: PlainArray;<br>API declaration: clear(): void;<br>Differences: clear(): void;|api/@ohos.util.PlainArray.d.ts|
|New API|NA|Class name: PlainArray;<br>API declaration: clone(): PlainArray\<T>;<br>Differences: clone(): PlainArray\<T>;|api/@ohos.util.PlainArray.d.ts|
|New API|NA|Class name: PlainArray;<br>API declaration: has(key: number): boolean;<br>Differences: has(key: number): boolean;|api/@ohos.util.PlainArray.d.ts|
|New API|NA|Class name: PlainArray;<br>API declaration: get(key: number): T;<br>Differences: get(key: number): T;|api/@ohos.util.PlainArray.d.ts|
|New API|NA|Class name: PlainArray;<br>API declaration: getIndexOfKey(key: number): number;<br>Differences: getIndexOfKey(key: number): number;|api/@ohos.util.PlainArray.d.ts|
|New API|NA|Class name: PlainArray;<br>API declaration: getIndexOfValue(value: T): number;<br>Differences: getIndexOfValue(value: T): number;|api/@ohos.util.PlainArray.d.ts|
|New API|NA|Class name: PlainArray;<br>API declaration: isEmpty(): boolean;<br>Differences: isEmpty(): boolean;|api/@ohos.util.PlainArray.d.ts|
|New API|NA|Class name: PlainArray;<br>API declaration: getKeyAt(index: number): number;<br>Differences: getKeyAt(index: number): number;|api/@ohos.util.PlainArray.d.ts|
|New API|NA|Class name: PlainArray;<br>API declaration: remove(key: number): T;<br>Differences: remove(key: number): T;|api/@ohos.util.PlainArray.d.ts|
|New API|NA|Class name: PlainArray;<br>API declaration: removeAt(index: number): T;<br>Differences: removeAt(index: number): T;|api/@ohos.util.PlainArray.d.ts|
|New API|NA|Class name: PlainArray;<br>API declaration: removeRangeFrom(index: number, size: number): number;<br>Differences: removeRangeFrom(index: number, size: number): number;|api/@ohos.util.PlainArray.d.ts|
|New API|NA|Class name: PlainArray;<br>API declaration: setValueAt(index: number, value: T): void;<br>Differences: setValueAt(index: number, value: T): void;|api/@ohos.util.PlainArray.d.ts|
|New API|NA|Class name: PlainArray;<br>API declaration: toString(): String;<br>Differences: toString(): String;|api/@ohos.util.PlainArray.d.ts|
|New API|NA|Class name: PlainArray;<br>API declaration: getValueAt(index: number): T;<br>Differences: getValueAt(index: number): T;|api/@ohos.util.PlainArray.d.ts|
|New API|NA|Class name: PlainArray;<br>API declaration: forEach(callbackFn: (value: T, index?: number, PlainArray?: PlainArray\<T>) => void, thisArg?: Object): void;<br>Differences: forEach(callbackFn: (value: T, index?: number, PlainArray?: PlainArray\<T>) => void, thisArg?: Object): void;|api/@ohos.util.PlainArray.d.ts|
|New API|NA|Class name: PlainArray;<br>API declaration: [Symbol.iterator](): IterableIterator\<[<br>        number,<br>        T<br>    ]>;<br>Differences: [Symbol.iterator](): IterableIterator\<[<br>        number,<br>        T<br>    ]>;|api/@ohos.util.PlainArray.d.ts|
|New API|NA|Class name: global;<br>API declaration: declare class Queue<br>Differences: declare class Queue|api/@ohos.util.Queue.d.ts|
|New API|NA|Class name: Queue;<br>API declaration: length: number;<br>Differences: length: number;|api/@ohos.util.Queue.d.ts|
|New API|NA|Class name: Queue;<br>API declaration: add(element: T): boolean;<br>Differences: add(element: T): boolean;|api/@ohos.util.Queue.d.ts|
|New API|NA|Class name: Queue;<br>API declaration: getFirst(): T;<br>Differences: getFirst(): T;|api/@ohos.util.Queue.d.ts|
|New API|NA|Class name: Queue;<br>API declaration: pop(): T;<br>Differences: pop(): T;|api/@ohos.util.Queue.d.ts|
|New API|NA|Class name: Queue;<br>API declaration: forEach(callbackFn: (value: T, index?: number, Queue?: Queue\<T>) => void, thisArg?: Object): void;<br>Differences: forEach(callbackFn: (value: T, index?: number, Queue?: Queue\<T>) => void, thisArg?: Object): void;|api/@ohos.util.Queue.d.ts|
|New API|NA|Class name: Queue;<br>API declaration: [Symbol.iterator](): IterableIterator\<T>;<br>Differences: [Symbol.iterator](): IterableIterator\<T>;|api/@ohos.util.Queue.d.ts|
|New API|NA|Class name: global;<br>API declaration: declare class Stack<br>Differences: declare class Stack|api/@ohos.util.Stack.d.ts|
|New API|NA|Class name: Stack;<br>API declaration: length: number;<br>Differences: length: number;|api/@ohos.util.Stack.d.ts|
|New API|NA|Class name: Stack;<br>API declaration: isEmpty(): boolean;<br>Differences: isEmpty(): boolean;|api/@ohos.util.Stack.d.ts|
|New API|NA|Class name: Stack;<br>API declaration: peek(): T;<br>Differences: peek(): T;|api/@ohos.util.Stack.d.ts|
|New API|NA|Class name: Stack;<br>API declaration: pop(): T;<br>Differences: pop(): T;|api/@ohos.util.Stack.d.ts|
|New API|NA|Class name: Stack;<br>API declaration: push(item: T): T;<br>Differences: push(item: T): T;|api/@ohos.util.Stack.d.ts|
|New API|NA|Class name: Stack;<br>API declaration: locate(element: T): number;<br>Differences: locate(element: T): number;|api/@ohos.util.Stack.d.ts|
|New API|NA|Class name: Stack;<br>API declaration: forEach(callbackFn: (value: T, index?: number, stack?: Stack\<T>) => void, thisArg?: Object): void;<br>Differences: forEach(callbackFn: (value: T, index?: number, stack?: Stack\<T>) => void, thisArg?: Object): void;|api/@ohos.util.Stack.d.ts|
|New API|NA|Class name: Stack;<br>API declaration: [Symbol.iterator](): IterableIterator\<T>;<br>Differences: [Symbol.iterator](): IterableIterator\<T>;|api/@ohos.util.Stack.d.ts|
|New API|NA|Class name: global;<br>API declaration: declare class TreeMap<br>Differences: declare class TreeMap|api/@ohos.util.TreeMap.d.ts|
|New API|NA|Class name: TreeMap;<br>API declaration: length: number;<br>Differences: length: number;|api/@ohos.util.TreeMap.d.ts|
|New API|NA|Class name: TreeMap;<br>API declaration: isEmpty(): boolean;<br>Differences: isEmpty(): boolean;|api/@ohos.util.TreeMap.d.ts|
|New API|NA|Class name: TreeMap;<br>API declaration: hasKey(key: K): boolean;<br>Differences: hasKey(key: K): boolean;|api/@ohos.util.TreeMap.d.ts|
|New API|NA|Class name: TreeMap;<br>API declaration: hasValue(value: V): boolean;<br>Differences: hasValue(value: V): boolean;|api/@ohos.util.TreeMap.d.ts|
|New API|NA|Class name: TreeMap;<br>API declaration: get(key: K): V;<br>Differences: get(key: K): V;|api/@ohos.util.TreeMap.d.ts|
|New API|NA|Class name: TreeMap;<br>API declaration: getFirstKey(): K;<br>Differences: getFirstKey(): K;|api/@ohos.util.TreeMap.d.ts|
|New API|NA|Class name: TreeMap;<br>API declaration: getLastKey(): K;<br>Differences: getLastKey(): K;|api/@ohos.util.TreeMap.d.ts|
|New API|NA|Class name: TreeMap;<br>API declaration: setAll(map: TreeMap\<K, V>): void;<br>Differences: setAll(map: TreeMap\<K, V>): void;|api/@ohos.util.TreeMap.d.ts|
|New API|NA|Class name: TreeMap;<br>API declaration: set(key: K, value: V): Object;<br>Differences: set(key: K, value: V): Object;|api/@ohos.util.TreeMap.d.ts|
|New API|NA|Class name: TreeMap;<br>API declaration: remove(key: K): V;<br>Differences: remove(key: K): V;|api/@ohos.util.TreeMap.d.ts|
|New API|NA|Class name: TreeMap;<br>API declaration: clear(): void;<br>Differences: clear(): void;|api/@ohos.util.TreeMap.d.ts|
|New API|NA|Class name: TreeMap;<br>API declaration: getLowerKey(key: K): K;<br>Differences: getLowerKey(key: K): K;|api/@ohos.util.TreeMap.d.ts|
|New API|NA|Class name: TreeMap;<br>API declaration: getHigherKey(key: K): K;<br>Differences: getHigherKey(key: K): K;|api/@ohos.util.TreeMap.d.ts|
|New API|NA|Class name: TreeMap;<br>API declaration: keys(): IterableIterator\<K>;<br>Differences: keys(): IterableIterator\<K>;|api/@ohos.util.TreeMap.d.ts|
|New API|NA|Class name: TreeMap;<br>API declaration: values(): IterableIterator\<V>;<br>Differences: values(): IterableIterator\<V>;|api/@ohos.util.TreeMap.d.ts|
|New API|NA|Class name: TreeMap;<br>API declaration: replace(key: K, newValue: V): boolean;<br>Differences: replace(key: K, newValue: V): boolean;|api/@ohos.util.TreeMap.d.ts|
|New API|NA|Class name: TreeMap;<br>API declaration: forEach(callbackFn: (value?: V, key?: K, map?: TreeMap\<K, V>) => void, thisArg?: Object): void;<br>Differences: forEach(callbackFn: (value?: V, key?: K, map?: TreeMap\<K, V>) => void, thisArg?: Object): void;|api/@ohos.util.TreeMap.d.ts|
|New API|NA|Class name: TreeMap;<br>API declaration: entries(): IterableIterator\<[<br>        K,<br>        V<br>    ]>;<br>Differences: entries(): IterableIterator\<[<br>        K,<br>        V<br>    ]>;|api/@ohos.util.TreeMap.d.ts|
|New API|NA|Class name: TreeMap;<br>API declaration: [Symbol.iterator](): IterableIterator\<[<br>        K,<br>        V<br>    ]>;<br>Differences: [Symbol.iterator](): IterableIterator\<[<br>        K,<br>        V<br>    ]>;|api/@ohos.util.TreeMap.d.ts|
|New API|NA|Class name: global;<br>API declaration: declare class TreeSet<br>Differences: declare class TreeSet|api/@ohos.util.TreeSet.d.ts|
|New API|NA|Class name: TreeSet;<br>API declaration: length: number;<br>Differences: length: number;|api/@ohos.util.TreeSet.d.ts|
|New API|NA|Class name: TreeSet;<br>API declaration: isEmpty(): boolean;<br>Differences: isEmpty(): boolean;|api/@ohos.util.TreeSet.d.ts|
|New API|NA|Class name: TreeSet;<br>API declaration: has(value: T): boolean;<br>Differences: has(value: T): boolean;|api/@ohos.util.TreeSet.d.ts|
|New API|NA|Class name: TreeSet;<br>API declaration: add(value: T): boolean;<br>Differences: add(value: T): boolean;|api/@ohos.util.TreeSet.d.ts|
|New API|NA|Class name: TreeSet;<br>API declaration: remove(value: T): boolean;<br>Differences: remove(value: T): boolean;|api/@ohos.util.TreeSet.d.ts|
|New API|NA|Class name: TreeSet;<br>API declaration: clear(): void;<br>Differences: clear(): void;|api/@ohos.util.TreeSet.d.ts|
|New API|NA|Class name: TreeSet;<br>API declaration: getFirstValue(): T;<br>Differences: getFirstValue(): T;|api/@ohos.util.TreeSet.d.ts|
|New API|NA|Class name: TreeSet;<br>API declaration: getLastValue(): T;<br>Differences: getLastValue(): T;|api/@ohos.util.TreeSet.d.ts|
|New API|NA|Class name: TreeSet;<br>API declaration: getLowerValue(key: T): T;<br>Differences: getLowerValue(key: T): T;|api/@ohos.util.TreeSet.d.ts|
|New API|NA|Class name: TreeSet;<br>API declaration: getHigherValue(key: T): T;<br>Differences: getHigherValue(key: T): T;|api/@ohos.util.TreeSet.d.ts|
|New API|NA|Class name: TreeSet;<br>API declaration: popFirst(): T;<br>Differences: popFirst(): T;|api/@ohos.util.TreeSet.d.ts|
|New API|NA|Class name: TreeSet;<br>API declaration: popLast(): T;<br>Differences: popLast(): T;|api/@ohos.util.TreeSet.d.ts|
|New API|NA|Class name: TreeSet;<br>API declaration: forEach(callbackFn: (value?: T, key?: T, set?: TreeSet\<T>) => void, thisArg?: Object): void;<br>Differences: forEach(callbackFn: (value?: T, key?: T, set?: TreeSet\<T>) => void, thisArg?: Object): void;|api/@ohos.util.TreeSet.d.ts|
|New API|NA|Class name: TreeSet;<br>API declaration: values(): IterableIterator\<T>;<br>Differences: values(): IterableIterator\<T>;|api/@ohos.util.TreeSet.d.ts|
|New API|NA|Class name: TreeSet;<br>API declaration: entries(): IterableIterator\<[<br>        T,<br>        T<br>    ]>;<br>Differences: entries(): IterableIterator\<[<br>        T,<br>        T<br>    ]>;|api/@ohos.util.TreeSet.d.ts|
|New API|NA|Class name: TreeSet;<br>API declaration: [Symbol.iterator](): IterableIterator\<T>;<br>Differences: [Symbol.iterator](): IterableIterator\<T>;|api/@ohos.util.TreeSet.d.ts|
|New API|NA|Class name: global;<br>API declaration: declare class Vector<br>Differences: declare class Vector|api/@ohos.util.Vector.d.ts|
|New API|NA|Class name: Vector;<br>API declaration: length: number;<br>Differences: length: number;|api/@ohos.util.Vector.d.ts|
|New API|NA|Class name: Vector;<br>API declaration: add(element: T): boolean;<br>Differences: add(element: T): boolean;|api/@ohos.util.Vector.d.ts|
|New API|NA|Class name: Vector;<br>API declaration: insert(element: T, index: number): void;<br>Differences: insert(element: T, index: number): void;|api/@ohos.util.Vector.d.ts|
|New API|NA|Class name: Vector;<br>API declaration: has(element: T): boolean;<br>Differences: has(element: T): boolean;|api/@ohos.util.Vector.d.ts|
|New API|NA|Class name: Vector;<br>API declaration: get(index: number): T;<br>Differences: get(index: number): T;|api/@ohos.util.Vector.d.ts|
|New API|NA|Class name: Vector;<br>API declaration: getIndexOf(element: T): number;<br>Differences: getIndexOf(element: T): number;|api/@ohos.util.Vector.d.ts|
|New API|NA|Class name: Vector;<br>API declaration: getFirstElement(): T;<br>Differences: getFirstElement(): T;|api/@ohos.util.Vector.d.ts|
|New API|NA|Class name: Vector;<br>API declaration: getLastElement(): T;<br>Differences: getLastElement(): T;|api/@ohos.util.Vector.d.ts|
|New API|NA|Class name: Vector;<br>API declaration: removeByIndex(index: number): T;<br>Differences: removeByIndex(index: number): T;|api/@ohos.util.Vector.d.ts|
|New API|NA|Class name: Vector;<br>API declaration: remove(element: T): boolean;<br>Differences: remove(element: T): boolean;|api/@ohos.util.Vector.d.ts|
|New API|NA|Class name: Vector;<br>API declaration: set(index: number, element: T): T;<br>Differences: set(index: number, element: T): T;|api/@ohos.util.Vector.d.ts|
|New API|NA|Class name: Vector;<br>API declaration: getLastIndexOf(element: T): number;<br>Differences: getLastIndexOf(element: T): number;|api/@ohos.util.Vector.d.ts|
|New API|NA|Class name: Vector;<br>API declaration: getLastIndexFrom(element: T, index: number): number;<br>Differences: getLastIndexFrom(element: T, index: number): number;|api/@ohos.util.Vector.d.ts|
|New API|NA|Class name: Vector;<br>API declaration: getIndexFrom(element: T, index: number): number;<br>Differences: getIndexFrom(element: T, index: number): number;|api/@ohos.util.Vector.d.ts|
|New API|NA|Class name: Vector;<br>API declaration: removeByRange(fromIndex: number, toIndex: number): void;<br>Differences: removeByRange(fromIndex: number, toIndex: number): void;|api/@ohos.util.Vector.d.ts|
|New API|NA|Class name: Vector;<br>API declaration: replaceAllElements(callbackFn: (value: T, index?: number, vector?: Vector\<T>) => T, thisArg?: Object): void;<br>Differences: replaceAllElements(callbackFn: (value: T, index?: number, vector?: Vector\<T>) => T, thisArg?: Object): void;|api/@ohos.util.Vector.d.ts|
|New API|NA|Class name: Vector;<br>API declaration: forEach(callbackFn: (value: T, index?: number, vector?: Vector\<T>) => void, thisArg?: Object): void;<br>Differences: forEach(callbackFn: (value: T, index?: number, vector?: Vector\<T>) => void, thisArg?: Object): void;|api/@ohos.util.Vector.d.ts|
|New API|NA|Class name: Vector;<br>API declaration: sort(comparator?: (firstValue: T, secondValue: T) => number): void;<br>Differences: sort(comparator?: (firstValue: T, secondValue: T) => number): void;|api/@ohos.util.Vector.d.ts|
|New API|NA|Class name: Vector;<br>API declaration: subVector(fromIndex: number, toIndex: number): Vector\<T>;<br>Differences: subVector(fromIndex: number, toIndex: number): Vector\<T>;|api/@ohos.util.Vector.d.ts|
|New API|NA|Class name: Vector;<br>API declaration: clear(): void;<br>Differences: clear(): void;|api/@ohos.util.Vector.d.ts|
|New API|NA|Class name: Vector;<br>API declaration: clone(): Vector\<T>;<br>Differences: clone(): Vector\<T>;|api/@ohos.util.Vector.d.ts|
|New API|NA|Class name: Vector;<br>API declaration: setLength(newSize: number): void;<br>Differences: setLength(newSize: number): void;|api/@ohos.util.Vector.d.ts|
|New API|NA|Class name: Vector;<br>API declaration: getCapacity(): number;<br>Differences: getCapacity(): number;|api/@ohos.util.Vector.d.ts|
|New API|NA|Class name: Vector;<br>API declaration: convertToArray(): Array\<T>;<br>Differences: convertToArray(): Array\<T>;|api/@ohos.util.Vector.d.ts|
|New API|NA|Class name: Vector;<br>API declaration: isEmpty(): boolean;<br>Differences: isEmpty(): boolean;|api/@ohos.util.Vector.d.ts|
|New API|NA|Class name: Vector;<br>API declaration: increaseCapacityTo(newCapacity: number): void;<br>Differences: increaseCapacityTo(newCapacity: number): void;|api/@ohos.util.Vector.d.ts|
|New API|NA|Class name: Vector;<br>API declaration: toString(): string;<br>Differences: toString(): string;|api/@ohos.util.Vector.d.ts|
|New API|NA|Class name: Vector;<br>API declaration: trimToCurrentLength(): void;<br>Differences: trimToCurrentLength(): void;|api/@ohos.util.Vector.d.ts|
|New API|NA|Class name: Vector;<br>API declaration: copyToArray(array: Array\<T>): void;<br>Differences: copyToArray(array: Array\<T>): void;|api/@ohos.util.Vector.d.ts|
|New API|NA|Class name: Vector;<br>API declaration: [Symbol.iterator](): IterableIterator\<T>;<br>Differences: [Symbol.iterator](): IterableIterator\<T>;|api/@ohos.util.Vector.d.ts|
|New API|NA|Class name: global;<br>API declaration: export interface WorkerOptions<br>Differences: export interface WorkerOptions|api/@ohos.worker.d.ts|
|New API|NA|Class name: WorkerOptions;<br>API declaration: type?: 'classic' \| 'module';<br>Differences: type?: 'classic' \| 'module';|api/@ohos.worker.d.ts|
|New API|NA|Class name: WorkerOptions;<br>API declaration: name?: string;<br>Differences: name?: string;|api/@ohos.worker.d.ts|
|New API|NA|Class name: WorkerOptions;<br>API declaration: shared?: boolean;<br>Differences: shared?: boolean;|api/@ohos.worker.d.ts|
|New API|NA|Class name: global;<br>API declaration: export interface Event<br>Differences: export interface Event|api/@ohos.worker.d.ts|
|New API|NA|Class name: Event;<br>API declaration: readonly type: string;<br>Differences: readonly type: string;|api/@ohos.worker.d.ts|
|New API|NA|Class name: Event;<br>API declaration: readonly timeStamp: number;<br>Differences: readonly timeStamp: number;|api/@ohos.worker.d.ts|
|New API|NA|Class name: global;<br>API declaration: export interface ErrorEvent<br>Differences: export interface ErrorEvent|api/@ohos.worker.d.ts|
|New API|NA|Class name: ErrorEvent;<br>API declaration: readonly message: string;<br>Differences: readonly message: string;|api/@ohos.worker.d.ts|
|New API|NA|Class name: ErrorEvent;<br>API declaration: readonly filename: string;<br>Differences: readonly filename: string;|api/@ohos.worker.d.ts|
|New API|NA|Class name: ErrorEvent;<br>API declaration: readonly lineno: number;<br>Differences: readonly lineno: number;|api/@ohos.worker.d.ts|
|New API|NA|Class name: ErrorEvent;<br>API declaration: readonly colno: number;<br>Differences: readonly colno: number;|api/@ohos.worker.d.ts|
|New API|NA|Class name: ErrorEvent;<br>API declaration: readonly error: Object;<br>Differences: readonly error: Object;|api/@ohos.worker.d.ts|
|New API|NA|Class name: global;<br>API declaration: export interface MessageEvent<br>Differences: export interface MessageEvent|api/@ohos.worker.d.ts|
|New API|NA|Class name: MessageEvent;<br>API declaration: readonly data: T;<br>Differences: readonly data: T;|api/@ohos.worker.d.ts|
|New API|NA|Class name: global;<br>API declaration: export interface MessageEvents<br>Differences: export interface MessageEvents|api/@ohos.worker.d.ts|
|New API|NA|Class name: MessageEvents;<br>API declaration: readonly data;<br>Differences: readonly data;|api/@ohos.worker.d.ts|
|New API|NA|Class name: global;<br>API declaration: export interface PostMessageOptions<br>Differences: export interface PostMessageOptions|api/@ohos.worker.d.ts|
|New API|NA|Class name: PostMessageOptions;<br>API declaration: transfer?: Object[];<br>Differences: transfer?: Object[];|api/@ohos.worker.d.ts|
|New API|NA|Class name: global;<br>API declaration: export interface EventListener<br>Differences: export interface EventListener|api/@ohos.worker.d.ts|
|New API|NA|Class name: global;<br>API declaration: export interface WorkerEventListener<br>Differences: export interface WorkerEventListener|api/@ohos.worker.d.ts|
|New API|NA|Class name: global;<br>API declaration: type MessageType = 'message' \| 'messageerror';<br>Differences: type MessageType = 'message' \| 'messageerror';|api/@ohos.worker.d.ts|
|New API|NA|Class name: global;<br>API declaration: export interface EventTarget<br>Differences: export interface EventTarget|api/@ohos.worker.d.ts|
|New API|NA|Class name: EventTarget;<br>API declaration: addEventListener(type: string, listener: EventListener): void;<br>Differences: addEventListener(type: string, listener: EventListener): void;|api/@ohos.worker.d.ts|
|New API|NA|Class name: EventTarget;<br>API declaration: dispatchEvent(event: Event): boolean;<br>Differences: dispatchEvent(event: Event): boolean;|api/@ohos.worker.d.ts|
|New API|NA|Class name: EventTarget;<br>API declaration: removeEventListener(type: string, callback?: EventListener): void;<br>Differences: removeEventListener(type: string, callback?: EventListener): void;|api/@ohos.worker.d.ts|
|New API|NA|Class name: EventTarget;<br>API declaration: removeAllListener(): void;<br>Differences: removeAllListener(): void;|api/@ohos.worker.d.ts|
|New API|NA|Class name: global;<br>API declaration: export interface WorkerEventTarget<br>Differences: export interface WorkerEventTarget|api/@ohos.worker.d.ts|
|New API|NA|Class name: WorkerEventTarget;<br>API declaration: addEventListener(type: string, listener: WorkerEventListener): void;<br>Differences: addEventListener(type: string, listener: WorkerEventListener): void;|api/@ohos.worker.d.ts|
|New API|NA|Class name: WorkerEventTarget;<br>API declaration: dispatchEvent(event: Event): boolean;<br>Differences: dispatchEvent(event: Event): boolean;|api/@ohos.worker.d.ts|
|New API|NA|Class name: WorkerEventTarget;<br>API declaration: removeEventListener(type: string, callback?: WorkerEventListener): void;<br>Differences: removeEventListener(type: string, callback?: WorkerEventListener): void;|api/@ohos.worker.d.ts|
|New API|NA|Class name: WorkerEventTarget;<br>API declaration: removeAllListener(): void;<br>Differences: removeAllListener(): void;|api/@ohos.worker.d.ts|
|New API|NA|Class name: global;<br>API declaration: declare interface WorkerGlobalScope<br>Differences: declare interface WorkerGlobalScope|api/@ohos.worker.d.ts|
|New API|NA|Class name: WorkerGlobalScope;<br>API declaration: readonly name: string;<br>Differences: readonly name: string;|api/@ohos.worker.d.ts|
|New API|NA|Class name: WorkerGlobalScope;<br>API declaration: onerror?: (ev: ErrorEvent) => void;<br>Differences: onerror?: (ev: ErrorEvent) => void;|api/@ohos.worker.d.ts|
|New API|NA|Class name: WorkerGlobalScope;<br>API declaration: readonly self: WorkerGlobalScope & typeof globalThis;<br>Differences: readonly self: WorkerGlobalScope & typeof globalThis;|api/@ohos.worker.d.ts|
|New API|NA|Class name: global;<br>API declaration: declare interface GlobalScope<br>Differences: declare interface GlobalScope|api/@ohos.worker.d.ts|
|New API|NA|Class name: GlobalScope;<br>API declaration: readonly name: string;<br>Differences: readonly name: string;|api/@ohos.worker.d.ts|
|New API|NA|Class name: GlobalScope;<br>API declaration: onerror?: (ev: ErrorEvent) => void;<br>Differences: onerror?: (ev: ErrorEvent) => void;|api/@ohos.worker.d.ts|
|New API|NA|Class name: GlobalScope;<br>API declaration: readonly self: GlobalScope & typeof globalThis;<br>Differences: readonly self: GlobalScope & typeof globalThis;|api/@ohos.worker.d.ts|
|New API|NA|Class name: global;<br>API declaration: export interface DedicatedWorkerGlobalScope<br>Differences: export interface DedicatedWorkerGlobalScope|api/@ohos.worker.d.ts|
|New API|NA|Class name: DedicatedWorkerGlobalScope;<br>API declaration: onmessage?: (this: DedicatedWorkerGlobalScope, ev: MessageEvent) => void;<br>Differences: onmessage?: (this: DedicatedWorkerGlobalScope, ev: MessageEvent) => void;|api/@ohos.worker.d.ts|
|New API|NA|Class name: DedicatedWorkerGlobalScope;<br>API declaration: onmessageerror?: (this: DedicatedWorkerGlobalScope, ev: MessageEvent) => void;<br>Differences: onmessageerror?: (this: DedicatedWorkerGlobalScope, ev: MessageEvent) => void;|api/@ohos.worker.d.ts|
|New API|NA|Class name: DedicatedWorkerGlobalScope;<br>API declaration: close(): void;<br>Differences: close(): void;|api/@ohos.worker.d.ts|
|New API|NA|Class name: DedicatedWorkerGlobalScope;<br>API declaration: postMessage(messageObject: Object, transfer: Transferable[]): void;<br>Differences: postMessage(messageObject: Object, transfer: Transferable[]): void;|api/@ohos.worker.d.ts|
|New API|NA|Class name: DedicatedWorkerGlobalScope;<br>API declaration: postMessage(messageObject: Object, options?: PostMessageOptions): void;<br>Differences: postMessage(messageObject: Object, options?: PostMessageOptions): void;|api/@ohos.worker.d.ts|
|New API|NA|Class name: DedicatedWorkerGlobalScope;<br>API declaration: postMessage(messageObject: Object, transfer: ArrayBuffer[]): void;<br>Differences: postMessage(messageObject: Object, transfer: ArrayBuffer[]): void;|api/@ohos.worker.d.ts|
|New API|NA|Class name: global;<br>API declaration: export interface ThreadWorkerGlobalScope<br>Differences: export interface ThreadWorkerGlobalScope|api/@ohos.worker.d.ts|
|New API|NA|Class name: ThreadWorkerGlobalScope;<br>API declaration: onmessage?: (this: ThreadWorkerGlobalScope, ev: MessageEvents) => void;<br>Differences: onmessage?: (this: ThreadWorkerGlobalScope, ev: MessageEvents) => void;|api/@ohos.worker.d.ts|
|New API|NA|Class name: ThreadWorkerGlobalScope;<br>API declaration: onmessageerror?: (this: ThreadWorkerGlobalScope, ev: MessageEvents) => void;<br>Differences: onmessageerror?: (this: ThreadWorkerGlobalScope, ev: MessageEvents) => void;|api/@ohos.worker.d.ts|
|New API|NA|Class name: ThreadWorkerGlobalScope;<br>API declaration: close(): void;<br>Differences: close(): void;|api/@ohos.worker.d.ts|
|New API|NA|Class name: ThreadWorkerGlobalScope;<br>API declaration: postMessage(messageObject: Object, transfer: ArrayBuffer[]): void;<br>Differences: postMessage(messageObject: Object, transfer: ArrayBuffer[]): void;|api/@ohos.worker.d.ts|
|New API|NA|Class name: ThreadWorkerGlobalScope;<br>API declaration: postMessage(messageObject: Object, options?: PostMessageOptions): void;<br>Differences: postMessage(messageObject: Object, options?: PostMessageOptions): void;|api/@ohos.worker.d.ts|
|New API|NA|Class name: ThreadWorkerGlobalScope;<br>API declaration: callGlobalCallObjectMethod(instanceName: string, methodName: string, timeout: number, ...args: Object[]): Object;<br>Differences: callGlobalCallObjectMethod(instanceName: string, methodName: string, timeout: number, ...args: Object[]): Object;|api/@ohos.worker.d.ts|
|New API|NA|Class name: global;<br>API declaration: declare namespace worker<br>Differences: declare namespace worker|api/@ohos.worker.d.ts|
|New API|NA|Class name: worker;<br>API declaration: class ThreadWorker<br>Differences: class ThreadWorker|api/@ohos.worker.d.ts|
|New API|NA|Class name: ThreadWorker;<br>API declaration: onexit?: (code: number) => void;<br>Differences: onexit?: (code: number) => void;|api/@ohos.worker.d.ts|
|New API|NA|Class name: ThreadWorker;<br>API declaration: onerror?: (err: ErrorEvent) => void;<br>Differences: onerror?: (err: ErrorEvent) => void;|api/@ohos.worker.d.ts|
|New API|NA|Class name: ThreadWorker;<br>API declaration: onmessage?: (event: MessageEvents) => void;<br>Differences: onmessage?: (event: MessageEvents) => void;|api/@ohos.worker.d.ts|
|New API|NA|Class name: ThreadWorker;<br>API declaration: onmessageerror?: (event: MessageEvents) => void;<br>Differences: onmessageerror?: (event: MessageEvents) => void;|api/@ohos.worker.d.ts|
|New API|NA|Class name: ThreadWorker;<br>API declaration: postMessage(message: Object, transfer: ArrayBuffer[]): void;<br>Differences: postMessage(message: Object, transfer: ArrayBuffer[]): void;|api/@ohos.worker.d.ts|
|New API|NA|Class name: ThreadWorker;<br>API declaration: postMessage(message: Object, options?: PostMessageOptions): void;<br>Differences: postMessage(message: Object, options?: PostMessageOptions): void;|api/@ohos.worker.d.ts|
|New API|NA|Class name: ThreadWorker;<br>API declaration: on(type: string, listener: WorkerEventListener): void;<br>Differences: on(type: string, listener: WorkerEventListener): void;|api/@ohos.worker.d.ts|
|New API|NA|Class name: ThreadWorker;<br>API declaration: once(type: string, listener: WorkerEventListener): void;<br>Differences: once(type: string, listener: WorkerEventListener): void;|api/@ohos.worker.d.ts|
|New API|NA|Class name: ThreadWorker;<br>API declaration: off(type: string, listener?: WorkerEventListener): void;<br>Differences: off(type: string, listener?: WorkerEventListener): void;|api/@ohos.worker.d.ts|
|New API|NA|Class name: ThreadWorker;<br>API declaration: terminate(): void;<br>Differences: terminate(): void;|api/@ohos.worker.d.ts|
|New API|NA|Class name: ThreadWorker;<br>API declaration: addEventListener(type: string, listener: WorkerEventListener): void;<br>Differences: addEventListener(type: string, listener: WorkerEventListener): void;|api/@ohos.worker.d.ts|
|New API|NA|Class name: ThreadWorker;<br>API declaration: dispatchEvent(event: Event): boolean;<br>Differences: dispatchEvent(event: Event): boolean;|api/@ohos.worker.d.ts|
|New API|NA|Class name: ThreadWorker;<br>API declaration: removeEventListener(type: string, callback?: WorkerEventListener): void;<br>Differences: removeEventListener(type: string, callback?: WorkerEventListener): void;|api/@ohos.worker.d.ts|
|New API|NA|Class name: ThreadWorker;<br>API declaration: removeAllListener(): void;<br>Differences: removeAllListener(): void;|api/@ohos.worker.d.ts|
|New API|NA|Class name: ThreadWorker;<br>API declaration: registerGlobalCallObject(instanceName: string, globalCallObject: Object): void;<br>Differences: registerGlobalCallObject(instanceName: string, globalCallObject: Object): void;|api/@ohos.worker.d.ts|
|New API|NA|Class name: ThreadWorker;<br>API declaration: unregisterGlobalCallObject(instanceName?: string): void;<br>Differences: unregisterGlobalCallObject(instanceName?: string): void;|api/@ohos.worker.d.ts|
|New API|NA|Class name: worker;<br>API declaration: class RestrictedWorker<br>Differences: class RestrictedWorker|api/@ohos.worker.d.ts|
|New API|NA|Class name: worker;<br>API declaration: class Worker<br>Differences: class Worker|api/@ohos.worker.d.ts|
|New API|NA|Class name: Worker;<br>API declaration: onexit?: (code: number) => void;<br>Differences: onexit?: (code: number) => void;|api/@ohos.worker.d.ts|
|New API|NA|Class name: Worker;<br>API declaration: onerror?: (err: ErrorEvent) => void;<br>Differences: onerror?: (err: ErrorEvent) => void;|api/@ohos.worker.d.ts|
|New API|NA|Class name: Worker;<br>API declaration: onmessage?: (event: MessageEvent) => void;<br>Differences: onmessage?: (event: MessageEvent) => void;|api/@ohos.worker.d.ts|
|New API|NA|Class name: Worker;<br>API declaration: onmessageerror?: (event: MessageEvent) => void;<br>Differences: onmessageerror?: (event: MessageEvent) => void;|api/@ohos.worker.d.ts|
|New API|NA|Class name: Worker;<br>API declaration: postMessage(message: Object, transfer: ArrayBuffer[]): void;<br>Differences: postMessage(message: Object, transfer: ArrayBuffer[]): void;|api/@ohos.worker.d.ts|
|New API|NA|Class name: Worker;<br>API declaration: postMessage(message: Object, options?: PostMessageOptions): void;<br>Differences: postMessage(message: Object, options?: PostMessageOptions): void;|api/@ohos.worker.d.ts|
|New API|NA|Class name: Worker;<br>API declaration: on(type: string, listener: EventListener): void;<br>Differences: on(type: string, listener: EventListener): void;|api/@ohos.worker.d.ts|
|New API|NA|Class name: Worker;<br>API declaration: once(type: string, listener: EventListener): void;<br>Differences: once(type: string, listener: EventListener): void;|api/@ohos.worker.d.ts|
|New API|NA|Class name: Worker;<br>API declaration: off(type: string, listener?: EventListener): void;<br>Differences: off(type: string, listener?: EventListener): void;|api/@ohos.worker.d.ts|
|New API|NA|Class name: Worker;<br>API declaration: terminate(): void;<br>Differences: terminate(): void;|api/@ohos.worker.d.ts|
|New API|NA|Class name: worker;<br>API declaration: const parentPort: DedicatedWorkerGlobalScope;<br>Differences: const parentPort: DedicatedWorkerGlobalScope;|api/@ohos.worker.d.ts|
|New API|NA|Class name: worker;<br>API declaration: const workerPort: ThreadWorkerGlobalScope;<br>Differences: const workerPort: ThreadWorkerGlobalScope;|api/@ohos.worker.d.ts|
|New API|NA|Class name: global;<br>API declaration: declare namespace xml<br>Differences: declare namespace xml|api/@ohos.xml.d.ts|
|New API|NA|Class name: xml;<br>API declaration: class XmlSerializer<br>Differences: class XmlSerializer|api/@ohos.xml.d.ts|
|New API|NA|Class name: XmlSerializer;<br>API declaration: setAttributes(name: string, value: string): void;<br>Differences: setAttributes(name: string, value: string): void;|api/@ohos.xml.d.ts|
|New API|NA|Class name: XmlSerializer;<br>API declaration: addEmptyElement(name: string): void;<br>Differences: addEmptyElement(name: string): void;|api/@ohos.xml.d.ts|
|New API|NA|Class name: XmlSerializer;<br>API declaration: setDeclaration(): void;<br>Differences: setDeclaration(): void;|api/@ohos.xml.d.ts|
|New API|NA|Class name: XmlSerializer;<br>API declaration: startElement(name: string): void;<br>Differences: startElement(name: string): void;|api/@ohos.xml.d.ts|
|New API|NA|Class name: XmlSerializer;<br>API declaration: endElement(): void;<br>Differences: endElement(): void;|api/@ohos.xml.d.ts|
|New API|NA|Class name: XmlSerializer;<br>API declaration: setNamespace(prefix: string, namespace: string): void;<br>Differences: setNamespace(prefix: string, namespace: string): void;|api/@ohos.xml.d.ts|
|New API|NA|Class name: XmlSerializer;<br>API declaration: setComment(text: string): void;<br>Differences: setComment(text: string): void;|api/@ohos.xml.d.ts|
|New API|NA|Class name: XmlSerializer;<br>API declaration: setCDATA(text: string): void;<br>Differences: setCDATA(text: string): void;|api/@ohos.xml.d.ts|
|New API|NA|Class name: XmlSerializer;<br>API declaration: setText(text: string): void;<br>Differences: setText(text: string): void;|api/@ohos.xml.d.ts|
|New API|NA|Class name: XmlSerializer;<br>API declaration: setDocType(text: string): void;<br>Differences: setDocType(text: string): void;|api/@ohos.xml.d.ts|
|New API|NA|Class name: xml;<br>API declaration: enum EventType<br>Differences: enum EventType|api/@ohos.xml.d.ts|
|New API|NA|Class name: EventType;<br>API declaration: START_DOCUMENT<br>Differences: START_DOCUMENT|api/@ohos.xml.d.ts|
|New API|NA|Class name: EventType;<br>API declaration: END_DOCUMENT<br>Differences: END_DOCUMENT|api/@ohos.xml.d.ts|
|New API|NA|Class name: EventType;<br>API declaration: START_TAG<br>Differences: START_TAG|api/@ohos.xml.d.ts|
|New API|NA|Class name: EventType;<br>API declaration: END_TAG<br>Differences: END_TAG|api/@ohos.xml.d.ts|
|New API|NA|Class name: EventType;<br>API declaration: TEXT<br>Differences: TEXT|api/@ohos.xml.d.ts|
|New API|NA|Class name: EventType;<br>API declaration: CDSECT<br>Differences: CDSECT|api/@ohos.xml.d.ts|
|New API|NA|Class name: EventType;<br>API declaration: COMMENT<br>Differences: COMMENT|api/@ohos.xml.d.ts|
|New API|NA|Class name: EventType;<br>API declaration: DOCDECL<br>Differences: DOCDECL|api/@ohos.xml.d.ts|
|New API|NA|Class name: EventType;<br>API declaration: INSTRUCTION<br>Differences: INSTRUCTION|api/@ohos.xml.d.ts|
|New API|NA|Class name: EventType;<br>API declaration: ENTITY_REFERENCE<br>Differences: ENTITY_REFERENCE|api/@ohos.xml.d.ts|
|New API|NA|Class name: EventType;<br>API declaration: WHITESPACE<br>Differences: WHITESPACE|api/@ohos.xml.d.ts|
|New API|NA|Class name: xml;<br>API declaration: interface ParseInfo<br>Differences: interface ParseInfo|api/@ohos.xml.d.ts|
|New API|NA|Class name: ParseInfo;<br>API declaration: getColumnNumber(): number;<br>Differences: getColumnNumber(): number;|api/@ohos.xml.d.ts|
|New API|NA|Class name: ParseInfo;<br>API declaration: getDepth(): number;<br>Differences: getDepth(): number;|api/@ohos.xml.d.ts|
|New API|NA|Class name: ParseInfo;<br>API declaration: getLineNumber(): number;<br>Differences: getLineNumber(): number;|api/@ohos.xml.d.ts|
|New API|NA|Class name: ParseInfo;<br>API declaration: getName(): string;<br>Differences: getName(): string;|api/@ohos.xml.d.ts|
|New API|NA|Class name: ParseInfo;<br>API declaration: getNamespace(): string;<br>Differences: getNamespace(): string;|api/@ohos.xml.d.ts|
|New API|NA|Class name: ParseInfo;<br>API declaration: getPrefix(): string;<br>Differences: getPrefix(): string;|api/@ohos.xml.d.ts|
|New API|NA|Class name: ParseInfo;<br>API declaration: getText(): string;<br>Differences: getText(): string;|api/@ohos.xml.d.ts|
|New API|NA|Class name: ParseInfo;<br>API declaration: isEmptyElementTag(): boolean;<br>Differences: isEmptyElementTag(): boolean;|api/@ohos.xml.d.ts|
|New API|NA|Class name: ParseInfo;<br>API declaration: isWhitespace(): boolean;<br>Differences: isWhitespace(): boolean;|api/@ohos.xml.d.ts|
|New API|NA|Class name: ParseInfo;<br>API declaration: getAttributeCount(): number;<br>Differences: getAttributeCount(): number;|api/@ohos.xml.d.ts|
|New API|NA|Class name: xml;<br>API declaration: interface ParseOptions<br>Differences: interface ParseOptions|api/@ohos.xml.d.ts|
|New API|NA|Class name: ParseOptions;<br>API declaration: supportDoctype?: boolean;<br>Differences: supportDoctype?: boolean;|api/@ohos.xml.d.ts|
|New API|NA|Class name: ParseOptions;<br>API declaration: ignoreNameSpace?: boolean;<br>Differences: ignoreNameSpace?: boolean;|api/@ohos.xml.d.ts|
|New API|NA|Class name: ParseOptions;<br>API declaration: tagValueCallbackFunction?: (name: string, value: string) => boolean;<br>Differences: tagValueCallbackFunction?: (name: string, value: string) => boolean;|api/@ohos.xml.d.ts|
|New API|NA|Class name: ParseOptions;<br>API declaration: attributeValueCallbackFunction?: (name: string, value: string) => boolean;<br>Differences: attributeValueCallbackFunction?: (name: string, value: string) => boolean;|api/@ohos.xml.d.ts|
|New API|NA|Class name: ParseOptions;<br>API declaration: tokenValueCallbackFunction?: (eventType: EventType, value: ParseInfo) => boolean;<br>Differences: tokenValueCallbackFunction?: (eventType: EventType, value: ParseInfo) => boolean;|api/@ohos.xml.d.ts|
|New API|NA|Class name: xml;<br>API declaration: class XmlPullParser<br>Differences: class XmlPullParser|api/@ohos.xml.d.ts|
|New API|NA|Class name: XmlPullParser;<br>API declaration: parse(option: ParseOptions): void;<br>Differences: parse(option: ParseOptions): void;|api/@ohos.xml.d.ts|
|New Kit|Class name: global;<br>API declaration: <br>Differences: NA|Class name: global;<br>API declaration: api\@ohos.buffer.d.ts<br>Differences: ArkTS|api/@ohos.buffer.d.ts|
|New Kit|Class name: global;<br>API declaration: <br>Differences: NA|Class name: global;<br>API declaration: api\@ohos.convertxml.d.ts<br>Differences: ArkTS|api/@ohos.convertxml.d.ts|
|New Kit|Class name: global;<br>API declaration: <br>Differences: NA|Class name: global;<br>API declaration: api\@ohos.process.d.ts<br>Differences: ArkTS|api/@ohos.process.d.ts|
|New Kit|Class name: global;<br>API declaration: <br>Differences: NA|Class name: global;<br>API declaration: api\@ohos.taskpool.d.ts<br>Differences: ArkTS|api/@ohos.taskpool.d.ts|
|New Kit|Class name: global;<br>API declaration: <br>Differences: NA|Class name: global;<br>API declaration: api\@ohos.uri.d.ts<br>Differences: ArkTS|api/@ohos.uri.d.ts|
|New Kit|Class name: global;<br>API declaration: <br>Differences: NA|Class name: global;<br>API declaration: api\@ohos.url.d.ts<br>Differences: ArkTS|api/@ohos.url.d.ts|
|New Kit|Class name: global;<br>API declaration: <br>Differences: NA|Class name: global;<br>API declaration: api\@ohos.util.ArrayList.d.ts<br>Differences: ArkTS|api/@ohos.util.ArrayList.d.ts|
|New Kit|Class name: global;<br>API declaration: <br>Differences: NA|Class name: global;<br>API declaration: api\@ohos.util.d.ts<br>Differences: ArkTS|api/@ohos.util.d.ts|
|New Kit|Class name: global;<br>API declaration: <br>Differences: NA|Class name: global;<br>API declaration: api\@ohos.util.Deque.d.ts<br>Differences: ArkTS|api/@ohos.util.Deque.d.ts|
|New Kit|Class name: global;<br>API declaration: <br>Differences: NA|Class name: global;<br>API declaration: api\@ohos.util.HashMap.d.ts<br>Differences: ArkTS|api/@ohos.util.HashMap.d.ts|
|New Kit|Class name: global;<br>API declaration: <br>Differences: NA|Class name: global;<br>API declaration: api\@ohos.util.HashSet.d.ts<br>Differences: ArkTS|api/@ohos.util.HashSet.d.ts|
|New Kit|Class name: global;<br>API declaration: <br>Differences: NA|Class name: global;<br>API declaration: api\@ohos.util.LightWeightMap.d.ts<br>Differences: ArkTS|api/@ohos.util.LightWeightMap.d.ts|
|New Kit|Class name: global;<br>API declaration: <br>Differences: NA|Class name: global;<br>API declaration: api\@ohos.util.LightWeightSet.d.ts<br>Differences: ArkTS|api/@ohos.util.LightWeightSet.d.ts|
|New Kit|Class name: global;<br>API declaration: <br>Differences: NA|Class name: global;<br>API declaration: api\@ohos.util.LinkedList.d.ts<br>Differences: ArkTS|api/@ohos.util.LinkedList.d.ts|
|New Kit|Class name: global;<br>API declaration: <br>Differences: NA|Class name: global;<br>API declaration: api\@ohos.util.List.d.ts<br>Differences: ArkTS|api/@ohos.util.List.d.ts|
|New Kit|Class name: global;<br>API declaration: <br>Differences: NA|Class name: global;<br>API declaration: api\@ohos.util.PlainArray.d.ts<br>Differences: ArkTS|api/@ohos.util.PlainArray.d.ts|
|New Kit|Class name: global;<br>API declaration: <br>Differences: NA|Class name: global;<br>API declaration: api\@ohos.util.Queue.d.ts<br>Differences: ArkTS|api/@ohos.util.Queue.d.ts|
|New Kit|Class name: global;<br>API declaration: <br>Differences: NA|Class name: global;<br>API declaration: api\@ohos.util.Stack.d.ts<br>Differences: ArkTS|api/@ohos.util.Stack.d.ts|
|New Kit|Class name: global;<br>API declaration: <br>Differences: NA|Class name: global;<br>API declaration: api\@ohos.util.TreeMap.d.ts<br>Differences: ArkTS|api/@ohos.util.TreeMap.d.ts|
|New Kit|Class name: global;<br>API declaration: <br>Differences: NA|Class name: global;<br>API declaration: api\@ohos.util.TreeSet.d.ts<br>Differences: ArkTS|api/@ohos.util.TreeSet.d.ts|
|New Kit|Class name: global;<br>API declaration: <br>Differences: NA|Class name: global;<br>API declaration: api\@ohos.util.Vector.d.ts<br>Differences: ArkTS|api/@ohos.util.Vector.d.ts|
|New Kit|Class name: global;<br>API declaration: <br>Differences: NA|Class name: global;<br>API declaration: api\@ohos.worker.d.ts<br>Differences: ArkTS|api/@ohos.worker.d.ts|
|New Kit|Class name: global;<br>API declaration: <br>Differences: NA|Class name: global;<br>API declaration: api\@ohos.xml.d.ts<br>Differences: ArkTS|api/@ohos.xml.d.ts|
|New Kit|Class name: global;<br>API declaration: <br>Differences: NA|Class name: global;<br>API declaration: kits\@kit.ArkTS.d.ts<br>Differences: ArkTS|kits/@kit.ArkTS.d.ts|

<!--no_check-->