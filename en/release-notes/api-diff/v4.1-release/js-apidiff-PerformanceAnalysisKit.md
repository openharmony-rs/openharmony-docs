| Change Type | Old Version | New Version | d.ts File |
| ---- | ------ | ------ | -------- |
|New API |NA|Class name: global;<br>API declaration: declare namespace bytrace<br>Differences: declare namespace bytrace|api/@ohos.bytrace.d.ts|
|New API |NA|Class name: bytrace;<br>API declaration: function startTrace(name: string, taskId: number, expectedTime?: number): void;<br>Differences: function startTrace(name: string, taskId: number, expectedTime?: number): void;|api/@ohos.bytrace.d.ts|
|New API |NA|Class name: bytrace;<br>API declaration: function finishTrace(name: string, taskId: number): void;<br>Differences: function finishTrace(name: string, taskId: number): void;|api/@ohos.bytrace.d.ts|
|New API |NA|Class name: bytrace;<br>API declaration: function traceByValue(name: string, count: number): void;<br>Differences: function traceByValue(name: string, count: number): void;|api/@ohos.bytrace.d.ts|
|New API |NA|Class name: global;<br>API declaration: declare namespace FaultLogger<br>Differences: declare namespace FaultLogger|api/@ohos.faultLogger.d.ts|
|New API |NA|Class name: FaultLogger;<br>API declaration: enum FaultType<br>Differences: enum FaultType|api/@ohos.faultLogger.d.ts|
|New API |NA|Class name: FaultType;<br>API declaration: NO_SPECIFIC = 0<br>Differences: NO_SPECIFIC = 0|api/@ohos.faultLogger.d.ts|
|New API |NA|Class name: FaultType;<br>API declaration: CPP_CRASH = 2<br>Differences: CPP_CRASH = 2|api/@ohos.faultLogger.d.ts|
|New API |NA|Class name: FaultType;<br>API declaration: JS_CRASH = 3<br>Differences: JS_CRASH = 3|api/@ohos.faultLogger.d.ts|
|New API |NA|Class name: FaultType;<br>API declaration: APP_FREEZE = 4<br>Differences: APP_FREEZE = 4|api/@ohos.faultLogger.d.ts|
|New API |NA|Class name: FaultLogger;<br>API declaration: function querySelfFaultLog(faultType: FaultType, callback: AsyncCallback\<Array\<FaultLogInfo>>): void;<br>Differences: function querySelfFaultLog(faultType: FaultType, callback: AsyncCallback\<Array\<FaultLogInfo>>): void;|api/@ohos.faultLogger.d.ts|
|New API |NA|Class name: FaultLogger;<br>API declaration: function querySelfFaultLog(faultType: FaultType): Promise\<Array\<FaultLogInfo>>;<br>Differences: function querySelfFaultLog(faultType: FaultType): Promise\<Array\<FaultLogInfo>>;|api/@ohos.faultLogger.d.ts|
|New API |NA|Class name: FaultLogger;<br>API declaration: function query(faultType: FaultType, callback: AsyncCallback\<Array\<FaultLogInfo>>): void;<br>Differences: function query(faultType: FaultType, callback: AsyncCallback\<Array\<FaultLogInfo>>): void;|api/@ohos.faultLogger.d.ts|
|New API |NA|Class name: FaultLogger;<br>API declaration: function query(faultType: FaultType): Promise\<Array\<FaultLogInfo>>;<br>Differences: function query(faultType: FaultType): Promise\<Array\<FaultLogInfo>>;|api/@ohos.faultLogger.d.ts|
|New API |NA|Class name: FaultLogger;<br>API declaration: interface FaultLogInfo<br>Differences: interface FaultLogInfo|api/@ohos.faultLogger.d.ts|
|New API |NA|Class name: FaultLogInfo;<br>API declaration: pid: number;<br>Differences: pid: number;|api/@ohos.faultLogger.d.ts|
|New API |NA|Class name: FaultLogInfo;<br>API declaration: uid: number;<br>Differences: uid: number;|api/@ohos.faultLogger.d.ts|
|New API |NA|Class name: FaultLogInfo;<br>API declaration: type: FaultType;<br>Differences: type: FaultType;|api/@ohos.faultLogger.d.ts|
|New API |NA|Class name: FaultLogInfo;<br>API declaration: timestamp: number;<br>Differences: timestamp: number;|api/@ohos.faultLogger.d.ts|
|New API |NA|Class name: FaultLogInfo;<br>API declaration: reason: string;<br>Differences: reason: string;|api/@ohos.faultLogger.d.ts|
|New API |NA|Class name: FaultLogInfo;<br>API declaration: module: string;<br>Differences: module: string;|api/@ohos.faultLogger.d.ts|
|New API |NA|Class name: FaultLogInfo;<br>API declaration: summary: string;<br>Differences: summary: string;|api/@ohos.faultLogger.d.ts|
|New API |NA|Class name: FaultLogInfo;<br>API declaration: fullLog: string;<br>Differences: fullLog: string;|api/@ohos.faultLogger.d.ts|
|New API |NA|Class name: global;<br>API declaration: declare namespace hiAppEvent<br>Differences: declare namespace hiAppEvent|api/@ohos.hiAppEvent.d.ts|
|New API |NA|Class name: hiAppEvent;<br>API declaration: enum EventType<br>Differences: enum EventType|api/@ohos.hiAppEvent.d.ts|
|New API |NA|Class name: EventType;<br>API declaration: FAULT = 1<br>Differences: FAULT = 1|api/@ohos.hiAppEvent.d.ts|
|New API |NA|Class name: EventType;<br>API declaration: STATISTIC = 2<br>Differences: STATISTIC = 2|api/@ohos.hiAppEvent.d.ts|
|New API |NA|Class name: EventType;<br>API declaration: SECURITY = 3<br>Differences: SECURITY = 3|api/@ohos.hiAppEvent.d.ts|
|New API |NA|Class name: EventType;<br>API declaration: BEHAVIOR = 4<br>Differences: BEHAVIOR = 4|api/@ohos.hiAppEvent.d.ts|
|New API |NA|Class name: hiAppEvent;<br>API declaration: namespace Event<br>Differences: namespace Event|api/@ohos.hiAppEvent.d.ts|
|New API |NA|Class name: Event;<br>API declaration: const USER_LOGIN: string;<br>Differences: const USER_LOGIN: string;|api/@ohos.hiAppEvent.d.ts|
|New API |NA|Class name: Event;<br>API declaration: const USER_LOGOUT: string;<br>Differences: const USER_LOGOUT: string;|api/@ohos.hiAppEvent.d.ts|
|New API |NA|Class name: Event;<br>API declaration: const DISTRIBUTED_SERVICE_START: string;<br>Differences: const DISTRIBUTED_SERVICE_START: string;|api/@ohos.hiAppEvent.d.ts|
|New API |NA|Class name: hiAppEvent;<br>API declaration: namespace Param<br>Differences: namespace Param|api/@ohos.hiAppEvent.d.ts|
|New API |NA|Class name: Param;<br>API declaration: const USER_ID: string;<br>Differences: const USER_ID: string;|api/@ohos.hiAppEvent.d.ts|
|New API |NA|Class name: Param;<br>API declaration: const DISTRIBUTED_SERVICE_NAME: string;<br>Differences: const DISTRIBUTED_SERVICE_NAME: string;|api/@ohos.hiAppEvent.d.ts|
|New API |NA|Class name: Param;<br>API declaration: const DISTRIBUTED_SERVICE_INSTANCE_ID: string;<br>Differences: const DISTRIBUTED_SERVICE_INSTANCE_ID: string;|api/@ohos.hiAppEvent.d.ts|
|New API |NA|Class name: hiAppEvent;<br>API declaration: function write(eventName: string, eventType: EventType, keyValues: object): Promise\<void>;<br>Differences: function write(eventName: string, eventType: EventType, keyValues: object): Promise\<void>;|api/@ohos.hiAppEvent.d.ts|
|New API |NA|Class name: hiAppEvent;<br>API declaration: function write(eventName: string, eventType: EventType, keyValues: object, callback: AsyncCallback\<void>): void;<br>Differences: function write(eventName: string, eventType: EventType, keyValues: object, callback: AsyncCallback\<void>): void;|api/@ohos.hiAppEvent.d.ts|
|New API |NA|Class name: hiAppEvent;<br>API declaration: function configure(config: ConfigOption): boolean;<br>Differences: function configure(config: ConfigOption): boolean;|api/@ohos.hiAppEvent.d.ts|
|New API |NA|Class name: hiAppEvent;<br>API declaration: interface ConfigOption<br>Differences: interface ConfigOption|api/@ohos.hiAppEvent.d.ts|
|New API |NA|Class name: ConfigOption;<br>API declaration: disable?: boolean;<br>Differences: disable?: boolean;|api/@ohos.hiAppEvent.d.ts|
|New API |NA|Class name: ConfigOption;<br>API declaration: maxStorage?: string;<br>Differences: maxStorage?: string;|api/@ohos.hiAppEvent.d.ts|
|New API |NA|Class name: global;<br>API declaration: declare namespace hichecker<br>Differences: declare namespace hichecker|api/@ohos.hichecker.d.ts|
|New API |NA|Class name: hichecker;<br>API declaration: const RULE_CAUTION_PRINT_LOG: 9223372036854775808n;<br>Differences: const RULE_CAUTION_PRINT_LOG: 9223372036854775808n;|api/@ohos.hichecker.d.ts|
|New API |NA|Class name: hichecker;<br>API declaration: const RULE_CAUTION_TRIGGER_CRASH: 4611686018427387904n;<br>Differences: const RULE_CAUTION_TRIGGER_CRASH: 4611686018427387904n;|api/@ohos.hichecker.d.ts|
|New API |NA|Class name: hichecker;<br>API declaration: const RULE_THREAD_CHECK_SLOW_PROCESS: 1n;<br>Differences: const RULE_THREAD_CHECK_SLOW_PROCESS: 1n;|api/@ohos.hichecker.d.ts|
|New API |NA|Class name: hichecker;<br>API declaration: const RULE_CHECK_ABILITY_CONNECTION_LEAK: 8589934592n;<br>Differences: const RULE_CHECK_ABILITY_CONNECTION_LEAK: 8589934592n;|api/@ohos.hichecker.d.ts|
|New API |NA|Class name: hichecker;<br>API declaration: const RULE_CHECK_ARKUI_PERFORMANCE: 17179869184n;<br>Differences: const RULE_CHECK_ARKUI_PERFORMANCE: 17179869184n;|api/@ohos.hichecker.d.ts|
|New API |NA|Class name: hichecker;<br>API declaration: function addRule(rule: bigint): void;<br>Differences: function addRule(rule: bigint): void;|api/@ohos.hichecker.d.ts|
|New API |NA|Class name: hichecker;<br>API declaration: function removeRule(rule: bigint): void;<br>Differences: function removeRule(rule: bigint): void;|api/@ohos.hichecker.d.ts|
|New API |NA|Class name: hichecker;<br>API declaration: function getRule(): bigint;<br>Differences: function getRule(): bigint;|api/@ohos.hichecker.d.ts|
|New API |NA|Class name: hichecker;<br>API declaration: function contains(rule: bigint): boolean;<br>Differences: function contains(rule: bigint): boolean;|api/@ohos.hichecker.d.ts|
|New API |NA|Class name: hichecker;<br>API declaration: function addCheckRule(rule: bigint): void;<br>Differences: function addCheckRule(rule: bigint): void;|api/@ohos.hichecker.d.ts|
|New API |NA|Class name: hichecker;<br>API declaration: function removeCheckRule(rule: bigint): void;<br>Differences: function removeCheckRule(rule: bigint): void;|api/@ohos.hichecker.d.ts|
|New API |NA|Class name: hichecker;<br>API declaration: function containsCheckRule(rule: bigint): boolean;<br>Differences: function containsCheckRule(rule: bigint): boolean;|api/@ohos.hichecker.d.ts|
|New API |NA|Class name: global;<br>API declaration: declare namespace hidebug<br>Differences: declare namespace hidebug|api/@ohos.hidebug.d.ts|
|New API |NA|Class name: hidebug;<br>API declaration: function getNativeHeapSize(): bigint;<br>Differences: function getNativeHeapSize(): bigint;|api/@ohos.hidebug.d.ts|
|New API |NA|Class name: hidebug;<br>API declaration: function getNativeHeapAllocatedSize(): bigint;<br>Differences: function getNativeHeapAllocatedSize(): bigint;|api/@ohos.hidebug.d.ts|
|New API |NA|Class name: hidebug;<br>API declaration: function getNativeHeapFreeSize(): bigint;<br>Differences: function getNativeHeapFreeSize(): bigint;|api/@ohos.hidebug.d.ts|
|New API |NA|Class name: hidebug;<br>API declaration: function getVss(): bigint;<br>Differences: function getVss(): bigint;|api/@ohos.hidebug.d.ts|
|New API |NA|Class name: hidebug;<br>API declaration: function getPss(): bigint;<br>Differences: function getPss(): bigint;|api/@ohos.hidebug.d.ts|
|New API |NA|Class name: hidebug;<br>API declaration: function getSharedDirty(): bigint;<br>Differences: function getSharedDirty(): bigint;|api/@ohos.hidebug.d.ts|
|New API |NA|Class name: hidebug;<br>API declaration: function getPrivateDirty(): bigint;<br>Differences: function getPrivateDirty(): bigint;|api/@ohos.hidebug.d.ts|
|New API |NA|Class name: hidebug;<br>API declaration: function getCpuUsage(): number;<br>Differences: function getCpuUsage(): number;|api/@ohos.hidebug.d.ts|
|New API |NA|Class name: hidebug;<br>API declaration: function startProfiling(filename: string): void;<br>Differences: function startProfiling(filename: string): void;|api/@ohos.hidebug.d.ts|
|New API |NA|Class name: hidebug;<br>API declaration: function stopProfiling(): void;<br>Differences: function stopProfiling(): void;|api/@ohos.hidebug.d.ts|
|New API |NA|Class name: hidebug;<br>API declaration: function dumpHeapData(filename: string): void;<br>Differences: function dumpHeapData(filename: string): void;|api/@ohos.hidebug.d.ts|
|New API |NA|Class name: hidebug;<br>API declaration: function startJsCpuProfiling(filename: string): void;<br>Differences: function startJsCpuProfiling(filename: string): void;|api/@ohos.hidebug.d.ts|
|New API |NA|Class name: hidebug;<br>API declaration: function stopJsCpuProfiling(): void;<br>Differences: function stopJsCpuProfiling(): void;|api/@ohos.hidebug.d.ts|
|New API |NA|Class name: hidebug;<br>API declaration: function dumpJsHeapData(filename: string): void;<br>Differences: function dumpJsHeapData(filename: string): void;|api/@ohos.hidebug.d.ts|
|New API |NA|Class name: hidebug;<br>API declaration: function getServiceDump(serviceid: number, fd: number, args: Array\<string>): void;<br>Differences: function getServiceDump(serviceid: number, fd: number, args: Array\<string>): void;|api/@ohos.hidebug.d.ts|
|New API |NA|Class name: global;<br>API declaration: declare namespace hilog<br>Differences: declare namespace hilog|api/@ohos.hilog.d.ts|
|New API |NA|Class name: hilog;<br>API declaration: function debug(domain: number, tag: string, format: string, ...args: any[]): void;<br>Differences: function debug(domain: number, tag: string, format: string, ...args: any[]): void;|api/@ohos.hilog.d.ts|
|New API |NA|Class name: hilog;<br>API declaration: function info(domain: number, tag: string, format: string, ...args: any[]): void;<br>Differences: function info(domain: number, tag: string, format: string, ...args: any[]): void;|api/@ohos.hilog.d.ts|
|New API |NA|Class name: hilog;<br>API declaration: function warn(domain: number, tag: string, format: string, ...args: any[]): void;<br>Differences: function warn(domain: number, tag: string, format: string, ...args: any[]): void;|api/@ohos.hilog.d.ts|
|New API |NA|Class name: hilog;<br>API declaration: function error(domain: number, tag: string, format: string, ...args: any[]): void;<br>Differences: function error(domain: number, tag: string, format: string, ...args: any[]): void;|api/@ohos.hilog.d.ts|
|New API |NA|Class name: hilog;<br>API declaration: function fatal(domain: number, tag: string, format: string, ...args: any[]): void;<br>Differences: function fatal(domain: number, tag: string, format: string, ...args: any[]): void;|api/@ohos.hilog.d.ts|
|New API |NA|Class name: hilog;<br>API declaration: function isLoggable(domain: number, tag: string, level: LogLevel): boolean;<br>Differences: function isLoggable(domain: number, tag: string, level: LogLevel): boolean;|api/@ohos.hilog.d.ts|
|New API |NA|Class name: hilog;<br>API declaration: enum LogLevel<br>Differences: enum LogLevel|api/@ohos.hilog.d.ts|
|New API |NA|Class name: LogLevel;<br>API declaration: DEBUG = 3<br>Differences: DEBUG = 3|api/@ohos.hilog.d.ts|
|New API |NA|Class name: LogLevel;<br>API declaration: INFO = 4<br>Differences: INFO = 4|api/@ohos.hilog.d.ts|
|New API |NA|Class name: LogLevel;<br>API declaration: WARN = 5<br>Differences: WARN = 5|api/@ohos.hilog.d.ts|
|New API |NA|Class name: LogLevel;<br>API declaration: ERROR = 6<br>Differences: ERROR = 6|api/@ohos.hilog.d.ts|
|New API |NA|Class name: LogLevel;<br>API declaration: FATAL = 7<br>Differences: FATAL = 7|api/@ohos.hilog.d.ts|
|New API |NA|Class name: global;<br>API declaration: declare namespace hiTraceChain<br>Differences: declare namespace hiTraceChain|api/@ohos.hiTraceChain.d.ts|
|New API |NA|Class name: hiTraceChain;<br>API declaration: enum HiTraceFlag<br>Differences: enum HiTraceFlag|api/@ohos.hiTraceChain.d.ts|
|New API |NA|Class name: HiTraceFlag;<br>API declaration: DEFAULT = 0<br>Differences: DEFAULT = 0|api/@ohos.hiTraceChain.d.ts|
|New API |NA|Class name: HiTraceFlag;<br>API declaration: INCLUDE_ASYNC = 1<br>Differences: INCLUDE_ASYNC = 1|api/@ohos.hiTraceChain.d.ts|
|New API |NA|Class name: HiTraceFlag;<br>API declaration: DONOT_CREATE_SPAN = 1 \<\< 1<br>Differences: DONOT_CREATE_SPAN = 1 \<\< 1|api/@ohos.hiTraceChain.d.ts|
|New API |NA|Class name: HiTraceFlag;<br>API declaration: TP_INFO = 1 \<\< 2<br>Differences: TP_INFO = 1 \<\< 2|api/@ohos.hiTraceChain.d.ts|
|New API |NA|Class name: HiTraceFlag;<br>API declaration: NO_BE_INFO = 1 \<\< 3<br>Differences: NO_BE_INFO = 1 \<\< 3|api/@ohos.hiTraceChain.d.ts|
|New API |NA|Class name: HiTraceFlag;<br>API declaration: DISABLE_LOG = 1 \<\< 4<br>Differences: DISABLE_LOG = 1 \<\< 4|api/@ohos.hiTraceChain.d.ts|
|New API |NA|Class name: HiTraceFlag;<br>API declaration: FAILURE_TRIGGER = 1 \<\< 5<br>Differences: FAILURE_TRIGGER = 1 \<\< 5|api/@ohos.hiTraceChain.d.ts|
|New API |NA|Class name: HiTraceFlag;<br>API declaration: D2D_TP_INFO = 1 \<\< 6<br>Differences: D2D_TP_INFO = 1 \<\< 6|api/@ohos.hiTraceChain.d.ts|
|New API |NA|Class name: hiTraceChain;<br>API declaration: enum HiTraceTracepointType<br>Differences: enum HiTraceTracepointType|api/@ohos.hiTraceChain.d.ts|
|New API |NA|Class name: HiTraceTracepointType;<br>API declaration: CS = 0<br>Differences: CS = 0|api/@ohos.hiTraceChain.d.ts|
|New API |NA|Class name: HiTraceTracepointType;<br>API declaration: CR = 1<br>Differences: CR = 1|api/@ohos.hiTraceChain.d.ts|
|New API |NA|Class name: HiTraceTracepointType;<br>API declaration: SS = 2<br>Differences: SS = 2|api/@ohos.hiTraceChain.d.ts|
|New API |NA|Class name: HiTraceTracepointType;<br>API declaration: SR = 3<br>Differences: SR = 3|api/@ohos.hiTraceChain.d.ts|
|New API |NA|Class name: HiTraceTracepointType;<br>API declaration: GENERAL = 4<br>Differences: GENERAL = 4|api/@ohos.hiTraceChain.d.ts|
|New API |NA|Class name: hiTraceChain;<br>API declaration: enum HiTraceCommunicationMode<br>Differences: enum HiTraceCommunicationMode|api/@ohos.hiTraceChain.d.ts|
|New API |NA|Class name: HiTraceCommunicationMode;<br>API declaration: DEFAULT = 0<br>Differences: DEFAULT = 0|api/@ohos.hiTraceChain.d.ts|
|New API |NA|Class name: HiTraceCommunicationMode;<br>API declaration: THREAD = 1<br>Differences: THREAD = 1|api/@ohos.hiTraceChain.d.ts|
|New API |NA|Class name: HiTraceCommunicationMode;<br>API declaration: PROCESS = 2<br>Differences: PROCESS = 2|api/@ohos.hiTraceChain.d.ts|
|New API |NA|Class name: HiTraceCommunicationMode;<br>API declaration: DEVICE = 3<br>Differences: DEVICE = 3|api/@ohos.hiTraceChain.d.ts|
|New API |NA|Class name: hiTraceChain;<br>API declaration: interface HiTraceId<br>Differences: interface HiTraceId|api/@ohos.hiTraceChain.d.ts|
|New API |NA|Class name: HiTraceId;<br>API declaration: chainId: bigint;<br>Differences: chainId: bigint;|api/@ohos.hiTraceChain.d.ts|
|New API |NA|Class name: HiTraceId;<br>API declaration: spanId?: number;<br>Differences: spanId?: number;|api/@ohos.hiTraceChain.d.ts|
|New API |NA|Class name: HiTraceId;<br>API declaration: parentSpanId?: number;<br>Differences: parentSpanId?: number;|api/@ohos.hiTraceChain.d.ts|
|New API |NA|Class name: HiTraceId;<br>API declaration: flags?: number;<br>Differences: flags?: number;|api/@ohos.hiTraceChain.d.ts|
|New API |NA|Class name: hiTraceChain;<br>API declaration: function begin(name: string, flags?: number): HiTraceId;<br>Differences: function begin(name: string, flags?: number): HiTraceId;|api/@ohos.hiTraceChain.d.ts|
|New API |NA|Class name: hiTraceChain;<br>API declaration: function end(id: HiTraceId): void;<br>Differences: function end(id: HiTraceId): void;|api/@ohos.hiTraceChain.d.ts|
|New API |NA|Class name: hiTraceChain;<br>API declaration: function getId(): HiTraceId;<br>Differences: function getId(): HiTraceId;|api/@ohos.hiTraceChain.d.ts|
|New API |NA|Class name: hiTraceChain;<br>API declaration: function setId(id: HiTraceId): void;<br>Differences: function setId(id: HiTraceId): void;|api/@ohos.hiTraceChain.d.ts|
|New API |NA|Class name: hiTraceChain;<br>API declaration: function clearId(): void;<br>Differences: function clearId(): void;|api/@ohos.hiTraceChain.d.ts|
|New API |NA|Class name: hiTraceChain;<br>API declaration: function createSpan(): HiTraceId;<br>Differences: function createSpan(): HiTraceId;|api/@ohos.hiTraceChain.d.ts|
|New API |NA|Class name: hiTraceChain;<br>API declaration: function tracepoint(mode: HiTraceCommunicationMode, type: HiTraceTracepointType, id: HiTraceId, msg?: string): void;<br>Differences: function tracepoint(mode: HiTraceCommunicationMode, type: HiTraceTracepointType, id: HiTraceId, msg?: string): void;|api/@ohos.hiTraceChain.d.ts|
|New API |NA|Class name: hiTraceChain;<br>API declaration: function isValid(id: HiTraceId): boolean;<br>Differences: function isValid(id: HiTraceId): boolean;|api/@ohos.hiTraceChain.d.ts|
|New API |NA|Class name: hiTraceChain;<br>API declaration: function isFlagEnabled(id: HiTraceId, flag: HiTraceFlag): boolean;<br>Differences: function isFlagEnabled(id: HiTraceId, flag: HiTraceFlag): boolean;|api/@ohos.hiTraceChain.d.ts|
|New API |NA|Class name: hiTraceChain;<br>API declaration: function enableFlag(id: HiTraceId, flag: HiTraceFlag): void;<br>Differences: function enableFlag(id: HiTraceId, flag: HiTraceFlag): void;|api/@ohos.hiTraceChain.d.ts|
|New API |NA|Class name: global;<br>API declaration: declare namespace hiTraceMeter<br>Differences: declare namespace hiTraceMeter|api/@ohos.hiTraceMeter.d.ts|
|New API |NA|Class name: hiTraceMeter;<br>API declaration: function startTrace(name: string, taskId: number): void;<br>Differences: function startTrace(name: string, taskId: number): void;|api/@ohos.hiTraceMeter.d.ts|
|New API |NA|Class name: hiTraceMeter;<br>API declaration: function finishTrace(name: string, taskId: number): void;<br>Differences: function finishTrace(name: string, taskId: number): void;|api/@ohos.hiTraceMeter.d.ts|
|New API |NA|Class name: hiTraceMeter;<br>API declaration: function traceByValue(name: string, count: number): void;<br>Differences: function traceByValue(name: string, count: number): void;|api/@ohos.hiTraceMeter.d.ts|
|New API |NA|Class name: global;<br>API declaration: declare namespace hiAppEvent<br>Differences: declare namespace hiAppEvent|api/@ohos.hiviewdfx.hiAppEvent.d.ts|
|New API |NA|Class name: hiAppEvent;<br>API declaration: enum EventType<br>Differences: enum EventType|api/@ohos.hiviewdfx.hiAppEvent.d.ts|
|New API |NA|Class name: EventType;<br>API declaration: FAULT = 1<br>Differences: FAULT = 1|api/@ohos.hiviewdfx.hiAppEvent.d.ts|
|New API |NA|Class name: EventType;<br>API declaration: STATISTIC = 2<br>Differences: STATISTIC = 2|api/@ohos.hiviewdfx.hiAppEvent.d.ts|
|New API |NA|Class name: EventType;<br>API declaration: SECURITY = 3<br>Differences: SECURITY = 3|api/@ohos.hiviewdfx.hiAppEvent.d.ts|
|New API |NA|Class name: EventType;<br>API declaration: BEHAVIOR = 4<br>Differences: BEHAVIOR = 4|api/@ohos.hiviewdfx.hiAppEvent.d.ts|
|New API |NA|Class name: hiAppEvent;<br>API declaration: namespace domain<br>Differences: namespace domain|api/@ohos.hiviewdfx.hiAppEvent.d.ts|
|New API |NA|Class name: domain;<br>API declaration: const OS: string;<br>Differences: const OS: string;|api/@ohos.hiviewdfx.hiAppEvent.d.ts|
|New API |NA|Class name: hiAppEvent;<br>API declaration: namespace event<br>Differences: namespace event|api/@ohos.hiviewdfx.hiAppEvent.d.ts|
|New API |NA|Class name: event;<br>API declaration: const USER_LOGIN: string;<br>Differences: const USER_LOGIN: string;|api/@ohos.hiviewdfx.hiAppEvent.d.ts|
|New API |NA|Class name: event;<br>API declaration: const USER_LOGOUT: string;<br>Differences: const USER_LOGOUT: string;|api/@ohos.hiviewdfx.hiAppEvent.d.ts|
|New API |NA|Class name: event;<br>API declaration: const DISTRIBUTED_SERVICE_START: string;<br>Differences: const DISTRIBUTED_SERVICE_START: string;|api/@ohos.hiviewdfx.hiAppEvent.d.ts|
|New API |NA|Class name: event;<br>API declaration: const APP_CRASH: string;<br>Differences: const APP_CRASH: string;|api/@ohos.hiviewdfx.hiAppEvent.d.ts|
|New API |NA|Class name: event;<br>API declaration: const APP_FREEZE: string;<br>Differences: const APP_FREEZE: string;|api/@ohos.hiviewdfx.hiAppEvent.d.ts|
|New API |NA|Class name: hiAppEvent;<br>API declaration: namespace param<br>Differences: namespace param|api/@ohos.hiviewdfx.hiAppEvent.d.ts|
|New API |NA|Class name: param;<br>API declaration: const USER_ID: string;<br>Differences: const USER_ID: string;|api/@ohos.hiviewdfx.hiAppEvent.d.ts|
|New API |NA|Class name: param;<br>API declaration: const DISTRIBUTED_SERVICE_NAME: string;<br>Differences: const DISTRIBUTED_SERVICE_NAME: string;|api/@ohos.hiviewdfx.hiAppEvent.d.ts|
|New API |NA|Class name: param;<br>API declaration: const DISTRIBUTED_SERVICE_INSTANCE_ID: string;<br>Differences: const DISTRIBUTED_SERVICE_INSTANCE_ID: string;|api/@ohos.hiviewdfx.hiAppEvent.d.ts|
|New API |NA|Class name: hiAppEvent;<br>API declaration: function configure(config: ConfigOption): void;<br>Differences: function configure(config: ConfigOption): void;|api/@ohos.hiviewdfx.hiAppEvent.d.ts|
|New API |NA|Class name: hiAppEvent;<br>API declaration: interface ConfigOption<br>Differences: interface ConfigOption|api/@ohos.hiviewdfx.hiAppEvent.d.ts|
|New API |NA|Class name: ConfigOption;<br>API declaration: disable?: boolean;<br>Differences: disable?: boolean;|api/@ohos.hiviewdfx.hiAppEvent.d.ts|
|New API |NA|Class name: ConfigOption;<br>API declaration: maxStorage?: string;<br>Differences: maxStorage?: string;|api/@ohos.hiviewdfx.hiAppEvent.d.ts|
|New API |NA|Class name: hiAppEvent;<br>API declaration: interface AppEventInfo<br>Differences: interface AppEventInfo|api/@ohos.hiviewdfx.hiAppEvent.d.ts|
|New API |NA|Class name: AppEventInfo;<br>API declaration: domain: string;<br>Differences: domain: string;|api/@ohos.hiviewdfx.hiAppEvent.d.ts|
|New API |NA|Class name: AppEventInfo;<br>API declaration: name: string;<br>Differences: name: string;|api/@ohos.hiviewdfx.hiAppEvent.d.ts|
|New API |NA|Class name: AppEventInfo;<br>API declaration: eventType: EventType;<br>Differences: eventType: EventType;|api/@ohos.hiviewdfx.hiAppEvent.d.ts|
|New API |NA|Class name: AppEventInfo;<br>API declaration: params: object;<br>Differences: params: object;|api/@ohos.hiviewdfx.hiAppEvent.d.ts|
|New API |NA|Class name: hiAppEvent;<br>API declaration: function write(info: AppEventInfo): Promise\<void>;<br>Differences: function write(info: AppEventInfo): Promise\<void>;|api/@ohos.hiviewdfx.hiAppEvent.d.ts|
|New API |NA|Class name: hiAppEvent;<br>API declaration: function write(info: AppEventInfo, callback: AsyncCallback\<void>): void;<br>Differences: function write(info: AppEventInfo, callback: AsyncCallback\<void>): void;|api/@ohos.hiviewdfx.hiAppEvent.d.ts|
|New API |NA|Class name: hiAppEvent;<br>API declaration: interface AppEventPackage<br>Differences: interface AppEventPackage|api/@ohos.hiviewdfx.hiAppEvent.d.ts|
|New API |NA|Class name: AppEventPackage;<br>API declaration: packageId: number;<br>Differences: packageId: number;|api/@ohos.hiviewdfx.hiAppEvent.d.ts|
|New API |NA|Class name: AppEventPackage;<br>API declaration: row: number;<br>Differences: row: number;|api/@ohos.hiviewdfx.hiAppEvent.d.ts|
|New API |NA|Class name: AppEventPackage;<br>API declaration: size: number;<br>Differences: size: number;|api/@ohos.hiviewdfx.hiAppEvent.d.ts|
|New API |NA|Class name: AppEventPackage;<br>API declaration: data: string[];<br>Differences: data: string[];|api/@ohos.hiviewdfx.hiAppEvent.d.ts|
|New API |NA|Class name: hiAppEvent;<br>API declaration: class AppEventPackageHolder<br>Differences: class AppEventPackageHolder|api/@ohos.hiviewdfx.hiAppEvent.d.ts|
|New API |NA|Class name: AppEventPackageHolder;<br>API declaration: setSize(size: number): void;<br>Differences: setSize(size: number): void;|api/@ohos.hiviewdfx.hiAppEvent.d.ts|
|New API |NA|Class name: AppEventPackageHolder;<br>API declaration: takeNext(): AppEventPackage;<br>Differences: takeNext(): AppEventPackage;|api/@ohos.hiviewdfx.hiAppEvent.d.ts|
|New API |NA|Class name: hiAppEvent;<br>API declaration: interface TriggerCondition<br>Differences: interface TriggerCondition|api/@ohos.hiviewdfx.hiAppEvent.d.ts|
|New API |NA|Class name: TriggerCondition;<br>API declaration: row?: number;<br>Differences: row?: number;|api/@ohos.hiviewdfx.hiAppEvent.d.ts|
|New API |NA|Class name: TriggerCondition;<br>API declaration: size?: number;<br>Differences: size?: number;|api/@ohos.hiviewdfx.hiAppEvent.d.ts|
|New API |NA|Class name: TriggerCondition;<br>API declaration: timeOut?: number;<br>Differences: timeOut?: number;|api/@ohos.hiviewdfx.hiAppEvent.d.ts|
|New API |NA|Class name: hiAppEvent;<br>API declaration: interface AppEventFilter<br>Differences: interface AppEventFilter|api/@ohos.hiviewdfx.hiAppEvent.d.ts|
|New API |NA|Class name: AppEventFilter;<br>API declaration: domain: string;<br>Differences: domain: string;|api/@ohos.hiviewdfx.hiAppEvent.d.ts|
|New API |NA|Class name: AppEventFilter;<br>API declaration: eventTypes?: EventType[];<br>Differences: eventTypes?: EventType[];|api/@ohos.hiviewdfx.hiAppEvent.d.ts|
|New API |NA|Class name: AppEventFilter;<br>API declaration: names?: string[];<br>Differences: names?: string[];|api/@ohos.hiviewdfx.hiAppEvent.d.ts|
|New API |NA|Class name: hiAppEvent;<br>API declaration: interface AppEventGroup<br>Differences: interface AppEventGroup|api/@ohos.hiviewdfx.hiAppEvent.d.ts|
|New API |NA|Class name: AppEventGroup;<br>API declaration: name: string;<br>Differences: name: string;|api/@ohos.hiviewdfx.hiAppEvent.d.ts|
|New API |NA|Class name: AppEventGroup;<br>API declaration: appEventInfos: Array\<AppEventInfo>;<br>Differences: appEventInfos: Array\<AppEventInfo>;|api/@ohos.hiviewdfx.hiAppEvent.d.ts|
|New API |NA|Class name: hiAppEvent;<br>API declaration: interface Watcher<br>Differences: interface Watcher|api/@ohos.hiviewdfx.hiAppEvent.d.ts|
|New API |NA|Class name: Watcher;<br>API declaration: name: string;<br>Differences: name: string;|api/@ohos.hiviewdfx.hiAppEvent.d.ts|
|New API |NA|Class name: Watcher;<br>API declaration: triggerCondition?: TriggerCondition;<br>Differences: triggerCondition?: TriggerCondition;|api/@ohos.hiviewdfx.hiAppEvent.d.ts|
|New API |NA|Class name: Watcher;<br>API declaration: appEventFilters?: AppEventFilter[];<br>Differences: appEventFilters?: AppEventFilter[];|api/@ohos.hiviewdfx.hiAppEvent.d.ts|
|New API |NA|Class name: Watcher;<br>API declaration: onTrigger?: (curRow: number, curSize: number, holder: AppEventPackageHolder) => void;<br>Differences: onTrigger?: (curRow: number, curSize: number, holder: AppEventPackageHolder) => void;|api/@ohos.hiviewdfx.hiAppEvent.d.ts|
|New API |NA|Class name: Watcher;<br>API declaration: onReceive?: (domain: string, appEventGroups: Array\<AppEventGroup>) => void;<br>Differences: onReceive?: (domain: string, appEventGroups: Array\<AppEventGroup>) => void;|api/@ohos.hiviewdfx.hiAppEvent.d.ts|
|New API |NA|Class name: hiAppEvent;<br>API declaration: function addWatcher(watcher: Watcher): AppEventPackageHolder;<br>Differences: function addWatcher(watcher: Watcher): AppEventPackageHolder;|api/@ohos.hiviewdfx.hiAppEvent.d.ts|
|New API |NA|Class name: hiAppEvent;<br>API declaration: function removeWatcher(watcher: Watcher): void;<br>Differences: function removeWatcher(watcher: Watcher): void;|api/@ohos.hiviewdfx.hiAppEvent.d.ts|
|New API |NA|Class name: hiAppEvent;<br>API declaration: function clearData(): void;<br>Differences: function clearData(): void;|api/@ohos.hiviewdfx.hiAppEvent.d.ts|
|New API |NA|Class name: hiAppEvent;<br>API declaration: function setUserId(name: string, value: string): void;<br>Differences: function setUserId(name: string, value: string): void;|api/@ohos.hiviewdfx.hiAppEvent.d.ts|
|New API |NA|Class name: hiAppEvent;<br>API declaration: function getUserId(name: string): string;<br>Differences: function getUserId(name: string): string;|api/@ohos.hiviewdfx.hiAppEvent.d.ts|
|New API |NA|Class name: hiAppEvent;<br>API declaration: function setUserProperty(name: string, value: string): void;<br>Differences: function setUserProperty(name: string, value: string): void;|api/@ohos.hiviewdfx.hiAppEvent.d.ts|
|New API |NA|Class name: hiAppEvent;<br>API declaration: function getUserProperty(name: string): string;<br>Differences: function getUserProperty(name: string): string;|api/@ohos.hiviewdfx.hiAppEvent.d.ts|
|New API |NA|Class name: hiAppEvent;<br>API declaration: interface AppEventReportConfig<br>Differences: interface AppEventReportConfig|api/@ohos.hiviewdfx.hiAppEvent.d.ts|
|New API |NA|Class name: AppEventReportConfig;<br>API declaration: domain?: string;<br>Differences: domain?: string;|api/@ohos.hiviewdfx.hiAppEvent.d.ts|
|New API |NA|Class name: AppEventReportConfig;<br>API declaration: name?: string;<br>Differences: name?: string;|api/@ohos.hiviewdfx.hiAppEvent.d.ts|
|New API |NA|Class name: AppEventReportConfig;<br>API declaration: isRealTime?: boolean;<br>Differences: isRealTime?: boolean;|api/@ohos.hiviewdfx.hiAppEvent.d.ts|
|New API |NA|Class name: hiAppEvent;<br>API declaration: interface Processor<br>Differences: interface Processor|api/@ohos.hiviewdfx.hiAppEvent.d.ts|
|New API |NA|Class name: Processor;<br>API declaration: name: string;<br>Differences: name: string;|api/@ohos.hiviewdfx.hiAppEvent.d.ts|
|New API |NA|Class name: Processor;<br>API declaration: debugMode?: boolean;<br>Differences: debugMode?: boolean;|api/@ohos.hiviewdfx.hiAppEvent.d.ts|
|New API |NA|Class name: Processor;<br>API declaration: routeInfo?: string;<br>Differences: routeInfo?: string;|api/@ohos.hiviewdfx.hiAppEvent.d.ts|
|New API |NA|Class name: Processor;<br>API declaration: appId?: string;<br>Differences: appId?: string;|api/@ohos.hiviewdfx.hiAppEvent.d.ts|
|New API |NA|Class name: Processor;<br>API declaration: onStartReport?: boolean;<br>Differences: onStartReport?: boolean;|api/@ohos.hiviewdfx.hiAppEvent.d.ts|
|New API |NA|Class name: Processor;<br>API declaration: onBackgroundReport?: boolean;<br>Differences: onBackgroundReport?: boolean;|api/@ohos.hiviewdfx.hiAppEvent.d.ts|
|New API |NA|Class name: Processor;<br>API declaration: periodReport?: number;<br>Differences: periodReport?: number;|api/@ohos.hiviewdfx.hiAppEvent.d.ts|
|New API |NA|Class name: Processor;<br>API declaration: batchReport?: number;<br>Differences: batchReport?: number;|api/@ohos.hiviewdfx.hiAppEvent.d.ts|
|New API |NA|Class name: Processor;<br>API declaration: userIds?: string[];<br>Differences: userIds?: string[];|api/@ohos.hiviewdfx.hiAppEvent.d.ts|
|New API |NA|Class name: Processor;<br>API declaration: userProperties?: string[];<br>Differences: userProperties?: string[];|api/@ohos.hiviewdfx.hiAppEvent.d.ts|
|New API |NA|Class name: Processor;<br>API declaration: eventConfigs?: AppEventReportConfig[];<br>Differences: eventConfigs?: AppEventReportConfig[];|api/@ohos.hiviewdfx.hiAppEvent.d.ts|
|New API |NA|Class name: hiAppEvent;<br>API declaration: function addProcessor(processor: Processor): number;<br>Differences: function addProcessor(processor: Processor): number;|api/@ohos.hiviewdfx.hiAppEvent.d.ts|
|New API |NA|Class name: hiAppEvent;<br>API declaration: function removeProcessor(id: number): void;<br>Differences: function removeProcessor(id: number): void;|api/@ohos.hiviewdfx.hiAppEvent.d.ts|
|New Kit|Class name: global;<br>API declaration: <br>Differences: NA|Class name: global;<br>API declaration: api\@ohos.bytrace.d.ts<br>Differences: PerformanceAnalysisKit|api/@ohos.bytrace.d.ts|
|New Kit|Class name: global;<br>API declaration: <br>Differences: NA|Class name: global;<br>API declaration: api\@ohos.faultLogger.d.ts<br>Differences: PerformanceAnalysisKit|api/@ohos.faultLogger.d.ts|
|New Kit|Class name: global;<br>API declaration: <br>Differences: NA|Class name: global;<br>API declaration: api\@ohos.hiAppEvent.d.ts<br>Differences: PerformanceAnalysisKit|api/@ohos.hiAppEvent.d.ts|
|New Kit|Class name: global;<br>API declaration: <br>Differences: NA|Class name: global;<br>API declaration: api\@ohos.hichecker.d.ts<br>Differences: PerformanceAnalysisKit|api/@ohos.hichecker.d.ts|
|New Kit|Class name: global;<br>API declaration: <br>Differences: NA|Class name: global;<br>API declaration: api\@ohos.hidebug.d.ts<br>Differences: PerformanceAnalysisKit|api/@ohos.hidebug.d.ts|
|New Kit|Class name: global;<br>API declaration: <br>Differences: NA|Class name: global;<br>API declaration: api\@ohos.hilog.d.ts<br>Differences: PerformanceAnalysisKit|api/@ohos.hilog.d.ts|
|New Kit|Class name: global;<br>API declaration: <br>Differences: NA|Class name: global;<br>API declaration: api\@ohos.hiTraceChain.d.ts<br>Differences: PerformanceAnalysisKit|api/@ohos.hiTraceChain.d.ts|
|New Kit|Class name: global;<br>API declaration: <br>Differences: NA|Class name: global;<br>API declaration: api\@ohos.hiTraceMeter.d.ts<br>Differences: PerformanceAnalysisKit|api/@ohos.hiTraceMeter.d.ts|
|New Kit|Class name: global;<br>API declaration: <br>Differences: NA|Class name: global;<br>API declaration: api\@ohos.hiviewdfx.hiAppEvent.d.ts<br>Differences: PerformanceAnalysisKit|api/@ohos.hiviewdfx.hiAppEvent.d.ts|
|New Kit|Class name: global;<br>API declaration: <br>Differences: NA|Class name: global;<br>API declaration: kits\@kit.PerformanceAnalysisKit.d.ts<br>Differences: PerformanceAnalysisKit|kits/@kit.PerformanceAnalysisKit.d.ts|
