| 操作 | 旧版本 | 新版本 | d.ts文件 |
| ---- | ------ | ------ | -------- |
|API废弃版本变更|类名：global；<br>API声明：declare namespace FaultLogger<br>差异内容：NA|类名：global；<br>API声明：declare namespace FaultLogger<br>差异内容：18|api/@ohos.faultLogger.d.ts|
|API废弃版本变更|类名：FaultLogger；<br>API声明：enum FaultType<br>差异内容：NA|类名：FaultLogger；<br>API声明：enum FaultType<br>差异内容：18|api/@ohos.faultLogger.d.ts|
|API废弃版本变更|类名：FaultType；<br>API声明：NO_SPECIFIC = 0<br>差异内容：NA|类名：FaultType；<br>API声明：NO_SPECIFIC = 0<br>差异内容：18|api/@ohos.faultLogger.d.ts|
|API废弃版本变更|类名：FaultType；<br>API声明：CPP_CRASH = 2<br>差异内容：NA|类名：FaultType；<br>API声明：CPP_CRASH = 2<br>差异内容：18|api/@ohos.faultLogger.d.ts|
|API废弃版本变更|类名：FaultType；<br>API声明：JS_CRASH = 3<br>差异内容：NA|类名：FaultType；<br>API声明：JS_CRASH = 3<br>差异内容：18|api/@ohos.faultLogger.d.ts|
|API废弃版本变更|类名：FaultType；<br>API声明：APP_FREEZE = 4<br>差异内容：NA|类名：FaultType；<br>API声明：APP_FREEZE = 4<br>差异内容：18|api/@ohos.faultLogger.d.ts|
|API废弃版本变更|类名：FaultLogger；<br>API声明：function query(faultType: FaultType, callback: AsyncCallback\<Array\<FaultLogInfo>>): void;<br>差异内容：NA|类名：FaultLogger；<br>API声明：function query(faultType: FaultType, callback: AsyncCallback\<Array\<FaultLogInfo>>): void;<br>差异内容：18|api/@ohos.faultLogger.d.ts|
|API废弃版本变更|类名：FaultLogger；<br>API声明：function query(faultType: FaultType): Promise\<Array\<FaultLogInfo>>;<br>差异内容：NA|类名：FaultLogger；<br>API声明：function query(faultType: FaultType): Promise\<Array\<FaultLogInfo>>;<br>差异内容：18|api/@ohos.faultLogger.d.ts|
|API废弃版本变更|类名：FaultLogger；<br>API声明：interface FaultLogInfo<br>差异内容：NA|类名：FaultLogger；<br>API声明：interface FaultLogInfo<br>差异内容：18|api/@ohos.faultLogger.d.ts|
|API废弃版本变更|类名：FaultLogInfo；<br>API声明：pid: number;<br>差异内容：NA|类名：FaultLogInfo；<br>API声明：pid: number;<br>差异内容：18|api/@ohos.faultLogger.d.ts|
|API废弃版本变更|类名：FaultLogInfo；<br>API声明：uid: number;<br>差异内容：NA|类名：FaultLogInfo；<br>API声明：uid: number;<br>差异内容：18|api/@ohos.faultLogger.d.ts|
|API废弃版本变更|类名：FaultLogInfo；<br>API声明：type: FaultType;<br>差异内容：NA|类名：FaultLogInfo；<br>API声明：type: FaultType;<br>差异内容：18|api/@ohos.faultLogger.d.ts|
|API废弃版本变更|类名：FaultLogInfo；<br>API声明：timestamp: number;<br>差异内容：NA|类名：FaultLogInfo；<br>API声明：timestamp: number;<br>差异内容：18|api/@ohos.faultLogger.d.ts|
|API废弃版本变更|类名：FaultLogInfo；<br>API声明：reason: string;<br>差异内容：NA|类名：FaultLogInfo；<br>API声明：reason: string;<br>差异内容：18|api/@ohos.faultLogger.d.ts|
|API废弃版本变更|类名：FaultLogInfo；<br>API声明：module: string;<br>差异内容：NA|类名：FaultLogInfo；<br>API声明：module: string;<br>差异内容：18|api/@ohos.faultLogger.d.ts|
|API废弃版本变更|类名：FaultLogInfo；<br>API声明：summary: string;<br>差异内容：NA|类名：FaultLogInfo；<br>API声明：summary: string;<br>差异内容：18|api/@ohos.faultLogger.d.ts|
|API废弃版本变更|类名：FaultLogInfo；<br>API声明：fullLog: string;<br>差异内容：NA|类名：FaultLogInfo；<br>API声明：fullLog: string;<br>差异内容：18|api/@ohos.faultLogger.d.ts|
|新增API|NA|类名：hidebug；<br>API声明：function dumpJsRawHeapData(needGC?: boolean): Promise\<string>;<br>差异内容：function dumpJsRawHeapData(needGC?: boolean): Promise\<string>;|api/@ohos.hidebug.d.ts|
