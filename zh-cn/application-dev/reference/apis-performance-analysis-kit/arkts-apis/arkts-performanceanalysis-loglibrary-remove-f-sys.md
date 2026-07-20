# remove（系统接口）

## 导入模块

```TypeScript
import { logLibrary } from '@kit.PerformanceAnalysisKit';
```

<a id="remove"></a>
## remove

```TypeScript
function remove(logType: string, logName: string): void
```

以同步方法删除指定日志类型的指定文件。

**起始版本：** 10

**需要权限：** ohos.permission.WRITE_HIVIEW_SYSTEM

<!--Device-logLibrary-function remove(logType: string, logName: string): void--><!--Device-logLibrary-function remove(logType: string, logName: string): void-End-->

**系统能力：** SystemCapability.HiviewDFX.Hiview.LogLibrary

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| logType | string | 是 | 日志类型字符串，例如"FAULTLOG", "BETACLUB", "REMOTELOG"等。 |
| logName | string | 是 | 日志文件名称。 |

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
    logLibrary.remove('FAULTLOG', logFiles[0].name);
  }
} catch (error) {
  console.error(`Failed to call logLibrary API. Code: ${error?.code}, message: ${error?.message}`);
}

```

