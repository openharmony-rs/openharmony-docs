| 操作 | 旧版本 | 新版本 | d.ts文件 |
| ---- | ------ | ------ | -------- |
|新增API|NA|类名：global；<br>API声明：declare namespace jsLeakWatcher<br>差异内容：declare namespace jsLeakWatcher|api/@ohos.hiviewdfx.jsLeakWatcher.d.ts|
|新增API|NA|类名：jsLeakWatcher；<br>API声明：function enable(isEnable: boolean): void;<br>差异内容：function enable(isEnable: boolean): void;|api/@ohos.hiviewdfx.jsLeakWatcher.d.ts|
|新增API|NA|类名：jsLeakWatcher；<br>API声明：function watch(obj: object, msg: string): void;<br>差异内容：function watch(obj: object, msg: string): void;|api/@ohos.hiviewdfx.jsLeakWatcher.d.ts|
|新增API|NA|类名：jsLeakWatcher；<br>API声明：function check(): string;<br>差异内容：function check(): string;|api/@ohos.hiviewdfx.jsLeakWatcher.d.ts|
|新增API|NA|类名：jsLeakWatcher；<br>API声明：function dump(filePath: string): Array\<string>;<br>差异内容：function dump(filePath: string): Array\<string>;|api/@ohos.hiviewdfx.jsLeakWatcher.d.ts|
|新增API|NA|类名：hidebug；<br>API声明：function getSystemCpuUsage(): number;<br>差异内容：function getSystemCpuUsage(): number;|api/@ohos.hidebug.d.ts|
|新增API|NA|类名：hidebug；<br>API声明：interface ThreadCpuUsage<br>差异内容：interface ThreadCpuUsage|api/@ohos.hidebug.d.ts|
|新增API|NA|类名：ThreadCpuUsage；<br>API声明：threadId: number;<br>差异内容：threadId: number;|api/@ohos.hidebug.d.ts|
|新增API|NA|类名：ThreadCpuUsage；<br>API声明：cpuUsage: number;<br>差异内容：cpuUsage: number;|api/@ohos.hidebug.d.ts|
|新增API|NA|类名：hidebug；<br>API声明：function getAppThreadCpuUsage(): ThreadCpuUsage[];<br>差异内容：function getAppThreadCpuUsage(): ThreadCpuUsage[];|api/@ohos.hidebug.d.ts|
|新增API|NA|类名：hidebug；<br>API声明：interface SystemMemInfo<br>差异内容：interface SystemMemInfo|api/@ohos.hidebug.d.ts|
|新增API|NA|类名：SystemMemInfo；<br>API声明：totalMem: bigint;<br>差异内容：totalMem: bigint;|api/@ohos.hidebug.d.ts|
|新增API|NA|类名：SystemMemInfo；<br>API声明：freeMem: bigint;<br>差异内容：freeMem: bigint;|api/@ohos.hidebug.d.ts|
|新增API|NA|类名：SystemMemInfo；<br>API声明：availableMem: bigint;<br>差异内容：availableMem: bigint;|api/@ohos.hidebug.d.ts|
|新增API|NA|类名：hidebug；<br>API声明：function getSystemMemInfo(): SystemMemInfo;<br>差异内容：function getSystemMemInfo(): SystemMemInfo;|api/@ohos.hidebug.d.ts|
|新增API|NA|类名：hidebug；<br>API声明：interface NativeMemInfo<br>差异内容：interface NativeMemInfo|api/@ohos.hidebug.d.ts|
|新增API|NA|类名：NativeMemInfo；<br>API声明：pss: bigint;<br>差异内容：pss: bigint;|api/@ohos.hidebug.d.ts|
|新增API|NA|类名：NativeMemInfo；<br>API声明：vss: bigint;<br>差异内容：vss: bigint;|api/@ohos.hidebug.d.ts|
|新增API|NA|类名：NativeMemInfo；<br>API声明：rss: bigint;<br>差异内容：rss: bigint;|api/@ohos.hidebug.d.ts|
|新增API|NA|类名：NativeMemInfo；<br>API声明：sharedDirty: bigint;<br>差异内容：sharedDirty: bigint;|api/@ohos.hidebug.d.ts|
|新增API|NA|类名：NativeMemInfo；<br>API声明：privateDirty: bigint;<br>差异内容：privateDirty: bigint;|api/@ohos.hidebug.d.ts|
|新增API|NA|类名：NativeMemInfo；<br>API声明：sharedClean: bigint;<br>差异内容：sharedClean: bigint;|api/@ohos.hidebug.d.ts|
|新增API|NA|类名：NativeMemInfo；<br>API声明：privateClean: bigint;<br>差异内容：privateClean: bigint;|api/@ohos.hidebug.d.ts|
|新增API|NA|类名：hidebug；<br>API声明：function getAppNativeMemInfo(): NativeMemInfo;<br>差异内容：function getAppNativeMemInfo(): NativeMemInfo;|api/@ohos.hidebug.d.ts|
|新增API|NA|类名：hidebug；<br>API声明：interface MemoryLimit<br>差异内容：interface MemoryLimit|api/@ohos.hidebug.d.ts|
|新增API|NA|类名：MemoryLimit；<br>API声明：rssLimit: bigint;<br>差异内容：rssLimit: bigint;|api/@ohos.hidebug.d.ts|
|新增API|NA|类名：MemoryLimit；<br>API声明：vssLimit: bigint;<br>差异内容：vssLimit: bigint;|api/@ohos.hidebug.d.ts|
|新增API|NA|类名：MemoryLimit；<br>API声明：vmHeapLimit: bigint;<br>差异内容：vmHeapLimit: bigint;|api/@ohos.hidebug.d.ts|
|新增API|NA|类名：MemoryLimit；<br>API声明：vmTotalHeapSize: bigint;<br>差异内容：vmTotalHeapSize: bigint;|api/@ohos.hidebug.d.ts|
|新增API|NA|类名：hidebug；<br>API声明：function getAppMemoryLimit(): MemoryLimit;<br>差异内容：function getAppMemoryLimit(): MemoryLimit;|api/@ohos.hidebug.d.ts|
|新增API|NA|类名：hidebug；<br>API声明：interface VMMemoryInfo<br>差异内容：interface VMMemoryInfo|api/@ohos.hidebug.d.ts|
|新增API|NA|类名：VMMemoryInfo；<br>API声明：totalHeap: bigint;<br>差异内容：totalHeap: bigint;|api/@ohos.hidebug.d.ts|
|新增API|NA|类名：VMMemoryInfo；<br>API声明：heapUsed: bigint;<br>差异内容：heapUsed: bigint;|api/@ohos.hidebug.d.ts|
|新增API|NA|类名：VMMemoryInfo；<br>API声明：allArraySize: bigint;<br>差异内容：allArraySize: bigint;|api/@ohos.hidebug.d.ts|
|新增API|NA|类名：hidebug；<br>API声明：function getAppVMMemoryInfo(): VMMemoryInfo;<br>差异内容：function getAppVMMemoryInfo(): VMMemoryInfo;|api/@ohos.hidebug.d.ts|
|新增API|NA|类名：hidebug；<br>API声明：enum TraceFlag<br>差异内容：enum TraceFlag|api/@ohos.hidebug.d.ts|
|新增API|NA|类名：TraceFlag；<br>API声明：MAIN_THREAD = 1<br>差异内容：MAIN_THREAD = 1|api/@ohos.hidebug.d.ts|
|新增API|NA|类名：TraceFlag；<br>API声明：ALL_THREADS = 2<br>差异内容：ALL_THREADS = 2|api/@ohos.hidebug.d.ts|
|新增API|NA|类名：hidebug；<br>API声明：namespace tags<br>差异内容：namespace tags|api/@ohos.hidebug.d.ts|
|新增API|NA|类名：tags；<br>API声明：const ABILITY_MANAGER: number;<br>差异内容：const ABILITY_MANAGER: number;|api/@ohos.hidebug.d.ts|
|新增API|NA|类名：tags；<br>API声明：const ARKUI: number;<br>差异内容：const ARKUI: number;|api/@ohos.hidebug.d.ts|
|新增API|NA|类名：tags；<br>API声明：const ARK: number;<br>差异内容：const ARK: number;|api/@ohos.hidebug.d.ts|
|新增API|NA|类名：tags；<br>API声明：const BLUETOOTH: number;<br>差异内容：const BLUETOOTH: number;|api/@ohos.hidebug.d.ts|
|新增API|NA|类名：tags；<br>API声明：const COMMON_LIBRARY: number;<br>差异内容：const COMMON_LIBRARY: number;|api/@ohos.hidebug.d.ts|
|新增API|NA|类名：tags；<br>API声明：const DISTRIBUTED_HARDWARE_DEVICE_MANAGER: number;<br>差异内容：const DISTRIBUTED_HARDWARE_DEVICE_MANAGER: number;|api/@ohos.hidebug.d.ts|
|新增API|NA|类名：tags；<br>API声明：const DISTRIBUTED_AUDIO: number;<br>差异内容：const DISTRIBUTED_AUDIO: number;|api/@ohos.hidebug.d.ts|
|新增API|NA|类名：tags；<br>API声明：const DISTRIBUTED_CAMERA: number;<br>差异内容：const DISTRIBUTED_CAMERA: number;|api/@ohos.hidebug.d.ts|
|新增API|NA|类名：tags；<br>API声明：const DISTRIBUTED_DATA: number;<br>差异内容：const DISTRIBUTED_DATA: number;|api/@ohos.hidebug.d.ts|
|新增API|NA|类名：tags；<br>API声明：const DISTRIBUTED_HARDWARE_FRAMEWORK: number;<br>差异内容：const DISTRIBUTED_HARDWARE_FRAMEWORK: number;|api/@ohos.hidebug.d.ts|
|新增API|NA|类名：tags；<br>API声明：const DISTRIBUTED_INPUT: number;<br>差异内容：const DISTRIBUTED_INPUT: number;|api/@ohos.hidebug.d.ts|
|新增API|NA|类名：tags；<br>API声明：const DISTRIBUTED_SCREEN: number;<br>差异内容：const DISTRIBUTED_SCREEN: number;|api/@ohos.hidebug.d.ts|
|新增API|NA|类名：tags；<br>API声明：const DISTRIBUTED_SCHEDULER: number;<br>差异内容：const DISTRIBUTED_SCHEDULER: number;|api/@ohos.hidebug.d.ts|
|新增API|NA|类名：tags；<br>API声明：const FFRT: number;<br>差异内容：const FFRT: number;|api/@ohos.hidebug.d.ts|
|新增API|NA|类名：tags；<br>API声明：const FILE_MANAGEMENT: number;<br>差异内容：const FILE_MANAGEMENT: number;|api/@ohos.hidebug.d.ts|
|新增API|NA|类名：tags；<br>API声明：const GLOBAL_RESOURCE_MANAGER: number;<br>差异内容：const GLOBAL_RESOURCE_MANAGER: number;|api/@ohos.hidebug.d.ts|
|新增API|NA|类名：tags；<br>API声明：const GRAPHICS: number;<br>差异内容：const GRAPHICS: number;|api/@ohos.hidebug.d.ts|
|新增API|NA|类名：tags；<br>API声明：const HDF: number;<br>差异内容：const HDF: number;|api/@ohos.hidebug.d.ts|
|新增API|NA|类名：tags；<br>API声明：const MISC: number;<br>差异内容：const MISC: number;|api/@ohos.hidebug.d.ts|
|新增API|NA|类名：tags；<br>API声明：const MULTIMODAL_INPUT: number;<br>差异内容：const MULTIMODAL_INPUT: number;|api/@ohos.hidebug.d.ts|
|新增API|NA|类名：tags；<br>API声明：const NET: number;<br>差异内容：const NET: number;|api/@ohos.hidebug.d.ts|
|新增API|NA|类名：tags；<br>API声明：const NOTIFICATION: number;<br>差异内容：const NOTIFICATION: number;|api/@ohos.hidebug.d.ts|
|新增API|NA|类名：tags；<br>API声明：const NWEB: number;<br>差异内容：const NWEB: number;|api/@ohos.hidebug.d.ts|
|新增API|NA|类名：tags；<br>API声明：const OHOS: number;<br>差异内容：const OHOS: number;|api/@ohos.hidebug.d.ts|
|新增API|NA|类名：tags；<br>API声明：const POWER_MANAGER: number;<br>差异内容：const POWER_MANAGER: number;|api/@ohos.hidebug.d.ts|
|新增API|NA|类名：tags；<br>API声明：const RPC: number;<br>差异内容：const RPC: number;|api/@ohos.hidebug.d.ts|
|新增API|NA|类名：tags；<br>API声明：const SAMGR: number;<br>差异内容：const SAMGR: number;|api/@ohos.hidebug.d.ts|
|新增API|NA|类名：tags；<br>API声明：const WINDOW_MANAGER: number;<br>差异内容：const WINDOW_MANAGER: number;|api/@ohos.hidebug.d.ts|
|新增API|NA|类名：tags；<br>API声明：const AUDIO: number;<br>差异内容：const AUDIO: number;|api/@ohos.hidebug.d.ts|
|新增API|NA|类名：tags；<br>API声明：const CAMERA: number;<br>差异内容：const CAMERA: number;|api/@ohos.hidebug.d.ts|
|新增API|NA|类名：tags；<br>API声明：const IMAGE: number;<br>差异内容：const IMAGE: number;|api/@ohos.hidebug.d.ts|
|新增API|NA|类名：tags；<br>API声明：const MEDIA: number;<br>差异内容：const MEDIA: number;|api/@ohos.hidebug.d.ts|
|新增API|NA|类名：hidebug；<br>API声明：function startAppTraceCapture(tags: number[], flag: TraceFlag, limitSize: number): string;<br>差异内容：function startAppTraceCapture(tags: number[], flag: TraceFlag, limitSize: number): string;|api/@ohos.hidebug.d.ts|
|新增API|NA|类名：hidebug；<br>API声明：function stopAppTraceCapture(): void;<br>差异内容：function stopAppTraceCapture(): void;|api/@ohos.hidebug.d.ts|
|新增API|NA|类名：hidebug；<br>API声明：type GcStats = Record\<string, number>;<br>差异内容：type GcStats = Record\<string, number>;|api/@ohos.hidebug.d.ts|
|新增API|NA|类名：hidebug；<br>API声明：function getVMRuntimeStats(): GcStats;<br>差异内容：function getVMRuntimeStats(): GcStats;|api/@ohos.hidebug.d.ts|
|新增API|NA|类名：hidebug；<br>API声明：function getVMRuntimeStat(item: string): number;<br>差异内容：function getVMRuntimeStat(item: string): number;|api/@ohos.hidebug.d.ts|
|新增API|NA|类名：hidebug；<br>API声明：function setAppResourceLimit(type: string, value: number, enableDebugLog: boolean): void;<br>差异内容：function setAppResourceLimit(type: string, value: number, enableDebugLog: boolean): void;|api/@ohos.hidebug.d.ts|
|新增API|NA|类名：hidebug；<br>API声明：function isDebugState(): boolean;<br>差异内容：function isDebugState(): boolean;|api/@ohos.hidebug.d.ts|
|新增API|NA|类名：event；<br>API声明：const APP_LAUNCH: string;<br>差异内容：const APP_LAUNCH: string;|api/@ohos.hiviewdfx.hiAppEvent.d.ts|
|新增API|NA|类名：event；<br>API声明：const SCROLL_JANK: string;<br>差异内容：const SCROLL_JANK: string;|api/@ohos.hiviewdfx.hiAppEvent.d.ts|
|新增API|NA|类名：event；<br>API声明：const CPU_USAGE_HIGH: string;<br>差异内容：const CPU_USAGE_HIGH: string;|api/@ohos.hiviewdfx.hiAppEvent.d.ts|
|新增API|NA|类名：event；<br>API声明：const BATTERY_USAGE: string;<br>差异内容：const BATTERY_USAGE: string;|api/@ohos.hiviewdfx.hiAppEvent.d.ts|
|新增API|NA|类名：event；<br>API声明：const RESOURCE_OVERLIMIT: string;<br>差异内容：const RESOURCE_OVERLIMIT: string;|api/@ohos.hiviewdfx.hiAppEvent.d.ts|
|新增API|NA|类名：event；<br>API声明：const ADDRESS_SANITIZER: string;<br>差异内容：const ADDRESS_SANITIZER: string;|api/@ohos.hiviewdfx.hiAppEvent.d.ts|
|新增API|NA|类名：event；<br>API声明：const MAIN_THREAD_JANK: string;<br>差异内容：const MAIN_THREAD_JANK: string;|api/@ohos.hiviewdfx.hiAppEvent.d.ts|
|新增API|NA|类名：hiAppEvent；<br>API声明：type ParamType = number \| string \| boolean \| Array\<string>;<br>差异内容：type ParamType = number \| string \| boolean \| Array\<string>;|api/@ohos.hiviewdfx.hiAppEvent.d.ts|
|新增API|NA|类名：hiAppEvent；<br>API声明：function setEventParam(params: Record\<string, ParamType>, domain: string, name?: string): Promise\<void>;<br>差异内容：function setEventParam(params: Record\<string, ParamType>, domain: string, name?: string): Promise\<void>;|api/@ohos.hiviewdfx.hiAppEvent.d.ts|
|新增API|NA|类名：AppEventPackage；<br>API声明：appEventInfos: Array\<AppEventInfo>;<br>差异内容：appEventInfos: Array\<AppEventInfo>;|api/@ohos.hiviewdfx.hiAppEvent.d.ts|
|新增API|NA|类名：AppEventPackageHolder；<br>API声明：setRow(size: number): void;<br>差异内容：setRow(size: number): void;|api/@ohos.hiviewdfx.hiAppEvent.d.ts|
|新增API|NA|类名：Processor；<br>API声明：configId?: number;<br>差异内容：configId?: number;|api/@ohos.hiviewdfx.hiAppEvent.d.ts|
|新增API|NA|类名：Processor；<br>API声明：customConfigs?: Record\<string, string>;<br>差异内容：customConfigs?: Record\<string, string>;|api/@ohos.hiviewdfx.hiAppEvent.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\@ohos.hiviewdfx.jsLeakWatcher.d.ts<br>差异内容：PerformanceAnalysisKit|api/@ohos.hiviewdfx.jsLeakWatcher.d.ts|
|API从不支持元服务到支持元服务|类名：global；<br>API声明：declare namespace hidebug<br>差异内容：NA|类名：global；<br>API声明：declare namespace hidebug<br>差异内容：atomicservice|api/@ohos.hidebug.d.ts|
