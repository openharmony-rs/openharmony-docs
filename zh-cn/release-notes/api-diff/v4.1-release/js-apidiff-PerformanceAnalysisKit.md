| 操作 | 旧版本 | 新版本 | d.ts文件 |
| ---- | ------ | ------ | -------- |
|新增API|NA|类名：global；<br>API声明：declare namespace bytrace<br>差异内容：declare namespace bytrace|api/@ohos.bytrace.d.ts|
|新增API|NA|类名：bytrace；<br>API声明：function startTrace(name: string, taskId: number, expectedTime?: number): void;<br>差异内容：function startTrace(name: string, taskId: number, expectedTime?: number): void;|api/@ohos.bytrace.d.ts|
|新增API|NA|类名：bytrace；<br>API声明：function finishTrace(name: string, taskId: number): void;<br>差异内容：function finishTrace(name: string, taskId: number): void;|api/@ohos.bytrace.d.ts|
|新增API|NA|类名：bytrace；<br>API声明：function traceByValue(name: string, count: number): void;<br>差异内容：function traceByValue(name: string, count: number): void;|api/@ohos.bytrace.d.ts|
|新增API|NA|类名：global；<br>API声明：declare namespace FaultLogger<br>差异内容：declare namespace FaultLogger|api/@ohos.faultLogger.d.ts|
|新增API|NA|类名：FaultLogger；<br>API声明：enum FaultType<br>差异内容：enum FaultType|api/@ohos.faultLogger.d.ts|
|新增API|NA|类名：FaultType；<br>API声明：NO_SPECIFIC = 0<br>差异内容：NO_SPECIFIC = 0|api/@ohos.faultLogger.d.ts|
|新增API|NA|类名：FaultType；<br>API声明：CPP_CRASH = 2<br>差异内容：CPP_CRASH = 2|api/@ohos.faultLogger.d.ts|
|新增API|NA|类名：FaultType；<br>API声明：JS_CRASH = 3<br>差异内容：JS_CRASH = 3|api/@ohos.faultLogger.d.ts|
|新增API|NA|类名：FaultType；<br>API声明：APP_FREEZE = 4<br>差异内容：APP_FREEZE = 4|api/@ohos.faultLogger.d.ts|
|新增API|NA|类名：FaultLogger；<br>API声明：function querySelfFaultLog(faultType: FaultType, callback: AsyncCallback\<Array\<FaultLogInfo>>): void;<br>差异内容：function querySelfFaultLog(faultType: FaultType, callback: AsyncCallback\<Array\<FaultLogInfo>>): void;|api/@ohos.faultLogger.d.ts|
|新增API|NA|类名：FaultLogger；<br>API声明：function querySelfFaultLog(faultType: FaultType): Promise\<Array\<FaultLogInfo>>;<br>差异内容：function querySelfFaultLog(faultType: FaultType): Promise\<Array\<FaultLogInfo>>;|api/@ohos.faultLogger.d.ts|
|新增API|NA|类名：FaultLogger；<br>API声明：function query(faultType: FaultType, callback: AsyncCallback\<Array\<FaultLogInfo>>): void;<br>差异内容：function query(faultType: FaultType, callback: AsyncCallback\<Array\<FaultLogInfo>>): void;|api/@ohos.faultLogger.d.ts|
|新增API|NA|类名：FaultLogger；<br>API声明：function query(faultType: FaultType): Promise\<Array\<FaultLogInfo>>;<br>差异内容：function query(faultType: FaultType): Promise\<Array\<FaultLogInfo>>;|api/@ohos.faultLogger.d.ts|
|新增API|NA|类名：FaultLogger；<br>API声明：interface FaultLogInfo<br>差异内容：interface FaultLogInfo|api/@ohos.faultLogger.d.ts|
|新增API|NA|类名：FaultLogInfo；<br>API声明：pid: number;<br>差异内容：pid: number;|api/@ohos.faultLogger.d.ts|
|新增API|NA|类名：FaultLogInfo；<br>API声明：uid: number;<br>差异内容：uid: number;|api/@ohos.faultLogger.d.ts|
|新增API|NA|类名：FaultLogInfo；<br>API声明：type: FaultType;<br>差异内容：type: FaultType;|api/@ohos.faultLogger.d.ts|
|新增API|NA|类名：FaultLogInfo；<br>API声明：timestamp: number;<br>差异内容：timestamp: number;|api/@ohos.faultLogger.d.ts|
|新增API|NA|类名：FaultLogInfo；<br>API声明：reason: string;<br>差异内容：reason: string;|api/@ohos.faultLogger.d.ts|
|新增API|NA|类名：FaultLogInfo；<br>API声明：module: string;<br>差异内容：module: string;|api/@ohos.faultLogger.d.ts|
|新增API|NA|类名：FaultLogInfo；<br>API声明：summary: string;<br>差异内容：summary: string;|api/@ohos.faultLogger.d.ts|
|新增API|NA|类名：FaultLogInfo；<br>API声明：fullLog: string;<br>差异内容：fullLog: string;|api/@ohos.faultLogger.d.ts|
|新增API|NA|类名：global；<br>API声明：declare namespace hiAppEvent<br>差异内容：declare namespace hiAppEvent|api/@ohos.hiAppEvent.d.ts|
|新增API|NA|类名：hiAppEvent；<br>API声明：enum EventType<br>差异内容：enum EventType|api/@ohos.hiAppEvent.d.ts|
|新增API|NA|类名：EventType；<br>API声明：FAULT = 1<br>差异内容：FAULT = 1|api/@ohos.hiAppEvent.d.ts|
|新增API|NA|类名：EventType；<br>API声明：STATISTIC = 2<br>差异内容：STATISTIC = 2|api/@ohos.hiAppEvent.d.ts|
|新增API|NA|类名：EventType；<br>API声明：SECURITY = 3<br>差异内容：SECURITY = 3|api/@ohos.hiAppEvent.d.ts|
|新增API|NA|类名：EventType；<br>API声明：BEHAVIOR = 4<br>差异内容：BEHAVIOR = 4|api/@ohos.hiAppEvent.d.ts|
|新增API|NA|类名：hiAppEvent；<br>API声明：namespace Event<br>差异内容：namespace Event|api/@ohos.hiAppEvent.d.ts|
|新增API|NA|类名：Event；<br>API声明：const USER_LOGIN: string;<br>差异内容：const USER_LOGIN: string;|api/@ohos.hiAppEvent.d.ts|
|新增API|NA|类名：Event；<br>API声明：const USER_LOGOUT: string;<br>差异内容：const USER_LOGOUT: string;|api/@ohos.hiAppEvent.d.ts|
|新增API|NA|类名：Event；<br>API声明：const DISTRIBUTED_SERVICE_START: string;<br>差异内容：const DISTRIBUTED_SERVICE_START: string;|api/@ohos.hiAppEvent.d.ts|
|新增API|NA|类名：hiAppEvent；<br>API声明：namespace Param<br>差异内容：namespace Param|api/@ohos.hiAppEvent.d.ts|
|新增API|NA|类名：Param；<br>API声明：const USER_ID: string;<br>差异内容：const USER_ID: string;|api/@ohos.hiAppEvent.d.ts|
|新增API|NA|类名：Param；<br>API声明：const DISTRIBUTED_SERVICE_NAME: string;<br>差异内容：const DISTRIBUTED_SERVICE_NAME: string;|api/@ohos.hiAppEvent.d.ts|
|新增API|NA|类名：Param；<br>API声明：const DISTRIBUTED_SERVICE_INSTANCE_ID: string;<br>差异内容：const DISTRIBUTED_SERVICE_INSTANCE_ID: string;|api/@ohos.hiAppEvent.d.ts|
|新增API|NA|类名：hiAppEvent；<br>API声明：function write(eventName: string, eventType: EventType, keyValues: object): Promise\<void>;<br>差异内容：function write(eventName: string, eventType: EventType, keyValues: object): Promise\<void>;|api/@ohos.hiAppEvent.d.ts|
|新增API|NA|类名：hiAppEvent；<br>API声明：function write(eventName: string, eventType: EventType, keyValues: object, callback: AsyncCallback\<void>): void;<br>差异内容：function write(eventName: string, eventType: EventType, keyValues: object, callback: AsyncCallback\<void>): void;|api/@ohos.hiAppEvent.d.ts|
|新增API|NA|类名：hiAppEvent；<br>API声明：function configure(config: ConfigOption): boolean;<br>差异内容：function configure(config: ConfigOption): boolean;|api/@ohos.hiAppEvent.d.ts|
|新增API|NA|类名：hiAppEvent；<br>API声明：interface ConfigOption<br>差异内容：interface ConfigOption|api/@ohos.hiAppEvent.d.ts|
|新增API|NA|类名：ConfigOption；<br>API声明：disable?: boolean;<br>差异内容：disable?: boolean;|api/@ohos.hiAppEvent.d.ts|
|新增API|NA|类名：ConfigOption；<br>API声明：maxStorage?: string;<br>差异内容：maxStorage?: string;|api/@ohos.hiAppEvent.d.ts|
|新增API|NA|类名：global；<br>API声明：declare namespace hichecker<br>差异内容：declare namespace hichecker|api/@ohos.hichecker.d.ts|
|新增API|NA|类名：hichecker；<br>API声明：const RULE_CAUTION_PRINT_LOG: 9223372036854775808n;<br>差异内容：const RULE_CAUTION_PRINT_LOG: 9223372036854775808n;|api/@ohos.hichecker.d.ts|
|新增API|NA|类名：hichecker；<br>API声明：const RULE_CAUTION_TRIGGER_CRASH: 4611686018427387904n;<br>差异内容：const RULE_CAUTION_TRIGGER_CRASH: 4611686018427387904n;|api/@ohos.hichecker.d.ts|
|新增API|NA|类名：hichecker；<br>API声明：const RULE_THREAD_CHECK_SLOW_PROCESS: 1n;<br>差异内容：const RULE_THREAD_CHECK_SLOW_PROCESS: 1n;|api/@ohos.hichecker.d.ts|
|新增API|NA|类名：hichecker；<br>API声明：const RULE_CHECK_ABILITY_CONNECTION_LEAK: 8589934592n;<br>差异内容：const RULE_CHECK_ABILITY_CONNECTION_LEAK: 8589934592n;|api/@ohos.hichecker.d.ts|
|新增API|NA|类名：hichecker；<br>API声明：const RULE_CHECK_ARKUI_PERFORMANCE: 17179869184n;<br>差异内容：const RULE_CHECK_ARKUI_PERFORMANCE: 17179869184n;|api/@ohos.hichecker.d.ts|
|新增API|NA|类名：hichecker；<br>API声明：function addRule(rule: bigint): void;<br>差异内容：function addRule(rule: bigint): void;|api/@ohos.hichecker.d.ts|
|新增API|NA|类名：hichecker；<br>API声明：function removeRule(rule: bigint): void;<br>差异内容：function removeRule(rule: bigint): void;|api/@ohos.hichecker.d.ts|
|新增API|NA|类名：hichecker；<br>API声明：function getRule(): bigint;<br>差异内容：function getRule(): bigint;|api/@ohos.hichecker.d.ts|
|新增API|NA|类名：hichecker；<br>API声明：function contains(rule: bigint): boolean;<br>差异内容：function contains(rule: bigint): boolean;|api/@ohos.hichecker.d.ts|
|新增API|NA|类名：hichecker；<br>API声明：function addCheckRule(rule: bigint): void;<br>差异内容：function addCheckRule(rule: bigint): void;|api/@ohos.hichecker.d.ts|
|新增API|NA|类名：hichecker；<br>API声明：function removeCheckRule(rule: bigint): void;<br>差异内容：function removeCheckRule(rule: bigint): void;|api/@ohos.hichecker.d.ts|
|新增API|NA|类名：hichecker；<br>API声明：function containsCheckRule(rule: bigint): boolean;<br>差异内容：function containsCheckRule(rule: bigint): boolean;|api/@ohos.hichecker.d.ts|
|新增API|NA|类名：global；<br>API声明：declare namespace hidebug<br>差异内容：declare namespace hidebug|api/@ohos.hidebug.d.ts|
|新增API|NA|类名：hidebug；<br>API声明：function getNativeHeapSize(): bigint;<br>差异内容：function getNativeHeapSize(): bigint;|api/@ohos.hidebug.d.ts|
|新增API|NA|类名：hidebug；<br>API声明：function getNativeHeapAllocatedSize(): bigint;<br>差异内容：function getNativeHeapAllocatedSize(): bigint;|api/@ohos.hidebug.d.ts|
|新增API|NA|类名：hidebug；<br>API声明：function getNativeHeapFreeSize(): bigint;<br>差异内容：function getNativeHeapFreeSize(): bigint;|api/@ohos.hidebug.d.ts|
|新增API|NA|类名：hidebug；<br>API声明：function getVss(): bigint;<br>差异内容：function getVss(): bigint;|api/@ohos.hidebug.d.ts|
|新增API|NA|类名：hidebug；<br>API声明：function getPss(): bigint;<br>差异内容：function getPss(): bigint;|api/@ohos.hidebug.d.ts|
|新增API|NA|类名：hidebug；<br>API声明：function getSharedDirty(): bigint;<br>差异内容：function getSharedDirty(): bigint;|api/@ohos.hidebug.d.ts|
|新增API|NA|类名：hidebug；<br>API声明：function getPrivateDirty(): bigint;<br>差异内容：function getPrivateDirty(): bigint;|api/@ohos.hidebug.d.ts|
|新增API|NA|类名：hidebug；<br>API声明：function getCpuUsage(): number;<br>差异内容：function getCpuUsage(): number;|api/@ohos.hidebug.d.ts|
|新增API|NA|类名：hidebug；<br>API声明：function startProfiling(filename: string): void;<br>差异内容：function startProfiling(filename: string): void;|api/@ohos.hidebug.d.ts|
|新增API|NA|类名：hidebug；<br>API声明：function stopProfiling(): void;<br>差异内容：function stopProfiling(): void;|api/@ohos.hidebug.d.ts|
|新增API|NA|类名：hidebug；<br>API声明：function dumpHeapData(filename: string): void;<br>差异内容：function dumpHeapData(filename: string): void;|api/@ohos.hidebug.d.ts|
|新增API|NA|类名：hidebug；<br>API声明：function startJsCpuProfiling(filename: string): void;<br>差异内容：function startJsCpuProfiling(filename: string): void;|api/@ohos.hidebug.d.ts|
|新增API|NA|类名：hidebug；<br>API声明：function stopJsCpuProfiling(): void;<br>差异内容：function stopJsCpuProfiling(): void;|api/@ohos.hidebug.d.ts|
|新增API|NA|类名：hidebug；<br>API声明：function dumpJsHeapData(filename: string): void;<br>差异内容：function dumpJsHeapData(filename: string): void;|api/@ohos.hidebug.d.ts|
|新增API|NA|类名：hidebug；<br>API声明：function getServiceDump(serviceid: number, fd: number, args: Array\<string>): void;<br>差异内容：function getServiceDump(serviceid: number, fd: number, args: Array\<string>): void;|api/@ohos.hidebug.d.ts|
|新增API|NA|类名：global；<br>API声明：declare namespace hilog<br>差异内容：declare namespace hilog|api/@ohos.hilog.d.ts|
|新增API|NA|类名：hilog；<br>API声明：function debug(domain: number, tag: string, format: string, ...args: any[]): void;<br>差异内容：function debug(domain: number, tag: string, format: string, ...args: any[]): void;|api/@ohos.hilog.d.ts|
|新增API|NA|类名：hilog；<br>API声明：function info(domain: number, tag: string, format: string, ...args: any[]): void;<br>差异内容：function info(domain: number, tag: string, format: string, ...args: any[]): void;|api/@ohos.hilog.d.ts|
|新增API|NA|类名：hilog；<br>API声明：function warn(domain: number, tag: string, format: string, ...args: any[]): void;<br>差异内容：function warn(domain: number, tag: string, format: string, ...args: any[]): void;|api/@ohos.hilog.d.ts|
|新增API|NA|类名：hilog；<br>API声明：function error(domain: number, tag: string, format: string, ...args: any[]): void;<br>差异内容：function error(domain: number, tag: string, format: string, ...args: any[]): void;|api/@ohos.hilog.d.ts|
|新增API|NA|类名：hilog；<br>API声明：function fatal(domain: number, tag: string, format: string, ...args: any[]): void;<br>差异内容：function fatal(domain: number, tag: string, format: string, ...args: any[]): void;|api/@ohos.hilog.d.ts|
|新增API|NA|类名：hilog；<br>API声明：function isLoggable(domain: number, tag: string, level: LogLevel): boolean;<br>差异内容：function isLoggable(domain: number, tag: string, level: LogLevel): boolean;|api/@ohos.hilog.d.ts|
|新增API|NA|类名：hilog；<br>API声明：enum LogLevel<br>差异内容：enum LogLevel|api/@ohos.hilog.d.ts|
|新增API|NA|类名：LogLevel；<br>API声明：DEBUG = 3<br>差异内容：DEBUG = 3|api/@ohos.hilog.d.ts|
|新增API|NA|类名：LogLevel；<br>API声明：INFO = 4<br>差异内容：INFO = 4|api/@ohos.hilog.d.ts|
|新增API|NA|类名：LogLevel；<br>API声明：WARN = 5<br>差异内容：WARN = 5|api/@ohos.hilog.d.ts|
|新增API|NA|类名：LogLevel；<br>API声明：ERROR = 6<br>差异内容：ERROR = 6|api/@ohos.hilog.d.ts|
|新增API|NA|类名：LogLevel；<br>API声明：FATAL = 7<br>差异内容：FATAL = 7|api/@ohos.hilog.d.ts|
|新增API|NA|类名：global；<br>API声明：declare namespace hiTraceChain<br>差异内容：declare namespace hiTraceChain|api/@ohos.hiTraceChain.d.ts|
|新增API|NA|类名：hiTraceChain；<br>API声明：enum HiTraceFlag<br>差异内容：enum HiTraceFlag|api/@ohos.hiTraceChain.d.ts|
|新增API|NA|类名：HiTraceFlag；<br>API声明：DEFAULT = 0<br>差异内容：DEFAULT = 0|api/@ohos.hiTraceChain.d.ts|
|新增API|NA|类名：HiTraceFlag；<br>API声明：INCLUDE_ASYNC = 1<br>差异内容：INCLUDE_ASYNC = 1|api/@ohos.hiTraceChain.d.ts|
|新增API|NA|类名：HiTraceFlag；<br>API声明：DONOT_CREATE_SPAN = 1 \<\< 1<br>差异内容：DONOT_CREATE_SPAN = 1 \<\< 1|api/@ohos.hiTraceChain.d.ts|
|新增API|NA|类名：HiTraceFlag；<br>API声明：TP_INFO = 1 \<\< 2<br>差异内容：TP_INFO = 1 \<\< 2|api/@ohos.hiTraceChain.d.ts|
|新增API|NA|类名：HiTraceFlag；<br>API声明：NO_BE_INFO = 1 \<\< 3<br>差异内容：NO_BE_INFO = 1 \<\< 3|api/@ohos.hiTraceChain.d.ts|
|新增API|NA|类名：HiTraceFlag；<br>API声明：DISABLE_LOG = 1 \<\< 4<br>差异内容：DISABLE_LOG = 1 \<\< 4|api/@ohos.hiTraceChain.d.ts|
|新增API|NA|类名：HiTraceFlag；<br>API声明：FAILURE_TRIGGER = 1 \<\< 5<br>差异内容：FAILURE_TRIGGER = 1 \<\< 5|api/@ohos.hiTraceChain.d.ts|
|新增API|NA|类名：HiTraceFlag；<br>API声明：D2D_TP_INFO = 1 \<\< 6<br>差异内容：D2D_TP_INFO = 1 \<\< 6|api/@ohos.hiTraceChain.d.ts|
|新增API|NA|类名：hiTraceChain；<br>API声明：enum HiTraceTracepointType<br>差异内容：enum HiTraceTracepointType|api/@ohos.hiTraceChain.d.ts|
|新增API|NA|类名：HiTraceTracepointType；<br>API声明：CS = 0<br>差异内容：CS = 0|api/@ohos.hiTraceChain.d.ts|
|新增API|NA|类名：HiTraceTracepointType；<br>API声明：CR = 1<br>差异内容：CR = 1|api/@ohos.hiTraceChain.d.ts|
|新增API|NA|类名：HiTraceTracepointType；<br>API声明：SS = 2<br>差异内容：SS = 2|api/@ohos.hiTraceChain.d.ts|
|新增API|NA|类名：HiTraceTracepointType；<br>API声明：SR = 3<br>差异内容：SR = 3|api/@ohos.hiTraceChain.d.ts|
|新增API|NA|类名：HiTraceTracepointType；<br>API声明：GENERAL = 4<br>差异内容：GENERAL = 4|api/@ohos.hiTraceChain.d.ts|
|新增API|NA|类名：hiTraceChain；<br>API声明：enum HiTraceCommunicationMode<br>差异内容：enum HiTraceCommunicationMode|api/@ohos.hiTraceChain.d.ts|
|新增API|NA|类名：HiTraceCommunicationMode；<br>API声明：DEFAULT = 0<br>差异内容：DEFAULT = 0|api/@ohos.hiTraceChain.d.ts|
|新增API|NA|类名：HiTraceCommunicationMode；<br>API声明：THREAD = 1<br>差异内容：THREAD = 1|api/@ohos.hiTraceChain.d.ts|
|新增API|NA|类名：HiTraceCommunicationMode；<br>API声明：PROCESS = 2<br>差异内容：PROCESS = 2|api/@ohos.hiTraceChain.d.ts|
|新增API|NA|类名：HiTraceCommunicationMode；<br>API声明：DEVICE = 3<br>差异内容：DEVICE = 3|api/@ohos.hiTraceChain.d.ts|
|新增API|NA|类名：hiTraceChain；<br>API声明：interface HiTraceId<br>差异内容：interface HiTraceId|api/@ohos.hiTraceChain.d.ts|
|新增API|NA|类名：HiTraceId；<br>API声明：chainId: bigint;<br>差异内容：chainId: bigint;|api/@ohos.hiTraceChain.d.ts|
|新增API|NA|类名：HiTraceId；<br>API声明：spanId?: number;<br>差异内容：spanId?: number;|api/@ohos.hiTraceChain.d.ts|
|新增API|NA|类名：HiTraceId；<br>API声明：parentSpanId?: number;<br>差异内容：parentSpanId?: number;|api/@ohos.hiTraceChain.d.ts|
|新增API|NA|类名：HiTraceId；<br>API声明：flags?: number;<br>差异内容：flags?: number;|api/@ohos.hiTraceChain.d.ts|
|新增API|NA|类名：hiTraceChain；<br>API声明：function begin(name: string, flags?: number): HiTraceId;<br>差异内容：function begin(name: string, flags?: number): HiTraceId;|api/@ohos.hiTraceChain.d.ts|
|新增API|NA|类名：hiTraceChain；<br>API声明：function end(id: HiTraceId): void;<br>差异内容：function end(id: HiTraceId): void;|api/@ohos.hiTraceChain.d.ts|
|新增API|NA|类名：hiTraceChain；<br>API声明：function getId(): HiTraceId;<br>差异内容：function getId(): HiTraceId;|api/@ohos.hiTraceChain.d.ts|
|新增API|NA|类名：hiTraceChain；<br>API声明：function setId(id: HiTraceId): void;<br>差异内容：function setId(id: HiTraceId): void;|api/@ohos.hiTraceChain.d.ts|
|新增API|NA|类名：hiTraceChain；<br>API声明：function clearId(): void;<br>差异内容：function clearId(): void;|api/@ohos.hiTraceChain.d.ts|
|新增API|NA|类名：hiTraceChain；<br>API声明：function createSpan(): HiTraceId;<br>差异内容：function createSpan(): HiTraceId;|api/@ohos.hiTraceChain.d.ts|
|新增API|NA|类名：hiTraceChain；<br>API声明：function tracepoint(mode: HiTraceCommunicationMode, type: HiTraceTracepointType, id: HiTraceId, msg?: string): void;<br>差异内容：function tracepoint(mode: HiTraceCommunicationMode, type: HiTraceTracepointType, id: HiTraceId, msg?: string): void;|api/@ohos.hiTraceChain.d.ts|
|新增API|NA|类名：hiTraceChain；<br>API声明：function isValid(id: HiTraceId): boolean;<br>差异内容：function isValid(id: HiTraceId): boolean;|api/@ohos.hiTraceChain.d.ts|
|新增API|NA|类名：hiTraceChain；<br>API声明：function isFlagEnabled(id: HiTraceId, flag: HiTraceFlag): boolean;<br>差异内容：function isFlagEnabled(id: HiTraceId, flag: HiTraceFlag): boolean;|api/@ohos.hiTraceChain.d.ts|
|新增API|NA|类名：hiTraceChain；<br>API声明：function enableFlag(id: HiTraceId, flag: HiTraceFlag): void;<br>差异内容：function enableFlag(id: HiTraceId, flag: HiTraceFlag): void;|api/@ohos.hiTraceChain.d.ts|
|新增API|NA|类名：global；<br>API声明：declare namespace hiTraceMeter<br>差异内容：declare namespace hiTraceMeter|api/@ohos.hiTraceMeter.d.ts|
|新增API|NA|类名：hiTraceMeter；<br>API声明：function startTrace(name: string, taskId: number): void;<br>差异内容：function startTrace(name: string, taskId: number): void;|api/@ohos.hiTraceMeter.d.ts|
|新增API|NA|类名：hiTraceMeter；<br>API声明：function finishTrace(name: string, taskId: number): void;<br>差异内容：function finishTrace(name: string, taskId: number): void;|api/@ohos.hiTraceMeter.d.ts|
|新增API|NA|类名：hiTraceMeter；<br>API声明：function traceByValue(name: string, count: number): void;<br>差异内容：function traceByValue(name: string, count: number): void;|api/@ohos.hiTraceMeter.d.ts|
|新增API|NA|类名：global；<br>API声明：declare namespace hiAppEvent<br>差异内容：declare namespace hiAppEvent|api/@ohos.hiviewdfx.hiAppEvent.d.ts|
|新增API|NA|类名：hiAppEvent；<br>API声明：enum EventType<br>差异内容：enum EventType|api/@ohos.hiviewdfx.hiAppEvent.d.ts|
|新增API|NA|类名：EventType；<br>API声明：FAULT = 1<br>差异内容：FAULT = 1|api/@ohos.hiviewdfx.hiAppEvent.d.ts|
|新增API|NA|类名：EventType；<br>API声明：STATISTIC = 2<br>差异内容：STATISTIC = 2|api/@ohos.hiviewdfx.hiAppEvent.d.ts|
|新增API|NA|类名：EventType；<br>API声明：SECURITY = 3<br>差异内容：SECURITY = 3|api/@ohos.hiviewdfx.hiAppEvent.d.ts|
|新增API|NA|类名：EventType；<br>API声明：BEHAVIOR = 4<br>差异内容：BEHAVIOR = 4|api/@ohos.hiviewdfx.hiAppEvent.d.ts|
|新增API|NA|类名：hiAppEvent；<br>API声明：namespace domain<br>差异内容：namespace domain|api/@ohos.hiviewdfx.hiAppEvent.d.ts|
|新增API|NA|类名：domain；<br>API声明：const OS: string;<br>差异内容：const OS: string;|api/@ohos.hiviewdfx.hiAppEvent.d.ts|
|新增API|NA|类名：hiAppEvent；<br>API声明：namespace event<br>差异内容：namespace event|api/@ohos.hiviewdfx.hiAppEvent.d.ts|
|新增API|NA|类名：event；<br>API声明：const USER_LOGIN: string;<br>差异内容：const USER_LOGIN: string;|api/@ohos.hiviewdfx.hiAppEvent.d.ts|
|新增API|NA|类名：event；<br>API声明：const USER_LOGOUT: string;<br>差异内容：const USER_LOGOUT: string;|api/@ohos.hiviewdfx.hiAppEvent.d.ts|
|新增API|NA|类名：event；<br>API声明：const DISTRIBUTED_SERVICE_START: string;<br>差异内容：const DISTRIBUTED_SERVICE_START: string;|api/@ohos.hiviewdfx.hiAppEvent.d.ts|
|新增API|NA|类名：event；<br>API声明：const APP_CRASH: string;<br>差异内容：const APP_CRASH: string;|api/@ohos.hiviewdfx.hiAppEvent.d.ts|
|新增API|NA|类名：event；<br>API声明：const APP_FREEZE: string;<br>差异内容：const APP_FREEZE: string;|api/@ohos.hiviewdfx.hiAppEvent.d.ts|
|新增API|NA|类名：hiAppEvent；<br>API声明：namespace param<br>差异内容：namespace param|api/@ohos.hiviewdfx.hiAppEvent.d.ts|
|新增API|NA|类名：param；<br>API声明：const USER_ID: string;<br>差异内容：const USER_ID: string;|api/@ohos.hiviewdfx.hiAppEvent.d.ts|
|新增API|NA|类名：param；<br>API声明：const DISTRIBUTED_SERVICE_NAME: string;<br>差异内容：const DISTRIBUTED_SERVICE_NAME: string;|api/@ohos.hiviewdfx.hiAppEvent.d.ts|
|新增API|NA|类名：param；<br>API声明：const DISTRIBUTED_SERVICE_INSTANCE_ID: string;<br>差异内容：const DISTRIBUTED_SERVICE_INSTANCE_ID: string;|api/@ohos.hiviewdfx.hiAppEvent.d.ts|
|新增API|NA|类名：hiAppEvent；<br>API声明：function configure(config: ConfigOption): void;<br>差异内容：function configure(config: ConfigOption): void;|api/@ohos.hiviewdfx.hiAppEvent.d.ts|
|新增API|NA|类名：hiAppEvent；<br>API声明：interface ConfigOption<br>差异内容：interface ConfigOption|api/@ohos.hiviewdfx.hiAppEvent.d.ts|
|新增API|NA|类名：ConfigOption；<br>API声明：disable?: boolean;<br>差异内容：disable?: boolean;|api/@ohos.hiviewdfx.hiAppEvent.d.ts|
|新增API|NA|类名：ConfigOption；<br>API声明：maxStorage?: string;<br>差异内容：maxStorage?: string;|api/@ohos.hiviewdfx.hiAppEvent.d.ts|
|新增API|NA|类名：hiAppEvent；<br>API声明：interface AppEventInfo<br>差异内容：interface AppEventInfo|api/@ohos.hiviewdfx.hiAppEvent.d.ts|
|新增API|NA|类名：AppEventInfo；<br>API声明：domain: string;<br>差异内容：domain: string;|api/@ohos.hiviewdfx.hiAppEvent.d.ts|
|新增API|NA|类名：AppEventInfo；<br>API声明：name: string;<br>差异内容：name: string;|api/@ohos.hiviewdfx.hiAppEvent.d.ts|
|新增API|NA|类名：AppEventInfo；<br>API声明：eventType: EventType;<br>差异内容：eventType: EventType;|api/@ohos.hiviewdfx.hiAppEvent.d.ts|
|新增API|NA|类名：AppEventInfo；<br>API声明：params: object;<br>差异内容：params: object;|api/@ohos.hiviewdfx.hiAppEvent.d.ts|
|新增API|NA|类名：hiAppEvent；<br>API声明：function write(info: AppEventInfo): Promise\<void>;<br>差异内容：function write(info: AppEventInfo): Promise\<void>;|api/@ohos.hiviewdfx.hiAppEvent.d.ts|
|新增API|NA|类名：hiAppEvent；<br>API声明：function write(info: AppEventInfo, callback: AsyncCallback\<void>): void;<br>差异内容：function write(info: AppEventInfo, callback: AsyncCallback\<void>): void;|api/@ohos.hiviewdfx.hiAppEvent.d.ts|
|新增API|NA|类名：hiAppEvent；<br>API声明：interface AppEventPackage<br>差异内容：interface AppEventPackage|api/@ohos.hiviewdfx.hiAppEvent.d.ts|
|新增API|NA|类名：AppEventPackage；<br>API声明：packageId: number;<br>差异内容：packageId: number;|api/@ohos.hiviewdfx.hiAppEvent.d.ts|
|新增API|NA|类名：AppEventPackage；<br>API声明：row: number;<br>差异内容：row: number;|api/@ohos.hiviewdfx.hiAppEvent.d.ts|
|新增API|NA|类名：AppEventPackage；<br>API声明：size: number;<br>差异内容：size: number;|api/@ohos.hiviewdfx.hiAppEvent.d.ts|
|新增API|NA|类名：AppEventPackage；<br>API声明：data: string[];<br>差异内容：data: string[];|api/@ohos.hiviewdfx.hiAppEvent.d.ts|
|新增API|NA|类名：hiAppEvent；<br>API声明：class AppEventPackageHolder<br>差异内容：class AppEventPackageHolder|api/@ohos.hiviewdfx.hiAppEvent.d.ts|
|新增API|NA|类名：AppEventPackageHolder；<br>API声明：setSize(size: number): void;<br>差异内容：setSize(size: number): void;|api/@ohos.hiviewdfx.hiAppEvent.d.ts|
|新增API|NA|类名：AppEventPackageHolder；<br>API声明：takeNext(): AppEventPackage;<br>差异内容：takeNext(): AppEventPackage;|api/@ohos.hiviewdfx.hiAppEvent.d.ts|
|新增API|NA|类名：hiAppEvent；<br>API声明：interface TriggerCondition<br>差异内容：interface TriggerCondition|api/@ohos.hiviewdfx.hiAppEvent.d.ts|
|新增API|NA|类名：TriggerCondition；<br>API声明：row?: number;<br>差异内容：row?: number;|api/@ohos.hiviewdfx.hiAppEvent.d.ts|
|新增API|NA|类名：TriggerCondition；<br>API声明：size?: number;<br>差异内容：size?: number;|api/@ohos.hiviewdfx.hiAppEvent.d.ts|
|新增API|NA|类名：TriggerCondition；<br>API声明：timeOut?: number;<br>差异内容：timeOut?: number;|api/@ohos.hiviewdfx.hiAppEvent.d.ts|
|新增API|NA|类名：hiAppEvent；<br>API声明：interface AppEventFilter<br>差异内容：interface AppEventFilter|api/@ohos.hiviewdfx.hiAppEvent.d.ts|
|新增API|NA|类名：AppEventFilter；<br>API声明：domain: string;<br>差异内容：domain: string;|api/@ohos.hiviewdfx.hiAppEvent.d.ts|
|新增API|NA|类名：AppEventFilter；<br>API声明：eventTypes?: EventType[];<br>差异内容：eventTypes?: EventType[];|api/@ohos.hiviewdfx.hiAppEvent.d.ts|
|新增API|NA|类名：AppEventFilter；<br>API声明：names?: string[];<br>差异内容：names?: string[];|api/@ohos.hiviewdfx.hiAppEvent.d.ts|
|新增API|NA|类名：hiAppEvent；<br>API声明：interface AppEventGroup<br>差异内容：interface AppEventGroup|api/@ohos.hiviewdfx.hiAppEvent.d.ts|
|新增API|NA|类名：AppEventGroup；<br>API声明：name: string;<br>差异内容：name: string;|api/@ohos.hiviewdfx.hiAppEvent.d.ts|
|新增API|NA|类名：AppEventGroup；<br>API声明：appEventInfos: Array\<AppEventInfo>;<br>差异内容：appEventInfos: Array\<AppEventInfo>;|api/@ohos.hiviewdfx.hiAppEvent.d.ts|
|新增API|NA|类名：hiAppEvent；<br>API声明：interface Watcher<br>差异内容：interface Watcher|api/@ohos.hiviewdfx.hiAppEvent.d.ts|
|新增API|NA|类名：Watcher；<br>API声明：name: string;<br>差异内容：name: string;|api/@ohos.hiviewdfx.hiAppEvent.d.ts|
|新增API|NA|类名：Watcher；<br>API声明：triggerCondition?: TriggerCondition;<br>差异内容：triggerCondition?: TriggerCondition;|api/@ohos.hiviewdfx.hiAppEvent.d.ts|
|新增API|NA|类名：Watcher；<br>API声明：appEventFilters?: AppEventFilter[];<br>差异内容：appEventFilters?: AppEventFilter[];|api/@ohos.hiviewdfx.hiAppEvent.d.ts|
|新增API|NA|类名：Watcher；<br>API声明：onTrigger?: (curRow: number, curSize: number, holder: AppEventPackageHolder) => void;<br>差异内容：onTrigger?: (curRow: number, curSize: number, holder: AppEventPackageHolder) => void;|api/@ohos.hiviewdfx.hiAppEvent.d.ts|
|新增API|NA|类名：Watcher；<br>API声明：onReceive?: (domain: string, appEventGroups: Array\<AppEventGroup>) => void;<br>差异内容：onReceive?: (domain: string, appEventGroups: Array\<AppEventGroup>) => void;|api/@ohos.hiviewdfx.hiAppEvent.d.ts|
|新增API|NA|类名：hiAppEvent；<br>API声明：function addWatcher(watcher: Watcher): AppEventPackageHolder;<br>差异内容：function addWatcher(watcher: Watcher): AppEventPackageHolder;|api/@ohos.hiviewdfx.hiAppEvent.d.ts|
|新增API|NA|类名：hiAppEvent；<br>API声明：function removeWatcher(watcher: Watcher): void;<br>差异内容：function removeWatcher(watcher: Watcher): void;|api/@ohos.hiviewdfx.hiAppEvent.d.ts|
|新增API|NA|类名：hiAppEvent；<br>API声明：function clearData(): void;<br>差异内容：function clearData(): void;|api/@ohos.hiviewdfx.hiAppEvent.d.ts|
|新增API|NA|类名：hiAppEvent；<br>API声明：function setUserId(name: string, value: string): void;<br>差异内容：function setUserId(name: string, value: string): void;|api/@ohos.hiviewdfx.hiAppEvent.d.ts|
|新增API|NA|类名：hiAppEvent；<br>API声明：function getUserId(name: string): string;<br>差异内容：function getUserId(name: string): string;|api/@ohos.hiviewdfx.hiAppEvent.d.ts|
|新增API|NA|类名：hiAppEvent；<br>API声明：function setUserProperty(name: string, value: string): void;<br>差异内容：function setUserProperty(name: string, value: string): void;|api/@ohos.hiviewdfx.hiAppEvent.d.ts|
|新增API|NA|类名：hiAppEvent；<br>API声明：function getUserProperty(name: string): string;<br>差异内容：function getUserProperty(name: string): string;|api/@ohos.hiviewdfx.hiAppEvent.d.ts|
|新增API|NA|类名：hiAppEvent；<br>API声明：interface AppEventReportConfig<br>差异内容：interface AppEventReportConfig|api/@ohos.hiviewdfx.hiAppEvent.d.ts|
|新增API|NA|类名：AppEventReportConfig；<br>API声明：domain?: string;<br>差异内容：domain?: string;|api/@ohos.hiviewdfx.hiAppEvent.d.ts|
|新增API|NA|类名：AppEventReportConfig；<br>API声明：name?: string;<br>差异内容：name?: string;|api/@ohos.hiviewdfx.hiAppEvent.d.ts|
|新增API|NA|类名：AppEventReportConfig；<br>API声明：isRealTime?: boolean;<br>差异内容：isRealTime?: boolean;|api/@ohos.hiviewdfx.hiAppEvent.d.ts|
|新增API|NA|类名：hiAppEvent；<br>API声明：interface Processor<br>差异内容：interface Processor|api/@ohos.hiviewdfx.hiAppEvent.d.ts|
|新增API|NA|类名：Processor；<br>API声明：name: string;<br>差异内容：name: string;|api/@ohos.hiviewdfx.hiAppEvent.d.ts|
|新增API|NA|类名：Processor；<br>API声明：debugMode?: boolean;<br>差异内容：debugMode?: boolean;|api/@ohos.hiviewdfx.hiAppEvent.d.ts|
|新增API|NA|类名：Processor；<br>API声明：routeInfo?: string;<br>差异内容：routeInfo?: string;|api/@ohos.hiviewdfx.hiAppEvent.d.ts|
|新增API|NA|类名：Processor；<br>API声明：appId?: string;<br>差异内容：appId?: string;|api/@ohos.hiviewdfx.hiAppEvent.d.ts|
|新增API|NA|类名：Processor；<br>API声明：onStartReport?: boolean;<br>差异内容：onStartReport?: boolean;|api/@ohos.hiviewdfx.hiAppEvent.d.ts|
|新增API|NA|类名：Processor；<br>API声明：onBackgroundReport?: boolean;<br>差异内容：onBackgroundReport?: boolean;|api/@ohos.hiviewdfx.hiAppEvent.d.ts|
|新增API|NA|类名：Processor；<br>API声明：periodReport?: number;<br>差异内容：periodReport?: number;|api/@ohos.hiviewdfx.hiAppEvent.d.ts|
|新增API|NA|类名：Processor；<br>API声明：batchReport?: number;<br>差异内容：batchReport?: number;|api/@ohos.hiviewdfx.hiAppEvent.d.ts|
|新增API|NA|类名：Processor；<br>API声明：userIds?: string[];<br>差异内容：userIds?: string[];|api/@ohos.hiviewdfx.hiAppEvent.d.ts|
|新增API|NA|类名：Processor；<br>API声明：userProperties?: string[];<br>差异内容：userProperties?: string[];|api/@ohos.hiviewdfx.hiAppEvent.d.ts|
|新增API|NA|类名：Processor；<br>API声明：eventConfigs?: AppEventReportConfig[];<br>差异内容：eventConfigs?: AppEventReportConfig[];|api/@ohos.hiviewdfx.hiAppEvent.d.ts|
|新增API|NA|类名：hiAppEvent；<br>API声明：function addProcessor(processor: Processor): number;<br>差异内容：function addProcessor(processor: Processor): number;|api/@ohos.hiviewdfx.hiAppEvent.d.ts|
|新增API|NA|类名：hiAppEvent；<br>API声明：function removeProcessor(id: number): void;<br>差异内容：function removeProcessor(id: number): void;|api/@ohos.hiviewdfx.hiAppEvent.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\@ohos.bytrace.d.ts<br>差异内容：PerformanceAnalysisKit|api/@ohos.bytrace.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\@ohos.faultLogger.d.ts<br>差异内容：PerformanceAnalysisKit|api/@ohos.faultLogger.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\@ohos.hiAppEvent.d.ts<br>差异内容：PerformanceAnalysisKit|api/@ohos.hiAppEvent.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\@ohos.hichecker.d.ts<br>差异内容：PerformanceAnalysisKit|api/@ohos.hichecker.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\@ohos.hidebug.d.ts<br>差异内容：PerformanceAnalysisKit|api/@ohos.hidebug.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\@ohos.hilog.d.ts<br>差异内容：PerformanceAnalysisKit|api/@ohos.hilog.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\@ohos.hiTraceChain.d.ts<br>差异内容：PerformanceAnalysisKit|api/@ohos.hiTraceChain.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\@ohos.hiTraceMeter.d.ts<br>差异内容：PerformanceAnalysisKit|api/@ohos.hiTraceMeter.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\@ohos.hiviewdfx.hiAppEvent.d.ts<br>差异内容：PerformanceAnalysisKit|api/@ohos.hiviewdfx.hiAppEvent.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：kits\@kit.PerformanceAnalysisKit.d.ts<br>差异内容：PerformanceAnalysisKit|kits/@kit.PerformanceAnalysisKit.d.ts|
