# Performance Analysis Kit术语

<!--Kit: Performance Analysis Kit-->
<!--Subsystem: HiviewDFX-->
<!--Owner: @mzyan-->
<!--Designer: @liyueric-->
<!--Tester: @gcw_KuLfPSbe-->
<!--Adviser: @foryourself-->

## 通用

### log版本

Log版本是指在系统中开启了日志记录功能的系统版本。这种版本会记录系统运行时的各种信息，包括应用程序的运行情况、系统错误信息、调试信息等等。这些信息可以通过hdc工具或者第三方应用程序查看和分析，有助于开发者进行调试和优化。

在设备中， 点击 “设置”-&gt;搜索关键字“关于本机”-&gt;“软件版本”进行查看，log版本会以“log”结尾。如：BRA-AL00 5.0.0.36(C00E15R4P92log)是log版本。

### nolog版本

Nolog版本是指在系统中关闭了日志记录功能的系统版本。这种版本不会记录系统运行时的信息，因此相对来说更加轻量级，运行速度也更快。但是，由于没有日志记录，开发者在调试和优化时会比较困难。

在设备中， 点击 “设置”-&gt;搜索关键字“关于本机”-&gt;“软件版本”进行查看，nolog版本版本号末尾不带有“log”关键字。如：BRA-AL00 5.0.0.36(C00E15R4P92)是nolog版本。

### debug版本应用

使用[debug模式](https://developer.huawei.com/consumer/cn/doc/harmonyos-guides/ide-hvigor-compilation-options-customizing-guide#section192461528194916)构建的应用。

### release版本应用

使用[release模式](https://developer.huawei.com/consumer/cn/doc/harmonyos-guides/ide-hvigor-compilation-options-customizing-guide#section192461528194916)构建的应用。

## 稳定性

### AppFreeze

用户在使用应用时，如果出现点击无反应或应用无响应等情况，并且持续时间超过一定限制，就会被定义为应用冻屏（AppFreeze），即应用无响应或卡死。

### Asan

Asan（Address Sanitizer）为内存地址消毒器，用于检测非法地址访问。

### CPP Crash

进程C++代码未处理posix崩溃异常信号时导致的异常退出，其中异常信号包含如下：

| 信号值(signo) | 信号 | 解释 | 触发原因 |
| -------- | -------- | -------- | -------- |
| 4 | SIGILL | 非法指令。 | 进程执行了非法、格式错误、未知或特权指令。 |
| 5 | SIGTRAP | 断点或陷阱异常。 | 异常或trap指令发生。 |
| 6 | SIGABRT | 进程终止。 | 进程异常终止，通常为进程自身调用标准函数库的abort()函数。 |
| 7 | SIGBUS | 非法内存访问。 | 进程访问了对齐或者不存在的物理地址。 |
| 8 | SIGFPE | 浮点异常。 | 进程执行了错误的算术运算，如除数为0、浮点溢出、整数溢出等。 |
| 11 | SIGSEGV | 无效内存访问。 | 进程访问了无效内存引用。 |
| 16 | SIGSTKFLT | 栈错误。 | 处理器执行了错误的栈操作，如栈空时弹出、栈满时压入。 |
| 31 | SIGSYS | 错误的系统调用。 | 系统调用时使用了错误或非法参数。 |

### GWP-Asan

GWP-Asan是一种原生内存分配器功能，支持检测内存释放后使用和堆缓冲区溢出问题。

### HWAsan

HWAsan（Hardware-Assisted Address Sanitizer）是Clang LLVM提供的一套内存错误检测系统，用来检测C/C++中常见的内存访问错误，相比Asan（Address Sanitizer），它在性能和内存开销上有不小提升。

### JS Crash

应用JS/ArkTS代码执行过程中发生的未捕获异常或错误，应用会因为无法继续正常运行而直接崩溃。

### TSan

TSan（Thread Sanitizer）是一个检测数据竞争的工具。

### UBSan

UBSan（Undefined Behavior Sanitizer）可以检测代码中出现的未定义行为，帮助用户清除未定义行为引起运行时的错误。

## 性能

### 丢帧

丢帧指在视频播放、游戏渲染或图像采集过程中，因系统性能不足、硬件限制或软件问题导致帧率低于预期，造成画面卡顿或数据丢失的现象。技术角度上讲丢帧是指单帧绘制时长超过1000ms/刷新率，导致设备不能按照刷新率绘帧的现象。丢帧与单帧绘制时长的关系主要体现在：单帧绘制时长超过显示设备的刷新周期（如16.7ms/帧）会导致丢帧。

## 功耗

### HWC

HWC（Hardware Composer）指专用硬件辅助系统，主要用于多图层叠加送显。

### 前台任务

前台任务指用户当前正在主动使用、界面可见并优先占用系统资源的应用或服务。

### 后台任务

后台任务指用户不直接操作界面的情况下，应用在后台执行的操作或服务，如下载、同步或播放音乐等。

### 帧率

帧率为每秒显示或处理的图像帧数。

### LTPO

LTPO（Low Temperature Polycrystalline Oxide）中文译为“低温多晶氧化物”。这是OLED屏背板的一种驱动技术。LTPO屏支持1~120Hz的自适应刷新率，使应用在需要高刷新率的场景下提升流畅性，而在视频、静止等场景中使用低刷新率降低显示功耗，延长电池续航。通常用“LTPO”指代自适应刷新率技术。

### 冗余绘制

冗余绘制是指界面中存在被其他图层遮挡或多次重复渲染的图层，导致系统在同一像素上进行多次无效绘制，浪费GPU资源并可能引起卡顿。

### 不可见动效

不可见动效指在界面中不直接呈现给用户，但用于增强交互反馈或状态过渡的动画效果，如页面切换时的滑动。

## 内存

### VSS

VSS（Virtual Set Size）指的是进程虚拟内存的大小，包括所有映射到该进程地址空间的内存区域，无论这些区域是否实际存在于物理内存中。

### PSS

PSS（Proportional Set Size）是一种更精确的内存使用度量方法，它将共享库所占的内存按比例分配给每个使用该库的进程。

### RSS

RSS（Resident Set Size）表示当前进程中实际驻留在物理内存中的大小。

### 脏页

脏页（Dirty Pages）指的是已经被修改过但还没有写回到磁盘上的缓存页面。

### 干净页

干净页（Clean Pages）指的是未被修改过的或者已经从磁盘正确同步过来的页面。

### 匿名页

匿名页（Anonymous Pages）指的是不对应任何具体文件的内存页，通常是堆栈或堆分配的结果。

### 文件页

文件页（File-backed Pages）指的是映射自具体文件的数据页，比如程序文本、共享库等。

### NMD

NMD（Native Malloc Detail）指的是进程的jemalloc快照详细信息。
