| 操作 | 旧版本 | 新版本 | d.ts文件 |
| ---- | ------ | ------ | -------- |
|新增API|NA|类名：global；<br>API声明：declare namespace mindSporeLite<br>差异内容：declare namespace mindSporeLite|api/@ohos.ai.mindSporeLite.d.ts|
|新增API|NA|类名：mindSporeLite；<br>API声明：function loadModelFromFile(model: string, context?: Context): Promise\<Model>;<br>差异内容：function loadModelFromFile(model: string, context?: Context): Promise\<Model>;|api/@ohos.ai.mindSporeLite.d.ts|
|新增API|NA|类名：mindSporeLite；<br>API声明：function loadModelFromFile(model: string, callback: Callback\<Model>): void;<br>差异内容：function loadModelFromFile(model: string, callback: Callback\<Model>): void;|api/@ohos.ai.mindSporeLite.d.ts|
|新增API|NA|类名：mindSporeLite；<br>API声明：function loadModelFromFile(model: string, context: Context, callback: Callback\<Model>): void;<br>差异内容：function loadModelFromFile(model: string, context: Context, callback: Callback\<Model>): void;|api/@ohos.ai.mindSporeLite.d.ts|
|新增API|NA|类名：mindSporeLite；<br>API声明：function loadModelFromBuffer(model: ArrayBuffer, context?: Context): Promise\<Model>;<br>差异内容：function loadModelFromBuffer(model: ArrayBuffer, context?: Context): Promise\<Model>;|api/@ohos.ai.mindSporeLite.d.ts|
|新增API|NA|类名：mindSporeLite；<br>API声明：function loadModelFromBuffer(model: ArrayBuffer, callback: Callback\<Model>): void;<br>差异内容：function loadModelFromBuffer(model: ArrayBuffer, callback: Callback\<Model>): void;|api/@ohos.ai.mindSporeLite.d.ts|
|新增API|NA|类名：mindSporeLite；<br>API声明：function loadModelFromBuffer(model: ArrayBuffer, context: Context, callback: Callback\<Model>): void;<br>差异内容：function loadModelFromBuffer(model: ArrayBuffer, context: Context, callback: Callback\<Model>): void;|api/@ohos.ai.mindSporeLite.d.ts|
|新增API|NA|类名：mindSporeLite；<br>API声明：function loadModelFromFd(model: number, context?: Context): Promise\<Model>;<br>差异内容：function loadModelFromFd(model: number, context?: Context): Promise\<Model>;|api/@ohos.ai.mindSporeLite.d.ts|
|新增API|NA|类名：mindSporeLite；<br>API声明：function loadModelFromFd(model: number, callback: Callback\<Model>): void;<br>差异内容：function loadModelFromFd(model: number, callback: Callback\<Model>): void;|api/@ohos.ai.mindSporeLite.d.ts|
|新增API|NA|类名：mindSporeLite；<br>API声明：function loadModelFromFd(model: number, context: Context, callback: Callback\<Model>): void;<br>差异内容：function loadModelFromFd(model: number, context: Context, callback: Callback\<Model>): void;|api/@ohos.ai.mindSporeLite.d.ts|
|新增API|NA|类名：mindSporeLite；<br>API声明：interface Model<br>差异内容：interface Model|api/@ohos.ai.mindSporeLite.d.ts|
|新增API|NA|类名：Model；<br>API声明：getInputs(): MSTensor[];<br>差异内容：getInputs(): MSTensor[];|api/@ohos.ai.mindSporeLite.d.ts|
|新增API|NA|类名：Model；<br>API声明：predict(inputs: MSTensor[], callback: Callback\<MSTensor[]>): void;<br>差异内容：predict(inputs: MSTensor[], callback: Callback\<MSTensor[]>): void;|api/@ohos.ai.mindSporeLite.d.ts|
|新增API|NA|类名：Model；<br>API声明：predict(inputs: MSTensor[]): Promise\<MSTensor[]>;<br>差异内容：predict(inputs: MSTensor[]): Promise\<MSTensor[]>;|api/@ohos.ai.mindSporeLite.d.ts|
|新增API|NA|类名：Model；<br>API声明：resize(inputs: MSTensor[], dims: Array\<Array\<number>>): boolean;<br>差异内容：resize(inputs: MSTensor[], dims: Array\<Array\<number>>): boolean;|api/@ohos.ai.mindSporeLite.d.ts|
|新增API|NA|类名：mindSporeLite；<br>API声明：interface Context<br>差异内容：interface Context|api/@ohos.ai.mindSporeLite.d.ts|
|新增API|NA|类名：Context；<br>API声明：target?: string[];<br>差异内容：target?: string[];|api/@ohos.ai.mindSporeLite.d.ts|
|新增API|NA|类名：Context；<br>API声明：cpu?: CpuDevice;<br>差异内容：cpu?: CpuDevice;|api/@ohos.ai.mindSporeLite.d.ts|
|新增API|NA|类名：Context；<br>API声明：nnrt?: NNRTDevice;<br>差异内容：nnrt?: NNRTDevice;|api/@ohos.ai.mindSporeLite.d.ts|
|新增API|NA|类名：mindSporeLite；<br>API声明：interface CpuDevice<br>差异内容：interface CpuDevice|api/@ohos.ai.mindSporeLite.d.ts|
|新增API|NA|类名：CpuDevice；<br>API声明：threadNum?: number;<br>差异内容：threadNum?: number;|api/@ohos.ai.mindSporeLite.d.ts|
|新增API|NA|类名：CpuDevice；<br>API声明：threadAffinityMode?: ThreadAffinityMode;<br>差异内容：threadAffinityMode?: ThreadAffinityMode;|api/@ohos.ai.mindSporeLite.d.ts|
|新增API|NA|类名：CpuDevice；<br>API声明：threadAffinityCoreList?: number[];<br>差异内容：threadAffinityCoreList?: number[];|api/@ohos.ai.mindSporeLite.d.ts|
|新增API|NA|类名：CpuDevice；<br>API声明：precisionMode?: string;<br>差异内容：precisionMode?: string;|api/@ohos.ai.mindSporeLite.d.ts|
|新增API|NA|类名：mindSporeLite；<br>API声明：interface NNRTDevice<br>差异内容：interface NNRTDevice|api/@ohos.ai.mindSporeLite.d.ts|
|新增API|NA|类名：mindSporeLite；<br>API声明：export enum ThreadAffinityMode<br>差异内容：export enum ThreadAffinityMode|api/@ohos.ai.mindSporeLite.d.ts|
|新增API|NA|类名：ThreadAffinityMode；<br>API声明：NO_AFFINITIES = 0<br>差异内容：NO_AFFINITIES = 0|api/@ohos.ai.mindSporeLite.d.ts|
|新增API|NA|类名：ThreadAffinityMode；<br>API声明：BIG_CORES_FIRST = 1<br>差异内容：BIG_CORES_FIRST = 1|api/@ohos.ai.mindSporeLite.d.ts|
|新增API|NA|类名：ThreadAffinityMode；<br>API声明：LITTLE_CORES_FIRST = 2<br>差异内容：LITTLE_CORES_FIRST = 2|api/@ohos.ai.mindSporeLite.d.ts|
|新增API|NA|类名：mindSporeLite；<br>API声明：interface MSTensor<br>差异内容：interface MSTensor|api/@ohos.ai.mindSporeLite.d.ts|
|新增API|NA|类名：MSTensor；<br>API声明：name: string;<br>差异内容：name: string;|api/@ohos.ai.mindSporeLite.d.ts|
|新增API|NA|类名：MSTensor；<br>API声明：shape: number[];<br>差异内容：shape: number[];|api/@ohos.ai.mindSporeLite.d.ts|
|新增API|NA|类名：MSTensor；<br>API声明：elementNum: number;<br>差异内容：elementNum: number;|api/@ohos.ai.mindSporeLite.d.ts|
|新增API|NA|类名：MSTensor；<br>API声明：dataSize: number;<br>差异内容：dataSize: number;|api/@ohos.ai.mindSporeLite.d.ts|
|新增API|NA|类名：MSTensor；<br>API声明：dtype: DataType;<br>差异内容：dtype: DataType;|api/@ohos.ai.mindSporeLite.d.ts|
|新增API|NA|类名：MSTensor；<br>API声明：format: Format;<br>差异内容：format: Format;|api/@ohos.ai.mindSporeLite.d.ts|
|新增API|NA|类名：MSTensor；<br>API声明：getData(): ArrayBuffer;<br>差异内容：getData(): ArrayBuffer;|api/@ohos.ai.mindSporeLite.d.ts|
|新增API|NA|类名：MSTensor；<br>API声明：setData(inputArray: ArrayBuffer): void;<br>差异内容：setData(inputArray: ArrayBuffer): void;|api/@ohos.ai.mindSporeLite.d.ts|
|新增API|NA|类名：mindSporeLite；<br>API声明：export enum DataType<br>差异内容：export enum DataType|api/@ohos.ai.mindSporeLite.d.ts|
|新增API|NA|类名：DataType；<br>API声明：TYPE_UNKNOWN = 0<br>差异内容：TYPE_UNKNOWN = 0|api/@ohos.ai.mindSporeLite.d.ts|
|新增API|NA|类名：DataType；<br>API声明：NUMBER_TYPE_INT8 = 32<br>差异内容：NUMBER_TYPE_INT8 = 32|api/@ohos.ai.mindSporeLite.d.ts|
|新增API|NA|类名：DataType；<br>API声明：NUMBER_TYPE_INT16 = 33<br>差异内容：NUMBER_TYPE_INT16 = 33|api/@ohos.ai.mindSporeLite.d.ts|
|新增API|NA|类名：DataType；<br>API声明：NUMBER_TYPE_INT32 = 34<br>差异内容：NUMBER_TYPE_INT32 = 34|api/@ohos.ai.mindSporeLite.d.ts|
|新增API|NA|类名：DataType；<br>API声明：NUMBER_TYPE_INT64 = 35<br>差异内容：NUMBER_TYPE_INT64 = 35|api/@ohos.ai.mindSporeLite.d.ts|
|新增API|NA|类名：DataType；<br>API声明：NUMBER_TYPE_UINT8 = 37<br>差异内容：NUMBER_TYPE_UINT8 = 37|api/@ohos.ai.mindSporeLite.d.ts|
|新增API|NA|类名：DataType；<br>API声明：NUMBER_TYPE_UINT16 = 38<br>差异内容：NUMBER_TYPE_UINT16 = 38|api/@ohos.ai.mindSporeLite.d.ts|
|新增API|NA|类名：DataType；<br>API声明：NUMBER_TYPE_UINT32 = 39<br>差异内容：NUMBER_TYPE_UINT32 = 39|api/@ohos.ai.mindSporeLite.d.ts|
|新增API|NA|类名：DataType；<br>API声明：NUMBER_TYPE_UINT64 = 40<br>差异内容：NUMBER_TYPE_UINT64 = 40|api/@ohos.ai.mindSporeLite.d.ts|
|新增API|NA|类名：DataType；<br>API声明：NUMBER_TYPE_FLOAT16 = 42<br>差异内容：NUMBER_TYPE_FLOAT16 = 42|api/@ohos.ai.mindSporeLite.d.ts|
|新增API|NA|类名：DataType；<br>API声明：NUMBER_TYPE_FLOAT32 = 43<br>差异内容：NUMBER_TYPE_FLOAT32 = 43|api/@ohos.ai.mindSporeLite.d.ts|
|新增API|NA|类名：DataType；<br>API声明：NUMBER_TYPE_FLOAT64 = 44<br>差异内容：NUMBER_TYPE_FLOAT64 = 44|api/@ohos.ai.mindSporeLite.d.ts|
|新增API|NA|类名：mindSporeLite；<br>API声明：export enum Format<br>差异内容：export enum Format|api/@ohos.ai.mindSporeLite.d.ts|
|新增API|NA|类名：Format；<br>API声明：DEFAULT_FORMAT = -1<br>差异内容：DEFAULT_FORMAT = -1|api/@ohos.ai.mindSporeLite.d.ts|
|新增API|NA|类名：Format；<br>API声明：NCHW = 0<br>差异内容：NCHW = 0|api/@ohos.ai.mindSporeLite.d.ts|
|新增API|NA|类名：Format；<br>API声明：NHWC = 1<br>差异内容：NHWC = 1|api/@ohos.ai.mindSporeLite.d.ts|
|新增API|NA|类名：Format；<br>API声明：NHWC4 = 2<br>差异内容：NHWC4 = 2|api/@ohos.ai.mindSporeLite.d.ts|
|新增API|NA|类名：Format；<br>API声明：HWKC = 3<br>差异内容：HWKC = 3|api/@ohos.ai.mindSporeLite.d.ts|
|新增API|NA|类名：Format；<br>API声明：HWCK = 4<br>差异内容：HWCK = 4|api/@ohos.ai.mindSporeLite.d.ts|
|新增API|NA|类名：Format；<br>API声明：KCHW = 5<br>差异内容：KCHW = 5|api/@ohos.ai.mindSporeLite.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\@ohos.ai.mindSporeLite.d.ts<br>差异内容：MindSporeLiteKit|api/@ohos.ai.mindSporeLite.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：kits\@kit.MindSporeLiteKit.d.ts<br>差异内容：MindSporeLiteKit|kits/@kit.MindSporeLiteKit.d.ts|
