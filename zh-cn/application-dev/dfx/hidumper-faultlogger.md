# Faultlogger
<!--Kit: Performance Analysis Kit-->
<!--Subsystem: HiviewDFX-->
<!--Owner: @chenshi51-->
<!--Designer: @Maplestory91-->
<!--Tester: @gcw_KuLfPSbe-->
<!--Adviser: @jinqiuheng-->

Faultlogger是基于[hidumper](hidumper.md)增强开发的命令行能力，支持查询故障日志文件列表、查看故障日志文件内容、按时间或应用包名筛选故障日志文件等功能。故障日志文件存储在设备的/data/log/faultlog/faultlogger目录下，Faultlogger从该目录中查询和读取故障日志文件。

## 环境准备

根据hidumper工具指导，完成[环境准备](hidumper.md#环境要求)。

## 命令行说明

可通过`hidumper -s 1201 -a "-p Faultlogger [options]"`命令访问Faultlogger模块的故障日志功能，其中-p选项用于指定HiviewService系统能力中的插件模块，1201为HiviewService的系统能力id。hidumper命令的详细用法可参考[获取指定系统服务提供的能力](hidumper.md#获取指定系统服务提供的能力)。

下表为options的选项参数说明。

| 选项 | 说明 |
| -------- | -------- |
| -h | 显示帮助信息。 |
| -l | 列出/data/log/faultlog/faultlogger目录中所有故障日志文件名，fileName格式为秒级时间戳，不含.log后缀。<br>**说明**：从API版本18开始，实际存储的文件名为毫秒级时间戳格式，以.log结尾；API版本18之前，实际存储的文件名为秒级时间戳格式，不含.log后缀。-l参数输出的fileName统一转换为秒级时间戳格式，不含.log后缀；因此从API版本18开始，-l查询的fileName不是设备上的真实文件名。 |
| -LogSuffixWithMs | 列出/data/log/faultlog/faultlogger目录中所有故障日志文件名，fileName后缀包含毫秒级时间戳并以.log结尾，为设备上的实际文件名。<br>**说明**：从API版本18开始支持该参数。该参数输出的fileName统一转换为毫秒级时间戳格式。 |
| -f fileName [--ext] | 查看指定故障日志文件的内容。<br>fileName可通过-l或-LogSuffixWithMs参数获取。<br>--ext为可选参数，仅适用于AppFreeze类型的故障日志文件；指定该参数时，将在原文件内容后拼接对应的增强日志文件内容一并输出。 |
| -t time | 查询/data/log/faultlog/faultlogger目录中指定时间之后生成的故障日志文件名。支持两种时间格式：Unix时间戳或年月日时分秒格式（如20250820211600）。 |
| -m moduleName | 查询/data/log/faultlog/faultlogger目录中与指定应用包名相关的故障日志文件名。 |
| -d | 展示所有故障日志文件的内容，各文件内容以`******`作为分隔标识，分隔标识后首行为文件名。 |

## 获取帮助信息

如果需要查看帮助信息，可以通过下列命令实现。

```shell
hidumper -s 1201 -a '-p Faultlogger -h'
```

输出如下：

```text
-------------------------------[ability]-------------------------------

----------------------------------HiviewService----------------------------------
Usage:
    hidumper -s 1201 -a "-p Faultlogger [options] [parameters]"
Examples:
    hidumper -s 1201 -a "-p Faultlogger -l"                  #Query fault files
    hidumper -s 1201 -a "-p Faultlogger -t 20250821100000"   #Query fault files after 2025-08-21 10:00:00
Available Options:
    -h                  Display this help information
    -l                  List all fault file names in the faultlogger directory
    -f fileName [--ext] View the content of a specified fault file,
                        the --ext parameter only can be used for appfreeze log file.
                        File names can be obtained using the -l parameter
    -t time             Query fault file names generated after the specified time in the faultlogger directory.
                        Supports two time formats:
                            Unix timestamp or year-month-day-hour-minute-second (e.g., 20250820211600)
    -m moduleName       Query fault file names related to the specified moduleName in the faultlogger directory
    -d                  Display detailed content of the file
    -LogSuffixWithMs    List all fault file names in the faultlogger directory
                        with millisecond timestamps in their suffixes
Additional Notes:
    The -s 1201 parameter specifies the hiview service ID for the operation
    Combine options for more precise queries (e.g., -t with -m to filter by both time and module)
    File names retrieved with -l or -LogSuffixWithMs
    can be used as parameters for the -f option to view specific file contents
    The -d option provides extended information including timestamps,
    severity levels, and contextual data when available
```

## 查询故障日志文件列表

### 查询所有故障日志文件名

可使用下列命令列出/data/log/faultlog/faultlogger目录中所有故障日志文件名。

```shell
hidumper -s 1201 -a '-p Faultlogger -l'
```

输出如下：

```text
-------------------------------[ability]-------------------------------

----------------------------------HiviewService----------------------------------
Fault log list:
******
cppcrash-com.ohos.sceneboard-20020022-20241106104006
appfreeze-com.ohos.settings-20020045-20241106103512
jscrash-com.ohos.camera-20020033-20241106103008
******
```

### 查询包含毫秒时间戳的故障日志文件名

可使用下列命令列出/data/log/faultlog/faultlogger目录中所有故障日志文件名，文件名后缀包含毫秒级时间戳并以.log结尾。

```shell
hidumper -s 1201 -a '-p Faultlogger -LogSuffixWithMs'
```

输出如下：

```text
-------------------------------[ability]-------------------------------

----------------------------------HiviewService----------------------------------
Fault log list:
******
cppcrash-com.ohos.sceneboard-20020022-20241106104006123.log
appfreeze-com.ohos.settings-20020045-20241106103512156.log
jscrash-com.ohos.camera-20020033-20241106103008456.log
******
```

由于使用秒级时间戳作为文件名可能出现同名文件，故在文件名中扩展3位数字表示毫秒时间，并在末尾添加.log后缀以区分两种文件命名格式。两种格式对应的故障日志文件内容一致。

在支持-LogSuffixWithMs的系统版本上，使用-l参数查询的文件名不含.log后缀，但实际文件以.log后缀存储在设备端。此时使用hdc按-l查询的文件名导出日志会失败，需使用-LogSuffixWithMs查询的文件名（含.log后缀）进行导出。导出命令参考：

```shell
hdc file recv /data/log/faultlog/faultlogger/{filename} {path}
```

例如：

```shell
hdc file recv /data/log/faultlog/faultlogger/cppcrash-com.ohos.sceneboard-20020022-20241106104006123.log ./
```

### 查询指定时间之后的故障日志文件名

可使用下列命令查询/data/log/faultlog/faultlogger目录中指定时间之后生成的故障日志文件名。time参数支持两种格式：Unix时间戳或年月日时分秒格式。

例如查询2025年8月21日10:00:00（北京时间，对应Unix时间戳1755741600）之后生成的故障日志文件名。

按照年月日时分秒格式查询：

```shell
hidumper -s 1201 -a '-p Faultlogger -t 20250821100000'
```

按照Unix时间戳格式查询：

```shell
hidumper -s 1201 -a '-p Faultlogger -t 1755741600'
```

输出如下：

```text
-------------------------------[ability]-------------------------------

----------------------------------HiviewService----------------------------------
Fault log list:
******
cppcrash-com.ohos.sceneboard-20020022-20250821154006
appfreeze-com.ohos.settings-20020045-20250821123012
******
```

### 查询指定应用包名的故障日志文件名

可使用下列命令查询/data/log/faultlog/faultlogger目录中与指定应用包名相关的故障日志文件名。

```shell
hidumper -s 1201 -a '-p Faultlogger -m com.ohos.sceneboard'
```

输出如下：

```text
-------------------------------[ability]-------------------------------

----------------------------------HiviewService----------------------------------
Fault log list:
******
cppcrash-com.ohos.sceneboard-20020022-20241106104006
syswarning-com.ohos.sceneboard-20020022-20241106104006
******
```

也可组合使用多个选项进行精确查询，例如同时按时间和应用包名筛选：

```shell
hidumper -s 1201 -a '-p Faultlogger -t 20250821100000 -m com.ohos.sceneboard'
```

## 查看故障日志文件内容

### 查看指定故障日志文件内容

可使用下列命令查看指定故障日志文件的内容。文件名可通过-l或-LogSuffixWithMs参数获取。故障日志的规格可参考：[CppCrash](cppcrash-guidelines.md#日志规格)、[JSCrash](jscrash-guidelines.md#日志规格)、[AppFreeze](appfreeze-guidelines.md#日志规格)、[AppFreeze增强日志](appfreeze-guidelines.md#增强日志规格)。

```shell
hidumper -s 1201 -a '-p Faultlogger -f cppcrash-com.ohos.sceneboard-20020022-20241106104006'
```

输出如下：

```text
-------------------------------[ability]-------------------------------

----------------------------------HiviewService----------------------------------
Generated by HiviewDFX@OpenHarmony
================================================================
BuildId: xxx
Pid: 20020022
Uid: 0
Package name: com.ohos.sceneboard
Process name: com.ohos.sceneboard
...
```

对于AppFreeze类型的故障日志文件，可指定--ext参数，此时会在原文件内容后拼接对应的增强日志文件内容一并输出：

```shell
hidumper -s 1201 -a '-p Faultlogger -f appfreeze-com.ohos.settings-20020045-20241106103512 --ext'
```

输出如下：

```text
-------------------------------[ability]-------------------------------

----------------------------------HiviewService----------------------------------
******
Generated by HiviewDFX@OpenHarmony
================================================================
BuildId: xxx
Pid: 20020045
Uid: 0
Package name: com.ohos.settings
Process name: com.ohos.settings
...
******
Generated by HiviewDFX@OpenHarmony
================================================================
TimeStamp: 2024-11-06 10:35:12.000
Module name: xxx
...
******
```

> **说明：**
>
> - `--ext`参数仅适用于AppFreeze类型的故障日志文件。
> - 增强日志文件包含应用冻结故障的扩展诊断信息。
> - 故障日志和增强日志均以`******`作为起止标识进行包裹。

### 查看所有故障日志文件内容

可使用下列命令展示所有故障日志文件的内容，各文件内容以`******`作为分隔标识，分隔标识后首行为文件名。

```shell
hidumper -s 1201 -a '-p Faultlogger -d'
```

输出如下：

```text
-------------------------------[ability]-------------------------------

----------------------------------HiviewService----------------------------------
Fault log list:
******
cppcrash-com.ohos.sceneboard-20020022-20241106104006
Generated by HiviewDFX@OpenHarmony
================================================================
BuildId: xxx
Pid: 20020022
Uid: 0
Package name: com.ohos.sceneboard
Process name: com.ohos.sceneboard
...
******
appfreeze-com.ohos.settings-20020045-20241106103512
Generated by HiviewDFX@OpenHarmony
================================================================
BuildId: xxx
Pid: 20020045
Uid: 0
Package name: com.ohos.settings
Process name: com.ohos.settings
...
```
