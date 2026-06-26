# @ohos.logLibrary (维测日志获取)(系统接口)

<!--Kit: Performance Analysis Kit-->
<!--Subsystem: HiviewDFX-->
<!--Owner: @BruceZong-->
<!--Designer: @tangyyan-->
<!--Tester: @gcw_KuLfPSbe-->
<!--Adviser: @jinqiuheng-->

本模块提供list、copy、move、remove等接口，支持查询、拷贝、移动和删除系统维测日志文件。

> **说明：**
>
> - 本模块同时支持ArkTS-Dyn、ArkTS-Sta。
> - 本模块首批接口从API version 10开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。
> - 本模块为系统接口。

## 导入模块

```ts
import { logLibrary } from '@kit.PerformanceAnalysisKit';
```

## LogEntry

日志文件对象接口。

**系统能力：** SystemCapability.HiviewDFX.Hiview.LogLibrary

**ArkTS-Dyn起始版本：** 10

**ArkTS-Sta起始版本：** 23

| 名称 | 类型 | 只读 | 可选 | 说明 |
| -------- | -------- | -------- | -------- | -------- |
| name | string | 否 | 否 | 文件名称。 |
| mtime | ArkTS-Dyn: number<br>ArkTS-Sta: long | 否 | 否  | 上次修改该文件的时间，表示距1970年1月1日0时0分0秒的秒数。 |
| size | ArkTS-Dyn: number<br>ArkTS-Sta: long | 否 | 否  | 文件大小，以字节为单位。 |

## logLibrary.list

list(logType: string): LogEntry[]

以同步方法查询指定类型的日志文件列表，接收string类型的对象作为参数，返回指定类型日志的文件列表信息。

使用场景：应用在问题定位或日志分析时，需要获取特定类型的日志文件列表。获取后可用于copy、move、remove等接口进行日志操作，如日志归档、清理等。

**需要权限：** ohos.permission.READ_HIVIEW_SYSTEM

**系统能力：** SystemCapability.HiviewDFX.Hiview.LogLibrary

**ArkTS-Dyn起始版本：** 10

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名    | 类型                      | 必填 | 说明                                                         |
| --------- | ------------------------- | ---- | ------------------------------------------------------------ |
| logType | string | 是 | 日志类型字符串，取值范围：需为系统已注册的日志类型（如："HILOG", "FAULTLOG", "BETACLUB", "REMOTELOG"等）。传入不在范围内的值时返回错误码401。 |

**返回值：**

| 类型                | 说明                                                         |
| ------------------- | ------------------------------------------------------------ |
| [LogEntry](#logentry)[] | 日志文件对象的数组，包含指定类型的所有日志文件。每个LogEntry对象包含文件名name、修改时间mtime和文件大小size信息，可用于后续的拷贝、移动或删除等操作。 |

**错误码：**

以下错误码的详细介绍请参见[维测日志错误码](errorcode-loglibrary-sys.md)。

| 错误码ID | 错误信息 |
| ------- | ----------------------------------------------------------------- |
| 201 | Permission denied. |
| 202 | Permission denied, non-system app called system api. |
| 401 | Invalid argument. Possible causes:<br>1. Mandatory parameters are left unspecified.<br>2. Incorrect parameter types.<br>3. Parameter verification failed. |

**示例：**

ArkTS-Dyn示例：

```ts
import { logLibrary } from '@kit.PerformanceAnalysisKit';

try {
  let logFiles = logLibrary.list('HILOG');
  // do something here.
} catch (error) {
  console.error(`Failed to call logLibrary API. Code: ${error?.code}, message: ${error?.message}`);
}
```

ArkTS-Sta示例：

```ts
import { logLibrary } from '@kit.PerformanceAnalysisKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let logObj = logLibrary.list('HILOG');
  // do something here.
} catch (err: BusinessError) {
  console.error(`error code: ${err?.code}, error msg: ${err?.message}`);
}
```

## logLibrary.copy

copy(logType: string, logName: string, dest: string): Promise&lt;void&gt;

拷贝指定日志类型的指定文件到目标应用目录下。调用成功后，目标目录会有新的日志文件副本，原文件保持不变。使用Promise异步回调。

使用场景：应用在需要备份日志或上传日志到服务器前，可将日志文件拷贝到应用目录。

**需要权限：** ohos.permission.READ_HIVIEW_SYSTEM

**系统能力：** SystemCapability.HiviewDFX.Hiview.LogLibrary

**ArkTS-Dyn起始版本：** 10

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名    | 类型                    | 必填 | 说明 |
| --------- | ----------------------- | ---- | --------------- |
| logType | string | 是 | 日志类型字符串，取值范围：需为系统已注册的日志类型（如："HILOG", "FAULTLOG", "BETACLUB", "REMOTELOG"等）。传入不在范围内的值时返回错误码401。 |
| logName | string | 是   | 日志文件名称。需先通过logLibrary.list方法查询日志文件列表，从中选择需要操作的文件，使用LogEntry.name字段作为参数值。传入空字符串、不存在的文件名或无效文件名时返回错误码21300001。 |
| dest | string | 是   | 目标目录，需填入相对目录名称，只支持合法的目录名字符。传入dest字符串后，日志文件将保存到应用缓存路径下的"hiview/\<dest>"文件夹，即"../cache/hiview/\<dest>"。可填入多层目录。<br>如果传入空字符串，将保存到根目录下，即应用缓存路径下的hiview文件夹。传入无效目录名时返回错误码401。 |

**返回值：**

| 类型                | 说明                                                         |
| ------------------- | ------------------------------------------------------------ |
| Promise&lt;void&gt; | Promise对象，resolve时无返回值表示拷贝成功，reject时抛出BusinessError对象表示拷贝失败。 |

**错误码：**

以下错误码的详细介绍请参见[维测日志错误码](errorcode-loglibrary-sys.md)。

| 错误码ID | 错误信息 |
| -------- | ---------------------------------------------------------------- |
| 201 | Permission denied. |
| 202 | Permission denied, non-system app called system api. |
| 401 | Invalid argument. Possible causes:<br>1. Mandatory parameters are left unspecified.<br>2. Incorrect parameter types.<br>3. Parameter verification failed. |
| 21300001 | Source file does not exists.  |

**示例：**

ArkTS-Dyn示例：

```ts
import { logLibrary } from '@kit.PerformanceAnalysisKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let logFiles = logLibrary.list('HILOG');
  if (logFiles.length > 0) {
    logLibrary.copy('HILOG', logFiles[0].name, ''
    ).then(
      (copyResult) => {
        // do something here.
      }
    ).catch(
      (err: BusinessError) => {
        // do something here.
      }
    )
  }
} catch (error) {
    console.error(`Failed to call logLibrary API. Code: ${error?.code}, message: ${error?.message}`);
}
```

ArkTS-Sta示例：

```ts
import { logLibrary } from '@kit.PerformanceAnalysisKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let logObj = logLibrary.list('HILOG');
  if (logObj.length > 0) {
    await logLibrary.copy('HILOG', logObj[0].name, '');
  }
} catch (err: BusinessError) {
  console.error(`error code: ${err?.code}, error msg: ${err?.message}`);
}
```

## logLibrary.copy

copy(logType: string, logName: string, dest: string, callback: AsyncCallback&lt;void&gt;): void

拷贝指定日志类型的指定文件到目标应用目录下。调用成功后，目标目录会有新的日志文件副本，原文件保持不变。使用callback异步回调。

使用场景：应用在需要备份日志或上传日志到服务器前，可将日志文件拷贝到应用目录。

**需要权限：** ohos.permission.READ_HIVIEW_SYSTEM

**系统能力：** SystemCapability.HiviewDFX.Hiview.LogLibrary

**ArkTS-Dyn起始版本：** 10

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名    | 类型                      | 必填 | 说明                                                         |
| --------- | ------------------------- | ---- | ------------------------------------------------------------ |
| logType | string | 是 | 日志类型字符串，取值范围：需为系统已注册的日志类型（如："HILOG", "FAULTLOG", "BETACLUB", "REMOTELOG"等）。传入不在范围内的值时返回错误码401。 |
| logName | string | 是   | 日志文件名称。需先通过logLibrary.list方法查询日志文件列表，从中选择需要操作的文件，使用LogEntry.name字段作为参数值。传入空字符串、不存在的文件名或无效文件名时返回错误码21300001。 |
| dest | string | 是   | 目标目录，需填入相对目录名称，只支持合法的目录名字符。传入dest字符串后，日志文件将保存到应用缓存路径下的"hiview/\<dest>"文件夹，即"../cache/hiview/\<dest>"。可填入多层目录。<br>如果传入空字符串，将保存到根目录下，即应用缓存路径下的hiview文件夹。传入无效目录名时返回错误码401。 |
| callback  | AsyncCallback&lt;void&gt; | 是 | 回调函数，用于接收操作结果。回调参数：第一个参数为错误对象（BusinessError类型，成功时为null）。成功时err为null，失败时通过err.code获取错误码，err.message获取错误描述。错误码含义参考下方错误码表格。 |

**错误码：**

以下错误码的详细介绍请参见[维测日志错误码](errorcode-loglibrary-sys.md)。

| 错误码ID | 错误信息 |
| ------- | ----------------------------------------------------------------- |
| 201 | Permission denied. |
| 202 | Permission denied, non-system app called system api. |
| 401 | Invalid argument. Possible causes:<br>1. Mandatory parameters are left unspecified.<br>2. Incorrect parameter types.<br>3. Parameter verification failed. |
| 21300001 | Source file does not exists.  |

**示例：**

ArkTS-Dyn示例：

```ts
import { logLibrary } from '@kit.PerformanceAnalysisKit';

try {
  let logFiles = logLibrary.list('HILOG');
  if (logFiles.length > 0) {
    logLibrary.copy('HILOG', logFiles[0].name, 'dir1', (error, copyResult) => {
      if (error) {
        console.error(`Failed to copy log file. Code: ${error.code}, message: ${error.message}`);
      } else {
        // copy success.
      }
    });
  }
} catch (error) {
    console.error(`Failed to call logLibrary API. Code: ${error?.code}, message: ${error?.message}`);
}
```

ArkTS-Sta示例：

```ts
import { logLibrary } from '@kit.PerformanceAnalysisKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let logObj = logLibrary.list('HILOG');
  if (logObj.length > 0) {
    logLibrary.copy('HILOG', logObj[0].name, 'dir1', (err: BusinessError | null) => {
      // copy结果
    });
  }
} catch (err: BusinessError) {
  console.error(`error code: ${err?.code}, error msg: ${err?.message}`);
}
```

## logLibrary.move

move(logType: string, logName: string, dest: string): Promise&lt;void&gt;

移动指定日志类型的指定文件到目标应用目录下。调用成功后，原文件会被删除，目标目录会有新的日志文件。使用Promise异步回调。

使用场景：应用在需要归档日志或整理日志时，可将日志文件移动到指定目录。

**需要权限：** ohos.permission.WRITE_HIVIEW_SYSTEM

**系统能力：** SystemCapability.HiviewDFX.Hiview.LogLibrary

**ArkTS-Dyn起始版本：** 10

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名    | 类型                    | 必填 | 说明 |
| --------- | ----------------------- | ---- | --------------- |
| logType | string | 是 | 日志类型字符串，取值范围：需为系统已注册的日志类型（如："HILOG", "FAULTLOG", "BETACLUB", "REMOTELOG"等）。传入不在范围内的值时返回错误码401。 |
| logName | string | 是   | 日志文件名称。需先通过logLibrary.list方法查询日志文件列表，从中选择需要操作的文件，使用LogEntry.name字段作为参数值。传入空字符串、不存在的文件名或无效文件名时返回错误码21300001。 |
| dest | string | 是   | 目标目录，需填入相对目录名称，只支持合法的目录名字符。传入dest字符串后，日志文件将保存到应用缓存路径下的"hiview/\<dest>"文件夹，即"../cache/hiview/\<dest>"。可填入多层目录。<br>如果传入空字符串，将保存到根目录下，即应用缓存路径下的hiview文件夹。传入无效目录名时返回错误码401。 |

**返回值：**

| 类型                | 说明                                                         |
| ------------------- | ------------------------------------------------------------ |
| Promise&lt;void&gt; | Promise对象，resolve时无返回值表示移动成功，reject时抛出BusinessError对象表示移动失败。 |

**错误码：**

以下错误码的详细介绍请参见[维测日志错误码](errorcode-loglibrary-sys.md)。

| 错误码ID | 错误信息 |
| -------- | ---------------------------------------------------------------- |
| 201 | Permission denied. |
| 202 | Permission denied, non-system app called system api. |
| 401 | Invalid argument. Possible causes:<br>1. Mandatory parameters are left unspecified.<br>2. Incorrect parameter types.<br>3. Parameter verification failed. |
| 21300001 | Source file does not exists.  |

**示例：**

ArkTS-Dyn示例：

```ts
import { logLibrary } from '@kit.PerformanceAnalysisKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let logFiles = logLibrary.list('FAULTLOG');
  if (logFiles.length > 0) {
    logLibrary.move('FAULTLOG', logFiles[0].name, ''
    ).then(
      (val) => {
        // do something here.
      }
    ).catch(
      (err: BusinessError) => {
        // do something here.
      }
    )
  }
} catch (error) {
    console.error(`Failed to call logLibrary API. Code: ${error?.code}, message: ${error?.message}`);
}
```

ArkTS-Sta示例：

```ts
import { logLibrary } from '@kit.PerformanceAnalysisKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let logObj = logLibrary.list('FAULTLOG');
  if (logObj.length > 0) {
    await logLibrary.move('FAULTLOG', logObj[0].name, '');
  }
} catch (err: BusinessError) {
  console.error(`error code: ${err?.code}, error msg: ${err?.message}`);
}
```

## logLibrary.move

move(logType: string, logName: string, dest: string, callback: AsyncCallback&lt;void&gt;): void

移动指定日志类型的指定文件到目标应用目录下。调用成功后，原文件会被删除，目标目录会有新的日志文件。使用callback异步回调。

使用场景：应用在需要归档日志或整理日志时，可将日志文件移动到指定目录。

**需要权限：** ohos.permission.WRITE_HIVIEW_SYSTEM

**系统能力：** SystemCapability.HiviewDFX.Hiview.LogLibrary

**ArkTS-Dyn起始版本：** 10

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名    | 类型                      | 必填 | 说明                                                         |
| --------- | ------------------------- | ---- | ------------------------------------------------------------ |
| logType | string | 是 | 日志类型字符串，取值范围：需为系统已注册的日志类型（如："HILOG", "FAULTLOG", "BETACLUB", "REMOTELOG"等）。传入不在范围内的值时返回错误码401。 |
| logName | string | 是   | 日志文件名称。需先通过logLibrary.list方法查询日志文件列表，从中选择需要操作的文件，使用LogEntry.name字段作为参数值。传入空字符串、不存在的文件名或无效文件名时返回错误码21300001。 |
| dest | string | 是   | 目标目录，需填入相对目录名称，只支持合法的目录名字符。传入dest字符串后，日志文件将保存到应用缓存路径下的"hiview/\<dest>"文件夹，即"../cache/hiview/\<dest>"。可填入多层目录。<br>如果传入空字符串，将保存到根目录下，即应用缓存路径下的hiview文件夹。传入无效目录名时返回错误码401。 |
| callback  | AsyncCallback&lt;void&gt; | 是 | 回调函数，用于接收操作结果。回调参数：第一个参数为错误对象（BusinessError类型，成功时为null）。成功时err为null，失败时通过err.code获取错误码，err.message获取错误描述。错误码含义参考下方错误码表格。 |

**错误码：**

以下错误码的详细介绍请参见[维测日志错误码](errorcode-loglibrary-sys.md)。

| 错误码ID | 错误信息 |
| ------- | ----------------------------------------------------------------- |
| 201 | Permission denied. |
| 202 | Permission denied, non-system app called system api. |
| 401 | Invalid argument. Possible causes:<br>1. Mandatory parameters are left unspecified.<br>2. Incorrect parameter types.<br>3. Parameter verification failed. |
| 21300001 | Source file does not exists.  |

**示例：**

ArkTS-Dyn示例：

```ts
import { logLibrary } from '@kit.PerformanceAnalysisKit';

try {
  let logFiles = logLibrary.list('FAULTLOG');
  if (logFiles.length > 0) {
    logLibrary.move('FAULTLOG', logFiles[0].name, 'dir1/dir2', (error, moveResult) => {
      if (error) {
        console.error(`Failed to move log file. Code: ${error.code}, message: ${error.message}`);
      } else {
        // move success.
      }
    });
  }
} catch (error) {
    console.error(`Failed to call logLibrary API. Code: ${error?.code}, message: ${error?.message}`);
}
```

ArkTS-Sta示例：

```ts
import { logLibrary } from '@kit.PerformanceAnalysisKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let logObj = logLibrary.list('FAULTLOG');
  if (logObj.length > 0) {
    logLibrary.move('FAULTLOG', logObj[0].name, 'dir1/dir2', (err: BusinessError | null) => {
      // move结果
    });
  }
} catch (err: BusinessError) {
  console.error(`error code: ${err?.code}, error msg: ${err?.message}`);
}
```

## logLibrary.remove

remove(logType: string, logName: string): void

以同步方法删除指定日志类型的指定文件。

使用场景：应用在需要清理过期日志或释放存储空间时，可删除不再需要的日志文件。

**需要权限：** ohos.permission.WRITE_HIVIEW_SYSTEM

**系统能力：** SystemCapability.HiviewDFX.Hiview.LogLibrary

**ArkTS-Dyn起始版本：** 10

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名    | 类型                      | 必填 | 说明                                                         |
| --------- | ------------------------- | ---- | ------------------------------------------------------------ |
| logType | string | 是 | 日志类型字符串，取值范围：需为系统已注册的日志类型（如："HILOG", "FAULTLOG", "BETACLUB", "REMOTELOG"等）。传入不在范围内的值时返回错误码401。 |
| logName | string | 是   | 日志文件名称。需先通过logLibrary.list方法查询日志文件列表，从中选择需要操作的文件，使用LogEntry.name字段作为参数值。传入空字符串、不存在的文件名或无效文件名时返回错误码21300001。 |

**错误码：**

以下错误码的详细介绍请参见[维测日志错误码](errorcode-loglibrary-sys.md)。

| 错误码ID | 错误信息 |
| ------- | ----------------------------------------------------------------- |
| 201 | Permission denied. |
| 202 | Permission denied, non-system app called system api. |
| 401 | Invalid argument. Possible causes:<br>1. Mandatory parameters are left unspecified.<br>2. Incorrect parameter types.<br>3. Parameter verification failed. |
| 21300001 | Source file does not exists.  |

**示例：**

ArkTS-Dyn示例：

```ts
import { logLibrary } from '@kit.PerformanceAnalysisKit';

try {
  let logFiles = logLibrary.list('FAULTLOG');
  if (logFiles.length > 0) {
    logLibrary.remove('FAULTLOG', logFiles[0].name);
  }
} catch (error) {
  console.error(`Failed to call logLibrary API. Code: ${error?.code}, message: ${error?.message}`);
}
```

ArkTS-Sta示例：

```ts
import { logLibrary } from '@kit.PerformanceAnalysisKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let logObj = logLibrary.list('FAULTLOG');
  if (logObj.length > 0) {
    logLibrary.remove('FAULTLOG', logObj[0].name);
  }
} catch (err: BusinessError) {
  console.error(`error code: ${err?.code}, error msg: ${err?.message}`);
}
```
