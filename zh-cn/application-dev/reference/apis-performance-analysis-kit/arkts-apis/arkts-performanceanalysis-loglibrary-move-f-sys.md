# move（系统接口）

## move

```TypeScript
function move(logType: string, logName: string, dest: string): Promise<void>
```

移动指定日志类型的指定文件到目标应用目录下。使用Promise回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**需要权限：** ohos.permission.WRITE_HIVIEW_SYSTEM

<!--Device-logLibrary-function move(logType: string, logName: string, dest: string): Promise<void>--><!--Device-logLibrary-function move(logType: string, logName: string, dest: string): Promise<void>-End-->

**系统能力：** SystemCapability.HiviewDFX.Hiview.LogLibrary

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| logType | string | 是 | 日志类型字符串，例如"FAULTLOG", "BETACLUB", "REMOTELOG"等。 |
| logName | string | 是 | 日志文件名称。 |
| dest | string | 是 | 目标目录，需填入相对目录名称。传入dest字串后，日志文件将保存到应用缓存路径下的"hiview/*dest*"文件夹，即"../cache/hiview/*dest*"。可填入多 层目录。 &lt;br&gt;如果传入空字串，将保存到根目录下，即应用缓存路径下的hiview文件夹。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise实例，可以在其then()、catch()方法中分别对移动成功、移动异常的回调进行处理。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Invalid argument. Possible causes: &lt;br&gt;1. Mandatory parameters are left unspecified. &lt;br&gt;2. Incorrect parameter types. &lt;br&gt;3. Parameter verification failed. |
| [21300001](../errorcode-loglibrary-sys.md#21300001-指定文件不存在) | Source file does not exists |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission denied, non-system app called system api |

## 示例

ArkTS-Dyn示例：

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

ArkTS-Sta示例：

```TypeScript
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


## move

```TypeScript
function move(logType: string, logName: string, dest: string, callback: AsyncCallback<void>): void
```

移动指定日志类型的指定文件到目标应用目录下。使用callback回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**需要权限：** ohos.permission.WRITE_HIVIEW_SYSTEM

<!--Device-logLibrary-function move(logType: string, logName: string, dest: string, callback: AsyncCallback<void>): void--><!--Device-logLibrary-function move(logType: string, logName: string, dest: string, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.HiviewDFX.Hiview.LogLibrary

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| logType | string | 是 | 日志类型字符串，例如“HILOG”, "FAULTLOG", "BETACLUB", "REMOTELOG"等。 |
| logName | string | 是 | 日志文件名称。 |
| dest | string | 是 | 目标目录，需填入相对目录名称。传入dest字串后，日志文件将保存到应用缓存路径下的"hiview/*dest*"文件夹，即"../cache/hiview/*dest*"。可填入多 层目录。 &lt;br&gt;如果传入空字串，将保存到根目录下，即应用缓存路径下的hiview文件夹。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;void&gt; | 是 | 回调函数，可以在回调函数中处理接口返回值。0表示移动成功，其它值表示移动失败。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Invalid argument. Possible causes: &lt;br&gt;1. Mandatory parameters are left unspecified. &lt;br&gt;2. Incorrect parameter types. &lt;br&gt;3. Parameter verification failed. |
| [21300001](../errorcode-loglibrary-sys.md#21300001-指定文件不存在) | Source file does not exists |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission denied, non-system app called system api |

## 示例

ArkTS-Dyn示例：

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

ArkTS-Sta示例：

```TypeScript
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

