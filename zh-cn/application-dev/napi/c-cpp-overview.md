# C/C++标准库机制概述

OpenHarmony NDK提供业界标准库[libc标准库](../reference/native-lib/musl.md)、[标准C++库](../reference/native-lib/cpp.md)，本文用于介绍C/C++标准库在OpenHarmony中的机制，开发者了解这些机制有助于在NDK开发过程中避免相关问题。

## 1. C++兼容性

在OpenHarmony系统中，系统库和应用Native库均使用C++标准库（参考[libc++版本](../reference/native-lib/cpp.md#libc版本)）。系统库依赖的C++标准库随镜像版本升级，应用Native库依赖的C++标准库随编译使用的SDK版本升级。由于两部分依赖的C++标准库会跨多个大版本，可能导致ABI兼容性问题。为解决此问题，OpenHarmony对系统库和应用Native库依赖的C++标准库进行了区分。

- 系统库：使用libc++.so，随系统镜像发布。
- 应用Native库：使用libc++_shared.so，随应用发布。

两个库使用不同的C++命名空间。libc++.so使用__h，libc++_shared.so使用__n1。

> **注意：**
>
> 系统和应用的C++标准库不能混用。Native API接口只能是C接口，用于隔离C++运行环境。如果HAR包中的libc++_shared.so版本不同于应用，可能导致不兼容问题。解决方法是使用相同SDK版本更新HAR包。

**已知C++兼容性问题：**

应用启动或dlopen时，hilog报错`symbol not found, s=__emutls_get_address`。原因是API9及之前版本的libc++_shared.so无此符号，而API11之后版本的libc++_shared.so有此符号。解决方法是更新应用或HAR包的SDK版本。

## 2. musl libc动态链接器

### 动态库加载命名空间隔离
动态库加载命名空间（namespace，下面统称为ns）是动态链接器设计的一个概念（区别于C++语言中的命名空间），其设计的主要目的是为了在进程中做native库资源访问的管控，以达到安全隔离的目的。例如系统native库允许加载系统目录（/system/lib64;/vendor/lib64等）下的native库，但是普通应用native库仅允许加载普通应用native库和ndk库，而不允许直接加载系统native库。

动态链接器在加载编译依赖（DT_NEEDED）中指定的共享库或调用`dlopen`加载指定的共享库时，都需要关联到具体的 ns。

OpenHarmony中动态库加载namespace配置的情况

- default ns：动态链接器启动时默认创建的ns，它可以搜索`/system/lib{abi};/vendor/lib{abi}`等系统目录路径下的so。

- ndk ns：动态链接器启动时默认创建的ns，它可以搜索`/system/lib{abi}/ndk`目录下的so，主要是暴露了NDK接口的so。

- app ns: 应用启动时创建的ns，它的搜索路径一般是应用的安装路径(可能为沙箱路径)，即可加载应用的so。

当前的命名空间机制主要限制了应用native库和系统native库之间的调用，规则如图所示：

1. default ns和ndk ns可以互相访问全部so，不能访问app ns的so。
2. app ns能访问ndk ns的全部so，不能访问default ns的so。

![zh-cn_image_musl_ld_namespace](figures/dl_namespace.png)

### rpath机制
rpath（run-time path）是在运行时指定共享库搜索路径的机制。该机制允许在可执行文件或共享库中嵌入一个用于在运行时指定库的搜索路径的信息。

由于命名空间隔离机制，应用仅允许加载对应安装目录拼接native库路径下（例如arm64平台上为`libs/arm64`）的应用native库，当应用程序涉及加载多个native库时，创建多个加载路径会导致无法加载新目录下的native库。这种情况可以通过rpath机制编译时指定搜索路径。

例如，应用安装目录`lib/arm64`下的`libhello.so`依赖新创建路径`lib/arm64/module`下的`libworld.so`，那么在应用的`CMakeList.txt`里设置上`rpath`编译选项后编译，使用`readelf`查看`libhello.so`的`rpath`配置如图所示，`$ORIGIN`为`libhello.so`所在路径，运行时即可正常加载module目录下的`libworld.so`。
```
SET(CMAKE_BUILD_WITH_INSTALL_RPATH TRUE)
SET(CMAKE_INSTALL_RPATH "\${ORIGIN}/module")
```
![zh-cn_image_musl_ld_rpath](figures/dl_rpath.png)

### 支持dlclose
支持使用dlclose真实卸载动态库的能力。

### 支持symbol-version机制
symbol-version是libc在**动态链接-符号重定位**阶段的符号检索机制，支持不同版本的符号重定位，也可以帮助解决重复符号的问题。可参考<a href="https://www.gnu.org/software/gnulib/manual/html_node/LD-Version-Scripts.html">LD Version Scripts (GNU Gnulib)</a>。

### 网络接口select支持fd fortify检测
宏定义FD_SET和FD_CLR增加了对fd有效值的检查。如果传入的fd不在区间`[0, 1024)`中，将触发abort crash。

宏定义FD_ISSET增加了对fd有效值的检查，如果传入的fd不在区间`[0, 1024)`中会返回false。

### 全球化支持
自API12起，newlocale及setlocale接口支持将locale设置C、C.UTF-8、en_US、en_US.UTF-8、zh_CN及zh_CN.UTF-8。新增在zh_CN及zh_CN.UTF-8的locale设置下对strtod_l、wcstod_l和localeconv的支持。注意strtod_l及wcstod_l不支持对十六进制及十六进制小数的转换。

### fdsan功能
[fdsan使用指导](./fdsan.md)可以帮助检测文件的重复关闭和关闭后使用问题。

## 3. 信号使用
为避免与系统保留信号冲突，开发者在使用信号时需遵循以下规则：
- 信号编号 1～34：为系统内部保留信号，禁止使用；
- 信号编号 35～45: 截止到目前 API 19，这些信号已被系统内部模块（如内存、DFX、运行时、系统服务等）占用，为避免与系统行为冲突并导致不可预期的问题，请勿使用该范围内的信号。
- SIGRTMIN和__libc_current_sigrtmin的值是35, 表示可供应用程序使用的实时信号起始编号(应用实际只能使用46及以上的信号)。

鸿蒙内部信号使用统计如下：

| 编号 | 名称      | 备注             | 编号 | 名称                                        | 备注                      |
|------|-----------|-----------------|------|--------------------------------------------|---------------------------|
| 1    | SIGHUP    |  控制终端挂起    | 24   | SIGXCPU                                    | 超出 CPU 时间限制          | 
| 2    | SIGINT    |  中断           | 25   | SIGXFSZ                                    | 文件超出大小限制            |
| 3    | SIGQUIT   |  键盘退出        | 26   | SIGVTALRM                                  | 虚拟定时器                 |
| 4    | SIGILL    |  非法指令        | 27   | SIGPROF                                    | profiling 计时器到期       |
| 5    | SIGTRAP   |  调试断点        | 28   | SIGWINCH                                   | 终端窗口大小变化           |
| 6    | SIGABRT   |  中止信号        | 29   | SIGIO                                      | I/O 可用通知               |
| 7    | SIGBUS    |  总线错误        | 30   | SIGPWR                                     | 电源故障                   |
| 8    | SIGFPE    |  算术异常        | 31   | SIGSYS                                     | 非法系统调用               |
| 9    | SIGKILL   |  强制终止        | 32   | SIGTIMER                                   | 定时器定时信号             |
| 10   | SIGUSR1   |  用户自定义信号 1 | 33   | SIGCANCEL                                  | 线程取消信号               |
| 11   | SIGSEGV   |  无效内存访问     | 34   | SIGSYNCCALL                                | 同步调用信号               |
| 12   | SIGUSR2   |  用户自定义信号 2 | 35   | MUSL_SIGNAL_NATIVE_REMOTE (SIGRTMIN + 0)   | 系统自留                   |
| 13   | SIGPIPE   |  管道损坏         | 36   | MUSL_SIGNAL_HOOK (SIGRTMIN + 1)            | 系统自留                  |
| 14   | SIGALRM   |  定时器信号       | 37   | MUSL_SIGNAL_UNHOOK (SIGRTMIN + 2)          | 系统自留                  |
| 15   | SIGTERM   |  程序终止请求     | 38   | MUSL_SIGNAL_NATIVE_LOCAL (SIGRTMIN + 3)    | 系统自留                  |
| 16   | SIGSTKFLT |  协处理器栈错误    | 39  | MUSL_SIGNAL_JSHEAP (SIGRTMIN + 4)          | 系统自留                  |
| 17   | SIGCHLD   |  子进程退出/停止   | 40  | MUSL_SIGNAL_JSHEAP_PRIV (SIGRTMIN + 5)     | 系统自留                  |
| 18   | SIGCONT   |  继续执行         | 41   | MUSL_SIGNAL_SAMPLE_STACK (SIGRTMIN + 6)    | 系统自留                  |
| 19   | SIGSTOP   |  强制停止         | 42   | MUSL_SIGNAL_LEAK_STACK (SIGRTMIN + 7)      | 系统自留                  |
| 20   | SIGTSTP   |  停止在终端输入   | 43   | MUSL_SIGNAL_RECYCLE_JEMALLOC (SIGRTMIN + 8) | 系统自留                  |
| 21   | SIGTTIN   |  后台读终端       | 44   | MUSL_SIGNAL_MEMCHECK (SIGRTMIN + 9)         | 系统自留                  |
| 22   | SIGTTOU   |  后台写终端       | 45   | MUSL_SIGNAL_FDTRACK (SIGRTMIN + 10)         | 系统自留                  |
| 23   | SIGURG    |  套接字有紧急数据  |   -  |                          -                  |                 -        |
