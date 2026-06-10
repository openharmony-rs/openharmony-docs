# @ohos.hilog (HiLog)

<!--Kit: Performance Analysis Kit-->
<!--Subsystem: HiviewDFX-->
<!--Owner: @buzhenwang-->
<!--Designer: @milkbread123-->
<!--Tester: @liyang2235-->
<!--Adviser: @jinqiuheng-->

The HiLog subsystem allows your applications or services to output logs based on the specified type, level, and format string. Such logs help you learn the running status of applications and better debug programs.

> **NOTE**
>
> The initial APIs of this module are supported since API version 7. Newly added APIs will be marked with a superscript to indicate their earliest API version.

## Modules to Import

```js
import { hilog } from '@kit.PerformanceAnalysisKit';
```

## hilog.isLoggable

isLoggable(domain: number, tag: string, level: LogLevel) : boolean

Checks whether logs are printable based on the specified service domain, log tag, and log level.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.HiviewDFX.HiLog

**Parameters**

| Name| Type                 | Mandatory| Description                                                        |
| ------ | --------------------- | ---- | ------------------------------------------------------------ |
| domain | number                | Yes  | Service domain of logs. The value ranges from **0x0** to **0xFFFF**. If the value exceeds the range, logs cannot be printed.<br>You can define the value as required.|
| tag    | string                | Yes  | Log tag in the string format. You are advised to use this parameter to identify a particular service behavior or the class holding the ongoing method. A tag can contain a maximum of 31 bytes. If a tag exceeds this limit, it will be truncated. Chinese characters are not recommended because garbled characters or alignment problems may occur.|
| level  | [LogLevel](#loglevel) | Yes  | Log level.                                                  |

**Return value**

| Type   | Description                                                        |
| ------- | ------------------------------------------------------------ |
| boolean | Returns **true** logs are printable based on the specified service domain, log tag, and log level; returns **false** otherwise.|

**Example**

```js
hilog.isLoggable(0x0001, "testTag", hilog.LogLevel.INFO);
```

## LogLevel

Enumerates the log levels.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.HiviewDFX.HiLog

| Name |   Value  | Description                                                        |
| ----- | ------ | ------------------------------------------------------------ |
| DEBUG | 3      | Log level used to record more detailed process information than INFO logs to help developers analyze service processes and locate faults.|
| INFO  | 4      | Log level used to record key service process nodes and exceptions that occur during service running,<br>for example, no network signal or login failure.<br>These logs should be recorded by the dominant module in the service to avoid repeated logging conducted by multiple invoked modules or low-level functions.|
| WARN  | 5      | Log level used to record severe, unexpected faults that have little impact on users and can be rectified by the programs themselves or through simple operations.|
| ERROR | 6      | Log level used to record program or functional errors that affect the normal running or use of the functionality and can be fixed at a high cost, for example, by resetting data.|
| FATAL | 7      | Log level used to record program or functionality crashes that cannot be rectified.              |

## hilog.debug

debug(domain: number, tag: string, format: string, ...args: any[]) : void

Prints DEBUG logs.

DEBUG logs are not recorded in official versions by default. They are available in debug versions or in official versions with the debug function enabled.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.HiviewDFX.HiLog

**Parameters**

| Name| Type  | Mandatory| Description                                                        |
| ------ | ------ | ---- | ------------------------------------------------------------ |
| domain | number | Yes  | Service domain of logs. The value ranges from **0x0** to **0xFFFF**. If the value exceeds the range, logs cannot be printed.<br>You can define the value as required.|
| tag    | string | Yes  | Log tag in the string format. You are advised to use this parameter to identify a particular service behavior or the class holding the ongoing method. A tag can contain a maximum of 31 bytes. If a tag exceeds this limit, it will be truncated. Chinese characters are not recommended because garbled characters or alignment problems may occur.|
| format | string | Yes  | Format string used to output logs in a specified format. It can contain several elements, where the parameter type and privacy identifier are mandatory.<br>Parameters labeled **{public}** are public data and are displayed in plaintext; parameters labeled **{private}** (default value) are private data and are filtered by **\<private>**.|
| args   | any[]  | No  | Variable-length parameter list corresponding to the format string. The number and type of parameters must map to the identifier in the format string.|

**Example**

This example is used to output a DEBUG log with the format string being **"%{public}s World %{private}d"**. The variable `%{public}s` is a plaintext string, and the variable `%{private}d` is a private integer.

```js
hilog.debug(0x0001, "testTag", "%{public}s World %{private}d", "hello", 3);
```

If **"hello"** is filled in **%{public}s** and **3** in **%{private}d**, the output log is as follows:

<!--RP3-->
```text
08-05 12:21:47.579  2695-2703  A00001/testTag  com.example.hilogDemo  D     hello World <private>
```
<!--RP3End-->

## hilog.info

info(domain: number, tag: string, format: string, ...args: any[]) : void

Prints INFO logs.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.HiviewDFX.HiLog

**Parameters**

| Name| Type  | Mandatory| Description                                                        |
| ------ | ------ | ---- | ------------------------------------------------------------ |
| domain | number | Yes  | Service domain of logs. The value ranges from **0x0** to **0xFFFF**. If the value exceeds the range, logs cannot be printed.<br>You can define the value as required. |
| tag    | string | Yes  | Log tag in the string format. You are advised to use this parameter to identify a particular service behavior or the class holding the ongoing method. A tag can contain a maximum of 31 bytes. If a tag exceeds this limit, it will be truncated. Chinese characters are not recommended because garbled characters or alignment problems may occur.|
| format | string | Yes  | Format string used to output logs in a specified format. It can contain several elements, where the parameter type and privacy identifier are mandatory.<br>Parameters labeled **{public}** are public data and are displayed in plaintext; parameters labeled **{private}** (default value) are private data and are filtered by **\<private>**.|
| args   | any[]  | No  | Variable-length parameter list corresponding to the format string. The number and type of parameters must map to the identifier in the format string.|

**Example**

This example is used to output an INFO log with the format string being **"%{public}s World %{private}d"**. The variable `%{public}s` is a plaintext string, and the variable `%{private}d` is a private integer.

```js
hilog.info(0x0001, "testTag", "%{public}s World %{private}d", "hello", 3);
```

If **"hello"** is filled in **%{public}s** and **3** in **%{private}d**, the output log is as follows:

<!--RP4-->
```text
08-05 12:21:47.579  2695-2703  A00001/testTag  com.example.hilogDemo  I     hello World <private>
```
<!--RP4End-->

## hilog.warn

warn(domain: number, tag: string, format: string, ...args: any[]) : void

Prints WARN logs.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.HiviewDFX.HiLog

**Parameters**

| Name| Type  | Mandatory| Description                                                        |
| ------ | ------ | ---- | ------------------------------------------------------------ |
| domain | number | Yes  | Service domain of logs. The value ranges from **0x0** to **0xFFFF**. If the value exceeds the range, logs cannot be printed.<br>You can define the value as required. |
| tag    | string | Yes  | Log tag in the string format. You are advised to use this parameter to identify a particular service behavior or the class holding the ongoing method. A tag can contain a maximum of 31 bytes. If a tag exceeds this limit, it will be truncated. Chinese characters are not recommended because garbled characters or alignment problems may occur.|
| format | string | Yes  | Format string used to output logs in a specified format. It can contain several elements, where the parameter type and privacy identifier are mandatory.<br>Parameters labeled **{public}** are public data and are displayed in plaintext; parameters labeled **{private}** (default value) are private data and are filtered by **\<private>**.|
| args   | any[]  | No  | Variable-length parameter list corresponding to the format string. The number and type of parameters must map to the identifier in the format string.|

**Example**

This example is used to output a WARN log with the format string being **"%{public}s World %{private}d"**. The variable `%{public}s` is a plaintext string, and the variable `%{private}d` is a private integer.

```js
hilog.warn(0x0001, "testTag", "%{public}s World %{private}d", "hello", 3);
```

If **"hello"** is filled in **%{public}s** and **3** in **%{private}d**, the output log is as follows:

<!--RP5-->
```text
08-05 12:21:47.579  2695-2703  A00001/testTag  com.example.hilogDemo  W     hello World <private>
```
<!--RP5End-->

## hilog.error

error(domain: number, tag: string, format: string, ...args: any[]) : void

Prints ERROR logs.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.HiviewDFX.HiLog

**Parameters**

| Name| Type  | Mandatory| Description                                                        |
| ------ | ------ | ---- | ------------------------------------------------------------ |
| domain | number | Yes  | Service domain of logs. The value ranges from **0x0** to **0xFFFF**. If the value exceeds the range, logs cannot be printed.<br>You can define the value as required. |
| tag    | string | Yes  | Log tag in the string format. You are advised to use this parameter to identify a particular service behavior or the class holding the ongoing method. A tag can contain a maximum of 31 bytes. If a tag exceeds this limit, it will be truncated. Chinese characters are not recommended because garbled characters or alignment problems may occur.|
| format | string | Yes  | Format string used to output logs in a specified format. It can contain several elements, where the parameter type and privacy identifier are mandatory.<br>Parameters labeled **{public}** are public data and are displayed in plaintext; parameters labeled **{private}** (default value) are private data and are filtered by **\<private>**.|
| args   | any[]  | No  | Variable-length parameter list corresponding to the format string. The number and type of parameters must map to the identifier in the format string.|

**Example**

This example is used to output an ERROR log with the format string being **"%{public}s World %{private}d"**. The variable `%{public}s` is a plaintext string, and the variable `%{private}d` is a private integer.

```js
hilog.error(0x0001, "testTag", "%{public}s World %{private}d", "hello", 3);
```

If **"hello"** is filled in **%{public}s** and **3** in **%{private}d**, the output log is as follows:

<!--RP6-->
```text
08-05 12:21:47.579  2695-2703  A00001/testTag  com.example.hilogDemo  E     hello World <private>
```
<!--RP6End-->

## hilog.fatal

fatal(domain: number, tag: string, format: string, ...args: any[]) : void

Prints FATAL logs.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.HiviewDFX.HiLog

**Parameters**

| Name| Type  | Mandatory| Description                                                        |
| ------ | ------ | ---- | ------------------------------------------------------------ |
| domain | number | Yes  | Service domain of logs. The value ranges from **0x0** to **0xFFFF**. If the value exceeds the range, logs cannot be printed.<br>You can define the value as required. |
| tag    | string | Yes  | Log tag in the string format. You are advised to use this parameter to identify a particular service behavior or the class holding the ongoing method. A tag can contain a maximum of 31 bytes. If a tag exceeds this limit, it will be truncated. Chinese characters are not recommended because garbled characters or alignment problems may occur.|
| format | string | Yes  | Format string used to output logs in a specified format. It can contain several elements, where the parameter type and privacy identifier are mandatory.<br>Parameters labeled **{public}** are public data and are displayed in plaintext; parameters labeled **{private}** (default value) are private data and are filtered by **\<private>**.|
| args   | any[]  | No  | Variable-length parameter list corresponding to the format string. The number and type of parameters must map to the identifier in the format string.|

**Example**

This example is used to output a FATAL log with the format string being **"%{public}s World %{private}d"**. The variable `%{public}s` is a plaintext string, and the variable `%{private}d` is a private integer.

```js
hilog.fatal(0x0001, "testTag", "%{public}s World %{private}d", "hello", 3);
```

If **"hello"** is filled in **%{public}s** and **3** in **%{private}d**, the output log is as follows:

<!--RP7-->
```text
08-05 12:21:47.579  2695-2703  A00001/testTag  com.example.hilogDemo  F     hello World <private>
```
<!--RP7End-->

## hilog.setMinLogLevel<sup>15+</sup>

setMinLogLevel(level: LogLevel): void

Sets the minimum log level.

> **NOTE**
>
> If the set log level is lower than the [global log level](../../dfx/hilog.md#displaying-and-setting-log-levels), the setting does not take effect.
>
> This function does not take effect for debug applications.

**Atomic service API**: This API can be used in atomic services since API version 15.

**System capability**: SystemCapability.HiviewDFX.HiLog

**Parameters**

| Name| Type                 | Mandatory| Description                                                        |
| ------ | --------------------- | ---- | ------------------------------------------------------------ |
| level  | [LogLevel](#loglevel) | Yes  | Log level.                                                  |

**Example**

The following example prints five HiLog logs of different levels and calls the **setMinLogLevel** API twice when the global log level is **INFO**:

```js
hilog.info(0x0001, "testTag", 'this is an info level log, id: %{public}d', 1);
hilog.setMinLogLevel(hilog.LogLevel.WARN);
hilog.info(0x0001, "testTag", 'this is an info level log, id: %{public}d', 2);
hilog.error(0x0001, 'testTag', 'this is an error level log, id: %{public}d', 3);
hilog.setMinLogLevel(hilog.LogLevel.DEBUG);
hilog.debug(0x0001, "testTag", 'this is a debug level log, id: %{public}d', 4);
hilog.info(0x0001, "testTag", 'this is an info level log, id: %{public}d', 5);
```

The first log is printed properly because the global log level is **INFO**.

After the minimum log level of the process is set to **WARN**, the second log does not meet the log level and fails to be printed. The third log is printed properly.

After the minimum log level of the process is set to **DEBUG**, the fourth log does not meet the global log level and fails to be printed. The fifth log is printed.

<!--RP1-->
The log result is as follows:
```text
08-07 23:50:01.532   13694-13694   A00001/testTag                  com.example.hilogDemo  I     this is an info level log, id: 1
08-07 23:50:01.532   13694-13694   A00001/testTag                  com.example.hilogDemo  E     this is an error level log, id: 3
08-07 23:50:01.532   13694-13694   A00001/testTag                  com.example.hilogDemo  I     this is an info level log, id: 5
```
<!--RP1End-->

## hilog.setLogLevel<sup>21+</sup>

setLogLevel(level: LogLevel, prefer: PreferStrategy): void

Sets the minimum log level of the current application process.

You can configure different preference strategies using the **prefer** parameter. The **PREFER_CLOSE_LOG** strategy has the same effect as the **setMinLogLevel()** function.

> **NOTE**
>
> This function does not take effect for debug applications.

**Atomic service API**: This API can be used in atomic services since API version 21.

**System capability**: SystemCapability.HiviewDFX.HiLog

**Parameters**

| Name| Type                 | Mandatory| Description                                                        |
| ------ | --------------------- | ---- | ------------------------------------------------------------ |
| level  | [LogLevel](#loglevel) | Yes  | Log level.                                                  |
| prefer  | [PreferStrategy](#preferstrategy21) | Yes  | Preference strategy.                                                  |

## PreferStrategy<sup>21+</sup>

Enumerates the preference strategies.

**Atomic service API**: This API can be used in atomic services since API version 21.

**System capability**: SystemCapability.HiviewDFX.HiLog

| Name |   Value  | Description                                                        |
| ------ | --------------------- | ------------------------------------------------------------ |
| UNSET_LOGLEVEL | 0 | The setting is cleared. The system-controlled minimum log level takes effect.|
| PREFER_CLOSE_LOG | 1 | The larger value of the new log level and the system-controlled minimum log level takes effect.|
| PREFER_OPEN_LOG | 2 | The smaller value of the new log level and the system-controlled minimum log level takes effect.|

**Example**

The following example describes how to print five HiLog logs of different levels and call the **setLogLevel** API twice when the global log level is **INFO**:

```js
hilog.info(0x0001, "testTag", 'this is an info level log, id: %{public}d', 1);
hilog.setLogLevel(hilog.LogLevel.WARN, hilog.PreferStrategy.PREFER_OPEN_LOG);
hilog.info(0x0001, "testTag", 'this is an info level log, id: %{public}d', 2);
hilog.error(0x0001, 'testTag', 'this is an error level log, id: %{public}d', 3);
hilog.setLogLevel(hilog.LogLevel.DEBUG, hilog.PreferStrategy.PREFER_CLOSE_LOG);
hilog.debug(0x0001, "testTag", 'this is a debug level log, id: %{public}d', 4);
hilog.info(0x0001, "testTag", 'this is an info level log, id: %{public}d', 5);
```

The first log is printed properly because the global log level is **INFO**.

When the minimum log level of the process is set to **WARN** and the **PREFER_OPEN_LOG** is strategy selected, the actual minimum log level is **INFO**. Therefore, the second and third logs can be printed properly.

When the minimum log level of the process is set to **DEBUG** and the **PREFER_CLOSE_LOG** strategy is selected (equivalent to **hilog.setMinLogLevel(hilog.LogLevel.DEBUG)**), the fourth log cannot be printed because the global log level is **INFO**. The fifth log can be printed.

<!--RP2-->
The log result is as follows:
```text
08-07 23:50:01.532   13694-13694   A00001/testTag                  com.example.hilogDemo  I     this is an info level log, id: 1
08-07 23:50:01.532   13694-13694   A00001/testTag                  com.example.hilogDemo  I     this is an info level log, id: 2
08-07 23:50:01.532   13694-13694   A00001/testTag                  com.example.hilogDemo  E     this is an error level log, id: 3
08-07 23:50:01.532   13694-13694   A00001/testTag                  com.example.hilogDemo  I     this is an info level log, id: 5
```
<!--RP2End-->


## Parameter Format

Parameters in the log are printed in the following format:

%{[private flag]}specifier

|  Private Flag| Description|
| ------------ | ---- |
|      Unspecified     | The default value is **private**, indicating that parameters in plaintext are not printed.|
|  private     | Prints private parameters.|
|  public      | Prints parameters in plaintext.|

| Specifier| Description| Example|
| ------------ | ---- | ---- |
|      d/i      | Prints logs of the **number** and **bigint** types.| 123 |
|   s     | Prints logs of the **string undefined bool** and **null** types.| "123" |
| o/O | Prints logs of the **object**, **undefined**, and **null** types.<br>This specifier is supported since API version 20.| { 'name': "Jack", 'age': 22 } |

**Example**
```js
let testObj: Record<string, string | number> = {
    'name': "Jack",
    'age': 22
}
let isBol = true;
let bigNum = BigInt(1234567890123456789);
hilog.info(0x0001, "jsHilogTest", "print object: %{public}s", JSON.stringify(testObj));
hilog.info(0x0001, "jsHilogTest", "print object: %{public}o", testObj);
hilog.info(0x0001, "jsHilogTest", "private flag: %{private}s %s, print null: %{public}s", "hello", "world", null);
hilog.info(0x0001, "jsHilogTest", "print undefined: %{public}s", undefined);
hilog.info(0x0001, "jsHilogTest", "print number: %{public}d %{public}i", 123, 456);
hilog.info(0x0001, "jsHilogTest", "print bigNum: %{public}d %{public}i", bigNum, bigNum);
hilog.info(0x0001, "jsHilogTest", "print boolean: %{public}s", isBol);
```

**Log result**:
<!--RP8-->
```text
08-09 13:26:29.094  2266-2266  A00001/jsHilogTest  com.example.hilogDemo  I  print object: {"name":"Jack","age":22}
08-09 13:26:29.094  2266-2266  A00001/jsHilogTest  com.example.hilogDemo  I  print object: {"name":"Jack","age":22}
08-09 13:26:29.094  2266-2266  A00001/jsHilogTest  com.example.hilogDemo  I  private flag: <private> <private>, print null: null
08-09 13:26:29.094  2266-2266  A00001/jsHilogTest  com.example.hilogDemo  I  print undefined: undefined
08-09 13:26:29.094  2266-2266  A00001/jsHilogTest  com.example.hilogDemo  I  print number: 123 456
08-09 13:26:29.095  2266-2266  A00001/jsHilogTest  com.example.hilogDemo  I  print bigNum: 1234567890123456768 1234567890123456768
08-09 13:26:29.095  2266-2266  A00001/jsHilogTest  com.example.hilogDemo  I  print boolean: true
```
<!--RP8End-->


## OutputType

Enumerates the output types of HiLog. **DEFAULT** and **CONSOLE_ONLY** are used when logs are output only to the console. **PRIVATE_SANDBOX_ONLY** is used for storing private logs. **SHARE_SANDBOX_ONLY** is used when logs need to be collected on the cloud. **PRIVATE_SANDBOX_WITH_CONSOLE** and **SHARE_SANDBOX_WITH_CONSOLE** are used when logs need to be output to the console and stored in the sandbox.

**Since**: 26.0.0

**Atomic service API**: This API can be used in atomic services since API version 26.

**System capability**: SystemCapability.HiviewDFX.HiLog

| Name |   Value  | Description                                                        |
| ------ | --------------------- | ------------------------------------------------------------ |
| DEFAULT | 0 | Default output type, which is equivalent to **CONSOLE_ONLY**. HiLog outputs logs only to the console.|
| CONSOLE_ONLY | 0 | HiLog outputs logs only to the console, which is equivalent to **DEFAULT**.|
| PRIVATE_SANDBOX_ONLY | 1 | HiLog outputs logs to the private sandbox of the application. This path can be accessed only by the application itself.|
| SHARE_SANDBOX_ONLY | 2 | HiLog outputs logs to the public sandbox of the application. This path can be accessed by both the application and the system.|
| PRIVATE_SANDBOX_WITH_CONSOLE | 3 | Both **CONSOLE_ONLY** and **PRIVATE_SANDBOX_ONLY** are enabled.|
| SHARE_SANDBOX_WITH_CONSOLE | 4 | Both **CONSOLE_ONLY** and **SHARE_SANDBOX_ONLY** are enabled.|

## hilog.setOutputType

setOutputType(type: OutputType): OutputType

Sets the output type of HiLog.

**Since**: 26.0.0

**Atomic service API**: This API can be used in atomic services since API version 26.

**System capability**: SystemCapability.HiviewDFX.HiLog

**Parameters**

| Name| Type                 | Mandatory| Description                                                        |
| ------ | --------------------- | ---- | ------------------------------------------------------------ |
| type  | [OutputType](#outputtype) | Yes  | Output type of HiLog.                                                  |

**Return value**

| Type   | Description                                                        |
| ------- | ------------------------------------------------------------ |
| [OutputType](#outputtype) | The previously set output type.|

**Example**
```js
hilog.setOutputType(hilog.OutputType.SHARE_SANDBOX_ONLY);
hilog.info(0x0001, "testTag", 'sandbox log to share sandbox only');
hilog.flush();
```

**Log result**:

Sandbox log output.
```text
05-15 16:57:04.238 40518 40518 I A00001/testTag: sandbox log to share sandbox only
```

## hilog.setOutputTypeByDomainID

setOutputTypeByDomainID(type: OutputType, domainIDs: Array&lt;number&gt;, isExclude: boolean): OutputType

Sets the output type of HiLog and configures the domain ID list to be output. You can choose to output only the domain IDs in the list or not.

**Since**: 26.0.0

**Atomic service API**: This API can be used in atomic services since API version 26.

**System capability**: SystemCapability.HiviewDFX.HiLog

**Parameters**

| Name| Type                 | Mandatory| Description                                                        |
| ------ | --------------------- | ---- | ------------------------------------------------------------ |
| type  | [OutputType](#outputtype) | Yes  | Output type of HiLog.                                                  |
| domainIDs  | Array&lt;number&gt; | Yes  | Domain ID list. The value range of each domain ID is 0x0000 to 0xFFFF. This parameter is valid only for application domains.                                                  |
| isExclude  | boolean | Yes  | Whether domain IDs take effect for the output type.<br>The value **true** indicates that the domain IDs in the list are excluded, and the configuration takes effect only for domains that are not in the list, and **false** indicates the opposite.|

**Return value**

| Type   | Description                                                        |
| ------- | ------------------------------------------------------------ |
| [OutputType](#outputtype) | The previously set output type.|

**Example**

```js
hilog.setOutputTypeByDomainID(hilog.OutputType.SHARE_SANDBOX_ONLY, [0x0001, 0x0002, 0x0003], false);
hilog.info(0x0001, "testTag", 'sandbox log to share sandbox only');
hilog.info(0x0002, "testTag", 'sandbox log to share sandbox only');
hilog.info(0x0003, "testTag", 'sandbox log to share sandbox only');
hilog.info(0x0004, "testTag", 'sandbox log to share sandbox only');
hilog.flush();
```

**Log result**:

Sandbox log output. The logs of domain **0x0004** are not printed.
```text
05-15 16:57:04.238 40518 40518 I A00001/testTag: sandbox log to share sandbox only
05-15 16:57:04.238 40518 40518 I A00002/testTag: sandbox log to share sandbox only
05-15 16:57:04.238 40518 40518 I A00003/testTag: sandbox log to share sandbox only
```

## hilog.getOutputType

getOutputType(): OutputType

Obtains the output type of HiLog.

**Since**: 26.0.0

**Atomic service API**: This API can be used in atomic services since API version 26.

**System capability**: SystemCapability.HiviewDFX.HiLog

**Return value**

| Type   | Description                                                        |
| ------- | ------------------------------------------------------------ |
| [OutputType](#outputtype) | Returns the output type of HiLog.|

**Example**
```js
hilog.setOutputType(hilog.OutputType.SHARE_SANDBOX_WITH_CONSOLE);
let last = hilog.getOutputType();
hilog.info(0x0001, "testTag", 'last output type:%{public}d', last);
```

**Log result**:

Console output.
```text
05-15 16:57:04.238  40518-40518  A00001/testTag  com.example.hilogDemo  I  last output type:4
```

## hilog.getOutputDir

getOutputDir(): string

Obtains the path of the HiLog logs in the sandbox. If the output type of HiLog is **DEFAULT**, an empty string is returned.

**Since**: 26.0.0

**Atomic service API**: This API can be used in atomic services since API version 26.

**System capability**: SystemCapability.HiviewDFX.HiLog

**Return value**

| Type   | Description                                                        |
| ------- | ------------------------------------------------------------ |
| string | Sandbox path of the HiLog logs.|

**Example**
```js
hilog.setOutputType(hilog.OutputType.SHARE_SANDBOX_WITH_CONSOLE);
let dir = hilog.getOutputDir();
hilog.info(0x0001, "testTag", 'sandbox output dir:%{public}s', dir);
```

**Log result**:

Console output.
```text
05-15 16:57:04.238  40518-40518  A00001/testTag  com.example.hilogDemo  I  sandbox output dir:/data/storage/el2/log/hiapplog/
```

## hilog.clean

clean(): void

Deletes all HiLog logs from the sandbox.

**Since**: 26.0.0

**Atomic service API**: This API can be used in atomic services since API version 26.

**System capability**: SystemCapability.HiviewDFX.HiLog

**Example**
```js
hilog.clean();
```

## hilog.flush

flush(): void

Refreshes HiLog logs in the sandbox.

**Since**: 26.0.0

**Atomic service API**: This API can be used in atomic services since API version 26.

**System capability**: SystemCapability.HiviewDFX.HiLog

**Example**
```js
hilog.flush();
```

## hilog.getLogFile

getLogFile(latestSeconds: number): Array&lt;string&gt;

Obtains the HiLog sandbox log files that have been modified within the specified number of seconds.

**Since**: 26.0.0

**Atomic service API**: This API can be used in atomic services since API version 26.

**System capability**: SystemCapability.HiviewDFX.HiLog

**Parameters**

| Name| Type                 | Mandatory| Description                                                        |
| ------ | --------------------- | ---- | ------------------------------------------------------------ |
| latestSeconds  | number | Yes  | Interval from the current time, in seconds.<br>If the input value is less than 0, the value is invalid and the return value is empty.            |

**Return value**

| Type   | Description                                                        |
| ------- | ------------------------------------------------------------ |
| Array&lt;string&gt; | List of sandbox files that have been written in a specified period.|

**Example**

Obtain the files that have been modified within 5 minutes.
```js
hilog.setOutputType(hilog.OutputType.SHARE_SANDBOX_WITH_CONSOLE);
hilog.info(0x0001, "testTag", 'sandbox log to share sandbox with console');
hilog.flush();
let logs = hilog.getLogFile(300);
hilog.info(0x0001, "testTag", 'sandbox log files:%{public}s', logs.toString());
```

**Log result**:

Sandbox log output.
```text
05-15 16:57:04.238 40518 40518 I A00001/testTag: sandbox log files:hiapplog.40518.001.20260515-165602.log
```
