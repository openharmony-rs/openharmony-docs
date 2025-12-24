| Change Type | Old Version | New Version | d.ts File |
| ---- | ------ | ------ | -------- |
|New API |NA|Class name: global;<br>API declaration: declare namespace jsLeakWatcher<br>Differences: declare namespace jsLeakWatcher|api/@ohos.hiviewdfx.jsLeakWatcher.d.ts|
|New API |NA|Class name: jsLeakWatcher;<br>API declaration: function enable(isEnable: boolean): void;<br>Differences: function enable(isEnable: boolean): void;|api/@ohos.hiviewdfx.jsLeakWatcher.d.ts|
|New API |NA|Class name: jsLeakWatcher;<br>API declaration: function watch(obj: object, msg: string): void;<br>Differences: function watch(obj: object, msg: string): void;|api/@ohos.hiviewdfx.jsLeakWatcher.d.ts|
|New API |NA|Class name: jsLeakWatcher;<br>API declaration: function check(): string;<br>Differences: function check(): string;|api/@ohos.hiviewdfx.jsLeakWatcher.d.ts|
|New API |NA|Class name: jsLeakWatcher;<br>API declaration: function dump(filePath: string): Array\<string>;<br>Differences: function dump(filePath: string): Array\<string>;|api/@ohos.hiviewdfx.jsLeakWatcher.d.ts|
|New API |NA|Class name: hidebug;<br>API declaration: function getSystemCpuUsage(): number;<br>Differences: function getSystemCpuUsage(): number;|api/@ohos.hidebug.d.ts|
|New API |NA|Class name: hidebug;<br>API declaration: interface ThreadCpuUsage<br>Differences: interface ThreadCpuUsage|api/@ohos.hidebug.d.ts|
|New API |NA|Class name: ThreadCpuUsage;<br>API declaration: threadId: number;<br>Differences: threadId: number;|api/@ohos.hidebug.d.ts|
|New API |NA|Class name: ThreadCpuUsage;<br>API declaration: cpuUsage: number;<br>Differences: cpuUsage: number;|api/@ohos.hidebug.d.ts|
|New API |NA|Class name: hidebug;<br>API declaration: function getAppThreadCpuUsage(): ThreadCpuUsage[];<br>Differences: function getAppThreadCpuUsage(): ThreadCpuUsage[];|api/@ohos.hidebug.d.ts|
|New API |NA|Class name: hidebug;<br>API declaration: interface SystemMemInfo<br>Differences: interface SystemMemInfo|api/@ohos.hidebug.d.ts|
|New API |NA|Class name: SystemMemInfo;<br>API declaration: totalMem: bigint;<br>Differences: totalMem: bigint;|api/@ohos.hidebug.d.ts|
|New API |NA|Class name: SystemMemInfo;<br>API declaration: freeMem: bigint;<br>Differences: freeMem: bigint;|api/@ohos.hidebug.d.ts|
|New API |NA|Class name: SystemMemInfo;<br>API declaration: availableMem: bigint;<br>Differences: availableMem: bigint;|api/@ohos.hidebug.d.ts|
|New API |NA|Class name: hidebug;<br>API declaration: function getSystemMemInfo(): SystemMemInfo;<br>Differences: function getSystemMemInfo(): SystemMemInfo;|api/@ohos.hidebug.d.ts|
|New API |NA|Class name: hidebug;<br>API declaration: interface NativeMemInfo<br>Differences: interface NativeMemInfo|api/@ohos.hidebug.d.ts|
|New API |NA|Class name: NativeMemInfo;<br>API declaration: pss: bigint;<br>Differences: pss: bigint;|api/@ohos.hidebug.d.ts|
|New API |NA|Class name: NativeMemInfo;<br>API declaration: vss: bigint;<br>Differences: vss: bigint;|api/@ohos.hidebug.d.ts|
|New API |NA|Class name: NativeMemInfo;<br>API declaration: rss: bigint;<br>Differences: rss: bigint;|api/@ohos.hidebug.d.ts|
|New API |NA|Class name: NativeMemInfo;<br>API declaration: sharedDirty: bigint;<br>Differences: sharedDirty: bigint;|api/@ohos.hidebug.d.ts|
|New API |NA|Class name: NativeMemInfo;<br>API declaration: privateDirty: bigint;<br>Differences: privateDirty: bigint;|api/@ohos.hidebug.d.ts|
|New API |NA|Class name: NativeMemInfo;<br>API declaration: sharedClean: bigint;<br>Differences: sharedClean: bigint;|api/@ohos.hidebug.d.ts|
|New API |NA|Class name: NativeMemInfo;<br>API declaration: privateClean: bigint;<br>Differences: privateClean: bigint;|api/@ohos.hidebug.d.ts|
|New API |NA|Class name: hidebug;<br>API declaration: function getAppNativeMemInfo(): NativeMemInfo;<br>Differences: function getAppNativeMemInfo(): NativeMemInfo;|api/@ohos.hidebug.d.ts|
|New API |NA|Class name: hidebug;<br>API declaration: interface MemoryLimit<br>Differences: interface MemoryLimit|api/@ohos.hidebug.d.ts|
|New API |NA|Class name: MemoryLimit;<br>API declaration: rssLimit: bigint;<br>Differences: rssLimit: bigint;|api/@ohos.hidebug.d.ts|
|New API |NA|Class name: MemoryLimit;<br>API declaration: vssLimit: bigint;<br>Differences: vssLimit: bigint;|api/@ohos.hidebug.d.ts|
|New API |NA|Class name: MemoryLimit;<br>API declaration: vmHeapLimit: bigint;<br>Differences: vmHeapLimit: bigint;|api/@ohos.hidebug.d.ts|
|New API |NA|Class name: MemoryLimit;<br>API declaration: vmTotalHeapSize: bigint;<br>Differences: vmTotalHeapSize: bigint;|api/@ohos.hidebug.d.ts|
|New API |NA|Class name: hidebug;<br>API declaration: function getAppMemoryLimit(): MemoryLimit;<br>Differences: function getAppMemoryLimit(): MemoryLimit;|api/@ohos.hidebug.d.ts|
|New API |NA|Class name: hidebug;<br>API declaration: interface VMMemoryInfo<br>Differences: interface VMMemoryInfo|api/@ohos.hidebug.d.ts|
|New API |NA|Class name: VMMemoryInfo;<br>API declaration: totalHeap: bigint;<br>Differences: totalHeap: bigint;|api/@ohos.hidebug.d.ts|
|New API |NA|Class name: VMMemoryInfo;<br>API declaration: heapUsed: bigint;<br>Differences: heapUsed: bigint;|api/@ohos.hidebug.d.ts|
|New API |NA|Class name: VMMemoryInfo;<br>API declaration: allArraySize: bigint;<br>Differences: allArraySize: bigint;|api/@ohos.hidebug.d.ts|
|New API |NA|Class name: hidebug;<br>API declaration: function getAppVMMemoryInfo(): VMMemoryInfo;<br>Differences: function getAppVMMemoryInfo(): VMMemoryInfo;|api/@ohos.hidebug.d.ts|
|New API |NA|Class name: hidebug;<br>API declaration: enum TraceFlag<br>Differences: enum TraceFlag|api/@ohos.hidebug.d.ts|
|New API |NA|Class name: TraceFlag;<br>API declaration: MAIN_THREAD = 1<br>Differences: MAIN_THREAD = 1|api/@ohos.hidebug.d.ts|
|New API |NA|Class name: TraceFlag;<br>API declaration: ALL_THREADS = 2<br>Differences: ALL_THREADS = 2|api/@ohos.hidebug.d.ts|
|New API |NA|Class name: hidebug;<br>API declaration: namespace tags<br>Differences: namespace tags|api/@ohos.hidebug.d.ts|
|New API |NA|Class name: tags;<br>API declaration: const ABILITY_MANAGER: number;<br>Differences: const ABILITY_MANAGER: number;|api/@ohos.hidebug.d.ts|
|New API |NA|Class name: tags;<br>API declaration: const ARKUI: number;<br>Differences: const ARKUI: number;|api/@ohos.hidebug.d.ts|
|New API |NA|Class name: tags;<br>API declaration: const ARK: number;<br>Differences: const ARK: number;|api/@ohos.hidebug.d.ts|
|New API |NA|Class name: tags;<br>API declaration: const BLUETOOTH: number;<br>Differences: const BLUETOOTH: number;|api/@ohos.hidebug.d.ts|
|New API |NA|Class name: tags;<br>API declaration: const COMMON_LIBRARY: number;<br>Differences: const COMMON_LIBRARY: number;|api/@ohos.hidebug.d.ts|
|New API |NA|Class name: tags;<br>API declaration: const DISTRIBUTED_HARDWARE_DEVICE_MANAGER: number;<br>Differences: const DISTRIBUTED_HARDWARE_DEVICE_MANAGER: number;|api/@ohos.hidebug.d.ts|
|New API |NA|Class name: tags;<br>API declaration: const DISTRIBUTED_AUDIO: number;<br>Differences: const DISTRIBUTED_AUDIO: number;|api/@ohos.hidebug.d.ts|
|New API |NA|Class name: tags;<br>API declaration: const DISTRIBUTED_CAMERA: number;<br>Differences: const DISTRIBUTED_CAMERA: number;|api/@ohos.hidebug.d.ts|
|New API |NA|Class name: tags;<br>API declaration: const DISTRIBUTED_DATA: number;<br>Differences: const DISTRIBUTED_DATA: number;|api/@ohos.hidebug.d.ts|
|New API |NA|Class name: tags;<br>API declaration: const DISTRIBUTED_HARDWARE_FRAMEWORK: number;<br>Differences: const DISTRIBUTED_HARDWARE_FRAMEWORK: number;|api/@ohos.hidebug.d.ts|
|New API |NA|Class name: tags;<br>API declaration: const DISTRIBUTED_INPUT: number;<br>Differences: const DISTRIBUTED_INPUT: number;|api/@ohos.hidebug.d.ts|
|New API |NA|Class name: tags;<br>API declaration: const DISTRIBUTED_SCREEN: number;<br>Differences: const DISTRIBUTED_SCREEN: number;|api/@ohos.hidebug.d.ts|
|New API |NA|Class name: tags;<br>API declaration: const DISTRIBUTED_SCHEDULER: number;<br>Differences: const DISTRIBUTED_SCHEDULER: number;|api/@ohos.hidebug.d.ts|
|New API |NA|Class name: tags;<br>API declaration: const FFRT: number;<br>Differences: const FFRT: number;|api/@ohos.hidebug.d.ts|
|New API |NA|Class name: tags;<br>API declaration: const FILE_MANAGEMENT: number;<br>Differences: const FILE_MANAGEMENT: number;|api/@ohos.hidebug.d.ts|
|New API |NA|Class name: tags;<br>API declaration: const GLOBAL_RESOURCE_MANAGER: number;<br>Differences: const GLOBAL_RESOURCE_MANAGER: number;|api/@ohos.hidebug.d.ts|
|New API |NA|Class name: tags;<br>API declaration: const GRAPHICS: number;<br>Differences: const GRAPHICS: number;|api/@ohos.hidebug.d.ts|
|New API |NA|Class name: tags;<br>API declaration: const HDF: number;<br>Differences: const HDF: number;|api/@ohos.hidebug.d.ts|
|New API |NA|Class name: tags;<br>API declaration: const MISC: number;<br>Differences: const MISC: number;|api/@ohos.hidebug.d.ts|
|New API |NA|Class name: tags;<br>API declaration: const MULTIMODAL_INPUT: number;<br>Differences: const MULTIMODAL_INPUT: number;|api/@ohos.hidebug.d.ts|
|New API |NA|Class name: tags;<br>API declaration: const NET: number;<br>Differences: const NET: number;|api/@ohos.hidebug.d.ts|
|New API |NA|Class name: tags;<br>API declaration: const NOTIFICATION: number;<br>Differences: const NOTIFICATION: number;|api/@ohos.hidebug.d.ts|
|New API |NA|Class name: tags;<br>API declaration: const NWEB: number;<br>Differences: const NWEB: number;|api/@ohos.hidebug.d.ts|
|New API |NA|Class name: tags;<br>API declaration: const OHOS: number;<br>Differences: const OHOS: number;|api/@ohos.hidebug.d.ts|
|New API |NA|Class name: tags;<br>API declaration: const POWER_MANAGER: number;<br>Differences: const POWER_MANAGER: number;|api/@ohos.hidebug.d.ts|
|New API |NA|Class name: tags;<br>API declaration: const RPC: number;<br>Differences: const RPC: number;|api/@ohos.hidebug.d.ts|
|New API |NA|Class name: tags;<br>API declaration: const SAMGR: number;<br>Differences: const SAMGR: number;|api/@ohos.hidebug.d.ts|
|New API |NA|Class name: tags;<br>API declaration: const WINDOW_MANAGER: number;<br>Differences: const WINDOW_MANAGER: number;|api/@ohos.hidebug.d.ts|
|New API |NA|Class name: tags;<br>API declaration: const AUDIO: number;<br>Differences: const AUDIO: number;|api/@ohos.hidebug.d.ts|
|New API |NA|Class name: tags;<br>API declaration: const CAMERA: number;<br>Differences: const CAMERA: number;|api/@ohos.hidebug.d.ts|
|New API |NA|Class name: tags;<br>API declaration: const IMAGE: number;<br>Differences: const IMAGE: number;|api/@ohos.hidebug.d.ts|
|New API |NA|Class name: tags;<br>API declaration: const MEDIA: number;<br>Differences: const MEDIA: number;|api/@ohos.hidebug.d.ts|
|New API |NA|Class name: hidebug;<br>API declaration: function startAppTraceCapture(tags: number[], flag: TraceFlag, limitSize: number): string;<br>Differences: function startAppTraceCapture(tags: number[], flag: TraceFlag, limitSize: number): string;|api/@ohos.hidebug.d.ts|
|New API |NA|Class name: hidebug;<br>API declaration: function stopAppTraceCapture(): void;<br>Differences: function stopAppTraceCapture(): void;|api/@ohos.hidebug.d.ts|
|New API |NA|Class name: hidebug;<br>API declaration: type GcStats = Record\<string, number>;<br>Differences: type GcStats = Record\<string, number>;|api/@ohos.hidebug.d.ts|
|New API |NA|Class name: hidebug;<br>API declaration: function getVMRuntimeStats(): GcStats;<br>Differences: function getVMRuntimeStats(): GcStats;|api/@ohos.hidebug.d.ts|
|New API |NA|Class name: hidebug;<br>API declaration: function getVMRuntimeStat(item: string): number;<br>Differences: function getVMRuntimeStat(item: string): number;|api/@ohos.hidebug.d.ts|
|New API |NA|Class name: hidebug;<br>API declaration: function setAppResourceLimit(type: string, value: number, enableDebugLog: boolean): void;<br>Differences: function setAppResourceLimit(type: string, value: number, enableDebugLog: boolean): void;|api/@ohos.hidebug.d.ts|
|New API |NA|Class name: hidebug;<br>API declaration: function isDebugState(): boolean;<br>Differences: function isDebugState(): boolean;|api/@ohos.hidebug.d.ts|
|New API |NA|Class name: event;<br>API declaration: const APP_LAUNCH: string;<br>Differences: const APP_LAUNCH: string;|api/@ohos.hiviewdfx.hiAppEvent.d.ts|
|New API |NA|Class name: event;<br>API declaration: const SCROLL_JANK: string;<br>Differences: const SCROLL_JANK: string;|api/@ohos.hiviewdfx.hiAppEvent.d.ts|
|New API |NA|Class name: event;<br>API declaration: const CPU_USAGE_HIGH: string;<br>Differences: const CPU_USAGE_HIGH: string;|api/@ohos.hiviewdfx.hiAppEvent.d.ts|
|New API |NA|Class name: event;<br>API declaration: const BATTERY_USAGE: string;<br>Differences: const BATTERY_USAGE: string;|api/@ohos.hiviewdfx.hiAppEvent.d.ts|
|New API |NA|Class name: event;<br>API declaration: const RESOURCE_OVERLIMIT: string;<br>Differences: const RESOURCE_OVERLIMIT: string;|api/@ohos.hiviewdfx.hiAppEvent.d.ts|
|New API |NA|Class name: event;<br>API declaration: const ADDRESS_SANITIZER: string;<br>Differences: const ADDRESS_SANITIZER: string;|api/@ohos.hiviewdfx.hiAppEvent.d.ts|
|New API |NA|Class name: event;<br>API declaration: const MAIN_THREAD_JANK: string;<br>Differences: const MAIN_THREAD_JANK: string;|api/@ohos.hiviewdfx.hiAppEvent.d.ts|
|New API |NA|Class name: hiAppEvent;<br>API declaration: type ParamType = number \| string \| boolean \| Array\<string>;<br>Differences: type ParamType = number \| string \| boolean \| Array\<string>;|api/@ohos.hiviewdfx.hiAppEvent.d.ts|
|New API |NA|Class name: hiAppEvent;<br>API declaration: function setEventParam(params: Record\<string, ParamType>, domain: string, name?: string): Promise\<void>;<br>Differences: function setEventParam(params: Record\<string, ParamType>, domain: string, name?: string): Promise\<void>;|api/@ohos.hiviewdfx.hiAppEvent.d.ts|
|New API |NA|Class name: AppEventPackage;<br>API declaration: appEventInfos: Array\<AppEventInfo>;<br>Differences: appEventInfos: Array\<AppEventInfo>;|api/@ohos.hiviewdfx.hiAppEvent.d.ts|
|New API |NA|Class name: AppEventPackageHolder;<br>API declaration: setRow(size: number): void;<br>Differences: setRow(size: number): void;|api/@ohos.hiviewdfx.hiAppEvent.d.ts|
|New API |NA|Class name: Processor;<br>API declaration: configId?: number;<br>Differences: configId?: number;|api/@ohos.hiviewdfx.hiAppEvent.d.ts|
|New API |NA|Class name: Processor;<br>API declaration: customConfigs?: Record\<string, string>;<br>Differences: customConfigs?: Record\<string, string>;|api/@ohos.hiviewdfx.hiAppEvent.d.ts|
|New Kit|Class name: global;<br>API declaration: <br>Differences: NA|Class name: global;<br>API declaration: api\@ohos.hiviewdfx.jsLeakWatcher.d.ts<br>Differences: PerformanceAnalysisKit|api/@ohos.hiviewdfx.jsLeakWatcher.d.ts|
|New support for atomic services|Class name: global;<br>API declaration: declare namespace hidebug<br>Differences: NA|Class name: global;<br>API declaration: declare namespace hidebug<br>Differences: atomicservice|api/@ohos.hidebug.d.ts|
