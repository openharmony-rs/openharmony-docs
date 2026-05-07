# hitrace

<!--Kit: Performance Analysis Kit-->
<!--Subsystem: HiviewDFX-->
<!--Owner: @qq_437963121-->
<!--Designer: @kutcherzhou1; @MontSaintMichel-->
<!--Tester: @gcw_KuLfPSbe-->
<!--Adviser: @foryourself-->

hitrace provides the capability of collecting trace information in text or binary format, including system logging and custom logging set through the [HiTraceMeter APIs](hitracemeter-intro.md), helping you observe program running status and locate faults.


## Environment Requirements

- The environment for OpenHarmony Device Connector (hdc) has been set up. For details, see [Environment Setup](hdc.md#environment-setup).

- The devices are properly connected and **hdc shell** is executed.


## Command Description

| Command| Description|
| -------- | -------- |
| -h/--help | Displays the help information.|
| -l/--list_categories | Displays the tag list.|
| --trace_begin | Starts capturing trace data.|
| --trace_finish | Stops capturing trace data.|
| --trace_finish_nodump | Stops capturing trace data. Unlike **--trace_finish**, this command does not output trace information.|
| --trace_dump | Dumps trace information.|
| --record | Enables the recording mode, which allows long-time trace data collection and persisting. This command must be used together with **--trace_begin** or **--trace_finish**.|
| --overwrite | Sets the behavior after the kernel buffer is full. If this option is not set, the earliest data is discarded by default. Otherwise, the latest data is discarded.|
| --file_size | Sets the file size, in KB. This option is valid only for collecting trace data in binary format.|
| -b N/--buffer_size N | Sets the buffer size for storing and reading trace data, in KB. The minimum value is 512, and the maximum value depends on the available memory of the device.|
| -t N/--time N | Sets the collection duration, in seconds.|
| -o/--output filename | Specifies the name of the target file. If the exported trace data is in text format, the default value is **stdout**. If you want to save the trace data to a file, you are advised to use the **/data/local/tmp** directory. This option is not supported if the exported trace data is in binary format.|
| -z | Compresses the captured trace data.|
| --text | Exports trace data in text format (text format is used by default).|
| --raw | Exports trace data in binary format (text format is used by default).|
| --trace_clock | Sets the clock type used by the timestamp in the trace data. The value can be **boot** (default), **global**, **mono**, **uptime**, or **perf**. Supported clock types vary according to devices. You are advised to use the default **boot** to collect data, which is the timestamp of the current startup, in seconds. The time types are described as follows:<br>- **boot**: timestamp that starts at system startup and continues to accumulate while the system is hibernated or suspended.<br>- **global**: global clock, which may cause performance overhead.<br>- **mono**: timestamp that starts at system startup and does not accumulate when the system is hibernated or suspended.<br>- **uptime**: timestamp that starts at system startup, which is similar to **mono**.<br>- **perf**: high-performance counter, which is suitable for performance analysis.|
| --start_bgsrv | Starts trace collection in the snapshot mode.|
| --dump_bgsrv | Dumps the trace data in the snapshot mode to a file.|
| --stop_bgsrv | Stops trace collection in the snapshot mode.|
| --trace_level | Sets the trace level threshold. The value can be **Debug**, **Info**, **Critical**, **Commercial**, or **D**, **I**, **C**, or **M**.<br>**Note**: This command is supported since API version 19.|
| --get_level | Queries the trace level threshold.<br>Note: This command is supported since API version 20.|

> **NOTE**
>
> Trace information can be saved in text or binary format. The trace information in text format can be viewed using a text editor, and the trace information in binary format can be analyzed using the [Smartperf_Host](https://gitcode.com/openharmony/developtools_smartperf_host). You can download the tool from [developtools_smartperf_host Release](https://gitcode.com/openharmony/developtools_smartperf_host/releases).


## Examples


### Querying Help Information


```shell
hitrace -h
```


**Example**


```shell
$ hitrace -h
2025/05/28 15:19:52 hitrace enter, running_state is SHOW_HELP
usage: hitrace [options] [categories...]
options include:
  -b N                   Set the size of the buffer (KB) for storing and reading traces.
                         The default buffer size is 18432 KB.
  --buffer_size N        Like "-b N".
  -l                     List available hitrace categories.
  --list_categories      Like "-l".
  -t N                   Set the hitrace running duration in seconds (5s by default), which depends on
                         the time required for analysis.
  --time N               Like "-t N".
  --trace_clock clock    Sets the type of the clock for adding a timestamp to a trace, which can be
                         boot (default), global, mono, uptime, or perf.
  --trace_begin          Start capturing traces.
  --trace_dump           Dump traces to a specified path (stdout by default).
  --trace_finish         Stop capturing traces and dumps traces to a specified path (stdout by default).
  --trace_finish_nodump  Stop capturing traces and not dumps traces.
  --record               Enable or disable long-term trace collection tasks in conjunction with
                         "--trace_begin" and "--trace_finish".
  --overwrite            Set the action to take when the buffer is full. If this option is used,
                         the latest traces are discarded; if this option is not used (default setting),
                         the earliest traces are discarded.
  -o filename            Specifies the name of the target file (stdout by default).
  --output filename      Like "-o filename".
  -z                     Compresses a captured trace.
  --text                 Specify the output format of trace as text.
  --raw                  Specify the output format of trace as raw trace, the default format is text.
  --start_bgsrv          Enable trace_service in snapshot mode.
  --dump_bgsrv           Trigger the dump trace task of the trace_service.
  --stop_bgsrv           Disable trace_service in snapshot mode.
  --file_size            Sets the size of the raw trace (KB). The default file size is 102400 KB.
                         Only effective in raw trace mode
  --trace_level level    Set the system parameter "persist.hitrace.level.threshold", which can control
                         the level threshold of tracing. Valid values for "level" include
                         D or Debug, I or Info, C or Critical, M or Commercial.
  --get_level            Query the system parameter "persist.hitrace.level.threshold",
                         which can control the level threshold of tracing.
```


### Displaying the Tag List in hitrace

```shell
hitrace -l
```

For details about the tags, see the following table.

| Name           | Description                                                        |
| :----------------- | :----------------------------------------------------------- |
| ability            | Ability manager service, which is a user-mode trace tag.                           |
| accesscontrol      | Access control module, which is a user-mode trace tag.                             |
| accessibility      | Accessibility software service manager, which is a user-mode trace tag.                     |
| ace                | ArkUI cross-platform engine development framework, which is a user-mode trace tag.                  |
| animation          | Animation module, which is a user-mode trace tag.                                 |
| app                | Application module, which is a user-mode trace tag. Trace points generated by the [HiTraceMeter](hitracemeter-intro.md) API are categorized under the app tag.|
| ark                | Ark module, which is a user-mode trace tag.                                  |
| account            | Account manager, which is a user-mode trace tag.                               |
| binder             | Binder communication kernel information, which is a kernel-mode trace tag.                       |
| bluetooth          | Bluetooth communication, which is a user-mode trace tag.                                 |
| cloud              | Cloud subsystem, which is a user-mode trace tag.                                 |
| commercial         | Nolog version, which is a user-mode trace tag.                            |
| commonlibrary      | Common library, which is a user-mode trace tag.                                   |
| dcamera            | Distributed camera, which is a user-mode trace tag.                               |
| daudio             | Distributed audio, which is a user-mode trace tag.                               |
| devicemanager      | Device manager, which is a user-mode trace tag.                               |
| deviceauth         | Device authentication, which is a user-mode trace tag.                                 |
| deviceprofile      | Device profile, which is a user-mode trace tag.                             |
| dhfwk              | Distributed hardware framework, which is a user-mode trace tag.                           |
| dinput             | Distributed input, which is a user-mode trace tag.                               |
| dlpcre             | Data leak prevention credential service, which is a user-mode trace tag.                       |
| disk               | Disk I/O, which is a kernel-mode trace tag.                                  |
| distributeddatamgr | Distributed data manager, which is a user-mode trace tag.                         |
| dscreen            | Distributed screen, which is a user-mode trace tag.                               |
| dsched             | Distributed scheduling, which is a user-mode trace tag.                               |
| dsoftbus           | Distributed soft bus, which is a user-mode trace tag.                             |
| drm                | Digital rights management, which is a user-mode trace tag.                             |
| erofs              | Enhanced read-only file system, which is a kernel-mode trace tag.                       |
| ffrt               | FFRT task, which is a user-mode trace tag.                                 |
| filemanagement     | File management, which is a user-mode trace tag.                                 |
| freq               | CPU frequency, which is a kernel-mode trace tag.                                  |
| gresource          | Global resource manager, which is a user-mode trace tag.                           |
| graphic            | Graphics module, which is a user-mode trace tag.                                 |
| hdcd               | hdcd tool, which is a user-mode trace tag.                                 |
| hdf                | Hardware driver framework, which is a user-mode trace tag.                             |
| huks               | Universal keystore, which is a user-mode trace tag.                               |
| idle               | CPU idle information, which is a kernel-mode trace tag.                              |
| interconn          | Interconnection subsystem, which is a user-mode trace tag.                               |
| ipa                | Thermal power consumption distributor, which is a kernel-mode trace tag.                             |
| irq                | IRQ event, which is a kernel-mode trace tag.                                  |
| irqoff             | IRQ-disabled code segment tracing, which is a kernel-mode trace tag.                        |
| i2c                | I2C bus event, which is a kernel-mode trace tag.                              |
| load               | CPU load, which is a kernel-mode trace tag.                                  |
| membus             | Memory bus usage, which is a kernel-mode trace tag.                           |
| memory             | Memory information, which is a kernel-mode trace tag.                                 |
| memreclaim         | Kernel memory reclamation, which is a kernel-mode trace tag.                             |
| misc               | MISC module, which is a user-mode trace tag.                                 |
| mdfs               | Mobile distributed file system, which is a user-mode trace tag.                       |
| mmc                | eMMC command, which is a kernel-mode trace tag.                       |
| multimodalinput    | Multi-modal input, which is a user-mode trace tag.                               |
| musl               | musl module, which is a user-mode trace tag.                                 |
| net                | Network module, which is a user-mode trace tag.                                 |
| notification       | Notification module, which is a user-mode trace tag.                                 |
| nweb               | NWeb module, which is a user-mode trace tag.                                 |
| ohos               | System common tag, which is a user-mode trace tag.                             |
| pagecache          | Page cache, which is a kernel-mode trace tag.                                   |
| power              | Power manager, which is a user-mode trace tag.                               |
| preemptoff         | Preemption-disabled code segment tracing, which is a kernel-mode trace tag.                       |
| push               | Push subsystem, which is a user-mode trace tag.                               |
| regulators         | Voltage and current regulator, which is a kernel-mode trace tag.                           |
| rpc                | RPC and IPC communication, which is a user-mode trace tag.                             |
| samgr              | Service ability management group, which is a user-mode trace tag.                           |
| sched              | CPU scheduling, which is a kernel-mode trace tag.                                  |
| schedlt            | Lightweight CPU scheduling, which is a kernel-mode trace tag.<br>Note: This tag is supported since API version 23.|
| security           | Security subsystem, which is a user-mode trace tag.                               |
| sensors            | Sensor module, which is a user-mode trace tag.                               |
| sync               | DMA synchronization, which is a kernel-mode trace tag.                                  |
| useriam            | User identity and access management, which is a user-mode trace tag.                       |
| ufs                | Universal flash storage command, which is a kernel-mode trace tag.                         |
| usb                | USB subsystem, which is a user-mode trace tag.                                |
| virse              | Virtualization service, which is a user-mode trace tag.                               |
| workq              | Kernel worker queue, which is a kernel-mode trace tag.                           |
| window             | Window manager, which is a user-mode trace tag.                               |
| zbinder            | ZBinder event, which is a kernel-mode trace tag.                              |
| zcamera            | Camera module, which is a user-mode trace tag.                                 |
| zimage             | Image module, which is a user-mode trace tag.                                 |
| zmedia             | Media module, which is a user-mode trace tag.                                 |
| zaudio             | Audio module, which is a user-mode trace tag.                                 |

**Example**

```shell
$ hitrace -l
2025/05/27 16:24:38 hitrace enter, running_state is SHOW_LIST_CATEGORY
            tagName:   description:
             ability - Ability Manager
       accesscontrol - Access Control Module
       accessibility - Accessibility Manager
             account - Account Manager
......
```


### Capturing Text Trace Data of a Specified Duration

If the **-o** parameter is not specified, the captured trace content is displayed in the CLI by default. The following command is used to collect data for 10 seconds, with the buffer size set to **204800** KB and the tag to **app**.

```shell
hitrace -t 10 -b 204800 app
```

**Example**


```shell
$ hitrace -t 10 -b 204800 app
2025/06/04 10:14:52 start capture, please wait 10s ...
# tracer: nop
#                                          _-----=> irqs-off
#                                         / _----=> need-resched
#                                        | / _---=> hardirq/softirq
#                                        || / _--=> preempt-depth
#                                        ||| /     delay
#           TASK-PID       TGID    CPU#  ||||   TIMESTAMP  FUNCTION
#              | |           |       |   ||||      |         |
 KstateRecvThrea-1132    (    952) [003] .... 589942.951387: tracing_mark_write: B|952|H:CheckMsgFromNetlink|I62
 KstateRecvThrea-1132    (    952) [003] .... 589942.951554: tracing_mark_write: B|952|H:OnKstateCallback, mask: 8, data: [PID 15461 KILLED][SIG 9]|I62
 KstateRecvThrea-1132    (    952) [003] .... 589942.951693: tracing_mark_write: E|952|I62
 KstateRecvThrea-1132    (    952) [003] .... 589942.951737: tracing_mark_write: E|952|I62
 state_change_ha-1139    (    952) [001] .... 589942.951909: tracing_mark_write: B|952|H:ProcessEvent, eventId: 6|I62
 state_change_ha-1139    (    952) [001] .... 589942.952510: tracing_mark_write: E|952|I62
2025/06/04 10:15:02 TraceFinish done.
```


Specify the **-o** option to save trace information to a specified directory. You are advised to save it to the **/data/local/tmp** directory.


```shell
hitrace -t 10 -b 204800 app -o /data/local/tmp/test.ftrace
```


**Example**


```shell
$ hitrace -t 10 -b 204800 app -o /data/local/tmp/test.ftrace
2025/06/04 10:19:47 start capture, please wait 10s ...
2025/06/04 10:19:57 capture done, start to read trace.
2025/06/04 10:19:57 trace read done, output: /data/local/tmp/test.ftrace
2025/06/04 10:19:57 TraceFinish done.
```


### Capturing Binary Trace Data of a Specified Duration

Specify the **--raw** option to capture binary trace data, which is always saved in **/data/log/hitrace**. After the collection is complete, the absolute path of the generated file is displayed in the CLI.

```shell
hitrace -t 10 -b 204800 app --raw
```


**Example**


```shell
$ hitrace -t 10 -b 204800 app --raw
2025/06/04 10:21:16 hitrace enter, running_state is RECORDING_SHORT_RAW
2025/06/04 10:21:16 args: tags:app bufferSize:204800 overwrite:1
2025/06/04 10:21:16 start capture, please wait 10s ...
2025/06/04 10:21:27 capture done, output files:
    /data/log/hitrace/record_trace_20250604102116@590322-695861087.sys
```


### Capturing Text Trace Data in Snapshot Mode

In snapshot mode, trace data is stored in the kernel buffer. When the data volume exceeds the buffer size, the earliest data is discarded by default.

Run the following command to enable the snapshot mode, with the buffer size set to 204800 KB and the collection tags to **app** and **graphic**.

```shell
hitrace --trace_begin -b 204800 app graphic
```

**Example**

```shell
$ hitrace --trace_begin -b 204800 app graphic
2025/06/04 16:03:39 hitrace enter, running_state is RECORDING_LONG_BEGIN
2025/06/04 16:03:39 args: tags:app,graphic bufferSize:204800 overwrite:1
2025/06/04 16:03:39 OpenRecording done.
```

After the snapshot mode is enabled, you can run the following command to export the data in the buffer. By default, the trace data is displayed in the CLI.

```shell
hitrace --trace_dump
```

**Example**

```shell
$ hitrace --trace_dump
2025/06/04 16:07:57 start to read trace.
# tracer: nop
#                                          _-----=> irqs-off
#                                         / _----=> need-resched
#                                        | / _---=> hardirq/softirq
#                                        || / _--=> preempt-depth
#                                        ||| /     delay
#           TASK-PID       TGID    CPU#  ||||   TIMESTAMP  FUNCTION
#              | |           |       |   ||||      |         |
 KstateRecvThrea-1132    (    952) [002] .... 610865.463378: tracing_mark_write: B|952|H:CheckMsgFromNetlink|I62
 KstateRecvThrea-1132    (    952) [002] .... 610865.463503: tracing_mark_write: B|952|H:OnKstateCallback, mask: 8, data: [PID 14446 KILLED][SIG 9]|I62
 KstateRecvThrea-1132    (    952) [002] .... 610865.463626: tracing_mark_write: E|952|I62
 KstateRecvThrea-1132    (    952) [002] .... 610865.463654: tracing_mark_write: E|952|I62
 state_change_ha-1139    (    952) [001] .... 610865.463767: tracing_mark_write: B|952|H:ProcessEvent, eventId: 6|I62
 state_change_ha-1139    (    952) [001] .... 610865.463879: tracing_mark_write: E|952|I62
 state_change_ha-1139    (    952) [001] .... 610866.506055: tracing_mark_write: B|952|H:ProcessEvent, eventId: 0|I62
 state_change_ha-1139    (    952) [001] .... 610866.506297: tracing_mark_write: B|952|H:HandleStateTransition, 20020111_com.ohos.medialibrary.medialibrarydata_[6255]|I62
 state_change_ha-1139    (    952) [001] .... 610866.506782: tracing_mark_write: E|952|I62
 state_change_ha-1139    (    952) [001] .... 610866.506824: tracing_mark_write: E|952|I62
 state_change_ha-1139    (    952) [001] .... 610866.557458: tracing_mark_write: B|952|H:ProcessEvent, eventId: 0|I62
 state_change_ha-1139    (    952) [001] .... 610866.558060: tracing_mark_write: E|952|I62
 state_change_ha-1139    (    952) [001] .... 610866.558101: tracing_mark_write: E|952|I62
```

You can also run the **-o** command to save the exported data to a specified file. You are advised to save the file to the **/data/local/tmp** directory.

```shell
hitrace --trace_dump -o /data/local/tmp/test.ftrace
```

**Example**

```shell
$ hitrace --trace_dump -o /data/local/tmp/test.ftrace
2025/06/04 16:09:10 start to read trace.
2025/06/04 16:09:10 trace read done, output: /data/local/tmp/test.ftrace
```

To stop the collection, run any of the following commands:

1. Stop the collection and display the trace information in the buffer in the CLI.

    ```shell
    hitrace --trace_finish
    ```

    **Example**

    ```shell
    $ hitrace --trace_finish
    2025/06/04 16:22:02 start to read trace.
    # tracer: nop
    #                                          _-----=> irqs-off
    #                                         / _----=> need-resched
    #                                        | / _---=> hardirq/softirq
    #                                        || / _--=> preempt-depth
    #                                        ||| /     delay
    #           TASK-PID       TGID    CPU#  ||||   TIMESTAMP  FUNCTION
    #              | |           |       |   ||||      |         |
    KstateRecvThrea-1132    (    952) [002] .... 610865.463378: tracing_mark_write: B|952|H:CheckMsgFromNetlink|I62
    KstateRecvThrea-1132    (    952) [002] .... 610865.463503: tracing_mark_write: B|952|H:OnKstateCallback, mask: 8, data: [PID 14446 KILLED][SIG 9]|I62
    KstateRecvThrea-1132    (    952) [002] .... 610865.463626: tracing_mark_write: E|952|I62
    KstateRecvThrea-1132    (    952) [002] .... 610865.463654: tracing_mark_write: E|952|I62
    ```

2. Stop the collection and save the trace information in the buffer to a specified file. You are advised to save it to /data/local/tmp.

    ```shell
    hitrace --trace_finish -o /data/local/tmp/test.ftrace
    ```

    **Example**

    ```shell
    $ hitrace --trace_finish -o /data/local/tmp/test.ftrace
    2025/06/04 16:24:52 start to read trace.
    2025/06/04 16:24:52 trace read done, output: /data/local/tmp/test.ftrace
    2025/06/04 16:24:52 Trace Closed.
    ```

3. Stop trace collection and do not output trace information.

    ```shell
    hitrace --trace_finish_nodump
    ```

    **Example**

    ```shell
    $ hitrace --trace_finish_nodump
    2025/06/04 16:26:11 hitrace enter, running_state is RECORDING_LONG_FINISH_NODUMP
    2025/06/04 16:26:11 end capture trace.
    ```


### Capturing Binary Trace Data in Snapshot Mode


When binary trace data is captured in snapshot mode, **tag** cannot be specified. By default, the following tags are collected:


```shell
"net", "dsched", "graphic", "multimodalinput", "dinput", "ark", "ace", "window","zaudio", "daudio", "zmedia", "dcamera", "zcamera", "dhfwk", "app", "gresource", "ability", "power", "samgr", "ffrt", "nweb", "hdf", "virse", "workq", "ipa", "sched", "freq", "disk", "sync", "binder", "mmc", "membus", "load"
```


Run the following command to start capturing binary trace data:


```shell
hitrace --start_bgsrv
```


**Example**


```shell
$ hitrace --start_bgsrv
2025/06/04 16:44:54 hitrace enter, running_state is SNAPSHOT_START
2025/06/04 16:44:54 OpenSnapshot done.
```


Run the following command to export the trace information in the buffer to a file. Binary trace data cannot be exported to a specified path or displayed in the CLI. The exported file path is displayed in the CLI.


```shell
hitrace --dump_bgsrv
```


**Example**


```shell
$ hitrace --dump_bgsrv
2025/06/04 16:50:34 hitrace enter, running_state is SNAPSHOT_DUMP
2025/06/04 16:50:35 DumpSnapshot done, output:
    /data/log/hitrace/trace_20250604164454@613340-339960.sys
```


Run the following command to stop the collection:


```shell
hitrace --stop_bgsrv
```


**Example**


```shell
$ hitrace --stop_bgsrv
2025/06/04 16:52:51 hitrace enter, running_state is SNAPSHOT_STOP
2025/06/04 16:52:52 CloseSnapshot done.
```


### Capturing Trace Data in Record Mode

In record mode, the system continuously saves binary trace data generated during running. When the file size exceeds the preset value, a new file is generated. The save path cannot be specified.

Run the following command to enable the record mode. Set the buffer size to 204800 KB, the file size to 102400 KB, and the tags to **app** and **graphic**.

```shell
hitrace --trace_begin --record -b 204800 --file_size 102400 app graphic
```

**Example**

```shell
$ hitrace --trace_begin --record -b 204800 --file_size 102400 app graphic
2025/06/04 17:03:37 hitrace enter, running_state is RECORDING_LONG_BEGIN_RECORD
2025/06/04 17:03:37 args: tags:app,graphic bufferSize:204800 overwrite:1 fileSize:102400
2025/06/04 17:03:37 trace capturing.
```


After the collection is complete, run the following command to stop the collection. The absolute path of the generated file is displayed in the CLI.


```shell
hitrace --trace_finish --record
```


**Example**


```shell
$ hitrace --trace_finish --record
2025/06/04 17:06:14 hitrace enter, running_state is RECORDING_LONG_FINISH_RECORD
2025/06/04 17:06:15 capture done, output files:
    /data/log/hitrace/record_trace_20250604170337@614463-183970330.sys
    /data/log/hitrace/record_trace_20250604170423@614508-554071886.sys
    /data/log/hitrace/record_trace_20250604170552@614597-598551039.sys
```


### Compressing Trace Data

```shell
hitrace -z -b 102400 -t 10 sched freq idle disk -o /data/local/tmp/test.ftrace
```

**Example**

```shell
$ hitrace -z -b 102400 -t 10 sched freq idle disk -o /data/local/tmp/test.ftrace
2024/11/14 12:00:18 start capture, please wait 10s ...
2024/11/14 12:00:28 capture done, start to read trace.
2024/11/14 12:00:29 trace read done, output: /data/local/tmp/test.ftrace
2024/11/14 12:00:29 TraceFinish done.
```


### Setting and Querying the Trace Level Threshold

The priority of the trace level is as follows: **M** (**Commercial**), **C** (**Critical**), **I** (**Info**) and **D** (**Debug**). The trace level lower than the threshold does not take effect.

You can use the logging APIs with the trace level (for details, see the logging APIs of API version 19 in [js-apis-hitracemeter](../reference/apis-performance-analysis-kit/js-apis-hitracemeter.md) and [_hitrace](../reference/apis-performance-analysis-kit/capi-trace-h.md)) to test whether the trace output under different thresholds meets the expectation.

```shell
// Set the trace level threshold.
hitrace --trace_level D/I/C/M
hitrace --trace_level Debug/Info/Critical/Commercial
// Query the trace level threshold.
hitrace --get_level
```

**Example**

```shell
$ hitrace --trace_level Info
2025/08/16 10:34:23 hitrace enter, running_state is SET_TRACE_LEVEL
2025/08/16 10:34:23 success to set trace level.
$ hitrace --get_level
2025/08/16 10:34:29 hitrace enter, running_state is GET_TRACE_LEVEL
2025/08/16 10:34:29 the current trace level threshold is Info
```


## Trace File Names

When hitrace is used to collect trace information in binary format, the file path cannot be specified. By default, the trace file is saved in the **/data/log/hitrace** directory. hitrace automatically generates the file name and displays the absolute path in the CLI.

In snapshot mode, the trace file name starts with **trace**; in record mode, it starts with **record**. The name ends with the local time and boot time (timestamp starting from the startup time).

For example, the file name **20250701215441** indicates that the file is generated at 21:54:41 on July 1, 2025, and the corresponding boot time is **6016.653165227**.

```shell
$ hitrace --dump_bgsrv
2025/07/01 21:54:41 hitrace enter, running_state is SNAPSHOT_DUMP
2025/07/01 21:54:42 DumpSnapshot done, output:
    /data/log/hitrace/trace_20250701215441@6016-653165227.sys
```


## FAQs


### What should I do if error code 1 is displayed after the hitrace command is executed?

**Symptom**

Error code 1 is displayed after the hitrace command is executed.

```shell
$ hitrace --dump_bgsrv
2025/07/04 17:20:38 hitrace enter, running_state is SNAPSHOT_DUMP
2025/07/04 17:20:38 error: DumpSnapshot failed, errorCode(1)
```

**Possible Causes and Solution**

Error code 1 indicates that the HiView process is abnormal. You can restart the mobile phone and collect data again.


### What should I do if the error message "not support category on this device" is displayed after the hitrace command is executed?

**Symptom**

After the hitrace command is executed, the error message "not support category on this device" is displayed.

```shell
$ hitrace -t 10 aaa
2025/07/04 17:24:21 error: aaa is not support category on this device.
2025/07/04 17:24:21 error: parsing args failed, exit.
```

**Possible Causes and Solution**

The tag specified in the command does not exist. You are advised to run the **hitrace -l** command to view the supported tags.


### What should I do if error code 1004 is displayed after the hitrace command is executed?

**Symptom**

Error code 1004 is displayed after the hitrace command is executed.

```shell
$ hitrace --dump_bgsrv
2025/07/04 17:25:58 hitrace enter, running_state is SNAPSHOT_DUMP
2025/07/04 17:25:58 error: DumpSnapshot failed, errorCode(1004)
```

**Possible Causes and Solution**

1004 indicates that an error occurs when data is written into the file. The possible causes are as follows:

1. When the trace data in text format is collected, the output file path specified by the **-o** option does not exist or you do not have the permission to use the path. You are advised to save the trace data to the **/data/local/tmp** directory.

2. When the disk space is full, no new trace file is generated. You are advised to release the disk space and ensure that the available space is greater than 500 MB. Then collect the trace data again.
