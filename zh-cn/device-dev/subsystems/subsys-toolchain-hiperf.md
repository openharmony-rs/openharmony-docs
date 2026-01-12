# hiperf使用指导


hiperf是为开发人员提供性能采样分析的工具，基于内核perf机制进行的用户态能力的扩展，可以对指定的程序或者整个系统进行性能采样。


hiperf支持的命令有：list、stat、record、report等，可以通过hiperf -h进行查看。


下面对hiperf的常用命令进行详细说明：


## list 命令


### 参数说明

列出设备上支持的所有perf事件名称，事件名称用于 stat 和 record命令的 -e 和 -g 参数。

  
```
Usage: hiperf list [event type]
```

  | 参数 | 功能说明 | 
| -------- | -------- |
| hw | 列出支持的&nbsp;hardware&nbsp;事件（PMU支持） | 
| sw | 列出支持的&nbsp;software&nbsp;事件 | 
| tp | 列出支持&nbsp;tracepoint&nbsp;事件 | 
| cache | 列出支持的&nbsp;cache&nbsp;事件（PMU支持） | 
| raw | 列出支持的原始PMU事件 | 


### 使用示例

下面列出了设备支持的hardware事件，并且会提示哪些事件此设备不支持。

  
```
hiperf list hw
event not support hw-stalled-cycles-backend
event not support hw-stalled-cycles-frontend
event not support hw-ref-cpu-cycles

Supported events for hardware:
        hw-cpu-cycles
        hw-instructions
        hw-cache-references
        hw-cache-misses
        hw-branch-instructions
        hw-branch-misses
        hw-bus-cycles
```


## stat 命令


### 参数说明

监听指定目标程序，周期性打印性能计数器的值。
  
```
Usage: hiperf stat [options]
       Collect performance counter information.
```


  | 参数 | 功能说明 | 
| -------- | -------- |
| -a | 采集监听整个系统的所有线程和默认的性能计数器的值。 | 
| -c | 指定cpu&nbsp;id，可以是0,1,2用逗号分隔。 | 
| -d&nbsp;&lt;_sec_&gt; | 指定监听的时间，单位为秒。 | 
| -i&nbsp;&lt;_ms_&gt; | 指定监听事件的间隔打印时间，单位毫秒。 | 
| -e | 指定监听的事件，可以通过list命令查看支持的所有事件，其中event:u&nbsp;或者&nbsp;:k&nbsp;表示限制事件为用户空间或者内核空间。 | 
| -g | 指定需要在同一组监听的事件，同一组事件会被放入同一个PMU监听。 | 
| --no-inherit | 不监听目标线程/进程启动的子线程。 | 
| -p | 指定需要监听的进程pid。 | 
| -t | 指定需要监听的线程tid。 | 
| --verbose | 显示详细的报告内容，包括一些原始的时间数据等等。 | 


### 使用示例

下面是通过 stat 监听整个系统3秒的示例：

  
```
hiperf stat -d 3 -a
this is root mode, perfEventParanoid assume as -1
Start Profiling...
Timeout exit (total 3009 ms)
                count                           name | comment                          | coverage
               132523         hw-branch-instructions | 15.750 M/sec                     | (100%)
                62554               hw-branch-misses | 47.202372% miss rate             | (100%)
              6994768                  hw-cpu-cycles | 0.832068 GHz                     | (100%)
              1237627                hw-instructions | 5.651758 cycles per instruction  | (100%)
                  248            sw-context-switches | 29.959 K/sec                     | (100%)
                    0                 sw-page-faults | 0.000 /sec                       | (100%)
              9402580                  sw-task-clock | 0.002758 cpus used               | (100%)
```


### 字段说明

  | 字段名 | 含义 | 
| -------- | -------- |
| count | 表示事件发生的次数。 | 
| name | 事件的名称，在&nbsp;list&nbsp;命令中可以看到所有支持的命令，hw&nbsp;和&nbsp;sw&nbsp;的前缀分别代表是hardware事件还是software事件。 | 
| comment | 一些经过计算的方便用户阅读的值。例如&nbsp;CPU&nbsp;的相对主频，千位进制换算等等。 | 
| coverage | 该事件在PMU中的&nbsp;enable&nbsp;百分比，受限于PMU数量，每次装载的PMU监听事件是有限的。 | 


## record 命令


### 参数说明

采样指定目标程序，并且将采样数据保存到指定的文件中（默认为perf.data）

  
```
Usage: hiperf record [options]
       Collect performance sampling information.
```

  | 参数 | 功能说明 | 
| -------- | -------- |
| -a | 对整个系统的所有进程和线程进行采样。 | 
| --exclude-hiperf | 不采样hiperf自身进程。 | 
| -c | 指定采样的cpu&nbsp;id。 | 
| --cpu-limit&nbsp;&lt;_percent_&gt; | 限定采样过程占用的CPU最大百分比。 | 
| -d&nbsp;&lt;sec&gt; | 指定采样时长，单位秒。 | 
| -f&nbsp;&lt;freq&gt; | 设置采样事件的触发频率，默认为4000。<br/>说明：该频率越高cpu负载会越高，但是数据采样会越多。 | 
| --period&nbsp;&lt;_num_&gt; | 设置采样事件触发周期，以次数为单位，即发生指定的次数后采样一次。 | 
| -e | 指定监听的事件，可以通过list命令查看支持的所有事件，其中event:u&nbsp;或者&nbsp;:k&nbsp;可以表示限制事件为用户空间或者内核空间。 | 
| -g | 指定需要在同一组监听的事件，同一组事件会被放入同一个PMU监听。 | 
| --no-inherit | 不监听目标线程或者进程启动的子线程。 | 
| -p | 指定需要监听的进程。 | 
| -t | 指定需要监听的线程。 | 
| --offcpu | 监听CPU调度事件，它等价于&nbsp;--period&nbsp;1&nbsp;-e&nbsp;sched:sched_switch&nbsp;事件。 | 
| -j&nbsp;&lt;_branch_filter1_&gt;[,_branch_filter2_]... | 监听分支预测事件。分支预测就是指令存在多个if&nbsp;else判定的情况下，CPU去预测下一步即将执行哪一条指令。 | 
| -s&nbsp;/&nbsp;--call-stack&nbsp;&lt;_fp&nbsp;\\|&nbsp;dwarf[,size]_&gt; | 设置用户栈的回栈方式，支持fp和dwarf两种方式。dwarf&nbsp;后面可以指定采样的用户堆栈大小，默认是&nbsp;65528。 | 
| --delay-unwind | 延迟回栈，等到采样结束再进行回栈。 | 
| --disable-unwind | 不进行回栈，用户的寄存器和堆栈数据会保存在perf.data中，供离线回栈使用。 | 
| --disable-callstack-expend | 默认会对回栈的调用栈信息进行合并扩展，此选项会关闭该功能。 | 
| --clockid&nbsp;&lt;_clock&nbsp;type_&gt; | 设置采样数据的时钟源，支持monotonic、boottime、realtime等。 | 
| --symbol-dir&nbsp;&lt;_dir_&gt; | 指定符号表路径，如果指定了回栈时会优先使用该路径下的符号表。 | 
| -m&nbsp;&lt;_mmap&nbsp;pages_&gt; | 指定缓存的大小，默认值为1024，以页为单位。参数需要为2的幂，范围为&nbsp;[2&nbsp;-&nbsp;1024]。<br/>说明：该值越高，事件丢失率会越低，但是内存占用会增大。 | 
| --app&nbsp;&lt;_package&nbsp;name_&gt; | 指定采样的目标应用的包名，默认超时等待时间为10秒。 | 
| --data-limit&nbsp;&lt;_SIZE[K\|M\|G]_&gt; | 指定采样结果的最大容量，支持K/M/G(B)为单位，默认无大小限制。 | 
| -o&nbsp;&lt;_output&nbsp;file&nbsp;name_&gt; | 指定采样数据结果文件名，默认为/data/local/tmp/perf.data。 | 
| -z | 启动压缩模式，在保存到文件的时候，会用gzip进行压缩。 | 
| --verbose | 采样的时候显示更详细的日志信息。 | 


### 使用示例

- 对整机所有进程采样3秒，并且显示详细的日志信息
    
  ```
  hiperf record -d 3 -a --verbose
  ```

- 指定使用fp方式进行回栈
    
  ```
  hiperf record -s fp -d 3 -a
  ```

- 指定使用dwarf方式进行回栈
    
  ```
  hiperf record -s dwarf -d 3 -a
  ```

- 指定采样offcpu事件
    
  ```
  hiperf record --offcpu -s dwarf -d 3 -a
  ```

- 指定延迟回栈
    
  ```
  hiperf record -d 3 -s dwarf --delay-unwind -a
  ```

- 禁用堆栈展开，此时会保存堆栈数据到perf.data文件
    
  ```
  hiperf record -d 3 -s dwarf --disable-unwind -a
  ```

- 指定追踪的包名，如果指定的包名对应的进程不存在则会延迟等待10秒，超时后进程退出
    
  ```
  hiperf record -d 3 -s dwarf --app com.ohos.launch
  ```

- 指定对采样结果数据进行压缩保存
    
  ```
  hiperf record -z -s dwarf -d 3  -a
  ```


## report 命令


### 参数说明

此命令主要用于展示record中抓取的采样数据

  
```
Usage: hiperf report [option]     
       Report sampling information from perf.data.
```

  | 参数 | 功能说明 | 
| -------- | -------- |
| --symbol-dir&nbsp;&lt;_dir_&gt; | 指定符号表路径。 | 
| --limit-percent&nbsp;&lt;_number_&gt; | 指定展示结果的最低百分比（低于的不显示）。 | 
| -s&nbsp;/&nbsp;--call-stack | 指定该选项后结果数据中会包含详细的调用栈信息。 | 
| --call-stack-limit-percent&nbsp;&lt;_number_&gt; | 调用栈的百分比最小值（低于的不显示）。 | 
| --proto | 将输入的&nbsp;perf.data&nbsp;文件转换为&nbsp;proto&nbsp;格式，默认文件名为&nbsp;perf.proto。 | 
| --json | 将输入的&nbsp;perf.data&nbsp;文件转换为&nbsp;json&nbsp;格式，默认文件名为&nbsp;perf.json。 | 
| --branch | 按分支预测的结果地址来展示报告，而不是调用栈的IP地址。 | 
| --&lt;_keys_&gt;&nbsp;&lt;_keyname1_&gt;[,_keyname2_][,...] | 按给出的关键字来过滤展示报告，keys支持：comms、pids、tids等&nbsp;例如&nbsp;--comms&nbsp;hiperf,hilog&nbsp;表示仅显示进程/线程名称为&nbsp;hiperf或者hilog的记录条目。 | 
| --sort&nbsp;&lt;_key1_&gt;[,_key2_][,...] | 按照给出的关键字来排序和显示，支持：pid、tid、comm等，可以指定多个关键字。 | 
| -i&nbsp;&lt;_filename_&gt; | 指定输入的采样数据（默认为perf.data)。 | 
| -o&nbsp;&lt;_filename_&gt; | 指定输出的报告文件名。 | 


### 使用示例

- 输出采样数据的报告，默认读取perf.data文件
    
  ```
  hiperf report
  ```

  输出结果举例：

    
  ```
  Heating count    comm            pid  tid  dso                                func
   5.68%  15073949 hiperf_example_ 1085 1091 /system/lib/ld-musl-arm.so.1       malloc
   2.57%   6834119 hiperf_example_ 1085 1091 [kernel.kallsyms]                  vector_swi
   2.27%   6013910 hiperf_example_ 1085 1087 /system/lib/ld-musl-arm.so.1       malloc
   2.19%   5805738 hiperf_example_ 1085 1091 /system/lib/ld-musl-arm.so.1       vfprintf
   2.09%   5543362 hiperf_example_ 1085 1091 [kernel.kallsyms]                  ktime_get_ts64
  report done
  ```

- 输出采集数据的调用栈报告
    
  ```
  hiperf report -s
  ```

- 指定符号表路径
    
  ```
  hiperf report -s --symbol-dir /data/local/tmp
  ```

- 指定结果过滤的关键字，指定后会只显示包含该关键字的信息。例如要过滤libutils.z.so，命令如下：
    
  ```
  hiperf report --dsos libutils.z.so
  ```

- 指定按照特定的关键字进行排序展示，比如按照dso进行排序：
    
  ```
  hiperf report --sort dso
  ```


## 接口说明


### hiperf_client

[hiperf_client](https://gitcode.com/openharmony/developtools_hiperf/tree/master/interfaces/innerkits/native/hiperf_client)是hiperf部件提供的Perf采集接口。其实现原理是通过创建子进程执行hiperf二进制程序，采用管道返回数据给调用方。hiperf命令行工具中的--pipe_input和--pipe_output参数用于配置命令输入管道描述符和响应输出管道描述符，通过命名管道（FIFO）实现hiperf_client（客户端）与hiperf服务端进程的双向通信，实现如开启、停止采样等操作。
> 说明：开发者可通过调用Start、Pause、Stop等接口采集Perf数据，perf采集配置接口参考表1，开发者无需关心hiperf_client对hiperf命令行的封装细节。如果有定制化开发的需求，可基于hiperf命令行提供的--pipe_input、--pipe_output参数传入管道句柄来获取数据，进行二次开发。

  **表1** C++接口说明函数参数和功能

| 类 | 方法 | 描述 | 
| -------- | -------- | -------- |
| RecordOption | void SetOutputFilename(const std::string &outputFilename) | 功能：设置输出文件路径，默认路径为/data/local/tmp/perf.data。<br/>输入参数：<br/>-&nbsp;outputFilename：字符串类型，指定性能数据文件的保存路径。<br/>输出参数：无。<br/>返回值：空。 | 
|  | const std::string GetOutputFileName() const | 功能：获取当前设置的输出文件路径。<br/>输入参数：无。<br/>输出参数：无。<br/>返回值：字符串类型，代表输出的文件路径。 | 
|  | void SetSelectEvents(const std::vector\<std::string> &selectEvents) | 功能：设置采样事件（如硬件事件、软件事件等）。<br/>输入参数：<br/>-&nbsp;selectEvents：字符串数组类型，每个元素是一个事件名。<br/>输出参数：无。<br/>返回值：空。 | 
|  | const std::vector\<std::string> &GetSelectEvents() const | 功能：获取当前设置的事件列表（默认值为 {"hw-cpu-cycles:u"}）。<br/>输入参数：无。<br/>输出参数：无。<br/>返回值：字符串数组，每个元素是一个事件名。 |  
|  | void SetSelectGroups(const std::vector\<std::string> &selectGroups) | 功能：设置用于事件分组采样的采集事件群组。<br/>输入参数：<br/>-&nbsp;selectGroups：字符串数组类型，每个元素代表一个事件群组。<br/>输出参数：无。<br/>返回值：无。 |
|  | void SetTargetSystemWide(bool enable) | 功能：设置是否采集整机的性能数据（即采集所有CPU上的所有进程）。<br/>输入参数：<br/>-&nbsp;enable：布尔类型，true表示启用采集整机，false表示禁用采集整机。<br/>输出参数：无。<br/>返回值：空。 | 
|  | void SetSelectPids(const std::vector\<pid_t> &selectPids) | 功能：设置要采集的目标进程ID。<br/>输入参数：<br/>-&nbsp;selectPids：pid_t类型的数组，包含了目标进程的pid。<br/>输出参数：无。<br/>返回值：空。 | 
|  | void SetSelectTids(const std::vector\<pid_t> &selectTids) | 功能：设置要采集的目标线程ID。<br/>输入参数：<br/>-&nbsp;selectTids：pid_t类型的数组，包含了目标线程的tid。<br/>输出参数：无。<br/>返回值：空。 | 
|  | void SetAppPackage(const std::string &appPackage) | 功能：设置要采集的应用程序名。<br/>输入参数：<br/>-&nbsp;appPackage：字符串类型，代表目标应用的包名。<br/>输出参数：无。<br/>返回值：空。 | 
|  | void SetSelectCpus(const std::vector\<int> &cpus) | 功能：设置采集的CPU ID。<br/>输入参数：<br/>-&nbsp;cpus：整型数组，每个元素是一个CPU ID。<br/>输出参数：无。<br/>返回值：空。 | 
|  | void SetTimeStopSec(int timeStopSec) | 功能：设置采集的持续时间。<br/>输入参数：<br/>-&nbsp;timeStopSec：整型，表示采集将在多少秒后自动停止；单位s，默认1000s。<br/>输出参数：无。<br/>返回值：空。 | 
|  | void SetFrequency(int frequency) | 功能：设置采样频率。<br/>输入参数：<br/>-&nbsp;frequency：整型，代表采样频率，默认4000次/s。<br/>输出参数：无。<br/>返回值：空。 | 
|  | void SetPeriod(int period) | 功能：设置采样周期。<br/>输入参数：<br/>-&nbsp;period：整型，代表采样周期。<br/>输出参数：无。<br/>返回值：空。 | 
|  | void SetCallGraph(const std::string &sampleTypes) | 功能：设置回栈模式。<br/>输入参数：<br/>-&nbsp;sampleTypes：字符串类型，可设置为fp(栈指针)、dwarf(调试信息表)两种模式中的一种，默认是fp模式；若指定为dwarf，可以设置采样的栈大小\[dwarf,###]（### 代表一个整数，取值范围在8到65528 之间，且必须是8字节对齐的）。<br/>输出参数：无。<br/>返回值：空。 | 
|  | void SetCompressData(bool enable) | 功能：设置是否以.gz的压缩文件形式输出。<br/>输入参数：<br/>-&nbsp;enable：布尔类型，true表示开启压缩，false表示关闭。<br/>输出参数：无。<br/>返回值：空。 | 
|  | void SetDataLimit(const std::string &limit) | 功能：设置采集数据的大小限制。当数据量达到此限制时，采集将自动停止。<br/>输入参数：<br/>-&nbsp;limit：字符串类型，格式：SIZE [K\|M\|G]，默认无限制。<br/>输出参数：无。<br/>返回值：空。 | 
|  | void SetNoInherit(bool enable) | 功能：设置是否采集子进程数据。<br/>输入参数：<br/>-&nbsp;enable：布尔类型，true表示不允许子进程继承采集，false表示允许子进程继承采集。<br/>输出参数：无。<br/>返回值：空。 | 
|  | void SetCallStackSamplingConfigs(int duration) | 功能：设置调用栈采样的持续时间。<br/>输入参数：<br/>-&nbsp;duration：整型，单位为s，表示调用栈采样将持续的时间。<br/>输出参数：无。<br/>返回值：空。 | 
|  | void SetExcludePerf(bool excludePerf) | 功能：设置是否在采集过程中排除hiperf工具自身产生的性能事件。<br/>输入参数：<br/>-&nbsp;excludePerf：布尔类型，true代表排除hiperf自身的事件，false代表不排除hiperf自身的事件。<br/>输出参数：无。<br/>返回值：空。 | 
|  | void SetCpuPercent(int cpuPercent) | 功能：设置采集时CPU最大占比。<br/>输入参数：<br/>-&nbsp;cpuPercent：整型，表示采样进程最多可以占用单个CPU核心的百分比，取值范围：1 - 100，默认25。<br/>输出参数：无。<br/>返回值：空。 | 
|  | void SetOffCPU(bool offCPU) | 功能：设置是否启用对线程脱离CPU调度的跟踪。<br/>输入参数：<br/>-&nbsp;offCPU：布尔类型，true代表开启Off-CPU分析，false代表关闭Off-CPU分析。<br/>输出参数：无。<br/>返回值：空。 | 
|  | void SetDelayUnwind(bool delayUnwind) | 功能：设置是否启用延迟栈展开。<br/>输入参数：<br/>-&nbsp;delayUnwind：布尔类型，true代表启用延迟栈展开，false代表禁用延迟栈展开。<br/>输出参数：无。<br/>返回值：空。 | 
|  | void SetDisableUnwind(bool disableUnwind) | 功能：设置是否禁用栈展开。<br/>输入参数：<br/>-&nbsp;disableUnwind：布尔类型，true代表禁用栈展开，false代表启用栈展开。<br/>输出参数：无。<br/>返回值：空。 | 
|  | void SetSymbolDir(const std::string &symbolDir_) | 功能：设置符号表文件路径。<br/>输入参数：<br/>-&nbsp;symbolDir_：字符串类型，代表符号表文件所在的目录路径。<br/>输出参数：无。<br/>返回值：空。 | 
|  | void SetClockId(const std::string &clockId) | 功能：设置采集时钟类型。<br/>输入参数：<br/>-&nbsp;clockId：字符串类型，支持monotonic和monotonic_raw，部分事件支持boottime、realtime和clock_tai时钟类型。<br/>输出参数：无。<br/>返回值：空。 | 
|  | void SetVecBranchSampleTypes(const std::vector\<std::string> &vecBranchSampleTypes) | 功能：设置分支采样的过滤条件。<br/>输入参数：<br/>-&nbsp;vecBranchSampleTypes：字符串数组，每个元素代表一种分支类型，支持的分支类型包括："any": 采集所有类型的分支；"any_call": 采集所有函数调用分支；"any_ret": 采集所有函数返回分支；"indirect": 采集所有间接分支（如间接函数调用、switch 跳转等）；"cond": 采集所有条件分支（如 if/else, for, while 等）；"u": 仅采集用户态（User Mode）的分支。"k": 仅采集内核态（Kernel Mode）的分支。<br/>输出参数：无。<br/>返回值：空。 | 
|  | void SetMmapPages(int mmapPages) | 功能：设置mmap页数量。<br/>输入参数：<br/>-&nbsp;mmapPages：整型，表示共享内存区域的页数，必须是2的幂；取值范围：2 - 1024，默认1024。<br/>输出参数：无。<br/>返回值：空。 | 
|  | void SetReport(bool report) | 功能：设置是否在性能数据采集结束后，自动生成并显示一份简要的性能报告。<br/>输入参数：<br/>-&nbsp;report：布尔类型，true表示启用自动生成报告，false禁用自动生成报告。<br/>输出参数：无。<br/>返回值：空。 | 
|  | void SetExcludeProcess(const std::vector\<std::string>& excludeProcess) | 功能：设置不采集的线程名。<br/>输入参数：<br/>-&nbsp;excludeProcess：字符串数组，每个元素代表一个线程名。<br/>输出参数：无。<br/>返回值：空。 | 
|  | void SetBackTrack(bool backtrack) | 功能：设置是否启用回溯采集功能。<br/>输入参数：<br/>-&nbsp;backtrack：布尔类型，true表示启用回溯采集功能，false表示禁用回溯采集功能。<br/>输出参数：无。<br/>返回值：空。 | 
|  | void SetBackTrackSec(int backTracesec) | 功能：设置回溯采集的时间。<br/>输入参数：<br/>-&nbsp;backTracesec：整型，单位为s，表示回溯的时长。<br/>输出参数：无。<br/>返回值：空。 | 
|  | bool IsTimeSpecified() const | 功能：校验当前的RecordOption配置中，是否指定了采集时长。<br/>输入参数：无。<br/>输出参数：无。<br/>返回值：布尔类型，true表示已经设置采集时长，false表示尚未设置采集时长。 | 
| Client | bool Start() | 功能：启动性能数据采集，采用默认参数。<br/>输入参数：无。<br/>输出参数：无。<br/>返回值：布尔类型，true表示成功；false表示失败。 | 
|  | bool Start(const RecordOption &option) | 功能：根据RecordOption对象中配置的参数，启动性能数据采集。。<br/>输入参数：<br/>-&nbsp;option：RecordOption对象类型，包含了所有采集相关的配置（如采样事件、目标进程 PID、采样频率等）。<br/>输出参数：无。<br/>返回值：布尔类型，true表示成功；false表示失败。 | 
|  | bool Start(const std::vector\<std::string> &args, bool immediately = true) | 功能：使用命令行参数的形式启动性能数据采集。<br/>输入参数：<br/>-&nbsp;args：字符串数组，每个元素代表一个命令行参数（如 {"-a", "--call-graph", "dwarf"}）。<br/>-&nbsp;immediately：布尔类型，true表示是在启动后立即开始采集；false表示启动采集进程，但暂不开始采集，等待后续调用Resume() 方法。<br/>输出参数：无。<br/>返回值：布尔类型，true表示成功；false表示失败。 | 
|  | bool Stop() | 功能：停止性能数据采集，结束监控并保存数据。<br/>输入参数：无。<br/>输出参数：无。<br/>返回值：布尔类型，true表示成功；false表示失败。 | 
|  | bool Pause() | 功能：暂停当前的性能数据采集（可通过Resume恢复）。<br/>输入参数：无。<br/>输出参数：无。<br/>返回值：布尔类型，true表示成功；false表示失败。 | 
|  | bool Resume() | 功能：恢复被Pause暂停的性能数据采集。<br/>输入参数：无。<br/>输出参数：无。<br/>返回值：布尔类型，true表示成功；false表示失败。 | 
|  | bool Output() | 功能：将采集到的数据立即写入文件。<br/>输入参数：无。<br/>输出参数：无。<br/>返回值：布尔类型，true表示成功；false表示失败。 | 
|  | bool PrePare(const RecordOption &option) | 功能：根据RecordOption配置，进行采集前的准备工作（如创建输出目录、检查权限、构建命令行等），通常与StartRun配合使用。<br/>输入参数：<br/>-&nbsp;option：RecordOption对象类型，包含采集配置。<br/>输出参数：无。<br/>返回值：布尔类型，true表示成功；false表示失败。 | 
|  | bool StartRun() | 功能：在PrePare成功调用后，启动采集子进程并开始数据采集。<br/>输出参数：无。<br/>返回值：布尔类型，true表示成功；false表示失败。 | 
|  | bool RunHiperfCmdSync(const RecordOption &option) | 功能：同步执行一次性能采集命令。该方法会阻塞，直到采集完成。<br/>输入参数：<br/>-&nbsp;option：RecordOption对象类型，包含采集配置。<br/>输出参数：无。<br/>返回值：布尔类型，true表示成功；false表示失败。 | 
|  | bool Setup(std::string outputDir) | 功能：设置或更改性能数据的输出目录。<br/>输入参数：<br/>-&nbsp;outputDir：字符串类型，指定新的输出目录路径。<br/>输出参数：无。<br/>返回值：布尔类型，true表示成功；false表示失败。 | 
|  | bool IsReady() | 功能：检查 Client 实例是否已准备好，例如输出目录是否有效、hiperf命令是否可执行等。<br/>输入参数：无。<br/>输出参数：无。<br/>返回值：布尔类型，true表示成功；false表示失败。 | 
|  | const std::string &GetOutputDir() const | 功能：获取当前设置的性能数据输出目录路径。<br/>输入参数：无。<br/>输出参数：无。<br/>返回值：字符串类型，当前设置的输出文件路径。 | 
|  | const std::string &GetCommandPath() const | 功能：获取当前HiperfClient实例所使用的hiperf命令行工具的完整路径。<br/>输入参数：无。<br/>输出参数：无。<br/>返回值：字符串类型，代表当前HiperfClient实例所使用的hiperf命令行工具的完整路径。 | 
|  | const std::string GetOutputPerfDataPath() const | 功能：获取性能数据输出文件（默认是/data/local/tmp/perf.data）的完整路径。<br/>输入参数：无。<br/>输出参数：无。<br/>返回值：字符串类型，代表性能数据文件的完整路径。 | 


### 使用示例
    
1. 引入hiperf_client模块头文件。
     
   ```
   #include "hiperf_client.h"
   ```

2. 调用hiperf_client提供的接口开始和终止采集。
     
   ```
   HiperfClient::Client myHiperf;  // 创建通信管道
   myHiperf.Start();  // 启动采集
   myHiperf.Stop();  // 结束采集，采集结束后文件会被保存至/data/local/tmp/perf.data，调用Setup()接口并传入文件路径参数可以修改文件保存路径
   ```

3. 在BUILD.gn对应的编译目标中增加编译依赖。
     
   ```
   external_deps = [ "hiperf:hiperf_client" ]
   ```