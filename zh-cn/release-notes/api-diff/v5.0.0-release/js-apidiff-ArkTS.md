| 操作 | 旧版本 | 新版本 | d.ts文件 |
| ---- | ------ | ------ | -------- |
|API废弃版本变更|类名：TextDecoder；<br>API声明：decodeWithStream(input: Uint8Array, options?: DecodeWithStreamOptions): string;<br>差异内容：NA|类名：TextDecoder；<br>API声明：decodeWithStream(input: Uint8Array, options?: DecodeWithStreamOptions): string;<br>差异内容：12|api/@ohos.util.d.ts|
|API废弃版本变更|类名：LightWeightSet；<br>API声明：equal(obj: Object): boolean;<br>差异内容：NA|类名：LightWeightSet；<br>API声明：equal(obj: Object): boolean;<br>差异内容：12|api/@ohos.util.LightWeightSet.d.ts|
|新增错误码|类名：Task；<br>API声明：addDependency(...tasks: Task[]): void;<br>差异内容：NA|类名：Task；<br>API声明：addDependency(...tasks: Task[]): void;<br>差异内容：10200052|api/@ohos.taskpool.d.ts|
|新增错误码|类名：Task；<br>API声明：removeDependency(...tasks: Task[]): void;<br>差异内容：NA|类名：Task；<br>API声明：removeDependency(...tasks: Task[]): void;<br>差异内容：10200052|api/@ohos.taskpool.d.ts|
|新增错误码|类名：TaskGroup；<br>API声明：addTask(task: Task): void;<br>差异内容：NA|类名：TaskGroup；<br>API声明：addTask(task: Task): void;<br>差异内容：10200051|api/@ohos.taskpool.d.ts|
|新增错误码|类名：taskpool；<br>API声明：function executeDelayed(delayTime: number, task: Task, priority?: Priority): Promise\<Object>;<br>差异内容：NA|类名：taskpool；<br>API声明：function executeDelayed(delayTime: number, task: Task, priority?: Priority): Promise\<Object>;<br>差异内容：10200006,10200014,10200051|api/@ohos.taskpool.d.ts|
|新增错误码|类名：util；<br>API声明：function parseUUID(uuid: string): Uint8Array;<br>差异内容：NA|类名：util；<br>API声明：function parseUUID(uuid: string): Uint8Array;<br>差异内容：10200002|api/@ohos.util.d.ts|
|删除错误码|类名：taskpool；<br>API声明：function execute(func: Function, ...args: Object[]): Promise\<Object>;<br>差异内容：10200003|类名：taskpool；<br>API声明：function execute(func: Function, ...args: Object[]): Promise\<Object>;<br>差异内容：NA|api/@ohos.taskpool.d.ts|
|错误码变更|类名：SequenceRunner；<br>API声明：execute(task: Task): Promise\<Object>;<br>差异内容：10200003,10200006,10200025,401|类名：SequenceRunner；<br>API声明：execute(task: Task): Promise\<Object>;<br>差异内容：10200006,10200025,10200051,401|api/@ohos.taskpool.d.ts|
|错误码变更|类名：taskpool；<br>API声明：function execute(task: Task, priority?: Priority): Promise\<Object>;<br>差异内容：10200003,10200006,10200014,401|类名：taskpool；<br>API声明：function execute(task: Task, priority?: Priority): Promise\<Object>;<br>差异内容：10200006,10200014,10200051,401|api/@ohos.taskpool.d.ts|
|函数变更|类名：Base64Helper；<br>API声明：encodeSync(src: Uint8Array): Uint8Array;<br>差异内容：NA|类名：Base64Helper；<br>API声明：encodeSync(src: Uint8Array, options?: Type): Uint8Array;<br>差异内容：options?: Type|api/@ohos.util.d.ts|
|函数变更|类名：Base64Helper；<br>API声明：encode(src: Uint8Array): Promise\<Uint8Array>;<br>差异内容：NA|类名：Base64Helper；<br>API声明：encode(src: Uint8Array, options?: Type): Promise\<Uint8Array>;<br>差异内容：options?: Type|api/@ohos.util.d.ts|
|属性变更|类名：MessageEvents；<br>API声明：readonly data;<br>差异内容：NA|类名：MessageEvents；<br>API声明：readonly data: any;<br>差异内容：any|api/@ohos.worker.d.ts|
|新增API|NA|类名：global；<br>API声明：declare namespace json<br>差异内容：declare namespace json|api/@ohos.util.json.d.ts|
|新增API|NA|类名：json；<br>API声明：type Transformer = (this: Object, key: string, value: Object) => Object \| undefined \| null;<br>差异内容：type Transformer = (this: Object, key: string, value: Object) => Object \| undefined \| null;|api/@ohos.util.json.d.ts|
|新增API|NA|类名：json；<br>API声明：function parse(text: string, reviver?: Transformer, options?: ParseOptions): Object \| null;<br>差异内容：function parse(text: string, reviver?: Transformer, options?: ParseOptions): Object \| null;|api/@ohos.util.json.d.ts|
|新增API|NA|类名：json；<br>API声明：function stringify(value: Object, replacer?: (number \| string)[] \| null, space?: string \| number): string;<br>差异内容：function stringify(value: Object, replacer?: (number \| string)[] \| null, space?: string \| number): string;|api/@ohos.util.json.d.ts|
|新增API|NA|类名：json；<br>API声明：function stringify(value: Object, replacer?: Transformer, space?: string \| number): string;<br>差异内容：function stringify(value: Object, replacer?: Transformer, space?: string \| number): string;|api/@ohos.util.json.d.ts|
|新增API|NA|类名：json；<br>API声明：function has(obj: object, property: string): boolean;<br>差异内容：function has(obj: object, property: string): boolean;|api/@ohos.util.json.d.ts|
|新增API|NA|类名：json；<br>API声明：function remove(obj: object, property: string): void;<br>差异内容：function remove(obj: object, property: string): void;|api/@ohos.util.json.d.ts|
|新增API|NA|类名：json；<br>API声明：const enum BigIntMode<br>差异内容：const enum BigIntMode|api/@ohos.util.json.d.ts|
|新增API|NA|类名：BigIntMode；<br>API声明：DEFAULT = 0<br>差异内容：DEFAULT = 0|api/@ohos.util.json.d.ts|
|新增API|NA|类名：BigIntMode；<br>API声明：PARSE_AS_BIGINT = 1<br>差异内容：PARSE_AS_BIGINT = 1|api/@ohos.util.json.d.ts|
|新增API|NA|类名：BigIntMode；<br>API声明：ALWAYS_PARSE_AS_BIGINT = 2<br>差异内容：ALWAYS_PARSE_AS_BIGINT = 2|api/@ohos.util.json.d.ts|
|新增API|NA|类名：json；<br>API声明：interface ParseOptions<br>差异内容：interface ParseOptions|api/@ohos.util.json.d.ts|
|新增API|NA|类名：ParseOptions；<br>API声明：bigIntMode: BigIntMode;<br>差异内容：bigIntMode: BigIntMode;|api/@ohos.util.json.d.ts|
|新增API|NA|类名：global；<br>API声明：declare namespace stream<br>差异内容：declare namespace stream|api/@ohos.util.stream.d.ts|
|新增API|NA|类名：stream；<br>API声明：class Writable<br>差异内容：class Writable|api/@ohos.util.stream.d.ts|
|新增API|NA|类名：Writable；<br>API声明：write(chunk?: string \| Uint8Array, encoding?: string, callback?: Function): boolean;<br>差异内容：write(chunk?: string \| Uint8Array, encoding?: string, callback?: Function): boolean;|api/@ohos.util.stream.d.ts|
|新增API|NA|类名：Writable；<br>API声明：end(chunk?: string \| Uint8Array, encoding?: string, callback?: Function): Writable;<br>差异内容：end(chunk?: string \| Uint8Array, encoding?: string, callback?: Function): Writable;|api/@ohos.util.stream.d.ts|
|新增API|NA|类名：Writable；<br>API声明：setDefaultEncoding(encoding?: string): boolean;<br>差异内容：setDefaultEncoding(encoding?: string): boolean;|api/@ohos.util.stream.d.ts|
|新增API|NA|类名：Writable；<br>API声明：cork(): boolean;<br>差异内容：cork(): boolean;|api/@ohos.util.stream.d.ts|
|新增API|NA|类名：Writable；<br>API声明：uncork(): boolean;<br>差异内容：uncork(): boolean;|api/@ohos.util.stream.d.ts|
|新增API|NA|类名：Writable；<br>API声明：on(event: string, callback: Callback\<emitter.EventData>): void;<br>差异内容：on(event: string, callback: Callback\<emitter.EventData>): void;|api/@ohos.util.stream.d.ts|
|新增API|NA|类名：Writable；<br>API声明：off(event: string, callback?: Callback\<emitter.EventData>): void;<br>差异内容：off(event: string, callback?: Callback\<emitter.EventData>): void;|api/@ohos.util.stream.d.ts|
|新增API|NA|类名：Writable；<br>API声明：doInitialize(callback: Function): void;<br>差异内容：doInitialize(callback: Function): void;|api/@ohos.util.stream.d.ts|
|新增API|NA|类名：Writable；<br>API声明：doWrite(chunk: string \| Uint8Array, encoding: string, callback: Function): void;<br>差异内容：doWrite(chunk: string \| Uint8Array, encoding: string, callback: Function): void;|api/@ohos.util.stream.d.ts|
|新增API|NA|类名：Writable；<br>API声明：doWritev(chunks: string[] \| Uint8Array[], callback: Function): void;<br>差异内容：doWritev(chunks: string[] \| Uint8Array[], callback: Function): void;|api/@ohos.util.stream.d.ts|
|新增API|NA|类名：Writable；<br>API声明：readonly writableObjectMode: boolean;<br>差异内容：readonly writableObjectMode: boolean;|api/@ohos.util.stream.d.ts|
|新增API|NA|类名：Writable；<br>API声明：readonly writableHighWatermark: number;<br>差异内容：readonly writableHighWatermark: number;|api/@ohos.util.stream.d.ts|
|新增API|NA|类名：Writable；<br>API声明：readonly writable: boolean;<br>差异内容：readonly writable: boolean;|api/@ohos.util.stream.d.ts|
|新增API|NA|类名：Writable；<br>API声明：readonly writableLength: number;<br>差异内容：readonly writableLength: number;|api/@ohos.util.stream.d.ts|
|新增API|NA|类名：Writable；<br>API声明：readonly writableCorked: number;<br>差异内容：readonly writableCorked: number;|api/@ohos.util.stream.d.ts|
|新增API|NA|类名：Writable；<br>API声明：readonly writableEnded: boolean;<br>差异内容：readonly writableEnded: boolean;|api/@ohos.util.stream.d.ts|
|新增API|NA|类名：Writable；<br>API声明：readonly writableFinished: boolean;<br>差异内容：readonly writableFinished: boolean;|api/@ohos.util.stream.d.ts|
|新增API|NA|类名：stream；<br>API声明：class Transform<br>差异内容：class Transform|api/@ohos.util.stream.d.ts|
|新增API|NA|类名：Transform；<br>API声明：doTransform(chunk: string, encoding: string, callback: Function): void;<br>差异内容：doTransform(chunk: string, encoding: string, callback: Function): void;|api/@ohos.util.stream.d.ts|
|新增API|NA|类名：Transform；<br>API声明：doFlush(callback: Function): void;<br>差异内容：doFlush(callback: Function): void;|api/@ohos.util.stream.d.ts|
|新增API|NA|类名：stream；<br>API声明：interface ReadableOptions<br>差异内容：interface ReadableOptions|api/@ohos.util.stream.d.ts|
|新增API|NA|类名：ReadableOptions；<br>API声明：encoding?: string;<br>差异内容：encoding?: string;|api/@ohos.util.stream.d.ts|
|新增API|NA|类名：stream；<br>API声明：class Readable<br>差异内容：class Readable|api/@ohos.util.stream.d.ts|
|新增API|NA|类名：Readable；<br>API声明：read(size?: number): string \| null;<br>差异内容：read(size?: number): string \| null;|api/@ohos.util.stream.d.ts|
|新增API|NA|类名：Readable；<br>API声明：resume(): Readable;<br>差异内容：resume(): Readable;|api/@ohos.util.stream.d.ts|
|新增API|NA|类名：Readable；<br>API声明：pause(): Readable;<br>差异内容：pause(): Readable;|api/@ohos.util.stream.d.ts|
|新增API|NA|类名：Readable；<br>API声明：setEncoding(encoding?: string): boolean;<br>差异内容：setEncoding(encoding?: string): boolean;|api/@ohos.util.stream.d.ts|
|新增API|NA|类名：Readable；<br>API声明：isPaused(): boolean;<br>差异内容：isPaused(): boolean;|api/@ohos.util.stream.d.ts|
|新增API|NA|类名：Readable；<br>API声明：pipe(destination: Writable, options?: Object): Writable;<br>差异内容：pipe(destination: Writable, options?: Object): Writable;|api/@ohos.util.stream.d.ts|
|新增API|NA|类名：Readable；<br>API声明：unpipe(destination?: Writable): Readable;<br>差异内容：unpipe(destination?: Writable): Readable;|api/@ohos.util.stream.d.ts|
|新增API|NA|类名：Readable；<br>API声明：on(event: string, callback: Callback\<emitter.EventData>): void;<br>差异内容：on(event: string, callback: Callback\<emitter.EventData>): void;|api/@ohos.util.stream.d.ts|
|新增API|NA|类名：Readable；<br>API声明：off(event: string, callback?: Callback\<emitter.EventData>): void;<br>差异内容：off(event: string, callback?: Callback\<emitter.EventData>): void;|api/@ohos.util.stream.d.ts|
|新增API|NA|类名：Readable；<br>API声明：doInitialize(callback: Function): void;<br>差异内容：doInitialize(callback: Function): void;|api/@ohos.util.stream.d.ts|
|新增API|NA|类名：Readable；<br>API声明：doRead(size: number): void;<br>差异内容：doRead(size: number): void;|api/@ohos.util.stream.d.ts|
|新增API|NA|类名：Readable；<br>API声明：push(chunk: Uint8Array \| string \| null, encoding?: string): boolean;<br>差异内容：push(chunk: Uint8Array \| string \| null, encoding?: string): boolean;|api/@ohos.util.stream.d.ts|
|新增API|NA|类名：Readable；<br>API声明：readonly readableObjectMode: boolean;<br>差异内容：readonly readableObjectMode: boolean;|api/@ohos.util.stream.d.ts|
|新增API|NA|类名：Readable；<br>API声明：readonly readable: boolean;<br>差异内容：readonly readable: boolean;|api/@ohos.util.stream.d.ts|
|新增API|NA|类名：Readable；<br>API声明：readonly readableHighWatermark: number;<br>差异内容：readonly readableHighWatermark: number;|api/@ohos.util.stream.d.ts|
|新增API|NA|类名：Readable；<br>API声明：readonly readableFlowing: boolean \| null;<br>差异内容：readonly readableFlowing: boolean \| null;|api/@ohos.util.stream.d.ts|
|新增API|NA|类名：Readable；<br>API声明：readonly readableLength: number;<br>差异内容：readonly readableLength: number;|api/@ohos.util.stream.d.ts|
|新增API|NA|类名：Readable；<br>API声明：readonly readableEncoding: string \| null;<br>差异内容：readonly readableEncoding: string \| null;|api/@ohos.util.stream.d.ts|
|新增API|NA|类名：Readable；<br>API声明：readonly readableEnded: boolean;<br>差异内容：readonly readableEnded: boolean;|api/@ohos.util.stream.d.ts|
|新增API|NA|类名：stream；<br>API声明：class Duplex<br>差异内容：class Duplex|api/@ohos.util.stream.d.ts|
|新增API|NA|类名：Duplex；<br>API声明：write(chunk?: string \| Uint8Array, encoding?: string, callback?: Function): boolean;<br>差异内容：write(chunk?: string \| Uint8Array, encoding?: string, callback?: Function): boolean;|api/@ohos.util.stream.d.ts|
|新增API|NA|类名：Duplex；<br>API声明：end(chunk?: string \| Uint8Array, encoding?: string, callback?: Function): Writable;<br>差异内容：end(chunk?: string \| Uint8Array, encoding?: string, callback?: Function): Writable;|api/@ohos.util.stream.d.ts|
|新增API|NA|类名：Duplex；<br>API声明：setDefaultEncoding(encoding?: string): boolean;<br>差异内容：setDefaultEncoding(encoding?: string): boolean;|api/@ohos.util.stream.d.ts|
|新增API|NA|类名：Duplex；<br>API声明：cork(): boolean;<br>差异内容：cork(): boolean;|api/@ohos.util.stream.d.ts|
|新增API|NA|类名：Duplex；<br>API声明：uncork(): boolean;<br>差异内容：uncork(): boolean;|api/@ohos.util.stream.d.ts|
|新增API|NA|类名：Duplex；<br>API声明：doWrite(chunk: string \| Uint8Array, encoding: string, callback: Function): void;<br>差异内容：doWrite(chunk: string \| Uint8Array, encoding: string, callback: Function): void;|api/@ohos.util.stream.d.ts|
|新增API|NA|类名：Duplex；<br>API声明：doWritev(chunks: string[] \| Uint8Array[], callback: Function): void;<br>差异内容：doWritev(chunks: string[] \| Uint8Array[], callback: Function): void;|api/@ohos.util.stream.d.ts|
|新增API|NA|类名：Duplex；<br>API声明：readonly writableObjectMode: boolean;<br>差异内容：readonly writableObjectMode: boolean;|api/@ohos.util.stream.d.ts|
|新增API|NA|类名：Duplex；<br>API声明：readonly writableHighWatermark: number;<br>差异内容：readonly writableHighWatermark: number;|api/@ohos.util.stream.d.ts|
|新增API|NA|类名：Duplex；<br>API声明：readonly writable: boolean;<br>差异内容：readonly writable: boolean;|api/@ohos.util.stream.d.ts|
|新增API|NA|类名：Duplex；<br>API声明：readonly writableLength: number;<br>差异内容：readonly writableLength: number;|api/@ohos.util.stream.d.ts|
|新增API|NA|类名：Duplex；<br>API声明：readonly writableCorked: number;<br>差异内容：readonly writableCorked: number;|api/@ohos.util.stream.d.ts|
|新增API|NA|类名：Duplex；<br>API声明：readonly writableEnded: boolean;<br>差异内容：readonly writableEnded: boolean;|api/@ohos.util.stream.d.ts|
|新增API|NA|类名：Duplex；<br>API声明：readonly writableFinished: boolean;<br>差异内容：readonly writableFinished: boolean;|api/@ohos.util.stream.d.ts|
|新增API|NA|类名：global；<br>API声明：declare namespace collections<br>差异内容：declare namespace collections|arkts/@arkts.collections.d.ets|
|新增API|NA|类名：collections；<br>API声明：type TypedArrayFromMapFn\<FromElementType, ToElementType> = (value: FromElementType, index: number) => ToElementType;<br>差异内容：type TypedArrayFromMapFn\<FromElementType, ToElementType> = (value: FromElementType, index: number) => ToElementType;|arkts/@arkts.collections.d.ets|
|新增API|NA|类名：collections；<br>API声明：type TypedArrayPredicateFn\<ElementType, ArrayType> =<br>    (value: ElementType, index: number, array: ArrayType) => boolean;<br>差异内容：type TypedArrayPredicateFn\<ElementType, ArrayType> =<br>    (value: ElementType, index: number, array: ArrayType) => boolean;|arkts/@arkts.collections.d.ets|
|新增API|NA|类名：collections；<br>API声明：type TypedArrayForEachCallback\<ElementType, ArrayType> =<br>    (value: ElementType, index: number, array: ArrayType) => void;<br>差异内容：type TypedArrayForEachCallback\<ElementType, ArrayType> =<br>    (value: ElementType, index: number, array: ArrayType) => void;|arkts/@arkts.collections.d.ets|
|新增API|NA|类名：collections；<br>API声明：type TypedArrayMapCallback\<ElementType, ArrayType> =<br>    (value: ElementType, index: number, array: ArrayType) => ElementType;<br>差异内容：type TypedArrayMapCallback\<ElementType, ArrayType> =<br>    (value: ElementType, index: number, array: ArrayType) => ElementType;|arkts/@arkts.collections.d.ets|
|新增API|NA|类名：collections；<br>API声明：type TypedArrayReduceCallback\<AccType, ElementType, ArrayType> =<br>    (previousValue: AccType, currentValue: ElementType, currentIndex: number, array: ArrayType) => AccType;<br>差异内容：type TypedArrayReduceCallback\<AccType, ElementType, ArrayType> =<br>    (previousValue: AccType, currentValue: ElementType, currentIndex: number, array: ArrayType) => AccType;|arkts/@arkts.collections.d.ets|
|新增API|NA|类名：collections；<br>API声明：type TypedArrayCompareFn\<ElementType> = (first: ElementType, second: ElementType) => number;<br>差异内容：type TypedArrayCompareFn\<ElementType> = (first: ElementType, second: ElementType) => number;|arkts/@arkts.collections.d.ets|
|新增API|NA|类名：collections；<br>API声明：type ISendable = lang.ISendable;<br>差异内容：type ISendable = lang.ISendable;|arkts/@arkts.collections.d.ets|
|新增API|NA|类名：collections；<br>API声明：interface ConcatArray<br>差异内容：interface ConcatArray|arkts/@arkts.collections.d.ets|
|新增API|NA|类名：ConcatArray；<br>API声明：readonly length: number;<br>差异内容：readonly length: number;|arkts/@arkts.collections.d.ets|
|新增API|NA|类名：ConcatArray；<br>API声明：readonly [index: number]: T;<br>差异内容：readonly [index: number]: T;|arkts/@arkts.collections.d.ets|
|新增API|NA|类名：ConcatArray；<br>API声明：join(separator?: string): string;<br>差异内容：join(separator?: string): string;|arkts/@arkts.collections.d.ets|
|新增API|NA|类名：ConcatArray；<br>API声明：slice(start?: number, end?: number): ConcatArray\<T>;<br>差异内容：slice(start?: number, end?: number): ConcatArray\<T>;|arkts/@arkts.collections.d.ets|
|新增API|NA|类名：collections；<br>API声明：class Array<br>差异内容：class Array|arkts/@arkts.collections.d.ets|
|新增API|NA|类名：Array；<br>API声明：readonly length: number;<br>差异内容：readonly length: number;|arkts/@arkts.collections.d.ets|
|新增API|NA|类名：Array；<br>API声明：static create\<T>(arrayLength: number, initialValue: T): Array\<T>;<br>差异内容：static create\<T>(arrayLength: number, initialValue: T): Array\<T>;|arkts/@arkts.collections.d.ets|
|新增API|NA|类名：Array；<br>API声明：static from\<T>(arrayLike: ArrayLike\<T>): Array\<T>;<br>差异内容：static from\<T>(arrayLike: ArrayLike\<T>): Array\<T>;|arkts/@arkts.collections.d.ets|
|新增API|NA|类名：Array；<br>API声明：static from\<T>(iterable: Iterable\<T>): Array\<T>;<br>差异内容：static from\<T>(iterable: Iterable\<T>): Array\<T>;|arkts/@arkts.collections.d.ets|
|新增API|NA|类名：Array；<br>API声明：pop(): T \| undefined;<br>差异内容：pop(): T \| undefined;|arkts/@arkts.collections.d.ets|
|新增API|NA|类名：Array；<br>API声明：push(...items: T[]): number;<br>差异内容：push(...items: T[]): number;|arkts/@arkts.collections.d.ets|
|新增API|NA|类名：Array；<br>API声明：join(separator?: string): string;<br>差异内容：join(separator?: string): string;|arkts/@arkts.collections.d.ets|
|新增API|NA|类名：Array；<br>API声明：shift(): T \| undefined;<br>差异内容：shift(): T \| undefined;|arkts/@arkts.collections.d.ets|
|新增API|NA|类名：Array；<br>API声明：unshift(...items: T[]): number;<br>差异内容：unshift(...items: T[]): number;|arkts/@arkts.collections.d.ets|
|新增API|NA|类名：Array；<br>API声明：slice(start?: number, end?: number): Array\<T>;<br>差异内容：slice(start?: number, end?: number): Array\<T>;|arkts/@arkts.collections.d.ets|
|新增API|NA|类名：Array；<br>API声明：sort(compareFn?: (a: T, b: T) => number): Array\<T>;<br>差异内容：sort(compareFn?: (a: T, b: T) => number): Array\<T>;|arkts/@arkts.collections.d.ets|
|新增API|NA|类名：Array；<br>API声明：indexOf(searchElement: T, fromIndex?: number): number;<br>差异内容：indexOf(searchElement: T, fromIndex?: number): number;|arkts/@arkts.collections.d.ets|
|新增API|NA|类名：Array；<br>API声明：forEach(callbackFn: (value: T, index: number, array: Array\<T>) => void): void;<br>差异内容：forEach(callbackFn: (value: T, index: number, array: Array\<T>) => void): void;|arkts/@arkts.collections.d.ets|
|新增API|NA|类名：Array；<br>API声明：map\<U>(callbackFn: (value: T, index: number, array: Array\<T>) => U): Array\<U>;<br>差异内容：map\<U>(callbackFn: (value: T, index: number, array: Array\<T>) => U): Array\<U>;|arkts/@arkts.collections.d.ets|
|新增API|NA|类名：Array；<br>API声明：filter(predicate: (value: T, index: number, array: Array\<T>) => boolean): Array\<T>;<br>差异内容：filter(predicate: (value: T, index: number, array: Array\<T>) => boolean): Array\<T>;|arkts/@arkts.collections.d.ets|
|新增API|NA|类名：Array；<br>API声明：reduce(callbackFn: (previousValue: T, currentValue: T, currentIndex: number, array: Array\<T>) => T): T;<br>差异内容：reduce(callbackFn: (previousValue: T, currentValue: T, currentIndex: number, array: Array\<T>) => T): T;|arkts/@arkts.collections.d.ets|
|新增API|NA|类名：Array；<br>API声明：reduce\<U>(<br>      callbackFn: (previousValue: U, currentValue: T, currentIndex: number, array: Array\<T>) => U,<br>      initialValue: U<br>    ): U;<br>差异内容：reduce\<U>(<br>      callbackFn: (previousValue: U, currentValue: T, currentIndex: number, array: Array\<T>) => U,<br>      initialValue: U<br>    ): U;|arkts/@arkts.collections.d.ets|
|新增API|NA|类名：Array；<br>API声明：at(index: number): T \| undefined;<br>差异内容：at(index: number): T \| undefined;|arkts/@arkts.collections.d.ets|
|新增API|NA|类名：Array；<br>API声明：[Symbol.iterator](): IterableIterator\<T>;<br>差异内容：[Symbol.iterator](): IterableIterator\<T>;|arkts/@arkts.collections.d.ets|
|新增API|NA|类名：Array；<br>API声明：entries(): IterableIterator\<[number, T]>;<br>差异内容：entries(): IterableIterator\<[number, T]>;|arkts/@arkts.collections.d.ets|
|新增API|NA|类名：Array；<br>API声明：keys(): IterableIterator\<number>;<br>差异内容：keys(): IterableIterator\<number>;|arkts/@arkts.collections.d.ets|
|新增API|NA|类名：Array；<br>API声明：values(): IterableIterator\<T>;<br>差异内容：values(): IterableIterator\<T>;|arkts/@arkts.collections.d.ets|
|新增API|NA|类名：Array；<br>API声明：find(predicate: (value: T, index: number, obj: Array\<T>) => boolean): T \| undefined;<br>差异内容：find(predicate: (value: T, index: number, obj: Array\<T>) => boolean): T \| undefined;|arkts/@arkts.collections.d.ets|
|新增API|NA|类名：Array；<br>API声明：includes(searchElement: T, fromIndex?: number): boolean;<br>差异内容：includes(searchElement: T, fromIndex?: number): boolean;|arkts/@arkts.collections.d.ets|
|新增API|NA|类名：Array；<br>API声明：findIndex(predicate: (value: T, index: number, obj: Array\<T>) => boolean): number;<br>差异内容：findIndex(predicate: (value: T, index: number, obj: Array\<T>) => boolean): number;|arkts/@arkts.collections.d.ets|
|新增API|NA|类名：Array；<br>API声明：fill(value: T, start?: number, end?: number): Array\<T>;<br>差异内容：fill(value: T, start?: number, end?: number): Array\<T>;|arkts/@arkts.collections.d.ets|
|新增API|NA|类名：Array；<br>API声明：shrinkTo(arrayLength: number): void;<br>差异内容：shrinkTo(arrayLength: number): void;|arkts/@arkts.collections.d.ets|
|新增API|NA|类名：Array；<br>API声明：extendTo(arrayLength: number, initialValue: T): void;<br>差异内容：extendTo(arrayLength: number, initialValue: T): void;|arkts/@arkts.collections.d.ets|
|新增API|NA|类名：Array；<br>API声明：[index: number]: T;<br>差异内容：[index: number]: T;|arkts/@arkts.collections.d.ets|
|新增API|NA|类名：Array；<br>API声明：concat(...items: ConcatArray\<T>[]): Array\<T>;<br>差异内容：concat(...items: ConcatArray\<T>[]): Array\<T>;|arkts/@arkts.collections.d.ets|
|新增API|NA|类名：Array；<br>API声明：splice(start: number): Array\<T>;<br>差异内容：splice(start: number): Array\<T>;|arkts/@arkts.collections.d.ets|
|新增API|NA|类名：Array；<br>API声明：splice(start: number, deleteCount: number, ...items: T[]): Array\<T>;<br>差异内容：splice(start: number, deleteCount: number, ...items: T[]): Array\<T>;|arkts/@arkts.collections.d.ets|
|新增API|NA|类名：collections；<br>API声明：class Map<br>差异内容：class Map|arkts/@arkts.collections.d.ets|
|新增API|NA|类名：Map；<br>API声明：readonly size: number;<br>差异内容：readonly size: number;|arkts/@arkts.collections.d.ets|
|新增API|NA|类名：Map；<br>API声明：[Symbol.iterator](): IterableIterator\<[K, V]><br>差异内容：[Symbol.iterator](): IterableIterator\<[K, V]>|arkts/@arkts.collections.d.ets|
|新增API|NA|类名：Map；<br>API声明：entries(): IterableIterator\<[K, V]>;<br>差异内容：entries(): IterableIterator\<[K, V]>;|arkts/@arkts.collections.d.ets|
|新增API|NA|类名：Map；<br>API声明：keys(): IterableIterator\<K>;<br>差异内容：keys(): IterableIterator\<K>;|arkts/@arkts.collections.d.ets|
|新增API|NA|类名：Map；<br>API声明：values(): IterableIterator\<V>;<br>差异内容：values(): IterableIterator\<V>;|arkts/@arkts.collections.d.ets|
|新增API|NA|类名：Map；<br>API声明：clear(): void;<br>差异内容：clear(): void;|arkts/@arkts.collections.d.ets|
|新增API|NA|类名：Map；<br>API声明：delete(key: K): boolean;<br>差异内容：delete(key: K): boolean;|arkts/@arkts.collections.d.ets|
|新增API|NA|类名：Map；<br>API声明：forEach(callbackFn: (value: V, key: K, map: Map\<K, V>) => void): void;<br>差异内容：forEach(callbackFn: (value: V, key: K, map: Map\<K, V>) => void): void;|arkts/@arkts.collections.d.ets|
|新增API|NA|类名：Map；<br>API声明：get(key: K): V \| undefined;<br>差异内容：get(key: K): V \| undefined;|arkts/@arkts.collections.d.ets|
|新增API|NA|类名：Map；<br>API声明：has(key: K): boolean;<br>差异内容：has(key: K): boolean;|arkts/@arkts.collections.d.ets|
|新增API|NA|类名：Map；<br>API声明：set(key: K, value: V): Map\<K, V>;<br>差异内容：set(key: K, value: V): Map\<K, V>;|arkts/@arkts.collections.d.ets|
|新增API|NA|类名：collections；<br>API声明：class Set<br>差异内容：class Set|arkts/@arkts.collections.d.ets|
|新增API|NA|类名：Set；<br>API声明：readonly size: number;<br>差异内容：readonly size: number;|arkts/@arkts.collections.d.ets|
|新增API|NA|类名：Set；<br>API声明：[Symbol.iterator](): IterableIterator\<T>;<br>差异内容：[Symbol.iterator](): IterableIterator\<T>;|arkts/@arkts.collections.d.ets|
|新增API|NA|类名：Set；<br>API声明：entries(): IterableIterator\<[T, T]>;<br>差异内容：entries(): IterableIterator\<[T, T]>;|arkts/@arkts.collections.d.ets|
|新增API|NA|类名：Set；<br>API声明：keys(): IterableIterator\<T>;<br>差异内容：keys(): IterableIterator\<T>;|arkts/@arkts.collections.d.ets|
|新增API|NA|类名：Set；<br>API声明：values(): IterableIterator\<T>;<br>差异内容：values(): IterableIterator\<T>;|arkts/@arkts.collections.d.ets|
|新增API|NA|类名：Set；<br>API声明：add(value: T): Set\<T>;<br>差异内容：add(value: T): Set\<T>;|arkts/@arkts.collections.d.ets|
|新增API|NA|类名：Set；<br>API声明：clear(): void;<br>差异内容：clear(): void;|arkts/@arkts.collections.d.ets|
|新增API|NA|类名：Set；<br>API声明：delete(value: T): boolean;<br>差异内容：delete(value: T): boolean;|arkts/@arkts.collections.d.ets|
|新增API|NA|类名：Set；<br>API声明：forEach(callbackFn: (value: T, value2: T, set: Set\<T>) => void): void;<br>差异内容：forEach(callbackFn: (value: T, value2: T, set: Set\<T>) => void): void;|arkts/@arkts.collections.d.ets|
|新增API|NA|类名：Set；<br>API声明：has(value: T): boolean;<br>差异内容：has(value: T): boolean;|arkts/@arkts.collections.d.ets|
|新增API|NA|类名：collections；<br>API声明：class ArrayBuffer<br>差异内容：class ArrayBuffer|arkts/@arkts.collections.d.ets|
|新增API|NA|类名：ArrayBuffer；<br>API声明：readonly byteLength: number;<br>差异内容：readonly byteLength: number;|arkts/@arkts.collections.d.ets|
|新增API|NA|类名：ArrayBuffer；<br>API声明：slice(begin: number, end?: number): ArrayBuffer;<br>差异内容：slice(begin: number, end?: number): ArrayBuffer;|arkts/@arkts.collections.d.ets|
|新增API|NA|类名：collections；<br>API声明：class Int8Array<br>差异内容：class Int8Array|arkts/@arkts.collections.d.ets|
|新增API|NA|类名：Int8Array；<br>API声明：static readonly BYTES_PER_ELEMENT: number;<br>差异内容：static readonly BYTES_PER_ELEMENT: number;|arkts/@arkts.collections.d.ets|
|新增API|NA|类名：Int8Array；<br>API声明：readonly buffer: ArrayBuffer;<br>差异内容：readonly buffer: ArrayBuffer;|arkts/@arkts.collections.d.ets|
|新增API|NA|类名：Int8Array；<br>API声明：readonly byteLength: number;<br>差异内容：readonly byteLength: number;|arkts/@arkts.collections.d.ets|
|新增API|NA|类名：Int8Array；<br>API声明：readonly byteOffset: number;<br>差异内容：readonly byteOffset: number;|arkts/@arkts.collections.d.ets|
|新增API|NA|类名：Int8Array；<br>API声明：readonly length: number;<br>差异内容：readonly length: number;|arkts/@arkts.collections.d.ets|
|新增API|NA|类名：Int8Array；<br>API声明：static from(arrayLike: ArrayLike\<number>): Int8Array;<br>差异内容：static from(arrayLike: ArrayLike\<number>): Int8Array;|arkts/@arkts.collections.d.ets|
|新增API|NA|类名：Int8Array；<br>API声明：static from\<T>(arrayLike: ArrayLike\<T>, mapFn: TypedArrayFromMapFn\<T, number>): Int8Array;<br>差异内容：static from\<T>(arrayLike: ArrayLike\<T>, mapFn: TypedArrayFromMapFn\<T, number>): Int8Array;|arkts/@arkts.collections.d.ets|
|新增API|NA|类名：Int8Array；<br>API声明：static from(arrayLike: Iterable\<number>, mapFn?: TypedArrayFromMapFn\<number, number>): Int8Array;<br>差异内容：static from(arrayLike: Iterable\<number>, mapFn?: TypedArrayFromMapFn\<number, number>): Int8Array;|arkts/@arkts.collections.d.ets|
|新增API|NA|类名：Int8Array；<br>API声明：copyWithin(target: number, start: number, end?: number): Int8Array;<br>差异内容：copyWithin(target: number, start: number, end?: number): Int8Array;|arkts/@arkts.collections.d.ets|
|新增API|NA|类名：Int8Array；<br>API声明：every(predicate: TypedArrayPredicateFn\<number, Int8Array>): boolean;<br>差异内容：every(predicate: TypedArrayPredicateFn\<number, Int8Array>): boolean;|arkts/@arkts.collections.d.ets|
|新增API|NA|类名：Int8Array；<br>API声明：fill(value: number, start?: number, end?: number): Int8Array;<br>差异内容：fill(value: number, start?: number, end?: number): Int8Array;|arkts/@arkts.collections.d.ets|
|新增API|NA|类名：Int8Array；<br>API声明：filter(predicate: TypedArrayPredicateFn\<number, Int8Array>): Int8Array;<br>差异内容：filter(predicate: TypedArrayPredicateFn\<number, Int8Array>): Int8Array;|arkts/@arkts.collections.d.ets|
|新增API|NA|类名：Int8Array；<br>API声明：find(predicate: TypedArrayPredicateFn\<number, Int8Array>): number \| undefined;<br>差异内容：find(predicate: TypedArrayPredicateFn\<number, Int8Array>): number \| undefined;|arkts/@arkts.collections.d.ets|
|新增API|NA|类名：Int8Array；<br>API声明：findIndex(predicate: TypedArrayPredicateFn\<number, Int8Array>): number;<br>差异内容：findIndex(predicate: TypedArrayPredicateFn\<number, Int8Array>): number;|arkts/@arkts.collections.d.ets|
|新增API|NA|类名：Int8Array；<br>API声明：forEach(callbackFn: TypedArrayForEachCallback\<number, Int8Array>): void;<br>差异内容：forEach(callbackFn: TypedArrayForEachCallback\<number, Int8Array>): void;|arkts/@arkts.collections.d.ets|
|新增API|NA|类名：Int8Array；<br>API声明：indexOf(searchElement: number, fromIndex?: number): number;<br>差异内容：indexOf(searchElement: number, fromIndex?: number): number;|arkts/@arkts.collections.d.ets|
|新增API|NA|类名：Int8Array；<br>API声明：join(separator?: string): string;<br>差异内容：join(separator?: string): string;|arkts/@arkts.collections.d.ets|
|新增API|NA|类名：Int8Array；<br>API声明：map(callbackFn: TypedArrayMapCallback\<number, Int8Array>): Int8Array;<br>差异内容：map(callbackFn: TypedArrayMapCallback\<number, Int8Array>): Int8Array;|arkts/@arkts.collections.d.ets|
|新增API|NA|类名：Int8Array；<br>API声明：reduce(callbackFn: TypedArrayReduceCallback\<number, number, Int8Array>): number;<br>差异内容：reduce(callbackFn: TypedArrayReduceCallback\<number, number, Int8Array>): number;|arkts/@arkts.collections.d.ets|
|新增API|NA|类名：Int8Array；<br>API声明：reduce(callbackFn: TypedArrayReduceCallback\<number, number, Int8Array>, initialValue: number): number;<br>差异内容：reduce(callbackFn: TypedArrayReduceCallback\<number, number, Int8Array>, initialValue: number): number;|arkts/@arkts.collections.d.ets|
|新增API|NA|类名：Int8Array；<br>API声明：reduce\<U>(callbackFn: TypedArrayReduceCallback\<U, number, Int8Array>, initialValue: U): U;<br>差异内容：reduce\<U>(callbackFn: TypedArrayReduceCallback\<U, number, Int8Array>, initialValue: U): U;|arkts/@arkts.collections.d.ets|
|新增API|NA|类名：Int8Array；<br>API声明：reverse(): Int8Array;<br>差异内容：reverse(): Int8Array;|arkts/@arkts.collections.d.ets|
|新增API|NA|类名：Int8Array；<br>API声明：set(array: ArrayLike\<number>, offset?: number): void;<br>差异内容：set(array: ArrayLike\<number>, offset?: number): void;|arkts/@arkts.collections.d.ets|
|新增API|NA|类名：Int8Array；<br>API声明：slice(start?: number, end?: number): Int8Array;<br>差异内容：slice(start?: number, end?: number): Int8Array;|arkts/@arkts.collections.d.ets|
|新增API|NA|类名：Int8Array；<br>API声明：some(predicate: TypedArrayPredicateFn\<number, Int8Array>): boolean;<br>差异内容：some(predicate: TypedArrayPredicateFn\<number, Int8Array>): boolean;|arkts/@arkts.collections.d.ets|
|新增API|NA|类名：Int8Array；<br>API声明：sort(compareFn?: TypedArrayCompareFn\<number>): Int8Array;<br>差异内容：sort(compareFn?: TypedArrayCompareFn\<number>): Int8Array;|arkts/@arkts.collections.d.ets|
|新增API|NA|类名：Int8Array；<br>API声明：subarray(begin?: number, end?: number): Int8Array;<br>差异内容：subarray(begin?: number, end?: number): Int8Array;|arkts/@arkts.collections.d.ets|
|新增API|NA|类名：Int8Array；<br>API声明：at(index: number): number \| undefined;<br>差异内容：at(index: number): number \| undefined;|arkts/@arkts.collections.d.ets|
|新增API|NA|类名：Int8Array；<br>API声明：[Symbol.iterator](): IterableIterator\<number>;<br>差异内容：[Symbol.iterator](): IterableIterator\<number>;|arkts/@arkts.collections.d.ets|
|新增API|NA|类名：Int8Array；<br>API声明：entries(): IterableIterator\<[number, number]>;<br>差异内容：entries(): IterableIterator\<[number, number]>;|arkts/@arkts.collections.d.ets|
|新增API|NA|类名：Int8Array；<br>API声明：keys(): IterableIterator\<number>;<br>差异内容：keys(): IterableIterator\<number>;|arkts/@arkts.collections.d.ets|
|新增API|NA|类名：Int8Array；<br>API声明：values(): IterableIterator\<number>;<br>差异内容：values(): IterableIterator\<number>;|arkts/@arkts.collections.d.ets|
|新增API|NA|类名：Int8Array；<br>API声明：includes(searchElement: number, fromIndex?: number): boolean;<br>差异内容：includes(searchElement: number, fromIndex?: number): boolean;|arkts/@arkts.collections.d.ets|
|新增API|NA|类名：Int8Array；<br>API声明：[index: number]: number;<br>差异内容：[index: number]: number;|arkts/@arkts.collections.d.ets|
|新增API|NA|类名：collections；<br>API声明：class Uint8ClampedArray<br>差异内容：class Uint8ClampedArray|arkts/@arkts.collections.d.ets|
|新增API|NA|类名：Uint8ClampedArray；<br>API声明：static readonly BYTES_PER_ELEMENT: number;<br>差异内容：static readonly BYTES_PER_ELEMENT: number;|arkts/@arkts.collections.d.ets|
|新增API|NA|类名：Uint8ClampedArray；<br>API声明：readonly buffer: ArrayBuffer;<br>差异内容：readonly buffer: ArrayBuffer;|arkts/@arkts.collections.d.ets|
|新增API|NA|类名：Uint8ClampedArray；<br>API声明：readonly byteLength: number;<br>差异内容：readonly byteLength: number;|arkts/@arkts.collections.d.ets|
|新增API|NA|类名：Uint8ClampedArray；<br>API声明：readonly byteOffset: number;<br>差异内容：readonly byteOffset: number;|arkts/@arkts.collections.d.ets|
|新增API|NA|类名：Uint8ClampedArray；<br>API声明：readonly length: number;<br>差异内容：readonly length: number;|arkts/@arkts.collections.d.ets|
|新增API|NA|类名：Uint8ClampedArray；<br>API声明：static from(arrayLike: ArrayLike\<number>): Uint8ClampedArray;<br>差异内容：static from(arrayLike: ArrayLike\<number>): Uint8ClampedArray;|arkts/@arkts.collections.d.ets|
|新增API|NA|类名：Uint8ClampedArray；<br>API声明：static from\<T>(arrayLike: ArrayLike\<T>, mapFn: TypedArrayFromMapFn\<T, number>): Uint8ClampedArray;<br>差异内容：static from\<T>(arrayLike: ArrayLike\<T>, mapFn: TypedArrayFromMapFn\<T, number>): Uint8ClampedArray;|arkts/@arkts.collections.d.ets|
|新增API|NA|类名：Uint8ClampedArray；<br>API声明：static from(arrayLike: Iterable\<number>, mapFn?: TypedArrayFromMapFn\<number, number>): Uint8ClampedArray;<br>差异内容：static from(arrayLike: Iterable\<number>, mapFn?: TypedArrayFromMapFn\<number, number>): Uint8ClampedArray;|arkts/@arkts.collections.d.ets|
|新增API|NA|类名：Uint8ClampedArray；<br>API声明：copyWithin(target: number, start: number, end?: number): Uint8ClampedArray;<br>差异内容：copyWithin(target: number, start: number, end?: number): Uint8ClampedArray;|arkts/@arkts.collections.d.ets|
|新增API|NA|类名：Uint8ClampedArray；<br>API声明：every(predicate: TypedArrayPredicateFn\<number, Uint8ClampedArray>): boolean;<br>差异内容：every(predicate: TypedArrayPredicateFn\<number, Uint8ClampedArray>): boolean;|arkts/@arkts.collections.d.ets|
|新增API|NA|类名：Uint8ClampedArray；<br>API声明：fill(value: number, start?: number, end?: number): Uint8ClampedArray;<br>差异内容：fill(value: number, start?: number, end?: number): Uint8ClampedArray;|arkts/@arkts.collections.d.ets|
|新增API|NA|类名：Uint8ClampedArray；<br>API声明：filter(predicate: TypedArrayPredicateFn\<number, Uint8ClampedArray>): Uint8ClampedArray;<br>差异内容：filter(predicate: TypedArrayPredicateFn\<number, Uint8ClampedArray>): Uint8ClampedArray;|arkts/@arkts.collections.d.ets|
|新增API|NA|类名：Uint8ClampedArray；<br>API声明：find(predicate: TypedArrayPredicateFn\<number, Uint8ClampedArray>): number \| undefined;<br>差异内容：find(predicate: TypedArrayPredicateFn\<number, Uint8ClampedArray>): number \| undefined;|arkts/@arkts.collections.d.ets|
|新增API|NA|类名：Uint8ClampedArray；<br>API声明：findIndex(predicate: TypedArrayPredicateFn\<number, Uint8ClampedArray>): number;<br>差异内容：findIndex(predicate: TypedArrayPredicateFn\<number, Uint8ClampedArray>): number;|arkts/@arkts.collections.d.ets|
|新增API|NA|类名：Uint8ClampedArray；<br>API声明：forEach(callbackFn: TypedArrayForEachCallback\<number, Uint8ClampedArray>): void;<br>差异内容：forEach(callbackFn: TypedArrayForEachCallback\<number, Uint8ClampedArray>): void;|arkts/@arkts.collections.d.ets|
|新增API|NA|类名：Uint8ClampedArray；<br>API声明：indexOf(searchElement: number, fromIndex?: number): number;<br>差异内容：indexOf(searchElement: number, fromIndex?: number): number;|arkts/@arkts.collections.d.ets|
|新增API|NA|类名：Uint8ClampedArray；<br>API声明：join(separator?: string): string;<br>差异内容：join(separator?: string): string;|arkts/@arkts.collections.d.ets|
|新增API|NA|类名：Uint8ClampedArray；<br>API声明：map(callbackFn: TypedArrayMapCallback\<number, Uint8ClampedArray>): Uint8ClampedArray;<br>差异内容：map(callbackFn: TypedArrayMapCallback\<number, Uint8ClampedArray>): Uint8ClampedArray;|arkts/@arkts.collections.d.ets|
|新增API|NA|类名：Uint8ClampedArray；<br>API声明：reduce(callbackFn: TypedArrayReduceCallback\<number, number, Uint8ClampedArray>): number;<br>差异内容：reduce(callbackFn: TypedArrayReduceCallback\<number, number, Uint8ClampedArray>): number;|arkts/@arkts.collections.d.ets|
|新增API|NA|类名：Uint8ClampedArray；<br>API声明：reduce\<U = number>(callbackFn: TypedArrayReduceCallback\<U, number, Uint8ClampedArray>, initialValue: U): U;<br>差异内容：reduce\<U = number>(callbackFn: TypedArrayReduceCallback\<U, number, Uint8ClampedArray>, initialValue: U): U;|arkts/@arkts.collections.d.ets|
|新增API|NA|类名：Uint8ClampedArray；<br>API声明：reverse(): Uint8ClampedArray;<br>差异内容：reverse(): Uint8ClampedArray;|arkts/@arkts.collections.d.ets|
|新增API|NA|类名：Uint8ClampedArray；<br>API声明：set(array: ArrayLike\<number>, offset?: number): void;<br>差异内容：set(array: ArrayLike\<number>, offset?: number): void;|arkts/@arkts.collections.d.ets|
|新增API|NA|类名：Uint8ClampedArray；<br>API声明：slice(start?: number, end?: number): Uint8ClampedArray;<br>差异内容：slice(start?: number, end?: number): Uint8ClampedArray;|arkts/@arkts.collections.d.ets|
|新增API|NA|类名：Uint8ClampedArray；<br>API声明：some(predicate: TypedArrayPredicateFn\<number, Uint8ClampedArray>): boolean;<br>差异内容：some(predicate: TypedArrayPredicateFn\<number, Uint8ClampedArray>): boolean;|arkts/@arkts.collections.d.ets|
|新增API|NA|类名：Uint8ClampedArray；<br>API声明：sort(compareFn?: TypedArrayCompareFn\<number>): Uint8ClampedArray;<br>差异内容：sort(compareFn?: TypedArrayCompareFn\<number>): Uint8ClampedArray;|arkts/@arkts.collections.d.ets|
|新增API|NA|类名：Uint8ClampedArray；<br>API声明：subarray(begin?: number, end?: number): Uint8ClampedArray;<br>差异内容：subarray(begin?: number, end?: number): Uint8ClampedArray;|arkts/@arkts.collections.d.ets|
|新增API|NA|类名：Uint8ClampedArray；<br>API声明：at(index: number): number \| undefined;<br>差异内容：at(index: number): number \| undefined;|arkts/@arkts.collections.d.ets|
|新增API|NA|类名：Uint8ClampedArray；<br>API声明：[Symbol.iterator](): IterableIterator\<number>;<br>差异内容：[Symbol.iterator](): IterableIterator\<number>;|arkts/@arkts.collections.d.ets|
|新增API|NA|类名：Uint8ClampedArray；<br>API声明：entries(): IterableIterator\<[number, number]>;<br>差异内容：entries(): IterableIterator\<[number, number]>;|arkts/@arkts.collections.d.ets|
|新增API|NA|类名：Uint8ClampedArray；<br>API声明：keys(): IterableIterator\<number>;<br>差异内容：keys(): IterableIterator\<number>;|arkts/@arkts.collections.d.ets|
|新增API|NA|类名：Uint8ClampedArray；<br>API声明：values(): IterableIterator\<number>;<br>差异内容：values(): IterableIterator\<number>;|arkts/@arkts.collections.d.ets|
|新增API|NA|类名：Uint8ClampedArray；<br>API声明：includes(searchElement: number, fromIndex?: number): boolean;<br>差异内容：includes(searchElement: number, fromIndex?: number): boolean;|arkts/@arkts.collections.d.ets|
|新增API|NA|类名：Uint8ClampedArray；<br>API声明：[index: number]: number;<br>差异内容：[index: number]: number;|arkts/@arkts.collections.d.ets|
|新增API|NA|类名：collections；<br>API声明：class Uint8Array<br>差异内容：class Uint8Array|arkts/@arkts.collections.d.ets|
|新增API|NA|类名：Uint8Array；<br>API声明：static readonly BYTES_PER_ELEMENT: number;<br>差异内容：static readonly BYTES_PER_ELEMENT: number;|arkts/@arkts.collections.d.ets|
|新增API|NA|类名：Uint8Array；<br>API声明：readonly buffer: ArrayBuffer;<br>差异内容：readonly buffer: ArrayBuffer;|arkts/@arkts.collections.d.ets|
|新增API|NA|类名：Uint8Array；<br>API声明：readonly byteLength: number;<br>差异内容：readonly byteLength: number;|arkts/@arkts.collections.d.ets|
|新增API|NA|类名：Uint8Array；<br>API声明：readonly byteOffset: number;<br>差异内容：readonly byteOffset: number;|arkts/@arkts.collections.d.ets|
|新增API|NA|类名：Uint8Array；<br>API声明：readonly length: number;<br>差异内容：readonly length: number;|arkts/@arkts.collections.d.ets|
|新增API|NA|类名：Uint8Array；<br>API声明：static from(arrayLike: ArrayLike\<number>): Uint8Array;<br>差异内容：static from(arrayLike: ArrayLike\<number>): Uint8Array;|arkts/@arkts.collections.d.ets|
|新增API|NA|类名：Uint8Array；<br>API声明：static from\<T>(arrayLike: ArrayLike\<T>, mapFn: TypedArrayFromMapFn\<T, number>): Uint8Array;<br>差异内容：static from\<T>(arrayLike: ArrayLike\<T>, mapFn: TypedArrayFromMapFn\<T, number>): Uint8Array;|arkts/@arkts.collections.d.ets|
|新增API|NA|类名：Uint8Array；<br>API声明：static from(arrayLike: Iterable\<number>, mapFn?: TypedArrayFromMapFn\<number, number>): Uint8Array;<br>差异内容：static from(arrayLike: Iterable\<number>, mapFn?: TypedArrayFromMapFn\<number, number>): Uint8Array;|arkts/@arkts.collections.d.ets|
|新增API|NA|类名：Uint8Array；<br>API声明：copyWithin(target: number, start: number, end?: number): Uint8Array;<br>差异内容：copyWithin(target: number, start: number, end?: number): Uint8Array;|arkts/@arkts.collections.d.ets|
|新增API|NA|类名：Uint8Array；<br>API声明：every(predicate: TypedArrayPredicateFn\<number, Uint8Array>): boolean;<br>差异内容：every(predicate: TypedArrayPredicateFn\<number, Uint8Array>): boolean;|arkts/@arkts.collections.d.ets|
|新增API|NA|类名：Uint8Array；<br>API声明：fill(value: number, start?: number, end?: number): Uint8Array;<br>差异内容：fill(value: number, start?: number, end?: number): Uint8Array;|arkts/@arkts.collections.d.ets|
|新增API|NA|类名：Uint8Array；<br>API声明：filter(predicate: TypedArrayPredicateFn\<number, Uint8Array>): Uint8Array;<br>差异内容：filter(predicate: TypedArrayPredicateFn\<number, Uint8Array>): Uint8Array;|arkts/@arkts.collections.d.ets|
|新增API|NA|类名：Uint8Array；<br>API声明：find(predicate: TypedArrayPredicateFn\<number, Uint8Array>): number \| undefined;<br>差异内容：find(predicate: TypedArrayPredicateFn\<number, Uint8Array>): number \| undefined;|arkts/@arkts.collections.d.ets|
|新增API|NA|类名：Uint8Array；<br>API声明：findIndex(predicate: TypedArrayPredicateFn\<number, Uint8Array>): number;<br>差异内容：findIndex(predicate: TypedArrayPredicateFn\<number, Uint8Array>): number;|arkts/@arkts.collections.d.ets|
|新增API|NA|类名：Uint8Array；<br>API声明：forEach(callbackFn: TypedArrayForEachCallback\<number, Uint8Array>): void;<br>差异内容：forEach(callbackFn: TypedArrayForEachCallback\<number, Uint8Array>): void;|arkts/@arkts.collections.d.ets|
|新增API|NA|类名：Uint8Array；<br>API声明：indexOf(searchElement: number, fromIndex?: number): number;<br>差异内容：indexOf(searchElement: number, fromIndex?: number): number;|arkts/@arkts.collections.d.ets|
|新增API|NA|类名：Uint8Array；<br>API声明：join(separator?: string): string;<br>差异内容：join(separator?: string): string;|arkts/@arkts.collections.d.ets|
|新增API|NA|类名：Uint8Array；<br>API声明：map(callbackFn: TypedArrayMapCallback\<number, Uint8Array>): Uint8Array;<br>差异内容：map(callbackFn: TypedArrayMapCallback\<number, Uint8Array>): Uint8Array;|arkts/@arkts.collections.d.ets|
|新增API|NA|类名：Uint8Array；<br>API声明：reduce(callbackFn: TypedArrayReduceCallback\<number, number, Uint8Array>): number;<br>差异内容：reduce(callbackFn: TypedArrayReduceCallback\<number, number, Uint8Array>): number;|arkts/@arkts.collections.d.ets|
|新增API|NA|类名：Uint8Array；<br>API声明：reduce(callbackFn: TypedArrayReduceCallback\<number, number, Uint8Array>, initialValue: number): number;<br>差异内容：reduce(callbackFn: TypedArrayReduceCallback\<number, number, Uint8Array>, initialValue: number): number;|arkts/@arkts.collections.d.ets|
|新增API|NA|类名：Uint8Array；<br>API声明：reduce\<U>(callbackFn: TypedArrayReduceCallback\<U, number, Uint8Array>, initialValue: U): U;<br>差异内容：reduce\<U>(callbackFn: TypedArrayReduceCallback\<U, number, Uint8Array>, initialValue: U): U;|arkts/@arkts.collections.d.ets|
|新增API|NA|类名：Uint8Array；<br>API声明：reverse(): Uint8Array;<br>差异内容：reverse(): Uint8Array;|arkts/@arkts.collections.d.ets|
|新增API|NA|类名：Uint8Array；<br>API声明：set(array: ArrayLike\<number>, offset?: number): void;<br>差异内容：set(array: ArrayLike\<number>, offset?: number): void;|arkts/@arkts.collections.d.ets|
|新增API|NA|类名：Uint8Array；<br>API声明：slice(start?: number, end?: number): Uint8Array;<br>差异内容：slice(start?: number, end?: number): Uint8Array;|arkts/@arkts.collections.d.ets|
|新增API|NA|类名：Uint8Array；<br>API声明：some(predicate: TypedArrayPredicateFn\<number, Uint8Array>): boolean;<br>差异内容：some(predicate: TypedArrayPredicateFn\<number, Uint8Array>): boolean;|arkts/@arkts.collections.d.ets|
|新增API|NA|类名：Uint8Array；<br>API声明：sort(compareFn?: TypedArrayCompareFn\<number>): Uint8Array;<br>差异内容：sort(compareFn?: TypedArrayCompareFn\<number>): Uint8Array;|arkts/@arkts.collections.d.ets|
|新增API|NA|类名：Uint8Array；<br>API声明：subarray(begin?: number, end?: number): Uint8Array;<br>差异内容：subarray(begin?: number, end?: number): Uint8Array;|arkts/@arkts.collections.d.ets|
|新增API|NA|类名：Uint8Array；<br>API声明：at(index: number): number \| undefined;<br>差异内容：at(index: number): number \| undefined;|arkts/@arkts.collections.d.ets|
|新增API|NA|类名：Uint8Array；<br>API声明：[Symbol.iterator](): IterableIterator\<number>;<br>差异内容：[Symbol.iterator](): IterableIterator\<number>;|arkts/@arkts.collections.d.ets|
|新增API|NA|类名：Uint8Array；<br>API声明：entries(): IterableIterator\<[number, number]>;<br>差异内容：entries(): IterableIterator\<[number, number]>;|arkts/@arkts.collections.d.ets|
|新增API|NA|类名：Uint8Array；<br>API声明：keys(): IterableIterator\<number>;<br>差异内容：keys(): IterableIterator\<number>;|arkts/@arkts.collections.d.ets|
|新增API|NA|类名：Uint8Array；<br>API声明：values(): IterableIterator\<number>;<br>差异内容：values(): IterableIterator\<number>;|arkts/@arkts.collections.d.ets|
|新增API|NA|类名：Uint8Array；<br>API声明：includes(searchElement: number, fromIndex?: number): boolean;<br>差异内容：includes(searchElement: number, fromIndex?: number): boolean;|arkts/@arkts.collections.d.ets|
|新增API|NA|类名：Uint8Array；<br>API声明：[index: number]: number;<br>差异内容：[index: number]: number;|arkts/@arkts.collections.d.ets|
|新增API|NA|类名：collections；<br>API声明：class Int16Array<br>差异内容：class Int16Array|arkts/@arkts.collections.d.ets|
|新增API|NA|类名：Int16Array；<br>API声明：static readonly BYTES_PER_ELEMENT: number;<br>差异内容：static readonly BYTES_PER_ELEMENT: number;|arkts/@arkts.collections.d.ets|
|新增API|NA|类名：Int16Array；<br>API声明：readonly buffer: ArrayBuffer;<br>差异内容：readonly buffer: ArrayBuffer;|arkts/@arkts.collections.d.ets|
|新增API|NA|类名：Int16Array；<br>API声明：readonly byteLength: number;<br>差异内容：readonly byteLength: number;|arkts/@arkts.collections.d.ets|
|新增API|NA|类名：Int16Array；<br>API声明：readonly byteOffset: number;<br>差异内容：readonly byteOffset: number;|arkts/@arkts.collections.d.ets|
|新增API|NA|类名：Int16Array；<br>API声明：readonly length: number;<br>差异内容：readonly length: number;|arkts/@arkts.collections.d.ets|
|新增API|NA|类名：Int16Array；<br>API声明：static from(arrayLike: ArrayLike\<number>): Int16Array;<br>差异内容：static from(arrayLike: ArrayLike\<number>): Int16Array;|arkts/@arkts.collections.d.ets|
|新增API|NA|类名：Int16Array；<br>API声明：static from\<T>(arrayLike: ArrayLike\<T>, mapFn: TypedArrayFromMapFn\<T, number>): Int16Array;<br>差异内容：static from\<T>(arrayLike: ArrayLike\<T>, mapFn: TypedArrayFromMapFn\<T, number>): Int16Array;|arkts/@arkts.collections.d.ets|
|新增API|NA|类名：Int16Array；<br>API声明：static from(arrayLike: Iterable\<number>, mapFn?: TypedArrayFromMapFn\<number, number>): Int16Array;<br>差异内容：static from(arrayLike: Iterable\<number>, mapFn?: TypedArrayFromMapFn\<number, number>): Int16Array;|arkts/@arkts.collections.d.ets|
|新增API|NA|类名：Int16Array；<br>API声明：copyWithin(target: number, start: number, end?: number): Int16Array;<br>差异内容：copyWithin(target: number, start: number, end?: number): Int16Array;|arkts/@arkts.collections.d.ets|
|新增API|NA|类名：Int16Array；<br>API声明：every(predicate: TypedArrayPredicateFn\<number, Int16Array>): boolean;<br>差异内容：every(predicate: TypedArrayPredicateFn\<number, Int16Array>): boolean;|arkts/@arkts.collections.d.ets|
|新增API|NA|类名：Int16Array；<br>API声明：fill(value: number, start?: number, end?: number): Int16Array;<br>差异内容：fill(value: number, start?: number, end?: number): Int16Array;|arkts/@arkts.collections.d.ets|
|新增API|NA|类名：Int16Array；<br>API声明：filter(predicate: TypedArrayPredicateFn\<number, Int16Array>): Int16Array;<br>差异内容：filter(predicate: TypedArrayPredicateFn\<number, Int16Array>): Int16Array;|arkts/@arkts.collections.d.ets|
|新增API|NA|类名：Int16Array；<br>API声明：find(predicate: TypedArrayPredicateFn\<number, Int16Array>): number \| undefined;<br>差异内容：find(predicate: TypedArrayPredicateFn\<number, Int16Array>): number \| undefined;|arkts/@arkts.collections.d.ets|
|新增API|NA|类名：Int16Array；<br>API声明：findIndex(predicate: TypedArrayPredicateFn\<number, Int16Array>): number;<br>差异内容：findIndex(predicate: TypedArrayPredicateFn\<number, Int16Array>): number;|arkts/@arkts.collections.d.ets|
|新增API|NA|类名：Int16Array；<br>API声明：forEach(callbackFn: TypedArrayForEachCallback\<number, Int16Array>): void;<br>差异内容：forEach(callbackFn: TypedArrayForEachCallback\<number, Int16Array>): void;|arkts/@arkts.collections.d.ets|
|新增API|NA|类名：Int16Array；<br>API声明：indexOf(searchElement: number, fromIndex?: number): number;<br>差异内容：indexOf(searchElement: number, fromIndex?: number): number;|arkts/@arkts.collections.d.ets|
|新增API|NA|类名：Int16Array；<br>API声明：join(separator?: string): string;<br>差异内容：join(separator?: string): string;|arkts/@arkts.collections.d.ets|
|新增API|NA|类名：Int16Array；<br>API声明：map(callbackFn: TypedArrayMapCallback\<number, Int16Array>): Int16Array;<br>差异内容：map(callbackFn: TypedArrayMapCallback\<number, Int16Array>): Int16Array;|arkts/@arkts.collections.d.ets|
|新增API|NA|类名：Int16Array；<br>API声明：reduce(callbackFn: TypedArrayReduceCallback\<number, number, Int16Array>): number;<br>差异内容：reduce(callbackFn: TypedArrayReduceCallback\<number, number, Int16Array>): number;|arkts/@arkts.collections.d.ets|
|新增API|NA|类名：Int16Array；<br>API声明：reduce(callbackFn: TypedArrayReduceCallback\<number, number, Int16Array>, initialValue: number): number;<br>差异内容：reduce(callbackFn: TypedArrayReduceCallback\<number, number, Int16Array>, initialValue: number): number;|arkts/@arkts.collections.d.ets|
|新增API|NA|类名：Int16Array；<br>API声明：reduce\<U>(callbackFn: TypedArrayReduceCallback\<U, number, Int16Array>, initialValue: U): U;<br>差异内容：reduce\<U>(callbackFn: TypedArrayReduceCallback\<U, number, Int16Array>, initialValue: U): U;|arkts/@arkts.collections.d.ets|
|新增API|NA|类名：Int16Array；<br>API声明：reverse(): Int16Array;<br>差异内容：reverse(): Int16Array;|arkts/@arkts.collections.d.ets|
|新增API|NA|类名：Int16Array；<br>API声明：set(array: ArrayLike\<number>, offset?: number): void;<br>差异内容：set(array: ArrayLike\<number>, offset?: number): void;|arkts/@arkts.collections.d.ets|
|新增API|NA|类名：Int16Array；<br>API声明：slice(start?: number, end?: number): Int16Array;<br>差异内容：slice(start?: number, end?: number): Int16Array;|arkts/@arkts.collections.d.ets|
|新增API|NA|类名：Int16Array；<br>API声明：some(predicate: TypedArrayPredicateFn\<number, Int16Array>): boolean;<br>差异内容：some(predicate: TypedArrayPredicateFn\<number, Int16Array>): boolean;|arkts/@arkts.collections.d.ets|
|新增API|NA|类名：Int16Array；<br>API声明：sort(compareFn?: TypedArrayCompareFn\<number>): Int16Array;<br>差异内容：sort(compareFn?: TypedArrayCompareFn\<number>): Int16Array;|arkts/@arkts.collections.d.ets|
|新增API|NA|类名：Int16Array；<br>API声明：subarray(begin?: number, end?: number): Int16Array;<br>差异内容：subarray(begin?: number, end?: number): Int16Array;|arkts/@arkts.collections.d.ets|
|新增API|NA|类名：Int16Array；<br>API声明：at(index: number): number \| undefined;<br>差异内容：at(index: number): number \| undefined;|arkts/@arkts.collections.d.ets|
|新增API|NA|类名：Int16Array；<br>API声明：[Symbol.iterator](): IterableIterator\<number>;<br>差异内容：[Symbol.iterator](): IterableIterator\<number>;|arkts/@arkts.collections.d.ets|
|新增API|NA|类名：Int16Array；<br>API声明：entries(): IterableIterator\<[number, number]>;<br>差异内容：entries(): IterableIterator\<[number, number]>;|arkts/@arkts.collections.d.ets|
|新增API|NA|类名：Int16Array；<br>API声明：keys(): IterableIterator\<number>;<br>差异内容：keys(): IterableIterator\<number>;|arkts/@arkts.collections.d.ets|
|新增API|NA|类名：Int16Array；<br>API声明：values(): IterableIterator\<number>;<br>差异内容：values(): IterableIterator\<number>;|arkts/@arkts.collections.d.ets|
|新增API|NA|类名：Int16Array；<br>API声明：includes(searchElement: number, fromIndex?: number): boolean;<br>差异内容：includes(searchElement: number, fromIndex?: number): boolean;|arkts/@arkts.collections.d.ets|
|新增API|NA|类名：Int16Array；<br>API声明：[index: number]: number;<br>差异内容：[index: number]: number;|arkts/@arkts.collections.d.ets|
|新增API|NA|类名：collections；<br>API声明：class Uint16Array<br>差异内容：class Uint16Array|arkts/@arkts.collections.d.ets|
|新增API|NA|类名：Uint16Array；<br>API声明：static readonly BYTES_PER_ELEMENT: number;<br>差异内容：static readonly BYTES_PER_ELEMENT: number;|arkts/@arkts.collections.d.ets|
|新增API|NA|类名：Uint16Array；<br>API声明：readonly buffer: ArrayBuffer;<br>差异内容：readonly buffer: ArrayBuffer;|arkts/@arkts.collections.d.ets|
|新增API|NA|类名：Uint16Array；<br>API声明：readonly byteLength: number;<br>差异内容：readonly byteLength: number;|arkts/@arkts.collections.d.ets|
|新增API|NA|类名：Uint16Array；<br>API声明：readonly byteOffset: number;<br>差异内容：readonly byteOffset: number;|arkts/@arkts.collections.d.ets|
|新增API|NA|类名：Uint16Array；<br>API声明：readonly length: number;<br>差异内容：readonly length: number;|arkts/@arkts.collections.d.ets|
|新增API|NA|类名：Uint16Array；<br>API声明：static from(arrayLike: ArrayLike\<number>): Uint16Array;<br>差异内容：static from(arrayLike: ArrayLike\<number>): Uint16Array;|arkts/@arkts.collections.d.ets|
|新增API|NA|类名：Uint16Array；<br>API声明：static from\<T>(arrayLike: ArrayLike\<T>, mapFn: TypedArrayFromMapFn\<T, number>): Uint16Array;<br>差异内容：static from\<T>(arrayLike: ArrayLike\<T>, mapFn: TypedArrayFromMapFn\<T, number>): Uint16Array;|arkts/@arkts.collections.d.ets|
|新增API|NA|类名：Uint16Array；<br>API声明：static from(arrayLike: Iterable\<number>, mapFn?: TypedArrayFromMapFn\<number, number>): Uint16Array;<br>差异内容：static from(arrayLike: Iterable\<number>, mapFn?: TypedArrayFromMapFn\<number, number>): Uint16Array;|arkts/@arkts.collections.d.ets|
|新增API|NA|类名：Uint16Array；<br>API声明：copyWithin(target: number, start: number, end?: number): Uint16Array;<br>差异内容：copyWithin(target: number, start: number, end?: number): Uint16Array;|arkts/@arkts.collections.d.ets|
|新增API|NA|类名：Uint16Array；<br>API声明：every(predicate: TypedArrayPredicateFn\<number, Uint16Array>): boolean;<br>差异内容：every(predicate: TypedArrayPredicateFn\<number, Uint16Array>): boolean;|arkts/@arkts.collections.d.ets|
|新增API|NA|类名：Uint16Array；<br>API声明：fill(value: number, start?: number, end?: number): Uint16Array;<br>差异内容：fill(value: number, start?: number, end?: number): Uint16Array;|arkts/@arkts.collections.d.ets|
|新增API|NA|类名：Uint16Array；<br>API声明：filter(predicate: TypedArrayPredicateFn\<number, Uint16Array>): Uint16Array;<br>差异内容：filter(predicate: TypedArrayPredicateFn\<number, Uint16Array>): Uint16Array;|arkts/@arkts.collections.d.ets|
|新增API|NA|类名：Uint16Array；<br>API声明：find(predicate: TypedArrayPredicateFn\<number, Uint16Array>): number \| undefined;<br>差异内容：find(predicate: TypedArrayPredicateFn\<number, Uint16Array>): number \| undefined;|arkts/@arkts.collections.d.ets|
|新增API|NA|类名：Uint16Array；<br>API声明：findIndex(predicate: TypedArrayPredicateFn\<number, Uint16Array>): number;<br>差异内容：findIndex(predicate: TypedArrayPredicateFn\<number, Uint16Array>): number;|arkts/@arkts.collections.d.ets|
|新增API|NA|类名：Uint16Array；<br>API声明：forEach(callbackFn: TypedArrayForEachCallback\<number, Uint16Array>): void;<br>差异内容：forEach(callbackFn: TypedArrayForEachCallback\<number, Uint16Array>): void;|arkts/@arkts.collections.d.ets|
|新增API|NA|类名：Uint16Array；<br>API声明：indexOf(searchElement: number, fromIndex?: number): number;<br>差异内容：indexOf(searchElement: number, fromIndex?: number): number;|arkts/@arkts.collections.d.ets|
|新增API|NA|类名：Uint16Array；<br>API声明：join(separator?: string): string;<br>差异内容：join(separator?: string): string;|arkts/@arkts.collections.d.ets|
|新增API|NA|类名：Uint16Array；<br>API声明：map(callbackFn: TypedArrayMapCallback\<number, Uint16Array>): Uint16Array;<br>差异内容：map(callbackFn: TypedArrayMapCallback\<number, Uint16Array>): Uint16Array;|arkts/@arkts.collections.d.ets|
|新增API|NA|类名：Uint16Array；<br>API声明：reduce(callbackFn: TypedArrayReduceCallback\<number, number, Uint16Array>): number;<br>差异内容：reduce(callbackFn: TypedArrayReduceCallback\<number, number, Uint16Array>): number;|arkts/@arkts.collections.d.ets|
|新增API|NA|类名：Uint16Array；<br>API声明：reduce(callbackFn: TypedArrayReduceCallback\<number, number, Uint16Array>, initialValue: number): number;<br>差异内容：reduce(callbackFn: TypedArrayReduceCallback\<number, number, Uint16Array>, initialValue: number): number;|arkts/@arkts.collections.d.ets|
|新增API|NA|类名：Uint16Array；<br>API声明：reduce\<U>(callbackFn: TypedArrayReduceCallback\<U, number, Uint16Array>, initialValue: U): U;<br>差异内容：reduce\<U>(callbackFn: TypedArrayReduceCallback\<U, number, Uint16Array>, initialValue: U): U;|arkts/@arkts.collections.d.ets|
|新增API|NA|类名：Uint16Array；<br>API声明：reverse(): Uint16Array;<br>差异内容：reverse(): Uint16Array;|arkts/@arkts.collections.d.ets|
|新增API|NA|类名：Uint16Array；<br>API声明：set(array: ArrayLike\<number>, offset?: number): void;<br>差异内容：set(array: ArrayLike\<number>, offset?: number): void;|arkts/@arkts.collections.d.ets|
|新增API|NA|类名：Uint16Array；<br>API声明：slice(start?: number, end?: number): Uint16Array;<br>差异内容：slice(start?: number, end?: number): Uint16Array;|arkts/@arkts.collections.d.ets|
|新增API|NA|类名：Uint16Array；<br>API声明：some(predicate: TypedArrayPredicateFn\<number, Uint16Array>): boolean;<br>差异内容：some(predicate: TypedArrayPredicateFn\<number, Uint16Array>): boolean;|arkts/@arkts.collections.d.ets|
|新增API|NA|类名：Uint16Array；<br>API声明：sort(compareFn?: TypedArrayCompareFn\<number>): Uint16Array;<br>差异内容：sort(compareFn?: TypedArrayCompareFn\<number>): Uint16Array;|arkts/@arkts.collections.d.ets|
|新增API|NA|类名：Uint16Array；<br>API声明：subarray(begin?: number, end?: number): Uint16Array;<br>差异内容：subarray(begin?: number, end?: number): Uint16Array;|arkts/@arkts.collections.d.ets|
|新增API|NA|类名：Uint16Array；<br>API声明：at(index: number): number \| undefined;<br>差异内容：at(index: number): number \| undefined;|arkts/@arkts.collections.d.ets|
|新增API|NA|类名：Uint16Array；<br>API声明：[Symbol.iterator](): IterableIterator\<number>;<br>差异内容：[Symbol.iterator](): IterableIterator\<number>;|arkts/@arkts.collections.d.ets|
|新增API|NA|类名：Uint16Array；<br>API声明：entries(): IterableIterator\<[number, number]>;<br>差异内容：entries(): IterableIterator\<[number, number]>;|arkts/@arkts.collections.d.ets|
|新增API|NA|类名：Uint16Array；<br>API声明：keys(): IterableIterator\<number>;<br>差异内容：keys(): IterableIterator\<number>;|arkts/@arkts.collections.d.ets|
|新增API|NA|类名：Uint16Array；<br>API声明：values(): IterableIterator\<number>;<br>差异内容：values(): IterableIterator\<number>;|arkts/@arkts.collections.d.ets|
|新增API|NA|类名：Uint16Array；<br>API声明：includes(searchElement: number, fromIndex?: number): boolean;<br>差异内容：includes(searchElement: number, fromIndex?: number): boolean;|arkts/@arkts.collections.d.ets|
|新增API|NA|类名：Uint16Array；<br>API声明：[index: number]: number;<br>差异内容：[index: number]: number;|arkts/@arkts.collections.d.ets|
|新增API|NA|类名：collections；<br>API声明：class Int32Array<br>差异内容：class Int32Array|arkts/@arkts.collections.d.ets|
|新增API|NA|类名：Int32Array；<br>API声明：static readonly BYTES_PER_ELEMENT: number;<br>差异内容：static readonly BYTES_PER_ELEMENT: number;|arkts/@arkts.collections.d.ets|
|新增API|NA|类名：Int32Array；<br>API声明：readonly buffer: ArrayBuffer;<br>差异内容：readonly buffer: ArrayBuffer;|arkts/@arkts.collections.d.ets|
|新增API|NA|类名：Int32Array；<br>API声明：readonly byteLength: number;<br>差异内容：readonly byteLength: number;|arkts/@arkts.collections.d.ets|
|新增API|NA|类名：Int32Array；<br>API声明：readonly byteOffset: number;<br>差异内容：readonly byteOffset: number;|arkts/@arkts.collections.d.ets|
|新增API|NA|类名：Int32Array；<br>API声明：readonly length: number;<br>差异内容：readonly length: number;|arkts/@arkts.collections.d.ets|
|新增API|NA|类名：Int32Array；<br>API声明：static from(arrayLike: ArrayLike\<number>): Int32Array;<br>差异内容：static from(arrayLike: ArrayLike\<number>): Int32Array;|arkts/@arkts.collections.d.ets|
|新增API|NA|类名：Int32Array；<br>API声明：static from\<T>(arrayLike: ArrayLike\<T>, mapFn: TypedArrayFromMapFn\<T, number>): Int32Array;<br>差异内容：static from\<T>(arrayLike: ArrayLike\<T>, mapFn: TypedArrayFromMapFn\<T, number>): Int32Array;|arkts/@arkts.collections.d.ets|
|新增API|NA|类名：Int32Array；<br>API声明：static from(arrayLike: Iterable\<number>, mapFn?: TypedArrayFromMapFn\<number, number>): Int32Array;<br>差异内容：static from(arrayLike: Iterable\<number>, mapFn?: TypedArrayFromMapFn\<number, number>): Int32Array;|arkts/@arkts.collections.d.ets|
|新增API|NA|类名：Int32Array；<br>API声明：copyWithin(target: number, start: number, end?: number): Int32Array;<br>差异内容：copyWithin(target: number, start: number, end?: number): Int32Array;|arkts/@arkts.collections.d.ets|
|新增API|NA|类名：Int32Array；<br>API声明：every(predicate: TypedArrayPredicateFn\<number, Int32Array>): boolean;<br>差异内容：every(predicate: TypedArrayPredicateFn\<number, Int32Array>): boolean;|arkts/@arkts.collections.d.ets|
|新增API|NA|类名：Int32Array；<br>API声明：fill(value: number, start?: number, end?: number): Int32Array;<br>差异内容：fill(value: number, start?: number, end?: number): Int32Array;|arkts/@arkts.collections.d.ets|
|新增API|NA|类名：Int32Array；<br>API声明：filter(predicate: TypedArrayPredicateFn\<number, Int32Array>): Int32Array;<br>差异内容：filter(predicate: TypedArrayPredicateFn\<number, Int32Array>): Int32Array;|arkts/@arkts.collections.d.ets|
|新增API|NA|类名：Int32Array；<br>API声明：find(predicate: TypedArrayPredicateFn\<number, Int32Array>): number \| undefined;<br>差异内容：find(predicate: TypedArrayPredicateFn\<number, Int32Array>): number \| undefined;|arkts/@arkts.collections.d.ets|
|新增API|NA|类名：Int32Array；<br>API声明：findIndex(predicate: TypedArrayPredicateFn\<number, Int32Array>): number;<br>差异内容：findIndex(predicate: TypedArrayPredicateFn\<number, Int32Array>): number;|arkts/@arkts.collections.d.ets|
|新增API|NA|类名：Int32Array；<br>API声明：forEach(callbackFn: TypedArrayForEachCallback\<number, Int32Array>): void;<br>差异内容：forEach(callbackFn: TypedArrayForEachCallback\<number, Int32Array>): void;|arkts/@arkts.collections.d.ets|
|新增API|NA|类名：Int32Array；<br>API声明：indexOf(searchElement: number, fromIndex?: number): number;<br>差异内容：indexOf(searchElement: number, fromIndex?: number): number;|arkts/@arkts.collections.d.ets|
|新增API|NA|类名：Int32Array；<br>API声明：join(separator?: string): string;<br>差异内容：join(separator?: string): string;|arkts/@arkts.collections.d.ets|
|新增API|NA|类名：Int32Array；<br>API声明：map(callbackFn: TypedArrayMapCallback\<number, Int32Array>): Int32Array;<br>差异内容：map(callbackFn: TypedArrayMapCallback\<number, Int32Array>): Int32Array;|arkts/@arkts.collections.d.ets|
|新增API|NA|类名：Int32Array；<br>API声明：reduce(callbackFn: TypedArrayReduceCallback\<number, number, Int32Array>): number;<br>差异内容：reduce(callbackFn: TypedArrayReduceCallback\<number, number, Int32Array>): number;|arkts/@arkts.collections.d.ets|
|新增API|NA|类名：Int32Array；<br>API声明：reduce(callbackFn: TypedArrayReduceCallback\<number, number, Int32Array>, initialValue: number): number;<br>差异内容：reduce(callbackFn: TypedArrayReduceCallback\<number, number, Int32Array>, initialValue: number): number;|arkts/@arkts.collections.d.ets|
|新增API|NA|类名：Int32Array；<br>API声明：reduce\<U>(callbackFn: TypedArrayReduceCallback\<U, number, Int32Array>, initialValue: U): U;<br>差异内容：reduce\<U>(callbackFn: TypedArrayReduceCallback\<U, number, Int32Array>, initialValue: U): U;|arkts/@arkts.collections.d.ets|
|新增API|NA|类名：Int32Array；<br>API声明：reverse(): Int32Array;<br>差异内容：reverse(): Int32Array;|arkts/@arkts.collections.d.ets|
|新增API|NA|类名：Int32Array；<br>API声明：set(array: ArrayLike\<number>, offset?: number): void;<br>差异内容：set(array: ArrayLike\<number>, offset?: number): void;|arkts/@arkts.collections.d.ets|
|新增API|NA|类名：Int32Array；<br>API声明：slice(start?: number, end?: number): Int32Array;<br>差异内容：slice(start?: number, end?: number): Int32Array;|arkts/@arkts.collections.d.ets|
|新增API|NA|类名：Int32Array；<br>API声明：some(predicate: TypedArrayPredicateFn\<number, Int32Array>): boolean;<br>差异内容：some(predicate: TypedArrayPredicateFn\<number, Int32Array>): boolean;|arkts/@arkts.collections.d.ets|
|新增API|NA|类名：Int32Array；<br>API声明：sort(compareFn?: TypedArrayCompareFn\<number>): Int32Array;<br>差异内容：sort(compareFn?: TypedArrayCompareFn\<number>): Int32Array;|arkts/@arkts.collections.d.ets|
|新增API|NA|类名：Int32Array；<br>API声明：subarray(begin?: number, end?: number): Int32Array;<br>差异内容：subarray(begin?: number, end?: number): Int32Array;|arkts/@arkts.collections.d.ets|
|新增API|NA|类名：Int32Array；<br>API声明：at(index: number): number \| undefined;<br>差异内容：at(index: number): number \| undefined;|arkts/@arkts.collections.d.ets|
|新增API|NA|类名：Int32Array；<br>API声明：[Symbol.iterator](): IterableIterator\<number>;<br>差异内容：[Symbol.iterator](): IterableIterator\<number>;|arkts/@arkts.collections.d.ets|
|新增API|NA|类名：Int32Array；<br>API声明：entries(): IterableIterator\<[number, number]>;<br>差异内容：entries(): IterableIterator\<[number, number]>;|arkts/@arkts.collections.d.ets|
|新增API|NA|类名：Int32Array；<br>API声明：keys(): IterableIterator\<number>;<br>差异内容：keys(): IterableIterator\<number>;|arkts/@arkts.collections.d.ets|
|新增API|NA|类名：Int32Array；<br>API声明：values(): IterableIterator\<number>;<br>差异内容：values(): IterableIterator\<number>;|arkts/@arkts.collections.d.ets|
|新增API|NA|类名：Int32Array；<br>API声明：includes(searchElement: number, fromIndex?: number): boolean;<br>差异内容：includes(searchElement: number, fromIndex?: number): boolean;|arkts/@arkts.collections.d.ets|
|新增API|NA|类名：Int32Array；<br>API声明：[index: number]: number;<br>差异内容：[index: number]: number;|arkts/@arkts.collections.d.ets|
|新增API|NA|类名：collections；<br>API声明：class Uint32Array<br>差异内容：class Uint32Array|arkts/@arkts.collections.d.ets|
|新增API|NA|类名：Uint32Array；<br>API声明：static readonly BYTES_PER_ELEMENT: number;<br>差异内容：static readonly BYTES_PER_ELEMENT: number;|arkts/@arkts.collections.d.ets|
|新增API|NA|类名：Uint32Array；<br>API声明：readonly buffer: ArrayBuffer;<br>差异内容：readonly buffer: ArrayBuffer;|arkts/@arkts.collections.d.ets|
|新增API|NA|类名：Uint32Array；<br>API声明：readonly byteLength: number;<br>差异内容：readonly byteLength: number;|arkts/@arkts.collections.d.ets|
|新增API|NA|类名：Uint32Array；<br>API声明：readonly byteOffset: number;<br>差异内容：readonly byteOffset: number;|arkts/@arkts.collections.d.ets|
|新增API|NA|类名：Uint32Array；<br>API声明：readonly length: number;<br>差异内容：readonly length: number;|arkts/@arkts.collections.d.ets|
|新增API|NA|类名：Uint32Array；<br>API声明：static from(arrayLike: ArrayLike\<number>): Uint32Array;<br>差异内容：static from(arrayLike: ArrayLike\<number>): Uint32Array;|arkts/@arkts.collections.d.ets|
|新增API|NA|类名：Uint32Array；<br>API声明：static from\<T>(arrayLike: ArrayLike\<T>, mapFn: TypedArrayFromMapFn\<T, number>): Uint32Array;<br>差异内容：static from\<T>(arrayLike: ArrayLike\<T>, mapFn: TypedArrayFromMapFn\<T, number>): Uint32Array;|arkts/@arkts.collections.d.ets|
|新增API|NA|类名：Uint32Array；<br>API声明：static from(arrayLike: Iterable\<number>, mapFn?: TypedArrayFromMapFn\<number, number>): Uint32Array;<br>差异内容：static from(arrayLike: Iterable\<number>, mapFn?: TypedArrayFromMapFn\<number, number>): Uint32Array;|arkts/@arkts.collections.d.ets|
|新增API|NA|类名：Uint32Array；<br>API声明：copyWithin(target: number, start: number, end?: number): Uint32Array;<br>差异内容：copyWithin(target: number, start: number, end?: number): Uint32Array;|arkts/@arkts.collections.d.ets|
|新增API|NA|类名：Uint32Array；<br>API声明：every(predicate: TypedArrayPredicateFn\<number, Uint32Array>): boolean;<br>差异内容：every(predicate: TypedArrayPredicateFn\<number, Uint32Array>): boolean;|arkts/@arkts.collections.d.ets|
|新增API|NA|类名：Uint32Array；<br>API声明：fill(value: number, start?: number, end?: number): Uint32Array;<br>差异内容：fill(value: number, start?: number, end?: number): Uint32Array;|arkts/@arkts.collections.d.ets|
|新增API|NA|类名：Uint32Array；<br>API声明：filter(predicate: TypedArrayPredicateFn\<number, Uint32Array>): Uint32Array;<br>差异内容：filter(predicate: TypedArrayPredicateFn\<number, Uint32Array>): Uint32Array;|arkts/@arkts.collections.d.ets|
|新增API|NA|类名：Uint32Array；<br>API声明：find(predicate: TypedArrayPredicateFn\<number, Uint32Array>): number \| undefined;<br>差异内容：find(predicate: TypedArrayPredicateFn\<number, Uint32Array>): number \| undefined;|arkts/@arkts.collections.d.ets|
|新增API|NA|类名：Uint32Array；<br>API声明：findIndex(predicate: TypedArrayPredicateFn\<number, Uint32Array>): number;<br>差异内容：findIndex(predicate: TypedArrayPredicateFn\<number, Uint32Array>): number;|arkts/@arkts.collections.d.ets|
|新增API|NA|类名：Uint32Array；<br>API声明：forEach(callbackFn: TypedArrayForEachCallback\<number, Uint32Array>): void;<br>差异内容：forEach(callbackFn: TypedArrayForEachCallback\<number, Uint32Array>): void;|arkts/@arkts.collections.d.ets|
|新增API|NA|类名：Uint32Array；<br>API声明：indexOf(searchElement: number, fromIndex?: number): number;<br>差异内容：indexOf(searchElement: number, fromIndex?: number): number;|arkts/@arkts.collections.d.ets|
|新增API|NA|类名：Uint32Array；<br>API声明：join(separator?: string): string;<br>差异内容：join(separator?: string): string;|arkts/@arkts.collections.d.ets|
|新增API|NA|类名：Uint32Array；<br>API声明：map(callbackFn: TypedArrayMapCallback\<number, Uint32Array>): Uint32Array;<br>差异内容：map(callbackFn: TypedArrayMapCallback\<number, Uint32Array>): Uint32Array;|arkts/@arkts.collections.d.ets|
|新增API|NA|类名：Uint32Array；<br>API声明：reduce(callbackFn: TypedArrayReduceCallback\<number, number, Uint32Array>): number;<br>差异内容：reduce(callbackFn: TypedArrayReduceCallback\<number, number, Uint32Array>): number;|arkts/@arkts.collections.d.ets|
|新增API|NA|类名：Uint32Array；<br>API声明：reduce(callbackFn: TypedArrayReduceCallback\<number, number, Uint32Array>, initialValue: number): number;<br>差异内容：reduce(callbackFn: TypedArrayReduceCallback\<number, number, Uint32Array>, initialValue: number): number;|arkts/@arkts.collections.d.ets|
|新增API|NA|类名：Uint32Array；<br>API声明：reduce\<U>(callbackFn: TypedArrayReduceCallback\<U, number, Uint32Array>, initialValue: U): U;<br>差异内容：reduce\<U>(callbackFn: TypedArrayReduceCallback\<U, number, Uint32Array>, initialValue: U): U;|arkts/@arkts.collections.d.ets|
|新增API|NA|类名：Uint32Array；<br>API声明：reverse(): Uint32Array;<br>差异内容：reverse(): Uint32Array;|arkts/@arkts.collections.d.ets|
|新增API|NA|类名：Uint32Array；<br>API声明：set(array: ArrayLike\<number>, offset?: number): void;<br>差异内容：set(array: ArrayLike\<number>, offset?: number): void;|arkts/@arkts.collections.d.ets|
|新增API|NA|类名：Uint32Array；<br>API声明：slice(start?: number, end?: number): Uint32Array;<br>差异内容：slice(start?: number, end?: number): Uint32Array;|arkts/@arkts.collections.d.ets|
|新增API|NA|类名：Uint32Array；<br>API声明：some(predicate: TypedArrayPredicateFn\<number, Uint32Array>): boolean;<br>差异内容：some(predicate: TypedArrayPredicateFn\<number, Uint32Array>): boolean;|arkts/@arkts.collections.d.ets|
|新增API|NA|类名：Uint32Array；<br>API声明：sort(compareFn?: TypedArrayCompareFn\<number>): Uint32Array;<br>差异内容：sort(compareFn?: TypedArrayCompareFn\<number>): Uint32Array;|arkts/@arkts.collections.d.ets|
|新增API|NA|类名：Uint32Array；<br>API声明：subarray(begin?: number, end?: number): Uint32Array;<br>差异内容：subarray(begin?: number, end?: number): Uint32Array;|arkts/@arkts.collections.d.ets|
|新增API|NA|类名：Uint32Array；<br>API声明：at(index: number): number \| undefined;<br>差异内容：at(index: number): number \| undefined;|arkts/@arkts.collections.d.ets|
|新增API|NA|类名：Uint32Array；<br>API声明：[Symbol.iterator](): IterableIterator\<number>;<br>差异内容：[Symbol.iterator](): IterableIterator\<number>;|arkts/@arkts.collections.d.ets|
|新增API|NA|类名：Uint32Array；<br>API声明：entries(): IterableIterator\<[number, number]>;<br>差异内容：entries(): IterableIterator\<[number, number]>;|arkts/@arkts.collections.d.ets|
|新增API|NA|类名：Uint32Array；<br>API声明：keys(): IterableIterator\<number>;<br>差异内容：keys(): IterableIterator\<number>;|arkts/@arkts.collections.d.ets|
|新增API|NA|类名：Uint32Array；<br>API声明：values(): IterableIterator\<number>;<br>差异内容：values(): IterableIterator\<number>;|arkts/@arkts.collections.d.ets|
|新增API|NA|类名：Uint32Array；<br>API声明：includes(searchElement: number, fromIndex?: number): boolean;<br>差异内容：includes(searchElement: number, fromIndex?: number): boolean;|arkts/@arkts.collections.d.ets|
|新增API|NA|类名：Uint32Array；<br>API声明：[index: number]: number;<br>差异内容：[index: number]: number;|arkts/@arkts.collections.d.ets|
|新增API|NA|类名：collections；<br>API声明：class Float32Array<br>差异内容：class Float32Array|arkts/@arkts.collections.d.ets|
|新增API|NA|类名：Float32Array；<br>API声明：static readonly BYTES_PER_ELEMENT: number;<br>差异内容：static readonly BYTES_PER_ELEMENT: number;|arkts/@arkts.collections.d.ets|
|新增API|NA|类名：Float32Array；<br>API声明：readonly buffer: ArrayBuffer;<br>差异内容：readonly buffer: ArrayBuffer;|arkts/@arkts.collections.d.ets|
|新增API|NA|类名：Float32Array；<br>API声明：readonly byteLength: number;<br>差异内容：readonly byteLength: number;|arkts/@arkts.collections.d.ets|
|新增API|NA|类名：Float32Array；<br>API声明：readonly byteOffset: number;<br>差异内容：readonly byteOffset: number;|arkts/@arkts.collections.d.ets|
|新增API|NA|类名：Float32Array；<br>API声明：readonly length: number;<br>差异内容：readonly length: number;|arkts/@arkts.collections.d.ets|
|新增API|NA|类名：Float32Array；<br>API声明：static from(arrayLike: ArrayLike\<number>): Float32Array;<br>差异内容：static from(arrayLike: ArrayLike\<number>): Float32Array;|arkts/@arkts.collections.d.ets|
|新增API|NA|类名：Float32Array；<br>API声明：static from\<T>(arrayLike: ArrayLike\<T>, mapFn: TypedArrayFromMapFn\<T, number>): Float32Array;<br>差异内容：static from\<T>(arrayLike: ArrayLike\<T>, mapFn: TypedArrayFromMapFn\<T, number>): Float32Array;|arkts/@arkts.collections.d.ets|
|新增API|NA|类名：Float32Array；<br>API声明：static from(arrayLike: Iterable\<number>, mapFn?: TypedArrayFromMapFn\<number, number>): Float32Array;<br>差异内容：static from(arrayLike: Iterable\<number>, mapFn?: TypedArrayFromMapFn\<number, number>): Float32Array;|arkts/@arkts.collections.d.ets|
|新增API|NA|类名：Float32Array；<br>API声明：copyWithin(target: number, start: number, end?: number): Float32Array;<br>差异内容：copyWithin(target: number, start: number, end?: number): Float32Array;|arkts/@arkts.collections.d.ets|
|新增API|NA|类名：Float32Array；<br>API声明：every(predicate: TypedArrayPredicateFn\<number, Float32Array>): boolean;<br>差异内容：every(predicate: TypedArrayPredicateFn\<number, Float32Array>): boolean;|arkts/@arkts.collections.d.ets|
|新增API|NA|类名：Float32Array；<br>API声明：fill(value: number, start?: number, end?: number): Float32Array;<br>差异内容：fill(value: number, start?: number, end?: number): Float32Array;|arkts/@arkts.collections.d.ets|
|新增API|NA|类名：Float32Array；<br>API声明：filter(predicate: TypedArrayPredicateFn\<number, Float32Array>): Float32Array;<br>差异内容：filter(predicate: TypedArrayPredicateFn\<number, Float32Array>): Float32Array;|arkts/@arkts.collections.d.ets|
|新增API|NA|类名：Float32Array；<br>API声明：find(predicate: TypedArrayPredicateFn\<number, Float32Array>): number \| undefined;<br>差异内容：find(predicate: TypedArrayPredicateFn\<number, Float32Array>): number \| undefined;|arkts/@arkts.collections.d.ets|
|新增API|NA|类名：Float32Array；<br>API声明：findIndex(predicate: TypedArrayPredicateFn\<number, Float32Array>): number;<br>差异内容：findIndex(predicate: TypedArrayPredicateFn\<number, Float32Array>): number;|arkts/@arkts.collections.d.ets|
|新增API|NA|类名：Float32Array；<br>API声明：forEach(callbackFn: TypedArrayForEachCallback\<number, Float32Array>): void;<br>差异内容：forEach(callbackFn: TypedArrayForEachCallback\<number, Float32Array>): void;|arkts/@arkts.collections.d.ets|
|新增API|NA|类名：Float32Array；<br>API声明：indexOf(searchElement: number, fromIndex?: number): number;<br>差异内容：indexOf(searchElement: number, fromIndex?: number): number;|arkts/@arkts.collections.d.ets|
|新增API|NA|类名：Float32Array；<br>API声明：join(separator?: string): string;<br>差异内容：join(separator?: string): string;|arkts/@arkts.collections.d.ets|
|新增API|NA|类名：Float32Array；<br>API声明：map(callbackFn: TypedArrayMapCallback\<number, Float32Array>): Float32Array;<br>差异内容：map(callbackFn: TypedArrayMapCallback\<number, Float32Array>): Float32Array;|arkts/@arkts.collections.d.ets|
|新增API|NA|类名：Float32Array；<br>API声明：reduce(callbackFn: TypedArrayReduceCallback\<number, number, Float32Array>): number;<br>差异内容：reduce(callbackFn: TypedArrayReduceCallback\<number, number, Float32Array>): number;|arkts/@arkts.collections.d.ets|
|新增API|NA|类名：Float32Array；<br>API声明：reduce\<U = number>(callbackFn: TypedArrayReduceCallback\<U, number, Float32Array>, initialValue: U): U;<br>差异内容：reduce\<U = number>(callbackFn: TypedArrayReduceCallback\<U, number, Float32Array>, initialValue: U): U;|arkts/@arkts.collections.d.ets|
|新增API|NA|类名：Float32Array；<br>API声明：reverse(): Float32Array;<br>差异内容：reverse(): Float32Array;|arkts/@arkts.collections.d.ets|
|新增API|NA|类名：Float32Array；<br>API声明：set(array: ArrayLike\<number>, offset?: number): void;<br>差异内容：set(array: ArrayLike\<number>, offset?: number): void;|arkts/@arkts.collections.d.ets|
|新增API|NA|类名：Float32Array；<br>API声明：slice(start?: number, end?: number): Float32Array;<br>差异内容：slice(start?: number, end?: number): Float32Array;|arkts/@arkts.collections.d.ets|
|新增API|NA|类名：Float32Array；<br>API声明：some(predicate: TypedArrayPredicateFn\<number, Float32Array>): boolean;<br>差异内容：some(predicate: TypedArrayPredicateFn\<number, Float32Array>): boolean;|arkts/@arkts.collections.d.ets|
|新增API|NA|类名：Float32Array；<br>API声明：sort(compareFn?: TypedArrayCompareFn\<number>): Float32Array;<br>差异内容：sort(compareFn?: TypedArrayCompareFn\<number>): Float32Array;|arkts/@arkts.collections.d.ets|
|新增API|NA|类名：Float32Array；<br>API声明：subarray(begin?: number, end?: number): Float32Array;<br>差异内容：subarray(begin?: number, end?: number): Float32Array;|arkts/@arkts.collections.d.ets|
|新增API|NA|类名：Float32Array；<br>API声明：at(index: number): number \| undefined;<br>差异内容：at(index: number): number \| undefined;|arkts/@arkts.collections.d.ets|
|新增API|NA|类名：Float32Array；<br>API声明：[Symbol.iterator](): IterableIterator\<number>;<br>差异内容：[Symbol.iterator](): IterableIterator\<number>;|arkts/@arkts.collections.d.ets|
|新增API|NA|类名：Float32Array；<br>API声明：entries(): IterableIterator\<[number, number]>;<br>差异内容：entries(): IterableIterator\<[number, number]>;|arkts/@arkts.collections.d.ets|
|新增API|NA|类名：Float32Array；<br>API声明：keys(): IterableIterator\<number>;<br>差异内容：keys(): IterableIterator\<number>;|arkts/@arkts.collections.d.ets|
|新增API|NA|类名：Float32Array；<br>API声明：values(): IterableIterator\<number>;<br>差异内容：values(): IterableIterator\<number>;|arkts/@arkts.collections.d.ets|
|新增API|NA|类名：Float32Array；<br>API声明：includes(searchElement: number, fromIndex?: number): boolean;<br>差异内容：includes(searchElement: number, fromIndex?: number): boolean;|arkts/@arkts.collections.d.ets|
|新增API|NA|类名：Float32Array；<br>API声明：[index: number]: number;<br>差异内容：[index: number]: number;|arkts/@arkts.collections.d.ets|
|新增API|NA|类名：collections；<br>API声明：class BitVector<br>差异内容：class BitVector|arkts/@arkts.collections.d.ets|
|新增API|NA|类名：BitVector；<br>API声明：readonly length: number;<br>差异内容：readonly length: number;|arkts/@arkts.collections.d.ets|
|新增API|NA|类名：BitVector；<br>API声明：push(element: number): boolean;<br>差异内容：push(element: number): boolean;|arkts/@arkts.collections.d.ets|
|新增API|NA|类名：BitVector；<br>API声明：pop(): number;<br>差异内容：pop(): number;|arkts/@arkts.collections.d.ets|
|新增API|NA|类名：BitVector；<br>API声明：has(element: number, fromIndex: number, toIndex: number): boolean;<br>差异内容：has(element: number, fromIndex: number, toIndex: number): boolean;|arkts/@arkts.collections.d.ets|
|新增API|NA|类名：BitVector；<br>API声明：setBitsByRange(element: number, fromIndex: number, toIndex: number): void;<br>差异内容：setBitsByRange(element: number, fromIndex: number, toIndex: number): void;|arkts/@arkts.collections.d.ets|
|新增API|NA|类名：BitVector；<br>API声明：setAllBits(element: number): void;<br>差异内容：setAllBits(element: number): void;|arkts/@arkts.collections.d.ets|
|新增API|NA|类名：BitVector；<br>API声明：getBitsByRange(fromIndex: number, toIndex: number): BitVector;<br>差异内容：getBitsByRange(fromIndex: number, toIndex: number): BitVector;|arkts/@arkts.collections.d.ets|
|新增API|NA|类名：BitVector；<br>API声明：resize(size: number): void;<br>差异内容：resize(size: number): void;|arkts/@arkts.collections.d.ets|
|新增API|NA|类名：BitVector；<br>API声明：getBitCountByRange(element: number, fromIndex: number, toIndex: number): number;<br>差异内容：getBitCountByRange(element: number, fromIndex: number, toIndex: number): number;|arkts/@arkts.collections.d.ets|
|新增API|NA|类名：BitVector；<br>API声明：getIndexOf(element: number, fromIndex: number, toIndex: number): number;<br>差异内容：getIndexOf(element: number, fromIndex: number, toIndex: number): number;|arkts/@arkts.collections.d.ets|
|新增API|NA|类名：BitVector；<br>API声明：getLastIndexOf(element: number, fromIndex: number, toIndex: number): number;<br>差异内容：getLastIndexOf(element: number, fromIndex: number, toIndex: number): number;|arkts/@arkts.collections.d.ets|
|新增API|NA|类名：BitVector；<br>API声明：flipBitByIndex(index: number): void;<br>差异内容：flipBitByIndex(index: number): void;|arkts/@arkts.collections.d.ets|
|新增API|NA|类名：BitVector；<br>API声明：flipBitsByRange(fromIndex: number, toIndex: number): void;<br>差异内容：flipBitsByRange(fromIndex: number, toIndex: number): void;|arkts/@arkts.collections.d.ets|
|新增API|NA|类名：BitVector；<br>API声明：[Symbol.iterator](): IterableIterator\<number>;<br>差异内容：[Symbol.iterator](): IterableIterator\<number>;|arkts/@arkts.collections.d.ets|
|新增API|NA|类名：BitVector；<br>API声明：values(): IterableIterator\<number>;<br>差异内容：values(): IterableIterator\<number>;|arkts/@arkts.collections.d.ets|
|新增API|NA|类名：BitVector；<br>API声明：[index: number]: number;<br>差异内容：[index: number]: number;|arkts/@arkts.collections.d.ets|
|新增API|NA|类名：global；<br>API声明：declare namespace lang<br>差异内容：declare namespace lang|arkts/@arkts.lang.d.ets|
|新增API|NA|类名：lang；<br>API声明：interface ISendable<br>差异内容：interface ISendable|arkts/@arkts.lang.d.ets|
|新增API|NA|类名：global；<br>API声明：type Rounding = 0 \| 1 \| 2 \| 3 \| 4 \| 5 \| 6 \| 7 \| 8;<br>差异内容：type Rounding = 0 \| 1 \| 2 \| 3 \| 4 \| 5 \| 6 \| 7 \| 8;|arkts/@arkts.math.Decimal.d.ets|
|新增API|NA|类名：global；<br>API声明：type Modulo = Rounding \| 9;<br>差异内容：type Modulo = Rounding \| 9;|arkts/@arkts.math.Decimal.d.ets|
|新增API|NA|类名：global；<br>API声明：type Value = string \| number \| Decimal;<br>差异内容：type Value = string \| number \| Decimal;|arkts/@arkts.math.Decimal.d.ets|
|新增API|NA|类名：global；<br>API声明：interface DecimalConfig<br>差异内容：interface DecimalConfig|arkts/@arkts.math.Decimal.d.ets|
|新增API|NA|类名：DecimalConfig；<br>API声明：precision?: number;<br>差异内容：precision?: number;|arkts/@arkts.math.Decimal.d.ets|
|新增API|NA|类名：DecimalConfig；<br>API声明：rounding?: Rounding;<br>差异内容：rounding?: Rounding;|arkts/@arkts.math.Decimal.d.ets|
|新增API|NA|类名：DecimalConfig；<br>API声明：toExpNeg?: number;<br>差异内容：toExpNeg?: number;|arkts/@arkts.math.Decimal.d.ets|
|新增API|NA|类名：DecimalConfig；<br>API声明：toExpPos?: number;<br>差异内容：toExpPos?: number;|arkts/@arkts.math.Decimal.d.ets|
|新增API|NA|类名：DecimalConfig；<br>API声明：minE?: number;<br>差异内容：minE?: number;|arkts/@arkts.math.Decimal.d.ets|
|新增API|NA|类名：DecimalConfig；<br>API声明：maxE?: number;<br>差异内容：maxE?: number;|arkts/@arkts.math.Decimal.d.ets|
|新增API|NA|类名：DecimalConfig；<br>API声明：crypto?: boolean;<br>差异内容：crypto?: boolean;|arkts/@arkts.math.Decimal.d.ets|
|新增API|NA|类名：DecimalConfig；<br>API声明：modulo?: Modulo;<br>差异内容：modulo?: Modulo;|arkts/@arkts.math.Decimal.d.ets|
|新增API|NA|类名：DecimalConfig；<br>API声明：defaults?: boolean;<br>差异内容：defaults?: boolean;|arkts/@arkts.math.Decimal.d.ets|
|新增API|NA|类名：global；<br>API声明：declare class Decimal<br>差异内容：declare class Decimal|arkts/@arkts.math.Decimal.d.ets|
|新增API|NA|类名：Decimal；<br>API声明：readonly d: number[];<br>差异内容：readonly d: number[];|arkts/@arkts.math.Decimal.d.ets|
|新增API|NA|类名：Decimal；<br>API声明：readonly e: number;<br>差异内容：readonly e: number;|arkts/@arkts.math.Decimal.d.ets|
|新增API|NA|类名：Decimal；<br>API声明：readonly s: number;<br>差异内容：readonly s: number;|arkts/@arkts.math.Decimal.d.ets|
|新增API|NA|类名：Decimal；<br>API声明：abs(): Decimal;<br>差异内容：abs(): Decimal;|arkts/@arkts.math.Decimal.d.ets|
|新增API|NA|类名：Decimal；<br>API声明：static abs(n: Value): Decimal;<br>差异内容：static abs(n: Value): Decimal;|arkts/@arkts.math.Decimal.d.ets|
|新增API|NA|类名：Decimal；<br>API声明：floor(): Decimal;<br>差异内容：floor(): Decimal;|arkts/@arkts.math.Decimal.d.ets|
|新增API|NA|类名：Decimal；<br>API声明：static floor(n: Value): Decimal;<br>差异内容：static floor(n: Value): Decimal;|arkts/@arkts.math.Decimal.d.ets|
|新增API|NA|类名：Decimal；<br>API声明：ceil(): Decimal;<br>差异内容：ceil(): Decimal;|arkts/@arkts.math.Decimal.d.ets|
|新增API|NA|类名：Decimal；<br>API声明：static ceil(n: Value): Decimal;<br>差异内容：static ceil(n: Value): Decimal;|arkts/@arkts.math.Decimal.d.ets|
|新增API|NA|类名：Decimal；<br>API声明：trunc(): Decimal;<br>差异内容：trunc(): Decimal;|arkts/@arkts.math.Decimal.d.ets|
|新增API|NA|类名：Decimal；<br>API声明：static trunc(n: Value): Decimal;<br>差异内容：static trunc(n: Value): Decimal;|arkts/@arkts.math.Decimal.d.ets|
|新增API|NA|类名：Decimal；<br>API声明：clamp(min: Value, max: Value): Decimal;<br>差异内容：clamp(min: Value, max: Value): Decimal;|arkts/@arkts.math.Decimal.d.ets|
|新增API|NA|类名：Decimal；<br>API声明：static clamp(n: Value, min: Value, max: Value): Decimal;<br>差异内容：static clamp(n: Value, min: Value, max: Value): Decimal;|arkts/@arkts.math.Decimal.d.ets|
|新增API|NA|类名：Decimal；<br>API声明：add(n: Value): Decimal;<br>差异内容：add(n: Value): Decimal;|arkts/@arkts.math.Decimal.d.ets|
|新增API|NA|类名：Decimal；<br>API声明：static add(x: Value, y: Value): Decimal;<br>差异内容：static add(x: Value, y: Value): Decimal;|arkts/@arkts.math.Decimal.d.ets|
|新增API|NA|类名：Decimal；<br>API声明：sub(n: Value): Decimal;<br>差异内容：sub(n: Value): Decimal;|arkts/@arkts.math.Decimal.d.ets|
|新增API|NA|类名：Decimal；<br>API声明：static sub(x: Value, y: Value): Decimal;<br>差异内容：static sub(x: Value, y: Value): Decimal;|arkts/@arkts.math.Decimal.d.ets|
|新增API|NA|类名：Decimal；<br>API声明：mul(n: Value): Decimal;<br>差异内容：mul(n: Value): Decimal;|arkts/@arkts.math.Decimal.d.ets|
|新增API|NA|类名：Decimal；<br>API声明：static mul(x: Value, y: Value): Decimal;<br>差异内容：static mul(x: Value, y: Value): Decimal;|arkts/@arkts.math.Decimal.d.ets|
|新增API|NA|类名：Decimal；<br>API声明：div(n: Value): Decimal;<br>差异内容：div(n: Value): Decimal;|arkts/@arkts.math.Decimal.d.ets|
|新增API|NA|类名：Decimal；<br>API声明：static div(x: Value, y: Value): Decimal;<br>差异内容：static div(x: Value, y: Value): Decimal;|arkts/@arkts.math.Decimal.d.ets|
|新增API|NA|类名：Decimal；<br>API声明：mod(n: Value): Decimal;<br>差异内容：mod(n: Value): Decimal;|arkts/@arkts.math.Decimal.d.ets|
|新增API|NA|类名：Decimal；<br>API声明：static mod(x: Value, y: Value): Decimal;<br>差异内容：static mod(x: Value, y: Value): Decimal;|arkts/@arkts.math.Decimal.d.ets|
|新增API|NA|类名：Decimal；<br>API声明：sqrt(): Decimal;<br>差异内容：sqrt(): Decimal;|arkts/@arkts.math.Decimal.d.ets|
|新增API|NA|类名：Decimal；<br>API声明：static sqrt(n: Value): Decimal;<br>差异内容：static sqrt(n: Value): Decimal;|arkts/@arkts.math.Decimal.d.ets|
|新增API|NA|类名：Decimal；<br>API声明：cbrt(): Decimal;<br>差异内容：cbrt(): Decimal;|arkts/@arkts.math.Decimal.d.ets|
|新增API|NA|类名：Decimal；<br>API声明：static cbrt(n: Value): Decimal;<br>差异内容：static cbrt(n: Value): Decimal;|arkts/@arkts.math.Decimal.d.ets|
|新增API|NA|类名：Decimal；<br>API声明：pow(n: Value): Decimal;<br>差异内容：pow(n: Value): Decimal;|arkts/@arkts.math.Decimal.d.ets|
|新增API|NA|类名：Decimal；<br>API声明：static pow(base: Value, exponent: Value): Decimal;<br>差异内容：static pow(base: Value, exponent: Value): Decimal;|arkts/@arkts.math.Decimal.d.ets|
|新增API|NA|类名：Decimal；<br>API声明：exp(): Decimal;<br>差异内容：exp(): Decimal;|arkts/@arkts.math.Decimal.d.ets|
|新增API|NA|类名：Decimal；<br>API声明：static exp(n: Value): Decimal;<br>差异内容：static exp(n: Value): Decimal;|arkts/@arkts.math.Decimal.d.ets|
|新增API|NA|类名：Decimal；<br>API声明：log(n: Value): Decimal;<br>差异内容：log(n: Value): Decimal;|arkts/@arkts.math.Decimal.d.ets|
|新增API|NA|类名：Decimal；<br>API声明：static log(n: Value, base: Value): Decimal;<br>差异内容：static log(n: Value, base: Value): Decimal;|arkts/@arkts.math.Decimal.d.ets|
|新增API|NA|类名：Decimal；<br>API声明：ln(): Decimal;<br>差异内容：ln(): Decimal;|arkts/@arkts.math.Decimal.d.ets|
|新增API|NA|类名：Decimal；<br>API声明：static ln(n: Value): Decimal;<br>差异内容：static ln(n: Value): Decimal;|arkts/@arkts.math.Decimal.d.ets|
|新增API|NA|类名：Decimal；<br>API声明：cos(): Decimal;<br>差异内容：cos(): Decimal;|arkts/@arkts.math.Decimal.d.ets|
|新增API|NA|类名：Decimal；<br>API声明：static cos(n: Value): Decimal;<br>差异内容：static cos(n: Value): Decimal;|arkts/@arkts.math.Decimal.d.ets|
|新增API|NA|类名：Decimal；<br>API声明：sin(): Decimal;<br>差异内容：sin(): Decimal;|arkts/@arkts.math.Decimal.d.ets|
|新增API|NA|类名：Decimal；<br>API声明：static sin(n: Value): Decimal;<br>差异内容：static sin(n: Value): Decimal;|arkts/@arkts.math.Decimal.d.ets|
|新增API|NA|类名：Decimal；<br>API声明：tan(): Decimal;<br>差异内容：tan(): Decimal;|arkts/@arkts.math.Decimal.d.ets|
|新增API|NA|类名：Decimal；<br>API声明：static tan(n: Value): Decimal;<br>差异内容：static tan(n: Value): Decimal;|arkts/@arkts.math.Decimal.d.ets|
|新增API|NA|类名：Decimal；<br>API声明：cosh(): Decimal;<br>差异内容：cosh(): Decimal;|arkts/@arkts.math.Decimal.d.ets|
|新增API|NA|类名：Decimal；<br>API声明：static cosh(n: Value): Decimal;<br>差异内容：static cosh(n: Value): Decimal;|arkts/@arkts.math.Decimal.d.ets|
|新增API|NA|类名：Decimal；<br>API声明：sinh(): Decimal;<br>差异内容：sinh(): Decimal;|arkts/@arkts.math.Decimal.d.ets|
|新增API|NA|类名：Decimal；<br>API声明：static sinh(n: Value): Decimal;<br>差异内容：static sinh(n: Value): Decimal;|arkts/@arkts.math.Decimal.d.ets|
|新增API|NA|类名：Decimal；<br>API声明：tanh(): Decimal;<br>差异内容：tanh(): Decimal;|arkts/@arkts.math.Decimal.d.ets|
|新增API|NA|类名：Decimal；<br>API声明：static tanh(n: Value): Decimal;<br>差异内容：static tanh(n: Value): Decimal;|arkts/@arkts.math.Decimal.d.ets|
|新增API|NA|类名：Decimal；<br>API声明：acos(): Decimal;<br>差异内容：acos(): Decimal;|arkts/@arkts.math.Decimal.d.ets|
|新增API|NA|类名：Decimal；<br>API声明：static acos(n: Value): Decimal;<br>差异内容：static acos(n: Value): Decimal;|arkts/@arkts.math.Decimal.d.ets|
|新增API|NA|类名：Decimal；<br>API声明：asin(): Decimal;<br>差异内容：asin(): Decimal;|arkts/@arkts.math.Decimal.d.ets|
|新增API|NA|类名：Decimal；<br>API声明：static asin(n: Value): Decimal;<br>差异内容：static asin(n: Value): Decimal;|arkts/@arkts.math.Decimal.d.ets|
|新增API|NA|类名：Decimal；<br>API声明：atan(): Decimal;<br>差异内容：atan(): Decimal;|arkts/@arkts.math.Decimal.d.ets|
|新增API|NA|类名：Decimal；<br>API声明：static atan(n: Value): Decimal;<br>差异内容：static atan(n: Value): Decimal;|arkts/@arkts.math.Decimal.d.ets|
|新增API|NA|类名：Decimal；<br>API声明：acosh(): Decimal;<br>差异内容：acosh(): Decimal;|arkts/@arkts.math.Decimal.d.ets|
|新增API|NA|类名：Decimal；<br>API声明：static acosh(n: Value): Decimal;<br>差异内容：static acosh(n: Value): Decimal;|arkts/@arkts.math.Decimal.d.ets|
|新增API|NA|类名：Decimal；<br>API声明：asinh(): Decimal;<br>差异内容：asinh(): Decimal;|arkts/@arkts.math.Decimal.d.ets|
|新增API|NA|类名：Decimal；<br>API声明：static asinh(n: Value): Decimal;<br>差异内容：static asinh(n: Value): Decimal;|arkts/@arkts.math.Decimal.d.ets|
|新增API|NA|类名：Decimal；<br>API声明：atanh(): Decimal;<br>差异内容：atanh(): Decimal;|arkts/@arkts.math.Decimal.d.ets|
|新增API|NA|类名：Decimal；<br>API声明：static atanh(n: Value): Decimal;<br>差异内容：static atanh(n: Value): Decimal;|arkts/@arkts.math.Decimal.d.ets|
|新增API|NA|类名：Decimal；<br>API声明：comparedTo(n: Value): number;<br>差异内容：comparedTo(n: Value): number;|arkts/@arkts.math.Decimal.d.ets|
|新增API|NA|类名：Decimal；<br>API声明：equals(n: Value): boolean;<br>差异内容：equals(n: Value): boolean;|arkts/@arkts.math.Decimal.d.ets|
|新增API|NA|类名：Decimal；<br>API声明：greaterThan(n: Value): boolean;<br>差异内容：greaterThan(n: Value): boolean;|arkts/@arkts.math.Decimal.d.ets|
|新增API|NA|类名：Decimal；<br>API声明：greaterThanOrEqualTo(n: Value): boolean;<br>差异内容：greaterThanOrEqualTo(n: Value): boolean;|arkts/@arkts.math.Decimal.d.ets|
|新增API|NA|类名：Decimal；<br>API声明：lessThan(n: Value): boolean;<br>差异内容：lessThan(n: Value): boolean;|arkts/@arkts.math.Decimal.d.ets|
|新增API|NA|类名：Decimal；<br>API声明：lessThanOrEqualTo(n: Value): boolean;<br>差异内容：lessThanOrEqualTo(n: Value): boolean;|arkts/@arkts.math.Decimal.d.ets|
|新增API|NA|类名：Decimal；<br>API声明：isFinite(): boolean;<br>差异内容：isFinite(): boolean;|arkts/@arkts.math.Decimal.d.ets|
|新增API|NA|类名：Decimal；<br>API声明：isInteger(): boolean;<br>差异内容：isInteger(): boolean;|arkts/@arkts.math.Decimal.d.ets|
|新增API|NA|类名：Decimal；<br>API声明：isNaN(): boolean;<br>差异内容：isNaN(): boolean;|arkts/@arkts.math.Decimal.d.ets|
|新增API|NA|类名：Decimal；<br>API声明：isNegative(): boolean;<br>差异内容：isNegative(): boolean;|arkts/@arkts.math.Decimal.d.ets|
|新增API|NA|类名：Decimal；<br>API声明：isPositive(): boolean;<br>差异内容：isPositive(): boolean;|arkts/@arkts.math.Decimal.d.ets|
|新增API|NA|类名：Decimal；<br>API声明：isZero(): boolean;<br>差异内容：isZero(): boolean;|arkts/@arkts.math.Decimal.d.ets|
|新增API|NA|类名：Decimal；<br>API声明：dividedToIntegerBy(n: Value): Decimal;<br>差异内容：dividedToIntegerBy(n: Value): Decimal;|arkts/@arkts.math.Decimal.d.ets|
|新增API|NA|类名：Decimal；<br>API声明：negate(): Decimal;<br>差异内容：negate(): Decimal;|arkts/@arkts.math.Decimal.d.ets|
|新增API|NA|类名：Decimal；<br>API声明：toBinary(): string;<br>差异内容：toBinary(): string;|arkts/@arkts.math.Decimal.d.ets|
|新增API|NA|类名：Decimal；<br>API声明：toBinary(significantDigits: number): string;<br>差异内容：toBinary(significantDigits: number): string;|arkts/@arkts.math.Decimal.d.ets|
|新增API|NA|类名：Decimal；<br>API声明：toBinary(significantDigits: number, rounding: Rounding): string;<br>差异内容：toBinary(significantDigits: number, rounding: Rounding): string;|arkts/@arkts.math.Decimal.d.ets|
|新增API|NA|类名：Decimal；<br>API声明：toOctal(): string;<br>差异内容：toOctal(): string;|arkts/@arkts.math.Decimal.d.ets|
|新增API|NA|类名：Decimal；<br>API声明：toOctal(significantDigits: number): string;<br>差异内容：toOctal(significantDigits: number): string;|arkts/@arkts.math.Decimal.d.ets|
|新增API|NA|类名：Decimal；<br>API声明：toOctal(significantDigits: number, rounding: Rounding): string;<br>差异内容：toOctal(significantDigits: number, rounding: Rounding): string;|arkts/@arkts.math.Decimal.d.ets|
|新增API|NA|类名：Decimal；<br>API声明：toHexadecimal(): string;<br>差异内容：toHexadecimal(): string;|arkts/@arkts.math.Decimal.d.ets|
|新增API|NA|类名：Decimal；<br>API声明：toHexadecimal(significantDigits: number): string;<br>差异内容：toHexadecimal(significantDigits: number): string;|arkts/@arkts.math.Decimal.d.ets|
|新增API|NA|类名：Decimal；<br>API声明：toHexadecimal(significantDigits: number, rounding: Rounding): string;<br>差异内容：toHexadecimal(significantDigits: number, rounding: Rounding): string;|arkts/@arkts.math.Decimal.d.ets|
|新增API|NA|类名：Decimal；<br>API声明：toDecimalPlaces(): Decimal;<br>差异内容：toDecimalPlaces(): Decimal;|arkts/@arkts.math.Decimal.d.ets|
|新增API|NA|类名：Decimal；<br>API声明：toDecimalPlaces(decimalPlaces: number): Decimal;<br>差异内容：toDecimalPlaces(decimalPlaces: number): Decimal;|arkts/@arkts.math.Decimal.d.ets|
|新增API|NA|类名：Decimal；<br>API声明：toDecimalPlaces(decimalPlaces: number, rounding: Rounding): Decimal;<br>差异内容：toDecimalPlaces(decimalPlaces: number, rounding: Rounding): Decimal;|arkts/@arkts.math.Decimal.d.ets|
|新增API|NA|类名：Decimal；<br>API声明：toExponential(): string;<br>差异内容：toExponential(): string;|arkts/@arkts.math.Decimal.d.ets|
|新增API|NA|类名：Decimal；<br>API声明：toExponential(decimalPlaces: number): string;<br>差异内容：toExponential(decimalPlaces: number): string;|arkts/@arkts.math.Decimal.d.ets|
|新增API|NA|类名：Decimal；<br>API声明：toExponential(decimalPlaces: number, rounding: Rounding): string;<br>差异内容：toExponential(decimalPlaces: number, rounding: Rounding): string;|arkts/@arkts.math.Decimal.d.ets|
|新增API|NA|类名：Decimal；<br>API声明：toFixed(): string;<br>差异内容：toFixed(): string;|arkts/@arkts.math.Decimal.d.ets|
|新增API|NA|类名：Decimal；<br>API声明：toFixed(decimalPlaces: number): string;<br>差异内容：toFixed(decimalPlaces: number): string;|arkts/@arkts.math.Decimal.d.ets|
|新增API|NA|类名：Decimal；<br>API声明：toFixed(decimalPlaces: number, rounding: Rounding): string;<br>差异内容：toFixed(decimalPlaces: number, rounding: Rounding): string;|arkts/@arkts.math.Decimal.d.ets|
|新增API|NA|类名：Decimal；<br>API声明：toFraction(): Decimal[];<br>差异内容：toFraction(): Decimal[];|arkts/@arkts.math.Decimal.d.ets|
|新增API|NA|类名：Decimal；<br>API声明：toFraction(maxDenominator: Value): Decimal[];<br>差异内容：toFraction(maxDenominator: Value): Decimal[];|arkts/@arkts.math.Decimal.d.ets|
|新增API|NA|类名：Decimal；<br>API声明：toNearest(n: Value): Decimal;<br>差异内容：toNearest(n: Value): Decimal;|arkts/@arkts.math.Decimal.d.ets|
|新增API|NA|类名：Decimal；<br>API声明：toNearest(n: Value, rounding: Rounding): Decimal;<br>差异内容：toNearest(n: Value, rounding: Rounding): Decimal;|arkts/@arkts.math.Decimal.d.ets|
|新增API|NA|类名：Decimal；<br>API声明：toPrecision(): string;<br>差异内容：toPrecision(): string;|arkts/@arkts.math.Decimal.d.ets|
|新增API|NA|类名：Decimal；<br>API声明：toPrecision(significantDigits: number): string;<br>差异内容：toPrecision(significantDigits: number): string;|arkts/@arkts.math.Decimal.d.ets|
|新增API|NA|类名：Decimal；<br>API声明：toPrecision(significantDigits: number, rounding: Rounding): string;<br>差异内容：toPrecision(significantDigits: number, rounding: Rounding): string;|arkts/@arkts.math.Decimal.d.ets|
|新增API|NA|类名：Decimal；<br>API声明：toSignificantDigits(): Decimal;<br>差异内容：toSignificantDigits(): Decimal;|arkts/@arkts.math.Decimal.d.ets|
|新增API|NA|类名：Decimal；<br>API声明：toSignificantDigits(significantDigits: number): Decimal;<br>差异内容：toSignificantDigits(significantDigits: number): Decimal;|arkts/@arkts.math.Decimal.d.ets|
|新增API|NA|类名：Decimal；<br>API声明：toSignificantDigits(significantDigits: number, rounding: Rounding): Decimal;<br>差异内容：toSignificantDigits(significantDigits: number, rounding: Rounding): Decimal;|arkts/@arkts.math.Decimal.d.ets|
|新增API|NA|类名：Decimal；<br>API声明：toNumber(): number;<br>差异内容：toNumber(): number;|arkts/@arkts.math.Decimal.d.ets|
|新增API|NA|类名：Decimal；<br>API声明：toString(): string;<br>差异内容：toString(): string;|arkts/@arkts.math.Decimal.d.ets|
|新增API|NA|类名：Decimal；<br>API声明：valueOf(): string;<br>差异内容：valueOf(): string;|arkts/@arkts.math.Decimal.d.ets|
|新增API|NA|类名：Decimal；<br>API声明：decimalPlaces(): number;<br>差异内容：decimalPlaces(): number;|arkts/@arkts.math.Decimal.d.ets|
|新增API|NA|类名：Decimal；<br>API声明：precision(): number;<br>差异内容：precision(): number;|arkts/@arkts.math.Decimal.d.ets|
|新增API|NA|类名：Decimal；<br>API声明：precision(includeZeros: boolean \| number): number;<br>差异内容：precision(includeZeros: boolean \| number): number;|arkts/@arkts.math.Decimal.d.ets|
|新增API|NA|类名：Decimal；<br>API声明：static sum(...n: Value[]): Decimal;<br>差异内容：static sum(...n: Value[]): Decimal;|arkts/@arkts.math.Decimal.d.ets|
|新增API|NA|类名：Decimal；<br>API声明：static log2(n: Value): Decimal;<br>差异内容：static log2(n: Value): Decimal;|arkts/@arkts.math.Decimal.d.ets|
|新增API|NA|类名：Decimal；<br>API声明：static log10(n: Value): Decimal;<br>差异内容：static log10(n: Value): Decimal;|arkts/@arkts.math.Decimal.d.ets|
|新增API|NA|类名：Decimal；<br>API声明：static atan2(y: Value, x: Value): Decimal;<br>差异内容：static atan2(y: Value, x: Value): Decimal;|arkts/@arkts.math.Decimal.d.ets|
|新增API|NA|类名：Decimal；<br>API声明：static hypot(...n: Value[]): Decimal;<br>差异内容：static hypot(...n: Value[]): Decimal;|arkts/@arkts.math.Decimal.d.ets|
|新增API|NA|类名：Decimal；<br>API声明：static max(...n: Value[]): Decimal;<br>差异内容：static max(...n: Value[]): Decimal;|arkts/@arkts.math.Decimal.d.ets|
|新增API|NA|类名：Decimal；<br>API声明：static min(...n: Value[]): Decimal;<br>差异内容：static min(...n: Value[]): Decimal;|arkts/@arkts.math.Decimal.d.ets|
|新增API|NA|类名：Decimal；<br>API声明：static random(): Decimal;<br>差异内容：static random(): Decimal;|arkts/@arkts.math.Decimal.d.ets|
|新增API|NA|类名：Decimal；<br>API声明：static random(significantDigits: number): Decimal;<br>差异内容：static random(significantDigits: number): Decimal;|arkts/@arkts.math.Decimal.d.ets|
|新增API|NA|类名：Decimal；<br>API声明：static sign(n: Value): number;<br>差异内容：static sign(n: Value): number;|arkts/@arkts.math.Decimal.d.ets|
|新增API|NA|类名：Decimal；<br>API声明：static round(n: Value): Decimal;<br>差异内容：static round(n: Value): Decimal;|arkts/@arkts.math.Decimal.d.ets|
|新增API|NA|类名：Decimal；<br>API声明：static set(config: DecimalConfig): void;<br>差异内容：static set(config: DecimalConfig): void;|arkts/@arkts.math.Decimal.d.ets|
|新增API|NA|类名：Decimal；<br>API声明：static readonly ROUND_UP : 0;<br>差异内容：static readonly ROUND_UP : 0;|arkts/@arkts.math.Decimal.d.ets|
|新增API|NA|类名：Decimal；<br>API声明：static readonly ROUND_DOWN : 1;<br>差异内容：static readonly ROUND_DOWN : 1;|arkts/@arkts.math.Decimal.d.ets|
|新增API|NA|类名：Decimal；<br>API声明：static readonly ROUND_CEILING : 2;<br>差异内容：static readonly ROUND_CEILING : 2;|arkts/@arkts.math.Decimal.d.ets|
|新增API|NA|类名：Decimal；<br>API声明：static readonly ROUND_FLOOR : 3;<br>差异内容：static readonly ROUND_FLOOR : 3;|arkts/@arkts.math.Decimal.d.ets|
|新增API|NA|类名：Decimal；<br>API声明：static readonly ROUND_HALF_UP : 4;<br>差异内容：static readonly ROUND_HALF_UP : 4;|arkts/@arkts.math.Decimal.d.ets|
|新增API|NA|类名：Decimal；<br>API声明：static readonly ROUND_HALF_DOWN : 5;<br>差异内容：static readonly ROUND_HALF_DOWN : 5;|arkts/@arkts.math.Decimal.d.ets|
|新增API|NA|类名：Decimal；<br>API声明：static readonly ROUND_HALF_EVEN : 6;<br>差异内容：static readonly ROUND_HALF_EVEN : 6;|arkts/@arkts.math.Decimal.d.ets|
|新增API|NA|类名：Decimal；<br>API声明：static readonly ROUND_HALF_CEILING : 7;<br>差异内容：static readonly ROUND_HALF_CEILING : 7;|arkts/@arkts.math.Decimal.d.ets|
|新增API|NA|类名：Decimal；<br>API声明：static readonly ROUND_HALF_FLOOR : 8;<br>差异内容：static readonly ROUND_HALF_FLOOR : 8;|arkts/@arkts.math.Decimal.d.ets|
|新增API|NA|类名：Decimal；<br>API声明：static readonly EUCLIDEAN : 9;<br>差异内容：static readonly EUCLIDEAN : 9;|arkts/@arkts.math.Decimal.d.ets|
|新增API|NA|类名：global；<br>API声明：declare namespace utils<br>差异内容：declare namespace utils|arkts/@arkts.utils.d.ets|
|新增API|NA|类名：utils；<br>API声明：namespace locks<br>差异内容：namespace locks|arkts/@arkts.utils.d.ets|
|新增API|NA|类名：locks；<br>API声明：type AsyncLockCallback\<T> = () => T \| Promise\<T>;<br>差异内容：type AsyncLockCallback\<T> = () => T \| Promise\<T>;|arkts/@arkts.utils.d.ets|
|新增API|NA|类名：locks；<br>API声明：class AsyncLock<br>差异内容：class AsyncLock|arkts/@arkts.utils.d.ets|
|新增API|NA|类名：AsyncLock；<br>API声明：static request(name: string): AsyncLock;<br>差异内容：static request(name: string): AsyncLock;|arkts/@arkts.utils.d.ets|
|新增API|NA|类名：AsyncLock；<br>API声明：static query(name: string): AsyncLockState;<br>差异内容：static query(name: string): AsyncLockState;|arkts/@arkts.utils.d.ets|
|新增API|NA|类名：AsyncLock；<br>API声明：static queryAll(): AsyncLockState[];<br>差异内容：static queryAll(): AsyncLockState[];|arkts/@arkts.utils.d.ets|
|新增API|NA|类名：AsyncLock；<br>API声明：lockAsync\<T>(callback: AsyncLockCallback\<T>): Promise\<T>;<br>差异内容：lockAsync\<T>(callback: AsyncLockCallback\<T>): Promise\<T>;|arkts/@arkts.utils.d.ets|
|新增API|NA|类名：AsyncLock；<br>API声明：lockAsync\<T>(callback: AsyncLockCallback\<T>, mode: AsyncLockMode): Promise\<T>;<br>差异内容：lockAsync\<T>(callback: AsyncLockCallback\<T>, mode: AsyncLockMode): Promise\<T>;|arkts/@arkts.utils.d.ets|
|新增API|NA|类名：AsyncLock；<br>API声明：lockAsync\<T, U>(callback: AsyncLockCallback\<T>, mode: AsyncLockMode,<br>        options: AsyncLockOptions\<U>): Promise\<T \| U>;<br>差异内容：lockAsync\<T, U>(callback: AsyncLockCallback\<T>, mode: AsyncLockMode,<br>        options: AsyncLockOptions\<U>): Promise\<T \| U>;|arkts/@arkts.utils.d.ets|
|新增API|NA|类名：AsyncLock；<br>API声明：readonly name: string;<br>差异内容：readonly name: string;|arkts/@arkts.utils.d.ets|
|新增API|NA|类名：locks；<br>API声明：enum AsyncLockMode<br>差异内容：enum AsyncLockMode|arkts/@arkts.utils.d.ets|
|新增API|NA|类名：AsyncLockMode；<br>API声明：SHARED = 1<br>差异内容：SHARED = 1|arkts/@arkts.utils.d.ets|
|新增API|NA|类名：AsyncLockMode；<br>API声明：EXCLUSIVE = 2<br>差异内容：EXCLUSIVE = 2|arkts/@arkts.utils.d.ets|
|新增API|NA|类名：locks；<br>API声明：class AsyncLockOptions<br>差异内容：class AsyncLockOptions|arkts/@arkts.utils.d.ets|
|新增API|NA|类名：AsyncLockOptions；<br>API声明：isAvailable: boolean;<br>差异内容：isAvailable: boolean;|arkts/@arkts.utils.d.ets|
|新增API|NA|类名：AsyncLockOptions；<br>API声明：signal: AbortSignal\<T> \| null;<br>差异内容：signal: AbortSignal\<T> \| null;|arkts/@arkts.utils.d.ets|
|新增API|NA|类名：AsyncLockOptions；<br>API声明：timeout: number;<br>差异内容：timeout: number;|arkts/@arkts.utils.d.ets|
|新增API|NA|类名：locks；<br>API声明：class AsyncLockState<br>差异内容：class AsyncLockState|arkts/@arkts.utils.d.ets|
|新增API|NA|类名：AsyncLockState；<br>API声明：held: AsyncLockInfo[];<br>差异内容：held: AsyncLockInfo[];|arkts/@arkts.utils.d.ets|
|新增API|NA|类名：AsyncLockState；<br>API声明：pending: AsyncLockInfo[];<br>差异内容：pending: AsyncLockInfo[];|arkts/@arkts.utils.d.ets|
|新增API|NA|类名：locks；<br>API声明：class AsyncLockInfo<br>差异内容：class AsyncLockInfo|arkts/@arkts.utils.d.ets|
|新增API|NA|类名：AsyncLockInfo；<br>API声明：name: string;<br>差异内容：name: string;|arkts/@arkts.utils.d.ets|
|新增API|NA|类名：AsyncLockInfo；<br>API声明：mode: AsyncLockMode;<br>差异内容：mode: AsyncLockMode;|arkts/@arkts.utils.d.ets|
|新增API|NA|类名：AsyncLockInfo；<br>API声明：contextId: number;<br>差异内容：contextId: number;|arkts/@arkts.utils.d.ets|
|新增API|NA|类名：locks；<br>API声明：class AbortSignal<br>差异内容：class AbortSignal|arkts/@arkts.utils.d.ets|
|新增API|NA|类名：AbortSignal；<br>API声明：aborted: boolean;<br>差异内容：aborted: boolean;|arkts/@arkts.utils.d.ets|
|新增API|NA|类名：AbortSignal；<br>API声明：reason: T<br>差异内容：reason: T|arkts/@arkts.utils.d.ets|
|新增API|NA|类名：utils；<br>API声明：namespace ASON<br>差异内容：namespace ASON|arkts/@arkts.utils.d.ets|
|新增API|NA|类名：ASON；<br>API声明：type ISendable = lang.ISendable;<br>差异内容：type ISendable = lang.ISendable;|arkts/@arkts.utils.d.ets|
|新增API|NA|类名：ASON；<br>API声明：type Transformer = (this: ISendable, key: string,<br>      value: ISendable \| undefined \| null) => ISendable \| undefined \| null<br>差异内容：type Transformer = (this: ISendable, key: string,<br>      value: ISendable \| undefined \| null) => ISendable \| undefined \| null|arkts/@arkts.utils.d.ets|
|新增API|NA|类名：ASON；<br>API声明：function parse(text: string, reviver?: Transformer, options?: ParseOptions): ISendable \| null;<br>差异内容：function parse(text: string, reviver?: Transformer, options?: ParseOptions): ISendable \| null;|arkts/@arkts.utils.d.ets|
|新增API|NA|类名：ASON；<br>API声明：function stringify(value: ISendable \| null \| undefined): string;<br>差异内容：function stringify(value: ISendable \| null \| undefined): string;|arkts/@arkts.utils.d.ets|
|新增API|NA|类名：ASON；<br>API声明：const enum BigIntMode<br>差异内容：const enum BigIntMode|arkts/@arkts.utils.d.ets|
|新增API|NA|类名：BigIntMode；<br>API声明：DEFAULT = 0<br>差异内容：DEFAULT = 0|arkts/@arkts.utils.d.ets|
|新增API|NA|类名：BigIntMode；<br>API声明：PARSE_AS_BIGINT = 1<br>差异内容：PARSE_AS_BIGINT = 1|arkts/@arkts.utils.d.ets|
|新增API|NA|类名：BigIntMode；<br>API声明：ALWAYS_PARSE_AS_BIGINT = 2<br>差异内容：ALWAYS_PARSE_AS_BIGINT = 2|arkts/@arkts.utils.d.ets|
|新增API|NA|类名：ASON；<br>API声明：const enum ParseReturnType<br>差异内容：const enum ParseReturnType|arkts/@arkts.utils.d.ets|
|新增API|NA|类名：ParseReturnType；<br>API声明：OBJECT = 0<br>差异内容：OBJECT = 0|arkts/@arkts.utils.d.ets|
|新增API|NA|类名：ASON；<br>API声明：interface ParseOptions<br>差异内容：interface ParseOptions|arkts/@arkts.utils.d.ets|
|新增API|NA|类名：ParseOptions；<br>API声明：bigIntMode: BigIntMode;<br>差异内容：bigIntMode: BigIntMode;|arkts/@arkts.utils.d.ets|
|新增API|NA|类名：ParseOptions；<br>API声明：parseReturnType: ParseReturnType;<br>差异内容：parseReturnType: ParseReturnType;|arkts/@arkts.utils.d.ets|
|新增API|NA|类名：utils；<br>API声明：function isSendable(value: Object \| null \| undefined): boolean;<br>差异内容：function isSendable(value: Object \| null \| undefined): boolean;|arkts/@arkts.utils.d.ets|
|新增API|NA|类名：Priority；<br>API声明：IDLE = 3<br>差异内容：IDLE = 3|api/@ohos.taskpool.d.ts|
|新增API|NA|类名：taskpool；<br>API声明：type CallbackFunction = () => void;<br>差异内容：type CallbackFunction = () => void;|api/@ohos.taskpool.d.ts|
|新增API|NA|类名：taskpool；<br>API声明：type CallbackFunctionWithError = (e: Error) => void;<br>差异内容：type CallbackFunctionWithError = (e: Error) => void;|api/@ohos.taskpool.d.ts|
|新增API|NA|类名：Task；<br>API声明：onEnqueued(callback: CallbackFunction): void;<br>差异内容：onEnqueued(callback: CallbackFunction): void;|api/@ohos.taskpool.d.ts|
|新增API|NA|类名：Task；<br>API声明：onStartExecution(callback: CallbackFunction): void;<br>差异内容：onStartExecution(callback: CallbackFunction): void;|api/@ohos.taskpool.d.ts|
|新增API|NA|类名：Task；<br>API声明：onExecutionFailed(callback: CallbackFunctionWithError): void;<br>差异内容：onExecutionFailed(callback: CallbackFunctionWithError): void;|api/@ohos.taskpool.d.ts|
|新增API|NA|类名：Task；<br>API声明：onExecutionSucceeded(callback: CallbackFunction): void;<br>差异内容：onExecutionSucceeded(callback: CallbackFunction): void;|api/@ohos.taskpool.d.ts|
|新增API|NA|类名：Task；<br>API声明：isDone(): boolean;<br>差异内容：isDone(): boolean;|api/@ohos.taskpool.d.ts|
|新增API|NA|类名：taskpool；<br>API声明：class LongTask<br>差异内容：class LongTask|api/@ohos.taskpool.d.ts|
|新增API|NA|类名：TaskInfo；<br>API声明：name: string;<br>差异内容：name: string;|api/@ohos.taskpool.d.ts|
|新增API|NA|类名：taskpool；<br>API声明：function executePeriodically(period: number, task: Task, priority?: Priority): void;<br>差异内容：function executePeriodically(period: number, task: Task, priority?: Priority): void;|api/@ohos.taskpool.d.ts|
|新增API|NA|类名：taskpool；<br>API声明：function terminateTask(longTask: LongTask): void;<br>差异内容：function terminateTask(longTask: LongTask): void;|api/@ohos.taskpool.d.ts|
|新增API|NA|类名：taskpool；<br>API声明：function isConcurrent(func: Function): boolean;<br>差异内容：function isConcurrent(func: Function): boolean;|api/@ohos.taskpool.d.ts|
|新增API|NA|类名：ArrayList；<br>API声明：[index: number]: T;<br>差异内容：[index: number]: T;|api/@ohos.util.ArrayList.d.ts|
|新增API|NA|类名：util；<br>API声明：function getHash(object: object): number;<br>差异内容：function getHash(object: object): number;|api/@ohos.util.d.ts|
|新增API|NA|类名：util；<br>API声明：interface DecodeToStringOptions<br>差异内容：interface DecodeToStringOptions|api/@ohos.util.d.ts|
|新增API|NA|类名：DecodeToStringOptions；<br>API声明：stream?: boolean;<br>差异内容：stream?: boolean;|api/@ohos.util.d.ts|
|新增API|NA|类名：TextDecoder；<br>API声明：decodeToString(input: Uint8Array, options?: DecodeToStringOptions): string;<br>差异内容：decodeToString(input: Uint8Array, options?: DecodeToStringOptions): string;|api/@ohos.util.d.ts|
|新增API|NA|类名：TextEncoder；<br>API声明：static create(encoding?: string): TextEncoder;<br>差异内容：static create(encoding?: string): TextEncoder;|api/@ohos.util.d.ts|
|新增API|NA|类名：Type；<br>API声明：BASIC_URL_SAFE<br>差异内容：BASIC_URL_SAFE|api/@ohos.util.d.ts|
|新增API|NA|类名：Type；<br>API声明：MIME_URL_SAFE<br>差异内容：MIME_URL_SAFE|api/@ohos.util.d.ts|
|新增API|NA|类名：util；<br>API声明：class StringDecoder<br>差异内容：class StringDecoder|api/@ohos.util.d.ts|
|新增API|NA|类名：StringDecoder；<br>API声明：write(chunk: string \| Uint8Array): string;<br>差异内容：write(chunk: string \| Uint8Array): string;|api/@ohos.util.d.ts|
|新增API|NA|类名：StringDecoder；<br>API声明：end(chunk?: string \| Uint8Array): string;<br>差异内容：end(chunk?: string \| Uint8Array): string;|api/@ohos.util.d.ts|
|新增API|NA|类名：ThreadWorkerGlobalScope；<br>API声明：postMessageWithSharedSendable(message: Object, transfer?: ArrayBuffer[]): void;<br>差异内容：postMessageWithSharedSendable(message: Object, transfer?: ArrayBuffer[]): void;|api/@ohos.worker.d.ts|
|新增API|NA|类名：ThreadWorker；<br>API声明：postMessageWithSharedSendable(message: Object, transfer?: ArrayBuffer[]): void;<br>差异内容：postMessageWithSharedSendable(message: Object, transfer?: ArrayBuffer[]): void;|api/@ohos.worker.d.ts|
|新增API|NA|类名：URI；<br>API声明：getQueryValue(key: string): string;<br>差异内容：getQueryValue(key: string): string;|api/@ohos.uri.d.ts|
|新增API|NA|类名：URI；<br>API声明：addQueryValue(key: string, value: string): URI;<br>差异内容：addQueryValue(key: string, value: string): URI;|api/@ohos.uri.d.ts|
|新增API|NA|类名：URI；<br>API声明：getQueryNames(): string[];<br>差异内容：getQueryNames(): string[];|api/@ohos.uri.d.ts|
|新增API|NA|类名：URI；<br>API声明：getQueryValues(key: string): string[];<br>差异内容：getQueryValues(key: string): string[];|api/@ohos.uri.d.ts|
|新增API|NA|类名：URI；<br>API声明：getBooleanQueryValue(key: string, defaultValue: boolean): boolean;<br>差异内容：getBooleanQueryValue(key: string, defaultValue: boolean): boolean;|api/@ohos.uri.d.ts|
|新增API|NA|类名：URI；<br>API声明：clearQuery(): URI;<br>差异内容：clearQuery(): URI;|api/@ohos.uri.d.ts|
|新增API|NA|类名：URI；<br>API声明：getLastSegment(): string;<br>差异内容：getLastSegment(): string;|api/@ohos.uri.d.ts|
|新增API|NA|类名：URI；<br>API声明：getSegment(): string[];<br>差异内容：getSegment(): string[];|api/@ohos.uri.d.ts|
|新增API|NA|类名：URI；<br>API声明：addSegment(pathSegment: string): URI;<br>差异内容：addSegment(pathSegment: string): URI;|api/@ohos.uri.d.ts|
|新增API|NA|类名：URI；<br>API声明：addEncodedSegment(pathSegment: string): URI;<br>差异内容：addEncodedSegment(pathSegment: string): URI;|api/@ohos.uri.d.ts|
|新增API|NA|类名：URI；<br>API声明：checkHierarchical(): boolean;<br>差异内容：checkHierarchical(): boolean;|api/@ohos.uri.d.ts|
|新增API|NA|类名：URI；<br>API声明：checkOpaque(): boolean;<br>差异内容：checkOpaque(): boolean;|api/@ohos.uri.d.ts|
|新增API|NA|类名：URI；<br>API声明：checkRelative(): boolean;<br>差异内容：checkRelative(): boolean;|api/@ohos.uri.d.ts|
|新增API|NA|类名：URI；<br>API声明：static createFromParts(scheme: string, ssp: string, fragment: string): URI;<br>差异内容：static createFromParts(scheme: string, ssp: string, fragment: string): URI;|api/@ohos.uri.d.ts|
|新增API|NA|类名：URI；<br>API声明：encodedUserInfo: string;<br>差异内容：encodedUserInfo: string;|api/@ohos.uri.d.ts|
|新增API|NA|类名：URI；<br>API声明：encodedPath: string;<br>差异内容：encodedPath: string;|api/@ohos.uri.d.ts|
|新增API|NA|类名：URI；<br>API声明：encodedQuery: string;<br>差异内容：encodedQuery: string;|api/@ohos.uri.d.ts|
|新增API|NA|类名：URI；<br>API声明：encodedFragment: string;<br>差异内容：encodedFragment: string;|api/@ohos.uri.d.ts|
|新增API|NA|类名：URI；<br>API声明：encodedAuthority: string;<br>差异内容：encodedAuthority: string;|api/@ohos.uri.d.ts|
|新增API|NA|类名：URI；<br>API声明：encodedSSP: string;<br>差异内容：encodedSSP: string;|api/@ohos.uri.d.ts|
|删除API|类名：worker；<br>API声明：class RestrictedWorker<br>差异内容：class RestrictedWorker|NA|api/@ohos.worker.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\@ohos.util.json.d.ts<br>差异内容：ArkTS|api/@ohos.util.json.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\@ohos.util.stream.d.ts<br>差异内容：ArkTS|api/@ohos.util.stream.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：arkts\@arkts.collections.d.ets<br>差异内容：ArkTS|arkts/@arkts.collections.d.ets|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：arkts\@arkts.lang.d.ets<br>差异内容：ArkTS|arkts/@arkts.lang.d.ets|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：arkts\@arkts.math.Decimal.d.ets<br>差异内容：ArkTS|arkts/@arkts.math.Decimal.d.ets|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：arkts\@arkts.utils.d.ets<br>差异内容：ArkTS|arkts/@arkts.utils.d.ets|
|API从不支持元服务到支持元服务|类名：global；<br>API声明：declare class ArrayList<br>差异内容：NA|类名：global；<br>API声明：declare class ArrayList<br>差异内容：atomicservice|api/@ohos.util.ArrayList.d.ts|
|API从不支持元服务到支持元服务|类名：ArrayList；<br>API声明：length: number;<br>差异内容：NA|类名：ArrayList；<br>API声明：length: number;<br>差异内容：atomicservice|api/@ohos.util.ArrayList.d.ts|
|API从不支持元服务到支持元服务|类名：ArrayList；<br>API声明：add(element: T): boolean;<br>差异内容：NA|类名：ArrayList；<br>API声明：add(element: T): boolean;<br>差异内容：atomicservice|api/@ohos.util.ArrayList.d.ts|
|API从不支持元服务到支持元服务|类名：ArrayList；<br>API声明：insert(element: T, index: number): void;<br>差异内容：NA|类名：ArrayList；<br>API声明：insert(element: T, index: number): void;<br>差异内容：atomicservice|api/@ohos.util.ArrayList.d.ts|
|API从不支持元服务到支持元服务|类名：ArrayList；<br>API声明：has(element: T): boolean;<br>差异内容：NA|类名：ArrayList；<br>API声明：has(element: T): boolean;<br>差异内容：atomicservice|api/@ohos.util.ArrayList.d.ts|
|API从不支持元服务到支持元服务|类名：ArrayList；<br>API声明：getIndexOf(element: T): number;<br>差异内容：NA|类名：ArrayList；<br>API声明：getIndexOf(element: T): number;<br>差异内容：atomicservice|api/@ohos.util.ArrayList.d.ts|
|API从不支持元服务到支持元服务|类名：ArrayList；<br>API声明：removeByIndex(index: number): T;<br>差异内容：NA|类名：ArrayList；<br>API声明：removeByIndex(index: number): T;<br>差异内容：atomicservice|api/@ohos.util.ArrayList.d.ts|
|API从不支持元服务到支持元服务|类名：ArrayList；<br>API声明：remove(element: T): boolean;<br>差异内容：NA|类名：ArrayList；<br>API声明：remove(element: T): boolean;<br>差异内容：atomicservice|api/@ohos.util.ArrayList.d.ts|
|API从不支持元服务到支持元服务|类名：ArrayList；<br>API声明：getLastIndexOf(element: T): number;<br>差异内容：NA|类名：ArrayList；<br>API声明：getLastIndexOf(element: T): number;<br>差异内容：atomicservice|api/@ohos.util.ArrayList.d.ts|
|API从不支持元服务到支持元服务|类名：ArrayList；<br>API声明：removeByRange(fromIndex: number, toIndex: number): void;<br>差异内容：NA|类名：ArrayList；<br>API声明：removeByRange(fromIndex: number, toIndex: number): void;<br>差异内容：atomicservice|api/@ohos.util.ArrayList.d.ts|
|API从不支持元服务到支持元服务|类名：ArrayList；<br>API声明：replaceAllElements(callbackFn: (value: T, index?: number, arrlist?: ArrayList\<T>) => T, thisArg?: Object): void;<br>差异内容：NA|类名：ArrayList；<br>API声明：replaceAllElements(callbackFn: (value: T, index?: number, arrlist?: ArrayList\<T>) => T, thisArg?: Object): void;<br>差异内容：atomicservice|api/@ohos.util.ArrayList.d.ts|
|API从不支持元服务到支持元服务|类名：ArrayList；<br>API声明：forEach(callbackFn: (value: T, index?: number, arrlist?: ArrayList\<T>) => void, thisArg?: Object): void;<br>差异内容：NA|类名：ArrayList；<br>API声明：forEach(callbackFn: (value: T, index?: number, arrlist?: ArrayList\<T>) => void, thisArg?: Object): void;<br>差异内容：atomicservice|api/@ohos.util.ArrayList.d.ts|
|API从不支持元服务到支持元服务|类名：ArrayList；<br>API声明：sort(comparator?: (firstValue: T, secondValue: T) => number): void;<br>差异内容：NA|类名：ArrayList；<br>API声明：sort(comparator?: (firstValue: T, secondValue: T) => number): void;<br>差异内容：atomicservice|api/@ohos.util.ArrayList.d.ts|
|API从不支持元服务到支持元服务|类名：ArrayList；<br>API声明：subArrayList(fromIndex: number, toIndex: number): ArrayList\<T>;<br>差异内容：NA|类名：ArrayList；<br>API声明：subArrayList(fromIndex: number, toIndex: number): ArrayList\<T>;<br>差异内容：atomicservice|api/@ohos.util.ArrayList.d.ts|
|API从不支持元服务到支持元服务|类名：ArrayList；<br>API声明：clear(): void;<br>差异内容：NA|类名：ArrayList；<br>API声明：clear(): void;<br>差异内容：atomicservice|api/@ohos.util.ArrayList.d.ts|
|API从不支持元服务到支持元服务|类名：ArrayList；<br>API声明：clone(): ArrayList\<T>;<br>差异内容：NA|类名：ArrayList；<br>API声明：clone(): ArrayList\<T>;<br>差异内容：atomicservice|api/@ohos.util.ArrayList.d.ts|
|API从不支持元服务到支持元服务|类名：ArrayList；<br>API声明：getCapacity(): number;<br>差异内容：NA|类名：ArrayList；<br>API声明：getCapacity(): number;<br>差异内容：atomicservice|api/@ohos.util.ArrayList.d.ts|
|API从不支持元服务到支持元服务|类名：ArrayList；<br>API声明：convertToArray(): Array\<T>;<br>差异内容：NA|类名：ArrayList；<br>API声明：convertToArray(): Array\<T>;<br>差异内容：atomicservice|api/@ohos.util.ArrayList.d.ts|
|API从不支持元服务到支持元服务|类名：ArrayList；<br>API声明：isEmpty(): boolean;<br>差异内容：NA|类名：ArrayList；<br>API声明：isEmpty(): boolean;<br>差异内容：atomicservice|api/@ohos.util.ArrayList.d.ts|
|API从不支持元服务到支持元服务|类名：ArrayList；<br>API声明：increaseCapacityTo(newCapacity: number): void;<br>差异内容：NA|类名：ArrayList；<br>API声明：increaseCapacityTo(newCapacity: number): void;<br>差异内容：atomicservice|api/@ohos.util.ArrayList.d.ts|
|API从不支持元服务到支持元服务|类名：ArrayList；<br>API声明：trimToCurrentLength(): void;<br>差异内容：NA|类名：ArrayList；<br>API声明：trimToCurrentLength(): void;<br>差异内容：atomicservice|api/@ohos.util.ArrayList.d.ts|
|API从不支持元服务到支持元服务|类名：ArrayList；<br>API声明：[Symbol.iterator](): IterableIterator\<T>;<br>差异内容：NA|类名：ArrayList；<br>API声明：[Symbol.iterator](): IterableIterator\<T>;<br>差异内容：atomicservice|api/@ohos.util.ArrayList.d.ts|
|API从不支持元服务到支持元服务|类名：util；<br>API声明：function format(format: string, ...args: Object[]): string;<br>差异内容：NA|类名：util；<br>API声明：function format(format: string, ...args: Object[]): string;<br>差异内容：atomicservice|api/@ohos.util.d.ts|
|API从不支持元服务到支持元服务|类名：util；<br>API声明：function errnoToString(errno: number): string;<br>差异内容：NA|类名：util；<br>API声明：function errnoToString(errno: number): string;<br>差异内容：atomicservice|api/@ohos.util.d.ts|
|API从不支持元服务到支持元服务|类名：util；<br>API声明：function callbackWrapper(original: Function): (err: Object, value: Object) => void;<br>差异内容：NA|类名：util；<br>API声明：function callbackWrapper(original: Function): (err: Object, value: Object) => void;<br>差异内容：atomicservice|api/@ohos.util.d.ts|
|API从不支持元服务到支持元服务|类名：util；<br>API声明：function promisify(original: (err: Object, value: Object) => void): Function;<br>差异内容：NA|类名：util；<br>API声明：function promisify(original: (err: Object, value: Object) => void): Function;<br>差异内容：atomicservice|api/@ohos.util.d.ts|
|API从不支持元服务到支持元服务|类名：util；<br>API声明：function generateRandomUUID(entropyCache?: boolean): string;<br>差异内容：NA|类名：util；<br>API声明：function generateRandomUUID(entropyCache?: boolean): string;<br>差异内容：atomicservice|api/@ohos.util.d.ts|
|API从不支持元服务到支持元服务|类名：util；<br>API声明：function generateRandomBinaryUUID(entropyCache?: boolean): Uint8Array;<br>差异内容：NA|类名：util；<br>API声明：function generateRandomBinaryUUID(entropyCache?: boolean): Uint8Array;<br>差异内容：atomicservice|api/@ohos.util.d.ts|
|API从不支持元服务到支持元服务|类名：util；<br>API声明：function parseUUID(uuid: string): Uint8Array;<br>差异内容：NA|类名：util；<br>API声明：function parseUUID(uuid: string): Uint8Array;<br>差异内容：atomicservice|api/@ohos.util.d.ts|
|API从不支持元服务到支持元服务|类名：TextDecoder；<br>API声明：readonly encoding: string;<br>差异内容：NA|类名：TextDecoder；<br>API声明：readonly encoding: string;<br>差异内容：atomicservice|api/@ohos.util.d.ts|
|API从不支持元服务到支持元服务|类名：TextDecoder；<br>API声明：readonly fatal: boolean;<br>差异内容：NA|类名：TextDecoder；<br>API声明：readonly fatal: boolean;<br>差异内容：atomicservice|api/@ohos.util.d.ts|
|API从不支持元服务到支持元服务|类名：TextDecoder；<br>API声明：readonly ignoreBOM = false;<br>差异内容：NA|类名：TextDecoder；<br>API声明：readonly ignoreBOM = false;<br>差异内容：atomicservice|api/@ohos.util.d.ts|
|API从不支持元服务到支持元服务|类名：TextEncoder；<br>API声明：readonly encoding = 'utf-8';<br>差异内容：NA|类名：TextEncoder；<br>API声明：readonly encoding = 'utf-8';<br>差异内容：atomicservice|api/@ohos.util.d.ts|
|API从不支持元服务到支持元服务|类名：util；<br>API声明：class RationalNumber<br>差异内容：NA|类名：util；<br>API声明：class RationalNumber<br>差异内容：atomicservice|api/@ohos.util.d.ts|
|API从不支持元服务到支持元服务|类名：RationalNumber；<br>API声明：static parseRationalNumber(numerator: number, denominator: number): RationalNumber;<br>差异内容：NA|类名：RationalNumber；<br>API声明：static parseRationalNumber(numerator: number, denominator: number): RationalNumber;<br>差异内容：atomicservice|api/@ohos.util.d.ts|
|API从不支持元服务到支持元服务|类名：RationalNumber；<br>API声明：static createRationalFromString(rationalString: string): RationalNumber;<br>差异内容：NA|类名：RationalNumber；<br>API声明：static createRationalFromString(rationalString: string): RationalNumber;<br>差异内容：atomicservice|api/@ohos.util.d.ts|
|API从不支持元服务到支持元服务|类名：RationalNumber；<br>API声明：compare(another: RationalNumber): number;<br>差异内容：NA|类名：RationalNumber；<br>API声明：compare(another: RationalNumber): number;<br>差异内容：atomicservice|api/@ohos.util.d.ts|
|API从不支持元服务到支持元服务|类名：RationalNumber；<br>API声明：equals(obj: Object): boolean;<br>差异内容：NA|类名：RationalNumber；<br>API声明：equals(obj: Object): boolean;<br>差异内容：atomicservice|api/@ohos.util.d.ts|
|API从不支持元服务到支持元服务|类名：RationalNumber；<br>API声明：valueOf(): number;<br>差异内容：NA|类名：RationalNumber；<br>API声明：valueOf(): number;<br>差异内容：atomicservice|api/@ohos.util.d.ts|
|API从不支持元服务到支持元服务|类名：RationalNumber；<br>API声明：static getCommonFactor(number1: number, number2: number): number;<br>差异内容：NA|类名：RationalNumber；<br>API声明：static getCommonFactor(number1: number, number2: number): number;<br>差异内容：atomicservice|api/@ohos.util.d.ts|
|API从不支持元服务到支持元服务|类名：RationalNumber；<br>API声明：getDenominator(): number;<br>差异内容：NA|类名：RationalNumber；<br>API声明：getDenominator(): number;<br>差异内容：atomicservice|api/@ohos.util.d.ts|
|API从不支持元服务到支持元服务|类名：RationalNumber；<br>API声明：getNumerator(): number;<br>差异内容：NA|类名：RationalNumber；<br>API声明：getNumerator(): number;<br>差异内容：atomicservice|api/@ohos.util.d.ts|
|API从不支持元服务到支持元服务|类名：RationalNumber；<br>API声明：isFinite(): boolean;<br>差异内容：NA|类名：RationalNumber；<br>API声明：isFinite(): boolean;<br>差异内容：atomicservice|api/@ohos.util.d.ts|
|API从不支持元服务到支持元服务|类名：RationalNumber；<br>API声明：isNaN(): boolean;<br>差异内容：NA|类名：RationalNumber；<br>API声明：isNaN(): boolean;<br>差异内容：atomicservice|api/@ohos.util.d.ts|
|API从不支持元服务到支持元服务|类名：RationalNumber；<br>API声明：isZero(): boolean;<br>差异内容：NA|类名：RationalNumber；<br>API声明：isZero(): boolean;<br>差异内容：atomicservice|api/@ohos.util.d.ts|
|API从不支持元服务到支持元服务|类名：RationalNumber；<br>API声明：toString(): string;<br>差异内容：NA|类名：RationalNumber；<br>API声明：toString(): string;<br>差异内容：atomicservice|api/@ohos.util.d.ts|
|API从不支持元服务到支持元服务|类名：util；<br>API声明：class LRUCache<br>差异内容：NA|类名：util；<br>API声明：class LRUCache<br>差异内容：atomicservice|api/@ohos.util.d.ts|
|API从不支持元服务到支持元服务|类名：LRUCache；<br>API声明：updateCapacity(newCapacity: number): void;<br>差异内容：NA|类名：LRUCache；<br>API声明：updateCapacity(newCapacity: number): void;<br>差异内容：atomicservice|api/@ohos.util.d.ts|
|API从不支持元服务到支持元服务|类名：LRUCache；<br>API声明：toString(): string;<br>差异内容：NA|类名：LRUCache；<br>API声明：toString(): string;<br>差异内容：atomicservice|api/@ohos.util.d.ts|
|API从不支持元服务到支持元服务|类名：LRUCache；<br>API声明：length: number;<br>差异内容：NA|类名：LRUCache；<br>API声明：length: number;<br>差异内容：atomicservice|api/@ohos.util.d.ts|
|API从不支持元服务到支持元服务|类名：LRUCache；<br>API声明：getCapacity(): number;<br>差异内容：NA|类名：LRUCache；<br>API声明：getCapacity(): number;<br>差异内容：atomicservice|api/@ohos.util.d.ts|
|API从不支持元服务到支持元服务|类名：LRUCache；<br>API声明：clear(): void;<br>差异内容：NA|类名：LRUCache；<br>API声明：clear(): void;<br>差异内容：atomicservice|api/@ohos.util.d.ts|
|API从不支持元服务到支持元服务|类名：LRUCache；<br>API声明：getCreateCount(): number;<br>差异内容：NA|类名：LRUCache；<br>API声明：getCreateCount(): number;<br>差异内容：atomicservice|api/@ohos.util.d.ts|
|API从不支持元服务到支持元服务|类名：LRUCache；<br>API声明：getMissCount(): number;<br>差异内容：NA|类名：LRUCache；<br>API声明：getMissCount(): number;<br>差异内容：atomicservice|api/@ohos.util.d.ts|
|API从不支持元服务到支持元服务|类名：LRUCache；<br>API声明：getRemovalCount(): number;<br>差异内容：NA|类名：LRUCache；<br>API声明：getRemovalCount(): number;<br>差异内容：atomicservice|api/@ohos.util.d.ts|
|API从不支持元服务到支持元服务|类名：LRUCache；<br>API声明：getMatchCount(): number;<br>差异内容：NA|类名：LRUCache；<br>API声明：getMatchCount(): number;<br>差异内容：atomicservice|api/@ohos.util.d.ts|
|API从不支持元服务到支持元服务|类名：LRUCache；<br>API声明：getPutCount(): number;<br>差异内容：NA|类名：LRUCache；<br>API声明：getPutCount(): number;<br>差异内容：atomicservice|api/@ohos.util.d.ts|
|API从不支持元服务到支持元服务|类名：LRUCache；<br>API声明：isEmpty(): boolean;<br>差异内容：NA|类名：LRUCache；<br>API声明：isEmpty(): boolean;<br>差异内容：atomicservice|api/@ohos.util.d.ts|
|API从不支持元服务到支持元服务|类名：LRUCache；<br>API声明：get(key: K): V \| undefined;<br>差异内容：NA|类名：LRUCache；<br>API声明：get(key: K): V \| undefined;<br>差异内容：atomicservice|api/@ohos.util.d.ts|
|API从不支持元服务到支持元服务|类名：LRUCache；<br>API声明：put(key: K, value: V): V;<br>差异内容：NA|类名：LRUCache；<br>API声明：put(key: K, value: V): V;<br>差异内容：atomicservice|api/@ohos.util.d.ts|
|API从不支持元服务到支持元服务|类名：LRUCache；<br>API声明：values(): V[];<br>差异内容：NA|类名：LRUCache；<br>API声明：values(): V[];<br>差异内容：atomicservice|api/@ohos.util.d.ts|
|API从不支持元服务到支持元服务|类名：LRUCache；<br>API声明：keys(): K[];<br>差异内容：NA|类名：LRUCache；<br>API声明：keys(): K[];<br>差异内容：atomicservice|api/@ohos.util.d.ts|
|API从不支持元服务到支持元服务|类名：LRUCache；<br>API声明：remove(key: K): V \| undefined;<br>差异内容：NA|类名：LRUCache；<br>API声明：remove(key: K): V \| undefined;<br>差异内容：atomicservice|api/@ohos.util.d.ts|
|API从不支持元服务到支持元服务|类名：LRUCache；<br>API声明：afterRemoval(isEvict: boolean, key: K, value: V, newValue: V): void;<br>差异内容：NA|类名：LRUCache；<br>API声明：afterRemoval(isEvict: boolean, key: K, value: V, newValue: V): void;<br>差异内容：atomicservice|api/@ohos.util.d.ts|
|API从不支持元服务到支持元服务|类名：LRUCache；<br>API声明：contains(key: K): boolean;<br>差异内容：NA|类名：LRUCache；<br>API声明：contains(key: K): boolean;<br>差异内容：atomicservice|api/@ohos.util.d.ts|
|API从不支持元服务到支持元服务|类名：LRUCache；<br>API声明：createDefault(key: K): V;<br>差异内容：NA|类名：LRUCache；<br>API声明：createDefault(key: K): V;<br>差异内容：atomicservice|api/@ohos.util.d.ts|
|API从不支持元服务到支持元服务|类名：LRUCache；<br>API声明：entries(): IterableIterator\<[<br>            K,<br>            V<br>        ]>;<br>差异内容：NA|类名：LRUCache；<br>API声明：entries(): IterableIterator\<[<br>            K,<br>            V<br>        ]>;<br>差异内容：atomicservice|api/@ohos.util.d.ts|
|API从不支持元服务到支持元服务|类名：LRUCache；<br>API声明：[Symbol.iterator](): IterableIterator\<[<br>            K,<br>            V<br>        ]>;<br>差异内容：NA|类名：LRUCache；<br>API声明：[Symbol.iterator](): IterableIterator\<[<br>            K,<br>            V<br>        ]>;<br>差异内容：atomicservice|api/@ohos.util.d.ts|
|API从不支持元服务到支持元服务|类名：util；<br>API声明：interface ScopeComparable<br>差异内容：NA|类名：util；<br>API声明：interface ScopeComparable<br>差异内容：atomicservice|api/@ohos.util.d.ts|
|API从不支持元服务到支持元服务|类名：ScopeComparable；<br>API声明：compareTo(other: ScopeComparable): boolean;<br>差异内容：NA|类名：ScopeComparable；<br>API声明：compareTo(other: ScopeComparable): boolean;<br>差异内容：atomicservice|api/@ohos.util.d.ts|
|API从不支持元服务到支持元服务|类名：util；<br>API声明：type ScopeType = ScopeComparable \| number;<br>差异内容：NA|类名：util；<br>API声明：type ScopeType = ScopeComparable \| number;<br>差异内容：atomicservice|api/@ohos.util.d.ts|
|API从不支持元服务到支持元服务|类名：util；<br>API声明：class ScopeHelper<br>差异内容：NA|类名：util；<br>API声明：class ScopeHelper<br>差异内容：atomicservice|api/@ohos.util.d.ts|
|API从不支持元服务到支持元服务|类名：ScopeHelper；<br>API声明：toString(): string;<br>差异内容：NA|类名：ScopeHelper；<br>API声明：toString(): string;<br>差异内容：atomicservice|api/@ohos.util.d.ts|
|API从不支持元服务到支持元服务|类名：ScopeHelper；<br>API声明：intersect(range: ScopeHelper): ScopeHelper;<br>差异内容：NA|类名：ScopeHelper；<br>API声明：intersect(range: ScopeHelper): ScopeHelper;<br>差异内容：atomicservice|api/@ohos.util.d.ts|
|API从不支持元服务到支持元服务|类名：ScopeHelper；<br>API声明：intersect(lowerObj: ScopeType, upperObj: ScopeType): ScopeHelper;<br>差异内容：NA|类名：ScopeHelper；<br>API声明：intersect(lowerObj: ScopeType, upperObj: ScopeType): ScopeHelper;<br>差异内容：atomicservice|api/@ohos.util.d.ts|
|API从不支持元服务到支持元服务|类名：ScopeHelper；<br>API声明：getUpper(): ScopeType;<br>差异内容：NA|类名：ScopeHelper；<br>API声明：getUpper(): ScopeType;<br>差异内容：atomicservice|api/@ohos.util.d.ts|
|API从不支持元服务到支持元服务|类名：ScopeHelper；<br>API声明：getLower(): ScopeType;<br>差异内容：NA|类名：ScopeHelper；<br>API声明：getLower(): ScopeType;<br>差异内容：atomicservice|api/@ohos.util.d.ts|
|API从不支持元服务到支持元服务|类名：ScopeHelper；<br>API声明：expand(lowerObj: ScopeType, upperObj: ScopeType): ScopeHelper;<br>差异内容：NA|类名：ScopeHelper；<br>API声明：expand(lowerObj: ScopeType, upperObj: ScopeType): ScopeHelper;<br>差异内容：atomicservice|api/@ohos.util.d.ts|
|API从不支持元服务到支持元服务|类名：ScopeHelper；<br>API声明：expand(range: ScopeHelper): ScopeHelper;<br>差异内容：NA|类名：ScopeHelper；<br>API声明：expand(range: ScopeHelper): ScopeHelper;<br>差异内容：atomicservice|api/@ohos.util.d.ts|
|API从不支持元服务到支持元服务|类名：ScopeHelper；<br>API声明：expand(value: ScopeType): ScopeHelper;<br>差异内容：NA|类名：ScopeHelper；<br>API声明：expand(value: ScopeType): ScopeHelper;<br>差异内容：atomicservice|api/@ohos.util.d.ts|
|API从不支持元服务到支持元服务|类名：ScopeHelper；<br>API声明：contains(value: ScopeType): boolean;<br>差异内容：NA|类名：ScopeHelper；<br>API声明：contains(value: ScopeType): boolean;<br>差异内容：atomicservice|api/@ohos.util.d.ts|
|API从不支持元服务到支持元服务|类名：ScopeHelper；<br>API声明：contains(range: ScopeHelper): boolean;<br>差异内容：NA|类名：ScopeHelper；<br>API声明：contains(range: ScopeHelper): boolean;<br>差异内容：atomicservice|api/@ohos.util.d.ts|
|API从不支持元服务到支持元服务|类名：ScopeHelper；<br>API声明：clamp(value: ScopeType): ScopeType;<br>差异内容：NA|类名：ScopeHelper；<br>API声明：clamp(value: ScopeType): ScopeType;<br>差异内容：atomicservice|api/@ohos.util.d.ts|
|API从不支持元服务到支持元服务|类名：Base64Helper；<br>API声明：encodeToString(src: Uint8Array, options?: Type): Promise\<string>;<br>差异内容：NA|类名：Base64Helper；<br>API声明：encodeToString(src: Uint8Array, options?: Type): Promise\<string>;<br>差异内容：atomicservice|api/@ohos.util.d.ts|
|API从不支持元服务到支持元服务|类名：Base64Helper；<br>API声明：decode(src: Uint8Array \| string, options?: Type): Promise\<Uint8Array>;<br>差异内容：NA|类名：Base64Helper；<br>API声明：decode(src: Uint8Array \| string, options?: Type): Promise\<Uint8Array>;<br>差异内容：atomicservice|api/@ohos.util.d.ts|
|API从不支持元服务到支持元服务|类名：util；<br>API声明：class types<br>差异内容：NA|类名：util；<br>API声明：class types<br>差异内容：atomicservice|api/@ohos.util.d.ts|
|API从不支持元服务到支持元服务|类名：types；<br>API声明：isAnyArrayBuffer(value: Object): boolean;<br>差异内容：NA|类名：types；<br>API声明：isAnyArrayBuffer(value: Object): boolean;<br>差异内容：atomicservice|api/@ohos.util.d.ts|
|API从不支持元服务到支持元服务|类名：types；<br>API声明：isArrayBufferView(value: Object): boolean;<br>差异内容：NA|类名：types；<br>API声明：isArrayBufferView(value: Object): boolean;<br>差异内容：atomicservice|api/@ohos.util.d.ts|
|API从不支持元服务到支持元服务|类名：types；<br>API声明：isArgumentsObject(value: Object): boolean;<br>差异内容：NA|类名：types；<br>API声明：isArgumentsObject(value: Object): boolean;<br>差异内容：atomicservice|api/@ohos.util.d.ts|
|API从不支持元服务到支持元服务|类名：types；<br>API声明：isArrayBuffer(value: Object): boolean;<br>差异内容：NA|类名：types；<br>API声明：isArrayBuffer(value: Object): boolean;<br>差异内容：atomicservice|api/@ohos.util.d.ts|
|API从不支持元服务到支持元服务|类名：types；<br>API声明：isAsyncFunction(value: Object): boolean;<br>差异内容：NA|类名：types；<br>API声明：isAsyncFunction(value: Object): boolean;<br>差异内容：atomicservice|api/@ohos.util.d.ts|
|API从不支持元服务到支持元服务|类名：types；<br>API声明：isBigInt64Array(value: Object): boolean;<br>差异内容：NA|类名：types；<br>API声明：isBigInt64Array(value: Object): boolean;<br>差异内容：atomicservice|api/@ohos.util.d.ts|
|API从不支持元服务到支持元服务|类名：types；<br>API声明：isBigUint64Array(value: Object): boolean;<br>差异内容：NA|类名：types；<br>API声明：isBigUint64Array(value: Object): boolean;<br>差异内容：atomicservice|api/@ohos.util.d.ts|
|API从不支持元服务到支持元服务|类名：types；<br>API声明：isBooleanObject(value: Object): boolean;<br>差异内容：NA|类名：types；<br>API声明：isBooleanObject(value: Object): boolean;<br>差异内容：atomicservice|api/@ohos.util.d.ts|
|API从不支持元服务到支持元服务|类名：types；<br>API声明：isBoxedPrimitive(value: Object): boolean;<br>差异内容：NA|类名：types；<br>API声明：isBoxedPrimitive(value: Object): boolean;<br>差异内容：atomicservice|api/@ohos.util.d.ts|
|API从不支持元服务到支持元服务|类名：types；<br>API声明：isDataView(value: Object): boolean;<br>差异内容：NA|类名：types；<br>API声明：isDataView(value: Object): boolean;<br>差异内容：atomicservice|api/@ohos.util.d.ts|
|API从不支持元服务到支持元服务|类名：types；<br>API声明：isDate(value: Object): boolean;<br>差异内容：NA|类名：types；<br>API声明：isDate(value: Object): boolean;<br>差异内容：atomicservice|api/@ohos.util.d.ts|
|API从不支持元服务到支持元服务|类名：types；<br>API声明：isExternal(value: Object): boolean;<br>差异内容：NA|类名：types；<br>API声明：isExternal(value: Object): boolean;<br>差异内容：atomicservice|api/@ohos.util.d.ts|
|API从不支持元服务到支持元服务|类名：types；<br>API声明：isFloat32Array(value: Object): boolean;<br>差异内容：NA|类名：types；<br>API声明：isFloat32Array(value: Object): boolean;<br>差异内容：atomicservice|api/@ohos.util.d.ts|
|API从不支持元服务到支持元服务|类名：types；<br>API声明：isFloat64Array(value: Object): boolean;<br>差异内容：NA|类名：types；<br>API声明：isFloat64Array(value: Object): boolean;<br>差异内容：atomicservice|api/@ohos.util.d.ts|
|API从不支持元服务到支持元服务|类名：types；<br>API声明：isGeneratorFunction(value: Object): boolean;<br>差异内容：NA|类名：types；<br>API声明：isGeneratorFunction(value: Object): boolean;<br>差异内容：atomicservice|api/@ohos.util.d.ts|
|API从不支持元服务到支持元服务|类名：types；<br>API声明：isGeneratorObject(value: Object): boolean;<br>差异内容：NA|类名：types；<br>API声明：isGeneratorObject(value: Object): boolean;<br>差异内容：atomicservice|api/@ohos.util.d.ts|
|API从不支持元服务到支持元服务|类名：types；<br>API声明：isInt8Array(value: Object): boolean;<br>差异内容：NA|类名：types；<br>API声明：isInt8Array(value: Object): boolean;<br>差异内容：atomicservice|api/@ohos.util.d.ts|
|API从不支持元服务到支持元服务|类名：types；<br>API声明：isInt16Array(value: Object): boolean;<br>差异内容：NA|类名：types；<br>API声明：isInt16Array(value: Object): boolean;<br>差异内容：atomicservice|api/@ohos.util.d.ts|
|API从不支持元服务到支持元服务|类名：types；<br>API声明：isInt32Array(value: Object): boolean;<br>差异内容：NA|类名：types；<br>API声明：isInt32Array(value: Object): boolean;<br>差异内容：atomicservice|api/@ohos.util.d.ts|
|API从不支持元服务到支持元服务|类名：types；<br>API声明：isMap(value: Object): boolean;<br>差异内容：NA|类名：types；<br>API声明：isMap(value: Object): boolean;<br>差异内容：atomicservice|api/@ohos.util.d.ts|
|API从不支持元服务到支持元服务|类名：types；<br>API声明：isMapIterator(value: Object): boolean;<br>差异内容：NA|类名：types；<br>API声明：isMapIterator(value: Object): boolean;<br>差异内容：atomicservice|api/@ohos.util.d.ts|
|API从不支持元服务到支持元服务|类名：types；<br>API声明：isModuleNamespaceObject(value: Object): boolean;<br>差异内容：NA|类名：types；<br>API声明：isModuleNamespaceObject(value: Object): boolean;<br>差异内容：atomicservice|api/@ohos.util.d.ts|
|API从不支持元服务到支持元服务|类名：types；<br>API声明：isNativeError(value: Object): boolean;<br>差异内容：NA|类名：types；<br>API声明：isNativeError(value: Object): boolean;<br>差异内容：atomicservice|api/@ohos.util.d.ts|
|API从不支持元服务到支持元服务|类名：types；<br>API声明：isNumberObject(value: Object): boolean;<br>差异内容：NA|类名：types；<br>API声明：isNumberObject(value: Object): boolean;<br>差异内容：atomicservice|api/@ohos.util.d.ts|
|API从不支持元服务到支持元服务|类名：types；<br>API声明：isPromise(value: Object): boolean;<br>差异内容：NA|类名：types；<br>API声明：isPromise(value: Object): boolean;<br>差异内容：atomicservice|api/@ohos.util.d.ts|
|API从不支持元服务到支持元服务|类名：types；<br>API声明：isProxy(value: Object): boolean;<br>差异内容：NA|类名：types；<br>API声明：isProxy(value: Object): boolean;<br>差异内容：atomicservice|api/@ohos.util.d.ts|
|API从不支持元服务到支持元服务|类名：types；<br>API声明：isRegExp(value: Object): boolean;<br>差异内容：NA|类名：types；<br>API声明：isRegExp(value: Object): boolean;<br>差异内容：atomicservice|api/@ohos.util.d.ts|
|API从不支持元服务到支持元服务|类名：types；<br>API声明：isSet(value: Object): boolean;<br>差异内容：NA|类名：types；<br>API声明：isSet(value: Object): boolean;<br>差异内容：atomicservice|api/@ohos.util.d.ts|
|API从不支持元服务到支持元服务|类名：types；<br>API声明：isSetIterator(value: Object): boolean;<br>差异内容：NA|类名：types；<br>API声明：isSetIterator(value: Object): boolean;<br>差异内容：atomicservice|api/@ohos.util.d.ts|
|API从不支持元服务到支持元服务|类名：types；<br>API声明：isSharedArrayBuffer(value: Object): boolean;<br>差异内容：NA|类名：types；<br>API声明：isSharedArrayBuffer(value: Object): boolean;<br>差异内容：atomicservice|api/@ohos.util.d.ts|
|API从不支持元服务到支持元服务|类名：types；<br>API声明：isStringObject(value: Object): boolean;<br>差异内容：NA|类名：types；<br>API声明：isStringObject(value: Object): boolean;<br>差异内容：atomicservice|api/@ohos.util.d.ts|
|API从不支持元服务到支持元服务|类名：types；<br>API声明：isSymbolObject(value: Object): boolean;<br>差异内容：NA|类名：types；<br>API声明：isSymbolObject(value: Object): boolean;<br>差异内容：atomicservice|api/@ohos.util.d.ts|
|API从不支持元服务到支持元服务|类名：types；<br>API声明：isTypedArray(value: Object): boolean;<br>差异内容：NA|类名：types；<br>API声明：isTypedArray(value: Object): boolean;<br>差异内容：atomicservice|api/@ohos.util.d.ts|
|API从不支持元服务到支持元服务|类名：types；<br>API声明：isUint8Array(value: Object): boolean;<br>差异内容：NA|类名：types；<br>API声明：isUint8Array(value: Object): boolean;<br>差异内容：atomicservice|api/@ohos.util.d.ts|
|API从不支持元服务到支持元服务|类名：types；<br>API声明：isUint8ClampedArray(value: Object): boolean;<br>差异内容：NA|类名：types；<br>API声明：isUint8ClampedArray(value: Object): boolean;<br>差异内容：atomicservice|api/@ohos.util.d.ts|
|API从不支持元服务到支持元服务|类名：types；<br>API声明：isUint16Array(value: Object): boolean;<br>差异内容：NA|类名：types；<br>API声明：isUint16Array(value: Object): boolean;<br>差异内容：atomicservice|api/@ohos.util.d.ts|
|API从不支持元服务到支持元服务|类名：types；<br>API声明：isUint32Array(value: Object): boolean;<br>差异内容：NA|类名：types；<br>API声明：isUint32Array(value: Object): boolean;<br>差异内容：atomicservice|api/@ohos.util.d.ts|
|API从不支持元服务到支持元服务|类名：types；<br>API声明：isWeakMap(value: Object): boolean;<br>差异内容：NA|类名：types；<br>API声明：isWeakMap(value: Object): boolean;<br>差异内容：atomicservice|api/@ohos.util.d.ts|
|API从不支持元服务到支持元服务|类名：types；<br>API声明：isWeakSet(value: Object): boolean;<br>差异内容：NA|类名：types；<br>API声明：isWeakSet(value: Object): boolean;<br>差异内容：atomicservice|api/@ohos.util.d.ts|
|API从不支持元服务到支持元服务|类名：util；<br>API声明：class Aspect<br>差异内容：NA|类名：util；<br>API声明：class Aspect<br>差异内容：atomicservice|api/@ohos.util.d.ts|
|API从不支持元服务到支持元服务|类名：Aspect；<br>API声明：static addBefore(targetClass: Object, methodName: string, isStatic: boolean, before: Function): void;<br>差异内容：NA|类名：Aspect；<br>API声明：static addBefore(targetClass: Object, methodName: string, isStatic: boolean, before: Function): void;<br>差异内容：atomicservice|api/@ohos.util.d.ts|
|API从不支持元服务到支持元服务|类名：Aspect；<br>API声明：static addAfter(targetClass: Object, methodName: string, isStatic: boolean, after: Function): void;<br>差异内容：NA|类名：Aspect；<br>API声明：static addAfter(targetClass: Object, methodName: string, isStatic: boolean, after: Function): void;<br>差异内容：atomicservice|api/@ohos.util.d.ts|
|API从不支持元服务到支持元服务|类名：Aspect；<br>API声明：static replace(targetClass: Object, methodName: string, isStatic: boolean, instead: Function): void;<br>差异内容：NA|类名：Aspect；<br>API声明：static replace(targetClass: Object, methodName: string, isStatic: boolean, instead: Function): void;<br>差异内容：atomicservice|api/@ohos.util.d.ts|
|API从不支持元服务到支持元服务|类名：global；<br>API声明：declare class Deque<br>差异内容：NA|类名：global；<br>API声明：declare class Deque<br>差异内容：atomicservice|api/@ohos.util.Deque.d.ts|
|API从不支持元服务到支持元服务|类名：Deque；<br>API声明：length: number;<br>差异内容：NA|类名：Deque；<br>API声明：length: number;<br>差异内容：atomicservice|api/@ohos.util.Deque.d.ts|
|API从不支持元服务到支持元服务|类名：Deque；<br>API声明：insertFront(element: T): void;<br>差异内容：NA|类名：Deque；<br>API声明：insertFront(element: T): void;<br>差异内容：atomicservice|api/@ohos.util.Deque.d.ts|
|API从不支持元服务到支持元服务|类名：Deque；<br>API声明：insertEnd(element: T): void;<br>差异内容：NA|类名：Deque；<br>API声明：insertEnd(element: T): void;<br>差异内容：atomicservice|api/@ohos.util.Deque.d.ts|
|API从不支持元服务到支持元服务|类名：Deque；<br>API声明：has(element: T): boolean;<br>差异内容：NA|类名：Deque；<br>API声明：has(element: T): boolean;<br>差异内容：atomicservice|api/@ohos.util.Deque.d.ts|
|API从不支持元服务到支持元服务|类名：Deque；<br>API声明：getFirst(): T;<br>差异内容：NA|类名：Deque；<br>API声明：getFirst(): T;<br>差异内容：atomicservice|api/@ohos.util.Deque.d.ts|
|API从不支持元服务到支持元服务|类名：Deque；<br>API声明：getLast(): T;<br>差异内容：NA|类名：Deque；<br>API声明：getLast(): T;<br>差异内容：atomicservice|api/@ohos.util.Deque.d.ts|
|API从不支持元服务到支持元服务|类名：Deque；<br>API声明：popFirst(): T;<br>差异内容：NA|类名：Deque；<br>API声明：popFirst(): T;<br>差异内容：atomicservice|api/@ohos.util.Deque.d.ts|
|API从不支持元服务到支持元服务|类名：Deque；<br>API声明：popLast(): T;<br>差异内容：NA|类名：Deque；<br>API声明：popLast(): T;<br>差异内容：atomicservice|api/@ohos.util.Deque.d.ts|
|API从不支持元服务到支持元服务|类名：Deque；<br>API声明：forEach(callbackFn: (value: T, index?: number, deque?: Deque\<T>) => void, thisArg?: Object): void;<br>差异内容：NA|类名：Deque；<br>API声明：forEach(callbackFn: (value: T, index?: number, deque?: Deque\<T>) => void, thisArg?: Object): void;<br>差异内容：atomicservice|api/@ohos.util.Deque.d.ts|
|API从不支持元服务到支持元服务|类名：Deque；<br>API声明：[Symbol.iterator](): IterableIterator\<T>;<br>差异内容：NA|类名：Deque；<br>API声明：[Symbol.iterator](): IterableIterator\<T>;<br>差异内容：atomicservice|api/@ohos.util.Deque.d.ts|
|API从不支持元服务到支持元服务|类名：global；<br>API声明：declare class HashMap<br>差异内容：NA|类名：global；<br>API声明：declare class HashMap<br>差异内容：atomicservice|api/@ohos.util.HashMap.d.ts|
|API从不支持元服务到支持元服务|类名：HashMap；<br>API声明：length: number;<br>差异内容：NA|类名：HashMap；<br>API声明：length: number;<br>差异内容：atomicservice|api/@ohos.util.HashMap.d.ts|
|API从不支持元服务到支持元服务|类名：HashMap；<br>API声明：isEmpty(): boolean;<br>差异内容：NA|类名：HashMap；<br>API声明：isEmpty(): boolean;<br>差异内容：atomicservice|api/@ohos.util.HashMap.d.ts|
|API从不支持元服务到支持元服务|类名：HashMap；<br>API声明：hasKey(key: K): boolean;<br>差异内容：NA|类名：HashMap；<br>API声明：hasKey(key: K): boolean;<br>差异内容：atomicservice|api/@ohos.util.HashMap.d.ts|
|API从不支持元服务到支持元服务|类名：HashMap；<br>API声明：hasValue(value: V): boolean;<br>差异内容：NA|类名：HashMap；<br>API声明：hasValue(value: V): boolean;<br>差异内容：atomicservice|api/@ohos.util.HashMap.d.ts|
|API从不支持元服务到支持元服务|类名：HashMap；<br>API声明：get(key: K): V;<br>差异内容：NA|类名：HashMap；<br>API声明：get(key: K): V;<br>差异内容：atomicservice|api/@ohos.util.HashMap.d.ts|
|API从不支持元服务到支持元服务|类名：HashMap；<br>API声明：setAll(map: HashMap\<K, V>): void;<br>差异内容：NA|类名：HashMap；<br>API声明：setAll(map: HashMap\<K, V>): void;<br>差异内容：atomicservice|api/@ohos.util.HashMap.d.ts|
|API从不支持元服务到支持元服务|类名：HashMap；<br>API声明：set(key: K, value: V): Object;<br>差异内容：NA|类名：HashMap；<br>API声明：set(key: K, value: V): Object;<br>差异内容：atomicservice|api/@ohos.util.HashMap.d.ts|
|API从不支持元服务到支持元服务|类名：HashMap；<br>API声明：remove(key: K): V;<br>差异内容：NA|类名：HashMap；<br>API声明：remove(key: K): V;<br>差异内容：atomicservice|api/@ohos.util.HashMap.d.ts|
|API从不支持元服务到支持元服务|类名：HashMap；<br>API声明：clear(): void;<br>差异内容：NA|类名：HashMap；<br>API声明：clear(): void;<br>差异内容：atomicservice|api/@ohos.util.HashMap.d.ts|
|API从不支持元服务到支持元服务|类名：HashMap；<br>API声明：keys(): IterableIterator\<K>;<br>差异内容：NA|类名：HashMap；<br>API声明：keys(): IterableIterator\<K>;<br>差异内容：atomicservice|api/@ohos.util.HashMap.d.ts|
|API从不支持元服务到支持元服务|类名：HashMap；<br>API声明：values(): IterableIterator\<V>;<br>差异内容：NA|类名：HashMap；<br>API声明：values(): IterableIterator\<V>;<br>差异内容：atomicservice|api/@ohos.util.HashMap.d.ts|
|API从不支持元服务到支持元服务|类名：HashMap；<br>API声明：replace(key: K, newValue: V): boolean;<br>差异内容：NA|类名：HashMap；<br>API声明：replace(key: K, newValue: V): boolean;<br>差异内容：atomicservice|api/@ohos.util.HashMap.d.ts|
|API从不支持元服务到支持元服务|类名：HashMap；<br>API声明：forEach(callbackFn: (value?: V, key?: K, map?: HashMap\<K, V>) => void, thisArg?: Object): void;<br>差异内容：NA|类名：HashMap；<br>API声明：forEach(callbackFn: (value?: V, key?: K, map?: HashMap\<K, V>) => void, thisArg?: Object): void;<br>差异内容：atomicservice|api/@ohos.util.HashMap.d.ts|
|API从不支持元服务到支持元服务|类名：HashMap；<br>API声明：entries(): IterableIterator\<[<br>        K,<br>        V<br>    ]>;<br>差异内容：NA|类名：HashMap；<br>API声明：entries(): IterableIterator\<[<br>        K,<br>        V<br>    ]>;<br>差异内容：atomicservice|api/@ohos.util.HashMap.d.ts|
|API从不支持元服务到支持元服务|类名：HashMap；<br>API声明：[Symbol.iterator](): IterableIterator\<[<br>        K,<br>        V<br>    ]>;<br>差异内容：NA|类名：HashMap；<br>API声明：[Symbol.iterator](): IterableIterator\<[<br>        K,<br>        V<br>    ]>;<br>差异内容：atomicservice|api/@ohos.util.HashMap.d.ts|
|API从不支持元服务到支持元服务|类名：global；<br>API声明：declare class HashSet<br>差异内容：NA|类名：global；<br>API声明：declare class HashSet<br>差异内容：atomicservice|api/@ohos.util.HashSet.d.ts|
|API从不支持元服务到支持元服务|类名：HashSet；<br>API声明：length: number;<br>差异内容：NA|类名：HashSet；<br>API声明：length: number;<br>差异内容：atomicservice|api/@ohos.util.HashSet.d.ts|
|API从不支持元服务到支持元服务|类名：HashSet；<br>API声明：isEmpty(): boolean;<br>差异内容：NA|类名：HashSet；<br>API声明：isEmpty(): boolean;<br>差异内容：atomicservice|api/@ohos.util.HashSet.d.ts|
|API从不支持元服务到支持元服务|类名：HashSet；<br>API声明：has(value: T): boolean;<br>差异内容：NA|类名：HashSet；<br>API声明：has(value: T): boolean;<br>差异内容：atomicservice|api/@ohos.util.HashSet.d.ts|
|API从不支持元服务到支持元服务|类名：HashSet；<br>API声明：add(value: T): boolean;<br>差异内容：NA|类名：HashSet；<br>API声明：add(value: T): boolean;<br>差异内容：atomicservice|api/@ohos.util.HashSet.d.ts|
|API从不支持元服务到支持元服务|类名：HashSet；<br>API声明：remove(value: T): boolean;<br>差异内容：NA|类名：HashSet；<br>API声明：remove(value: T): boolean;<br>差异内容：atomicservice|api/@ohos.util.HashSet.d.ts|
|API从不支持元服务到支持元服务|类名：HashSet；<br>API声明：clear(): void;<br>差异内容：NA|类名：HashSet；<br>API声明：clear(): void;<br>差异内容：atomicservice|api/@ohos.util.HashSet.d.ts|
|API从不支持元服务到支持元服务|类名：HashSet；<br>API声明：forEach(callbackFn: (value?: T, key?: T, set?: HashSet\<T>) => void, thisArg?: Object): void;<br>差异内容：NA|类名：HashSet；<br>API声明：forEach(callbackFn: (value?: T, key?: T, set?: HashSet\<T>) => void, thisArg?: Object): void;<br>差异内容：atomicservice|api/@ohos.util.HashSet.d.ts|
|API从不支持元服务到支持元服务|类名：HashSet；<br>API声明：values(): IterableIterator\<T>;<br>差异内容：NA|类名：HashSet；<br>API声明：values(): IterableIterator\<T>;<br>差异内容：atomicservice|api/@ohos.util.HashSet.d.ts|
|API从不支持元服务到支持元服务|类名：HashSet；<br>API声明：entries(): IterableIterator\<[<br>        T,<br>        T<br>    ]>;<br>差异内容：NA|类名：HashSet；<br>API声明：entries(): IterableIterator\<[<br>        T,<br>        T<br>    ]>;<br>差异内容：atomicservice|api/@ohos.util.HashSet.d.ts|
|API从不支持元服务到支持元服务|类名：HashSet；<br>API声明：[Symbol.iterator](): IterableIterator\<T>;<br>差异内容：NA|类名：HashSet；<br>API声明：[Symbol.iterator](): IterableIterator\<T>;<br>差异内容：atomicservice|api/@ohos.util.HashSet.d.ts|
|API从不支持元服务到支持元服务|类名：global；<br>API声明：declare class LightWeightMap<br>差异内容：NA|类名：global；<br>API声明：declare class LightWeightMap<br>差异内容：atomicservice|api/@ohos.util.LightWeightMap.d.ts|
|API从不支持元服务到支持元服务|类名：LightWeightMap；<br>API声明：length: number;<br>差异内容：NA|类名：LightWeightMap；<br>API声明：length: number;<br>差异内容：atomicservice|api/@ohos.util.LightWeightMap.d.ts|
|API从不支持元服务到支持元服务|类名：LightWeightMap；<br>API声明：hasAll(map: LightWeightMap\<K, V>): boolean;<br>差异内容：NA|类名：LightWeightMap；<br>API声明：hasAll(map: LightWeightMap\<K, V>): boolean;<br>差异内容：atomicservice|api/@ohos.util.LightWeightMap.d.ts|
|API从不支持元服务到支持元服务|类名：LightWeightMap；<br>API声明：hasKey(key: K): boolean;<br>差异内容：NA|类名：LightWeightMap；<br>API声明：hasKey(key: K): boolean;<br>差异内容：atomicservice|api/@ohos.util.LightWeightMap.d.ts|
|API从不支持元服务到支持元服务|类名：LightWeightMap；<br>API声明：hasValue(value: V): boolean;<br>差异内容：NA|类名：LightWeightMap；<br>API声明：hasValue(value: V): boolean;<br>差异内容：atomicservice|api/@ohos.util.LightWeightMap.d.ts|
|API从不支持元服务到支持元服务|类名：LightWeightMap；<br>API声明：increaseCapacityTo(minimumCapacity: number): void;<br>差异内容：NA|类名：LightWeightMap；<br>API声明：increaseCapacityTo(minimumCapacity: number): void;<br>差异内容：atomicservice|api/@ohos.util.LightWeightMap.d.ts|
|API从不支持元服务到支持元服务|类名：LightWeightMap；<br>API声明：entries(): IterableIterator\<[<br>        K,<br>        V<br>    ]>;<br>差异内容：NA|类名：LightWeightMap；<br>API声明：entries(): IterableIterator\<[<br>        K,<br>        V<br>    ]>;<br>差异内容：atomicservice|api/@ohos.util.LightWeightMap.d.ts|
|API从不支持元服务到支持元服务|类名：LightWeightMap；<br>API声明：get(key: K): V;<br>差异内容：NA|类名：LightWeightMap；<br>API声明：get(key: K): V;<br>差异内容：atomicservice|api/@ohos.util.LightWeightMap.d.ts|
|API从不支持元服务到支持元服务|类名：LightWeightMap；<br>API声明：getIndexOfKey(key: K): number;<br>差异内容：NA|类名：LightWeightMap；<br>API声明：getIndexOfKey(key: K): number;<br>差异内容：atomicservice|api/@ohos.util.LightWeightMap.d.ts|
|API从不支持元服务到支持元服务|类名：LightWeightMap；<br>API声明：getIndexOfValue(value: V): number;<br>差异内容：NA|类名：LightWeightMap；<br>API声明：getIndexOfValue(value: V): number;<br>差异内容：atomicservice|api/@ohos.util.LightWeightMap.d.ts|
|API从不支持元服务到支持元服务|类名：LightWeightMap；<br>API声明：isEmpty(): boolean;<br>差异内容：NA|类名：LightWeightMap；<br>API声明：isEmpty(): boolean;<br>差异内容：atomicservice|api/@ohos.util.LightWeightMap.d.ts|
|API从不支持元服务到支持元服务|类名：LightWeightMap；<br>API声明：getKeyAt(index: number): K;<br>差异内容：NA|类名：LightWeightMap；<br>API声明：getKeyAt(index: number): K;<br>差异内容：atomicservice|api/@ohos.util.LightWeightMap.d.ts|
|API从不支持元服务到支持元服务|类名：LightWeightMap；<br>API声明：keys(): IterableIterator\<K>;<br>差异内容：NA|类名：LightWeightMap；<br>API声明：keys(): IterableIterator\<K>;<br>差异内容：atomicservice|api/@ohos.util.LightWeightMap.d.ts|
|API从不支持元服务到支持元服务|类名：LightWeightMap；<br>API声明：setAll(map: LightWeightMap\<K, V>): void;<br>差异内容：NA|类名：LightWeightMap；<br>API声明：setAll(map: LightWeightMap\<K, V>): void;<br>差异内容：atomicservice|api/@ohos.util.LightWeightMap.d.ts|
|API从不支持元服务到支持元服务|类名：LightWeightMap；<br>API声明：set(key: K, value: V): Object;<br>差异内容：NA|类名：LightWeightMap；<br>API声明：set(key: K, value: V): Object;<br>差异内容：atomicservice|api/@ohos.util.LightWeightMap.d.ts|
|API从不支持元服务到支持元服务|类名：LightWeightMap；<br>API声明：remove(key: K): V;<br>差异内容：NA|类名：LightWeightMap；<br>API声明：remove(key: K): V;<br>差异内容：atomicservice|api/@ohos.util.LightWeightMap.d.ts|
|API从不支持元服务到支持元服务|类名：LightWeightMap；<br>API声明：removeAt(index: number): boolean;<br>差异内容：NA|类名：LightWeightMap；<br>API声明：removeAt(index: number): boolean;<br>差异内容：atomicservice|api/@ohos.util.LightWeightMap.d.ts|
|API从不支持元服务到支持元服务|类名：LightWeightMap；<br>API声明：clear(): void;<br>差异内容：NA|类名：LightWeightMap；<br>API声明：clear(): void;<br>差异内容：atomicservice|api/@ohos.util.LightWeightMap.d.ts|
|API从不支持元服务到支持元服务|类名：LightWeightMap；<br>API声明：setValueAt(index: number, newValue: V): boolean;<br>差异内容：NA|类名：LightWeightMap；<br>API声明：setValueAt(index: number, newValue: V): boolean;<br>差异内容：atomicservice|api/@ohos.util.LightWeightMap.d.ts|
|API从不支持元服务到支持元服务|类名：LightWeightMap；<br>API声明：forEach(callbackFn: (value?: V, key?: K, map?: LightWeightMap\<K, V>) => void, thisArg?: Object): void;<br>差异内容：NA|类名：LightWeightMap；<br>API声明：forEach(callbackFn: (value?: V, key?: K, map?: LightWeightMap\<K, V>) => void, thisArg?: Object): void;<br>差异内容：atomicservice|api/@ohos.util.LightWeightMap.d.ts|
|API从不支持元服务到支持元服务|类名：LightWeightMap；<br>API声明：[Symbol.iterator](): IterableIterator\<[<br>        K,<br>        V<br>    ]>;<br>差异内容：NA|类名：LightWeightMap；<br>API声明：[Symbol.iterator](): IterableIterator\<[<br>        K,<br>        V<br>    ]>;<br>差异内容：atomicservice|api/@ohos.util.LightWeightMap.d.ts|
|API从不支持元服务到支持元服务|类名：LightWeightMap；<br>API声明：toString(): String;<br>差异内容：NA|类名：LightWeightMap；<br>API声明：toString(): String;<br>差异内容：atomicservice|api/@ohos.util.LightWeightMap.d.ts|
|API从不支持元服务到支持元服务|类名：LightWeightMap；<br>API声明：getValueAt(index: number): V;<br>差异内容：NA|类名：LightWeightMap；<br>API声明：getValueAt(index: number): V;<br>差异内容：atomicservice|api/@ohos.util.LightWeightMap.d.ts|
|API从不支持元服务到支持元服务|类名：LightWeightMap；<br>API声明：values(): IterableIterator\<V>;<br>差异内容：NA|类名：LightWeightMap；<br>API声明：values(): IterableIterator\<V>;<br>差异内容：atomicservice|api/@ohos.util.LightWeightMap.d.ts|
|API从不支持元服务到支持元服务|类名：global；<br>API声明：declare class LightWeightSet<br>差异内容：NA|类名：global；<br>API声明：declare class LightWeightSet<br>差异内容：atomicservice|api/@ohos.util.LightWeightSet.d.ts|
|API从不支持元服务到支持元服务|类名：LightWeightSet；<br>API声明：length: number;<br>差异内容：NA|类名：LightWeightSet；<br>API声明：length: number;<br>差异内容：atomicservice|api/@ohos.util.LightWeightSet.d.ts|
|API从不支持元服务到支持元服务|类名：LightWeightSet；<br>API声明：add(obj: T): boolean;<br>差异内容：NA|类名：LightWeightSet；<br>API声明：add(obj: T): boolean;<br>差异内容：atomicservice|api/@ohos.util.LightWeightSet.d.ts|
|API从不支持元服务到支持元服务|类名：LightWeightSet；<br>API声明：addAll(set: LightWeightSet\<T>): boolean;<br>差异内容：NA|类名：LightWeightSet；<br>API声明：addAll(set: LightWeightSet\<T>): boolean;<br>差异内容：atomicservice|api/@ohos.util.LightWeightSet.d.ts|
|API从不支持元服务到支持元服务|类名：LightWeightSet；<br>API声明：hasAll(set: LightWeightSet\<T>): boolean;<br>差异内容：NA|类名：LightWeightSet；<br>API声明：hasAll(set: LightWeightSet\<T>): boolean;<br>差异内容：atomicservice|api/@ohos.util.LightWeightSet.d.ts|
|API从不支持元服务到支持元服务|类名：LightWeightSet；<br>API声明：has(key: T): boolean;<br>差异内容：NA|类名：LightWeightSet；<br>API声明：has(key: T): boolean;<br>差异内容：atomicservice|api/@ohos.util.LightWeightSet.d.ts|
|API从不支持元服务到支持元服务|类名：LightWeightSet；<br>API声明：increaseCapacityTo(minimumCapacity: number): void;<br>差异内容：NA|类名：LightWeightSet；<br>API声明：increaseCapacityTo(minimumCapacity: number): void;<br>差异内容：atomicservice|api/@ohos.util.LightWeightSet.d.ts|
|API从不支持元服务到支持元服务|类名：LightWeightSet；<br>API声明：getIndexOf(key: T): number;<br>差异内容：NA|类名：LightWeightSet；<br>API声明：getIndexOf(key: T): number;<br>差异内容：atomicservice|api/@ohos.util.LightWeightSet.d.ts|
|API从不支持元服务到支持元服务|类名：LightWeightSet；<br>API声明：remove(key: T): T;<br>差异内容：NA|类名：LightWeightSet；<br>API声明：remove(key: T): T;<br>差异内容：atomicservice|api/@ohos.util.LightWeightSet.d.ts|
|API从不支持元服务到支持元服务|类名：LightWeightSet；<br>API声明：removeAt(index: number): boolean;<br>差异内容：NA|类名：LightWeightSet；<br>API声明：removeAt(index: number): boolean;<br>差异内容：atomicservice|api/@ohos.util.LightWeightSet.d.ts|
|API从不支持元服务到支持元服务|类名：LightWeightSet；<br>API声明：clear(): void;<br>差异内容：NA|类名：LightWeightSet；<br>API声明：clear(): void;<br>差异内容：atomicservice|api/@ohos.util.LightWeightSet.d.ts|
|API从不支持元服务到支持元服务|类名：LightWeightSet；<br>API声明：forEach(callbackFn: (value?: T, key?: T, set?: LightWeightSet\<T>) => void, thisArg?: Object): void;<br>差异内容：NA|类名：LightWeightSet；<br>API声明：forEach(callbackFn: (value?: T, key?: T, set?: LightWeightSet\<T>) => void, thisArg?: Object): void;<br>差异内容：atomicservice|api/@ohos.util.LightWeightSet.d.ts|
|API从不支持元服务到支持元服务|类名：LightWeightSet；<br>API声明：[Symbol.iterator](): IterableIterator\<T>;<br>差异内容：NA|类名：LightWeightSet；<br>API声明：[Symbol.iterator](): IterableIterator\<T>;<br>差异内容：atomicservice|api/@ohos.util.LightWeightSet.d.ts|
|API从不支持元服务到支持元服务|类名：LightWeightSet；<br>API声明：toString(): String;<br>差异内容：NA|类名：LightWeightSet；<br>API声明：toString(): String;<br>差异内容：atomicservice|api/@ohos.util.LightWeightSet.d.ts|
|API从不支持元服务到支持元服务|类名：LightWeightSet；<br>API声明：toArray(): Array\<T>;<br>差异内容：NA|类名：LightWeightSet；<br>API声明：toArray(): Array\<T>;<br>差异内容：atomicservice|api/@ohos.util.LightWeightSet.d.ts|
|API从不支持元服务到支持元服务|类名：LightWeightSet；<br>API声明：getValueAt(index: number): T;<br>差异内容：NA|类名：LightWeightSet；<br>API声明：getValueAt(index: number): T;<br>差异内容：atomicservice|api/@ohos.util.LightWeightSet.d.ts|
|API从不支持元服务到支持元服务|类名：LightWeightSet；<br>API声明：values(): IterableIterator\<T>;<br>差异内容：NA|类名：LightWeightSet；<br>API声明：values(): IterableIterator\<T>;<br>差异内容：atomicservice|api/@ohos.util.LightWeightSet.d.ts|
|API从不支持元服务到支持元服务|类名：LightWeightSet；<br>API声明：entries(): IterableIterator\<[<br>        T,<br>        T<br>    ]>;<br>差异内容：NA|类名：LightWeightSet；<br>API声明：entries(): IterableIterator\<[<br>        T,<br>        T<br>    ]>;<br>差异内容：atomicservice|api/@ohos.util.LightWeightSet.d.ts|
|API从不支持元服务到支持元服务|类名：LightWeightSet；<br>API声明：isEmpty(): boolean;<br>差异内容：NA|类名：LightWeightSet；<br>API声明：isEmpty(): boolean;<br>差异内容：atomicservice|api/@ohos.util.LightWeightSet.d.ts|
|API从不支持元服务到支持元服务|类名：global；<br>API声明：declare class LinkedList<br>差异内容：NA|类名：global；<br>API声明：declare class LinkedList<br>差异内容：atomicservice|api/@ohos.util.LinkedList.d.ts|
|API从不支持元服务到支持元服务|类名：LinkedList；<br>API声明：length: number;<br>差异内容：NA|类名：LinkedList；<br>API声明：length: number;<br>差异内容：atomicservice|api/@ohos.util.LinkedList.d.ts|
|API从不支持元服务到支持元服务|类名：LinkedList；<br>API声明：add(element: T): boolean;<br>差异内容：NA|类名：LinkedList；<br>API声明：add(element: T): boolean;<br>差异内容：atomicservice|api/@ohos.util.LinkedList.d.ts|
|API从不支持元服务到支持元服务|类名：LinkedList；<br>API声明：insert(index: number, element: T): void;<br>差异内容：NA|类名：LinkedList；<br>API声明：insert(index: number, element: T): void;<br>差异内容：atomicservice|api/@ohos.util.LinkedList.d.ts|
|API从不支持元服务到支持元服务|类名：LinkedList；<br>API声明：get(index: number): T;<br>差异内容：NA|类名：LinkedList；<br>API声明：get(index: number): T;<br>差异内容：atomicservice|api/@ohos.util.LinkedList.d.ts|
|API从不支持元服务到支持元服务|类名：LinkedList；<br>API声明：addFirst(element: T): void;<br>差异内容：NA|类名：LinkedList；<br>API声明：addFirst(element: T): void;<br>差异内容：atomicservice|api/@ohos.util.LinkedList.d.ts|
|API从不支持元服务到支持元服务|类名：LinkedList；<br>API声明：removeFirst(): T;<br>差异内容：NA|类名：LinkedList；<br>API声明：removeFirst(): T;<br>差异内容：atomicservice|api/@ohos.util.LinkedList.d.ts|
|API从不支持元服务到支持元服务|类名：LinkedList；<br>API声明：removeLast(): T;<br>差异内容：NA|类名：LinkedList；<br>API声明：removeLast(): T;<br>差异内容：atomicservice|api/@ohos.util.LinkedList.d.ts|
|API从不支持元服务到支持元服务|类名：LinkedList；<br>API声明：has(element: T): boolean;<br>差异内容：NA|类名：LinkedList；<br>API声明：has(element: T): boolean;<br>差异内容：atomicservice|api/@ohos.util.LinkedList.d.ts|
|API从不支持元服务到支持元服务|类名：LinkedList；<br>API声明：getIndexOf(element: T): number;<br>差异内容：NA|类名：LinkedList；<br>API声明：getIndexOf(element: T): number;<br>差异内容：atomicservice|api/@ohos.util.LinkedList.d.ts|
|API从不支持元服务到支持元服务|类名：LinkedList；<br>API声明：removeByIndex(index: number): T;<br>差异内容：NA|类名：LinkedList；<br>API声明：removeByIndex(index: number): T;<br>差异内容：atomicservice|api/@ohos.util.LinkedList.d.ts|
|API从不支持元服务到支持元服务|类名：LinkedList；<br>API声明：remove(element: T): boolean;<br>差异内容：NA|类名：LinkedList；<br>API声明：remove(element: T): boolean;<br>差异内容：atomicservice|api/@ohos.util.LinkedList.d.ts|
|API从不支持元服务到支持元服务|类名：LinkedList；<br>API声明：removeFirstFound(element: T): boolean;<br>差异内容：NA|类名：LinkedList；<br>API声明：removeFirstFound(element: T): boolean;<br>差异内容：atomicservice|api/@ohos.util.LinkedList.d.ts|
|API从不支持元服务到支持元服务|类名：LinkedList；<br>API声明：removeLastFound(element: T): boolean;<br>差异内容：NA|类名：LinkedList；<br>API声明：removeLastFound(element: T): boolean;<br>差异内容：atomicservice|api/@ohos.util.LinkedList.d.ts|
|API从不支持元服务到支持元服务|类名：LinkedList；<br>API声明：getLastIndexOf(element: T): number;<br>差异内容：NA|类名：LinkedList；<br>API声明：getLastIndexOf(element: T): number;<br>差异内容：atomicservice|api/@ohos.util.LinkedList.d.ts|
|API从不支持元服务到支持元服务|类名：LinkedList；<br>API声明：getFirst(): T;<br>差异内容：NA|类名：LinkedList；<br>API声明：getFirst(): T;<br>差异内容：atomicservice|api/@ohos.util.LinkedList.d.ts|
|API从不支持元服务到支持元服务|类名：LinkedList；<br>API声明：getLast(): T;<br>差异内容：NA|类名：LinkedList；<br>API声明：getLast(): T;<br>差异内容：atomicservice|api/@ohos.util.LinkedList.d.ts|
|API从不支持元服务到支持元服务|类名：LinkedList；<br>API声明：set(index: number, element: T): T;<br>差异内容：NA|类名：LinkedList；<br>API声明：set(index: number, element: T): T;<br>差异内容：atomicservice|api/@ohos.util.LinkedList.d.ts|
|API从不支持元服务到支持元服务|类名：LinkedList；<br>API声明：forEach(callbackFn: (value: T, index?: number, LinkedList?: LinkedList\<T>) => void, thisArg?: Object): void;<br>差异内容：NA|类名：LinkedList；<br>API声明：forEach(callbackFn: (value: T, index?: number, LinkedList?: LinkedList\<T>) => void, thisArg?: Object): void;<br>差异内容：atomicservice|api/@ohos.util.LinkedList.d.ts|
|API从不支持元服务到支持元服务|类名：LinkedList；<br>API声明：clear(): void;<br>差异内容：NA|类名：LinkedList；<br>API声明：clear(): void;<br>差异内容：atomicservice|api/@ohos.util.LinkedList.d.ts|
|API从不支持元服务到支持元服务|类名：LinkedList；<br>API声明：clone(): LinkedList\<T>;<br>差异内容：NA|类名：LinkedList；<br>API声明：clone(): LinkedList\<T>;<br>差异内容：atomicservice|api/@ohos.util.LinkedList.d.ts|
|API从不支持元服务到支持元服务|类名：LinkedList；<br>API声明：convertToArray(): Array\<T>;<br>差异内容：NA|类名：LinkedList；<br>API声明：convertToArray(): Array\<T>;<br>差异内容：atomicservice|api/@ohos.util.LinkedList.d.ts|
|API从不支持元服务到支持元服务|类名：LinkedList；<br>API声明：[Symbol.iterator](): IterableIterator\<T>;<br>差异内容：NA|类名：LinkedList；<br>API声明：[Symbol.iterator](): IterableIterator\<T>;<br>差异内容：atomicservice|api/@ohos.util.LinkedList.d.ts|
|API从不支持元服务到支持元服务|类名：global；<br>API声明：declare class List<br>差异内容：NA|类名：global；<br>API声明：declare class List<br>差异内容：atomicservice|api/@ohos.util.List.d.ts|
|API从不支持元服务到支持元服务|类名：List；<br>API声明：length: number;<br>差异内容：NA|类名：List；<br>API声明：length: number;<br>差异内容：atomicservice|api/@ohos.util.List.d.ts|
|API从不支持元服务到支持元服务|类名：List；<br>API声明：add(element: T): boolean;<br>差异内容：NA|类名：List；<br>API声明：add(element: T): boolean;<br>差异内容：atomicservice|api/@ohos.util.List.d.ts|
|API从不支持元服务到支持元服务|类名：List；<br>API声明：insert(element: T, index: number): void;<br>差异内容：NA|类名：List；<br>API声明：insert(element: T, index: number): void;<br>差异内容：atomicservice|api/@ohos.util.List.d.ts|
|API从不支持元服务到支持元服务|类名：List；<br>API声明：get(index: number): T;<br>差异内容：NA|类名：List；<br>API声明：get(index: number): T;<br>差异内容：atomicservice|api/@ohos.util.List.d.ts|
|API从不支持元服务到支持元服务|类名：List；<br>API声明：has(element: T): boolean;<br>差异内容：NA|类名：List；<br>API声明：has(element: T): boolean;<br>差异内容：atomicservice|api/@ohos.util.List.d.ts|
|API从不支持元服务到支持元服务|类名：List；<br>API声明：getIndexOf(element: T): number;<br>差异内容：NA|类名：List；<br>API声明：getIndexOf(element: T): number;<br>差异内容：atomicservice|api/@ohos.util.List.d.ts|
|API从不支持元服务到支持元服务|类名：List；<br>API声明：removeByIndex(index: number): T;<br>差异内容：NA|类名：List；<br>API声明：removeByIndex(index: number): T;<br>差异内容：atomicservice|api/@ohos.util.List.d.ts|
|API从不支持元服务到支持元服务|类名：List；<br>API声明：remove(element: T): boolean;<br>差异内容：NA|类名：List；<br>API声明：remove(element: T): boolean;<br>差异内容：atomicservice|api/@ohos.util.List.d.ts|
|API从不支持元服务到支持元服务|类名：List；<br>API声明：getLastIndexOf(element: T): number;<br>差异内容：NA|类名：List；<br>API声明：getLastIndexOf(element: T): number;<br>差异内容：atomicservice|api/@ohos.util.List.d.ts|
|API从不支持元服务到支持元服务|类名：List；<br>API声明：getFirst(): T;<br>差异内容：NA|类名：List；<br>API声明：getFirst(): T;<br>差异内容：atomicservice|api/@ohos.util.List.d.ts|
|API从不支持元服务到支持元服务|类名：List；<br>API声明：getLast(): T;<br>差异内容：NA|类名：List；<br>API声明：getLast(): T;<br>差异内容：atomicservice|api/@ohos.util.List.d.ts|
|API从不支持元服务到支持元服务|类名：List；<br>API声明：set(index: number, element: T): T;<br>差异内容：NA|类名：List；<br>API声明：set(index: number, element: T): T;<br>差异内容：atomicservice|api/@ohos.util.List.d.ts|
|API从不支持元服务到支持元服务|类名：List；<br>API声明：equal(obj: Object): boolean;<br>差异内容：NA|类名：List；<br>API声明：equal(obj: Object): boolean;<br>差异内容：atomicservice|api/@ohos.util.List.d.ts|
|API从不支持元服务到支持元服务|类名：List；<br>API声明：forEach(callbackFn: (value: T, index?: number, List?: List\<T>) => void, thisArg?: Object): void;<br>差异内容：NA|类名：List；<br>API声明：forEach(callbackFn: (value: T, index?: number, List?: List\<T>) => void, thisArg?: Object): void;<br>差异内容：atomicservice|api/@ohos.util.List.d.ts|
|API从不支持元服务到支持元服务|类名：List；<br>API声明：sort(comparator: (firstValue: T, secondValue: T) => number): void;<br>差异内容：NA|类名：List；<br>API声明：sort(comparator: (firstValue: T, secondValue: T) => number): void;<br>差异内容：atomicservice|api/@ohos.util.List.d.ts|
|API从不支持元服务到支持元服务|类名：List；<br>API声明：clear(): void;<br>差异内容：NA|类名：List；<br>API声明：clear(): void;<br>差异内容：atomicservice|api/@ohos.util.List.d.ts|
|API从不支持元服务到支持元服务|类名：List；<br>API声明：getSubList(fromIndex: number, toIndex: number): List\<T>;<br>差异内容：NA|类名：List；<br>API声明：getSubList(fromIndex: number, toIndex: number): List\<T>;<br>差异内容：atomicservice|api/@ohos.util.List.d.ts|
|API从不支持元服务到支持元服务|类名：List；<br>API声明：replaceAllElements(callbackFn: (value: T, index?: number, list?: List\<T>) => T, thisArg?: Object): void;<br>差异内容：NA|类名：List；<br>API声明：replaceAllElements(callbackFn: (value: T, index?: number, list?: List\<T>) => T, thisArg?: Object): void;<br>差异内容：atomicservice|api/@ohos.util.List.d.ts|
|API从不支持元服务到支持元服务|类名：List；<br>API声明：convertToArray(): Array\<T>;<br>差异内容：NA|类名：List；<br>API声明：convertToArray(): Array\<T>;<br>差异内容：atomicservice|api/@ohos.util.List.d.ts|
|API从不支持元服务到支持元服务|类名：List；<br>API声明：isEmpty(): boolean;<br>差异内容：NA|类名：List；<br>API声明：isEmpty(): boolean;<br>差异内容：atomicservice|api/@ohos.util.List.d.ts|
|API从不支持元服务到支持元服务|类名：List；<br>API声明：[Symbol.iterator](): IterableIterator\<T>;<br>差异内容：NA|类名：List；<br>API声明：[Symbol.iterator](): IterableIterator\<T>;<br>差异内容：atomicservice|api/@ohos.util.List.d.ts|
|API从不支持元服务到支持元服务|类名：global；<br>API声明：declare class PlainArray<br>差异内容：NA|类名：global；<br>API声明：declare class PlainArray<br>差异内容：atomicservice|api/@ohos.util.PlainArray.d.ts|
|API从不支持元服务到支持元服务|类名：PlainArray；<br>API声明：length: number;<br>差异内容：NA|类名：PlainArray；<br>API声明：length: number;<br>差异内容：atomicservice|api/@ohos.util.PlainArray.d.ts|
|API从不支持元服务到支持元服务|类名：PlainArray；<br>API声明：add(key: number, value: T): void;<br>差异内容：NA|类名：PlainArray；<br>API声明：add(key: number, value: T): void;<br>差异内容：atomicservice|api/@ohos.util.PlainArray.d.ts|
|API从不支持元服务到支持元服务|类名：PlainArray；<br>API声明：clear(): void;<br>差异内容：NA|类名：PlainArray；<br>API声明：clear(): void;<br>差异内容：atomicservice|api/@ohos.util.PlainArray.d.ts|
|API从不支持元服务到支持元服务|类名：PlainArray；<br>API声明：clone(): PlainArray\<T>;<br>差异内容：NA|类名：PlainArray；<br>API声明：clone(): PlainArray\<T>;<br>差异内容：atomicservice|api/@ohos.util.PlainArray.d.ts|
|API从不支持元服务到支持元服务|类名：PlainArray；<br>API声明：has(key: number): boolean;<br>差异内容：NA|类名：PlainArray；<br>API声明：has(key: number): boolean;<br>差异内容：atomicservice|api/@ohos.util.PlainArray.d.ts|
|API从不支持元服务到支持元服务|类名：PlainArray；<br>API声明：get(key: number): T;<br>差异内容：NA|类名：PlainArray；<br>API声明：get(key: number): T;<br>差异内容：atomicservice|api/@ohos.util.PlainArray.d.ts|
|API从不支持元服务到支持元服务|类名：PlainArray；<br>API声明：getIndexOfKey(key: number): number;<br>差异内容：NA|类名：PlainArray；<br>API声明：getIndexOfKey(key: number): number;<br>差异内容：atomicservice|api/@ohos.util.PlainArray.d.ts|
|API从不支持元服务到支持元服务|类名：PlainArray；<br>API声明：getIndexOfValue(value: T): number;<br>差异内容：NA|类名：PlainArray；<br>API声明：getIndexOfValue(value: T): number;<br>差异内容：atomicservice|api/@ohos.util.PlainArray.d.ts|
|API从不支持元服务到支持元服务|类名：PlainArray；<br>API声明：isEmpty(): boolean;<br>差异内容：NA|类名：PlainArray；<br>API声明：isEmpty(): boolean;<br>差异内容：atomicservice|api/@ohos.util.PlainArray.d.ts|
|API从不支持元服务到支持元服务|类名：PlainArray；<br>API声明：getKeyAt(index: number): number;<br>差异内容：NA|类名：PlainArray；<br>API声明：getKeyAt(index: number): number;<br>差异内容：atomicservice|api/@ohos.util.PlainArray.d.ts|
|API从不支持元服务到支持元服务|类名：PlainArray；<br>API声明：remove(key: number): T;<br>差异内容：NA|类名：PlainArray；<br>API声明：remove(key: number): T;<br>差异内容：atomicservice|api/@ohos.util.PlainArray.d.ts|
|API从不支持元服务到支持元服务|类名：PlainArray；<br>API声明：removeAt(index: number): T;<br>差异内容：NA|类名：PlainArray；<br>API声明：removeAt(index: number): T;<br>差异内容：atomicservice|api/@ohos.util.PlainArray.d.ts|
|API从不支持元服务到支持元服务|类名：PlainArray；<br>API声明：removeRangeFrom(index: number, size: number): number;<br>差异内容：NA|类名：PlainArray；<br>API声明：removeRangeFrom(index: number, size: number): number;<br>差异内容：atomicservice|api/@ohos.util.PlainArray.d.ts|
|API从不支持元服务到支持元服务|类名：PlainArray；<br>API声明：setValueAt(index: number, value: T): void;<br>差异内容：NA|类名：PlainArray；<br>API声明：setValueAt(index: number, value: T): void;<br>差异内容：atomicservice|api/@ohos.util.PlainArray.d.ts|
|API从不支持元服务到支持元服务|类名：PlainArray；<br>API声明：toString(): String;<br>差异内容：NA|类名：PlainArray；<br>API声明：toString(): String;<br>差异内容：atomicservice|api/@ohos.util.PlainArray.d.ts|
|API从不支持元服务到支持元服务|类名：PlainArray；<br>API声明：getValueAt(index: number): T;<br>差异内容：NA|类名：PlainArray；<br>API声明：getValueAt(index: number): T;<br>差异内容：atomicservice|api/@ohos.util.PlainArray.d.ts|
|API从不支持元服务到支持元服务|类名：PlainArray；<br>API声明：forEach(callbackFn: (value: T, index?: number, PlainArray?: PlainArray\<T>) => void, thisArg?: Object): void;<br>差异内容：NA|类名：PlainArray；<br>API声明：forEach(callbackFn: (value: T, index?: number, PlainArray?: PlainArray\<T>) => void, thisArg?: Object): void;<br>差异内容：atomicservice|api/@ohos.util.PlainArray.d.ts|
|API从不支持元服务到支持元服务|类名：PlainArray；<br>API声明：[Symbol.iterator](): IterableIterator\<[<br>        number,<br>        T<br>    ]>;<br>差异内容：NA|类名：PlainArray；<br>API声明：[Symbol.iterator](): IterableIterator\<[<br>        number,<br>        T<br>    ]>;<br>差异内容：atomicservice|api/@ohos.util.PlainArray.d.ts|
|API从不支持元服务到支持元服务|类名：global；<br>API声明：declare class Queue<br>差异内容：NA|类名：global；<br>API声明：declare class Queue<br>差异内容：atomicservice|api/@ohos.util.Queue.d.ts|
|API从不支持元服务到支持元服务|类名：Queue；<br>API声明：length: number;<br>差异内容：NA|类名：Queue；<br>API声明：length: number;<br>差异内容：atomicservice|api/@ohos.util.Queue.d.ts|
|API从不支持元服务到支持元服务|类名：Queue；<br>API声明：add(element: T): boolean;<br>差异内容：NA|类名：Queue；<br>API声明：add(element: T): boolean;<br>差异内容：atomicservice|api/@ohos.util.Queue.d.ts|
|API从不支持元服务到支持元服务|类名：Queue；<br>API声明：getFirst(): T;<br>差异内容：NA|类名：Queue；<br>API声明：getFirst(): T;<br>差异内容：atomicservice|api/@ohos.util.Queue.d.ts|
|API从不支持元服务到支持元服务|类名：Queue；<br>API声明：pop(): T;<br>差异内容：NA|类名：Queue；<br>API声明：pop(): T;<br>差异内容：atomicservice|api/@ohos.util.Queue.d.ts|
|API从不支持元服务到支持元服务|类名：Queue；<br>API声明：forEach(callbackFn: (value: T, index?: number, Queue?: Queue\<T>) => void, thisArg?: Object): void;<br>差异内容：NA|类名：Queue；<br>API声明：forEach(callbackFn: (value: T, index?: number, Queue?: Queue\<T>) => void, thisArg?: Object): void;<br>差异内容：atomicservice|api/@ohos.util.Queue.d.ts|
|API从不支持元服务到支持元服务|类名：Queue；<br>API声明：[Symbol.iterator](): IterableIterator\<T>;<br>差异内容：NA|类名：Queue；<br>API声明：[Symbol.iterator](): IterableIterator\<T>;<br>差异内容：atomicservice|api/@ohos.util.Queue.d.ts|
|API从不支持元服务到支持元服务|类名：global；<br>API声明：declare class Stack<br>差异内容：NA|类名：global；<br>API声明：declare class Stack<br>差异内容：atomicservice|api/@ohos.util.Stack.d.ts|
|API从不支持元服务到支持元服务|类名：Stack；<br>API声明：length: number;<br>差异内容：NA|类名：Stack；<br>API声明：length: number;<br>差异内容：atomicservice|api/@ohos.util.Stack.d.ts|
|API从不支持元服务到支持元服务|类名：Stack；<br>API声明：isEmpty(): boolean;<br>差异内容：NA|类名：Stack；<br>API声明：isEmpty(): boolean;<br>差异内容：atomicservice|api/@ohos.util.Stack.d.ts|
|API从不支持元服务到支持元服务|类名：Stack；<br>API声明：peek(): T;<br>差异内容：NA|类名：Stack；<br>API声明：peek(): T;<br>差异内容：atomicservice|api/@ohos.util.Stack.d.ts|
|API从不支持元服务到支持元服务|类名：Stack；<br>API声明：pop(): T;<br>差异内容：NA|类名：Stack；<br>API声明：pop(): T;<br>差异内容：atomicservice|api/@ohos.util.Stack.d.ts|
|API从不支持元服务到支持元服务|类名：Stack；<br>API声明：push(item: T): T;<br>差异内容：NA|类名：Stack；<br>API声明：push(item: T): T;<br>差异内容：atomicservice|api/@ohos.util.Stack.d.ts|
|API从不支持元服务到支持元服务|类名：Stack；<br>API声明：locate(element: T): number;<br>差异内容：NA|类名：Stack；<br>API声明：locate(element: T): number;<br>差异内容：atomicservice|api/@ohos.util.Stack.d.ts|
|API从不支持元服务到支持元服务|类名：Stack；<br>API声明：forEach(callbackFn: (value: T, index?: number, stack?: Stack\<T>) => void, thisArg?: Object): void;<br>差异内容：NA|类名：Stack；<br>API声明：forEach(callbackFn: (value: T, index?: number, stack?: Stack\<T>) => void, thisArg?: Object): void;<br>差异内容：atomicservice|api/@ohos.util.Stack.d.ts|
|API从不支持元服务到支持元服务|类名：Stack；<br>API声明：[Symbol.iterator](): IterableIterator\<T>;<br>差异内容：NA|类名：Stack；<br>API声明：[Symbol.iterator](): IterableIterator\<T>;<br>差异内容：atomicservice|api/@ohos.util.Stack.d.ts|
|API从不支持元服务到支持元服务|类名：global；<br>API声明：declare class TreeMap<br>差异内容：NA|类名：global；<br>API声明：declare class TreeMap<br>差异内容：atomicservice|api/@ohos.util.TreeMap.d.ts|
|API从不支持元服务到支持元服务|类名：TreeMap；<br>API声明：length: number;<br>差异内容：NA|类名：TreeMap；<br>API声明：length: number;<br>差异内容：atomicservice|api/@ohos.util.TreeMap.d.ts|
|API从不支持元服务到支持元服务|类名：TreeMap；<br>API声明：isEmpty(): boolean;<br>差异内容：NA|类名：TreeMap；<br>API声明：isEmpty(): boolean;<br>差异内容：atomicservice|api/@ohos.util.TreeMap.d.ts|
|API从不支持元服务到支持元服务|类名：TreeMap；<br>API声明：hasKey(key: K): boolean;<br>差异内容：NA|类名：TreeMap；<br>API声明：hasKey(key: K): boolean;<br>差异内容：atomicservice|api/@ohos.util.TreeMap.d.ts|
|API从不支持元服务到支持元服务|类名：TreeMap；<br>API声明：hasValue(value: V): boolean;<br>差异内容：NA|类名：TreeMap；<br>API声明：hasValue(value: V): boolean;<br>差异内容：atomicservice|api/@ohos.util.TreeMap.d.ts|
|API从不支持元服务到支持元服务|类名：TreeMap；<br>API声明：get(key: K): V;<br>差异内容：NA|类名：TreeMap；<br>API声明：get(key: K): V;<br>差异内容：atomicservice|api/@ohos.util.TreeMap.d.ts|
|API从不支持元服务到支持元服务|类名：TreeMap；<br>API声明：getFirstKey(): K;<br>差异内容：NA|类名：TreeMap；<br>API声明：getFirstKey(): K;<br>差异内容：atomicservice|api/@ohos.util.TreeMap.d.ts|
|API从不支持元服务到支持元服务|类名：TreeMap；<br>API声明：getLastKey(): K;<br>差异内容：NA|类名：TreeMap；<br>API声明：getLastKey(): K;<br>差异内容：atomicservice|api/@ohos.util.TreeMap.d.ts|
|API从不支持元服务到支持元服务|类名：TreeMap；<br>API声明：setAll(map: TreeMap\<K, V>): void;<br>差异内容：NA|类名：TreeMap；<br>API声明：setAll(map: TreeMap\<K, V>): void;<br>差异内容：atomicservice|api/@ohos.util.TreeMap.d.ts|
|API从不支持元服务到支持元服务|类名：TreeMap；<br>API声明：set(key: K, value: V): Object;<br>差异内容：NA|类名：TreeMap；<br>API声明：set(key: K, value: V): Object;<br>差异内容：atomicservice|api/@ohos.util.TreeMap.d.ts|
|API从不支持元服务到支持元服务|类名：TreeMap；<br>API声明：remove(key: K): V;<br>差异内容：NA|类名：TreeMap；<br>API声明：remove(key: K): V;<br>差异内容：atomicservice|api/@ohos.util.TreeMap.d.ts|
|API从不支持元服务到支持元服务|类名：TreeMap；<br>API声明：clear(): void;<br>差异内容：NA|类名：TreeMap；<br>API声明：clear(): void;<br>差异内容：atomicservice|api/@ohos.util.TreeMap.d.ts|
|API从不支持元服务到支持元服务|类名：TreeMap；<br>API声明：getLowerKey(key: K): K;<br>差异内容：NA|类名：TreeMap；<br>API声明：getLowerKey(key: K): K;<br>差异内容：atomicservice|api/@ohos.util.TreeMap.d.ts|
|API从不支持元服务到支持元服务|类名：TreeMap；<br>API声明：getHigherKey(key: K): K;<br>差异内容：NA|类名：TreeMap；<br>API声明：getHigherKey(key: K): K;<br>差异内容：atomicservice|api/@ohos.util.TreeMap.d.ts|
|API从不支持元服务到支持元服务|类名：TreeMap；<br>API声明：keys(): IterableIterator\<K>;<br>差异内容：NA|类名：TreeMap；<br>API声明：keys(): IterableIterator\<K>;<br>差异内容：atomicservice|api/@ohos.util.TreeMap.d.ts|
|API从不支持元服务到支持元服务|类名：TreeMap；<br>API声明：values(): IterableIterator\<V>;<br>差异内容：NA|类名：TreeMap；<br>API声明：values(): IterableIterator\<V>;<br>差异内容：atomicservice|api/@ohos.util.TreeMap.d.ts|
|API从不支持元服务到支持元服务|类名：TreeMap；<br>API声明：replace(key: K, newValue: V): boolean;<br>差异内容：NA|类名：TreeMap；<br>API声明：replace(key: K, newValue: V): boolean;<br>差异内容：atomicservice|api/@ohos.util.TreeMap.d.ts|
|API从不支持元服务到支持元服务|类名：TreeMap；<br>API声明：forEach(callbackFn: (value?: V, key?: K, map?: TreeMap\<K, V>) => void, thisArg?: Object): void;<br>差异内容：NA|类名：TreeMap；<br>API声明：forEach(callbackFn: (value?: V, key?: K, map?: TreeMap\<K, V>) => void, thisArg?: Object): void;<br>差异内容：atomicservice|api/@ohos.util.TreeMap.d.ts|
|API从不支持元服务到支持元服务|类名：TreeMap；<br>API声明：entries(): IterableIterator\<[<br>        K,<br>        V<br>    ]>;<br>差异内容：NA|类名：TreeMap；<br>API声明：entries(): IterableIterator\<[<br>        K,<br>        V<br>    ]>;<br>差异内容：atomicservice|api/@ohos.util.TreeMap.d.ts|
|API从不支持元服务到支持元服务|类名：TreeMap；<br>API声明：[Symbol.iterator](): IterableIterator\<[<br>        K,<br>        V<br>    ]>;<br>差异内容：NA|类名：TreeMap；<br>API声明：[Symbol.iterator](): IterableIterator\<[<br>        K,<br>        V<br>    ]>;<br>差异内容：atomicservice|api/@ohos.util.TreeMap.d.ts|
|API从不支持元服务到支持元服务|类名：global；<br>API声明：declare class TreeSet<br>差异内容：NA|类名：global；<br>API声明：declare class TreeSet<br>差异内容：atomicservice|api/@ohos.util.TreeSet.d.ts|
|API从不支持元服务到支持元服务|类名：TreeSet；<br>API声明：length: number;<br>差异内容：NA|类名：TreeSet；<br>API声明：length: number;<br>差异内容：atomicservice|api/@ohos.util.TreeSet.d.ts|
|API从不支持元服务到支持元服务|类名：TreeSet；<br>API声明：isEmpty(): boolean;<br>差异内容：NA|类名：TreeSet；<br>API声明：isEmpty(): boolean;<br>差异内容：atomicservice|api/@ohos.util.TreeSet.d.ts|
|API从不支持元服务到支持元服务|类名：TreeSet；<br>API声明：has(value: T): boolean;<br>差异内容：NA|类名：TreeSet；<br>API声明：has(value: T): boolean;<br>差异内容：atomicservice|api/@ohos.util.TreeSet.d.ts|
|API从不支持元服务到支持元服务|类名：TreeSet；<br>API声明：add(value: T): boolean;<br>差异内容：NA|类名：TreeSet；<br>API声明：add(value: T): boolean;<br>差异内容：atomicservice|api/@ohos.util.TreeSet.d.ts|
|API从不支持元服务到支持元服务|类名：TreeSet；<br>API声明：remove(value: T): boolean;<br>差异内容：NA|类名：TreeSet；<br>API声明：remove(value: T): boolean;<br>差异内容：atomicservice|api/@ohos.util.TreeSet.d.ts|
|API从不支持元服务到支持元服务|类名：TreeSet；<br>API声明：clear(): void;<br>差异内容：NA|类名：TreeSet；<br>API声明：clear(): void;<br>差异内容：atomicservice|api/@ohos.util.TreeSet.d.ts|
|API从不支持元服务到支持元服务|类名：TreeSet；<br>API声明：getFirstValue(): T;<br>差异内容：NA|类名：TreeSet；<br>API声明：getFirstValue(): T;<br>差异内容：atomicservice|api/@ohos.util.TreeSet.d.ts|
|API从不支持元服务到支持元服务|类名：TreeSet；<br>API声明：getLastValue(): T;<br>差异内容：NA|类名：TreeSet；<br>API声明：getLastValue(): T;<br>差异内容：atomicservice|api/@ohos.util.TreeSet.d.ts|
|API从不支持元服务到支持元服务|类名：TreeSet；<br>API声明：getLowerValue(key: T): T;<br>差异内容：NA|类名：TreeSet；<br>API声明：getLowerValue(key: T): T;<br>差异内容：atomicservice|api/@ohos.util.TreeSet.d.ts|
|API从不支持元服务到支持元服务|类名：TreeSet；<br>API声明：getHigherValue(key: T): T;<br>差异内容：NA|类名：TreeSet；<br>API声明：getHigherValue(key: T): T;<br>差异内容：atomicservice|api/@ohos.util.TreeSet.d.ts|
|API从不支持元服务到支持元服务|类名：TreeSet；<br>API声明：popFirst(): T;<br>差异内容：NA|类名：TreeSet；<br>API声明：popFirst(): T;<br>差异内容：atomicservice|api/@ohos.util.TreeSet.d.ts|
|API从不支持元服务到支持元服务|类名：TreeSet；<br>API声明：popLast(): T;<br>差异内容：NA|类名：TreeSet；<br>API声明：popLast(): T;<br>差异内容：atomicservice|api/@ohos.util.TreeSet.d.ts|
|API从不支持元服务到支持元服务|类名：TreeSet；<br>API声明：forEach(callbackFn: (value?: T, key?: T, set?: TreeSet\<T>) => void, thisArg?: Object): void;<br>差异内容：NA|类名：TreeSet；<br>API声明：forEach(callbackFn: (value?: T, key?: T, set?: TreeSet\<T>) => void, thisArg?: Object): void;<br>差异内容：atomicservice|api/@ohos.util.TreeSet.d.ts|
|API从不支持元服务到支持元服务|类名：TreeSet；<br>API声明：values(): IterableIterator\<T>;<br>差异内容：NA|类名：TreeSet；<br>API声明：values(): IterableIterator\<T>;<br>差异内容：atomicservice|api/@ohos.util.TreeSet.d.ts|
|API从不支持元服务到支持元服务|类名：TreeSet；<br>API声明：entries(): IterableIterator\<[<br>        T,<br>        T<br>    ]>;<br>差异内容：NA|类名：TreeSet；<br>API声明：entries(): IterableIterator\<[<br>        T,<br>        T<br>    ]>;<br>差异内容：atomicservice|api/@ohos.util.TreeSet.d.ts|
|API从不支持元服务到支持元服务|类名：TreeSet；<br>API声明：[Symbol.iterator](): IterableIterator\<T>;<br>差异内容：NA|类名：TreeSet；<br>API声明：[Symbol.iterator](): IterableIterator\<T>;<br>差异内容：atomicservice|api/@ohos.util.TreeSet.d.ts|
|API从不支持元服务到支持元服务|类名：WorkerOptions；<br>API声明：shared?: boolean;<br>差异内容：NA|类名：WorkerOptions；<br>API声明：shared?: boolean;<br>差异内容：atomicservice|api/@ohos.worker.d.ts|
|API从不支持元服务到支持元服务|类名：Event；<br>API声明：readonly type: string;<br>差异内容：NA|类名：Event；<br>API声明：readonly type: string;<br>差异内容：atomicservice|api/@ohos.worker.d.ts|
|API从不支持元服务到支持元服务|类名：Event；<br>API声明：readonly timeStamp: number;<br>差异内容：NA|类名：Event；<br>API声明：readonly timeStamp: number;<br>差异内容：atomicservice|api/@ohos.worker.d.ts|
|API从不支持元服务到支持元服务|类名：global；<br>API声明：export interface MessageEvent<br>差异内容：NA|类名：global；<br>API声明：export interface MessageEvent<br>差异内容：atomicservice|api/@ohos.worker.d.ts|
|API从不支持元服务到支持元服务|类名：MessageEvent；<br>API声明：readonly data: T;<br>差异内容：NA|类名：MessageEvent；<br>API声明：readonly data: T;<br>差异内容：atomicservice|api/@ohos.worker.d.ts|
|API从不支持元服务到支持元服务|类名：global；<br>API声明：export interface WorkerEventListener<br>差异内容：NA|类名：global；<br>API声明：export interface WorkerEventListener<br>差异内容：atomicservice|api/@ohos.worker.d.ts|
|API从不支持元服务到支持元服务|类名：global；<br>API声明：type MessageType = 'message' \| 'messageerror';<br>差异内容：NA|类名：global；<br>API声明：type MessageType = 'message' \| 'messageerror';<br>差异内容：atomicservice|api/@ohos.worker.d.ts|
|API从不支持元服务到支持元服务|类名：WorkerEventTarget；<br>API声明：addEventListener(type: string, listener: WorkerEventListener): void;<br>差异内容：NA|类名：WorkerEventTarget；<br>API声明：addEventListener(type: string, listener: WorkerEventListener): void;<br>差异内容：atomicservice|api/@ohos.worker.d.ts|
|API从不支持元服务到支持元服务|类名：WorkerEventTarget；<br>API声明：dispatchEvent(event: Event): boolean;<br>差异内容：NA|类名：WorkerEventTarget；<br>API声明：dispatchEvent(event: Event): boolean;<br>差异内容：atomicservice|api/@ohos.worker.d.ts|
|API从不支持元服务到支持元服务|类名：WorkerEventTarget；<br>API声明：removeEventListener(type: string, callback?: WorkerEventListener): void;<br>差异内容：NA|类名：WorkerEventTarget；<br>API声明：removeEventListener(type: string, callback?: WorkerEventListener): void;<br>差异内容：atomicservice|api/@ohos.worker.d.ts|
|API从不支持元服务到支持元服务|类名：WorkerEventTarget；<br>API声明：removeAllListener(): void;<br>差异内容：NA|类名：WorkerEventTarget；<br>API声明：removeAllListener(): void;<br>差异内容：atomicservice|api/@ohos.worker.d.ts|
|API从不支持元服务到支持元服务|类名：ThreadWorkerGlobalScope；<br>API声明：callGlobalCallObjectMethod(instanceName: string, methodName: string, timeout: number, ...args: Object[]): Object;<br>差异内容：NA|类名：ThreadWorkerGlobalScope；<br>API声明：callGlobalCallObjectMethod(instanceName: string, methodName: string, timeout: number, ...args: Object[]): Object;<br>差异内容：atomicservice|api/@ohos.worker.d.ts|
|API从不支持元服务到支持元服务|类名：ThreadWorker；<br>API声明：on(type: string, listener: WorkerEventListener): void;<br>差异内容：NA|类名：ThreadWorker；<br>API声明：on(type: string, listener: WorkerEventListener): void;<br>差异内容：atomicservice|api/@ohos.worker.d.ts|
|API从不支持元服务到支持元服务|类名：ThreadWorker；<br>API声明：once(type: string, listener: WorkerEventListener): void;<br>差异内容：NA|类名：ThreadWorker；<br>API声明：once(type: string, listener: WorkerEventListener): void;<br>差异内容：atomicservice|api/@ohos.worker.d.ts|
|API从不支持元服务到支持元服务|类名：ThreadWorker；<br>API声明：off(type: string, listener?: WorkerEventListener): void;<br>差异内容：NA|类名：ThreadWorker；<br>API声明：off(type: string, listener?: WorkerEventListener): void;<br>差异内容：atomicservice|api/@ohos.worker.d.ts|
|API从不支持元服务到支持元服务|类名：ThreadWorker；<br>API声明：addEventListener(type: string, listener: WorkerEventListener): void;<br>差异内容：NA|类名：ThreadWorker；<br>API声明：addEventListener(type: string, listener: WorkerEventListener): void;<br>差异内容：atomicservice|api/@ohos.worker.d.ts|
|API从不支持元服务到支持元服务|类名：ThreadWorker；<br>API声明：dispatchEvent(event: Event): boolean;<br>差异内容：NA|类名：ThreadWorker；<br>API声明：dispatchEvent(event: Event): boolean;<br>差异内容：atomicservice|api/@ohos.worker.d.ts|
|API从不支持元服务到支持元服务|类名：ThreadWorker；<br>API声明：removeEventListener(type: string, callback?: WorkerEventListener): void;<br>差异内容：NA|类名：ThreadWorker；<br>API声明：removeEventListener(type: string, callback?: WorkerEventListener): void;<br>差异内容：atomicservice|api/@ohos.worker.d.ts|
|API从不支持元服务到支持元服务|类名：ThreadWorker；<br>API声明：removeAllListener(): void;<br>差异内容：NA|类名：ThreadWorker；<br>API声明：removeAllListener(): void;<br>差异内容：atomicservice|api/@ohos.worker.d.ts|
|API从不支持元服务到支持元服务|类名：ThreadWorker；<br>API声明：registerGlobalCallObject(instanceName: string, globalCallObject: Object): void;<br>差异内容：NA|类名：ThreadWorker；<br>API声明：registerGlobalCallObject(instanceName: string, globalCallObject: Object): void;<br>差异内容：atomicservice|api/@ohos.worker.d.ts|
|API从不支持元服务到支持元服务|类名：ThreadWorker；<br>API声明：unregisterGlobalCallObject(instanceName?: string): void;<br>差异内容：NA|类名：ThreadWorker；<br>API声明：unregisterGlobalCallObject(instanceName?: string): void;<br>差异内容：atomicservice|api/@ohos.worker.d.ts|
