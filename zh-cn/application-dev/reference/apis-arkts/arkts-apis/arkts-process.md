# @ohos.process

**process** 模块提供进程管理相关接口，例如获取进程信息的接口。

**起始版本：** 7

**系统能力：** SystemCapability.Utils.Lang

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [abort](arkts-arkts-process-abort-f.md#abort-1) | 中止进程并生成核心文件。该方法会导致进程立即退出，请谨慎使用。<br/> |
| <!--DelRow-->[chdir](arkts-arkts-process-chdir-f-sys.md#chdir-1) | 修改当前目录。<br/> |
| <!--DelRow-->[cwd](arkts-arkts-process-cwd-f-sys.md#cwd-1) | 返回当前工作目录。<br/> |
| [exit](arkts-arkts-process-exit-f.md#exit-1) | 终止程序。<br/><br/>请谨慎使用此接口。调用此接口后应用将退出。如果输入参数非 0，可能会导致数据丢失或出现异常。<br/> |
| [getEnvironmentVar](arkts-arkts-process-getenvironmentvar-f.md#getEnvironmentVar-1) | 获取环境变量名对应的值。<br/> |
| [getPastCpuTime](arkts-arkts-process-getpastcputime-f.md#getPastCpuTime-1) | 获取进程启动到当前时间的 CPU 时间（以毫秒为单位）。<br/> |
| [getStartRealtime](arkts-arkts-process-getstartrealtime-f.md#getStartRealtime-1) | 获取系统启动到进程启动的实时时间（以毫秒为单位，不包含系统休眠时间）。<br/> |
| [getSystemConfig](arkts-arkts-process-getsystemconfig-f.md#getSystemConfig-1) | 获取系统配置信息。<br/> |
| [getThreadPriority](arkts-arkts-process-getthreadpriority-f.md#getThreadPriority-1) | 根据指定的 tid 获取线程优先级，优先级顺序取决于当前操作系统。<br/> |
| [getUidForName](arkts-arkts-process-getuidforname-f.md#getUidForName-1) | 根据指定的用户名，从系统的用户数据库中获取该用户的 uid。<br/> |
| [is64Bit](arkts-arkts-process-is64bit-f.md#is64Bit-1) | 检查运行环境是否为 64 位。<br/> |
| [isAppUid](arkts-arkts-process-isappuid-f.md#isAppUid-1) | 判断 uid 是否属于应用程序。<br/> |
| [isIsolatedProcess](arkts-arkts-process-isisolatedprocess-f.md#isIsolatedProcess-1) | 检查进程是否已被隔离。<br/> |
| [kill](arkts-arkts-process-kill-f.md#kill-1) | 发送信号到指定进程，结束该进程。<br/> |
| <!--DelRow-->[off](arkts-arkts-process-off-f-sys.md#off-1) | 移除已注册的事件。<br/> |
| <!--DelRow-->[on](arkts-arkts-process-on-f-sys.md#on-1) | 注册事件。<br/> |
| <!--DelRow-->[runCmd](arkts-arkts-process-runcmd-f-sys.md#runCmd-1) | 返回一个子进程对象，并 spawn 一个新的 ChildProcess 来运行命令。<br/> |
| [uptime](arkts-arkts-process-uptime-f.md#uptime-1) | 获取当前系统已运行的时间（以秒为单位）。<br/> |

### 类

| 名称 | 说明 |
| --- | --- |
| [ProcessManager](arkts-arkts-process-processmanager-c.md) | 提供进程管理相关接口，包括进程 UID 判断、用户信息查询、线程优先级获取、环境变量获取、进程退出和信号发送等功能。<br/><br/>通过 `new process.ProcessManager()` 构造 ProcessManager 对象。<br/> |

### 接口

| 名称 | 说明 |
| --- | --- |
| <!--DelRow-->[ChildProcess](arkts-arkts-process-childprocess-i-sys.md) | childprocess 对象可用于创建新的进程。<br/> |
| <!--DelRow-->[ConditionType](arkts-arkts-process-conditiontype-i-sys.md) | 提供 ConditionType 类型，包括 timeout、killSignal、maxBuffer。<br/> |

### 类型

| 名称 | 说明 |
| --- | --- |
| [EventListener](arkts-arkts-process-eventlistener-t.md) | 用户存储的事件信息。<br/> |

### 常量

| 名称 | 说明 |
| --- | --- |
| <!--DelRow-->[egid](arkts-arkts-process-con-sys.md#egid) | 返回进程的有效组 ID（数值形式）。<br/> |
| <!--DelRow-->[euid](arkts-arkts-process-con-sys.md#euid) | 返回进程的有效用户标识（数值形式）。<br/> |
| <!--DelRow-->[gid](arkts-arkts-process-con-sys.md#gid) | 返回进程的组 ID（数值形式）。<br/> |
| <!--DelRow-->[groups](arkts-arkts-process-con-sys.md#groups) | 返回包含补充组 ID 的数组。<br/> |
| [pid](arkts-arkts-process-con.md#pid) | 进程的 ID（PID）。<br/> |
| <!--DelRow-->[ppid](arkts-arkts-process-con-sys.md#ppid) | 返回 ppid 表示当前子进程的 pid。<br/> |
| [tid](arkts-arkts-process-con.md#tid) | 线程的 ID（TID）。<br/> |
| [uid](arkts-arkts-process-con.md#uid) | 进程的用户标识（UID）。<br/> |

