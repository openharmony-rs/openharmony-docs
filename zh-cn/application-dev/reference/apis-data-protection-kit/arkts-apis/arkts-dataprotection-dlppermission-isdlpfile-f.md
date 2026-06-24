# isDLPFile

## isDLPFile

```TypeScript
function isDLPFile(fd: number): Promise<boolean>
```

根据文件的fd，查询该文件是否是DLP文件。使用Promise异步回调。

在文件处理流程中，需要先判断文件是否为DLP文件，再决定后续处理策略（如是否需要通过DLP沙箱打开）。

**起始版本：** 10

**系统能力：** SystemCapability.Security.DataLossPrevention

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| fd | number | 是 | 待查询文件的fd（文件描述符）。取值范围为[0, 231-1]。当fd小于0时，函数返回false；当fd大于231-1时，fd的值被截<br/>断。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;boolean&gt; | Promise对象。返回true表示是DLP文件，返回false表示非DLP文件。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br/>2. Incorrect parameter types. |
| [19100001](../../errorcode-universal.md#19100001-Invalid) | Invalid parameter value. |
| [19100011](../../errorcode-universal.md#19100011-The) | The system ability works abnormally. |

**示例：**

```TypeScript
import { dlpPermission } from '@kit.DataProtectionKit';
import { fileIo } from '@kit.CoreFileKit';

let uri = "file://docs/storage/Users/currentUser/Documents/test.txt.dlp";
let file: number | undefined = undefined;
file = fileIo.openSync(uri).fd;
dlpPermission.isDLPFile(file).then((isDLPFile: boolean) => {
    console.info(JSON.stringify(isDLPFile));
}).catch((error: BusinessError)=> {
    console.error(error.message);
}).finally(()=> {
    if (file !== undefined) {
        fileIo.closeSync(file);
    }
});

```


## isDLPFile

```TypeScript
function isDLPFile(fd: number, callback: AsyncCallback<boolean>): void
```

根据文件的fd，查询该文件是否是DLP文件。调用成功后返回查询结果，true表示是DLP文件，false表示非DLP文件。使用callback异步回调。

在文件处理流程中，需要先判断文件是否为DLP文件，再决定后续处理策略（如是否需要通过DLP沙箱打开）。

**起始版本：** 10

**系统能力：** SystemCapability.Security.DataLossPrevention

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| fd | number | 是 | 待查询文件的fd（文件描述符）。取值范围为[0, 231-1]。当fd小于0时，函数返回false；当fd大于231-1时，fd的值被截<br/>断。 |
| callback | AsyncCallback&lt;boolean&gt; | 是 | 回调函数，用于接收查询结果。回调参数包括：err（错误对象，查询成功时为undefined）和res（查询结果，返回true表示是DLP<br/>文件，返回false表示非DLP文件）。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br/>2. Incorrect parameter types. |
| [19100001](../../errorcode-universal.md#19100001-Invalid) | Invalid parameter value. |
| [19100011](../../errorcode-universal.md#19100011-The) | The system ability works abnormally. |

**示例：**

```TypeScript
import { dlpPermission } from '@kit.DataProtectionKit';
import { fileIo } from '@kit.CoreFileKit';

let uri = "file://docs/storage/Users/currentUser/Desktop/test.txt.dlp";
let file: number | undefined = undefined;
file = fileIo.openSync(uri).fd;
dlpPermission.isDLPFile(file, (err, isDLPFile) => {
 if (err != undefined) {
    console.error('isDLPFile error,', err.code, err.message);
  } else {
    console.info('isDLPFile:', isDLPFile);
  }
  fileIo.closeSync(file);
});

```

