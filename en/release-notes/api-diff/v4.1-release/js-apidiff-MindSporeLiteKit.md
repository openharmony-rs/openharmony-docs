| Change Type | Old Version | New Version | d.ts File |
| ---- | ------ | ------ | -------- |
|New API |NA|Class name: global;<br>API declaration: declare namespace mindSporeLite<br>Differences: declare namespace mindSporeLite|api/@ohos.ai.mindSporeLite.d.ts|
|New API |NA|Class name: mindSporeLite;<br>API declaration: function loadModelFromFile(model: string, context?: Context): Promise\<Model>;<br>Differences: function loadModelFromFile(model: string, context?: Context): Promise\<Model>;|api/@ohos.ai.mindSporeLite.d.ts|
|New API |NA|Class name: mindSporeLite;<br>API declaration: function loadModelFromFile(model: string, callback: Callback\<Model>): void;<br>Differences: function loadModelFromFile(model: string, callback: Callback\<Model>): void;|api/@ohos.ai.mindSporeLite.d.ts|
|New API |NA|Class name: mindSporeLite;<br>API declaration: function loadModelFromFile(model: string, context: Context, callback: Callback\<Model>): void;<br>Differences: function loadModelFromFile(model: string, context: Context, callback: Callback\<Model>): void;|api/@ohos.ai.mindSporeLite.d.ts|
|New API |NA|Class name: mindSporeLite;<br>API declaration: function loadModelFromBuffer(model: ArrayBuffer, context?: Context): Promise\<Model>;<br>Differences: function loadModelFromBuffer(model: ArrayBuffer, context?: Context): Promise\<Model>;|api/@ohos.ai.mindSporeLite.d.ts|
|New API |NA|Class name: mindSporeLite;<br>API declaration: function loadModelFromBuffer(model: ArrayBuffer, callback: Callback\<Model>): void;<br>Differences: function loadModelFromBuffer(model: ArrayBuffer, callback: Callback\<Model>): void;|api/@ohos.ai.mindSporeLite.d.ts|
|New API |NA|Class name: mindSporeLite;<br>API declaration: function loadModelFromBuffer(model: ArrayBuffer, context: Context, callback: Callback\<Model>): void;<br>Differences: function loadModelFromBuffer(model: ArrayBuffer, context: Context, callback: Callback\<Model>): void;|api/@ohos.ai.mindSporeLite.d.ts|
|New API |NA|Class name: mindSporeLite;<br>API declaration: function loadModelFromFd(model: number, context?: Context): Promise\<Model>;<br>Differences: function loadModelFromFd(model: number, context?: Context): Promise\<Model>;|api/@ohos.ai.mindSporeLite.d.ts|
|New API |NA|Class name: mindSporeLite;<br>API declaration: function loadModelFromFd(model: number, callback: Callback\<Model>): void;<br>Differences: function loadModelFromFd(model: number, callback: Callback\<Model>): void;|api/@ohos.ai.mindSporeLite.d.ts|
|New API |NA|Class name: mindSporeLite;<br>API declaration: function loadModelFromFd(model: number, context: Context, callback: Callback\<Model>): void;<br>Differences: function loadModelFromFd(model: number, context: Context, callback: Callback\<Model>): void;|api/@ohos.ai.mindSporeLite.d.ts|
|New API |NA|Class name: mindSporeLite;<br>API declaration: interface Model<br>Differences: interface Model|api/@ohos.ai.mindSporeLite.d.ts|
|New API |NA|Class name: Model;<br>API declaration: getInputs(): MSTensor[];<br>Differences: getInputs(): MSTensor[];|api/@ohos.ai.mindSporeLite.d.ts|
|New API |NA|Class name: Model;<br>API declaration: predict(inputs: MSTensor[], callback: Callback\<MSTensor[]>): void;<br>Differences: predict(inputs: MSTensor[], callback: Callback\<MSTensor[]>): void;|api/@ohos.ai.mindSporeLite.d.ts|
|New API |NA|Class name: Model;<br>API declaration: predict(inputs: MSTensor[]): Promise\<MSTensor[]>;<br>Differences: predict(inputs: MSTensor[]): Promise\<MSTensor[]>;|api/@ohos.ai.mindSporeLite.d.ts|
|New API |NA|Class name: Model;<br>API declaration: resize(inputs: MSTensor[], dims: Array\<Array\<number>>): boolean;<br>Differences: resize(inputs: MSTensor[], dims: Array\<Array\<number>>): boolean;|api/@ohos.ai.mindSporeLite.d.ts|
|New API |NA|Class name: mindSporeLite;<br>API declaration: interface Context<br>Differences: interface Context|api/@ohos.ai.mindSporeLite.d.ts|
|New API |NA|Class name: Context;<br>API declaration: target?: string[];<br>Differences: target?: string[];|api/@ohos.ai.mindSporeLite.d.ts|
|New API |NA|Class name: Context;<br>API declaration: cpu?: CpuDevice;<br>Differences: cpu?: CpuDevice;|api/@ohos.ai.mindSporeLite.d.ts|
|New API |NA|Class name: Context;<br>API declaration: nnrt?: NNRTDevice;<br>Differences: nnrt?: NNRTDevice;|api/@ohos.ai.mindSporeLite.d.ts|
|New API |NA|Class name: mindSporeLite;<br>API declaration: interface CpuDevice<br>Differences: interface CpuDevice|api/@ohos.ai.mindSporeLite.d.ts|
|New API |NA|Class name: CpuDevice;<br>API declaration: threadNum?: number;<br>Differences: threadNum?: number;|api/@ohos.ai.mindSporeLite.d.ts|
|New API |NA|Class name: CpuDevice;<br>API declaration: threadAffinityMode?: ThreadAffinityMode;<br>Differences: threadAffinityMode?: ThreadAffinityMode;|api/@ohos.ai.mindSporeLite.d.ts|
|New API |NA|Class name: CpuDevice;<br>API declaration: threadAffinityCoreList?: number[];<br>Differences: threadAffinityCoreList?: number[];|api/@ohos.ai.mindSporeLite.d.ts|
|New API |NA|Class name: CpuDevice;<br>API declaration: precisionMode?: string;<br>Differences: precisionMode?: string;|api/@ohos.ai.mindSporeLite.d.ts|
|New API |NA|Class name: mindSporeLite;<br>API declaration: interface NNRTDevice<br>Differences: interface NNRTDevice|api/@ohos.ai.mindSporeLite.d.ts|
|New API |NA|Class name: mindSporeLite;<br>API declaration: export enum ThreadAffinityMode<br>Differences: export enum ThreadAffinityMode|api/@ohos.ai.mindSporeLite.d.ts|
|New API |NA|Class name: ThreadAffinityMode;<br>API declaration: NO_AFFINITIES = 0<br>Differences: NO_AFFINITIES = 0|api/@ohos.ai.mindSporeLite.d.ts|
|New API |NA|Class name: ThreadAffinityMode;<br>API declaration: BIG_CORES_FIRST = 1<br>Differences: BIG_CORES_FIRST = 1|api/@ohos.ai.mindSporeLite.d.ts|
|New API |NA|Class name: ThreadAffinityMode;<br>API declaration: LITTLE_CORES_FIRST = 2<br>Differences: LITTLE_CORES_FIRST = 2|api/@ohos.ai.mindSporeLite.d.ts|
|New API |NA|Class name: mindSporeLite;<br>API declaration: interface MSTensor<br>Differences: interface MSTensor|api/@ohos.ai.mindSporeLite.d.ts|
|New API |NA|Class name: MSTensor;<br>API declaration: name: string;<br>Differences: name: string;|api/@ohos.ai.mindSporeLite.d.ts|
|New API |NA|Class name: MSTensor;<br>API declaration: shape: number[];<br>Differences: shape: number[];|api/@ohos.ai.mindSporeLite.d.ts|
|New API |NA|Class name: MSTensor;<br>API declaration: elementNum: number;<br>Differences: elementNum: number;|api/@ohos.ai.mindSporeLite.d.ts|
|New API |NA|Class name: MSTensor;<br>API declaration: dataSize: number;<br>Differences: dataSize: number;|api/@ohos.ai.mindSporeLite.d.ts|
|New API |NA|Class name: MSTensor;<br>API declaration: dtype: DataType;<br>Differences: dtype: DataType;|api/@ohos.ai.mindSporeLite.d.ts|
|New API |NA|Class name: MSTensor;<br>API declaration: format: Format;<br>Differences: format: Format;|api/@ohos.ai.mindSporeLite.d.ts|
|New API |NA|Class name: MSTensor;<br>API declaration: getData(): ArrayBuffer;<br>Differences: getData(): ArrayBuffer;|api/@ohos.ai.mindSporeLite.d.ts|
|New API |NA|Class name: MSTensor;<br>API declaration: setData(inputArray: ArrayBuffer): void;<br>Differences: setData(inputArray: ArrayBuffer): void;|api/@ohos.ai.mindSporeLite.d.ts|
|New API |NA|Class name: mindSporeLite;<br>API declaration: export enum DataType<br>Differences: export enum DataType|api/@ohos.ai.mindSporeLite.d.ts|
|New API |NA|Class name: DataType;<br>API declaration: TYPE_UNKNOWN = 0<br>Differences: TYPE_UNKNOWN = 0|api/@ohos.ai.mindSporeLite.d.ts|
|New API |NA|Class name: DataType;<br>API declaration: NUMBER_TYPE_INT8 = 32<br>Differences: NUMBER_TYPE_INT8 = 32|api/@ohos.ai.mindSporeLite.d.ts|
|New API |NA|Class name: DataType;<br>API declaration: NUMBER_TYPE_INT16 = 33<br>Differences: NUMBER_TYPE_INT16 = 33|api/@ohos.ai.mindSporeLite.d.ts|
|New API |NA|Class name: DataType;<br>API declaration: NUMBER_TYPE_INT32 = 34<br>Differences: NUMBER_TYPE_INT32 = 34|api/@ohos.ai.mindSporeLite.d.ts|
|New API |NA|Class name: DataType;<br>API declaration: NUMBER_TYPE_INT64 = 35<br>Differences: NUMBER_TYPE_INT64 = 35|api/@ohos.ai.mindSporeLite.d.ts|
|New API |NA|Class name: DataType;<br>API declaration: NUMBER_TYPE_UINT8 = 37<br>Differences: NUMBER_TYPE_UINT8 = 37|api/@ohos.ai.mindSporeLite.d.ts|
|New API |NA|Class name: DataType;<br>API declaration: NUMBER_TYPE_UINT16 = 38<br>Differences: NUMBER_TYPE_UINT16 = 38|api/@ohos.ai.mindSporeLite.d.ts|
|New API |NA|Class name: DataType;<br>API declaration: NUMBER_TYPE_UINT32 = 39<br>Differences: NUMBER_TYPE_UINT32 = 39|api/@ohos.ai.mindSporeLite.d.ts|
|New API |NA|Class name: DataType;<br>API declaration: NUMBER_TYPE_UINT64 = 40<br>Differences: NUMBER_TYPE_UINT64 = 40|api/@ohos.ai.mindSporeLite.d.ts|
|New API |NA|Class name: DataType;<br>API declaration: NUMBER_TYPE_FLOAT16 = 42<br>Differences: NUMBER_TYPE_FLOAT16 = 42|api/@ohos.ai.mindSporeLite.d.ts|
|New API |NA|Class name: DataType;<br>API declaration: NUMBER_TYPE_FLOAT32 = 43<br>Differences: NUMBER_TYPE_FLOAT32 = 43|api/@ohos.ai.mindSporeLite.d.ts|
|New API |NA|Class name: DataType;<br>API declaration: NUMBER_TYPE_FLOAT64 = 44<br>Differences: NUMBER_TYPE_FLOAT64 = 44|api/@ohos.ai.mindSporeLite.d.ts|
|New API |NA|Class name: mindSporeLite;<br>API declaration: export enum Format<br>Differences: export enum Format|api/@ohos.ai.mindSporeLite.d.ts|
|New API |NA|Class name: Format;<br>API declaration: DEFAULT_FORMAT = -1<br>Differences: DEFAULT_FORMAT = -1|api/@ohos.ai.mindSporeLite.d.ts|
|New API |NA|Class name: Format;<br>API declaration: NCHW = 0<br>Differences: NCHW = 0|api/@ohos.ai.mindSporeLite.d.ts|
|New API |NA|Class name: Format;<br>API declaration: NHWC = 1<br>Differences: NHWC = 1|api/@ohos.ai.mindSporeLite.d.ts|
|New API |NA|Class name: Format;<br>API declaration: NHWC4 = 2<br>Differences: NHWC4 = 2|api/@ohos.ai.mindSporeLite.d.ts|
|New API |NA|Class name: Format;<br>API declaration: HWKC = 3<br>Differences: HWKC = 3|api/@ohos.ai.mindSporeLite.d.ts|
|New API |NA|Class name: Format;<br>API declaration: HWCK = 4<br>Differences: HWCK = 4|api/@ohos.ai.mindSporeLite.d.ts|
|New API |NA|Class name: Format;<br>API declaration: KCHW = 5<br>Differences: KCHW = 5|api/@ohos.ai.mindSporeLite.d.ts|
|New Kit|Class name: global;<br>API declaration: <br>Differences: NA|Class name: global;<br>API declaration: api\@ohos.ai.mindSporeLite.d.ts<br>Differences: MindSporeLiteKit|api/@ohos.ai.mindSporeLite.d.ts|
|New Kit|Class name: global;<br>API declaration: <br>Differences: NA|Class name: global;<br>API declaration: kits\@kit.MindSporeLiteKit.d.ts<br>Differences: MindSporeLiteKit|kits/@kit.MindSporeLiteKit.d.ts|
