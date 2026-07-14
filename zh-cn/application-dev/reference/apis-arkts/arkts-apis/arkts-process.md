# @ohos.process

**process** 模块提供进程管理相关接口，例如获取进程信息的接口。

**起始版本：** 7

**系统能力：** SystemCapability.Utils.Lang

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [abort](arkts-arkts-abort-f.md#abort-1) | 中止进程并生成核心文件。该方法会导致进程立即退出，请谨慎使用。 |
| [exit](arkts-arkts-exit-f.md#exit-1) | 终止程序。请谨慎使用此接口。调用此接口后应用将退出。如果输入参数非 0，可能会导致数据丢失或出现异常。 |
| [getEnvironmentVar](arkts-arkts-getenvironmentvar-f.md#getenvironmentvar-1) | 获取环境变量名对应的值。 |
| [getPastCpuTime](arkts-arkts-getpastcputime-f.md#getpastcputime-1) | 获取进程启动到当前时间的 CPU 时间（以毫秒为单位）。 |
| [getStartRealtime](arkts-arkts-getstartrealtime-f.md#getstartrealtime-1) | 获取系统启动到进程启动的实时时间（以毫秒为单位，不包含系统休眠时间）。 |
| [getSystemConfig](arkts-arkts-getsystemconfig-f.md#getsystemconfig-1) | 获取系统配置信息。 |
| [getThreadPriority](arkts-arkts-getthreadpriority-f.md#getthreadpriority-1) | 根据指定的 tid 获取线程优先级，优先级顺序取决于当前操作系统。 |
| [getUidForName](arkts-arkts-getuidforname-f.md#getuidforname-1) | 根据指定的用户名，从系统的用户数据库中获取该用户的 uid。 |
| [is64Bit](arkts-arkts-is64bit-f.md#is64bit-1) | 检查运行环境是否为 64 位。 |
| [isAppUid](arkts-arkts-isappuid-f.md#isappuid-1) | 判断 uid 是否属于应用程序。 |
| [isIsolatedProcess](arkts-arkts-isisolatedprocess-f.md#isisolatedprocess-1) | 检查进程是否已被隔离。 |
| [kill](arkts-arkts-kill-f.md#kill-1) | 发送信号到指定进程，结束该进程。 |
| [uptime](arkts-arkts-uptime-f.md#uptime-1) | 获取当前系统已运行的时间（以秒为单位）。 |

<!--Del-->
### 函数（系统接口）

| 名称 | 说明 |
| --- | --- |
| [chdir](arkts-arkts-chdir-f-sys.md#chdir-1) | 修改当前目录。 |
| [cwd](arkts-arkts-cwd-f-sys.md#cwd-1) | 返回当前工作目录。 |
| [off](arkts-arkts-off-f-sys.md#off-1) | 移除已注册的事件。 |
| [on](arkts-arkts-on-f-sys.md#on-1) | 注册事件。 |
| [runCmd](arkts-arkts-runcmd-f-sys.md#runcmd-1) | 返回一个子进程对象，并 spawn 一个新的 ChildProcess 来运行命令。 |
<!--DelEnd-->

### 类

| 名称 | 说明 |
| --- | --- |
| [ProcessManager](arkts-arkts-processmanager-c.md) | 提供进程管理相关接口，包括进程 UID 判断、用户信息查询、线程优先级获取、环境变量获取、进程退出和信号发送等功能。通过 `new process.ProcessManager()` 构造 ProcessManager 对象。 |

<!--Del-->
### 接口（系统接口）

| 名称 | 说明 |
| --- | --- |
| [ChildProcess](arkts-arkts-childprocess-i-sys.md) | childprocess 对象可用于创建新的进程。 |
| [ConditionType](arkts-arkts-conditiontype-i-sys.md) | 提供 ConditionType 类型，包括 timeout、killSignal、maxBuffer。 |
<!--DelEnd-->

### 类型

| 名称 | 说明 |
| --- | --- |
| [EventListener](arkts-arkts-eventlistener-t.md) | 用户存储的事件信息。 |

### 常量

| 名称 | 说明 |
| --- | --- |
| [pid](arkts-arkts-process-con.md#pid) | 进程的 ID（PID）。 |
| [tid](arkts-arkts-process-con.md#tid) | 线程的 ID（TID）。 |
| [uid](arkts-arkts-process-con.md#uid) | 进程的用户标识（UID）。 |

<!--Del-->
### 常量（系统接口）

| 名称 | 说明 |
| --- | --- |
| [egid](arkts-arkts-process-con-sys.md#egid) | 返回进程的有效组 ID（数值形式）。 |
| [euid](arkts-arkts-process-con-sys.md#euid) | 返回进程的有效用户标识（数值形式）。 |
| [gid](arkts-arkts-process-con-sys.md#gid) | 返回进程的组 ID（数值形式）。 |
| [groups](arkts-arkts-process-con-sys.md#groups) | 返回包含补充组 ID 的数组。 |
| [ppid](arkts-arkts-process-con-sys.md#ppid) | 返回 ppid 表示当前子进程的 pid。 |
<!--DelEnd-->

