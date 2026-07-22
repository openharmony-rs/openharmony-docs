# move（系统接口）

## 导入模块

```TypeScript
import { logLibrary } from '@kit.PerformanceAnalysisKit';
```

## move

```TypeScript
function move(logType: string, logName: string, dest: string): Promise<void>
```

移动指定日志类型的指定文件到目标应用目录下。使用Promise回调。

**起始版本：** 10

**需要权限：** ohos.permission.WRITE_HIVIEW_SYSTEM

<!--Device-logLibrary-function move(logType: string, logName: string, dest: string): Promise<void>--><!--Device-logLibrary-function move(logType: string, logName: string, dest: string): Promise<void>-End-->

**系统能力：** SystemCapability.HiviewDFX.Hiview.LogLibrary

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| logType | string | 是 | 日志类型字符串，例如"FAULTLOG", "BETACLUB", "REMOTELOG"等。 |
| logName | string | 是 | 日志文件名称。 |
| dest | string | 是 | 目标目录，需填入相对目录名称。传入dest字串后，日志文件将保存到应用缓存路径下的"hiview/*dest*"文件夹，即"../cache/hiview/*dest*"。可填入多层目录。<br>如果传入空字串，将保存到根目录下，即应用缓存路径下的hiview文件夹。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise实例，可以在其then()、catch()方法中分别对移动成功、移动异常的回调进行处理。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission denied, non-system app called system api |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Invalid argument. Possible causes:<br>1. Mandatory parameters are left unspecified.<br>2. Incorrect parameter types.<br>3. Parameter verification failed. |
| [21300001](../errorcode-loglibrary-sys.md#21300001-指定文件不存在) | Source file does not exists |

**示例：**

```TypeScript
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


## move

```TypeScript
function move(logType: string, logName: string, dest: string, callback: AsyncCallback<void>): void
```

移动指定日志类型的指定文件到目标应用目录下。使用callback回调。

**起始版本：** 10

**需要权限：** ohos.permission.WRITE_HIVIEW_SYSTEM

<!--Device-logLibrary-function move(logType: string, logName: string, dest: string, callback: AsyncCallback<void>): void--><!--Device-logLibrary-function move(logType: string, logName: string, dest: string, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.HiviewDFX.Hiview.LogLibrary

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| logType | string | 是 | 日志类型字符串，例如“HILOG”, "FAULTLOG", "BETACLUB", "REMOTELOG"等。 |
| logName | string | 是 | 日志文件名称。 |
| dest | string | 是 | 目标目录，需填入相对目录名称。传入dest字串后，日志文件将保存到应用缓存路径下的"hiview/*dest*"文件夹，即"../cache/hiview/*dest*"。可填入多层目录。<br>如果传入空字串，将保存到根目录下，即应用缓存路径下的hiview文件夹。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | 回调函数，可以在回调函数中处理接口返回值。0表示移动成功，其它值表示移动失败。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission denied, non-system app called system api |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Invalid argument. Possible causes:<br>1. Mandatory parameters are left unspecified.<br>2. Incorrect parameter types.<br>3. Parameter verification failed. |
| [21300001](../errorcode-loglibrary-sys.md#21300001-指定文件不存在) | Source file does not exists |

**示例：**

```TypeScript
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

