# Faultlogger
<!--Kit: Performance Analysis Kit-->
<!--Subsystem: HiviewDFX-->
<!--Owner: @chenshi51-->
<!--Designer: @Maplestory91-->
<!--Tester: @gcw_KuLfPSbe-->
<!--Adviser: @jinqiuheng-->
<!-- md-trans-meta sourceCommit=0711013cb4474f6a33fc6adaa098c39ad0faae73 translatedAt=2026-10-31T06:41:24.028Z pushedAt=2026-10-31T06:41:24.028Z nl=1 -->

Faultlogger extends the [hidumper](hidumper.md) command-line tool to list fault log files, view their contents, and filter them by time or application bundle name. Fault logs are stored in **/data/log/faultlog/faultlogger** on the device. Faultlogger queries and reads files from this directory.

## Environment Setup

Follow [Environment Setup](hidumper.md#environment-setup) in the hidumper guide to prepare the environment.

## Command-Line Options

Run `hidumper -s 1201 -a "-p Faultlogger [options]"` to access the Faultlogger module's fault log functions. The **-p** option specifies a plugin module in the HiviewService system service, whose ID is **1201**. For details about hidumper commands, see [Obtaining Capabilities of a Specified System Service](hidumper.md#obtaining-capabilities-of-a-specified-system-service).

The following table describes the available options.

| Option | Description |
| -------- | -------- |
| -h | Displays help information. |
| -l | Lists all fault log file names in **/data/log/faultlog/faultlogger**. The **fileName** uses a timestamp in seconds and does not include the **.log** suffix.<br>**Note:** Starting from API version 18, files are stored with timestamps in milliseconds and the **.log** suffix. In earlier versions, they use timestamps in seconds without the suffix. The **-l** option always converts the output to timestamps in seconds without **.log**. Therefore, starting from API version 18, the **fileName** returned by **-l** is not the actual file name on the device. |
| -LogSuffixWithMs | Lists all fault log file names in **/data/log/faultlog/faultlogger**. The file name suffix contains a timestamp in milliseconds and ends with **.log**, matching the actual file name on the device.<br>**Note:** This option is supported starting from API version 18. The output **fileName** always uses a timestamp in milliseconds. |
| -f fileName [--ext] | Displays the contents of the specified fault log file.<br>Obtain **fileName** using **-l** or **-LogSuffixWithMs**.<br>The optional **--ext** argument applies only to AppFreeze logs. When specified, the corresponding enhanced log is appended to the original log contents in the output. |
| -t time | Lists the names of fault log files generated after the specified time in **/data/log/faultlog/faultlogger**. The time can be a Unix timestamp or use the year-month-day-hour-minute-second format, for example, **20250820211600**. |
| -m moduleName | Lists the names of fault log files associated with the specified application bundle name in **/data/log/faultlog/faultlogger**. |
| -d | Displays the contents of all fault log files. Files are separated by `******`, followed on the next line by the file name. |

## Obtaining Help Information

Run the following command to view help information.

```shell
hidumper -s 1201 -a '-p Faultlogger -h'
```

The output is as follows:

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

## Listing Fault Log Files

### Listing All Fault Log File Names

Run the following command to list all fault log file names in **/data/log/faultlog/faultlogger**.

```shell
hidumper -s 1201 -a '-p Faultlogger -l'
```

The output is as follows:

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

### Listing Fault Log File Names with Millisecond Timestamps

Run the following command to list all fault log file names in **/data/log/faultlog/faultlogger**. The file name suffix contains a timestamp in milliseconds and ends with **.log**.

```shell
hidumper -s 1201 -a '-p Faultlogger -LogSuffixWithMs'
```

The output is as follows:

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

Using timestamps in seconds as file names can cause duplicate names. To avoid this, three digits representing milliseconds and the **.log** suffix are added to distinguish the two naming formats. Fault logs in the two formats contain the same information.

On system versions that support **-LogSuffixWithMs**, file names returned by **-l** do not include **.log**, but the files on the device have this suffix. Exporting logs with hdc using file names returned by **-l** therefore fails. Instead, use the file names returned by **-LogSuffixWithMs**, including **.log**. The export command is as follows:

```shell
hdc file recv /data/log/faultlog/faultlogger/{filename} {path}
```

For example:

```shell
hdc file recv /data/log/faultlog/faultlogger/cppcrash-com.ohos.sceneboard-20020022-20241106104006123.log ./
```

### Listing Fault Log File Names After a Specified Time

Run the following command to list fault log files generated after a specified time in **/data/log/faultlog/faultlogger**. The **time** parameter accepts a Unix timestamp or the year-month-day-hour-minute-second format.

For example, query fault log files generated after August 21, 2025, at 10:00:00 Beijing time (Unix timestamp **1755741600**).

Using the year-month-day-hour-minute-second format:

```shell
hidumper -s 1201 -a '-p Faultlogger -t 20250821100000'
```

Using a Unix timestamp:

```shell
hidumper -s 1201 -a '-p Faultlogger -t 1755741600'
```

The output is as follows:

```text
-------------------------------[ability]-------------------------------

----------------------------------HiviewService----------------------------------
Fault log list:
******
cppcrash-com.ohos.sceneboard-20020022-20250821154006
appfreeze-com.ohos.settings-20020045-20250821123012
******
```

### Listing Fault Log File Names for a Specified Application

Run the following command to list fault log files associated with a specified application bundle name in **/data/log/faultlog/faultlogger**.

```shell
hidumper -s 1201 -a '-p Faultlogger -m com.ohos.sceneboard'
```

The output is as follows:

```text
-------------------------------[ability]-------------------------------

----------------------------------HiviewService----------------------------------
Fault log list:
******
cppcrash-com.ohos.sceneboard-20020022-20241106104006
syswarning-com.ohos.sceneboard-20020022-20241106104006
******
```

You can combine options for more precise queries. For example, filter by both time and application bundle name:

```shell
hidumper -s 1201 -a '-p Faultlogger -t 20250821100000 -m com.ohos.sceneboard'
```

## Viewing Fault Log Contents

### Viewing a Specified Fault Log

Run the following command to view a specified fault log file. Obtain its file name using **-l** or **-LogSuffixWithMs**. For log specifications, see [CppCrash](cppcrash-guidelines.md#log-specifications), [JSCrash](jscrash-guidelines.md#log-specifications), [AppFreeze](appfreeze-guidelines.md#log-specifications), and [AppFreeze Enhanced Logs](appfreeze-guidelines.md#enhanced-log-specifications).

```shell
hidumper -s 1201 -a '-p Faultlogger -f cppcrash-com.ohos.sceneboard-20020022-20241106104006'
```

The output is as follows:

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

For AppFreeze logs, specify **--ext** to append the corresponding enhanced log contents to the original log output:

```shell
hidumper -s 1201 -a '-p Faultlogger -f appfreeze-com.ohos.settings-20020045-20241106103512 --ext'
```

The output is as follows:

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

> **NOTE**
>
> - The `--ext` argument applies only to AppFreeze logs.
> - Enhanced logs contain additional diagnostic information about application freezes.
> - Both the fault log and the enhanced log are enclosed by `******` start and end markers.

### Viewing All Fault Logs

Run the following command to display all fault logs. Files are separated by `******`, followed on the next line by the file name.

```shell
hidumper -s 1201 -a '-p Faultlogger -d'
```

The output is as follows:

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
