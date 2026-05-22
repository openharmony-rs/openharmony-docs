# ArkWeb术语解释

## B

### Breakpad

崩溃信息处理项目，用于编译minidump_stackwalk工具的项目源码。

### 崩溃信息

Crash Information，记录进程崩溃原因、线程信息、寄存器信息等的数据。

### 崩溃原因

Crash Reason，导致进程异常终止的具体原因。

### 崩溃栈信息

Crash Stack Information，崩溃时的函数调用堆栈信息。

### 崩溃转储文件

Crash Dump File，记录进程崩溃时状态信息的二进制文件。

## C

### Crash address

崩溃地址，导致进程崩溃的内存地址。

### Crash reason

崩溃原因，导致进程crash的信号类型。

### Crashpad

Chromium内核提供的进程崩溃信息处理工具，用于记录进程崩溃信息。

## D

### dmp文件

崩溃转储文件，记录进程崩溃信息的二进制格式文件，后缀为dmp。

### 段错误

Segmentation Fault，内存访问权限错误导致的崩溃类型。

### 调用栈

Call Stack，函数调用的堆栈序列信息。

## F

### filesDir

文件目录，应用沙箱中的文件存储目录。

### 反编译

Decompilation，将机器码转换为可读源码的过程。

### 符号表

Symbol Table，用于调试和解析源码位置的符号信息表。

## H

### Hilog日志

系统日志，记录系统运行信息的日志输出。

## J

### 寄存器信息

Register Information，CPU寄存器在崩溃时的状态数据。

### 进程崩溃

Process Crash，进程因异常而终止运行的现象。

## L

### libweb_engine.so

Web引擎动态库，包含Web组件核心功能的共享对象文件。

### LLVM

编译器工具链，用于解析崩溃源码位置的工具集。

### llvm-addr2line

地址转行号工具，用于解析崩溃源码位置的LLVM工具链工具。

## M

### minidump_stackwalk

小型转储栈遍历工具，用于解析dmp文件获取崩溃信息的工具。

## N

### Native访问

原生代码（Native Code）对应用沙箱数据的访问能力，通过Crashpad相关接口实现。

## P

### Process uptime

进程运行时间，进程从启动到崩溃的时间长度。

### 偏移地址

Offset Address，相对于基地址的内存地址偏移量。

## S

### SandboxedHandler

沙箱处理程序，Crashpad中处理崩溃的沙箱化处理器。

### SandBox；沙箱

应用运行的隔离环境，限制应用对系统资源和个人数据的访问权限，保障系统安全。

### SEGV_MAPERR

段错误映射错误，表示内存映射错误的段错误类型。

### SIGSEGV

段错误信号，表示内存访问错误的信号类型。

### 沙箱目录

Sandbox Directory，应用沙箱中用于存储文件的目录路径。

## T

### Thread

线程，进程中的执行单元。

## X

### 线程信息

Thread Information，线程状态、调用栈等相关信息。
